# MemReplay

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/23306657
- Page ID: 23306657
- Breadcrumb: CRYENGINE Tools > MemReplay
- Parent: CRYENGINE Tools

## Child Pages

- [Getting Started with MemReplay](MemReplay/Getting%20Started%20with%20MemReplay.md)
- [Setup and Loading data with MemReplay Tool](MemReplay/Setup%20and%20Loading%20data%20with%20MemReplay%20Tool.md)
- [Online Recording in MemReplay](MemReplay/Online%20Recording%20in%20MemReplay.md)
- [MemReplay Tool at First Sight](MemReplay/MemReplay%20Tool%20at%20First%20Sight.md)
- [MemReplay Tool Advanced Knowledge](MemReplay/MemReplay%20Tool%20Advanced%20Knowledge.md)
- [MemReplay in Code](MemReplay/MemReplay%20in%20Code.md)

## Content

##
Overview

CRYENGINE has around 1,000,000 allocations that are active when a game is running. Furthermore, the total count of allocations and frees while playing a game is even higher.

Therefore, there there needs to be a solid method in order to visualize the multitude of memory access.
**
MemReplay
**
 is a tool consisting of two major parts:

Chapters:

[MemReplay Features](#memreplay-features)

-
The first part is built into the Engine code itself. When active (see Quickstart guide at the bottom of this document), it records every allocation and every free to disk

-
The second part is a standalone application which analyzes the data to produce readable information, pretty graphs and tree maps
*
Example of MemReplay tool after loading
*

![Image](https://www.cryengine.com/docs/static/attachments/26964592)

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
[Getting Started with MemReplay](MemReplay/Getting%20Started%20with%20MemReplay.md)

-
[Setup and Loading data with MemReplay Tool](MemReplay/Setup%20and%20Loading%20data%20with%20MemReplay%20Tool.md)

-
[Online Recording in MemReplay](MemReplay/Online%20Recording%20in%20MemReplay.md)

-
[MemReplay Tool at First Sight](MemReplay/MemReplay%20Tool%20at%20First%20Sight.md)

-
[MemReplay Tool Advanced Knowledge](MemReplay/MemReplay%20Tool%20Advanced%20Knowledge.md)

-
[MemReplay in Code](MemReplay/MemReplay%20in%20Code.md)
