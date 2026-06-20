# CRYENGINE 5.1

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/47316993/pages/44962610
- Page ID: 44962610
- Breadcrumb: Engine Release Notes (Current) > CRYENGINE 5 > CRYENGINE 5.1
- Parent: CRYENGINE 5

## Child Pages

- [CRYENGINE 5.1.0](CRYENGINE%205.1/CRYENGINE%205.1.0.md)
- [CRYENGINE 5.1.1](CRYENGINE%205.1/CRYENGINE%205.1.1.md)

## Content

##
Code Interface Changes

See the
Important

[CRYENGINE 5.1 Data and Code Changes](CRYENGINE%205.1/CRYENGINE%205.1.0/Important%20CRYENGINE%205.1%20Data%20and%20Code%20Changes.md)
 article for more information.

If you upgrade from CRYENGINE 5.0, please read

[Migrating from CRYENGINE 5.0 to CRYENGINE 5.1 .](CRYENGINE%205.1/CRYENGINE%205.1.0/Migrating%20from%20CRYENGINE%205.0%20to%20CRYENGINE%205.1.md)

##
Editor

##
Editor General

-
**
New
**
: Added copy/cut/paste actions - this works across layers even across different files.

-
**
New
**
: Increased camera speed range. Changing speed with mouse wheel will now spawn a transparent slider with camera speed on the Viewport.

-
**
New
**
: Main menu bar search for quickly finding and executing commands.

-
**
Refactored
**
: Updated question dialogs.

-
**
Refactored
**
: Use separate enum for transform mode and for transform flag.

-
**
Refactored
**
: Improve interaction with gizmos.

-
**
Refactored
**
: Vegetation: Improved item removal in Vegetation Tool.

-
**
Refactored
**
: Make Designer use the same object type for all primitives. Use file string to create the proper geometry for Designer.

-
**
Refactored
**
: New material picker. Uses generic Engine file dialog.

-
**
Fixed
**
: Removed color code prefixes in the console, color codes are now handled properly.

-
**
Fixed
**
: Scale icons with distance option not getting saved.

-
**
Fixed
**
: Create object panel recreating objects when reloaded from layout.

-
**
Fixed
**
: RC not called correctly if the path contains spaces.

-
**
Fixed
**
: Particle Editor crashes on selecting "Go to Database".

-
**
Fixed
**
: Editor side terrain texture tiles trashing.

-
**
Fixed
**
: Do not set fake mouse events unless mouse is actually inside the window.

-
**
Fixed
**
: Cursor flickering when hovering over an object.

-
**
Fixed
**
: Highlight getting stuck on Editor when mouse exits the Viewport.

-
**
Fixed
**
: MFX_reload - cannot be executed, because of new console operation.

-
**
Fixed
**
: Properly fix rotating non-uniformly scaled objects - not working correctly for all object types and remove specific workaround for Designer.

-
**
Fixed
**
: Issue where the AI Shapes were out of sync between Sandbox and CryAISystem.

-
**
Fixed
**
: Vegetation Tool reacts on Shift toggle - doesn't check the pressed/released state.

-
**
Fixed
**
: Clip Volume objects did not create the correct type of Tool.

-
**
Fixed
**
: Selected Terrain Layer does not get updated in UI after layer is moved up/down.

-
**
Fixed
**
: Updated default page for Go To Documentation (F1) functionality.

-
**
Fixed
**
: Area Box bounding box not updated on size change.

-
**
Fixed
**
: "Export Vegetation Objects" should trigger warning when no vegetation is selected.

-
**
Fixed
**
: Export Occlusion Mesh not exposed in UI in Sandbox.

-
**
Fixed
**
: Remove redundant words from description to make message better fit in dialog.

-
**
Fixed
**
: Level Settings are sometimes not populated.

-
**
Fixed
**
: Preview in Vegetation Tool and create objects to not show by default.

-
**
Fixed
**
: Tools will now not be rendered when mouse is outside the Viewport. Note: while interacting with a Tool, mouse is still considered to be inside Viewport.

-
**
Fixed
**
: Make sure correct axis is hidden in ortho views and only for world/view reference coordinate systems - local always needs all axes.

