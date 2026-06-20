# CRYENGINE 5.4.0 Preview(s)

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/47316993/pages/44962702
- Page ID: 44962702
- Breadcrumb: Engine Release Notes (Current) > CRYENGINE 5 > CRYENGINE 5.4 > CRYENGINE 5.4 Previews > CRYENGINE 5.4.0 Preview(s)
- Parent: CRYENGINE 5.4 Previews

## Child Pages

- [CRYENGINE 5.4.0 Preview 2](CRYENGINE 5.4.0 Preview(s)/CRYENGINE 5.4.0 Preview 2.md)
- [CRYENGINE 5.4.0 Preview 3](CRYENGINE 5.4.0 Preview(s)/CRYENGINE 5.4.0 Preview 3.md)
- [CRYENGINE 5.4.0 Preview 4](CRYENGINE 5.4.0 Preview(s)/CRYENGINE 5.4.0 Preview 4.md)
- [CRYENGINE 5.4.0 Preview 5](CRYENGINE 5.4.0 Preview(s)/CRYENGINE 5.4.0 Preview 5.md)
- [CRYENGINE 5.4.0 Preview 6](CRYENGINE 5.4.0 Preview(s)/CRYENGINE 5.4.0 Preview 6.md)
- [CRYENGINE 5.4.0 Preview 7](CRYENGINE 5.4.0 Preview(s)/CRYENGINE 5.4.0 Preview 7.md)

## Content

[/docs](
[Image: /docs/static/attachments/44962713]
)

[https://www.cryengine.com/support](
[Image: /docs/static/attachments/44962710]
)

##
Preview Overview

This week, the CRYENGINE 5.4 Preview is a major update which couldn’t have been achieved without all of the feedback from the community. There are several major advancements and integrations that we think will make things more accessible and let you achieve even more, more rapidly.

With over 623 improvements, fixes and features this release includes all new Vulkan API support, and although it’s our first step on the road you can expect further support on this soon. Also included is the Entity Component System with unified standard entities across C++ and Schematyc.

For Artists, we have a much requested Substance integration for the reading of material archives and manipulation of texture inputs with in-editor graphing. Additionally, we have expanded the feature set of the terrain system to allow for better blending of terrain and objects within your level.

Iterating on existing technology there is a second iteration of the Asset System which provides improvements and extended usage across tools, with thumbnail generation and all new dependency tracking. To get started, you can find the CRYENGINE 5.4 Preview on Github
**
[https://github.com/CRYTEK/CRYENGINE/releases/tag/5.4.0_preview](
HERE
)
!
**

**

**

The build is based on a CRYENGINE 5.4 Preview release. So please make sure to remember to backup your projects before trying out the Preview build.

*
Coming Soon
*

[Image: /docs/static/attachments/44962709]

##
Sections

[#preview-overview](
Preview Overview
)
[#sections](
Sections
)
[#code-interface-changes](
Code Interface Changes
)
[#release-highlights](
Release Highlights
)
[#known-issues](
Known Issues
)
[#animation](
Animation
)
[#ai](
AI
)
[#audio](
Audio
)
[#coresystem](
Core/System
)
[#graphics-and-rendering](
Graphics and Rendering
)
[#physics](
Physics
)
[#network](
Network
)
[#project-system](
Project System
)
[#sandbox](
Sandbox
)
[#tools](
Tools
)

##
Code Interface Changes

For more information, see the
**
[/docs/static/engines/cryengine-5/categories/47316993/pages/44962696](
Important CRYENGINE 5.4 Data and Code Changes
)

**
article.

If you are upgrading from CRYENGINE 5.3, please read this topic:
[/docs/static/engines/cryengine-5/categories/47316993/pages/44962697](
**
Migrating from CRYENGINE 5.3 to CRYENGINE 5.4
**
.
)

##
Release Highlights

##
Substance Integration

Both internally and externally, we have seen the industry embrace the concept of harnessing procedural texture creation to extend the usage of individual assets. For some time now, our internal teams have actively used Substance in their workflow so it is a logical addition to be supported within our Sandbox Editor.

With this integration, we are using Substance Archive files (*.sbsar) to create Substance Graph instances and generate textures out of them. The important thing to keep in mind is that CRYENGINE implementation doesn't directly output graph outputs from a substance graph, but rather pre-configured texture outputs that are using substance graph outputs as inputs.

Keep in mind the archive still needs to be built inside of the Substance Designer where the properties are then exposed to the Sandbox Editor through the archive for the modular end result.

-
[/docs/static/engines/cryengine-5/categories/23756816/pages/29450468](
Allegorithmic Substance Documentation
)

##
Terrain Upgrades

For many years now one of the most heavily requested upgrades to the Engine is that of the 3D Engine and specifically the terrain system. In 5.4, we have added several terrain features that allow for the blending and integration of separate objects into the terrain mesh. This dramatically extends the possibilities of current terrain editing tools, allowing for a much higher level of detail, overhangs, or terrain over the objects allowing for general greater flexibility.

A slight overview on the integration goes as follows:

In the current release, the object meshes get copied at an early stage into the heightmap mesh and become a seamless part of the terrain mesh supporting most of the heightmap properties and 3D terrain materials.

Also, as a side note to the terrain blending, we have enabled auto high-pass in the 5.4 version of the Engine, thus eliminating an additional and cumbersome step to users, and which only pertained to terrain materials.

##
Vulkan API Support

With 5.4, the engine includes a beta version of the Vulkan renderer to accompany the DX12 implementation from last year. Vulkan being a cross-platform 3D graphics and compute API that enables developers to have high-performance real-time 3D graphics applications with balanced CPU/GPU usage.

For the preview release, Vulkan support in CRYENGINE will be compatible for projects on PC, and aim for additional Android support beyond the 5.4 release.

To enable the Vulkan renderer, you need to enter
*
"r_driver=vk"
*
into your
*
.cryproject
*
 file. Keep in mind you must also run the remote shader compiler locally as the renderer is dependent on this step.

[Image: /docs/static/attachments/44962708]

##
Entity Components

A longstanding issue within CRYENGINE is the reliance on game code to expose and manage entities within your scene. CRYENGINE's Component Entity System provides a modular and intuitive way to construct games. The technology works at both the system level and the entity level.

The interaction model within the Sandbox Editor allows Developers to create a blank entity container that houses the advanced game logic wrapped into specific components. Examples of base components are: Mesh, Light, Constraints, or even Character Controllers.

With these components, you can then develop prefabs to be placed by Level Designers throughout your game for standardization and exposure to Schematyc for triggering and event updating.

[Image: /docs/static/attachments/44962707]

##
Extended Detail Bending (Robinson Tech)

Upgraded in 5.4 is the new "Extended Detail Bending" toggle - found in the vegetation shader. The history behind this feature comes out of our
*
Robinson: The Journey
*
 development and how we needed a more accurate and physically dependent bending solution for our vegetation.

This feature provides Artists with much more control over detail bending on their branches. For example, new bending allows not only small micro movement on leaves, but also whole branches of trees or chunks of grass. So Artists can have one big chunk of grass with phased animations so that movement looks natural. Aiding in the variations, we also apply a world-space mapped noise texture to simulate random breeze for variations to the movement.

[Image: /docs/static/attachments/44962706]

##
C# Templates

We have added the following templates in C#:

-
C# Plugin

-
C# Blank

-
C# Rolling Ball

-
C# 3rd person
Carrying on with our Launcher improvements, we have also expanded our selection of templates to get you up and running with CRYENGINE. Several things have been brought over from our C++ arsenal and that includes the Plugin and 3rd Person templates in a C# flavor.

5.4 will also introduce the new Sandbox Editor Plugin template, this allows for development of new Sandbox Editor functionality when using the yet to be released full Sandbox Editor source code. In future release, we expect to add more templates to CRYENGINE which not only shows the beginning part, but also finalized examples that guide you through each phase of game development.

-
[/docs/static/engines/cryengine-5/categories/23756813/pages/26874562](
C# Game Templates Documentation
)
[Image: /docs/static/attachments/44962705]

##
Asset System Updates

In 5.3, we shipped a base implementation of the Asset System (that was long overdue in the Sandbox Editor) that allows users to directly interact with their assets and directories. We know that the most optimal solution is to never touch the Windows Explorer in order to achieve the change you want - the Asset System certainly brings us one step closer to this reality. To achieve this, we have now added direct drag-and-drop support for the Asset Browser along with other tools integration (Material Editor, Particle Editor).

To aid in the assistance of changing the paths or managing dependencies, we have introduced an all new Dependency Graph with the 5.4 version of the Engine.

Now within the Asset Browser, we have exposed dynamic CGF switching functionality with the added benefit of having a direct view of a thumbnail to preview and select the asset that best suits your needs in your development. That allows you to step down the list to find the asset best suited for your scenario.

-
[/docs/static/engines/cryengine-5/categories/23756816/pages/35260066](
Asset System Documentation
)
[Image: /docs/static/attachments/44962704]

##
UPDATE: Editor Source Code (Not included in preview release)

With the 5.4 full release, the Sandbox Editor source code will be provided to users so that they can extend the Sandbox Editor for their own custom tools and applications. In this release, we have taken time to provide the resources and knowledge necessary to work within the Sandbox Editor code and to develop Editor Plugins that are fully integrated with the Sandbox Editor and its most advanced systems.

With the release of the Sandbox Editor source code, we have also planned to expose a new Sandbox Editor programming section within our Technical Documentation. This section would include sample plugins that can be used to access and extend the Sandbox Editor from the base we deliver.

We are looking forward to contributions from the community to strengthen and supplement the tools that are offered with CRYENGINE!

[Image: /docs/static/attachments/44962703]

**
- CRYENGINE Team
**

**

**

##
Known Issues

-
**
CRASH:
**
 Typing a numeric value into texture name field triggers assert and crash (CDeviceResourceSetDesc::UpdateResource).

-
**
DX12:
**
 Taking a screenshot freezes the game.

-
**
DX12:
**
 Vegetation and brush streaming is slow/partially missing.

-
**
CRASH:
**
 Possible crash when creating a new map and switching/changing terrain texture size several times in a row   (CryRenderD3D11.dll!std::_Hash<std::_Umap_traits<void * __ptr64).

-
**
CRASH:
**
 Docking Schematyc-window to main Viewport crashes (CryRenderD3D11.dll!CCryDeviceContextWrapper::OMSetRenderTargets).

-
**
CT:
**
 Editing an *.animevents-file in the CT and saving the changes do not work.

-
**
WARNING:
**
**
(TRACK)
**
 Capture Track produces warning: End capture failed.

-
**
SCHEM:
**
 Nodes are broken in LightenUp2.

-
**
SCHEM:
**
 Components of LightenUp2 are broken.

-
**
CRASH:
**
 Sandbox Editor corrupted after crash in mannequin (CFragmentSequencePlayback::Update()).

-
**
MANNEQUIN:
**
 Performance drops when moving the camera around in the Mannequin Editor.

-
**
CRASH:
**
 Creating several new levels causes crash (CryRenderD3D11.dll!CCryDeviceContextWrapper::PSSetShaderResources).

-
**
CRASH:
**
 Creating several new levels with added animations-folder causes crash (CryRenderD3D11.dll!CCryDeviceContextWrapper::PSSetShaderResources).

-
**
TRACK:
**
 Standard Events are missing from TrackView.

-
**
RENDER:
**
 Selected objects are not rendered correctly.

-
**
RENDER: (PARTICLE)
**
Environment probes do not affect particles.

-
**
CRASH: (MULTIPLAYER
**
) Client may crash at match end (Entity_grid_checker rwi.cpp).

-
**
CRASH:
**
 Disable a lights-PFX in Schem-Properties, then switching to main Viewport causes crash  (Cry3DEngine.dll!CLightVolumesMgr::Update).

-
**
RENDERING:
**
 Ocean is missing/not rendered, skybox is too bright in Woodland.

-
**
CRASH: (LEVEL EXPLORER)
**
Using undo and redo and deleting the main layer can cause crash (EditorCommon.dll!CBaseObject::Serialize(CObjectArchive & ar)).

-
**
SPAM:
**
 Camera movement in 3rd person template causes massive spam.

-
**
CT: (PHYSICS)
**
Most of the rope/cloth physics properties don't have any effect on physicalized objects.

-
**
MANNEQUIN:
**
 Mannequin Editor does not hot reload files, nor does it try to load new ones on deliberate load commands.

-
**
CRASH:
**
**
(PE/ PFX)
**
 Dragging PFX from a file-creation-dialogue into the map and then using cancel causes crash (Cry3DEngine.dll!pfx2::CParticleEffect::Compile()).

-
**
ERROR:
**
 Spam in NC when jumped into Game using 3rd person shooter-template (Animation-queue).

-
**
SANDBOX:
**
 'Package Build' function is broken.

-
**
CRASH:
**
**
(MANNEQUIN)
**
 Assigning an animation to a key that is not aligned with the animation next to it causes crash.

-
**
CRASH:
**
**
(CT)
**
 Loading a different *.cgf while a character-animation plays occasionally causes crash (EditorCommon.dll!Explorer::EntryBase::Serialize).

-
**
CRASH:
**
**
(FG)
**
 Using Undo/Redo often (after adding a node) causes crash (Sandbox.exe!CHyperGraph::GetAllEdges).

-
**
DESIGNER:
**
 PolyLine tool does not finish properly.

-
**
Substance Integration:
**
Undo not working.

-
**
Substance Integration:
**
It is not possible to create materials out of substances - just textures and assign them to materials manually.

-
**
Substance Integration:
**
When a Substance Archive(s) is/are modified outside of a Sandbox Editor session, then instances that depend on the archive(s) are not recalculated.

-
**
**
Substance Integration:
**
**
Disabling output in an instance does not lead to resulting texture removal.

