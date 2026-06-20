# FreeSDK 3.4.0

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/47316993/pages/44963027
- Page ID: 44963027
- Breadcrumb: Engine Release Notes (Current) > CRYENGINE 3.x > FreeSDK Archive > FreeSDK 3.4.0
- Parent: FreeSDK Archive

## Content

##
CryENGINE 3 Free SDK – Build 3696 Changelog

Released April 13th, 2012.

Among the key enhancements free CryENGINE 3 SDK users can look forward to in version 3.4 are:

-
**
Revamped DirectX 11 Tessellation
**

DX11 support and tessellation has come a long way since Crysis 2. Phong, PN triangles and displacement maps, along with no need for pre-tessellated assets, makes CryENGINE's DX11 support among the best in the industry.

-
**
Multi-layer Navigation Mesh
**

The multi-layer navigation is a powerful new and easy-to-use navigation system that AI agents utilize to path-find through game maps.

-
**
Improved Skin Rendering and Eye Shader
**

New scattering approach gives more realistic rendering with fewer artifacts. New settings, checkboxes and sliders for things like oiliness, iris control, colors, pupil dilatation, tessellation and parallax support make CryENGINE character rendering more advanced and customizable than ever before.

-
**
Advanced/Improved/Extended Glass Shader
**

The glass shader is a specialized tool for rendering glass-based surfaces. It can represent a wide range of glass types, including regular windows, stained glass, leaded glass, beveled glass, some crystal types and some types of transparent plastics as well. The improved glass shader now also boasts features such as a dirt layer designed to produce extremely realistic-looking glass surfaces complete with dust and dirt, differential fog and refraction blur.
On top of these key updates, version 3.4 of the free CryENGINE 3 SDK addresses a number of bugs from previous releases and gives developers access to further improvements that include:

-
Improved glass rendering.

-
Geometric light beams.

-
Point light shafts.

-
Time of day based filmic HDR tone mapping.

-
Curves and key tangents for time of day.

-
User controlled per cascade shadow bias through time of day.

-
Improved transitions between levels of detail.

-
Volumetric fog features extended and improved.

-
Improved distance cloud shading.

##
Full Changelog

-
Refactored UI game events

-
Added new UIGameEvent class (moved functions from UIActionEvents to this class)

-
New interface for auto registering to UIManager

-
Continuous update is not automatically paused/restored when filtering/restoring the visible objects inside sandbox. Pausing the continuous update also when jumping into game in Sandbox.

-
Include node indices in navigation graph debug draw

-
DX11 CBuffer Downscale Improvements + fixes

-
Make sure vehicles can use the Multi-layer Navigation

-
Added Overwrite All button to checkout dialog

-
Added FG node to catch and trigger upon animation events set up in character editor

-
Changed UIEventSystems of old game dll to use new event dispatchers

-
HUD3D use correct offsets for different resolutions

-
Now correctly set the alpha for glass phys fragments.

-
Added variable stable fragment size to glass, meaning smaller pieces can stick nearer edges.

-
Coloured glass particle effects to match glass material (Off by default).

-
Enabled glass cvars in release builds.

-
Fixing EngineAssets location

-
Add icon and version number to remote shader compiler

-
Remove some obsolete shaders from the shader list

-
Gamma changes now respect window focus in Dx10/11 (As per Dx9 in DeviceLost state).

-
Support for non-uniform phys scaling (clone-based)

-
Set the web server port for the Remote Shader Compiler

-
Re-added EF_Query( EFQ_D3DDevic )

-
FrameProfileSystem now displays frame time, lost time, and overhead with same averaging method as profile entries.

-
Time of Day: added serialization of key flags for splines

-
Sandbox, Time of Day: added toolbar for Spline editor, dockable frames.

-
Added "Reverse" to MaterialEffect particle hit direction options.

-
Add GeometryBeam inside the Sandbox shader list

-
Remote Shader Compiler to VS2010

-
Set ai_MNMEditorBackgroundUpdate to 1 by default

-
Shadowpool caching support, blockpacker usage fixed

