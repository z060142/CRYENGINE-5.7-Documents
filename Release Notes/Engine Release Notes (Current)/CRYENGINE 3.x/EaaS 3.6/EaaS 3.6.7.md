# EaaS 3.6.7

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/47316993/pages/44963013
- Page ID: 44963013
- Breadcrumb: Engine Release Notes (Current) > CRYENGINE 3.x > EaaS 3.6 > EaaS 3.6.7
- Parent: EaaS 3.6

## Content

Previously there was a mention of removing 64k Mesh Vertex limit and the Snow entity shadow bug fixed, but this was an error and they will appear in 3.6.8.

Released 17th September, 2014.

##
Editor

-
**
New
**
: (FBX) Added source-unit support for FBX import.

-
**
New
**
: (FBX) Added support for unit size conversion.

-
**
New
**
: (Terrain Editor) Loading PGM with optional clipping function.

-
**
New
**
: (Flowgraph) Add userstats node for example GameSDK.

-
**
New
**
: (Flowgraph) Added Actor:LocalPlayerMovementParameter Flownode. Allows controlling of several player movements such as jump height, changeable at run-time (CE-4234).

-
**
New
**
: Added "ed_keepEditorActive" CVar to prevent sandbox (and viewports) from freezing when no focus is set (CE-4290).

-
**
New
**
: Added Editor toolbar buttons for single step physics (step/pause).

-
**
New
**
: Added ToolbarIconSize setting in Sandbox Preferences to allow changing of Toolbar icon size without using ed_ToolbarIconSize CVar (CE-4350).

-
**
New
**
: Improved non-uniform scaling support on brushes with various setups (CE-3918).

-
**
New
**
: CVar ed_ToolbarIconSize can be changed during run-time.

-
**
New
**
: Added link to Documentation portal in Sandbox dashboard/welcome screen.

-
**
New
**
: Added "Photoshop.exe" to the Texture Editor slot in Sandbox Preferences so users don't have to add this in manually.

-
**
New
**
: Additional logging info for some sys CVars on startup (CE-4323).

-
**
Fixed
**
: (FBX) Refactored and added possibility to write manifest file with generic information about geometry scene. The manifest will be used by editor's geometry importer.

-
**
Fixed
**
: (Prefab) Gizmo position not updated, when prefab changed (CE-2388) clone function | pivot has huge offset to group shape (CE-388)

-
**
Fixed
**
: (Flowgraph) Fixed Input:ActionFilter node outputs not firing.

-
**
Fixed
**
: (Mannequin) Fixed middle mouse not working when editing procedural weapon animation offsets (CE-4246).

-
**
Fixed
**
: (AISystem) AI movement request in simulation mode is no longer blocked by a potentially running animation

-
**
Fixed
**
: Crash when ungrouping brushes (CE-4363).

-
**
Fixed
**
: Loading a level with AI/Physics enabled causes you to spawn with a black screen (CE-4229).

-
**
Fixed
**
: InPlaceComboBox (drop-down selector) now uses proper XT colors, rather than hard-coded RGB, looks better with Light and Dark skinning. Fixed menu spelling error.

-
**
Fixed
**
: Possible unlimited recursion in asset resolver.

-
**
Fixed
**
: Data from previously selected group was being assigned to new one (CE-4359).

-
**
Fixed
**
: SplineObjects Follow terrain while move control points with Ctrl key pressed (
CE-4027
).

-
**
Fixed
**
: Console Variables window no longer forced to be on top of all windows, even non-sandbox applications.

-
**
Optimized
**
: Bad sys_game_dll is now treated as fatal (CE-4324).

##
CryDesigner

-
**
New
**
: Added the
[/docs/static/engines/cryengine-3/categories/1114113/pages/18383153](
Cube Editor
)
.

-
**
New
**
: Added the boundary check in the Bevel tool as expanding edges.

-
**
New
**
: Made dimension numbers displayed as 3 digits.

-
**
New
**
: Added a function for merging the selected faces in the existing Merge tool in addition to merging the selected designer objects.

