# CRYENGINE 5.3

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/47316993/pages/44962657
- Page ID: 44962657
- Breadcrumb: Engine Release Notes (Current) > CRYENGINE 5 > CRYENGINE 5.3
- Parent: CRYENGINE 5

## Child Pages

- [CRYENGINE 5.3.4](CRYENGINE%205.3/CRYENGINE%205.3.4.md)
- [CRYENGINE 5.3.3](CRYENGINE%205.3/CRYENGINE%205.3.3.md)
- [CRYENGINE 5.3.2](CRYENGINE%205.3/CRYENGINE%205.3.2.md)
- [CRYENGINE 5.3.1](CRYENGINE%205.3/CRYENGINE%205.3.1.md)
- [CRYENGINE 5.3.0](CRYENGINE%205.3/CRYENGINE%205.3.0.md)

## Content

## Code Interface Changes

See the**[Important CRYENGINE 5.3 Data and Code Changes](CRYENGINE%205.3/CRYENGINE%205.3.0/Important%20CRYENGINE%205.3%20Data%20and%20Code%20Changes.md)** article for more information.

If you are upgrading from CRYENGINE 5.2 please read **[Migrating from CRYENGINE 5.2 to CRYENGINE 5.3](CRYENGINE%205.3/CRYENGINE%205.3.0/Migrating%20from%20CRYENGINE%205.2%20to%20CRYENGINE%205.3.md)**.

## Release Highlights

**CRYENGINE 5.3 is now available for download**

Welcome to the release highlights for our latest major update, CRYENGINE 5.3 - and what a release it is! Our keystone feature is a new Visual Scripting language called Schematyc that allows anyone to create gameplay systems using predefined nodes. We also now have support for NVIDIA’s popular PhysX physics solution, a range of big improvements to our Sandbox Editor and an all-new Asset System and Browser.

We should also point out that in the spirit of our new, community-driven approach, CE 5.3 includes several features that are released earlier than usual as Beta versions. This way, you can all give your feedback straight away as we continue to improve and iterate on these features in future releases.

With that said, let’s take a look at some of the highlights of CRYENGINE 5.3:

**Schematyc (Beta Release)**

Schematyc is a node-based visual scripting language aimed at changing the way gameplay systems can be built within CRYENGINE. It gives Designers the power to create new gameplay functionality using a set of building blocks, but without needing an actual Programmer every step of the way. As such it should especially benefit smaller indie teams, where we know that experienced C++ programmers can often be a rarity, as it allows everyone on the team to help with gameplay scripting.

