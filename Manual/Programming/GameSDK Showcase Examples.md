# GameSDK Showcase Examples

> Real-world C++ patterns extracted from the GameSDK sample project
> (`Code/GameSDK/GameDll/`). Each example demonstrates a different subsystem
> and shows how Crytek's own engineers structure non-trivial gameplay code.

These examples use the legacy `IGameObjectExtension` system (the predecessor
to the modern `IEntityComponent`). They are still excellent reference for
**how to structure** a complex gameplay class — physics event handling,
inter-system communication, Flow Graph integration, and state management. For
new projects, adapt the patterns to `IEntityComponent` (see
[Entities and Components](Entities%20and%20Components.md)).

---

## Example 1 — Boids: Flock AI Behavior

**Source:** `Code/GameSDK/GameDll/Boids/`

The Boids system simulates flocking behavior — birds, fish, bugs, chickens.
It demonstrates:

- A **manager class** (`CFlock`) that owns many **individual agents** (`CBoidObject` subclasses)
- Per-agent AI "thinking" with the classic boids algorithm (alignment, cohesion, separation)
- Physics integration for collision avoidance
- Multiple specialized subclasses (`CBoidBird`, `CBoidFish`, `CBoidBugs`, `CBoidChicken`)

### Flock Types

```cpp
enum EFlockType
{
    EFLOCK_BIRDS,
    EFLOCK_FISH,
    EFLOCK_BUGS,
    EFLOCK_CHICKENS,
    EFLOCK_FROGS,
    EFLOCK_TURTLES,
};
```
> source:Code/GameSDK/GameDll/Boids/Flock.h:13-21

### The Flock Manager

`CFlock` is the container that owns all boids in a single flock:

```cpp
class CFlock
{
public:
    CFlock(IEntity* pEntity, EFlockType flockType);
    virtual ~CFlock();

    virtual void CreateBoids(SBoidsCreateContext& ctx);
    virtual void Reset();
    virtual bool CreateEntities();
    virtual CBoidObject* CreateBoid() { return 0; }

    void SetPos(const Vec3& pos);
    Vec3 GetPos() const { return m_origin; }

    void AddBoid(CBoidObject* boid);
    int  GetBoidsCount() { return m_boids.size(); }
    CBoidObject* GetBoid(int index) { return m_boids[index]; }

    float GetMaxVisibilityDistance() const { return m_bc.maxVisibleDistance; }
    void  GetBoidSettings(SBoidContext& bc) { bc = m_bc; }
    void  SetBoidSettings(SBoidContext& bc);

    bool IsFollowPlayer() const { return m_bc.followPlayer; }

    bool RayTest(Vec3& raySrc, Vec3& rayTrg, SFlockHit& hit);

    static void GetDefaultBoidsContext(SBoidContext& bc);
};
```
> source:Code/GameSDK/GameDll/Boids/Flock.h:53-99

### Boid Context (Behavior Parameters)

Each flock shares a `SBoidContext` that holds all the behavior tuning knobs:

```cpp
struct SBoidContext
{
    Vec3 playerPos;
    Vec3 flockPos;

    int behavior;

    float fSpawnRadius;
    float fBoidRadius;
    float fBoidMass;
    float fGravity;

    float MinHeight;
    float MaxHeight;

    float MaxAttractDistance;
    float MinAttractDistance;

    float MaxSpeed;
    float MinSpeed;

    // Group behavior factors.
    float factorAlignment;
    float factorCohesion;
    float factorSeparation;
    // Other behavior factors.
    float factorAttractToOrigin;
    float factorKeepHeight;
    float factorAvoidLand;
    float factorTakeOff;
    float cosFovAngle;
    float factorRandomAccel;

    // Ground behavior factors.
    float factorAlignmentGround;
    float factorCohesionGround;
    float factorSeparationGround;
    float factorAttractToOriginGround;
    float walkSpeed;
    // ...
};
```
> source:Code/GameSDK/GameDll/Boids/BoidObject.h:47-100

### The Think Method (Boids Algorithm)

The core AI logic lives in `CBoidBird::Think()`. It computes acceleration
based on the three classic boids rules plus environment awareness:

