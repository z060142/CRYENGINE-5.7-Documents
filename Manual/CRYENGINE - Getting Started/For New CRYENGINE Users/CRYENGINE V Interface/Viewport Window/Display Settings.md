# Display Settings

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/35848606
- Page ID: 35848606
- Breadcrumb: CRYENGINE - Getting Started > For New CRYENGINE Users > CRYENGINE V Interface > Viewport Window > Display Settings
- Parent: Viewport Window

## Content

## Overview

The Perspective Viewport is the only Viewport that is adjustable. On this page, we'll discuss the Display Settings.

![Image](https://www.cryengine.com/docs/static/attachments/35953484)

### Hide by Category

All options under this heading let you hide and unhide certain objects in the Viewport.

They are shown by default, so ticking the box will hide them.

### Render Types

Similar to Hide by Category, the options under this heading let you hide and unhide certain Render Types in the Viewport.

Contrary to Hide by Category, these boxes are ticked, so unticking the boxes will hide them.

#### Display Options

Setting | Description
--- | ---
**Render Mode** | **Solid** renders the scene in solid mode, which is the default mode:![Image](https://www.cryengine.com/docs/static/attachments/35953494) ** Wireframe** renders the scene in wireframe mode: **![Image](https://www.cryengine.com/docs/static/attachments/35953493)**
**Safe Frame** | Displays a Target Aspect Ratio frame to show what is visible in game mode:![Image](https://www.cryengine.com/docs/static/attachments/35953491)

#### Profile Options

Setting | Description
--- | ---
**Frame Profiler** | This option displays the names of the functions that are currently being called by the game engine. - **Count**: The number of times the function is called - ** Time:** Shows the current frametime taken up by an instance The more time a process takes up, the more expensive it is. Obviously, when debugging, it's a good idea to address these processes first. However, it is also a good idea to take note of processes with a relatively low time, but a high count number, as this can also cause issues. - ** Latest Peaks:** Shows any recent in frametime over a certain value for any functions shown; the purple number to the left displays the number of recent pagefaults caused by the engine - ** Pagefaults:** happen when the game engine runs out of memory and the operating system accesses the hard drive.
**Memory Info** | Displays current memory info. Useful for finding memory leaks.
**Render Debug** | **Render Resources** displays various statistics about DirectX use. ** Draw Calls per Object** shows the number of draw calls needed to draw an object. ** Render Budgets** shows information about CPU/GPU time and memory spent per frame

#### Stereo Settings

Setting | Description
--- | ---
**Stereo Mode** | Enable / Disable the dual rendering mode in Sandbox
**Stereo Output** | Pick from the list the type of 3d output you would like to render. e.g.: Side by side, anaglyphic, VR headset etc.
**Eye Distance (m)** | Distance between eyes used for stereo (interocular distance)
**Screen Distance (m)** | Distance to plane where stereo parallax converges to zero
**Flip Eyes** | If the information for each eye comes in the wrong order, you can flip the two around

[Hide by Category](#hide-by-category)[Render Types](#render-types)[Display Options](#display-options)[Profile Options](#profile-options)[Stereo Settings](#stereo-settings)
