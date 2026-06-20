# Engine Architecture Overview

This page explains the CRYENGINE 5.7 runtime architecture: how the engine
starts, how modules are organized, the main loop structure, and how game code
plugs into the system.

---

## Module Architecture

CRYENGINE is composed of ~23 engine modules, each compiled as a separate DLL
and loaded at startup. Modules communicate through the global environment
singleton `gEnv`.

```
Launcher (WindowsLauncher.exe / Editor.exe)
  └── CrySystem.dll (core)
        ├── Cry3DEngine.dll     — 3D world rendering
        ├── CryRenderer.dll     — GPU rendering (D3D11/D3D12/Vulkan)
        ├── CryAction.dll       — game framework
        ├── CryEntitySystem.dll — entity management
        ├── CryPhysics.dll      — physics engine
        ├── CryAISystem.dll     — AI / navigation
        ├── CryAnimation.dll    — character animation
        ├── CryAudioSystem.dll  — audio middleware
        ├── CryNetwork.dll      — networking
        ├── CryInput.dll        — input devices
        ├── CryScriptSystem.dll — Lua scripting
        ├── CryMovie.dll        — cutscenes / TrackView
        ├── CryFont.dll         — font rendering
        ├── CryFlowGraph.dll    — visual scripting
        ├── CryLiveCreate.dll   — real-time editor link
        ├── CryDynamicResponseSystem.dll — DRS
        ├── CrySchematyc.dll    — entity logic scripting
        └── Game.dll            — game-specific code (plugin)
```

### Module Summary

| Module | Interface | Purpose |
|--------|-----------|---------|
| CrySystem | `ISystem` | Core: main loop, memory, console, file system, module loading |
| Cry3DEngine | `I3DEngine` | Terrain, vegetation, sky, fog, water, occlusion, time-of-day |
| CryRenderer | `IRenderer` | GPU rendering: D3D11, D3D12, Vulkan |
| CryAction | `IGameFramework` | Game framework, level system, view system, game rules |
| CryEntitySystem | `IEntitySystem` | Entity spawning, components, layers, archetypes |
| CryPhysics | `IPhysicalWorld` | Rigid bodies, collisions, constraints, cloth, vehicles |
| CryAISystem | `IAISystem` | Pathfinding, behavior trees, perception, cover |
| CryAnimation | `ICharacterManager` | Skeletons, animation blending, attachments, Mannequin |
| CryAudioSystem | `IAudioSystem` | Audio middleware abstraction (Wwise/FMOD) |
| CryNetwork | `INetwork` | Client-server networking, lobby, voice |
| CryInput | `IInput` | Keyboard, mouse, gamepad, motion controllers |
| CryScriptSystem | `IScriptSystem` | Lua VM, script bindings |
| CryMovie | `IMovieSystem` | Cutscenes, TrackView, cinematic camera |
| CryFont | `ICryFont` | Glyph caching, text rendering |
| CryFlowGraph | `IFlowSystem` | Visual scripting node graph |
| CrySchematyc | `ICrySchematycCore` | Entity logic scripting with node editor |
| CryDynamicResponseSystem | `IDynamicResponseSystem` | Signal-based response system |

---

## The Global Environment — gEnv

`gEnv` is the central access point for all engine subsystems. It is a global
instance of `SSystemGlobalEnvironment` containing ~50 interface pointers.

**Header:** `Code/CryEngine/CryCommon/CrySystem/ISystem.h`

### Key Members

```cpp
// Core
gEnv->pSystem, gEnv->pTimer, gEnv->pLog, gEnv->pConsole, gEnv->pCryPak

// Rendering
gEnv->pRenderer, gEnv->p3DEngine, gEnv->pAuxGeomRenderer

// Gameplay
gEnv->pGameFramework, gEnv->pEntitySystem, gEnv->pPhysicalWorld,
gEnv->pAISystem, gEnv->pFlowSystem

// Animation & Audio
gEnv->pCharacterManager, gEnv->pAudioSystem

// Input & UI
gEnv->pInput, gEnv->pHardwareMouse

// Scripting
gEnv->pScriptSystem, gEnv->pSchematyc

// Networking
gEnv->pNetwork, gEnv->pLobby

// Debug & Tools
gEnv->pMovieSystem, gEnv->pDynamicResponseSystem, gEnv->pUDR,
gEnv->pJobManager, gEnv->pThreadManager
```

### Runtime State Helpers