```cpp
void CBoidBird::Think( float dt, SBoidContext &bc )
{
    m_accel.zero();

    float factorAlignment = bc.factorAlignment;
    float factorCohesion = bc.factorCohesion;
    float factorSeparation = bc.factorSeparation;
    float factorAvoidLand = bc.factorAvoidLand;
    float factorAttractToOrigin = bc.factorAttractToOrigin;
    float factorKeepHeight = bc.factorKeepHeight;

    // ...state-specific factor adjustments...

    // Free will: try to maintain average speed.
    float targetSpeed = (bc.MaxSpeed + bc.MinSpeed) / 2;
    m_accel -= m_heading * (m_speed - targetSpeed) * 0.5f;

    // Desired height (Gaussian weight).
    float dh = m_desiredHeigh - m_pos.z;
    float dhexp = -(dh * dh) / (3 * 3);
    dhexp = clamp_tpl(dhexp, -70.0f, 70.0f);
    m_accel.z = exp_tpl(dhexp) * factorKeepHeight;

    // Flock behavior: alignment, cohesion, separation.
    if (factorAlignment != 0)
    {
        Vec3 alignmentAccel, cohesionAccel, separationAccel;
        CalcFlockBehavior(bc, alignmentAccel, cohesionAccel, separationAccel);
        m_accel += alignmentAccel  * factorAlignment;
        m_accel += cohesionAccel   * factorCohesion;
        m_accel += separationAccel * factorSeparation;
    }

    // Avoid land.
    if (height < bc.MinHeight && m_status != Bird::LANDING)
    {
        float v = (1.0f - height / bc.MinHeight);
        m_accel += Vec3(0, 0, v * v) * bc.factorAvoidLand;
    }
    else if (height > bc.MaxHeight)
    {
        float v = (height - bc.MaxHeight) * 0.1f;
        m_accel += Vec3(0, 0, -v);
    }

    // Attract to origin (or follow player).
    if (bc.followPlayer)
        m_accel += (bc.playerPos - m_pos) * factorAttractToOrigin;
    else
    {
        if (cry_random(0, 31) == 1)
            m_randomVec = Vec3(Boid::Frand(), Boid::Frand(), 0) * bc.factorRandomAccel;
        m_accel += m_randomVec;
        m_accel += (bc.flockPos - m_pos) * factorAttractToOrigin;
    }
    // ...
}
```
> source:Code/GameSDK/GameDll/Boids/BoidBird.cpp:512-631 (trimmed)

Key takeaways:

- **Boids algorithm**: the three classic forces (alignment, cohesion, separation) are computed by `CalcFlockBehavior()` and scaled by per-flock factors. This is textbook flocking AI.
- **Gaussian height weighting**: `exp_tpl(-(dh*dh)/9)` produces a smooth bell curve that gently pushes the boid toward its desired height. This is a nice trick for smooth, non-linear behavior.
- **Random acceleration**: occasionally injects a random vector (`cry_random(0, 31) == 1`) to make the flock look organic rather than mechanical.
- **State-specific tuning**: factors are adjusted per state (landing, takeoff, ground) — the same physics model with different weights.

### How to Adapt to Modern Components

The `CFlock`/`CBoidObject` pattern (manager + agents) can be adapted to
`IEntityComponent`:

- Make `CFlock` a `IEntityComponent` (singleton on a "FlockManager" entity)
- Each boid becomes an entity with a `CBoidComponent : public IEntityComponent`
- `Think()` runs in `ProcessEvent(EEvent::Update)`
- `CalcFlockBehavior()` queries sibling components on nearby entities

Required when adapting:

- Keep the ownership boundary clear: one manager owns the agent list, while
  each agent owns its own transform/state.
- Provide a visible mesh or explicit debug/log output for spawned agents.
  Default-class entities can exist and move while remaining visually invisible.

Avoid:

- Do not copy the GameSDK flock classes into a Blank-style project unchanged.
  Treat them as behavior structure, not as a drop-in modern component API.

---

## Example 2 — Deflector Shield: Physics Collision + Projectile Deflection