-
**
Fixed
**
: Reference picture objects not loading textures. Also fix scale aspect ratio preservation - use Boolean instead of extra scale factor.

-
**
Fixed
**
: Importing a previously exported terrain block with opened Vegetation Editor causes crash.

-
**
Fixed
**
: Preview in file open dialog shown by default.

-
**
Fixed
**
: Crash in FileSystem Monitor.

-
**
Fixed
**
: Missing icons in TrackView.

-
**
Fixed
**
: Added event type to Database Manager to correctly handle removal of libraries on create Tool panel.

-
**
Fixed
**
: Merge option not working after separate is used.

-
**
Fixed
**
: Crash when creating a new GeomCache.

-
**
Fixed
**
: "save as" behavior for particle effects.

-
**
Fixed
**
: File select dialog missing for GeomCaches.

-
**
Fixed
**
: Environment Editor button icons missing.

-
**
Fixed
**
: Can't rename a Custom Command.

-
**
Fixed
**
: Modified the precision slider to set the value to wherever you clicked on the slider instead of doing page moves.

-
**
Fixed
**
: Road placement now enables terrain snapping if neither geometry nor terrain snapping are enabled.

-
**
Fixed
**
: Maximize menu item not working.

-
**
Fixed
**
: Missing "Show in Explorer" icon.

-
**
Fixed
**
: Crash when deleting a large selection of objects.

-
**
Fixed
**
: Actions will now get default command icons if they don't have one assigned already.

-
**
Fixed
**
: Save file selection dialogs which didn't append the default file extension.

-
**
Fixed
**
: Issue within XT that was causing the Editor to freeze during loading when windows custom theme is loaded.

-
**
Fixed
**
: Crash when closing a second instance of the Sandbox from the "another instance is already running" dialog.

-
**
Fixed
**
: Renamed and replaced icons for the +, - and x (when editing a shortcut in the Shortcut Editor).

-
**
Fixed
**
: Level Explorer no longer displays the objects that are contained in a prefab or group.

-
**
Fixed
**
: Deleting a prefab object should no longer crash the Level Explorer.

-
**
Fixed
**
: Meters Per Unit option bugged which causes a crash.

-
**
Fixed
**
: Crash when deleting parented objects.

-
**
Fixed
**
: For creation of shapes never reuse the constraints - instead always snap to terrain.

-
**
Fixed
**
: Viewport speed not getting clamped correctly.

-
**
Fixed
**
: Changing Override Material of Skydome causes crash.

-
**
Fixed
**
: Loading of reference picture image not working.

-
**
Fixed
**
: Environment probes with big light boxes not visible if central widget not visible.

-
**
Fixed
**
: Locking camera is now also allowed for Trackview Camera as well. Also added code to make Trackview Camera movable when attempting to move through camera view. It should now insert keyframes or move the whole object as needed.

-
**
Fixed
**
: Material synchronization with 3dsMax.

-
**
Fixed
**
: Save file selection dialogs which didn't append the default file extension.

-
**
Fixed
**
: Layouts-folder missing in \AppData\Roaming\Crytek\CRYENGINE-folder.

-
**
Fixed
**
: Resetting layout causes crash. Bound snapping changes directly to menu member function.

-
**
Fixed
**
: Clicking an item in the Level Explorer no longer moves it to the end of the list.

-
**
Fixed
**
: Environment probes not working after regenerating cubemaps.

-
**
Tweaked
**
: Name of camera appears again on the camera menu.

-
**
Tweaked
**
: Use enum instead of magic numbers for motion state.

-
**
Tweaked
**
: Do not accelerate with mouse wheel if middle mouse button is pressed.

-
**
Tweaked
**
: Make sure that increasing and decreasing camera speed with mouse wheel gives roughly the same numerical values. Floating point errors will still be accumulated, but should not be significant.

-
**
Tweaked
**
: Do not scale icons with distance by default.

-
**
Tweaked
**
: Swap colors of XY, YZ, ZX planes in move gizmo so color is more even.

-
**
Tweaked
**
: Gizmos get a bigger collision radius for their axis.

-
**
Tweaked
**
: Icons and gizmos are scaled based on Z distance from camera, not full distance. Avoids gizmos increasing in size as they move to the sides of the screen.

