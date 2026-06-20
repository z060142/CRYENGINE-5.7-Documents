# EaaS 3.8.4

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/47316993/pages/44962933
- Page ID: 44962933
- Breadcrumb: Engine Release Notes (Current) > CRYENGINE 3.x > EaaS 3.8 > EaaS 3.8.4
- Parent: EaaS 3.8

## Child Pages

- [Important 3.8.4 EaaS Code and Data Changes](EaaS 3.8.4/Important 3.8.4 EaaS Code and Data Changes.md)

## Content

##
Overview

##
Release Highlights

##
Heightmap-Based Ambient Occlusion

With the new
[/docs/static/engines/cryengine-3/categories/1114113/pages/21890652](
Heightmap-Based Ambient Occlusion
)
 (Height Map AO), CRYENGINE 3.8.4 introduces a highly efficient option to obtain large-scale ambient occlusion in outdoor environments without the need for any prebaking. In combination with Screen Space Directional Occlusion (SSDO), the Heightmap AO provides additional shading cues to improve the depth perception of a scene. The focus of the technique is on high performance and to make it suitable for Virtual Reality (VR) and consoles (approximately 0.3 ms on PC).

[Image: /docs/static/attachments/44962941]

##
New Rendering Pipeline Profiler

3.8.4 introduces a new unified rendering pipeline profiler, that provides information from various iterations of our previous internal profiling tools in a better and cleaner interface. The profiler can be enabled with
**
r_profiler 1.
**

**
[Image: /docs/static/attachments/44962940]

**

##
Code Interface Changes

See the
[/docs/static/engines/cryengine-5/categories/47316993/pages/44962942](
Important 3.8.4 Code and Data Changes
)
 article for more information

##
Editor

##
Editor General

-
**
New
**
: (FBX Exporter). Added support for vertex colors and normals.

-
**
New
**
: (FlowGraph) Vehicle. FG nodes to control and select seat views.

-
**
Refactored
**
: Sandbox PRT dependency is now compiled through WAF module.

-
**
Optimized
**
: Allow 0-radius ropes for special purposes.

-
**
Fixed
**
: (FBX Export) Vertex Color export. Swap back Red and Blue components (was swapped in render mesh).

-
**
Fixed
**
: Make sure inputs are forwarded properly when using AI/Physics mode before Game Mode.

-
**
Fixed
**
: Warn if launching Game Mode when multiplayer rules are active and no spawn points exist.

-
**
Fixed
**
: For Unlink tool in Sandbox - moves content of prefabs.

-
**
Fixed
**
: Where PropertyItem control wouldn't recognize a forced modified flag.

-
**
Fixed
**
: Smart file open dialog - now returns game paths formatted like the normal 'custom' file open dialog does (compare with CCustomFileDialog::GetFilePath()).

-
**
Fixed
**
: For Transformation is corrupted while linking prefab to entity.

-
**
Fixed
**
: Fix for Linked prefabs are badly exported.

-
**
Fixed
**
: Possible crash and memory leak in CBreakpointsTreeCtrl.

-
**
Fixed
**
: Aligning prefab to grid - will no longer align internal objects.

-
**
Tweaked
**
: Don't force update for child objects visibility flag in a parent-child relationship.

-
**
Tweaked
**
: AI NavMesh operation "Request full MNM rebuild" - now keeps rebuilding regardless of what "Continuous Update" is set to.

##
Designer Tool

[Image: /docs/static/attachments/44962939]

**
Extrude Multiple
**

-
**
New
**
: ExtrudeMultiple tool has been added.
[/docs/static/engines/cryengine-3/categories/1114113/pages/21890915](
Manual
)

-
**
Refactored
**
: HeightManipulator.

-
**
Refactored
**
: ConeTool codes have been refactored by reusing CylinderTool codes.

-
**
Refactored
**
: Renamed xxxDesignerEventxxx to xxxDesignerNotifyxxx.

