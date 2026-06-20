# CRYENGINE 5.7.1

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/47316993/pages/96010250
- Page ID: 96010250
- Breadcrumb: Engine Release Notes (Current) > CRYENGINE 5 > CRYENGINE 5.7 > CRYENGINE 5.7.1
- Parent: CRYENGINE 5.7

## Content

Known Issues
Oculus VR: Using the
`
map
`
 console command will very likely cause a crash.

##
Animation

##
Animation General

-
**
New
**
: Character motion is taken into account when applying wind.

##
Core/System

##
Engine General

-
**
New
**
: Added the ability to set whether elements are compiled for clients, dedicated servers or both.

##
CMake

-
**
Fixed
**
: Updated the download link for automated SDK downloads.

##
Schematyc

-
**
Fixed
**
: Crash when connecting to a node that expects a Script Array.

-
**
Fixed
**
: Crash where some UI Element XML would specify types that would generate FlowGraph 'Any' types (Scaleform Schematyc now assumes "String" type for these unspecified types).

##
Graphics and Rendering

##
Renderer General

-
**
Fixed
**
: The
`
 r_SnowDisplacement
`
 CVar.

-
**
Fixed
**
: Deferred Decals, through a change to the Mip calculation.

-
**
Fixed
**
: VolumetricClouds not binding all necessary resources under some circumstances.

-
**
Fixed
**
: Crash on shutdown when using Skybox material in a level, by preventing dangling smart pointers and waiting for the texture compiler job to finish.

-
**
Fixed
**
: Several thread race condition related crashes, by preventing multiple render-thread process overlaps.

-
**
Fixed
**
: Broken Scaleform rendering on Vulkan.

-
**
Tweaked
**
: Improved unload-to-load level transitions.

-
**
Tweaked
**
: Splash-screen implemented without Aux renderer - it now uses the standard graphics pipeline.

-
**
Tweaked
**
: Loadtime (startup, level change, etc.) FPS limited to 72 instead of 120.

##
Virtual Reality

-
**
Tweaked
**
: Splash-texture fill-in was activated.

##
3D Engine

-
**
Fixed
**
: Lights culling inconsistently within different VisArea shapes.

-
**
Fixed
**
: Crash when triggering a cubemap capture with merged meshes in the scene due to invalid reference.

##
Plugins

-
**
Fixed
**
: Crash with Dedicated Launcher and CryScaleformSchematyc.

##
Sandbox

##
Editor General

-
**
Tweaked
**
: Schematyc templates can be created using Sandbox for LTS.

##
Project System

##
CryVersionSelector

-
**
Fixed
**
: Visual Studio 2022 was added to the Generate Engine Solution context popup.

##
Tools

##
General

-
**
New
**
: Updated the 3ds Max Exporter to support Autodesk 3ds Max 2022.

-
**
New
**
: Updated the Maya Exporter to support Autodesk Maya 2022.

-
**
Tweaked
**
: Visual Studio 2022 and Windows SDK 10.0.20348.0 were added to meta dependencies in the Launcher.