-
**
Tweaked
**
: Added local machine registry directory check for Launcher path (making Sandbox compatible to 'all user' installations).

-
**
Tweaked
**
: Updated layouts for default, animation, cinematic, Flowgraph and Level Design.

-
**
Tweaked
**
: Added camera speed icons.

-
**
Tweaked
**
: Show preview in Vegatation Tool and Create Object Tool by default.

-
**
Tweaked
**
: Central cube gizmo of scale primitive is highlighted too.

-
**
Tweaked
**
: Move Cone primitive for gizmo further outwards so line is not showing.

-
**
Tweaked
**
: Rename entries Area Box, Area Sphere etc. to just Box, Sphere etc. in Create Object.

-
**
Tweaked
**
: (Templates) New game projects don't use Engine root specific user folder.

##
Designer Tool

-
**
Refactored
**
: Creating Designer shapes is now possible without a Designer Object selected. Shapes go to own Panel to differentiate from other Tools which need selection.

-
**
Refactored
**
: Create new objects with shape tools if user has explicitly pressed shift. Use the same behaviour for all shapes.

-
**
Refactored
**
: Cube Editor now uses material panel in Groups/UV tab like every other Tool.

-
**
Fixed
**
: Crash when changing to CubeEditor Tool.

-
**
Fixed
**
: Creation of AreaSold/ClipVolume object types.

-
**
Fixed
**
: Missing and flickering subdivided Designer meshes on load.

-
**
Fixed
**
: Crash when exiting Designer Tool while subtool panel is active.

-
**
Fixed
**
: Sub-material dropdown not refreshing on object selection.

-
**
Fixed
**
: Missing icons for new Designer primitive types.

-
**
Fixed
**
: Reset the subdivision slider when freezing the subdivision, else it's very easy to mistakenly subdivide too much.

-
**
Fixed
**
: Designer gizmos disappearing on key move.

-
**
Tweaked
**
: Don't use tabs for subpanel in new Sandbox.

##
Trackview

-
**
New
**
: You can now enable or disable tracks.

-
**
Fixed
**
: Crash when opening the events dialog.

-
**
Fixed
**
: Keys getting placed incorrectly if the scrollbar is at the bottom of the Trackview Editor.

-
**
Fixed
**
: Shake track is broken.

-
**
Fixed
**
: Start time changes aren't working.

-
**
Fixed
**
: Keyframe inspector has the wrong fields.

-
**
Fixed
**
: Wrong time range when creating a new sequence.

##
Renderer

##
Renderer General

-
**
New
**
: MipMap generation utility pass.

-
**
New
**
: Added resource layout deduplication and caching.

-
**
Refactored
**
: (Render) moved light volume update conditional logic to RT_RenderScene.

-
**
Refactored
**
: Move Clip Volumes to RenderView.

-
**
Refactored
**
: Support for rendering multiple primitives in CPrimitiveRenderPass.

-
**
Refactored
**
: Preparations for VolumeRenderPass: Remove vertex buffer deduplication from CPrimitiveRenderPass and cache primitives by primitive type instead. FullscreenTriWPOS is no longer deduplicated as it is used rarely and will be refactored to read dynamic data from constant buffer.

-
**
Refactored
**
: Remove unused CDeviceGraphicsCommandList::IsCompatiblePipelineStateImpl and DeviceGraphicsCommandList::IsCompatibleResourceLayoutImpl.

-
**
Refactored
**
: Cleanups.

-
**
Refactored
**
: Perform root signature deduplication at device object level for all platforms.

-
**
Optimized
**
: Geometry-stream info is deduplicated in a more optimal fashion (~2%).

-
**
Optimized
**
: Deduplicated PSOs and RootSignatures in DeviceObjects and DX12 wrapper.

-
**
Fixed
**
: Accidentally allowed to have light volume update happen twice in a frame.

-
**
Fixed
**
: (OpenVR) Disabled messages for asynchronous GetLocalTrackingState/GetNativeTrackingState calls.

-
**
Fixed
**
: (OpenVR) Scaleform HMD quad positioning.

