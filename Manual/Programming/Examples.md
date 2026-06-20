# Examples

> Five worked examples from minimal to complete. All code is taken from the
> engine source or GameTemplates so you can't go wrong.

---

## Example A — Minimal "Hello World" Component

The smallest unit that compiles, registers, and appears in the editor. Save as
`Components/HelloComponent.h` and include it from one .cpp.

```cpp
// HelloComponent.h
#pragma once
#include <CryEntitySystem/IEntityComponent.h>
#include <CrySchematyc/Env/IEnvRegistrar.h>
#include <CrySchematyc/Env/Elements/EnvComponent.h>
#include <CryCore/StaticInstanceList.h>

class CHelloComponent final : public IEntityComponent
{
public:
    virtual Cry::Entity::EventFlags GetEventMask() const override
    {
        return Cry::Entity::EEvent::GameplayStarted;
    }

    virtual void ProcessEvent(const SEntityEvent& event) override
    {
        if (event.event == Cry::Entity::EEvent::GameplayStarted)
            CryLogAlways("[Hello] Hello from entity %s!", m_pEntity->GetName());
    }

    static void ReflectType(Schematyc::CTypeDesc<CHelloComponent>& desc)
    {
        desc.SetGUID("{01234567-89AB-CDEF-0123-456789ABCDEF}"_cry_guid);
        desc.SetEditorCategory("Tutorial");
        desc.SetLabel("Hello");
        desc.SetDescription("Logs a message when gameplay starts.");
    }
};

namespace
{
    static void RegisterHelloComponent(Schematyc::IEnvRegistrar& registrar)
    {
        Schematyc::CEnvRegistrationScope scope =
            registrar.Scope(IEntity::GetEntityScopeGUID());
        scope.Register(SCHEMATYC_MAKE_ENV_COMPONENT(CHelloComponent));
    }
    CRY_STATIC_AUTO_REGISTER_FUNCTION(&RegisterHelloComponent);
}
```

How to use it:

1. Drop this file into `Code/Components/`.
2. Build the project.
3. In the Sandbox Editor, create an entity, select it, click "Add Component"
   in the Inspector, choose **Tutorial → Hello**.
4. Press **F5** (or **Ctrl+G**) to enter game mode. The console shows
   `[Hello] Hello from entity <name>!`.

The four moving parts (GUID in `ReflectType`, `CRY_STATIC_AUTO_REGISTER_FUNCTION`,
`Scope(IEntity::GetEntityScopeGUID())`, `SCHEMATYC_MAKE_ENV_COMPONENT`) are all
present. Match them and you have a working component.

---

## Example B — Rotator Component with an Editable Property

Adds a member to `ReflectType` via `AddMember` so the designer can tweak a value
in the property panel.

```cpp
// RotatorComponent.h
#pragma once
#include <CryEntitySystem/IEntityComponent.h>
#include <CrySchematyc/Env/IEnvRegistrar.h>
#include <CrySchematyc/Env/Elements/EnvComponent.h>
#include <CryCore/StaticInstanceList.h>

class CRotatorComponent final : public IEntityComponent
{
public:
    virtual Cry::Entity::EventFlags GetEventMask() const override
    {
        return Cry::Entity::EEvent::Update;
    }

    virtual void ProcessEvent(const SEntityEvent& event) override
    {
        if (event.event != Cry::Entity::EEvent::Update)
            return;

        const float frameTime = event.fParam[0];
        Ang3 yaw(0, 0, m_degreesPerSecond * frameTime * gf_PI / 180.0f);
        Matrix34 tm = m_pEntity->GetWorldTM();
        tm.AddRotation(yaw);   // rotate around Z
        m_pEntity->SetWorldTM(tm);
    }

    static void ReflectType(Schematyc::CTypeDesc<CRotatorComponent>& desc)
    {
        desc.SetGUID("{AAAAAAAA-BBBB-CCCC-DDDD-EEEEEEEEEEEE}"_cry_guid);
        desc.SetEditorCategory("Tutorial");
        desc.SetLabel("Rotator");
        desc.SetDescription("Continuously rotates the entity around Z.");

        desc.AddMember(&CRotatorComponent::m_degreesPerSecond, 'rotd',
                       "RotationSpeed", "Rotation Speed (deg/s)",
                       "How fast to spin around the Z axis",
                       90.0f);
    }

private:
    float m_degreesPerSecond = 90.0f;
};

namespace
{
    static void RegisterRotatorComponent(Schematyc::IEnvRegistrar& registrar)
    {
        Schematyc::CEnvRegistrationScope scope =
            registrar.Scope(IEntity::GetEntityScopeGUID());
        scope.Register(SCHEMATYC_MAKE_ENV_COMPONENT(CRotatorComponent));
    }
    CRY_STATIC_AUTO_REGISTER_FUNCTION(&RegisterRotatorComponent);
}
```

