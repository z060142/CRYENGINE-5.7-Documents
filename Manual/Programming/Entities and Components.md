# Entities and Components

> Where your gameplay code actually lives.

Entities are the things in the world — players, lights, doors, bullets, cameras.
Components are the pieces of functionality attached to an entity — a mesh, a
physics body, an input handler, your custom game logic. **You will spend 90% of
your programming time writing components.**

---

## 1. What Is an Entity? What Is a Component?

> Entities themselves can not contain custom logic, instead they can contain
> Components (see `IEntityComponent`).
> source:Code/CryEngine/CryCommon/CryEntitySystem/IEntity.h:415-416

```
IEntity  (a thing in the world — has transform, name, id, flags)
  ├── IEntityComponent  (mesh)        ┐
  ├── IEntityComponent  (physics)     │  Each component = one piece of
  ├── IEntityComponent  (input)       │  functionality. You add/remove them
  ├── IEntityComponent  (your code)   ┘  at runtime or in the editor.
  └── ...
```

An entity is just a container. It holds a transform (position, rotation,
scale), a name, an `EntityId`, flags, and a list of components. All gameplay
logic lives in the components.

---

## 2. The `IEntityComponent` Interface

The base interface lives in
source:Code/CryEngine/CryCommon/CryEntitySystem/IEntityComponent.h:239.
The virtual methods you most commonly override:

| Method | When called | Typical use |
|--------|-------------|-------------|
| `Initialize()` | Once, after construction | Get/create sibling components, bind input, set up RMI |
| `GetEventMask()` | Engine queries which events you want | Return bitmask of `Cry::Entity::EEvent` flags |
| `ProcessEvent(event)` | When a subscribed event fires | Switch on `event.event`, do per-frame logic |
| `NetSerialize(ser, aspect, ...)` | Network replication | Read/write networked fields |
| `GetNetSerializeAspectMask()` | Engine queries which aspects you serialize | Return your aspect bitmask |
| `OnTransformChanged()` | Entity transform changed | React to movement |
| `OnShutDown()` | Right before the component is destroyed | Cleanup |

> source:Code/CryEngine/CryCommon/CryEntitySystem/IEntityComponent.h:380-447

### Minimum Implementation

```cpp
class CMyComponent : public IEntityComponent
{
public:
    virtual void Initialize() override;                    // one-time setup
    virtual Cry::Entity::EventFlags GetEventMask() const override;  // which events
    virtual void ProcessEvent(const SEntityEvent& event) override;  // handle events
};
```
> source:Code/CryEngine/CryCommon/CryEntitySystem/IEntityComponent.h:380-402

### Component Lifecycle

```
Entity::SpawnEntity(params)
  → Component constructor
  → Initialize()
  → [Editor] GameplayStarted event
  → Per frame: ProcessEvent(Update)  [if subscribed]
  → Entity removal: ProcessEvent(Remove)
  → Component destructor
```

---

## 3. Entity Events You Will Subscribe To

Events are bit flags in `Cry::Entity::EEvent`. The ones you'll use on day one:

| Event | When | `event` payload |
|-------|------|------------------|
| `GameplayStarted` (`BIT64(31)`) | Game mode entered | — |
| `Update` (`BIT64(55)`) | Every frame (must enable update) | `fParam[0]` = frame delta time |
| `PrePhysicsUpdate` (`BIT64(54)`) | Before physics step | `fParam[0]` = frame time |
| `Reset` (`BIT64(4)`) | Enter/leave game mode in editor | `nParam[0]` = 1 enter, 0 leave |
| `BecomeLocalPlayer` (`BIT64(47)`) | Entity becomes the local player | — |
| `PhysicsCollision` (`BIT64(26)`) | Collision happened | `nParam[0]` = `const EventPhysCollision*` |
| `TransformChanged` (`BIT64(0)`) | Position/rotation/scale changed | `nParam[0]` = `EEntityXFormFlags` |
| `EditorPropertyChanged` (`BIT64(42)`) | A property was edited in Sandbox | `nParam[0]` = component ptr |
| `TimerExpired` (`BIT64(56)`) | A component timer fired | `nParam[0]` = timer id |
| `Remove` (`BIT64(3)`) | Before entity removal | — |
> source:Code/CryEngine/CryCommon/CryEntitySystem/IEntityBasicTypes.h:94-349

Legacy constant aliases exist (`ENTITY_EVENT_COLLISION`, `ENTITY_EVENT_START_GAME`,
etc.) and map to the same values
source:Code/CryEngine/CryCommon/CryEntitySystem/IEntityBasicTypes.h:358-414 —
prefer the modern `Cry::Entity::EEvent::...` names in new code.

