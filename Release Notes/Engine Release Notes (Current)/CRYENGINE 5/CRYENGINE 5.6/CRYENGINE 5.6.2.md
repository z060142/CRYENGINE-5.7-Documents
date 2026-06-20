# CRYENGINE 5.6.2

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/47316993/pages/44970536
- Page ID: 44970536
- Breadcrumb: Engine Release Notes (Current) > CRYENGINE 5 > CRYENGINE 5.6 > CRYENGINE 5.6.2
- Parent: CRYENGINE 5.6

## Content

Known Issues

- When loading a second level in a template project, the player will not spawn when entering game mode until the Sandbox is restarted.
- Drag and dropping entities with children into another layer crashes the Editor.
- Starting a C++-Plugin-only project in Editor/Game Launcher causes a crash.
- Turning on the "Ambient" light option for the Point Light entity component triggers asserts and sometimes causes crashes.
- Using Edit and Continue on any project causes compilation error.

## Animation

- **Fixed:** Updated the public ICharacter::FinishAnimationComputations() method to also process Parent Character instances along the attachment hierarchy (in order to mitigate sync ordering issues).
- **Fixed:** Addressed a change that was missing from an earlier submission.
- **Tweaked:** Introduced an emergency cleanup step in COperatorQueue to mitigate issues with operations being accumulated over multiple frames when the Pose Modifier is not being executed (for example due to animation update culling).

## AI

- **Fixed:** Crash on opening UQS Editor and UQS History without an open Viewport. (EditorCommon.dll!CViewport::AddPostRenderer(IPostRenderer * pPostRenderer).

## Audio

- **New:** Added CrySpatialFMod to ce/main.
- **New:** Added module definition for CryAudioImplPlugins.
- **Tweaked:** (SDL Mixer) Implement optional preloading of audio files.
- **Tweaked:** Updated FMOD Studio to version 2.00.04.
- **Tweaked:** Updated WWise to version 2019.1.4 (see Core/System re. VS2015 SDK and WWise 2019.1.4).
- **Tweaked:** Implement offset for Audio Listener component.
- **Tweaked:** (ADX2) Initialization should not fail when ACF doesn't exist.
- **Tweaked:** Expose Audio Listener selection (to user) in Listener component.
- **Tweaked:** Implement multi-listener support for material effects.
- **Tweaked:** (ACE) Add option to duplicate controls.
- **Tweaked:** (ACE) Hide rename option from context menu (when a default control is selected).
- **Tweaked:** (ACE) Add option to rename a control to the name of a selected connection.
- **Tweaked:** Enable 3D positioning for Audio Triggers in the Character Tool.

## Core/System

- **Fixed:**(PakTools) Compilation error for PAK Encryption/Sign/Decryption tools (due to enums not updated to match the latest LibTomCrypt SDK being used).
- **Tweaked:** Update cryengine.cryengine version to 5.6.2.
- **Tweaked:** (Jobsystem, DedicatedServer) Fix compiler error when compiling with option JobManager_Support_Statoscope and Dedicated_Server in release.
- **Tweaked:** Updated OculusSDK to version 1.40.
- **Tweaked:** Add VS2015 SDK for WWise 20191.4.

## CMake/Build

- **Fixed:** Disabled Schematyc2 because of deprecation.
- **Fixed:** CMake setup behavior.
- **Fixed:** CMake Oculus VR plugin version check and comments.
- **Fixed:** (Config Files) Autoexec and console batch files that ran through exec would only process CVar assignments.
- **Fixed:** Error if Xbox One XDK environment variable doesn't exist.
- **Tweaked:** Disable Oculus VR plugin (when using VS2019 16.3.0 - due to compilation issue).
- **Tweaked:** (CMake) Add project command to root CMakeLists.txt.
- **Tweaked:** Use CMake target properties for setting Visual Studio debugger command and arguments.
- **Tweaked:** De-escalate warning about missing optional SDK to just a notice.
- **Tweaked:** Disable Rail GamePlatform plugin if missing the SDK.
- **Tweaked:** WinPixEventRuntime SDK is no longer required for building the Engine.

## Graphics and Rendering

- **Refactored:** Removed CTerrainNode::IntersectWithShadowFrustum and CTerrain::IntersectWithShadowFrustum.
- **Fixed:** Terrain holes in Game Launcher.
- **Fixed:** Memory corruption in Terrain Load.
- **Fixed:** Additional fix to avoid invalid permanent render object submission in Terrain Nodes.

## Particles

- **Fixed:** Use proper shader aliases to get relevant shader flags. Also tweaked debug colors.
- **Fixed:** Mark effect modified - when adding or connecting nodes in graph view (fixes "Save As" issue).

## Physics

- **Tweaked:** Physics worker threads were not respecting the thread to fully finish prior to re-creating it.

## Project System

- **Fixed:** Cannot start from generated proxy projects due to missing path separator in the Visual Studio debugger command.
- **Fixed:** Guard against encoding error issues on certain systems from non-English locales when registering the Engine.
- **Fixed:** (CryVersionSelect) Update and fixes on cryengine.cryengine.
- **Fixed:** Package Build of template projects fail due to Project Manager serializing GUID in project json even if not applicable.
- **Tweaked:** Support VS2019 for Engine and project solution generator.

## Sandbox

- **Fixed:** Issue where if a window's minimum size was larger than it's maximum size (when resizing it from the left) it would actually move the window.
- **Fixed:** Undocking a collection of tabs will make the menu button invisible.
- **Fixed:** Resizing the tool in a floating state leads to flickering.
- **Fixed:** Importing models with multi submaterials (via FBX) switches the ID positions.
- **Fixed:** Notification pop-ups from showing up during startup (due to them behaving erratically, since not everything is fully constructed and the layouts finalized).
- **Fixed:** Un-attaching and attaching the PE's curve-window will make the hamburger menu appear in the Inspector and the Curve-window.

## Mobile & Consoles

**Tweaked:** (Xbox) Update XDK to version July 2018 QFE 9.
