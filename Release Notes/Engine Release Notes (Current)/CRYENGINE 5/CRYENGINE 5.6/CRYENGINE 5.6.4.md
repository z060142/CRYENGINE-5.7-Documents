# CRYENGINE 5.6.4

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/47316993/pages/53543106
- Page ID: 53543106
- Breadcrumb: Engine Release Notes (Current) > CRYENGINE 5 > CRYENGINE 5.6 > CRYENGINE 5.6.4
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
 Crash on changing to a different tab in ClothPiece::~ClothPiece().

##
AI

##
AI System

-
**
Fixed:
**
 ObserverComponent and ObservableComponent don't register to VisionMap if the game runs from the GameLauncher.

-
**
Fixed:
**
 Calling SetFactionID() from C++ on FactionComponent won't register FactionID to FactionSystem.

-
**
Fixed:
**
 Saving the level and generating an environment probe triggers an assertion failure (NavigationSystem.cpp L 1172) and a warning which will pop up endlessly (Editor background thread is still running) making the editor unusable.

##
Audio

##
Audio General

-
**
New:
**
 Added Audio:Preload Flow Graph node.

-
**
Fixed:
**
 Tweaking fade lengths to avoid cutting transients at the beginning of signals (CrySpatialFmod).

-
**
Fixed:
**
 (ACE) Audio controls could not get renamed if only the case was changed.

-
**
Fixed:
**
 (ACE) Preview in middleware data panel did not stop when deselecting everything.

-
**
Tweaked:
**
 Updated to FMOD Studio 2.00.05.

-
**
Tweaked:
**
 Updated to Oculus spatializer 1.41.0.

-
**
Tweaked:
**
 CrySpatialFmod Engine independent platform includes.

-
**
Tweaked:
**
 Adjusted fade lengths to avoid cutting transients at the beginning of signals | Adding ORBIS to Cmake setup | fixed artifacts during fast rotations.

-
**
Tweaked:
**
 Updated to SDL2_mixer-2.0.4 and with that added support of following additional formats:

*.opus (OPUS).

*.flac (FLAC).

*.mod (MOD (15 and 31 instruments)).

*.aiff (APPLE).

*.xm (FastTracker 2).

*.mid (MIDI).

*.voc (VOC).

*.669 (Composer, Unis).

*.amf (DSMI Advanced Module, ASYLUM Music Format (v1.0)).

*.apun (APlayer).

*.dsm (DSIK internal format).

*.far (Farandole Composer).

*.gdm (General DigiMusic).

*.it (Impulse Tracker).

*.imf (Imago Orpheus).

*.med (OctaMED).

*.mtm (MultiTracker Module Editor).

*.okt (Amiga Oktalyzer).

*.s3m (Scream Tracker 3).

*.stm (Scream Tracker).

*.stx (Scream Tracker Music Interface Kit).

*.ult (UltraTracker).

*.uni (MikMod).

-
**
Tweaked:
**
 Implemented callbacks for preload requests.

-
**
Tweaked:
**
 Marked Audio:PreloadData Flow Graph node as obsolete.

##
Core/System

##
System

-
**
Fixed:
**
 Fixed an issue with FileSystem::CEnumerator not getting intialized properly when launching Sandbox directly from a Visual Studio session of an external .cryproject directory.

##
CMake

-
**
Fixed:
**
 External project generation with engine source downloads SDKs.

-
**
Tweaked:
**
 Generate MODULENAME_API dllimport/export for every project by default. Initial cleanup for dllimport/export code.

##
Flow Graph

-
**
Fixed:
**
 Crash when using AI:Execute Flow Graph node.

##
Schematyc

-
**
Fixed:
**
 Schematyc Experimental editor crashes sometimes when switching between node graphs.

-
**
Fixed:
**
 Resource selectors for EntityClassName, ActionMap and ActionMapAction don't function correctly and cause an assert in Sandbox.

##
Core Systems

-
**
Fixed:
**
 Compile errors reported by the C++20 standard.

##
Graphics and Rendering

##
3D Engine

-
**
Fixed:
**
 Integration of occlusion-culling of light-sources.

##
Sandbox

##
Editor General

-
**
Fixed:
**
 Pressing F2 to rename an asset triggers the confirmation dialog twice.

-
**
Fixed:
**
 When helpers are on, deleting the Geometry of a brush triggers 'XY does not have geometry' warning 100 times.

-
**
Fixed:
**
 The color picker overlay in the Material Editor is too wide.

-
**
Fixed:
**
 Crash that was being caused when changing an objects layer when this object had one or multiple child link objects.

-
**
Fixed:
**
 Unsaved file list is placed in scrollable area. When user has a lot of changes, they can't access Save/Discard buttons and see complete file list.

##
Tools

##
Resource Compiler

-
**
Fixed:
**
 Prevent RC error in case files are provided with absolute paths while source assets folder is provided with relative path.

-
**
Fixed:
**
 Prevent RC error in case paths contain ".." or "."

-
**
Fixed:
**
 Prevent RC error in case one unrelated skeleton fails to load.

-
**
Fixed:
**
 Unable to import 8k textures.

##
Mobile & Consoles

##
XBox

-
**
Fixed:
**
 WWise compilation problem on Durango (stdafx missing).
