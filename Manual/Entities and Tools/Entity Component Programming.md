# Entity Component Programming

CRYENGINE 5.4+ uses a modern Entity Component system. Entities are containers
that hold Components — each component provides a specific piece of
functionality (mesh, physics, camera, input, AI, custom...). This replaces the
legacy `IGameObjectExtension` system.

> **API reference:** For the full `IEntityComponent` interface, type/instance
> GUIDs, events, transform, create/query functions, and editor properties,
> see [Entity Components (API Reference)](../../API%20Reference/Entity/Components.md)
> and [Entity (API Reference)](../../API%20Reference/Entity.md). This page
> focuses on concepts, workflows, the Schematyc integration, and the built-in
> component catalog.

---

## Architecture

```
IEntitySystem (entity manager)
  └── IEntity (container)
        ├── IEntityComponent (mesh, physics, camera, input, AI, custom...)
        ├── IEntityComponent
        └── IEntityComponent ...
              └── Schematyc integration (signals, functions, editor exposure)
```

Components are registered with **Schematyc** to appear in the Sandbox Editor's
"Add Component" menu and to participate in visual scripting.

---

## IEntityComponent — The Base Interface

**Header:** `Code/CryEngine/CryCommon/CryEntitySystem/IEntityComponent.h`

Every component inherits from `IEntityComponent`. The minimum implementation
requires three methods:

```cpp
class CMyComponent : public IEntityComponent
{
public:
    virtual void Initialize() override;                    // one-time setup
    virtual Cry::Entity::EventFlags GetEventMask() const override;  // which events
    virtual void ProcessEvent(const SEntityEvent& event) override;  // handle events
};
```

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

### Accessing Components

```cpp
auto* pMesh  = m_pEntity->GetComponent<Cry::DefaultComponents::CStaticMeshComponent>();
auto* pInput = m_pEntity->GetOrCreateComponent<Cry::DefaultComponents::CInputComponent>();
m_pEntity->GetAllComponents<CMyComponent>();
m_pEntity->VisitComponents([](IEntityComponent* p) { /* ... */ });
```

For the complete set of create/query/template/low-level functions, see
[Components (API Reference)](../../API%20Reference/Entity/Components.md).

### Component Flags

Key flags (`EEntityComponentFlags`):

| Flag | Meaning |
|------|---------|
| `Singleton` | Only one instance per entity |
| `Legacy` | Legacy component (no Schematyc) |
| `HiddenFromUser` | Not shown in editor UI |
| `Transform` | Has its own transform offset |
| `Socket` | Can be a parent to other components |
| `Attach` | Can be attached to a parent component |
| `ClientOnly` / `ServerOnly` | Network scope restriction |
| `NetNotReplicate` | Not network-replicated |

---

## Entity Events

**Header:** `Code/CryEngine/CryCommon/CryEntitySystem/IEntityBasicTypes.h`

Components subscribe to events via `GetEventMask()`. The most commonly used:

| Event | When | Typical Use |
|-------|------|-------------|
| `GameplayStarted` | Game mode entered | Activate gameplay logic |
| `Update` | Every frame | Per-frame logic (`fParam[0]` = delta time) |
| `PrePhysicsUpdate` | Before physics step | Pre-physics adjustments |
| `TransformChanged` | Entity moved/rotated/scaled | React to movement |
| `Reset` | Editor reset / game restart | Reset state |
| `Remove` | Before entity removal | Cleanup |
| `Hidden` / `Unhidden` | Visibility change | Pause/resume processing |
| `PhysicsCollision` | Collision occurred | Collision response |
| `EditorPropertyChanged` | Property edited in Sandbox | React to editor changes |
| `BecomeLocalPlayer` | Entity becomes local player | Initialize player-specific logic |
| `NetworkAuthorityChanged` | Authority transfer | Handle authority change |

The full enum defines 57 events — see the header for the complete list.

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

## Schematyc — Registering Components for the Editor

Schematyc is the **environment registry** that makes components visible in
the Sandbox Editor, exposes their properties, and enables visual scripting.

> **Important:** Schematyc is mandatory for any component that should appear
> in the editor's "Add Component" menu or participate in visual scripting.

### Step 1: Component Descriptor (ReflectType)

Every Schematyc-registered component must have a `ReflectType` specialization
that describes its metadata:

```cpp
inline void ReflectType(Schematyc::CTypeDesc<CMyComponent>& desc)
{
    desc.SetGUID("{XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX}"_cry_guid);
    desc.SetLabel("My Component");
    desc.SetDescription("Description shown in Sandbox");
    desc.SetEditorCategory("Custom");
    desc.SetComponentFlags({ IEntityComponent::EFlags::Transform,
                              IEntityComponent::EFlags::Socket });

    // Expose properties to the Sandbox property panel
    desc.AddMember(&CMyComponent::m_speed, 'sped', "Speed", "Speed",
                   "Movement speed", 10.0f);
    desc.AddMember(&CMyComponent::m_enabled, 'enab', "Enabled", "Enabled",
                   "Enable component", true);
}
```

GUIDs can be generated in Visual Studio via **Tools → Create GUID**
(Registry Format).

### Step 2: Registration Macro

```cpp
SCHEMATYC_MAKE_ENV_COMPONENT(CMyComponent)
```

This creates a `CEnvComponent<CMyComponent>` descriptor for Schematyc.

### Step 3: Register During Plugin Init

```cpp
bool CMyPlugin::Initialize(SSystemGlobalEnvironment& env, const SSystemInitParams& params)
{
    Schematyc::IEnvRegistrar& registrar = gEnv->pSchematyc->GetEnvRegistry().GetRegistrar();
    auto scope = registrar.Scope(IEntity::GetEntityScopeGUID());
    scope.Register(SCHEMATYC_MAKE_ENV_COMPONENT(CMyComponent));
    return true;
}
```

### Schematyc Signals

Components can send and receive signals for decoupled communication:

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

### Schematyc Functions & Actions

- **Functions** — expose C++ methods to Schematyc visual scripting via
  `SCHEMATYC_MAKE_ENV_FUNCTION`.
- **Actions** — long-running operations with init/start/stop/shutdown phases.
  Inherit from `Schematyc::CAction` and register with
  `SCHEMATYC_MAKE_ENV_ACTION`.

---

## IEntitySystem — Entity Manager

**Header:** `Code/CryEngine/CryCommon/CryEntitySystem/IEntitySystem.h`

Obtained via `gEnv->pEntitySystem`.

### Spawning Entities

```cpp
SEntitySpawnParams params;
params.vPosition = Vec3(0, 0, 0);
params.qRotation = IDENTITY;
params.sName = "MyEntity";
params.pClass = pEntityClass;  // optional

IEntity* pEntity = gEnv->pEntitySystem->SpawnEntity(params);

// Add components after spawn
pEntity->GetOrCreateComponent<Cry::DefaultComponents::CStaticMeshComponent>();
pEntity->GetOrCreateComponent<Cry::DefaultComponents::CRigidBodyComponent>();
```

### Lookup, Removal, Flags, Transform, Slots, Hierarchy

For the full API on entity lookup (by ID/name/GUID/iterator), removal,
flags (`ENTITY_FLAG_CASTSHADOW`, `ENTITY_FLAG_NO_SAVE`, etc.), transform
manipulation, slots (geometry/character loading), physicalization,
parent/child hierarchy, and entity links, see
[Entity (API Reference)](../../API%20Reference/Entity.md) and
[Slots, Geometry and Effects](../../API%20Reference/Entity/Slots,%20Geometry%20and%20Effects.md)
and
[Physics and Movement](../../API%20Reference/Entity/Physics%20and%20Movement.md).

---

## Default Components Reference

The `Cry::DefaultComponents` namespace provides built-in components that
appear in the Sandbox "Add Component" menu. All are registered via
`SCHEMATYC_MAKE_ENV_COMPONENT`.

> **Editor docs:** For editor-side usage of these components (properties
> panel, workflows), see
> [Entity Components](Entity%20Components.md) and the version-specific
> subpages.

### Geometry

| Component | Purpose |
|-----------|---------|
| `CStaticMeshComponent` | Static mesh (.cgf) |
| `CAnimatedMeshComponent` | Animated/skinned mesh (.cdf/.chr) |
| `CAdvancedAnimationComponent` | Mannequin animation controller |
| `CAlembicComponent` | Alembic geometry cache playback |

### Physics

