# EaaS 3.8.5

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/47316993/pages/44962943
- Page ID: 44962943
- Breadcrumb: Engine Release Notes (Current) > CRYENGINE 3.x > EaaS 3.8 > EaaS 3.8.5
- Parent: EaaS 3.8

## Content

##
Editor

##
Editor General

-
**
New
**
: Shift-Escape triggers in-game menu in the Editor without leaving game. Escape quits as normal.

-
**
Fixed
**
: Mouse move events were sent every frame even if there was no movement.

-
**
Fixed
**
: Handle spec changes for road objects.

-
**
Fixed
**
: Preserve cursor changes while in Editor.

-
**
Fixed
**
: Roads, rivers and distance clouds being exported to game when on a 'No Export' layer.

-
**
Fixed
**
: Potential crash when showing the 'Duplicate objectname' dialog.

-
**
Fixed
**
: Crash in AuxGeom Renderer - caused by unexpected reference-to-value conversion.

-
**
Fixed
**
: More reliable initialization of gEnv in plugins.

-
**
Fixed
**
: Do not allow object names containing '%' as they can crash the Sandbox.

-
**
Fixed
**
: (Trackview) Sometimes a sequence won't play when jumping into game mode after editing them.

-
**
Fixed
**
: (Trackview) "Undo" Add/Delete Sequence creates cloned representations of already existing nodes.

-
**
Fixed
**
: (Trackview) "Undo" leaves traces in sequences which can lead to crashes.

-
**
Fixed
**
: (Vehicle Editor) Selected class for vehicle part appears twice in the dropdown menu.

-
**
Fixed
**
: Remove malfunctioning vehicle debug view and respective CVar v_debugView. Use instead CVar's v_debugViewDetach 1/2 and v_debugViewAbove.

##
Renderer

##
Renderer General

-
**
Fixed
**
: ScreenFader effect behaves incorrectly when HUD doesn't get drawn.

-
**
Fixed
**
: Light-clip volume entity links in pure game mode.

-
**
Fixed
**
: Engine won't handle LOD's for Vegetation Objects if cloth-feature included.

-
**
Fixed
**
: LOD baker smoothness map generation and wrong UV layout.

-
**
Fixed
**
: Fixed dynamic textures not loading properly if the same texture is registered already as a different texture type.

-
**
Fixed
**
: AUX geometry draw flickers.

##
SVOGI

-
**
Fixed
**
: Crash on light source delete in the launcher.

-
**
Fixed
**
: Terrain holes support (underground geometry placed in terrain holes is also voxelized now).

-
**
Fixed
**
: Debug assert related to forward tiled shading when GI is disabled.

-
**
Fixed
**
: Crash in clip volume voxelization.

-
**
Fixed
**
: sRGB handling in voxelization, now voxels have color closer to original geometry.

-
**
Tweaked
**
: Improved low glossiness handling in specular tracing (only for mode 2).

-
**
Fixed
**
: Screen depth tracing not working in levels with great view distance (only for mode 1-2).

-
**
New:
**
 Added PointLightsMultiplier and EmissiveMultiplier cvars.

##
Volumetric Fog

-
**
Optimized
**
: Added the feature of tiled FogVolume density injection.

-
**
Fixed
**
: Stripe-artifacts appear on very dense FogVolume.

-
**
Fixed
**
: The transition of noise distribution is discontinuous when DensityNoisetimeFrequency parameter is changed.

-
**
Tweaked
**
: The value range of DensityNoiseFrequency and DensityOffset in FogVolume entity.

##
Engine

##
System

-
**
Fixed
**
: Improved layout of 'profile' 1 & 2 debug views.

-
**
Fixed
**
: Inconsistent XML serialization of strings containing newlines.

-
**
Fixed
**
: Unify allocator construct member functions for all allocators to use, which is C+11 compliant.

-
**
Fixed
**
: (Vegetation) e_MergedMeshesDebug memory information.

-
**
Fixed
**
: (Vegetation) Fix for merged mesh pool overflow, e_MergedMeshesViewDistRatio adjusted to produce reasonable 500m max view distance.

##
Particles