**Source:** `Code/GameSDK/GameDll/Environment/DeflectorShield.h/.cpp`

The Deflector Shield intercepts incoming projectiles and "reflects" their
energy back after a delay. It demonstrates:

- Physics collision event handling via `IGameObject` events
- Deferred action (buffered deflections that fire after a delay)
- Local-space storage of deflection data (so shield movement doesn't break spawns)
- Particle effects on impact
- Projectile spawning with spread

### Collision Event Registration

The shield registers for collision events in `PostInit`:

```cpp
namespace DS
{
    void RegisterEvents( IGameObjectExtension& goExt, IGameObject& gameObject )
    {
        const int eventID = eGFE_OnCollision;
        gameObject.UnRegisterExtForEvents( &goExt, NULL, 0 );
        gameObject.RegisterExtForEvents( &goExt, &eventID, 1 );
    }
}

void CDeflectorShield::PostInit(IGameObject * pGameObject)
{
    DS::RegisterEvents( *this, *pGameObject );
}
```
> source:Code/GameSDK/GameDll/Environment/DeflectorShield.cpp:28-67

Also enables physics collision logging:

```cpp
bool CDeflectorShield::Init(IGameObject * pGameObject)
{
    SetGameObject(pGameObject);
    GetGameObject()->EnablePhysicsEvent(true, eEPE_OnCollisionLogged);
    LoadScriptProperties();
    return true;
}
```
> source:Code/GameSDK/GameDll/Environment/DeflectorShield.cpp:55-62

### Processing a Collision

When a projectile hits the shield, its collision data is stored in local
space (so the shield can move during the delay without breaking the spawn
position):

```cpp
void CDeflectorShield::ProcessProjectile(CProjectile* pProjectile,
                                          Vec3 hitPosition, Vec3 hitNormal,
                                          Vec3 hitDirection)
{
    if (CanProjectilePassThroughShield(pProjectile))
        return;

    const Matrix34& intoWorldTransform = GetEntity()->GetWorldTM();
    Matrix34 intoLocalTransform = intoWorldTransform.GetInvertedFast();

    SDeflectedEnergy deflectedEnergy;
    deflectedEnergy.m_delay = 0.0f;
    deflectedEnergy.m_localPosition = intoLocalTransform.TransformPoint(hitPosition);
    deflectedEnergy.m_localDirection = intoLocalTransform.TransformVector(-hitDirection);
    deflectedEnergy.m_damage = CLAMP(pProjectile->GetDamage(), m_minDamage, m_maxDamage);

    if (deflectedEnergy.m_localDirection.NormalizeSafe() > 0.0f)
    {
        m_deflectedEnergies.push_back(deflectedEnergy);
        GetGameObject()->EnableUpdateSlot(this, 0);
    }

    if (m_pDeflectedEffect)
        m_pDeflectedEffect->Spawn(IParticleEffect::ParticleLoc(hitPosition, hitNormal));

    pProjectile->Destroy();
}
```
> source:Code/GameSDK/GameDll/Environment/DeflectorShield.cpp:276-304

Key technique — **local-space buffering**: the hit position and direction are
transformed into the shield's local space immediately. When the deflected energy
is later shot back (after the delay), it's transformed back to world space using
the shield's *current* transform. This means the shield can rotate/move during
the delay and the energy still spawns from the right relative position.

### Shooting the Deflected Energy

After a delay, the buffered energy is shot back as a new projectile:

```cpp
void CDeflectorShield::ShootDeflectedEnergy(const SDeflectedEnergy& energy)
{
    if (!m_pAmmoClass)
        return;
    CProjectile* pEnergyBlast = g_pGame->GetWeaponSystem()->SpawnAmmo(m_pAmmoClass, false);
    if (!pEnergyBlast)
        return;

    const Matrix34& worldTransform = GetEntity()->GetWorldTM();

    // Transform the buffered local-space position/direction back to world.
    const Vec3 worldReflectPos = worldTransform.TransformPoint(energy.m_localPosition);
    const Vec3 worldReflectDir = worldTransform.TransformVector(energy.m_localDirection);

    // Add spread using two orthogonal vectors to the reflect direction.
    const Vec3 worldSpreadU = worldReflectDir.GetOrthogonal();
    const Vec3 worldSpreadV = worldReflectDir.Cross(worldSpreadU);

    const Vec3 position = worldReflectPos + worldReflectDir * 0.05f;
    Vec3 direction =
        worldReflectDir +
        (worldSpreadU * cry_random(0.0f, m_spread)) +
        (worldSpreadV * cry_random(0.0f, m_spread));
    direction.Normalize();

    CProjectile::SProjectileDesc projectileDesc(
        0, 0, 0, energy.m_damage, m_dropMinDistance, m_dropPerMeter,
        float(m_minDamage), m_hitTypeId, 0, false);
    pEnergyBlast->SetParams(projectileDesc);
    pEnergyBlast->Launch(position, direction, Vec3(ZERO));
}
```
> source:Code/GameSDK/GameDll/Environment/DeflectorShield.cpp:339-369

Key technique — **spread via orthogonal basis**: to add random spread to a
direction, compute two vectors orthogonal to the direction (`GetOrthogonal()`
and `Cross()`), then add scaled random offsets along them. This produces
uniform spread in a cone rather than a box.

---

## Example 3 — Moving Platform Manager: Physics Event Callbacks

**Source:** `Code/GameSDK/GameDll/MovingPlatforms/MovingPlatformMgr.h/.cpp`

This is a **global physics event listener** that tracks when objects land on
moving platforms and removes them if they've been stuck too long (cleanup for
physics glitches). It demonstrates:

- Registering static callbacks with the physics world
- Using physics foreign data to identify entity types
- A time-based cleanup system (remove objects after N seconds)

### Registration

The manager registers itself as a physics event client in its constructor:

```cpp
CMovingPlatformMgr::CMovingPlatformMgr()
{
    const int kLogged = 1;
    gEnv->pPhysicalWorld->AddEventClient(
        EventPhysCollision::id, StaticOnCollision, kLogged);
    gEnv->pPhysicalWorld->AddEventClient(
        EventPhysEntityDeleted::id, StaticOnDeleted, kLogged);
}

CMovingPlatformMgr::~CMovingPlatformMgr()
{
    const int kLogged = 1;
    gEnv->pPhysicalWorld->RemoveEventClient(
        EventPhysCollision::id, StaticOnCollision, kLogged);
    gEnv->pPhysicalWorld->RemoveEventClient(
        EventPhysEntityDeleted::id, StaticOnDeleted, kLogged);
}
```
> source:Code/GameSDK/GameDll/MovingPlatforms/MovingPlatformMgr.cpp:15-28

### Collision Handling

The collision callback inspects both physics entities' foreign data to find
which is the platform and which is the passenger:

```cpp
int CMovingPlatformMgr::OnCollisionLogged( const EventPhys* pEvent )
{
    const EventPhysCollision* pCollision = static_cast<const EventPhysCollision*>(pEvent);

    // Get Foreign Data for both colliding entities.
    pe_params_foreign_data ppf[2];
    if (!pCollision->pEntity[0]->GetParams(&ppf[0]))
        return 1;
    if (!pCollision->pEntity[1]->GetParams(&ppf[1]))
        return 1;

    // Exactly one must be a Moving Platform, both must be Entity type.
    if (!((ppf[0].iForeignFlags ^ ppf[1].iForeignFlags) & PFF_MOVING_PLATFORM) ||
        ppf[0].iForeignData != PHYS_FOREIGN_ID_ENTITY ||
        ppf[1].iForeignData != PHYS_FOREIGN_ID_ENTITY)
        return 1;

    // Identify which is platform and which is passenger.
    const int PLAT = iszero(ppf[0].iForeignFlags & PFF_MOVING_PLATFORM);
    const int PASS = 1 - PLAT;

    // Platform must be Rigid.
    IPhysicalEntity* pPlatPhys = pCollision->pEntity[PLAT];
    if (pPlatPhys->GetType() != PE_RIGID)
        return 1;

    IEntity* pPlatEntity = (IEntity*)ppf[PLAT].pForeignData;
    IEntity* pPassEntity = (IEntity*)ppf[PASS].pForeignData;
    if (!pPlatEntity || !pPassEntity)
        return 1;

    // Check upward collision normal.
    static float scale[2] = {-1.f, +1.f};
    if ((pCollision->n.z * scale[PLAT]) < 0.3f)
        return 1;

    // New contact: add to tracking list.
    SContact& contact = m_contacts[passengerEntityId];
    contact.fTimeSinceFirstContact = 0.f;
    contact.fTimeSinceLastContact = 0.f;

    return 1;
}
```
> source:Code/GameSDK/GameDll/MovingPlatforms/MovingPlatformMgr.cpp:31-125 (trimmed)

