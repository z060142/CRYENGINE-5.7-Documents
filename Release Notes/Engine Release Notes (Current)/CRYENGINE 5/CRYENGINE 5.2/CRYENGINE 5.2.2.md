# CRYENGINE 5.2.2

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/47316993/pages/44962647
- Page ID: 44962647
- Breadcrumb: Engine Release Notes (Current) > CRYENGINE 5 > CRYENGINE 5.2 > CRYENGINE 5.2.2
- Parent: CRYENGINE 5.2

## Content

##
Core/System

##
System

-
**
Fixed:
**
 (Linux) RenderThread stackoverflow. Increment stack from 128kb -> 256kb.

-
**
Tweaked:
**
 Increment some stack sizes to prevent potential stack overflow.

##
WAF

-
**
Tweaked:
**
 Note that redistribution of mfc140.dll from Windows/system32 is okay (
[https://msdn.microsoft.com/en-us/library/ms235264.aspx](https://msdn.microsoft.com/en-us/library/ms235264.aspx)
).

##
Samples

##
GameSDK

-
**
Fixed:
**
 Other players not rotating by default.

##
Templates

-
**
Fixed:
**
 Top down shooter bullet mass being inconsistent with the other templates - fixes boxes not moving when shot as in other templates.

-
**
Fixed:
**
Template player being revived outside of Editor game mode.

##
Graphics and Rendering

##
Renderer General

-
**
Fixed:
**
 (Render) Enabling Total_Illumination_v2 will make dissolving of shadows choppy.

##
Sandbox

##
Editor General

-
**
Fixed:
**
 Navigation areas not updating world bounding box correctly and not updating themselves when height was altered.

-
**
Fixed:
**
 Crash when removing the last toolbar from the toolbar customization screen.

-
**
Fixed:
**
 Crash that was occurring when a toolbar was loaded and contained a non-existent & non-custom command.

-
**
Fixed:
**
 Importing alembic files (.abc) doesn't work in Live-Version 5.2.1.

-
**
Fixed:
**
 Crash in LevelLayerModel when an object within a group or prefab was linked to a sibling. Issue was resolved by making sure the order of operations was sane: detach, then attach; rather than start attaching, detach, finish attaching.

##
Designer Tool

-
**
Fixed:
**
 Subdivide tool not exiting after freezing.

-
**
Fixed:
**
 Bevel tool not exitable with escape after finishing.

-
**
Fixed:
**
 Designer crash when setting invalid tool and quickly moving the mouse over the render viewport.

-
**
Fixed:
**
 Crash on trying to access unused parent tool variable from freed Designer Tool.

##
Particle Editor

-
**
Fixed
**
: Fixed a crash when creating connections after multiple nodes were deleted.

-
**
Fixed
**
: Fixed a crash that occured when clicking into an empty curve editor widget.

-
**
Fixed
**
: Fixed a crash that occured when removing a feature with pin.

-
**
Fixed
**
: Blocked not allowed dragging of feature dragging with right mouse button.

##
Tools

##
Resource Compiler

-
**
Fixed:
**
 FBX importer has artifacts - caused by missing smoothing information.

-
**
Fixed
**
: Engine crashes when saving any material/texture changes in the FBX importer.

##
Known Issues

-
The Visual C++ 11.0 x86 and x64 redistributable packages must be installed. They are available at
[https://support.microsoft.com/en-us/kb/2977003](https://support.microsoft.com/en-us/kb/2977003)
.
