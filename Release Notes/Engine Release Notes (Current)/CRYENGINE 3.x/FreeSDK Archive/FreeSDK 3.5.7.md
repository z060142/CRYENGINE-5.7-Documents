# FreeSDK 3.5.7

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/47316993/pages/44963034
- Page ID: 44963034
- Breadcrumb: Engine Release Notes (Current) > CRYENGINE 3.x > FreeSDK Archive > FreeSDK 3.5.7
- Parent: FreeSDK Archive

## Content

Released February 4th, 2014

##
Important Info

Known Issues

-
A rare issue may occur where rope positions are moved back to origin point (0,0,0) on level Save/Export. We advise to check your level after Save/Export. If in the event your ropes have moved you have the option to restore from a backup (.bak) file or reposition the ropes.

-
Restoring from CryDesigner's "Exclusive Mode" may not restore TOD settings correctly.

##
New Feature

-
(Game) Added friction to the vehicles depending on surface type.

-
AIActors keep track of their initial position now.

-
Skel-extensions.

-
(Flowgraph) New nodes Math:ArcSinus, Math:ArcCosinus, Math:ArcTangens, Math:Ceil, Math:Floor, Math:Mod.

-
(Particles) New camera-related params: fFocusCameraDir, fCameraDistanceBias. Also bFocusRotatesEmitter (revived from CE 3.4). Refactored and optimized particle render functions.

-
Add compile-time support information to RC's generic info.

-
(CryDesigner) Added a debugger tool.

-
(AISystem) dynamic path adjustments work more reliably with "large" obstacles on slopes (CE-1959).

-
(Game) corpses can now time out via CVar g_corpseManager_timeoutInSeconds (CE-1989).

-
(Physics) Exposed rope awake flag. This allows ropes to be activated automatically on game start, rather than needing to fire an impulse through flowgraph.

-
Exposed "floating" flag in surfacetypes.xml.

-
(Physics) World dump update.

-
Dynamic water volumes.

-
(CryDesigner) Added "Seamless edit" check box so that turn seamless edit on and off.

-
(CryDesigner) Implemented "Select All".

-
(Particles) New params for alpha test control (CE-892).

-
(CryDesigner) Implemented the Exclusive Editing Mode.

-
(CryDesigner) Added a new parameter "Step Rise" for Stair tool.

##
Fixed

-
(Sandbox) corpses no longer persist throughout multiple game sessions in Sandbox (CE-1988).

-
Fixed vehicle partially invisible after respawning (CE-1957).

-
(Particles) Fixed crash when vertex count over limit, and buffer alignment bug.

-
(Editor) Restored SnapToGrid, Wireframe, Remember & Goto Location toolbar functionality (CE-2116).

-
(CryDesigner) Fixed a bug about remaining side faces while push/pull.

-
(Particles, Editor) Moving emitter entities no longer spawns multiple emitters.

-
Fix Undo not working when using terrain painter "Flood" (CE-1958).

-
Fixed it so reserving unbound entities works again (fixes case where a net entity is referenced before it spawns).

-
Issue with skeleton's memory statistics (CE-1731).

-
Dynamic water volumes fixes.

-
(Game) Can't drive tank in multiplayer (CE-1352).

-
(AISystem) some weapon offset for peeking were missing in the Human AI character.

-
(AISystem) non-queued signals were causing wait-operations to never finish (CE-1956).

-
(Scaleform) UIElements instances leaking in editor.

-
(Flowgraph) Reload in UIEmulator broke Flowgraphs.

-
(CryDesigner) Made mirrored objects not be able to attend "Merge", "ResetXForm" and "Pivot to Center".

-
(CryDesigner) Fixed bevel tool bugs.

-
(CryDeisgner) Fixed bugs causing broken faces in an union operation.

-
(Game) Grenades don't explode (CE-1333).

-
Water volumes serialization issue (CE-2046).

-
(3DEngine) material glow parameter doesn't get updated correctly when triggered via flowgraph (CE-1653).

-
Apply texture modifiers for vegetation & shadow gen pass (CE-1827).

-
Advanced watervolume profiler crash in 64bit (CE-2024).

-
Perforce plug-in: Fix crash if no connection, fix reconnection.

-
(Renderer) Reset current device context shaders when unbinding resources (CE-2016).

-
(Particles) Spawn on ParentCollision now works for every collision. Incorporated new fCameraDistanceBias into static bounds. Fixed scaling and speed errors with child particles.

-
(Sound) Fix for soundlistener getting disabled when using trackview (CE-1912).

-
(Game) Removed unused Level-tag logic from game-localization (CE-1948).

-
Possible crash on layer hiding/unhiding (CE-1962).

-
Fixed wrong LODs on composite objects (CE-86).

-
(ScriptProxy) OnCollision not properly clearing m_hitTable (CE-2006).

-
Removed rope position forcing in ai/physics mode.

-
(Game) Fixed physics Impulse parameter not working for Recoil in weapon scripts (CE-2018).

-
Fixed a bug related to missing polygons after moving elements.

