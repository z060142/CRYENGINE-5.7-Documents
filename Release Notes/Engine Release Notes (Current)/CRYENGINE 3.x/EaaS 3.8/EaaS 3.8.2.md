# EaaS 3.8.2

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/47316993/pages/44962927
- Page ID: 44962927
- Breadcrumb: Engine Release Notes (Current) > CRYENGINE 3.x > EaaS 3.8 > EaaS 3.8.2
- Parent: EaaS 3.8

## Content

Released 30th July, 2015

##
Overview

##
Release Highlights

##
New Depth-of-Field Implementation

CRYENGINE 3.8.2 introduces an all-new DOF implementation that fixes many of the edge bleeding artifacts of the previous technique, while being more bandwidth-friendly and thus efficient at the same time. The new implementation is based on the gather-based technique that was prototyped during Ryse and presented at SIGGRAPH back then.

![Image](https://www.cryengine.com/docs/static/attachments/44962929)

![Image](https://www.cryengine.com/docs/static/attachments/44962928)

*
Left: Old DOF implementation (note the ghosting/silhouette around the characters). Right: New DOF implementation.
*

##
Improved Motion Blur Quality

Our motion blur implementation uses a more sophisticated sample weighting scheme now which improves the quality of silhouettes at slightly better performance. The motion blur amount is controlled now using real-world shutter speed settings (e.g. 1/125 s).

##
Improved Volumetric Fog Quality

We put a lot of effort on further improving the quality of our new voxel-based volumetric fog. In particular, the temporal stability is a lot better and flickering and ghosting artifacts are greatly reduced.

##
Important Code and Data Changes

New unified CRY_PLATFORM_xxx defines were introduced as replacement for compiler-specific and/or custom defines. See file CryPlatformDefines.h for details.

The Dedicated Server build process is being updated. Below is an overview.

File Location

 |
DLL's Folder

 |
Description

 |

Bin64/GameSDK.exe

 |
Bin64/*.dll

 |
This is the full game client.

 |

Bin64/GameSDK_Server.exe

 |
Bin64/*.dll

 |
This uses the exact same DLL's as the full game client.

*
Known issue with client joining, will be resolved in 3.8.3.
*

 |

Bin64_dedicated/GameSDK_Server.exe

 |
Bin64_dedicated/*.dll

 |
This uses a different set of DLL's specifically setup for Dedicated Server.

 |

##
Editor

-
**
New
**
: Added tool-tip help to constraint entity.

-
**
New
**
: More console output during automatic joints generation.

-
**
New
**
: Added flowgraph node for physical collisions.

-
**
New
**
: Prefab events now transmit any data.

-
**
New
**
: Calling GameDLL method when user clicks the "Update Scripts" button in the editor.
**

**

-
**
Fixed
**
: (Prefabs) Crash when renaming prefabs (and maybe other objects) with non ASCII characters.

-
**
Fixed
**
: (Equipment pack) Space button behavior for checkboxes (CE-6396).

-
**
Fixed
**
: Picked up weapons no longer disappear after exiting gamemode (CE-6510).

-
**
Fixed
**
: Update time of day upon TimeOfDayEdit input (CE-6027).

-
**
Fixed
**
: Crash when renaming and deleting prefabs.

-
**
Fixed
**
: HypergraphView right button click produces warnings in console (CE-6547).

-
**
Fixed
**
: Use relative path to store the last loaded level (CE-6142).

-
**
Fixed
**
: Also raising the ENTITY_EVENT_XFORM_FINISHED_EDITOR entity event when an object was freshly placed.

-
**
Fixed
**
: (CryDesigner) Broken polygons while moving vertex/edge/polygon.

-
**
Fixed
**
: (CryDesigner) Not displaying cursor in "Done" status in Cylinder and Cone tools.

-
**
Fixed
**
: (CryDesigner) Missing some polygons in a designer object from 3.5.8 when loading the designer object in 3.8.1.

-
**
Fixed
**
: (CryDesigner) ResetXForm tool which didn't work on multiple selected objects.

-
**
Fixed
**
: (Trackview) Comment node now reacts to Enable/Disable switch (CE-6448).

-
**
Tweaked
**
: Changed "glossiness" naming to "smoothness" in the Material UI.

-
**
Tweaked
**
: Expose entity selection changes from Editor to Game though IEditorGame.

-
**
Tweaked
**
: Minor tweaks in PrefabEvents and its FlowPrefabNodes.

-
**
Tweaked
**
: Tweaked Default TOD settings: Fog Color height offset to 0 (centered), Lowered radial lobe so it doesn't appear in front of geometry, decreased max exposure from 10 to 2.8, decreased shadow jitter at night time.

-
**
Tweaked
**
: Switched Qt version to 5.4.2, added WebKit libraries.

##
Rendering

-
**
New
**
: Gather-based DOF implementation which fixes edge bleeding artifacts and is more efficient (toggled with r_depthOfFieldMode 0/1).

-
**
New:
**
 Improved motion blur quality.

-
**
New:
**
 Added CVar r_MotionBlurCameraMotionScale to reduce camera motion blur without affecting object motion blur.

-
**
New:
**
 Motion blur shutter speed (r_MotionBlurShutterSpeed) is specified as reciprocal of exposure time in seconds now (e.g. 1/125 s)

-
**
**
**
New
**
**
:
**
 (Shading) Reduce Fresnel when surface reflectance is below two percent (useful for specular occlusion, also allows to manually lower specular on terrain and vegetation where it can appear overly strong).

-
**
**
New
**
:
**
 Made super-sampling configurable for non-main viewports.

-
**
**
New
**
:
**
 (HLSLcc) Added python build scripts to simplify change workflow.

-
**
Refactored:
**
 (Textures) Removed unused priority field.

-
**
Refactored:
**
 (Textures) Removed unused HighQualityFiltering functionality.

-
**
Refactored:
**
 Removed unreferenced techniques from PostEffects.cfx.

-
**
Refactored:
**
 Removed deprecated light boxes. Superseded by clip volumes (CE-6206).

-
**
Refactored:
**
 HDR related cleanups: Removed obsolete CVars r_HDRBrightOffset, r_HDRBrightThreshold, r_HDRBrightLevel, r_HDREyeAdaptationFactor, r_HDREyeAdaptationBase.

-
**
Refactored
**
: (VR) Refactoring of VR stereo resources and renderer initialization.

-
**
Fixed:
**
 Fixed non-HDR skyboxes when reverse depth is enabled (CE-6527).

-
**
Fixed:
**
 Fixed varying terrain offset when using arbitrary near plane distance.

-
**
Fixed:
**
 (Shadows) Maintain frustum order while sorting shadow frustums by light (CE-5168).

-
**
Fixed:
**
 (Shadows) Recompute cached shadows when display options change (CE-6430).

-
**
Fixed:
**
 (
HLSLcc
) GATHER4 was missing sampler part in combined texture name (CE-6674).

-
**
Fixed:
**
 Replaced broken r_UseAlphaBlend by r_TransparentPasses to skip rendering of transparent objects (CE-6226).

-
**
Fixed:
**
 Fixed shader compile error on GLES3.1.

-
**
Fixed:
**
 Add basic support for PBO copy of default framebuffer texture (required for copying to/from staging textures such as in screenshots) (CE-6439).

-
**
Fixed:
**
 Adjusted depth test for picked up items when changing between 1st person and 3rd person camera mode (CE-72).

-
**
Fixed:
**
 Fixed tiled shading crash when invalid texture is specified and added warning in displayinfo section (CE-6427).

-
**
Fixed:
**
 Allow very small sun intensity values.

-
**
Fixed:
**
 NaN check in eye adaptation shader.

-
**
Fixed:
**
 Uninitialized memory in STexState.

-
**
Fixed:
**
 Viewport resolution restoration on renderer context switch.

-
**
Fixed:
**
 Ignore CVars r_Fullscreen, r_BackbufferWidth, r_BackbufferHeight in HandleDisplayPropertyChanges on console as well as mobile (CE-6595).

-
**
Fixed:
**
 Improved how camera shutter speed gets incorporated to make motion blur resolution- and framerate-independent.

-
**
Fixed:
**
 Missing swap chain release and resolution change by the stereo renderer in CD3D9Renderer::ChangeViewport (causes everything being shaded black in Editor).

-
**
Fixed:
**
 Replaced ambiguous GetNativeWidth/Height with

GetOverlayWidth/Height to get UI and debug text resolution, and
GetBackbufferWidth/Height for backbuffer resolution.

-
**
Fixed:
**
 Replaced fatal error with normal error when the number of static instance buffers is exceeded (CE-3360).

-
**
Fixed:
**
 Use the actual current viewport size when scaling 2D geometry (CE-6410).

-
**
Fixed:
**
 (
DXGL
) Always use the native resolution on mobile. Minor DXGL fixes (CE-6499).

-
**
Fixed:
**
 (
DXGL
) Call ResizeTarget when the output resolution changes - correctly applies changes to desktop mode when fullscreen and window size when windowed; also update viewport sizes.

-
**
Fixed:
**
 (DXGL) CopyTexture and CopySubTexture now work with default framebuffer textures, although not in the most efficient way (previously would crash).

-
**
Fixed:
**
 (DXGL) Fixed cache-related bugs caused by frame buffers being created with a previously used name still in the cache. In particular this solves non deterministic black screens when changing resolution.

-
**
Fixed:
**
 (HLSLcc) Fixed build script ignoring the "portable" flag.

-
**
Fixed
**
: (VR) Fixed swap chain resizing, fullscreen mode changes, and full screen window activation (alt+tab) when sys_vr_support is enabled (CE-6458).

-
**
Fixed
**
: (VR) Do not create/recreate the intermediate buffers in CD3DStereoRenderer::OnResolutionChanged() if stereo device is "none".

-
**
Fixed
**
: (VR) Do not use a temporary depth surface for the eye depth buffer since those are released on level unload. Fixed uninitialized data causing potential access violation when the Oculus texture creation fails (CE-6457).

-
**
Fixed
**
: (VR) Fixed issue with stereo and multiple viewports in CD3D9Renderer::ChangeViewport causing the eye textures to be recreated on every viewport change even without stereo enabled - now it only does when the main swapchain is created or resized (CE-6646).

-
**
**
Tweaked
**
:
**
 Min depth downsample stored in ztargetscaled.g.

##
Volumetric Fog

-
**
New:
**
 Added CVar r_VolumetricFogMinimumLightBulbSize to reduce light flickering.

-
**
New:
**
 Added radial lobe parameter to Light entity.

-
**
New:
**
 Use downscaled sun shadow maps.

-
**
New:
**
 Added ambient light support.

-
**
**
Tweaked
**
:
**
Mitigated sharp transition between environment probes.

-
**
**
Tweaked
**
:
**
 Reduced flickering.

-
**
**
Optimized
**
:
**
 Optimized analytical volumetric fog.

-
**
Optimized:
**
Improved performance.

-
**
Fixed:
**
 Fixed r_DeferredShadingEnvProbes, r_DeferredShadingAmbientLights, and r_DeferredShadingLights not being respected.

-
**
Fixed:
**
 Fixed shadow quality not getting better when r_VolumetricFogShadow=0 and r_VolumetricFogSample>0.

-
**
Fixed:
**
 Reduced seam visibility between ray-marched and analytical volumetric fog.

-
**
Fixed:
**
 Fixed clip volume not affecting voxel-based volumetric fog correctly when the range parameter is changed.

-
**
Fixed:
**
 Removed redundant CVar r_VolumetricFog (CE-6464).

-
**
Fixed:
**
 Fixed analytical volumetric fog disappearing (CE-6486).

-
**
Fixed:
**
 Fixed horizon artifacts with certain ramp settings (CE-6487).

-
**
Fixed:
**
 Fixed volumetric fog not looking consistent when camera is rotated (CE-6444).

##
SVOGI (Experimental)

-
**
New:
**

Added support for surface material color for projectors (was missing in basic mode 0)

-
**
Fixed:
**
 Mostly solved missing AO outside of voxelized area by using sort of large scale SSAO

-
**
Fixed:
**
 GI on forward shaded materials like hair and eyes

-
**
Fixed:
**
 Tracing quality improvements and few bug fixes

##
Engine

##
Engine General

-
**
New
**
: Updated Steamworks SDK to 1.33b.

-
**
New
**
: Adding new methods to the octree to allow both moving and removing primitives so that we can cope with more dynamic situations.

-
**
New
**
: Added sys_build_folder CVar. Optionally specifies external full path to the build folder to read pak files from. Can be a full path to an external folder or a relative path to a folder inside of the local build.

-
**
New
**
: Make TIMEJUMPED_TRANSITION_TIME into a CVar.

-
**
Refactored
**
: Using std::unordered_map instead of hash_map, std::tr1::unordered_map, ...

-
**
Refactored
**
: Removed unnecessary #undef GetClassName.

-
**
Refactored
**
: Introducing CRY_PLATFORM_xxx defines as replacement for compiler-specific and/or custom defines.

-
**
Refactored
**
: (Serialization, QPropertyTree) Merging Serialization library changes with original yasli code.

-
**
Fixed
**
: (Launcher) Fixed crash when opening any map (CE-6606) (CE-6607).

-
**
Fixed
**
: (QPropertyTree) fixed resource selector not respecting read-only flag.

-
**
Fixed
**
: Fixed TBN extraction from quaternion.

-
**
Fixed
**
: Renamed ARRAY_COUNT and ARRAY_VAR macros to CRY_ARRAY_COUNT and CRY_ARRAY_VAR (CE-6273).

-
**
Tweaked
**
: Cleaned Color_tpl's Set()/set() functions.

-
**
Tweaked
**
: Migrated to next libtiff version: tiff-4.0.4 (from tiff-3.0.3).

-
**
Tweaked
**
: Moved pipeline plugins are now part of release configurations.

-
**
Tweaked
**
: Added support for std::unique_ptr and std::shared_ptr in the serialization library.

-
**
Tweaked
**
: CListenerSet also now iterating over the registered listeners with a custom functor.

##
Physics

-
**
New
**
: Make breeze areas optionally awake objects when moving via BreezeAwakeThreshold param (CE-6308).

-
**
Fixed
**
: Don't use hard-coded mat_leaves surface type if vegetation proxy already has surface type (CE-6493).

-
**
Tweaked
**
: Getting rid of vector2xxx types (using Vec2xxx instead).

##
Common

-
**
New
**
: Added generic Octree class to CryCommon.

-
**
Tweaked
**
: Documented texture flags.

##
System

-
**
New
**
: Added FormatV function to string classes.
**

**

-
**
Refactored
**
: Removed Softcode support. Use Recode instead.

-
**
Refactored
**
: Disabled file handle cache.

##
WAF

-
**
Fixed
**
: x86 toolchain detection.

-
**
Fixed
**
: Use Windows 8.0 Manifest Tools (MT.exe) for x86 and x64 (for autodetect: on/off).

-
**
Fixed
**
: Converted cry_waf.sh line endings to Unix-style.

-
**
Refactored
**
: Refactor MSVC auto-detection.

-
**
Tweaked
**
: Refactor MSBUILD platform auto-detection when generating VS solutions.

-
**
Tweaked
**
: Strip platform if not supported by MSBUILD after giving user the option to generate the folder.

-
**
Tweaked
**
: Do not flag an error when MSBUILD platform does not exist and WAF was executed without ADMIN RIGHTS.

-
**
Tweaked
**
: For waf_files show error when key is not unique for a dictionary level.

-
**
Tweaked
**
: Improve debugging experience.

##
3D Engine

-
**
New
**
: (VR) Allow AuxGeom to be rendered in Stereoscopic mode.

-
**
New
**
: (VR) Change FG-Node VR:GetCameraAngles into VR:TransformInfo and added extra info about player, camera and HMD transform.

-
**
New
**
: Octree now allows the re-evaluation of a limited set of nodes.
**

**

-
**
Fixed
**
: Reading non-aligned data from compiled physical proxies chunk.

-
**
Fixed
**
: (Occlusion) Take viewport into account when downsampling device depth buffer.

-
**
Fixed
**
: (Debugging) Fixed info text for e_DebugDraw 3 (CE-2839).

-
**
Fixed
**
: (Debugging) Modified job system profiler layout (CE-2767).

-
**
Fixed
**
: Procedural vegetation objects are no longer spawned on wrong layers (CE-6532) (CE-6649)

-
**
Tweaked
**
: (VR) Move Oculus specific coordinates for TrackingState to OculusDevice.

-
**
Tweaked
**
: (Octree) tweaked comments and converted a for loop into a range-based for loop as suggested in the previous review.

-
**
Tweaked
**
: CVar sys_job_system_profiler produces different colors for different platforms (CE-92).

##
Particles

-
**
New:
**
 Refactored MoveRelEmitter, adding options to ignore emitter size or rotation (CE-3783) (CE-4528).

-
**
Fixed
**
: Fixed disappearing emitters, caused by incorrect 3DEngine.GetRenderer pointer. Now compute angular density and max distance from PassInfo.Camera whenever needed (CE-6282).

-
**
Fixed
**
: Restored SimplePhysics and RigidBody collision. GetRandomPos attachment fixes: More properly separated physics and render objects in particle structure; use StatObj physics geometry when Physics attachment requested; GetRandomPos implementations check for empty extents, fixing crashes; fixed false positive effect updating based on TextureTiling memcmp (CE-2621).

-
**
Fixed
**
: Fixed Facing=Velocity behavior. Restored Stretch.OffsetRatio behavior (CE-6373).

-
**
Fixed
**
: Avoid division by small parent size with MoveRelEmitter. Fixed inconsistent position and size changes with parent size change (CE-6528) (CE-6530).

-
**
Fixed
**
: Normalize quat after MoveRelEmitter transform, to avoid cumulative error and invalid matrices (CE-6757).

-
**
Fixed
**
: Avoid isqrt(0) in TargetMovement (CE-6529).

-
**
Refactored
**
: Moved CParticleEmitter functions back to correct file (leftover SPU code).

##
RC/Tools

##
Tools General

-
**
Refactored
**
: Remove Patch/7za.exe as it's already in the Tools sub-folder.

-
**
Refactored
**
: Remove Patch/makepatchpak.bat as it is unused.

-
**
Fixed
**
: (Statoscope) Fixed crash when opening two logs at once.

-
**
Fixed
**
: (Statoscope) Show log compare under 'Item Info' when using the function profiler (CE-6462).

-
**
Fixed
**
: (CryMaxExporter) Fixed crash in 3dsMax when selecting vertices in CrySkin's envelopes (CE-6656).

##
Resource Compiler

-
**
New
**
: (RC ImageCompiler) Added CVars r_TextureCompiling and r_TextureCompilingIndicator to mute compilation of textures and the display of indicator textures (CE-6186).
**

**

-
**
Refactored
**
: Deleted profile and performance configurations of RC.

-
**
Fixed
**
: (RC ImageCompiler) Fixed failure in previewing images in BC6 format (missed converting to 4-float RGBA format before calling NormalizeImageRange()).

-
**
Tweaked
**
: (RC ImageCompiler) Switched error measurement to measure in gamma-space instead of linear space.

-
**
Tweaked
**
: (RC ImageCompiler) Migrated from PowerVR SDK 3.3 to 3.5.

-
**
Tweaked
**
: Removed RC and shader cache generator from 'Tools/Editor' module.

##
Animation

##
CryAnimation

-
**
Refactored
**
: Command Buffer: Everything executed in the animation job is now executed through the command buffer.
**

**
Increased command buffer size because we have more commands now. (see Command::CBuffer::BufferMemorySize, now set to 8192)

-
**
Fixed
**
: Fixed assert 'm_lastDatabaseUnloadTimeStamp <= currTimeStamp' by using a different kind of timer for the timestamps.

-
**
Fixed
**
: Only the first pose modifier on layer -1 ("after physics") was executed, now all of them are.

-
**
Fixed
**
: Multithreading issues in the AttachmentManager and in secondary animation.

-
**
Fixed
**
: Secondary Animation: Avoid division by zero in CheckHalfCapsule.

##
Character Tool

-
**
Fixed
**
: Avoid warning "elements not used by BlendSpace" whenever user saves the BlendSpace file. We now only write out XML nodes into BlendSpace file if there are actual child nodes in the element.

-
**
Fixed
**
: Fixed preview of animevents on blendspaces.

-
**
Fixed
**
: Removed offset for audio events (CE-6554).

-
**
Fixed
**
: Fixed assert when selecting blendspaces in Character Tool (CE-6068).

-
**
Fixed
**
: Fixed slow update when changing locomotion parameters.

-
**
Fixed
**
: Workaround for crash when changing filtering options.

-
**
Fixed
**
: Prevent the loader from crashing (CE-5430).

-
**
Fixed
**
: Crash in GlobalAnimationHeaderLMG::Init_XXX() functions while editing blend-spaces (CE-6608).

-
**
Tweaked
**
: User now changes the diameter instead of the radius of the inner collision box of a lozenge; improve UI description (based on new serialization decorator RadiusAsDiameter) (CE-5850).

##
Mannequin

-
**
New
**
: Added "Add to Source Control" button to the File Manager (useful when adding new sub .adb files for example) (CE-5960).

-
**
New
**
: Particle Effect procclip: Effect Name can now be edited using the standard browser (CE-6064).

-
**
Fixed
**
: Animation Browser does not update its paths when open and a new AnimLayer is selected in the track view (CE-5962).

-
**
Fixed
**
: Assert in CWnd::GetWindowRect when the mannequin file manager opens.

-
**
Fixed
**
: Assert 'Fragment completion time set multiple times'.

-
**
Fixed
**
: Assert in CClipTrack::GetSecondaryTime (CE-6479).

-
**
Fixed
**
: Crash when manually deleting fragments from an ADB file. When we reload ADB files from the file change monitor, we now reset the editor by reloading the current preview file (similar to how it's done elsewhere) (CE-6381).

##
Action

##
Flowgraph

-
**
New
**
: Additional requested changes to collision flowgraph node.

-
**
New
**
: Improved constraint flowgraph help hints.

-
**
New
**
: More output in flowgraph collision node.

-
**
New
**
: Allow entities to listen for events from Flowgraph in code.
**

**

-
**
Fixed
**
: Disabled color tint from Image:FilterVisualArtifacts correctly. Tint colors that were saved before this change can no longer be loaded and need to be set again (CE-6398).

-
**
Fixed
**
: Crash when jumping in game and prefab inputs are triggered.

-
**
Fixed
**
: Check for entities without physics in constrain flowgraph nodes.

-
**
Fixed
**
: "Lock" and "UnLock" outputs of door nodes now fire events (CE-6397).

##
TimeDemo

-
**
New
**
: Added VR support for Timedemo.

-
**
Fixed
**
: Timedemo bug for legacy format.

-
**
Fixed
**
: TimeDemoRecorder's player rotation for HMD playback.

-
**
Tweaked
**
: Timedemo related refactoring in View and TimeDemoRecorder.

##
Audio

##
Audio General

-
**
New
**
: Updated Wwise to v2015.1 build 5416 (DEV-247)
**
.
**

-
**
New
**
: Added ability to set a position and rotation offset on the audio listener in reference to its entity (CE-6022).

-
**
New
**
: Added hard coded RTPC "time_of_day" which is updated if present and changes have been made to TOD.

-
**
New
**
: Medium audio interface cleanup, removed unused code, additionally implemented handling of delayed playback of middleware events.

-
**
Fixed
**
: ATS did not retrigger when entering game mode in Editor.

-
**
Fixed
**
: Not all error codes were translated correctly into an Failure-code for callbacks.

-
**
Fixed
**
: TrackView SceneNode and EntityNode audio keys were not applied if no duration was set.

-
**
Fixed
**
: Case where RTPC flowgraph nodes did not update anymore.

-
**
Fixed
**
: Bug in AreaManager where entities that were near an area never left it upon teleportation (CE-5000).

-
**
Fixed
**
: Bug in CAudioSystemImpl_wwise::PostEnvironmentAmounts where the method always returned failure (DEV-251).

-
**
Fixed
**
: Crash when not supplying arguments to the es_AudioListenerOffset CVar.

-
**
Fixed
**
: Iterator invalidation in AudioProxy and AFCM.

-
**
Fixed
**
: Where a playing AudioTrigger on AAA and AAR entities wasn't stopped when the ATL-Trigger was changed (CE-6484).

-
**
Fixed
**
: Where after a save/load procedure some environmental sounds were gone (CE-5593).

-
**
Fixed
**
: Where an ATS did not update its environment when placed in the level.

-
**
Fixed
**
: Where sometimes the wrong environment was set on audio objects.

-
**
Fixed
**
: Where the audio listener offset matrix took scaling into account (CE-6549).

-
**
Fixed
**
: Wrong IOS platform define in AudioSystemImplCVars.cpp (DEV-252).

-
**
Fixed
**
: Set the audio listener entity to not serialize during save/load, this is not necessary as the entire entity is recreated.

-
**
Fixed
**
: When removing the ATL-StartTrigger string from an AAA and ATS entity the corresponding event was not stopped additionally when the entities got hidden error messages appeared in the log.

-
**
Fixed
**
: (DRS) Missed to add the Drs-Proxy to the SerializationOrder array.

-
**
Fixed
**
: Ambience wouldn't start triggered via an AAE when the player spawned inside the corresponding area when near a nested area (CE-6683)

-
**
Tweaked
**
: Added ATL event ID to the request info on callbacks for delayed starting middleware events.

-
**
Tweaked
**
: Compiling SDL Mixer on Linux.

-
**
Tweaked
**
: Enabled visualization of merged mesh type vegetation clusters, for that introduced CVars e_MergedMeshesClusterVisualization and e_MergedMeshesClusterVisualizationDimension (DEV-231).

-
**
Tweaked
**
: If IS_EAAS is defined, don't enable WWISE_USE_OCULUS.

##
ACE (Audio Controls Editor)

-
**
New
**
: Controls are selected in edit mode as soon as they're added.

-
**
New
**
: Remove Qt dependency for ACE external .dlls (DEV-245).

-
**
New
**
: Use QPropertyTree for the connection properties (DEV-246).

-
**
Fixed
**
: Deleting the last control in a folder marks parent as modified (CE-6511).

-
**
Fixed
**
: Manually add internal requests to default controls (CE-6552).

-
**
Fixed:
**
 Fixed crash when deleting connections (CE-6766).

-
**
Tweaked
**
: Control connections are sorted alphabetically in the Inspector Panel.

-
**
Tweaked
**
: Last connected control wasn't getting added when connecting to a preload.

##
AI System

-
**
New
**
: MovementSystem now does optional path re-planning upon NavMesh changes at run-time (CE-6382).

-
**
New
**
: Added ai_MNMAllowDynamicRegenInEditor CVar to allow MNM to be regenerated in Editor while in game mode.
**

**

-
**
Fixed
**
: BehaviorTreeManager: switched order of some member variables to prevent accessing dangling pointers in their destructors (CE-6620).

-
**
Fixed
**
: Communication configuration is now loaded when the AI system is initialized and no longer on ESYSTEM_EVENT_GAME_POST_INIT to ensure all communication data is ready at AI scripts startup time (CE-4383).

-
**
Fixed
**
: Editor in game-mode was listening to NavMesh changes for Agents that didn't exist.

-
**
Fixed
**
: NavigationSystem::RemoveAllIslandConnectionsForObject() erroneously got passed in an OffMeshLinkID instead of the EntityId.

-
**
Fixed
**
: Re-added the built-in MBT editor which was incorrectly removed in previous release (CE-6588).

-
**
Fixed
**
: When requesting paths, the MovementSystem was always defaulting to a hard-coded NavigationAgentTypeID of 1.

-
**
Fixed
**
: Uninitialized boolean causing random values to be serialized in save games. (CE-6550)

-
**
Refactored
**
: IMovementActorAdapter is now const-correct.

-
**
Refactored
**
: Moved all functionality from AIBubblesNotfier to AIBubblesSystem since SoftCode is removed by now.

##
Game

-
**
Fixed
**
: Added missing HitTypes to HitTypes.xml: PistolBulletIncendiary, ShotgunShell/Solid, Rocket, ExplosiveGrenade (DEV-186).

-
**
Fixed
**
: Clear water droplet effect when entering a vehicle (CE-5130).

-
**
Fixed
**
: "Could not get forcefeedback effect id" warnings that appeared when starting the game (CE-6548).

-
**
Fixed
**
: Getting stuck while standing up after slide (CE-6347) (CE-6118).

-
**
Fixed
**
: USE_BLEND_FROM_RAGDOLL was not defined resulting in AI not getting up once knocked over (CE-6426).

-
**
Fixed
**
: Create a log entry when a force feedback effect cannot be found (CE-6320).

-
**
Tweaked
**
: Added MovementModifiers description info to Rifle script. Deceased firingSpeedScale to 0.75.
[Release Highlights](#release-highlights)
[Important Code and Data Changes](#important-code-and-data-changes)
[Editor](#editor)
[Rendering](#rendering)
[Engine](#engine)
[3D Engine](#3d-engine)
[Particles](#particles)
[RC/Tools](#rctools)
[Animation](#animation)
[Action](#action)
[Audio](#audio)
[AI System](#ai-system)
[Game](#game)