```cpp
gEnv->IsEditor()           // Running under Sandbox Editor
gEnv->IsEditorGameMode()   // Editor in game mode (Ctrl+G)
gEnv->IsEditing()          // Editor in edit mode
gEnv->IsDedicated()        // Dedicated server
gEnv->IsClient()           // Client instance
gEnv->IsGameOrSimulation() // Game or simulation active
gEnv->bMultiplayer         // Multiplayer session
gEnv->bServer              // Server instance
```

---

## Initialization Sequence

### Phase 1: Platform Entry Point

The launcher (Windows, Linux, Android, Dedicated Server, or Editor) calls
`CryInitializeEngine()` with `SSystemInitParams`.

```cpp
WinMain()
  → SSystemInitParams params;
  → CryInitializeEngine(params);
```

### Phase 2: CryInitializeEngine

```
CryInitializeEngine(params)
  1. Set working directory to engine root
  2. Load CrySystem.dll
  3. CreateSystemInterface(params) → returns ISystem*
  4. If manual loop (Editor): return ISystem* to caller
  5. If automatic loop: system runs RunMainLoop() internally
```

### Phase 3: CSystem::Initialize — The Big Init

This is the massive initialization sequence (~1200 lines). Key steps in order:

```
-- Early Setup --
  Parse command line, set editor/dedicated flags on gEnv,
  detect hardware

-- Core Infrastructure --
  Create ProjectManager (load .cryproject JSON)
  InitFileSystem (CryPak, log, console)
  Load config files: game.cfg, user.cfg

-- Subsystem Initialization (in order) --
  JobManager → StreamEngine → Physics → Localization →
  AudioSystem → MonoBridge (optional) → ProjectPlugins →
  Renderer → Network → MovieSystem → Timer → Input →
  Animation → 3DEngine → ScriptSystem → Schematyc →
  EntitySystem → LiveCreate → DynamicResponseSystem →
  FlowGraph → AISystem → GameFramework (load game DLL) →
  Fire ESYSTEM_EVENT_CRYSYSTEM_INIT_DONE
```

### SSystemInitParams

Key fields passed to the engine at startup
(`Code/CryEngine/CryCommon/CrySystem/SystemInitParams.h`):

| Field | Purpose |
|-------|---------|
| `hWnd` | Main window handle |
| `sLogFileName` | Log file name |
| `szSystemCmdLine` | Full command line string |
| `bEditor` | Editor mode |
| `bDedicatedServer` | Dedicated server mode |
| `bSkipRenderer` | Skip renderer (headless) |
| `bSkipNetwork` / `bSkipInput` | Skip subsystems |
| `bMinimal` | Minimal mode (no audio banks) |
| `bTesting` | Unit test mode |
| `pUserCallback` | User-defined callbacks |

---

## Main Loop

### DoFrame — The Frame Sequence

Each frame follows a precise order. `DoFrame()` is called in an infinite loop
by `RunMainLoop()`.

```
FRAME START
  1. ProfilingSystem::StartFrame
  2. GameFramework::PreSystemUpdate
  3. PluginManager::UpdateBeforeSystem
  4. Network::SyncWithGame
  5. RenderBegin

MAIN UPDATE  (CSystem::Update)
  ├─ StreamEngine, CharacterManager
  ├─ Timer::UpdateOnFrameStart
  ├─ 3DEngine::OnFrameStart
  ├─ ScriptSystem::Update
  ├─ Input::Update
  ├─ DynamicResponseSystem::Update
  ├─ Console::Update
  ├─ Physics: PrePhysicsUpdate → PhysicalWorld::TimeStep → AISystem::Update
  ├─ EntitySystem::Update
  ├─ MovieSystem update
  ├─ AudioSystem::ExternalUpdate
  ├─ Schematyc::Update
  └─ UDR::Update

POST UPDATE
  7.  GameFramework::PostSystemUpdate
  8.  PluginManager::MainUpdate(frameTime)
  9.  CharacterManager::SyncAllAnimations
  10. GameFramework::PreFinalizeCamera
  11. 3DEngine::PrepareOcclusion

RENDER
  12. GameFramework::PreRender
  13. PluginManager::UpdateBeforeRender
  14. Render() — submit scene to GPU
  15. GameFramework::PostRender
  16. PluginManager::UpdateAfterRender
  17. RenderEnd() — swap buffers

FRAME END
  18. GameFramework::PostRenderSubmit
  19. PluginManager::UpdateAfterRenderSubmit
  20. ProfilingSystem::EndFrame
  21. SleepIfNeeded() — FPS throttling
```

