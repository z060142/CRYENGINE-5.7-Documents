# CRYENGINE 5.4.0 Preview 4

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/47316993/pages/44962723
- Page ID: 44962723
- Breadcrumb: Engine Release Notes (Current) > CRYENGINE 5 > CRYENGINE 5.4 > CRYENGINE 5.4 Previews > CRYENGINE 5.4.0 Preview(s) > CRYENGINE 5.4.0 Preview 4
- Parent: CRYENGINE 5.4.0 Preview(s)

## Content

## Overview - CRYENGINE 5.4.0 Preview 4

We are very pleased to bring you the 5.4.0 Preview 4 release. This is another “hot-fix” preview release where we have addressed further issues identified by you our community.

#### Entity Components

In this preview release we are able to bring you the first phase of the Entity Components [documentation](../../../../../../Manual/Entities%20and%20Tools/Entity%20Components.md). Over the coming months we will continue to add to this documentation, but in the meantime we would very much like to hear what you think about this new feature in CRYENGINE.

#### Substance Viewport Shader

Also in this Preview Release, we bring you a custom Substance shader that has been designed to match the viewport shading of Allegorithmic's Substance Designer and Painter software. To download the tool and for more general information follow this [link](../../../../../../Manual/Editor%20Tools/Substance/Substance%20-%20CRYENGINE%20Shader.md).

#### Photoshop Ultimate Texture Saver

Finally in this Preview Release, we bring you an extension to Photoshop - the Ultimate Texture Saver. This feature has been developed to make life much easier for Texture Artists and replaces 8 separate files with just 1. To download the tool and for more general information follow this [link](http://docs.cryengine.com/pages/viewpage.action?title=Photoshop+-+Ultimate+Texture+Saver&spaceKey=CEMANUAL).

Finally, thank you once again for your feedback, please keep it coming (but as always through the normal channels please).

## Accessing the 5.4.0 Preview 4 Release

- Go to [https://github.com/CRYTEK/CRYENGINE/releases/5.4.0_preview4](https://github.com/CRYTEK/CRYENGINE/releases/5.4.0_preview4)
- Download CRYENGINE_preview_5.4.0.120_pc.zip
- Unzip it somewhere and open the directory “CRYENGINE_preview_5.4.0.120_pc”
- Double-click on “InstallEngine.bat"

## Code Interface Changes

For more information, see the [Important CRYENGINE 5.4 Data and Code Changes (5.4 Preview Releases)](../Important%20CRYENGINE%205.4%20Data%20and%20Code%20Changes%20(5.4%20Preview%20Releases).md)article.

If you are upgrading from CRYENGINE 5.3, please read this topic: [Migrating from CRYENGINE 5.3 to CRYENGINE 5.4 (5.4 Preview Releases)](../Migrating%20from%20CRYENGINE%205.3%20to%20CRYENGINE%205.4%20(5.4%20Preview%20Releases).md)[.](/docs)

## Known Issues

- **CRASH:** (Schematyc/Particle) If too many or large graphs are opened or created, then the Sandbox Editor runs out of GDI and or USER handles, resulting in a crash

- **TEMPLATES:** C++ First Person Shooter template is missing the spawnpoint.

### Audio

#### Audio General

- **Fixed:** Global changes weren't applied in Wwise 2017.1.0.

### Core/System

#### Engine General

- **Refactored:** Save/Load entity component members (when going in and out of game mode) to prevent Setter nodes or user code modifying properties that were not supposed to be changed.
- **Fixed:** Geometry components stop casting shadows when duplicated.
- **Fixed:** Crash caused by dangling pointer in substitution component.
- **Fixed:** Fixed CMake setting NMake as the generator instead of Visual Studio.

#### Action General

- **Fixed:** Savegames can be loaded without writing the file extension in the console.

#### Game

- **Fixed:** In multiplayer games, the Audio Listener wasn't reactivated after killcam. Also made sure that Entities that are also Audio Listeners can create aux Audio Objects.

### Graphics and Rendering

#### Particles

- **Fixed:** Crash during GPU particle editing: class members moved for correct destruction order.
- **Fixed:** Restored AnimBlend and DrawOnTop functionality.
- **Fixed:** Audio would not play if Emitter was Primed. Now plays if Emitter starts at anytime during its Emitter lifetime.
- **Fixed:** Potential crashes caused by multi-threaded static function data init.
- **Fixed:** Emitters did not always create unique seed if spawned from Engine.
- **Fixed:** AudioTrigger start/stop events caused by improper conversion from previous format.

### Physics

- **Fixed:** Enforce rigid-body component to be awake on level-start in case of 'enabled by default'.

### Sandbox

#### Editor General

- **Fixed:** (Trackview) Creating a key adds two events to undo/redo-queue.
- **Fixed:** (Entity AI) SmartObject renderobject does not change with the type.
- **Fixed:** Create/Open level dialogs will now create the level folder if it didn't previously exist.