-
**
Fixed
**
: Not being able to select an object after entering AI/Physics Simulation mode.

-
**
Fixed
**
: Made it possible to edit them with the seamless editing as more than two designer object are selected.

-
**
Fixed
**
: Crash caused by exiting the drawing line tool after undoing.

-
**
Fixed
**
: An object which was highlighted in the object mode tool, being kept highlighted after exiting the object mode tool.

-
**
Fixed
**
: Not updating backfaces of faces with a smoothing group.

-
**
Fixed
**
: Designer Objects will have no properties listed in the Rollupbar when selecting them from the Select Objects window after using the "Select None" button in the same window (CE-3437).

-
**
Fixed
**
: Disappearing a previous created designer object after creating a box object (CE-4357).

-
**
Fixed
**
: Drawing a rectangle or a box on a plane which is not parallel with the main axis.

##
Audio

-
**
New:
**
 Switching to loading Audio System Implementations as plugins.

-
**
New:
**
 Added sound obstruction/occlusion capability to the AudioAreaEntity.lua script.

-
**
New
**
: (ACB) Filter the list of controls in the popup selection menu to only the ones available to the currently loaded level

-
**
New
**
: Boids audio support.

-
**
Fixed
**
: (ACB) Load all level controls.

-
**
Fixed
**
: Now properly reloading audio file cache entries upon updating ATL preload requests.

##
Engine

-
**
New
**
: (RC) RC will now show a warning when attempting to run an RCJob-job that doesn't use the same platform as RC thinks should be used.

-
**
New
**
: (RC) (CharacterCompiler) Added support of /vertexpositionformat=exporter and fixed code formatting.

-
**
New
**
: (CryPak) Added cvar sys_pak_loadmodepaks (default 0), controls if the pak files in modes folder are used (CE-4341)

-
**
**
New
**
:
**
(ScriptSystem) Added additional overloaded ScriptAnyValue::CopyTo() method that outputs into a string object.

-
**
New
**
: Added ability to specify Poly/Tris limit for system budget monitoring via sys_budget_numpolys CVar.

-
**
New
**
: Updated to Steamworks 1.30.

-
**
Fixed
**
: (CryPak) Default value of sys_pakloadcache set to 0 (from 1), since we no longer generate level caches (CE-4341).

-
**
Fixed
**
: (CryPak) Path "../../../../foo" was "folded" to non-equivalent "..\..\foo", causing incorrect paths being used when saving level.pak (CE-4322)

-
**
Fixed
**
: (MayaExporter) Changed floating point precision from 'precise' to 'strict' for all Maya versions (this is in addition to a previous changelist, where only Maya 2014 was modified).

-
**
Fixed
**
: (RC Helper) InvokeResourceCompiler() didn't handle absolute paths correctly (CE-4283). Fixes inability to generate Probes in External Game Folders.

-
**
Fixed
**
: (RC Image Compiler) Fixed a copypaste bug in validation code of PVRTC compressor.

-
**
Fixed
**
: (RC) Improved error reporting in loading RC's physics dll.

-
**
Fixed
**
: (CryTIFF) Opening MARI's 4-channel TIFF files in Photoshop produced RGB channels multiplied by alpha channel (because of a bug/issue/feature in TIFF library). Fixed, alpha multiplication is not applied anymore.

-
**
Fixed
**
: (Physics) Preventing having garbage in unused parts of OBBTree node elements.

-
**
Fixed
**
: Exporting VGrid from character editor for 1d and 2d blendspaces is broken (CE-4326).

-
**
Fixed
**
: Exclusive controller falsely set on init.

-
**
Fixed
**
: Fixed typos in Physical error warning (CE-4241).

-
**
Fixed
**
: Crash in IKTorsoAim_Helper because of hard-coded bone names combined with non-defensive coding.

-
**
Fixed
**
: Entities would disappear if Receive Wind option was checked (CE-2524).

-
**
Fixed
**
: Crash bug when deleting skel extension.

