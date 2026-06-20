# CryAction

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/23309036
- Page ID: 23309036
- Breadcrumb: CRYENGINE Engine Code > Engine Modules > CryAction
- Parent: Engine Modules

## Overview

CryAction is the game framework module that sits between your game project and the core engine. It is implemented by the `CCryAction` class (`source:Code/CryEngine/CryAction/CryAction.h:89`), which implements the `IGameFramework` interface (`source:Code/CryEngine/CryCommon/CryGame/IGameFramework.h:597`). The name "CryAction" originates from its role as the framework for the Crysis action game series.

CryAction is exposed as a single DLL (`CryAction.dll`) and is accessible globally through `gEnv->pGameFramework` (`source:Code/CryEngine/CryAction/CryAction.cpp:1745`).

## Architecture

`CCryAction` is a singleton (accessible via `CCryAction::GetCryAction()`, `source:Code/CryEngine/CryAction/CryAction.h:282`) that owns pointers to all game subsystems. It implements the full `IGameFramework` interface and manages the game lifecycle.

### Key Interfaces

| Interface | Description | Source |
|-----------|-------------|--------|
| `IGameFramework` | Central game framework interface (597-1053) | `CryCommon/CryGame/IGameFramework.h:597` |
| `IGameFrameworkEngineModule` | Engine module registration GUID | `CryCommon/CryGame/IGameFramework.h:583` |
| `IGameFrameworkListener` | Callback interface for framework events | `CryCommon/CryGame/IGameFramework.h:557` |
| `IGameLevelLoadListener` | Callback for level loading steps | `CryCommon/CryGame/IGameFramework.h:588` |
| `IBreakEventListener` | Callback for breakage events | `CryCommon/CryGame/IGameFramework.h:572` |
| `IPersistantDebug` | Time-based debug geometry drawing | `CryCommon/CryGame/IGameFramework.h:355` |
| `IGameStatsConfig` | Game statistics configuration | `CryCommon/CryGame/IGameFramework.h:334` |
| `IBreakReplicator` | Break event replication | `CryCommon/CryGame/IGameFramework.h:345` |
| `INetworkedClientListener` | Network client connection events | `CryAction/CryAction.h:268` |

### Enums

| Enum | Values | Source |
|------|--------|--------|
| `EGameStartFlags` | `eGSF_NoLevelLoading`, `eGSF_Server`, `eGSF_Client`, `eGSF_NoDelayedStart`, `eGSF_BlockingClientConnect`, `eGSF_NoGameRules`, `eGSF_LocalOnly`, `eGSF_NoQueries`, `eGSF_NoSpawnPlayer`, `eGSF_BlockingMapLoad`, `eGSF_DemoRecorder`, `eGSF_DemoPlayback`, `eGSF_ImmersiveMultiplayer`, `eGSF_RequireController`, `eGSF_RequireKeyboardMouse`, `eGSF_HostMigrated`, `eGSF_NonBlockingConnect` | `IGameFramework.h:148` |
| `ESaveGameReason` | `eSGR_LevelStart`, `eSGR_FlowGraph`, `eSGR_Command`, `eSGR_QuickSave` | `IGameFramework.h:172` |
| `ELoadGameResult` | `eLGR_Ok`, `eLGR_Failed`, `eLGR_FailedAndDestroyedState`, `eLGR_CantQuick_NeedFullLoad` | `IGameFramework.h:180` |
| `EGameFrameworkEvent` | `eGFE_PauseGame` through `eGFE_Last` (22 events) | `IGameFramework.h:477` |
| `EActionEvent` | `eAE_channelCreated` through `eAE_loadLevel` (28 events) | `IGameFramework.h:503` |
| `EFRAMEWORKLISTENERPRIORITY` | `FRAMEWORKLISTENERPRIORITY_DEFAULT`, `_GAME`, `_HUD`, `_MENU` | `IGameFramework.h:546` |
| `EEntityEventPriority` | `EEntityEventPriority_GameObject` through `_StartAnimProc` | `IGameFramework.h:466` |

### Structs

| Struct | Purpose | Source |
|--------|---------|--------|
| `SGameStartParams` | Parameters to start a game context | `IGameFramework.h:206` |
| `SGameContextParams` | Parameters to change game context (level, rules) | `IGameFramework.h:190` |
| `SEntitySchedulingProfiles` | Network scheduling profiles for entities | `IGameFramework.h:137` |
| `SEntityTagParams` | Parameters for persistent debug entity tags | `IGameFramework.h:241` |
| `SActionEvent` | Event data for framework action events | `IGameFramework.h:531` |
| `SRenderNodeCloneLookup` | Maps original to cloned render nodes for break playback | `IGameFramework.h:299` |