### ESystemUpdateFlags

Control which subsystems are updated each frame: `ESYSUPDATE_IGNORE_AI`,
`ESYSUPDATE_IGNORE_PHYSICS`, `ESYSUPDATE_EDITOR`,
`ESYSUPDATE_MULTIPLAYER`, `ESYSUPDATE_EDITOR_AI_PHYSICS`.

---

## ISystem — The Core Engine Interface

**Header:** `Code/CryEngine/CryCommon/CrySystem/ISystem.h`

`ISystem` is the central engine interface. It owns the main loop, module
loading, memory management, and provides access to every subsystem via
`Get*` methods (`GetI3DEngine`, `GetIRenderer`, `GetIPhysicalWorld`, etc.).

### System Events

`ISystemEventDispatcher` broadcasts lifecycle events to registered listeners.
Register via `gEnv->pSystem->GetISystemEventDispatcher()->RegisterListener()`.

Key events for game code:

| Event | When |
|-------|------|
| `ESYSTEM_EVENT_GAME_POST_INIT_DONE` | All init done, safe to load |
| `ESYSTEM_EVENT_LEVEL_LOAD_START` / `_END` | Level loading lifecycle |
| `ESYSTEM_EVENT_LEVEL_GAMEPLAY_START` | Gameplay can begin |
| `ESYSTEM_EVENT_LEVEL_UNLOAD` | Level unloading |
| `ESYSTEM_EVENT_GAME_PAUSED` / `_RESUMED` | Pause/resume |
| `ESYSTEM_EVENT_EDITOR_GAME_MODE_CHANGED` | Editor game mode toggle |
| `ESYSTEM_EVENT_FULL_SHUTDOWN` | Full engine shutdown |

### System Global State

`ESystemGlobalState` tracks the engine's lifecycle phase from init through
level loading (`LEVEL_LOAD_START_PREPARE` → `LEVEL_LOAD_START_OBJECTS` →
`LEVEL_LOAD_END` → `LEVEL_LOAD_COMPLETE` → `RUNNING`).

---

## IEnginePlugin — Game Module Entry Point

**Header:** `Code/CryEngine/CryCommon/CrySystem/ICryPlugin.h`

`Cry::IEnginePlugin` is the modern replacement for the deprecated
`IGameStartup`/`IGame` system. Every game project implements at least one
plugin.

### Lifecycle

```cpp
class CMyGamePlugin : public Cry::IEnginePlugin
{
public:
    virtual bool Initialize(SSystemGlobalEnvironment& env,
                             const SSystemInitParams& initParams) override;

    // Optional per-frame update hooks (enable with EnableUpdate):
    virtual void MainUpdate(float frameTime) override;       // main game logic
    virtual void UpdateBeforeSystem() override;
    virtual void UpdateBeforePhysics() override;
    virtual void UpdateBeforeFinalizeCamera() override;
    virtual void UpdateBeforeRender() override;
    virtual void UpdateAfterRender() override;
    virtual void UpdateAfterRenderSubmit() override;

    virtual bool RegisterFlowNodes() override;
    virtual bool UnregisterFlowNodes() override;
};

CRYREGISTER_SINGLETON_CLASS(CMyGamePlugin)
```

### Update Step Order

Plugins opt into specific update steps via `EnableUpdate(EUpdateStep, bool)`:

| Step | When | Best For |
|------|------|----------|
| `BeforeSystem` | Before ISystem update | Earliest possible logic |
| `BeforePhysics` | Before physics step | Queuing physics jobs |
| `MainUpdate` | After ISystem update | **Main game logic** |
| `BeforeFinalizeCamera` | Before occlusion culling | Camera adjustments |
| `BeforeRender` | Before scene rendering | Pre-render setup |
| `AfterRender` | After render submitted | Post-render work |
| `AfterRenderSubmit` | After frame complete | End-of-frame cleanup |

### Plugin Manager

`Cry::IPluginManager` (via `gEnv->pSystem->GetIPluginManager()`) manages all
loaded plugins:

```cpp
auto* pMyPlugin = gEnv->pSystem->GetIPluginManager()->QueryPlugin<CMyGamePlugin>();
```

For details, see [Plugin System](../Beta%20Features/Plugin%20System.md).

---

## ITimer — Time and Framerate

**Header:** `Code/CryEngine/CryCommon/CrySystem/ITimer.h` · via `gEnv->pTimer`