-
**
Fixed
**
: Added a predicator for comparing two const char* strings to template parameter list of uiFactor class.

-
**
Fixed
**
: Crash bug when entering and leaving clipvolume - has been fixed by a removed Designer Editor pointer variable in MainPanel and SubPanel. Now uses the global pointer.

-
**
Fixed
**
: Broken polygons - caused as polylines are drawn on a non planar polygon.

-
**
Fixed
**
: The unchecked cast shadow flag bug by default.

-
**
Fixed
**
: Moving a pivot back after transforming a gizmo and leaving the pivot tool.

-
**
Fixed
**
: Broken Viewport - after switching Viewport to orthognal view using a pop up menu and then back to perspective.

-
**
Fixed
**
: Only position ResetXForm bug.

-
**
Fixed
**
: Bug caused by moving Elements(vertices/edges/faces) in Mirrror mode.

-
**
Fixed
**
: Not being able to pick a vertex.

-
**
Tweaked
**
: A panel for the Extrude Tool has been added to include options for scaling and leaving loop edges. Help messages also added.

-
**
Tweaked
**
: Applied Offset Manipulator to Extrude Tool.

-
**
Tweaked
**
: OffsetManipulator has been implemented for the Offset Tool.

-
**
Tweaked
**
: Customized PivotPanel of Pivot Tool has been replaced with PropertyTreePanel.

-
**
Tweaked
**
: Z-dimensional axis number color has been made brighter and is now easier to read.

-
**
Tweaked
**
: Exclusive mode camera name has been chaged from "Crydesigner Camera" to "Exclusive Mode Camera".

##
UV Mapping Editor

[Image: /docs/static/attachments/44962938]

**
Smart Sew
**

-
**
New
**
: SmartSew has been added.
[/docs](
Manual
)

-
**
New
**
: LoopSelection has been added.
[/docs](
Manual
)

-
**
Fixed
**
: Crash bug caused on Windows 8.1/10 when unwrapping polygons to UV Mapping Editor.

-
**
Fixed
**
: Crash bug when loading another level while keeping UV Mapping Editor open.

-
**
Fixed
**
: Crash bug with UV Mapping Editor open when creating a new level.

-
**
Tweaked
**
: Moved unwrapping methods from UV Mapping Tool to UV Mapping Editor.

-
**
Tweaked
**
: Enabled automatic cleaning of unused unwrapped polygons.

-
**
Tweaked
**
: F5 shortcut added to clean unused UV polygons.

-
**
Tweaked
**
: Rotation Snapping improved to make detecting mouse rotation more accurate.

-
**
Tweaked
**
: Plane Unwrapping improved so that ratio to original width and height is kept.

##
Trackview

-
**
New
**
: Trackviews key properties window - now able to display Pos and Rot key frame values correctly.

-
**
Fixed
**
: "Disable Player" and "Non-Skippable" cutscene options.

-
**
Fixed
**
: Child entities stay permanently hidden when scrubbing past the visibility track.

-
**
Fixed
**
: It is not possible to manually set a value in the trackview key properties to the same value that had previously been typed in.

-
**
Fixed
**
: Start and Stop markers are ignored after using level save.

##
Renderer

##
Renderer General

-
**
New
**
: Unified rendering pipeline profiler with enhanced accumulated stats (new CVar r_profiler which replaces r_artProfile, r_stats 15-17 and r_showmt).

-
**
New
**
: Dynamic distance shadows.

-
**
New
**
: Supersampling support in Game Launcher.

-
**
New
**
: Temporal AA is now working with dual stereo rendering and VR.

-
**
New
**
: Emittance map has a custom slot and a gamma parameter to allow increases in the range.

-
**
New
**
: Intensity of emissive materials is now specified using kilonits (kcd/m2) and the material emissive color gets applied.