## Initialization Sequence

CryAction initialization occurs in `CCryAction::Initialize()` (`source:Code/CryEngine/CryAction/CryAction.cpp:1741`). The sequence is:

1. **Set global pointer**: `gEnv->pGameFramework = this` (line 1745)
2. **Create listener array**: `m_pGFListeners` with capacity 20 (lines 1748-1753)
3. **Register flow nodes**: `CryRegisterFlowNodes()` (line 1758)
4. **Register system event listener**: `CSystemEventListener_Action` (line 1764)
5. **Initialize Flash UI**: `GetIFlashUIPtr()` (lines 1768-1774)
6. **Cache engine pointers**: `m_pNetwork`, `m_p3DEngine`, `m_pScriptSystem`, `m_pEntitySystem`, `m_pTimer`, `m_pLog` (lines 1781-1786)
7. **Init CVars**: `InitCVars()` (line 1819)
8. **Init Game Volumes Manager**: `InitGameVolumesManager()` (line 1821)
9. **Create DevMode** (if dev mode): `new CDevMode()` (line 1825)
10. **Create TimeDemoRecorder**: `m_pDefaultTimeDemoRecorder` (line 1827)
11. **Register RMI CVars**: `CScriptRMI::RegisterCVars()` (line 1830)
12. **Create GameObject CVars**: `CGameObject::CreateCVars()` (line 1831)
13. **Create ScriptRMI**: `new CScriptRMI()` (line 1832)

### Subsystem Creation (lines 1835-1921)

| Subsystem | Class | Created At |
|-----------|-------|------------|
| Effect System | `CEffectSystem` | Line 1835 |
| UI Draw | `CUIDraw` | Line 1837 |
| Level System | `CLevelSystem` | Line 1838 |
| Network CVars | `CNetworkCVars` | Line 1842 |
| CryAction CVars | `CCryActionCVars` | Line 1843 |
| Actor System | `CActorSystem` | Line 1845 |
| Item System | `CItemSystem` (conditional on `g_legacyItemSystem`) | Line 1848 |
| Action Map Manager | `CActionMapManager` | Line 1850 |
| Cooperative Animation Manager | `CCooperativeAnimationManager` | Line 1854 |
| View System | `CViewSystem` | Line 1856 |
| Gameplay Recorder | `CGameplayRecorder` | Line 1857 |
| Game Rules System | `CGameRulesSystem` | Line 1858 |
| Vehicle System | `CVehicleSystem` | Line 1859 |
| Shared Params Manager | `CSharedParamsManager` | Line 1861 |
| Gameplay Analyst | `CGameplayAnalyst` (conditional) | Line 1864 |
| Game Object System | `CGameObjectSystem` | Line 1867 |
| Animation Graph CVars | `CAnimationGraphCVars` | Line 1892 |
| Mannequin Interface | `CMannequinInterface` | Line 1893 |
| Callback Timer | `CallbackTimer` (editor only) | Line 1895 |
| Persistent Debug | `CPersistantDebug` | Line 1896 |
| Player Profile Manager | `CPlayerProfileManager` (conditional) | Line 1914 |
| Time of Day Scheduler | `CTimeOfDayScheduler` | Line 1918 |
| Custom Action Manager | `CCustomActionManager` | Line 1920 |
| Custom Event Manager | `CCustomEventManager` | Line 1921 |

