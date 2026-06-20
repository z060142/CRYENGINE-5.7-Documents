# Schematyc Guide

> How to make your C++ component visible in the Sandbox Editor with editable
> properties.

This is the bit newcomers find confusing, so it gets its own article.

---

## 1. The Two Halves of "Schematyc"

1. **Reflection** (`ReflectType`) — you describe your component's class to the
   engine: a unique GUID, a label, an editor category, and which member
   variables should appear as editable properties.
2. **Registration** — at startup, you hand those reflected descriptions to the
   Schematyc environment registry under a scope. The Sandbox Editor reads that
   registry and populates its "Add Component" menu.

Both halves are required. A component with `ReflectType` but no registration is
invisible to the editor. A component that is registered but has no `ReflectType`
won't appear in the menu either (registration uses the class descriptor produced
by `ReflectType`).

---

## 2. `ReflectType` — Describing the Component

`ReflectType` is a **static** member function. The engine calls it once, lazily,
the first time it needs metadata for your class. The minimal version just sets
a GUID:

```cpp
class CPlayerComponent final : public IEntityComponent
{
    static void ReflectType(Schematyc::CTypeDesc<CPlayerComponent>& desc)
    {
        desc.SetGUID("{63F4C0C6-32AF-4ACB-8FB0-57D45DD14725}"_cry_guid);
    }
    // ...
};
```
> source:Code/GameTemplates/cpp/Blank/Code/Components/Player.h:50-53

A more descriptive version (from the `SpawnPoint` template component) sets
label, category, description and component flags so it shows up nicely in the
editor:

```cpp
static void ReflectType(Schematyc::CTypeDesc<CSpawnPointComponent>& desc)
{
    desc.SetGUID("{41316132-8A1E-4073-B0CD-A242FD3D2E90}"_cry_guid);
    desc.SetEditorCategory("Game");
    desc.SetLabel("SpawnPoint");
    desc.SetDescription("This spawn point can be used to spawn entities");
    desc.SetComponentFlags({ IEntityComponent::EFlags::Transform,
                              IEntityComponent::EFlags::Socket,
                              IEntityComponent::EFlags::Attach });
}
```
> source:Code/GameTemplates/cpp/TopDownShooter/Code/Components/SpawnPoint.h:18-25

Key `CTypeDesc` methods:

| Method | Purpose |
|--------|---------|
| `SetGUID(guid)` | Unique class identifier. Generate a new GUID per class. source:Code/CryEngine/CryCommon/CrySchematyc/Reflection/TypeDesc.h:199 |
| `SetLabel("SpawnPoint")` | Display name in the editor source:Code/CryEngine/CryCommon/CrySchematyc/Reflection/TypeDesc.h:201 |
| `SetEditorCategory("Game")` | Category folder in the Add Component menu source:Code/CryEngine/CryCommon/CrySchematyc/Reflection/TypeDesc.h:216 |
| `SetDescription("...")` | Tooltip text |
| `SetComponentFlags({...})` | Component behavior flags (see [Entities and Components](Entities%20and%20Components.md#4-component-flags)) |
| `AddMember(...)` | Expose a property to the editor (see §3) |
| `AddDependency<T>()` | Hard dependency: T must exist and init before this source:Code/CryEngine/CryCommon/CryEntitySystem/IEntityComponent.h:171-175 |
| `AddSoftDependency<T>()` | Soft dependency: T should init before this if present |
| `AddIncompatible<T>()` | Cannot coexist with T on the same entity |

> **GUID generation:** Use **Tools → Create GUID** in Visual Studio (Registry
> Format) or any online GUID generator. The `"_cry_guid"` suffix tells the
> engine to parse the string at compile time.

---

## 3. Exposing Properties to the Editor — `AddMember`

`AddMember` reflects a C++ member variable so the Sandbox property panel can
edit it. The signature in the engine is:

```cpp
CClassMemberDesc& AddMember(MEMBER_TYPE MEMBER_TYPE_PARENT::* pMember,
                            uint32 id,
                            const char* szName,
                            const char* szLabel,
                            const char* szDescription,
                            const MEMBER_DEFAULT_VALUE_TYPE& defaultValue);
```
> source:Code/CryEngine/CryCommon/CrySchematyc/Reflection/TypeDesc.h:586-592

A real example from the built-in Camera Component:

```cpp
desc.AddMember(&CCameraComponent::m_type,        'type', "Type",        "Type",        "Method of rendering to use for the camera", ECameraType::Default);
desc.AddMember(&CCameraComponent::m_bActivateOnCreate, 'actv', "Active",      "Active",      "Whether or not this camera should be activated on component creation", true);
desc.AddMember(&CCameraComponent::m_nearPlane,   'near', "NearPlane",   "Near Plane",  nullptr, 0.25f);
desc.AddMember(&CCameraComponent::m_farPlane,    'far',  "FarPlane",    "Far Plane",   nullptr, 1024.f);
desc.AddMember(&CCameraComponent::m_fieldOfView, 'fov',  "FieldOfView", "Field of View", nullptr, 70.0_degrees);
```
> source:Code/CryPlugins/CryDefaultEntities/Module/DefaultComponents/Cameras/CameraComponent.h:127-131

### Breaking down the call

For `desc.AddMember(&CCameraComponent::m_nearPlane, 'near', "NearPlane", "Near Plane", nullptr, 0.25f);`:

| Argument | Value | Meaning |
|----------|-------|---------|
| member pointer | `&CCameraComponent::m_nearPlane` | The C++ field to reflect |
| `id` | `'near'` (4-char literal → `uint32`) | Stable, per-class unique member id used for serialization. **Must be unique within the class** and **never reused**. |
| `szName` | `"NearPlane"` | Internal name |
| `szLabel` | `"Near Plane"` | Label shown in the Sandbox property panel |
| `szDescription` | `nullptr` | Tooltip text (or `nullptr` for none) |
| `defaultValue` | `0.25f` | Default value shown on creation |

> **The `id` matters:** it is what the engine writes into saved files to find
> the field back. If you ever rename the C++ member, keep the `id` constant so
> old saves still load. Use a four-character literal that hints at the field
> (`'near'`, `'fov'`, `'sped'`, ...).

### Supported property types

`AddMember` works for:

- Primitive types: `float`, `int`, `bool`, `uint32`, ...
- Math types: `Vec3`, `Quat`, `ColorF`, `Ang3`, ...
- Strings: `Schematyc::CSharedString` or `string`
- Enums (with their own `ReflectType`)
- Nested structs that themselves have a `ReflectType`

See source:Code/CryPlugins/CryDefaultEntities/Module/DefaultComponents/Lights/PointLightComponent.h:62-71
for an example reflecting nested param structs.

### Nested struct properties

If your component has a group of related properties, put them in a struct with
its own `ReflectType`:

```cpp
struct SCombatParams
{
    float damage = 10.0f;
    float range = 5.0f;

    static void ReflectType(Schematyc::CTypeDesc<SCombatParams>& desc)
    {
        desc.SetGUID("{XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX}"_cry_guid);
        desc.AddMember(&SCombatParams::damage, 'dmg', "Damage", "Damage", nullptr, 10.0f);
        desc.AddMember(&SCombatParams::range, 'rang', "Range", "Range", nullptr, 5.0f);
    }
};

class CWeaponComponent : public IEntityComponent
{
    static void ReflectType(Schematyc::CTypeDesc<CWeaponComponent>& desc)
    {
        desc.SetGUID("{YYYYYYYY-YYYY-YYYY-YYYY-YYYYYYYYYYYY}"_cry_guid);
        desc.SetLabel("Weapon");
        desc.AddMember(&CWeaponComponent::m_combat, 'cmbt', "Combat", "Combat Params",
                       "Damage and range", SCombatParams());
    }

    SCombatParams m_combat;
};
```

---

## 4. Registration — `CRY_STATIC_AUTO_REGISTER_FUNCTION`

`ReflectType` only describes the class. To actually add it to the Schematyc
environment, you write a tiny registration function in the .cpp:

```cpp
namespace
{
    static void RegisterPlayerComponent(Schematyc::IEnvRegistrar& registrar)
    {
        Schematyc::CEnvRegistrationScope scope =
            registrar.Scope(IEntity::GetEntityScopeGUID());
        {
            Schematyc::CEnvRegistrationScope componentScope =
                scope.Register(SCHEMATYC_MAKE_ENV_COMPONENT(CPlayerComponent));
        }
    }

    CRY_STATIC_AUTO_REGISTER_FUNCTION(&RegisterPlayerComponent);
}
```
> source:Code/GameTemplates/cpp/TopDownShooter/Code/Components/Player.cpp:14-25

Three things to notice:

1. **`IEntity::GetEntityScopeGUID()`** — all entity components must be registered
   under this fixed scope GUID (`"be845278-0dd2-409f-b8be-97895607c256"`).
   source:Code/CryEngine/CryCommon/CryEntitySystem/IEntity.h:421-425
2. **`SCHEMATYC_MAKE_ENV_COMPONENT(CPlayerComponent)`** — wraps your class into
   an `IEnvElement` that the registry can store.
   source:Code/CryEngine/CryCommon/CrySchematyc/Env/Elements/EnvComponent.h:12
3. **`CRY_STATIC_AUTO_REGISTER_FUNCTION(&RegisterPlayerComponent)`** — adds the
   function pointer to a static linked list of registration callbacks. At
   plugin load time, those callbacks are *not* called immediately; they are
   collected and invoked later when the plugin's
   `ESYSTEM_EVENT_REGISTER_SCHEMATYC_ENV` handler calls
   `Detail::CStaticAutoRegistrar<...>::InvokeStaticCallbacks(registrar)`.
   source:Code/CryEngine/CryCommon/CryCore/StaticInstanceList.h:59-61
   source:Code/CryEngine/CryCommon/CryCore/StaticInstanceList.h:76-85

This two-stage flow (static list → deferred invoke) is why your component
shows up in the editor **only after** the plugin's `RegisterPackage` runs.
Forget the `RegisterPackage` call in `OnSystemEvent` and nothing registers.

---

## 5. The Full Registration Flow — Putting It Together

```
Engine boots
  → loads your DLL (per .cryproject)
  → CRYREGISTER_SINGLETON_CLASS creates the plugin factory
  → engine creates your plugin singleton
  → plugin::Initialize() runs
       → you RegisterListener(this) for system events
  → ...later...
  → engine fires ESYSTEM_EVENT_REGISTER_SCHEMATYC_ENV
       → your plugin::OnSystemEvent calls
            gEnv->pSchematyc->GetEnvRegistry().RegisterPackage(
                ... staticAutoRegisterLambda ...)
       → the lambda calls
            Detail::CStaticAutoRegistrar<...>::InvokeStaticCallbacks(registrar)
       → which calls your RegisterPlayerComponent(registrar)
       → which calls scope.Register(SCHEMATYC_MAKE_ENV_COMPONENT(CPlayerComponent))
       → Schematyc reads CPlayerComponent::ReflectType()
       → your component is now in the registry
  → Sandbox Editor (when it opens) reads the registry
  → your component appears in the "Add Component" menu under "Game"
```

If at any point in this chain something is missing, the component will not
appear. See [Troubleshooting](Troubleshooting.md) for the full checklist.

---

## 6. Schematyc Signals (Advanced)

Components can send and receive signals for decoupled communication. A signal
is a struct with a `ReflectType` (just like a component):

```cpp
struct SPlayerDiedSignal {
    inline void ReflectType(Schematyc::CTypeDesc<SPlayerDiedSignal>& desc) {
        desc.SetGUID("{...}"_cry_guid);
        desc.SetLabel("PlayerDied");
    }
};

// Send
pEntity->GetSchematycObject()->ProcessSignal(SPlayerDiedSignal(), GetGUID());

// Receive (in another component)
void COtherComponent::ProcessSignal(const SObjectSignal& signal) {
    if (signal.typeGUID == Schematyc::GetTypeGUID<SPlayerDiedSignal>()) { /* ... */ }
}
```

Signals enable Schematyc visual-scripting graphs to react to C++ events without
a hard dependency between the sender and receiver.

---

## 7. Schematyc Functions & Actions (Advanced)

Beyond components, Schematyc can expose:

- **Functions** — C++ methods callable from Schematyc visual scripting via
  `SCHEMATYC_MAKE_ENV_FUNCTION`.
  source:Code/CryEngine/CryCommon/CrySchematyc/Env/Elements/EnvFunction.h:17
- **Actions** — long-running operations with init/start/stop/shutdown phases.
  Inherit from `Schematyc::CAction` and register with
  `SCHEMATYC_MAKE_ENV_ACTION`.

These are used when you want Schematyc graph authors to call into your C++ code
from a visual node. For most gameplay, components with `ReflectType` +
`AddMember` are sufficient.

---

## Next

- [Examples](Examples.md) — see ReflectType + AddMember + registration in
  working code
- [Lua Scripting](Lua%20Scripting.md) — the lighter-weight alternative for
  designer-facing scripting
- [Entity Component Programming](../Entities%20and%20Tools/Entity%20Component%20Programming.md) — deeper API reference