-
Being able to choose an entity class category from within Lua scripts and external entity class handlers used inside the Editor, instead of always putting them into "Default"

-
Added callback to handle glass system cvar changes. Tidies up the temp crash fix.

-
Enabled the new glass system by default when in multiplayer.

-
Implements the light animation by (ab)using the light node in the movie system.

-
Adds position/rotation animation support to the light animation system.

-
Makes it possible to scrub a light animation through the regular TrackView interface.

-
Move more textures to Engine\EngineAssets

-
Lua debugger GUI improvements

-
Added GameScript projects to GameCodeOnly solutions

-
Implements the film curve preview in the Time Of Day dialog.

-
New UIEvent receiver and sender helpers for variable args and arg count

-
Some helper functions for easier UIEventDesc creation

-
Allow to use Vec3 as type for UIEvent FlowNode ports

-
Rework TemplBeamProc 1. Dust 2. Air Turbulence 3. Volumetric Shadows

-
Re-add start and end colors

-
Simple tool to check flags

-
New glass shader featuring: Improved lighting consistency. Support for opaque layer, tint color map, alphatest shadows using opaque map, blurred refraction (High end only). Removed support for alphablended non-refractive glass. Tidied up legacy code.

-
Glass Shader: Added diffuse multiplier to vertex alpha.

-
Glass Shader: Added global opacity multiplier.

-
Enable geometry instancing by default

-
Changed UIEventSystems to use new easier style (new game dll first)

-
Improve default values for film curve tod settings

-
Add MotionBuilder 2012 exporter to be built in the tools solution file

-
Updated UpdateCryGameScriptsProject

-
HUD3d position C2 calculation

-
Database Save button now enabled/disabled depending on count of modified libraries.

-
Added cvar to define if _mp should be auto added to sound files on mp

-
Enhanced particle MaterialEffects, allowing direction type to be specified per-effect, same as other effect modifiers. Compatible with ealier XML that specifies it per group.

-
Allow lazy updates for flash elements

-
Allow to override dyn tex with from uielement

-
Only render uielelemnt to dyn tex if needed (with lazy render flag)

Optimizations:

-
Removed useless GUID info from ParticleEffects.

-
Resizing and "Look & Feel" of the solid panel

-
Perf improvements to glass triangle hashing loop.

-
Saving of ~300 bytes per glass RN by removal of temp vars and class restructuring.

-
Swapped a large continuous glass array for a smaller cyclic one. Up to 40kb PC and 10kb consoles saved.

-
Glass impact decal params are now only calculated once instead of every frame.

-
Using CTRL + Middle Mouse to add/remove a flowgraph breakpoint

-
ITimer and FrameProfile systems now consistently use CryGetTicks(), replacing runtime tests and function pointers.

-
Removed unused members in ProfilerInfo.

-
Added state to SParticleUpdateContext to reduce repeated computations.

-
Integration of multi-particle ParticleEmitter.EmitParticles() change.

-
Sped up emit rate/count computation in SubEmitter.EmitParticles(). Cache EmitCountScale, avoid calling GetExtent() during particle emission.

-
Removed SAnimationDesc struct from code and new AnimGraph files, following C2 behavior. Replaced with runtime functions to compute SAnimationMovement and get SAnimationSelectionProperties*.

-
Removed unused GetAnimationLength functions.

-
Adjusting view distance ratio on a few object for consistency

-
Sandbox Rollupbar resizing and "look & feel"

-
Cleaned up gamma ramp calculations, now round results correctly.

-
Prevent execution of sound creation code with an empty sound name string and display of an unnecessary error message to the log

Refactoring:

-
Little simplification to tod sun shadow cascades control/removed hdr contrast control

-
Tweakable per-cascade shadow bias

-
Significantly improve shader compilation speed by replacing fxc with cryfxc

-
Move cryfxc into PCD3D11/v005

-
Adding d3d compiler dll to be complete

-
Rename %DETAIL_MAPPING back to %DETAIL_BUMP_MAPPING to maintain backward compatibility