-
**
Fixed
**
: A runtime shader flag with #elif (#elif %_RT) is ignored when a bit mask for runtime shader flag is generated.

-
**
Fixed
**
: GPU bending.

-
**
Fixed
**
: Enabled global terrain normal map on distance.

-
**
Fixed
**
: OpenGL rendering with new Pipeline.

-
**
Fixed
**
: Potential issues with dirty flags in PrimitiveRenderPass.

-
**
Fixed
**
: Primitive geometry cache cleanup.

-
**
Fixed
**
: Crash due to binding of invalid vertex/index buffers.

-
**
Fixed
**
: Made SStreamInfo non-constructable - now has to be provided by the API.

-
**
Fixed
**
: Add validation for resource set buffer count.

-
**
Fixed
**
: Added missing CompiledObject assignment on CloneShaderResources.

-
**
Fixed
**
: Typeless format specifier for 32bit depth (was partially typed).

-
**
Fixed
**
: Refcounting inconsistency for depth buffers (fixes MSAA as well).

-
**
Fixed
**
: Clean up root signature cache in CDeviceObjectFactory::ReleaseResources.

-
**
Fixed
**
: Resource layout validation.

-
**
Fixed
**
: ShadowGen performance when GI is on.

-
**
Fixed
**
: Shutdown crash due to refcounting issues of null resources.

-
**
Fixed
**
: Update shader items with dynamic tex modifiers after object compilation.

-
**
Fixed
**
: Submit pending resource barriers during CCommandList::PatchRenderTargetView as not doing so causes flash rendering corruption on NVIDIA.

-
**
Fixed
**
: Make sure Viewport doesn't get overwritten by FX_SetActiveRenderTargets in CStandardGraphicsPipeline::SwitchToLegacyPipeline.

-
**
Fixed
**
: Jittering shadows due to wrong matrix being used for cascade stabilization.

-
**
Fixed
**
: Added quality-setting reflection to graphicspipeline >= 1.

-
**
Fixed
**
: Added material-alpha back into alpha-tex value calculation.

-
**
Fixed
**
: Capture node saves no output.

-
**
Fixed
**
: CVar capture_frames is broken.

-
**
Fixed
**
: Vegetation pixel shader outputs NaN in opaque pass when e_volumetricFog=1.

-
**
Fixed
**
: Star rendering.

-
**
Fixed
**
: Reset of batch flags.

-
**
Fixed
**
: Reenabled occlusion culling.

-
**
Fixed
**
: Workaround for a gcc4 compiler bug when defining alignment in a typedef with template types.

-
**
Fixed
**
: Record draw call and dip count into correct renderlist.

-
**
Fixed
**
: Shadow casters culling.

-
**
Fixed
**
: Record draw call and dip count into correct renderlist
.

-
**
Fixed
**
: .ui in materials.

-
**
Fixed
**
: (OpenVR) Scaleform HMD quad positioning.

-
**
Fixed
**
: Changed the way timestamps are queried to get more accurate results in dx12.

-
**
Tweaked
**
: Some cleanups in SDeviceResourceLayoutDesc::IsValid.

-
**
Tweaked
**
: Converted depth targets to CTexture.

-
**
Tweaked
**
: Various INDENT-OFF statements to fix broken formatting.

-
**
Tweaked
**
: Removed GPU sync from positive profiler IDs, allow syncing for all negative profiler IDs.

-
**
Tweaked
**
: Added thread information for GFxVideo_Decoder_2+.

##
SVOGI

-
**
New:
**
Analytical occluders prototype. Artist can place additional occluders into scene allowing more detailed indirect shadows. Same system is used for soft indirect shadows from characters.

-
**
**
Refactored
**
**
: Removed Light Propagation Volumes (old GI solution).

-
**
Optimized
**
: RSM rendering for GI.

-
**
Fixed
**
: Reduced ghosting.

-
**
Fixed:
**
 Troposphere upscaling.

-
**
Fixed
**
: Shadow bias problem when GI is active.

-
**
Fixed
**
: Too low light bounce if diffuse texture has 0 in alpha channel.

-
**
Fixed
**
: Enabled support for geom entities (static) voxelization.

-
**
Fixed
**
: DX12 crash.

