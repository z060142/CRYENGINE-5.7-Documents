# EaaS 3.6.1

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/47316993/pages/44963008
- Page ID: 44963008
- Breadcrumb: Engine Release Notes (Current) > CRYENGINE 3.x > EaaS 3.6 > EaaS 3.6.1
- Parent: EaaS 3.6

## Content

Version not released

### Fixed

- (Mannequin) Release actioncontroller before deleting animation context.
- (Sandbox) Terrain editor: Axis behavior (CE-3017).
- (Sandbox) Stack overflow during level chainloading.
- (Sandbox) Entity: Show fullpath for archetypes in properties (CE-2716).
- (Sandbox) AI/Physics greyed out (CE-2864).
- (Sandbox) Removed deprecated Water Wave tool from UI, causing crashes on adding (CE-2851).
- (CryDesigner) Fixed a potential workflow issue of the CryDesigner to allow to set whether designer objects are saved to a binary file in the Preferences. By default the Designer Objects will be saved to each.lyr file.
- (CryDesigner) Fixed a crash bug taking place when loading level caused by not skipping a null object in a binary loading time (CE-3089).
- (CryDesigner) Fixed a crash bug caused changing a tool from then object mode tool without a designer object.
- (Renderer) Copy rendermesh type and flags during full copy.
- (Renderer) Potential crash during shutdown.
- (Shader) Removed unused technique DeferredLightProj to fix startup assert.
- (Shader) Wrong assert for valid semantics SV_
- (Common) Removed Vec3 assert to avoid unnecessary spam during e.g. vector resizing with default structs like SVF_P3F_C4B_T2F.
- (System) CPU detection failing with Avast! virtualization (CE-1238).
- (GameSDK) Level mission objectives don't work in Launcher (CE-3077).
- (Vegetation) Only dissolve during shadow pass.
- (Network) Port conflicts resulting in server nub not being created (CE-1430).
- (Entity) Fixed incorrect model path for turret entity.
- Only send Synergy relative mouse movement events if middle mouse button held down.
- Fix crash when adding Track to material node.
- Node name doesn't update color after assigning material or changing name.
- Fixed array index out of bound when resizing the terrain from low to high resolution along with different meters per unit (CE-1872).
- Multiple select of same entity does not expose parameters (CE-2974).
- Reject degenerate phys areas (CE-2951).
- Fix for ropes tied on both ends on ragdolls (CE-2977).
- Fixed a bug about the undo after merging multiple designer objects (CE-2895).
- Fixed a bug not displaying p4v message box to say to overwrite a file which is ready-only.
- Fixed "Pivot To Center" tool so that multiple selected designer objects can be applied in a time.
- Fixed a bug of the Grid Snapping so that the cursor on an edge can be snapped to grid as well.
- Fixed bugs in the Extrude Tool and Offset Tool so that wrong directed faces can't be created.
- ManualFrameStep build fix (typo).
- Disabling irrelevant input processing actions when manual frame step mode is inactive.
- Fix splitter processing of volumes with only a single mip.
- LODs: Fixed erase from iterator.
- Fixed global entities with physics proxy missing after reloading segments (CE-2634)
- Fixed assert in float2int.
- Fixed a crash bug taking place when entering the game mode while using the Array tool or Clone tool (CE-2975).
- Phys profiling fixes.
- Multi-threading fix for advanced water volumes.
- Problem with attached rope twist damping.
- Potential collider lists integrity problem.
- Fix for a crash if more than 256 textures tried to stream at once. The texture streaming slot was getting truncated by a bad cast.
- Fixed clash between tag "collision" as a type of hitdeathreaction as well as a hit_type: renamed the former to collisionreaction and fixed data referring to it.
- Resaved hitDeathTags.xml
- (Assets) Fixed Forest grass aligning to terrain.
- (Assets) Re-exported Airfield to fix bug with Tree LODs (CE-2876).
- (Assets) Updated materialeffects spreadsheet.
- (Assets) Fixed Forest boat causing orthonormal errors by setting scale to 1 (was set to 1.07).
- (Assets) Fixed incorrect paths on rock_large01 material.
- (Assets) Fixed Crash with EntityFlashTag material pointing to unavailable.ui asset (CE-2936).
- (Scaleform) Fixed scrolling in main menu.
- (Scaleform) Bad menu config - controller - buttons make screen black (CE-3057).
- (Scaleform) Fixed hitbox of slider and switch.
- (Scaleform) Removed logging message <Flash> - Navigate in: <direction> (CE-1638).
- (Scaleform) Fixed Objectives key not working in Launcher. Remapped to TAB key where it should be (no scoreboard in SP, no objectives in MP).
- (Scaleform) Fixed "Error: CallMethod... Menus_Startmenu.gfx" (CE-211).
- (Scaleform) Fixed Escape button in Launcher not returning to game (CE-2781).
- (Scaleform) Refilled the empty solid objects in the Forest Level file with valid regions (CE-2827).
- (Scaleform) Menu background pic mis-aligned, fixed alignment of dialogbox overlay (CE-1824).
- (Scaleform) when navigating backwards in a menu, item 0 is highlighted but not selected.
- (Scaleform) When pressing down on an item and then dragging the mouse in the game menu, item stays highlighted (CE-2808).
- Fixed clash between tag "collision" as a type of hitdeathreaction as well as a hit_type: renamed the former to collisionreaction and fixed data referring to it.
- Improve In Game Menu Level Selection (CE-3063).

### Added