-
**
Refactored
**
: Separated 3 resolution values according to the different rendering phases and modes (rendering resolution for 3D, native resolution for upscaling/downscaling and native ui, backbuffer resolution for multiple views such as the stereo combined view).

-
**
Fixed
**
: Behavior of r_ShadowGenDepthClip.

-
**
Fixed
**
: GPU and render CPU times appear under-reported.

-
**
Fixed
**
: Enumerate just GPU's supporting feature level 11.0 and above.

-
**
Fixed
**
: Fonts are now rendered in the correct position and with native resolution instead of rendering resolution.

-
**
Fixed
**
: Ensure light matrix is orthonormal (when light is attached to an object with scaling).

-
**
Fixed
**
: Alpha testing not working in forward passes.

-
**
Fixed
**
: Debug views showing up in secondary Viewports.

-
**
Fixed
**
: SS Reflection flickering when secondary Viewport is open.

-
**
Fixed
**
: Restored depth stencil view during rendering to the native target (fixes Scaleform masks not working in main menu).

-
**
Fixed
**
: Behavior of 'No Shadow' material flag on characters, ropes and roads.

-
**
Fixed
**
: BGR swapping when using RGB textures.

-
**
Fixed
**
: Show error message and exit gracefully when launching the Editor on a system without a compliant GPU.

-
**
Fixed
**
: Improved vegetation shading - fixed shading discontinuities and overly strong specular gain on foliage planes.

-
**
Tweaked
**
: Check GPU in Editor and do not allow app to start if no suitable GPU is found.

-
**
Tweaked
**
: Show more accurate error message when non-supported GPU is detected.

-
**
Tweaked
**
: Added hint for graphics drivers to prefer high performance devices in case no app profile exists.

-
**
Tweaked
**
: Added TAA pattern with 3 samples.

-
**
Tweaked
**
: Stereo device is set by default to none - to save memory.

-
**
Tweaked
**
: Decal opacity map now uses untransformed texture coordinates.

##
SVOGI

-
**
New:
**
Screen space depth tracing may be optionally integrated into voxel tracing code, allowing some occlusion from non voxelized geometry.

-
**
New:
**
Sun injection in modes 1-2 (usually based on voxel tracing only) can be supplemented by RSM allowing more precise injection.

-
**
New:
**
Added new LowSpec mode - new LowSpec mode 1 is between the old modes 0 and 1 that permits a good balance between quality and speed.

-
**
Fixed:
**
Crash on unload in the Launcher.

##
Volumetric Fog

-
**
New
**
: Support for sun radial scattering.
**

**

-
**
New
**
: Added Flow Node inputs to FogVolume - permits easier setting of the values of the entity.

-
**
Fixed:
**
 Banding artifact when extinction parameter is very high and global density is very low.

-
**
Tweaked
**
: Acceptable range and effect of FogVolume parameters.

##
OpenGL

-
**
New
**
: Added a flag to exclude the version string - useful for driver bug workarounds.

-
**
New
**
: Added missing UMIN and UMAX.

