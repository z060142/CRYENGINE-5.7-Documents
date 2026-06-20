# EaaS 3.6.3

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/47316993/pages/44963006
- Page ID: 44963006
- Breadcrumb: Engine Release Notes (Current) > CRYENGINE 3.x > EaaS 3.6 > EaaS 3.6.3
- Parent: EaaS 3.6

## Content

Released June 6th, 2014

##
Sandbox

-
**
New
**
: Send a warning to the log when failing to access CVar from Python (CE-3621).

-
**
New
**
: Changed Vegetation tool to enable shadows (low minspec) by default (CE-3615).

-
**
New
**
: Added (sub/child)layer streaming support in Editor game-mode (CE-3502). Still requires e_ObjectLayersActivation=1 be set!

-
**
New
**
: Changed Vegetation tool to enable shadows (low minspec) by default (CE-3615).

-
**
Fixed
**
: Improved support for using custom Game folder in Editor. Updated PathUtil to correctly compute paths when the game directory lies outside the root folder, but on the same drive (result starts with ..). Updated CryPak to correctly open paths starting with .. (CE-2916).

-
**
Fixed
**
: Crash for Watervolumes. Checks for unsupported primitives in booleans/dynamic water (CE-3234).

-
**
Fixed
**
: Improved the Vertex Snapping by changing ways of detecting vertices using ray collision check with a boundbox around each vertex. Disabled older Vertex Snapping system.

-
**
Fixed
**
: Crash in AxisHelperExtended when there are no collision entities.

-
**
Fixed
**
: Bug with the flowgraph disappearing when changing nodes of a flow graph of an entity object which belongs to a prefab (CE-2583).

-
**
Fixed
**
: Enable alt-tab while in Welcome screen (CE-3510).

-
**
Fixed
**
: Comparison of invalid iterator in CSequencerDopeSheet.

-
**
Fixed
**
: Issue with a geometry cache file open/compile dialog not opening correctly (
[http://steamcommunity.com/games/220980/announcements/detail/1532660850808039477](
hotfix 2639
)
).

-
**
Fixed
**
: Issue that prevented a debugger from being attached to the Sandbox process (hotfix 2639).

-
**
Optimized
**
: Removed deprecated Object Manager "ignore external layers" flag.

-
**
Optimized
**
: Removed 'Cancel' button from loading bar (which has no valid use).

-
**
Optimized
**
: Removed obsolete AVI recorder tool.

-
**
Optimized
**
: Removed obsolete RibbonUI toolbar.

-
**
Optimized
**
: All import/export file operations limited to standard English characters in filename to prevent compatibility issues (CE-3318).

-
**
Optimized
**
: Lowered default Ocean wave size to 0.4. Updated default TOD to include night time @ midnight. Added keys for every 6 hours, based off midday settings for now.

##
CryDesigner

-
**
New
**
: Made a designer object highlight like a brush object when the mouse cursor is over.

-
**
New
**
: Added a rotation circle gizmo to rotate a uv coordinate and Improved a way of modifying uv setting of a texture by manipulating the Translation/RotationCircle/Scale Gizmos (CE-3443).

-
**
New
**
: Improved the Lathe Tool and Enabled it.

-
**
New
**
: Designer objects support for Runtime Prefabs.

-
**
New
**
: Implemented the Magnet tool.

-
**
Fixed
**
: Bug on a selected face in the texture mapping tool disappearing after saving a level and loading it (CE-3443).

-
**
Fixed
**
: Compile error when vtx_idx is uint32 in CBrushBase.cpp.

-
**
Fixed
**
: Bug about not removing a render mesh as the designer object is deleted in a group or the group is deleted.

-
**
Fixed
**
: Added faces of a old solid to a designer object when converting it without an union operation.

-
**
Fixed
**
: Removed calling ResetDB() after loading a designer object.

-
**
Fixed
**
: Got highlight box size to be calculated by a world vertex position.

##
Animation and Characters

-
**
New
**
: Added ca_vaEnable CVar to enable Vertex Animation.

-
**
New
**
: Added ca_vaSkipVertexAnimationLOD CVar to skip LOD 0 if the model uses vertex animation.

