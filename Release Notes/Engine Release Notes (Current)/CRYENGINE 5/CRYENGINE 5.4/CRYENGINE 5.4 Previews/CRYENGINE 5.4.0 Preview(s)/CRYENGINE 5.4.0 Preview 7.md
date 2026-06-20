# CRYENGINE 5.4.0 Preview 7

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/47316993/pages/44962726
- Page ID: 44962726
- Breadcrumb: Engine Release Notes (Current) > CRYENGINE 5 > CRYENGINE 5.4 > CRYENGINE 5.4 Previews > CRYENGINE 5.4.0 Preview(s) > CRYENGINE 5.4.0 Preview 7
- Parent: CRYENGINE 5.4.0 Preview(s)

## Content

##
Overview - CRYENGINE 5.4.0 Preview 7

We are very pleased to bring you the 5.4.0 Preview 7 release. Great progress has been made and as you will notice there are no known issues in the Preview 7 Release. We could not have gotten this far without the support of our great community, so once again a massive thank you for all your feedback, please keep it coming (but through the normal channels please).

##
Entity Components

To help the community get to grips with the newly introduced Entity Components feature our Developers have written some
[Entity Component Use Case](/docs)
 documentation. CRYENGINE users may be particularly interested in the two Advanced Use Cases that show how different Components can be combined to create some great effects. This documentation will be expanded on over the coming months, so keep your eyes peeled for further updates.

##
Project Launcher Tools

Also in this Preview Release, we bring you updated documentation for the
[Project Launcher Tools](/docs)
.

##
Accessing the 5.4.0 Preview 7 Release

-
Go to
[https://github.com/CRYTEK/CRYENGINE/releases/5.4.0_preview7](https://github.com/CRYTEK/CRYENGINE/releases/5.4.0_preview7)
.

-
Download CRYENGINE_preview_5.4.0.151_pc.zip.

-
Unzip it the downloaded package in your system, and then open the directory “CRYENGINE_preview_5.4.0.151_pc”.

-
Double-click on “InstallEngine.bat".
Code Interface Changes
For more information, see the
[Important CRYENGINE 5.4 Data and Code Changes (5.4 Preview Releases)](../Important%20CRYENGINE%205.4%20Data%20and%20Code%20Changes%20(5.4%20Preview%20Releases).md)
**

**
article.

If you are upgrading from CRYENGINE 5.3, please read this topic:
[Migrating from CRYENGINE 5.3 to CRYENGINE 5.4 (5.4 Preview Releases)](../Migrating%20from%20CRYENGINE%205.3%20to%20CRYENGINE%205.4%20(5.4%20Preview%20Releases).md)
[.](/docs)

##
Mannequin

-
**
Fixed:
**
 Issue with the Mannequin Editor - sometimes becoming unresponsive for extended periods of time when hovering the mouse cursor over its window.

-
**
Fixed:
**
 Multiple key selections in Transition Editor.

-
**
Fixed:
**
 Issue with certain edit operations in Transition Editor - randomly affecting keys which were not selected by the user.

-
**
Fixed:
**
 A potential crash in the Transition Editor by preventing mandatory keys from being deleted from the transition properties track. The context menu Delete option is now properly grayed out for all immutable keys.

-
**
Tweaked:
**
 Disabled default key selection - performed when opening the Transition Editor.

##
Audio

##
Audio General

-
**
Tweaked:
**
 Updated Wwise SDK to v2017.1.1 build 6340.

##
Core/System

##
Game

-
**
Tweaked:
**
 Update cryproject file to point to 'GameSDK' directory.

##
Graphics and Rendering

##
Renderer General

-
**
Fixed:
**
 (Shaders) Couldn't compile HW shader Hair@HairPS.

-
**
Fixed:
**
 Cubemap generation issue.

-
**
Fixed:
**
 Check for dirty outputs in CFullscreenPass::InputChanged.

##
C#

##
C#.Core

-
**
Fixed:
**
 Crashes when reloading the mono runtime.

-
**
Fixed:
**
 C# components - now set the right default value when initialized in a SchematycEntity.

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
 Component properties not showing up in Schematyc.

-
**
Fixed:
**
 Component properties being deallocated, but not destroyed.

-
**
Fixed:
**
 Default value of component properties not being set.

-
**
Fixed:
**
 Entity pointer being unavailable when properties were set.

##
Sandbox

##
Editor General

-
**
Fixed:
**
 Editor crashing when deleting/renaming level.pak folder CLayerSetSwitchNode::OnLoadingComplete.

-
**
Fixed:
**
 Positioning duplicated objects - results in massive frameratedrop.

##
Tools

##
Tools General

-
**
Tweaked:
**
 Added support for unattended option to disable message boxes and asserts.
