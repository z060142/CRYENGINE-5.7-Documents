# FreeSDK 3.3.9

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/47316993/pages/44963026
- Page ID: 44963026
- Breadcrumb: Engine Release Notes (Current) > CRYENGINE 3.x > FreeSDK Archive > FreeSDK 3.3.9
- Parent: FreeSDK Archive

## Content

### CryENGINE 3 Free SDK – Build 3410 Changelog

Released February 23rd, 2012.

**Major New Features:**

- DX9 Parallax Occlusion Mapping (POM)
- DX9 Screen-Space Directional Occlusion (SSDO)
- DX9 Particle Global Illumination (GI)
- New “Very High” graphics configuration
- Added Scaleform support (v3.9.93)

**Important Updates:**

- Improved SLI/CF support
- Improved 32-bit Editor support
- Improved support for 5.1/7.1 surround sound setups
- Improved support for Windows font sizes
- Improved Sandbox UI
- Added Visual Studio 2010 support
- Removed Visual Studio 2008 support

**Full Changelog:**

- Added UI Emulator
- Added UI Actions
- Added sample HUD & Launcher menu
- Fixed multi-GPU (SLI/CF) flickering issue
- Fixed issue with NVIDIA driver support for 32-bit Launcher/Editor
- Added new surface explosion effects
- Restored particle lifetime curves for alpha, size, etc
- Fixed falling leaves & ground smoke graphical bugs
- Added and reworked existing sound reverb presets
- Added aquatic plants
- Fixed seagull boid error
- Cleaned up and reworked weapons project (sounds, structure)
- Cleaned up and reworked environment project (sounds, structure)
- Fixed LODs of beach trees
- Added LODs for various vegetation assets
- Added new assets for Forest level rework
- Reworked Forest level & improved quality of level, including assets, terrain, area shapes, etc
- Added POM textures for Forest
- Added new destroyed texture for vehicles
- Fixed tire explosion sound
- Fixed red dot for Rocket Launcher not working
- Updated props prefab library with many houses included interiors
- Improved soil & wood impact effects
- Updated ocean material for Forest
- Improved Flowgraph Debugger (Support for Breakpoints)
- Improved surface effects for vehicles
- Refactored vehicle pfx and vfx libraries
- Fixed empty Rocket Launcher effects
- Improved SCAR muzzle flash
- Added SCAR loop tail sounds
- Added AI character Civilian, behavior "Wander between points of interest"
- Added boost functionality to all vehicles
- Improved house/barrel LOD quality
- Added support for AI territories & waves for vehicles
- Adjusted vehicle debris pooling to improve memory management
- Added more control over XYZ detail material slope
- Fixed vegetation bending issues
- Fixed crash when using light shapes
- Fixed bi-directional rotation params for particles
- Fixed stack overflow issue for Win x64
- Fixed level heap violation associated with level unload, temp surfaces and fog volume containers
- Many adjustments to the sound system
- Many adjustments to voxel system
- Fixed crash on Launcher start-up and ALT+TAB functionality
- Fixed LOD loading bug
- Further improvements to Asset Browser
- Fixed geometry issue with light objects
- Fixed potential crash if no top animation exists in layer for hit death reaction
- Fixed crash if no raycaster exists anymore
- Fixed potential issue when animation controls an entity directly
- Fixed potential crash in renderer
- Fixed DOF linkage error
- Fixed DX9 vertex decl. issue
- Added Mute button to Sandbox UI
- Fixed incorrect texture reference in default vehicle lights
- Fixed fakeLight property not working for vehicle lights
- Fixed terrain SetWaterLevel not updating water level in physics
- Fixed environment probe crash
- Fixed issue with Rocket Launcher only dropping after projectile had been destroyed
- Enabled terrain shadow casting on all specs except Low
- Re-enable Fresnel tweaking for water
- Enable dynamic textures and projector texture
- Fixed issue with non-actor entities not receiving hits
- Fixed Character Editor crash when using Morph Targets
- Fixed projection problems with bump map decals applied on vegetation objects
- Fixed issue with pickable items and AI weapons
- Fixed boid animations
- Made several adjustments to boid code
- Fixed issue with under water sound mood
- Fixed particle issue when TurbulenceSpeed < 0
- Fixed rare Editor crash
- Improvements to rigid entity / fluid interaction
- Fixed close attack issue with AI losing sight of player
- Fixed rare issue where using "Save As" in Editor resulted in the.cry file being deleted if an error occurred
- Improved ocean particle interaction based on wave height
- Added ability to define tire explosion particle effects (instead of being hard coded)
- Added ability to define custom params for Rocket Launcher RDS (instead of being hard coded)
- Updated FMOD (4.38.04) binaries - Fix for 5.1/7.1 surround sound crash
- Fixed memory leak in Editor
- Improved emitter debug bounding box drawing, scales correctly, alpha support, etc.
- Improved vegetation profiler
- Allow water volumes to be turned on / off
- Improved scope view for Rocket Launcher
- Fixed crash for using Windows Font > 100% in size
- Fixed shadow disappearing when light props are modified
- Fixed 3rd person camera reset when changing seats in vehicles
- Fixed crash when using broken_mtl option in surface type
- Fixed issue with voxel LOD seams
- Fixed hot reloading of animations in Character Editor not working
- Fixed animation events at 0.0f not triggering
- Fixed updating of current ammo pool on ammo pickup
- Updated latest EAX code
- Fixed Animation System Assert on startup (last unloading of DBA)
- Fixed Animation System Assert in PoseBlenderAim
- Fixed Focus and confine cursor problems in the Launcher
- Fixed issue with LookIK
- Fixed Time of Day synchronisation
- Fixed infinite ammo bug
- Fixed white spec on the rocket launcher scope glass and renamed ids
- Fixed ammo pool not updating on pickup ammo
- Added some missing textures spec & ddn
- Fixed rendering bugs related to vegetation wind
- Changed pfx modifications to use only one library. Now all weapons use the weapon_fx.xml
- Adjustments to civilian AI & reaction to the player
- Updated MaxCryExport: disable export of vertex animation by default
- Fixed VehicleLights flownode not working
- Added ScriptBind and FlowNode for loading TimeOfDay files
- Fixed Crash on opening WheelMaster dialog in the Vehicle Editor
- Fixed Vehicle Editor crash after closing WheelMaster dialog
- Fixed AI Debug Draw TagPoints
- Fixed Starting 2 material effects while using melee attacks ("No Surface Type") and wrong direction
- Updated bullet effects for most surfaces
- Improved dock area assets, collision proxies, LOD’s, scale of objects
- Fixed collision issue on lower area of light house
- Added multiple improvements to decal assets quality
- Added new TOD Street light prefab
- Added Tractor sample asset
- Updated Resource Compiler
- Renamed BehaviorSelectionTree to SelectionTreeEditor
- Adding Auto Backup option in the File menu to easy enable/disable the auto backup of the level
- Updated XT Toolkit
- Being able to start animations from Lua with animation driven motion
- Rename DefaultVehicle to EmptyVehicle
- Updated Editor tips
- Improves the filter edit control behavior in the node tree pane of TrackView by allowing a tab-switch of current matches
- Added ability to change order of track events in the ‘Edit Events’ dialog
- Added quick access for Entities using the Animated Character Extension in the context menu
- Improved civilians reaction to player
- Allow moving keys to the time between 0 and the sequence start time.
- Maya: Validate message control system. Allow some validation messages to be disabled by the user
- Maya: Getting UDP from bone geometries into the game
- Point Light Shaft Properties added to light entity
- Audio Caching for Items
- Added possibility to check for matching rows/colums and wrong ordering in Material Effects with setting mfx_debug to 3
- Collada: Changed the rotation from Y-up to make the facing correct
- Added ScriptBind and FlowNode for loading TimeOfDay files
- Remove old key dialogs from TrackView
- Updated the SDK character model
- Maya: Plugin version update
- Improve the naming of director nodes in TrackView
- Fixed Terrain collision enabled icon being backwards
- Fix broken undo/redo of keys and splines after redo adding a entity to TrackView
- Improved default lighting setup in Character Editor and Animation Graph Editor
- Launcher: Level.cfg are now loaded
- Fixed picking an object inside a group/prefab not working
- Fixed Autostarting a TrackView sequence doesn't hide the player
- Fixed two-handed pickups
- Re-factored graphics configs and removed redundant CVars