-
Added inline tick functions to ITimer: GetTicks(), GetTicksPerSecond(), TicksToSeconds(). Removed silly virtual TicksToMillis/Nanos(). Also added GetNonFiberTicks(), which subtracts FiberYieldTime(), simplifying a lot of code. Removed redundant tick functions and members from FrameProfileSystem.

-
Movd OPT_STRUCT facilities from TypeInfo.h to platform.h. Made member and acccessor names more consistent: _Member, Accessor(), Setter(val)

-
Remove not needed ifdef GAME_IS_CRYSIS2

-
Branch refactoring

-
Update the ToolkitPro .dll inside the Tools directory

-
Removed support for deprecated fog mode. Prerequisite for coming volumetric fog enhancements.

-
Add parser support for shader interpolator arrays

-
Terrain non linear alpha blending factor support ("blend layer")

-
Updates for per-light shadow bias / lights specular was mismatching sun specular / tone mapper curve tod control / brute force dof quality mode+ resolution scale fix

-
Separates the HDR parameters and packs together with the film curve preview in the TimeOfDay dialog.

-
Increase the range of volumetric scale

-
Move light beam update to a new shader

-
Adapting 3dMouse default values

-
Validate shaders for fog and water volumes

-
Removing geom_instancing=0

-
Small tweak to vignetting texture (was a bit overkill)

-
Remove grass material pre-multiply on diffuse colour

-
Removing per art request cvdetailscale (and old cvnumlayers)

-
Moved CryCG to mingw-gcc based builds

-
Move two more textures to Engine\EngineAssets

Added:

-
Added missing file that's being referenced for grenades

-
Adding scripts only RC Job

Deleted:

-
Deleted StaticSymbols.cpp (obsolete)

-
Delete no longer needed test file

-
Delete depreciated Tool Box config file

-
Delete depreciated Modelling Panel file

-
Delete unused/unavailable item from equipment pack

-
Delete depreciated file (Tools -> User Commands)

Tweaks:

-
Updated AsianCoaxialWeapon to use HMG weapon sounds. Lowered rate of fire for visuals to match audio.

-
Removed GAME_IS_CRYSIS2 from AI system, replaced with local define in AI system if new flight navigation should be used

-
Better facing for dynamic flash tags

-
Adjusting new script separation RC Job processing

-
Adding R_HDRBlueShift = 0.

-
Adding new glass decal controls, default values.

-
Fixed issue with unused grenade types (flash, emp, smoke) spamming console. Fixed spacing. Fixed issue with incorrectly pointing helper.

-
Removed vehicleCollisionDestructionSpeed="4" param from MH60. Was blowing up far too easily when nudging other vehicles.

-
Removed commented out CVars. Changed r_HDRRendering default to '3'.

-
Lowered grenade damage (250 -> 150). Lowered min/max radius 5/15 -> 2/10. More realistic behaviour for a frag grenade, less chance of killing yourself.

-
Keeping the joint velocities when "ragdollizing" the actor. Better for the Hit/Death Reactionsystem (death reactions).

-
Sandbox, Time of Day: More sensible default zoom settings, cleanup.

-
Added isPassengerShielded="1" to gunner seat for protection against rockets.

-
Tweaked damage and radius on vehicle explosions. Fixed issue with Abrams explosion not causing reaction (delay set to 0.2).

-
Updated path to new cloth asset

-
Updating size of glass texture atlas.

-
Changed the default TOD to suit new filmic tone mapper (r_HDRRendering 3)

-
Ensured lock pointer is NULL before attempting to lock to help track down a possible failed LockVB crash

-
Renamed CryEngine_GameCodeOnly to CryEngine_GameCodeOnly_LEGACY

-
Small code cleanup

-
Adjusting RC Job for new script processing

-
Tweak default TOD - decreased DOF settings

-
Adding ai_MNMEditorBackgroundUpdate to system.cfg to generate nav mesh in editor whilst not the primary focus

-
Removed upper limit for maximum players in multiplayer

-
R_shadowsstencilprepass const cvar set to 2

