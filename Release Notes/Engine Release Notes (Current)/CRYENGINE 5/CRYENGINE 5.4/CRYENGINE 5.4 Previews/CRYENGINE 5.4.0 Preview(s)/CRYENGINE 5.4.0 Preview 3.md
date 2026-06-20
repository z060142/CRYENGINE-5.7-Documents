# CRYENGINE 5.4.0 Preview 3

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/47316993/pages/44962722
- Page ID: 44962722
- Breadcrumb: Engine Release Notes (Current) > CRYENGINE 5 > CRYENGINE 5.4 > CRYENGINE 5.4 Previews > CRYENGINE 5.4.0 Preview(s) > CRYENGINE 5.4.0 Preview 3
- Parent: CRYENGINE 5.4.0 Preview(s)

## Content

##
Overview - CRYENGINE 5.4.0 Preview 3

We are very pleased to bring you the 5.4.0 Preview 3 release. This is another “hot-fix” preview release where we have addressed further issues identified by you our community.

##
Pull Requests

As our community you will know that
[https://www.cryengine.com/news/cryengine-github-pull-requests-are-go-here-s-what-you-need-to-know](
CRYENGINE Pull Requests
)
are go - for more information
about Pull Requests follow this
[https://help.github.com/articles/creating-a-pull-request/](
link
)
on GitHub. Please note that the 'branch' for submitting CRYENGINE Pull Requests is called
*
pullrequests
*

Just to let you know, we are working on some detailed steps for the submission of Pull Requests - these will be available very soon.

Finally, thank you once again for your feedback, please keep it coming (but through the normal channels).

##
Vulkan Support in CRYENGINE

We are very pleased to let you know that we have begun adding
[/docs/static/engines/cryengine-5/categories/23756816/pages/27594203](
documentation
)
 for Vulkan support in CRYENGINE. We will continue to add to our Rendering documentation over the coming months.

##
Accessing the 5.4.0 Preview 3 Release

-
Go to
[https://github.com/CRYTEK/CRYENGINE/releases/5.4.0_preview3](
https://github.com/CRYTEK/CRYENGINE/releases/5.4.0_preview3
)

-
Download CRYENGINE_preview_5.4.0.108_pc.zip

-
Unzip it somewhere and open the directory “CRYENGINE_preview_5.4.0.108_pc”

-
Double-click on “InstallEngine.bat"

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
 (Schematyc/Particle) If too many or large graphs are opened or created, then the Sandbox Editor runs out of GDI and or USER handles, resulting in a crash

-
**
CRASH:
**
 (CMake) The Generate Solution option for C++ projects can result in setting NMake as the generator for CMake instead of Visual Studio, resulting in CMake to crash

##
Audio

##
Audio General

-
**
New:
**
 Added Listener Component and fixed Listener for ModelViewPort.

-
**
Tweaked:
**
 Updated Wwise SDK to v2017.1.0 build 6302.

-
**
Tweaked:
**
 Updated FMOD Studio API to version 1.09.06.

##
Core/System

##
Engine General

-
**
Refactored:
**
 Save/Load Entity Component members when going in and out of game mode - to prevent Setter nodes or user code modifying properties that were not supposed to be changed.

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
Tweaked:
**
 Improve markup of license.md.

##
System

-
**
Fixed:
**
 Engine would silently start without project folder and/or assets - now shows errors to the user.

##
CMake

-
**
Tweaked:
**
 Sign CMake binaries and DLLs.

##
Graphics and Rendering

##
Particles

-
**
Fixed:
**
 Random seed not being exposed to UI spawn parameters.

##
Sandbox

##
Editor General

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
 (UI) All colors set to black (in Preferences) after registering Engine.

-
**
Fixed:
**
 Occasional crash when rapidly docking and undocking windows.
