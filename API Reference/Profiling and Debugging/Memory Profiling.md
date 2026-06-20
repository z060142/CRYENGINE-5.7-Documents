# Memory Profiling

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/26216310
- Page ID: 26216310
- Breadcrumb: Profiling and Debugging > Memory Profiling
- Parent: Profiling and Debugging

## Child Pages

- [_Getting Started with MemReplay](Memory Profiling/_Getting Started with MemReplay.md)
- [_MemReplay Tool Advanced Knowledge](Memory Profiling/_MemReplay Tool Advanced Knowledge.md)
- [_MemReplay Tool at First Sight](Memory Profiling/_MemReplay Tool at First Sight.md)
- [_MemReplay in Code](Memory Profiling/_MemReplay in Code.md)
- [_Online Recording in MemReplay](Memory Profiling/_Online Recording in MemReplay.md)
- [_Setup and Loading data with MemReplay Tool](Memory Profiling/_Setup and Loading data with MemReplay Tool.md)

## Content

##
Overview

CRYENGINE has around 1,000,000 allocations that are active when a game is running. Furthermore, the total count of allocations and frees while playing a game is even higher.

Therefore, there needs to be a solid method in order to visualize the multitude of memory access.
**
MemReplay
**
 is a tool consisting of two major parts:

Chapters:

[#memreplay-features](
MemReplay Features
)

-
The first part is built into the Engine code itself. When active (see Quick Start guide at the bottom of this document), it records every allocation and every free to disk.

-
The second part is a standalone application which analyzes the data to produce readable information, pretty graphs and tree maps.
*
Example of MemReplay tool after loading
*

[Image: /docs/static/attachments/26964592]

##
MemReplay Features

MemReplay helps to detect hidden errors in handling memory which, in the worst case, causes the application to crash. It has the following main purposes:

-
Finding expensive memory allocations which can lead to "Out of memory"

-
Measuring per system/class memory usage

-
Finding memory leaks

-
Locating memory tramples

-
Finding Double frees

-
[/docs/static/engines/cryengine-5/categories/23756813/pages/29791764](
_Getting Started with MemReplay
)

-
[/docs/static/engines/cryengine-5/categories/23756813/pages/29791772](
_MemReplay Tool Advanced Knowledge
)

-
[/docs/static/engines/cryengine-5/categories/23756813/pages/29791770](
_MemReplay Tool at First Sight
)

-
[/docs/static/engines/cryengine-5/categories/23756813/pages/29791774](
_MemReplay in Code
)

-
[/docs/static/engines/cryengine-5/categories/23756813/pages/29791768](
_Online Recording in MemReplay
)

-
[/docs/static/engines/cryengine-5/categories/23756813/pages/29791766](
_Setup and Loading data with MemReplay Tool
)