Notes:

- `event.fParam[0]` is the frame delta time for the `Update` event
  (source:Code/CryEngine/CryCommon/CryEntitySystem/IEntityBasicTypes.h:337-340).
- `AddMember` arguments are: pointer-to-member, the 4-char id `'rotd'`, internal
  name, label, tooltip, default value
  (source:Code/CryEngine/CryCommon/CrySchematyc/Reflection/TypeDesc.h:586-592).

---

## Example C — Full Player Component (Input + Camera + Movement)

This is the `CPlayerComponent` from the `Blank` template, trimmed to the parts
that matter for understanding. It shows the **complete** pattern: input binding,
camera/audio creation on local-player setup, per-frame movement, and network
replication of the input flags.

### Header

```cpp
// Player.h
#pragma once
#include <CryEntitySystem/IEntityComponent.h>
#include <CryMath/Cry_Camera.h>
#include <CrySchematyc/Utils/EnumFlags.h>
#include <DefaultComponents/Cameras/CameraComponent.h>
#include <DefaultComponents/Input/InputComponent.h>
#include <DefaultComponents/Audio/ListenerComponent.h>

class CPlayerComponent final : public IEntityComponent
{
    enum class EInputFlag : uint8
    {
        MoveLeft    = 1 << 0,
        MoveRight   = 1 << 1,
        MoveForward = 1 << 2,
        MoveBack    = 1 << 3
    };

    static constexpr EEntityAspects InputAspect = eEA_GameClientD;

public:
    virtual void Initialize() override;
    virtual Cry::Entity::EventFlags GetEventMask() const override;
    virtual void ProcessEvent(const SEntityEvent& event) override;
    virtual bool NetSerialize(TSerialize ser, EEntityAspects aspect,
                              uint8 profile, int flags) override;
    virtual NetworkAspectType GetNetSerializeAspectMask() const override
    { return InputAspect; }

    static void ReflectType(Schematyc::CTypeDesc<CPlayerComponent>& desc)
    {
        desc.SetGUID("{63F4C0C6-32AF-4ACB-8FB0-57D45DD14725}"_cry_guid);
    }

    bool IsLocalClient() const
    { return (m_pEntity->GetFlags() & ENTITY_FLAG_LOCAL_PLAYER) != 0; }

protected:
    void InitializeLocalPlayer();
    void HandleInputFlagChange(CEnumFlags<EInputFlag> flags,
                                CEnumFlags<EActionActivationMode> activationMode);

    bool m_isAlive = false;
    Cry::DefaultComponents::CCameraComponent*         m_pCameraComponent  = nullptr;
    Cry::DefaultComponents::CInputComponent*          m_pInputComponent   = nullptr;
    Cry::Audio::DefaultComponents::CListenerComponent* m_pAudioListenerComponent = nullptr;

    CEnumFlags<EInputFlag> m_inputFlags;
    Vec2 m_mouseDeltaRotation;
};
```
> source:Code/GameTemplates/cpp/Blank/Code/Components/Player.h:1-95 (trimmed for clarity)

### Implementation