-
**
**
Substance Integration:
**
**
Even if there are no changes in a Substance Instance (after closing the Instance Editor) then high quality outputs are recalculated.

-
**
CRASH: (FG)
**
 Using shortcut "Q" to quickly add a node causes crash (CHyperGraphView::OnKeyDown). Adding manually avoids crash.

##
Animation

##
Animation General

-
**
Refactored:
**
 Added a function to extend a skeleton with n number of skins (in a batch).

-
**
Fixed:
**
 Character sync to saved state.

-
**
Fixed:
**
 Issue with not syncing invisible ragdolls correctly.

-
**
Tweaked:
**
 Added more profiler markers in AttachmentManager.

##
Character Tool

-
**
New:
**
Create serializable animation layer stacks in Animation Tool.

-
**
Fixed:
**
 LoadAndLockResources wasnt preloading VCloth attachment skins.

-
**
Tweaked:
**
 Character Tool can now play animation fx events from multiple AnimFX libraries.

##
Mannequin

-
**
Fixed:
**
 Occasional crash while rotating camera and zooming at the same time (with mouse wheel).

-
**
Fixed:
**
 Missing floor-grid rendering in mannequin viewport.

##
AI

##
AI System

-
**
New:
**
 (PerceptionSystem) AI Cleanup - Move PerceptionManager to a plugin.

-
**
New:
**
 Added new navigation UpdatesManager interface and implementation.

-
**
New:
**
 (Navigation) NavMesh Improvement - Grouping 'per agent type' in menu.

-
**
Refactored:
**
 Changes in AI System interfaces.

-
**
Refactored:
**
 Navmesh updates refactoring.

-
**
Refactored:
**
 Setting navmesh raycast default version to the newest one.

-
**
Optimized:
**
AI Cleanup - Removing old navigation system.

-
**
Optimized:
**
AI Cleanup - Removing SelectionTree from the AISystem.

-
**
Fixed:
**
 Navmesh raycast not returning correct results in some cases (fixed in ai_MNMRaycastImplementation 2).

-
**
Fixed:
**
 Dead puppet's BTs were still ticking and potentially running TPS queries.

-
**
Fixed:
**
Navmesh isn't updated in Physics/AI mode in the Sandbox Editor when physical entity is destructed by physics on demand system.

-
**
Fixed:
**
Editing terrain could result in unconnected navmesh tiles.

-
**
Fixed:
**
Updating navmesh when editing exclusion areas in the Sandbox Editor for example, Delete & Undo.

-
**
Fixed:
**
Assets in navigation system when exporting a level with exclusion areas for the second time.

-
**
Fixed:
**
Rare multithread related crash in WorldVoxelizer when updating navmesh.

-
**
Fixed:
**
(Navigation) Navmesh Improvement - No re-validation after leaving game mode.

-
**
Fixed:
**
NavigationSystem - When creating a new level, exclusion volumes associated to agents carried over from the previous level instead of being cleared.

-
**
Tweaked:
**
(Navigation) Navmesh Improvement - No re-validation when level is loaded.

##
UQS

-
**
New:
**
Implement save menu action in the UQS Query Editor.

-
**
New:
**
Implement support for elements copy in the UQS Query Editor.

-
**
Fixed:
**
(HistoryInspector) Debug-rendering in edit-mode would sometimes no longer work - depending on how foreign editor-plugins changed the current Viewport.

-
**
Fixed:
**
CItemListProxy_Writable - Pointers to the underlying itemlist weren't retrieved in the case where the itemlist had been already filled in a previous round trip, thus causing a crash when writing to the items.

-
**
Fixed:
**
Memory leaks and crashes due to wrong use of
*
unique_ptrs
*
.

-
**
Fixed:
**
Changed all places that were still relying on element names instead of element GUIDs. Added the concept of a default query type via UQS::Core::IUtils::GetDefaultQueryFactory for when creating a new query in the editor.

-
**
Fixed:
**
Client-side ItemMonitors would get destroyed by the wrong deleter on the core-side, thus causing crashes in mixed debug/release builds.

-
**
Tweaked:
**
Enable property tree undo in the UQS Query Editor.

##
Audio

##
Audio General

-
**
New:
**
Added PortAudio ACE plugin.

-
**
New:
**
Audio system using Oculus Audio SDK 1.1.2 with Wwise.

-
**
New:
**
Added Oculus HRTF support.

-
**
New:
**
Substituted CVar "
*
s_PositionUpdateThreshold
*
" with "
*
s_PositionUpdateThresholdMultiplier
*
". An audio object's distance to the listener is multiplied by this value to now determine the position update threshold.

-
**
New:
**
Added ability to set an audio parameter on a Mannequin audio clip.

-
**
New:
**
Added SDL_mixer and dependent libraries to the compilation of the Engine, this is to enable us to conveniently build SDL_mixer for any supported platform ourselves.

-
**
New:
**
Pooled audio objects and events in the middleware.

-
**
New:
**
Pooled audio objects.

-
**
New:
**
Missing dropdown options from the audio trigger spot.

-
**
Refactored:
**
Moved all of the audio data into its own namespace namely "CryAudio" - adjusted include paths in audio interfaces to have proper formatting. Renamed the IAudioSystem interface to ISystem after it's been embedded into the CryAudio namespace.

-
**
Refactored
**
: Removed external PushRequest method from the AudioSystem interface and with that all external PushRequest types. Introduced task specific methods to the IAudioObject interface to substitute object specific external PushRequests and corresponding methods to the IAudioSystem interface for system global tasks. This frees us from copying external request data into internal structures. Introduced ExecuteTriggerEx to the IAudioSystem interface as a sort of convenience-fire-and-forget-type method for instant audio events that need an audio object where the user doesn't require explicit handling of such an object. This additionally combines tasks which were single requests before. Changed how listeners register to PushRequests, this is now handled more conveniently and currently available events are available through the EAudioSystemEvents enum. Removed the AudioProxy class, it is now substituted directly by the already existing AudioObjects. Data duplication and needle's cycle burning are drastically minimized. Renamed the CryAudio::Impl::IAudioImpl::NewAudioListener method to CryAudio::Impl::IAudioImpl::ConstructAudioListener. Renamed the CryAudio::Impl::IAudioImpl::DeleteAudioListener method to CryAudio::Impl::IAudioImpl::DestructAudioListener. Removed the "NewDefaultAudioListener" method from the CryAudio::Impl::IAudioImpl struct as it became obsolete. Listeners are simply constructed through the already existing ConstructAudioListener method. Renamed the IAudioSystem::GetAudioRtpcId method to IAudioSystem::GetAudioParameterId. Documented and "doxygened" the IAudioSystem interface. Updated documentation of the IAudioImpl interface. Adjusted client code according to these changes.

-
**
Refactored:
**
Removed memory allocators for the audio implementations, now they use the module heap.

-
**
Refactored:
**
Direct calls to the audio entities and objects.

-
**
Refactored:
**
Unified the name property of audio controls.

-
**
Refactored:
**
Removed use of allocator from null implementation.

-
**
Refactored:
**
Using pool objects for standalone files.

-
**
Refactored:
**
Removed id lookup for standalone files.

-
**
Optimized:
**
Removed blocking request when creating audio objects on demand.

-
**
Optimized:
**
Replaced the audio system request queue with an MPSC queue.

-
**
Optimized:
**
Removed unnecessary variable.

-
**
Optimized:
**
Removed audio event id.

-
**
Optimized:
**
Pooled audio events.

-
**
Optimized:
**
Removed the debug-name-store functionality, storing debug data on the objects now.

-
**
Fixed:
**
 Fixed an assert where debug display tried to access the adaptive Occlusion value before it was determined.

-
**
Fixed:
**
 Crash when altering values of AudioSpot used in SCHEM-entity - jump into game and an exit causes a crash.

-
**
Fixed:
**
 Trying to execute an audio trigger at (0,0,0)...'  - warning when playing a sound on proc layer in Mannequin preview.

-
**
Fixed:
**
Crash when audio triggers were played via the global-audio-object (Sidewinder Template).

-
**
Fixed:
**
Play Mode 'Delay' is not working properly on ATS.

-
**
Fixed:
**
Crash/bug where the audio object was already released, when the sync-callback was executed in the next External Update.

-
**
Fixed:
**
Occlusion calculation did not disable beyond activity radius.

-
**
Fixed:
**
Fixed compilation on durango.

-
**
Fixed:
**
Removed audio specific "using namespace" directives from entire Engine code files to prevent data collisions with objects in global namespace and prevent bleeding namespace directives in no-uber type builds.

-
**
Fixed:
**
Do not clear an audio object's name when releasing an implementation.

-
**
Fixed:
**
Compile error where a PortAudio impl specific enum was declared in the wrong namespace.

-
**
Fixed:
**
Missing include.

-
**
Fixed:
**
Revived the "sounds on ropes" feature.

-
**
Fixed:
**
Global audio object implementations are updated again.

-
**
Fixed:
**
Crash when shutting down and getting event finished callbacks in Wwise.

-
**
Fixed:
**
Updated Wwise SDK to v2016.2.1 build 5995.

-
**
Fixed:
**
Bug in CMake setup when including the Oculus spatializer dll.

-
**
Fixed:
**
Move middleware specific audio editors to their own folder within EditorCommon.

-
**
Fixed:
**
FMOD dlls now properly added to the build.

-
**
Fixed:
**
Crash when reloading audio.

-
**
Fixed:
**
The ACE is displaying ".cryasset" files.

-
**
Fixed:
**
Crash in CEntityComponentAudio when running with NULL AudioSystem.

-
**
Fixed:
**
Audio objects too close to the listener now automatically disable occlusion calculations, "too close" can be defined via the newly introduced CVar "s_OcclusionMinDistance", current default value is 10 cm.

-
**
Fixed:
**
A local variable of name "id" clashed with a member variable also named "id".

-
**
Fixed:
**
Only add switch/state connection if the middleware successfully created it.

-
**
Fixed:
**
Fixed compile error.

-
**
Fixed:
**
Switches, RTPC's and environments properly set when changed.

-
**
Fixed:
**
FMOD Studio events did not assume obstruction and occlusion values on start.

-
**
Fixed:
**
Missing audio object names.

-
**
Fixed
**
: Quitting game launcher crashes (CryAudioSystem.dll!CryAudio::CSystem::PushRequest).

-
**
Tweaked:
**
Updated Wwise SDK to v2016.2.3 build 6077.

-
**
Tweaked:
**
Updated FMOD Studio API to version 1.09.04.

-
**
Tweaked:
**
In PortAudio impl swapped hard coded file path length of 512 with audio global MaxFilePathLength.

-
**
Tweaked:
**
Renamed EPortAudioEventType to EEventType.

-
**
Tweaked:
**
Renamed TAudioGamepadUniqueID typedef to AudioGamepadUniqueId to conform with naming convention.

-
**
Tweaked:
**
Renamed global variable g_audioLogger to g_logger and implementation specific global loggers to g_implLogger.

-
**
Tweaked:
**
Renamed CAudioLogger to CLogger and put it into the CryAudio namespace.

-
**
Tweaked:
**
Adjusted remaining unscoped enums to now be scoped.

-
**
Tweaked:
**
Changed all audio specific unscoped enums to scoped enums.

-
**
Tweaked:
**
Audio object can now be renamed at runtime.

-
**
Tweaked:
**
Separated IListener and IObject from IAudioSystem into their own files, also introduced IProfileData interface to get access to audio system internal profile data.

-
**
Tweaked:
**
Prevent putting requests in callback queue if there's no listener associated with the request.

-
**
Tweaked:
**
Renamed the following default controls - object_doppler_tracking to relative_velocity_tracking, object_velocity_tracking to absolute_velocity_tracking, object_doppler to relative_velocity and object_speed to absolute_velocity.

-
**
Tweaked:
**
Default controls now get hashed at compile time.

-
**
Tweaked:
**
Removed some not needed code.

-
**
Tweaked:
**
Increased to updated frequency for abs and rel velocity parameters of audio objects from 10 to 100Hz.

-
**
Tweaked:
**
Updated FMOD Studio API to version 1.09.01.

-
**
Tweaked:
**
Minor coding guideline adjustments in the SDL_mixer implementation.

-
**
Tweaked:
**
When the audio thread is sleeping it is woken up if a new request is pushed in from another thread.

-
**
Tweaked:
**
Remove unnecessary variable from Wwise audio object.

##
ACE (Audio Controls Editor)

-
**
Fixed:
**
When drag & dropping Wwise switch/state groups, the corresponding audio system switch states keep their name within their parent switch - used to create unique state names during that operation which was wrong.

-
**
Fixed:
**
Generation of unique folder names when drag & dropping from the middleware pane.

-
**
Fixed:
**
Crash when adding the very first state to a switch, also enabled adding more than one state.

-
**
Fixed:
**
Crash when removing preload connections.

-
**
Fixed:
**
Numerous usability issues with the ACE.

-
**
Fixed:
**
Renaming of environments after ACE refactor.

-
**
Fixed:
**
First generation bugs after ACE refactoring - ACE refactoring to use the Asset Manager model.

##
DRS (Dynamic Response System)

-
**
New:
**
Added an option to swap variables.

-
**
New:
**
Added warning if CopyVariable fails.

-
**
New:
**
Added serialization for cool-down variables.

-
**
New:
**
Added CopyVariable action.

-
**
New:
**
Added an option to execute a DRS signal on the selected entity (and to create the drs-actor if missing).

-
**
New:
**
Added Import/export to/from .TSV.

-
**
Refactored:
**
How "local" variable collections are created/managed.

-
**
Refactored:
**
Initialize the DRS automatically on startup - based on the new CVar drs_dataPath.

