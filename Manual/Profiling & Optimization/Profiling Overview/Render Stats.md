# Render Stats

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/26215385
- Page ID: 26215385
- Breadcrumb: Profiling & Optimization > Profiling Overview > Render Stats
- Parent: Profiling Overview

## Content

##
Overview

r_stats is a multi-function Console Variable that contains many debugging tools for the rendering in CRYENGINE.

##
r_stats 1

Detailed breakdown of the frame statistics. Lists information on Drawcalls, Device resource switching & sizes and also a performance breakdown of the time spent per sub-system that makes up the frame time.

![Image](https://www.cryengine.com/docs/static/attachments/35406830)

##
r_stats 3

Breakdown of the frame time split into the various sub-systems. Also lists information on the video memory consumption.

![Image](https://www.cryengine.com/docs/static/attachments/35406829)

##
r_stats 4

Same as version 3, but without the video memory information.

![Image](https://www.cryengine.com/docs/static/attachments/35406828)

##
r_stats 5

Statistics on the occlusion.

![Image](https://www.cryengine.com/docs/static/attachments/35406827)

##
r_stats 6

Displays the drawcall count for each object instance in the scene.

The numbers above each object are broken down into Total DP (zpass, general, transparent, shadows, misc).

Since CRYENGINE 3.8.1, you can also specify a value for r_statsMinDrawCalls to filter out results below the specified value.

![Image](https://www.cryengine.com/docs/static/attachments/35406826)

##
r_stats 8

Details information on the total instances in the scene & in how many batches.

![Image](https://www.cryengine.com/docs/static/attachments/35406825)

##
r_stats 13

Cleared render targets

![Image](https://www.cryengine.com/docs/static/attachments/35406822)

[r_stats 1](#rstats-1)
[r_stats 3](#rstats-3)
[r_stats 4](#rstats-4)
[r_stats 5](#rstats-5)
[r_stats 6](#rstats-6)
[r_stats 8](#rstats-8)
[r_stats 13](#rstats-13)
