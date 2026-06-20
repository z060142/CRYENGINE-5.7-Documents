# Important CRYENGINE 5.5 Data and Code Changes (5.5 Preview Releases)

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/47316993/pages/44962794
- Page ID: 44962794
- Breadcrumb: Engine Release Notes (Current) > CRYENGINE 5 > CRYENGINE 5.5 > CRYENGINE 5.5 Previews > Important CRYENGINE 5.5 Data and Code Changes (5.5 Preview Releases)
- Parent: CRYENGINE 5.5 Previews

## Content

The following is not intended to be a complete list of CRYENGINE 5.5 C++ API changes, rather it is an indication of the most important changes that Programmers need to be aware of.

### Table of Contents

### Deprecation Notices:

This release officially deprecates:

- CryLobby / Lobby System - Replaced with the new CryGamePlatform plug-in, wrapping both the Steam and PSN APIs. Xbox One will follow in the future. The lobby system will be removed in a future release.

### Renderer

- The r_Fullscreen and  r_FullscreenWindow CVars have been replaced with r_WindowType.
- Usage: r_WindowType [0=normal window/1=borderless window/2=borderless full screen/3=exclusive full screen]
- The Windows key is now enabled in the engine by default, use g_disableWinKeys=1 to return to prior behavior. This fixes inability to move the Launcher window with the Windows and arrow keys.

### Entity System & Schematyc

- Entity Components no longer require the IID function

### Plugins

- The ICryPlugin interface has been moved to the Cry namespace and renamed to IEnginePlugin
- Plug-ins no longer need to implement the GetName and GetCategory functions as default implementations has been added

#### Updates

Plug-in update support has been refactored in order to provide more opportunities for hooking into various system events. The OnPluginUpdate function has been replaced with several different callbacks and an accompanying enumeration entry:

Function | Enum Entry | Note
--- | --- | ---
UpdateBeforeSystem | IEnginePlugin::EUpdateStep::BeforeSystem |
UpdateBeforePhysics | IEnginePlugin::EUpdateStep::BeforePhysics | Replaces EUpdateType_PrePhysicsUpdate
MainUpdate | IEnginePlugin::EUpdateStep::MainUpdate | Replaces EUpdateType_Update
UpdateBeforeFinalizeCamera | IEnginePlugin::EUpdateStep::BeforeFinalizeCamera |
UpdateBeforeRender | IEnginePlugin::EUpdateStep::BeforeRender |
UpdateAfterRender | IEnginePlugin::EUpdateStep::AfterRender |
UpdateAfterRenderSubmit | IEnginePlugin::EUpdateStep::UpdateAfterRenderSubmit |

To enable a specific update, call IEnginePlugin::EnableUpdate with the specific step enumeration entry.

### Game Framework Removal

The Game Framework, also known as CryAction, is currently being removed - with vital parts moving into other parts of the engine.

#### Initialization Changes

The Game Framework was previously responsible for starting the engine:

Previous Initialization Flow

- Launcher is started by manually loading CryAction.dll, finding entry point addresses etc.
- An instance of IGameFramework (gEnv->pGameFramework) is created
- The game framework loads CrySystem.dll
- The game framework creates an instance of ISystem (gEnv->pSystem).
- System initializes other engine modules

New Initialization Flow

- Launcher is started
- An instance of ISystem is automatically created by calling the new CryInitializeEngine function, resulting in load of CrySystem.dll, and initializing an instance of ISystem.
- System initializes other engine modules, including the game framework

This results in possible issues with existing code where the game framework was presumed to exist at a certain point. In this case, correct your code by moving use of IGameFramework to the ESYSTEM_EVENT_GAME_POST_INIT system event.

#### Update Changes

The Game Framework was previously responsible for updating the engine. This has now been changed to move the management of each frame to CrySystem. This change should not impact existing code.

### Miscellaneous

- eCryM_Game has been removed, change existing references to eCryM_EnginePlugin for newer projects, otherwise eCryM_LegacyGameDLL.

[Deprecation Notices:](#deprecation-notices)[Renderer](#renderer)[Entity System & Schematyc](#entity-system-and-schematyc)[Plugins](#plugins)[Game Framework Removal](#game-framework-removal)[Miscellaneous](#miscellaneous)