-
**
Refactored:
**
Removed no longer needed CryDrsCommonElements extension.

-
**
Refactored:
**
Removed exoctic SpeakLineBasedOnVariable action from GameSDK.

-
**
Fixed:
**
Constantly-updating variables were not editable.

-
**
Fixed:
**
(DRS) Wrong entries in selection dropdowns from Responses.

-
**
Fixed:
**
A shutdown crash that happens when the game registered custom actions/conditions to the DRS.

-
**
Fixed:
**
Typos in error message.

-
**
Fixed:
**
TimeSinceResponse Condition now also checks the last "StartTime" of a response - in case an instance of the response is currently running.

-
**
Fixed:
**
Crash when adding variables via UI.

-
**
Fixed:
**
Crash when an entity playing a sound via a drs-action is deleted.

-
**
Fixed:
**
No-uber.

-
**
Fixed:
**
(DRS) Sending signal crashes.

-
**
Fixed:
**
Assert about line not running when cancelled - only occurred if the same line is (re)started and has finished in the same frame.

-
**
Fixed:
**
Saving of DialogLineDatabase was not working with game templates.

-
**
Fixed:
**
Creation of responses-folder did not work.

-
**
Fixed:
**
Startup crash when using the NullImpl.

-
**
Tweaked:
**
Wait-Action now has a min and a max Time property - to allow random wait times.

-
**
Tweaked:
**
Small code cleanups based on Visual Assist comments (mainly removed default constructors and added override keyword to destructors).

-
**
Tweaked:
**
Sorted Actions & Conditions alphabetically.

-
**
Tweaked:
**
Improved code quality based on Visual Assist Code Analysis.

-
**
Tweaked:
**
Updated the drs-audio actions.

-
**
Tweaked:
**
Made the autosave feature of the dialog line database optional.

##
Core/System

##
Engine General

-
**
**
New
**
:
**
EntitySystem component refactor.

-
**
**
New
**
:
**
Unified Entity and Schematyc components.

-
**
New:
**
Added support for changing entity component masks at runtime, allowing for toggling update and more.

-
**
New:
**
Added IEntityArchetypeManagerExtension interface and support for it.

-
**
New:
**
(Yasli) Added new compile time checks to serialization interface.

-
**
New
**
: Automatically unregister CVars when a plugin is shutting down.

-
**
Refactored:
**
IUILayout interface.

-
**
Refactored:
**
(Flowgraph) Added an Interface for communication with the game specific precache system.

-
**
Refactored:
**
Refactor properties by merging property handler and attributes into IEntityPropertyGroup that can be implemented once per entity component.

-
**
Refactored:
**
Removed the requirement for release builds to use signed paks.

-
**
Refactored:
**
Removed string-based-set-or-create game token method.

-
**
Refactored:
**
Added a 3rdParty folder to Code/CryEngine/CryCommon. Allow users to include 3rdParty header libraries via #include <3rdParty/abc/x.h> or <abc/x.h> anywhere in code, for e.g. CryCommon header files.

-
**
Refactored:
**
(EAAS) Remove IS_EAAS from build.

-
**
Refactored
**
: SGUID using CryGUID

-
**
Optimized:
**
Rendering of the AreaManager's area grid. Also added CVar "es_DrawAreaGridCells" to draw cell specific data such as number and coordinates.

-
**
Fixed:
**
 Some cases of Engine assets not being loaded.

-
**
Fixed:
**
Remove extra call to
*
Detail::CStaticAutoRegistrar<>::InvokeStaticCallbacks
*
 causing default entity components to be registered twice in monolithic builds.

-
**
Fixed:
**
Area solids calculated wrong bounding box.

-
**
Fixed:
**
Reverted change to inrange. Fixed potential alignment issues by changing some pointer casts from Matrix44* to Matrix44f*.

-
**
Fixed:
**
Lua scripts not being updated.

-
**
Fixed:
**
 Issue where a fatal error would be triggered when dynamically creating area components.

-
**
Fixed:
**
Case where game rules and local player id could be reserved too late.

-
**
Fixed:
**
Placing an Audio Area Random causes all entities to disappear after saving and reloading.

-
**
Fixed:
**
Compile time CRC computation constexpr wasn't compiled as such.

-
**
Fixed:
**
Paste a file in windows while GameLauncher.exe is running does not work.

-
**
Fixed:
**
Nullptr rendernode check in breakability.

-
**
Fixed:
**
Values are not set correctly on any EntityComponent that's not the first component.

-
**
Fixed:
**
Crash caused due to simultaneous access to an area grid member from different threads.

-
**
Fixed:
**
Added in-place construction/destruction for non-trivial/POD custom types "T" in the concurrent queues.

-
**
Fixed:
**
Bug where it was not possible to remove a component and directly afterwards add the same component again.

-
**
Fixed:
**
Problem when audio thread queried the areaSystem during level loading.

-
**
Fixed:
**
Duplicating component based objects in the Sandbox Editor doesn't work properly.

-
**
Fixed:
**
Entity activation requests lost during the active entity updates.

-
**
Fixed:
**
(CryAction) Allow Designers to target the Rumble to a particular controller.

-
**
Fixed:
**
Detect HTML tag as end of localization key.

-
**
Fixed:
**
A leak when showing additional geometry in TextFields for e.g. borders, cursor etc.

-
**
Fixed:
**
Multiple definition of friend in class GCC 4.9.3.

-
**
Fixed:
**
(TPS) Bug that caused data not to be loaded correctly.

-
**
Fixed:
**
Problems related to 'release' configuration.

-
**
Fixed:
**
Places where "engine" was missing for asset located in the engine.pak.

-
**
Fixed:
**
Wrong CPUID bit being tested for SSE3.

-
**
Fixed
**
: fixed where the "InnerFadeDistance" property wasn't properly ex-/imported for AreaBox, AreaSphere and AreaShape.

-
**
Tweaked
**
: Implement component unit tests.

-
**
Tweaked:
**
CryFixedArray compile error when tracing array subscript out of range usage.

-
**
Tweaked:
**
Define unreachable code marker.

-
**
Tweaked:
**
Update .gitignore to exclude CMake solution directory.

-
**
Tweaked:
**
Add es_DebugEntityUsageSortMode command to sort existing es_DebugEntityUsage output.

-
**
Fixed
**
: (Yasli) Couldn't attach errors/warnings while serializing Enums due to missing TypeID on the enum type.

##
Common

-
**
New:
**
ActionButton can now accept lambdas with captures - added data oriented polymorphic type handling. Names make no sense at the moment- added a reset button to reset an attribute to its default value.

-
**
Refactored:
**
Move automated CVar and Command unregistration into its own class.

-
**
Refactored:
**
Remove need for Release function in entity components.

-
**
Refactored:
**
Remove implicit declaration of constructors and destructors when using ICryUnknown.

-
**
Refactored:
**
 Allow creation of enum serialization spec for already declared enums.

-
**
Optimized:
**
Move vector for smart_ptr - should be no exception for the vector to use move semantics.

-
**
Fixed:
**
Template issue in deciding what are valid strings for CryPath to operate on. Fixes issues with FixedStrings and wchar types.

-
**
Fixed:
**
Potential infinite loop on startup.

-
**
Fixed:
**
Fix Static Linking (OPTION_STATIC_LINKING) by using /WHOLEARCHIVE Visual Studio 2015 linker option - to prevent the linker optimizing away static factory registrations.

-
**
Tweaked:
**
Define YASLI_CXX11 always.

##
System

-
**
New:
**
INumberVector base class to vectors and matrices - consolidates many common functions. Added a relative IsEquivalent option. Added proper Invert and Determinant to Matrix44, normalizing and projection functions to Vectors. Updated IsValid and SetInvalid to use C++ 11 functions.

-
**
New:
**
Automatically create .cryproject file for legacy workflow projects.

-
**
New:
**
Replace game.cfg with new console variables section in .cryproject file - existing data is automatically migrated.

-
**
New:
**
Moved cryplugin.csv contents into .cryproject file - automatically migrate data to the new or existing project file.

-
**
New:
**
Added support for statically linking plugins.

-
**
New:
**
Developer Console can be disabled in release builds (compile time switch).

-
**
New:
**
More infomation is logged when assert is triggered in non-release builds.

-
**
New:
**
 (GamePause) Add Node Game:PauseGameUpdate to allow Designers to enable/disable game update.

-
**
Refactored:
**
Update IArchiveHost interface to support forceVersion on all calls and helper functions.

-
**
Refactored:
**
Introduce sys_archive_host_xml_version CVar to select CryXmlVersion in the ArchiveHost.

-
**
Refactored:
**
Re-arrange Engine initialization to make the log and console available earlier for the project system.

-
**
Refactored:
**
Project manager to load using Yasli - removed the need for jsmn.

-
**
Refactored:
**
Refactored IEngineModule to never check by string.

-
**
Refactored:
**
Simplify plugin shutdown.

-
**
Refactored:
**
Remove CSystem::SetAffinity as it should be controlled via .thread_config.

-
**
Refactored:
**
Renamed CDebugAllowFileAccess to CScopedAllowFileAccessFromThisThread and added SCOPED_ALLOW_FILE_ACCESS_FROM_THIS_THREA?D macro.

-
**
Refactored:
**
Added better debugging capabilities to CListenerSet:.

-
**
Refactored:
**
CFunctorsList uses parameter pack.

-
**
Refactored:
**
Remove sys_plugin_reload command until it can be implemented correctly.

-
**
Optimized:
**
Replaced Cry_XOptimise and renderer SSE code with standard Vec4 code. Merged Matrix44H and Matrix44CT definitions.

-
**
Optimized:
**
New versions of vectors and matrices based on SIMD types: Vector4H, PlaneH, Matrix34H, Matrix44H. #CRY_HARDWARE_VECTOR4 substitutes these for non-SIMD versions. Vec4f etc. are typedefs for _tpl versions when unaligned access is needed. Added unit tests to perform timings and validation on H classes. Perform QuadraticTest on f64s to better test algorithm.

-
**
New:
**
SIMD_traits for scalar/vector type relationships. Horizontal min, max and add functions. Template specializations for specific shuffle configurations. convert<T*> to load from memory into SIMD. Changed 2-argument shuffle<> to mix0011<> and mix0101<> to indicate what they actually do.

-
**
Fixed:
**
Make sure all static geometry is included when saving level statistics.

-
**
Fixed:
**
Set dev-mode flag earlier to allow modification of cheat CVars from config files in the Launcher.

-
**
Fixed:
**
Unregister CVars before their owners are destructed. Removed IAutoCleanup.

-
**
Fixed:
**
Do not try to load plugins that do not exist on disk.

-
**
Fixed:
**
Updated path for default font xml.

-
**
Fixed:
**
Global IsEquivalent was not specialized with correct epsilon for Vec3.

-
**
Fixed:
**
Remove debug #pragma message from happening during compilation.

