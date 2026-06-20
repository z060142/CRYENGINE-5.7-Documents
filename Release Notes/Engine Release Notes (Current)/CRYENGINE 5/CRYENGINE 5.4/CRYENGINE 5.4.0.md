# CRYENGINE 5.4.0

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/47316993/pages/44962676
- Page ID: 44962676
- Breadcrumb: Engine Release Notes (Current) > CRYENGINE 5 > CRYENGINE 5.4 > CRYENGINE 5.4.0
- Parent: CRYENGINE 5.4

## Child Pages

- [Important CRYENGINE 5.4 Data and Code Changes](CRYENGINE%205.4.0/Important%20CRYENGINE%205.4%20Data%20and%20Code%20Changes.md)
- [Migrating from CRYENGINE 5.3 to CRYENGINE 5.4](CRYENGINE%205.4.0/Migrating%20from%20CRYENGINE%205.3%20to%20CRYENGINE%205.4.md)
- [Third Party SDKs in 5.4.0](CRYENGINE%205.4.0/Third%20Party%20SDKs%20in%205.4.0.md)

## Content

![Image](https://www.cryengine.com/docs/static/attachments/44962689)

[![Image](https://www.cryengine.com/docs/static/attachments/44962678)](https://www.cryengine.com/support)

## 5.4 Overview

Welcome to our latest major update, CRYENGINE 5.4. We know it has been a long time in the making, but we are sure you'll agree with us - it has been worth the wait.

We have made over 960 improvements & fixes and have introduced lots of new features in CRYENGINE 5.4, these include; Substance Integration for the reading of material archives and the manipulation of texture inputs with in-editor graphing. We have also expanded the feature set of the Terrain System, which allows for much better blending of terrain and objects within your level. We have added all new Vulkan API support and an Entity Components feature (including some Use Case documentation). Also new in CRYENGINE 5.4 is Extended Detail Bending, 2 brand new C# Templates and updates to the previously introduced Asset System which now provides improvements and extended usage across tools, with thumbnail generation and all new dependency tracking.

Carrying on we have also introduced a Pull Request facility through GitHub which allows our fantastic CRYENGINE Community to collaborate with us on improving CRYENGINE. Finally, we have also introduced a Substance Viewport Shader, a Photoshop Ultimate Texture Saver, over 30 new Particle Presets, several new Anti-Aliasing techniques, Object Linking through the Level Explorer and last but not least some updated documentation for the Project Launcher Tools. So we are sure that you cannot wait to get started - so go and get CRYENGINE 5.4 on Github**[HERE!](https://github.com/CRYTEK/CRYENGINE)**

## Contributors

We would like to say a massive thank you to the following for their valuable contribution in the making of this 5.4 release of CRYENGINE.

- Shivam Mistry
- sorbetsandwich
- gdeban
- uniflare
- Chylix
- ochounos

## Sections

[5.4 Overview](#54-overview)[Contributors](#contributors)[Sections](#sections)[Code Interface Changes](#code-interface-changes)[Release Highlights](#release-highlights)[Animation](#animation)[AI](#ai)[Audio](#audio)[Core/System](#coresystem)[Graphics and Rendering](#graphics-and-rendering)[Physics](#physics)[Project System](#project-system)[Sandbox](#sandbox)[Tools](#tools)

## Code Interface Changes

For more information, see the [Important CRYENGINE 5.4 Data and Code Changes](CRYENGINE%205.4.0/Important%20CRYENGINE%205.4%20Data%20and%20Code%20Changes.md)article.

If you are upgrading from CRYENGINE 5.3, please read this topic: [Migrating from CRYENGINE 5.3 to CRYENGINE 5.4](CRYENGINE%205.4.0/Migrating%20from%20CRYENGINE%205.3%20to%20CRYENGINE%205.4.md)[.](/docs)

## Release Highlights

#### Substance Integration

Both internally and externally we have seen the industry embrace the concept of harnessing procedural texture creation to extend the usage of individual assets. For some time now, our internal teams have actively used Substance in their workflow so it is a logical addition to be supported within our Sandbox Editor.

With this integration we are using Substance Archive files (*.sbsar) to create Substance Graph instances and generate textures out of them. The important thing to keep in mind is that CRYENGINE implementation doesn't directly output graph outputs from a substance graph, but rather pre-configured texture outputs that are using substance graph outputs as inputs. It is also important to keep in mind that the archive still needs to be built inside of the Substance Designer where the properties are then exposed to the Sandbox Editor through the archive for the modular end result.

**[Allegorithmic Substance Documentation](../../../../Manual/Editor%20Tools/Substance.md)**

#### Terrain System Upgrades

CRYENGINE 5.4 adds several new terrain features. Objects can now be blended seamlessly into the terrain. This dramatically extends the possibilities of current terrain editing tools, allowing for a much higher level of realism, overhanging rock faces and a much greater level of flexibility.

The selected object meshes get copied at an early stage into the heightmap mesh to become a seamless part of the terrain. While integrated objects support most of the height map properties and even 3D terrain materials.

On top of that, we introduce Soft Depth Test for terrain materials which allows for soft blending between terrain and objects on terrain.

Additionally, we have enabled in-shader auto high-pass in release 5.4 - this eliminates an additional and cumbersome step to users, which only pertained to terrain materials. Now the same diffuse texture file may be used for terrain material and other shaders.

You can even extend this further by using the new "Use Original Diffuse Map" material flag which allows you to completely match the look of terrain materials and object materials.

**[Terrain Editor](../../../../Manual/Editor%20Tools/Terrain%20Editor.md)**

**[Terrain Object Blending](../../../../Manual/Editor%20Tools/Terrain%20Editor/Terrain%20Object%20Blending.md)**

#### Vulkan API Support

Release 5.4 includes a beta version of the Vulkan renderer to accompany our DX12 implementation from last year. Vulkan is a cross-platform 3D graphics and compute API that enables developers to have high-performance real-time 3D graphics applications with balanced CPU/GPU usage.

For the 5.4 release, Vulkan support in CRYENGINE will be compatible for projects on PC only, but we are aiming for additional Android support in the future.

To enable the Vulkan renderer you need either add *"r_driver=vk"* into your system.cfg or add “name”: “r_driver”, “value”: “vk” to the “console_variables” part of the.cryproject file. Do keep in mind that you must also run the remote shader compiler locally as the renderer is dependent on this step.

![Image](https://www.cryengine.com/docs/static/attachments/44962677)

**[Vulkan Support in CRYENGINE Documentation](../../../../Manual/Beta%20Features/Vulkan%20Support%20in%20CRYENGINE.md)**

#### Entity Components

A longstanding issue within CRYENGINE has been the reliance on game code to expose and manage entities within your level. CRYENGINE's Entity Component System provides a modular and intuitive way to construct games. The technology works at both the system level and at the entity level.

The interaction model (within the Sandbox Editor) allows Developers the ability to create empty (blank) entity containers which in turn house the advanced game logic wrapped into specific components. Some examples of base components are: Mesh, Lights, Constraints and even Character Controllers. With these types of components users can develop prefabs that can be placed by Level Designers throughout a game for both standardization and exposure to Schematyc for triggering and event updating.

To help the community get to grips with the newly introduced Entity Components feature our Developers have written some Entity Component Use Case documentation. CRYENGINE users may be particularly interested in the two Combining Components Use Cases 1 RigidBody and Particles & 2 Collectibles and PowerUps that show how different Components can be combined to create some great effects. The documentation will be expanded on over the coming months, so keep your eyes peeled for further updates.

![Image](https://www.cryengine.com/docs/static/attachments/44962695)

**[Entity Component Use Case Documentation](../../../../Manual/Tutorials/Game%20and%20Level%20Design/Entity%20Component%20Tutorials.md)**

**[1: RigidBody and Particles Documentation](../../../../Manual/Tutorials/Game%20and%20Level%20Design/Entity%20Component%20Tutorials/Tutorial%20-%20Combining%20Components%201%20-%20RigidBody%20and%20Particles.md)**

**[2: Collectibles and PowerUps Documentation](../../../../Manual/Tutorials/Game%20and%20Level%20Design/Entity%20Component%20Tutorials/Tutorial%20-%20Combining%20Components%202%20-%20Collectibles%20and%20PowerUps.md)**

#### Extended Detail Bending (Robinson Tech)

Upgraded in release 5.4 is the new "Extended Detail Bending" toggle - found in the vegetation shader. The history behind this feature comes from Crytek's *Robinson: The Journey* development and how we needed a more accurate and physically dependent bending solution for our vegetation.

This feature provides Artists with much more control over detail bending of their tree branches. For example, this new bending feature allows not only small micro movement of leaves, but also whole branches of trees or chunks of grass. So for example Artists can now have one large clump of grass with phased animations, this allows movement to look much more natural. Aiding in the variations we also apply a world-space mapped noise texture to simulate random breeze for even greater variation in movement.

![Image](https://www.cryengine.com/docs/static/attachments/44962694)

**[Vegetation Shader Documentation](../../../../Manual/Graphics%20%26%20Rendering/Shaders/Shaders%20in%20CRYENGINE/Shader%20Reference/Vegetation%20Shader.md)**

#### C# Templates

We have added the following templates in C#:

- C# Plugin
- C# 3rd person

Carrying on with our Launcher improvements, we have also expanded our selection of templates to make getting up and running with CRYENGINE even easier. Several things have been brought over from our C++ arsenal and that includes the Plugin and 3rd Person templates in a C# flavor.

We expect to add more templates to CRYENGINE in future releases, this will not only demo the beginning part of making a game, but also show finalized examples that guide you through each phase of game development.

![Image](https://www.cryengine.com/docs/static/attachments/44962693)

**[C# Game Templates Documentation](../../../../API%20Reference/CRYENGINE%20Code%20Tutorials/C%23%20Programming/C%23%20Game%20Templates.md)**

#### Asset System Updates

In release 5.3 we shipped a base implementation of the new Asset System, this allowed users to directly interact with their assets and directories. We know that the most optimal solution is to never touch Windows Explorer in order to achieve the changes you want and the new Asset System updates certainly bring us one step closer to this reality. Through on-going development, we have now added direct drag-and-drop support for the Asset Browser along with other tools integration (Material Editor, Particle Editor).

In release 5.4 we have also introduced an all-new Dependency Graph to aid in the assistance of changing the paths or managing dependencies.

We have also exposed dynamic CGF switching functionality, this has the added benefit of not only having a direct thumbnail view (to preview an asset), but also the ability to select the asset that best suits your needs. This development also allows you to step down the list of assets and thus helps in finding best asset for your given scenario.

![Image](https://www.cryengine.com/docs/static/attachments/44962692)

**[Asset System Documentation](../../../../Manual/Editor%20Tools/Asset%20Browser.md)**

#### CRYENGINE Pull Requests

At the end of July, we introduced CRYENGINE Pull Requests to the CRYENGINE community (we felt it was worth another mention in these release highlights). This facility is available via GitHub, for general information provided by GitHub regarding Pull Requests, please refer here Pull Requests.

We have also written some CRYENGINE documentation to assist the CRYENGINE community in submitting pull requests.

We also want to take this opportunity to say a massive thank you to all of our CRYENGINE Community members for their contributions in helping us to develop the Engine. Please keep your feedback coming, (but through the normal channels).

![Image](https://www.cryengine.com/docs/static/attachments/44962687)

**[CRYENGINE Pull Requests](https://www.cryengine.com/news/cryengine-github-pull-requests-are-go-here-s-what-you-need-to-know)**

**[GitHub Pull Request Documentation](https://help.github.com/articles/creating-a-pull-request/)**

**[CRYENGINE Pull Request Submission Documentation](/docs)**

#### Substance Viewport Shader

Also in release 5.4 we bring you a custom Substance Shader that has been designed to match the viewport shading of Allegorithmic's Substance Designer and Painter software. To download the tool and for more general information follow the link underneath the image on the right.

![Image](https://www.cryengine.com/docs/static/attachments/44962686)

**[Substance - CRYENGINE Shader Documentation](../../../../Manual/Editor%20Tools/Substance/Substance%20-%20CRYENGINE%20Shader.md)**

#### Photoshop Ultimate Texture Saver

Also in release 5.4 we bring you an extension to Photoshop - the Ultimate Texture Saver. This feature has been developed to make life much easier for Texture Artists and replaces 8 separate files with just 1. To download the tool and for more general information follow the link on the right. We hope you can enjoy the luxury of handling seamlessly all your texture maps under one Photoshop file.

**![Image](https://www.cryengine.com/docs/static/attachments/44962688)**

**[Photoshop - Ultimate Texture Saver Documentation](../../../../Manual/Asset%20Prep%20(External)/Asset%20Exporting%20Overview/Texture%20Creation%20Overview/Ultimate%20Texture%20Saver.md)**

#### Particle Presets

Also in release 5.4 we bring you the Particle Editor Presets Library. This new feature comprises a comprehensive list of predefined particle effects such as explosions, fire, embers and smoke that can be added to your level from the off. These effects then act as the base for the creation of much more elaborate particle effects.

For more detailed information on the Particle Editor Presets Library follow the link on the right.

**![Image](https://www.cryengine.com/docs/static/attachments/44962685)**

**[Particle Presets Library Documentation](../../../../Manual/Editor%20Tools/Particle%20Editor/Particle%20Presets%20Library.md)**

#### Anti-Aliasing

Also in this 5.4 release, we are introducing some new Anti-Aliasing techniques that will even further improve our graphics quality. While there is a range of different anti-aliasing methods available, finding an efficient implementation and one that provides great quality remains one of the biggest challenges in rendering. This is even more true for VR applications, where jagged edges and crawling pixels can cause severe viewer discomfort and where the rendering techniques employed have to operate within a very tight performance budget. Currently, we support the following methods:

- **SMAA and Temporal Antialiasing**
- **Temporal Supersampling (TSAA)**
- **Supersampling**

For more information on Anti-Aliasing follow the link on the right.

**![Image](https://www.cryengine.com/docs/static/attachments/44962682)**

**[Anti-Aliasing Documentation](../../../../Manual/Post-processing/Anti-Aliasing.md)**

#### Object Linking (through the Level Explorer)

Also added you can now add objects to a group and link them through the Level Explorer, for more information watch the GIF or follow the link on the right.

**![Image](https://www.cryengine.com/docs/static/attachments/44962684)**

**[Object Linking in the Level Explorer](../../../../Manual/Editor%20Tools/Level%20Editor%20Tab/Level%20Explorer/Object%20Linking.md)**

#### Project Launcher Tools Updated Documentation

Finally, in release 5.4 we bring you some updated documentation for the Project Launcher Tools. We have focused in particular on the Package Build command that now allows you to redistribute your files quicker without having to wonder what to add and remove in your final build. For more information follow the link on the right.

**![Image](https://www.cryengine.com/docs/static/attachments/44962683)**

**[Project Launcher Tools Documentation](/docs)**

## Animation

#### Animation General

- **Fixed:** (Renderer) Crash when 8-weight compute skinning is selected.
- **Fixed:** Provide an option to enable mutually exclusive Viewport updates (CT, MANN, LevelEditor) - available via Preferences -> Viewport. Hence, performance of tools (e.g. CT, MANN) is improved while a large level is loaded.
- **Fixed:** (CharacterTool) Scrubbing time - use all active animation layers for preview (similar to 'normal' play mode).
- **Fixed:** (Character Tool) Improved serialization of blendspace pseudo-examples and annotations in the Character Tool GUI.
- **Fixed:** A bug in the directory structure lookup cache, preventing animation files from being correctly discovered when ca_useIMG_CAF mode is enabled.

#### Character Tool

- **Fixed:** A signal/slot race condition crash caused by in PropertiesPanel::m_propertyTree sometimes trying to revert to an expired object when loading/reloading character files. Property tree is now safely refreshed in a subsequent OnExplorerSelectionChanged handler.
- **Fixed:** A bug which caused the "Additional Extraction" section to get glitched when modifying dependent blendspace properties. List of parameters is now limited to only those which support extraction.
- **Fixed:** An issue with input fields under the "Animation Layers" section not getting properly updated in certain scenarios when editing blendspaces.
- **Fixed:** Improved serialization of parameter overrides under the "Examples" section. Size of the value fields have been adjusted. Labels with names of corresponding parameters have been added. Value overrides are now properly referencing their parameter types by IDs rather than indices and persist through changes to dependent blendspace properties to mitigate various non-intuitive behaviors.
- **Fixed:** An issue with animation layer properties and blendspace properties displaying different names for the same parameters. Removed duplicated parameter/name mappings. Removed an unused parameter flag.
- **Fixed:** Multiple layout serialization bugs and simplified serialization logic. Window size is now properly restored after closing Character Tool and opening it again. Layout reset now restores default geometry of dock widgets on top of their composition.
- **Fixed:** An issue with the Character Tool not reverting to its open assets when answered 'no' to the unsaved changes dialog.
- **Fixed:** An issue with outdated animation entries being queried for blendspace parameter preview. Removed empty string from the blendspace parameter names to mitigate a common error occurring on blendspace reload.
- **Fixed:** Worked around an issue in the Character Tool with the indicator of changed content occasionally failing to disappear when performing a save.

#### Mannequin

- **Fixed:** An issue with the Mannequin Editor sometimes becoming unresponsive for an extended period of time when hovering the mouse cursor over its window.
- **Fixed:** Multiple key selections in the Transition Editor.
- **Fixed:** An issue with certain edit operations in the Transition Editor randomly affecting keys which were not selected by the user.
- **Fixed:** A potential crash in the Transition Editor by preventing mandatory keys from being deleted from the transition properties track. The context menu delete option is now properly grayed out for all immutable keys.
- **Tweaked:** Disabled default key selection - performed when opening the Transition Editor.

## AI

#### AI System

- **Refactored:** Setting navmesh raycast default version to the most recent version.
- **Optimized:** Navigation mesh visalizations and added a new CVar 'ai_NavmeshTileDistanceDraw'.
- **Fixed:** Behavior Tree node QueryTPS didn't check for eTPSQS_Error, thus in rare cases failing an assert.
- **Fixed:** Player was no longer registered in the AISystem after deserialization of the level when respawning from death, thus enemy AI would no longer be able to attack player.

#### UQS

- **Fixed:** Changed all places that were still relying on element names instead of element GUIDs. Added the concept of a default query type via UQS::Core::IUtils::GetDefaultQueryFactory (for the creation of a new query in the Sandbox Editor).

## Audio

#### Audio General

- **New:** Added preload component.
- **New:** Added listener component and fixed listener for ModelViewPort.
- **Fixed:** Global changes weren't applied in Wwise 2017.1.0.
- **Fixed:** Only enable Oculus based HRTF support if Oculus SDK is present.
- **Fixed:** Removed interface methods from the IAudioSystem interface.
- **Fixed:** An assert where debug display tried to access the adaptiveOcclusion value before it was determined.
- **Fixed:** When altering values of AudioSpot used in SCHEM-entity and then jumping into game caused a crash on exit.
- **Tweaked:** Updated Wwise SDK to v2017.1.1 build 6340.
- **Tweaked:** Updated FMOD Studio API to version 1.09.06.

## Core/System

#### Engine General

- **Optimized:** Improved the performance of the entity component helpers/icons in the Sandbox Editor.
- **Fixed:** Inability to change mesh component type at run-time.
- **Fixed:** Inability to re-activate particle component without reloading if the particle was disabled by default.
- **Fixed:** Camera component missing selection helpers.
- **Fixed:** Environment Probe component missing size indicator.
- **Fixed:** CAdvancedAnimationComponent::SetMotionParameter not respecting motion parameter overrides coming from higher-level systems.
- **Fixed:** Unresponsive fragment transitions when calling CAdvancedAnimationComponent::QueueFragment. Fixed a related memory leak issue.
- **Fixed:** Inability to disable collisions on physics primitive components.
- **Fixed:** Mesh and primitive components using incorrect entity slot ids.
- **Fixed:** Schematyc objets not triggering Start Node when spawned dynamically after gameplay has started.
- **Fixed:** CEntity::PhysicalizeSlot not passing the slot's custom material to the newly created physical part.
- **Fixed:** Geometry components stop casting shadows when duplicated.
- **Fixed:** Crash caused by dangling pointer in substitution component.
- **Fixed:** Properties of similar entities cannot be displayed unless they are copies.
- **Fixed:** 'Open Editor' icon not appearing next to particle fields.
- **Fixed:** Inability to specify the material for geometry components.
- **Fixed:** Some components didn't expose all functions to Schematyc.
- **Fixed:** Crash caused by inactive cameras not being correctly disabled.
- **Fixed:** Controller input doesn't work with the default input component.
- **Fixed:** Input component doesn't register multiple input groups properly.
- **Fixed:** PS4 pad doesn't work on windows machines.
- **Fixed:** Quat was not properly initialized in debug builds.
- **Fixed:** PoolAllocator was choosing non-power-of-2 alignment for some type sizes.
- **Fixed:** Newer Schematyc-based components relying on the legacy IID system - the IID function is now no longer needed for new components.
- **Fixed:** Schematyc package not being deregistered - prevents possible crash on shutdown.
- **Fixed:** Issue where during load, components were being created and initialized sequentially - instead of being created in one batch and then initialized.
- **Fixed:** ENTITY_EVENT_PHYS_POSTSTEP event never being sent.
- **Fixed:** Static Linking (OPTION_STATIC_LINKING) by using /WHOLEARCHIVE Visual Studio 2015 linker option, to prevent linker optimizing away static factory registrations.
- **Fixed:**'Trying to execute an audio trigger at (0,0,0)...' warning when playing a sound on proc layer in Mannequin preview.
- **Fixed:** Asynchronous Time Warp on OSVR.
- **Fixed:** Some cases of Engine assets not being loaded.
- **Tweaked:** Exclude some paths that, whilst not present in //ce/main_stabilisation, are in //ce/main (this will prevent problems with integrations).
- **Tweaked:** Correct invalid comments in default components.
- **Tweaked:** Improve markup of license.md.
- **Tweaked:** Note that pull requests must be made against the 'pullrequests' branch.
- **Tweaked:** Implement component unit tests to avoid regressions of older bugs that keep popping up.

#### Common

- **Refactored:** Deprecate macros that create GUIDs from two integers.
- **Refactored:** Unify CryGUID conversions from and to string.
- **Refactored:** Allow creation of enum serialization spec for already declared enums.
- **Optimized:** Remove CryGUIDHelper.

#### System

- **Fixed:** Engine starting without a project when migration was not possible.
- **Fixed:** Can't execute console commands from the cryproject file.
- **Fixed:** Crash on start-up if.cryproject file did not exist.
- **Fixed:** Inability to load.cryproject from disk in release builds.
- **Fixed:** Binary XML nodes not supporting cloning - now returns itself since the nodes are read-only anyway.
- **Fixed:** Releasing render pipeline when the renderer is released.
- **Fixed:** Loading of newer.cryproject versions causing a complete override of the file with dummy values.
- **Fixed:** No asset directory detecting an error when migrating from legacy sys_game_folder workflow to.cryproject.
- **Fixed:** Engine would silently start without project folder and/or assets - now shows errors to the user.
- **Fixed:** Assert when attaching remote console.
- **Fixed:** Engine root being added as a pak mod. Resulted in any files in the Engine root being constantly searched for, causing slowdowns and unrelated files to be added to file browsers. Additionally added %EDITOR% pak alias to avoid future issues with loading editor assets.
- **Fixed:** Plugins not being unloaded in the inverse order of loading.
- **Fixed:** (PS4) Cubemap descriptors.
- **Fixed:** Remote console deadlock on shutdown.
- **Tweaked:** Sign binaries and DLLs.

#### WAF

- **Tweaked:** Minor formatting tweaks in waf_branch_spec.py.

#### CMake

- **New:** CMake now downloads the SDKs through GitHub if bootstrap is not possible.
- **Fixed:** Where changed CMake options for Vulkan and HRTF weren't reflected by the CMake GUI. Additionally fixed runtime file deployment of PortAudio dlls.
- **Tweaked:** Sign binaries and DLLs.
- **Tweaked:** Added VS2017 options to cry_cmake.
- **Tweaked:** Modify Win32 and Win64 batch files to allow both VS2015 or VS2017 for building.

#### Action General

- **Fixed:** Persistent debug not working in Sandbox Editor.
- **Fixed:** Savegames can be loaded without writing the file extension in the console.

#### Flowgraph

- **Fixed:** Quick selection for FG-Nodes is broken.
- **Fixed:** (CECR) Crash when using Entity:SpawnArchetype in a new project not using the legacy IGame interface.
- **Fixed:** (CECR) Possible crash when retrieving game token if graph was null.

#### Game

- **Fixed:** Wrong sound playing when entering a map for the first time.
- **Fixed:** Where in multiplayer games the audio listener wasn't reactivated after killcam. Made sure that entities that are also audio listeners can create aux audio objects.
- **Fixed:** No longer attempting to call a missing script function.
- **Tweaked:** Update.cryproject file to point to 'GameSDK' directory.

#### Schematyc

- **New:** Expose Vector3 Project and Reflect nodes.
- **New:** Expose Negate and Sign nodes.
- **Optimized:** Removed Flowgraph integration - unfortunately too unstable due to not implementing Flowgraph events correctly.
- **Fixed:** Schematyc entity components being created and initialized sequentially - instead of being created in one batch and then initialized.
- **Tweaked:** Remove support for setting raw component members via the Set node - directly modified designer set data and this will affect what is saved to disk. Functionality will be reintroduced in a future update.

#### Templates

- **Fixed:** Blank and plugin template not registering user created entity components.
- **Fixed:** (ThirdPersonShooter) Warning spam issue occurring during camera movement by introducing more inertia when toggling the state of Mannequin tags.
- **Fixed:** ReflectType on CBulletComponent in all templates.
- **Fixed:** ReflectType on CBulletComponent in ThirdPersonShooter template.
- **Fixed:** Restore the network sync feature in the RollingBall template.
- **Tweaked:** (ThirdPersonShooter) Introduced a simple mouse input smoothing filter to mitigate jerky motion when turning around.

## Graphics and Rendering

#### Renderer General

- **Refactored:** Replacing all CryMakeUnique with stl::make_unique.
- **Fixed:** (Shaders) Fixed "Couldn't compile HW shader Hair@HairPS".
- **Fixed:** Cubemap generation issue.
- **Fixed:** Flickering debug information in the Sandbox Editor.
- **Fixed:** Exporting decals with nullptr material issue.
- **Fixed:** Disabled multi-threaded resource creation to allow sys_spec changes to succeed.
- **Fixed:** Release/build nullptr access when shutdown.
- **Fixed:** Depth-buffer resolution mismatch when initializing pipelines.
- **Fixed:** Make sure material resource set for CREFogVolume contains valid resources.
- **Fixed:** OpenVR plugin crashes on closing GameLauncher.
- **Fixed:** Launcher doesn't close properly on quit.
- **Fixed:** Disable depth fixup on PS4 to circumvent GPU hang.
- **Fixed:** Graphics-pipeline shutdown.
- **Fixed:** Changed upper bound of call-back removal to prevent stack overflow.
- **Fixed:** Nullptr access when shader creation fails.
- **Fixed:** Texture pointer invalidation by inverse weak pointer pattern.
- **Fixed:** Fatal error when the renderer cannot create its device. It also shows a proper message when a non-Vulkan GPU is used in combination with Vulkan renderer.
- **Fixed:** Warning in NC after map is loaded (Texture does not exist: texelspermeter.dds).
- **Fixed:** Viewport switching with AA on.
- **Fixed:** Prevent shader precaching on Vulkan and PS4 - we cannot compile individual shaders without resource layout on these platforms.
- **Fixed:** Supersampling and downsampling being too dark.
- **Fixed:** Viewport rendering "bleed".
- **Fixed:** API spec violation when resizing the Viewport in the Sandbox Editor.
- **Fixed:** Highlight pass PSO.
- **Fixed:** SelectionID pass depth buffer.
- **Fixed:** Scene depth resolution for supersampling.
- **Fixed:** Moon texture release.
- **Fixed:** Removed debug asserts/breaks.
- **Fixed:** DX12 validation error on startup - cannot access backbuffers in use by compositor/device.
- **Fixed:** (Shaders) Remove now obsolete hlslcc workarounds for unaligned variables in constant buffer.
- **Fixed:** XBox One backbuffer format.
- **Fixed:** Cubemap streaming upload assert.
- **Fixed:** Clear rendertargets of HDR Pipeline before use.
- **Fixed:** Numeric coding of texture types - can't be changed in any way.
- **Fixed:** Convert material to multi-material crashes (Sandbox.exe!CMaterial::UpdateHighlighting).
- **Fixed:** Ground material is wrongly applied to objects such as spheres in vr_demo.
- **Fixed:** Assert when starting game/ComputeRenderPass.cpp.
- **Fixed:** Upsample pass reading sRGB.
- **Fixed:** Z-target downsampling on XBox One.
- **Tweaked:** Added Editor startup information for shader compilation to fix unclear startup "freeze" when all shaders need compiling.

#### Vulkan

- **Fixed:** Assert caused by CDeviceTexture::GetLayout returning no data.

#### 3D Engine

- **Refactored:** Added CVar to control integration of object meshes into terrain mesh.
- **Fixed:** Crash in LightVolumes caused by light count exceeding local array bounds. Added constant for limit.
- **Fixed:** Precision improvement in CSkyLightNishita - potentially fixes assert.
- **Fixed:** Missing UI reaction for 'objects into terrain mesh integration' feature.
- **Fixed:** CVar "e_ViewDistRatioLights" not being updated.
- **Fixed:** (VR) Oculus headset works, but GameLauncher.exe window only shows a black screen.

#### Particles

- **Fixed:** Prevent out of bounds access in specular probe texture array.
- **Fixed:** Non-functioning presets. Mesh presets now have sphere default, ribbon has anti-gravity.
- **Fixed:** Crash from null attribute pointer.
- **Fixed:** TimeSource domain fixes. Per-instance contexts now always access parent data. Only parent age data is "age-anti-aliased".
- **Fixed:** Serialization conversion bug.
- **Fixed:** Some example effects in Engine Assets to work properly.
- **Fixed:** Particle Entity Components now reliably activate and deactivate emitters without creating duplicates. Emitters no longer spawn particles when inactive.
- **Fixed:** Restored env lighting to particles. Restored unit-scale Diffuse parameter.
- **Fixed:** Serialize "enabled" state of features.
- **Fixed:** Crash during GPU particles editing. Class members moved for correct destruction order.
- **Fixed:** Restored AnimBlend and DrawOnTop functionality.
- **Fixed:** Audio would not play if emitter was Primed. Now plays if emitter starts any time during its emitter lifetime.
- **Fixed:** Potential crashes caused by multi-threaded static function data init.
- **Fixed:** Emitters did not always create unique seed if spawned from Engine.
- **Fixed:** AudioTrigger start/stop events caused by improper conversion from previous format.
- **Fixed:** Random seed not being exposed to UI spawn parameters.
- **Fixed:** Re-added default particle component template.
- **Fixed:** AudioTrigger crash. Restricted EOcclusionType enum to allowed values.
- **Fixed:** Crash in GPU particles caused by delayed emitter pointer assignment.
- **Fixed:** Crash from recent audio checkin (GetNumResources returned wrong value). Restored particle entity deactivate behavior, allowing particles to execute audio stop functions. Fixed unit tests after change to unique renaming.
- **Fixed:** Feature AudioTrigger now allows both start and stop trigger in same feature, making it consistent with other audio triggers in the Engine.
- **Fixed:** Crash in creating unique component name, and generalized to work with no number limit.

#### Plugins

- Optimized**:** Remove now unused FPS plugin.

#### PS4 Renderer

- **Optimized:** Render occlusion buffer debug visualization in one draw call.
- **Fixed:** Workaround for assert caused by numerical issues DU to RCP call on PS4.
- **Fixed:** Particle tessellation is broken. Disable for now to avoid rendering artifacts.
- **Fixed:** GPU timestamps.
- **Fixed:** Implement null resources.
- **Fixed:** Depth readback.

#### C#

#### C#.Core

- **Fixed:** Updated mono with fix for possible shutdown issue.
- **Fixed:** Crashes when reloading the mono runtime.
- **Fixed:** C# components now set the right default value when initialized in a SchematycEntity.
- **Fixed:** CMonoProperty::Set not passing value types to managed code correctly.
- **Fixed:** CMonoObject::CopyFrom not copying reference types correctly.
- **Fixed:** Component properties not showing up in Schematyc.
- **Fixed:** Component properties being deallocated but not destroyed.
- **Fixed:** Default value of component properties not being set.
- **Fixed:** Entity pointer being unavailable when properties were set.
- **Fixed:** (CECR) Possible crash if managed plugin class was removed.
- **Fixed:** (CECR) Crash during startup if plugin domain failed to initialize.
- **Fixed:** (CECR) Crash if the compilation of C# source files in assets directory failed.

#### CryMonoBridge

- **Refactored:** Added GetComponents, GetComponentsWithInterface and GetComponentWithInterface to the C# Entity.

## Physics

#### Physics

- **Fixed:** Check for RWI called in the destroyed world.
- **Fixed:** Issue with loading ocean area in physdebugger.
- **Fixed:** Player not responding to gravity changes.
- **Fixed:** (Components) (Physics) Enforce rigid-body component to be awake on level-start in case of 'enabled by default'.

## Project System

#### CryVersionSelector

- **New:** CryVersionSelector now remembers your last selected platform.
- **New:** Added Generate Engine Solution to the.cryengine file.
- **Fixed:** CMake opening the wrong source directory.
- **Fixed:** CMake setting NMake as the generator instead of Visual Studio.
- **Tweaked:** Generated CMakelist now includes an easier way to switch the target to Gamelauncher, Server and the Sandbox Editor.
- **Tweaked:** Added error-messages if Windows only features are used outside of Windows.
- **Tweaked:** Updated the order of the options when right-clicking.cryproject and.cryengine files.

## Sandbox

#### Editor General

- **New:** Use mobile GPUs instead of CPU for rendering.
- **New:** (FBX IMPORTER) Generate texture coordinates option added.
- **New:**(FBX IMPORTER) Compute normals option added.
- **Fixed:** Sandbox Editor crash when deleting/renaming level.pak folder CLayerSetSwitchNode::OnLoadingComplete.
- **Fixed:** Positioning duplicated objects results in massive frameratedrop.
- **Fixed:** Opening & closing the Tag Definition Editor will now keep the ID selection.
- **Fixed:** Mannequin layout wasn't saved after closing.
- **Fixed:** Timeline in Mannequin sometimes got lost between other panels.
- **Fixed:** Undoing the creation of a vegetation object will now clear selection in the vegetation tree view.
- **Fixed:** Issue with joint generation on entities without script tables.
- **Fixed:** Crash where code tried to remove a non existing entity and accessed an invalid pointer.
- **Fixed:** Crash when showing Navigation Area context menu.
- **Fixed:** Navmesh wasn't updated when editing holes in terrain.
- **Fixed:** Navigation areas are again slightly offset below the terrain after they are created.
- **Fixed:** Public Schematyc components not allowing modification of Transform.
- **Fixed:** Make File > Exit close Editor correctly.
- **Fixed:** (TRACKVIEW) Creating a key adds two events to undo/redo-queue.
- **Fixed:** TRange.IsEmpty could crash CurveEditor.
- **Fixed:** (ENTITY AI) SmartObject renderobject does not change with the type.
- **Fixed:** Create/Open level dialogs will now create the level folder if it didn't previously exist.
- **Fixed:** Inability to edit and see an objects default material in the inspector.
- **Fixed:** (PREFAB) Prefab properties don't hot reload after using undo.
- **Fixed:** Issues with undoing folder layer creation, including a potential crash.
- **Fixed:** (UI) All colors set to black in preferences after registering Engine.
- **Fixed:** Possible crashes if Engine initialization failed early.
- **Fixed:** Shapes not being immediately updated after the transform is changed when using the mouse wheel.
- **Fixed:** Inability to select entities by clicking on their editor-only helper object.
- **Fixed:** (TERRAIN) Ocean not visible after resizing the terrain.
- **Fixed:** Crash when trying to detach individual objects from a prefab through the properties panel.
- **Fixed:** (CECR) Possible crash caused by the ability to undo selection of invalid layer.
- **Fixed: (** FLOW GRAPH) Using undo/redo often (after adding a node) cause a crash (Sandbox.exe!CHyperGraph::GetAllEdges).
- **Fixed:** Scrolling the mouse wheel while placing a navigation area shape causes to rotate the shape and sets the points movement offset.
- **Fixed:** Object tree in Prefabs Library collapses after placing a prefab.
- **Fixed:** Opening any selection window once - causes the property panel to flicker/redraw on each change.
- **Fixed:** Assertion triggered when scaling component-based entities.
- **Fixed:** (FLOW GRAPH) Using "q" to quickly add a node causes an instant crash CHyperGraphView::OnKeyDown.
- **Fixed:** Default entity icon being shown for entities with helpers.
- **Fixed:** Reverting of a component's properties in the inspector recreating the entire entity.
- **Fixed:** Case where components were duplicated after undoing entity deletion.
- **Fixed:** Entities without scripts being reloaded when scripts changed.
- **Fixed:** Crash when undoing layer deletion through the context menu in the level explorer and then doing undo/redo.
- **Fixed:** (TRACKVIEW) Creating a key adds two events to the undo/redo-queue.
- **Fixed:** Moving objects between layers for large object counts. This issue could stall the Sandbox Editor indefinitely.
- **Fixed:** Open File dialog - sort by size produces inprecise results.
- **Fixed:** (TRACKVIEW) Capture track produces warning (End capture failed).
- **Fixed:** Non-uber fix.
- **Fixed:** Asset Browser remembers thumbnail size, splitter placement.
- **Fixed:** (TRACKVIEW) Now takes into account which item was clicked when scaling and moving keys, rather than snapping to the first key on the timeline.
- **Fixed:** (UI) PFX2 tool/icon bar pane maximizing/stretching view.
- **Fixed:** (LEVEL EXPLORER) Layers - create/delete layers not captured by undo/redo queue.
- **Fixed:** (TRACKVIEW) Track selection.
- **Fixed:** (FLOW GRAPH) The 'New AI Action' dialogue window is missing a button to create a new folder.
- **Fixed:** (DATABASE VIEW) Prefab instance counter.
- **Fixed:** (DESIGNER) Slice number broken.
- **Fixed:** Crash when loading a level with Mannequin open.
- **Fixed:** (PREFAB) Areas/shapes, AI Points, Decals are hidden in a closed prefab that is placed in the Viewport.
- **Fixed:** Missing settings in camera properties.
- **Fixed:** Crash when undoing layer deletion due to a stale layer pointer.
- **Fixed:** CVar toolbuttons in toolbars - now have the CVar value they are set to appear on the tooltip.
- **Fixed:** Changed styling for disabled scrollbars so that they better reflect their current state.
- **Fixed:** An issue where spamming the generate mip map button would make the screen go permanently black.
- **Fixed:** Crash when undoing/redoing the deletion of a layer.
- **Fixed:** Align to grid option doesn't work unless grid snapping is enabled.
- **Fixed:** An issue in track view where if the user wasn't recording changes, had a rotation keyframe on the entity and when trying to modify rotation on said entity (through the properties panel or transform tool) then rotation on the keyframed axis would be locked. Fixed a similar issue with scale as well.
- **Fixed:** Creating a new level with added animations folder triggers errors in NC.
- **Fixed:** Creating a new map sometimes triggers an assert.
- **Fixed:** Scrolling the mouse wheel while placing a shape causes to rotate the shape and sets the points movement offset.
- **Fixed:** Selection of objects inside groups being unreliable.
- **Fixed:** Inability to select entities with meshes by simply clicking on the mesh.
- **Fixed:** Crash during early shutdown by removing special shutdown behavior.
- **Fixed:** (CHARACTER TOOL) Adjusting dimensions in Blendspace does not allow you to change the dimensions values.
- **Fixed:** (CHARACTER TOOL) Will now auto expand folders when the search is used. Also the filter is now applied as the user types.
- **Fixed:** Selecting the first animation does nothing, selecting the second plays automatically.
- **Fixed:** Crash when immediately switching from Area:Solid to Area:ClipVolume, or double-clicking on any of these.
- **Fixed:** Selection mask doesn't work for AI Navigation Seed Point.
- **Fixed:** No selected material in the material editor after clicking on edit material in the properties panel.
- **Fixed:** Rectangular selection works properly for all objects.
- **Fixed:** (FBX IMPORTER) Imported *.fbx with locomotion animation is missing root translocation.
- **Fixed:** Crashhandler doesn't give the opportunity to save the map.
- **Fixed:** Property trees not copying text to the OS-level clipboard.
- **Fixed:** Color picker alpha is not propagated to Engine.
- **Fixed:** AudioAreas (and some other legacy (proxy) Components) were not exported anymore.
- **Fixed:** Designer tool crashing when selection changes while in the UV Mapping Tool.
- **Fixed:** Occasional crash when rapidly docking and undocking windows.
- **Fixed:** (FBX IMPORTER) Physical proxies have wrong transformation.
- **Fixed:** (TRACKVIEW) Properties Panel shows only X-values of keys.
- **Tweaked:** Context Editor is now called Preview Editor.

## Tools

#### Tools General

- **Optimized:** Remove obsolete script to copy Wwise SDK.
- **Fixed:** Viewport problems in several tools (CT, MANN, Schematyc) - wrong depth buffer used, resulting in strong artifacts.
- **Tweaked:** Added support for unattended option to disable message boxes and asserts.