-
**
Fixed
**
: Integer overflow with large mesh size differences (CE-4367).

-
**
Optimized
**
: (System) Updated description text for several sys_X CVars to clarify their use (CE-4330).

-
**
Optimized
**
: (Vegetation) Marked Vegetation Sprites CVars as deprecated, use x-tree LOD instead (CE-3938, CE-3045)

##
Rendering

-
**
New
**
: Added debug info text to e_ShadowsCascadesDebug CVar to inform which color represents which cascade (CE-4349).

-
**
Fixed
**
: "Couldn't allocate specular probe texture atlas" error (DirectX10 hardware support). Display correct error message when trying to create a D3D11 renderer on a feature level lower than 11.0 as such levels are no longer supported since the global adoption of BC6 environment probes. (CE-3283).

-
**
Fixed
**
: RenderThread and RenderLoadingThread are accessing the same ID3D11DeviceContext without synchronization (CE-1279).

-
**
Fixed
**
: Don't stream post-process textures. Fixes streaming faults with textures used in the HUD, for example.

##
Particles

-
**
New
**
: Particle editor "Assign to Selected" button now has persistent mode (indicated by highlighted button). Selecting new effect auto-assigns it to selected entities.

-
**
New
**
: Selected effects display bounding boxes of emission volume. Requires editor "Highlight selected geometry" on (CE-3259).

-
**
Fixed
**
: Improved reliability of enabling/disabling effects when editing; disabled effects remain in container list, and order is consistent.

-
**
Fixed
**
: More reliable phys area updates; EventPhysAreaChange now merges old and new area bounding boxes; SPhysEnviron event handler now updates area position synchronously, avoiding 1-frame delay in most cases. SPhysEnviron.GetWorldPhysAreas retains existing SArea objects rather than replacing them, to avoid references to obsolete SAreas.

-
**
Fixed
**
: Changed Params.Color from Color3B to Color3F (no size increase). No longer loses precision due to sRGB/linear conversion saved to 8 bits. Param Alpha scale and AlphaClip.Scale now properly influence min render alpha, geometry and decal alpha.

-
**
Fixed
**
: Static BB computation to account for stretch at time 0, and properly handle focus params. Fixed and enhanced GetEmitFocusDir to also return focus orientation, for particle forces and particle init.