-
**
Fixed:
**
AISystem now gets initialized after FlowGraphSystem (otherwise it won't be able to register FG nodes).

-
**
Fixed:
**
CVars marked as cheat are visible in the console in release builds.

-
**
Fixed:
**
Assert pop-up window doesn't display reason message of previous assert when no message is specified.

-
**
Fixed:
**
 Assert when attaching remote console.

-
**
Fixed:
**
 Engine root being added as a pak mod - resulted in files in Engine root being constantly being searched for - causing slowdowns and unrelated files added to file browsers. Additionally added %EDITOR% pak alias to avoid future issues with loading Editor assets.

-
**
Fixed
**
: (CrashRpt) Missing crash dumps on Windows 7/8 - improves reported callstack for CryFatalError.

-
**
Fixed:
**
 (CryMovie) Debugbreak in LightAnimaitonSets.

-
**
Tweaked:
**
Move legacy game folder functionality to the project system.

-
**
Tweaked:
**
(XboxOne) Update to Durango XDK March 2017.

-
**
Tweaked:
**
(Orbis) Update to SDK 4.008.131.

-
**
Tweaked:
**
Add support for using relative paths with the -project command line argument.

-
**
Tweaked:
**
Automated calling of ModuleInitISystem.

-
**
Tweaked:
**
Removed need to specify class name when loading plugins through code - instead automatically select first ICryPlugin implementation in the module.

-
**
Tweaked:
**
(Orbis) Log assert messages via SCE API, this way assert from non-main-threads become visible immediately. Also, implement sys_asserts=3 mode (debug-break).

-
**
Tweaked:
**
Use std::numeric_limits::epsilon instead of a self-written approach to checkGreaterZero.

##
WAF

-
**
Fixed:
**
ScaleformHelper usage by WAF (all configs) and CMake (release config).

-
**
Tweaked:
**
Don't monolithically link MonoBridge into release configs - it's an optional feature.

-
**
Tweaked:
**
Copy the right portaudio binaries (performance and release config).

##
CMake

-
**
New:
**
Allow building PakEncrypt with CMake.

-
**
New:
**
Added option to enable/disable building the Engine itself.

-
**
New:
**
Allow building CryScaleformHelper with CMake.

-
**
New:
**
Allow building Shader Cache Generator with CMake.

-
**
Refactored:
**
Removed obsolete MSVC toolchain to avoid confusion.

-
**
Refactored:
**
Removed MS-customised CMake (it's not new enough).

-
**
Optimized:
**
Don't copy unnecessary debug DLLs or PDBs to bin/win_x64.

-
**
Optimized:
**
Only copy .pdb and .dll files to bin/* when they are required by build options.

-
**
Fixed:
**
 CMake configuration fixes.

-
**
Fixed:
**
Make GCC use LLVM std.

-
**
Fixed:
**
CMake generation of Durango Solutions.

-
**
Fixed:
**
Set plugin options before parsing CMakeLists.txt files.

-
**
Fixed:
**
Sandbox Editor compilation with Visual Studio 2017.

-
**
Fixed:
**
GameTemplate solution contains an invalid path as a debug command.

-
**
Fixed:
**
Build without CrySchematyc.

-
**
Fixed:
**
Visual Studio 2017 compilation fixes.

-
**
Fixed:
**
ShaderCacheGen needs png16 as it depends on the renderer.

-
**
Fixed:
**
Missing Schematyc modules in a clean CMake solution.

-
**
Fixed
**
: Optional libraries were not getting included in the final build if using their default values.

-
**
Fixed
**
: Fix Static Linking (OPTION_STATIC_LINKING) by using /WHOLE ARCHIVE Visual Studio 2015 linker option, to prevent linker optimizing away static factory registrations.

-
**
Fixed
**
: Speeding up MSVC compilation with IncredibBuild and with uber files enabled.

-
**
Tweaked
**
: Added option to allow unsigned PAK files for release builds.

-
**
Tweaked
**
: Don't deploy Mono files on every compilation - this will be handled by the build system.

##
Action General

-
**
New:
**
Added Stats:TextureStreaming flow node.

-
**
Refactored:
**
CGameObject aspects serialization is redirected to CNetEntity.

-
**
Refactored:
**
IGameObjectExtension::SetAuthority has been converted to ENTITY_EVENT_SET_AUTHORITY. * Example client->server and server->clients RMI messages. * PlayerInput sends keystrokes over the network through aspects. * Server-authoritative player movement. * Multiple clients can connect to the listen server.

-
**
Refactored:
**
Decouple connection events from game rules.

-
**
Fixed:
**
Proper entity component declarations for CAnimatedCharacterComponent.

-
**
Fixed:
**
Broken vehicles do not go through their states of damage properly.

-
**
Fixed:
**
Starting GameLauncher triggers vehicle LUA-errors in console.

-
**
Fixed:
**
Freeze during shutdown.

-
**
Fixed:
**
"CEntityObject::Reload" reported an error because the saved "GameObject entityComponent" could not be loaded from xml.

-
**
Fixed:
**
Shutdown crash.

-
**
Fixed:
**
std::vector returned from Interface.

-
**
Fixed:
**
Broken SpawnSerializer for non-default GameObject extensions.

-
**
Fixed:
**
Abrams tank not displayed in first person view mode.

-
**
Fixed:
**
CFlowplayer::LocalPlayerId - Temporarily brakes Rolling Ball template. In Sandbox Editor, on Ctrl-G, the ball spawn location is incorrect.

##
Flowgraph

-
**
New:
**
Added right-click option on nodes to (un)assign the selected Prefab.

-
**
New:
**
Right-click on a Prefab Instance in the Viewport to get its usage in Flowgraph.

-
**
New:
**
Double-click on a Prefab:Instance node to select the prefab instance in the Viewport.

-
**
New:
**
Exposed script physics params to Flowgraph (in a better way than before).

-
**
New:
**
Extract Flowgraph from CryAction to a plugin.

-
**
New:
**
Added a Math:Wrap node that wraps a value into a given interval.

-
**
New:
**
Added a "Red" output to the Camera:GetTransform node.

-
**
New:
**
New flownodes: "GameEntity:Containers:Add/Remove Entity", "Merge", "Clear", "Actions", "QueryContainerSize", "QueryRandomEntity", "QueryContainerId", "QueryIsInContainer", "QueryEntityByIndex", "Listener", "Filters".

-
**
New:
**
Entity Containers for Flowgraph - a system to manage and operate on sets of entities.

-
**
New:
**
New node Entity:GetChildrenInfo for getting the ids and number of children of an entity.

-
**
New:
**
 Entity:CheckDistance to work with world position with linked entities.

-
**
New:
**
Entity:BeamEntity now supports Parent coordinate system as well as World. Removed unused Memo port.

-
**
New
**
**
:
**
 Added Timer Type (in flow node time) - Timer allows the selection of the Engine timer type to use (i.e. default or UI timer). This is useful for e.g when using this node in UI_Actions Flowgraph even when game update is paused.

-
**
New:
**
 Extending Time:RealTime FG Node to add day, month and year.

-
**
New:
**
 Added a node to select flags to combine from a drop down list.

-
**
New:
**
 Added inputs to Physics:RayCast and PhysicsRayCastCamera to allow Designers to enter their collision flags.

-
**
New:
**
 Added some outputs to Physics:RayCast so that it matches the output of Physics:RayCastCamera.

-
**
New:
**
 Added a new node for converting a physics part ID to a joint ID/name.

-
**
New:
**
 Added FG node "AI:BehaviorTree".

-
**
New:
**
 Added a Math:Wrap node that wraps a value into a given interval.

-
**
New:
**
 Added an input to the interpol-nodes - allows to change the transition-function which is applied to the result.

-
**
New:
**
 Added an Interpol:Easing node that applies an easing-function to a given percentage in a range between 0 and 1.

-
**
New:
**
 Added new flownodes "Math:AutoNoise1D" and "Math:Auto3DNoise".

-
**
New:
**
 New FG node Engine:ShadowCacheParams for changing shadow cascade parameters.

-
**
New:
**
Added flow node "Engine:OcclusionAreaSwitch" to toggle occlusion areas within an area.

-
**
Refactored:
**
CHyperGraphDialog interface - cleanup unused functions and component interactions.

-
**
Refactored:
**
Fix inconsistent smart pointer usage and dangling pointer crash.

-
**
Refactored:
**
Rename one of the CFlowGraph classes to CHyperFlowGraph to avoid confusion.

-
**
Refactored:
**
Add get ports to FG nodes 'Entity:Velocity' and 'Physics:Dynamics'.

-
**
Optimized:
**
Block unnecessary UI updates during level unload for the full window and not just the tree list.

-
**
Optimized:
**
Minimize performance impact when rebuilding prefab instance FGs by about 1/5th of the time.

-
**
Optimized:
**
Do not rebuild all Prefab Instance graphs when using the quicksearch node.

-
**
Optimized:
**
Change collision FGN's RemoveAll to only remove listeners registered through this node.

-
**
Optimized:
**
Removed Game:Stop node - as it does not serve any real purpose.

-
**
Fixed:
**
 Crash on level load.

-
**
Fixed:
**
 Crash on game shutdown in CFlowNode_RaycastCamera.

-
**
Fixed:
**
 Changed the param of a material on an entity that was preventing changing the entity's material.

-
**
Fixed:
**
 PlayMannequinFragment should not queue a fragment if the id was incorrect.

-
**
Fixed:
**
 Bug in EntityFaceAt node that caused totally wrong world matrix to be applied to objects.

-
**
Fixed:
**
 Assert when asking the local rotation of a parented entity through FG.

-
**
Fixed:
**
 Vis area system now respects disabled occlusion areas.

-
**
Fixed:
**
FG debug not working.

-
**
Fixed:
**
Using CTRL+S in the FG window does not save the level.

-
**
Fixed:
**
Entity limit when selecting 'Add Selected Entity'.

-
**
Fixed:
**
'Add Comment Box/Black Box' not showing when right clicking on the selection.

-
**
Fixed:
**
The category view mask is no longer saved in the Windows registry, but via the personalization manager.

-
**
Fixed:
**
Graph naming and the title display.

-
**
Fixed:
**
Cases where deleting graphs would leave traces in the UI.

-
**
Fixed:
**
Exiting vr_demo triggers assert.

-
**
Fixed:
**
Newly created graphs not flowing without undo/redo.

-
**
Fixed:
**
Can't add a Flowgraph Entity as a node.

-
**
Fixed:
**
IFlowNode::SActivationInfo stores a pointer into std::vector which is invalided when the vector is resized.

-
**
Fixed:
**
Crash on shutdown.

-
**
Fixed:
**
Prefab Instance nodes sometimes firing events with the previous assigned instance.

-
**
Fixed:
**
Right-click "Find in Flowgraph" would not gain focus.

-
**
Fixed:
**
Entity Containers and AutoNoiseNodes after the Flowgraph extraction.

-
**
Fixed:
**
Sandbox Editor might crash on level load when DataBase View was modified before.

-
**
Fixed:
**
BlackBox comment type discards Flowgraph nodes in Game Launcher.

-
**
Fixed:
**
Using EntityChangeMaterial node causes affected Entity to not revert back to it's default material when jumping out of game mode.

-
**
Fixed:
**
Unhide GeomEntity does not work.

-
**
Fixed:
**
Added missing descriptions to some nodes and make Get methods const.

-
**
Fixed:
**
Tweaks and fixes for the properties window.

-
**
Fixed:
**
Tweaks and fixes for the nodes/components window.

-
**
Fixed:
**
Entity:Attachment Node - Allow bone names and character slots to be set after game start.

-
**
Fixed:
**
Flow nodes which can't handle linked entities.

-
**
Fixed:
**
'Physics:RayCastCamera' - Remove offset in raycast start and always exclude the player from the hit results.

-
**
Fixed:
**
 Possible crash if tokens contain different types.

-
**
Tweaked:
**
Set a debug name for the graphs for more useful warnings, debugging and profiling.

-
**
Tweaked:
**
Improve description of GameToken FlowNode port.

-
**
Tweaked:
**
Added node IDs to GameToken error messages.

-
**
Tweaked:
**
Fix the Shadow-refresh node (the previous code-path did not perform the necessary refresh).

-
**
Tweaked:
**
Added a node "Environment:RefreshStaticShadows" to force-static shadow refresh on changing settings/fast-travel/menu transitions etc.

-
**
Tweaked:
**
Added a temporary workaround string for Formats.

-
**
Tweaked:
**
Added 'Get' port to 'Entity:ParentId' node.

-
**
Tweaked:
**
Added comment to Entity:GetPos about scale coordinate system.

-
**
Tweaked:
**
 In fg_debugmodules - render instance number first, then the name so it doesn't get trampled with long module names.

-
**
Tweaked:
**
 Add r_shadowscache CVar to the exposed parameters in Shadow FG node.

##
Game

-
**
Optimized:
**
Whizby and ricochet audio objects don't need occlusion to be enabled.

-
**
Fixed:
**
Unnatural gap between tornado's main part and top part.

-
**
Fixed:
**
For locked head rotation in multiplayer.

-
**
Fixed:
**
Abrams turret playing sound after overheating.

-
**
Fixed:
**
Audio trigger 'Stop_w_tank_machinegun_fire' spammed after firing the Abrams machine gun.

-
**
Fixed:
**
Assertion failure while idling in the Sandbox Editor and holding the grenade (SaltBufferArray.h: rSalt > oldSalt).

##
Schematyc

-
**
New:
**
Added Impulse and AngularImpulse to the physics component.

-
**
New:
**
Display error when sender GUID is not passed with component/action signal.

-
**
New:
**
Added a CrySystemsComponent to allow communication with other systems (currently game tokens, but trackview or FG could be other options in the future).

-
**
New:
**
Simplify component registration.

-
**
New:
**
Update action instance.

-
**
New:
**
Implement compile-time reflection tests on all compilers.

-
**
New:
**
Added author and description to env packages.

-
**
New:
**
Create experimental action node.

-
**
New:
**
Implement signal 'sender' filtering system.

-
**
New:
**
Added Clamp nodes for vec2,3 and floats.

-
**
New:
**
Added basic DRS component.

-
**
New:
**
Added flags for the move-function, but to only set specific components of the movement vector.

-
**
Refactored:
**
Unify runtime params with runtime graph node instance params: Where possible replace CRuntimeParams with CRuntimeParamMap.

-
**
Refactored:
**
Refactor geom component to use new registration method.

-
**
Refactored:
**
Refactor components to use new registration method.

-
**
Refactored:
**
Deprecate custom component properties.

-
**
Refactored:
**
Simplify IEnvComponent interface.

-
**
Refactored:
**
Clean up reflection system.

-
**
Refactored:
**
Remove author and wikilink from env elements.

-
**
Refactored:
**
Simplify IEnvDataType interface.

-
**
Refactored:
**
Simplify IEnvSignal interface.

-
**
Refactored:
**
Clean up IScriptElement interface.

-
**
Refactored:
**
Unify property setup to use new entity component properties.

-
**
Fixed:
**
 Range checks were missing when setting FOV from property.

-
**
Fixed:
**
Input::Action-Signals are not called and expose different interfaces.

-
**
Fixed:
**
QuatToString - More parameters than specified by the format string.

-
**
Fixed:
**
Reverted a change to PropertiesWidget to handle object deletion since it crashed.

-
**
Fixed:
**
SetVisible/IsVisible of the GeomComponent was not working.

-
**
Fixed:
**
Non-working signal-receiver - component-bound-signals were sent by the object and not though the component.

-
**
Fixed:
**
LineStarted/Ended Signal was not sent correctly.

-
**
Fixed:
**
Compilation of input component.

-
**
Fixed:
**
Copy/Paste Offset.

-
**
Fixed:
**
Connections were deleted when clicking on parameter name.

-
**
Tweaked:
**
Some of the input-key names.

##
Templates

-
**
New:
**
Added Third Person Shooter template to the C# game templates.

-
**
New:
**
The C++ RollingBall template is now network-enabled.

-
**
Refactored:
**
CGameObject deprecation - Converted RollingBall template to use IEntityComponents + CEntity instead of CGameObject for the player (ball).

-
**
Fixed:
**
RollingBall template is displayed as a Blank template in the Sandbox Editor.

-
**
Fixed:
**
Update the ball look direction for remote players.

-
**
Fixed:
**
 Restore the network sync feature in the RollingBall template.

##
ProfVis

-
**
New:
**
Added pan left and right - once zoomed by holding the middle mouse button.

-
**
New:
**
Clicking on a function (in the treeview or datagrid view) will show everything running at the same time on all threads.

-
**
New:
**
Added filter all functions above a certain threshold.

-
**
New:
**
Added filter name and args separately.

-
**
New:
**
Added number of calls if the function is called multiple times in the scope.

-
**
New:
**
Call Graph on the right (highlighting the problematic parts).

-
**
Fixed:
**
Server crash of ProfVis if sys_bp_frames_threshold != 0.

-
**
Fixed:
**
Improved BootProfiler multithread safety.

-
**
Tweaked:
**
Added sys_bp_frames_worker_thread, which allows to have the ProfVis running in "Gather frames under certain threshold" mode and without affecting the main thread (It uses a worker thread to dump the sessions).

##
Auto Testing

-
**
Refactored:
**
Refine test log error output, fall back value output as byte dump and unsigned output to provide both decimal and hexadecimal.

-
**
Refactored:
**
Move interprocess communication (StatsAgent) to CrySystem for supporting non-GameSDK games to improve windows launcher.

-
**
Refactored:
**
Integrate unit test target, cleanup unit test system, auto open report for failed tests when using excel reporter and to simplify excel report rules.

-
**
Fixed:
**
 Communication pipe - improved code spelling, formatting, quality and header inclusion dependencies.

-
**
Tweaked:
**
Encourage value comparisons in tests - instead of testing true/false.

-
**
Tweaked:
**
Fix timedemo shutdown crash by preventing cross module allocation.

-
**
Tweaked:
**
Code modernization, misspelling fixes, leak fixes.

-
**
Tweaked:
**
Added command line option for opening report locally when test fails.

-
**
Tweaked:
**
Added guard condition to fix error for non-engine builds - caused by unit test target.

##
C#

-
**
New:
**
Introduce support for Xamarin Studio.

-
**
New:
**
Added install file for the Xamarin Studio CryEngine Addin, which allows debugging C# projects in Xamarin Studio.

-
**
New:
**
Add support for C# plugins not implementing ICryEnginePlugin, for example to provide a pure component collection.

-
**
New:
**
Introduce basic support for compiling *.cs files from the asset directory at startup.

-
**
New:
**
Introduce new Third Person Shooter template.

-
**
New:
**
Managed Audio wrapper.

-
**
New:
**
Managed wrapper for Animation and Character classes.

-
**
New:
**

CVars and Console Commands can now be created from C#.

-
**
Refactored:
**
Wrap mono API in new MonoInternals namespace.

-
**
Refactored:
**
Replace singleton interface based API with direct access of implementation.

-
**
Refactored:
**
Remove IListener from swig and implemented it natively in the managed Audio wrapper.

-
**
Refactored:
**
Wrap math classes to avoid excessive virtual calls and marshaling.

-
**
Refactored:
**
 EntityClassAttribute has been deprecated and functionality was moved to the EntityComponentAttribute.

-
**
Refactored:
**
The EntityComponent now has a default icon in the Sandbox.

-
**
Fixed:
**
Conversion of managed strings to native causing memory leaks.

-
**
Fixed:
**
Plugin dll's being locked after loading, preventing rebuild for reload.

-
**
Fixed:
**
Crash after reloading assemblies multiple times.

-
**
Fixed:
**
Improper shutdown of domains and failure to unpin objects after serialization.

-
**
Fixed:
**
Serialization of read-only fields, added unit test.

-
**
Fixed:
**
Add the AllowDuplicate functionality to the C# components.

-
**
Fixed:
**

*
EntityComponent.OnUpdate
*
 not being called every frame.

-
**
Fixed:
**
 Textures never being removed causing a memory leak.

-
**
Tweaked:
**
Remove flow node systems from C# CryEngine.Core assembly.

-
**
Tweaked:
**
Expose
*
EntityComponent.OnGameplayStart
*
, OnRemove and OnEditorUpdate.

-
**
Tweaked:
**
Updated Swig to version 3.0.12.

-
**
Tweaked:
**
Cache entity callbacks to avoid querying at runtime.

##
C# Backend

-
**
Fixed:
**
Prevent compiling every C# file on the disk when asset directory cannot be found.

-
**
Tweaked:
**
Improve devirtualization inside own module.

-
**
Tweaked:
**
Expose IMonoMethod interface in order to clarify API - now allows for querying methods independently of invoking them as a future optimization.

##
Graphics and Rendering

##
Renderer General

-
**
New:
**
Added Vulkan support.

-
**
New:
**
Ported snow rendering passes to new graphics pipeline.

-
**
New:
**
Ported rain rendering passes to new graphics pipeline.

-
**
New:
**
Added CRainStage and CSnowStage for new graphics pipeline.

-
**
New:
**
Ported CHUDSilhouette to new graphics pipeline.

-
**
New:
**
Ported CHUD3D to new graphics pipeline.

-
**
New:
**
Added Color and RGBA conversion to silhouette param to HUDUtils.

-
**
New
**
: Implemented ApplyForceToEnvironment for grid wind.

-
**
New
**
: Implemented shader extensions files support from GameShaders folder.

-
**
New:
**
 (Brush.cpp) Added application of IRenderNode silhouette param during render step in CBrush::Render(const struct SRendParams& _EntDrawParams, const SRenderingPassInfo& passInfo) to make use of new SExposedPublicRenderParams from IRenderNode.h.

-
**
New:
**
(CharacterRenderNode.cpp) Added application of IRenderNode silhouette param during render step in void CCharacterRenderNode::Render(const SRendParams& inputRendParams, const SRenderingPassInfo& passInfo) to make use of new SExposedPublicRenderParams from IRenderNode.h.

-
**
New:
**
 (IRenderNode.h) Added tracking of silhouette param value.

-
**
New:
**
Ported CFilterSharpening, CFilterBlurring, CUberGamePostProcess, CFlashBang, CFilterKillCamera, CScreenBlood, and CPostStereo to new graphics pipeline.

-
**
New:
**
Ported water flow, water droplets and underwater GOD rays to new graphics pipeline.

-
**
New:
**
Added post effect stage for new graphics pipeline.

-
**
New:
**
Ported TexBlurAnisotropicVertical to new graphics pipeline.

-
**
New:
**
Added terrain debugpass.

-
**
New:
**
Added terrain zprepass.

-
**
New:
**
Restored vegetation billboards (by default disabled by CVar).

-
**
New:
**
Added CV_CameraRightVector to CBPerViewGlobal.

-
**
New:
**
Expose new IRenderer::CreateTextureArray function.

-
**
New:
**
Added defrag allocator support for validating that unpinned blocks don't change content over time.

-
**
Refactored:
**
Remove deprecated Cloud entity.

-
**
Refactored:
**
Added DecalAngleBasedFading parameter for e.g. for snow effect on objects.

-
**
Refactored:
**
Removed obsolete property Waves Speed for Ocean Animation.

-
**
Refactored:
**
Removed deprecated VolumeObject entity.

-
**
Refactored:
**
Small changes for compatibility with VecH types. Added UFloat4.Load function - works with scalar or SIMD types simplifying lots of code.

-
**
Refactored:
**
TerrainLayer shader improvements: Enabled in-shader real-time diffuse texture high-pass filter with radius adjustable in material properties. This removes the requirement to high-pass textures in RC and from now on the same texture file may be used for terrain and other objects. Also supported direct diffuse texture mode allowing to bypass any terrain specific diffuse texture processing. This simplifies the matching of the look of terrain and other objects.

-
**
Refactored:
**
Removed rendering functionalities in old graphics pipeline such as rain, snow and water normal gen.

-
**
Fixed:
**
NaN when %DEPTH_FIXUP is enabled.

-
**
Fixed:
**
Stack stomp caused by cubemap uploads.

-
**
Fixed:
**
SVOGI specular tracing flicker.

-
**
Fixed:
**
Disable sharing of compiled object between shadows and non-shadows as this is not thread safe.

-
**
Fixed:
**
Race condition between gbuffer rendering and shadowmap prepare - same compiled object could be used for gbuffer rendering while being compiled for shadowmaps.

-
**
Fixed:
**
SVOGI not waiting for shadow rendering to complete.

-
**
Fixed:
**
Volume texture updates.

-
**
Fixed:
**
Broken "e_debugdraw" modes.

-
**
Fixed:
**
Crash when removing entities on dedicated server.

-
**
Fixed:
**
CRenderMesh and CRenderElement leaks when chain-loading levels.

-
**
Fixed:
**
Broken glass shader with NEAREST Flag

-
**
Fixed
**
: Fixed volume based tiled shading for non-opaque objects.

-
**
Fixed:
**
Assertion triggered when rotating a water volume around the X And Y axis.

-
**
Fixed:
**
Assertion is triggered when a water volume material asset is set to Ocean Material property in Level Settings.

-
**
Fixed:
**
Adjusted GI temporal reprojection.

-
**
Fixed:
**
Made each utility pass a unique instance within CStandardGraphicsPipeline::Execute.

-
**
Fixed:
**
Crash happens in CStandardGraphicsPipeline::ExecuteAnisotropicVerticalBlur.

-
**
Fixed:
**
Made scissor-rectangle culling always enabled to adapt DX12 bahavior.

-
**
Fixed:
**
CRenderPrimitive wrongly reuses CDeviceGraphicsPSO when vertex format changes.

-
**
Fixed:
**
Discrepancies between VR implementations.

-
**
Fixed:
**
Added tessellation to debug passes.

-
**
Fixed:
**
Directional map interpretation for hair.

-
**
Fixed:
**
 SelectionID pass depth buffer.

-
**
Fixed:
**
 Cubemap streaming upload assert.

-
**
Fixed:
**
 Clear rendertargets of HDRPipeline before use.

-
**
Fixed:
**
 Numeric coding of texture types, can't be changed in any way.

-
**
Fixed:
**
Broken LOD dissolve.

-
**
Fixed:
**
Broken HUD silhouette rendering.

-
**
Fixed
**
: Fixed shader asserts / crashes in NV Multires mode.

-
**
Fixed
**
: Fixed crash during Shaders generation.

-
**
Tweaked:
**
Fixed FileAccessScope error from warning.

-
**
Tweaked:
**
Made SkipAlphaTest a cheat and suppress interpretation in release builds.

##
Volumetric Fog

-
**
Optimized:
**
Reduced draw calls of clip volume rendering for volumetric Fog. This can't be used on PS4 because currently depth stencil array texture is prohibited on PS4 renderer.

-
**
Fixed:
**
A potential issue that wrong sampler state could be used.

-
**
Fixed:
**
Shader compilation error on PS4.

-
**
Fixed:
**
Added the implementation for not using depth stencil array texture - currently needs CryRenderD3D11 instead of CryRenderGNM.

-
**
Fixed:
**
Crash happens at CCryDX12DeviceContext::BindResources in recursive render pass when activating DX12 renderer.

-
**
Fixed:
**
Crash happens at CWaterStage::PreparePerPassResources when moving to the level which doesn't have global environment probes.

-
**
Fixed:
**
Clip Volume texture for volumetric fog isn't initialized properly when shaders are compiled asynchronously.

-
**
Tweaked:
**
Time of Day default values to make volumetric fog look physically correct.

##
Volumetric Clouds

-
**
New:
**
Added noise texture properties for Volumetric Cloud.

-
**
Fixed
**
: Fixed CloudBlocker entity doesn't work.

##
3D Engine

-
**
New:
**
Support for integration of object meshes into terrain mesh. Allows overcoming multiple limitations of current heightmap editor.

-
**
New:
**
Checkboxes for the GameToken node to trigger on start and to only trigger when the value changes.

-
**
New:
**
Warnings for Designers about forced conversions and missing tokens. Remove spurious warning for not found graph tokens.

-
**
New:
**
Added RenderNodeStatusListener to Engine interface.

-
**
Refactored:
**
Removed traversal over render node slots (because now we only have one).

-
**
Refactored:
**
Removed obsolete parameters in a few functions in IRenderNode interface.

-
**
Refactored:
**
Movable brush render node separated into stand-alone eERType_MovableBrush type.

-
**
Refactored:
**
Reduce the default game template files required by the Engine.

-
**
Refactored:
**
Tokens have their default value on game start and Sandbox Editor jump to game without triggering.

-
**
Refactored:
**
 Added CVar to control integration of object meshes into terrain mesh.

-
**
Optimized:
**
Removed IEntity* m_pOwnerEntity from IRenderNode (saved 30MB).

-
**
Optimized:
**
Level load/unload speedup by adjusting cached shadows processing.

-
**
Optimized:
**
Cache comparison values in the nodes with correct type.

-
**
Optimized:
**
(SVOGI) Optimized global env probe search code.

-
**
Optimized:
**
(SVOGI) Underground voxelization is allowed for selected brushes ("Support Secondary Visarea" flag).

-
**
Optimized:
**
(SVOGI) Added thread affinity CVars for GI voxelization (for consoles).

-
**
Optimized:
**
(SVOGI) Added budget CVar (e_svoMaxAreaMeshSizeKB) limiting amount of geometry voxelized per area (by skipping less important objects).

-
**
Fixed:
**
(Vegetation) Crash when enabling painting certain vegetation assets with "auto merged" enabled. High-poly objects are automatically skipped from merging if number of polygons is higher than e_MergedMeshesMaxTriangles.

-
**
Fixed:
**
Crash on dedicated server during the level unload.

-
**
Fixed:
**
(VR) Oculus crashes on startup.

-
**
Fixed:
**
Support coll_type in surfacetypes for individual phys proxies of a node.

-
**
Fixed:
**
Crash in IMaterial release by compiled render object.

-
**
Fixed:
**
Buffer overrun on load level (reproduced in Win32 build).

-
**
Fixed:
**
Restored capsule shadows support.

-
**
Fixed:
**
Restored LOD dissolve on entities.

-
**
Fixed:
**
Dangling entity pointer workaround.

-
**
Fixed:
**
StatObj leak caused by refcount-deadlock.

-
**
Fixed:
**
Workaround for terrain texture exported in a platform incompatible format: decompression on CPU.

-
**
Fixed:
**
Assert on removing graph tokens.

-
**
Fixed:
**
Problem with graph token registration - made obvious when having tokens with the same name on different FG Modules.

-
**
Fixed:
**
Static object GetExtent not working when render mesh was not yet loaded.

-
**
Fixed:
**
Tokens have the data type that is defined instead of always string, plus fix wrong type conversions.

-
**
Fixed:
**
Character capsule shadows.

-
**
Fixed:
**
Durango Debug/Release compilation.

-
**
Fixed:
**
An issue with foliage cleanup.

-
**
Fixed:
**
(SVOGI) Added protection against rare GPU hang.

-
**
Fixed:
**
(SVOGI) Incorrect unload of old unused voxel segments.

-
**
Fixed:
**
(SVOGI) Cases when GI voxelization skipped some areas (on consoles).

-
**
Fixed:
**
(SVOGI) Interiors are rendered too bright in daylight.

-
**
Fixed:
**
CBrush::OnRenderNodeBecomeVisible is not Thread Safe.

-
**
Fixed:
**
Vegetation billboards - Fixed unwanted processing if feature is not used, (caused crash in some cases).

-
**
Fixed:
**
Geometric mean calculation of sub-objects.

-
**
Fixed:
**
Broken SVOGI voxelization. Fixed analytical proxies not working together with voxels.

-
**
Fixed:
**
SVOGI memory corruption.

-
**
Fixed:
**
MP - Let your avatar be killed several times triggers assert.

-
**
Fixed:
**
Activating auto merge feature on dead tree assets crashed the Sandbox Editor.

-
**
Fixed:
**
Placing several GeomChache-entities will make them look blurred.

-
**
Fixed:
**
 Missing UI reaction for 'objects into terrain mesh integration' feature.

-
**
Fixed:
**
 CVar "e_ViewDistRatioLights" not being updated.

-
**
Fixed:
**
 (VR) Oculus headset works, but GameLauncher.exe-window only shows black screen.

-
**
Tweaked:
**
Profile marker tweaks.

-
**
Tweaked:
**
Add graph name to game token warnings.

##
Particles

-
**
New:
**
MotionCryPhysics now has option for Mesh (rigid-body) physics. SurfaceType implemented as dynamic enum; Density converted to g/ml.

-
**
New:
**
Particle templates.

-
**
New:
**
Added Collision.RotateToNormal option (useful for SecondGenOnCollide spawning). Added Decal.Thickness option, pfx1 conversion for Decals.

-
**
New:
**
CVar to automatically replace pfx1 effects with pfx2 in-game. Also conversion tweaks.

-
**
New:
**
More improvements to particle attribute implementation - setting age to 1.0 is enough no need to set ES_EXPIRED.

-
**
New:
**
(Entity) Added spawn params structure to ParticleEntity.

-
**
New:
**
Added spawn params to particle emitter.

-
**
New:
**
Implemented count scale, speed scale and size scale from SpawnParams.

-
**
New:
**
(Entity) Particle entity only restarts emitter when needed and not any time serialization is executed.

-
**
New:
**
(Entity) Added restart and kill buttons to particle entity.

-
**
New:
**
Particle color attributes are stored as ColorB.

-
**
New:
**
(Entity) Particle entity can change custom emitter attributes.

-
**
New:
**
(Schematyc) Particle component can change emitter attributes.

-
**
New:
**
(Schematyc) Added SetParameters node to particle component to change spawn params settings during runtime.

-
**
New:
**
(Schematyc) Added set attributes nodes.

-
**
New:
**
Reset particle emitter entity connection when a GeomRef is specifically set.

-
**
New:
**
(Schematyc) Added SetSpawnGeometry node to particle component and GetGeom node to geometry component.

-
**
New:
**
Added axis option to location circle and velocity cone.

-
**
New:
**
Camera Distance time source.

-
**
New:
**
SpawnParams now allows to override particle spec.

-
**
New:
**
Added memory utilization stats per runtime.

-
**
New:
**
 Added offset to render sprites.

-
**
New:
**
Added camera offset to sprites.

-
**
New:
**
Bring back attribute modifier - more practical than just using Linear modifier.

-
**
New:
**
Added offset option to ribbons.

-
**
New:
**
Initial version of Render:Decals.

-
**
New:
**
Added debug draw bounding box.

-
**
New:
**
Moved particle display stats to particle system and changed the way it gets displayed.

-
**
New:
**
New Wavicle display and statoscope stats.

-
**
New:
**
"updated particle" stats should always be consistent.

-
**
New:
**
Much improved collision behavior, no more missed collisions, consistent bounce and slide. Log collision only when not sliding. Use faster and more reliable Terrain.RayTrace. Added sliding friction.

-
**
New:
**
Implemented priming - set update time to equilibrium time when primed. Should only occur on level startup or when testing. No update time subdividing yet, many functions currently do not work well with long update times.

-
**
New:
**
(Flowgraph) Added AttributeSet and AttributeGet flow nodes.

-
**
New:
**
SpawnDistance now uses actual inter-particle distance, rather than sometimes-absent velocity.

-
**
New:
**
More conversions from pfx1 - Connection, TailLength, OnParentCollide, Restart (Pulse), more Facing modes, Spiral (Turbulence), Collisions, LightSource, AudioSource, BindEmitterToCamera, Visible Indoors/Underwater, SortBias, Comment.

-
**
Refactored:
**
Improve UpdateRanges to allow range-based looping.

-
**
Refactored:
**
Removed legacy particle attribute integration with LUA.

-
**
Refactored:
**
SpawnParams now has regular Serialisation function.

-
**
Refactored:
**
Reimplemented attribute type auto-conversion using a type table instead of switch cases.

-
**
Refactored:
**
Removed some render sprites static dispatching - no performance implication.

-
**
Refactored:
**
Merging write to GPU functions in feature sprites - no performance implication.

-
**
Refactored:
**
Decoupled FeatureCollision from FeatureMotion, added EUL_PostUpdate.

-
**
Optimized:
**
Reduce the number if 3D Engine re-registers by caching an inflated bbox.

-
**
Optimized:
**
Do not update emitters which are set to invisible.

-
**
Optimized:
**
Only update emitter vis and phys environment when cached bounds also change.

-
**
Optimized:
**
Created separate vectors for CPU and GPU runtimes to prevent some virtual calls.

-
**
Optimized:
**
Avoiding some asserts in profile builds and only have them in debug builds instead.

-
**
Optimized:
**
Improved DragFastIntegral, much more accurate for long update times, almost as fast as quadratic.

-
**
Fixed
**
: Bug fixes from dev_wavicle: out-of-bounds array crash on instance restarts; incorrect stream access in ParentSpeedSampler; null-stream access in SpawnParams code; bug in FieldColor modifiers (HNT-17675).

-
**
Fixed:
**
Crash when changing spawn in direction of effect while running.

-
**
Fixed:
**
Implemented Get/SetOwnerEntity. Emitters now search consistently for EmitGeom in all slots.

-
**
Fixed:
**
Null-stream access in SpawnParams code.

-
**
Fixed:
**
Changing effect options were not properly setting the asset to modified.

-
**
Fixed:
**
Lifetime not properly clamped when modifiers can make them negative.

-
**
Fixed:
**
Emitter ID improperly initialized - sorting profiler entries undefined.

-
**
Fixed:
**
Crash fix in profiler - display profiler before trimming emitters.

-
**
Fixed:
**
Color curve modifier was not using scale and bias parameters.

-
**
Fixed:
**
Null pointer access in CParticleComponent::SetName.

-
**
Fixed:
**
RenderMeshes and LocationGeometry attachment now properly use particle sizes. Load full mesh w/o streaming when accessing pieces.

-
**
Fixed:
**
Location Bind to camera was not properly aligning particles when the camera moved.

-
**
Fixed:
**
Particles killed by KillOnParentDeath were not triggering SecondGen:OnDeath.

-
**
Fixed:
**
Extra Instance creation that could double particles created. Fixed Emitter.EmitParticle and AddInstance. Streamlined some functions.

-
**
Fixed:
**
Particle effect edit version takes into consideration all component material modification ID - prevents renderer crashes after editing a material.

-
**
Fixed:
**
Enforce hard limits on Params.

-
**
Fixed:
**
(Entity) Properly setting attribute table when jumping into game mode.

-
**
Fixed:
**
Independent emitters could sometimes stay active forever.

-
**
Fixed:
**
(UI) Fixed Load Selected Entity and Particle Edit buttons.

-
**
Fixed:
**
First generation immortal particles where not being removed after inactivating an emitter.

-
**
Fixed:
**
Ribbons lighting in free mode.

-
**
Fixed:
**
Screen space collisions in fluid dynamics.

-
**
Fixed:
**
CRY_DEBUG_PARTICLE_SYSTEM to actually define pragmas.

-
**
Fixed:
**
More timing fixes - SecondGenOnDeath now spawns at correct sub-frame time. NormalAge again allowed > 1 to determine death time. Spawn start age now more accurate. Merged TriggerParticles functions.

-
**
Fixed:
**
Removed all runtime instances when emitter is deactivated; prevents emitters which are supposed to be dormant from creating new particles.

-
**
Fixed:
**
Improper physic and vis environment initialization when emitter bounding box changed sizes.

-
**
Fixed:
**
Collision improvements - Collisions now more accurate using prev and cur positions. Combined collision detection and response. SecondGenOnCollision is now sub-frame correct. Removed threshold on collision frame-time. Changed contact flags to much simpler bitfield. Generalised TriggerParticles to take SInstance array.

-
**
Fixed:
**
Avoiding texture memory leaks.

-
**
Fixed:
**
Several pfx1 conversion issues.

-
**
Fixed:
**
 The feature AudioTrigger now allows both a start and stop trigger in the same feature - makes it consistent with other audio triggers in the Engine.

-
**
Fixed:
**
 Crash in creating unique component name, and generalized to work with no number limit.

-
**
Tweaked:
**
RenderSprites.axisScale default = 0.

##
PS4 Renderer

-
**
New:
**
Ported to new render pipeline

-
**
New:
**
Support for HW Tessellation pipelines (on-chip only).

-
**
New:
**
Support for GeometryShader pipelines (on-chip and off-chip).

##
XBox One Renderer

-
**
Optimized:
**
Durango texture defrag support.

-
**
Fixed:
**
Fixed Z-target downsampling.

-
**
Tweaked:
**
Fixed texture pool size to 1.5GB - streaming now uses texture pool size as a guide and relies upon defrag to ensure allocation success.

##
Physics

##
Physics

-
**
New:
**
Added standalone phys debugger and support for binary world dumps.

-
**
New:
**
Added ground planes to world dump.

-
**
New:
**
Storing partid in contacts result when doing PWI.

-
**
New:
**
Support multiple grids/local simulation (initially disabled).

-
**
Optimized:
**
Support for large Z coordinate in entity grid.

-
**
Optimized:
**
Tweaked proxy helpers transparency settings.

-
**
Optimized:
**
Tweaked triangle hash grids for flat objects.

-
**
Fixed:
**
Ray hit dist is >0 during underflows in faraway rays.

-
**
Fixed:
**
Restored phys debugger compilability.

-
**
Fixed:
**
RemoveGeometry will remove all parts with the same ID.

-
**
Fixed:
**
Potential multithreading issue.

-
**
Fixed:
**
Restored phys debugger compilability after CryCommon changes.

-
**
Fixed:
**
Small issue with writing dumps.

-
**
Fixed:
**
Tweaked collision safety for fast objects.

-
**
Fixed:
**
Disabled ragdoll step rollback on deep collisions since it wasn't working well.

-
**
Fixed:
**
Fixed vehicle wheel sync issue.

-
**
Fixed:
**
Cloth scaling.

-
**
Fixed:
**
Some on-demand physics fixes.

-
**
Fixed:
**
Box-cylinder unprojection issue (false contact rejection).

-
**
Fixed:
**
Issue with obb-based brush grid registration plus potential MT lock with traceable parts.

-
**
Fixed:
**
Removed temp test bounciness disabling.

-
**
Fixed:
**
Issue with AABB tree rebuilding for 0-tri meshes.

-
**
Fixed:
**
Entities not deleted if no immediate deletion listeners registered.

-
**
Fixed:
**
Small issue with vehicle wheel position update.

-
**
Fixed:
**
Issue with certain types of custom intersection checks.

-
**
Fixed:
**
Some rare collision issues.

-
**
Fixed:
**
Preserve StatObj pointer when converting box to mesh for breaking.

-
**
Fixed:
**
Improved/capped ragdolls' rotation.

-
**
Fixed:
**
rwi_ignore_terrain_holes.

-
**
Fixed:
**
Issue with entity deletion purging.

-
**
Fixed:
**
Exporting a CGF with 16-bit positions will crash the Sandbox Editor and the Engine.

-
**
Fixed:
**
 Player not responding to gravity changes.

-
**
Tweaked:
**
Renaming variables to solve name collision with define "slots" in Qt.

##
PhysX

-
**
Optimized:
**
Scene tweaks (always CCD, enable stabilization). Improved support for pe_params_part, enabled scratch buf.

-
**
Fixed:
**
Support vehicles with more than 4 wheels.

##
Network

##
Network

-
**
New:
**
IEntityComponent-based entities have gained networking support:

-
All IGameObject/CGameObject dependencies have been removed.

-
RMIs are supported by explicitly Register/Invoke .

-
Game code can override IEntityComponent::NetSerialize for aspects serialization.

-
Introduced INetEntity/CNetEntity as a part of CEntity to encapsulate networking.

-
**
Refactored:
**
CGameObject-based entities were missing network profiles after INetEntity refactoring.

-
**
Refactored:
**
CGameObject serialization wasn't invoked properly due to a renamed method NetSerializeEntity.

-
**
Refactored:
**
Aspect hashing removal. It was disabled and superseded by partial updates.

-
**
Fixed:
**
Debug printing of memory statistics in net_meminfo 4.

-
**
Fixed:
**
DEBUG_KIT compilation.

-
**
Fixed:
**
PersistantDebug text flickering.

-
**
Fixed:
**
Physics proxy wasn't properly serialized for GameObjects (affected vehicles).

-
**
Fixed:
**
(DedicatedServer) Crash due to the memory corruption on dedicated server start.

-
**
Tweaked:
**
Dedicated server fixes.

##
Project System

##
Projects

-
**
New:
**
Automatically generate CMakeLists.txt and solutions for C# projects.

-
**
New:
**
 Added Package Build option to the cryproject files which exports projects to a redistributable state.

-
**
New:
**
Introduce new 'sys_project' CVar for specifying which .cryproject to load, allows for absolute and relative (to the Engine directory) paths. Default is 'game.cryproject'.

-
**
New:
**
Allow specifying Engine version '.' indicating that Engine is in the same directory as the .cryproject file.

-
**
Refactored:
**
 Removed the Build Solution option from the cryproject files.

-
**
Tweaked:
**
Handle case where value of "sys_project" is missing the ".cryproject" extension.

-
**
Tweaked:
**
 Always update window title with project name.

-
**
Tweaked:
**
 After switching the target engine for a project the solution is not automatically generated again.

##
Sandbox

##
Editor General

-
**
New:
**
Show node Quicksearch when dragging an edge onto nothing.

-
**
New:
**
Mark missing nodes in red in the Viewport.

-
**
New:
**
(TrackView) Record icon is now red.

-
**
New:
**
(TrackView) Mousewheel above the track tree will scroll while mousewheel above the dopesheet will zoom.

-
**
New:
**
Question dialogs cannot be cancelled unless they have a cancel button. If not the question must be answered.

-
**
New:
**
Replaced missing icon for scale snap.

-
**
New:
**
Gravity volumes can now be edited with a gizmo.

-
**
New:
**
Sample editor command registration.

-
**
New:
**
Re-use previous tool positions when opening tools.

-
**
New:
**
Moving assets.

-
**
New:
**
Cleaned up Viewport context menu when selecting an object. Added option to allow detaching of objects from group to the root or detaching them onto their parent group. This is also reflected on the main window menus.

-
**
New:
**
 Linking & attaching to group/prefab can now be done on the level explorer by dragging & dropping objects.

-
**
New:
**
Allow linking objects that reside in different layers.

-
**
New:
**
 (CharacterTool) Separate debug draw of Modifier & Attachment gizmos.

-
**
New:
**
Revive LOD Generator.

-
**
New:
**
Snapping for scale.

-
**
New:
**
Added option to hide/unhide Links to the Viewport Display Options menu.

-
**
New:
**
New item "duplicate layer" in Terrain Editor.

-
**
New:
**
Axis lock when moving curves while Shift is pressed.

-
**
New:
**
On GameToken FG nodes: right-click > search token usage plus right-click > open token in library.

-
**
New:
**
Canceling color picker with ESC button.

-
**
New:
**
Terrain layer properties displayed in rows.

-
**
New:
**
Added reference axes when using the Rotate Tool. Now drawing the pivot point of the object when performing a translation.

-
**
New:
**
"Update Navigation Area" option in context menu for selected NavigationAreaObject.

-
**
New:
**
Navmesh update mode in Sandbox Editor - update only after no new entity changes are received.

-
**
New:
**
Add extra mode of interaction for rotation gizmos - move along tangent of circle.

-
**
New:
**
Bring back option to display object frame of reference for selected objects.

-
**
New:
**
(AISystem) MNM update progress displayed in Sandbox Editor notification center.

-
**
New:
**
Level Explorer actions for Hide/Show All and Freeze/Unfreeze All and toggles.

-
**
New:
**
Numeric fields converts ',' to '.'.

-
**
New:
**
Double-click on "frozen" icon isolates object/layer as the only editable object in the layer.

-
**
New:
**
Double-click on "visible" icon isolates object/layer as the only visible object in the layer.

-
**
New:
**
Added Freeze/Hide All In Layer.

-
**
New:
**
Bring back archetype entity attributes serialization in Database view, but implementing it through IEntityArchetypeManagerExtension.

-
**
New:
**
 Added button for legacy pickers to all resource selectors (where it makes sense).

-
**
New:
**
 Texture import is now supported from common image formats.

-
**
New:
**
 (CryPak) Added support for %ENGINE% alias to address paths coming from engine.pak whereas no prefix will look in the project folder. For backwards compatibility, if a path is not found in the project folder, then the engine folder will be used as a fallback.

-
**
New:
**
 (Asset Browser) Context menu with actions, thumbnails and thumbnail view. Removed preview window. Engine assets now handled properly in a separate folder.

-
**
New:
**
 Level creation now integrated with Asset System.

-
**
New:
**
 Particle Editor now integrated with Asset System.

-
**
New:
**
 Added read-only folders and assets in the Asset Browser.

-
**
New:
**
 Added asset dependency tracking and dependency graph viewer.

-
**
New:
**
 Added re-import of assets.

-
**
New:
**
 Generate material, model thumbnails.

-
**
New:
**
 Validate RC version in Sandbox Editor.

-
**
Refactored:
**
Set Paste with Links through Ctrl+V and Paste without through Ctrl+Shift+V.

-
**
Refactored:
**
Cleanup - remove unused special drag mode for edges.

-
**
Refactored:
**
Fix regression - Graph disabled, status not visible.

-
**
Refactored:
**
Cleanup the Flowgraph tree list.

-
**
Refactored:
**
Rename files and organize them in folders. Split the Component and Tree list to its own files.

-
**
Refactored:
**
Restructuring AI menu and commands in Editor, added the possibility to assign keyboard shortcuts.

-
**
Refactored:
**
Selection update notifications are now sent in all selection altering code paths.

-
**
Refactored:
**
Separate Flowgraph load of Global and Level FG Modules.

-
**
Refactored:
**
Fix Editor slowdowns related to Flowgraph Modules and Flowgraph reloading.

-
**
Refactored:
**
Removed Fetch/Hold code, functionality was no longer used or desired.

-
**
Refactored:
**
Re-implemented terrain resize operation without level Hold/Fetch.

-
**
Refactored:
**
Initialize EditorCommon's global IEditor pointer at the beginning of CEdtiorImpl constructor instead of at the end. This is to allow EditorCommon sytems to access GetIEditor on initialization.

-
**
Refactored:
**
Enable undo on QPropertyTree in MBT Editor, DescriptorDB and Archetype DatabaseView.

-
**
Refactored:
**
(SVOGI) Added "Global illumination" flag into designer object properties.

-
**
Refactored:
**
Removed the need for registering resource pickers on Editor plugins side - using a macro is now sufficient.

-
**
Refactored:
**
Change rotation gizmo UI - remove dotted line, add arrows to denote interaction direction.

-
**
Refactored:
**
Cleanup unused functions from Viewport, Aspect ratio and window rectangle.

-
**
Refactored:
**
If property widgets are left without observable items, delete them and unlock the parent inspector.

-
**
Refactored:
**
 (Sandbox plugin system) Added SmartObjects editor plugin, sample editor plugin and MFCTools plugin. Added placeholder dialog editor and vehicle editor plugins.

-
**
Refactored:
**
 Moved Yasli code into CRYENGINE code solution.

-
**
Refactored:
**
 Draw thick lines with geometry shader.

-
**
Refactored:
**
 Remove obsolete cryasset tag.

-
**
Refactored:
**
 Move asset types from MeshImporter to Sandbox Editor.

-
**
Optimized:
**
Cleanup FG Tree Reload on Object Change - improves level loading and object editing.

-
**
Optimized:
**
Fix slowdown in ReloadEntityScripts.

-
**
Optimized:
**
Fix slowdown when creating a new module on production levels.

-
**
Optimized:
**
Review FG UI reloading.

-
**
Optimized:
**
ClipVolumeObject is updated, only when it was changed before exporting it's data.

-
**
Optimized:
**
 Replaced all MFC numeric dialog boxes.

-
**
Optimized:
**
AI Cleanup - Removing old navigation system and clearing AI code in Editor.

-
**
Optimized:
**
 DisplayContext only pushes matrices to AuxGeometry when matrices actually change, and not before each draw call.

-
**
Optimized:
**
 Remove CPU side transforms from DisplayContext pipeline and use GPU side transforms instead.

-
**
Fixed:
**
Now using exponential moving average to calculate if we need to stop processing Engine updates if the UI is being hovered/used. This is necessary to keep UI snappy when the Engine is running at low frame rates.

-
**
Fixed:
**
Group properties showing up again in properties panel. Removed group operators from base object, since these actions could be accomplished by many other means and without polluting the already overcrowded properties.

-
**
Fixed:
**
Issues with quick search node.

-
**
Fixed:
**
Restore column order when setting state of Level Explorer.

-
**
Fixed:
**
If an object is attached and position doesn't need to be recalculated make sure to recalculate it's new world matrix after the parent is assigned.

-
**
Fixed:
**
(Terrain Editor) Objects float when using Raise/Lower and Smooth operation in combination with Undo.

-
**
Fixed:
**
Cases where invalid Qt icons were used -  added assertion to avoid regression in the future.

-
**
Fixed:
**
Currently selected graph not visible in the tree when selected from the search.

-
**
Fixed:
**
Multiple issues with the graph tree such as wrong names when entities are added or renamed, graphs in the wrong place on prefab creation, constant folding and flickering and performance issues.

-
**
Fixed
**
: Relative paths to textures in materials weren't reflected while syncing to 3ds Max.

-
**
Fixed
**
: Missing throw for std::runtime_exception is some python functions.

-
**
Fixed:
**
Renamed "Freeze" button to "Apply" in Designer->Subdivision so that it's more intuitive.

-
**
Fixed:
**
Masked selection works for brushes when they are in a group.

-
**
Fixed:
**
Gizmo should now appear in the correct position when modifying designer vertices.

-
**
Fixed:
**
Mannequin preview works even without a level loaded.

-
**
Fixed:
**
Search results turn white when sorted.

-
**
Fixed:
**
Now it's possible to paint vegetation only on brushes.

-
**
Fixed:
**
Always show "Archetype Entity" category.

-
**
Fixed:
**
Loading of Archetype Editor object.

-
**
Fixed:
**
Duplicating an object should now have it move in the correct coordinate system.

-
**
Fixed:
**
Crash when dragging through check boxes in the property tree where it was recreating the property tree and invalidating a row that was later caching.

-
**
Fixed:
**
Ensure Ctrl-Tab is handled by tool tab widgets.

-
**
Fixed:
**
Pressed shift and ctrl doesn't block panning of the camera.

-
**
Fixed:
**
Changed wording in notification when there's an action to execute.

-
**
Fixed:
**
Now roof audio occlusion should show as intended.

-
**
Fixed:
**
Imported *.obj-file doesn't show up in MI.

-
**
Fixed:
**
Hidden solids do not show up when helpers turned off.

-
**
Fixed:
**
Slider in Designer Tool subdivision moves only 1 step when clicked.

-
**
Fixed:
**
Rotation gizmo disc makes at most one lap when rotating.

-
**
Fixed:
**
Issue of undo for uniform scale not being pushed to undo history.

-
**
Fixed:
**
Removed "cancel" option in dialogs where "no" and "cancel" had the same effect.

-
**
Fixed:
**
Better handling of closing question dialogs - closing will now cancel instead of giving "no" answer.

-
**
Fixed:
**
Now it's possible to rotate multiple objects using track ball and view-aligned gizmo in objects' local space.

-
**
Fixed:
**
Highlighting for rotation gizmos when looking at them from the side.

-
**
Fixed:
**
Occasional problem when keys do not get added on straight curves.

-
**
Fixed:
**
Selecting an item in a Database View will now always work if the item exists in this view.

-
**
Fixed:
**
Layer rename now removes the old layer from disk on save.

-
**
Fixed:
**
Changed UI description for Cube Editor, mousewheel actually changes the tool's mode and not the brush size.

-
**
Fixed:
**
Crash renaming a lense flare effect.

-
**
Fixed:
**
Added context menu on Level Explorer when selecting a folder to allow importing a layer within the folder.

-
**
Fixed:
**
Level closing optimizations - in particular do not invalidate matrices when closing, as this triggers a lot of unnecessary work.

-
**
Fixed:
**
Crash when changing the type of view in the level explorer, and find objects when there were filters that weren't shared between the different views.

-
**
Fixed:
**
Deleting layer doesn't change active layer.

-
**
Fixed:
**
Mouse Wheel rotation of duplicated object.

-
**
Fixed:
**
When duplicating a pair of objects that have an entity link, if the entity link name corresponds to the previous targets name, then the name will be adjusted to match the new target.

-
**
Fixed:
**
Auto-update all instances checkbox in the properties panel where it was simply not toggleable at all.

-
**
Fixed:
**
Creating a layer in the Level Explorer will no longer throw a warning saying that a layer with the same name already existed.

-
**
Fixed:
**
Prefab children picking functionality in the Properties Panel is no longer triggered when single clicking the field. Also added functionality that allows selecting the object on double click.

-
**
Fixed:
**
Entity links pointer was dangling while removing all entity links.

-
**
Fixed:
**
Crash when Curve Editor is active in the Particle Editor and owner is changed (Self, Parent).

-
**
Fixed:
**
Assert on saving level and changing camera-angle.

-
**
Fixed:
**
Memory leak in ReloadEntityScripts.

-
**
Fixed:
**
Entity node changes via LUA scripts not applied on ReloadScript of the entity or of all entities.

-
**
Fixed:
**
Graph loosing changes if not open when adding/removing other graphs.

-
**
Fixed:
**
Graph marked as unchanged if open when adding/removing other graphs.

-
**
Fixed:
**
Activating debug on a graph marks it as unchanged.

-
**
Fixed:
**
Save dialog for new FG modules.

-
**
Fixed:
**
Clicking on a graph marks it as unchanged.

-
**
Fixed:
**
Mouse should still not trigger when the left mouse button is released.

-
**
Fixed:
**
Tooltip not showing up in Level Explorer. Tooltip now using correct background color and margins.

-
**
Fixed:
**
Floats rounded to 2 decimal places when set in the 'Console Variables' window.

-
**
Fixed:
**
Cannot set the value of string CVars in the 'Console Variables' window.

-
**
Fixed:
**
 Level Explorer will populate its content properly when loading a level in "show active layer" mode.

-
**
Fixed:
**
Sorting in the Level Explorer.

-
**
Fixed:
**
Background color UI in LOD generator.

-
**
Fixed:
**
Made it possible to rename entity links from the Properties Panel.

-
**
Fixed:
**
Designer Tool no longer uses custom styling.

-
**
Fixed:
**
 Disabled double click to expand groups/prefabs/layers in the Level Explorer. Double clicking in this specific tree view should set a layer as active or select and go to an object.

-
**
Fixed:
**
Removed deprecated vegetation imposters display option.

-
**
Fixed:
**
Layer Picker can now only select object layers.

-
**
Fixed:
**
Go To dialog goes to world origin when pressing OK.

-
**
Fixed:
**
Changing AI preferences from main menu will now trigger preferences to be saved out. This fix should apply to any other preference that also has a menu option.

-
**
Fixed:
**
Rotating axis when aligned with view.

-
**
Fixed:
**
Make Qt read-only properties not display in red.

-
**
Fixed:
**
Suppress warning on missing tokens for MaterialFX graphs before the level and token libraries are loaded.

-
**
Fixed:
**
Changes not detected in module graphs when editing graph tokens.

-
**
Fixed:
**
Preserve visible Level Explorer columns when loading new level.

-
**
Fixed:
**
Remove irrelevant warning with Prefabs event source node in FG.

-
**
Fixed:
**
Crash when deleting multiple FG nodes.

-
**
Fixed:
**
Malfunctioning FG simple comment editing.

-
**
Fixed:
**
A material which has MTL_FLAG_NOPREVIEW is rendered to material preview window.

-
**
Fixed:
**
Area solid export which sometimes produces corrupted files.

-
**
Fixed:
**
The Flowgraph window should never open more than once.

-
**
Fixed:
**
Crashes on GoTo Game Token definition.

-
**
Fixed:
**
Texture preview of selected layer in Terrain Editor.

-
**
Fixed:
**
A less intrusive approach to fix missing enum strings on UI side.

-
**
Fixed:
**
Made it so the Editor action is checked for physics single step mode when enabled.

-
**
Fixed:
**
Slowdown and potential crash on saving archetypes. Archetypes can now be refreshed manually instead of on save.

-
**
Fixed:
**
Object is highlighted in the vegetation list when clicked in move mode.

-
**
Fixed:
**
EnvironmentProbe is missing some properties.

-
**
Fixed:
**
 Issue when trying to edit a shape while the Rotation Tool was selected resulting in a crash.

-
**
Fixed:
**
Changed freeze/hide all except specific layer to behave exactly the same. Removed functionality for caching layer visibility when performing operation.

-
**
Fixed:
**
Issue with designer objects when trying to modify them in parent space, where it should be assumed that the parent is the actual object that is being modified rather than it's actual parent.

-
**
Fixed:
**
Export of AreaSolids.

-
**
Fixed:
**
Wrong tooltip on filter button.

-
**
Fixed:
**
Alignment of the snapping and ports with the grid. Copy/paste and add nodes also follows the grid.

-
**
Fixed:
**
 An imported PFX1 is displayed with its whole path.

-
**
Fixed:
**
Changed Clone Tool grid snapping to behave the same as when not dealing with cloning at all. Also added missing handling of normal snapping when using the axis constraint gizmos.

-
**
Fixed:
**
Debug toggle for modules.

-
**
Fixed:
**
No longer able to add commands to a toolbar if they're already a part of that toolbar.

-
**
Fixed:
**
Disabled showing LODs in create objects panel.

-
**
Fixed:
**
Attaching to prefab from group controls in properties panel.

-
**
Fixed:
**
Issue where resetting the material on an object within a prefab was not resetting it for all instances.

-
**
Fixed:
**
Suspend game input if leaving fullscreen mode and game is running.

-
**
Fixed:
**
Deleting a child from a prefab from the properties panel would clear the prefab (at least just visually in the Viewport).

-
**
Fixed:
**
Undoing changes to entity properties which was not possible.

-
**
Fixed:
**
Crash when quickly and repeatedly toggling fullscreen.

-
**
Fixed:
**
Crash when exporting CVars.

-
**
Fixed:
**
Correctly restore tree view columns from layout.

-
**
Fixed:
**
Mouse events in Viewport working incorrectly on HiDPI screen.

-
**
Fixed:
**
Check all key sequences when forwarding shortcuts to main window, not just first one.

-
**
Fixed:
**
(NavigationSystem) Navmesh is not updated when terrain geometry isn't edited.

-
**
Fixed:
**
'ReloadGeometry' erases the properties of all geom entities in the scene.

-
**
Fixed:
**
Issue that was causing objects to have duplicate names when loading an existing map.

-
**
Fixed:
**
Issue where changes to vis areas height were not being reflected on the Viewport/game.

-
**
Fixed:
**
Favorite filter button in CVar list.

-
**
Fixed:
**
Issue with sorting favorites in CVar list.

-
**
Fixed:
**
 Making a child layer visible should make the parent layer visible as well (but not all it's parent's children).

-
**
Fixed:
**
Previous state will not be remembered by layers when toggling all other layers to be hidden.

-
**
Fixed:
**
Unhiding objects will now only modify objects within layers that are not hidden.

-
**
Fixed:
**
Crash when trying to pick for a prefab and properties window has been closed.

-
**
Fixed:
**
PropertyRowResourceFilePath freezing QPropertyTree inside MFC windows.

-
**
Fixed:
**
CAutoLogTime marker for entity archetypes database loading.

-
**
Fixed:
**
Prefab's children transform invalidation during attachment to improve level loading times.

-
**
Fixed:
**
For numbers in object names being ignored when creating a new object.

-
**
Fixed:
**
When a group is open use information from child objects for highlighting.

-
**
Fixed:
**
Icons drawn on top of gizmos.

-
**
Fixed:
**
Assert when exporting to Engine.

-
**
Fixed:
**
Spline objects having way too high offset from ground during creation.

-
**
Fixed:
**
Issue where selecting a CVar in the CVar dialog would return the wrong CVar. Also fixed an issue with double click not working.

-
**
Fixed:
**
For assert that had to do with accepting notifications and dealing with combined notifications.

-
**
Fixed:
**
QMenuComboBox that was asserting when an item was removed. This was due to the fact that it was changing the selected index and trying to toggle the deleted items state.

-
**
Fixed:
**
Inspector locked feature not working anymore.

-
**
Fixed:
**
Translation Gizmo not grid-snapping in regard to the grid manner.

-
**
Fixed:
**
 Generating a cubemap a second time triggers warning in NC (CAssetManager).

-
**
Fixed:
**
Several issues with renaming materials in the Material Editor.

-
**
Fixed:
**
 Issue where grouping geom entities and creating prefabs had empty bounding boxes.

-
**
Fixed:
**
 (Terrain Editor) Objects float when using Flatten-tool.

-
**
Fixed:
**
Very blurry textures in CGF preview.

-
**
Fixed:
**
Removed redundant update of DesignerObject after exporting it's data.

-
**
Fixed:
**
Removed warning in texture-previewer for pow2, as it is irrelevant for the preview (and not possible for cubemaps).

-
**
Fixed:
**
Trigger texture loading at a slightly more robust moment.

-
**
Fixed:
**
Double registration of materials (which triggered warnings).

-
**
Fixed:
**
Material preview rect invalidation.

-
**
Fixed:
**
Added texture-streaming hook allowing material previews to force streaming and resource update events.

-
**
Fixed:
**
Duplicated Level Settings update calls during level load.

-
**
Fixed:
**
Debugview buttons not toggled properly when CVars change.

-
**
Fixed:
**
 (Character Tool) Adjusting dimensions in Blendspace does not allow you to change the dimensions values.

-
**
Fixed:
**
 Character Tool will now auto expand folders when the search is used. Also the filter is now applied as the user types.

-
**
Fixed:
**
 Selecting the first animation does nothing, selecting the second plays automatically.

-
**
Fixed:
**
 Crash when immediately switching from Area:Solid to Area:ClipVolume or double clicking on any of these.

-
**
Fixed:
**
 Selection mask doesn't work for AI Navigation Seed Point.

-
**
Fixed:
**
 (FBX Importer) Compute normals option added.

-
**
Fixed:
**
 No selected material in the Material Editor after clicking on edit material in properties panel.

-
**
Fixed:
**
 Rectangular selection works properly for all objects.

-
**
Fixed:
**
 (FBX) Imported *.fbx with locomotion animation is missing root translocation.

-
**
Fixed:
**
 Designer Tool crashing when selection changes while in the UV Mapping Tool.

-
**
Fixed:
**
 Warning "Vegetation object is not suitable for merging".

-
**
Fixed:
**
 (Qt Track) Properties Panel only shows X-values of keys.

-
**
Fixed:
**
 (FBX Importer) "Generate texture coordinates" option added.

-
**
Fixed:
**
 (FBX Importer) Physical proxies have wrong transformation.

-
**
Fixed:
**
 (Mesh Importer) Mesh node can now be used as a bone.

-
**
Fixed:
**
 (Mesh Importer) Added UI option "Use 32 bit precision".

-
**
Fixed:
**
 Layers can now be changed using double click in the layer picker dialog.

-
**
Fixed:
**
 Area Solids and Clip volumes can be created again.

-
**
Fixed:
**
 Crash/stack overflow in UV Mapping Editor when using SmartSew.

-
**
Fixed:
**
 LODs will not show up in file dialogs (to select models).

-
**
Fixed:
**
 Cloning objects will now start their position at mouse cursor.

-
**
Fixed:
**
 Starting the game without an active Viewport.

-
**
Fixed:
**
 When opening in Explorer - A file path that doesn't exist will open its parent folder.

-
**
Fixed:
**
 File dialogs no longer clear input field when selecting directories.

-
**
Fixed:
**
 File-monitor trying to read busy files when re-exporting from 3ds max.

-
**
Fixed:
**
 (ParticleEditor) Fixed an issue that allowed to create disallowed connection which resulted in a crash.

**
Fixed:
**
 (ParticleEditor) Fixed a crash when deleting a connected node.

-
**
Tweaked:
**
Hide TestABF and TestABFNew panels from the LOD generator UI.

-
**
Tweaked:
**
Add profile markers for level close.

-
**
Tweaked:
**
(Trackview) Reordered toolbar buttons - playback is now more standard and add entity to Trackview is now first in its group.

-
**
Tweaked:
**
New default Editor Layout with Content Browser.

-
**
Tweaked:
**
Additional profile markers for loading times.

-
**
Tweaked:
**
Add profile markers.

-
**
Tweaked:
**
Selection on graphs is no longer persisted and is not included in Undo/Redo.

-
**
Tweaked:
**
Added CVar sys_debugger_adjustments. When debugger present emitters created in Editor are inactive at start.

-
**
Tweaked:
**
Corrected Icon for the entity containers.

-
**
Tweaked:
**
 Display tweaks.

-
**
Tweaked:
**
 Changing open pane default commands, to either open or focus if there's already one open.

-
**
Tweaked:
**
 Added commands for Vegetation Tool paint|erase|select.

-
**
Tweaked:
**
 Moved CEntity members around to avoid alignment bytes (reduces size from 432 to 416 bytes).

-
**
Tweaked:
**
 Create tool no longer uses personalization.

##
Trackview

-
**
New:
**
Magnetic snapping between keys or ruler marker.

-
**
New:
**
TrackView Ruler markings snapping.

-
**
New:
**
Adding frame snapping in TrackView.

-
**
Fixed:
**
'RenderSequence'-FPS-drop down looks bad.

-
**
Fixed:
**
Change zoom/scroll keyboard and mouse bindings.

-
**
Fixed:
**
"Sequence Properties" command would have been a better fit on View tab instead of File tab.

##
Tools

##
Tools General

-
**
New:
**
Added new programs - KeyImport and KeyExtract that create a
*
key.dat
*
 from public and private keys (and vice versa), but do not build them by default.

-
**
New:
**
CryMaxExport, MayaCryExport and MotionBuilderCryExport compiling with CMake.

-
**
New:
**
CryTIFPlugin compiling with CMake.

-
**
New:
**
 (MayaCryExport) Exporter for Maya 2017.

-
**
Fixed:
**
Texturestreaming initialization when no device is present.

-
**
Fixed:
**
(Export) Cryasset file can break 3dsMax export.

-
**
Fixed:
**
Added include paths to CMakeLists.txt for stdafx and CryTIFPlugin.pipl.

-
**
Fixed:
**
 Inability to start dedicated server from project system.

-
**
Fixed:
**
 MeshBaker shader compilation.

-
**
Tweaked:
**
 Allow multiple runs of Statoscope during one game session.

##
Resource Compiler

-
**
Fixed:
**
Splitting of 32x32 DDNA textures is wrong.
