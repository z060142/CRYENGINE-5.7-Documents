# CRYENGINE 5.5.0 Preview 1

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/47316993/pages/44962769
- Page ID: 44962769
- Breadcrumb: Engine Release Notes (Current) > CRYENGINE 5 > CRYENGINE 5.5 > CRYENGINE 5.5 Previews > CRYENGINE 5.5.0 Preview 1
- Parent: CRYENGINE 5.5 Previews

## Content

![Image](https://www.cryengine.com/docs/static/attachments/44962788)

[![Image](https://www.cryengine.com/docs/static/attachments/44962785)](https://www.cryengine.com/support)

##
5.5 Overview

Welcome to our latest major update - CRYENGINE 5.5. We have been developing 5.5 in conjunction with the title Hunt:Showdown at our Frankfurt studio and we very much look forward to users having access to the various fixes and improvements that have trickled down into the main branch from Hunt's development. Along with these improvements we have added several new features and migrated various Entities from the legacy GameSDK code to the new Components.

In total we have made over 1600 improvements & fixes and have introduced several new features in CRYENGINE 5.5, these include; the all new .level file format - this allows for much easier team collaboration and permits level files to exist anywhere in your project directory. The Development Team has also updated the Terrain System for all new displacement brushes and better material blending, alongside a new feature that allows for heightmap sizes of less than 1 meter. We have also added deeper C# functionality by exposing it to Schematyc for Signals and Functions. We have also made the creation of C# scripts easier by allowing users to create and edit C# scripts and have them dynamically update within the browser itself.

For users of Unity we have created a migration guide to help with transitioning with code and assets from Unity to CRYENGINE. Numerous topics on animation and general asset setup are covered, including detailed breakdowns on code comparisons to help guide you through a familiar workflow. Included with this is a simple shooter example breakdown to help users get up and running on code snippets and into the engine faster than ever.

Another topic that will be a delight and show progress on the front of accessibility is the all new C++ documentation and Sandbox programming with the release of the Editor source code. Having access to these portals you will now be able to enrich your game quality and ease your developments with a customized Editor user experience. This coincides with the long due project of completely overhauling the documentation on the user manual, something that will take time to finish but worth showing to get the communities feedback on structure and readability. To emphasize we will aim to clean up the docs with the included hierarchy within the range of the Preview release so it should be taken as a "Beta" access to our plans on that front.

Finally, in answer
to numerous requests from the CRYENGINE Community for a CRYENGINE on-boarding/beginners course we bring you Flappy Boid,
a C# Visual Studio debugger, packaging and building through CrySelect, SVOGI Offline Voxelization, a reskinned Material Editor in Qt, and last but not least various Entity Components for Rain, Water Ripples and VR interaction. Given this diverse range of updates and the expansion of platform support - so don't wait, go and get CRYENGINE 5.5 through the CRYENGINE Launcher NOW!

##
Contributors

We would like to say a massive thank you to the following for their valuable contribution in the making of this 5.5 release of CRYENGINE.

-
Chylix

-
Shivam Mistry

-
Tiago Morais Morgado

-
ochounos

-
uniflare

##
Sections

[5.5 Overview](#55-overview)
[Contributors](#contributors)
[Sections](#sections)
[Code Interface Changes](#code-interface-changes)
[Release Highlights](#release-highlights)
[Known Issues](#known-issues)
[Animation](#animation)
[AI](#ai)
[Audio](#audio)
[Core/System](#coresystem)
[Graphics and Rendering](#graphics-and-rendering)
[C#](#c)
[Physics](#physics)
[Network](#network)
[Project System](#project-system)
[Sandbox](#sandbox)
[Tools](#tools)

##
Code Interface Changes

For more information. see the
[Important CRYENGINE 5.5 Data and Code Changes](../CRYENGINE%205.5.0/Important%20CRYENGINE%205.5%20Data%20and%20Code%20Changes.md)
.

If you are updating from CRYENGINE 5.4, please read this topic:
[Migrating from CRYENGINE 5.4 to CRYENGINE 5.5](../CRYENGINE%205.5.0/Migrating%20from%20CRYENGINE%205.4%20to%20CRYENGINE%205.5.md)
[.](/docs/static/engines/cryengine-5/categories/23756816/pages/29445533)

##
Release Highlights

##
Preview Through Launcher and Editor Source Code

We really do want to make CRYENGINE users lives much easier - so to that end you can now get CRYENGINE Preview versions through the CRYENGINE Launcher.

On top of this we have also exposed the full Sandbox Editor source code to the Github repository for users to clone and begin customizing their Sandbox Editor experience. Go to the Crytek/CRYENGINE
[Github](https://github.com/CRYTEK/CRYENGINE)
 repository to begin creating plugins or submitting pull requests to the CE branch.

We really look forward to seeing other user names appear on the Contributors list above - what better way to showcase your newest plugins and products using CRYENGINE.

![Image](https://www.cryengine.com/docs/static/attachments/44962782)

##
New Sandbox Level File Format

A significant change for CRYENGINE 5.5 is the new Level File Format. This feature has been added in order for the Sandbox Editor to future-proof itself inside the concept of collaborative editing and for the usage of version control systems.

Another aspect of this integration is the ability to place level files anywhere within your project directory. Layers have also been upgraded to allow for dynamic population and are no longer hard-coded inside of an archive.

Finally, the terrain is now visible as an object inside of the Level Editor and on all projects inside of 5.5 and it can be added or removed just like any other item, allowing for more modularity to the workflow.

![Image](https://www.cryengine.com/docs/static/attachments/44962781)

##
Unity Migration Guide

For 5.5 we have added a Unity Migration Guide to our CRYENGINE V documentation. This guide is designed to help Unity Engine users transfer their skills and or content over to CRYENGINE faster than ever before.

 Within this guide Developers can expect to find detailed information on the basics of files and directory structure, alongside detailed breakdowns of asset conversion and export setups for use in the Sandbox Editor.

 Several development disciplines are broken down within the guide that pertain to textures, models, UI and code so as to cover the largest range of topics needed for a functional prototype.

 After reading this guide the CRYENGINE team are confident that you will be able to feel comfortable in the Sandbox Editor interface while creating your next development.

![Image](https://www.cryengine.com/docs/static/attachments/44962780)

[Unity Migration Guide Documentation](../../../../../Manual/CRYENGINE%20-%20Getting%20Started/Migration%20Guides/CRYENGINE%20From%20Unity.md)

##
Flappy Boid

Flappy Boid is our answer to the numerous requests from the CRYENGINE Community for a CRYENGINE on-boarding/beginners course. Flappy Boid has been designed to be a fun way to learn many of the core game development concepts in CRYENGINE V while building a finished game.

Topics include; scripting game mechanics using Flow Graph, removing and modifying GameSDK player functionality, using and animating cameras, physics, basic movement, audio, modeling, texturing, score-keeping, particle effects and much more.

We really like Flappy Boid and we are sure that the CRYENGINE community will feel exactly the same about it and will go turn it into their own great games!

![Image](https://www.cryengine.com/docs/static/attachments/44962783)

[CRYENGINE Marketplace Flappy Boid](https://www.cryengine.com/asset-db/product/crytek/flappy-boid)

##
Documentation Overhaul

CRYENGINE users have long been asking for more documentation and for more up to date documentation for their projects. So with 5.5 we have not only focused on the user facing side, but the programming side as well.

We have been hard at work, and in 5.5 we expose the progress that has been made on the monumental task of updating the user manual for Designers, Artists and others who use the Sandbox Editor. This work is far from being complete, but we will be expanding on this and we should be able to deprecate all other documentation by the end of the Preview release cycle.

Finally, we have
completely overhauled the C++ documentation to include numerous code snippets and have also extended the documentation to now include the Sandbox programming portal to coincide with the Editor source code release. Another aspect of this overhaul has been properly exposing the API for reference within Confluence and not in a separate portal.

To the right are links to the Sandbox Programming, the C++ documentation and a link to the API reference within Confluence.

![Image](https://www.cryengine.com/docs/static/attachments/44962778)

[CRYENGINE V Manual (BETA WIP)](/docs/static/engines/cryengine-5/categories/23756816/pages/26869929)

[CRYENGINE Sandbox Programming](../../../../../API%20Reference/CRYENGINE%20Sandbox%20Programming.md)

[Technical Documentation 5.7 LTS](/docs/static/engines/cryengine-5/categories/23756813)

[C++ API Reference](/docs/static/engines/cryengine-5/categories/28704770)

##
Sandbox UI/UX Changes

New in 5.5, the Sandbox Editor now provides users with additional upgrades and tweaks to improve workflow.

We have de-cluttered the Viewport work area by creating a drop-down for tabs, this results in you being able to see every open window within a given dock and so allows the nesting of everything inside a side pane.

Additionally we have now made it possible for you to control the distance of your helpers within the Viewport. This will not only help in the optimization of your development scene when too many items/icons begin to collect in your level, but also improves performance by removing unnecessary calls.

Lastly, we have provided the ability to CTRL click the visibility icon to hide all (solo mode). This will help you to get to an item quickly and then jump back into the full scene when there is a complex collection of entities.

So with these changes and several more we hope you find the development experience in the Sandbox Editor getting easier!

![Image](https://www.cryengine.com/docs/static/attachments/44962777)

##
Updated Entity Components

In what will be a trend for many future releases, we bring several new and legacy Components to the new Entity System. Rain and water ripple Entities have been ported over from Legacy Entities.

 In addition to the above, a new VR Camera and Interaction Component both ship with 5.5 - this will allow you to get up and running with VR even easier than it was before.

 With this new integration, Component developers will be able to customize the geometry their controller uses, as well as being able to dynamically constrain items to the controller position when a trigger is pressed.

 We are sure that users will find these new Components to be a nice addition to the library and we very much look forward to pushing out more Components in future releases.

![Image](https://www.cryengine.com/docs/static/attachments/44962776)

##
Automated Packaging and Backing up

We know that for non-coders the notion of sharing your CRYENGINE content and packaging it for release has not been easy in the past. So we have addressed this, and with 5.5 we are introducing package build functionality directly within the CrySelect interface. There are options of building out to either profile or release and the location.

 The other upgrade to Cryselect is the addition of the new Back-up Tool, so you can now easily create a backup of your project before switching to another Engine version. Simply put the new back-up feature takes all plugins shared libraries, assets, code, solutions, cryproject, and config files into account.

We are sure that these new additions to Cryselect will really help alleviate some of the previous pain points that Developers have had during migration and delivery of their games.

![Image](https://www.cryengine.com/docs/static/attachments/44962775)

##
C# Upgrades

Within the C# implementation we have most noticeably expanded how you create C# assets - this can now be achieved directly inside of the Asset Browser. This luxury allows you to just click the newly created asset and it will open a Visual Studio instance.

 Speaking about Visual Studio, C# users will now be able to debug through the IDE with our new C# extension. By default our C# implementation has required Mono in order to run, so an extension has been written to expose this in Visual Studio (given its lack of support for the Mono runtime).

 Finally, you will notice that inside of the C# implementation you are now able to expose both Signals and Functions to Schematyc for use inside of your Entity Components when developing. Oh boy, C# you are growing so fast!

![Image](https://www.cryengine.com/docs/static/attachments/44962774)

##
Character Proxy Creation

For a long time now the entire process behind creating a character has been seen as locked off to specific 3rd party tools and not flexible enough for most production pipelines.

 In previous versions of CRYENGINE we have seen the FBX animation import feature introduced and most recently we allowed for the tweaking of ragdolls and their joint limits directly in the Character Tool. With this new feature we have now extended that flexibility to allow for the physics proxy creation to be allowed directly in the Character Tool viewport and be interchangeable in a production environment. There are no dependencies placed on the proxy creation and it simply sits alongside your Character Definition File to allow for seamless editing and versioning.

![Image](https://www.cryengine.com/docs/static/attachments/44962773)

[Proxy Generation Documentation](/docs/static/engines/cryengine-5/categories/23756816/pages/29450429)

##
Terrain System Improvements

The Terrain System just keeps on getting better and better. In our 5.5 release we bring you the new Weighted Blending of Terrain Materials - this feature will drastically improve the blending of your terrain textures and will provide you with super realistic transitioning.

 In the past we have not had the ability to blend multiple materials together, well in 5.5 we have lifted that threshold to support for 3 materials. We have also added support for a smaller unit size of less than 1 meter in the terrain. Users can find this new setting in the Create New Level settings or Resize Terrain menu within the Sandbox Editor.

 Last but not least, are the improvements in detailing of your Heightmaps. In 5.5 we bring you a new displacement option in the Terrain Sculpting Tools. This can be viewed as a stamp option that allows users to import preset shapes that could have been defined elsewhere or directly through heightmap data that comes from online resources.

![Image](https://www.cryengine.com/docs/static/attachments/44962772)

##
SVOGI Improvements

SVOGI has historically been a big push with CRYENGINE and a feature that almost all developers now use and adore. Coming with production-proven experience and the enhanced emphasis on SVOGI being able to run on consoles, we have now enabled Developers with the tool to cache SVOGI on disk and have the GI to be calculated completely offline.

 The second feature improvement we would like to let you know about is the advancement in SVO Ray-traced Shadows and how this feature is something that can be considered as an alternative to using cached shadow maps in your scene. Immediately you can see several optimizations and improvements coming from this integration;

-
No additional CPU side work

-
Transparent shadows from transparent objects

-
No additional large allocations of shadow maps on the GPU

-
Soft penumbra with little performance loss
We are sure that you will find these features really useful in your current development work and that your scenes will have the proper ambient tonality as would be seen in real life.

![Image](https://www.cryengine.com/docs/static/attachments/44962771)

##
Game Platform Plugins

For 5.5 we have a brand new Game Platform plugin, this allows for easy access to common distribution platforms and data transfer protocols. Our aim is to alleviate and expedite the publishing of CE content on multiple platforms along with the additional benefits of promoting material through their features.

 Nowadays Steam and PSN are almost essential to the development and deployment of a game to the mass market. So within our new Game Platform plugin we have exposed the ability for you to now access multiple features through Steamworks or PSN API's. Some of the features that most developers will find of use are; matchmaking, leaderboards and achievements that will help users to drive customer retention.

The other integration concerns HTTP and the new libCURL integration that exposes a client-side URL transfer library. For any backend work, then keep this integration in mind as it provides numerous features such as being thread-safe, IPv6 compatible and is extremely fast.

![Image](https://www.cryengine.com/docs/static/attachments/44962770)

##
Known Issues

-
**
Anim:
**
 Save/load breaks default character movement - note: singleplayer only).

-
**
Save:
**
 Using Save as... after a save makes brushes disappear and unusable.

-
**
Crash:
**
 Clicking the group button, then clicking un-group in properties several times causes a crash.

-
**
Crash:
**
 (Asset Browser) Renaming imported textures causes Sandbox Editor to crash.

-
**
Crash:
**
 Creating prefab in Level Explorer from a linked object causes a crash.

-
**
Rendering:
**
 Resizing the Properties Panel corrupts rendering in the Character Tool.

-
**
Designer:
**
 Designer surfaces are invisible or flicker during edit mode and after.

-
**
Crash:
**
 Extracting objects from prefab crashes the Sandbox Editor.

-
**
Global VFX:
**
 Switching layers breaks particles, visuals and audio for them.

-
**
Crash:
**
 Adding a Camera Component to an Empty Entity causes a crash.

-
**
Area:
**
 VisArea does not hide objects outside of the area.

-
**
Substance:
**
 Creating a substance graph preset does not create the related texture files (diff, spec, ddna, etc.).

-
**
Crash:
**
 (Template) Adding a Component to an EnvProbe in Schematyc or a blank template causes a crash.

-
**
Terrain Painting:
**
Painting terrain texture doesn't work if "Mask by Altitude and Slope" checkbox is enabled.

-
**
DX12:
**
 Various issues related to DX12.

-
**
Vulkan:
**
 Various issues related to Vulkan.

-
**
VR:
**
 Currently not working.

-
**
C#:
**
 Memory corruption can occur after reloading scripts in Sandbox, resulting in possible crashes and undefined behavior.

##
Animation

##
Animation General

-
**
New:
**
 Added support for physicalized attachments with several phys parts.

-
**
New:
**
 Added CVar to enable "force skinning" for all Vcloth-attachments.

-
**
New:
**
 Implemented pose preservation for animation LODs. A new ca_ResetCulledJointsToBindPose CVar has been introduced to control whether transforms of culled joints should be reset to bind pose or preserved from last evaluated frame. Default behavior has changed from reset to preserve.

-
**
New:
**
 Added an explicit sleep speed setting for character ropes.

-
**
New:
**
 Added CVar for rendering characters attachments proxies in-game.

-
**
New:
**
 Changes in motion parameters applied to a locked blendspace are now picked up on each iteration when looping.

-
**
New:
**
 Added attachment flag to disable nearest rendering per attachment.

-
**
New:
**
 (VCloth) added a 'hide' flag for disabling simulation & rendering.

-
**
New:
**
 (VCloth) Improved simulation frustum culling/improved precision for switching to skinning mode.

-
**
New:
**
 (VCloth) Added GPU vertex skinning (if simulation is NOT running).

-
**
New:
**
Added a CVar to force Animation LODs on characters (ca_ForceAnimationLod).

-
**
Fixed:
**
Race condition crash in PoseAlignerChain. This crash occurs occasionally when using ground alignment IK.

-
**
**
Fixed
**
:
**
Audio event which was added to an animation in the Character Tool is not played in Sandbox Editor or game mode.

-
**
Fixed:
**
 8 weight skinning i.e. 8 weight-compute skinning and 8 weight-vertex skinning.

-
**
Fixed:
**
 (Physics) More safety checks for incorrectly assigned character cloth attachments.

-
**
Fixed:
**
 Broken nullcheck condition in CharacterManager::LoadCharacterDefinition.

-
**
Fixed:
**
 Mem corruption on incorrectly assigned cloth attachments.

-
**
Fixed:
**
 Added safety logic to avoid Vcloth re-initalization/skinning in low-framerate situations.

-
**
Fixed:
**
 Some physicalized attachment fixes.

-
**
Fixed:
**
 Potential crash by querying bitmask instead of rendernode pointer.

-
**
Fixed:
**
 (Renderer) Crash when 8-weight compute skinning is selected.

-
**
Fixed:
**
 Added option to enable mutual exclusive Viewport updates (CT, Mannequin, LevelEditor). Available via Preferences -> Viewport.

-
**
Fixed:
**
 Fixed scale support for character physics.

-
**
Fixed:
**
 Added CVar to disable the rendering of a level in the Sandbox Editor (if not in focus) - Improves the performance of tools (e.g. CT, Mannequin) when a large level is loaded.

-
**
Fixed:
**
 LOD debug draw for characters.

-
**
Fixed:
**
 Bug in directory structure lookup cache - was preventing animation files from being correctly discovered when ca_useIMG_CAF mode is enabled.

-
**
Fixed:
**
 Blendshape animation with wrinkle maps not working.

-
**
Fixed:
**
 Blendshape Weight Joints not working.

-
**
Fixed:
**
 (Components) (Physics) Enforce rigid-body Component to be awake on level-start in case of 'enabled by default'.

-
**
Fixed:
**
 Issue when reloading chrparams where previous skeleton LODs were not cleared on the skeleton.

-
**
Optimized
**
:
 Only enable close-to-origin collisions for body-colliding character ropes.

-
**
Tweaked:
**
 Added more debug output to ca_debugAnimUsage for displaying information on used blendspaces.

-
**
Tweaked:
**
 Added a CVar to filter animation command queue debug output (ca_DebugCommandBufferFilter).

-
**
Tweaked:
**
Added API examples for pose modifiers and motion parameters.

-
**
Tweaked
**
: Add Mannequin API examples.

-
**
Tweaked
**
: Introduce API example for ISkeletonAnim::StartAnimation.

##
Character Tool

-
**
New:
**
 (PhysDebugger) Added external ragdoll test mode to the Character Tool (CT).

-
**
New:
**
 Implemented color support for CTimeline keys.

-
**
Fixed:
**
 Breaking CCrc32 interface.

-
**
Fixed:
**
 Multiple Asset Panel issues caused by System::explorerData not being populated with provider subtrees on creation.

-
**
Fixed:
**
 Paused animation - no longer resumes playback when selecting it (again) in the Asset Panel.

-
**
Fixed:
**
 Issue with occasional animation jitter occurring when dragging animation event keys around the timeline.

-
**
Fixed:
**
 Issue with character animation starting to play when modifying various properties (even though the timeline in a paused state).

-
**
Fixed:
**
 Timeline widget not displaying its keys precisely at their logical position. Updated the default timeline key width to 16. Prevented the timeline in Character Tool from always resetting its zoom to full animation range when adding or modifying keys.

-
**
Fixed:
**
 Implemented a serialization rule which prohibits motion parameters from being duplicated in a blendspace setup.

-
**
Fixed:
**
 A signal/slot race condition crash - caused by in PropertiesPanel::m_propertyTree sometimes trying to revert to an expired object when loading/reloading character files. Instead Property Tree is now safely refreshed in a subsequent OnExplorerSelectionChanged handler.

-
**
Fixed:
**
 Bug which caused the "Additional Extraction" section to get glitched when modifying dependent blendspace properties. List of parameters is now limited to only those which support extraction.

-
**
Fixed:
**
 Issue with input fields under the "Animation Layers" section not getting properly updated in certain scenarios when editing blendspaces.

-
**
Fixed:
**
 Improved serialization of parameter overrides under the "Examples" section. Size of the value fields have been adjusted. Labels with names of corresponding parameters have been added. Value overrides are now properly referencing their parameter types by IDs rather than indices and persist through changes to dependent blendspace properties to mitigate various non-intuitive behaviors.

-
**
Fixed:
**
 Issue with animation layer properties and blendspace properties displaying different names for the same parameters. Removed duplicated parameter/name mappings. Removed an unused parameter flag.

-
**
Fixed:
**
 Multiple layout serialization bugs and simplified serialization logic. Window size is now properly restored after closing Character Tool and opening it again. Layout reset now restores default geometry of dock widgets on top of their composition.

-
**
Fixed:
**
 Issue with Character Tool - not reverting to its open assets when answered 'no' to the unsaved changes dialog.

-
**
Fixed:
**
 Issue with outdated animation entries being queried for blendspace parameter preview. Removed empty string from the blendspace parameter names to mitigate a common error occurring on blendspace reload.

-
**
Fixed:
**
 Issue in Character Tool with the indicator of changed content occasionally failing to disappear when performing a save.

-
**
Fixed:
**
 Blendspace Previewer does not work after undocking it from Character Tool (with mutual exclusive Viewport updates enabled).

-
**
Fixed:
**
 Fixed 'hide' checkbox for Vcloth.

-
**
Fixed:
**
 Engine freeze due to spawned spam messages - added WarningOnce to avoid countless numbers of same message.

-
**
Fixed:
**
 Scrubbing time - use all active animation layers for preview (similar to 'normal' play mode).

-
**
Fixed:
**
 Improved serialization of blendspace pseudo-examples and annotations in the Character Tool GUI:.

-
**
Fixed:
**
 Added a slider to change font size of rendered joint names.

-
**
Fixed:
**
 Issues in Character Tool when dragging keys in timeline.

##
Mannequin

-
**
Optimized:
**
 Reducing floor-grid rendering in Mannequin from hundreds of draw calls to 1 draw call.

-
**
Fixed:
**
 Issue with Mannequin Editor - sometimes becoming unresponsive for extended period of time when hovering the mouse cursor over its window.

-
**
Fixed:
**
 Multiple key selections in Transition Editor.

-
**
Fixed:
**
 Issue with certain edit operations in Transition Editor randomly affecting keys which were not selected by the user.

-
**
Fixed:
**
 Potential crash in Transition Editor - by preventing mandatory keys from being deleted from the transition properties track. The context menu delete option is now properly grayed out for all immutable keys.

-
**
Fixed:
**
 Improve randomization of mannequin options.

-
**
Fixed:
**
 Newly created tag definition files are not being displaying in the tag Definitions Editor.

-
**
Fixed:
**
 Crash (on opening Mannequin Editor).

-
**
Fixed:
**
 Depth buffer problems in Mannequin viewport.

-
**
Fixed:
**
 Brighter color for font in fragment selection window.

-
**
Fixed:
**
 Autoselect search filter bar on left click.

-
**
Fixed:
**
 Transition settings dialogue pops up behind mannequin main window.

-
**
Fixed:
**
 Crash in CMannTransitionSettingsDlg::PopulateComboBoxes.

-
**
Tweaked:
**
 Disabled default key selection - performed when opening the Transition Editor.

##
AI

##
AI System

-
**
New:
**
 Debug draw functions are getting NavMesh query filter from NavigationComponent with name "MNMDebugQueryFilter".

-
**
New:
**
 Islands connectivity is taking navigation annotations into account.

-
**
New:
**
 OffMeshLinks now also report their resulting start/end triangleIDs when being added via world positions.

-
**
New:
**
 (Vision Map) Added a Statistical Analysis mode

-
**
New:
**
 Added Navigation Markup Shape Component.

-
**
New:
**
 Added Navigation Query filter - allows filtering of accessible triangles and computing different costs of traversing triangles.

-
**
New:
**
 Adding support for navigation mesh markup, allowing different area types and flags per triangle.

-
**
New:
**
 Added maximum time to move in a certain direction to the PathFollowResult.

-
**
New:
**
 Added basic behavior tree nodes "Basic_MoveToPosition", "Basic_MoveToCover".

-
**
New:
**
 Added Audition Map for AI Listener Component.

-
**
New:
**
 Added Cover User Entity Component.

-
**
New:
**
 Added Behavior Tree Entity Component.

-
**
New:
**
 Added Listener Entity Component using AuditionMap.

-
**
New:
**
 Added Observer Entity Component using VisionMap.

-
**
New:
**
 Added Faction Entity Component using FactionMap.

-
**
New:
**
 Added Navigation Entity Component.

-
**
New:
**
 Added IMNMCustomPathCostComputer interface to allow for game-side path-cost computations; propagates through the whole request chain and is used by the CMNMPathFinder.

-
**
New:
**
 (AISystem) New Entity extended flag, specifying that the Entity's geometry should be excluded from NavMesh generation.

-
**
New:
**
 Expose boundary and exclusion volumes information as part of MNM tile generator extension parameters.

-
**
Refactored:
**
Moving AI specific code from Entity implementation to AI Component preparation for update optimization.

-
**
Refactored:
**
 Added base interface classes to AI Components so they can be created and used in code.

-
**
Refactored:
**
 Added NavMesh query filter to all functions from Navigation system that need it.

-
**
Refactored:
**
 Added SSnapToNavMeshRulesInfo which tells how the pathFinder should snap start/end points onto the NavMesh.

-
**
Refactored
**
: Exposed update calls to some AI systems - so there can be more fine grained control when they are updated.

-
**
Refactored:
**
 (CoverSystem) CoverUser is now created for every Entity that is registered to the CoverSystem.

-
**
Refactored:
**
 (CoverSystem & MovementSystem) Usage changed to 'movement ability' in movement system.

-
**
Refactored:
**
 Added FactionReactionChanged callback to FactionMap (AIObject dependency is removed from FactionMap.

-
**
Refactored:
**
 Collision Avoidance System is now independent of AIObject class.

-
**
Refactored:
**
 Setting NavMesh raycast default version to the most recent.

-
**
Refactored:
**
 Moving formations code from AISystem to separate files.

-
**
Refactored:
**
 Removed AIObject dependency from Navigation System.

-
**
Optimized:
**
 Navigation mesh visalizations (+ added new CVar 'ai_NavmeshTileDistanceDraw').

-
**
Optimized:
**
 Disabled behavior tree debug information by default for pure game.

-
**
Optimized:
**

Cleanup - Removed CodeCoverage.

-
**
Optimized:
**
Cleanup - Removed old navigation system.

-
**
Optimized:
**
Cleanup - Removed Walkability.

-
**
Fixed:
**
 Registering smart object as off-mesh link doesn't work after creating a new level.

-
**
Fixed:
**
 (Components) Completing and fixing Navigation Markup Shapes Component, synchronizing with exported data, more shapes possible per Component.

-
**
Fixed:
**
 Crash when generating NavMesh on dense terrain.

-
**
Fixed:
**
 Crash in canceling AI sequence when Actor was no longer valid.

-
**
Fixed:
**
 Crash in Raycast when visiting degenerate triangle.

-
**
Fixed:
**
 Compilation error (warning treated as error).

-
**
Fixed:
**
 Crash in Pathfinding: All Pathfinding processing requests are now checked when the NavMesh tile is changed.

-
**
Fixed:
**
 Possible crash on shutdown.

-
**
Fixed:
**
 AI Entity Component being saved with levels.

-
**
Fixed
**
: Building with OPTION_DEDICATED_SERVER.

-
**
Fixed:
**
 Correctly resetting Pathfinder state in Pathfinding Component after cancelling movement request.

-
**
Fixed:
**
 BT node QueryTPS didn't check for eTPSQS_Error, thus in rare cases failing an assert.

-
**
Fixed:
**
 AIObject.cpp did not compile with no uber files.

-
**
Fixed:
**
 Player was no longer registered in the AISystem after deserialization of the level when respawning from death, thus enemy AI would no longer be able to attack.

-
**
Fixed:
**
 Fixed NavMesh updating when placing objects near tile edges.

-
**
Tweaked:
**
 Navigation system is initialized and loaded sooner (before Schematyc is loading Entity Classes).

-
**
Tweaked:
**
 No longer failing an assert when "too many" Physical Entities would get checked (this is a limitation of the Physics System).

-
**
Tweaked:
**
 Support for older NavMesh versions.

##
UQS

-
**
New:
**
 Added facility to let the game override certain aspects that otherwise work automatically (with some default behavior/settings); 1: periodic update, 2: periodic 3D debug rendering, 3: default data source, 4: registration of StdLib.

-
**
New:
**
 CHubPlugin now updates the Hub (unless overridden by the game).

-
**
New:
**
 CHub now handles the startup and registration logic of DataSource_XML and StdLib (unless overridden by game).

-
**
New:
**
 Added settings-manager class to allow for tweaking several aspects and CVars of the UQS Core.

-
**
Refactored:
**
 Turned several CryEngineStaticModule projects into CryFileContainers - due to potential conflicts in the used memory manager when some functions in the .libs get inlined while others don't.

-
**
Optimized:
**
 (CQueryHistory) Adding new entries and inserting them into the right position is now done in aprrox. O(1) instead of O(n) time.

-
**
Optimized:
**
 (CItemList_Writable) Added CloneItems to support bulk-copying via a single virtual function call behind the scene.

-
**
Optimized:
**
 (CQuery_Regular) Time-slicing phase 3 now (in case we create debug visualization for "a lot" of items for e.g. 2000 points in 3D space).

-
**
Fixed:
**
 (History Inspector) Crash when clicking on "Clear History"

-
**
Fixed:
**
 CDebugRenderPrimitive_Text::Draw had eDrawText_800x600 set - was conflicting with the recent IRenderAuxGeom changes (text would then get drawn in odd locations).

-
**
Fixed:
**
 CItemListProxy_Writable<>::CloneItems was using untyped pointers.

-
**
Fixed:
**
 (CQueryManager) CTimeValue was using the wrong time unit for comparisons to detect time-budget excess.

-
**
Fixed:
**
 (CQuery_Regular) Frame-counting for the 1st phase was misleading (always said "1 frames" even if further phases could have already run in that very first frame).

-
**
Fixed:
**
 (CQueryHistoryInGameGUI) The history was no longer controllable via keyboard keys while being in-game.

-
**
Fixed:
**
 CQuery_Regular::UpdateDeferredTask had an assert that shouldn't have been included.

-
**
Fixed:
**
 CVariantDict::AddOrReplaceFromOriginalValue no longer causes a handled crash when the UQS plugin hasn't been loaded.

-
**
Fixed:
**
 Debug rendering of Entity's AABB was broken.

-
**
Fixed:
**
 Changed all places that were still relying on element names instead of element GUIDs; added the concept of a default query type via UQS::Core::IUtils::GetDefaultQueryFactory for when creating a new query in the Sandbox Editor.

-
**
Tweaked:
**
 Added new CVar "uqs_printTimeExcessWarningsToConsole" to suppress emitting warning messages due to time excess to the console.

-
**
Tweaked:
**
 Added profile markers at various places.

-
**
Tweaked:
**
 Now displays whether an evaluator is "cheap" or "expensive".

-
**
Tweaked:
**
 (CQueryBase) Timing measurements are more precise.

-
**
Tweaked:
**
 Added better detection to warn about query time-budget excess.

-
**
Tweaked:
**
 (Query_Regular) One too many deferred evaluation cycles were started when the final result set was potentially known already (which could have resulted in unnecessary work being done).

-
**
Tweaked:
**
 (History Inspector) Now also shows the file name of the loaded history in the window title.

##
Audio

##
Middleware Updates

-
Updated to Fmod Studio 1.10.04.

-
Updated to Wwise SDK v2017.2.2 build 65553.

-
Updated to Fmod Studio API version 1.10.02.

-
Updated Oculus spatializer for Wwise from 1.17.0 to 1.20.0.

##
Audio General

-
**
**
New
**
:
**
Audio parameter and switch implementation for SDL Mixer.

-
**
New:
**
 Added Occlusion Component.

-
**
New:
**
 Added Environment Component.

-
**
New:
**
 Added Preload Component.

-
**
New:
**
 Added Listener Component and fixed Listener for ModelViewPort.

-
**
New:
**
 AudioSpotComponent now has a random offset property.

-
**
New:
**
 AudioSpotComponent now works correctly when multiple instances of the Component are added to an Entity.

-
**
Refactored:
**
 Removed the logger class and made the Audio System responsible for handling the audio specific logging. As a result introduced a new interface method IAudioSystem::Log. Updated all implementations accordingly to use the new Cry::Audio::Log instead.

-
**
Refactored:
**
 Deleted AudioAreaComponent.

-
**
Optimized:
**
 Removed the 10ms restriction for the updating of object velocity controls - that's now synced to the external thread.

-
**
Optimized:
**
 AudioObjectManager now calculates Listener specific data that is needed by Audio Objects and their propagation processors.

-
**
Optimized:
**
 Listeners now use the deltaTime calculated in the Audio System to calculate their logarithmic decay towards zero.

-
**
Optimized:
**
 Removed deltaTime parameter from CryAudio::Impl::IImpl::Update method as it wasn't used/useful by/for implementations.

-
**
Optimized:
**
 Removed the now obsolete CVar s_TickWithMainThread.

-
**
Optimized:
**
 If external thread falls below 30 fps the audio thread will decouple and stay at 30 fps.

-
**
Optimized:
**
 Generally optimized the Audio System execution by syncing it roughly to external thread pass - this has optimized occlusion query as it doesn't issue as many raycast requests.

-
**
Fixed:
**
 Wwise implementation - did not load the convolution reverb plugin properly.

-
**
Fixed:
**
 Now take into account if occlusion results should be accumulated or not during very first sample run.

-
**
Fixed:
**
 Audio Listeners now update their name if the owning Entity's name was changed.

-
**
Fixed:
**
 Parameters were not updated in Fmod 1.10.02.

-
**
Fixed:
**
 Added missing warnings about unknown XML tags to middleware implementations.

-
**
Fixed:
**
 Added missing warnings for duplicated switches and parameters.

-
**
Fixed:
**
 False error warnings - because of empty connections of "do_nothing" trigger. Added class CDoNothingTrigger and execute triggers on CATLTriggerImpl instead of CATLAudioObject to prevent this.

-
**
Fixed:
**
 An Audio Object's absolute velocity decay wasn't forwarded to its absolute_velocity parameter.

-
**
Fixed:
**
 (Renderer) Audio aux rendering (flickering issue).

-
**
Fixed:
**
 SExecuteTriggerData ctor did not properly forward the Entity ID for determining the current environments.

-
**
Fixed:
**
 Bug where the Wwise implementation didn't properly set the global object and Listener IDs.

-
**
Fixed:
**
 Shutdown crash on dangling Wwise cookie during EndOfEvent callback.

-
**
Fixed:
**
 Error message when stopping events in either Fmod or SDL_mixer implementations.

-
**
Fixed:
**
 Bugs found by SCA.

-
**
Fixed:
**
 Added missing unregister calls to recently changed and introduced audio CVars.

-
**
Fixed:
**
 Bug where an AreaAmbienceSound doesn't get started when teleported into the area.

-
**
Fixed:
**
 Removed the ENTITY_FLAG_EXTENDED_AUDIO_DISABLED flag in IEntity - was causing a bug where a sound doesn't get stopped when the flag has been set while a sound is still playing.

-
**
Fixed:
**
 Bug where a ListenerComponent keeps listening to sounds when setting is inactive.

-
**
Fixed:
**
 Global changes weren't applied in Wwise 2017.1.0.

-
**
Fixed:
**
 Only enable Oculus based HRTF support if Oculus SDK is present.

-
**
Fixed:
**
 Removed some interface methods from the IAudioSystem interface.

-
**
Fixed:
**
 File monitor in ACE.

-
**
Fixed:
**
 An assert where debug display tried to access the adaptiveOcclusion value before it was determined.

-
**
Fixed:
**
 Debug filters didn't work on debug text of Audio Objects - it now works like the debug info of the Audio Event Manager and Audio Object Manager including virtual voice behavior when s_ShowActiveAudioObjectsOnly is set.

-
**
Fixed:
**
 Altering values of AudioSpot used in Schematyc Entity - jump into game and exit causes crash.

-
**
Tweaked:
**
 Updated to Fmod Studio 1.10.04.

-
**
Tweaked:
**
 Updated to Wwise SDK v2017.2.2 build 65553.

-
**
Tweaked:
**
 Audio Listener Component received the parent Entity's name (this confused people). Now named "Audio Listener" however, the underlying Listener object still holds the following naming format for debugging purposes "audio_listener_<entityname>_<entityId>".

-
**
Tweaked:
**
 Updated Oculus spatializer for Wwise from 1.17.0 to 1.20.0.

-
**
Tweaked:
**
 Made the parsing measurement log a comment instead of a warning.

-
**
Tweaked:
**
 Removed the timestamp from audio log messages as it was redundant.

-
**
Tweaked:
**
 Clarified statements for IAudioSystem::ExecuteTrigger and IAudioSystem::ExecuteTriggerEx in the interface documentation.

-
**
Tweaked:
**
 Updated to Fmod Studio API version 1.10.02.

-
**
Tweaked:
**
 Removed deprecated CVar "s_AudioProxiesInitType".

-
**
Tweaked:
**
 Added ability to set the Listener occlusion plane via CVar s_ListenerOcclusionPlaneSize. Increased the plane's default size from 15cm to 100cm.

-
**
Tweaked:
**
 Renamed audio logging CVar from s_AudioLoggingOptions to s_LoggingOptions.

-
**
Tweaked:
**
 Audio logging is now enabled by default by setting s_LoggingOptions to abc.

-
**
Tweaked:
**
 Moved the "s_DebugDistance" CVar to production only code block - it is not needed in release builds.

-
**
Tweaked:
**
 Introduced CVar "s_AccumulateOcclusion" that allows for altering how occlusion values encountered by a raycast are treated. The default behavior was and is to accumulate, meaning the CVar's default is 1. If disabled only the highest value is considered.

-
**
Tweaked:
**
 Adjusted names of Audio Component icons to follow the same naming convention.

-
**
Tweaked:
**
 Area Component can now choose between Audio Listeners and area triggering entities.

-
**
Tweaked:
**
 Renamed CVar "s_ShowActiveAudioObjectsOnly" to "s_HideInactiveAudioObjects".

-
**
Tweaked:
**
 Occlusion rays are affected by object debug filter.

-
**
Tweaked:
**
 Draw Object Standalone Files is now "s_DrawAudioDebug j" (was "i").

-
**
Tweaked:
**
 Draw Occlusion Rays is now "s_DrawAudioDebug i" (was "h").

-
**
Tweaked:
**
 Draw Occlusion Ray Labels is now "s_DrawAudioDebug h" (was "g").

-
**
Tweaked:
**
 Added "s_DrawAudioDebug n" to apply filter, also to inactive object debug info.

-
**
Tweaked:
**
 Added "s_DrawAudioDebug m" to hide Audio System memory info.

-
**
Tweaked:
**
 Separated drawing of distance value from label in Audio Object debug info (distance is "s_DrawAudioDebug g").

-
**
Tweaked:
**
 All enabled debug info of an object is shown (if at least one info type matches s_debugFilter).

-
**
Tweaked:
**
 Renamed command "s_SetRtpc" to "s_SetParameter".

-
**
Tweaked:
**
 Updated formatting of audio debug info.

-
**
Tweaked:
**
 Added color coding to Audio Object debug info.

-
**
Tweaked:
**
 Display current values of debug filter, radius and draw option in top debug info.

-
**
Tweaked:
**
 Removed deprecated CVars "s_AudioTriggersDebugFilter" and "s_AudioObjectsDebugFilter".

-
**
Tweaked:
**
 Added CVar "s_DebugFilter" that works with all types of audio debug info.

-
**
Tweaked:
**
 Added CVar "s_DebugDistance" to limit the draw distance of Audio Object debug info.

##
Audio Controls Editor

-
**
New:
**

Changed folder structure of audio assets and ACE XML files. Each middleware writes its data into their own ACE files.

-
**
New:
**

Added file monitor for ACE files, audio assets and middleware projects.

-
**
New:
**

Prevent renaming, moving and deleting of default controls.

-
**
New:
**

Added default controls to pause all and resume all sounds.

-
**
New:
**

Added event actions "pause" and "resume" for Fmod Studio and SDL Mixer events.

-
**
New:
**

Added fade-in and fade-out times for SDL Mixer events.

-
**
New:
**

Audio parameter and switch implementation for SDL Mixer to control event volumes.

-
**
New:
**

Added support for Fmod Studio VCAs.

-
**
New:
**

Added description property for libraries, folders and Audio Controls.

-
**
New:
**

Added attribute filtering.

-
**
New:
**

Added icons and tool tips in Audio Controls Panel for items with no connections and their parents.

-
**
New:
**

Added icons and tool tips in Audio Controls Panel for libraries, folders and switches that don't contain any Audio Controls.

-
**
New:
**

Show/hide "Add" button menu items depending on current selection.

-
New: Added "State" to "Add" button menu.

-
**
New:
**

A state can be created by dropping a middleware parameter or VCA onto a switch.

-
**
New:
**

Added sorting in tree views.

-
**
New:
**

Parent items of invalid connections are also indicated now - makes errors easier to find.

-
**
New:
**

Added option to create a parent folder of the current selected system controls.

-
**
New:
**

Added context menu options to load and unload preload requests. Only available for global non-auto-loaded preloads.

-
**
New:
**

Added context menu options to expand and collapse selected items.

-
**
New
**
: Added context menu option to select system controls from connected middleware controls.

-
**
New:
**

Added context menu option to select middleware control from Connections Panel.

-
**
New:
**

Added context menu option to open containing folder (for middleware items), that are files on disk.

-
**
New:
**

Execute Audio Trigger on mouse double-click.

-
**
New:
**

Added button to refresh the Audio System.

-
**
New:
**

Added window docking.

-
**
Fixed:
**

Crash when middleware is switched after ACE has been closed.

-
**
Fixed:
**

Crash when closing and re-opening the ACE while a connection was selected.

-
**
Fixed:
**

Crash when parsing ACE file - that contains a default parameter which already exists.

-
**
Fixed:
**

It was not possible to save an automatically generated default controls library.

-
**
Fixed:
**

Audio Controls did not get reloaded when opening the ACE.

-
**
Fixed:
**

Could not delete write protected files.

-
**
Fixed:
**

Empty libraries could not get saved.

-
**
Fixed:
**

Default controls could not be saved in completely empty projects.

-
**
Fixed:
**

Renaming a library or folder did not show a warning when reloading without saving.

-
**
Fixed:
**

Placeholder connections disappeared from Inspector Panel on file monitor update.

-
**
Fixed:
**

Pressing "Save" button of Audio System Settings dialog marked all libraries wrongly as modified (that contain controls of the current middleware).

-
**
Fixed:
**

Modified states did not get set to unmodified after saving.

-
**
Fixed:
**

Newly created empty folders did not get set to unmodified after saving.

-
**
Fixed:
**

When a newly created control gets deleted without being saved, its properties will still be displayed after reloading Audio Systems data.

-
**
Fixed:
**

It was possible to rename Audio Controls to empty strings.

-
**
Fixed:
**

Audio System Controls could get dropped on their current parent item (which would mark it wrongly as modified).

-
**
Fixed:
**

When a preload request gets deleted there was no dialog to ask for refreshing the Audio System after saving.

-
**
Fixed:
**

After saving a modified library that contained unmodified preload requests, a dialog wrongly opened to refresh the Audio system.

-
**
Fixed:
**

It was possible to have states or folders with the same name in the same parent by moving them from one parent to another.

-
**
Fixed:
**

Drag and drop between system controls at the first hierarchy level inside libraries didn't work.

-
**
Fixed:
**

Controls could get wrongly connected if user drops data too quickly.

-
**
Fixed:
**

Multi-rename of Audio Controls.

-
**
Fixed:
**

Multi-edit of connection properties didn't work.

-
**
Fixed:
**

New libraries created from menu did not get selected automatically.

-
**
Fixed:
**

Reset control type, filters correctly when a new Audio Control gets added while filtering is active - so the new control gets selected automatically.

-
**
Fixed:
**

Controls of different types could not have the same name.

-
**
Fixed:
**

States and folders with different parent items could not have the same name.

-
**
Fixed:
**

Setting a connection property to its current value marked it as wrongly modified.

-
**
Fixed:
**

Connection states were not updated when middleware project path was changed.

-
**
Fixed:
**

Changing a property of a connection will indicate in the UI that the connection is not selected anymore.

-
**
Fixed:
**

Properties Panel didn't show connections of selected system control after it was closed and re-created.

-
**
Fixed:
**

"Remove Connection" context menu in the Connections Panel appeared even if no connection was selected.

-
**
Fixed:
**

Adding a new connection via drag and drop was slow.

-
**
Fixed:
**

Mute and unmute triggers did not work if the user triggered them directly.

-
**
Fixed:
**

It was possible to execute a trigger, delete a control and save libraries while in editing mode.

-
**
Fixed:
**

Text filter in Middleware Controls Panel didn't expand hierarchy of matching items.

-
**
Fixed:
**

Project path in preferences can now only get changed for middleware that have projects.

-
**
Fixed:
**

Audio System controls not supported could get added by the selected middleware implementation.

-
**
Fixed:
**

SDL Mixer "start" connection properties were shown even if the action type was not "start".

-
**
Fixed:
**

SDL Mixer controls did not update their connection status when all their connections were removed.

-
**
Fixed:
**

SDL Mixer Max attenuation distance could have been smaller than min attenuation distance.

-
**
Fixed:
**

Wrong loop count indication in SDL Mixer.

-
**
Fixed:
**

Console spam of default parameters in SDL Mixer.

-
**
Fixed:
**

Fmod Studio parameters could not get assigned to environments.

-
**
Fixed:
**

Fmod Studio folders and mixer groups were always marked wrongly as not connected.

-
**
Fixed:
**

Wwise stategroups and switchgroups were always marked wrongly as unconnected.

-
**
Fixed:
**

Wwise parameters connected to environments had no multiplier and shift properties.

-
**
Fixed:
**

Wwise switches and states could wrongly get connected to environments.

-
**
Tweaked:
**

Renamed "RTPC" to "Parameter".

-
**
Tweaked:
**

Force global scope on default controls.

-
**
Tweaked:
**

Removed internal default controls from XML.

-
**
Tweaked:
**

Hide internal default controls in ACE (that should not be connected to any middleware control).

-
**
Tweaked:
**

Automatically select and edit new added library, folder or control.

-
**
Tweaked:
**

Automatically select new connection that was added via drag and drop in Connections Panel.

-
**
Tweaked:
**

Tree view items keep their expanded and selected state after a refresh.

-
**
Tweaked:
**

Save and restore last selected connections of system controls until the data gets reloaded.

-
**
Tweaked:
**

Selecting a system control also selects its first connection if no other connection was previously selected.

-
**
Tweaked:
**

Indicate each modified control with an * in its tree view.

-
**
Tweaked:
**

"Save" button for Audio Controls is only enabled when changes have been made.

-
**
Tweaked:
**

"Save" button in Audio System Settings is only enabled when the project path gets changed.

-
**
Tweaked:
**

"Ok" button in resource selector is only enabled when an Audio Control is selected.

-
**
Tweaked:
**

Removed option to override activity radius.

-
**
Tweaked:
**

Removed obsolete activity radius properties from ACE UI.

-
**
Tweaked:
**

Removed "Save" option from context menu - it was misleading for the user as it saved all libraries and not just the selected library.

-
**
Tweaked:
**

Added warning for unsaved changes when switching middleware and option to save modified libraries.

-
**
Tweaked:
**

Disable ACE UI when no valid middleware is loaded.

-
**
Tweaked:
**

Sort tree view after a control has been renamed.

-
**
Tweaked:
**

Added notification in preferences - if the selected middleware does not support projects.

-
**
Tweaked:
**

Change mouse cursor while saving and reloading.

-
**
Tweaked:
**

Moved preferences button to the drop down menu.

-
**
Tweaked:
**

Adjusted layout of preferences dialog.

-
**
Tweaked:
**

Replaced library and folder icons.

-
**
Tweaked:
**

Sort middleware controls by type before sorting them by name.

##
Audio Resource Selector

-
**
New:
**

Added context menu with "Execute Trigger" option.

-
**
New:
**

Added clear button to text filter.

-
**
New:
**

Added sorting.

-
**
Fixed:
**

"*" was shown for changed and unsaved libraries and error colors for placeholder connections.

-
**
Fixed:
**

It was possible to select libraries and folders.

-
**
Fixed:
**

Opening the resource selector for a different control type (than before), then the previously selected control could get wrongly assigned.

##
DRS (Dynamic Response System)

-
**
New:
**
 SetGameToken action did not warn about incorrect variable types.

-
**
New:
**
 Improved UI for signal history.

-
**
New:
**
 Added more flexibility to set the value of GameTokens from the DRS.

-
**
Fixed:
**
 Issue where ResponseSystem.cpp static and global initializes a class defined in ActionSpeakLine.cpp.

-
**
Fixed:
**
 Crash in ResponseManager after removing an actor with the signals queued for processing.

-
**
Fixed:
**
 SetGameToken action was only working correctly for Floats.

-
**
Fixed:
**
 Missing callback flag for standalone files.

-
**
Fixed:
**
 Scrollbar not working in the variables widget when auto-update was active.

##
Core/System

##
Engine General

-
**
New:
**
 Introduced new VR interaction Component.

-
**
New:
**
 Introduce new roomscale VR Camera Component.

-
**
New:
**
 Move default primitives from template assets to default Engine assets, use as default Mesh Component object.

-
**
New:
**
 (IArea) Added IsPointInside.

-
**
New:
**
 Added CVar to change origin of coordinates provided on mouse wheel scroll.

-
**
New:
**
 Added a method to create a new timer with a unique Id.

-
**
New:
**

Added Windows API disk usage information to DiskProfiler.

-
**
New:
**
 (AutoTesting) Watch dog thread for detecting freezes over a certain amount of time.

-
**
New:
**
 (AutoTesting) Headless client mode.

-
**
New:
**
 (CVar) Add command sys_dump_cvars to dump all CVars to disk.

-
**
New:
**
(ProfVis) Added Thread Analyzer Tool. The tool can analyze a batch of frame(s) files and look for similarity within a given thread with some constraints. This will be useful to analyze the frame profiler data we get from QA.

-
**
New:
**
(ProfVis) Added filter total time per thread. Shows the accumulated time of the current filter per thread.

-
**
Refactored:
**
Clean up of unused CVars.

-
**
Refactored:
**
 Remove older file headers and include guards.

-
**
Refactored:
**
 Clarify use of Entity transform flags/reasons for in the Entity interfaces by using the CEnumFlags structure.

-
**
Refactored:
**
 Added stl::find_and_erase_all_if. Removed redundant stl::append_unique.

-
**
Refactored:
**
 _smart_ptr const correctness support, copy assignment fix, unit tests.

-
**
Refactored:
**
 Extracted polygon triangulation code from WaterVolumeRenderNode into a TPolygon2D class, in GeomQuery.h. Extended CArea Shape functionality to compute side normals and allow open shapes (for random point generation only).

-
**
Refactored:
**
 Use CryVariant in ScriptAnyValue.

-
**
Refactored:
**

Replaced sleep with CrySleep where appropriate.

-
**
Optimized:
**
Refactor Eentity event and updates for ~1.5 - 2x performance improvement - better scaling with many Entity Components.

-
**
Optimized:
**
 Remove unused Timeout Manager.

-
**
Optimized:
**
 (BootProfiler) Remove block size from 356bytes to 80bytes. Do not preallocate fixed string for arguments as it is not used most of the time. At 4680 records per pool saves ~1.3Mb ... with 900+ pools active just on boot up this saves a lot.

-
**
Optimized:
**
 (Yasli) Use stack string for improved performance (speed up Sandbox Editor startup time by 90ms).

-
**
Fixed:
**
Case where replacing an Entity Component would leave a dangling pointer in update Listeners.

-
**
Fixed:
**
 Every logged collision event requiring a look-up of the script proxy (iterate through all Components) for both source and target Entities.

-
**
Fixed:
**
 New Components no longer being able to receive immediate collision events.

-
**
Fixed:
**
 Action map groups could override the same action name.

-
**
Fixed:
**
 Potenial crash when sorting Entity Event Listener.

-
**
Fixed:
**
 Issue where Components could be in two different Editor categories with the same name.

-
**
Fixed:
**
 Issue where Components could not be created using a base interface ID.

-
**
Fixed:
**
 Null pointer de-reference when using Chinese IME on Windows 10.

-
**
Fixed:
**
 Components using the same base address when loaded from disk.

-
**
Fixed:
**
 Components loaded from disk not being correctly initialized.

-
**
Fixed:
**
 Restored pieces = setup for breakable objects.

-
**
Fixed:
**
 Windows keys being disabled by default - use g_disableWinKeys=1 to return to previous behavior.

-
**
Fixed:
**
 Missing light bounce for point lights.

-
**
Fixed:
**
 Assert for unique/not required in yasli smart_ptr serialisation code.

-
**
Fixed:
**
 Remove self-assignment.

-
**
Fixed:
**
 Cost-correctness of a string.

-
**
Fixed:
**
 ProcessEvent not passing event as a const reference.

-
**
Fixed:
**
 Slots containing characters are offset by the Entity matrix, not the Entity slot - resulting in bboxes present at the wrong point.

-
**
Fixed:
**
 Legacy Light Entities floating above ground when dragged into a level.

-
**
Fixed:
**
 (UI Cursor) Make the mouse cursor changeable via CVar.

-
**
Fixed:
**
 Ref-counter copy constructors must reset ref to 0.

-
**
Fixed:
**
 Inability to re-activate Particle Componentwithout reloading if the particle was disabled by default.

-
**
Fixed:
**
 Changing the Volume Class does not update a Game Volume correctly.

-
**
Fixed:
**
 Missing property setting when turning a Game Volume into a different Game Volume type.

-
**
Fixed:
**
 Mesh and Primitive Components using incorrect Entity slot ids.

-
**
Fixed:
**
 Schematyc objects not triggering Start node when spawned dynamically after gameplay has started.

-
**
Fixed:
**
 'Open Editor' icon not appearing next to particle fields.

-
**
Fixed:
**
 Inability to specify material for Geometry Components.

-
**
Fixed:
**
 (CECR) Crash caused by inactive cameras not being correctly disabled.

-
**
Fixed:
**
 Controller input doesn't work with the default input Component.

-
**
Fixed:
**
 PS4 pad doesn't work on windows machines.

-
**
Fixed:
**
 Quat was not properly initialized in debug builds.

-
**
Fixed:
**
 PoolAllocator was choosing non-power-of-2 alignment for some type sizes.

-
**
Fixed:
**
 Newer Schematyc based Components relying on the legacy IID system - the IID function is now no longer needed for new Components.

-
**
Fixed:
**
 Schematyc package not being deregistered - preventing possible crash on shutdown.

-
**
Fixed:
**
 Issue where during load, Components being created and initialized sequentially - instead of being created in one batch and then initialized thereafter.

-
**
Fixed:
**
 Inability to reliably query other Schematyc Components inside the Initialize call. We now add a Schematyc Object's Components without initializing them, and then go through all Components again to initialize them in the added order.

-
**
Fixed:
**
 HeapAllocator.Array now aligns both beginning and end of allocations for safe SIMD access.

-
**
Fixed:
**
 ENABLE_GFX_VIDEO compilation.

-
**
Fixed:
**
 Let Entity be de-activated after Component event mask has changed.

-
**
Fixed:
**
Made IEntity::MoveSlot ignore self as the target.

-
**
Fixed:
**
Screenshots being taken in screen resolution instead of render resolution in Sandbox Editor.

-
**
Fixed:
**

CSystem::GetRootFolder returning an empty string.

-
**
Fixed:
**

FrameProfiler toggle.

-
**
Fixed:
**
 Sandbox E
ditor screenshot creation.

-
**
Fixed:
**

Windows 7 entering sleep mode while using a PS4 gamepad.

-
**
Fixed:
**
CBinaryXmlNode::getAttr and CXmlNode::getAttr did not match and reported different values depending on if a file was read from binary or lose locations, also the methods will now return "false" if an entry existed but was essentially an empty string.

-
**
Fixed:
**
 (Build) Wrong directory used in post build copy of OrbisLauncher.

-
**
Fixed:
**
 (Bootprofiler) Ensure start time is taken when a record block is initialized and not prior (potentially allocating a whole bucket of records).

-
**
Fixed:
**
 (Yasli) Fix heap corruption.

-
**
Tweaked:
**
Move EEntityEvent to namespace for Doxygen documentation, mark global namespace event as deprecated.

-
**
Tweaked:
**
 Move generate cubemap button to the top of the Environment Probe Component.

-
**
Tweaked:
**
 Added API examples for the preview rendering.

-
**
Tweaked:
**
 Introduce API examples for IEntity::Load* functions.

-
**
Tweaked:
**
 Introduce additional API examples.

-
**
Tweaked:
**
 Add 'applyImmediately' option to CAdvancedAnimationComponent::SetCharacterFile, always load new character from disk.

-
**
Tweaked:
**
 Clean up of CEntityComponentLuaScript.

-
**
Tweaked:
**
 Introduce unit tests for checking valid Entity world and local transformation.

-
**
Tweaked:
**
 Add new ESYSTEM_EVENT_LEVEL_LOAD_ENTITIES event - useful for spawning Entities before load from disk.

-
**
Tweaked:
**
 Support comparison between CryStringT and CryStackStringT.

-
**
Tweaked:
**
 Correct legacy game object extension implementations to specify event mask.

-
**
Tweaked:
**
 Added animation speed property to the Animated Mesh Component.

-
**
Tweaked:
**
 Remove dead helpers for getting classes and comparing Entity identifiers by class.

-
**
Tweaked:
**
 Update README.md to point users to CMake documentation instead of WAF.

-
**
Tweaked:
**
 Added Spawn and Remove Entity functions for Schematyc use.

-
**
Tweaked:
**
 Cleaned CPU analysis info log output.

-
**
Tweaked:
**
 (XBox) Re-enabled 7th core usage for Durango.

-
**
Tweaked:
**

Allowed viewing of .log files while they are being used on Windows.

-
**
Tweaked:
**
 (XBox)
Upgraded XBox One XDK to latest version (Nov 17).

-
**
Tweaked:
**
 (AutoTesting) Allow watchdog to be set in cfg.

-
**
Tweaked:
**
 (AutoTesting) Unit test system turns failed asserts and fatal errors into test failure for the running test.

-
**
Tweaked:
**
 (AutoTesting) Fix time demo deferred loading bug.

-
**
Tweaked:
**
 (AutoTesting) Failing unit test actively triggers debug breakpoint.

-
**
Tweaked:
**
 (AutoTesting) Refine unit test report content for equality/approx. value comparison, append missing comments and documentation.

-
**
Tweaked:
**
 (AutoTesting) Fix problem - time demo is not starting when command is queued after loading map.

-
**
Tweaked:
**
 (AutoTesting) Improve CryUnitTest output formatting to better support pointers.

##
Common

-
**
**
New
**
:
**
Introduce new CryAPIExamples module to compile Doxygen snippets.

-
**
Refactored:
**
 Deprecated macros that create GUIDs from two integers.

-
**
Refactored:
**
 Unify CryGUID conversions from and to string.

-
**
Refactored:
**
 Allow creation of enum serialization spec for already declared enums.

-
**
Refactored:
**
Remove CryGUID helper.

-
**
Fixed:
**
 Wrong return type check after call to GetFileAttributesExW.

-
**
Fixed:
**
 Singleton pattern used in CryCommon which resulted in one instance per DLL.

-
**
Fixed:
**
 Fixed yasli handling of enum classes of a smaller size than sizeof(int).

-
**
Tweaked:
**
 Document IPersistentDebug.

-
**
Tweaked:
**
 Document IProjectManager.

-
**
Tweaked:
**
 Move action map manager interface to CryCommon.

-
**
Tweaked:
**
 SNetObjectId not receiving Doxygen comments.

-
**
Tweaked:
**
 Move Mannequin interfaces to CryCommon for Doxygen support, document common types.

-
**
Tweaked:
**
 IStatObj not using correct Doxygen style comments.

-
**
Tweaked:
**
 Add default values to the SFogVolumeProperties structure.

-
**
Tweaked:
**
 INetContext, IRenderer and IPhysicalWorld not having Doxygen pages generated.

-
**
Tweaked:
**
 Tweak CRY_DEPRECATED define to allow use on classes, use [[deprecated]] in case of C++ 14.

-
**
Tweaked:
**
 Add copy constructor to CHashedString.

-
**
Tweaked:
**
 Temp. disable a failing test.

##
System

-
**
New:
**
 (Linux) Added simple crash handler python script.

-
**
New:
**
 (Linux) Allow overriding GCC and Clang versions (done by the Kit in QtCreator).

-
**
New:
**
 Added support for deferring execution of a console command until it has been registered, used for .cryproject commands.

-
**
New:
**
 Added new 'sys_ignore_asserts_from_module' command for ignoring asserts from an individual module.

-
**
New:
**
 Moved all profile CVars into ProfileSystem.cpp, where they belong, renaming class members to match the CVars and eliminating  unnecessary code.

-
**
New:
**
 Added CVars profile_row and profile_col (to position text) and profile_min_display_ms (to customize time threshold). Don't display peaks if profile_peak_display = 0. Fixed height check after render cleanup.

-
**
New:
**
 Export BootProfiler into the Chrome trace format.

-
**
New:
**
 Added CVar sys_system_timer_resolution to allow control of System Timer Resolution on windows.

-
**
Refactored:
**
Move render & render end from CryAction to CrySystem.

-
**
Refactored:
**
 Move render begin from CryAction to CrySystem.

-
**
Refactored:
**
 Move manual frame step controller from CryAction to CrySystem.

-
**
Refactored:
**
 Move start of update to CrySystem ( DoFrame() ).

-
**
Refactored:
**
 Move Engine init to CrySystem, change CryAction into an Engine module.

-
**
Refactored:
**
 Remove option to not create a console.

-
**
Refactored:
**
 Remove deprecated FUNCTION_PROFILER, FRAME_PROFILER, STALL_PROFILER and replace with CRY_PROFILE_FUNCTION, CRY_PROFILE_SECTION, CRY_PROFILE_SECTION_WAITING.

-
**
Refactored:
**
 Correct spelling mistake CSystemEventListner -> CSystemEventListener.

-
**
Refactored:
**
(XBox) Removed useless checks in CLog::CreateBackupFile and refactored to make use of XDK API CopyFile2 on Durango.

-
**
Optimized:
**
 (JobSystem) Run jobs created on any worker rather than only a worker. - prevents a single worker ending up with all the work and not being able to share it to other 'starved' workers. Note: Jobs created in jobs will have immediate execution priority (true before, however the work was not shared to other workers which is now the case).

-
**
Fixed:
**
Mouse cursor visible on alt tab and fix double cursor visible on startup.

-
**
Fixed:
**
Alt tab mouse cursor window lock.

-
**
Fixed:
**
 Command line not being executed when running the shader cache generator.

-
**
Fixed:
**
 CVar Whitelist not working anymore.

-
**
Fixed:
**
 OOM handling when cleaning up bucket allocator.

-
**
Fixed:
**
 Linux Clang compilation with C++14.

-
**
Fixed:
**
 Crash 'SaveLevelStatistics' without any map loaded results in crash COctreeNode::GetObjectsByType.

-
**
Fixed:
**
 Frame pacing in release builds.

-
**
Fixed:
**
 Using WhiteList without checking in _RELEASE.

-
**
Fixed:
**
 Potential nullptr access.

-
**
Fixed:
**
 Potential shutdown crash in profiling code.

-
**
Fixed:
**
 Modules not being unloaded on failure to initialize.

-
**
Fixed:
**
 (RC) Engine not starting with special characters in path.

-
**
Fixed:
**
 Crash in boot profiler on Sandbox Editor exit.

-
**
Fixed:
**
 PrepareOcclusion now uses the correct render camera during freeze.

-
**
Fixed:
**
 Vec3 * Matrix34 must return a Vec4.

-
**
Fixed:
**
 UnitTest MathVector, corrected tolerance value. Disabled vector timing via ifdef, improving compile times.

-
**
Fixed:
**
 Crash when string is located right at the end of the memory page and the next page is not accessible.

-
**
Fixed:
**
 Startup crash due to GameDLL being loaded and unloaded during initialization.

-
**
Fixed:
**
 Inconsistent setting of global environment's dedicated server option.

-
**
Fixed:
**
 Wrong warning missing thread configuration when only common configuration is defined.

-
**
Fixed:
**
 Inconsistent unattended mode support, sometimes showing alerts even if the user prevented this.

-
**
Fixed:
**
 Message boxes appearing inconsistently and across different platforms (sometimes not appearing at all in pure game mode).

-
**
Fixed:
**
 Clipboard breaks when running 3 or more instances of CRYENGINE simultaneously.

-
**
Fixed:
**
 Implmementation of ilog2 on Clang and GCC by using IntegerLog2 from BitFiddling.h on all compilers.

-
**
Fixed:
**
 (Orbis) Debug compilation.

-
**
Fixed:
**
 Engine starting without a project when migration was not possible.

-
**
Fixed:
**
 Cannot execute console commands from the .cryproject file.

-
**
Fixed:
**
 Crash on start-up if .cryproject file did not exist.

-
**
Fixed:
**
 Inability to load .cryproject from disk in release builds.

-
**
Fixed:
**
 Binary XML nodes not supporting cloning - now returns itself since the nodes are readonly anyway.

-
**
Fixed:
**
 Releasing render pipeline when the renderer is released.

-
**
Fixed:
**
 Loading of newer .cryproject versions causing a complete override of the file with dummy values.

-
**
Fixed:
**
 No asset directory detected error when migrating from legacy sys_game_folder workflow to .cryproject.

-
**
Fixed:
**
 Engine would silently start without project folder and/or assets - now shows errors to the user.

-
**
Fixed:
**
 Assert when attaching remote console.

-
**
Fixed:
**
 Engine root being added as a pak mod - resulted in files in Engine root being constantly searched for, causing slowdowns and unrelated files added to file browsers. Additionally added %EDITOR% pak alias to avoid future issues with loading Editor assets.

-
**
Fixed:
**
 Plugins not being unloaded in the inverse order of loading.

-
**
Fixed:
**
 (PS4) Cubemap descriptors.

-
**
Fixed:
**
 (XBox) Upsample to read sRGB.

-
**
Fixed:
**

(XBox) Z-target downsampling.

-
**
Fixed:
**
(XBox) Missing backbuffer clears.

-
**
Fixed:
**
 (XBox) Texture swizzling.

-
**
Fixed:
**
 (XBox) Font uploads.

-
**
Fixed:
**
 (XBox) Scaleform and backbuffer clears.

-
**
Tweaked:
**
 Document ISystem::GetCamera and SetCamera.

-
**
Tweaked:
**
 (Linux) Use clang 3.9 and gcc 6 by default.

-
**
Tweaked:
**
 (NoCopy) Remove non-default ctor and correctly delete copy ctor/operator and add NoMove.

-
**
Tweaked:
**
 (Linux) Add warning suppressions for gcc 7.2.

-
**
Tweaked:
**
 (Linux) Add warning suppressions for clang 5.0.

-
**
Tweaked:
**
 Prevented CPhysRenderer from indiscriminately drawing all debug geometry with the e_DrawInFrontOn flag enabled.

-
**
Tweaked:
**
 Project Manager now supports updating .cryproject with newly added default plugins from versions other than 0.

-
**
Tweaked:
**
 Introduced message box warnings if plugins failed to load.

-
**
Tweaked:
**
 Move IGameFramework::Run to CSystem::RunMainLoop.

-
**
Tweaked:
**
 (XBox) Remove special case where XB1 launcher needed to update the Engine manually.

-
**
Tweaked:
**
 Increase Windows timer resolution to reduce wait time within third-party APIs.

-
**
Tweaked:
**
 (XBox) Introduce Message Box support via CryMessageBox.

-
**
Tweaked:
**
 Sign binaries and DLLs.

-
**
Tweaked:
**
 Allow running Engine without a project - default to this behavior when unit testing.

-
**
Tweaked:
**
 (XBox One) Disable buffer and texture defragmentation.

-
**
Tweaked:
**
 PlatformOS shutdown issue.

-
**
Tweaked:
**
 Release build not loading .cryproject from command line problem.

-
**
Tweaked:
**
 (JobSystem) Create N-2 workers. Where N is the number of logical cores. Try to ensure that Main and Render thread do not get interrupted too much.

##
Entity System

-
**
New:
**
(DefaultEntities) Added Water Ripple Component.

-
**
New:
**
(DefaultEntities) Added Rain Component.

-
**
New:
**
Entity Component Spawn Serialization - port of prior game object functionality to Components.

-
**
New:
**
Added new Thruster Component: Apply continuous or sporadic impulses from a specific point on a physical entity!F Add new Vehicle and Wheel Components: Create wheeled vehicles using Schematyc.

-
**
New:
**
Added new Child Entity Component: Allows automatically spawning another Entity within a Schematyc class.

-
**
New:
**
Added new Physics Area Component: Allows simulating wind or overriding gravity in a shape.

-
**
Refactored:
**
(CryDefaultEntiites) Move reflected types and members to the headers in order to allow usage inside third-party templates as an almost header-only setup.
**

**

-
**
Refactored:
**
Remove global Entity event sink - now preferred to use listeners on individual Entities in preparation for larger Entity event optimization.

-
**
Optimized:
**
Improved the performance of the Entity Component helpers/icons in Sandbox Editor.

-
**
Optimized:
**
Use one allocation for all Entities and Components loaded from XML, resulting in one batch of contiguous memory.

-
**
Optimized:
**
Refactor Entity event and updates for ~1.5 - 2x performance improvement - scaling better with many Entity Components.

-
**
Fixed:
**
(DefaultEntities) Settings missing in Fog Volume Component.

-
**
Fixed:
**
(DefaultEntities) Access violation when calling Ragdollsize on a CharacterControllerComponent.

-
**
Fixed:
**
(DefaultComponents) Mesh Component doesn't reset after setting a new object.

-
**
Fixed:
**
 (DefaultEntities) FogVolume is missing some attributes.

-
**
Fixed:
**
 (DefaultEntities) OnCollision signal sends the wrong Entity.

-
**
Fixed:
**
 (DefaultEntities) Assigned animation on an Animated Mesh Entity does not playback in the viewport and in-game.

-
**
Fixed:
**
 (DefaultEntities) Projector Light is floating above the ground when dragged into the level.

-
**
Fixed:
**
BaseEntity Ccomponent showing up in the Inspector.

-
**
Fixed:
**
 Input Component doesn't register multiple input groups properly.

-
**
Fixed:
**
 Some Components didn't expose all functions to Schematyc.

-
**
Fixed:
**
 GetEntityIterator doesn't return a smart pointer which could lead to potential memory leak.

-
**
Fixed:
**
 Required Entity buffer size not accounting for Components due to incorrect XML parsing.

-
**
Fixed:
**
 Components using the same base address when loaded from disk.

-
**
Fixed:
**
 Components loaded from disk not being correctly initialized.

-
**
Fixed:
**
 Legacy Entity Component load resulting in an empty instance GUID.

-
**
Fixed:
**
 Legacy-Light-Entities floating above ground when dragged into a level.

-
**
Fixed:
**
 Components scale doesn't get saved properly.

-
**
Fixed:
**
 Entity removal sinks being able to prevent an entity from being deleted during full entity system unload.

-
**
Fixed:
**
 Entity's parent not being set on children until after their Components were initialized.

-
**
Fixed:
**
 Cases where  default Components were shut down too late.

-
**
Fixed:
**
 Inability to rotate the projector light Component's local transform.

-
**
Fixed:
**
 Inability to change Mesh Component type at run-time.

-
**
Fixed:
**
 Inability to re-activate Particle Component without reloading if the particle was disabled by default.

-
**
Fixed:
**
 Camera Component missing selection helpers.

-
**
Fixed:
**
 Environment Probe Component missing size indicator.

-
**
Fixed:
**
 CAdvancedAnimationComponent::SetMotionParameter not respecting motion parameter overrides coming from higher-level systems.

-
**
Fixed:
**
 Unresponsive fragment transitions when calling CAdvancedAnimationComponent::QueueFragment. Fixed a related memory leak issue.

-
**
Fixed:
**
 Inability to disable collisions on Physics Primitive Components.

-
**
Fixed:
**

Mesh and Primitive Components using incorrect Entity slot ids.

-
**
Fixed:
**
CEntity::PhysicalizeSlot not passing the slot's custom material to the newly created physical part.

-
**
Fixed:
**
Geometry Components stop casting shadows when duplicated.

-
**
Fixed:
**
Crash caused by dangling pointer in Substitution Component.

-
**
Fixed:
**
Properties of similar Entities cannot be displayed unless they are copies.

-
**
Fixed:
**
ENTITY_EVENT_PHYS_POSTSTEP event never being sent.

-
**
Tweaked:
**
(CryEntitySystem) Expose IEntity::GetWorldScale.

-
**
Tweaked:
**
(CryDefaultEntites) Change VR Interaction Component to use physics constraints.

-
**
Tweaked:
**
 (CryEntitySystem) Remove segmented world remnant logic and functions.

-
**
Tweaked:
**
 (DefaultEntities) Add view distance for Light Entities.

-
**
Tweaked:
**
(DefaultEntities) Add a resting option to the Ridigbody Component.

-
**
Tweaked:
**
Remove need for new Entity Components to define IID function.

-
**
Tweaked:
**
Implement Component unit tests to avoid regressions of older bugs that keep popping up.

-
**
Tweaked:
**
Avoid unnecessary copy for Entity return values.

-
**
Tweaked:
**
Add Spawn and Remove Entity functions for Schematyc use.

-
**
Tweaked:
**
 Correct invalid comments in default Components.

-
**
Tweaked:
**
 Move Entity storage from dynamically allocated vector to array within the system itself.

-
**
Tweaked:
**
 Remove specialized Entity event handling in CEntity::SendEvent in preparation for optimizations.

-
**
Tweaked:
**
 Remove IEntity::GetForwardDir caching.

-
**
Tweaked:
**
Expose ENTITY_EVENT_SPAWNED_REMOTELY, same as IGameObjectExtension::PostRemoteSpawn.

-
**
Tweaked:
**
Add IEntity helpers for removing the first or all instances of an Entity Component type in an Entity.

-
**
Tweaked:
**
Remove Entity link name character limit.

-
**
Tweaked:
**
Remove hardcoded EntityId limits. Now determined (based) on EntityId, EntitySalt and EntityIndex types - Default behavior is exactly the same as before with a maximum limit of 65533 entities.

##
CMake

-
**
**
New
**
:
**
Support building API examples without the Engine for auto compilation.

-
**
New:
**
 Use '_release' directory suffix when building release configuration within visual studio (previously needed to re-run CMake to set the output directory).

-
**
New:
**
Upgrade CMake to 3.10.1.

-
**
New:
**
 CMake now downloads the SDKs through Github if bootstrap is not possible.

-
**
New:
**
 Support Recode.

-
**
Refactored:
**
 Move PS4 SDK path detection into PS4-Clang.cmake, rather than in build_meta/build_with_cmake.py.

-
**
Refactored:
**
 Add include paths directly into .cmake files for Ninja builds.

-
**
Refactored:
**
 Add per-project non-uber option.

-
**
**
Fixed
**
:
**
Inability to build shader cache generator from a project solution.

-
**
Fixed:
**
 VR plugins enabled when SDK was not present.

-
**
Fixed:
**
 Sensor system not being built when PROJECT_GAMEHUNT is set, wrap in own namespace to be safe.

-
**
Fixed:
**
 Disable ScaleformHelper when building DedicatedServer.

-
**
Fixed:
**
 Building with OPTION_DEDICATED_SERVER on linux.

-
**
Fixed:
**
 OPTION_SANDBOX disabled too late.

-
**
Fixed:
**
 Where changed CMake options for Vulkan and HRTF weren't reflected by the CMake GUI, additionally fixed runtime file deployment of PortAudio dlls.

-
**
Tweaked:
**
 Always enable Release configuration in VS, automatically disable Sandbox Editor build.

-
**
Tweaked:
**
 Expose option to enable/disable the developer console in Release builds.

-
**
Tweaked:
**
 Add macro for automatically adding sources in directory.

-
**
Tweaked:
**
 Sign binaries and DLLs.

-
**
Tweaked:
**
 Add VS2017 options to cry_cmake.

-
**
Tweaked:
**
 Modify Win32 and Win64 batch files to allow both VS2015 or VS2017 for building.

##
Action General

-
**
New:
**
 Support loading levels from outside the levels folder - now identified as a folder with level.pak file inside.

-
**
**
Fixed
**
:
**
ENTITY_FLAG_LOCAL_PLAYER being replicated over the network.

-
**
Fixed:
**
 Inability to send bind Entities to the network unless they contained a legacy game object.

-
**
Fixed:
**
 Use lobby listen port as server port (only if lobby service is properly initialized).

-
**
Fixed:
**
 ManualFrameStep feature not working over the network.

-
**
Fixed:
**
 Crash on setting Entity position during destruction of multiplayer game.

-
**
Fixed:
**
 Crash due to uninitialized values.

-
**
Fixed:
**
 Handling of level paths in the level system.

-
**
Fixed:
**
 Engine shutting down when legacy context was not available.

-
**
Fixed:
**
 Crashes on dedicated server in Mannequin debug due to the missing renderer.

-
**
Fixed:
**
 Persistent debug not working in Sandbox Editor.

-
**
Fixed:
**
 Savegames can be loaded without writing the file extension in the console.

-
**
Fixed:
**
 Inability to build Engine + cryproject monolithically.

-
**
Tweaked:
**
 Mark IGame, IEditorGame and IGameStartup as deprecated.

-
**
Tweaked:
**
 Mark IGameObjectExtension as deprecated.

##
Flow Graph

-
**
New:
**
 Added a new flow node to get the current environmental preset.

-
**
Fixed:
**
 Multiple EntityInfo nodes cannot be attached to the QueryIsInContainer node.

-
**
Fixed:
**
 Closing the Module Ports Dialog via OK switches the active Flow Graph.

-
**
Fixed:
**
 Level modules won't be loaded in game launcher.

-
**
Fixed:
**
 Entities whose archetypes have been deleted are listed in every Flow Graph.

-
**
Fixed:
**
 Level Modules are broken after loading.

-
**
Fixed:
**
 A newly created node cannot be undone with CTRL+Z.

-
**
Fixed:
**
 Quick selection for FG-Nodes is broken.

-
**
Fixed:
**
 (CECR) Crash when using Entity:SpawnArchetype in a new project not using the legacy IGame interface.

-
**
Fixed
**
: (CECR) Possible crash when retrieving game token if graph was null.

-
**
Fixed:
**
 Prevent Entities that are part of a Prefab from being added to a Flow Graph and display a warning if the user tries to do so.

-
**
Fixed:
**
 (Schematyc) Physics SetParams FG node exposure to schematyc.

##
Game

-
**
New:
**
 Added function used for syncing game exported data from level paks when the level is loaded in Sandbox Editor.

-
**
Optimized:
**

Remove GameZero.cryproject and all references to GameZero from WAF and build scripts.

-
**
Optimized:
**

Remove old GameZero project, replaced with Blank game template.

-
**
Fixed:
**
 Reload tree cut shapes on each level load.

-
**
Fixed:
**
 Crash on shutdown after visiting the multiplayer lobby.

-
**
Fixed:
**
 A broken animation with the stationary machine gun.

-
**
Fixed:
**
 Wrong sound playing when entering a map for the first time.

-
**
Fixed:
**
 Where in multiplayer games the Audio Listener wasn't reactivated after killcam. Entities that are Audio Listeners can now also create aux Audio Objects.

-
**
Fixed:
**
 No longer attempt to call a missing script function.

-
**
Tweaked:
**
 Update .cryproject file to point to 'GameSDK' directory.

##
Schematyc

-
**
New:
**
 Added Breakable Joint Component.

-
**
New:
**
 Added new "Create per Client" option for Schematyc Entities - results in an instance being automatically created each time a client connects to the server.

-
**
New:
**
 Expose Vector3 Project and Reflect nodes.

-
**
New:
**
 Expose Negate and Sign nodes.

-
**
New:
**
 Added new GetEntityTranform, GetEntityPosition and GetEntityRotation schematyc functions.

-
**
New:
**
 Added an AudioFadingAreaComponent.

-
**
Refactored:
**
 Move Entity functions from Entity base Component to new Entity data type (renamed from EntityId).

-
**
Optimized:
**
 Allow soft dependencies to non-singleton Components.

-
**
Fixed:
**
 Find References of properties is broken.

-
**
Fixed:
**
 Find All References of signals is broken.

-
**
Fixed:
**
 Find and Find All References of actions is broken.

-
**
Fixed:
**
 Go to Schematyc button in Modular Behavior Tree.

-
**
Fixed:
**
 Schematyc freezes while material picking.

-
**
Fixed:
**
 Crash because of changed destruction order after Schematyc was moved to Engine.

-
**
Fixed:
**
 Schematyc Entity Components being created and initialized sequentially - instead of created in one batch and then initialized after.

-
**
Tweaked:
**
 Remove support for setting raw Component members via the Set node.

-
**
Tweaked:
**
Remove Flow Graph integration - currently too unstable due to not implementing Flow Graph events correctly.

##
Templates

-
**
**
Fixed
**
:
**
Rolling Ball template not synchronizing player's physical states over the network.

-
**
Fixed:
**
 Blank and plugin template not registering user created Entity Components.

-
**
Fixed:
**
 (ThirdPersonShooter) Fixed warning spam issue occurring during camera movement by introducing more inertia when toggling the state of Mannequin tags.

-
**
Fixed:
**
 ReflectType on CBulletComponent in all templates.

-
**
Fixed:
**
 ReflectType on CBulletComponent in ThirdPersonShooter template.

-
**
Fixed:
**
 Restore the network sync feature in the RollingBall template.

-
**
Tweaked:
**
 (ThirdPersonShooter) Introduced a simple mouse input smoothing filter to mitigate jerky motion when turning around.

##
Graphics and Rendering

##
Renderer General

-
**
New:
**
 Added a new debug mode to display shadow caster (e_shadowsDebug 4).

-
**
New:
**
 Cache shaders by each technique - avoids repeated disk accessing.

-
**
New:
**
 Borderless window mode.

-
**
New:
**
 Add CVar "r_profilerSmoothingWeight" to allow control over timed r_profiler values for easier visual debugging.

-
**
New:
**
 Made FocusMin available as parameter for Depth Of Field.

-
**
New:
**
 (Plugins) Added new light Entity UI parameter - "Link To Sky Color". Helps to simulate sky light through windows and have it consistent with TOD and GI.

-
**
New:
**
 Introduce async camera callback support (like we use for Oculus).

-
**
New:
**
 Switch to OpenVR SDK 1.0.7.

-
**
New:
**
 Added Omni Camera support - render full 360 view of world that could be exported to 360 camera.

-
**
New:
**
 ColorGrading is now applied to Flares during PostAAComposites.

-
**
New:
**
 Transparent objects can now be rendered with NEAREST flag.

-
**
New:
**
 Added new shadow bias mode that attempts to compute optimal bias without any manual settings.
**
NOTE:
**
 Highly experimental.

-
**
New:
**
 Added tiled shading based cubemap sampling for water volumes.

-
**
Refactored:
**
When adding a
**

**
new platform just need to add shaderlist file name to the GetShaderlistName function.

-
**
Refactored:
**
 (Vulkan) Correct fatal error message when two resource layout hashes collide.

-
**
Refactored:
**
 (Vulkan) Trigger a fatal error when the resource layout encoding does not have enough space to store it.

-
**
Refactored:
**
 Replacing r_shadersorbis, r_shadersdx10, r_shadersdx11, r_shadersGL4, r_shadersGLES3, r_shadersdurango, r_shadersVulkan CVars with r_ShaderTarget CVar which specifies the target to which shaders must be built for.

-
**
Refactored:
**
 Unify swapchain creation paths - now exclusively handled by render display context.

-
**
Refactored:
**
 Remove unnecessary duplicate code.

-
**
Refactored:
**
 Improving ElementPool interface.

-
**
Refactored:
**
 Using element pool for render views.

-
**
Refactored:
**
 New way for aux rendering.

-
**
Refactored:
**
 Dropping the flush function from IRenderAuxGeom as Submit does the same thing.

-
**
Refactored:
**
 The aux geometry command buffers can be submitted from any thread.

-
**
Refactored:
**
 Temporary depth textures throughout the renderer.

-
**
Refactored:
**
 Remove tempVecs/Matrs global states and refactor it into appropriate shadow info struct. Use new approach for volumetric scattering techniques.

-
**
Refactored:
**
 Refactor vertex format system.

-
**
Refactored:
**
 The input layout of all techniques using FullscreenTriVS as vertex shader.

-
**
Refactored:
**
 Streamed points for full screen triangles are produced in the shader.

-
**
Refactored:
**
 Removing all %_RT_PER_INSTANCE_CB_TEMP cases as it is true in the new pipeline.

-
**
Refactored:
**
 Refactor window management, adding support for resizing the window through Windows.

-
**
Refactored:
**
 Moving Vulkan constant descriptor set creation immediately after buffer creation.

-
**
Refactored:
**
PixFormat reference.

-
**
Refactored:
**
Some
**

**
profile labels (remove double entries, provide better names).

-
**
Refactored:
**
 Enable multi threaded rendering in Sandbox Editor.

-
**
Refactored:
**
 Global state and removed lots of unused code.

-
**
Refactored:
**
 Cleanup display context handling in Sandbox Editor.

-
**
Refactored:
**
 Cleanup screenshot and backbuffer copy code.

-
**
Refactored:
**
 Port remaining legacy pipeline rendering code to the new pipeline.

-
**
Refactored:
**
 Refactor Aux buffer handling and rendering.

-
**
Refactored:
**
 Remove unused shader reflection code.

-
**
Refactored:
**
 Cleanup renderer resource initialization and destruction.

-
**
Refactored:
**
 Add lambda command for renderthread and convert most rendering commands to lambda.

-
**
Refactored:
**
 Remove legacy immediate mode rendering functionality: FX_* functions,..

-
**
Refactored:
**
 Remove per-level shader cache support - not used since PS3 and X360 support removal.

-
**
Refactored:
**
 Using the safe version of sscanf.

-
**
Refactored:
**
 (Shaders) Adjusted distant terrain normal mapping fading.

-
**
Refactored:
**
 Ported AfterPost LDR/HDR rendering to new pipeline.

-
**
Refactored:
**
 Ported HalfRes rendering to new pipeline.

-
**
Refactored:
**
 Ported NearestDepthUpsample to new pipeline.

-
**
Refactored:
**
 Replacing all CryMakeUnique with stl::make_unique.

-
**
Refactored:
**
 Tone mapping shader is using texture2d instead of old sampler2d (ToneMapping.cpp is also affected).

-
**
Refactored:
**
 Changed ColorWriteMask to an enum lookup to support independent color write for MRT.

-
**
Refactored:
**
 Ported DepthFixup to new pipeline.

-
**
Refactored:
**
 Non-0 level depth access.

-
**
Refactored:
**
 Debug build pointer cast.

-
**
Refactored:
**
 Native resolution downsampling.

-
**
Refactored:
**
 Native resolution upsampling.

-
**
Refactored:
**
 Refactored code and variables for comprehension.

-
**
Refactored:
**
Rename bLocked to bAcquireLock in CRenderMesh::UpdateModifiedMeshes and CRenderMesh::ClearStaleMemory to make it easier to understand.

-
**
Refactored:
**
Convert globals of half type to floats, fixing shader compilation with compatibility mode off.

-
**
Refactored:
**
Update SkyPass technique to use new API, save sampler slots.

-
**
Refactored:
**
Update techniques ReprojectShadowMap, HUD3D.General, Downsample4x4, UpdateBloomRT to use newer API. Replace old arbitrary COLOR[n] semantic with new arbitrary S_VTarget[n] semantic.

-
**
Refactored:
**
Update TextureToTexture, Down/UpSample, Depth merge, Gaussian blur, SelectionSilhouetteHighlight, PostAA, LumaEdgeDetectionSMAA, NeighborhoodBlendingSMAA, BlendWeightSMAA, PostAAComposites, MsaaDebug, DebugPostAA techniques to use newer texture API, reduce sampler footprint.

-
**
Refactored:
**
Update PackVelocities, VelocityTileNeighborhood techniques to use newer texture API, reduce sampler footprint.

-
**
Refactored:
**
Update DownscaleDof, TileMinCoC, Dof, CompositeDof techniques to use newer texture API, reduce sampler footprint.

-
**
Refactored:
**
Update SSSSS_Blur technique to use newer texture API, reduce sampler footprint. Remove unused techniques: DeferredLightVolume, DeferredLightPass, DeferredDecal, DeferredCubemapVolumePass, DeferredCubemapPass, AmbientPass, FilterGBuffer.

-
**
Refactored:
**
Update SSReflection_Comp, SSDO_Filter techniques to use newer texture API, reduce sampler footprint.

-
**
Refactored:
**
Update Fog, HDR post processing techniques to use newer texture API, reduce sampler footprint.

-
**
Refactored:
**
Update SunShaftsGen, SunShaftsMaskGen techniques to use newer texture API, reduce sampler footprint.

-
**
Refactored:
**
Update DebugGBuffer, SSDO_Sampling techniques to use newer texture API, reduce sampler footprint. Remove no longer used techniques: ResolveStencilLegacy, ClearReservedStencil, MSAASampleFreqStencilMask, MSAACustomResolve, DeferredShadingPass, DeferredDecalVolume

-
**
Refactored:
**
Update SSR_Raytrace, HeightMapAOPass technique to use newer texture API, reduce sampler footprint.

-
**
Refactored:
**
 Shadowpool update code and correctly respect ShadowMapFrustum::nShadowPoolUpdateRate.

-
**
Optimized:
**
 Allow instance-data only update of compiled render objects.

-
**
Optimized:
**
 Delayed destruction of temporary depth targets.

-
**
Optimized:
**
 Optimize WaterVolume - detect if camera is inside volume and 'under water'.

-
**
Optimized:
**
 Avoid unnecessary renderpass updates.

-
**
Optimized:
**
 Made texture format query static.

-
**
Optimized:
**
 Removed persistent pixelformat pointer storage from texture.

-
**
Optimized:
**
 Add PixFormat query-cache (results don't change at run-time).

-
**
Optimized:
**
(Shaders) Removed deprecated ParticlesCustomPass.cfi which were causing compilation errors to occur even though unused.

-
**
Fixed:
**
 Revived missing HDR debug mode that shows average luminance info.

-
**
Fixed:
**
 Race-condition in permanent-render-object management.

-
**
Fixed:
**
 I
ncorrect calculation of delayed deletion offset.

-
**
Fixed:
**
Sending the correct shaderlist filename to remote shader compiler for Vulkan shaders.

-
**
Fixed: (
**
DX12) Fixed lost device state when transitioning into fullscreen from windowed and minimized state.

-
**
Fixed:
**
 sys_job_system_proiler 1 aux drawings.

-
**
Fixed:
**
 Crash when deleting water volumes - because of immediate release of CRElement.

-
**
Fixed:
**
 (XBox One) D3D memory leak.

-
**
Fixed:
**
 (PS4) The "r_driver should match shader target" fatal error issue for PS4 shader cache generation.

-
**
Fixed:
**
 (PS4) Shader cache generation failure. r_Driver=Dx11 is allowed for Orbis shader target flag.

-
**
Fixed:
**
 Vulkan shader cache generation. The encoded resource layout size is reduced by half. It is base64 encoded and sent with request line to remote shader compiler.

-
**
Fixed:
**
 Permanent render object's general pass transform to be overwritten by shadow passes.

-
**
Fixed:
**
 Textured aux geometry color.

-
**
Fixed:
**
 Crash when clicking generate cubemap in Sandbox Editor.

-
**
Fixed:
**
 Low spec crash in Sandbox Editor.

-
**
Fixed:
**
 (Shaders) Fixed SS shadow on grass.

-
**
Fixed:
**
 (Shaders) Fixed too dark SS shadows from the grass.

-
**
Fixed:
**
 Aux rendering lag and flickering issue in Character Tool.

-
**
Fixed:
**
 Screen space shadows missing in the distance.

-
**
Fixed:
**
 Aux geometries depth rendering issue.

-
**
Fixed:
**
 Cursor may get stuck in previous client window dimensions after changing the resolution.

-
**
Fixed:
**
 Incorrect calculation of delayed deletion offset.

-
**
Fixed:
**
 (Stretch region pass) UV layout of ePrim_FullscreenQuadCentered is flipped.

-
**
Fixed:
**
 Silence vertex attribute mismatch warning.

-
**
Fixed:
**
 Changing both resolution and fullscreen mode at the same time does not work properly.

-
**
Fixed:
**
 Resolution not adjusted correctly when exiting fullscreen.

-
**
Fixed:
**
 Avoid division by zero.

-
**
Fixed:
**
 D3DHWShaderCompiling.cpp: Fix compile error.

-
**
Fixed:
**
 Slightly better handling of CResFile and in-memory cache.

-
**
Fixed:
**
 (PostAA) Missing texture attachment.

-
**
Fixed:
**
 Fixed r_showdyntextures debug view.

-
**
Fixed:
**
 Restores the original CreateCone method behavior and make Light Entity shadow frustum drawing consistent.

-
**
Fixed:
**
 Cone mesh used by aux - to have the cone's apex point to the center.

-
**
Fixed:
**
 Nearest handling in some attachments and fix nearest shadows.

-
**
Fixed:
**
 dds from tif is not generated after the run-time update of tif file.

-
**
Fixed:
**
 Shader cache loading issue.

-
**
Fixed:
**
 Missing cubemaps issue.

-
**
Fixed:
**
 Shader cache path.

-
**
Fixed:
**
 RELEASE level chainloading.

-
**
Fixed:
**
 Decal flicker during LOD dissolve.

-
**
Fixed:
**
 Case where textures were not reloaded correctly after being updated at runtime.

-
**
Fixed:
**
 Race condition ClearJobResources not waiting for meshSubRenderMesh jobs to finish.

-
**
Fixed:
**
 Re-enable supersampling in Sandbox Editor.

-
**
Fixed:
**
 Fix non-existent DDS warning being output immediately after a texture was queued with RC.

-
**
Fixed:
**
 Rendertargets (PostFXMaps) not being recreated when switching from supersampling 2 to 1.

-
**
Fixed:
**
 (PostAA) Invalid syntax in PostAAComposites_PS.

-
**
Fixed:
**
 Scalform loading and Vulkan's woodland black screen issue.

-
**
Fixed:
**
 FPEs by initializing uninitialized things.

-
**
Fixed:
**
 VK render's gaussian blur shader issue.

-
**
Fixed:
**
 Edge case crash when no shaders are loaded.

-
**
Fixed:
**
 Depth value of the drawn images.

-
**
Fixed:
**
 Use texture copy for PostAA depth texture, correct supersampled RenderView viewport size.

-
**
Fixed:
**
 Missing sampler state which causes an issue in Vulkan's volumetric fog.

-
**
Fixed:
**
 Double Destroy call on index/vertex buffer fix.

-
**
Fixed
**
: m_inlineConstantBuffers gets correctly filled after resolution change.

-
**
Fixed:
**
 (Shaders) Fix depth lookup in sun shafts generation.

-
**
Fixed:
**
 'Show object icons on top of objects' - working again.

-
**
Fixed:
**
 Unsynchronized access to renderer resources from render-loading thread during loading.

-
**
Fixed:
**
 Incorrectly translating BGRA device format to BGRX when using sRGB.

-
**
Fixed:
**
 (Shaders) SSDO depth sampling. Remove unused sampler from HDRBloomGaussian.

-
**
Fixed:
**
 Re-enable forward shadow setup. Fixes volumetric fog shadows.

-
**
Fixed:
**
 Add missing move of SCompiledRenderPrimitive::instanceConstantBuffers in move constructor. Add missing reset of SCompiledRenderPrimitive::instanceConstantBuffers in SCompiledRenderPrimitive::Reset.

-
**
Fixed:
**
 Visarea/portal culling.

-
**
Fixed:
**
 Null constant buffer null descriptor set issue.

-
**
Fixed:
**
 The allocated per instance constant buffer size is corrected.

-
**
Fixed:
**
 Missing Sandbox Editor aux geometry rendering issue with geometries submitted from non-main/render thread.

-
**
Fixed:
**
 Not updated aux geometries command buffer cameras when the display's properties are changed.

-
**
Fixed:
**
 Asserts in CStretchRegionPass.

-
**
Fixed:
**
 Crash due to failed constant buffer allocation on DX11.

-
**
Fixed:
**
 Shutdown order of RenderElements and SDynTexture pool is correct now: Removing custom shutdown code in CREWaterOcean.

-
**
Fixed:
**
 Asynchronous dispatch for compute skinning.

-
**
Fixed:
**
 Compute skinning tangent-frame calculation.

-
**
Fixed:
**
 Compute skinning resource-allocation and resource-set assignment.

-
**
Fixed:
**
 Meta main menu background.

-
**
Fixed:
**
 Sandbox Editor not compiling Engine assets by default when auto RC invoke was on.

-
**
Fixed:
**
 DX12 async upload violation (initial data for CGpuBuffer).

-
**
Fixed:
**
 SVOGI in Vvulkan renderer.

-
**
Fixed:
**
 Bug that occurs sometimes when the shaders are sent to be compiled by the remote compiler.

-
**
Fixed:
**
 Tiled shading issue in Vulkan renderer.

-
**
Fixed:
**
 Debug draw modes with negative values.

-
**
Fixed:
**
 (Shaders, Water) Fixed wrong normal-vector.

-
**
Fixed:
**
 Volumetric shadow in Vulkan renderer.

-
**
Fixed:
**
 Purple artifacts on road decals that use POM self shadowing by masking out blue color channel in the color write mask.

-
**
Fixed:
**
 Render target width being half as wide as it should be.

-
**
Fixed:
**
 Async camera injection not updating render view.

-
**
Fixed:
**
 Frame rate being limited to 60 fps in loading screen - causing head tracking lag.

-
**
Fixed:
**
 Incorrect calculation for seconds until photons hit the screen.

-
**
Fixed:
**
 Black artifacts appearing in some test levels - caused by unbound texture resource to copyTexToTex shader.

-
**
Fixed:
**
 Invalid positions in RenderMesh.GetRandomPos; read f32 or f16 as needed, without CachePos. Caused threading errors.

-
**
Fixed:
**
 Blendstates in Vulkan implementation.

-
**
Fixed:
**
 Wrong blending state for the decals. Chrominance blending has been dropped to remove weird effects that can occur.

-
**
Fixed:
**
 (Shaders) SVOGI point light bounce fix.

-
**
Fixed:
**
 Blendstate that can occur due to dual src blend being enabled in multiple render target slots.

-
**
Fixed:
**
 Crash which happens when SVO textures are not yet created.

-
**
Fixed:
**
 r_DeferredShadingTiled=3.

-
**
Fixed:
**
 Crash due to creating texture in loading thread.

-
**
Fixed:
**
 (Shaders) "Couldn't compile HW shader 'Hair@HairPS".

-
**
Fixed:
**
 Cubemap generation issue.

-
**
Fixed:
**
 Tiledshading volumelistgen execute too early.

-
**
Fixed:
**
 Flickering debug information in Sandbox Editor.

-
**
Fixed:
**
 Pass valid light name to profile label scope.

-
**
Fixed:
**
 Exporting decals with nullptr material issue.

-
**
Fixed:
**
 Debug information flickering issue.

-
**
Fixed:
**
 Disabled multi-threaded resource creation to allow sys_spec changes to succeed.

-
**
Fixed:
**
 Scene resolve of refractive objects not copying the target due to incomplete conditions.

-
**
Fixed:
**
 Release/build nullptr access when ShutDown.

-
**
Fixed:
**
 Depth-buffer resolution mismatch when initializing pipelines.

-
**
Fixed:
**
 Make sure material resource set for CREFogVolume contains valid resources.

-
**
Fixed:
**
 OpenVR plugin crashes on closing GameLauncher.

-
**
Fixed:
**
 Launcher doesn't close properly on quit.

-
**
Fixed:
**
 Disable depth fixup on PS4 - to circumvent GPU hang.

-
**
Fixed:
**
 Graphics-pipeline shutdown.

-
**
Fixed:
**
 Changed upper bound of call-back removal to prevent stack overflow.

-
**
Fixed:
**
 Nullptr-access when shader-creation fails.

-
**
Fixed:
**
 Texture-pointer invalidation by inverse weak-pointer pattern.

-
**
Fixed:
**
 Fatal error message when the renderer cannot create its device. It also shows correct message when a non-Vulkan GPU is used in combination with Vulkan renderer.

-
**
Fixed:
**
Warning in NC after map is loaded (Texture does not exist: texelspermeter.dds).

-
**
Fixed:
**
 All uses of RenderLights now use SetRadius to compute true illumination radius.

-
**
Fixed:
**
 The wrong write color mask used in Vulkan implementation.

-
**
Fixed:
**
 Enabling tone mapping pipeline gamma correction and illegal colors detection debugging features.

-
**
Fixed:
**
 Dissolving debug level of detail colors at transition points.

-
**
Fixed:
**
 Viewport switching with AA on.

-
**
Fixed:
**
 DX12 depth-readback crash.

-
**
Fixed:
**
 Aux-crash when viewport destruction.

-
**
Fixed:
**
 Main Viewport resolution mismatch.

-
**
Fixed:
**
 Secondary render viewport resizing.

-
**
Fixed:
**
 Secondary render viewport resizing.

-
**
Fixed:
**
 (Shaders) Fixing tangent-space reference frame for the Lightshaft.

-
**
Fixed:
**
 Wrong texture-type.

-
**
Fixed:
**
 Priority inversion in viewport rendering.

-
**
Fixed:
**
 Free backbuffers for custom contexts.

-
**
Fixed:
**
 Prevent light-reference invalidation caused by container-type.

-
**
Fixed:
**
 Assert in full screen primitive.

-
**
Fixed:
**
 Projectors when used with GI.

-
**
Fixed:
**
 Added additional checks for transparent nearest objects. Removed code that produced duplicate renderItems.

-
**
Fixed:
**
 (Shaders) Fix for particle DEPTH_FIXUP (deprecated constant was being used).

-
**
Fixed:
**
 Brushes with NEAREST flag now properly render.

-
**
Fixed:
**
 Possible crash on startup when PostAA copies PrevBackBuffer due to resource format mismatch.

-
**
Fixed:
**
 Bounding boxes were not updated with the skeletal animation.

-
**
Fixed:
**
 Particles now use the correct blend state for depth_fixup.

-
**
Fixed:
**
 Debug build.

-
**
Fixed:
**
 API-spec violation when flushing AuxGeom.

-
**
Fixed:
**
 Depth/stencil for scaleform.

-
**
Fixed:
**
 GBuffer debug visualization to work with deferred decals.

-
**
Fixed:
**
 Prevent shader precaching on Vulkan and PS4 (we cannot compile individual shaders without resource layout on these platforms).

-
**
Fixed:
**
 Crash on dedicated server when setting a rendering CVar.

-
**
Fixed:
**
 Supersampling and downsampling too dark.

-
**
Fixed:
**
 Viewport rendering "bleed".

-
**
Fixed:
**
 API-spec violation when resizing the viewport in the Sandbox Editor.

-
**
Fixed:
**
 Highlight pass PSO.

-
**
Fixed:
**
 SelectionID pass depth buffer.

-
**
Fixed:
**
 Per object depth test flag for silhouettes.

-
**
Fixed:
**
 Scene depth resolution for supersampling.

-
**
Fixed:
**
 Moon texture release.

-
**
Fixed:
**
 Removed debug asserts/breaks.

-
**
Fixed:
**
 DX12 validation error on startup: cannot access backbuffers in use by compositor/device.

-
**
Fixed:
**
 Use linear 16 bit history buffer for PostAA to prevent persistent artifacts in dark areas.

-
**
Fixed:
**
 (Shaders) Remove now obsolete hlslcc workarounds for unaligned variables in constant buffer.

-
**
Fixed:
**
 XBox One backbuffer format.

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
 Wrong failed flag check.

-
**
Fixed:
**
 Added stronger protection for threaded access of CRenderMesh:: s_MeshModifiedList.

-
**
Fixed:
**
Terrain detail materials texture filtering in the distance.

-
**
Fixed:
**
Crash in COctreeNode::MarkAsUncompiled.

-
**
Fixed:
**
Check for dirty outputs in CFullscreenPass::InputChanged

-
**
Fixed:
**
Depth-readback assert

-
**
Fixed:
**
Ground material is wrongly applied to objects such as spheres in vr_demo

-
**
Fixed:
**
Convert material to multi-material crashes (Sandbox.exe!CMaterial::UpdateHighlighting)

-
**
Fixed:
**
Warning "Vegetation object is not suitable for merging".

-
**
Tweaked:
**
 Improve multi-monitor window management, automatically switch output when the window is moved onto a new monitor.

-
**
Tweaked:
**
 Reduce flickering when entering fullscreen.

-
**
Tweaked:
**
 Correct warning and log formatting.

-
**
Tweaked:
**
 Replace custom path helpers with PathUtils.

-
**
Tweaked:
**
 (Shaders) Renamed spec opacity property in Illum shader for more clarity for Artists.

-
**
Tweaked:
**
 (Renderer) Added opacity slider for decal normal and specular blending to Illum shader.

-
**
Tweaked:
**
 Quad layer setup based on QA recommendations.

-
**
Tweaked:
**
 API settings for optimal performance and behavior.

-
**
Tweaked:
**
 Social screen implementation.

-
**
Tweaked:
**
 Add Sandbox Editor startup information for shader compilation to fix unclear startup "freeze" when all shaders need compiling.

-
**
Tweaked:
**
 Outputing a fatal error when the non-optional principle textures are missing.

-
**
Tweaked:
**
 Make legacy pipeline switches as cheap as possible until they are removed.

-
**
Tweaked:
**
 Completely defuse rendertarget stack level 0.

-
**
Tweaked:
**
 Use depth dilation for AA mode 3 as well to improve silhouettes.

-
**
Tweaked:
**
 Fixed BGR and 4-bit texture format expansion.

-
**
Tweaked:
**
 Added support for some exotic formats.

-
**
Tweaked:
**
 Changed texture array management to eTT_2DArray/eTT_CubeArray and added respective support for streaming.

-
**
Tweaked:
**
 Added option in the StretchRegionPass to blend the region in, instead of overriding the target's values.

-
**
Tweaked:
**
Remove artificial max decal count restriction.

-
**
Tweaked:
**
Fix and simplify shader cache generation build process workflow.

-
**
Tweaked:
**

Added missing description to e_debugdraw 8.

##
SVOGI

-
**
Fixed:
**
 Refactor SVOGI streaming.

-
**
Fixed:
**
 Analytical occluders z-fighting; Added e_svoTI_PointLightsBias CVar for simulation of more bounces.

##
Vulkan

-
**
Fixed:
**
 Assert on startup. Null constant buffer size needs to be at lest 256 bytes.

-
**
Fixed:
**
 Correctly enable depth bias dynamic state.

-
**
Fixed:
**
 Assert caused by CDeviceTexture::GetLayout returning no data.

##
Volumetric Clouds

-
**
Fixed:
**
 Shader runtime flag %_RT_SAMPLE2 is wrongly used to activate two functionalities of volumetric clouds.

##
3D Engine

-
**
New:
**
 (Renderer) Added option to compute sun shadows from static world using SVO ray tracing (e.g. this allows excluding all static objects from shadow maps).

-
**
New:
**
 Added CVar to set the minimum mass of a phys particle to do render mesh distance checks.

-
**
New:
**
 Added optional important flag to the SurfaceType.

-
**
New:
**
 (Sandbox Editor) Support for SVOGI offline voxelization.

-
**
New:
**
 Added new e_debugdraw mode to display per object max view distance.

-
**
New:
**
 Added proper viewDistRatio for decals + CVar consistent with other types (Brush, etc.).

-
**
Refactored:
**
 Added more information into the extended display info for SVOGI - number of bouncing point lights.

-
**
Refactored:
**
 Removed some obsolete code from Terrain Engine (border only mesh update).

-
**
Refactored:
**
 Fixed temp-data concurrent access.

-
**
Refactored:
**
 SVOGI refactoring.

-
**
Refactored:
**
 (CryAction) (CryAISystem) (Sandbox Editor) Completely removed deprecated Segmented World implementation.

-
**
Refactored:
**
 (Sandbox) Supported smaller heightmap unit size (down to 0.5m) for more detailed terrain.

-
**
Refactored:
**
 MovableBrush uses same Render function as Brush.

-
**
Refactored:
**
 Added CVar to control integration of object meshes into terrain mesh.

-
**
Optimized:
**
Per objects shadow maps ported to one pass scene graph traversal.

-
**
Optimized:
**
Cached shadow maps are ported to one pass scene graph traversal.

-
**
Optimized:
**
 Reorganized terrain rendering for less waiting in main thread.

-
**
Optimized:
**
 Enabled shadow gen jobs for brushes, vegetation and roads.

-
**
Optimized:
**
 (Renderer) One-pass scene graph traversal (single traverse submits render objects simultaneously into main and shadow render views).

-
**
Optimized:
**
 Locking pattern for temp-data.

-
**
Optimized:
**
 Fix object modifications while dynamic distance shadows were active causing a recompilation of the whole level's octree.

-
**
Optimized:
**
 Scene graph update/compiling by further splitting static and dynamic content.

-
**
Optimized:
**
 GI is disabled by default on non-desktop platforms.

-
**
Optimized:
**
 Heightmap sector mesh generation: border adjustment depending on current neighbor sectors LOD is replaced with static safety borders.

-
**
Optimized:
**
 Octree render content is now using ALL job worker threads for rendering the octree nodes.

-
**
Fixed:
**
 Assert for MovableBrushes ending up inside CObjManager::RenderObject.

-
**
Fixed:
**
 All Entities disappearing if too many shadow casting lights are visible.

-
**
Fixed:
**
 Missing GI color bounce from projectors in "static light" mode.

-
**
Fixed:
**
 Terrain segment border artifacts when soft depth test is used.

-
**
Fixed:
**
 Crash on opening a specific level.

-
**
Fixed:
**
 Re-enable omni-directional shadows.

-
**
Fixed:
**
 Log spam "RenderMesh not assigned" on dedicated server.

-
**
Fixed:
**
 Signed type mismatch.

-
**
Fixed:
**
 TempData-persistency being broken.

-
**
Fixed:
**
 StatObjRend: Clamp LodMax and LodMin read from CVars.

-
**
Fixed:
**
 (Physics)(AISystem) Getting height of the terrain from heightfield is now thread-safe - correct terrain heights are returned in NavMesh generation jobs.

-
**
Fixed:
**
 Issue with invalid shutdown order of Engine systems for e.g. Character system expects all references to resources it owns to be released by the point of its shutdown.

-
**
Fixed:
**
 Permanent-object instance-data dirtyfication caused by write-lock.

-
**
Fixed:
**
 Removed light radius calculation from animated light update.

-
**
Fixed:
**
 Heigtmap LOD in the distance (was too high in some cases).

-
**
Fixed:
**
 Issue where lights controlled by lightStyle using intensities of 0 were culled, because their effective radius became 0.

-
**
Fixed:
**
 Terrain mesh not updated after some Sandbox Editor operations.

-
**
Fixed:
**
 Remove immediate waiting of streaming for StatObjects.

-
**
Fixed:
**
 Crash in LightVolumes caused by light count exceeding local array bounds. Added constant for limit.

-
**
Fixed:
**
 Large precision improvement in CSkyLightNishita - potentially fixes assert.

-
**
Fixed:
**
 Using override material for rendering decal when it is not null.

-
**
Fixed:
**
 Improved RenderLight management: SetRadius now sets m_fRadius to computed illuminance distance (limited by clip radius argument). Illuminance threshold is controlled by CVar e_IlluminanceThreshold.

-
**
Fixed:
**
 Light volume issues, by removing obsolete thresholds for light intensity and radius. Replaced obsolete m_fBaseRadius with m_fClipRadius. Replaced incorrect and bloated CDLight.operator= (which omitted ShadowMaskIndex) with normal copy.

-
**
Fixed:
**
 Missing terrain holes.

-
**
Fixed:
**
 Removed 5cm quantization of terrain elevation (heightmap may appear up 5 cm higher now).

-
**
Fixed:
**
 Loading of old terrain format in launcher.

-
**
Fixed:
**
 GI voxelization opacity for vegetation: e_svoTI_VegetationMaxOpacity also now affects brushes with vegetation shader.

-
**
Fixed:
**
 Sets obj ID for subObjs on brushes with NEAREST flag.

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
 (VR) Oculus headset works, but GameLauncher.exe-window only shows a black screen.

-
**
Fixed:
**
 Cgf non-streamed loading.

-
**
**
Tweaked
**
:
**
Add sensible default values to rope render node parameters (same as Sandbox Editor uses).

-
**
Tweaked:
**
 Get better logging about Characters that have an invalid matrix (print character name and current position).

##
Particles

-
**
**
New
**
:
**
SpawnCount now has option for Max or Total particles emitted.

-
**
New:
**
 Wavicle emitters now respond to local wind and gravity areas. PerParticleForceComputation option selects computing area forces per particle (stored in acceleration and velocity fields), or per-emitter, averaged over local areas. Moved some functionality from Pfx1 ParticleEffect.h to ParticleEnviron.h, extended PhysEnviron functionality to compute average forces within a box.

-
**
New:
**
 Area shapes now respect vertex Z values for particle attachment. Fixed issues with open shapes and updating shapes.

-
**
New:
**
 Added SpawnParams (and Schematyc serialization) to allow emitters to ignore VisAreas and VisArea clipping. Replaced code which auto-registered by bounds centre when bounds didn't contain origin. Optimized bounds computation in Pfx2.

-
**
New:
**
 Added IParticleEffect.CreateAttributeInstance.

-
**
New:
**
 Extend IParticleAttributes API, add direct access to attribute TValue variant type, add Serialization and Execute functions. Simplified IParticleAttributes usage, removed switch statements, etc.

-
New
: Attribute refactoring and improvements: Effects have only AttributeTable. Emitters have AttributeInstance which binds dynamically to Table via name. Editing AttributeInstance presents Table as a fixed form with names. Editing Attribute Modifiers displays attribute selection as drop-down. Simplified AttributeValue to use CryVariant. Simplified Attribute Min/Max Values to use enabled values.

-
**
New:
**
 Particle Emitter Entity Component can edit effect attributes.

-
**
New:
**
 LocationGeometry now has AugmentLocation option (combines effect location volumes with attachment volume).

-
**
New:
**
 Implement attachment to Area shapes.

-
**
New:
**
 Replaced Feature update lists with Dispatcher objects.

-
**
New:
**
 Added custom Emitter Features, editable from particle Entity Component. For attachment, spawn volume, color, velocity, etc.

-
**
New:
**
 Particles can now attach to Area entities.

-
**
New:
**
 Feature LightSource now uses particle size for bulb size. Renamed LightSource.Radius param to ClipRadius because normally it should be left at infinity.

-
**
New:
**
 Refactored Pfx1 and Pfx2 stats to inherit from NumberVector - allows averaging over frames with float and int versions. Pfx1 stats now display below Pfx2 stats in the same format. Added emitter stats to Pfx1 along with Component. Restored CollectEffectStats function (with sorting).

-
**
New:
**
 Added feature Light Lens Flare.

-
**
New:
**
 Added FeatureAnglesAlign World mode. Simplified AlignType construction.

-
**
New:
**
 GPU particle counts.

-
**
New:
**
 Added TimeOfDay and ExposureValue global domains.

-
**
New:
**
 Added modifier global access and added level time into it.

-
**
New:
**
 Components don't need any feature to be able to work properly - adding default size, time and spawn features.

-
**
**
Refactored
**
:
**
Accessing instance data is automatically templated. SpawnEntries arrays now temporary. Spawn features now have virtual GetSpawnCounts, rather than giant templated SpawnParticles. Particle count scale from SpawnParams etc now properly applied after GetSpawnCounts calculation. Added Runtime.GetEmitLocation.

-
**
Refactored:
**
 Particle stats now track allocated and alive elements separately. Added info to ParticleProfiler file dump.

-
**
Refactored:
**
 CPU/GPU interface cleanup: Consistent naming between modules. Remove duplicate SComponentParams members. Simplify interfaces, new interfaces for module interoperation. .

-
**
Refactored:
**
 Component parenting improvements: Sort Components by dependency, replace ComponentIds with ComponentPtrs, rename symbols from "SecondGen" to "Child", simplify loops.

-
**
Refactored:
**
 Combined all Life features into one, compute Lifetime and InvLifetime together.

-
**
Refactored:
**
 Infinite values now displayed as "Infinity" in Sandbox Editor. Moved version fix code to VisibilityParams. Compile fixes.

-
**
Refactored:
**
 Restored proper unit scale for Lighting Diffuse value.

-
**
Refactored:
**
 Standardised implementation of params which have infinite/disabled state: Edited with an enable toggle, otherwise serialized with possible infinite value. Refactored TValue<TTraits> templates, unifying limits and conversion. Removed soft limits as they are not supported by PropertyTree.

-
**
Refactored:
**
 Replace iteration macros with range-based loops.

-
**
Refactored
**
: Renamed Modifiers Time Source to Domain.

-
**
Refactored:
**
 Keep Features in .cpp only files. Refactored default and exclusive feature implementations. Duplicate features are auto-disabled.

-
**
Refactored:
**

Refactored and simplified Runtime management, removed RuntimeRefs; instance code, replaced size_t with uint; AddRemove functions, SwapToEndRemove functions; SpawnParticles and GetSpawnCount functions; replaced SpawnData.delay with negative .timer value

-
**
Optimized:
**
 Moved some bounds computation to main thread for consistency, simplified expansion function.

-
**
Optimized:
**
 Improved job scheduling and synchronisation. e_ParticlesThread = 2 allows update jobs to sync later, and also allows ComputeVertices to perform update itself rather than waiting. e_ParticlesThread = 3 reschedules emitter jobs by visibility and gives ComputeVertices priority.

-
**
Optimized:
**
 SParticleFX objects now pre-load their effects. Detect and warn when particle effects and assets are loaded at runtime.

-
**
Optimized:
**
 More main-thread optimisations. Moved Emitter.PostUpdate and .IsAlive functionality to jobs.

-
**
Optimized:
**
 Improved Wavicle main thread performance: sped up Emitter.Update; moved BoundingBox and Stats computations into jobs; consolidated MainPreUpdate calls per effect; removed support for per Component jobs, only support fast per-emitter jobs; batched emitters into jobs based on maximum jobs-per-thread setting. Enabled starting and stopping >1 job in SJobSyncVariable.

-
**
Optimized:
**
 Update only living emitters.

-
**
Optimized:
**
 Speeded up GetRandomPos: Now GetRandomPoints fills array of points; composite objects group calls to their parts together; cache RandomPos array in RenderMesh during GetExtents.

-
**
Optimized:
**
 Streamlined SpawnParticles and GetSpawnCount functions. Replaced SpawnData.delay with negative timer value.

-
**
Optimized:
**
 Job Manager no longer creates not required Component list when set to emitter granularity.

-
**
Optimized:
**
 Job scheduling granularity. e_ParticlesThread = 1 (default): 1 job per emitter; 2: one job per Component; 3 (previous): multiple jobs per Component.

-
**
Optimized:
**
 GPU/CPU particle code integration.

-
**
Optimized:
**
 STempInitBuffer simplifies data initialization, allocates data only for spawned particles.

-
**
Optimized:
**
 Vectorised stream Fill functions. Reversed inheritance of IStream and IOStream, removed not required members from IOStream.

-
**
Fixed:
**
 Broken Audio Component.

-
**
Fixed:
**
 Emitter Activate issues. Parent particle now added only once.

-
**
Fixed:
**
 Several errors involving Emitter Features. Altered effect is now completely cloned for proper parenting. Component.SetParent cleans up children. Clearing Emitter Features now updates emitter. Emitter Features no longer flagged as changed when empty.

-
**
Fixed:
**
 Calculation of GPU max particle counts, including extra frame for particle life. Restore FeatureSpawnCount.duration default to 0.

-
**
Fixed:
**
 Potential null access in anim attachments.

-
**
Fixed:
**
 Drag was ignored with some feature settings.

-
**
Fixed:
**
 Only create RenderObjects as needed.

-
**
Fixed:
**
 Restarting of inactive emitters on sys_spec change.

-
**
Fixed:
**
 Crash caused by improper destruction order.

-
**
Fixed:
**
 Invalid float data in Spawn feature. Fixed zero-normalize in shape areas.

-
**
Fixed:
**
 Simplified modifier context handling. ModInherit now has a separate base type for proper class factory population.

-
**
Fixed:
**
 Crash caused by referencing deleted Components (e.g. during editing). Prevent registering empty emitters.

-
**
Fixed:
**
 Collision checks no longer move particles above terrain. Fixes SpawnOnCollide effects underground.

-
**
Fixed:
**
 Clean up IPhysicalEntity and IAudioObject data when killing emitters.

-
**
Fixed:
**
 Potential JobManager crash when changing levels.

-
**
Fixed:
**
 Zero particle submesh data when editing effect preventing dangling reference. Added SParticleDataTypeInfo.zeroClear option, simplified EParticleDataType declarations.

-
**
Fixed:
**
 Crash related to audio features.

-
**
Fixed:
**
 Crash on Emitter.Kill. Restored e_ParticlesProfiler display.

-
**
Fixed:
**
 Crash caused by force-deleting StatObjs.

-
**
Fixed:
**
 Ref-counting cycle that caused leaks and crashes.

-
**
Fixed:
**
 Angles3D.RandomSpin now works in local space.

-
**
Fixed:
**
 Crashes related to unactivated Components.

-
**
Fixed:
**
 Data corruption in particle update, incorrect scheduling of stats gathering and memheap checks, incorrect GPU stats gathering, incorrect bounds computations. Cleaned up some code.

-
**
Fixed:
**
 Emitters not updating due to incorrect Age function.

-
**
Fixed:
**
 Non-spawning of certain effects that incorrectly had restart periods. They now start just once (as before).

-
Fixed
: Rendering bug caused by delayed shader loading.

-
**
Fixed:
**
 Crash when child Component was disabled. Fixed error rendering zero-size decals.

-
**
Fixed:
**
 Disabled Components are again disabled (huge performance bug).

-
**
Fixed:
**
 Changed ChaosKeyV to match recent ChaosKey change and fixed unit test. Fixed assert in Pfx1 TextureTile.Correct.

-
**
Fixed:
**
 EnableByConfig feature.

-
**
Fixed:
**
 Bugs and reduced artifacts in LocationOmni rotation wrapping. SChaosKey now replaces seed with jumbled value instead of incrementing it every iteration, so eliminating repeated sequences when key seed changes by a small value each frame.

-
**
Fixed:
**
 Crash on deleting Component in Sandbox Editor.

-
Fixed
: CParticleContainer_RealId unit test, added Attribute unit tests.

-
**
Fixed:
**
 Emitter feature issues.

-
**
Fixed:
**
 SpawnParams.CountScale applies only to top-level Components.

-
**
Fixed:
**
 Assert for FillData type-check. Added fast assert in Vec3 stream writing for valid data.

-
**
Fixed:
**
 Proper ref-counting for GeomRef particle/object attachment.

-
**
Fixed:
**
 Prevent out of bounds access in specular probe texture array.

-
**
Fixed:
**
 Non-functioning presets. Mesh presets now have sphere default, ribbon has anti-gravity.

-
**
Fixed:
**
 Crash from null attribute pointer.

-
**
Fixed:
**
 TimeSource domain fixes. Per-instance contexts now always access parent data. Only parent age data is "age-anti-aliased".

-
**
Fixed:
**
 Serialization conversion bug.

-
**
Fixed:
**
 Some example effects in Engine Assets not working properly.

-
**
Fixed:
**
 Particle Entity Components now reliably activate and deactivate emitters without creating duplicates. Emitters no longer spawn particles when inactive.

-
**
Fixed:
**
 Restored env lighting to particles. Restored unit-scale Diffuse parameter.

-
**
Fixed:
**
 Serialize "enabled" state of features.

-
**
Fixed:
**
 Crash during GPU particles editing: class members moved for correct destruction order.

-
**
Fixed:
**
 Restored AnimBlend and DrawOnTop functionality.

-
**
Fixed:
**
 Audio would not play if emitter was Primed. Now plays if emitter starts anytime during its emitter lifetime.

-
**
Fixed:
**
 Potential crashes caused by multi-threaded static function data init.

-
**
Fixed:
**
 Emitters did not always create unique seed if spawned from Engine.

-
**
Fixed:
**
 AudioTrigger start/stop events caused by improper conversion from previous format.

-
**
Fixed:
**
 LightSource now includes light radius in bounding volume calculation.

-
**
Fixed:
**
 Random seed not being exposed to UI spawn parameters.

-
**
Fixed:
**
 Many Spawn issues. Spawn fraction correctly computed for all mortal effects. Age increment correctly computed for short durations. Non-default duration properly read from older versions.

-
**
Fixed:
**
 UpdateAll routine uses proper update range after AddRemove. Fixed other errors and crashes.

-
**
Fixed:
**
 Changed "auto" to "auto const&" for Component iteration - fixes occasional incorrect ref count and erroneous deletion due to multi-threading.

-
**
Fixed:
**
 Restored AnimBlend and DrawOnTop functionality.

-
**
Fixed:
**
 Fixed audio stop events.

-
**
Fixed:
**
 Restored function of e_ParticlesMaxScreenFill.

-
**
Fixed:
**
 Orientation fix for placed Pfx1 converted emitters.

-
**
Fixed:
**
 Pfx1 conversion fixes. Fixed emission direction. Don't replace already-loaded effects. Don't create inactive effects. Refactored some interfaces.

-
**
Fixed:
**
 Invalid data stream initialization.

-
**
Fixed:
**
 CParamMod now correctly converts values during serialization.

-
**
Fixed:
**
 Fixed array overflow in GetExtents.

-
**
Fixed:
**
 Fixed Pfx1 conversion issues: AudioSource, LifeImmortal and added node positions.

-
**
Fixed:
**
 Re-added default Particle Component template.

-
**
Fixed:
**
 AudioTrigger crash. Restricted EOcclusionType enum to allowed values.

-
**
Fixed:
**
 Crash in GPU particles caused by delayed emitter pointer assignment.

-
**
Fixed:
**
 Crash from recent audio checkin (GetNumResources returned wrong value). Restored particle Entity deactivate behavior allowing particles to execute Audio Stop functions. Fixed unit tests after change to unique renaming.

-
**
Fixed:
**
 Feature AudioTrigger now allows both start and stop trigger in same feature making it consistent with other Audio Triggers in the Engine.

-
Fixed
: Crash in creating unique Component name and generalized to work with no number limit.

-
**
Fixed:
**
 Bug fixes re. activation issues, spawn issues. Spawn Fraction now correctly computed for all mortal effects - age increment correctly computed for short durations.

-
**
Fixed:
**
 Removed some global interfaces no longer required on GPU side.

-
**
Refactored:
**
 Simplified many code paths and symbol names.

-
**
Fixed:
**
 GPU particles now stop on Kill event.

-
**
Fixed:
**
 GPU max particle counts now auto-computed. Spawned particles more reliably clamped.

-
**
Fixed:
**
GPU init params are now updated by modifiers.

-
**
Fixed:
**
 CPU features now handle all GPU particle Spawning.

-
**
Fixed:
**
 Many CPU features now update GPU params - removing GPU feature classes.

-
**
Refactored:
**
All Components now have CPU runtime which contains optional GPU runtime pointer

-
**
Tweaked:
**
 Debug displays and info (adjust bounds and text color by distance, use short effect names). Restrict Mod and Color Random range. Fixed uninit member vars.

-
**
Tweaked:
**
 Added "e_ParticlesDebug t+" feature to enable alternate terrain collision test.

##
Plugins

-
**
New:
**
 Added PS4 support to the HTTP plugin.

-
**
New:
**
 Game Platform plugin with Steam and PSN API support.

-
**
New:
**
 HTTP plugin.

-
**
Refactored:
**
 Clean up plugin interface adding inline documentation and expanding available update callbacks.

-
**
Optimized
**
**
:
**

Remove now unused FPS plugin.

-
**
Tweaked:
**
 Clean up HTTP interface, wrap in namespace.

##
PS4 Renderer

-
**
Optimized:
**
 Render occlusion buffer debug visualzation in one draw call.

-
**
Fixed:
**
 Workaround for assert caused by numerical issues du to rcp call on PS4.

-
**
Fixed:
**
 Particle tessellation is broken. Disable for now to avoid rendering artifacts.

-
**
Fixed:
**
 Fix GPU timestamps.

-
**
Fixed:
**
 Implement null resources.

-
**
Fixed:
**
 Fix depth readback.

##
C#

##
C#.Core

-
**
New:
**
 Added Visual Studio 2017 debugging support for C#.

-
**
New:
**
 Added support for C# in the asset directory integrated with the Asset Browser.

-
New
: Open C# assets in an IDE with a solution, or the file only.

-
**
New:
**
 Solution file is now generated automatically for C# files in the assets directory.

-
**
New:
**
 Added C# Output window in the Sandbox Editor to show compile errors.

-
**
New:
**
 Update to Mono 5.10, adding support for
[C# 7](https://docs.microsoft.com/en-us/dotnet/csharp/whats-new/csharp-7)
 (also brings functionality from
[C# 7.1](https://docs.microsoft.com/en-us/dotnet/csharp/whats-new/csharp-7-1)
 and
[C# 7.2)](https://docs.microsoft.com/en-us/dotnet/csharp/whats-new/csharp-7-2)
, .NET 4.7.1 and portable PDB files powered by the new Roslyn compiler.

-
**
New:
**
 Added support for exposing Entity Components functions and signals to Schematyc.

-
**
Refactored:
**
 Matrix3x3, Matrix3x4, and Matrix4x4 now only provide access to the values by index, instead of direct access to the values.

-
**
Refactored:
**
 More values are now exposed in CollisionEvents.

-
**
Refactored:
**
 Split up Camera.ProjectToScreen into ProjectToScreen and ProjectToViewport and exposed more results.

-
**
Refactored:
**
 Added GetComponents, GetComponentsWithInterface and GetComponentWithInterface to the C# Entity.

-
**
Refactored:
**
 Added the option to the EntityComponentAttribute to assign the icon by using the IconType enum.

-
**
Refactored:
**
 Added generic GetValue and SetValue methods to the ParticleAttributes.

-
**
Fixed:
**
 .NET-Exception-error when the user creates a C#-class, renames it and deletes it.

-
**
Fixed:
**
 .NET-Exception-error when the user creates a C#-class with an invalid name.

-
**
Fixed:
**
 OnInitialize is called on Entity Components before the level is done loading.

-
**
Fixed:
**
 Updated Mono with fix for possible shutdown issue.

-
**
Fixed:
**
 Crashes when reloading the mono runtime.

-
**
Fixed:
**
 C# Components now set the right default value when initialized in a SchematycEntity.

-
**
Fixed:
**
 CMonoProperty::Set not passing value types to managed code correctly.

-
**
Fixed:
**
 CMonoObject::CopyFrom not copying reference types correctly.

-
**
Fixed:
**
 Managed domains duplicating when reloading the managed assemblies.

-
**
Fixed:
**
 Double deletion if C# backend failed to initialize.

-
**
Fixed:
**
 Component properties not showing up in Schematyc.

-
**
Fixed:
**
 Component properties being deallocated but not destroyed.

-
**
Fixed:
**
 Default value of Component properties not being set.

-
**
Fixed:
**
 Entity pointer being unavailable when properties were set.

-
**
Fixed:
**
 Possible crash if managed plugin class was removed.

-
**
Fixed:
**
 Crash during startup if plugin domain failed to initialize.

-
**
Fixed:
**
 Crash if compilation of C# source files in assets directory failed.

-
**
Tweaked:
**
 Exposed IsInSimulationMode property in the Engine.

##
C# UI

-
**
Refactored:
**
 Split up the SceneObject update into a render update and a game update.

-
**
Fixed:
**
 Canvas texture is now cleared every frame.

##
Physics

##
Physics

-
**
New:
**
 Particles now do rwi hit separation with importance.

-
**
New:
**
 Exposed immediate event clients notification and trace-pending-rays lock.

-
**
New:
**
 Added CVar to debugbreak if a specific Entity is awoken.

-
**
New:
**
 Added an optional rigidbody-based player implementation.

-
**
New:
**
 Added custom material mapping support to phys dumps/phys debugger.

-
**
Refactored:
**
 Added description to some inteface functions

-
**
Optimized:
**
 Small profile output improvements - show independent in p_list_active_objects, don't show inactive ents in p_profile.

-
**
Optimized:
**
 Allow more leeway in character physics primitive approximation. Restored primitive keywords in bone properties, tweaked capsule detection and primitive order.

-
**
Optimized:
**
 Improved default gear ratios for wheeled vehicles.

-
**
Optimized:
**
 Allow rigidbodies attached to living ents to fall asleep.

-
**
**
Fixed
**
:
**
Fix memory leak in BakeScaleIntoGeometry.

-
**
Fixed:
**
 Some cppcheck warnings/errors.

-
**
Fixed:
**
 MT lock for phys geometry loading.

-
**
Fixed:
**
 Box-box collision fixes (sometimes missed edge-edge collisions, tweaked surface alignment tolerances).

-
**
Fixed:
**
 keep water area active if only wave sim in it is active.

-
**
Fixed:
**
 Potential concurrency issue with saving world's stats.

-
**
Fixed:
**
 SetStateFromSnapshotTxt issue with trailing 0's in snapshot.

-
**
Fixed:
**
 Temp constraint buffer reallocation problem if too many ragdolls.

-
**
Fixed:
**
 Tweaks/fixes of soft Entity raytracing (use closest hit, use callback in RayTraceEntity).

-
Fixed
: Incorrect skinning assignment for soft bodies.

-
**
Fixed:
**
 Missing assignment in SEntityGrid::Setup.

-
**
Fixed:
**
 Make sure rigidbody projectiles always raytrace when flying and don't split steps for inactive constrained players.

-
**
Fixed:
**
 Unaligned Matrix34 in EventPhysUpdateMesh.

-
**
Fixed:
**
 Make sure animated skeletons update constraints.

-
**
Fixed:
**
 Automatic proxy general fixes (vox array overflow on open meshes, problem with >64 voxel resolution and issues with non-merged islands).

-
**
Fixed:
**
 Possible crash on level load and unload.

-
**
Fixed:
**
 Restored phys debugger compilation.

-
**
Fixed:
**
 Problem with ReserveEntityCount when no Entities are present.

-
**
Fixed:
**
 Disable RK4 for kinematic rigidbodies.

-
**
Fixed:
**
 Pre-allocate Entity lists if terrain is created.

-
**
Fixed:
**
 Some issues with text world dumps.

-
**
Fixed:
**
 Indices in GetInternalLock.

-
**
Fixed:
**
 Phys dump fix for particles and other partless Entities/contacts for living ents.

-
**
Fixed:
**
 Capsule and cylinder non-projection issues (false hits).

-
**
Fixed:
**
 Check for rwi called in destroyed world.

-
**
Fixed:
**
 Issue with loading ocean area in physdebugger.

-
**
Fixed:
**
 Properly use living-living collisions on entities with >1 extra parts.

-
**
Fixed:
**
 Player not responding to gravity changes.

-
**
Fixed:
**
 More safety checks for asynchronous external calls to TimeStep.

-
**
Fixed:
**
 Issue with constraint dump loading.

-
**
Fixed:
**
 Potential problem with auxiliary calls to world's TimeStep.

-
**
Fixed:
**
 Issues with PhysX - allow geometry saving (used for Designer Objects), fix non-uni scaled boxes; increased scratchbuf

-
**
Tweaked:
**
 Raycast queue optimization using last hit.

##
Network

##
Network

-
**
Optimized:
**
 Improve network update performance by avoiding gathering deep bandwidth profile data when it's not needed.

-
**
Fixed:
**
 Crash when aspect profile changed and unbind messages received together.

-
**
Fixed:
**
 Dangerous type cast leading to invalid memory access in NET_IMPLEMENT_SIMPLE_ATSYNC_MESSAGE.

-
**
**
Tweaked
**
:
**
Document INetChannel.

-
**
Tweaked:
**
 Increase default value of net_numNetIDHighBitBits from 11 to 13.

-
**
Tweaked:
**
 Increase Memento bucket allocator limit from 16 Mb up to 32 Mb.

##
Lobby

-
**
Refactored:
**
 Remove boost from CryLobby.

##
Project System

##
Projects

-
**
**
New
**
:
**
Add SDK and runtime dependencies to the .cryengine file.

-
**
New:
**
 Added support for only loading plugins on certain platforms.

-
**
New:
**
 GameSDK.cryproject and GameZero.cryproject now load UQS per default.

-
**
Fixed:
**
 GameSDK project parsing.

-
**
Fixed:
**
Check for 'folder exist' check. Would not work in release as pak system is configured to check pak files only and not lose files/folders on disk.

-
**
Tweaked:
**
 Warn user if .cryproject loading failed due to using a newer version of the .cryproject format.

##
CryVersionSelector

-
**
New:
**
 When switching Engine the user now has to option to automatically create a backup of the project before switching.

-
**
New:
**
 A backup can now be created of a project in the CryVersionSelector.

-
**
New:
**
 Update package build options with export path selection, configuration selection and the option to include debug symbols.

-
**
New:
**
 CryVersionSelector now remembers your last selected platform.

-
**
New:
**
 Added Generate Engine Solution to the .cryengine file.

-
**
Refactored:
**
 Cleaned up cryrun.py.

-
**
**
Fixed
**
:
**
Project plugin binaries being statically linked with Engine in release mode (can not occur since projects are compiled independently).

-
**
Fixed:
**
 Duplicate launcher projects when building .cryproject with OPTION_ENGINE enabled.

-
**
Fixed:
**
 Error when opening CMake without a generated solution.

-
**
Fixed:
**
 Crash when generating solutions and having no version of Visual Studio 2015 or 2017 installed.

-
**
Fixed:
**
 Issue where generating a solution would create infinite directories in the solution folder.

-
**
Fixed:
**
 CMake opening the wrong source directory.

-
**
Fixed:
**
 CMake setting NMake as the generator instead of Visual Studio.

-
Tweaked
: Generated CMakelist now includes an easier way to switch the target to Gamelauncher, Server and Sandbox Editor.

-
**
Tweaked:
**
 Added error-messages if Windows only features are used outside of Windows.

-
**
Tweaked:
**
 Updated the order of the options when right-clicking .cryproject and .cryengine files.

##
Sandbox

##
Editor General

-
**
New:
**
 (Sandbox Level File Format). The old level file format will be checked automatically on Sandbox Editor startup. If a project has any levels in the old format, then a confirmation dialog box opens. If the user confirms the update, then the conversion process runs in the background and on completion the notification log records the total number of levels upgraded. The new level file extension is *.level and all old *.cry files are backed-up as *.bak.

-
**
New:
**
 (Asset Browser) Allow deletion of assets via del key.

-
**
New:
**
 Added support for automatic generation of terrain base texture from terrain materials info (added new parameter AutoGenerateBaseTexture in level settings).

-
**
New:
**
 Added a button next to the thumbnail presets for list view in the Asset Browser.

-
**
New:
**
 Improved drag-tooltip pixmap handling and positioning.

-
**
New:
**
 Added Vec3Widget - a generic vector edit box.

-
**
New:
**
 Added CColorButton - a generic color widget with a color picker.

-
**
New:
**
 QPropertyTree2: Associated widgets and decorators.

-
**
New:
**
 Added new implementation of yasli property tree ( QPropertyTree2 ) based on QWidgets.

-
**
New:
**
 Create filter menu from saved filtering presets.

-
**
New:
**
 Exporting/importing a terrain block is missing the layer filter color.

-
**
New:
**
 Entities GUID's from prefabs should be persistent after loading a level in Sandbox Editor.

-
**
New:
**
 Progress bar when importing CGF, Skin, CHR, etc. files when they are added/changed to/in an asset folder.

-
**
New:
**
 (Character Tool) UI improvements to phys proxy editing, partial phys helpers rendering modes and added proxy mirror.

-
**
New:
**
 A pilot implementation of tracking of dependency instance count in asset system.

-
**
New:
**
Can create thumbnails for cryassets..

-
**
New:
**
 Save modified assets from the Asset Browser by new 'Save All' menu.

-
**
New:
**
 (Animation) support phys proxies creation and editing in the Character Tool.

-
**
New:
**
 Level cryasset now next to the Level Folder.

-
**
New:
**
 Terrain is now visible in the Level Editor as a Level Object.

-
**
New:
**
 Detect layers automatically based on file structure.

-
**
New:
**
 .cry file removed, replaced with the level.editor_xml renamed to .level.

-
**
New:
**
 BIG asset thumbnail feature: when holding ctrl the asset thumbnail may show a bigger more informative version of itself.

-
**
New:
**
 Numeric dialog will validate/close on Enter/Escape as expected.

-
**
New:
**
 Basic string or number dialogs now automatically grab keyboard focus when they are shown.

-
**
New:
**
 Added command to focus Editor main frame search box. Defaulted to Ctrl+Alt+F.

-
**
New:
**
 Custom displacement map for Terrain Sculpting Tool.

-
**
New:
**
 QThumbnailView now supports backup/restore selection on model reset - much like QAdvancedTreeView.

-
**
New:
**
 Abstract Menus can now be disabled.

-
**
New:
**
 Inspector can now be set to not be lockable.

-
**
New:
**
 Modified Asset Editor will display the * in title bar.

-
**
New:
**
 (Asset Editor) now handles discarding asset changes properly.

-
**
New:
**
 (Asset Editor) now handles read-only changes as well as setting/clearing modified flag of the asset.

-
**
New:
**
 (Asset System) Added Change signal and flags.

-
**
New:
**
 (Asset Editor) Now supports drag&drop of assets to open.

-
**
New:
**
 (Asset Editor) Help menu now always shown.

-
**
New:
**
 New Material Editor integrated with asset system (Qt front end).

-
**
New:
**
 Now able to set a maximum draw distance for object helper icons.

-
**
New:
**
 Prefab type is now displayed in Properties Panel and Level Explorer.

-
**
New:
**
 (Trackview) Modifying start and end time of an animation should display correctly.

-
**
New:
**
 (Trackview) Show animation length.

-
New
: (Trackview) Delete Entity should not delete track.

-
**
New:
**
Details column to display extension of the file type in the Asset Browser's 'Detail' view.

-
**
New:
**
 (Trackview) Added ability to copy subtrack keys. Fixed selection during copying.

-
**
New:
**
 Implement new Entity Component browser invoked by "Add Component" in the Inspector - Allows searching, tree view, Component description tooltips and now indicates why a Component is disabled.

-
**
New:
**
 UDPs for Shadow, LOD and View ratios.

-
**
New:
**
 Integrate Camera Components with Sandbox Editor UI.

-
**
New:
**
(Trackview) Snapping is incorrect.

-
**
New:
**
Asset Browser automatically shows CGF, Skin, CHR when added to an asset folder.

-
**
New:
**
 (Trackview) Transforming an object in the Viewport won't hide trajectory preview.

-
**
New:
**
 (Trackview) Marquee select will highlight keys to be selected.

-
**
New:
**
 (Trackview) Hovering over keys will highlight them.

-
**
New:
**
Select Asset window select and scroll to the current assigned object in the properties.

-
**
New:
**
 (UX) CEditor layouts should also be saved in personalization.

-
**
New:
**
 UX: Added layer color column to Level Explorer indicating the layers color (also for children).

-
**
New:
**
 (Asset Browser) Adaptive layout.

-
**
New:
**
 (3DEngine) Weighted blending of terrain materials (multiple materials can be mixed together for each heightmap unit). Levels must be re-exported in order to be loadable in launcher.

-
**
New:
**
 Use native OS file browser for importing and exporting.

-
**
New:
**
 Use mobile GPUs instead of CPU for rendering.

-
**
New:
**
 Add new "Open in Explorer" option for Asset Browser folders.

-
**
New:
**
 Auto-importing of old assets that do not have .cryasset files. Added support of thumbnails in pak files.

-
**
New:
**
 (Flow Graph) Show initialization step in a different color.

-
**
New:
**
 Reorganize Toolbar and right-click context menu.

-
**
New:
**
 Mark multiple lines or flow-nodes and Activate/Deactivate all + Activate/Deactivate all nodes inside a comment.

-
**
Refactored:
**
 Added VoxelizationMapBorder GI parameter into level settings UI.

-
**
Refactored:
**
 Added ShadowsSoftness parameter into GI settings UI.

-
**
Refactored:
**
 Removed yasli::Slider. Use yasli::Range instead.

-
**
Refactored:
**
 The resource picker system:.

-
**
Refactored:
**
 Static mesh Entity UI property "Global Illumination" is renamed to "GI and Usage Mode" like it was initially in old GeomEntity.

-
**
Refactored:
**
 Adjusted initial value of terrain texture resolution for better quality.

-
**
Refactored:
**
 (Asset Editor) Recent files are now referencing the asset file and no longer the first file of the asset.

-
**
Refactored:
**
 (AISystem) It is now possible to simulate navigation of multiple selected entities in Sandbox Editor when AI/Physics mode is running.

-
**
Refactored:
**
 Adjusted initial terrain max height value.

-
**
Refactored:
**
 (3DEngine) Added "Instancing" check box into vegetation properties. This allows enabling static instancing optimization only for objects where it makes sense and without risk of changing the look of other objects.

-
**
Optimized:
**
 A minor performance fix of CLevelLayerModel.

-
**
Optimized:
**
 Performance improvements for undo's of grouping and ungrouping.

-
**
Optimized:
**
 Optimize export/import of large groups.

-
**
Optimized:
**
 (Group) CEMETERY grouping/ungrouping, deletion.

-
**
Optimized:
**
 (Group) CEMETERY grouping/ungrouping, exporting/importing a large number of objects is very slow.

-
**
Optimized:
**
 (Performance) Saving large maps takes a long time.

-
**
Optimized:
**
 (Performance) Render Framedrop when enabling/disabling helpers in woodland (~ 40%).

-
**
Optimized:
**
 Improve object selection performance.

-
**
Optimized:
**
 Reduced the amount of time it takes to extract all objects from a prefab to 1/50th of the time. Changed prefab operators to use std::vector rather than CSelectionGroup to gather affected objects. Removed unnecessary selection notifications, removed not required and poorly contained selection function from PrefabManager.

-
**
Optimized:
**
 Fixed slowdown during terrain sculpting (mainly by postponing objects reposition).

-
**
Optimized:
**
 Generate terrain texture speedup.

-
**
Optimized:
**
 Fixed too low frame rate during terrain layers painting.

-
**
Optimized:
**
 Memory runs out when handling groups with many objects.

-
**
Fixed:
**
 'Snap to Grid' value cannot be set below 1.

-
**
Fixed:
**
 Editing a Game Volume inside of a prefab/group moves the GV outside of the map.

-
**
Fixed:
**
 Issue where painting on terrain (when having a slope min and max) was showing erroneous results. Changed vegetation painting to use same GetAccurateSlope function that terrain painting uses.

-
**
Fixed:
**
 Fixing missed changes in the interface display method from a previous update.

-
**
Fixed:
**
 Effects converted from Pfx1is not visible in Asset Browser.

-
**
Fixed:
**
 Crash trying to read empty texture property.

-
**
Fixed:
**
 Removed unused Perception Modifier from the AI Objects menu.

-
**
Fixed:
**
 (Mannequin) FragmentEditor/TransitionEditor/Previewer: "Go to end" button does not work.

-
**
Fixed:
**
 Static model resource picker not using the asset system.

-
**
Fixed:
**
 Using 'Save as' to save an animation in a custom folder doesn't work.

-
**
Fixed:
**
 A wrongly named folder is created on the HDD if an *.FBX file was dragged into the Asset Browser.

-
**
Fixed:
**
 (Character Tool) Fix character update on undo/redo.

-
**
Fixed:
**
 The Legacy Environment Probe stops working after generating cubemaps 2 or 3 times in a row.

-
**
Fixed:
**
 Crash in Entity link row picker where it was calling repaint on a property tree that was in the process of being destroyed.

-
**
Fixed:
**
 PyThreadState can be zeroed out in ShibokenWrapper => extra check to prevent Access Violation when update event happens.

-
**
Fixed:
**
 Crash if Pick Tool was active when the Sandbox Editor layout changed.

-
**
Fixed:
**
 If an Edit Tool button has created an Edit Tool, it'll now also remove it on destruction.

-
**
Fixed:
**
 Solved issue with objects within prefabs losing their selection flags when modified that would eventually lead to them never being deselected.

-
**
Fixed:
**
 Objects within prefabs that were selected and modified would not be removed from the selection.

-
**
Fixed:
**
 Modifying the outputs of a substance instance by adding a 'Texture Output' causes a crash.

-
**
Fixed:
**
 (Schematyc) Random crash while working in Schematyc (EditorCommon.dll!CMergingProxyModel::Unmount(QAbstractItemModel * submodel)).

-
**
Fixed:
**
 Moving an edge on its local axis of an AS, CV or DO deletes its faces.

-
**
Fixed:
**
 Typo in MNM regeneration information box (side instead of size).

-
**
Fixed:
**
 After moving a vertex of an AS, CV or DO on its local axis it changes the gizmo to world axis.

-
**
Fixed:
**
 (DRS) Closing the DRS window when Response History is filled with data leads to a crash.

-
**
Fixed:
**
 Adding any Component to an empty Entity results in a crash. CCrySignal::DiconnectById.

-
**
Fixed:
**
 Crash when opening certain particle effects (DebugCallStack::FatalError).

-
**
Fixed:
**
 Creating a new material in the AB triggers a floating window which just contains Button with the label GameSDK.

-
**
Fixed:
**
 Area Selection Mask does not include AreaSolid.

-
**
Fixed:
**
 Crash Adding IsDestinationReachable node to Schematyc's signal graph and right click in Graph View causes crash (EditorCommon.dll!CDictionaryModel::parent).

-
**
Fixed:
**
 Assert Duplicate objects, left click on them in Level Explorer and moving the cursor into the main viewport triggers assert.

-
**
Fixed:
**
 Creating a new layer in a folder will create a new layer, but select the last layer to rename.

-
**
Fixed:
**
 Prefab proxies are not active on unhidden layers after export.

-
**
Fixed:
**
 Entity can be linked with itself.

-
**
Fixed:
**
 Crash Editing the outputs of a deleted substance archive causes crash.

-
**
Fixed:
**
 (LOD) cgf files can only be browsed after the *.pak file has been unzipped.

-
**
Fixed:
**
 (Asset Browser) Creating a new level just opens the level without asking to save the previously opened level.

-
**
Fixed:
**
 Texture Compiler fails with the 'file not found' error if the texture path contains spaces.

-
**
Fixed:
**
 Selecting a selection mode crashes the Sandbox Editor.

-
**
Fixed:
**
 Notification windows are freezing and still visible after the Sandbox Editor is closed.

-
**
Fixed:
**
 Resetting the layout via the console causes a crash. This is due to the tab system destroying all panels and children before they are able to finish execution. They will continue executing after being destroyed.

-
**
Fixed:
**
 (Trackview) Copying an animation in Trackview via Ctrl+C crashes (CryMovie.dll!TAnimTrack<STimeRangeKey>::SerializeKeys).

-
**
Fixed:
**
 Adding Trackview button to Audio Toolbar and pressing it crashes (EditorTrackView.dll!`anonymous namespace'::PyTrackViewAddLayerNode).

-
**
Fixed:
**
 Moving layers is now an undoable action.

-
**
Fixed:
**
 (UI) Mouse cursor appears outside of main viewport during game mode.

-
**
Fixed:
**
 Adding handlers for opening documentation help in UQS, Python Script panels, Object Create Tool, Character Tool, DRS & Environment Editor.

-
**
Fixed:
**
 Sandbox Editor legacy material loading.

-
**
Fixed:
**
 Crash when jumping into game without active main Viewport.

-
**
Fixed:
**
 Crash when changing the graphics settings without a level loaded.

-
**
Fixed:
**
 Duplicating a group that has linked children will create empty rows in the property tree.

-
**
Fixed:
**
 Bugs and crashes in QCollapsibleFrame.

-
**
Fixed:
**
 Loading of saved filtering presets does not work.

-
**
Fixed:
**
 Always notify on selection batch changes.

-
**
Fixed:
**
 Issue where moving a vegetation object to another group wouldn't have an immediate effect.

-
**
Fixed:
**
 Texture compiler does not compile Engine textures if the Engine and the active project are on different disk drives.

-
**
Fixed:
**
 Layers don't get saved when moving an object from one layer to another.

-
**
Fixed:
**
 Exiting Move Tool causes a crash.

-
**
Fixed:
**
 Crash in legacy filesystem where creating a new level would create new mappings for files and folders within packfiles without removing the old mapping. Opening a file dialog would then try to access old data and crash.

-
**
Fixed:
**
 Enabling snap to terrain breaks ability to move vertices, edges and polygons.

-
**
Fixed:
**
 Edges cannot be selected when the targeted edge is outside of the Viewport.

-
**
Fixed:
**
 Duplicating a brush will reset LOD Ratio and View Dist Ratio.

-
**
Fixed:
**
 (Clip Volumes) Entity links are not saved after reloading the level.

-
**
Fixed:
**
 Crash when changing geometry in a prefab.

-
**
Fixed:
**
 Dragging an asset from 'Select Asset' dialogue into the level causes crash.

-
**
Fixed:
**
 Fixed an issue where objects that were detached from a prefab were unselectable.

-
**
Fixed:
**
 Bone linking of anim objects offsets the object and breaks transformation.

-
**
Fixed:
**
 Issue where undo was never completed if switching tools in the middle of a clone operation.

-
**
Fixed:
**
 If assets change, the thumbnails are not updated to reflect the changes.

-
**
Fixed:
**
 Multi select rotation in view space around local and world axis. Fixed free rotation in local space. Fixed parent space transformations when objects weren't attached to any parent (they were previously using their local space, are now switched to use world space).

-
**
Fixed:
**
 Crash on creating a prefab while editing a shape.

-
**
Fixed:
**
 Rotation around view is now handled properly regardless of what space you are in.

-
**
Fixed:
**
 Buffer overflow crash.

-
**
Fixed:
**
 Crash when switching tools in Designer while editing an object inside a prefab.

-
**
Fixed:
**
 CVegetationMap::PlaceObjectsOnTerrain being called twice in a row during level load.

-
**
Fixed:
**
 Particle pickers not working in property tree.

-
**
Fixed:
**
 Terrain layer color in list now matches selected color. Removed Level Explorer specific code from generic AdvancedItemDelegate, this is now specified through an itemdelegate behavior for a column. Updated PropertyRowCryColor to not transform values to and from gamma/linear. Also reverted hardcoded value added to Level Explorer indentation.

-
**
Fixed:
**
 Crash when closing the Sandbox Editor.

-
**
Fixed:
**
 Popping in Vegetation Editor when selecting between objects. Also fixed an issue where the selecting objects with the vegetation select tool wouldn't scroll to selection in the Vegetation Editor.

-
**
Fixed:
**
 Crash in CPrefabObject::GetTypeDescription.

-
**
Fixed:
**
 Fps drop when creating a Designer Object in large levels.

-
**
Fixed:
**
 (Designer) Local space move, rotate and scale gizmo is pointing in the wrong direction for vertices and edges.

-
**
Fixed:
**
 Issue where any file change within the Level Folder would trigger all objects in the level to handle the change, rather than just changes to cgf files. This has an impact on level save. Layers are now created with the modified flag set to true. Layer rename sets the modified flag to true. Preference for saving only modified layers is now set to true by default.

-
**
Fixed:
**
 Implemented copy/paste for Curve properties, fixed associated bugs. PropertyRowCurve now directly accesses Curve Editor content.

-
**
Fixed:
**
 Area Solids are displayed in game when viewport helpers are enabled.

-
**
Fixed:
**
 Generated breakable objects have unique part names.

-
**
Fixed:
**
 Crash linking and grouping brushes caused crash.

-
**
Fixed:
**
 Crash creating/placing/selecting an Area Solid causes Engine to crash.

-
**
Fixed:
**
 Moving prefabs and groups causes the framerate to drop.

-
**
Fixed:
**
 Entities being exported without considering hierarchies, not respecting order of loading.

-
**
Fixed:
**
 (Entity) rotation transformation doesn't work with typical angle values.

-
**
Fixed:
**
 (Entity) scale transformation doesn't work properly.

-
**
Fixed:
**
 Case where child-parent hierarchy was not respected during level load, resulting in children being initialized first.

-
**
Fixed:
**
 Crashes in Designer when double clicking clip volume or area solid or switching between them.

-
**
Fixed:
**
 Issue where mutli select wasn't showing the transform gizmo.

-
**
Fixed:
**
 Inability to load CGA's with the Serialization::GeomPath resource selector.

-
**
Fixed:
**
 Order of linked objects not being preserved during level load.

-
**
Fixed:
**
 Not able to enable/disable the Global Illumination of a duplicated light.

-
**
Fixed:
**
 Toggle selection (ctrl + drag) not having any effect.

-
**
Fixed:
**
 Ungrouping sending Inspector refresh event for each grouped object.

-
**
Fixed:
**
 Inspector flickering.

-
**
Fixed:
**
 (Lighting Pipeline) strange color change of pre-existing presets when creating a new preset in the Descriptor Database.

-
**
Fixed:
**
 Not possible to export assets as fbx. New options dialog, fixed texture export.

-
**
Fixed:
**
 Memory leak when selecting objects with the Properties Panel open.

-
**
Fixed:
**
 Clicking the 'Edit Outputs' button of a new substance graph causes crash.

-
**
Fixed:
**
 Creating a new Substance graph for a substance file causes crash.

-
**
Fixed:
**
 Redoing the creation of a group crashes the Sandbox Editor.

-
**
Fixed:
**
 A number of crashes in the Material Editor when converting to multi-material.

-
**
Fixed:
**
 Cancelling creation of new asset will no longer close the currently edited asset.

-
**
Fixed:
**
 Crash in Area, re-open shapes.

-
**
Fixed:
**
 Changing the rotation value is not possible when it is changed by 0.1 units or less.

-
**
Fixed:
**
 Mannequin Layout now gets loaded correctly.

-
**
Fixed:
**
 QAdvancedTreeView should use attribute name if available to save column data and not the DisplayRole.

-
**
Fixed:
**
 Duplicating a prefab with a Game Volume resets the GV height to default.

-
**
Fixed:
**
 QuickAssetBrowser and FindWindow now save and restore their layout properly.

-
**
Fixed
**
: Duplicating a Game Volume looses its Entity attributes and Components.

-
**
Fixed:
**
 Asset favorites filter is now working on asset dialogs (open/save).

-
**
Fixed:
**
 Asset favorites are no longer lost on Sandbox Editor restart.

-
**
Fixed:
**
 Personalization Manager is now loaded before any other module guaranteeing expected results.

-
**
Fixed:
**
 Behavior of cropped animation. Fixed blend gap to work with cropped animation.

-
**
Fixed:
**
 Blend gap not working in Trackview.

-
**
Fixed:
**
 Game Volume height resets to default value.

-
**
Fixed:
**
 Freeze all but selected layer no longer freezes child layers.

-
**
Fixed:
**
 Crash when typing a search for a keyboard shortcut while editing a shortcut.

-
**
Fixed:
**
 Removed old settings that were deprecated with new selection highlight system.

-
**
Fixed:
**
 Bug where Toolbars customization would be lost when loading the Sandbox Editor.

-
**
Fixed:
**
 Sandbox Editor hittest on character attachments.

-
**
Fixed:
**
 Save as in Substance Archive Graph Editor, crashes the Sandbox Editor.

-
**
Fixed:
**
 (Trackview) If the end time is less than animation length, then TV shouldn't blend.

-
**
Fixed:
**
 Added support for copying notification history.

-
**
Fixed:
**
 Asset layout details are not centered/all equal in Character Tool.

-
**
Fixed:
**
 (Character Tool) Right click dropdown window appears outside of the Engine after using RMB inside of Character Tools asset menu bar.

-
**
Fixed:
**
 Objects cannot be selected in the viewport when placed with helpers off.

-
**
Fixed:
**
 (Asset Browser) Pop up warning doesn't show up when a dependency file gets renamed via F2.

-
**
Fixed:
**
 Editor crashing when deleting/renaming level.pak folder CLayerSetSwitchNode::OnLoadingComplete.

-
**
Fixed:
**
 (Performance) Positioning duplicated objects - resulting in massive frame rate drop.

-
**
Fixed:
**
 (Trackview) Keys with a value of 0 break the zoom level in the curve editor.

-
**
Fixed:
**
 (Trackview) Changing multiple keys 'Value' also changes 'Time' to the same value and causes the keys to move.

-
**
Fixed:
**
 Opening & closing the Tag Definition Editor will now keep the ID selection.

-
**
Fixed:
**
 (Trackview) Rotating object with record set to on creates position keys.

-
**
Fixed:
**
 Animation playback doesn't work when scrubbing.

-
**
Fixed:
**
 Mannequin layout wasn't saved after closing.

-
**
Fixed:
**
 Timeline in Mannequin sometimes got lost between other panels.

-
**
Fixed:
**
 Undoing the creation of a vegetation object will now clear selection in the vegetation tree view.

-
**
Fixed:
**
 Compile errors for the Visual Studio 2017 Update 3.

-
**
Fixed:
**
 Issue with joint generation on Entities without script tables.

-
**
Fixed:
**
 (Trackview) Add Node, Track, etc menus should be in alphabetical order.

-
**
Fixed:
**
 Crash where code tried to remove a non-existing Entity and accessed an invalid pointer.

-
**
Fixed:
**
 Game Volumes 'Shape' and 'Game Shape' properties have the same check boxes.

-
**
Fixed:
**
 DirectorActivityVolume Game Volume is missing the Game Shape property 'Closed'.

-
Fixed
: Progress notifications can be hidden from notification list if they haven't completed.

-
**
Fixed:
**
 (Trackview) Remember all settings (show key text, snapping, etc).

-
**
Fixed:
**
 Crash when showing Navigation Area context menu.

-
**
Fixed:
**
 NavMesh wasn't updated when editing holes in terrain.

-
**
Fixed:
**
 Navigation areas are again slightly offset below the terrain after creation.

-
**
Fixed:
**
 (Flow Graph) Using the shortcut 'Q' in Flow Graph switches to another graph and creates a node.

-
**
Fixed:
**
 Public Schematyc Components not allowing modification of Transform.

-
**
Fixed:
**
 (UX) Layer not being able to unfreeze if parent is frozen.

-
**
Fixed:
**
 (UX) Toolbar buttons not showing correct checked state or being out of synchronization.

-
**
Fixed:
**
 (UX) Level Explorer object icons did not represent the objects category.

-
**
Fixed:
**
 Make File > Exit not closing Sandbox Editor correctly.

-
**
Fixed:
**
 (Trackview) Creating a key adds two events to undo/redo-queue.

-
**
Fixed:
**
 TRange.IsEmpty could crash curve editor.

-
**
Fixed:
**
 Removed code from ObjectManager.

-
**
Fixed:
**
 Crash on new level creation with unit size 0.5.

-
**
Fixed:
**
 (Entity AI) SmartObject renderobject does not change with the type.

-
**
Fixed:
**
 Create/Open level dialogs will now create the level folder if it didn't previously exist.

-
**
Fixed:
**
 Inability to edit/see an objects default material in the Inspector.

-
**
Fixed:
**
 (Prefab) Prefab properties don't hot reload after using undo.

-
**
Fixed:
**
 Issues with undoing folder layer creation, including a potential crash.

-
**
Fixed:
**
 (UI) All colors set to black in preferences after registering Engine.

-
**
Fixed:
**
 Possible crashes if Engine initialization failed early.

-
**
Fixed:
**
 Shapes not being immediately updated after transform is changed when using the mouse wheel.

-
**
Fixed:
**
 Inability to select Entities by clicking on their editor only helper object.

-
**
Fixed:
**
 (Terrain) Ocean not visible after resizing the terrain.

-
**
Fixed:
**
 Crash when trying to detach individual objects from a prefab through the Properties Panel.

-
**
Fixed:
**
 (CECR) Possible crash caused by ability to undo selection of invalid layer.

-
**
Fixed:
**
(Flow Graph)
**

**
Using undo/redo often after adding a node crashes Sandbox Editor.

-
**
Fixed:
**
 Scrolling the mouse wheel while placing a navigation area shape causes to rotate the shape and sets the points movement offset.

-
**
Fixed:
**
 Object tree in Prefabs Library collapses after placing a prefab.

-
**
Fixed:
**
 Opening any selection window once causes the Properties Panel to flicker/redraw on each change.

-
**
Fixed:
**
 Assertion triggered when scaling Component based Entities.

-
**
Fixed:
**
(Flow Graph) Using "q" to quickly add a node causes an instant crash.

-
**
Fixed:
**
 Default Entity icon being shown for Entities with helpers.

-
**
Fixed:
**
 Reverting a Component's properties in the Inspector recreates the entire Entity.

-
**
Fixed:
**
 Case where Components were duplicated after undoing Entity deletion.

-
**
Fixed:
**
 Entities without scripts being reloaded when scripts changed.

-
**
Fixed:
**
 Crash when undoing layer deletion through context menu in Level Explorer and then doing undo/redo.

-
**
Fixed:
**
 (Trackview) Creating a key adds two events to undo/redo-queue.

-
**
Fixed:
**
 Moving objects between layers for large object counts.

-
**
Fixed:
**
 Open File dialog - sort by size produces imprecise results.

-
**
Fixed:
**
 (Trackview) Capture Track produces warning: End capture failed.

-
**
Fixed:
**
 (Trackview) Now takes into account which item was clicked when scaling and moving keys - rather than snapping to the first key on the timeline.

-
**
Fixed:
**
 Asset Browser remembers thumbnail size, splitter placement.

-
**
Fixed:
**
 (UI) Pfx2 Tool/Icon bar pane maximizing/stretching.

-
**
Fixed:
**
 (Designer Tool) Crash when selection changes while in the UV Mapping Tool.

-
**
Fixed:
**
 Crash when duplicating groups that contained other groups.

-
**
Fixed:
**
 (Level Explorer) Layers: Create/delete layers not captured by undo/redo queue.

-
**
Fixed:
**
 (Trackview) Track selection.

-
**
Fixed:
**
 (Flow Graph) The 'New AI Action' dialogue window is missing a button to create a new folder.

-
**
Fixed:
**
 (Database View) Fixed Prefab instance counter.

-
**
Fixed:
**
 (Designer) Slice Number broken.

-
**
Fixed:
**
 Crash when loading a level with Mannequin open.

-
**
Fixed:
**
 (Prefab) Areas/Shapes, AI Points and Decals are hidden in a closed prefab that is placed in the viewport.

-
**
Fixed:
**
 Missing settings in camera properties.

-
**
Fixed:
**
 Crash when undoing layer deletion due to a stale layer pointer.

-
**
Fixed:
**
 CVar tool buttons in Toolbars now have the CVar value they are set to appear on the tooltip.

-
**
Fixed:
**
 Changed styling for disabled scrollbars so they better reflect their current state.

-
**
Fixed:
**
 LOD baker decal issues.

-
**
Fixed:
**
 All Entity classes being reloaded every time a non-legacy class is added or modified.

-
**
Fixed:
**
 Issue where spamming the generate mip map button would make the screen go permanently black.

-
**
Fixed:
**
 Crash when undoing & redoing the deletion of a layer.

-
**
Fixed:
**
 Align to grid option doesn't work unless grid snapping is enabled.

-
**
Fixed:
**
 Issue in Trackview where if the user wasn't recording changes, had a rotation keyframe on their Entity and tried to modify rotation on said Entity through the Properties Panel or Transform Tool, rotation on the keyframed axis would be locked. Fixed a similar issue with scale as well.

-
**
Fixed
**
: Automatic joint generation after entitysys refactoring.

-
**
Fixed:
**
 Creating a new level with added animations folder triggers errors in NC.

-
**
Fixed:
**
 Creating a new map sometimes triggers an assert.

-
**
Fixed:
**
 Visual helpers for Entities are not showing.

-
**
Fixed:
**
 Selection of objects inside groups being unreliable.

-
**
Fixed:
**
 Inability to select Entities with meshes by simply clicking on the mesh.

-
**
Fixed:
**
 Crash during early shutdown by removing special shutdown behavior.

-
**
Fixed:
**
 (Flow Graph) Copy/Paste issues.

-
**
Fixed:
**
 (Character Tool) Adjusting dimensions in blendspace does not allow you to change the dimensions values.

-
**
Fixed:
**
 (Character Tool) Will now auto expand folders when the search is used. Also the filter is now applied as the user types.

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
 (Flow Graph) FG tree list multiple selection broken.

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
 No selected material in Material Editor after clicking on edit material in Properties Panel.

-
**
Fixed:
**
 Rectangular selection works properly for all objects.

-
**
Fixed:
**
 Baking the alpha map in the LOD Generator causes the vertex alpha to be baked on top of the transparency alpha.

-
**
Fixed:
**
 (FBX) Imported *.fbx with locomotion animation is missing root translocation.

-
**
Fixed:
**
 Debugger not showing empty strings.

-
**
Fixed:
**
 Problems introduced with the FG tree list refactor.

-
**
Fixed:
**
 (FBX Importer) Physical proxies have wrong transformation.

-
**
Fixed
**
: (FBX Importer) Importing a skeleton twice crashes.

-
**
Fixed:
**
 (FBX Importer) Selecting skin of imported skeleton file triggers an assert.

-
Fixed: (FBX Importer) Added "Generate texture coordinates" option.

-
**
Fixed:
**
 Handle Python related errors on widget creation by creating replacement widget.

-
**
Fixed:
**
 Crash when rapidly docking and undocking windows.

-
**
Fixed:
**
 Fix placement of non-maximized windows when restoring layout.

-
**
Fixed:
**
AudioAreas (and some other legacy (proxy) Components) were not exported.

-
**
Tweaked:
**
 Helpers now displayed on first run of the Sandbox Editor.

-
**
Tweaked:
**
 Changed lock/freeze icon for Level Explorer and it's menu entries (new logic/icon is visually synced with visibility functionality).

-
**
Tweaked:
**
 Changed indentation for Level Explorer (was way too big before).

-
**
Tweaked:
**
Original layer of the duplicate error is referenced next to it.

-
**
Tweaked:
**
 Exposed some of the ShapeObject features to GameVolumes.

-
**
Tweaked:
**
 Create camera from current view.

-
**
Tweaked:
**
 Changed splash screen text to be drawn on bottom left with correct spacing.

-
**
Tweaked:
**
 (UX) Icons replaced to better communicate the purpose of clicking a button.

-
**
Tweaked:
**
 (UX) Changed snap to angle values.

-
**
Tweaked:
**
 (UX) Level Explorer styling adjusted.

-
**
Tweaked:
**
 (UX) Change the way navigating many docked tabs is handled. Replace scroll buttons with dropdown menus.

-
**
Tweaked:
**
 (UX) Remove detach from context menu on a tab.

-
**
Tweaked:
**
 (UX) Removed the panel undock handle from tab panel.

-
**
Tweaked:
**
 (UX) Object helper icon (in viewport) scaling adjusted plus display range and clipping now adjustable in preferences.

-
**
Tweaked:
**
 (UX) Icon size slider in Asset Browser changed to distinct sizing buttons.

-
**
Tweaked:
**
 Context Editor is now called Preview Editor.

-
**
Tweaked:
**
 Removed the splitter of Property Tree in embeded MFC controls (used in Database View).

-
**
Tweaked:
**
 Do not write an empty "SoundData" node for areas.

##
Trackview

-
**
New:
**
 Trackview Toolbar now a proper Toolbar with docking.

-
**
New:
**
 Show different cursors while interacting with the dope sheet for better user feedback.

-
**
New:
**
 Automatically expose Entity Component members/properties to Trackview tracks .

-
**
Refactore
**
d
**
:
**
 Cleaned up unnecessary drawing that was obscured by the outside background right (and thus was never visible).

-
**
Optimized:
**
 Increased performance by only caching tracks that are in view for rendering (~>20ms in large sequences).

-
**
Fixed:
**
 Profile display for timeline render passes.

-
**
Fixed:
**
 Scroll acceleration in Trackview Timeline mouse handler.

-
**
Fixed:
**
Properties Panel shows only X-values of keys.
**

**

-
**
Tweaked:
**
 Moved some Toolbar elements.

-
**
Tweaked:
**
 Centered track names in Trackview.

-
**
Tweaked:
**
 Increased default height for tracks in Trackview for better readability (was too close together leading to a sense of constriction).

-
**
Tweaked:
**
 Clamp the dope sheet outward zoom (behaves similarly to the original Trackview).

-
**
Tweaked:
**
 Minor performance improvements by replacing QVector<> in STreeRenderCache and STracksRenderCache with std::vector<>, which minimizes memory allocations during repainting.

-
**
Tweaked:
**

Do not write an empty "SoundData" node for areas.

##
Tools

##
Tools General

-
**
New:
**
 Added CryExport plugin for Max 2018.

-
**
New:
**
 Added Physics 3D Lattice Granularity UI property.

-
**
New:
**
 Exporter for Maya 2018.

-
**
Optimized:
**
 For e.g. Character Tool - reducing floor grid rendering in QViewport from hundreds of draw calls to 1 draw call.

-
**
Optimized:
**
Remove obsolete script to copy Wwise SDK.

-
**
**
Fixed
**
:
**
PakShaders.bat not working with new project workflow. Now takes two parameters: platform (i.e. d3d11) and Eengine root directory.

-
**
Fixed:
**
 .cryproject format.

-
**
Fixed:
**
 Viewport problems in several tools (Character Tool, Mannequin, Schematyc). Wrong depth buffer used, resulting in strong artefacts.

-
**
Tweaked:
**
 Added support for unattended option to disable message boxes and asserts.

-
**
Tweaked:
**
 When the Remote Shader Compiler is run, output the process id to a "pid.txt" file.

##
Resource Compiler

-
**
New:
**
 Deploy netgen library with RC.

-
**
New:
**
 Create .pak file only when all splitting has been determined.

-
**
**
Fixed
**
:
**
Command line parser may return an extra argument with a random content.

-
**
Fixed:
**
 Issue where CryStringLocalT operations could result in reference tracked strings being created, resulting in crashes on RC caused by deleting the same string on different threads.

-
**
Fixed:
**
 Possible out of bounds access when compressing paks.

-
**
Fixed:
**
 C# assets and Schematyc Entities not being included by the RC.

-
**
Fixed:
**
 Inability to build RC with VS 2017 when FBX support was on.

-
**
Fixed:
**
 Missing slice offsetting.

-
**
Fixed:
**
 Implemented full optimal tiling for texture surfaces.
