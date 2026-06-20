# EaaS 3.6.11

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/47316993/pages/44963017
- Page ID: 44963017
- Breadcrumb: Engine Release Notes (Current) > CRYENGINE 3.x > EaaS 3.6 > EaaS 3.6.11
- Parent: EaaS 3.6

## Content

Released 14th November, 2014

##
Editor

-
**
New
**
: (Flowgraph) Added Flownode to change ocean material.

-
**
New
**
: Refine terrain texture tiles added into main "Terrain" menu, in addition to inside Terrain Texture Layers tool menu (CE-1391).

-
**
Fixed
**
: (Trackview) Fixed lights being unable to set ColorParams because of removed HDRDynamic value from light.lua script (CE-4802).

-
**
Fixed
**
: (TimeofDay) TOD values are not accepted unless Return key is pressed (CE-4402).

-
**
Fixed
**
: (CryDesigner) Unassigning material should reset to default material (CE-2698).

-
**
Fixed
**
: AIPath creation only worked with at least 3 points, minimum now set to 2 (CE-4790).

-
**
Optimized
**
: (Vegetation) Merge tool tip and UI layout (CE-4642).

-
**
Optimized
**
: Removed deprecated CloudVolume button in RollupBar (CE-4202).

##
Engine

-
**
New:
**
(Particles) New enum classes and macros, for conveniently declaring enums without prefixes, and creating TypeInfo simultaneously. No longer need ENUM_INFO definitions. Nested all ParticleParams enums in ParticleParams.

-
**
New:
**
(Physics) Exposed stiffness and death pose on deadbodies/ragdolls (CE-4736).

-
**
New:
**
Using PhysProxies to compute the BBox.

-
**
New:
**
Save VCloth params in CDFs.

-
**
New
**
: Added r_DeferredShadingAreaLights=1 to system.cfg for AreaLight use.

-
**
Fixed
**
: (Bending) Crash when two threads simultaneously use bending pool.

-
**
Fixed
**
: (Debug) e_debugdraw 2 & 3 - Ghosting issue on instancing.

-
**
Fixed
**
: (RC ImageCompiler) Fixed wrong # of parameters passed to RCLogWarning().

-
**
Fixed
**
: (AreaLights) Light projectors when tiled shading is enabled. Ambient area lights when area light support is off to keep compatibility with previous behavior. Skip regular rectangular area lights when support is disabled. Draw area light helpers only when light is selected.

-
**
Fixed
**
: Override material needs to have priority over object material in texture streaming. This fixes the Texture Streaming issue introduced in 3.6.10.

-
**
Fixed
**
: Deadlock when cache is playing and walking into vegetation because C3DEngine::Tick is sometimes called twice in the same frame.

-
**
Fixed
**
: More cleanup on VCloth (removed culling morphs code and facial marking for tangents).

-
**
Fixed
**
: Removed an unnecessary assert in Rasteriser::Raster (CE-4843).

-
**
Optimized
**
: (Particles) Change particle lighting adjustment defaults to 1. Remove obsolete SunMultiplier.

-
**
Optimized
**
: (Particles) Moved alpha-clipping in shader for earlier rejection.

-
**
Optimized
**
: (System) Show all streaming priorities with sys_streaming_debug.

-
**
Optimized
**
: (Debug) Improved e_debugdraw 20.

-
**
Optimized
**
: (Maya, Collada, RC) Refactored/fixed computation of node transforms (CE-4762).

-
**
Optimized
**
: Refactored water ripples coordinate transform code. Added debug mode to visualize water hits.

-
**
Optimized
**
: Restore 3s render delay when showing error messages.

##
Renderer

-
**
Fixed
**
: (Scaleform) HUD: There are artifacts on the HUD (CE-4415).

-
**
Fixed
**
: Extend 'disable temporal effects flag' to multiple GPUs.

-
**
Fixed
**
: Log sampler/texture mismatch once per case to prevent Editor hanging on looped/spammed warnings (CE-3950).

-
**
Fixed
**
: Enable NullRenderAuxGeom for null renderer, fixes r_debug_renderer_show_window for dedicated servers to debug server side physics proxies.

##
Audio

-
**
New
**
: Initial implementation using SDL Mixer.

-
**
New
**
: Added support for executing TriggerFinished callbacks on the Main thread.

-
**
New
**
: Added the Trigger Finished Event handling to the FlowAudioTriggerNode.

-
**
New
**
: Added TriggerFinishedCallback support.

