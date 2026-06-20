# CRYENGINE 5.5.1

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/47316993/pages/44962765
- Page ID: 44962765
- Breadcrumb: Engine Release Notes (Current) > CRYENGINE 5 > CRYENGINE 5.5 > CRYENGINE 5.5.1
- Parent: CRYENGINE 5.5

## Content

##
Release Highlights

CRYENGINE 5.5.1 while being a minor release does bring some worthwhile fixes and updates to the Engine.

##
Accessing CRYENGINE 5.5.1 and Sandbox Editor Source Code

Engine versions are now available through the CRYENGINE Launcher.

-
Log into the CRYENGINE Launcher

-
Go to LIBRARY -> My Engines where your currently installed and available Engines are listed. From there Engines can be updated (installed).
Sandbox Editor source code is only available via Github:
[https://github.com/CRYTEK/CRYENGINE](https://github.com/CRYTEK/CRYENGINE/releases/tag/5.5.1)

##
Audio

##
Middleware Update

-
**
Updated to
**
Oculus spatializer version 1.29.0.

##
Sandbox

##
Editor General

-
**
Fixed:
**
 Texture compilation notification is permanently compiling. Fixes a multithreading issue with CProgressNotification (where the notification may never be removed if its lifetime is short).

-
**
Fixed:
**
 Changes and edits to Designer Objects do not mark its layer as modified.

-
**
Fixed:
**
 Creating a new level didn't allow the user to save changes to layers.

##
Tools

##
Resource Compiler

-
**
Fixed:
**
 Missing Normalmap_lowQ Preset from CryTiff plugin.