### Time-Based Cleanup

The `Update` method checks all tracked contacts and removes objects that have
been on a platform too long (physics glitch cleanup):

```cpp
void CMovingPlatformMgr::Update( const float dt )
{
    if (!gEnv->bServer || m_contacts.empty())
        return;

    for (TContactList::iterator it = m_contacts.begin();
         it != m_contacts.end(); )
    {
        const EntityId entityId = it->first;
        IEntity* pEntity = gEnv->pEntitySystem->GetEntity(entityId);
        if (!pEntity || !pEntity->GetPhysics())
        {
            m_contacts.erase(it++);
            continue;
        }

        SContact& contact = it->second;
        contact.Update(dt);

        if (contact.fTimeSinceFirstContact > 4.f)
        {
            // Been on here too long — remove the stuck object.
            gEnv->pEntitySystem->RemoveEntity(pEntity->GetId());
            m_contacts.erase(it++);
        }
        else if (contact.fTimeSinceLastContact > 0.5f)
        {
            // Probably fell off or went to sleep.
            m_contacts.erase(it++);
        }
        else
        {
            ++it;
        }
    }
}
```
> source:Code/GameSDK/GameDll/MovingPlatforms/MovingPlatformMgr.cpp:146-189 (trimmed)

Key takeaways:

- **`gEnv->pPhysicalWorld->AddEventClient()`** — registers a static C function
  as a physics event callback. The `kLogged = 1` parameter means it only
  receives events for entities that have collision logging enabled (via
  `EnablePhysicsEvent(true, eEPE_OnCollisionLogged)`).
- **Foreign data flags** — `PFF_MOVING_PLATFORM` is a custom bit flag set on
  the physics entity's foreign data. This is how the system identifies which
  entity is a moving platform without checking entity classes.
- **Collision normal check** — `pCollision->n.z * scale[PLAT] < 0.3f` ensures
  the collision is roughly "from above" (the passenger is on top of the
  platform, not hitting its side).
- **Static callback pattern** — the static `StaticOnCollision` forwards to
  the singleton instance. This is necessary because the physics event client
  is a C function pointer, not a virtual interface.

---

## Example 4 — Custom Flow Graph Node: Screen Fader

**Source:** `Code/GameSDK/GameDll/Nodes/FlowFadeNode.h/.cpp`

This example shows how to create a **custom Flow Graph node** — a node that
fades the screen to/from a color. It demonstrates:

- Deriving from `CFlowBaseNode`
- Declaring input/output ports
- Processing Flow Graph events (`eFE_Initialize`, `eFE_Activate`, `eFE_Update`)
- Registering the node with `REGISTER_FLOW_NODE` and the owning plugin's
  flow-node registration hooks

### Node Class Declaration