-
Removed hardcoded weapon attachment definitions, instead loaded in a data driven way.

-
Made some glass index types more explicit to help avoid errors.

-
Updated glass decal atlas - Slightly increased white-levels on larger break pattern.

-
Removed glass system cvar from multiplayer.cfg as now globally enabled.

-
Renamed CryEngine_VS10.mk to new name as well

-
Changed 0xCE 0x94 to delta

-
Added canary for CRenderObject id overflow

-
Tweak HMMWV - added dynamic light for headlights

-
Disabled the game side stealth-o-meter code in the Target Track Threat Modifier. CL676413 - !B Fixed issue where the visual stimulus would be pushed down because the outThreat wouldn't be set by the threat modifier.

-
Removed unnecessary file copy and linker flag

-
Minor cleanup of make variables

-
Reduced smart path follower look ahead distance to 0.33 meters instead of 10

-
Updated system.cfg to clarify sys_spec is only for Launcher and not for Editor

-
Cleaned GameCodeOnly solutions

-
Character shader refactoring/cleanup.

-
Update multiplayer.cfg - Removed several duplicate CVars. Removed graphics related CVars that shouldn't be MP specific and are defined in main CVarGroups (viewdistratios, etc). Removed obsolete CVars.

-
Removed unnecessary UI warnings

Fixes:

-
Sandbox will now notify the designer if they are trying to "Export to Engine" while the navigation data didn't finish the processing operation. Also Launcher will load the navigation data even if there is a version inconsistency between the MNM configuration file and the exported data

-
Fix the result value returned by the RayCast in case the ending triangle is not acceptable.

-
Small fix due to renamed GetUserName

-
DX11 CBuffer Downscale Improvements

-
Disabled warning "Could not read AI Cover Surfaces" when there are no Cover Surfaces on the map

-
Crash when drawing debug information for formations

-
Fixed Entity Pool

-
Fixed GetOutputXMLFileName if empty string is passed

-
Time Of Day: Fixed creation of property nodes after re-opening the dialog box

-
Fixed: HitDeath Reactions didn't consider caused damage for explosions

-
Fixed: HitDeathReactions never checked if ragdollizing the actor is allowed

-
Fix global initialisers in x64 release builds

-
Fixed: Possible infinite loop while loading malformed Lua breakpoint information from breakpoints.lst

-
Improved Scoped Time Logger

-
Fixed potential crash in CStructInfo.FindSubVar

-
Fixed: Readded Game Token type not set correctly (always used type string, bad for network serialization)

-
Move into Compiler from typo'd directory.

-
Removed double-triangle hash on glass node initialisation.

-
Fixed a case where glass phys frags with id 0 were using garbage geometry.

-
Fixed: No Bird boids animations

-
Blend layer color input fix for vegetation

-
Crash fix for MP if no game mode is set

-
Fixed CSaltBufferArray::IsValid

-
Fixed: Missing caused damage parameter when notifying the HDR system (Collision)

-
Final fix for x64 static linking

-
Fixed: Weird living entity behavior on non terrain ground.

-
Fixed health not updated on hud

-
Fixes the issue of 'r_measureoverdraw' not working in DX11.

-
Fixed: Crash in BreakableManager

-
Fixed: Wrong path to default CGF

-
Shadow tweaks

-
Finally fixed crash in profile system when changing profile_allthreads from 0 to 1.

-
!I potential multithreading problem with rigidbody mass recomputation

-
Enable flowgraph nodes Input:Key and Input:Action in multiplayer

-
AnimationGraph: Fix for animation randomizer not being properly called, resulting in unrandomized repetition when multiple characters enter the same state

-
Tick timing fixes and cleanup:

-
Fixed inconsistencies in CryGetTicks, QueryPerformanceCounter, and QueryPerformanceFrequency. CryGetTicks is now equivalent to QPC on all platforms, fixing some profiling results. Win32/64 use Windows QPC rather than RDTSC, as it's guaranteed thread-safe, and has acceptable performance on Profile builds.