-
**
Fixed
**
: Too low occlusion from non-vegetation.

-
**
Fixed
**
: Xbox GI shader compiling problem. Added simplified RSM mode.

-
**
Tweaked
**
: Improved specular tracing (for mode 2).

##
Volumetric Fog and Clouds

-
**
New
**
: (Volumetric Fog) Added emissive feature to voxel-based Volumetric Fog. FogVolume and particle can emit light by themselves.

-
**
Fixed
**
: (Volumetric Fog) Potential flickering bug of FogVolume and lighting for Volumetric Fog.

-
**
Fixed
**
: (Volumetric Fog) Particles as participating media not working when e_volumetricFog=1.

-
**
Fixed
**
: (Volumetric Fog) Added r_VolumetricFogSunLightCorrection to fix the sun luminance for Volumetric Fog not matching the luminance for the material shading.

-
**
Fixed
**
: (Volumetric Fog) Internal jitter for sampling position not working when t_scale=0.

-
**
Fixed
**
: (Volumetric Fog) SkyHDR shader's SamplerState slot not matching the Texture2D slot at runtime when e_volumetricFog=1.

-
**
Fixed
**
: (Volumetric Fog) Disabled use of Volumetric Fog in recursive rendering passes.

-
**
Fixed
**
: (Volumetric Clouds) Added missing screen space functionality of Cloud Blockers to GameSDK.

##
DirectX 12

-
**
New
**
: DX12 subresource barriers.

-
**
New
**
: Concurrency Analyzer.

-
**
Optimized
**
: Added pre-hashing of shader-bytecode.

-
**
Optimized
**
: Added second level cache for RootSignatures.

-
**
Optimized
**
: Omitted some fence-value queries by masking - in order to work earlier than currently.

-
**
Optimized
**
: Collect and batch barriers for latest possible moment of submission.

##
Engine

##
Common

-
**
New
**
: Move CryCommon/CryPlatform to CryCore/Platform.

-
**
New
**
: Move CryCommon/CryProfiling to CrySystem/Profilers.

-
**
New
**
: Move newly added files into physical correct location.

-
**
New
**
: Add files missing from waf_files to CryCommon waf_files.

-
**
New
**
: Physically move CryCommon files on disk to match VS filter structure.

-
**
New
**
: Implement ray-cone intersection routine.

-
**
Refactored
**
: CryVR interface files.

-
**
Refactored
**
: Move Yasli to new CryCommon layout.

-
**
Refactored
**
: Rename CryCinematics to CryMovie.

-
**
Refactored
**
: Change all #include directives targeting a CryCommon file to match new CryCommon file locations throughout the whole Engine.

-
**
Refactored
**
: SERIALIZE_ENUM_DECLARE to not declare static variables, avoiding some startup order problems. EnumDescription is initialized when getEnumDescription is first called. IMPLEMENT macros are now obsolete.

-
**
Fixed
**
: Enum serialization and UI. Enum aliases now handled with derived class - can be declared in any order. SERIALIZATION_ENUM_DEFINE must be at global or namespace scope.

-
**
Fixed
**
: Crash when using assert before CryInput is initialized.

-
**
Fixed
**
: Enum serialization - getEnumDescription<Enum> now always returns the same object. Auto-described enums now use an aux structure which references the standard EnumDescription.

-
**
Fixed
**
: Correct ceiling and floor for fixed_t.

-
**
Tweaked
**
: Improved SERIALIZE_VAR macro to handle naming conventions.

-
**
Tweaked
**
: Add AlignmentTools.h to waf_files.

-
**
Tweaked
**
: Add missing "RingBuffer.h" to waf_files.

-
**
Tweaked
**
: Remove duplicate of IDebugHistory.h.

-
**
Tweaked
**
: Tweak crycommon.waf_files layout.

-
**
Tweaked
**
: Remove redundant min/max checks when testing AABB-Triangle intersection and OBB-Traingle intersection.

-
**
Tweaked
**
: Delete unused CryNEON_Math.h.

##
Physics

-
**
Refactored
**
: Move polynomial.h to CryCommon.

##
Network

-
**
Tweaked
**
: Removal of Rebroadcaster, PeerContextView and NETWORK_HOST_MIGRATION.

