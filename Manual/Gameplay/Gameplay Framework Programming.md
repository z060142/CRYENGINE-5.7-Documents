# Gameplay Framework Programming

The CRYENGINE Gameplay Framework is the central hub connecting all game-level
subsystems. It is exposed through `IGameFramework`, obtained via
`gEnv->pGameFramework`. Every game programmer working with CRYENGINE at the
C++ level interacts with this framework.

> **API reference:** For full interface signatures, see the headers under
> `Code/CryEngine/CryCommon/CryGame/` and `Code/CryEngine/CryAction/`. This
> page focuses on concepts, workflows, and when-to-use guidance.

---

## Architecture Overview

```
IGameStartup (entry point, deprecated → Cry::IEnginePlugin)
    └── IGame (game module, deprecated → Cry::IEnginePlugin)
            └── IGameFramework (central hub, always available)
                    ├── IGameObjectSystem    — game object / extension management
                    ├── ILevelSystem         — level loading & rotation
                    ├── IActorSystem         — player / AI actor management
                    ├── IItemSystem          — weapons, items, inventory
                    ├── IVehicleSystem       — vehicle management
                    ├── IViewSystem          — camera / view management
                    ├── IGameRulesSystem     — game mode / rules
                    ├── IFlowSystem          — Flow Graph visual scripting
                    ├── IGameTokenSystem     — named plot tokens
                    ├── IEffectSystem        — visual effects
                    ├── IMaterialEffects     — material-based effects
                    ├── IGameStatistics      — telemetry / stats
                    ├── IForceFeedbackSystem — gamepad rumble
                    ├── IGameSessionHandler  — multiplayer sessions
                    ├── ISharedParamsManager — shared parameter management
                    ├── ICheckpointSystem    — checkpoint save/restore
                    ├── IGameVolumes         — 3D volume queries
                    ├── IMannequin           — animation / character system
                    ├── IActionMapManager    — input action mapping
                    ├── IPlayerProfileManager— player profiles
                    ├── IGameplayRecorder    — gameplay recording / replay
                    └── IPersistantDebug     — persistent debug drawing
```

The framework owns the game update loop and dispatches events to registered
listeners. It is the bridge between the engine core (`ISystem`) and
game-specific code (`IGame` / `Cry::IEnginePlugin`).

---

## IGameFramework — The Central Hub

**Header:** `Code/CryEngine/CryCommon/CryGame/IGameFramework.h`

Obtain the framework via `gEnv->pGameFramework`. It is always valid once
CryAction has initialized.

### Lifecycle Hooks

The framework hooks into the engine's main loop at specific points. Game
code registers a listener (`IGameFrameworkListener`) to receive these
callbacks in priority order:

| Priority | Typical Use |
|----------|-------------|
| `DEFAULT` | Game logic (first) |
| `GAME` | Game layer |
| `HUD` | HUD rendering |
| `MENU` | Menu overlay (last) |

Key listener callbacks: `OnPostUpdate(dt)` for per-frame logic,
`OnSaveGame`/`OnLoadGame` for serialization, `OnActionEvent` for lifecycle
events (connected, disconnected, level loaded, etc.).

### Subsystem Accessors

Every game subsystem is reached through `Get*` methods on `IGameFramework`.
The common pattern:

```cpp
IGameFramework* pGF = gEnv->pGameFramework;
IActorSystem*    pAS  = pGF->GetIActorSystem();
ILevelSystem*    pLS  = pGF->GetILevelSystem();
IGameRulesSystem*pGRS = pGF->GetIGameRulesSystem();
IViewSystem*     pVS  = pGF->GetIViewSystem();
IItemSystem*     pIS  = pGF->GetIItemSystem();
IVehicleSystem*  pVHS = pGF->GetIVehicleSystem();
```

The framework also provides access to `IFlowSystem`, `IMannequin`,
`IActionMapManager`, `IGameTokenSystem`, `IGameStatistics`,
`IForceFeedbackSystem`, `IPlayerProfileManager`, `ICheckpointSystem`,
`IPersistantDebug`, and more — see the header for the full list.

### Game Context Management

A "game context" is a running game session — a loaded level with active game
rules and optionally network connections. The lifecycle is:

```
StartGameContext(SGameStartParams)
  → loads level, activates game rules, sets up networking
  → StartedGameContext() returns true

ChangeGameContext(SGameContextParams)  [server only]
  → switch level or rules mid-session

EndGameContext()
  → tears down current session
```

`SGameStartParams` controls the session: flags (`eGSF_Server`,
`eGSF_Client`, `eGSF_LocalOnly`, `eGSF_NoGameRules`, etc.), max players,
port, session handle. `SGameContextParams` specifies `levelName` and
`gameRules`.

### Client & Network Utilities

The framework provides quick access to the local player and synchronized
server time:

```cpp
IActor* pLocalPlayer = pGF->GetClientActor();
EntityId localId      = pGF->GetClientActorId();
INetChannel* pChannel = pGF->GetClientChannel();
CTimeValue serverTime = pGF->GetServerTime();
IGameObject* pGO = pGF->GetGameObject(entityId);
```

For network-safe class ID mapping (used in multiplayer serialization), use
`GetNetworkSafeClassId` / `GetNetworkSafeClassName`.

### Save & Load

```cpp
pGF->SaveGame("save.xml", false /*quick*/, true /*immediate*/);
pGF->LoadGame("save.xml", false /*quick*/);
pGF->AllowSave(true);  pGF->AllowLoad(true);
```

Save reasons (`eSGR_LevelStart`, `eSGR_QuickSave`, `eSGR_FlowGraph`,
`eSGR_Command`) and load results (`eLGR_Ok`, `eLGR_Failed`,
`eLGR_CantQuick_NeedFullLoad`) are defined in the header.

### Editor Integration

When running under Sandbox Editor, the framework notifies game code of
mode changes: `OnEditorSetGameMode` (0=leave, 1=enter, 3/4=AI/Physics),
`IsEditing()`, `SetEditorLevel` / `GetEditorLevel`.

---

## Game Module Entry Points

### Legacy: IGameStartup / IGame (deprecated since v5.3)

The old entry point was a DLL-exported function returning `IGameStartup*`,
which created an `IGame` instance. These interfaces are still present for
backward compatibility but should not be used in new projects.

### Modern: Cry::IEnginePlugin (since v5.3)

The modern replacement is `Cry::IEnginePlugin`, documented in
[Plugin System](../Beta%20Features/Plugin%20System.md). A typical game plugin
skeleton:

```cpp
class CGamePlugin : public Cry::IEnginePlugin {
public:
    void Initialize() override;
    void OnGameStart() override;
    void OnGameStop() override;
    void Shutdown() override;
};
CRYREGISTER_SINGLETON_CLASS(CGamePlugin)
```

---

## IGameObject & IGameObjectExtension

Game objects wrap entities with gameplay-specific functionality through
extensions. An entity can have multiple extensions (Actor, Item, Vehicle,
etc.), each providing a specific gameplay role.

> **Note:** `IGameObject` inherits from `IEntityComponent`. For new projects,
> consider using the modern [Entity Component System](../Entities%20and%20Tools/Entity%20Component%20Programming.md)
> directly. The game object extension system is the legacy predecessor.

### Extension Lifecycle

```
Entity Spawn
  → Init(pGameObject) → PostInit(pGameObject)
  → [Server] SerializeSpawnInfo → sent to clients
  → [Client] InitClient → PostInitClient → PostRemoteSpawn

Per Frame
  → Update(ctx, slot)  [if update slot enabled]
  → PostUpdate(frameTime)

Entity Removal
  → Extension destroyed with game object
```

### Key Operations

- **Query/activate extensions** by name or ID: `QueryExtension`,
  `ActivateExtension`, `AcquireExtension`, `ReleaseExtension`
- **Update slots**: `EnableUpdateSlot` / `DisableUpdateSlot` with conditions
  (`eUEC_Always`, `eUEC_Visible`, `eUEC_InRange`, `eUEC_VisibleAndInRange`,
  etc.)
- **Network**: `ChangedNetworkState(aspects)`, `RequestRemoteUpdate`,
  `InvokeRMI` (Remote Method Invocation for multiplayer RPCs)