```cpp
class CFlowFadeNode : public CFlowBaseNode<eNCT_Instanced>
{
public:
    CFlowFadeNode(SActivationInfo* pActInfo)
        : m_bPlaying(false), m_bNeedFaderStop(false), m_direction(0),
          m_ticket(0), m_postSerializeTrigger(0), m_nFaderOffset(0) {}

    IFlowNodePtr Clone(SActivationInfo* pActInfo)
    {
        return new CFlowFadeNode(pActInfo);
    }

    enum EInputPorts
    {
        EIP_FadeGroup = 0,
        EIP_FadeIn,
        EIP_FadeOut,
        EIP_UseCurrentColor,
        EIP_InTime,
        EIP_OutTime,
        EIP_Color,
        EIP_TextureName,
        EIP_UpdateAlways,
    };

    enum EOutputPorts
    {
        EOP_FadedIn = 0,
        EOP_FadedOut,
        EOP_FadeColor
    };

    virtual void GetConfiguration(SFlowNodeConfig& config);
    virtual void ProcessEvent(EFlowEvent event, SActivationInfo* pActInfo);
    virtual void GetMemoryUsage(ICrySizer* s) const { s->Add(*this); }
    virtual void Serialize(SActivationInfo* pActInfo, TSerialize ser);

protected:
    int  m_ticket;
    int  m_direction;
    int  m_nFaderOffset;
    int  m_postSerializeTrigger;
    bool m_bPlaying;
    bool m_bNeedFaderStop;
};
```
> source:Code/GameSDK/GameDll/Nodes/FlowFadeNode.cpp:294-526 (trimmed)

### Port Configuration

```cpp
void CFlowFadeNode::GetConfiguration(SFlowNodeConfig& config)
{
    static const SInputPortConfig inputs[] = {
        InputPortConfig<int>("FadeGroup",    0,    _HELP("Fade Group [0-3]"), 0, _UICONFIG("enum_int:0=0,1=1,2=2,3=3")),
        InputPortConfig_Void("FadeIn",       _HELP("Fade back from the specified color back to normal screen")),
        InputPortConfig_Void("FadeOut",      _HELP("Fade the screen to the specified color")),
        InputPortConfig<bool>("UseCurColor", true, _HELP("If checked, use the current color as Source color")),
        InputPortConfig<float>("FadeInTime", 2.0f, _HELP("Duration of fade in")),
        InputPortConfig<float>("FadeOutTime",2.0f, _HELP("Duration of fade out")),
        InputPortConfig<Vec3>("color_FadeColor", _HELP("Target Color to fade to")),
        InputPortConfig<string>("tex_TextureName", _HELP("Texture Name")),
        InputPortConfig<bool>("UpdateAlways", false, _HELP("If checked, the Fader will be updated always")),
        { 0 }
    };
    static const SOutputPortConfig outputs[] = {
        OutputPortConfig_Void("FadedIn",   _HELP("FadedIn")),
        OutputPortConfig_Void("FadedOut",  _HELP("FadedOut")),
        OutputPortConfig<Vec3>("CurColor", _HELP("Current Faded Color")),
        { 0 }
    };
    config.pInputPorts = inputs;
    config.pOutputPorts = outputs;
    config.sDescription = _HELP("Controls Screen Fading.");
    config.SetCategory(EFLN_ADVANCED);
}
```
> source:Code/GameSDK/GameDll/Nodes/FlowFadeNode.cpp:396-420

### Event Processing

```cpp
void CFlowFadeNode::ProcessEvent(EFlowEvent event, SActivationInfo* pActInfo)
{
    switch (event)
    {
    case eFE_Initialize:
        // Reset state on graph init / reload.
        if (m_bNeedFaderStop)
        {
            StopFader(pActInfo);
            m_bPlaying = false;
            m_bNeedFaderStop = false;
            m_ticket = 0;
        }
        pActInfo->pGraph->SetRegularlyUpdated(pActInfo->myID, false);
        break;

    case eFE_Activate:
        if (IsPortActive(pActInfo, EIP_FadeIn))
        {
            StopFader(pActInfo);
            pActInfo->pGraph->SetRegularlyUpdated(pActInfo->myID, true);
            m_direction = -1;
            StartFader(pActInfo);
            m_bPlaying = true;
        }
        if (IsPortActive(pActInfo, EIP_FadeOut))
        {
            StopFader(pActInfo);
            pActInfo->pGraph->SetRegularlyUpdated(pActInfo->myID, true);
            m_direction = 1;
            StartFader(pActInfo);
            m_bPlaying = true;
        }
        break;

    case eFE_Update:
        // Check if fade is done, fire output port.
        CHUDFader* pFader = GetFader(pActInfo);
        if (pFader == 0 || m_bPlaying == false)
        {
            pActInfo->pGraph->SetRegularlyUpdated(pActInfo->myID, false);
            m_bPlaying = false;
            return;
        }

        if (pFader->IsPlaying(m_ticket) == false)
        {
            if (m_direction < 0.0f)
                ActivateOutput(pActInfo, EOP_FadedIn, true);
            else
                ActivateOutput(pActInfo, EOP_FadedOut, true);
            pActInfo->pGraph->SetRegularlyUpdated(pActInfo->myID, false);
            m_bPlaying = false;
        }
        break;
    }
}
```
> source:Code/GameSDK/GameDll/Nodes/FlowFadeNode.cpp:422-518 (trimmed)