```cpp
// Player.cpp
#include "StdAfx.h"
#include "Player.h"
#include "GamePlugin.h"
#include <CrySchematyc/Env/Elements/EnvComponent.h>
#include <CryCore/StaticInstanceList.h>
#include <CryNetwork/Rmi.h>

namespace
{
    static void RegisterPlayerComponent(Schematyc::IEnvRegistrar& registrar)
    {
        Schematyc::CEnvRegistrationScope scope =
            registrar.Scope(IEntity::GetEntityScopeGUID());
        scope.Register(SCHEMATYC_MAKE_ENV_COMPONENT(CPlayerComponent));
    }
    CRY_STATIC_AUTO_REGISTER_FUNCTION(&RegisterPlayerComponent);
}

void CPlayerComponent::Initialize()
{
    m_pEntity->GetNetEntity()->BindToNetwork();
}

void CPlayerComponent::InitializeLocalPlayer()
{
    // Camera + audio listener are local-player-only
    m_pCameraComponent  = m_pEntity->GetOrCreateComponent<Cry::DefaultComponents::CCameraComponent>();
    m_pAudioListenerComponent = m_pEntity->GetOrCreateComponent<Cry::Audio::DefaultComponents::CListenerComponent>();
    m_pInputComponent   = m_pEntity->GetOrCreateComponent<Cry::DefaultComponents::CInputComponent>();

    // WASD
    m_pInputComponent->RegisterAction("player", "moveleft",
        [this](int mode, float value){ HandleInputFlagChange(EInputFlag::MoveLeft, (EActionActivationMode)mode); });
    m_pInputComponent->BindAction("player", "moveleft", eAID_KeyboardMouse, EKeyId::eKI_A);

    m_pInputComponent->RegisterAction("player", "moveright",
        [this](int mode, float value){ HandleInputFlagChange(EInputFlag::MoveRight, (EActionActivationMode)mode); });
    m_pInputComponent->BindAction("player", "moveright", eAID_KeyboardMouse, EKeyId::eKI_D);

    m_pInputComponent->RegisterAction("player", "moveforward",
        [this](int mode, float value){ HandleInputFlagChange(EInputFlag::MoveForward, (EActionActivationMode)mode); });
    m_pInputComponent->BindAction("player", "moveforward", eAID_KeyboardMouse, EKeyId::eKI_W);

    m_pInputComponent->RegisterAction("player", "moveback",
        [this](int mode, float value){ HandleInputFlagChange(EInputFlag::MoveBack, (EActionActivationMode)mode); });
    m_pInputComponent->BindAction("player", "moveback", eAID_KeyboardMouse, EKeyId::eKI_S);

    // Mouse look
    m_pInputComponent->RegisterAction("player", "mouse_rotateyaw",
        [this](int mode, float value){ m_mouseDeltaRotation.x -= value; });
    m_pInputComponent->BindAction("player", "mouse_rotateyaw", eAID_KeyboardMouse, EKeyId::eKI_MouseX);

    m_pInputComponent->RegisterAction("player", "mouse_rotatepitch",
        [this](int mode, float value){ m_mouseDeltaRotation.y -= value; });
    m_pInputComponent->BindAction("player", "mouse_rotatepitch", eAID_KeyboardMouse, EKeyId::eKI_MouseY);
}

Cry::Entity::EventFlags CPlayerComponent::GetEventMask() const
{
    return Cry::Entity::EEvent::BecomeLocalPlayer
         | Cry::Entity::EEvent::Update
         | Cry::Entity::EEvent::Reset;
}

void CPlayerComponent::ProcessEvent(const SEntityEvent& event)
{
    switch (event.event)
    {
    case Cry::Entity::EEvent::BecomeLocalPlayer:
        InitializeLocalPlayer();
        break;

    case Cry::Entity::EEvent::Update:
        if (!m_isAlive) return;

        const float frameTime = event.fParam[0];
        const float moveSpeed = 20.5f;
        Vec3 velocity = ZERO;

        if (m_inputFlags & EInputFlag::MoveLeft)   velocity.x -= moveSpeed * frameTime;
        if (m_inputFlags & EInputFlag::MoveRight)  velocity.x += moveSpeed * frameTime;
        if (m_inputFlags & EInputFlag::MoveForward)velocity.y += moveSpeed * frameTime;
        if (m_inputFlags & EInputFlag::MoveBack)   velocity.y -= moveSpeed * frameTime;

        Matrix34 tm = m_pEntity->GetWorldTM();
        tm.AddTranslation(tm.TransformVector(velocity));

        Ang3 ypr = CCamera::CreateAnglesYPR(Matrix33(tm));
        const float rotationSpeed = 0.002f;
        ypr.x += m_mouseDeltaRotation.x * rotationSpeed;
        ypr.y += m_mouseDeltaRotation.y * rotationSpeed;
        ypr.z = 0;
        tm.SetRotation33(CCamera::CreateOrientationYPR(ypr));

        m_mouseDeltaRotation = ZERO;
        m_pEntity->SetWorldTM(tm);
        break;

    case Cry::Entity::EEvent::Reset:
        m_isAlive = event.nParam[0] != 0;
        break;
    }
}

bool CPlayerComponent::NetSerialize(TSerialize ser, EEntityAspects aspect,
                                      uint8 profile, int flags)
{
    if (aspect == InputAspect)
    {
        ser.BeginGroup("PlayerInput");
        ser.Value("m_inputFlags", m_inputFlags.UnderlyingValue(), 'ui8');
        ser.EndGroup();
    }
    return true;
}

void CPlayerComponent::HandleInputFlagChange(
    const CEnumFlags<EInputFlag> flags,
    const CEnumFlags<EActionActivationMode> activationMode)
{
    if (activationMode == eAAM_OnRelease)
        m_inputFlags &= ~flags;
    else
        m_inputFlags |= flags;

    if (IsLocalClient())
        NetMarkAspectsDirty(InputAspect);
}
```
> source:Code/GameTemplates/cpp/Blank/Code/Components/Player.cpp:24-271 (trimmed)

