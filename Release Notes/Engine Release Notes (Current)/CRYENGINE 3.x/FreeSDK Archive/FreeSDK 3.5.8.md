# FreeSDK 3.5.8

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/47316993/pages/44963035
- Page ID: 44963035
- Breadcrumb: Engine Release Notes (Current) > CRYENGINE 3.x > FreeSDK Archive > FreeSDK 3.5.8
- Parent: FreeSDK Archive

## Content

Released March 3rd, 2014

### Important Info

Known Issues

- Scriptbind HUD issue when attempting to display mission objectives in pure-game mode. Editor only support for current implementation but will be resolved ASAP for pure-game.

### New Feature

- (AISystem) failed Actions in the Modular Behavior Tree can now be printed via CVar: ai_DebugModularBehaviorTreeFailedActions.
- (Particles) Added WindScale sub-field to AirResistance param. Moved RotationalDragScale there as well (CE-2291).
- Runtime skel-extensions.
- Clear separation of doubles and reals.
- Added GetIAttachmentSkin() to access skin instances directly.
- (AISystem) Boids can now be turned invincible via Sandbox (CE-2200).
- Exposed a way to make force-limited constraints soft instead of breaking.
- (CryDesigner) Implemented Flip tool to flip selected faces.
- (Flowgraph) Added levelPath filtering to OnGetLevels node. This allows custom filtering of level results, Multiplayer menu only loads levels in Multiplayer folder. Added Multiplayer:GameOption node for getting and setting values from playlist system.
- (Particles) Alpha clipping applied to decals as well.
- (Particles) Particle sub-effects now directly instanstiable.
- (CryDesigner) Added a new parameter "Step Rise" for Stair tool.
- (Sandbox) Added an input box to modify the vegetation painter radius (CE-2068).
- (UIActions) LobbyHost: Added Variant switch for playlist system. Added HostMPCustomSettings page (WIP) to handle custom game settings which works with playlist/variants system. Added localization strings.
- (Playlists) Added DefaultPlaylistSDK example script. Referenced Playlist in PlaylistIndex script. Added "Hardcore" variant version into StandardVariants script.
- (EntitySystem) EntityId can now be rendered via CVar es_debugDrawEntityIDs.
- Added SP_Objectives graph to handle basic mission text (CE-2250). Updated HUD_Radar to display Mission entities on in-game minimap. MissionObjective, Human AI and Vehicles currently supported (CE-2250).
- (UIActions) Added Stereo3D options into Graphics Menu.
- (UIActions) Added ability to select Playerclass/Equipment via in-game MP menu.
- Added ActionScript function to handle off-radar entities.
- (UIActions) HostMP: Added LevelPath filtering to filter levels only in the levels/Multiplayer folder. Can be re-defined or disabled via UIActions.
- (CryDesigner) Enabled to export Designer objects to.obj file (CE-2403). Enabled to draw a debug outline of a designer object as it is selected (CE-2403). Made a pivot of the selected designer object with transformation be center when PivotToCenter button pressed (CE-2403).

### Fixed