-
**
Fixed
**
: Broken bump-map normals (bad #if placement). Fixed issues with curvature: now affects only lighting normals, not expansion of near geometry (CE-4267).

-
**
Optimized
**
: Manager.Update optimization. Removed some obsolete PS3 code. All emitters can now Update in threads. Fixed invalid asserts.

##
Game

-
**
New
**
: Added CVar "i_lying_item_limit_sp" to control the number of dropped items lying around in singleplayer games, renamed existing CVar "i_lying_item_limit" to "i_lying_item_limit_mp" (CE-4320).

-
**
Fixed
**
: (Audio) Several entities referencing FMOD sound setup which causes failure (CE-4382 / CE-4392).

-
**
Fixed
**
: (Lobby) Make sure DLC is correctly ignored in the lobby from both sides.

-
**
Fixed
**
: (Mannequin) Character T-Posing in MP after vehicle usage.

-
**
Fixed
**
: (AISystem) Changed some script calls into events to not have to rely on behavior variables (CE-4321).

-
**
Fixed
**
: Spawning a vehicle and entering it via FG causes a crash on exiting game mode (CE-4209)

-
**
Fixed
**
: Vehicle system assumes that actors have animated characters (CE-4133)

-
**
Fixed
**
: Boids no surface type error due to character streaming.

-
**
Optimized
**
: Put AutoTester Xml-Reports folder within the User directory, instead of parent of the base directory (../ puts it too high, no prefix puts it inside the GameDLL/GameSDK folder).

##
Assets

-
**
New
**
: (UIActions) Added visible attribute to addImage FG node to make image visible once it's loaded (CE-3793).

-
**
New
**
: (UIActions) Add get-listbox-value node (CE-4378).

-
**
New
**
: (UIActions) Create dialog spinner for waiting times (CE-4178).

-
**
New
**
: (UIActions) User stats for Steam (CE-4128).

-
**
New
**
: (UIActions) Added new Difficulty selection to Singleplayer menu.

-
**
New
**
: Added assault and sniper scope scripts for use with Rifle weapon. Added ironsight_rifle accessory, cut existing ironsight mesh from rifle and referenced new mesh in accessory. Updated rifle fp/tp meshes, moved/added attachment helpers in tp. Updated CDF for fp to reference additional/moved attachment helpers. Fixed proxy missing from material and referencing alternate material in max file. Updated equipment packs to reference new accessories and set initial setups. Delayed shell eject PFX so bullets don't travel through weapon/attachments.

-
**
New
**
: Updated grenade asset material/textures. Added grenade animations. Updated grenade scripts.

-
**
New
**
: Added blurmask textures for weapon scope attachments.

-
**
Fixed
**
: (UIActions) Coordinates for setting Images in Main UI now are positioned with origin point in 0/0.

-
**
Fixed
**
: (UIActions) Re-implement loading screen for loading levels in menu (CE-4184).

-
**
Fixed
**
: Pistol hammer not returning to correct position (CE-3596).

-
**
Fixed
**
: Some material sub_mat id's were set to not allow layer activation.

-
**
Fixed
**
: Updated forest_sky_dome material to reduce artifacts.

-
**
Fixed
**
: Changed virtual voice setting to kill voice - was set to continue, so every tail would stack up when firing inside and play when you would enter an outside area.

-
**
Fixed
**
: Fixed warning due to virtual voice setting on sound seed air.

-
**
Fixed
**
: Created flowgraph logic to trigger state changes in Wwise.

-
**
Fixed
**
: Updated tractor asset material, enabled 2-sided on materials that needed it (CE-4236) and tweaked textures.

-
**
Fixed
**
: Bad proxy setup from GateHouse asset. Removed unnecessary duplicate proxy setup.

-
**
Fixed
**
: LOD issues with Ruin assets. Added/optimized proxies. Fixed numerous gaps in Ruin mesh due to tessellation. Added mesh variations from Max scene.

-
**
Fixed
**
: Filled in terrain holes on Forest to prevent LOD glitch in Launcher (CE-4285).

-
**
Optimized:
**
 (Audio) Over 200 various Wwise audio asset changes.

-
**
Optimized:
**
 (ActionMaps) Removed unused MP radio commands. Removed commented out use functions. Re-added toggle_explosive/special actions for special weapon selection. Moved quick-throw grenades to player_mp actionmap. Readded zoom_toggle action for scope use. Cleaned out alternative controller maps with invalid setups. Increased version number.

-
**
Optimized
**
: (UIActions) Using ListboxValue instead of ListboxCaption for level loading

-
**
Optimized
**
: (UIActions) Remove auto search link (CE-4180).

-
**
Optimized
**
: Updated flash_light asset, set current mesh to be LOD1, refined silhouette for LOD0. Tweaked Detailmap settings.

-
**
Optimized
**
: Re-exported and renamed Silencer assets. Cleaned up Max scene. Created LOD for TP mesh.

-
**
Optimized
**
: Updated silencer helper positions and re-exported. Renamed attachment helper names for consistency. Added support for Silencer on pistol. Removed unnecessary accessory content from Pistol.

-
**
Optimized:
**
 Forest: Moved speedboat content into Mission layer as AB3 layers are streamed in after mission starts. Tweaked TOD settings. Set speedboat driver to use interruptible MBT (CE-4353) and set to Red CDF version.

-
**
Optimized:
**
 Fixed door positions and useMessage strings in Forest (CE-4237).

-
**
Optimized:
**
 Disabled xtrees again in Airfield (CE-4315).

-
**
Optimized:
**
 Updated palm tree materials and textures. Updated cliff_bush materials. Deleted unused textures.

-
**
Optimized:
**
 Updated blood sprite textures with 1024px versions to improve aliasing quality (CE-4343).
