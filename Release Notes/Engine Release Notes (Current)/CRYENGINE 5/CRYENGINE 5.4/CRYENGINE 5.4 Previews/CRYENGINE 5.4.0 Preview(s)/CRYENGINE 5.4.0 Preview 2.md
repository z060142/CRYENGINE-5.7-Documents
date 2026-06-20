# CRYENGINE 5.4.0 Preview 2

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/47316993/pages/44962721
- Page ID: 44962721
- Breadcrumb: Engine Release Notes (Current) > CRYENGINE 5 > CRYENGINE 5.4 > CRYENGINE 5.4 Previews > CRYENGINE 5.4.0 Preview(s) > CRYENGINE 5.4.0 Preview 2
- Parent: CRYENGINE 5.4.0 Preview(s)

## Content

## Overview - CRYENGINE 5.4.0 Preview 2

We are very pleased to bring you the 5.4.0 Preview 2 release. This is a “hot-fix” preview release where we have addressed a number of issues identified by you our community.

As always we welcome further feedback and comments through our normal channels.

## Accessing the 5.4.0 Preview 2 Release

- Go to [https://github.com/CRYTEK/CRYENGINE/releases/5.4.0_preview2](https://github.com/CRYTEK/CRYENGINE/releases/5.4.0_preview2)
- Download CRYENGINE_preview_5.4.0.98_pc.zip
- Unzip it somewhere and open the directory “CRYENGINE_preview_5.4.0.98_pc”
- Double-click on “InstallEngine.bat"

## Code Interface Changes

For more information, see the [Important CRYENGINE 5.4 Data and Code Changes (5.4 Preview Releases)](../Important%20CRYENGINE%205.4%20Data%20and%20Code%20Changes%20(5.4%20Preview%20Releases).md)article.

If you are upgrading from CRYENGINE 5.3, please read this topic: [Migrating from CRYENGINE 5.3 to CRYENGINE 5.4 (5.4 Preview Releases)](../Migrating%20from%20CRYENGINE%205.3%20to%20CRYENGINE%205.4%20(5.4%20Preview%20Releases).md)[.](/docs)

## Animation

#### Animation General

- **Fixed:** (Renderer) Crash when 8-weight compute skinning is selected.

## Core/System

#### Engine General

- **Fixed:** Crash caused by inactive cameras not being correctly disabled.
- **Fixed:** Input component doesn't register multiple input groups properly.
- **Fixed:** PoolAllocator was choosing non-power-of-2 alignment for some type sizes.
- **Fixed:** Schematyc package not being de-registered - prevents possible crash on shutdown.
- **Fixed:** Issue where during load, Components are created and initialized sequentially, instead of being created in one batch and then initialized.

#### Common

- **Refactored:** Deprecate macros that create GUIDs from two integers.
- **Refactored:** Unify CryGUID conversions from and to string.
- **Optimized:** Remove CryGUIDHelper.

#### CMake

- **Fixed:** Where changed CMake options for Vulkan and HRTF weren't reflected by the CMake GUI. Additionally fixed runtime file deployment of PortAudio dlls.
- **Tweaked:** Add VS2017 options to cry_cmake.
- **Tweaked:** Modify Win32 and Win64 batch files to allow both VS2015 or VS2017 for building.

#### Flowgraph

- **Fixed:** Crash when using Entity:SpawnArchetype in a new project not using the legacy IGame interface.
- **Fixed:** Possible crash when retrieving game token if graph was null.

#### Schematyc

- **Optimized:** Flowgraph integration - currently too unstable due to not implementing Flowgraph events correctly.
- **Fixed:** Schematyc Entity Components being created and initialized sequentially, instead of being created in one batch and then initialized.

### C#

#### C#.Core

- **Fixed:** Possible crash if managed plugin class was removed.
- **Fixed:** Crash during startup if plugin domain failed to initialize.
- **Fixed:** Crash if compilation of C# source files in assets directory failed.

## Sandbox

#### Editor General

- **New:** Use mobile GPUs instead of CPU for rendering.
- **Fixed:** (Terrain) Ocean not visible after resizing the terrain.
- **Fixed:** Crash when trying to detach individual objects from a prefab through the properties panel.
- **Fixed:** Possible crash caused by the ability to undo selection of an invalid layer.
- **Fixed:** (FG) Crash when using undo/redo often (after adding a node) causes crash.
- **Fixed:** Object tree in Prefabs Library collapses after placing a prefab.
- **Fixed:** Opening any selection window once causes the property panel to flicker/redraw on each change.
- **Fixed:** (FG) Crash when using "q" to quickly (when adding a node) causes an instant crash.
- **Fixed:** Default Entity icon being shown for Entities with helpers.
- **Fixed:** Reverting a Component's properties in the Inspector recreates the entire Entity.
- **Fixed:** Case where Components were duplicated after undoing Entity deletion.
- **Fixed:** Entities without scripts being reloaded when scripts changed.
- **Fixed:** Crash when undoing layer deletion through context menu in Level Explorer, and then doing undo/redo.
- **Fixed:** (TrackView) Creating a key adds two events to the undo/redo-queue.
- **Fixed:** Optimized the moving of objects between layers (for large object counts). This issue could potentially stall the Sandbox Editor indefinitely.
- **Fixed:** (Open File dialog) Sort by size produces imprecise results.
- **Fixed:** (TrackView) Capture Track produces warning: End capture failed.
- **Fixed:** Non-uber fix.
- **Fixed:** Asset Browser remembers thumbnail size, splitter placement.