14. **Register game object events**: 19 events registered via `m_pGameObjectSystem->RegisterEvent()` (lines 1873-1889)
15. **Set MovieSystem user**: `movieSys->SetUser(m_pViewSystem)` (line 1925)
16. **Init Vehicle System**: `m_pVehicleSystem->Init()` (line 1929)
17. **Register Inventory factory**: `REGISTER_FACTORY("Inventory", CInventory)` (line 1934)
18. **Register ItemSystem as LevelSystem listener** (line 1939)
19. **Init Script Binds**: `InitScriptBinds()` (line 1942)
20. **Init Player Profile Manager**: `m_pPlayerProfileManager->Initialize()` (line 1955)
21. **Create Game Stats Config**: `CGameStatsConfig` (line 1966)
22. **Create Game Statistics**: `CGameStatistics` (line 1971)
23. **Init AI debug renderers** (if AI system present) (lines 1973-1982)
24. **Create Physics Queues** (editor only) (line 1985)
25. **Create NetMsg Dispatcher, Entity Container Manager, Entity Attachment Registry** (lines 1994-1996)
26. **Init Game DLL**: `InitGame(startupParams)` loads the game DLL and calls `IGameStartup::Init()` (line 1998)
27. **Register Vehicles**: `m_pVehicleSystem->RegisterVehicles(this)` (line 2001)
28. **Register GameObject factories**: `m_pGameObjectSystem->RegisterFactories(this)` (line 2003)
29. **Register Extensions**: `CGameContext::RegisterExtensions(this)` (line 2004)
30. **Execute command line** (if requested) (line 2007)
31. **Complete Init**: `CompleteInit()` (line 2010)
32. **Fire event**: `ESYSTEM_EVENT_GAME_FRAMEWORK_INIT_DONE` (line 2014)
33. **Execute autoexec.cfg** (line 2016)

### Script Binds Created

All created in `InitScriptBinds()` (`source:Code/CryEngine/CryAction/CryAction.cpp:2265`):

| Script Bind | Class | Purpose |
|-------------|-------|---------|
| `ScriptBind_Network` | `CScriptBind_Network` | Network Lua bindings |
| `ScriptBind_Action` | `CScriptBind_Action` | General CryAction Lua bindings |
| `ScriptBind_ItemSystem` | `CScriptBind_ItemSystem` | Item system Lua bindings (conditional) |
| `ScriptBind_ActorSystem` | `CScriptBind_ActorSystem` | Actor system Lua bindings |
| `ScriptBind_ActionMapManager` | `CScriptBind_ActionMapManager` | Action map Lua bindings |
| `ScriptBind_VehicleSystem` | `CScriptBind_VehicleSystem` | Vehicle system Lua bindings |
| `ScriptBind_Vehicle` | `CScriptBind_Vehicle` | Vehicle instance Lua bindings |
| `ScriptBind_VehicleSeat` | `CScriptBind_VehicleSeat` | Vehicle seat Lua bindings |
| `ScriptBind_Inventory` | `CScriptBind_Inventory` | Inventory Lua bindings (conditional) |
| `ScriptBind_UIAction` | `CScriptBind_UIAction` | Flash UI action Lua bindings |

## Update Loop

CryAction participates in the engine's main loop through these methods, called by `ISystem`:

| Method | When Called | Source |
|--------|-------------|--------|
| `PreSystemUpdate()` | Before `ISystem::Update`, after renderer prepares new frame | `CryAction.h:100` |
| `PostSystemUpdate()` | After `ISystem::Update`, core engine systems updated | `CryAction.h:101` |
| `PreFinalizeCamera()` | Before camera is passed to 3D engine for occlusion culling | `CryAction.h:102` |
| `PreRender()` | Just before `ISystem::Render` | `CryAction.h:103` |
| `PostRender()` | After `ISystem::Render`, renderer has started rendering | `CryAction.h:104` |
| `PostRenderSubmit()` | After `ISystem::RenderEnd`, frame is final | `CryAction.h:105` |

## Game Context Lifecycle

The game context represents a running game session (level + game rules):

1. **Start**: `StartGameContext(const SGameStartParams*)` — initializes server/client, loads level, spawns players (`source:CryAction.h:165`)
2. **Change**: `ChangeGameContext(const SGameContextParams*)` — switches level/rules on the server (`source:CryAction.h:166`)
3. **End**: `EndGameContext()` — tears down the running session (`source:CryAction.h:167`)
4. **Query**: `StartedGameContext()` / `StartingGameContext()` — check context state (`source:CryAction.h:168-169`)

## Console Commands

CryAction registers the following console commands (`source:Code/CryEngine/CryAction/CryAction.cpp:362-452`):

| Command | Description |
|---------|-------------|
| `dumpmaps` | Lists all available levels |
| `map` | Loads a level with game rules |
| `unload` | Unloads current level |
| `play` | Plays a time demo |
| `connect` | Connects to a server |
| `disconnect` | Disconnects from server |
| `disconnectchannel` | Disconnects a specific channel |
| `status` | Server status |
| `version` | Version info |
| `saveTag` / `loadTag` | Save/load tagged save |
| `save` / `load` | Save/load game |
| `genStringsSaveGame` | Generate save game strings |
| `kick` / `ban` / `unban` / `banstatus` | Player management |
| `openURL` | Opens URL in browser |
| `test_reset` | Test reset |
| `rcon_*` | Remote control commands |
| `http_startserver` / `http_stopserver` | Simple HTTP server |
| `mutePlayer` | Mute a player by entity ID |