-
**
New
**
: Added ca_vaBlendEnable CVar to disable corrective shapes.

-
**
Fixed
**
: When an animation is paused and started again in Character Editor, now the animation events will play for the frame the animation is started from.

-
**
Fixed
**
: Animation events on the first couple of frames of an animation being ignored.

-
**
Fixed
**
: Index column of the joint combo-box in the Character Editor.

-
**
Fixed
**
: VerifyLMGs() issue.

-
**
Fixed
**
: VertexAnimation.

-
**
Fixed
**
: Leak in character physics (CE-3103).

-
**
Fixed
**
: Restored wireframe character rendering.

-
**
Optimized
**
: Removed unused mesh merge & saveCHR functionality.

##
Trackview

-
**
Fixed
**
: Depth of field track.

-
**
Fixed
**
: No rendering updates in forest due to start sequence.

-
**
Fixed
**
: Not being able to rename camera node.

##
Engine

-
**
New
**
: FP32 simulation on Merged Mesh system to improve 'jittering' effect.

-
**
Fixed
**
: Null pointer crash in CDevMode when the actor didn't have a movement controller (CE-3607).

-
**
Fixed
**
: Made win64/win32 checking code more explicit.

-
**
Fixed
**
: Don't boolean-break objects with non-uniform scaling (CE-3454).

-
**
Fixed
**
: Bug MatMan - submaterials release (CE-3210).

-
**
Fixed
**
: JobManager Profiler doesn't show main/render thread information (CE-2935).

-
**
Fixed
**
: Crash with stale entity ptrs in deferred events on level reset (CE-3382). 0 ptr check on level unload (CE-3424).

-
**
Fixed
**
: Passing netaddresses over DLL boundaries.

-
**
Fixed
**
: Some uninitialized zoom values (CE-3389).

-
**
Optimized
**
: Removed CrySystem MD5 dependency.

-
**
Optimized
**
: Disable async octree updates by default.

-
**
Optimized
**
: Texture streaming job optimizations.

-
**
Optimized
**
: Replaced the new base64 code with an existing one in CryNetwork to avoid duplicate functions.

##
Resource Compiler

-
**
Fixed
**
: Added auto removal of alpha channel from LightProjector textures..

-
**
Fixed
**
: RC ImageCompiler: fixed crash in RGBK (accessing non-existing mip).

##
Game

-
**
Fixed
**
: Helicopter movement/handling fixes.

-
**
Fixed
**
: Fixed an issue with a dedicated server crash on startup (hotfix 2639).

##
Audio

-
**
New
**
: Added do_nothing event. Added ATL configs.

-
**
New
**
: Added a new CVar: s_IgnoreWindowFocus (hotfix 2639).

-
**
New
**
: Added the StopAllSounds request to the AudioSystem (hotfix 2639).

-
**
Fixed
**
: Various tweaks and updates to SDK soundbanks.

-
**
Fixed
**
: Added physics_collisions sound bank to preloads, cleaned up some unused events from the globalaudiocontrols.xml.

-
**
Fixed
**
: Added the auto-generated ATLTriggers for the SDK Wwise project.

-
**
Fixed
**
: Audio pass on Airfield level.

-
**
Fixed
**
: Reload sounds for pistol and rifle.

-
**
Fixed
**
: Sounds being cutoff when changing Menus.

-
**
Fixed
**
: Added speedboat soundbank to Forest level preloads.

-
**
Fixed
**
: Incorrect attenuation preset for Forest hilltop ambience.

-
**
Fixed
**
: Removed empty preload requests.

##
Renderer

-
**
Fixed
**
: Console being overwritten by aux geometry used by profile and debug modes.

-
**
Fixed
**
: Improved Multi-Monitor Support. When moving the window, update preferred monitor so when transitioning to full-screen, the closest monitor is picked (instead of the primary) (CE-3601).

-
**
Fixed
**
: Explicit flush for async dips to prevent access of deleted resource view.

-
**
Fixed
**
: Sun Rays in TOD not working.

-
**
Fixed
**
: Wrong flag usage on water/ocean shader (CE-3409).

-
**
Fixed
**
: Render nearest shadows when tiled shading is enabled.

