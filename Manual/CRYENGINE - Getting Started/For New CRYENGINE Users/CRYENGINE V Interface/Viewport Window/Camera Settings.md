# Camera Settings

- Breadcrumb: CRYENGINE - Getting Started > For New CRYENGINE Users > CRYENGINE V Interface > Viewport Window > Camera Settings
- Parent: Viewport Window

## Overview

The Perspective Viewport is the only viewport whose camera is adjustable. This page covers the **Camera Settings** available in the viewport's top-left corner menu — `source:Code/Sandbox/EditorQt/LevelEditor/LevelEditorViewport.cpp:335` (`PopulateMenu`).

![Image](https://www.cryengine.com/docs/static/attachments/44967974)

## Camera Settings for the Perspective Viewport

| Setting | Description | Default | Source |
|---------|-------------|---------|--------|
| **Speed** | Changes the movement speed within that viewport. Can also be changed by scrolling the mouse wheel while moving around in the viewport (see [Viewport Navigation](../../CRYENGINE%20V%20Basics/Viewport%20Navigation.md)). | — | `LevelEditorViewport.cpp:805` |
| **Camera Speed Height-relative** | When enabled, adjusts the speed of camera movement based on the height of the camera above terrain or objects. The camera speed is multiplied by the height in meters (clamped to a range of 1–1000). This lets you move precisely when close to the ground, or quickly to different parts of the level, without constantly adjusting the camera speed slider. | `false` | `RenderViewport.h:36,56` |
| **Camera Terrain Collisions** | Toggles terrain collision on and off. When on, the camera does not go through the terrain when hitting it, but will always move along it. This option also affects **Speed Height-Relative**: when on, camera height is measured above terrain *or* objects; when off, terrain only. | `false` | `RenderViewport.h:34,54` |
| **Camera Object Collisions** | Toggles object collision on and off. When on, the camera does not go through objects on the terrain when hitting them, but will always move along them. | `false` | `RenderViewport.h:35,55` |
| **FOV** | Sets the Field of View. Presets and custom values are available via a sub-menu — `source:Code/Sandbox/EditorQt/LevelEditor/LevelEditorViewport.cpp:350`. | — | `LevelEditorViewport.cpp:350` |

### Resolution

Sets the resolution for this viewport — `source:Code/Sandbox/EditorQt/LevelEditor/LevelEditorViewport.cpp:358`.

| Option | Description |
|--------|-------------|
| **Window Resolution** | Game framebuffer has the exact same size as the viewport window. If you need a set/static resolution that does not change with window size, use a preset or custom resolution. |
| **Preset Resolutions** | Lets you choose a game framebuffer resolution from a list of commonly used resolutions. |
| **Custom...** | Opens a dialog that allows users to create and set a custom game framebuffer resolution for the viewport. The top numbers correspond to width and height of the framebuffer. If a certain aspect ratio is needed, the aspect ratio drop down can be used to enforce an aspect ratio according to the current width or height. Any custom resolution added will be added to a list below the preset resolutions for further use. |
| **Clear Custom Resolutions** | Clears the custom resolutions set with the option above. |

**Positioning** (when using a preset or custom resolution):

| Option | Description |
|--------|-------------|
| **Stretch** | The contents of the game framebuffer are scaled to the boundaries of the editor window, preserving the aspect ratio of the internal resolution. |
| **Center / Top Right / Top Left / Bottom Right / Bottom Left** | The contents of the game framebuffer are positioned to the relevant area of the editor window. The size of the framebuffer is preserved. You will need to increase the size of the window manually to see all the contents if the framebuffer is bigger than the window. **Note:** Selecting any of the positioning options will make the framebuffer resolution a set/static resolution, even if it was a window resolution before. |

### Camera Selection

| Option | Description | Source |
|--------|-------------|--------|
| **Create Camera from Current View** | Creates a Camera entity (with a Camera Component) from the current viewport view. Copies the current FOV. | `LevelEditorViewport.cpp:365,808` |
| **Default** | Sets the view to the default (editor) camera. | `LevelEditorViewport.cpp:399` |
| **Trackview** | Sets the view to the Trackview Camera. | — |
| **Camera Entity** | Lets you jump between different cameras you have created with "Create Camera from Current View" or placed in the level. | `LevelEditorViewport.cpp:392` (`AddCameraMenuItems`) |
| **Create Viewport** | Opens another viewport of your choice in a new window. This can also be done by going to **Tools -> Viewport** and choosing the viewport you want to open. | — |

> **Note:** When "Create Camera from Current View" is used, a new entity with a `Cry::DefaultComponents::CCameraComponent` is created at the current camera position, and the current FOV is copied to it — `source:Code/Sandbox/EditorQt/LevelEditor/LevelEditorViewport.cpp:815-827`.

## See Also

- [Viewport Navigation](../../CRYENGINE%20V%20Basics/Viewport%20Navigation.md) — navigating in the viewport
- [Cameras Components](../../../../../Entities%20and%20Tools/Entity%20Components/Entity%20Components%20(From%20Engine%20Version%205.6)/Cameras%20Components.md) — Camera Component reference
- [Camera Object](../../../../../Editor%20Tools/Level%20Editor%20Tab/Create%20Object/Misc%20Objects/Camera%20Object.md) — legacy Camera Object