### Registration

```cpp
REGISTER_FLOW_NODE("Image:ScreenFader", CFlowFadeNode);
```
> source:Code/GameSDK/GameDll/Nodes/FlowFadeNode.cpp:528

Key takeaways:

- **`CFlowBaseNode<eNCT_Instanced>`** — the base class for Flow Graph nodes.
  `eNCT_Instanced` means each node instance gets its own C++ object (vs
  `eNCT_Singleton` which shares one).
- **Port configuration** — `InputPortConfig<T>` and `OutputPortConfig<T>`
  declare the node's ports. The `tex_` prefix on a string port makes it a
  texture picker, `color_` makes a Vec3 a color picker, `enum_int:` adds a
  dropdown. These are editor UI hints.
- **Three event types** — `eFE_Initialize` (graph init/reload), `eFE_Activate`
  (an input port was triggered), `eFE_Update` (per-frame, only if
  `SetRegularlyUpdated(true)` was called).
- **`SetRegularlyUpdated`** — opts into per-frame `eFE_Update` events. Always
  disable it when done to avoid unnecessary per-frame work.
- **`ActivateOutput`** — fires an output port, which triggers connected nodes.
- **`REGISTER_FLOW_NODE("Category:Name", ClassName)`** — registers the node so
  it can be picked up by the engine's auto-registration list.
- **Plugin flow-node hooks** — a plugin that owns flow nodes should implement
  `RegisterFlowNodes()` / `UnregisterFlowNodes()`. The engine provides
  `PLUGIN_FLOWNODE_REGISTER` and `PLUGIN_FLOWNODE_UNREGISTER` helper macros for
  the usual auto-registration path. source:Code/CryEngine/CryCommon/CrySystem/ICryPlugin.h:73-77 source:Code/CryEngine/CryCommon/CrySystem/ICryPlugin.h:113-138
- **Tickets** — the `m_ticket` system prevents stale callbacks from old fade
  operations from firing outputs for a new fade. This is a robust pattern for
  any async/deferred operation in Flow Graph nodes.

Required:

- Define the node class and `REGISTER_FLOW_NODE(...)`.
- Make the owning plugin expose flow-node registration/unregistration, usually
  via `PLUGIN_FLOWNODE_REGISTER` and `PLUGIN_FLOWNODE_UNREGISTER`.
- Test the node in the Flow Graph editor and trigger at least one input; compile
  success alone does not prove editor registration.

Avoid:

- Do not assume `REGISTER_FLOW_NODE(...)` by itself is enough for every plugin
  layout.

---

## Example 5 — IGameFrameworkListener: Global Update via Framework

**Source:** `Code/GameSDK/GameDll/Nodes/FlowFadeNode.cpp` (CMasterFader class)

`CMasterFader` shows how to get per-frame updates **without** an entity — by
registering as an `IGameFrameworkListener`. This is the legacy equivalent of
`Cry::IEnginePlugin::MainUpdate()`.

```cpp
class CMasterFader : public IGameFrameworkListener
{
public:
    CMasterFader();
    ~CMasterFader();

    // IGameFrameworkListener
    virtual void OnPostUpdate(float fDeltaTime) override;
    virtual void OnSaveGame(ISaveGame* pSaveGame) override {}
    virtual void OnLoadGame(ILoadGame* pLoadGame) override {}
    virtual void OnLevelEnd(const char* nextLevel) override {}
    virtual void OnActionEvent(const SActionEvent& event) override;
    // ~IGameFrameworkListener

    CHUDFader* GetHUDFader(int group);
    void Update(float fDeltaTime);
    void Register();
    void UnRegister();

    bool m_bRegistered;
    CHUDFader* m_pHUDFader[NUM_FADERS];
};
```
> source:Code/GameSDK/GameDll/Nodes/FlowFadeNode.h:65-93