-
Fixes for when MAX_JOINT_AMOUNT for animations is raised above 256. Some previously hardcoded arrays now use the define.

-
(CryDesigner) Added filling a face based on two unconnected edges.

-
(Shaders) Fixed issue with Flowmap using incorrect channel in Watervolume shader.

-
(Particles) fix for incorrect alpha scaling. Reverted some unneeded alpha scale param conversions. Alpha clipping applied to decals as well.

-
(CryDesigner) Fixed a bug displaying incorrect measurement helper number of a front stair.

-
(Particles) Fixed sorting errors between particles and other transparent objects, by using proper 3DEngine-set distance (CE-1147).

-
Force-integrate ReactiveTextureStreamer.cpp. Fixes StdAfx.h casing.

-
Fix for crashing UIElements on exit.

-
(Particles) Fixed SpawnOnCollision/Death with parent Bounciness < 0 (CE-2212).

-
Disable TryLock feature on SRW locks for Windows. Fixes inability to start CRYENGINE on Windows Vista.

-
(Game) Updated weapon_fx particles, fixed MG weapon overheat effect not playing.

-
(AISystem) some weapon offset for peeking were missing in the Human AI character.

-
Typesorting postponed (Char attachments).

##
Added

-
New BehaviorTrees with custom TPS queries added specifically for SDK tutoring purpose.

-
(Assets) Added pistol melee 1p animation. Added pistol pfx. Removed unnecessary duplicate SP/MP params. Small tidy of structure.

-
(CryDesigner) Added and modified materials and texture for CryDesigner Selection so that lighting doesn't affect the material.

-
(Assets) Added sample material/textures for blend layer with POM.

-
(Assets) Added several floor tile materials and textures with blend variations.

-
(Assets) Added CRYENGINE logo textures. Updated jointed_breakable material. Updated cloth_2 material which has the CE logo on it.

-
(Assets) Added rough version water volume material.

-
(Assets) Added sample water volume material and textures with decal setup.

-
(Assets) Updated weapon tracer assets to newer, larger version. Deleted old unused assets.

-
(Animation) added turn animation for when standing (CE-1793).

##
Optimization

-
More proper default out-of-grid settings.

-
Tweak to coll_type tag parsing for surface types.

-
(RENDERER) Lowered bandwidth for lens flare RT to 10F.

-
(Sandbox) Update Boost (for Python integration) from 46.1 up to 55.0. To support libs for VS 2012.

##
Refactored

-
Cleanup of physics setup.

-
Removed RawFace structure.

-
Replaced BrushUtil:: namespace with BUtil:: namespace.

-
Cleanup and Decoupling of CAnimationSet.

-
Removed redundant functions.

-
Phys testbed maintenance.

-
Saved both entity guid and resolved id during export; MP levels request to use entity id, which can be generated via batch export.

-
Deleted unused codes on drawing helpers.

-
(CryDesigner) Renamed "PushPull" to "Extrude".

-
(CryDesigner) Changed the clip tool name from "Clip" to "Slice".

##
Tweak

-
(Game) Don't use LowLevel physics when vehicles are stationary.

-
(Game) Keep physics awake for a bit longer to prevent it falling asleep on the apex of a slope.

-
(Flowgraph) Added ability to unassign an entity in a Node (CE-1611).

-
(Particles) Warning "ignoring spawning of immortal independent effect" now shows full sub-effect name (CE-796).

-
(Rendering) Warning "mismatch between texture and sampler type" no longer displayed for simple missing assets (CE-27).

-
(AISystem) secondary visual sensor added to "default" perception configuration.

-
(AISystem) Tactical Position System: more further debug rendering added.

-
Abrams: Added additional empty params. Removed deprecated params. Added recoil shake to weapons.

-
(Game) Added CVar g_suppressHitSanityCheckWarnings (CE-1298).

-
(Savegame) Unified savegame name, now based on IGame::GetName.

-
Rifle: Removed unnecessary duplicate SP/MP params. Small tidy of structure. Moved some duplicate values from sub-sections into default section. Removed invalid params. Made tracers visible.

-
(Physics) Enabled e_DeformableObjects by default (CE-1991).

-
(Particles) Editor now displays TRangeParam<> doublets in compact Vec2 format.

-
Strip semi-commas off the end of #pragma statements. Added missing shader compiler DLL.

-
Changed the bone limit for current gen consoles and PC to 1024 (last gen consoles use the old value of 256).

-
Behavior Tree visualizer now also shows the Selection Variables.

-
AI script Human_x.lua now defaults to the "SDK_Grunt_04" behavior tree.

-
(Assets) Forest update. Added AB particle layers and moved particles. Moved logic into logic layers. Added small steps into some houses. Deleted non-streaming layer and put assets into appropriate layers. Converted some brushes into geomEnt for ropes. Broke up some of the terrain painting with more varied materials.

-
(Assets) Forest: Moved some objects in the wrong layers. Replaced Cave geometry beams with volumetric beam materials on the lights.

-
Updated deformable_barrel material.

-
Readjusted the orientation of the HUD bone to prevent tilting of the onscreen Hud during aim and walk with the Pistol.