**Vehicle Updates** Speedboat

- Tweaked material & fixed surface type errors
- Many adjustments to damage behaviors and effects
- Improved wake/spray effects
- Improved 1st and 3rd person cameras
- Added ability to custom define wave effect in XML file (instead of being hard coded)

Abrams

- Added gun overheat effect for Abrams, fixed errors
- Updated Abrams material
- Fixed faulty left tread
- Added recoil animation for main cannon
- Many adjustments to damage behaviors and effects
- Added new sounds and states (engine stop, exhaust smoke puff, etc)
- Increased main cannon damage, improved effects & sounds
- Added lights to Abrams
- Tweaked main cannon projectile to be visible
- Added MP modification to Abrams to give separate driver/gunner control
- Fixed inaccurate Abrams damaged model

MH60 Blackhawk

- Fixed decal issue & made general improvements to material
- Added new texture for downwash effect & improved environment interaction effects
- Many adjustments to damage behaviors and effects
- Added navigation lights toggle
- Added new sounds and states (engine stop, exhaust smoke puff, etc)
- Fixed control issue when helicopter is at its highest limit
- Fixed controls locking up when using gamepad
- Improved handling of rotor animation, uses engine animation, not hard coded
- Added ability to adjust velocity damping via XML instead of hard coded

HMMWV

- Updated HMMWV material
- Many adjustments to damage behaviors and effects
- Improved surface interaction and effects
- Many tweaks to vehicle handling, performance & environment interaction
- Improved 1st and 3rd person cameras