-
Sandbox: "Inside the Time of Day window, groups of keyframes cannot be deleted." -

-
Sandbox: "Time of Day: When first opening the Time of Day, the timeline scrubber does not render/refresh"

-
Fixed: Material Picker doesn't pick correct submaterial

-
Fixed: Don't receive update item callbacks when setting the initial values in the TimeOfDayDialog

-
Fixed wrong vcproj file settings in Project.mk

-
Fix dissolving issues on sprites causing flickering

-
Sprite-model dissolving quality improvements

-
Fix up lod dissolving issues on view change

-
Dissolve improvements - distance based, cross over LODs to minimise volume differences and screen-space noise

-
Implement dissolve to-from nothing/bottom LOD/sprite

-
Fixed D3D11 staging texture leak - introduced pool of staging textures

-
Ensured that staging textures only get freed on Unlock, if they were allocated as a result of a Lock

-
Fixed log(0) FPE

-
Fixed: Footstep sounds and player water interaction not working

-
AnimationGraph: Additives Modifier will now correctly end looping animations even if multiple characters are in the same state

-
Duplicated cvar registrations

-
Compile fixes for VS2010, plus fix for long running shader servers

-
Fix shader lists being left as .tmp files if rename fails (adds same 5s retry as with delete of old .txt files)

-
Removed non-ansi characters that makes errors when building with asian locale

-
Correctly adding the mnm data file (.bai) to the level.pak

-
Renamed IUIElement to IUIObject since it conflicts with IFlashUI

-
Crashfix if shader error message occur while platform os is not initialized yet

-
Fixed DebugCallStack::FillStackTrace in 64-bit mode

-
Fixed: Expended ammo was never reset correctly when dropping/picking up the weapon.

-
Various fixes for pointer checks, missing initialisation, incorrect asserts, unhelpful log messages, bad indentation.

-
Fixed: Puppet range container was never reset. Was constantly growing inside Sandbox.

-
Alpha value now used for refractive particles on blending as well as bump scaling, for proper results with overlapping particles.

-
Fixed FPE in ParticleContainer.ComputeUpdateContext when TurbulenceSize was small.

-
Fixed correct editor set level

-
Fixed function BasicActor:InitialSetup

-
Fixed compile error in debug win32

-
Refactor instancing RT flags to reduce shader combinations

-
Fixed "ai_DebugDrawVolumeVoxels" and removed (unused) volume hidespots-related code

-
Fixed basic event hanlder

-
Fixed correct windows event handlint

-
Temporary crash fix for new glass system

-
Static analyzer warnings fix

-
Fix crash when a texture is used for rendering which was created during the precache phase

-
Fixed assert in Debug-Renderer

-
Compile fix + fix for gs tweakables not being properly set/declared

-
Ensure right view projection matrix used for waterfoginto

-
Fix Color shift bug. Renamed the generation params

-
Couple more shader compilation fixes/cleanups

-
Register class otherwise renderer will not be able to create render window

-
Don't add bullet impulse if there was no rendermesh hit

-
AI: CGoalPipeXMLReader::ParseGoalOp (COPWait does not work for XML goal pipes)

-
Fixed: Full recursive clone for archetype entities properties table

-
AI: CETHR-1075: SIGNALFILTER_SUPERFACTION always sends signal to Player (regardless of faction)

-
An issue with multiple phys areas affecting an entity

-
Fixed: Boolean properties didn't work when using external entity property handler

-
Some fixes to linked scaled physics objects

-
Fixed: Typing in new helper directions didn't update correctly the actual helper rotation in the Vehicle Editor. Only worked when rotating it in the viewport.

-
Fixed static linking of dedicated server without staticsymbols.cpp

-
Fixed mem overwrite crash in WriteVerticesIndirect, and removed implicit container count limit

-
Fix AnimGraph file compatibility with new cvar which indicates AnimDesc objects in ver 63 files.

-
Re-enabled USE_SELECTION_PROPERTIES define, as AnimationSelectionProperties required for pre-Crysis2 AnimGraph code.