Registration:

```cpp
void CMasterFader::Register()
{
    if (m_bRegistered)
        return;
    g_pGame->GetIGameFramework()->RegisterListener(
        this, "HUD_Master_Fader", FRAMEWORKLISTENERPRIORITY_HUD);
    m_bRegistered = true;
}
```
> source:Code/GameSDK/GameDll/Nodes/FlowFadeNode.cpp:260-269

The listener receives `OnPostUpdate(dt)` every frame, which it forwards to its
internal `Update`:

```cpp
void CMasterFader::OnPostUpdate(float fDeltaTime)
{
    Update(fDeltaTime);
}
```
> source:Code/GameSDK/GameDll/Nodes/FlowFadeNode.cpp:194-197

Key takeaways:

- **`IGameFrameworkListener`** is the legacy way to get global per-frame
  updates. In modern code, use `Cry::IEnginePlugin::MainUpdate()` instead
  (see [Plugin Update Loop](Plugin%20Update%20Loop.md)).
- **Priority** — `FRAMEWORKLISTENERPRIORITY_HUD` controls the order in which
  listeners are called. Other options include `DEFAULT`, `GAME`, `MENU`.
  source:Code/GameSDK/GameDll/Nodes/FlowFadeNode.cpp:267
- **`OnActionEvent`** — receives game lifecycle events
  (`eAE_unloadLevel`, `eAE_inGame`, etc.). Used here to clean up when the
  level unloads.

---

## Pattern Summary

| Pattern | Example | Modern equivalent |
|---------|---------|-------------------|
| Manager + agents (flock) | `CFlock` + `CBoidObject` | `IEntityComponent` on a manager entity + component per agent |
| Physics collision events | `eGFE_OnCollision` via `IGameObject` | For entity-local collisions use entity physics events in a component; for global monitoring use `IPhysicalWorld::AddEventClient(EventPhysCollision::id, ...)` |
| Global physics event client | `pPhysicalWorld->AddEventClient()` | Same API still works; can also use `IEntityComponent` on relevant entities |
| Custom Flow Graph node | `CFlowBaseNode` + `REGISTER_FLOW_NODE` | Same API, plus plugin `RegisterFlowNodes()` / `UnregisterFlowNodes()` hooks; also consider Schematyc functions |
| Global per-frame update | `IGameFrameworkListener::OnPostUpdate` | `Cry::IEnginePlugin::MainUpdate` via `EnableUpdate` |
| Local-space buffering | Transform hit data to local, restore later | Same pattern works in `IEntityComponent` |
| Spread via orthogonal basis | `GetOrthogonal()` + `Cross()` | Pure math, works anywhere |
| Ticket system | `m_ticket` to invalidate stale callbacks | Same pattern for any async operation |

## Porting Notes

Required:

- Decide whether the GameSDK example is demonstrating a gameplay algorithm, a
  legacy framework hook, or an engine API that still exists. Port those cases
  differently.
- Pair global physics event registration with removal. A global
  `AddEventClient` listener outlives individual entities unless you remove it.
- For global per-frame systems, prefer plugin `MainUpdate` in modern plugin
  projects; for entity-local behavior, prefer component update events.

Avoid:

- Do not assume GameSDK entity classes, legacy entity cards, or GameSDK-specific
  framework objects exist in a Blank-derived project.
- Do not use global physics callbacks when an entity-local event is sufficient.

---

## Next

- [Examples](Examples.md) — simpler component examples from GameTemplates
- [Plugin Update Loop](Plugin%20Update%20Loop.md) — modern global update
- [Entities and Components](Entities%20and%20Components.md) — modern entity system
- [Gameplay Framework Programming](../Gameplay/Gameplay%20Framework%20Programming.md) — IGameFramework, IGameObject (legacy extensions)