-
**
Fixed
**
: Workaround for AMD driver bug (#version 440 breaks std140 layout).

-
**
Fixed
**
: MOV types.

-
**
Fixed
**
: Correct implementation of SWAPC.

-
**
Fixed
**
: Support shader pipeline combinations with shader resource slots that do not fit into the default fixed mapping.

-
**
Tweaked
**
: Removed unused constant buffer slot merge and streaming constant buffer sorting modes - cleaned up streaming constant buffer code.

-
**
Tweaked
**
: Unification and refactoring of resource mappings (DX per stage slots -> GL global units).

##
Engine

##
Common

-
**
New
**
: Improvements to the Diag33_tpl class template - cleanup and implementation of missing operators.

-
**
Fixed
**
: Yasli issues related to error/warning messages and icons not appearing in property trees.

-
**
Fixed
**
: Detect Windows 8.1/10 correctly during startup.

-
**
Fixed:
**
 Release compilation failed when compiling via vc140.

-
**
Tweaked
**
: Change of the scaling component in the QuatTNS_tpl class template from Vec3_tpl to Diag33_tpl.

##
Physics

-
**
New
**
: Support non-collidable subdivided ropes.

-
**
New
**
: Circumvent 16bit index limitation for phys meshes with shared indices.

-
**
New
**
: Support per-constraint solver hardness.

-
**
Fixed
**
: Removed energy loss for animated ragdolls.

-
**
Fixed
**
: Potential floating point exception in rigidbody solver.

-
**
Fixed
**
: Fixed sphere proxies not generating water splashes.

-
**
Fixed
**
: Floating point exception in ropes with 0 radius.

##
System

-
**
Refactored
**
: Added wildcard support for sys_filesystemCaseSensitivity.

-
**
Fixed
**
: Files do not get loaded if sys_filesystemCaseSensitivity is set to 2 and they generate an error.

-
**
Fixed
**
: Save error screenshots as JPEG.

-
**
Fixed
**
: RemoteConsole closing invalid socket.

-
**
Fixed
**
: Splash screen - is now rendered with the correct scaling and on the current render target.

-
**
Fixed
**
: RT_Draw2dImageInternal - now uses the current Viewport for layout rather than the 3D rendering resolution.

-
**
Tweaked
**
: Improved log messages caused by sys_filesystemCaseSensitivity.

##
WAF

-
**
New
**
: Export binary output location to <root>/build.settings.

-
**
New
**
: New "module_provides" wscript entry. Allows a module to export entries to module depending on the module via "use_module".

-
**
New
**
: Modules can specify extra settings for module users.

-
**
New
**
: Output performance and release build into their own folders.

-
**
New
**
: Copy RC to all configuration folders i.e. after release RC has built it should be available in the debug/profile and in the performance and release folders.

-
**
New
**
: Reconfigure WAF if changes have been noticed in user_settings.options file.

-
**
New
**
: Strip out options in user_settings.options that are no longer part of the default_settings.options.

-
**
New
**
: Updated WAF support for VS2013 and VS2015.

-
**
Fixed
**
: Support special characters in path when detecting MSVC.

-
**
Fixed
**
: Recode support is enabled even if no license key is present.

-
**
Fixed
**
: Automatically create missing Incredibuild registry keys.

-
**
Tweaked
**
: "use" and "use_module" - directives are now no longer ignored if another dependency also includes the same library (unless the dependency is a static library).

##
3rdParty

-
**
Refactored
**
: Alembic compilation from WAF instead of precompiled libraries.

-
**
Refactored
**
: LibTomCrypt and LibTomMath are now compiled through the WAF module so that the correct compiler is always used.

-
**
Refactored
**
: Linking of Scaleform has been made more flexible (more information moved into WAF, away from C++) and can now pick MSVC version.

-
**
Fixed
**
: Always expose Scaleform video volume CVar.

##
3D Engine

-
**
New
**
: Exposed CVar - for game to specify cursor (r_MouseCursorTexture).

-
**
Refactored
**
: (VR) removed eye depth buffer now redundant.

-
**
Fixed
**
: Recompute rope's bbox when leaving Game Mode (for visibility).

##
Particles

-
**
Fixed
**
: Incorrect miplevel calculation for particle decals with texture tiling.

-
**
Fixed
**
: FPE when particle decal size is too small.

##
RC/Tools

##
Tools General

-
**
New
**
: Export more than 100 morph targets from 3dsMax when using linked morph nodes.

-
**
New
**
: Export 8 bone weights per vertex from 3dsMax.

-
**
Refactored
**
:
**

**
SettingsMgr.exe: removed button [Scan for builds].

##
Resource Compiler

-
**
Tweaked
**
: Moved RC binaries to Tools/rc folder.

##
Animation

##
Animation General

-
**
New:
**
Added technical documentation.
[/docs/static/engines/cryengine-3/categories/1638401/pages/21890231](
Time in CryAnimation
)
.

-
**
New:
**
All character instances are now processed asynchronously, including attached character instances - previously whenever a character instance had attached character instances it would execute those in the main thread. This includes a major refactor of the way we process characters.

-
**
New
**
: (Experimental). Added basic support for uniform joint scaling on ANM files playing on CGA. Use the console variable
`
ca_UseScaling
`
 to toggle scaling support in the animation system.

-
**
Fixed
**
: Auxiliary debug rendering through
`
g_pAuxGeom
`
 is now thread safe - replaced calls to
`
IRenderer->Draw2DLabel
`
 to calls on
`
g_pAuxGeom
`
 to make them thread safe too.

-
**
Fixed
**
: Character physics didn't go to 'sleep' - caused by
`
CSkeletonAnim::m_isAnimPlaying
`
 staying at 1 (even though no animation was playing).

-
**
Fixed
**
: Crash when assets in blend spaces become invalid (e.g. when underlying animation set changed).
**

**

-
**
Tweaked
**
: Added header documentation to
`
ISkeletonPose::GetAbs/RelJointByID
`
.

##
Character Tool

-
**
New
**
: Added the ability to create new animation events file (from within the properties panel of chrparams files) when no animation events file is specified:

[Image: /docs/static/attachments/44962937]

-
**
New
**
: Added display of the included animation events file (the animation events file that is specified in an included chrparams file), if any.

[Image: /docs/static/attachments/44962936]

-
**
Fixed
**
: Time not being synchronized between compressed & uncompressed view.

-
**
Fixed
**
: Double appearance of the 'Missing attachment name' warning.

-
**
Fixed
**
: The next/prev frame keys (',' and '.').

-
**
Fixed
**
: The 'frames' playback mode - a side effect is that the resolution of the time used when editing animation events is increased; this might introduce slight changes in time when re-saving).