-
**
Fixed
**
: Emitter priming no longer ignores sub-effects with disabled parents.

-
**
Fixed
**
: Disappearing emitters due to too-small dynamic bounds maintenance.

##
RC/Tools

##
Tools

-
**
New
**
: Batch script and python script to enable simple copying of Wwise headers and libraries.

##
Resource Compiler

-
**
Fixed
**
: Removed resolution reduction from the Minimap preset.

-
**
Fixed
**
: Crash in getting computed cubemap pixels.

-
**
Fixed
**
: Crash incorrect printf arguments.

-
**
Fixed
**
: Wrong asserts and code related to non-div-by-4 images.

-
**
Fixed
**
: DXT1 error if the output image is not compressed - DXT1 error no longer computed.

-
**
Fixed
**
: UpdateAndSaveSettingsToTIF(): Some compressed images were saved with data loss.

##
Animation

##
Animation General

-
**
Fixed
**
: Crash in the animation command buffer - related to a race condition occurring on a frame-local memory allocation call.

##
Character Tool

-
**
New
**
: Added warning when software skinning is not enabled when blendshapes are present.

-
**
Fixed
**
: Reload entities when saving from CharacterTool.

-
**
Fixed
**
: Missing keyboard support for undo/redo in properties panel.

-
**
Fixed
**
: All animations in the same folder of a CGA showed up in its animationlist (and not just those with the proper prefix).

-
**
Fixed
**
: Blendshapes not appearing when creating a character.

-
**
Fixed
**
: Possible fix for crashes in CTransitionQueue::UnloadAnimationAssets - now ensures that whenever a chrparams gets reloaded all other characters using the same animationset stop their animations as well.

##
Mannequin

-
**
Fixed
**
: Crash when loading a new level while having a fragment opened in the Mannequin Editor.

##
Action

##
Flowgraph

-
**
Fixed
**
: Weapon:HitInfo - did not work with explosions.

-
**
Fixed
**
: Null-terminated array not terminated - can crash depending on the final image layout (random).

-
**
Fixed:
**
 Add color picker widget for Debug:Draw flow nodes.

-
**
Fixed
**
: Cleanup for Inventory:ItemRemove flow node - fixes output in case of removing an item that is not in the inventory.

##
Audio

##
Audio General

-
**
Optimized
**
: An audio middleware switch at runtime no longer kills and recreates all of the ATL resources.

-
**
Fixed
**
: Repositioned the Audio Listener after runtime middleware switch.

-
**
Fixed
**
: Audio system shutdown not cleaning up all resources.

-
**
Fixed
**
: Where switches and their states debug drawing overlapped.

-
**
Fixed
**
: PlayFile and StopFile to not lose callback info data when being queued.

-
**
Fixed
**
: AudioProxy position updates to also take rotation into account and additionally preventing the Audio Listener from being spammed with position updates even though it did not move.

-
**
Fixed
**
: Crash in CAudioEventManager::Init on audio middleware switch when an unsigned variable flipped around.

-
**
Fixed
**
: Crash in audio debug name store during shutdown.

-
**
Fixed
**
: Crash on shutdown with audio trying to access an invalid logging system.

-
**
Fixed
**
: Crash on a level load where a physics RWI callback accessed an invalid ray counter.

-
**
Fixed
**
: Audio environment updates for FlowAudioTriggerNode

-
**
Fixed
**
: Audio environment updates for AudioTriggerSpot

-
**
Fixed
**
: Double playback of ATS triggers after save/load

-
**
Tweaked
**
: Now keeping track of standalone audio files.

##
ACE (Audio Controls Editor)

-
**
Fixed
**
: Issue with libraries being deleted when the casing of the name was changed.

-
**
Fixed
**
: Disabled drag and drop of folders with the same name.

##
Game

-
**
Fixed
**
: Play sound when turning the turret of an Abrams.

-
**
Fixed
**
: Prevent crash when hitting Tab in main menu after multiplayer game.

-
**
Fixed
**
: Potentially added additional weapons to the player's inventory when loading a savegame.

-
**
Fixed
**
: Reloading scripts spawned a rifle under each AI character.