## Subsystems

### Game Managers

| Manager | Interface | Description | Child Page |
|---------|-----------|-------------|------------|
| Action Map Manager | `IActionMapManager` | Input-to-action mapping | [ActionMapManager](CryAction/ActionMapManager.md) |
| Material Effects | `IMaterialEffects` | Surface-based effects (audio, decals, particles) | — |
| Player Profiles | `IPlayerProfileManager` | Save/load player settings | — |
| Flash UI | `IFlashUI` | Scaleform Flash UI integration | — |

### Game Systems

| System | Interface | Description | Child Page |
|--------|-----------|-------------|------------|
| Actor System | `IActorSystem` | Player and AI actor management | — |
| Checkpoint System | `ICheckpointSystem` | Checkpoint save/load | — |
| Effect System | `IEffectSystem` | Managed effect lifecycle | [Effect System](CryAction/Effect%20System.md) |
| Flow System | `IFlowSystem` | Visual scripting (Flow Graph) | — |
| Force Feedback System | `IForceFeedbackSystem` | Controller vibration | — |
| Game Rules System | `IGameRulesSystem` | Game mode rules | — |
| Game Token System | `IGameTokenSystem` | Named value tokens for plot/state | — |
| Item System | `IItemSystem` | Item/weapon management | [Item System](CryAction/Item%20System.md) |
| Level System | `ILevelSystem` | Level discovery and loading | [Level System](CryAction/Level%20System.md) |
| Vehicle System | `IVehicleSystem` | Vehicle management | [Vehicle System](CryAction/Vehicle%20System.md) |
| View System | `IViewSystem` | Camera view management | [View System](CryAction/View%20System.md) |

### Additional Subsystems

| Subsystem | Interface/Class | Description |
|-----------|----------------|-------------|
| Game Object System | `IGameObjectSystem` | Game object extension registration |
| Gameplay Recorder | `IGameplayRecorder` | Gameplay event recording |
| Cooperative Animation Manager | `ICooperativeAnimationManager` | Multi-actor animations |
| Custom Action Manager | `ICustomActionManager` | Custom action sequences |
| Custom Event Manager | `ICustomEventManager` | Custom event dispatch |
| Shared Params Manager | `ISharedParamsManager` | Shared parameter storage |
| Persistent Debug | `IPersistantDebug` | Time-based debug drawing |
| Mannequin | `IMannequin` | Animation controller system |
| Game Volumes Manager | `IGameVolumes` | Editor shape/volume game objects |
| Time Demo Recorder | `ITimeDemoRecorder` | Gameplay recording/playback |
| Game Statistics | `IGameStatistics` | Telemetry and stats |
| Game Session Handler | `IGameSessionHandler` | Multiplayer session management |
| Break Replicator | `IBreakReplicator` | Procedural break replication |
| Net Message Dispatcher | `CNetMessageDistpatcher` | Network message routing |
| Entity Container Manager | `CEntityContainerMgr` | Entity grouping/containers |

## Public Interfaces (I*.h in CryAction/)

All public interfaces are located in `Code/CryEngine/CryAction/`:

| Interface | Purpose |
|-----------|---------|
| `IActionMapManager.h` | Action map management |
| `IActorSystem.h` | Actor registration and lookup |
| `IAnimatedCharacter.h` | Animated character movement |
| `IAnimationGraph.h` | Animation graph state |
| `ICheckPointSystem.h` | Checkpoint save/load |
| `ICooperativeAnimationManager.h` | Cooperative animations |
| `ICryMannequin*.h` (6 files) | Mannequin animation system |
| `IEffectSystem.h` | Effect lifecycle |
| `IForceFeedbackSystem.h` | Controller force feedback |
| `IGameObject.h` | Game object interface |
| `IGameObjectSystem.h` | Game object extension system |
| `IGameplayRecorder.h` | Gameplay event recording |
| `IGameRulesSystem.h` | Game rules registration |
| `IGameSessionHandler.h` | Session management |
| `IInteractor.h` | Entity interaction |
| `IItem.h` | Item interface |
| `IItemSystem.h` | Item system |
| `ILevelSystem.h` | Level discovery/loading |
| `ILoadGame.h` / `ISaveGame.h` | Save/load game |
| `IMetadataRecorder.h` | Metadata recording |
| `IMovementController.h` | Character movement control |
| `IPlayerProfiles.h` | Player profile management |
| `IRangeSignaling.h` | Range-based signaling |
| `ISharedParamsManager.h` | Shared parameters |
| `ISubtitleManager.h` | Subtitle display |
| `IUIDraw.h` | UI drawing utilities |
| `IVehicleSystem.h` | Vehicle system |
| `IViewSystem.h` | View/camera system |
| `IWeapon.h` | Weapon interface |
| `IWorldQuery.h` | World raycast queries |