- **Physics events**: `EnablePhysicsEvent`, `WantsPhysicsEvent`
- **AI**: `SetAIActivation` with activation modes
- **Movement**: `SetMovementController` / `GetMovementController`

For the complete interface, see `Code/CryEngine/CryAction/IGameObject.h`.

### IGameObjectSystem

Manages extension registration and game object creation:

- `RegisterExtension(name, creator, entityClass)` — register a new extension
  type
- `CreateGameObjectForEntity(entityId)` — attach a game object to an entity
- `BroadcastEvent(SGameObjectEvent)` — send events to all game objects

See `Code/CryEngine/CryAction/IGameObjectSystem.h` for details.

---

## IGameRules & IGameRulesSystem

Game rules define the game mode — win conditions, scoring, spawning, team
management, and hit/damage processing. They are the server-authoritative
game logic layer.

### IGameRules

Key callback groups (all defined in
`Code/CryEngine/CryAction/IGameRulesSystem.h`):

- **Client connection**: `OnClientConnect`, `OnClientDisconnect`,
  `OnClientEnteredGame`, `ShouldKeepClient`
- **Hit & damage**: `ClientHit`, `ServerHit`, `GetHitTypeId` — the `HitInfo`
  struct carries shooter, target, weapon, damage, position, direction,
  material, partId
- **Entity lifecycle**: `OnEntitySpawn`, `OnEntityRemoved`, `OnEntityReused`
- **Respawn**: `CreateEntityRespawnData`, `ScheduleEntityRespawn`,
  `AbortEntityRespawn`
- **Messaging**: `SendTextMessage`, `SendChatMessage`
- **Time limit**: `IsTimeLimited`, `GetRemainingGameTime`, `SetRemainingGameTime`
- **Teams**: `GetTeamName`
- **Host migration**: `SetChannelForMigratingPlayer`, `StoreMigratingPlayer`
- **Hit listeners**: `AddHitListener` / `RemoveHitListener`
- **Collision**: `OnCollision`

### IGameRulesSystem

- `RegisterGameRules(rulesName, extensionName)` — register a rules type
- `CreateGameRules(rulesName)` / `DestroyGameRules()` — create/destroy
  active rules instance
- `GetCurrentGameRules()` — get the active rules
- `AddGameRulesAlias`, `AddGameRulesLevelLocation` — aliasing and level
  association

For sample GameRules implementations, see
[Game Rules Script Callbacks](../../API%20Reference/CRYENGINE%20Game%20Code/Game%20Rules%20Script%20Callbacks.md)
and the GameSDK samples.

---

## IActor & IActorSystem

Actors represent player and AI characters. They manage health, inventory,
animation, movement, and vehicle interaction.

### IActor

Key functionality groups (header: `Code/CryEngine/CryAction/IActorSystem.h`):

- **Health**: `SetHealth` / `GetHealth` / `SetMaxHealth` / `IsDead` / `Fall`
- **Identity**: `IsPlayer`, `IsClient`, `GetTeamId`, `InitLocalPlayer`
- **Inventory & items**: `GetInventory`, `GetCurrentItem`, `HolsterItem`,
  `DropItem`
- **Animation**: `PlayAction`, `GetAnimationGraphState`,
  `GetAnimatedCharacter`
- **Movement & view**: `GetMovementController`, `SetViewRotation`,
  `IsThirdPerson`, `ToggleThirdPerson`
- **Vehicle**: `LinkToVehicle`, `GetLinkedVehicle`
- **Network**: `GetChannelId` / `SetChannelId`, `IsMigrating`

### IActorSystem

- `GetActor(entityId)` / `GetActorByChannelId(channelId)` — lookup
- `CreateActor(channelId, name, class, pos, rot, scale)` — spawn
- `GetActorCount()`, `CreateActorIterator()` — iteration
- `AddActor` / `RemoveActor` — registration

---

## ILevelSystem

The level system manages level discovery, loading, unloading, and level
rotation (playlist) for multiplayer.

### Core Operations

- **Discovery**: `Rescan(folder, tag)`, `GetLevelCount()`,
  `GetLevelInfo(name)`
- **Loading**: `LoadLevel(name)` (blocking) or `StartLoadLevel(name)` +
  `UpdateLoadLevelStatus()` (time-sliced, returns `InProgress`/`Done`/
  `Failed`)