- (Sandbox) Added PyLog functionality.
- (AISystem) Added new idle/interruptable MBT.
- (Flowgraph) Resurrected SetObjectMaterial node. Remapped to Material folder (not Engine).
- (SDKs: GPA) Use GPA 2014 R2 (CE-2917).
- Re-implemented support of 3ds Max 2010.
- Added support of 3dsMax 2015.
- Added support for Maya 2015.
- Added new "Particle" physics entity which exposes the particle physics parameters.

### Deleted

- (Editor) Remove "sketch mode" option in Sandbox (CE-2963)
- Deleted unused files - BrushIndoor.h/cpp, BrushDesignerMeasureTool.h/cpp, BrushDesignerExtrudeEdgeTool.h/cpp, AreaSolidPanel.h/cpp.
- Deleted unneeded Scope Definition files (since 3.5.9 the scope defs are not needed anymore).

### Optimization

- Tightened up phys explosion debug draw (CE-2915).

### Refactored

- (Sandbox) Removed obsolete LightPropagationVolume area object. Updated Error log message to show proper error messages for missing runtime classes.
- (Sandbox) Time Of Day: Removed deprecated properties: Lights HDR dynamic power, Sky color, Sky color multiplier, Ambient ground color, Ambient ground color multiplier, Ambient min height, Ambient max height, Sky custom color, Sky custom color multiplier, Sky custom color influence, Sun shafts visibility. Increased maximum value for Star Intensity from 3 to 16 (CE-2728).
- (Sandbox) Removed obsolete Calculate Sky Terrain Accessibility checkbox from Texture generation dialog.
- (Entity) Hidden unsupported entities: DeflectorShield, GravityStream, MissionPathHelper, ScanSpot, SpotterScannable, TacticalEntity, VTOLSpawnPoint.
- (Entity) Cleanup of Light entities, including EnvProbes. Removed all dead parameters. Moved Shadow parameters to new "Shadows" category. Added missing parameters from Light to RigidBody/Destroyable lights. Moved Flare properties to Style section. Moved random params to Options section.
- Copy GameSDK\Materials\sky\sky.mtl to Engine\EngineAssets\Materials\sky\sky.mtl. This file is required for new levels and should be in the Engine folder. Also copying associated textures and updated LevelTemplates script to affect new levels.
- Removed incm3(),decm3() and isneg() in vector orthonormalization.
- Remove custom allocation scheme for geom cache buffer handles.
- Added missing constructors, operators & documentation.
- Heavy refactoring and cleanup of Example FlashUI.

### Tweak

- (AISystem) Remove idle animation to prevent popping when giving commands.
- (AISystem) use of incompatible flow nodes inside AIAction nodes is now detected and warned about.
- (AISystem) BehaviorTree node Parallel was missing some checks for its success- and failure-mode setup.
- (Sandbox) Set terrain height to 32m for a new level by default (CE-1949).
- (Sandbox) Added next-gen export options to the layer settings and removed last-gen platforms from it (CE-2208).
- (Sandbox) Updated DebugView toolbar functionality.
- (CVars) Updated helper information text for various CVars.
- (Game) Moved XboxLive nodes to a more appropriate group.
- (Flowgraph) Time:TimedCounter supports to continue counting.
- (Flowgraph) Using numpad +/- instead of o/p for zooming in and out of a flowgraph (CE-2677).
- (3DEngine) Removed deprecated C1C vegetation profiler prototype.
- (Assets) Updated default Time of Day XML to suit PBS.
- (UIActions) Fixed positioning of image in gamepadlayout menu.
- (CryDesigner) Made a subtool panel placed at the just upper than the designer menu panel.
- (CryDesigner) Improved the "Box Primitive Creation Tool" so that side faces can be interacted with the existing faces.
- (CryDesigner) Added the "Binary Save" item in Geometry setting panel to select if a designer object will be saved as a binary or not.
- (CryDesigner) Added routines to Delete empty designer objected in proper timings.
- (CryDesigner) Restored the Seamless editing.
- (CryDesigner) Added a routine to delete an empty areasolid automatically.
- Updated Steam SDK to 1.28.
- Added support for MotionBuilder 2015.
- Changed "Pivot BBox" tool name to "Pivot To Center" (CE-2896).
- Added the highlight of vertex and edge elements (CE-2473).
- Manual frame step mode: remove spacebar hotkey, added back support for backtracking.
- Moved manual frame step mode hotkey to "Pause" in order to avoid conflicts with the profile CVar.
- Exporting an object from sandbox should default to the base folder for the current level and default to the specific file type (CE-2249).
- LODs: Changed some messages that were bloating the log files.
- Set tiled deferred shading on by default (CE-3006).
- Documentation generation: Update Lua docomatic settings - hide AttachTo, DetachFrom and Release() functions.
- Cleaned rc.ini.

### New Feature

- (Game) Camera node added to get the pos and dir of the viewcamera.
- (Sandbox) Terrain Editor: Import heightmap as tif file (CE-3059).
- (UIActions) Join Multiplayer Server List not populated, now automatically searches for servers when menu is shown (CE-3064).
- Added DebugVisuals toolbar Fixed script-toolbars not showing up in editor (CE-2997).
- Steam user stats.
- Basic Steam leaderboards.
- Ability to change geom cache buffer size at run-time.
- Added the SnapToGrid Tool (CE-2645).
- Added a mode to keep center of the pivot position every time changes take place (CE-2474).
- Applied new CryDesigner to the AreaSolid.
- Manual frame step now works in MP.
- Added a command to step frame by frame.
- Manual frame step mode: added support for going back in time using capture_frames.
- Allow to specify alembic compile preset name in XML.
- Added ragdollize flownode.