Key things to learn:

- **Input** is bound via `CInputComponent::RegisterAction(group, name, lambda)`
  + `BindAction(group, name, device, key)`. The lambda receives
  `(int activationMode, float value)`. The activation mode is one of
  `eAAM_OnPress`, `eAAM_OnRelease`, `eAAM_OnHold`
  (source:Code/CryEngine/CryCommon/CryAction/IActionMapManager.h:15-20).
  The device enum `eAID_KeyboardMouse` is a bit flag at
  source:Code/CryEngine/CryCommon/CryAction/IActionMapManager.h:95.
- **Camera & audio listener** are *only* created on the local player, inside
  `InitializeLocalPlayer()`. This is triggered by the `BecomeLocalPlayer`
  event.
- **Per-frame logic** lives in `ProcessEvent` under the `Update` case. The frame
  time is in `event.fParam[0]`.
- **Network replication** is the `NetSerialize` + `GetNetSerializeAspectMask`
  pair. Mark dirty with `NetMarkAspectsDirty(InputAspect)` after local input
  changes.
- **`CCamera::CreateAnglesYPR` / `CreateOrientationYPR`** convert between yaw/
  pitch/roll Euler angles and a rotation matrix. See
  [Cameras (API Reference)](../../../API%20Reference/Entity/Cameras.md).

---

## Example D — Bullet Component (Physics + Collision)

The `Bullet` component from `TopDownShooter` shows loading geometry,
physicalizing an entity, applying an impulse, and listening for collision:

```cpp
// Bullet.h
class CBulletComponent final : public IEntityComponent
{
public:
    virtual void Initialize() override
    {
        const int geometrySlot = 0;
        m_pEntity->LoadGeometry(geometrySlot,
            "%ENGINE%/EngineAssets/Objects/primitive_sphere.cgf");

        auto* pBulletMaterial =
            gEnv->p3DEngine->GetMaterialManager()->LoadMaterial("Materials/bullet");
        m_pEntity->SetMaterial(pBulletMaterial);

        SEntityPhysicalizeParams physParams;
        physParams.type = PE_RIGID;
        physParams.mass = 20000.f;
        m_pEntity->Physicalize(physParams);

        GetEntity()->SetViewDistRatio(255);

        if (auto* pPhysics = GetEntity()->GetPhysics())
        {
            pe_action_impulse impulseAction;
            const float initialVelocity = 1000.f;
            impulseAction.impulse =
                GetEntity()->GetWorldRotation().GetColumn1() * initialVelocity;
            pPhysics->Action(&impulseAction);
        }
    }

    static void ReflectType(Schematyc::CTypeDesc<CBulletComponent>& desc)
    {
        desc.SetGUID("{B53A9A5F-F27A-42CB-82C7-B1E379C41A2A}"_cry_guid);
    }

    virtual Cry::Entity::EventFlags GetEventMask() const override
    { return ENTITY_EVENT_COLLISION; }

    virtual void ProcessEvent(const SEntityEvent& event) override
    {
        if (event.event == ENTITY_EVENT_COLLISION)
        {
            // event.nParam[0] is const EventPhysCollision*
            gEnv->pEntitySystem->RemoveEntity(GetEntityId());
        }
    }
};
```
> source:Code/GameTemplates/cpp/TopDownShooter/Code/Components/Bullet.h:1-69

Things to notice:

- **`LoadGeometry(slot, path)`** — slot 0 is the standard geometry slot. The
  `%ENGINE%` token resolves to the engine assets folder
  (source:Code/CryEngine/CryCommon/CryEntitySystem/IEntity.h:1178-1179).
- **`SEntityPhysicalizeParams`** — controls physicalization. `type` is one of
  `PE_RIGID`, `PE_STATIC`, `PE_SOFT`, `PE_PARTICLE`, `PE_PLAYER`, `PE_AREA`,
  `PE_WHEELEDVEHICLE`, ... `mass` or `density` must be set (only one)
  (source:Code/CryEngine/CryCommon/CryEntitySystem/IEntity.h:272-352).
- **`pe_action_impulse`** — the physics action that applies a one-shot impulse.
  Sent via `pPhysics->Action(...)`. The bullet fires in the entity's forward
  direction (`GetWorldRotation().GetColumn1()`), which matches
  `IEntity::GetForwardDir()`
  (source:Code/CryEngine/CryCommon/CryEntitySystem/IEntity.h:1330-1340).
- **`ENTITY_EVENT_COLLISION`** is a legacy alias for
  `Cry::Entity::EEvent::PhysicsCollision`
  (source:Code/CryEngine/CryCommon/CryEntitySystem/IEntityBasicTypes.h:385).
  The collision data is at `event.nParam[0]` as a `const EventPhysCollision*`
  (source:Code/CryEngine/CryCommon/CryEntitySystem/IEntityBasicTypes.h:219-223).

To spawn a bullet at runtime:

```cpp
SEntitySpawnParams spawnParams;
spawnParams.pClass = gEnv->pEntitySystem->GetClassRegistry()->GetDefaultClass();
spawnParams.sName  = "Bullet";
spawnParams.vPosition = m_pEntity->GetWorldPos();
spawnParams.qRotation = m_pEntity->GetWorldRotation();

if (IEntity* pBulletEntity = gEnv->pEntitySystem->SpawnEntity(spawnParams))
{
    pBulletEntity->GetOrCreateComponentClass<CBulletComponent>();
}
```

---

## Example E — SpawnPoint Component (Editor-Visible, No Logic)

The `SpawnPoint` from `TopDownShooter` is a minimal component that exists only
to mark a position in the editor. It has no `Initialize` or `ProcessEvent` —
just `ReflectType` with editor metadata:

```cpp
// SpawnPoint.h
class CSpawnPointComponent final : public IEntityComponent
{
public:
    CSpawnPointComponent() = default;
    virtual ~CSpawnPointComponent() = default;

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

    static Matrix34 GetFirstSpawnPointTransform()
    {
        IEntityItPtr pEntityIterator = gEnv->pEntitySystem->GetEntityIterator();
        pEntityIterator->MoveFirst();

        while (!pEntityIterator->IsEnd())
        {
            IEntity *pEntity = pEntityIterator->Next();
            if (CSpawnPointComponent* pSpawner = pEntity->GetComponent<CSpawnPointComponent>())
            {
                return pSpawner->GetWorldTransformMatrix();
            }
        }
        return IDENTITY;
    }
};
```
> source:Code/GameTemplates/cpp/TopDownShooter/Code/Components/SpawnPoint.h:1-45

The registration (in the .cpp):

```cpp
// SpawnPoint.cpp
static void RegisterSpawnPointComponent(Schematyc::IEnvRegistrar& registrar)
{
    Schematyc::CEnvRegistrationScope scope = registrar.Scope(IEntity::GetEntityScopeGUID());
    {
        Schematyc::CEnvRegistrationScope componentScope = scope.Register(SCHEMATYC_MAKE_ENV_COMPONENT(CSpawnPointComponent));
    }
}
CRY_STATIC_AUTO_REGISTER_FUNCTION(&RegisterSpawnPointComponent)
```
> source:Code/GameTemplates/cpp/TopDownShooter/Code/Components/SpawnPoint.cpp:17-28

The `GetFirstSpawnPointTransform()` static helper iterates all entities looking
for one with a `CSpawnPointComponent` and returns its world transform. This is
how the player finds where to spawn.

---

## Next

- [Plugin Update Loop](Plugin%20Update%20Loop.md) — per-frame plugin-level logic
- [Troubleshooting](Troubleshooting.md) — common pitfalls
- [Entity Component Programming](../Entities%20and%20Tools/Entity%20Component%20Programming.md) — deeper API reference