| Component | Purpose |
|-----------|---------|
| `CRigidBodyComponent` | Rigid body dynamics |
| `CRagdollComponent` | Ragdoll (extends RigidBody) |
| `CCharacterControllerComponent` | Walking character controller |
| `CVehiclePhysicsComponent` | Wheeled vehicle physics |
| `CWheelComponent` | Individual wheel (requires Vehicle) |
| `CAreaComponent` | Physics area (gravity, buoyancy) |
| `CThrusterComponent` | Constant/single thrust force |
| `CClothComponent` | Cloth simulation |
| `CPhysParticleComponent` | Physics particle |
| `CWaterVolumeComponent` | Water volume |
| `CLocalGridComponent` | Local physics grid |
| `CBoxPrimitiveComponent` / `CSpherePrimitiveComponent` / `CCapsulePrimitiveComponent` / `CCylinderPrimitiveComponent` | Collider primitives |

### Cameras

| Component | Purpose |
|-----------|---------|
| `CCameraComponent` | Standard camera |
| `CRoomscaleCameraComponent` | Room-scale VR camera |

### Lights

| Component | Purpose |
|-----------|---------|
| `CPointLightComponent` | Point/omni light |
| `CProjectorLightComponent` | Projector/spot light |
| `CEnvironmentProbeComponent` | Environment probe (cubemap) |

### Audio

| Component | Purpose |
|-----------|---------|
| `CListenerComponent` | Audio listener |
| `CTriggerComponent` | Play/stop audio triggers |
| `CParameterComponent` | Set audio RTPC parameter |
| `CSwitchStateComponent` | Set audio switch state |
| `CEnvironmentComponent` | Audio environment |
| `CPreloadComponent` | Preload/unload audio banks |
| `CAreaComponent` | Audio area with fade/enter/exit signals |
| `COcclusionComponent` | Audio occlusion/obstruction |

### Effects

| Component | Purpose |
|-----------|---------|
| `CDecalComponent` | Decal projection |
| `CFogComponent` | Fog volume |
| `CParticleComponent` | Particle emitter |
| `CRainComponent` | Rain volume |
| `CWaterRippleComponent` | Water ripple interaction |

### Constraints

| Component | Purpose |
|-----------|---------|
| `CPointConstraintComponent` | Point constraint (ball joint) |
| `CLineConstraintComponent` | Line constraint (slider) |
| `CPlaneConstraintComponent` | Plane constraint |
| `CBreakableJointComponent` | Breakable joint |

### Input

| Component | Purpose |
|-----------|---------|
| `CInputComponent` | Keyboard/mouse/gamepad input binding |

### Debug

| Component | Purpose |
|-----------|---------|
| `CDebugDrawComponent` | Debug drawing primitives |

### AI (in CryAISystem / CryPerceptionSystem / CrySensorSystem)

| Component | Purpose |
|-----------|---------|
| `CEntityAIBehaviorTreeComponent` | Behavior tree execution |
| `CEntityAINavigationComponent` | Navigation/movement |
| `CEntityAIFactionComponent` | Faction membership |
| `CEntityAICoverUserComponent` | Cover usage |
| `CEntityAIObserverComponent` | Vision perception |
| `CEntityAIObservableComponent` | Observable by others |
| `CEntityAIListenerComponent` | Hearing perception |
| `CAINavigationMarkupShapeComponent` | NavMesh markup |

---

## Creating a Custom Component — Full Example

```cpp
// MyPlayerComponent.h
class CMyPlayerComponent final : public IEntityComponent
{
public:
    virtual void Initialize() override;
    virtual Cry::Entity::EventFlags GetEventMask() const override;
    virtual void ProcessEvent(const SEntityEvent& event) override;

    static void ReflectType(Schematyc::CTypeDesc<CMyPlayerComponent>& desc)
    {
        desc.SetGUID("{A1B2C3D4-E5F6-7890-ABCD-EF1234567890}"_cry_guid);
        desc.SetLabel("My Player");
        desc.SetDescription("Custom player component");
        desc.SetEditorCategory("Game");
        desc.SetComponentFlags({ IEntityComponent::EFlags::Singleton,
                                  IEntityComponent::EFlags::Socket });
        desc.AddMember(&CMyPlayerComponent::m_health, 'hlth', "Health",
                       "Health", "Player health", 100.0f);
        desc.AddMember(&CMyPlayerComponent::m_speed, 'sped', "Speed",
                       "Speed", "Movement speed", 5.0f);
    }

protected:
    float m_health = 100.0f;
    float m_speed  = 5.0f;
};
```

