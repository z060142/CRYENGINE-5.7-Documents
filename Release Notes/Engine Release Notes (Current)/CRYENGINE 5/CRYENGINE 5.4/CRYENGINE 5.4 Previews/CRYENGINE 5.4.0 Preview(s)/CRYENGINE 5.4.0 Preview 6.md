# CRYENGINE 5.4.0 Preview 6

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/47316993/pages/44962725
- Page ID: 44962725
- Breadcrumb: Engine Release Notes (Current) > CRYENGINE 5 > CRYENGINE 5.4 > CRYENGINE 5.4 Previews > CRYENGINE 5.4.0 Preview(s) > CRYENGINE 5.4.0 Preview 6
- Parent: CRYENGINE 5.4.0 Preview(s)

## Content

##
Overview - CRYENGINE 5.4.0 Preview 6

We are very pleased to bring you the 5.4.0 Preview 6 release. This is another “hot-fix” preview release where we have addressed further issues identified by you our community.

Once again thank you very much for your feedback, please keep it coming (but through the normal channels please).

##
Particle Presets

In this Preview Release, we bring you the Particle Editor Presets Library. This new feature comprises a comprehensive list of predefined particle effects such as explosions, fire, embers and smoke that can be added to your level from the off. These effects then act as the base for the creation of much more elaborate particle effects.

For more detailed information on the Particle Editor Presets Library, please refer to
**
[/docs/static/engines/cryengine-5/categories/23756816/pages/36869024](
Particle Presets Library
)
.
**

##
Anti-Aliasing

Also in this Preview Release, we want to introduce some new
Anti-Aliasing techniques that will even further improve our graphics
quality. While there is a
range of different anti-aliasing methods available, finding an efficient implementation and one that provides great quality remains one of the biggest challenges in rendering. This is even more true for VR applications, where jagged edges and crawling pixels can cause severe viewer discomfort and where the rendering techniques employed have to operate within a very tight performance budget. Currently, we
support the following methods:

-
**
SMAA and Temporal Antialiasing
**

-
**
Temporal Supersampling (TSAA)
**

-
**
Supersampling
**
For more information on Anti-Aliasing, please refer to
[/docs/static/engines/cryengine-5/categories/23756816/pages/26872518](
Anti-Aliasing
)
.

##
Schematyc Editor

Finally in this Preview Release, we bring you our updated documentation for the Schematyc Editor Interface. For more information, please refer to
**
[/docs/static/engines/cryengine-5/categories/23756816/pages/36868211](
Schematyc Editor
)
.
**

##
Accessing the 5.4.0 Preview 6 Release

-
Go to
[https://github.com/CRYTEK/CRYENGINE/releases/5.4.0_preview6](
https://github.com/CRYTEK/CRYENGINE/releases/5.4.0_preview6
)
.

-
Download CRYENGINE_preview_5.4.0.143_pc.zip.

-
Unzip it the downloaded package in your system, and then open the directory “CRYENGINE_preview_5.4.0.143_pc”.

-
Double-click on “InstallEngine.bat".

##
Code Interface Changes

For more information, see the
[/docs/static/engines/cryengine-5/categories/47316993/pages/44962727](
Important CRYENGINE 5.4 Data and Code Changes (5.4 Preview Releases)
)
**

**
article.

If you are upgrading from CRYENGINE 5.3, please read this topic:
[/docs/static/engines/cryengine-5/categories/47316993/pages/44962700](
Migrating from CRYENGINE 5.3 to CRYENGINE 5.4 (5.4 Preview Releases)
)
[/docs](
.
)

##
Known Issues

-
**
CRASH:
**

(Schematyc/Particle) If too many or large graphs are opened or created, then the Sandbox Editor runs out of GDI and or USER handles, resulting in a crash.

-
**
CRASH:
**
(GameLauncher) Loading a newly generated and exported Woodland map in the GameLauncher will cause a crash on AMD Graphics cards.

-
**
CRASH:
**
 (Crash Reporter) Not working in 5.4.0 Preview 6 Release.

-
**
SPAM:
**
(Shader Spam)
**

**
Cannot compile HW shader
'Hair@HairPS(80000000008)(X1).

##
Animation

##
Character Tool

-
**
Fixed:
**
 A signal/slot race condition crash caused by in PropertiesPanel::m_propertyTree sometimes trying to revert to an expired object when loading/reloading character files. Property tree is now safely refreshed in a subsequent OnExplorerSelectionChanged handler.

##
Audio

##
Audio General

-
**
New:
**
 Added preload component.

##
Core/System

##
Engine General

-
**
Fixed:
**
 Inability to change mesh component type at run-time.

-
**
Fixed:
**
 Inability to re-activate particle component without reloading (if the particle was disabled by default).

-
**
Fixed:
**
 Camera component missing selection helpers.

-
**
Fixed:
**
 Environment Probe component missing size indicator.

##
System

-
**
Fixed:
**
 Engine starting without a project when migration was not possible.

-
**
Fixed:
**
 Cannot execute console commands from the cryproject file.

-
**
Fixed:
**
 Crash on startup if cryproject file did not exist.

-
**
Fixed:
**
 Inability to load cryproject from disk in release builds.

-
**
Fixed:
**
 Binary XML nodes not supporting cloning - now returns itself since the nodes are readonly anyway.

-
**
New:
**
 (CryVersionSelector) Now remembers your last selected platform.

-
**
New:
**
 (CryVersionSelector) Added Generate Engine Solution to the CryEngine file.

-
**
Fixed:
**
 (CryVersionSelector) Fixed CMake opening the wrong source directory.

-
**
Tweaked:
**
 (CryVersionSelector) Generated CMakelist now includes an easier way to switch the target to Gamelauncher, Server and the Sandbox Editor.

-
**
Tweaked:
**
 (CryVersionSelector) Added error-messages if Windows only features are used outside of Windows.

-
**
Tweaked:
**
 (CryVersionSelector) Updated the order of the options when right-clicking cryproject and CryEngine files.

##
CMake

-
**
New:
**
 Now downloads the SDKs through GitHub if bootstrap is not possible.

##
Flowgraph

-
**
Fixed:
**
 Quick selection for Flowgraph nodes is broken.

##
Templates

-
**
Fixed:
**
 Blank and plugin template not registering user created Entity Components.

##
Graphics and Rendering

##
Renderer General

-
**
Refactored:
**
 Replaced all CryMakeUnique with stl::make_unique.

-
**
Fixed:
**
 Cubemap generation issue.

-
**
Fixed:
**
 The flickering debug information in the Sandbox Editor.

-
**
Fixed:
**
 Exporting decals with nullptr material issue.

-
**
Fixed:
**
 Disabled multi-threaded resource creation to allow sys_spec changes to succeed.

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
 Make sure material resource set for FogVolume contains valid resources.

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
 Disable depth fixup on PS4 to circumvent GPU hang.

-
**
Fixed:
**
 Graphics pipeline shutdown.

-
**
Fixed:
**
 Changed upper bound of call-back removal to prevent stack overflow.

-
**
Fixed:
**
 Nullptr access when shader creation fails.

-
**
Tweaked:
**
 Added Sandbox Editor startup information for shader compilation - to fix unclear startup "freeze" when all shaders need compiling.

##
Particles

-
**
Fixed:
**
 Prevent out of bounds access in specular probe texture array.

-
**
Fixed:
**
 Non-functioning presets. Mesh presets now have sphere default and the ribbon has anti-gravity.

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

##
Sandbox

##
Editor General

-
**
Fixed:
**
 Opening & closing the Tag Definition Editor will now keep the ID selection.

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
 issue with joint generation on entities without script tables.