-
**
Fixed
**
: Light overdraw visualization (r_deferredshadingdebug 2) to work with ambient lights and when tiled shading is enabled (CE-3462).

-
**
Fixed
**
: Removed hardcoded states preventing Decals from being able to have alpha and glow simultaneously (CE-2304).

-
**
Fixed
**
: Support for AffectedBySun on VisAreas.

-
**
Fixed
**
: Improved forward shading consistency.

-
**
Fixed
**
: Various fixes for shadows from point lights.

-
**
Fixed
**
: Extended tiled deferred shading to support VisArea masking.

-
**
Fixed
**
: Changed r_DeferredShadingTiled CVar to be set to ‘1’ by default on PC (hotfix 2639).

-
**
Optimized
**
: Added postprocess debug smoothing as r_postprocesseffects 2 updates too fast & makes it unreadable (CE-2925).

-
**
Optimized
**
: Cleanup in D3DDeferredShading.cpp.

##
Particles

-
**
Fixed
**
: Issue with Graphs not being visible in Particle Editor.

-
**
Fixed
**
: Prevent build-up of dead particles and sub-emitters: Sub-emitters processed and cleaned even when particles not rendered (CE-3316).

-
**
Fixed
**
: Crash sometimes occurring with static variable initialized in multi-threaded function. Fixed incorrect target orbiting direction when priming particles.

##
Assets

-
**
New
**
: Added icon and weapon name to HUD.

-
**
Fixed
**
: Tweaked vehicle lights (CE-366).

-
**
Fixed
**
: Various material tweaks for Airfield assets.

-
**
Fixed
**
: Fixed missing texture paths in stone_toad material. Fixed asset material pathing. Optimized stand-in model.

-
**
Fixed
**
: Resized shader compiling cubemap texture to 256 to avoid tiled shading error (CE-3464).

-
**
Fixed
**
: Error with MtlPlane.cgf looking for unavailable material (objects/grid_gray). MtlPlane object added to MtlObjects max file (CE-1338).

-
**
Fixed
**
: Lowered Tracer thickness for Pistol/Rifle.

-
**
Fixed
**
: Font error with Flash UI assets.

-
**
Fixed
**
: Spruce tree material not using available Opacity map.

-
**
Fixed
**
: Tweaked HMMWV and Abrams materials.

##
LOD Generator

-
**
New
**
: LOD Generator now uses the vertex index format from ProjectDefines instead of hard-coding it.

-
**
Fixed
**
: Initial fixes for LOD baker to work with new PBS material model used in 3.6.

##
AI System

-
**
Fixed
**
: AISequence would not start running when passing in an actionNodeId of 0 (CE-3394).

-
**
Fixed
**
: NavigationSystem::UpdateMeshes() was sometimes causing invalidated iterators to get compared.

-
**
Fixed
**
: Flow node "AI:GroupAlertness" didn't fire "green" state on start of the node; SAVEGAME_VERSION_VALUE incremented (CE-2964).

-
**
Fixed
**
: Flow node AI:FactionReaction's output ports were switched (CE-2964).

-
**
Fixed
**
: Turret was not recognized as such by the flow node "AI:SetTurretFaction" (CE-2964).

-
**
Fixed
**
: Corrected the alertness levels in all SDK modular behavior trees (CE-3387).

-
**
Fixed
**
: Deleting vegetation didn't update the navmesh (CE-3531).

-
**
Fixed
**
: Using the flow node "AI:SetState" no longer causes a crash (CE-2964).

-
**
Fixed
**
: Impacting bullet was erroneously passed to the AISystem as AISTIM_BULLET_HIT twice instead of AISTIM_SOUND as well.

-
**
Optimized
**
: Refactored the base class for AISequence-compatible flow nodes to make implementations easier for new nodes in the future

##
Tools

-
**
Fixed
**
: Updated CryToolsInstaller manifest for preventing PCA ("Did this program install correctly?") pop-up (CE-3594).

-
**
Fixed
**
: (LuaRemoteDebugger) triggering a breakpoint automatically brings the application to the front now (CE-3420).

-
**
Fixed
**
: Issue with CryToolsInstaller failing to install the 3DS Max plugin (hotfix 2639).