```cpp
// MyPlayerComponent.cpp
void CMyPlayerComponent::Initialize()
{
    m_pInput = m_pEntity->GetOrCreateComponent<Cry::DefaultComponents::CInputComponent>();
    m_pCharController = m_pEntity->GetOrCreateComponent<Cry::DefaultComponents::CCharacterControllerComponent>();

    m_pInput->RegisterAction("player", "moveforward",
        [this](int mode, float value) { m_moveForward = value; });
    m_pInput->BindKeyboardAction("player", "moveforward", EKeyboardInputId::eKI_W);
}

Cry::Entity::EventFlags CMyPlayerComponent::GetEventMask() const
{
    return Cry::Entity::EEvent::GameplayStarted
         | Cry::Entity::EEvent::Update
         | Cry::Entity::EEvent::Reset;
}

void CMyPlayerComponent::ProcessEvent(const SEntityEvent& event)
{
    switch (event.event)
    {
    case Cry::Entity::EEvent::GameplayStarted:
        break;
    case Cry::Entity::EEvent::Update:
    {
        float frameTime = event.fParam[0];
        Vec3 moveDir = m_pEntity->GetForwardDir() * m_moveForward * m_speed;
        m_pCharController->AddVelocity(moveDir * frameTime);
        break;
    }
    case Cry::Entity::EEvent::Reset:
        m_health = 100.0f;
        m_moveForward = 0.0f;
        break;
    }
}

SCHEMATYC_MAKE_ENV_COMPONENT(CMyPlayerComponent)
```

---

## Entity Classes with Default Components

For entities that always need the same set of components, register an entity
class with default components:

```cpp
IEntityClass* pClass = RegisterEntityClassWithDefaultComponent<CMyPlayerComponent>(
    "MyPlayer",
    "{B1B2B3B4-C5C6-7890-ABCD-EF1234567890}"_cry_guid,  // class GUID
    "{A1A2A3A4-B5B6-7890-ABCD-EF1234567890}"_cry_guid); // component GUID

SEntitySpawnParams params;
params.pClass = pClass;
IEntity* pEntity = gEnv->pEntitySystem->SpawnEntity(params);
// CMyPlayerComponent is automatically created
```

---

## Component Dependency System

Components can declare dependencies and incompatibilities in `ReflectType`:

```cpp
desc.AddDependency<Cry::DefaultComponents::CStaticMeshComponent>();        // hard
desc.AddSoftDependency<Cry::DefaultComponents::CRigidBodyComponent>();     // soft
desc.AddIncompatible<Cry::DefaultComponents::CCharacterControllerComponent>();
```

---

## Network Replication

Components replicate state over the network by overriding `NetSerialize` and
`GetNetSerializeAspects`:

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

    virtual NetworkAspectType GetNetSerializeAspects() const override
    { return eEA_GameClientDynamic; }

protected:
    float m_health;
    int   m_ammo;
};
```

See [Networking](../../API%20Reference/Entity/Networking.md) for aspect
definitions and RMI patterns.

---

## Related Documentation

- [Entity Components](Entity%20Components.md) — editor-side component usage
- [Entity (API Reference)](../../API%20Reference/Entity.md) — IEntity, IEntitySystem
- [Components (API Reference)](../../API%20Reference/Entity/Components.md) — IEntityComponent API
- [Slots, Geometry and Effects](../../API%20Reference/Entity/Slots,%20Geometry%20and%20Effects.md) — slot types
- [Physics and Movement](../../API%20Reference/Entity/Physics%20and%20Movement.md) — physicalization
- [Networking](../../API%20Reference/Entity/Networking.md) — network replication
- [Gameplay Framework](../Gameplay/Gameplay%20Framework%20Programming.md) — IGameFramework, IGameObject (legacy)
- [Plugin System](../Beta%20Features/Plugin%20System.md) — Cry::IEnginePlugin, game module entry point
- [Schematyc Editor](../Beta%20Features/Schematyc.md) — Schematyc visual scripting overview