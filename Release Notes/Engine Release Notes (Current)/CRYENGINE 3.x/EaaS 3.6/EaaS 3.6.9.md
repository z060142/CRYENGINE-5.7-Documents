# EaaS 3.6.9

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/47316993/pages/44963015
- Page ID: 44963015
- Breadcrumb: Engine Release Notes (Current) > CRYENGINE 3.x > EaaS 3.6 > EaaS 3.6.9
- Parent: EaaS 3.6

## Content

Released 17th October, 2014

Make sure you visit the GameCode documentation which has been updated here:
[/docs/static/engines/cryengine-3/categories/1638401/pages/1605726](
Getting Started with Game Code
)
.

And also the
[/docs/static/engines/cryengine-3/categories/1114113/pages/17826279](
ATL for Programmers
)
 article for updated information on Audio programming.

Remember to delete 'loose' SDK content if you've extracted pak files into your build! Otherwise that old loose content will override the new content inside the pak files.

See:
[/docs/static/engines/cryengine-3/categories/1638401/pages/1605746#DirectoryStructure-PakFiles](
Directory Structure - PakFiles
)
 and
[/docs/static/engines/cryengine-3/categories/1638401/pages/1605659#CryPak-Layering](
CryPak - Layering
)

##
Editor

-
**
New
**
: (Flowgraph) Added 'OnSprintStaminaChanged' to ActorSensor flownode.

-
**
New
**
: (Flowgraph) Added surfacetype to phys raycast fg nodes (CE-4550).

-
**
New
**
: (Flowgraph) Output weapon firemode name (string) from WeaponSensor node.

-
**
New
**
: (Layer Editor) Extra layer control buttons to allow easy enable/disable of layers (
CE-3960
).

-
**
New
**
: Added "Convert to GameVolume" function to allow conversion of shapes (watervolumes) into GameVolumes (CE-1739).

-
**
Fixed
**
: (LODGen) Crash when you click Generate LOD Chain (CE-2928).

-
**
Fixed
**
: (LODGen) Crash when mesh contains sub-objects (CE-4566).

-
**
Fixed
**
: (Terrain) 'Sync Radius for all Types' checkbox in terrain editor not syncing radiuses right away (CE-4289).

-
**
Fixed
**
: (Particle Editor) Enabling & disabling effects properly updates emitters. Reverted previous change that retained containers of disabled effects. Disabling and re-enabling all sub-effects now properly restarts existing emitters. Fixed minor update bug with attached geometry.

-
**
Fixed
**
: (Flowgraph) Fixed comment box moving down on undo and import (CE-4608).

-
**
Fixed
**
: Entering game mode after creating a new level with AI/Physics enabled causes a crash (CE-4705).

-
**
Fixed
**
: Reset cloth on game mode switches (CE-2952).

-
**
Fixed
**
: Flowgraph and ModularBehaviorTree Editor are not overriding HyperGraphs CanConnectPorts method anymore (CE-4614).

-
**
Fixed
**
: Memory leak on level loading (CE-4447).

-
**
Fixed
**
: Fixed wind area entity icon disappearing when not active (CE-2720).

-
**
Fixed
**
: GeomCache file dialog pointing to incorrect folder location.

-
**
Fixed
**
: TOD value could be set to minus (enabled CTimelineCtrl range checking) (CE-4401).

-
**
Fixed
**
: Vehicle Editor save functions.

-
**
Fixed
**
: Comment entity now also shows if it's linked to another entity (CE-3926).

-
**
Fixed
**
: Made "reload geometry" re-physicalize everything (CE-73).

-
**
Optimized
**
: (FlashUI) reworked flash UI flownodes.

-
**
Optimized
**
: Tweaked GameVolume script so that default colors aren't purple. Increased default fog density. Added description text to AwakeAreaWhenMoving param.

-
**
Optimized
**
: Uniformed default settings for fogcolor, density and multiplier for Rivers, WaterVolumes and GameVolumes.

-
**
Optimized
**
: Narrowed the arrow shape for Debug:draw:direction flownode (CE-4480).

##
Audio

-
**
New
**
: EntityAudioProxies now handle any number of AudioProxies.

-
**
New
**
: Added CryAudioCommon project for the header files shared between the ATL and AudioSystemImplementations.

-
**
Optimized
**
: Minor audio code formatting and audio logging cleanup.

-
**
Optimized
**
: ATL debug name store is now only present in non-release builds.

-
**
Optimized
**
: Update docomatic configuration to include CrySoundSystem/Common files. Updated docs coming shortly!

-
**
Optimized
**
: Added summary descriptions to the CryAudioCommon headers, small changes and fixes for the existing docs.

-
**
Optimized
**
: Updated library path for Wwise v2014.1 build 5158.

