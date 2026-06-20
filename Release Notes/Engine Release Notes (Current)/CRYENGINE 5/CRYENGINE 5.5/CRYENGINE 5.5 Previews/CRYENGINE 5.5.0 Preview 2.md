# CRYENGINE 5.5.0 Preview 2

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/47316993/pages/44962789
- Page ID: 44962789
- Breadcrumb: Engine Release Notes (Current) > CRYENGINE 5 > CRYENGINE 5.5 > CRYENGINE 5.5 Previews > CRYENGINE 5.5.0 Preview 2
- Parent: CRYENGINE 5.5 Previews

## Content

##
Overview - CRYENGINE 5.5.0 Preview 2

We are very pleased to bring you the 5.5.0 Preview 2 release. Our Dev Team have been busy improving on the first preview that was released on 20th March 2018.

As always we really do welcome further feedback and comments from the CRYENGINE Community, but please can these come through our normal channels i.e. the
[Github Issue Reporter](https://github.com/CRYTEK/CRYENGINE/issues)
 and the .

##
Accessing the 5.5.0 Preview 2 Release

CRYENGINE Preview versions are now available through the CRYENGINE Launcher.

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

CRYENGINE can still be obtained from Github as can full Sandbox Editor source code.

-
Go to
[https://github.com/CRYTEK/CRYENGINE/releases/5.5.0_preview2](https://github.com/CRYTEK/CRYENGINE/releases/5.5.0_preview2)

-
**
Download CRYENGINE_preview_5.5.0.108_pc.zip
**

-
**
Unzip it somewhere and open the directory “CRYENGINE_preview_5.5.0.108_pc”
**

-
Double click on
**
InstallEngine.bat
**

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
Rendering:
**
 Resizing the Properties panel corrupts rendering in the Character Tool.

-
**
Designer:
**
 Designer surfaces are invisible or flicker during edit mode and after.

-
**
Global VFX:
**
 Switching layers breaks particles, visuals and audio for them.

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

-
**
Visual Studio 2017 (15.7):
**
Sandbox will crash due to an exception. Occurs when building Sandbox using Visual Studio 15.7, then running the built Sandbox.

**
Workarounds:
**

1. Use Visual Studio 2015 to build CRYENGINE and Sandbox for 5.5.

2. Don't upgrade to 15.7, or downgrade to a version prior to Visual Studio 15.7.

##
Audio

##
Audio General

-
**
Fixed:
**
 Wwise implementation now uses proper MSVC libraries during linking in regards to the used compiler toolset.

-
**
Fixed:
**
 Clang compiler error.

##
Sandbox

##
Editor General

-
**
Fixed:
**
 Crash when opening a certain particle effect.

-
**
Fixed:
**
 Crash in Trackview.

-
**
Fixed:
**
 Crash when ungrouping an empty group.

-
**
Fixed:
**
 Crash when extracting objects from a prefab.

-
**
Fixed:
**
 Crash when renaming imported textures.

-
**
Fixed:
**
 Creating a substance graph preset does not create the related texture files.

-
**
Fixed:
**
 Warnings when reloading item scripts in GameSDK.

-
**
Fixed:
**
 Message notification for the texture compiler may not dissappear.

-
**
Fixed:
**
 (FBX Importer) Mesh importer cannot save new files.

-
**
Fixed:
**
 (Terrain Editor) Painting terrain texture does not work if
**
Mask by Altitude and Slope
**
 checkbox is enabled.

##
Core/System

##
Engine General

-
**
Fixed:
**
 (Schematyc) Switched the logic of Equal and NotEqual.
