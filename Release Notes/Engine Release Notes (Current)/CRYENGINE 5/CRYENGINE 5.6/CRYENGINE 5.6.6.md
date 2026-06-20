# CRYENGINE 5.6.6

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/47316993/pages/65437703
- Page ID: 65437703
- Breadcrumb: Engine Release Notes (Current) > CRYENGINE 5 > CRYENGINE 5.6 > CRYENGINE 5.6.6
- Parent: CRYENGINE 5.6

## Content

##
Animation

##
Animation General

-
**
Fixed:

**
Implemented several attachment update fixes.

-
**
Fixed:
**
 Avoid VertexAnimation stalls (particularly on Xbox) by shifting skinning/simulation-sync.

-
**
Tweaked:
**
 Introduced CAttachmentManager::SProcessingBuffer to double-buffer the attachment array for use in animation jobs (mitigates racing attachment creation/destruction calls).

-
**
Tweaked:
**
 Removed shared ownership semantics from the IAttachment interface. The lifetime of IAttachment objects is now fully managed internally.

-
**
Tweaked:
**
Removed support for CA_ImmediateMode (unstable feature, causing data races).

##
Editor

-
**
Tweaked:
**
 Removed inversion of parameter/checkbox "Animation Driven Motion".

##
AI

##
AI General

-
**
Fixed:
**
 (UQS Editor) Crash after creating a new universal query and closing the UQS Editor.

-
**
Fixed:
**
 (Behavior Tree Editor) Generated XML document cannot be read.

-
**
Fixed:
**
 F
lowgraph node Actor:VisualDetector node never activating (wrong typeMask used for observer parameters).

-
**
Fixed:
**
 Incorrect FactionId parameter type in Schematyc Node Description.

##
Audio

##
Audio General

-
**
Fixed:
**
Legacy AudioTriggerSpotEntity not stopping events when deleted.

-
**
Fixed:
**

Localized files not correctly loaded when switching language in runtime.

-
**
Tweaked:
**

Updated to FMOD Studio 2.00.07.

-
**
Tweaked:
**

Updated to Wwise SDK v2019.1.7.

##
Core/System

##
Core General

-
**
Fixed:
**
 (PS4) Crash on boot.

-
**
Fixed:
**
 Compilation errors introduced with MSVC 16.4.

-
**
Fixed:
**

CCryPak::IsFolder bit flag check.

-
**
Fixed:
**

Crash when obtaining global enum name from Flowgraph node.

##
C#

-
**
Tweaked:
**
Added prerequisites for C# Extension to support VS2019.

##
Project System

-
**
Fixed:
**

GameLauncher fails to find project file when sys_project and -project are missing (default to game.cryproject if neither exists).

-
**
Fixed:
**

.cryproject loading when project path is absolute.

-
**
Tweaked:

**
Added .env files to XML file list used in project package build.

##
Sandbox

##
Editor General

-
**
Fixed:
**
 (Level Explorer) Bug regarding the sorting of layers according to Visible, Frozen and Color state.

-
**
Fixed:
**
 (Level Explorer) B
ug which doesn't allow freeze and unfreeze object (through shortcuts).

-
**
Fixed:
**
 (Trackview) Setting UI refresh rate to a very low value crashes the Editor.

-
**
Fixed:
**
 (Legacy Property Tree) The "Copy All" and "Paste All" functions do not do anything.

-
**
Tweaked:
**
Added level info to ILevelSystemListener::OnLoadingStart event (instead of passing a null pointer in Sandbox).

-
**
Tweaked:

**
Making all the vectors const in LevelExplorerCommandHelper.

-
**
Tweaked:
**
 U
pdated Substance Importer to Substance Engine 6.3 (no textures from Substance Material).

##
Tools

##
Tools General

-
**
Fixed:
**

Contents of Tools/PakEncrypt going missing.

##
Plugins and Projects

-
**
Tweaked:
**

Added 3DS Max 2019 exporter.

-
**
Tweaked:
**

Added 3DS Max 2021 exporter.

-
**
Tweaked:
**
 "Sync Material" in 3DS Max plugin forcing .tif instead of .dds
