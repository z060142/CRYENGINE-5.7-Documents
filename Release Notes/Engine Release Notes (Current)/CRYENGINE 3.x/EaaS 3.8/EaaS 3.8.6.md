# EaaS 3.8.6

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/47316993/pages/44962944
- Page ID: 44962944
- Breadcrumb: Engine Release Notes (Current) > CRYENGINE 3.x > EaaS 3.8 > EaaS 3.8.6
- Parent: EaaS 3.8

## Content

##
Release Highlights

##
NoMaps

![Image](https://www.cryengine.com/docs/static/attachments/44962945)

NoMaps is a standalone tool created by Crytek to achieve high quality tangent-space normal maps for CRYENGINE. In the past when people tried to create tangent-space normal maps for our ENGINE they had to use software which assumed how our renderer accomplished tangent-space. The problem was that no software would know how exactly CRYENGINE rendered tangent-space, hence normal maps were never guaranteed to be completely accurate - or stay compatible between ENGINE revisions/versions. Now with NoMaps Crytek offers a standalone tool which produces tangent-space normal maps directly for CRYENGINE. This software takes the object and its matching object-space normal map and then converts it into a tangent-space normal map that fits its mesh perfectly. In this way NoMaps helps in achieving high quality assets for CRYENGINE, while simplifying previous workflows (only an object-space normal map is required).

##
Oculus 0.8 SDK + Touch Controllers support

CRYENGINE 3.8.6 comes with support for Oculus 0.8.0.0-beta SDK and Oculus Touch Controllers. However, in order to make use of these features you will need to install the
[Oculus 0.8.0.0-beta Runtime for Windows](https://developer.oculus.com/downloads/pc/0.8.0.0-beta/Oculus_Runtime_for_Windows/)
 and install the GPU drivers that are recommended by Oculus.

##
Editor

##
Editor General

-
**
Fixed
**
: Navigation areas did not update their navmesh when moved.

-
**
Fixed
**
: Water volumes did not update their newly assigned material.

-
**
Fixed
**
: Water volumes did not update their content upon being moved.

-
**
Fixed
**
: AreaSystem - Area shapes are now allowed to be created from 2 points only.

-
**
Fixed
**
: AreaSystem - Preventive fix to ensure successful AreaShape serialization if there is a mismatch between a number of local points and Audio Obstruction points.

-
**
Fixed
**
: AreaSystem - The Area Proxy was not updating correctly during a clone operation.

-
**
Fixed
**
: AreaSolid - "Filled" parameter is now available.

-
**
Fixed
**
: AreaSolid - Leaking sound from a thin gap in AreaSolid.

-
**
Fixed
**
: Embedded LOD vs. loose LOD loading in the LOD-generator.

-
**
Fixed
**
: Inverse tangent-frame generation in the LOD-generator.

-
**
Fixed
**
: Crash on material check-out in the Editor.

-
**
Fixed
**
: G-buffer debug views not resetting properly.

-
**
Fixed
**
: AreaProxies - No longer being created on objects derived from CShapeObject that are not closed (this has fixed for e.g. instance ledges that do not need an AreaProxy to be created (caused by not properly initialized AreaProxies)).

-
**
Fixed
**
: GameVolumes - GameVolumes that were turned into prefabs did not properly initialize their area proxies.

-
**
Tweaked
**
: AreaSolid - Material (s) used on an AreaSolid Entity have been modified so that they are no longer sensitive to light.

-
**
Tweaked
**
: Layer settings dialog - Renamed some checkboxes, now gives better clarification of what the checkbox does.

-
**
Tweaked
**
: RollupBar property items without a valid limit - No longer creates a slider control.

##
Designer Tool

-
**
New
**
: Extrude Edge has been added.

-
**
New
**
: Multiple Offset has been implemented.

-
**
Fixed
**
: Abrupt movement of selected elements when they are moved by dragging a movement Gizmo (when its center is pushed).

-
**
Fixed
**
: Broken smoothing groups - After editing UV mapping.

-
**
Fixed
**
: Losing smoothing groups of polygons when they are selected in the UV mapping tool.

-
**
Fixed
**
: Losing UV mapping and smoothing group data after confirming a mirror mode.

-
**
Fixed
**
: Losing polygons spanning a mirror plane after confirming a mirror mode.

-
**
Fixed
**
: Applied non-uniform scale to each polygon of a designer object (avoids unexpected deformation, so the non-uniform scale isn't accumulated to the world transform of an object).

-
**
Fixed
**
: Added a function so that isolated areas are separated from UV islands.

-
**
Fixed
**
: SmartSew - Bug re. SmartSew mirrored islands welding the wrong UV's.

-
**
Fixed
**
: Primitive creation tools - Not exiting when ESC is pressed (after the primitive shape has been created).

-
**
Fixed
**
: Bug re. Gizmo display - Where multiple designer objects were being selected.

-
**
Tweaked
**
: Lathe tool - Magnet tool has been removed (makes the Lathe tool much easier to use).

-
**
Tweaked
**
: Dimension numbers as displayed on the axis arrows have been made brighter and the color of the blue dimension arrow has been made darker.

-
**
Tweaked
**
: Functions regarding displaying vertices/edges have been separated to Display.h/cpp.

-
**
Tweaked
**
: LoopPolygons - LoopPolygons class has been introduced to manage loops created from a polygon.

-
**
Tweaked
**
: A way of repeating prev action in Offset and Extrude - Changed from LMB double click to ALT + LMB.

##
Trackview

-
**
Fixed
**
: Copying linked objects of a Trackview sequence - Sets the parent to base position.

-
**
Fixed
**
: GoTo track - Wasn't firing in direct Trackview playback.

-
**
Fixed
**
: Trackview - Not correctly reset after leaving Gamemode.

-
**
Fixed
**
: Selecting a keyframe - Will crash the Editor when floating point exceptions are enabled.

-
**
Tweaked
**
: Added scale keys to use the improved key properties display window.

##
Renderer

##
Renderer General

-
**
Fixed
**
: Env probe lighting on Hair shader.

-
**
Fixed
**
: Can't run the Renderer with sys_float_exceptions=1.

-
**
Fixed
**
: 8-weight GPU skinning in shader (was using previous frame data when there was no previous frame).

-
**
Fixed
**
: "Filled" parameter of Clip Volume Object is now available.

-
**
Fixed
**
: Default maps for texture slots (fixes decals looking different in Release).

-
**
Fixed
**
: Improved angle based fadeout for deferred decals.

##
Shadows

-
**
Fixed
**
: Out of bounds access when only per object shadows are rendered.

-
**
Fixed
**
: Count empty nodes as well when performing time sliced traversal of octree for static shadow casters.

##
SVOGI

-
**
Fixed
**
: Clouds shadow support.

-
**
Fixed
**
: Specular on forward shaded materials such as hair.

-
**
Fixed
**
: Voxels were not updated on very low specs.

-
**
Fixed
**
: Specular on eye and hair shaders.

-
**
Fixed
**
: Improved screen space depth tracing.

-
**
Fixed
**
: Broken SVOGI shader on next Level load.

-
**
Fixed
**
: Missing meshes in voxelization (if they were not streamed in).

-
**
Fixed
**
: Material leaks - Added support for "_NTI" lights.

-
**
Fixed
**
: Potential crash on Level unload.

-
**
Fixed
**
: Reduced flickering in scenes with high frequency details.

-
**
Fixed
**
: Post fix for flickering reduction in scenes with high frequency details.

-
**
Fixed
**
: Crash on material check-out; Fixed false occlusion from clip volumes; added 2 new parameters.

##
Volumetric Fog

-
**
Fixed
**
: Shader compilation error when r_VolumetricFogSample is set to 2.

-
**
Fixed
**
: Banding artifact appears in very dark environment when r_HDREyeAdaptationMode is set to 1.

##
Engine

##
Engine General

-
**
New
**
: IHmdController - Refactored interface to generalize it for other controller vendors.

-
**
New
**
: Added SDL2 as a dependency in the compilation step for Linux.

-
**
Fixed
**
: On UDP error, log error before closing socket.

-
**
Fixed
**
: Added the assert term window to the Linux WAF compilation scripts.

-
**
Fixed
**
: Suppress keyboard events for the duration of IME composition.

-
**
Fixed
**
: LOD Baker, broken material located in the EngineAssets folder (after applying a LOD) has been solved.

##
Common

-
**
Fixed
**
: Heap corruption - Caused by CryStackString's move (and by extension, swap) members.

##
Physics

-
**
Fixed
**
: Restored the original explosion occlusion code.

-
**
Fixed
**
: Never disable line collisions for ropes with environment collisions.

-
**
Fixed
**
: Capsule-sphere un-projection issue.

-
**
Fixed
**
: Issue with "ground plane" on boolean breakables.

-
**
Fixed
**
: Check for empty ragdoll during net sync.

-
**
Fixed
**
: Cleaned up pGeomProxy refcounting.

-
**
Fixed
**
: Issue in CapBodyVel for vehicles.

##
System

-
**
New
**
: Indicate if profiling (CVar profile) is paused and if SCROLL_LOCK is active.

-
**
Fixed
**
: Crash at shutdown when touch controllers are not supported for the selected VR HMD.

-
**
Fixed
**
: Allow periods for screenshot console command to specify format, default to JPEG.

-
**
Tweaked
**
: Improved code that handles the sys_filesystemCaseSensitivity CVar.

##
WAF

-
**
New
**
: Specify force shared modules for monolithic builds.

##
3D Engine

-
**
Refactored
**
: Added occlusion culling camera validation.

-
**
Fixed
**
: Merged meshes update very slow.

##
Particles

-
**
Fixed
**
: Parent particles were never de-allocated, thus exhausting particle pool (timing bug).

##
RC/Tools

##
Tools General

-
**
New
**
: Added wrinkle map preset to rc.ini.

-
**
Fixed
**
: Added missing file existence check (led to crashes during uninstall).

-
**
Fixed
**
: CryToolsInstaller - Used wrong folder name for Maya patching/settings (Note: it seems that Autodesk has removed suffix x64 in paths starting from Maya 2016).

##
Animation

##
Character Tool

-
**
Fixed
**
: AnimEventPlayer - Empty AnimEventPlayer class returned true in its Play method even though it didn't play anything. This caused the CharacterTool to stop playing Audio Events.

-
**
Fixed
**
: Audio triggers not following the bone they were assigned to.

##
Action

##
Action General

-
**
Fixed
**
: Crash after calling #System.RemoveEntity in Sandbox.

-
**
Fixed
**
: Forcefeedback - Wasn't working in Launcher.

##
Flowgraph

-
**
New
**
: Game:LockPlayer node.

-
**
Fixed
**
: Correct parameter list in Flowgraph for material parameter selection.

-
**
Tweaked
**
: Deprecate Game:LockPlayerRotation node.

##
Audio

##
Audio General

-
**
Fixed
**
: Setting the current environments on Audio Objects (on spawn) did not work as expected.

-
**
Fixed
**
: AudioTriggerSpots - Did not update the new bTriggerAreasOnMove property correctly.

-
**
Fixed
**
: Audio functionality on areas - Broke when an area property changed. Code unification, numerous bug fixes and performance improvements to the area system.

-
**
Fixed
**
: Fallback to NULL implementation did not work.

-
**
Fixed
**
: Projectile whiz and ricochet sounds not working with ATL.

-
**
Fixed
**
: When entering Gamemode in the Editor particles on hidden layers regained Audio functionality - This is now prevented so Audio remains off.

-
**
Fixed
**
: AudioPreload - Flowgraph nodes not unloading when leaving Gamemode.

-
**
Tweaked
**
: Updated to Wwise v2015.1.4 build 5497.

-
**
Tweaked
**
: Report type callbacks for Audio standalone files now also carry over formerly passed in user data.

##
ACE (Audio Controls Editor)

-
**
Fixed
**
: Crash during shutdown where the ACE tried to access an invalid Audio System member.