[Image: /docs/static/attachments/44962935]

-
**
Fixed:
**
 the display of certain top-level warnings/errors.

-
**
Fixed:
**
 The display of the warning/error icons on closed branches in the property tree.

[Image: /docs/static/attachments/44962934]

-
**
Tweaked
**
: Added and improved many tooltips and warnings (mostly related to the properties within chrparams).

##
Mannequin

-
**
Fixed
**
: Crashes because IAction::UpdatePending was called when the action has no rootscope - this happened in a corner case where all the scopes that the action was running on used an inactive scopecontext (for example when the game calls ClearScopeContext on those scopecontexts). Fixed by not calling UpdatePending unless there is a valid active rootscope.

-
**
Fixed
**
: Issues where the currently selected item was deselected.

##
Facial Editor

-
**
Fixed
**
: Crash when browsing a facial library without opening a character.

##
Action

##
Action General

-
**
New
**
: Reload action maps during Editor runtime.

-
**
Refactored
**
: General Input:Flownode.

-
**
Fixed
**
: PropertySet flow node would not reset it's changes in the Editor on Game Mode exit.

-
**
Fixed
**
: ActionMapManager notifies listener about newly initialized action maps.

-
**
Fixed
**
: ControllerLayouts are not getting initialized correctly.

-
**
Fixed
**
: "i_listActionMaps" display problems.

-
**
Fixed
**
: Saving a game from the game menu - will now also work when not in dev-mode.

-
**
Tweaked
**
: Expose new action map functionality to scriptbinds.

-
**
Tweaked
**
: Increased v_draw_components font size to make it more readable - added semi-transparency and solid rendering to make sense of the bboxes.

-
**
Tweaked
**
: Action maps are now disabled (by default) after creation (only exception is "default" action map which is always activated)

##
Flowgraph

-
**
New
**
: Flownode Game:LockPlayerRotation.

-
**
New
**
: Added node "Physics:GetPhysId" to get phys id from entity id.

-
**
New
**
: Support two points in constraint flownode.