- **Current level**: `GetCurrentLevel()` returns `ILevelInfo` (name, path,
  display name, heightmap size, supported game types, default game rules)
- **Unloading**: `UnLoadLevel()`, `PrepareNextLevel(name)`
- **Rotation**: `LoadRotation()`, `GetLevelRotation()` — multiplayer
  playlist with `AddLevel`, `Advance`, `GetNextLevel`, `IsRandom`

### ILevelSystemListener

Register to receive loading events: `OnLevelNotFound`, `OnLoadingStart`,
`OnLoadingProgress`, `OnLoadingComplete`, `OnLoadingError`,
`OnUnloadComplete`. Useful for implementing loading screens.

---

## IViewSystem

The view system manages cameras — creating views, linking them to entities,
and controlling view parameters like position, rotation, FOV, and shake.

- `CreateView()` / `RemoveView()` / `SetActiveView()` / `GetActiveView()`
- `GetViewByEntityId(id)` — find a view linked to an entity
- `SetBlendParams(posSpeed, rotSpeed, blendOut)` — control view transitions
- `UpdateAudioListeners()` — sync audio listener positions to active views

### IView

A view is linked to an entity (typically a camera entity or the player) and
carries `SViewParams`: position, rotation, FOV, nearplane, blend speeds.
View shake is supported via `SetViewShake(angle, shift, duration, frequency,
randomness, shakeID)`.

---

## IItemSystem & IInventory

`IItemSystem` manages weapons, pickups, and equipment:

- `GetItem(id)`, `CreateItem(name, pos, rot)`
- `RegisterItemCategory(category)`
- `GetIEquipmentManager()` — equipment loadout management

`IInventory` (obtained from `IActor::GetInventory()`) tracks held items with
capacity/count, `AddItem` / `RemoveItem`, and slot categories
(`eInventorySlot_Weapon`, `eInventorySlot_Explosives`, `eInventorySlot_Grenades`,
`eInventorySlot_Special`).

For weapon system details, see
[Weapon System](../../API%20Reference/CRYENGINE%20Game%20Code/Weapon%20System.md).

---

## IVehicleSystem

Manages vehicles and their components:

- `GetVehicle(entityId)` — lookup
- `RegisterVehicleClass(name, creator)` — register a vehicle type
- `AddVehicle` / `RemoveVehicle` — registration

`IVehicle` provides: `Reset`, `GetDriverId`, `GetPassengerCount`,
`Enter(actorId, seatId)`, `Exit(actorId)`, `OnAction(action, mode, value)`,
plus methods for movement, damage, components, and events.

For vehicle scripting and XML setup, see
[Vehicle Scripting](../../API%20Reference/CRYENGINE%20Game%20Code/Miscellaneous%20Game%20Code/Vehicle%20Scripting.md).

---

## Game Statistics (IGameStatistics)

**Header:** `Code/CryEngine/CryCommon/CryGame/IGameStatistics.h`

The statistics system provides a hierarchical event/state tracking framework
for telemetry, analytics, and gameplay recording.

### Core Concepts

- **Events** — timestamped occurrences (kill, shot, death, score, etc.).
  Registered via `RegisterGameEvent(scriptName, serializeName)`.
- **States** — persistent values (health, team, weapon, player name).
  Registered via `RegisterGameState`.
- **Scopes** — hierarchical grouping (round → team → player). Managed with
  `PushGameScope` / `PopGameScope`.
- **Elements** — individual tracked entities within a scope. Added via
  `AddGameElement(locator)`.

`IStatsTracker` records state values and events: `StateValue(stateID, value)`,
`Event(eventID, value)`.

Common event types include `eSE_Kill`, `eSE_Score`, `eSE_Shot`, `eSE_Hit`,
`eSE_Death`, `eSE_Reload`. Common states include `eSS_Map`, `eSS_Gamemode`,
`eSS_Team`, `eSS_Score`, `eSS_PlayerName`.

---

## Game Tokens (IGameTokenSystem)

**Header:** `Code/CryEngine/CryCommon/CryGame/IGameTokens.h`

Game tokens are named plot-state variables used for tracking narrative
progress, quest states, and gameplay flags. They persist across level
transitions.

