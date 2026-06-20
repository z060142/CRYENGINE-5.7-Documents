# _MemReplay Tool at First Sight

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/29791770
- Page ID: 29791770
- Breadcrumb: Profiling and Debugging > Memory Profiling > _MemReplay Tool at First Sight
- Parent: Memory Profiling

## Content

## Overview

This article explains how to start investigating a MemReplay log file. Please refer to [Getting Started with MemReplay](../../CRYENGINE%20Tools/MemReplay/Getting%20Started%20with%20MemReplay.md) and [Setup and Loading data with MemReplay Tool](../../CRYENGINE%20Tools/MemReplay/Setup%20and%20Loading%20data%20with%20MemReplay%20Tool.md) if you have not yet successfully loaded a.zmrl file.

Chapters:

[Usage Screen](#usage-screen)[Tracing Memory](#tracing-memory)

## Usage Screen

If you have loaded a.zmrl file into the MemReplay Tool you will see something similar to the following screenshot.

![Image](https://www.cryengine.com/docs/static/attachments/29926180)

The example log file which has been loaded here is showing all the allocations for life cycle:

starting the executable -> main menu -> loading forest level -> reaching spawn point -> player interaction possible

The **By Allocation Event** window and the ** By Frame** window both represent the same memory allocations. However, they differ in the way they display them:

- **By Allocation Event**: Each graph sample represents exactly one allocation (not related to time).
- **By Frame**: Each graph sample represents exactly one frame (not related to number of allocations or time).

There are three lines with different colors (**Requested**, ** Consumed** and ** Pagefile)** which have different memory usage meanings:

- **Requested**: The amount of memory requested by the Engine. This line might be hidden behind the * Consumed* memory since they usually match.
- **Consumed**: The actual memory in use. This is the parameter you are most likely to be interested in.
- **Pagefile**: Consumed memory of process. On PC, it might be that some allocations are performed on a different RAM for e.g. textures on VRAM.
**NOTE:** *Pagefile* memory usage only gives information about the actual usage of the process.

The color of the three lines (**Requested**, ** Consumed** and ** Pagefile)** can be adjusted by selecting the right tab.

- **Uniform Zooming**: Scroll mouse wheel.
- **Free-Zoom**: Hold Middle mouse button and drag mouse.
- **Panning**: Hold Right mouse button and drag mouse.

Adding new markers
New markers are added inside the code by making use of the macro **MEMSTAT_LABEL**, ** MEMSTAT_LABEL_FMT** or ** MEMSTAT_LABEL_SCOPED**

## Tracing Memory

The following example shows, how memory allocations are investigated. Select an area inside the **By Allocation Event** or the ** By Frame** window.

![Image](https://www.cryengine.com/docs/static/attachments/29926179)

In the top bar, click the **D** button which gives you *view selection details*.

![Image](https://www.cryengine.com/docs/static/attachments/29926178)

Then press **Go!**

The **Alloc Ev Range** is representing the actual selection and can be adjusted if required.

![Image](https://www.cryengine.com/docs/static/attachments/29926177)

This opens a new tab which looks similar to the one in the following screenshot. By clicking on the green memory block, the callstack on the left is updated.

![Image](https://www.cryengine.com/docs/static/attachments/29926176)

In this example the memory block and callstack reveal that **6.4MB** have been allocated by ** Create2DTexture()** in the range specified.

Selecting the **Code** tab at the bottom shows you the actual position inside code.

![Image](https://www.cryengine.com/docs/static/attachments/29926175)

Pressing the **D** button again after selecting a function from the callstack will invoke a jump to the line of code in Visual Studio. Note it is required to have the solution already opened in Visual Studio.

Getting more information about the memory block is easy. Select the memory block you want to explore and click on the **C** button on the top bar to show the **context tree**.

![Image](https://www.cryengine.com/docs/static/attachments/29926174)

This gives a summary of the items which together form the memory block you have selected.

In this example, the 6.4MB memory block consists of textures such as*blood_anim_a.dds*, * foam_tiled2.dds* and others.

![Image](https://www.cryengine.com/docs/static/attachments/29926173)

Context tree information can programmatically be added by using macros **MEMSTAT_CONTEXT** and ** MEMSTAT_CONTEXT_FMT**

A categorized context tree can be generated from **Tools -> Build context trees**. If no area is selected, then it will be generated for the complete life cycle of the capture log.

![Image](https://www.cryengine.com/docs/static/attachments/29926172)
