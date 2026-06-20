# FreeSDK 3.5.6

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/47316993/pages/44963033
- Page ID: 44963033
- Breadcrumb: Engine Release Notes (Current) > CRYENGINE 3.x > FreeSDK Archive > FreeSDK 3.5.6
- Parent: FreeSDK Archive

## Content

Released December 20th, 2013.

##
Important Info

Music System changes
Important to note that in 3.5.5 and 3.5.6 there have been changes to the Music system sample rate which may affect your music. The default sample rate has been changed from 44.1KHz to 48KHz.

If you choose to stick with the 48KHz, you will need to update your Music assets to match that sample rate. If you don't wish to update the assets, you can revert back to 44.1KHz by using
**
s_MusicSampleRate 44100
**
.

Known Issues

-
A rare issue may occur where rope positions are moved back to origin point (0,0,0) on level Save/Export. We advise to check your level after Save/Export and when Hiding/Unhiding layers. If in the event your ropes have moved you have the option to restore from a backup (.bak) file or reposition the ropes.

##
Fixed

-
Fixed mipmap-selection bug for cubemaps (was always lowest mip).

-
AIPlayer: when running a game in Sandbox, the AIPlayer would not get updated in the first game session (but in all succeeding ones).

-
Hazard entities were no longer dealing damage to the player (CE-1298).

-
(System) Wrong memory address range page size.

-
Sandbox Custom Shelves broken (CE-1795).

-
SmartObjects would never get updated if no AI actor was present in the level.

-
(Particles) Fixed FPE in occlusion testing for large particles. Skip occlusion testing for DrawOnTop and DrawNear.

-
(Particles) Fixed transform error in GetRandomPos for mesh subobjects.

-
(Game) Squad Manager error during initialization of lobby.

-
Fixed issue with unavailable PFX being called in VTOLVehicleManager code.

-
Chunkexplore: fixed and improved chunk visualization, added visualization of the chunk file header.

-
(AI) Vehicles won't loop path (CE-1900).

-
Fixes zoom mode periodically switching on and off every 4 frames causing merged meshes to flicker (CE-1727).

-
g_HideArms Crashes - added guard against crash and added SDK attachment name for arms (CE-1688).

-
Renamed LoopCut tool to Clip tool.

-
Added a line to avoid infinite looping as removing edges regarding as a vertex in CBrushRegion.

-
Dealt with a case when side back regions in BrushArgument are adjacent with another region in the Designer as push/pull is being done.

-
Fixed a bug related to scaling elements in the move tool and reduce possibility of causing floating issue.

-
Disabled snap grid in drawing lines tool.

-
Made it possible to draw dimension figures in creation phase.

-
Fixed a few floating precision issues in 2D bsp operation.

-
Fixed a bug about dealing with coplanar regions in 3D boolean operation.

-
Dealt with inverted faces created as converting a solid object to a designer object in loading phase.

-
Modified a cancel process of a tool by pressing ESC as an order through select tool before exiting the designer mode.

-
Fixed Turtle Boid not using turtle asset. Deleted unneeded Salamanders, Plover and Crow boids.

-
(AISystem) SmartPathFollower prevents short-cutting through obstacles (CE-1933).

-
VectorSet, VectorMap : Fixed insert( Iterator first, last ) bug. Could result in duplicate entries in the Map or Set.

-
(Particles) Crash in release builds due to missing perf hud support.

-
Terrain: Accidental painting bug (CE-1695).

-
Added missing entries to entity scheduler.

-
(Particles) Fixed half-res rendering and vertex instancing selection (inconsistent flags). Made CVars more consistent.

-
(Recode) Removed spurious PCH includes in headers.

-
Added 1920x1200 preset to main menu graphics resolution list (CE-1818).

-
Fixed a bug causing for elements of a designer object created newly not to be selected (CE-1841).

-
Increased a speed of primitive shapes and changed the number of maximum sides of sphere from 128 to 32 (CE-1842).

-
Sound event does not playback in animation control window, Sound listeners are now activated/deactivated on window activation instead of Viewport activation (CE-1829).

-
Fixes the panel display render flags.

-
(Game) Added GetUsableText Message for Items (CE-642).

-
Vehicle first person camera gets the wrong rotation if no bone or helper is defined.

-
Clearing the wanted list will release textures, which will queue un-links that need to be pumped before texture vec is processed.

-
AI SmartPathFollower no longer attempts to shortcut through obstacles when moving on path segments that lead around obstacles (CE-1933).

-
Fixed a bug of jumping group objects after make a prefab out of the group objects.

-
(Physics) Area fixes: removed redundant Vec3 "size" aka "falloff" box, which wasn't always set. Gravity query was wrongly returned as true even outside area (is_unused error). Added "FalloffInner" property to area entities. Implemented "Ellipsoidal" property for Wind and Gravity entities.

-
Fixed a few bugs in the mirror tool about removing edges on a mirror plane and unexpected regions on a mirror plane taking place.

-
Fixed a bug about not assigning layer id to a designer object (CE-1898).

-
Made the prefab more reliable (CE-1301, CE-1366).

-
(Game) Boids: birds were walking while idle animation was running. OnGround-state is now subdivided into Walking/Slowdown/Idle (was implicitly only Walking/Idle before). Durations for these OnGround sub-states can be specified in lua now (defaults to the previously hard-coded values in the BirdBoid class). Walking speed while slowing down is now linearly interpolated (feels more natural as the animation speed is tight to it as well) (CE-1799).