Key operations:
- `SetOrCreateToken(name, defaultValue)` / `FindToken(name)` /
  `DeleteToken` / `RenameToken`
- `RegisterListener(tokenName, listener)` — get notified when a token
  changes
- `SerializeSaveLevelToLevel(tokens, count)` /
  `SerializeReadLevelToLevel()` — persist tokens across level changes
- `LoadLibs(fileSpec)` / `RemoveLibrary(prefix)` — token library management

---

## Persistent Debug Drawing (IPersistantDebug)

Obtained via `gEnv->pGameFramework->GetIPersistantDebug()`. Provides debug
geometry that persists across frames without needing per-frame re-rendering:

```cpp
auto* pDbg = pGF->GetIPersistantDebug();
pDbg->Begin("MyDebug", true);  // start a named debug group, clear previous
pDbg->AddSphere(pos, 1.0f, ColorF(1,0,0,1), 5.0f /*timeout seconds*/);
pDbg->AddLine(pos1, pos2, ColorF(0,1,0,1), 5.0f);
pDbg->AddText3D(pos, 2.0f, ColorF(1,1,1,1), 5.0f, "Label: %d", value);
pDbg->AddAABB(min, max, ColorF(0,0,1,1), 5.0f);
```

Supports spheres, lines, directions, planar discs, cones, cylinders, 2D
text, 3D text, AABBs, and entity tags.

---

## Quick Reference

```cpp
// The global environment pointer gives access to everything
IGameFramework* pGF = gEnv->pGameFramework;

// Common access patterns
IActor* pLocalPlayer   = pGF->GetClientActor();
IItem*  pCurrentWeapon = pLocalPlayer->GetCurrentItem();
IView*  pActiveView    = pGF->GetIViewSystem()->GetActiveView();
IGameRules* pRules     = pGF->GetIGameRulesSystem()->GetCurrentGameRules();
ILevelInfo* pLevel     = pGF->GetILevelSystem()->GetCurrentLevel();

// Starting a local game
SGameStartParams params;
params.flags = eGSF_LocalOnly | eGSF_NoGameRules;
params.pContextParams = &ctxParams;  // levelName, gameRules
pGF->StartGameContext(&params);

// Registering for framework events
class MyListener : public IGameFrameworkListener {
    void OnPostUpdate(float dt) override { /* per-frame logic */ }
    void OnActionEvent(const SActionEvent& ev) override {
        if (ev.m_event == eAE_inGame) { /* game started */ }
    }
};
pGF->RegisterListener(&myListener, "MySystem", FRAMEWORKLISTENERPRIORITY_GAME);
```

---

## Related Documentation

- [Entity Component System](../Entities%20and%20Tools/Entity%20Components.md) — modern component-based entity architecture
- [Entity Component Programming](../Entities%20and%20Tools/Entity%20Component%20Programming.md) — how to write custom components
- [Plugin System](../Beta%20Features/Plugin%20System.md) — `Cry::IEnginePlugin` (modern replacement for `IGameStartup`)
- [Engine Architecture Overview](../CRYENGINE%20-%20Getting%20Started/Engine%20Architecture%20Overview.md) — module structure, main loop
- [Flow Graph Programming](../../API%20Reference/CRYENGINE%20Game%20Code/Flowgraph%20Programming.md) — visual scripting
- [Weapon System](../../API%20Reference/CRYENGINE%20Game%20Code/Weapon%20System.md) — weapon/item C++ API
- [Game Objects](../../API%20Reference/CRYENGINE%20Game%20Code/Game%20Objects.md) — IGameObject API reference
- [Game Rules Script Callbacks](../../API%20Reference/CRYENGINE%20Game%20Code/Game%20Rules%20Script%20Callbacks.md) — GameRules callbacks
- [Vehicle Scripting](../../API%20Reference/CRYENGINE%20Game%20Code/Miscellaneous%20Game%20Code/Vehicle%20Scripting.md) — vehicle XML and scripting
- [Entity System API](../../API%20Reference/Entity.md) — IEntity, IEntityComponent, IEntitySystem
- [Networking](../../API%20Reference/Entity/Networking.md) — INetEntity, aspects, RMI