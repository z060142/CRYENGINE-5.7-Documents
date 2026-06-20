# MemReplay Tool Advanced Knowledge

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/23306662
- Page ID: 23306662
- Breadcrumb: CRYENGINE Tools > MemReplay > MemReplay Tool Advanced Knowledge
- Parent: MemReplay

## Content

### Overview

This article describes some advanced MemReplay functions. If you want to get an overview of the tool's functionality please refer to [MemReplay Tool at First Sight](MemReplay%20Tool%20at%20First%20Sight.md).
Chapters:

[Inspecting No Frees Analysis](#inspecting-no-frees-analysis)[Inspecting Heap](#inspecting-heap)[Tracing Allocation History](#tracing-allocation-history)

### Inspecting No Frees Analysis

**Tools -> Debugging -> No frees analysis**

Sometimes you want to figure out which allocations have occurred in a specific frame of time. By using the **D**-button to get selection details, allocations and frees are both taken into account.

If an allocation has happened outside the scope, but the free is inside, MemReplay will display negative numbers as the following screenshot shows.

![Image](https://www.cryengine.com/docs/static/attachments/26964635)

Instead of pressing the **D**-Button you can use ** No frees analysis**. This displays allocations only, which results in a result similar to the following screenshot.

![Image](https://www.cryengine.com/docs/static/attachments/26964636)

### Inspecting Heap

**Tools -> Inspect heap**

This option generates a graphical representation of the memory heap usage. This can be helpful to find large memory blocks or fragmentation.

![Image](https://www.cryengine.com/docs/static/attachments/26964637)

### Tracing Allocation History

**Tools -> Debugging -> Trace allocation history**

This option gives an overview as to which allocations, frees and references have affected the memory address specified.

As an example, the following screenshot shows that five allocations and respectively five frees have been performed on memory address **0x0000000060f45290**.

![Image](https://www.cryengine.com/docs/static/attachments/26964638)