-
(Physics) More area fixes: CPhysArea.m_falloff0 now defaults to 1, matching previous default behavior where falloff was ignored if m_size vec was 0 (fixes global wind area). Fixed incorrect calculation of CPhysArea.m_rsize. Reverted buggy change to CPhysicalProxy.OnEntityXForm. Now compute relative distance to area center differently for box and sphere geoms, in both CPhysArea and SPhysEnviron particle functions.

-
Fixed a critical bug in Flowgraph that was producing a unusable menu.

-
(Mannequin) First person swim animations not working.

-
Re-exported HUD assets to use the material hud_plane.mtl as default.

-
(Assets) Windmill: Fixed animation, UV issues, asset and mtl.

-
(Assets) Cloth: Re-exported with FP32 settings needed for use with the Cloth entity.

##
Added

-
Added elevator assets and re-pathed default objects for Elevator scripts.

-
LensFlares: Added missing lens flares for vehicle lights.

##
Deleted

-
Deprecating AISpawner and AIAlertness entities which are now controlled through FlowGraph.

-
Deprecated Solid creation in place of Designer objects. Existing Solids remain intact and are automatically converted to Designer objects.

-
Removed obsolete music assets.

##
Optimization

-
Reduced PFX count on spawned wood chips. Also disabled the physics sim on the parts as not really benefiting the destruction of the object.

-
(Assets) Breakable Fence: Fixed the entity refreshing of broken pieces. Material Surface Type changed to normal wood (non-breakable).

##
Refactored

-
Removed average color calculations.

-
Generalized color-model option.

-
Replaced old round-to-nearest-integer code by truncate-towards-zero code.

-
Removed cubemap generation/tagging for any 6x1 texture, now only "cm=1" presets will be cubemaps.

-
Readded Export Occlusion Mesh function into the File menu (CE-1320).

-
Updated music and music logic for SDK Forest level.

##
Tweak

-
AnimObject: Added default wind turbine model, set playing and loop to true by default, tidied structure.

-
AnimObject: Set default model to Windsock instead (windmill too large for a default object).

-
Multi-threaded cube-mipmapper.

-
(Physics) Increased the physics AABB/OBB tree ext box buffer from 32 -> 64.

-
(Savegame) Unified savegame name, now based on IGame::GetName.

-
ProximityTrigger: Set TriggerOnce to false by default. Tidied structure.

-
(Game) takeDamage console command allows passing a damage value (defaults to 100).

-
Renamed Wireframe to "Display Triangulation Result" in the drawing-wireframe radio box.

-
Adjusted the designer epsilon from 1.0e-5 to 1.0e-4.

-
(Game) Set default package 0 if no loadout is set by game/level (CE-1170).

-
Fixed default path on Cloth entity script. Set air_resistance to 1 by default.

-
(Editor) Registry key renamed from Sandbox 3.5 to Sandbox.

-
Changed MusicLogic switch behavior to not play start layers and to switch to current sample pos while ignoring sync points.

-
Makes contiguous resource ids in groups.

-
Added GravitySphere icon and unified all Gravity scripts to use it. Removed duplicate Target icon and repathed scripts which used it. Remove duplicate Light1 icon, nothing used it. Removed duplicate Sound icon, repathed script which used it.

-
Added a class to wrap up some functionality for writing files that was duplicated at multiple spots in the editor. In addition, now it will not prompt the user to check out/overwrite a file if it hasn't changed (it compares the temp version with the original and only writes it if they differ).

-
(RC) Now it's allowed to have only one rc.ini file (in bin32/rc or in bin64/rc) (CE-1835).

-
Removed ErrorDialog CVar from Editor.cfg, no longer needed.

-
Fixed texture paths on avmine.

-
(Assets) Added detailmap to decal_cylinder asset (as per requirement for SilPOM). Increased displacement for fallen_log asset, decreased steps for optimization.

##
New Feature

-
Added HDR i/o.

-
Support for native loading of HDR probes: long/lat, vertical and horizontal cross.

-
Support for: R8, R16, R16F, RGBA16F, R32F.

-
Support for: YCbCr and YFbFr color-spaces.

-
Support non-breaking rope force limit.

-
Support for multi-channel TIFs from Photoshop.

-
Support for: signed BC4 and BC5.

-
Made generation of cubemap diffuse and the preset to be an option in the RC.ini.

-
Optimized refresh of the preview for options which only change the display.

-
Adaptive preview-mode display based on the image's content.

-
One-pass TIF writing, instead of two-pass (was: 1st content, 2nd settings).

-
(Particles) Facing enhancements. New Facing = CameraX mode aligns particle X axis only to camera, and curves lighting in X axis only. Facing now works on geom particles too.

-
Added dialog to preserve the local material name in the 3dsMax material sync tool (CE-1635).

-
(Designer) Added a function to fill a hole based on selected edge elements.

-
(Designer) Added dimension figures axis' to Designer object as default.

-
(Designer) Made dimension figures displayed as push/pull, drawing rectangle/polygon, creating stairs, etc, are being done.

-
Added a way of changing selection combination among vertex, edge and face.

-
(Designer) Enabled to drill multiple selected regions in one time.

-
(Designer) Made selected tool's button highlighted.

-
Added p_max_bone_velocity to limit animation-based velocity estimation.

-
MemReplay tracking for video memory.

-
(Designer) Enabled boolean operation to designer object with mirror mode.

-
Fog volume type dropdown list for the FogVolume entity (CE-1839).