- (Editor) ErrorDialog will freeze the editor when called by certain dialogs (CE-2132).
- Fixed a bug where if you had an unconnected navmesh triangle and added an off mesh link to it the link array could get corrupted.
- (Flowgraph) Context menu selection options are only available if a node is actually selected (CE-2168).
- (GameDLL) Removed Tracker perk effects particle references from RecordingSystem (CE-2339).
- (CryDesigner) Fixed a bug related to not restoring time after coming back (CE-2199).
- (Sandbox) Fix an issue that the vegetation painter radius can to go to 0 (CE-2068).
- (Vehicle) Destroyed model isn't loading (CE-1957).
- (Shaders) Fixed issue with Flowmap using incorrect channel in Watervolume shader.
- (Scaleform) When minimizing and then restoring the game, any videos that are playing will play super-fast (CE-2117).
- (AISystem) AIActor's initial position now gets serialized (also bumped the SAVEGAME_VERSION_VALUE to 25).
- (Particles) Fixed emitter sorting ambiguity when camera inside bounding box, now use negative distances.
- (Game) after de-serialization, an Item was always selected even if none was selected before (CE-1393).
- Dynamic water volume param changing issue in AI/Physics mode (CE-2284).
- (Particles) Restored EmitGeom release in Emitter.Reset, to prevent dangling CharInstance pointer crash during shutdown (CE-1907).
- (Scaleform) FlashUIElement FunctionNode tried to access bad memory in destructor.
- (Flowgraph) Clear freenodeType vector on ReloadNodeTypes.
- (Sandbox) Character Editor: Fix SaveAs dialog functionality (CE-2379).
- Issue with cylinder collisions with ropes/cloth.
- (CryDesigner) Fixed a bug related to Exclusive Mode about not restoring time rightly when coming back to the normal edit mode.
- (AISystem) a looping animation is now immediately stopped when the Animate node is terminated.
- Fix for the re-hover over help text (CE-2013).
- Character Editor crashing when opening any character CAttachmentManager::UpdateAllRemapTables (CE-2281).
- Moving an entity in editor will now call OnTransformFromEditorDone instead of OnReset.
- (Particles) OrientToVelocity now accounts for vortex motion (CE-2260).
- Fixed ftoi() 32-bit for Recode. Static local causes rewrite of function which conflicts with __asm usage. Making the static local const resolves the issue.
- Fixed thread mismatch in texture streamer (CE-2202).
- (AISystem) behavior tree SDK_Grunt_04: certain group members could become Idle while others were still in Combat.
- Tightened up rope attachment handling on hiding/unhiding (CE-1876).
- Fix CNetMessageSinkHelper to work with Recode. Recode cannot directly stub static member arrays with a specialized dimension.
- (Sandbox) Modify Terrain tool: Correct toggle height for Raise/Lower by holding CTRL (CE-352).
- (Entities) Wind entities are now outdoor-only only if the Outdoor Only option is set (CE-227).
- Sandbox: Support ed_lowercasepaths for saving level data files.
- Problem with dynamic water volume inside/outside fog detection (CE-2290).
- Fixed missing Tagpoint editor icon when the entity is copied (CE-1986).
- (Scaleform) Tentative fix for crashing UIElements on exit.
- Fixed bug causing improper culling of attachments due to caching of value from recursive rendering calls.
- (Assert) Incorrect items being called in GameRulesStandardSetup.
- Fixed pe_status_area (CE-2109).
- (Editor) Soundmoods Database toolbar is missing (CE-2233).
- Multi-threading issue with wave sim (CE-2354).
- Fix for the re-hover over help text (CE-2013).
- (Scaleform) Flowgraph modules containing Flash UI nodes will call wrong functions (CE-2305).
- (CryDesigner) Made TOD, CV, Camera and Lights etc settings restored before loading an level so that Exclusive Mode settings won't affect the next level.
- Entities created through the Entity-Pool can have individual models now (CE-2110).
- (Game) Items placed in world disappear in MP (CE-1227).
- (Game) Item respawn doesn't work in MP (CE-1228).
- Removed unsupported SizeRandom parameter from boid scripts.
- (CryDesigner) Fixed a bug displaying incorrect measurement helper number of a front stair.
- (RC) Fixed 32-bit ImageCompiler (it was failing to compute gamma table properly).
- (CryDesigner) Fix a crash bug when pressing "apply" button in mirror tool (CE-2144).
- (CryDesigner) Create Tool: Fixed some wrong calculation of radius of sphere.
- (CryDesigner) Fixed a bug about not displaying a gizmo when starting Slice tool.
- (Profiling) r_displayinfo 2 showing incorrect information for the 'AI' and 'Anim' ms counter (CE-2303).
- Fixed SpawnArchetype flow node from spawning entity using broken property values (CE-1979).
- (CryDesigner) Fixed a bug about Geometry Flags Panel not showing when selecting more than 2 designer objects (CE-2248).
- (UIActions) HostMP: Added gl_skip=0 CVar to prevent automatic skipping in menu after first time server launch. JoinMP: Added gl_skip=1 CVar to allow skipping in menu if a game had previously been hosted and thus disabled. Simplified layout.
- (UIActions) Sys_StateControl: Added LocalPlayer node for correct DOF effect in MP. Added additional helper comments. MM_LoadingScreen: Added helper comment to show where to enable/disable loading screen images. MM_DisplayIngameMenu: Added helper comments and setup to show how to turn background image on/off for in-game menu. Now set to off by default. MM_DisplayMenuLoading, MM_DisplayMenu, MM_DisplayLoadingScreen: Additional helper comments.
- (UIActions) Fixed bug with Resolution not displaying correctly in Graphics menu (CE-2274).
- (UIActions) Fixed issue with scoreboard not displaying. Needs Actor:LocalPlayer for the Action node.
- (UIActions) Fixed chat functionality not working (HUD2D was not enabled, incorrect filters). Added setup to handle ForbiddenArea warning (CE-304). Changed "MP" category to "InGame" to handle both SP and MP graphs. Disabled similar/duplicate ProfileSettings and SetPlayerName pages to isolate UNDEFINED name issue. Removed IsMultiplayer check causing error on MP class selection. Renamed Server/Player IDs in MM_HostMP to prevent duplicate IDs being used across different graphs. Moved MM_DisplayMenuLoading into MM_Display group. Further layout tweaks.
- (Flash) HUD2D: Renamed "Jackal" to "Shotgun" so Shotgun weapon receives proper crosshair.
- (UIActions) Fixed issue with playernames not being set from HostMP/JoinMP. Replaced SetName node with cl_Nickname CVar as temporary solution. Added string:concat for more concise info on lobby type.
- (UIActions) Fixed a bug, resulting in wrong results from TextField. Fixes "UNDEFINED" issue in lobby.
- (Game) Flymode fixed (CE-1694).
- (Assets) Update Forest ruin material: Fixed black holes in ground. Adjusted blend layer settings.
- (Particles) Restored refraction functionality broken by alpha clipping (CE-2375).
- Prevent CrashHandler from being invoked in exported code.
- (Flowgraph) Crash when trying to enable/disable debugging on a group/folder instead of a flowgraph.
- (CryDesigner) Fixed a crash bug taking place when selecting and deselecting a designer object or undoing/redoing it (CE-2406).