-
**
Fixed
**
: Prevent crash when triggering an event from itself.

-
**
Fixed
**
: "Featuretests:SimulateInput" node (walk dir is back to front).

-
**
Fixed
**
: Issues with CameraProxy node.

-
**
Fixed
**
: Issues with collision flownode.

-
**
Fixed
**
: Do not allow invalid characters in module port names.

-
**
Tweaked
**
: Moved "Helicopter" nodes to inside the "Vehicle" category.

##
Audio

##
Audio General

-
**
Fixed
**
: Ambience type loops of a level kept playing after switching to another level.

-
**
Fixed
**
: Crash in CFlowNode_AudioTrigger::OnAudioTriggerFinished() when a callback referenced an invalid FlowGraph node.

-
**
Fixed
**
: Enabled particles to also propagate rotation information to audio proxies.

-
**
Fixed
**
: AudioProxy offset was not initialized.

-
**
Tweaked
**
: Particle effects now have audio obstruction and occlusion calculations turned off by default. Introduced a new property to set that per particle effect.

-
**
Tweaked
**
: Numerous fixes suggested by cppcheck.

-
**
Tweaked
**
: Updated to Wwise v2015.1.1 build 5434.

-
**
Tweaked
**
: Add Virtualized/Physicalized states for playing events.

-
**
Tweaked
**
: Add Wwise version build number to info debug header.

-
**
Tweaked
**
: Audio Area Ambience now drives a global RTPC when the listener enters the area.

##
ACE (Audio Controls Editor)

-
**
Fixed
**
: Add connection to the right group when connecting soundbanks to preloads.

-
**
Tweaked
**
: Fix for issues highlighted by cppcheck.

##
AI System

-
**
Refactored
**
: MeshGrid: Memory management for Tiles wrapped by separate class to track issues more centrally.

-
**
Fixed
**
: Some AI scripts were still trying to access the removed global AICharacter script table.

-
**
Tweaked
**
: MeshGrid::TileContainerArray: using #ifdefs to control the level of assert() failures.

##
Game

-
**
New
**
: Add the ability to repair vehicles by shooting vehicle with a weapon that has the "repair" hit_type. Will deal negative damage to vehicle.

-
**
New
**
: Make the 10cm min distance between points in a ShapeObject an optional feature (decided by GameVolumes).

-
**
Refactored
**
: Remove ILevel (a wrapper for ILevelInfo), instead ILevelInfo should be used directly.

-
**
Fixed
**
: Detach hands from camera rotation when on a ladder.

-
**
Fixed
**
: Disable screen effects when switching to a camera other than the client actor camera.

-
**
Fixed
**
: Reflect changes in character attachment ids in bodydamage code.

-
**
Fixed
**
: Do not allow switching between 1st person and 3rd person camera while using a ladder.

-
**
Fixed
**
: Ladders can now be used in third person mode when standing still in front of them.

-
**
Fixed
**
: Enable or disable the player's aim IK depending on the current camera mode on respawn.

-
**
Fixed
**
: GameActions will be notified when they are invalidated.

-
**
Fixed
**
: Ladder property "UseThirdPersonCamera".

-
**
Fixed
**
: ShapeObjects - now properly call the EntityObject's PostLoad so that Flowgraph and EntityLinks are properly loaded from them (required for GameVolumes to be able to have these features).

-
**
Fixed
**
: Added CVar to control disabling of Windows keys.

-
**
Tweaked
**
: Simplified GameZero InputExtension.
[#release-highlights](
Release Highlights
)
[#code-interface-changes](
Code Interface Changes
)
[#editor](
Editor
)
[#renderer](
Renderer
)
[#engine](
Engine
)
[#3d-engine](
3D Engine
)
[#particles](
Particles
)
[#rctools](
RC/Tools
)
[#animation](
Animation
)
[#action](
Action
)
[#audio](
Audio
)
[#ai-system](
AI System
)
[#game](
Game
)
