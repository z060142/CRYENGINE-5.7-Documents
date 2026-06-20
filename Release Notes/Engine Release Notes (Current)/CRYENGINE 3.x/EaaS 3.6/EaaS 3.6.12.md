# EaaS 3.6.12

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/47316993/pages/44963018
- Page ID: 44963018
- Breadcrumb: Engine Release Notes (Current) > CRYENGINE 3.x > EaaS 3.6 > EaaS 3.6.12
- Parent: EaaS 3.6

## Content

Released 28th November, 2014

##
Editor

-
**
New
**
: If material is in pak file, offer option to extract from pak file instead of explore.

-
**
New
**
: Added "Clear Registry Data" to Tools menu. This should make fixing any issues with shortcut keys safer and easier to fix (still WIP and doesn't catch all elements just yet) (CE-4155).

-
**
New
**
: Added (Editor) tag for displayInfo when in Editor.

-
**
New
**
: Added additional FOV presets.

-
**
Fixed
**
: (LensFlare) Level libraries don't load correctly (CE-2950).

-
**
Fixed
**
: Caustics intensity control can now be set to very low values (CE-1423).

-
**
Fixed
**
: Error dialog window doesn't receive focus (CE-1609).

-
**
Fixed
**
: Register entity type flownodes after the game.

-
**
Optimized
**
: Removed unsafe behavior that objects inside groups can be set to different layers (CE-4743).

-
**
Optimized
**
: Refactored Prefabs (Manager, Menu, Panel).

##
Engine

-
**
New
**
: Added e_DebugDrawFilter CVar to filter Helper/Dummies by name on assets with e_DebugDraw 15 activated (CE-4845).

-
**
New
**
: Allow cloth to be attached to ropes.

-
**
Fixed
**
: (Particles) Cubemap update always requested for new emitters; fixes flashing caused by invalid cubemaps (CE-4526).

-
**
Fixed
**
: (Particles) Fixed stretching again; now consistently stretches only in selected direction (CE-4900)

-
**
Fixed
**
: (RC ColladaLoader) Computing/writing proper node transforms for LOD nodes.

-
**
Fixed
**
: (MergedMeshes) Unable to change view distance ratio.

-
**
Fixed
**
: (EntitySystem) Area manager events are now also sent for immediate events (CE-4879).

-
**
Fixed
**
: Fix to fully locked rigidbody constraints "flip".

-
**
Fixed
**
: Missing no-stream flag, which caused a crash when turning texture streaming off (CE-4870).

-
**
Fixed
**
: Light bbox does not count with area light dimensions (CE-4934).

-
**
Fixed
**
: GroupID use wrong integer type.

-
**
Fixed
**
: Potential cloth attachment point fix.

-
**
Fixed
**
: Fixed refcounts for vcloth and skins.

-
**
Fixed
**
: Clean bone remapping tables for skin and vcloth objects.

-
**
Fixed
**
: Std::vector problem of use among different DEBUG/RELEASE.

-
**
Fixed
**
: Apply not-physicalized flag to RigidBodyEx immediately. Prevents requirement of manual script reload (CE-4914).

-
**
Fixed
**
: Put PakEncrypt.exe into the correct directory when it is built (was one directory too high).

-
**
Fixed
**
: Lighting fixes after area light integration: Fixed light projectors when tiled shading is enabled. Fixed ambient area lights when area light support is off to keep compatibility with previous behavior. Skip regular rectangular area lights when support is disabled. Draw area light helpers only when light is selected.

-
**
Optimized
**
: (Cgfsaver.*) Integrated proper separation of ResourceCompiler's and engine's code.

-
**
Optimized
**
: (MaxCryExport) Integrated removal of OpenMP (to have no dependency on OpenMP's .dll).

-
**
Optimized
**
: (MaxCryExport) Renamed/removed functions called ProcessXXX in favor of SaveXXX functions; added const.

-
**
Optimized
**
: Expand texture data size tables to cover src sizes, saves 4s on merged level load.

-
**
Optimized
**
: Assume HDD media type to begin with for mips, saves .5s on merged level load.

-
**
Optimized
**
: Unify CPythonToCryStringConverter & CPythonToMFCStringConverter.

##
Renderer

-
**
New
**
: Shadow cascade blending (see video below!).

-
**
Fixed
**
: Enable NullRenderAuxGeom for null renderer, fixes r_debug_renderer_show_window for dedicated servers to debug server side physics proxies.

-
**
Fixed
**
: Only update static shadow caster list when static map has been updated on all GPUs.

-
**
Fixed
**
: Shadow flickering fix for frame jittering.

-
**
Fixed
**
: Incorrect vertex index sizes. Fixes issues with light clip boxes (CE-4903).

-
**
Optimized
**
: Remove old Watervolume content from Water shader (CE-2533).

-
**
Optimized
**
: PipelineProfiler/r_stats 16 - text is jumping around (CE-1936).

##
Audio

-
**
New
**
: (ACB) Loading of controls done in the audio system implementation.

-
**
New
**
: (ACB) Removed the need of a model for the audio system implementation.

-
**
New
**
: (ACB) Renamed classes to be consistent with engine audio implementation.

-
**
New
**
: Introduced specific define to enable/disable audio logging and re-enabled Wwise specific logging.

-
**
New
**
: Updated Wwise API to v2014.1.1 build 5179.

-
**
New
**
: Fallback to loading samples if not found when executing an event.

-
**
New
**
: Added Localization handling.

-
**
Fixed
**
: Missing SDL .dlls.

-
**
Fixed
**
: Added a Fatal Error when trying to allocate memory with custom alignment set to zero.

-
**
Fixed
**
: Vehicle serialization to stop all running audio events on the vehicle for fast load.

-
**
Fixed
**
: Iterator invalidation on the debug name store and fixed threading issue in the AudioSystem.

-
**
Fixed
**
: Loading/unloading of file cache entries.

-
**
Fixed
**
: Audio Streaming crash on initialization.

-
**
Fixed
**
: Only start a vehicle's run loop if it is not already running.

-
**
Fixed
**
: Playback of Vorbis encoded streams.

-
**
Fixed
**
: Vehicles without a stop trigger now stop a running instance.

-
**
Fixed
**
: Crash when entering game mode in Editor.

-
**
Fixed
**
: NULL implementation FaileCacheEntry parsing.

-
**
Optimized
**
: Adjusted debug display for overall and active count of audio objects and events additionally decreased font size from 1.35 to 1.2 for those entries.

-
**
Optimized
**
: Consolidated NULL pointer checks in FileCacheManager in regards to FileCacheEntries.

-
**
Optimized
**
: Audio Implementation is now using new ATL feature of mapping RTPCs to Environments.

##
Game

-
**
New
**
: Added "can_rip_off" parameter to define whether mounted weapons can be ripped off or not. Default is true.

-
**
New
**
: Updated CarryEntity code not caring about asset helper positions.

-
**
New
**
: Updated scripts to use latest 07 AI Behavior Tree.

-
**
New
**
: Added 'usePlayerTeamVisualization' flag option to enable(default)/disable init of TeamPlayerVisualisation function per gamemode via the GameModes XML script. This function controls the automatic character material assignment based on Hostile/Friendly set by the PlayerTeamVisualization XML script.

-
**
Fixed
**
: (Action) Double broadcasting game object events during pausing/unpausing of the game.

-
**
Fixed
**
: Hide hud when killcam is active (CE-1348).

-
**
Fixed
**
: Shotgun was missing in killcam. Required updates to Scripts/KillCam/KillCam.xml.

-
**
Fixed
**
: Updated CaptureTheFlag scripts (entities + gamerules). Updated asset paths. Fixed incorrect Physics flag in CTFFlag script.

-
**
Fixed
**
: Removed character model override from equipment loadout packages. Fixed package attachments (seq = weap, att, weap, att, att). Shortened description strings to prevent asset. Added CTF equipment pack.

-
**
Fixed
**
: Crash when loading CTF game ("Hammer" fallback weapon unavailable) (CE-4768).

-
**
Fixed
**
: Crash in flow node Actor:EnslaveCharacter when no input entity provided.

-
**
Optimized
**
: (Physics) Disable unnecessary foliage physics calculation on dedicated servers.

-
**
Optimized
**
: Removed secondary_damage and added npc_additional_damage which is added on top of normal damage for AI->Player contact. Can use negative values (CE-2549).

-
**
Optimized
**
: Updated UI CVar descriptions (CE-3070).

-
**
Optimized
**
: Additional tweak to the restored stdwheeled behaviour to prevent HMMWV from rolling over (CE-4839).

##
Assets

-
**
New
**
: (Mannequin) Added pistol+flag Mannequin aimpose.

-
**
New
**
: (Mannequin) Added default friendly_leave setup. Set nw idlepose to nw animation instead of rifle.

-
**
New
**
: (Mannequin) Added HMG Mannequin setup and some additional anims.

-
**
New
**
: (Mannequin) Shotgun3P reload setup causing weapon to bounce around in hand by removing loop and adjusting timing on swaphand.

-
**
New
**
: (Mannequin) Added Grenade1P, Pistol3P and Rifle3P melee fragments (CE-4922).

-
**
New
**
: (Mannequin) Added correct Shotgun melee anims and fragments. Added change_firemode anims. Added bump setup for Shotgun.

-
**
New
**
: (Mannequin) Added Audio support for Silencer attachments on SDK weapons.

-
**
New
**
: (UIActions) Added buttonDisabled to main menu.

-
**
New
**
: Added double_neon_light asset.

-
**
New
**
: Added new 6x2m cloth asset and material.

-
**
New
**
: Included XMP Metadata "CE_NoAutoUpdate" into HUD_3D (CE-4594).

-
**
Fixed
**
: Ground smoke pfx. Tiling problems & also adjusted the min / max view dist.

-
**
Fixed
**
: Shotgun1P ironsight movement animation stopping as it wasn't set to loop (CE-4935).

-
**
Fixed
**
: Removed proc-layer on nw slide which caused t-pose (CE-4922).

-
**
Fixed
**
: Shotgun3P fire sound not working on AI due to 0.1s delay (CE-4952).

-
**
Optimized
**
: (UIActions) General tidy up.

-
**
Optimized
**
: (UIActions) Moved Class Selection into new separate menu. Disabled menu access in CTF gamemode.

-
**
Optimized
**
: Deleted "gun_mounted" assets, resetup as "mounted_gun" to match folder name. Exported FP and TP models. Setup CDF/CHR/CHRPARAMS. Added handle for ripoff animation sensibility. Cleaned up HMG weapon script.

-
**
Optimized
**
: Forest_Ruin tessellation settings (CE-4990).

-
**
Optimized
**
: Updated SkeletonList: Reorganized into groups in alphabetical order. Removed obsolete entries. Added rocketlauncher and HMG entries.

-
**
Optimized
**
: Tweaked grass_4 material, added new grass_4_ddna.

-
**
Optimized
**
: Deleted xtrees from Airfield. Disabled "UseSprites" checkbox.

##
Blended Shadow Cascades Feature