### Typical ProcessEvent Implementation

```cpp
void CMyComponent::ProcessEvent(const SEntityEvent& event)
{
    switch (event.event)
    {
    case Cry::Entity::EEvent::GameplayStarted:
        break;
    case Cry::Entity::EEvent::Update:
        // event.fParam[0] = frame delta time
        break;
    case Cry::Entity::EEvent::Reset:
        break;
    case Cry::Entity::EEvent::TransformChanged:
        // event.nParam[0] = EEntityXFormFlags
        break;
    }
}
```

---

## 4. Component Flags

When you write `ReflectType` (see [Schematyc Guide](Schematyc%20Guide.md)), you
can set component flags via `desc.SetComponentFlags({...})`. The flags control
how the component behaves in the editor and at runtime:

| Flag | Meaning |
|------|---------|
| `Singleton` | Only one instance per entity |
| `Transform` | Component has its own transform offset |
| `Socket` | Other components can attach to this one |
| `Attach` | This component can be attached to a parent's socket |
| `Legacy` | Legacy component, hidden from the UI |
| `HideFromInspector` | Not addable from the Inspector panel |
| `ServerOnly` / `ClientOnly` | Network scope restriction |
| `NetNotReplicate` | Not network-replicated |
| `HiddenFromUser` | Not shown in the UI at all |
| `NoSave` | Not saved with the entity |

> source:Code/CryEngine/CryCommon/CryEntitySystem/IEntityComponent.h:86-105

---

## 5. Accessing Components on an Entity

```cpp
// Get a sibling component (returns nullptr if absent)
auto* pMesh = m_pEntity->GetComponent<Cry::DefaultComponents::CStaticMeshComponent>();

// Get existing OR create a new one (the engine default way)
auto* pInput = m_pEntity->GetOrCreateComponent<Cry::DefaultComponents::CInputComponent>();

// Create with new (bypass factory — for unregistered components)
auto* pPlayer = m_pEntity->GetOrCreateComponentClass<CPlayerComponent>();

// Iterate all components of a type
DynArray<CMyComp*> all;
m_pEntity->GetAllComponents<CMyComp>(all);
```
> source:Code/CryEngine/CryCommon/CryEntitySystem/IEntity.h:860-943

The difference between `GetOrCreateComponent<T>()` and
`GetOrCreateComponentClass<T>()`:

- **`GetOrCreateComponent<T>()`** — creates via the CryExtension factory. Works
  for components that have been registered with a Schematyc GUID (i.e. they have
  `ReflectType` with `SetGUID`). This is the path that makes the component
  editable in the Sandbox Editor.
  source:Code/CryEngine/CryCommon/CryEntitySystem/IEntity.h:866-879
- **`GetOrCreateComponentClass<T>()`** — creates with `new` directly. Works for
  components that are *not* registered with Schematyc (e.g. the player component
  in the Blank template, which only has a GUID in `ReflectType` but is not
  registered as an env component — it is spawned directly from C++).
  source:Code/CryEngine/CryCommon/CryEntitySystem/IEntity.h:924-943

---

## 6. Spawning an Entity at Runtime

```cpp
SEntitySpawnParams params;
params.vPosition = Vec3(0, 0, 0);
params.qRotation = IDENTITY;
params.vScale    = Vec3(1.f);
params.sName     = "MyEntity";
params.pClass    = gEnv->pEntitySystem->GetClassRegistry()->GetDefaultClass();

if (IEntity* pEntity = gEnv->pEntitySystem->SpawnEntity(params))
{
    pEntity->GetOrCreateComponent<Cry::DefaultComponents::CStaticMeshComponent>();
    pEntity->GetOrCreateComponent<Cry::DefaultComponents::CRigidBodyComponent>();
}
```
> `SEntitySpawnParams` fields: source:Code/CryEngine/CryCommon/CryEntitySystem/IEntity.h:97-162
> `SpawnEntity`: source:Code/CryEngine/CryCommon/CryEntitySystem/IEntitySystem.h:363-369
> Default class lookup and flag bits: source:Code/GameTemplates/cpp/Blank/Code/GamePlugin.cpp:95-107

Key `SEntitySpawnParams` fields:

| Field | Type | Meaning |
|-------|------|---------|
| `vPosition` | `Vec3` | World position (or local if `pParent` set) |
| `qRotation` | `Quat` | World rotation (default `IDENTITY`) |
| `vScale` | `Vec3` | Scale (default `Vec3(1.f)`) |
| `sName` | `const char*` | Entity name (does not need to be unique) |
| `nFlags` | `uint32` | Entity flags (e.g. `ENTITY_FLAG_LOCAL_PLAYER`, `ENTITY_FLAG_CASTSHADOW`) |
| `pClass` | `IEntityClass*` | Entity class (null = default class) |
| `id` | `EntityId` | Optional specific ID (auto-generated if not set) |
| `pParent` | `IEntity*` | Optional parent for hierarchy |

> source:Code/CryEngine/CryCommon/CryEntitySystem/IEntity.h:97-162

---

## 7. Entity Lookup & Iteration

```cpp
// By ID
IEntity* pEntity = gEnv->pEntitySystem->GetEntity(entityId);

// By name
IEntity* pEntity = gEnv->pEntitySystem->FindEntityByName("MyEntity");

// Iterate all entities
IEntityItPtr pIt = gEnv->pEntitySystem->GetEntityIterator();
pIt->MoveFirst();
while (!pIt->IsEnd())
{
    IEntity* pEntity = pIt->Next();
    // ...
}

// Remove
gEnv->pEntitySystem->RemoveEntity(entityId);
```
> source:Code/CryEngine/CryCommon/CryEntitySystem/IEntitySystem.h:363-412

---

## 8. Entity Transform

```cpp
// Read
Vec3 pos     = pEntity->GetWorldPos();
Quat rot     = pEntity->GetWorldRotation();
Vec3 scale   = pEntity->GetScale();
Matrix34 tm  = pEntity->GetWorldTM();
Vec3 forward = pEntity->GetForwardDir();   // column1 of rotation
Vec3 right   = pEntity->GetRightDir();     // column0 of rotation

// Write
pEntity->SetWorldTM(newTM);
pEntity->SetPos(newPos);
pEntity->SetRotation(newRot);
```
> `GetForwardDir`: source:Code/CryEngine/CryCommon/CryEntitySystem/IEntity.h:1330-1340

> **Note:** `GetForwardDir()` returns column 1 (Y axis), and `GetRightDir()`
> returns column 0 (X axis). This matches CRYENGINE's convention where the
> forward direction is +Y, not +Z.

---

## 9. Registering an Entity Class with a Default Component

If you want a named entity class that always carries a particular component
(like `MyPlayer` always spawning with `CMyPlayerComponent`), use the helper
template:

```cpp
IEntityClass* pClass = RegisterEntityClassWithDefaultComponent<CMyPlayerComponent>(
    "MyPlayer",
    "{B1B2B3B4-C5C6-7890-ABCD-EF1234567890}"_cry_guid,   // entity class GUID
    "{A1A2A3A4-B5B6-7890-ABCD-EF1234567890}"_cry_guid);  // unique component instance GUID

// Later, spawning this class auto-creates the component:
SEntitySpawnParams params;
params.pClass = pClass;
gEnv->pEntitySystem->SpawnEntity(params);
```
> source:Code/CryEngine/CryCommon/CryEntitySystem/IEntitySystem.h:729-765

The first GUID is the **entity class** GUID; the second is a **unique instance
GUID** used to identify the component inside that specific entity class. Both
must be unique and never reused.

---

## 10. Network Replication

Components replicate state over the network by overriding `NetSerialize` and
`GetNetSerializeAspectMask`:

```cpp
class CMyNetworkedComponent : public IEntityComponent
{
public:
    virtual bool NetSerialize(TSerialize ser, EEntityAspects aspect,
                               uint8 profile, int flags) override
    {
        if (aspect & eEA_GameClientDynamic) {
            ser.Value("health", m_health, 'hlth');
            ser.Value("ammo", m_ammo, 'ammo');
        }
        return true;
    }

    virtual NetworkAspectType GetNetSerializeAspectMask() const override
    { return eEA_GameClientDynamic; }

protected:
    float m_health;
    int   m_ammo;
};
```
> source:Code/CryEngine/CryCommon/CryEntitySystem/IEntityComponent.h:407-422

Call `NetMarkAspectsDirty(aspect)` after local state changes to trigger
replication. For RMI (Remote Method Invocation) patterns, see
[Networking](../../../API%20Reference/Entity/Networking.md).

---

## Next

- [Schematyc Guide](Schematyc%20Guide.md) — how to make your component appear
  in the Sandbox Editor with editable properties
- [Examples](Examples.md) — ready-to-paste worked examples
- [Entity Component Programming](../Entities%20and%20Tools/Entity%20Component%20Programming.md) — deeper API reference