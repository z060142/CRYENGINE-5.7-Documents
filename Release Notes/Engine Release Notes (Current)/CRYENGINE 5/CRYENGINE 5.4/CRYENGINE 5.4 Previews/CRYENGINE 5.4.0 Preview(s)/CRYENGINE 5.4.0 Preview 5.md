# CRYENGINE 5.4.0 Preview 5

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/47316993/pages/44962724
- Page ID: 44962724
- Breadcrumb: Engine Release Notes (Current) > CRYENGINE 5 > CRYENGINE 5.4 > CRYENGINE 5.4 Previews > CRYENGINE 5.4.0 Preview(s) > CRYENGINE 5.4.0 Preview 5
- Parent: CRYENGINE 5.4.0 Preview(s)

## Content

## Overview - CRYENGINE 5.4.0 Preview 5

We are very pleased to bring you the 5.4.0 Preview 5 release. This is another “hot-fix” preview release where we have addressed further issues identified by you our community.

#### Pull Requests

As we promised in the 5.4.0 Preview 3 release, more detailed steps on submitting Pull Requests can now be found [here](/docs). The following links were first published in the Release Notes for the 5.4.0 Preview 3 release.

You can visit the below page for more information on handling pull requests in the CRYENGINE:

[CRYENGINE GitHub pull requests are go](https://www.cryengine.com/news/cryengine-github-pull-requests-are-go-here-s-what-you-need-to-know)

For general information provided by GitHub regarding Pull Requests, please refer here [Pull Requests](https://help.github.com/articles/creating-a-pull-request/).

Finally, thank you once again for your feedback, please keep it coming (but through the normal channels).

## Accessing the 5.4.0 Preview 5 Release

- Go to [https://github.com/CRYTEK/CRYENGINE/releases/5.4.0_preview5](https://github.com/CRYTEK/CRYENGINE/releases/5.4.0_preview5).
- Download CRYENGINE_preview_5.4.0.130_pc.zip.
- Unzip it the downloaded package in your system, and then open the directory “CRYENGINE_preview_5.4.0.130_pc”.
- Double-click on “InstallEngine.bat".

## Code Interface Changes

For more information, see the [Important CRYENGINE 5.4 Data and Code Changes (5.4 Preview Releases)](../Important%20CRYENGINE%205.4%20Data%20and%20Code%20Changes%20(5.4%20Preview%20Releases).md)article.

If you are upgrading from CRYENGINE 5.3, please read this topic: [Migrating from CRYENGINE 5.3 to CRYENGINE 5.4 (5.4 Preview Releases)](../Migrating%20from%20CRYENGINE%205.3%20to%20CRYENGINE%205.4%20(5.4%20Preview%20Releases).md)[.](/docs)

## Known Issues

- **CRASH:**(Schematyc/Particle) If too many or large graphs are opened or created, then the Sandbox Editor runs out of GDI and or USER handles, resulting in a crash.
- **CRASH:** (GameLauncher) Loading a newly generated and exported Woodland map in the GameLauncher will cause a crash on AMD Graphics cards.

### Core/System

#### Engine General

- **Fixed:** CAdvancedAnimationComponent::SetMotionParameter not respecting motion parameter overrides coming from higher-level systems.
- **Fixed:** Unresponsive fragment transitions when calling CAdvancedAnimationComponent::QueueFragment. Also fixed a related memory leak issue.
- **Fixed:** Inability to disable collisions on physics primitive components.
- **Fixed:** Mesh and primitive components using incorrect entity slot ids.
- **Fixed:** Schematyc objects not triggering start node when spawned dynamically after gameplay has started.
- **Fixed:** Remote console deadlock on shutdown.

#### System

- **Fixed:** Releasing render pipeline when the renderer is released.

#### Action General

- **Fixed:** Persistent debug not working in Sandbox Editor.

#### Templates

- **Fixed:** (Third Person Shooter) Warning spam issue - occurring during camera movement by introducing more inertia when toggling the state of Mannequin tags.
- **Fixed:** (First Person Shooter) Missing spawnpoint in the example level.
- **Tweaked:** (Third Person Shooter) Introduced a simple mouse input smoothing filter to mitigate jerky motion when turning around.

### Graphics and Rendering

#### Renderer General

- **Fixed:** Nullptr-access when shader-creation fails.
- **Fixed:** Texture-pointer invalidation by inverse weak-pointer pattern.
- **Fixed:** Fatal error when the renderer cannot create its device. Also now shows a proper messsage when a non-vulkan GPU is used in combination with Vulkan renderer.
- **Fixed:** Warning in Notification Center after map is loaded.

#### 3D Engine

- **Fixed:** Crash in LightVolumes caused by light count exceeding local array bounds. Added constant for limit.

#### Particles

- **Fixed:** Serialisation conversion bug.
- **Fixed:** Some example effects in Engine Assets - now work properly.
- **Fixed:** Particle Entity Components now reliably activate and deactivate emitters, without creating duplicates. Emitters no longer spawn particles when inactive.

### Sandbox

#### Editor General

- **Fixed:** Crash where code tried to remove a non existing entity and accessed an invalid pointer.
- **Fixed:** Crash when showing Navigation Area context menu.
- **Fixed:** Navmesh wasn't updated when editing holes in terrain.
- **Fixed:** Navigation areas sligtly offset bellow the terrain after creation.
- **Fixed:** Public Schematyc components not allowing modification of Transform.