-
**
New
**
: Introduced ability to playback streamed files in Wwise.

-
**
New
**
: Re-enabled toggling of audio updates on particle effect instances, introduced ability to select any RTPC for being used during particle effect updates.

-
**
New
**
: Initialize Wwise Comm system only if needed, for that introduced new cvar "s_WwiseEnableCommSystem".

-
**
Fixed
**
: Adjusted ParticleEffect.lua audio code to accommodate for the new AudioSystem functionality.

-
**
Fixed
**
: Particle effects spawned at run time now have audio enabled by default.

-
**
Fixed
**
: Dangling pAudioSystem pointer crash on system quit.

-
**
Fixed
**
: Iterator invalidation on the debug name store and fixed threading issue in the AudioSystem.

-
**
Optimized
**
: Minor audio code adjustment in CParticleSubEmitter::DeactivateAudio.

-
**
Optimized
**
: Added AudioID-to-string lookup for the external code. Non-null strings are returned only if INCLUDE_AUDIO_PRODUCTION_CODE is defined.

-
**
Optimized
**
: Changed defines in Wwise implementation to have the "Wwise" word.

##
Game

-
**
New
**
: (AISystem) New behavior tree SDK_Grunt_07 with emphasis on further AI assignments through the Flow Graph (CE-4475), tweaked existing TPS queries and added new ones for the new AI assignments.

-
**
New
**
: Added a GetViewCameraUpDir ScriptBind.

-
**
Fixed
**
: (Scaleform) HUD: Missing team parameter for scoreboard (CE-4411).

-
**
Fixed
**
: (Action) Double broadcasting game object events during pausing/unpausing of the game.

-
**
Fixed
**
: Weapon reload does not work when a use message is on screen (CE-4386)

-
**
Fixed
**
: Vehicles not animating in GameSDK.

-
**
Fixed
**
: Crash in flow node Actor:EnsalveCharacter when unrecognized scope specified (CE-4807).

-
**
Fixed
**
: Comment entity not displaying in game (CE-3925).

-
**
Optimized
**
: Switched HMMWV to stdwheeled by default to fix some stability issues (CE-4839).

##
Assets

-
**
New
**
: Switched boat script to use new boat model, updated helpers, tweaked handling slightly. Updated idle anim in Mannequin setup. Removed passenger setups for now.

-
**
New
**
: Added additional green_fern_bush asset variations.

-
**
New
**
: Added beam_spotlight projector material.

-
**
New
**
: Added pumpkin asset character attachment.

-
**
Fixed
**
: (Mannequin) swimming/idle animation gets stuck in loop + missing swim turn animation

-
**
Fixed
**
: Incorrect pathing on PrecacheLists script.

-
**
Fixed
**
: Updated boat proxy to make in-boat navigation better. Simplified some over complicated parts.

-
**
Fixed
**
: Asset paths in SmokeGrenade scripts. Tidied content.

-
**
Fixed
**
: Jet: Deleted unused CGA file. Fixed broken CGF model with duplicate faces. Added 3 additional LODs. Fixed proxy (CE-4438).

-
**
Fixed
**
: Updated texture paths for vegetation decal materials.

-
**
Fixed
**
: Geomcache example asset replaced stone toad with production-suitable example.

-
**
Fixed
**
: Beach_Rocks: Remove obsolete occlusion proxies. Separated out Proxies from rendermesh. Removed unused MatID 2 (plants) in material and max scene. Repositions LODs for better readability.

-
**
Fixed
**
: Disabled "TriggerOnce" on Forest waterfall area trigger so the effect triggers more than once (CE-4707).

-
**
Optimized
**
: Removed obsolete params in Pistol script. Commented out lasersight content until its actually in.

-
**
Optimized
**
: Removed obsolete params in Rocketlauncher script.

-
**
Optimized
**
: Removed obsolete params in FragGrenade script.

-
**
Optimized
**
: Removed obsolete params in Shotgun script. Tidied content. Removed ironsight accessory no longer needed on new mesh.

-
**
Optimized
**
: Cleaned up Rifle script, added more info. Removed obsolete params.

-
**
Optimized
**
: Tidied PickAndThrowWeapon script. Removed obsolete pose param.

-
**
Optimized
**
: Tweak wood textures/materials.

-
**
Optimized
**
: Brick texture/material updates.

-
**
Optimized
**
: Removing low quality lamp assets from props/misc/lights/.