##
C#

-
**
Refactored
**
: (Mono) Exposed AudioSystem functions.

-
**
Refactored
**
: (Mono) Improved Entity Wrapping.

-
**
Refactored
**
: (Mono) Latest Sydewinder implementation.

##
System

-
**
Refactored
**
: Moved Scaleform functionality into IScaleformHelper interface, which is loaded (if not already linked statically) from a shared library. This allows people without Scaleform source to still compile CrySystem and to also use Scaleform features.

-
**
Fixed
**
: Added standard CryVR CVars to OSVR.

-
**
Fixed
**
: Possible crash in OSVR renderer initialization.

-
**
Fixed
**
: Incorrect inclusion of sce file for posix.

-
**
Fixed
**
: Made some virtual methods unconditional to prevent ABI issues.

-
**
Tweaked
**
: Cleaned up OSVRDevice code.

-
**
Tweaked
**
: Updated to latest OSVR SDK and OSVR RenderManager and separated the files.

-
**
Tweaked
**
: Always pull in Oculus lib. so it inherits compilation settings compatible with CrySystem.

##
WAF

-
**
New
**
: Add a feature to rename #include paths of header and source files to match CryCommon restructuring.

-
**
New
**
: Add a feature to match waf_files file vs. filter to physical files on disk.

-
**
Optimized
**
: Avoid local compilation when building without an Incredibuild multi-core license.

-
**
Fixed
**
: Detect presence of PS4 and XB1 SDKs and use that to determine whether to copy their DLLs.

-
**
Fixed
**
: Error when specifying a module in "use_module" that was not part of the build for e.g. due to the platform configuration.

##
3D Engine

-
**
Refactored
**
: Terrain layer painting is modified to work with new 3D Engine side texture atlas and without using of any Custom Editor side textures. During painting textures look very close to how they will look after generation.

-
**
Optimized
**
: Enabled bindless texturing for terrain base pass and for vegetation "use terrain color" feature,

-
**
Fixed
**
: (VR, Config) Re-enabled default stereo output.

-
**
Fixed
**
: Static instancing crash.

-
**
Fixed
**
: (VR) Re-enable Oculus support.

-
**
Fixed
**
: Sky-dome initialization on level-reload.

-
**
Fixed
**
: (VR, Sandbox) Culling when using Sandbox with attached and enabled HMD.

-
**
Fixed
**
: Missing brushes on Editor start.

-
**
Fixed
**
: Crash on materials editing.

-
**
Fixed
**
: Sandbox might crash on start.

-
**
Fixed
**
: Static Instancing crash.

##
Particles

-
**
New
**
: Added effect param ForceDynamicBounds for effects with too-large static bounds. Added CVar e_ParticlesMinPhysicsDynamicBounds to select which physics modes force dynamic bounds.

-
**
New
**
: (GPU Fluids) Added CVar to enable/disable debug information about GPU Fluid Particle Simulation.

-
**
Refactored
**
: ParamMod.GetValues and GetValueRange can compute individual values or min-max ranges for any domain. Replaced and extended similar functions.

-
**
Fixed
**
: IntegralDragFast avoids blowing up by computing max drag factor and scaling the individual drag values.

-
**
Fixed
**
: Moved assign effect to CParticleEffectObject - both drag-n-drop from Particle Editor and from the Create Object panel work the same way.

-
**
Fixed
**
: Audio and Force generation no longer exclusive.

-
**
Fixed
**
: (GPU Fluids) Bring Fluid Dynamics component to a usable state by fixing the pipeline, tweaking default values and making particle influence adjustable.

##
RC/Tools

##
Tools General

-
**
New
**
: Add a copy of Uncrustify.

-
**
Fixed
**
: (Mono) Select Engine root relative to MonoDevelop binaries rather than CRYENGINEROOT environment variable.

##
Animation

##
Animation General

-
**
Fixed
**
: (Splines) Restored pevious AngAxisSpline implementation to fix rotation animations.

##
Mannequin

-
**
Fixed
**
: Entity cleanup logic in the CMannequinDialog class - solved cleanup crash and resource leaking issues.

##
Action

##
Action General