Additional shared interfaces in `CryCommon/CryAction/`:

| Interface | Purpose |
|-----------|---------|
| `IActionMapManager.h` | Core action map types (ActionId, SActionInput, IActionListener) |
| `ICustomActions.h` | Custom action sequences |
| `ICustomEvents.h` | Custom event system |
| `IDebugHistory.h` | Debug history graphs |
| `ILipSync.h` / `ILipSyncProvider.h` | Lip-sync animation |
| `IMaterialEffects.h` | Surface-based effects |
| `ITimeDemoRecorder.h` | Time demo recording |

## Child Pages

- [ActionMapManager](CryAction/ActionMapManager.md)
- [Effect System](CryAction/Effect%20System.md)
- [Item System](CryAction/Item%20System.md)
- [Level System](CryAction/Level%20System.md)
- [Vehicle System](CryAction/Vehicle%20System.md)
- [View System](CryAction/View%20System.md)

## Scriptbinds

- [ScriptBind_Action](../../CRYENGINE%20API%20Reference/ScriptBind%20Reference/CryAction%20Functions/ScriptBind_Action.md)
- [ScriptBind_ActionMapManager](../../CRYENGINE%20API%20Reference/ScriptBind%20Reference/CryAction%20Functions/ScriptBind_ActionMapManager.md)
- [ScriptBind_ActorSystem](../../CRYENGINE%20API%20Reference/ScriptBind%20Reference/CryAction%20Functions/ScriptBind_ActorSystem.md)
- [ScriptBind_GameStatistics](../../CRYENGINE%20API%20Reference/ScriptBind%20Reference/CryAction%20Functions/ScriptBind_GameStatistics.md)
- [ScriptBind_GameToken](../../CRYENGINE%20API%20Reference/ScriptBind%20Reference/CryAction%20Functions/ScriptBind_GameToken.md)
- [ScriptBind_Inventory](../../CRYENGINE%20API%20Reference/ScriptBind%20Reference/CryAction%20Functions/ScriptBind_Inventory.md)
- [ScriptBind_ItemSystem](../../CRYENGINE%20API%20Reference/ScriptBind%20Reference/CryAction%20Functions/ScriptBind_ItemSystem.md)
- [ScriptBind_Network](../../CRYENGINE%20API%20Reference/ScriptBind%20Reference/CryAction%20Functions/ScriptBind_Network.md)
- [ScriptBind_UIAction](../../CRYENGINE%20API%20Reference/ScriptBind%20Reference/CryAction%20Functions/ScriptBind_UIAction.md)
- [ScriptBind_Vehicle](../../CRYENGINE%20API%20Reference/ScriptBind%20Reference/CryAction%20Functions/ScriptBind_Vehicle.md)
- [ScriptBind_VehicleSeat](../../CRYENGINE%20API%20Reference/ScriptBind%20Reference/CryAction%20Functions/ScriptBind_VehicleSeat.md)
- [ScriptBind_VehicleSystem](../../CRYENGINE%20API%20Reference/ScriptBind%20Reference/CryAction%20Functions/ScriptBind_VehicleSystem.md)

## See Also

- [Engine Modules](../Engine%20Modules.md) — All engine module overview
- [Game Objects](../../CRYENGINE%20Game%20Code/Game%20Objects.md) — IGameObject extension system
- [Getting Started with Game Code](../../CRYENGINE%20Game%20Code/Getting%20Started%20with%20Game%20Code.md) — Game DLL development
- [Setting Up Controls and Action Maps](../../CRYENGINE%20Game%20Code/Miscellaneous%20Game%20Code/Setting%20Up%20Controls%20and%20Action%20Maps.md) — Action map configuration
- [CryInput](../CryInput.md) — Raw input handling