### Added

- (AISystem) new sample behavior tree SDK_Grunt_05 added.
- (Game) Added Flownode to inform about leaving and entering Forbidden Area (CE-304).
- (CryDesigner) Added a disc type primitive.
- (Assets) New Lamp assets (props/furniture/appliances/lamps).
- (Assets) Added additional stackedlogs assets, roundhouse assets and distancetrees assets (CE-2225).
- (Assets) Added turret.
- (Flash) Added source files for flash assets.
- Added 3-part example mission in Forest.

### Optimization

- (Particles) Now implement old effect param conversion directly via TypeInfo, rather than extra XML queries. Added ability to define aliased struct member names, and hidden enum values. Added CompatibilityParticleParams derived struct, with old params. Changed FindSubVar to always recurse base classes, removed obsolete Finalize serialization option. Increased earliest compatible version to 19 (back to 2008!).
- (Particles) Removed redundant particle render object sort step, fixed SRendItem construction to allow Renderer sort by distance to work. Consolidated multi-pass particle render object flag adjustments into single pass. Removed r_ParticlesHalfResMinCount cvar (could cause popping).
- Properly take partid offset into account during StatObj physicalization.
- Wave sim improvements.
- Small improvements to buoyancy calculation.

### Refactored

- (Sandbox) Refactor Deltree func. Fix recursive removing folders without slash ending.
- (CryDesigner) Renamed Polygon to Circle.
- (Sandbox) Refactor Auto Backup. Added adjustment number of autobackups (CE-2172).
- (UIActions) (UIActions) Overhaul of UIActions flowgraphs. Replaced hardcoded strings with localized versions. Added numerous missing tooltips. Restructured flowgraphs for better readability. Restructured menu localization strings spreadsheet, per menu. Deleted several unused strings.
- (Mannequin) Removed the sound tag from all the files since it became obsolete a while ago when sounds were moved to their own database.
- (Game) Removed obsolete and unreferenced UIObjective nodes, MissionStatelistener replaces the functionality (CE-2263).

### Tweak

- (AI) Fixed an incorrect assert condition in the navmesh island code.
- Removing unnecessary texture streaming assert.
- (Particles) Replaced params. nDrawLast with.fSortOffset, replaced fCameraDistanceBias with fCameraDistanceOffset, now with positive sense.
- MusicLogic now plays the start layer when switching Moods.
- (Scripts) Updated EquipmentLoadout scripts with more information and sample content.
- Fixing assert when a physics object is scaled.
- (Scripts) Removed invalid "crosshair" parameter from Shotgun.
- Fixing assert if a pak can't be loaded into memory.
- (FlowNodes) Updated descriptions for FlowHudEventsNodes.
- (Editor) Added new screen resolution option to viewport dropdown list (CE-2273).
- (Editor) Asset browser functionality to send cgf items directly to LOD generator.
- Made color chart code more tolerant to slight differences in the frame colors.
- Removing unnecessary shader assert.
- MissionObjective entity: Removed obsolete sPathToObjective parameter (CE-2263).
- (CryDesigner) Combined Drill and Erase tool to A tool called "Remove" tool.
- (CryDesigner) Removed drawing circle and rectangle because they have same functions as disc and rectangle tools in Creation panel.
- (CryDesigner) Renamed Plane tool to Rectangle tool.
- (CryDesigner) Moved edit box of entering number of edge count for curve and circle tool to the separated panel.
- (CryDesigner) Improved a tool for creation of primitives. In edit mode this creations has been available.
- (Assets) Forest: Updated grass in lighthouse area (CE-2153).
- (UIActions) Added extra functionality to be able to display objectives. Fixed incorrect (old) parameter being used in defaultProfile. Tidied ProfileSettings graph, still disabled.
- (Assets) Forest: Disabled radiochatter for AI character.
- (Assets) Improved lifering proxy.
- (Assets) Improved proxy of rack_a, added rack_b version.
- (Assets) Added wheel proxies to small_plane assets.