-
**
Refactored
**
: Remove direct #include reference to CryAction files from other modules and include CryAction for every module as include path instead.

-
**
Fixed
**
: Camera not resetting when exiting game mode after calling SetViewCamera scriptbind.

-
**
Fixed
**
: A memory management issue with a debug string instance being passed across a dll boundary. Removed the previous ad-hoc workaround for this issue to reduce complexity on the CryAction's client side.

-
**
Fixed
**
: Client crash when connecting to servers that did not have sv_pacifist CVar available.

##
Flowgraph

-
**
New
**
: Adds blend feature to the Entity:EntityFaceAt flownode.
**

**

-
**
Fixed
**
: Changing the param of a material on an entity would prevent from changing the entity's material.

##
Audio

##
Audio General

-
**
New
**
: Functionality to calculate the duration of a standalone audio file.

-
**
New
**
: Remove inheritance in Audio Object.

-
**
Optimized
**
: Small tweaks/fixes to the SDL impl.

-
**
Optimized
**
: Optimized setting of FMOD Studio buses to be more efficient.

-
**
Fixed
**
: Where FMOD Studio reverbs stopped decay procedure when the source event was stopped.

-
**
Fixed
**
: Where sometimes environments were not properly set to FMOD Studio.

-
**
Fixed
**
: Crash with overly busy audio debug drawing.

-
**
Fixed
**
: CVar was unregistered with an outdated name.

-
**
Fixed
**
: Parent ambiences not assuming reverbs of inner areas.

-
**
Fixed
**
: Audio trigger names were not being serialized and shown in the UI of Mannequin.

-
**
Tweaked
**
: Updated SDL_mixer to version 2.0.1 and enabled SDL_mixer implementation to play back Vorbis encoded mp3 files.

-
**
Tweaked
**
: Updated FMOD Studio API to version 1.08.02.

##
ACE (Audio Controls Editor)

-
**
Fixed
**
: Middleware icons missing when using the web launcher.

-
**
Fixed
**
: Some placeholder wwise controls were being shown even though they were a placeholder.

-
**
Fixed
**
: Crash when switching audio middlewares.

-
**
Fixed
**
: Crash when connecting implementation controls that live inside folders directly to the ATL controls panel.

-
**
Fixed
**
: Filtering buttons.

##
DRS (Dynamic Response System)

-
**
New
**
: Added an Execution-limit condition (to enable execute-only-once again).

-
**
New
**
: Added an "execute response" action to allow re-using of responses.

-
**
New
**
: Added a "done" port for the send-signal Flowgraph node - which is triggered when the response linked to the signal has finished.

-
**
New
**
: Added a listener interface for drs-signal-processing.

-
**
New
**
: Added a TimeSinceResponse Condition.

-
**
Refactored
**
: Removed the option to queue drs signals delayed (can be achieved with 'wait' actions).

-
**
Fixed
**
: A bug when playing dialog lines without audio and without animation.

-
**
Fixed
**
: Subtitle was not displayed for lines without audio trigger, but with talk-animation.

-
**
Tweaked
**
: Only increment the execution-counter on responses when at least the base-condition was met.

##
AI System

-
**
Fixed
**
: Dealing with normalizing the vector in a safe way now.

##
Game

-
**
Fixed
**
: Material effect for player landing is not spawned with an offset anymore as that lead to the effect along with audio to be spawned below ground if the player looked downwards or vice versa.

-
**
Fixed
**
: Cannot open Abrams Tank in Vehicle Editor.

-
**
Fixed
**
: UIManager didn't load Flowgraphs during initialization.

-
**
Tweaked
**
: Remove obsolete RCJob files. These are now accessible through Templates or the documentation.

##
Known Issues

-
TrackView Editor record button may become inactive while editing keyframes, causing the full sequence to move.

-
If objects are placed above height value 16 on the Z axis, they are not included in the AI navigation area.

-
On rare occasions while using DX12, the game executable may crash when the Airfield sample level is opened

-
When using an NVIDIA card with DX12, content does not render correctly on Oculus headsets.

-
When using Linux, the game executable crashes on level load.

-
Loading vegetation into the Vegetation Editor before a map has been created causes the Editor to crash.