Schematyc "Lighten Up" sample for users to reverse engineer and learn common Schematyc best practices: **[Lighten Up!](https://www.cryengine.com/marketplace/product/cryengine-schematyc-sample)**

![Image](https://www.cryengine.com/docs/static/attachments/44962659)

Note: This is a Beta release with limited functionality and nodes. We look forward to your feedback!

**The Sandbox Editor**

Our new Qt-based Sandbox Editor, that we released with CRYENGINE 5.0 is now the only supported Editor. The previously provided Legacy Editor (using the older MFC-based interface) will now be deprecated and thus no longer available going forward. You can learn more about this decision and our thinking behind it **[in this blog post](https://www.cryengine.com/news/an-update-on-our-sandbox-interface-and-the-legacy-editor)**. Other improvements to the Sandbox Editor include support for High-DPI displays for a more comfortable working experience and what we call the “F-Key Workflow” in which we have mapped many of the most commonly used commands in the Engine to your function keys.

For those of you who are just making the transition to the new Sandbox Editor, then we have prepared **[a page that will get you started](../../../Manual/CRYENGINE%20-%20Getting%20Started/Migration%20Guides/MFC%20Editor%20to%20Qt%20Editor%20Interface%20(CRYENGINE%20V).md)** and show you the biggest interface changes between the new and the old Sandbox Editor.

**Entity System Rework**

In this release we have done a refactor of the entity system in order to create a future-proof and unified way of extending the logic of game objects. This is done by unifying the previous game object extensions and proxies into "entity components." Components can be attached to any entity at any point during their lifetime and they can be created in C++, C# or Schematyc.

Extending these components to build complex entities can be seen in this playlist where we go from writing and exposing a CRYENGINE plugin and then building up components to be used within it.

**C# Refactor**

We have undertaken a rewrite on the C# integration introduced with CRYENGINE 5.0. This changes underlying functionality and style in order to be more in line with the.NET coding guidelines so we can provide a consistent development experience for developers coming from a heavy C# background. This also introduces support for new features such as the ability to write new entity components in C#.

**CMake Build System**

In the past, the WAF Build system served as the primary build tool to compile CRYENGINE. However, in order to simplify this aspect of the engine, we are making the switch over to CMake as our new go-to build system for CRYENGINE.

So what is CMake? CMake is a cross-platform open-source tool for compiler-independent build creation, and fits perfectly with our ongoing mission of making CRYENGINE more open and community-driven.

You can find the full documentation for**[CMake in CRYENGINE here](../../../API%20Reference/CRYENGINE%20Build%20System/CMake.md)**. We have also prepared some **[documentation covering the migration from WAF to CMake](../../../API%20Reference/CRYENGINE%20Build%20System/Migrating%20from%20WAF%20to%20CMake.md)**.

**Built-in PhysX Support**

**[NVIDIA’s PhysX technology](https://developer.nvidia.com/gameworks-physx-overview)** is coming to CRYENGINE in the 5.3 release as a Beta, this will be the first time that users will have a built-in alternative to our proprietary CryPhysics suite when building their games. This will give all Cryengineers more flexibility than ever before when it comes to selecting the right physics solution for their games’ unique needs.

For those unfamiliar with it, NVIDIA PhysX is a scalable multi-platform game physics solution that supports a wide range of devices and has been/is used in many of today’s most popular games and platforms.

[**Using NVIDIA PhysX in CRYENGINE**](/docs/static/engines/cryengine-5/categories/23756816/pages/26218186)

**New Asset System (Beta Release)**

This new Beta release is the first step on our way to a future In-Editor, Asset Browser-driven workflow. This will make the reliance on Windows Explorer a thing of the past when working on your CRYENGINE projects.

For the initial release in CE 5.3, this tool will allow you to search for anything within your project and to import assets without having to use separate importer tools outside of the Sandbox.

Want to learn more about the new Asset Browser and the metadata-driven Asset System? **[You can do so with our documentation](../../../Manual/Editor%20Tools/Asset%20Browser.md)**.

**FBX Pipeline Improvements**

Our FBX Import Pipeline has been one of our most popular additions to CRYENGINE this year and we are happy to add even more features with this release.

Firstly, we are adding the ability to create physicalized character skeletons and ragdolls as part of the importer workflow, this will allow users to assign mesh nodes as proxies for bones.

The second big improvement is automatic physical proxy generation for static geometry as part of the MeshImporter workflow, this will allow users the ability to edit these proxies afterwards.

The FBX Import Pipeline is a prime example of how community feedback can shape the future development of CRYENGINE, so we look forward to hear/read your thoughts on these new additions!

![Image](https://www.cryengine.com/docs/static/attachments/44962658)

**F-Key Workflow**

As part of the Asset Browser release, we have mapped some of the most commonly used functions to the function keys to make for an even faster and more intuitive workflow. Below is a short listing of several of the mappings provided:

- F1 - Help/documentation
- F2 - Asset Browser (toggle)
- F3 - Find
- F4 - Go to level editor (useful with many windows)
- F5 - Go to game
- F7 - Export to game

**Support for High-DPI monitors**

We are adding support to make the text in the Sandbox Editor both comfortable and efficient to work with for users of High-DPI monitors (such as 4K screens).

Higher resolution screens, especially 4K, will often have a significantly higher pixel density than a typical 1080p screen. This means that content which was designed to be readable on the 1080p screen needs to be adjusted in order to occupy a similar amount of physical space on a 4K monitor.

Users will have noticed issues in prior versions of the Editor that this support is required. So rest assured you can now use CRYENGINE at 4K until you melt your GPU.

**User Analytics**

CRYENGINE 5.3 now includes a User Analytics System (UAS). We have introduced this so that we can collect custom Sandbox Editor and Game Launcher events. By collecting user data such as;

- Which Sandbox tools are used the most
- Which Sandbox tools are not used very often
- Which Sandbox tools are not used at all
- How often are users affected by crashes
- What are average loading times

We will be more aware of the CRYENGINE user experience and therefore better able to direct our technical development to the needs of our users. Don't worry about the data we collect - it will only be used internally and for the purpose of improving the user experience of CRYENGINE.

**Universal Query System (Beta Release)**

With this release, we introduce a beta version of our new Universal Query System (UQS). It's a spatial query system that can be used by AI and other systems to ask 'smart' questions about their environment.

One of the highlights of this system is to be able to have the basic building blocks for complex queries be provided fully by, for example, the game code. That makes it easy and straightforward to extend. In the future it's meant to supersede the CryAISystem's Tactical Point System (TPS).

Expect more updates on UQS in the future and expansion on it within other systems like Schematyc!

**[UQS Documentation Link](/docs/static/engines/cryengine-5/categories/23756816/pages/26217637)**

## Game Templates

- **New:** Changed from legacy GameDLL usage to new game plugin - involves removing CGameStartup, CEditorGame and only using newer systems.
- **New:** Isometric Game Template - showcases isometric view and basic AI pathfinding.
- **New:** Plugin template - gives users a quick start for creating a new plugin.

## Animation

#### Animation General

- **New:** Changed animation transition weight to sine based and fixed issue with linear blending out of anim layers. Introduced DefaultTransitionInterpolationMode CVar to set interpolation globally.
- **New:** PoseModifier IkCCD - added debug draw.
- **New:** Removed unneeded assert on files not existing in resourcelist.txt. Thus, renaming of skeleton-files is now possible and without changing resourcelist.txt, since the containing files are not compulsory.
- **New:** Implemented PoseModifierSetup interface for querying Pose Modifiers.
- **Fixed:** Update relative movement on looping animations.
- **Fixed:** Selecting a specific animation for a key in Trackview triggers assert.
- **Fixed:** New character instance processing ignoring full skeleton update. This resolves Multiplayer behavior, where servers and clients may need to update characters despite visibility.
- **Fixed:** Manual seek usage in transition queue breaking animation events.
- **Fixed:** Added a missing nullcheck.
- **Fixed:** Updated an invalid range check condition in CAttachmentSKIN::GetVertexTransformationData. Added a couple of safety asserts.
- **Fixed:** Removed data-dependent runtime checks guarding attachment asset consistency with hard fatal error invocations.
- **Fixed:** A potential race condition in CSkeletonAnim::PushPoseModifier - modifier instances pushed during animation processing are now always appended to the correct queue.
- **Fixed:** Added a missing vertex/index count check before trying to allocate a render mesh chunk.
- **Tweaked:** Misspelled parameter name in IK xml-reader.
- **Tweaked:** Set default maximum skeleton animation layer count to 32.

#### Character Tool

- **Fixed:** Removed persistent serialization of session-specific state from the PropertiesPanel.

#### Mannequin

- **Fixed:** Reimplemented the animation resource picker functionality for animation fragments.
- **Fixed:** Fragments are not deleted anymore if dragged out of window or track.
- **Fixed:** Removed a bunch of redundant asserts checking against conditions that already have valid error handling control paths.
- **Fixed:** "Go to end button", removed unused member variable.
- **Fixed:** Added an early Editor flag initialization for character instances controlled by the Mannequin to mitigate certain scenarios in which it was not set on time.
- **Tweaked:** Changed ActionScopes from uint32 to uint64 to allow more than 30 scopes.

## AI

#### AI System

- **New:** Introduce MNM::Tile::ITileGrid and expose read-only navigation mesh using MNM::Tile::STileData.
- **New:** Introduce MNM::TileGenerator::IExtension interface to allow game projects to participate in MNM tile generation.
- **New:** Interface-method to set BehaviorTree.
- **New:** Registration of named BehaviorTree nodes.
- **New:** Added MNM::IMeshGrid::FindClosestTriangle.
- **New:** Added MNM::IMeshGrid::QueryTriangles, which supports custom triangle filters.
- **Refactored:** Move structures used for tile data to CryCommon, expose some utility functions.
- **Refactored:** Remove queries for the distance to the closest point, where they are not needed.
- **Refactored:** Rename distSq parameter to distance on NavigationSystem::GetClosestMeshLocation and MeshGrid::GetClosestTriangle to show actual value scale.
- **Refactored:** MeshGrid code which searches for closest triangles.
- **Refactored:** Provide a way to address and access neighbor tiles through MNM::IMeshGrid.
- **Refactored:** Rename MNM::Tile::ITileGrid to MNM::IMeshGrid.
- **Refactored:** Mark ValidateVolume and GetVolumeID function of INavigationSystem as const.
- **Refactored:** (MNM) Increase exported MNM.bai file version number to 9.
- **Refactored:** Rename MNM::IMeshGrid to MNM::INavMesh, MeshGrid to CMeshGrid, fix variable names and comments.
- **Fixed:** Set TriangleId on first/last path waypoints and on the off-mesh link exit waypoints.
- **Fixed:** Use 3D distance calculations instead of 2D in the SmartPathFollower when requested.
- **Fixed:** (NavigationSystem) When creating a new level, exclusion volumes associated to agents carried over from the previous level instead of getting cleared.
- **Fixed:** (CAISystem::SendSignal) When sending signals to a group, the pseudo group was also receiving those signals causing unrelated AI agents to base their decisions on inconsistent information.
- **Fixed:** Path beautification accessing wrong triangles on paths traversing through off-mesh links.
- **Fixed:** Crash when trying to register a lua-less entity with the AI system.
- **Fixed:** Made AISystem-internal flownodes compatible with new plugin system.
- **Fixed:** (CoverSampler) There was still an edge case where after simplification we could end up with less than 2 samples.
- **Fixed:** Crash due to access to the main thread's IRenderAuxGeom from the NavigationSystemBackgroundUpdate thread.
- **Fixed:** Potential div-by-zero crash during path-finder string pulling through very small triangles.
- **Fixed:** (MNM) Navigation area shapes with the same names destroying each other's volumes and meshes.
- **Fixed:** (MNM) Navigation exclusion volumes not exported.
- **Fixed:** (MNM) Crash on spawning tile generation job, because of the missing mesh boundary volume.
- **Fixed:** (Movement Planner) Now re-pathfinding if we figure that a previous pathfind request comes back with its result just after a UseSmartObject block has changed its state from "prepare" (still interruptible) to "traverse" (and is no longer interruptible).
- **Fixed:** Crash caused by the silent cloning of off-mesh link data.
- **Fixed:** (CSmartPathFollower) When about to start traversing a path, now allow for a much higher z-tolerance to find the start index on the path (this is important when still traversing a SmartObject at a significantly different height than where the upcoming path begins).
- **Fixed:** (CAIObject) Dynamically spawned objects. When the game exited and returned to editing mode objects such as grenades were ending up with a dangling handle into the VisionMap.
- **Fixed:** (OffMeshNavigation) Restoring offmesh links when SmartObject is unblocked.
- **Fixed:** CVehicleSeat::GetMovementState didn't take into consideration the scaling of a transformation matrix when computing direction vectors, thus causing non-unit vectors to end up in CAIActor::SetPos.
- **Fixed:** Bypass null IPhysicalEntities when checking line-of-fire.
- **Fixed:** (Cover Surfaces) Copying cover surfaces in the Editor caused inconsistencies in the free pool on the AISystem side that led to crashes when dynamic covers came into play.
- **Fixed:** (NavigationSystem) When exporting a map, it might have also exported invalid exclusion volume IDs, which would then dangle upon re-loading the map.
- **Fixed:** (AISequence) Start node now prints a warning should the Designer have forgotten to assign an entity to that particular node.
- **Fixed:** (Sequence nodes) Changed the way how nodes react on invalid sequence IDs to prevent consequential errors from preceding errors.
- **Tweaked:** (SequenceAgent) Now showing a bubble message instead of failing an assert when the Level Designer has assigned a non-CAIActor to the sequence.

## Audio

#### Audio General

- **New:** Decoupled Audio Objects and Audio Listeners.
- **New:** Removed id lookup.
- **New:** FlowGraph support for the Audio area Entity that was moved to C++.
- **New:** Added Audio Controls as possible properties for entities.
- **New:** Added all of the Audio Entities to the new C++ system**.**
- **New:** (SDLMixer) Added libmodplug 0.8.8.5 (only compiled on Linux/Android due to lack of C99 support in MSVC).
- **New:** (SDLMixer) Upgrade libmikmod to 3.3.10.
- **New:** (SDLMixer) Added flac 1.3.1.
- **New:** Missing dropdown options from the Audio trigger spot.
- **Refactored:** Removed dependency of Audio middleware implementations to the Audio Object id.
- **Optimized:** Removed the debug-name-store functionality - storing debug data on the objects now.
- **Optimized:** Removed primaryMemoryPoolSize CVar, because that variable described only a combination of all other pools and should therefore not be set manually.
- **Optimized:** Removed unneeded runtime polymorphism (cherry picked from audio_refactoring, but adjusted the changes to be compliant with guidelines. Additionally fixed a bug and inconsistencies in the original change list).
- **Optimized:** Slowed down Audio thread execution to around 100fps to be mainly in sync with the main thread and minimize the load on Physics by sending less ray casts per game frame.
- **Fixed:** Potential crash on executing Audio Track trigger keys.
- **Fixed:** Listener and Sound sources - were both set to 0,0,0 after loading a savegame.
- **Fixed:** Problem with muffled sound after loading a savegame.
- **Fixed:** Switches, rtpcs and environments now properly set when changed.
- **Fixed:** (nullptr) Access in PortAudio implementation.
- **Fixed:** Where unloading of memalloc-failed audio files corrupted the mem-usage counter. Additionally, the AFCM does not immediately unload ref-counted files anymore.
- **Fixed:** Default Audio Entities, plus some areas do not work in game templates - added Audio Entities and dependencies to the game templates.
- **Fixed:** FMOD Studio events did not assume obstruction and occlusion values on start.
- **Fixed:** Check for valid clip volume id before setting clip volume blend info.
- **Fixed:** Fixed assert when refreshing Audio with SDL Mixer.
- **Fixed:** Fixed compilation on Linux.
- **Fixed:** Added missing Audio Entities to WAF and CMake.
- **Fixed:** Where the "InnerFadeDistance" property wasn't properly ex-/imported for AreaBox, AreaSphere and AreaShape.
- **Fixed:** Removed assert when the global Audio preload is missing.
- **Fixed:** Removed unneeded assert for when occlusion Audio Objects and a listener are too close to each other.
- **Fixed:** Crash on shutdown where the GameSDK player class accessed an invalid entity, removed obsolete StopLoopingSounds method.
- **Fixed:** Crash with runtime audio middleware change. Implementation modules now have all the same module class name.
- **Fixed:** Audio ambiences not playing when using level specific Audio Triggers.
- **Tweaked:** Updated Wwise SDK to v2016.2.0 build 5972.
- **Tweaked:** Increased max length of Audio Control names to 128.
- **Tweaked:** Remove dynamic libary modules from SDL Mixer - everything is now static.
- **Tweaked:** FMOD Studio Snapshot connections to AudioTriggers can now be set to either get started or stopped.
- **Tweaked:** Minor cleanup in Audio FlowGraph nodes.
- **Tweaked:** FG AudioTrigger nodes now register/unregister asynchronously as a listener to Audio system events and only register if the "Done" output port connects to something.
- **Tweaked:** Removed obsolete "PREVENT_OBJECT_COPY" and "DELETE_DEFAULT_CONSTRUCTOR" macros from the Audio code.
- **Tweaked:** Updated FMOD Studio API to version 1.08.14.

#### ACE (Audio Controls Editor)

- **Fixed:** Where the ACE did not load activity radii.
- **Fixed:** Crash when accessing temporary data during ACE boot.
- **Fixed:** ACE sometimes crashes when being opened while running either FMOD Studio or SDL Mixer.

#### DRS (Dynamic Response System)

- **New:** Added a local variable that holds the priority of the currently spoken line, so that you can use that in conditions to find out if another line can be spoken or not.
- **New:** Added a flag to make SpeakLine actions cancel their parent-response in case they are canceled/skipped (to allow stopping of dialogs, if a line of it cannot be spoken).
- **New:** Added a flag to make SpeakLine action fire signals on Start/Finish/Skip/Cancel.
- **New:** Added a queuing system for dialog lines.
- **New:** The DRS does not load responses and lines automatically when created, but now waits for Init to be called by the game. Plus fixed a potential bug when custom-actions where registered after the DRS had already loaded all responses.
- **New:** Added a useful warning about referenced, but not-existing lines in the SpeakLine action.
- **New:** Added an option to activate/deactive removing of default values from stored/saved state data.
- **New:** Current state of lines (last picked variation) can now be serialized.
- **New:** Added a new way for only-once lines (on a per line base).
- **New:** Optimized how CancelSignal was working (to allow for having a CancelSignal action at the beginning of a response to stop any other running instance first).
- **New:** Added a new property for each drs-actor that starts speaking a line 'LastLineFinishTime', which can be used to check for a moment of silence before starting a new line (to not interrupt dialogs).
- **New:** Added a CVar drs_loggingOptions to enable logging to file for DRS events (in non release builds).
- **Optimized:** Swap queuedSignals instead of moving them to avoid re-allocations.
- **Fixed:** The "executeResponse action" was not canceling the response it was executing.
- **Fixed:** Changed the way how a stored state is given out via the interface - to avoid passing strings over module boundaries.
- **Fixed:** Fixed a CppCheck complain.
- **Fixed:** Make sure that FlowGraph nodes unregister as a listener in destruction.
- **Fixed:** AttachmentTag name-hash was cached but not used.
- **Fixed:** Crash where local variable collections are not created (only happening in a very special kind of setup).
- **Tweaked:** Cancel Response is now working more efficently.
- **Tweaked:** Added a way to cancel all running responses, but not the current response.

## Core/System

#### Engine General

- **New:** (Schematyc Beta) An experimental tool to build gameplay systems. Gives Designers the power to create new and reusable functionality from a set of building blocks provided by Programmers. Whereas FlowGraphs are great for level scripting, Schematyc is designed to provide more finite control of Objects within levels. All logic is driven by state and context in order to simplify the information presented to Designers, this greatly reduces latency and makes it possible to take new gameplay systems beyond the prototyping stage without the need to re-write them in C++.
- **New:** Added sub character instances to es_debugAnim.
- **New:** Added AutoComplete to es_debugAnim.
- **New:** Async level load.
- **New:** Generated template solution - now sets the correct VS startup project automatically.
- **New:** (DynArray) Added replace and emplace functions. Refactored all insertion functions to take all possible initialization values including default- and no-init. Now inits to T by default, same as std::vector. EInit argument can specify eZeroInit or eNoInit. Removed _raw functions. Optimized for moving temp values into array. Use variadic templates and forwarding to simplify replace, insert, etc. Resizing optimized - reallocation now occurs in 2 parts reducing data movement to the minimum required.
- **New:** Scaleform support for Ctrl+Key shortcuts (Ctrl+C, Ctrl+V, etc.).
- **New:** Added missing parts of the C++11 interface implemented on CryString.
- **New:** Added CryVariant.
- **New:** Rebuild the scan-code table when the input language changes.
- **New:** Entity System refactoring - No RenderProxy, No Physics Proxy.
- **Refactored:** Replaced putCharAscii with GetInputCharUnicode. It used to return non-ascii (current codepage) information.
- **Refactored:** Refactor properties by merging property handler and attributes into IEntityPropertyGroup that can be implemented once per entity component.
- **Refactored:** Remove boost variant from IReadWriteXMLSink.
- **Refactored:** Remove boost variant from CryNetwork.
- **Refactored:** Remove boost variant from IFlashUI.
- **Refactored:** Remove boost variant from IMovieSystem.
- **Refactored:** Remove boost variant from IFlowSystem.
- **Refactored:** Fixes for when not including Scaleform.
- **Refactored:** (DynArray) Implemented LocalDynArray. Optimised StaticDynArray and FixedDynArray. Removed ResizeStorage.
- **Refactored:**(SmartPtr) Replace non-thread safe return of count by NumRefs with Unique function which is thread safe as the calling thread must be holding the last reference.
- **Optimized:** Redo OPT_STRUCT macros to use plain struct data with auto member initialisation, instead of complicated TOptVar template. Can be used with constexpr.
- **Fixed:** Loading a full map (Woodland or Airfield) triggers an assert.
- **Fixed:** HTML support missing in CryGFxTranslator.
- **Fixed:** Added "Hide" property to GeomEntities (also added to geom entity FlowGraph node).
- **Fixed:** Support Sandbox mode for IsometricPathfinding template.
- **Fixed:** Prevent game projects from finding assets in the Engine's templates folder.
- **Fixed:** Engine containing references to two rope entities; RopeEntity has now been merged into the Rope Entity class.
- **Fixed:** Added missing main layer to project upgrade packages.
- **Fixed:** Entity archetypes will no longer be recreated everytime an Entity archetype is instantiated (this caused dangling pointers).
- **Fixed:** Fixed stencil-clear OoO execution.
- **Fixed:** Restore _CRY_ARRAY_H include guard to fix 3rd-party includes.
- **Fixed:** Fix rendering with GP=2 and MAP_DISCARD (i.e. DX11 and DXOrbis).
- **Fixed:** Shader precache will now also compile from text if the shader is not in the cache. This fixes crash-on-boot for PS4 when no cache is present. Note: Scaleform doesn't correctly display when booting without cache, but works with a populated cache.
- **Fixed:** Pick correct Viewport setup from renderer.
- **Fixed:** Crash on exit game mode in Sandbox.
- **Fixed:** bSkipRenderer as startup paramter. Allow runtime to run without renderer.
- **Fixed:** UIElements not loaded in CE 5.1.0.
- **Fixed:** Hidden in Game-Flag for GeomEntities does nothing.
- **Fixed:** Crash during Engine initialization when no PAK encryption is provided.
- **Fixed:** (TEXTBOX CURSOR) Cursor is not shown in textbox while editing.
- **Fixed:** Assert wasn't triggering after it was triggered for the first time.
- **Fixed:** Ref-counting of non-cacheable device objects.
- **Fixed:** Free constant buffer heap on exit.
- **Fixed:** Added DynArray unit tests to verify element construct/destruct/move behavior.
- **Fixed:** DynArray handles move-construction and swapping more correctly. Array storage classes now have dealloc instead of destructors fixing move behavior. Fixed alignment in HeapAllocator::Array. Added alignment asserts.
- **Fixed:** Behavior in CRenderProxy::GetRenderMaterial when part ID is not specified.
- **Fixed:** No state changed event, was sent by Physics when PhysicsProxy was created.
- **Fixed:** Starting multiplayer-game in GameLauncher triggers assert.
- **Fixed:** Preventing yasli from unintentionally stripping out symbols, additionally updated internal CMake to allow for updating the VS IDE when flags are changed.
- **Fixed:** Respawning on Airfield triggers a crash.
- **Fixed:** Multiple definition of friend in class GCC 4.9.3.
- **Fixed:** (3DEngine) The entity 'Fan' does not execute its scripts.
- **Fixed:** Geom Entities disappear when scaled.
- **Tweaked:** Support for PS4 controller on Windows when Orbis SDK present (MSVC 2015).
- **Tweaked:** Adjusted some of the CRY_ASSERT macro code to achieve code consistency.
- **Tweaked:** Array storage renaming and reformatting of single-line inline functions. Storage bases now implement begin and end. Removed slow MEMSTAT macros. Tweaked some internal typedefs. Replaced several derived types with type aliases.
- **Tweaked:** Changed Engine components initialization order.
- **Tweaked:** Guarded gEnv->pGame usage.
- **Tweaked:** Globally replaced gEnv->pGame->GetIGameFramework with gEnv->pGameFramework.
- **Tweaked:** Remove GetIGame & GetIGameFramework methods from ISystem.
- **Tweaked:** Remove warning if Entities.xml could not be found.

#### Common

- **Refactored:** Replace COMPILE_TIME_ASSERT macro with C++ 11's static_assert.
- **Refactored:** Replace STATIC_ASSERT macro with C++11's static_assert.
- **Refactored:** Remove unused GetPort... functions from IFlowGraph interface.
- **Refactored:** Remove metautils namespace and replace it with equivalents from the STL.
- **Refactored:** (CryEntitySystem) Standardized C++ and C# entity property registration into default IEntityPropertyHandler implementation.
- **Refactored:** Replace usage of gEnv->pGame with gEnv->pGameFramework->GetIGame to facilitate deprecation of IGame and IGameStartup.
- **Refactored:** Remove need for Windows specific HINSTANCE in system init params.
- **Refactored:** Introduce new CryGetCurrentModule define to unify use across platforms.
- **Refactored:** Remove need for Release function in entity components.
- **Refactored:** Remove implicit declaration of constructors and destructors when using ICryUnknown.
- **Fixed:** Fixed &&= to self in smartptr.
- **Fixed:** Don't rely on undefined behaviour of bit-find intrinsics.
- **Fixed:** Compilation warning in IAttachment.h.
- **Tweaked:** Make alloca address being aligned in addition to the size.
- **Tweaked:** IIndexedMesh.h requiring Cry_Geo.h include prior to itself.
- **Tweaked:** smart_ptr reset and swap get slightly faster when performing identity operation.
- **Tweaked:** Removed unnecessary IEditorGame functions.

#### System

- **New:** Expose ability to switch between VR tracking origin types - floor and eye level. This changes the default behavior from eye-level to floor-level - see hmd_tracking_origin to revert back.
- **New:** Updated detected CPU flags for new features, consolidated unecessary duplicated code and definitions. Log CPU features in one compact line. Remove obsolete SQRT_TEST code.
- **New:** Use Android SDK Platform 23.
- **New:** Added crymath::sign and signnz (replacing some sgn and sgnnz functions).
- **New:** Added SSE functions shuffle<> and get_scalar<> (replacing ExtractI32 and ExtractF32), to_v4<> for easier conversion, NumberValid overloads.
- **New:** Differentiated signed and unsigned int vector types, overloaded functions and operators. Added check_range asserts for conversions. Reverted to single SSE comparison mask type.
- **New:** Add CCryFile::WriteType helper function.
- **New:** Support starting Engine without an IGame implementation.
- **New:** Project Manager now sets 'sys_game_name' automatically - based on the cryproject file settings.
- **New:** (Linux) Use clang 3.8.
- **Refactored:** (Linux, Paths) Fixed where absolute filepaths were completely lowercase. The path to the Engine root should remain untouched though allowing users to store the Engine in folders with capitals in them.
- **Refactored:** Refactor HMD Manager to support external VR implementation registration.
- **Refactored:** Don't update Physics subsystem during async loading.
- **Refactored:** Moved some functions and tweaked solve_quadratic to work with SIMD types.
- **Refactored:** Moved random generator from per-module global to CrySystem to prevent the need for each module/plugin to reseed manually.
- **Optimized:** Replace CryLock usage of CriticalSection with SRW (Drop: Vista support).
- **Optimized:** Added more functions for SSE4. Replaced incorrect flag with CRY_COMPILER_SSE4.
- **Fixed:** Adjusted Plugin Manager to work with new mono library initialization.
- **Fixed:** Initialize variable sys_intromoviesduringinit.
- **Fixed:** Skip Scaleform helpers initialization in shadercache gen mode.
- **Fixed:** (Linux) Fix RenderThread stackoverflow. Increment stack form 128kb -> 256kb.
- **Fixed:** (CryMemory) Bucket allocator calculates the correct allocated size.
- **Fixed:** Added a check for dangling pointer (gEnv->pRenderer) when in dedicated mode.
- **Fixed:** Unable to sample on threads other than 'Main'.
- **Fixed:** (Android) Condition usage of geometry and compute shader.
- **Fixed:** Skip initialization of boot profiler in ShaderCacheGen mode.
- **Fixed:** (BootProfiler) Use correct type for thread id, sets CV_sys_bp_time_threshold to zero for runtime.
- **Fixed:** Fix symbol resolution for Xbox One.
- **Fixed:** Restored argument clamping for crymath asin and acos and removed redundant clamping in several calls. In SoundEngineUtil changed asin to asin_tpl to fix an FPE.
- **Fixed:** Export Memory Manager alloc functions from Launcher in monolithic builds so that dynamic dll's such as renderer can import them.
- **Fixed:** Win32 by disabling SSE - avoids alignment compile errors which are not as efficient anyway.
- **Fixed:** gcc by adding flax-vector-conversion option to WAF, making SSE casting behavior the same as on clang.
- **Fixed:** Read past end of buffer when log spam filtering is enabled.
- **Fixed:** (Orbis) SVOGI supported on PS4 and enabled for compilation.
- **Fixed:** (Orbis) Fixed 3D texture region update. Fixed support for huge pixel shaders.
- **Fixed:** FrameProfile WaitTimers were not reset correctly.
- **Fixed:** (Linux) Linux launcher attempts to load CryAction without a filename extension.
- **Fixed:** Crash during shutdown.
- **Fixed:** Possible crash in KD-tree construction.
- **Fixed:** Plugin loading aborting when a single plugin fails to load.
- **Fixed:** crashrpt static library build.
- **Fixed:** Correctly pass-through unicode input when using the in-game console while in game-mode of Sandbox. This previously passed a sign-extended 8-bit character (which would be invalid for non-ASCII characters).
- **Fixed:** (Xbox One) Game crashes/freezes due to memory leak.
- **Fixed:**(Clang) Clang 3.8.2 conformance changes.
- **Fixed:**(GNU 3.8 standard) error: static_assert failed "Allocator::value_type must be same type as value_type".
- **Tweaked:** (Android) Fix nightly build compilation of Android (now uses Clang, like WAF).
- **Tweaked:** set sys_streaming_use_optical_drive_thread to zero.
- **Tweaked:** set sys_float_exceptions to 0 by default.
- **Tweaked:** set sys_asserts to 1 by default (except in release mode).
- **Tweaked:** set r_displayInfo to 1 by default (release mode changes this to 0).
- **Tweaked:** set log_IncludeTime to 1 by default.
- **Tweaked:** set sys_PakLogInvalidFileAccess to 0 by default.
- **Tweaked:** Increment some stack sizes to prevent potential stack overflow by licencees.
- **Tweaked:** (Android) Hardcode gamezero to be loaded instead of GameSDK.
- **Tweaked:** Increase potential max worker/physics thread to logical instead of physical core count.
- **Tweaked:** (Android) Tweak LoadLibrary function to allow loading of dynamic library names without unix like library pre- or post fix. Such as game dynamic library.
- **Tweaked:** (BootProfiler) Enable Engine markers for frame_threshold mode.
- **Tweaked:** MemReplay 1.11.
- **Tweaked:** Reduced Cry_Math.h #include dependencies. Added many more SSE and non-SSE unit tests.
- **Tweaked:** Removed ENABLE_CRASH_HANDLER define, new CVar sys_enable_crash_handler.
- **Tweaked:** (Orbis) Set default value of r_multithreadeddrawing to 4.
- **Tweaked:** Remove warning if either editor.cfg or game.cfg did not exist.
- **Tweaked:**(Containters) Ensure VectorMap uses a "const" key in allocator's key/value std::pair.
- **Tweaked:**(JobManager) Move notify out of mutex protected block, this pattern makes the render-thread contend more than it should in certain unlucky scheduling cases.

#### WAF

- **New:** Use native VS 2015 Update 3 Android project support.
- **New:** SDL2 extension for Android.
- **New:** Allow Android projects to compile in non-monolithic mode.
- **New:** Android build with Clang (and GNU STL).
- **New:** Add protobuf support.
- **Refactored:** Drop VS Android Tegra support.
- **Fixed:** For monolithic builds, ensure a static library which is part of the build - is only every linked once into the monolithic host.
- **Fixed:** Don't build static libs that are not linked into a final dll/executable.
- **Fixed:** Explicitly specify 'gcc-4.9'/'g++-4.9' as the compiler.
- **Fixed:** Correct file_name_override handling when linking static libraries.
- **Fixed:** Show all used projects in VS solution.
- **Fixed:** Multiple project build. The second project build was ignored when analyzing use_module dependencies.
- **Fixed:** (WindowsLauncher) Include JSMN lib via use_module directive.
- **Tweaked:** Do not generate MSVS solution on Linux based machines.
- **Tweaked:** Show projects page as first page when opening WAF options.
- **Tweaked:** Note that redistribution of mfc140.dll from Windows/system32 is okay ([https://msdn.microsoft.com/en-us/library/ms235264.aspx](https://msdn.microsoft.com/en-us/library/ms235264.aspx)).
- **Tweaked:** Linux builds adding 'Wno-unused-result' to prevent error " ignoring return value of int scanf(const char*,...) declared with attribute warn_unused_result".

#### CMake

- **New:** Added CESharp projects to CMake build.
- **New:** Implement VS Android integration and drop VS Tegra support.
- **New:** Use MSVC default enabled state for /INCREMENTAL flag.
- **New:** Store solutions in solutions_cmake.
- **New:** Added native VS Android.
- **New:** Added CMakeSettings.json file for VS 2017 RC.
- **New:** Added CryLink to CMake.
- **New:** Added Buildbot and Jenkins scripts.
- **New:** Added Support for Linux (x64).
- **Refactored:** Renamed CRYENGINE_DIR in capital letters.
- **Refactored:** RemoveAndroid Tegra support. Use native VS Android instead.
- **Optimized:** Remove precompiled game template binaries and update scripts to compile them as part of the nightly builds.
- **Optimized:** Run 150 parallel jobs with ninja instead of 10.
- **Fixed:** Product version not shown in 'about' or 'properties' dialogs.
- **Fixed:** Added missing AudioSystem project.
- **Fixed:** Tools\CMake\toolchain\xboxone\XBoxOne-MSVC.cmake: renamed Game.exe -> GameLauncher.exe to fix "error APPX0703: Manifest references file 'Game.exe' which is not part of the payload.").
- **Fixed:** GCC: Don't use C++ warnings on C code.
- **Fixed:** On Linux, copy ncurses runtime files to output directory.
- **Fixed:** Ensure MSBUILD compiles projects in parallel.
- **Fixed:** Fix GCC flags.
- **Fixed:** Windows launcher target path.
- **Fixed:** Sandbox build being enabled in public builds where the EditorQt folder was not available.
- **Fixed:** Wwise Android CMake compilation.
- **Fixed:** Only copy ncurses libraries on Linux, not Windows.
- **Fixed:** Fixed CMake compilation for Sandbox.
- **Fixed:** (Physics) Add missing path in BuildEngine.cmake (merging artifact).
- **Fixed:** Workaround for CMake hackery not detecting Clang.
- **Fixed:** Ninja now also uses linker directly (to match MSBuild).
- **Fixed:** Static-library linking issues for monolithic configurations.
- **Tweaked:** Add PhysX compilation to buildbot/trybuild and jenkins/nightly.
- **Tweaked:** Don't deploy Mono files on every compilation, this will be handled by the build system.
- **Tweaked:** Cleanup Windows MSVC options.
- **Tweaked:** Allow multiple game projects being built at once.

#### Action General

- **New:** Automatically register scheduling profile for Actors and GameRules - Removes need for EntityScheduler.xml in GameZero / Blank game.
- **New:** Added new cl_ViewApplyHmdOffset CVar to support disabling default ViewSystem VR offset - in case a game decides to implement custom behavior.
- **New:** Expose IFlowSystem::HasRegisteredDefaultFlowNodes to support registering nodes after initial init.
- **Refactored:** Use existing CVar cl_initPlayerActor to control use of IActor during context establishment.
- **Refactored:** Unify game framework startup logic into new StartEngine method.
- **Refactored:** Move default view initialization to IGameObject::CaptureView instead of enforcing view system use for all games.
- **Refactored:** Remove need for cl_initClientActor CVar by ensuring consistent Engine behavior when Actor is/is not available.
- **Fixed:** Monolithic build behavior for plugin/game flownodes.
- **Fixed:** Framework extensions not being released in inverse order of creation.
- **Fixed:** Bad memory access in AnimatedCharacter.
- **Fixed:** Default GameSessionHandler::ShouldCallMapCommand implementation is prevented from working when CryLobby is disabled.
- **Fixed:** Removed assert for orthonormal vehicle matrix - because scaling is allowed.
- **Fixed:** Extension removal on UI files.
- **Fixed:** FlowGraph resetting in Editor.
- **Fixed:** Removed unneeded assert, which has been triggering on first click.
- **Fixed:** autoexec.cfg was no longer executed when started from within Sandbox.
- **Fixed:** Broken manual frame step and moved code from game to CryAction.
- **Fixed:** Loading of fixed timestep length in demo recorder.
- **Fixed:** Game not being initialized when the game module was monolithically linked into the Launcher. This caused weird issues due to uninitialized state, specifically weapons/items not appearing in GameSDK.
- **Fixed:** AudioListener entity attempts to serialize itself despite ENTITY_FLAG_NO_SAVE flag being set.
- **Fixed:** Wrong output port data type in EnterVehicle flownode.
- **Fixed:** Crash for undocking FragmentEditorPage in Mannequin.
- **Fixed:** CActionMap::IsActionInputTriggered blocks input if gEnv->pTimer goes back in time (e.g. because of serialization) and onHold is 1 in the action map.
- **Fixed:** Crash on shutdown.
- **Fixed:** Game warning being issued if Scripts/GameObjectSerializationOrder.xml did not exist.
- **Fixed:** Crash related to material effects in CryAction.
- **Fixed:** Return hardcoded local player id on GetClientEntityId as a fallback.
- **Fixed:** Removed an indirect assert call requiring actions not to contain invalid fragment IDs at the point of queuing and installing, which is a perfectly supported scenario.
- **Fixed:** Removed custom damage handling implementation from CVehiclePartTread to reuse base class facilities. Removed damage value checks from CVehiclePartBase state changing logic to respect implementation details of derived classes. Removed other redundant methods.
- **Fixed:** Disabled CAnimatedCharacter runtime tests.
- **Fixed:** Removed dependency of the MannequinObject on the legacy lua script. Moved user properties to IEntityPropertyGroup. Tweaked CMannequinObject to directly inherit from IEntityComponent.
- **Fixed:** Physics not working in GameTemplates without a gamedll.
- **Fixed:** Adapted CVehiclePartAnimatedJoint to work with new CGA animation update timings. Removed a now redundant update call from CVehicleSeatActionRotateTurret.
- **Tweaked:** Added warning message when specified game dll couldn't be loaded correctly.
- **Tweaked:** Removed obsolete CameraSource implementation in CryAction.
- **Tweaked:** ActionListener fix to be able to listen to a OnHold Event.
- **Tweaked:** CFlowNode_InputActionListener: removed redundant string construction.

#### FlowGraph

- **New:** Added new FG node to do pattern matching based on wildcards.
- **New:** PlayAnimation node supports custom speed multiplier input.
- **New:** Added "Speed" property to "PlayAnimation" FlowGraph node.
- **New:** Smoothing of animation transitions on enabling & disabling of targ chain.
- **New:** Update several nodes to let them take a joint ID as input, instead of forcing Designers to go through joint names (useful as raycast results already give them joint IDs).
- **New:** Added an input to PlayAnimation node to specifiy what percentage constitutes AlmostDone.
- **New:** Add new node 'Math:SetInteger'.
- **New:** Add cross and dot product operations to the Vec3:Calculate node.
- **New:** (FG Modules) Edit order of module ports with drag and drop.
- **New:** (FG Modules) Practical way to handle instance IDs.
- **New:** Add input port selector for Module names.
- **New:** (FG Modules) New node for getting count of active module instances.
- **New:** Global Instance Controller for FlowGraph Modules.
- **New:** FlowGraph modules redesign.
- **New:** Remove the need for game projects to contain FlowGraph substitutions and black list xml files.
- **Refactored:** ActorPlayerLink node is broken - Marked as obsolete.
- **Refactored:** 'Goto Module Definition' is now on the context menu for call nodes and any node port that is a module name.
- **Refactored:** Revised debug display for FlowGraph modules.
- **Refactored:** FlowGraph modules that can constantly output without requiring it to finish.
- **Optimized:** Rearrange members of the CFlowData structure so that they are more padding friendly.
- **Optimized:** (Modules) Preallocate module ports and separate inputs from outputs.
- **Optimized:** (Modules) Do not rebuild port configuration at runtime as it can only change at edit time.
- **Fixed:** Crash in FlowGraph when nodes try to output when they should be deleted due to badly implemented clone methods.
- **Fixed:** Critical Flowgraph-error on non-Windows platforms.
- **Fixed:** Crash on level exit caused by FG modules.
- **Fixed:** Typo in the FG module Input port validator.
- **Fixed:** Masking out node description texts for FG modules to reduce release executable size.
- **Fixed:** Global Call Nodes output '-1' instead of the invalid instance ID.
- **Fixed:** Global control node registry, when call nodes are changed at runtime or used from inside a module that gets deleted.
- **Fixed:** General fixes and tweaks to FG modules.
- **Fixed:** Double click on Call Node; selects the associated entity and not the module graph.
- **Fixed:** Update initial connections for a module default initial graph.
- **Fixed:** Call Nodes outputing all ports on successful finish.
- **Fixed:** Issues with FG module node InstanceCountListener.
- **Fixed:** Accept only valid port names for FG modules.
- **Fixed:** Input:ActionMaps:ActionListener unregister properly to prevent crashes when the node is destroyed e.g. from modules.
- **Fixed:** Substitutions.xml is not working.
- **Fixed:** GetPortString function and its uses.
- **Fixed:** Entity input type conversion on the entity FlowGraph nodes.
- **Fixed:** Set force update flag properly on PlayAnimation FG Node.
- **Fixed:** Force update entity if PlayAnimation FG node force skeleton update.
- **Tweaked:** Animations:PlayAnimation now compatible with AISequence.
- **Tweaked:** FG Modules - tweak the modules debug screen so that it is visible on PS4.

#### Movie System

- **Fixed:** Incorrect removal of sys_intromoviesduringinit.
- **Fixed:** Assertion failure when playing two animations with one animation being looped.
- **Fixed:** All cutscenes in Woodland that don't work.

#### Game

- **Refactored:** Move default actionmap initialization from CryAction to GameSDK.
- **Fixed:** Assert triggered in multiplayer after death on custom map without spectator point.
- **Fixed:** Assertions in Vehicle/VehicleSeat.
- **Fixed:** Assert in Lobby UI when invoking the Lagometer.
- **Fixed:** (MP) Assertion failed when flying around in helicopter.
- **Fixed:** Ladders could not be used from the top.
- **Fixed:** (MP) Other players are not rotating by default.
- **Fixed:** 'Map' command from autoexec.cfg gets overwritten and 'example' map is loaded on startup.
- **Fixed:** Crash on shutdown after visiting the multiplayer lobby.
- **Fixed:** Not possible to use vehicles in multiplayer.
- **Fixed:** Not possible to move around in Airfield.
- **Fixed:** Assertion when shooting tank-mg in multiplayer.
- **Fixed:** Assertion and crash when getting killed in multiplayer.
- **Fixed:** Various multiplayer asserts in GameSDK.
- **Fixed:** (MP) Game assertions when using weapons, VehicleSeats.
- **Fixed:** (MP) Assertion on player revival.
- **Fixed:** Player teleported to the car's position when jumping out of a moving HMMWV.
- **Fixed:** Threshold for OrthonormalRH check to avoid assert.
- **Fixed:** Firing a tank's secondary weapon for a short while will play machine gun-sound forever.
- **Fixed:** FG node "Minimap:EntityPos": could handle only one entity, but was used for more than one, thus erroneously repurposing m_entityId and causing asserts to fail.
- **Fixed:** FlowGraph is broken in GameZero.
- **Fixed:** GameSDK shutdown behavior.
- **Fixed:** On stereo output CVar on change functor not being unregistered.
- **Fixed:** Engine outputting errors if game did not provide Libs/UI/TexturePreloads.xml.
- **Fixed:** Removed GeomEntity as it's now part of the CryDefaultEntities plugin.
- **Fixed:** Cutscene with option "disable UI" causes multiple asserts to be fired.
- **Fixed:** Exiting airfield crashes on Xbox One (InputActionListener flownode could cause the Engine to crash when trying to access outdated entity info).
- **Fixed:** AI markers on the HUD were not added reliably.
- **Fixed:** Interaction popup shown while already interacting.
- **Fixed:** (Sandbox) Weapon of AI agent doesn't vanish anymore after getting shot.
- **Fixed:** Properly shutdown the game rules system when resizing the terrain.
- **Fixed:** Fix potential use of dangling action controller pointer when items are destroyed.
- **Fixed:** Assertion in AfterMatchAwards.
- **Fixed:** Effects placed by the tornado entity were rendering twice - was making asserts in the ComputeVertices job.
- **Fixed:** Sprinting with grenades in third person causes the HUD to move.
- **Tweaked:** Build Android non-monolthic (WAF).
- **Tweaked:** Remove majority of logic from GameZero startup.
- **Tweaked:** Make the game responsible for registering its game flownodes.
- **Tweaked:** Load GameZero example map without warnings.

### C#

#### C#.Core

- **New:** Extend MathHelpers.
- **New:** Actionmap handling.
- **New:** Implement domain serializer for future use in reloading.
- **New:** Support serializing all static fields in an assembly.
- **New:** The Core framework now automatically generates debug databases on build.
- **New:** Add DebugDraw helper for easily drawing primitives and text over time (wrapper of IPersistantDebug).
- **New:** Implement managed Vector3 class - replaces use cases of auto-generated Vec3 class that always invoked C++ for each expression.
- **New:** Implement managed Vector2 class - replaces use cases of auto-generated Vec2 class.
- **New:** Implement managed Quaternion class - replaces use cases of auto-generated Quat class.
- **New:** Implement managed Angles3 class.
- **New:** Implement managed Vector4 class - replaces use cases of auto-generated Vec4 class.
- **New:** Implement managed Matrix3x4 class - replaces use cases of auto-generated Matrix3x4 class.
- **New:** Build C# assemblies with CMake and Mono compiler.
- **New:** Add NUnit to SDKs bootstrap.
- **New:** CryEngine.Core assembly can now see the internals of CryEngine.Common in order to cut down on reflection usage.
- **New:** Expose ability to add internal calls manually instead of using SWIG.
- **New:** Re-integrate C# plugin reloading - was disabled with 5.2.0 release due to plugin system refactor.
- **New:** Expose WIP CryMono API to CryCommon.
- **New:** Implement managed exception handler dialog.
- **New:** C# Core framework is now added as a regular external project to the Visual Studio CMake solution.
- **New:** Exceptions are now thrown when methods fail to be found in the native IMonoClass implementation.
- **New:** Add support for invoking managed methods by method description via the IMonoClass and IMonoObject interfaces.
- **New:** Implement script reloading 2.0 - serializes all objects in app domains before unloading and then restores after having reloaded the modified assemblies. This allows for reloading C# code during gameplay, instead of being thrown out and restarting the game loop as if the Launcher had been restarted.
- **Refactored:** Minor cleanup.
- **Refactored:** Refactor entity system to follow.NET core guidelines.
- **Refactored:** Format core library based on.NET core guidelines.
- **Refactored:** Clean up IEntityComponent implementation.
- **Refactored:** Remove Logger class - use generic Log functions instead.
- **Refactored:** Unify handling of managed classes listening to C++ events - allows for easily unregistering these for assembly reloading.
- **Refactored:** Refactor Camera to be a static class instead of a component.
- **Refactored:** Move Application.UIPath to UIElement.DataDirectory.
- **Refactored:** Move Application.DataPath to FileSystem.DataDirectory.
- **Refactored:** Split out entity logic into one file per type.
- **Refactored:** Split out System.cs into one file per type.
- **Refactored:** Remove Application component - prefer logic in ICryEnginePlugin instead.
- **Refactored:** Move scene and component setup to UI namespace - now only used for the C# UI solution.
- **Refactored:** Adapting Sydewinder to latest Core code.
- **Refactored:** UI System refactored to be based on virtual functions rather than reflection.
- **Refactored:** Moved UI System from Core to Core.UI project.
- **Refactored:** Cleaned up using statements.
- **Refactored:** Make SampleApp and Sydewinder run with latest code.
- **Refactored:** Rework entity handling in order to fix C# build after entity system changes.
- **Refactored:** Removed C++ GameMono module - this is no longer required as running without a game dll is now possible.
- **Refactored:** Start wrapping MonoDomain functionality.
- **Refactored:** Wrap app domain usage into new CAppDomain class.
- **Refactored:** Start unifying C++ and C# plugin behavior.
- **Refactored:** Moved domain handling entirely from the managed side to native CryMonoBridge.
- **Refactored:** Remove need to compile CryEngine.Core for each C# project.
- **Refactored:** Optimize Web Launcher Engine download by moving Mono dependencies out to Engine directory, instead of in duplicating into every binary directory.
- **Refactored:** Refactor IMono* interfaces, automatically destroy temporaries.
- **Fixed:** Sydewinder & SampleApp project adjustments for the new plugin system.
- **Fixed:** Sydewinder would not exit gameMode in Sandbox on UI Click.
- **Fixed:** LevelLoaded now calling separate event. Called OnGameStart before.
- **Fixed:** Launcher did not call OnGameStarted.
- **Fixed:** Library initialization.
- **Fixed:** Managed entity initalization.
- **Fixed:** Mono not being unloaded on shutdown.
- **Fixed:** Managed library dependencies not being automatically loaded before fully initializing an assembly.
- **Tweaked:** Spelling of "extention" -> "extension".
- **Tweaked:** Serialize/deserialize using binary instead of strings.
- **Tweaked:** Moved CryMonoBridge and CryEngine.Core projects into new CryMono solution category.

## Graphics and Rendering

#### Renderer General

- **New:** Implemented shader sources loading from game folder.
- **New:** Expose GpuInfo from Renderer.
- **New:** Dynamic instancing for new rendering pipeline.
- **New:** Support enabling VR at runtime.
- **New:** Add barrier fusion CVar.
- **New:** Added offset UpdateBuffer API to the device buffer manager.
- **New:** Added minimum precision types to shader parser.
- **New:** Enable debug-layer CVar for OpenGL.
- **New:** Added support for GL4.5.
- **New:** Added ResourceSet multi-buffering for textures.
- **New:** Implement multi-threaded draw support for GNM.
- **New:** Ported water volume, ocean, water volume caustics, and ocean caustics to new graphics pipeline.
- **New:** Implement hmd_resolution_scale CVar from Climb and Robinson.
- **New:** Expose functionality to get Steam VR play area from the IHmdDevice interface.
- **New:** Add support for Gles3.1.
- **New:** (Shaders) Implemented shader extensions, file support from GameShaders folder.
- ****Refactored**:** Ported water volume normal gen to new graphics pipeline.
- **Refactored:** Removed function names from Runtime.ext because those functions no longer use %_RT_OCEAN_PARTICLE.
- **Refactored:** Remove deprecated prism object.
- **Refactored:** Simplify permanent renderobject creation.
- **Refactored:** Remove extrude option from rendermesh debug drawing - use drawinfront option instead.
- **Refactored:** (SVOGI) Ported to new pipeline.
- **Refactored:** Unify SetConstant* interface between CFullscreenPass and CComputeRenderpass so they can be used interchangeably.
- **Refactored:** Removed VBuffer and IBuffer implementations from DeviceBufferManager (deprecated and unused).
- **Refactored:** Devirtualizing DX11 interfaces and removing MS DX11 inheritance for DX12 PC, Durango, Vulcan, etc.
- **Refactored:** Added support for tiled forward shading of opaque objects in new pipeline.
- **Refactored:** Explicit constant buffer + multigpu dual stereo support for sun shafts.
- **Refactored:** Added buffer support to CFullscreenPass.
- **Refactored:** Remove some unused stencil passes.
- **Refactored:** Removed the rendering functionalities for old graphics pipeline which are fog, volumetric fog, volumetric clouds, water ripples, water volume, ocean, and deferred water volume and ocean caustics.
- **Refactored:** (Shaders) Remove ORBIS hacks from shader sources as they are no longer needed.
- **Refactored:** (Renderer) Now has it's own independent macro to control presence of Scaleform rendering feature. Thus, it no longer requires knowledge of Scaleform configuration to be injected by WAF/CMake.
- **Refactored:** (SVOGI) Textures usage converted into independent Samplers and Textures setup; Cleanup and duplicated code reduction of CPU side code.
- ****Refactored**:** Implemented simple RenderElement base class.
- **Refactored:**(GNM) New shader compiler (V030), hacks from DXOrbis at compilation time are now gone. Partial support for SM6.0.
- **Optimized:** Create[Vertex|Index]StreamSet no longer allocates and frees on the common path.
- **Optimized:** Implement fast path for multi-buffered resource-set rebuild.
- **Optimized:** (Shadows) Restrict cached shadow caster rendering to casters who are inside shadow hull when update strategy is eFullUpdateTimesliced.
- **Fixed:** Wrong shader technique is returned from CShader::GetTechnique when passing TTYPE_GENERAL as a requested technique.
- **Fixed:** Assert when partly opaque and transparent object gets drawn in forward pass.
- **Fixed:** %_RT_COMPUTE_SKINNING is assigned to the mask value which is assigned to %_RT_DEBUG1.
- **Fixed:** Choose PlaneSlice 1 to access green component of DepthStencil views (Device Lost after W10 Anniversary Update).
- **Fixed:** Missing shader-item/resource ref-counting.
- **Fixed:** Excluded GI shaders from offline shader compilation for unsupported platforms.
- **Fixed:** Improved multi-gpu vr support for SSDO.
- **Fixed**: Support for r_HDRBloomQuality 1.
- **Fixed:** Half-res SSDO and improved quality.
- **Fixed:** SSDO bent normal.
- **Fixed:** Depth writes being enabled on emittance forward pass.
- **Fixed:** mip level selection in GetEnvironmentCMap.
- **Fixed:** Various issues with hair rendering.
- **Fixed:** Invalidate permanent render objects in case rendering is aborted.
- **Fixed:** Crash due to division by zero.
- **Fixed:** D3DRendPipeline: bad memory access in old graphics pipeline.
- **Fixed:** Fixed out-of-memory-bounds access and potential driver crash while uploading material constants under D3D11.0.
- **Fixed:** Memory leak when using GP=0.
- **Fixed:** Add missing tokens eT_UIName, eT_UIDescription to!defined(SHADER_REFLECT_TEXTURE_SLOTS) codepath.
- **Fixed:** GPU Particles cleanup happening before right eye rendering.
- **Fixed:** (Render) Graphic issues while zooming with pistol on VR_Demo.
- **Fixed:** (Shadows) Fix vertex shader depth output for hair shadow gen.
- **Fixed:** Nearest rendering when multi-threaded drawing.
- **Fixed:** Fog rendering to support single pass stereo rendering.
- **Fixed:** FogVolume shader to support single pass stereo rendering.
- **Fixed:** Transparent object flickering due to FogVolumes.
- **Fixed:** Recursive renderpass interfering with main scene rendering for stereo.
- **Fixed:** Adjusted constant buffer alignment for particles.
- **Fixed:** Object deconstruction from circumventing ref-counting on assignment.
- **Fixed:** Always recreate compute skinning buffers as they are created as immutable (and updated from multiple threads).
- **Fixed:** (Shadows) Collect nearest object bounding boxes during RenderView writing phase to avoid race conditions with entity system update.
- **Fixed:** Fixed missing specular multiplier in per-view constant CV_SunColor.
- **Fixed:** nullptr access when binding water ocean resources.
- **Fixed:** Missing mgpu adjustment for r_graphicspipeline=2 shadowmask.
- **Fixed:** Input layout mismatch in ShadowMaskGen: Plain fullscreen tri is enough here.
- **Fixed:** Deferred decals in multigpu stereo.
- **Fixed:** multigpu stereo stencil passes.
- **Fixed:** Incorrect offset/size passed for constant buffer binding (this only affects Razor display since offset was always 0 and larger size does not affect result).
- **Fixed:** Uninitialized member variables of SViewInfo.
- **Fixed**: pload camera dependent data for deferred shading in world space, so multi gpu stereo rendering can correctly apply camera position.
- **Fixed:** Do not call profiling code in release builds.
- **Fixed:** mem leak and mem override in FX_PipelineShutdown.
- **Fixed:** Water fog is rendered before water surface when the camera is under the water.
- **Fixed:** Duplicated rendering of terrain layers.
- **Fixed:** The deletion of old ripple debug infos.
- **Fixed:** Clamp resource unit/slot limits by built-in limits.
- **Fixed:** Assert triggered when changing CVar r_StereoMode from Post Stereo to Dual Rendering.
- **Fixed:** Out of bounds array access in InitShaderReflection function.
- **Fixed:** Missing initialization for m_bCustomRenderElement.
- **Fixed:** Reset core command list after Scaleform buffer update to avoid issues due to potential command list split.
- **Fixed:** (Render) Enabling Total_Illumination_v2 will make dissolving of shadows choppy.
- **Fixed:** Prevent calling IsRecursiveRenderView from CD3D9Renderer::SetCamera.
- **Fixed:** Potential memory leaks.
- **Fixed:** Reset mip count when changing size of texture.
- **Fixed:** (XONE Renderer) Rendering issues/flickering.
- **Fixed:** Crash when stopping Flash loadtime playback when no commands had been requested.
- **Fixed:** VR social screen behavior not functioning as expected for HTC Vive and Oculus Rift.
- **Fixed:** Wrap all SVOGI code in #ifdef.
- **Fixed:** Various bug fixes - initialization and normalization.
- **Fixed:** Incoherent resource-state after mip-mapping.
- **Fixed:** Removed assert which is too conservative.
- **Fixed:** Check for SRenderPipeline::m_pSunLight is not needed in new pipeline.
- **Fixed:** Crash happens at CREImposter::ReleaseResources.
- **Fixed:** Make sure SPermanentRendItem::m_pCompiledObject is only updated by one thread.
- **Fixed:** Unintended matrix is used to render water volumes to caustics texture.
- **Fixed:** constantbuffer dirt-flag assignment.
- **Fixed:** Using constantbuffer after freeing it.
- **Fixed:** Missing cache clear when resetting CPrimitives.
- **Fixed:** Extra bones mapping being freed multiple times.
- **Fixed:** Skinning buffer allocated IMMUTABLE which can't be updated.
- **Fixed:** (3DEngine) Too many shader constants in GI shader.
- **Fixed:** Get CV_SunLightDir, CV_SunColor, CV_SkyColor from per frame constants to avoid race condition with 3DEngine.
- **Fixed:** Add previous frame camera to RenderView.
- **Fixed:** Prevent water being drawn when not all input resources are available (can occur in frame 0).
- **Fixed:** Command-list scheduler deadlock when running at very fast frame-rate.
- **Fixed:** Adjustment to make Performance build compile.
- **Fixed:** Omit compiling code which is not available in Release builds.
- **Fixed:** Fix over zealous assert in CConstantBuffer::ReturnToPool. No need to call CDeviceResourceSet::Clear in destructor.
- **Fixed:** Don't release textures used by new graphicspipeline on CVar changes.
- **Fixed:** Clear cached shadow primitives on shadow CVar changes.
- **Fixed:** (XONE) Serious render issues.
- **Fixed:** Resource-states being invalid in frame 0.
- **Fixed:** Dynamic clear rect count in Clear pass to avoid overflow.
- **Fixed:** DeviceResourceSet texture callbacks not registered when cloned.
- **Fixed:** (XONE UI) Highlighted menu items and buttons are orange.
- **Fixed:** (Shadows) Update cached shadows when vegetation is moved.
- **Fixed:** Crash on level loading, Incomplete Compiled Render Object may have null material resource set.
- **Fixed:** Fix barriers for resources being used by multiple command list types (originally from dev_deviceobjects_refactor).
- **Fixed:** Implemented texel density visualization in new pipeline.
- **Fixed:** Fix assert on loading meshes with chunks where the chunk index buffer offset is >= 60000.
- **Fixed:** Moved cleanup/freeing of perm. objects to EndFrame to prevent free-of-in-use problem.
- **Fixed:** Fixed r_shownormals and r_showtangents.
- **Fixed:** Skip custom render elements in secondary Viewports.
- **Fixed:** Fixed startup crash when VR is enabled and no HMD is available.
- **Fixed:** Fixed rain and snow entity rendering issues when recursive rendering is active.
- **Fixed:** Temporarily disabled broken r_measureoverdraw to prevent crash; it requires a proper implementation in the new pipeline.
- **Fixed:** Fixed shader compilation errors.
- **Fixed:** Make sure compute skinning instance data is not immediately released when CComputeSkinningStage::Execute is called multiple times per frame.
- **Fixed:** Make sure transparent objects are put into renderlist for transparency.
- **Fixed:** Bounced light of shadow casting light entities is darker than bounced light by not-shadow casting light.
- **Fixed:** (XONE) Walk around in vr_demo crashes.
- **Fixed:** Filter out NaNs during luminance measurement.
- **Fixed:** Fixed clip volume stencil reference for objects, so that tiled forward shading works in vis areas.
- **Fixed:** Fixed an assert triggered when moving around maps.
- **Fixed:** Finish any outstanding rendering tasks before changing sys spec.
- **Fixed:** (Shadows) Fix shadow gen from hair when hw depth bias is used.
- **Fixed:** Also update PSO state when not rendering a scene (i.e. menu). This fixes black screen during async compile from persisting when using remote compiler (i.e. consoles).
- **Fixed:** Dangling pointer access in CClearRegionPass due to primitive vector realloc.
- **Fixed:** Tiled shading on hair and a related general depth bias issue.
- **Fixed:** Artifacts when Volumetric Clouds is activated.
- **Fixed:** For multires.
- **Fixed:** Broken LOD dissolve.
- **Fixed:** Changing 'Sun color' in EE.
- **Fixed:** Multi-threaded drawing - crashing PS4.
- **Fixed:** Zero-sized scissor rect in partial resolves that can happen during resizing the Editor Viewport (object screen bounds get computed with previous Viewport dimensions while renderer has the new ones).
- **Fixed:** Crash when running OpenGL-driver.
- **Fixed:** Removed animated sequences from streaming (unsupported).
- **Fixed:** Added animated sequence handling for resource-sets and new pipeline.
- **Fixed:** Don't validate number of CGpuBuffer copies by default.
- **Fixed:** FlashUI: Made uielement name lookup case-insensitive.
- **Fixed:** LensFlares: Occlusion queries are only valid for the main viewport. Ignore them for other viewports.
- **Fixed:**(WaterVolume) Fixed water volume surface tearing when the camera is near the water volume surface.
- **Tweaked:** Allow empty resource-sets to be built and consider them valid. This fixes clip-volume primitives being discarded inappropriately.
- **Tweaked:** Disallow shader compilation by default for non-pc platforms.
- **Tweaked:** Set r_ShaderCompilerServer to 0.0.0.0 by default.
- **Tweaked:** Set r_ShadersAsyncActivation to 0 by default.
- **Tweaked:** Set r_ShadersAsyncCompiling to 3 by default.
- **Tweaked:** Renamed CV_r_AntialiasingModeEditor to r_AntialiasingModeEditor.
- **Tweaked:** Added always visible silhouette rendering option.
- **Tweaked:** (Shaders, Scaleform) Rearranged uniform buffer layout to be adjustable by ARB_enhanced_layouts.
- **Tweaked:** Show "not found" texture when.ui element is with path.
- **Tweaked:** Enabled volume based tiled shading by default.
- **Tweaked:** Removed unused texture streamer CVars.
- **Tweaked:** Allow command-list forfeit to consume nullptrs.
- **Tweaked:** The default backend for PS4 is now GNM backend.
- **Tweaked:** Android: OpenGL: Don't use BC6H and BC4 on texture atlases as not supported use eTF_EAC_R11 instead.
- **Tweaked:** Android: OpenGL: Enable EXT_texture_cube_map_array extension.
- **Tweaked:** Move duplicate VR WrapD3DRenderTarget function to CD3DStereoRenderer.

#### OpenGL

- **New:** Added WAF scripts for HLSLcc.
- **New:** Added support for RWBuffer atomics.
- **Fixed:** refcounting on framebuffer attachments.
- **Fixed:** Map requiring a valid size.
- **Tweaked:** Revert removal of default uniform buffer layout.
- **Tweaked:** Changed constantbuffer layout to packed (no auto-padding).

#### Volumetric Clouds

- **Fixed:** Volumetric Clouds texture can be changed only once.
- **Fixed:** Screen space cloud blocker not working due to a mismatch of constant buffer layout.
- **Fixed:** Unstable cloud shadow.

#### 3D Engine

- **New:** Decal surfacetype physicalization.
- **New:** Reintroduce CTimeOfDay::SetVariableValue functionality.
- **Refactored:** Removed non existing CVars from *.cfg files.
- **Refactored:** Removed obsolete e_Dissove functionality in favor of new e_LodTransitionTime solution.
- **Refactored:** Rework road serialization to avoid full mesh regeneration in Launcher - saves lots of time spent loading especially on slower CPUs. More data is committed to disk, but plenty of time is saved from recalculating the road mesh(es).
- **Optimized:** SSE2+AVC support for WindGrid updates.
- **Optimized:** Reduced the number of unnecessary software occlusion culling tests.
- **Optimized:** Moved default compute_tangents code to base SplineKey.compute_tangents. No longer always called by Spline.comp_deriv.
- **Fixed:** Issue with wind area sampling.
- **Fixed:** Supported GI outside of terrain bounds.
- **Fixed:** (Renderer) Zooming out of heightmap will display it incorrectly.
- **Fixed:** e_CoverageBufferCullIndividualBrushesMaxNodeSize was changed to non-constant. Reflects changes in CVar.
- **Fixed:** (ASSERT) Loading vegetation objects to VE: L: 400; MatMan.cpp.
- **Fixed:** When placing two maritime properties and browsing for the other one.
- **Fixed:** Heap corruption in Physics if deleting phys ents before 3D post render end.
- **Fixed:** Cubemap cache was picking cubemaps from hidden layers.
- **Fixed:** EnvironmentPreset bump preset version.
- **Fixed:** Corrupted terrain layers when material is modified in Editor.
- **Fixed:** Missing terrain layers.
- **Fixed:** (SVOGI) Troposphere, fixed voxelization LOD logic, fixed too bright secondary bounces.
- **Fixed:** Several crashes in instances streaming.
- **Fixed:** Crash for levels without terrain.
- **Fixed:** (ClipVolume) Simultaneous access to m_lstRenderNodes.
- **Fixed:** Unaligned memory access when using SSE.
- **Fixed:** Compiling error with e_CoverageBufferCullIndividualBrushesMaxNodeSize CVar.
- **Fixed:** (Renderer) Textures of HMMWV not displayed depending on distance (LOD dissolve is also activated for entities now).
- **Fixed:** (ASSERT) Checking AutoMerged in Vegetation Settings causes Assertion Failure.
- **Fixed:** (LAUNCHER) Assertion Failure while playing Head demo.
- **Fixed:** (SPAM) Loading a map in the Launcher shows pre-cache notification spam.
- **Fixed:** Crash in dedicated server due to the unavailable renderer.
- **Fixed:** Log spamming after creating a cloud entity because of uninitialized data.
- **Fixed:** Vegetation is not rendered on PC and consoles.
- **Fixed:** (TE) Sculpting, painting terrain and generating terrain texture without high quality textures causes render issues.
- **Fixed:** Crash using 'clear' from the context menu in the geometry field causes crash.
- **Fixed:** (HMMWV) Wheels do not switch LoDs. Now all entity slot a separate render node, CharacterRenderNode fixed to calculate LoD Distances correctly).
- **Fixed:** GeomCache-entity does not work.
- **Fixed:** (QT/MFC) Shadows of GeomEntity and Brush groups remain visible.
- **Fixed:** (VR) user.cfg file doesn't trigger VR mode.
- **Fixed:** Broken SVOGI voxelization, fixed analytical proxies not working together with voxels.
- **Fixed:** SVOGI memory corruption.
- **Fixed:** (MP) Let your Avatar be killed several times triggers assert.
- **Fixed:** Crash activating automerge feature on dead tree assets crashed the Editor.
- **Fixed:** Placing several GeomChache entities will make them look blurred.
- **Fixed:** Breakable objects ignoring hide masks after merging.

#### Particles

- **New:** (SecondGen) OnCollision feature.
- **New:** ConfigSpec modifier - allowing to scale particle characteristics based on spec.
- **New:** Feature Component category with EnableIf, SpawnIf and EnableByConfig features.
- **New:** Implemented indoor and water visibility options in Appearance Visibility feature.
- **New:** GPU Sprites sort order.
- **New:** Location Noise on GPU Particles.
- **New:** Implemented Spiral effector.
- **New:** Added Restart option to all spawn features that have duration - allows to create bursts and pulses.
- **New:** (GPUParticles) Moving all GPU only features to GPU Particles category.
- **New:** Moved MoveRelativeEmitter from Velocity to Motion category.
- **New:** Aadded align camera option to angles align velocity and parent features.
- **New:** Project Terrain and Project Water features.
- **New:** Feature Angles Align implementation.
- **New:** View Angle time source for modifiers.
- **New:** Particles profiler revamp.
- **New:** Location bind to camera feature.
- **New:** Implemented SpawnParams.TimeScale. Refactored Set/GetSpawnParams to not require storing entire SpawnParams structure. Reduce dependency on pfx1 ParticleParams.h.
- **New:** Added 2D and 3D angular velocity damping and multiplier to motion physics.
- **New:** SpawnCount can now create instant or continuous effects. Disabled Duration = infinite - as with other Spawn features. Default Duration is still 0.
- **New:** 2D and 3D particle spinning is integrated in Motion Physics now instead of feature angles.
- **New:** Affected by Fog tick box in Appearancde Lighting.
- **New:** Added Feature Velocity Compass.
- **Refactored:** TParticleHeap::Arrays no longer require stride padding (handled with alignment). Infinite emitter and lifetime values now use actual float infinity, all calculations are correct.
- **Optimized:** Feature meshes and feature light render do not have to lock particle updates or octree traversal since they are now deferred. Emitter color coding to better identify in the profiler display. Profiler display now has bars showing the runtime and execution time of particles and a list of the 8 most expensive components. Added e_particlesprofiler CVars (1) display, F start outputing *.csv files. CSV file output is not controlled by CVars. Added particle counts back to statoscope. Removed GPU particles profiler - to be added later, but for now separated from CPU particles.
- **Optimized:** Vectorized angular momentum.
- **Optimized:** Disabling light volumes on particles without albedo.
- **Fixed:** Some spawn features would not spawn particles right after the emitter was enabled - they would wait an 'amount' of time before spawning the first particle.
- **Fixed:** Fixes to SpawnDensity and GetSpatialExtents: Feature now defaults immortal, density no longer improperly squared. Instance data now properly mapped to parent particle ids. Added Extents for LocationOffset. Small fixes to LocationOmni.
- **Fixed:** SpawnFractions clamped to 1, rather than wrapped - fixes overflow with more accurate rcp.
- **Fixed:** Some pfx1 conversion errors: MotionPhysics when needed, VelocityOmniDirectional detection.
- **Fixed:** DragFastIntegral to be second-order (exactly) correct. Only load drag-related fields if drag enabled. Fixed maxParticleSize to use size max rather than base.
- **Fixed:** Assert triggered by shortening the lifetime of particles with target attraction.
- **Fixed:** GPU particle temporal anti-alising was inverted.
- **Fixed:** Prevent overlapping pulses of continuous emitters; fixes excessive incorrect particle emissions.
- **Fixed:** Corrected Pfx1 emissive lighting unit.
- **Fixed:** Safe to use non-multithreaded smart ptr in runtimes - avoids a FatalError in _i_multithread_reference_target::UseCount.
- **Fixed:** Double spawning of burst particles by clamping emission time ranges in the proper place.
- **Fixed:** Preventing particles with emissive material to get into forward opaque render list.
- **Fixed:** Crash when changing levels with GPU particles - properly reseting render elements.
- **Fixed:** Signed/unsigned SSE operations. Added ChaosKey unit text.
- **Fixed:** Properly updating Render Object flags per frame - fixes refraction resolve.
- **Fixed:** Enable automated simd vector type conversions on gcc.
- **Fixed:** Spline tangent flags not being properly preserved. Flags now explicitly stored by particle splines rather than trying to reconstruct.
- **Fixed:** Particle deform shader was not deforming blended frames.
- **Fixed:** SSE typedefs on gcc.
- **Fixed:** Properly updating component connectors after rename.
- **Fixed:** LocationOmni by properly initializing params. Corrected spelling of some UI names. Corrected case of names in ToDisplayName.
- **Fixed:** Asset reload button is working again.
- **Fixed:** Crash on fluid dynamics.
- **Fixed:** Skipping deferred render calls for runtimes in GPU mode.
- **Fixed:** Particle colors not being properly initialized.
- **Fixed:** Iterating through runtime references instead of smart pointers - prevents ref-counting issues.
- **Fixed:** GPU particles now work on PS4.
- **Fixed:** Particle entity was not being properly initialized in gamezero.
- **Tweaked:** If no motion feature detected, add a default CFeatureMotionPhysics - particles can always move regardless if any motion feature is present or not.
- **Tweaked:** Enable static & dynamic object collisions for most specs.

#### Plugins

- **New:** Support plugin build with CMake.
- **New:** Add new default Engine entities plugin containing the default Engine entities exposed by Sandbox - eliminates the need for each game to re-implement/copy default entities.
- **New:** Support for acquiring a new plugin instance via the IPluginManager interface - allows for statically linked plugins to be acquired by class id.
- **New:** Merge RigidEntity logic into GeomEntity class - now provides drop-down menu for Physics type.
- **New:** Added Oculus 1.10 support.
- **Refactored:** (CrySystem) Moved OpenVR, OSVR and OculusVR SDK implementation to plugins. Note: Rendering implementation is still kept in renderer for direct access.
- **Fixed:** FramesPerSeconds plugin compilation.
- **Fixed:** Various fixes for static linking.
- **Fixed:** CryPluginEventListeners.
- **Tweaked:** Removed externally exposed EHmdType enum - now handled specifically in the Oculus VR plugin.
- **Tweaked:** Tweaked plugins update behavior.

## Physics

#### Physics

- **New:** PhysX interface.
- **New:** Add CVar 'p_draw_helpers_opacity' to set visual level of opacity for physical helpers ('p_draw_helpers').
- **New:** (Game/Vehicles) improved support for 2-wheeled vehicles.
- **Fixed:** Issue with setting ragdoll's velocity.
- **Fixed:** Removed NormalizeFast for 0 vectors.
- **Fixed:** Loosened overly sensitive check for non-uniform scaling.
- **Fixed:** For overflow in hash sizes in ray-mesh checks.
- **Fixed:** Crash with non-uniformed scaled cloth.
- **Fixed:** For ropes - previously braking the awakening of non-colliding ropes.
- **Fixed:** Degeneracy issue in qhull2d.
- **Fixed:** swig duplicate destructor definition.
- **Fixed:** Serious issue with world time-stepping.
- **Fixed:** Corrected TriIndices(Edges), fixing crashes when destroying Physics Objects etc.
- **Fixed:** Box-box collision issue and brushes outside the grid.
- **Fixed:** Make sure that the old bounding box is set in the EventPhysStateChange event when a physical entity's geometry is removed.
- **Fixed:** Crash in PhysX due to changes in entity system, i.e. simplified living entity.
- **Tweaked:** Add PhysX build scripts - CMake and WAF.

## Network

#### Network

- **New:** Add default Engine compression policy and scheduler - removes need (but not the ability) to copy this for each game.
- **Fixed:** Error case for socket reconnect failure.
- **Fixed:** Cannot connect to other player.
- **Fixed:** Crash on startup if default scripts aren't found.
- **Fixed:** Assertion when checking GetCommMutex locked state.
- **Tweaked:** Added logging of backlog size in backoff request.
- **Tweaked:** AllocateObject log visible from loglevel > 1.
- **Tweaked:** Better error handling for Developers.

## Sandbox

#### Editor General

- **New:** New preferences system. Ported all settings from old format to new. Settings file will be read once and deleted after being ported to new system so users will be able to migrate their settings.
- **New:** Expand/Collapse all layers.
- **New:** Preliminary Hi-DPI support.
- **New:** Add resource picker, validator and editing for particles through the properties panel. This will work with both the old and new particle system.
- **New:** Style for default dialog buttons.
- **New:** All UI variable names are converted from camel case into human readable.
- **New:** Highlight selection feature for Editor using scene custom passes.
- **New:** Added perforce plugin tray icon with configurations pop-up.
- **New:** Unlocked support for automatic ground decal under vegetations (new UI parameter in vegetation).
- **New:** Added cloth slicing to phystool; misc phystool tweaks.
- **New:** (VE) Objects are automatically selected when added to treeview.
- **New:** Tree view arrows now highlight when row is selected. QComboBox will show up in red to alert users of a deprecated class.
- **New:** Added full hierarchy visualization in level explorer.
- **New:** Add clear transform operators for objects in right click menu.
- **New:** (MFC) Add drag and drop support for list boxes.
- **New:** Added project-specific personalization. Moved recent files to project specific personalization.
- **New:** Added Save/Load filters feature on all filtering panels.
- **New:** Added options for mouse wheel behavior: Zoom Only, Speed Only, Change based on movement.
- **New:** Added trackball rotation gizmo.
- **New:** Revert property tree after triggering action button.
- **New:** Added saving and loading of filters in all filtering widgets.
- **New:** Added Drag&Drop tooltip to indicate action.
- **New:** Added texture preview in dialogs and asset browser.
- **New:** F-key workflow. F2 Asset Browser, F4 Focus Level Editor, F5 Jump to Game, F7 Export.
- **New:** Most search boxes will expand their associated tree view when applicable.
- **New:** RC-compiled assets can be edited via the asset browser.
- **New:** Source files can be imported by Drag&Drop into the asset browser.
- **New:** Assets can be Drag&Dropped on Viewport to create an object.
- **New:** New Threading API for Sandbox.
- **New:** Added AssetSystem, AssetBrowser and related functionalities.
- **New:** Add right click menu to create prefab from selection or attach current selection to picked prefab.
- **New:** Remove requirement for games to provide an IEditorGame implementation.
- **New:** Allowing more complex python scripting in Sandbox. Python in Sandbox now contains all standard libraries, allows to create UI from python trough PySide2 and introduces Python plugins.
- **New:** Python Interactive Console tool to quickly write python code in Sandbox.
- **New:** If physical helpers are drawn ('p_draw_helpers'), then render gizmos on top to be visible and avoid occlusion.
- **New:** Editor Dialog now supports project and shared properties. Favorites and File dialogs now save their favorite/history data in project personalization.
- **New:** Added "Freeze all other layers" and "Toggle hide all other layers" to Folder Layers' right-click menu.
- **New:** Added asset preview tooltip for resource pickers in the property tree that support previews.
- **Refactored:** Removed two obsolete parameters in vegetation properties: UseAlphaBlending and RecvShadow.
- **Refactored:** Added GI properties into Editor UI for geom entities, lights, brushes and vegetation (removed old object name conventions and name suffixes).
- **Refactored:** Refactored entity link serialization to reintroduce support for custom link names.
- **Refactored:** Use CryGUID instead of windows GUID for everything apart from tool/object type RTTI.
- **Refactored:** Object Manager now registers one gizmo for all objects.
- **Refactored:** Change Generate Cubemap options. Now button in inspector will act on selection and there is new button that acts on the whole level under level->lighting menu.
- **Refactored:** Cleaning up folder/filter structure.
- **Refactored:** Replace StdMap wrapper with direct usage of std::map or std::unordered_map.
- **Refactored:** Scale gizmos will no longer scale negatively and will have more precision for values lower than 1.
- **Refactored:** Use visualization for active constraint. Make trackball gizmo smaller.
- **Refactored:** Removed dependency of EditorCommon from Sandbox.
- **Refactored:** UI Emulator removed.
- **Refactored:** Change split shape object implementation to behave similarly to spline objects.
- **Refactored:** Shape objects now use new gizmo system.
- **Refactored:** Added message box type and dialog question result enum to CryMessagebox.
- **Refactored:** Removed VoxelObject, CloudGroup, IVoxTerrain, Voxel_Paint functions.
- **Refactored:** Removed duplicated shadow casting and a few other unnecessary UI parameters for light entity.
- **Refactored:** Removed obsolete UI parameters for brushes and vegetation.
- **Refactored:** Dialog Editor moved to deprecated.
- **Refactored:** Cleaned up folder/filter structure.
- **Refactored:** Use Ring/Cylinder intersection for wheel gizmo - interacts much better at grazing angles.
- **Refactored:** Small refactoring of the game exporter.
- **Refactored:** Move gizmo management to qviewport so it's reusable by more systems and so that events are handled in the correct order.
- **Refactored:** Remove reliance from CPoint from ITransformManipulator interface so that some plugins do not need to rely on MFC headers.
- **Refactored:** Rename wheel gizmo to axisrotate gizmo.
- **Refactored:** CString replaced by CryString.
- **Refactored:** Removed AssetResolver, TextureBrowser.
- **Refactored:** Remove GameSDK specific ledge entities from Sandbox source.
- **Refactored:** Remove non-functional multiplayer game rules.
- **Refactored:** Remove unused selection group vertex snapping code.
- **Refactored:** Improve response performance by skipping idle updates when the framerate is too low.
- **Refactored:** Use centralized function to get manipulator/selection compatible matrix from current selection.
- **Refactored:** Remove unused scaling functions from BaseObject.
- **Refactored:** CRenderLock now uses a scoped trylock paradigm.
- **Refactored:** Removed SandboxLegacy code.
- **Optimized:** Object Manager selection updates in batches.
- **Optimized:** Speedup on "Duplicate Objects" action.
- **Optimized:** Improved phystool icon/ added phystool to the default game toolbar.
- **Optimized:** General object selection optimizations by committing selections in batches, Viewport marquee selection optimizations.
- **Optimized:** Personalization saving on a timer trigger to avoid multiple writes to the disk.
- **Fixed:** Crash when deleting folder layer.
- **Fixed:** Type conversion between Python and C++.
- **Fixed:** Removed SuperAcceptUndo, SuperBeginUndo, SuperCancelUndo.
- **Fixed:** Crash that occurred when a removed inspector content was redrawn while marked for deletion.
- **Fixed:** Removed deprecated blocking error dialog.
- **Fixed:** Make sure level folder exists before calling open level dialog.
- **Fixed:** Restored raising of ESYSTEM_EVENT_LEVEL_LOAD_END from CCryEditDoc::LoadLevel.
- **Fixed:** If a level is loaded with no layers, one will be created as a fallback.
- **Fixed:** Hiding helpers would not hide areaShapes.
- **Fixed:** Unintentional autocomplete in "Go to position" window made it unusable.
- **Fixed:** (UI) Canceling the 'log save' dialogue triggers map save.
- **Fixed:** Where AreaBox and AreaSphere lost their proxy data during script reloading.
- **Fixed:** Crash when opening a level while searching in the 'Console Variables' window.
- **Fixed:** Cover surfaces now explicitly cleared when a new level gets loaded or created - to get rid of some leftovers from the previous level.
- **Fixed:** Unfreeze single object in frozen layer.
- **Fixed:** Crash when going from Woodlands to Airfield would assert and crash the Editor.
- **Fixed:** Entity Attributes are now available in the Init and PostInit callbacks on the entity.
- **Fixed:** (Entity Audio) Cannot manually change the size of an area box after attaching an Audio Entity.
- **Fixed:** Vegetation scaling values are now between 0 and 300.
- **Fixed:** Removed broken menus in "big preview" of Material Editor, make the preview a sphere by default.
- **Fixed:** Source control menu appearing when source control is disabled in level explorer.
- **Fixed:** Make sure selection state is properly restored when undoing object freeze.
- **Fixed:** Crash when freezing objects. Make sure to always select/deselect through Object Manager.
- **Fixed:** Bad title in Import Vegetation Objects window.
- **Fixed:** Generating a mini map in a full level and then opening a different level will cause a crash.
- **Fixed:** Removed some false positive errors being logged when trying to load files that are not really crucial (layout, personalization, keybinds).
- **Fixed:** Read plugin manifest from same path as dll.
- **Fixed:** Dimension helpers having inconsistent sizes for large objects.
- **Fixed:** Save GameVolume class name instead of class index in levels and layers, so that adding GameVolumes to CryAction or shuffling GameVolumes doesn't break levels.
- **Fixed:** Display Axis while snapping is on and user is interacting with a move gizmo.
- **Fixed:** Layer hidden/frozen state not saved.
- **Fixed:** Not possible to choose an animation from a dropdown list (or entering the name manually).
- **Fixed:** Dockables now call same code path for all different closing scenarios. Ignoring close event will correctly prevent closing dockable.!XR Cleaned up dockable closing code.
- **Fixed:** Sorting in the create object panel.
- **Fixed:** 'Console Variables' window crashes when a CVar is unregistered.
- **Fixed:** "Type" field in property page of AI objects is properly filled.
- **Fixed:** Removed auto distribute vegetation button.
- **Fixed:** Issue where changing sequence properties and pressing ctrl+z would 'unselect' the sequence.
- **Fixed:** Re-added open all and close all prefabs.
- **Fixed:** Enable & disable 'Physics/AI' with a FG-setup which calls a global FG crashes.
- **Fixed:** ShapeObject target restoration on undo relying on order of deletion.
- **Fixed:** Crash during registering new entity class.
- **Fixed:** False positive warnings when creating a new level.
- **Fixed:** Asset browser's material preview shows wrong textures.
- **Fixed:** Log Do, Undo, Redo actions.
- **Fixed:** (Legacy) Cannot place an object in level.
- **Fixed:** Stuck MNM generation after "Generate..." options were triggered in AI menu.
- **Fixed:** "Texture" and "AnyFile" resource selectors not available in SandboxLegacy.
- **Fixed:** Navigation areas not updating world bounding box correctly and not updating themselves when height was tweaked.
- **Fixed:** Tags not saved properly on level save. CCryEditApp cannot be obtained anymore by AfxGetApp.
- **Fixed:** Level explorer now intercepts invalid object renaming.
- **Fixed:** Assert on script reloading of entities with non-FlowGraph type nodes in hypergraph.
- **Fixed:** Adds auto expand/collapse to search in Create Object Tool.
- **Fixed:** Issue where camera tag points were being saved/loaded from the wrong directory.
- **Fixed:** ApplicationShortuc context caused problems. This changelist changes the context to WindowShortcut and for parentless toolwindows. Implements a mechanism to send uncaught shortcut events to main window and to be processed there as main application wide shortcuts.
- **Fixed:** Loading vegetation into the VegEditor before a map is created causes a crash.
- **Fixed:** Pressing Esc won't exit current tool.
- **Fixed:** Pressing the mouse back button on the create object panel will now bring the user back to the create object 'main menu' widget.
- **Fixed:** Memory leak (and invalid data access) from unfreed menus of Viewport header. setMenu does not add ownership to menus, therefore add it manually.
- **Fixed:** Shape object editing not refreshing rope positions properly.
- **Fixed:** Configuration Manager wasn't being initialized.
- **Fixed:** (UI) Changing CVar in console leads to misplaced console-context-window.
- **Fixed:** Pure function call after duplication of an entity.
- **Fixed:** Sandbox initialization crashes when declining the "You need a valid CE Launcher.." message.
- **Fixed:** Unified crash handling dialogs.
- **Fixed:** Avoid recursive drawing while any Viewport is drawn. Renderer does not support recursive drawing regardless of the source.
- **Fixed:** Unfreeze and unhide single objects within frozen/hidden layers.
- **Fixed:** Extracting and cloning prefabs should create objects in current layer.
- **Fixed:** Disable Physics/AI Simulation in Sandbox when loading another level.
- **Fixed:** Level data could be corrupted when exporting while navigation data is being processed.
- **Fixed:** Asset loader crashes on files without extension.
- **Fixed:** Property tree freeze in MFC windows after some resource selector dialogs are closed.
- **Fixed:** An issue where environment probes were invisible when inside groups.
- **Fixed:** (UI) 'Continuous Update' is misspelled in Game -> AI.
- **Fixed:** Orbiting getting out of synch with selection.
- **Fixed:** Crash, when copying an object containing a yasli::BitVector property.
- **Fixed:** Game tokens not loaded from the libraries.
- **Fixed:** Crash when deleting an object. This only happened when in the level explorer and the 'View->Show All Objects' option was selected or when viewing the whole layer/object hierarchy and removing an object that was nested deep inside the hierarchy with the hierarchy entirely collapsed. Crash was being caused in our mount proxy when trying to mount a new model in the middle of a delete operation (between beginRemove and endRemove calls).
- **Fixed:** Crash when scaling AreaSphere.
- **Fixed:** Issue where PFX objects had their path assigned as the object's name.
- **Fixed:** Removed '_' in camel case to human-readable conversion.
- **Fixed:** Moon-texture is missing in custom level.
- **Fixed:** It is possible to export to the Engine without having navigation data processing completed. However, saving Navigation data is skipped in this case.
- **Fixed:** Numerical properties not working in entities belonging to prefab. EntityLink serialization was triggering refresh of propertyTree too often.
- **Fixed:** Crash when deleting an entity that is being referenced in a sequence that is not open by the Trackview.
- **Fixed:** Crash on delete by forcing tab panes to be deleted before the application exits.
- **Fixed:** Since script paths are read-only, hide operators of entities without scripts.
- **Fixed:** CapsLock and NumLock can now be used for keyboard shortcuts.
- **Fixed:** Issue where undoing a sequence creation in Trackview wouldn't really remove the sequence.
- **Fixed:** 2D Viewports blanking out when exceeding a certain size.
- **Fixed:** Crash on reordering module ports.
- **Fixed:** Using 'Reset/Get Physics State' triggers warning in NC/console (unknown command).
- **Fixed:** Add support for snapping to new gizmos.
- **Fixed:** (Win 7) Crash - Drag & Dropping an entity into the map crashes the Editor.
- **Fixed:** Incorrect lock usage.
- **Fixed:** (Lens Flare) Crash when selecting a Lens Flare library via the drop down menu.
- **Fixed:** Updated message for regaining mouse control while in game.
- **Fixed:** Fixed tokenized search - now token order does not matter.
- **Fixed:** (UI) Rotation-values in Properties-panel not changeable via arrow-symbols.
- **Fixed:** Crash when linking objects that were already linked to another.
- **Fixed:** (Load Assert) Assertion failed when creating a map with mpu values 32 and 64.
- **Fixed:** Display issue when rotating multiple objects with view aligned rotate gizmo.
- **Fixed:** Non-uber build fix.
- **Fixed:** Crash if recompressing animations when Compression Manager had not been created in cases where e_img_useCAF was non-zero.
- **Fixed:** Crash with AI Physics enabled when loading a level. Start loading the level after AI/Physics is reset.
- **Fixed:** Crash in LevelLayerModel when an object within a group or prefab was linked to a sibling. Issue was solved by making sure the order of operations was sane: detach, then attach; rather than start attaching, detach, finish attaching.
- **Fixed:** Crash when removing the last toolbar from the toolbar customization screen.
- **Fixed:** Crash that was occurring when a toolbar was loaded and contained a non-existant & non-custom command.
- **Fixed:** Changed ParticleEditor to not show the whole path in the tabs.
- **Fixed:** Entity attribute changes in Sandbox not propagated to the actual entity attributes.
- **Fixed:** Loading levels with lights in hidden layers now correctly disables those lights.
- **Fixed:** Make sure specific config files (user.cfg, autoexec.cfg) as well as command line is only executed once.
- **Fixed:** Prevent the same Viewport from being selected twice.
- **Fixed:** Re-implemented Sandbox early-shutdown crash fix.
- **Fixed:** Reset Viewport to last player position in Editor game mode.
- **Fixed**: Crash on failing to create an object.
- **Fixed:** CryMessageBox forever suspending Editor update.
- **Fixed:** Prevent QAnimation related crash when rapidly changing layouts.
- **Fixed:** Right-clicking on a free spot in window with track/node-names while a track/node is selected opens wrong context menu.
- **Fixed:** Make sure created objects are always snapped to terrain regardless of setting.
- **Fixed:** Crash that occurred when clicking into an empty curve editor widget.
- **Fixed:** Python not working in SandboxLegacy.
- **Fixed:** Crash when setting UDPs.
- **Fixed:** Shortcut conflicts when using Particle Editor.
- **Fixed:** Crash when exiting the Editor via Quit console command.
- **Fixed:** Unify handling of closing TV and closing a TV-sequence.
- **Fixed:** Incorrect path creation (missing separator).
- **Fixed:** Crash that could occur when deleting a feature.
- **Fixed:** Export Terrain Area saves no file when file-ending not added to filename.
- **Fixed:** Wrong options shown to user when RC.exe not found.
- **Fixed:** FBX animation importer does not display a list of colliding names.
- **Fixed:** keybind Editor not handling shift+key once the edit control has focus.
- **Fixed:** Where deleting grouped objects from prefabs crashed Editor. Also fixed an issue where marquee select was selecting all groups and prefabs in the view (even if not intersecting).
- **Fixed:** (Physics/AI simulation mode) When disabling the simulation, CryAISystem will now be asked to reset itself after all entities have reset, so that they can unregister their content before the CryAISystem wipes out its containers.
- **Fixed:** UI Actions list is no longer populated.
- **Fixed:** PhysTool's CVars were not registered.
- **Fixed:** Crash with null pointer dereference in SurfaceInfoPicker.
- **Fixed:** Track-names displayed behind search-field.
- **Fixed:** Only allow EntityObjects to be linked through entity links.
- **Fixed:** ObjectClone tool now relies on stored initial positions, just like the transform system, so Audio position can be updated correctly.
- **Fixed:** ObjectClone Tool not working in global coordinates.
- **Fixed:** ObjectCloneTool axis constraint plus terrain snapping not possible at the same time.
- **Fixed:** Particle effects from the database view are now created properly. Fixes duplicating and saving bugs.
- **Fixed:** Objects transforming to 0,0,0 at times. ViewToWorld will now return a point on the ocean when collision with terrain fails.
- **Fixed:** View space rotation/scaling not getting applied correctly.
- **Fixed:** Scaling is now applied/projected to local space of object correctly.
- **Fixed:** Trackball rotation with custom transform manipulators.
- **Fixed:** Crash in directory widget caused by continuous search.
- **Fixed:** Prevent users from linking objects to a group.
- **Fixed:** Alembic compiler(.abc) creates wrong cryasset.
- **Fixed:** Now using numeric version of show helpers in the ViewModes toolbar.
- **Fixed:** Lighting helpers not having icons, not being selectable and their bounding box being incorrect.
- **Fixed:** Make sure that shapeobjects recalculate their bounding box when their size changes.
- **Fixed:** Merge/split spline operations not cancellable by Esc.
- **Fixed:** The discard button.
- **Fixed:** Highlight getting lost on entity object update.
- **Fixed:** F11 to toggle Fullscreen doesn't work in the Editor.
- **Fixed:** Copy+paste on color properties does not work anymore.
- **Fixed:** Aborting object creation not possible unless Viewport is clicked.
- **Fixed:** Crash when changing FOV on the Viewport.
- **Fixed:** (CT) Gizmos (translate, rotate, scale) to be usable again.
- **Fixed:** New objects not being removed when undoing or cancelling a duplicate objects action.
- **Fixed:** Crash with vertex snapping tool when changing Viewports while the tool is active.
- **Fixed:** HiDPI Viewport fixes.
- **Fixed:** Crash on light entity copy.
- **Fixed:** (CT) Playback speed uses and keeps actual selected speed.
- **Fixed:** Issue where moving an object within a group without the gizmo was applying world coordinates as local.
- **Fixed:** Custom texture slot names in Material Editor.
- **Fixed:** GeomEntities crashing on duplication.
- **Fixed:** Tab grabbing input from game when in game mode.
- **Fixed:** Crash loading entity object with empty properties.
- **Fixed:** The notification center so now sorting by type is possible.
- **Fixed:** (CT) Spacing/stretching in QPropertyDialog - used from BatchFileDialog.
- **Fixed:** Re-added call to code that on object deletion it re-adds the number at the end of the unique name so it can be reused. This should fix a problem where while placing an object through the create object panel, an object would be created when the mouse entered the Viewport, then be deleted when the mouse left the Viewport. This generated a new number for that type and never returned it.
- **Fixed:** Duplicated Level Settings, update calls during level load.
- **Tweaked:** Typo "Raise terrain".
- **Tweaked:** IEditor now has an alternative method GetActiveDisplayViewport to return a pointer to the public IDisplayViewport interface.
- **Tweaked:** Only entities that request bounding box drawing explicitly should have one.
- **Tweaked:** Prefab right click menu now has the option to open prefab in database view.
- **Tweaked:** Increased yasli version.
- **Tweaked:** Don't show invisible variables.
- **Tweaked:** Updated Qt 5.6 to latest revision.
- **Tweaked:** Changed disabled/enabled style of propertytree rows.
- **Tweaked:** Print progress log message before exporting MNM file.
- **Tweaked:** Maximize Viewport - now only maximizes the content without the header.
- **Tweaked:** Make sure Sandbox can use the game instance instanciated by CryAction.
- **Tweaked:** Output more specific errors when entity load fails.
- **Tweaked:** Remove obsolete call to GetGameViewport.

#### Designer Tool

- **Fixed:** Clipvlolumes not respecting filled flag after helper show events.
- **Fixed:** Subdivide tool not exiting after freezing.
- **Fixed:** Bevel tool not exitable with Esc after finishing.
- **Fixed:** Crash when setting invalid tool and quickly moving the mouse over the renderviewport.
- **Fixed:** Crashes with multiple UV Mapping windows.
- **Fixed:** Only allow one UV Mapping window instance.
- **Fixed:** Bevel tool not cancelled properly.
- **Fixed:** More AreaSolid/ClipVolume hidden flag handling. Visibility changes could still mess with the hidden flag.
- **Fixed:** UV vertices not keeping their size with different zoom levels.
- **Fixed:** Account for corner cases in cylinder projection.
- **Fixed:** Multiple tool buttons highlighted at the same time.
- **Fixed:** Selection state being stuck in previous selected object while Designer session was still active.
- **Fixed:** Selection was referencing deleted polygons after "separate" tool was used.
- **Fixed:** Separate tool creating objects without any geometry being separated.
- **Fixed:** Clone tool naming.
- **Fixed:** Double Designer entry in creation menu and crash.
- **Fixed:** UV Editor gizmo interaction in Qt Editor and use new gizmo code.
- **Fixed:** Cube mapping producing bad results.
- **Fixed:** Crash on trying to access unused parent tool variable from freed Designer tool.
- **Fixed**: Grow and Connected tool can now also operate on vertices/edges.

#### Trackview

- **New:** Allow to add objects under group with Add Selected Entities button and right-click menu item with the same name.
- **New:** Improvement to how right click menu on nodes/tracks works - what is shown in menu, what is executed.
- **New:** Disable and Enable multiple tracks or nodes in Sequence at the same time.
- **New:** Add Selected Entites to Sequence.
- **Fixed:** Director node.
- **Fixed:** A newly created sequence is missing Playback start/stop markers.
- **Fixed:** Timeline does not dim area outside sequence start and end.
- **Fixed:** Fixed Assert when re-opening a closed sequence.
- **Fixed:** Timeline in Character Tool does not work.
- **Fixed:** Do not zoom in to object when Select Entity in Viewport is pressed.
- **Fixed:** Unify handling of closing TV and closing a TV-sequence.
- **Fixed:** Newly created track only partially shown/highly zoomed in.
- **Fixed:** Allow to add groups under groups, unlimited depth level.
- **Fixed:** Using Ctrl+C and Ctrl+V and left click in curve-window causes a crash.
- **Fixed:** Disable/enable track delete keys.
- **Fixed:** Bring back LightAnimationSets for backwards compatibility.
- **Fixed:** Open 'Render Sequence' window in TV causes error (XML reader).
- **Fixed:** Improve to dim area outside of timeline.
- **Fixed:** Reposition time markers to changed sequence start and end.
- **Fixed:** Setting the End Time of a sequence only affects Dopesheet, not Curve Editor.
- **Fixed:** Setting Start and End Time will not update the timeline.

## Tools

#### Tools General

- **New:** Add new VSIX.
- **Refactored:** Remove old VSIX.
- **Fixed:** Statobjmerging does not work. 3ds Max exporter may ignore - "Use 32 bit precision" option.

#### Resource Compiler

- **New:** Add parameter imageconverterquality=[preview, fast, normal, slow].
- **New:** Added generation of cryasset metadata files and removal of metadata.
- **New:** Moved RC projects to the new CMakeList.txt.
- **Refactored:** Update to PowerVR Texture Tool version 16.2.
- **Fixed:** FBX importer have artifacts caused by missing smoothing information.
- **Fixed:** Importing alembic files (.abc) doesn't work in Live-Version 5.2.1.
- **Fixed:** Photoshop RC crash.
- **Fixed:** Axis change only affects LOD 0.
- **Fixed:** Use correct pixel format for ES3 light projectors.

## Known Issues

- ****Known Issue****- Upgrading projects from CRYENGINE 5.2 to 5.3. See our documentation page **[here.](/docs/static/engines/cryengine-5/categories/23756816/pages/26218520)**
- **Known Issue** - Editor may crash when loading a level if "Enable Physics" is activated (workaround - Please make sure that "Enable Physics" is NOT activated when loading levels).
- **Known Issue** - Game Launcher will crash if the user exits the game whilst in/underwater (workaround - Please don't exit game mode whilst in/underwater).
- **Known Issue** - Render entity "GeomCache" is not displayed when placed in a level (workaround - After placing the GeomCache render entity in your level, go to File > Save, and the entity will be rendered).

[Code Interface Changes](#code-interface-changes)[Release Highlights](#release-highlights)[Game Templates](#game-templates)[Animation](#animation)[AI](#ai)[Audio](#audio)[Core/System](#coresystem)[Graphics and Rendering](#graphics-and-rendering)[Physics](#physics)[Network](#network)[Sandbox](#sandbox)[Tools](#tools)[Known Issues](#known-issues)
