# CRYENGINE 5.5.0 Preview 4

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/47316993/pages/44962791
- Page ID: 44962791
- Breadcrumb: Engine Release Notes (Current) > CRYENGINE 5 > CRYENGINE 5.5 > CRYENGINE 5.5 Previews > CRYENGINE 5.5.0 Preview 4
- Parent: CRYENGINE 5.5 Previews

## Content

##
Overview - CRYENGINE 5.5.0 Preview 4

We are very pleased to bring you the 5.5.0 Preview 4 release. Our Dev Team have been busy improving on the earlier previews that were released on 20 March 2018, 03 May 2018 and 24 May 2018.

As always we really do welcome further feedback and comments from the CRYENGINE Community, but please can these come through our normal channels i.e. the
[Github Issue Reporter](https://github.com/CRYTEK/CRYENGINE/issues)
 and the .

##
Accessing the 5.5.0 Preview 4 Release

Engine versions are now available through the CRYENGINE Launcher.

-
Log into the CRYENGINE Launcher

-
Go to
**
LIBRARY -> My Engines
**
 where your currently installed and available Engines are listed. From there Engines can be updated (installed).

##
 Github

Preview Engine versions are also available from Github, however Sandbox Editor source code is only available via Github.

-
Go to:

[https://github.com/CRYTEK/CRYENGINE /releases/5.5.0_preview4](https://github.com/CRYTEK/CRYENGINE/releases/5.5.0_preview4)

-
Download CRYENGINE_preview_5.5.0.208_pc.zip

-
Unzip it somewhere and open the directory “CRYENGINE_preview_5.5.0.208_pc”

-
Double click on
InstallEngine.bat

##
Code Interface Changes

For more information. see the
[Important CRYENGINE 5.5 Data and Code Changes](../CRYENGINE%205.5.0/Important%20CRYENGINE%205.5%20Data%20and%20Code%20Changes.md)
.

If you are updating from CRYENGINE 5.4, please read this topic:
[Migrating from CRYENGINE 5.4 to CRYENGINE 5.5](../CRYENGINE%205.5.0/Migrating%20from%20CRYENGINE%205.4%20to%20CRYENGINE%205.5.md)
[.](/docs/static/engines/cryengine-5/categories/23756816/pages/29445533)

##
Known Issues

-
**
UI:
**

Dependency Graph window is not responsive when opening from a selection window.  WORKAROUND: It can be closed from the Windows tray bar, however if you don't have separate icons enabled for the different editor windows on the tray, then this can be an issue. NOTE: Opening the Dependency Graph say for example from the Asset Browser or from the global menu
T
**
ools -> Dependency Graph
**
 works fine.

-
**
RENDERER:
**
 (PARTICLE)
Particle 'new_year' is not being rendered correctly.

-
**
RENDERER:
**
 (EDITOR ONLY)
 Shadow square following camera.

-
**
RENDERER:
**
 Some brushes could flicker directly after level load.

-
**
RENDERER:
**

SkyBox could be broken after several level loads.

-
**
CRASH:
**
 (VS2017)
After compiling and running the Engine with VS version 15.7 the Engine will crash (exception thrown), the problem originates from the last command in ( Editor\Python\plugins\crytools\startup.py ). For more information about this topic click .

-
**
C#:
**
Using the CRYENGINE C# extension for Visual Studio 2017 to start the GameLauncher, Sandbox Editor or Server can cause an error when used in the latest version of Visual Studio 2017. More information and a fix for this issue can be found
[here](../../../../../API%20Reference/CRYENGINE%20Code%20Tutorials/C%23%20Programming.md)
.

##
AI

##
AI System

-
**
Fixed:
**
 Old parts of the navigation area stay in the map when the area is moved (while navmesh updates are disabled and then enabled again).

##
Audio

##
Middleware Updates

-
Updated to Wwise SDK v2017.2.6

-
Updated to Fmod Studio 1.10.06

-
Updated Oculus spatializer plugin for Wwise 1.27.0

##
Core/System

##
Default Entities

-
**
Fixed:
**
Static Mesh Entity mass defaults to 0.

-
**
Fixed:
**
 Camera Component overrides view camera in edit mode.

-
**
Tweaked:
**
 Allow to scale Debug Draw-text (depending on camera-distance).

##
Flowgraph

-
**
Fixed:
**
 Saving Flowgraph modules between level loading causes crash.

##
Graphics and Rendering

##
Particles

-
**
Fixed:
**
 Error in Pfx1 that causes effects with incomplete parameters to spawn particles indefinitely.

##
C#

##
C#.Core

-
**
New:
**
 Added the SerializeValueAttribute to mark properties and fields for serialization (without exposing them to the Sandbox Editor Properties Panel).

-
**
New:
**
 Added missing mouse input to the Mouse class.

-
**
New:
**
 Added an extra CRYENGINE Mono extension that solves the issue of missing assemblies (e.g. Clide.Interfaces) in the latest version of Visual Studio 2017.

-
**
Optimized:
**
 Improve the ToString() method of the Rect struct.

-
**
Optimized:
**
Use Vector2 instead of Point in some cases.

-
**
Fixed:
**
 C# PhysicsEntity does not return the right value for PhysicalizationType after it has been physicalized.

-
**
Fixed:
**
 Crash when deleting a C# Component that's also currently in the level.

-
**
Fixed:
**
 Minor bugs in the C# debugging extension.

-
**
Fixed:
**
 Serializing properties when reloading the C# plugins.

-
**
Fixed:
**
 Several types of properties (Character, ActionMap and ActionMapAction) not being exposed correctly in the Sandbox Editor.

-
**
Tweaked:
**
 Expose Flags property on the Character class.

##
Physics

##
Physics

-
**
Fixed:
**
 Prevent cloth from falling asleep if affected by environmental wind.

##
Sandbox

##
Editor General

-
**
New:
**
 (Designer Tool) Ruler Tool - Added more distances to display and removed obsolete pathfinding information.

-
**
Fixed:
**
 Rotating a brush/prefab in world-space (before scaling it uniformly) breaks the scale on its rotated axis.

-
**
Fixed:
**
 Double clicking a level in the Asset Browser does not load the corresponding level.

-
**
Fixed:
**
 Assert triggers when using "save as" on a newly created Schematyc Entity.

-
**
Tweaked:
**
 Disable Substance Rebuilding all Instances context menu (if there are no instances). Disable Re-import context menu if asset does not have source file.

##
Additional Fixes

-
**
Fixed:
**
 Color output for screenshots.

-
**
Fixed:
**
 (Mesh Importer) Mesh Importer cannot save file to folders that do not exist on the disk.

-
**
Tweaked:
**
 (EngineAssets) Renamed primitive_plane_small to primitive_plane.