##
Engine

-
**
New
**
: (Tools) Add peak time to statoscope frame profiler.

-
**
New
**
: (CryExporter 3dsMax) Added button
Select in Viewport
 to select items directly from export list (CE-4213).

-
**
New
**
: Support for geom cache physics interactions.

-
**
Fixed
**
: (RC Maya Exporter Collada) Exporting scene as Z-Up only; emulating proper SceneRoot node when it doesn't exist in an Y-Up scene.

-
**
Fixed
**
: (Maya Exporter) Check for duplicate export names now correctly ignores names of the meshes inside of groups (names of such meshes do not produce export names).

-
**
Fixed
**
: (Physics) Clear constraint mask on entity hiding to prevent crash (CE-4607).

-
**
Fixed
**
: (ScriptSystem) IScriptTable::GetValue() returned a dangling pointer when passed a null IScriptTable pointer (CE-4629)

-
**
Fixed
**
: Memleak with non-uniform scaled phys geoms (CE-4610).

-
**
Fixed
**
: Speed scale not working in AnimGeomCacheNode.

-
**
Fixed
**
: (Build) Fixed an issue where Visual Studio 2012 Express edition failed to compile x64 targets because it attempts to use a non-existent toolchain. Now correctly falls back to the installed toolchain.

-
**
Optimized
**
: Remove CPU estimated clockspeed measurement completely. Speeds up boot time significantly.

##
Rendering

-
**
Fixed
**
: (Particles) Crashes in particle sorting (CE-3931). Sorting array now at least as big as particle count, plus over-estimated emissions for current frame. Fixed memory error caused by expired parent particles.

-
**
Fixed
**
: Crash during level switch, invalidated shadowFrustum (CE-4544).

-
**
Fixed
**
: VolumeObject shader: Fixed numSamples if statement. Fixed Jittering param not being toggleable.

-
**
Fixed
**
: Wrong PostAA velocity texture target.

-
**
Fixed
**
: Ambient lights not writing specular in some cases (CE-4611).

##
Assets

Several new example facial animations have been added (Animations/human/male/facial/) however some issues relating to ladders/vehicles have been discovered because of this new setup and will be resolved ASAP.

-
**
New
**
: (Audio) Added bush and leaves rustling loop events and assets to physics project.

-
**
New
**
: Added explosions for all SDK vehicles and implemented in Wwise and Editor.

-
**
New
**
: Added example facial animations. Added new head_a with face anim setup. Renamed existing head_a to head_noanim. Added head_a max file. Updated skeleton FXL file.

-
**
New
**
: Geomcache example brickwall with instancing.

-
**
New
**
: Added Stamina bar on HUD.

-
**
New
**
: Added explosion placeholder to forcefeedback xml.

-
**
New
**
: Added new campfire pfx where the smoke reacts to wind resistance.

-
**
New
**
: Added 3p/Sounds ADBs for Grenade/Shotgun.

-
**
New
**
: Shotgun: Added idle_break fragments. Fixed up several wrong animations. Removed some unneeded proc clips. Fixed ironsights. Added forcefeedback and weapon_lowering fragments.

-
**
Fixed
**
: (UIActions) Fixed Radar/minimap not working. Get being called before resolution information received. Simplified setup.

-
**
Fixed
**
: gotoAndStop error appearing when entering game mode (CE-4656).

-
**
Fixed
**
: Wrong Shotgun model being used in 3p (CE-4540).

-
**
Fixed
**
: Explosion entity sends correct explosiontype (CE-4524)

-
**
Fixed
**
: Added aimAnims block to Shotgun XML to prevent first-spawn issue with Shotgun (CE-4536).

-
**
Fixed
**
: Fixed boat explosion reflection artifacts. Switched from Additive to Alpha Based blend type (CE-2545). Removed tiny smoke particle not visible.

-
**
Optimized
**
: (UIActions) Tidied HUD_3D FG layout. No logic change.

-
**
Optimized
**
: Updated Mannequin setups. All weapons now using main 'item' tag instead of itemClass 'weaponType' tag (rifle -> SDKRifle).

-
**
Optimized
**
: Renamed "Grenade" to "SDKGrenade" to match existing weapon setups. Updated tag in weapon script. Renamed "expl" tag to "grenade". Added grenade to 3p context.

-
**
Optimized
**
: Updated the Abrams main cannon pfx (tank125) = fixed. Also removed the excessive glow on the tracer for the tank cannon.

-
**
Optimized
**
: Cleaned up MaterialFX flowgraphs (CE-4638).

-
**
Optimized
**
: Split out FFEvents to separate ADB for Shotgun to match other weapon setups.

-
**
Optimized
**
: Moved all distance based attenuation logic for waterfall_ambiences inside of blend tracks.