```cpp
float dt  = gEnv->pTimer->GetFrameTime();      // delta time (seconds)
float fps = gEnv->pTimer->GetFrameRate();       // current FPS
gEnv->pTimer->SetTimeScale(0.5f);               // slow-motion (half speed)
gEnv->pTimer->PauseTimer(ITimer::ETIMER_GAME, true);
```

Two timer channels: `ETIMER_GAME` (pausable, serialized, smoothed/scaled) and
`ETIMER_UI` (non-pausable, non-serialized, raw frametime).

---

## ILog — Logging

**Header:** `Code/CryEngine/CryCommon/CrySystem/ILog.h` · via `gEnv->pLog`

Standard logging macros:

```cpp
CryLog("Player spawned at (%f, %f, %f)", pos.x, pos.y, pos.z);
CryLogAlways("This always appears");                          // even with log verbosity off
CryWarning(VALIDATOR_MODULE_GAME, VALIDATOR_WARNING, "Low health");
CryError("Fatal condition reached");
CryComment("Debug info: state = %d", state);                 // low-priority
```

---

## IConsole — Console Variables and Commands

**Header:** `Code/CryEngine/CryCommon/CrySystem/IConsole.h` · via `gEnv->pConsole`

### Registering CVars

```cpp
REGISTER_CVAR2("my_int", &g_myInt, 42, VF_NULL, "My integer variable");
REGISTER_CVAR2("my_float", &g_myFloat, 3.14f, VF_NULL, "My float variable");
REGISTER_STRING_CVAR2("my_string", &g_myString, "default", VF_NULL, "My string");
```

### Registering Console Commands

```cpp
static void MyCommand(IConsoleCmdArgs* pArgs) {
    CryLog("Called with %d args", pArgs->GetArgCount());
}
REGISTER_COMMAND("my_command", MyCommand, VF_NULL, "Description");
```

### Accessing CVars at Runtime

```cpp
ICVar* pVar = gEnv->pConsole->GetCVar("my_int");
if (pVar) { int value = pVar->GetIVal(); pVar->Set(100); }
```

For the full console system reference, see
[Console (API Reference)](../../API%20Reference/_Console.md).

---

## Config Spec — Hardware Tier Detection

The engine detects hardware capability and assigns a config spec:

| Spec | Target |
|------|--------|
| `CONFIG_LOW_SPEC` | Low-end PC |
| `CONFIG_MEDIUM_SPEC` | Mid-range PC |
| `CONFIG_HIGH_SPEC` | High-end PC |
| `CONFIG_VERYHIGH_SPEC` | Ultra PC |
| `CONFIG_DURANGO` | Xbox One |
| `CONFIG_ORBIS` | PS4 |

```cpp
ESystemConfigSpec spec = gEnv->pSystem->GetConfigSpec();
if (spec >= CONFIG_HIGH_SPEC) { /* enable high-quality features */ }
```

---

## Quick Reference

```cpp
ISystem*        pSys     = gEnv->pSystem;
ITimer*         pTimer   = gEnv->pTimer;
ILog*           pLog     = gEnv->pLog;
IConsole*       pConsole = gEnv->pConsole;
IEntitySystem*  pES      = gEnv->pEntitySystem;
IGameFramework* pGF      = gEnv->pGameFramework;
IPhysicalWorld* pPhys    = gEnv->pPhysicalWorld;
IRenderer*      pRend    = gEnv->pRenderer;
I3DEngine*      p3D      = gEnv->p3DEngine;

float dt  = pTimer->GetFrameTime();
float fps = pTimer->GetFrameRate();

CryLog("message");
REGISTER_CVAR2("my_var", &g_val, 0, VF_NULL, "description");

pSys->GetISystemEventDispatcher()->RegisterListener(&myListener, "MySystem");
pSys->Quit();
```

---

## Related Documentation

- [Gameplay Framework](../Gameplay/Gameplay%20Framework%20Programming.md) — IGameFramework, game subsystems
- [Entity Component Programming](../Entities%20and%20Tools/Entity%20Component%20Programming.md) — IEntityComponent, Schematyc
- [Plugin System](../Beta%20Features/Plugin%20System.md) — Cry::IEnginePlugin details
- [Console (API Reference)](../../API%20Reference/_Console.md) — IConsole, CVars
- [Profiling & Optimization](../Profiling%20&%20Optimization.md) — debug CVars, performance
- [System Utilities](../System%20Utilities.md) — Resource Compiler, config files
- [Projects and Plug-ins](../../API%20Reference/Projects%20and%20Plug-ins.md) — .cryproject format