-
Lightbeam Hot Fix

-
Fix shader compilation bug

-
Fixed: HitDeath Reactionsystem health thresholds were never used

-
Fixed: TacticalPointSystem AvoidCircle not working correctly

-
Fixed: Display name sometimes not set to an empty string for the Material Picker Tool

-
Removed missing files from Editor project

-
Added free_container of s_pWaterHitsMGPU to avoid level leak

-
Fixed aux geom level leak

-
Fixed memory overwrite in terrain serialisation

-
Glass depth fog correctly uses refracted depth.

-
Instancing-related shader compiler error fixes

-
Preset wasn't specified (from now on it uses "Gradient" preset)

-
Had no crytif settings: now uses preset=DiffuseLowQ

-
Had no crytif settings specified, now it's HDRReflectionsRGBK_high

-
Fixing wrong preset used, now it's HDRCubemapRGBK_highQ

-
Adds mips to noise texture

-
SetMaxWaterDepth and SetMinWaterDepth use the wrong depth value in cm. They multiply the value in meter twice.

-
Fixed invalid index buffer sizing on glass fragments.

-
Removed redundant draw attempt on glass fragments.

-
Removed double offset in DX11 DevBuffer updates.

-
Sprites popping in and out.

-
Fix juddering sprite quads

-
Initialise LOD transition state on vegetation to prevent lots of dissolves when turning

-
Cut down on sprite updates due to light info changing

-
Sprite/model lighting differences - write more upward normal for sprites to receive more ambient light.

-
LOD/dissolving issues - account for instance scale in sprite switch distance

-
LOD popping/sprite accuracy - fix editor tool to allow artists to clear rotations on vegetation

-
Fixed missing sprites if vegetation lod0 mesh is not streamed in yet

-
Default to least detailed LOD for sprite generation - Grass sprite fix with new sprite system.

-
Fixing the debug draw of the path with the MNMPathStart and MNMPathEnd tag point. It now correctly checks if the path was found to add the start and end position to the path point.

-
Allow path and raycast debug also without MNMDebugLocator and minor code adjustments for the RayCast over the MeshGrid

-
Add AlphaBlendShadows in the shader parser for the new beam shader

-
Fixed Multi-layer Navigation menu items

-
Time Of Day: Time and Speed settings are always saved - after editing and dialog closure

-
Some fixes to articulated kinematic objects

-
Fixed: ZeroG update ignores global gravity

-
Fixes path to new engine assets dir

-
X64 relese fixes

-
Fixed CullRenderer crash due to uninitialized values

-
Fixed error in devirt when providing a path with ends with a path seperator

-
Abbreviated SpecFromDiffuse shader param names so that they fit in the material editor without resizing the labels

-
Fixed inverted zoom adjustment for particle Max Distances.

-
Some fixes to player-player collisions

-
Fixed: AI Actors not triggering Area triggers

-
MD: Fixed compile issue for MotionBuider plug-ins.

-
Fixed UIInput to be usable with controller analog stick as well

-
Fixed: Invalid point access in curved editor control

-
Safety guard for potential tone mapper updates with incorrect 0..1 mapping

-
Shader compilation fixes

-
Fix shader compile error

-
Couple more compile fixes

-
Fixed: Music Graph doesn't invalidate correctly the panels after loading a new graph

-
Fix for shadows batching into scene normals alpha channel (when shadows disabled, shadows term was glossiness)

-
Don't create shaders which are requested from compressed shaders only

-
Fixed documentation of console variable "ai_DebugDrawNavigation"

-
Fixed: Possible Crash when removing material effects FG content

-
Fixed typo in rope node that was using position as U texture coordinate.

-
Removing unexisting old file from DedicatedLauncher and Launcher

-
Fixed: Crash on chainloading a level on a Dedicated Server due to not unloading the previous level before changing the game context

-
Particle Effect Enable/Disable menu commands now modify library.

-
Fixed: Opening/Closing prefab or group didn't update the prefab flowgraph list correctly

-
The following shaders/features are removed: metal, custom, rain layer
