# Using the Main Graph Window

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/23306651
- Page ID: 23306651
- Breadcrumb: CRYENGINE Tools > Statoscope > Using the Main Graph Window
- Parent: Statoscope

## Content

##
Overview

This article covers the basics of Statoscope's interface and describes how to control the Viewport and display of the plot.

##
Viewport Controls

In the main graph window:

-
Left click & drag - pans

-
Right click & drag - zooms

-
Right click & drag left/right - scales the view horizontally

-
Right click & drag up/down - scales the view vertically

-
Right click & drag top right/bottom left - scales both horizontally and vertically at the same time
Chapters:

[#viewport-controls](
Viewport Controls
)
[#plot-modes](
Plot Modes
)
[#navigating-with-bar-plots-eg-function-profiling](
Navigating with Bar Plots (e.g. Function Profiling)
)
[#hovering](
Hovering
)
[#axestarget-lines](
Axes/Target lines
)
[#x-scale](
X Scale
)
[#y-scale](
Y Scale
)
To reset the Viewport, go to
**
View/Fit To Frame Records.
**
This is useful if the data is off screen.

##
Plot Modes

Currently there are three ways of displaying data:

-
Lines (e.g. fps, number of drawcalls)

-
Bars (e.g. function profiles, per entity bandwidth stats)

-
Intervals (e.g. status of queued streaming tasks)
Additionally, vertical lines, user markers show when infrequent actions occur, for e.g. invalid file access, level load/unload.

##
Navigating with Bar Plots (e.g. Function Profiling)

Typically, many more frames are present in a log than can easily be shown (at the same time), so only a subset of bars are displayed when zoomed out. This is indicated by the bars being rendered at 50% opacity.

The bars displayed are actual frames, rather than a composition of several frames with the values averaged. The ones chosen are the tallest (for profilers of course this is longest) of the range that they represent. This makes it easy to identify rare spikes when zoomed out.

Function Profiling is enabled via
**
e_StatoscopeDataGroups r+
**
[Image: /docs/static/attachments/26965067]

Notice the compacted bars
being rendered at 50% opacity

[Image: /docs/static/attachments/26965068]

The transition pictured is the result of a very small change in the X zoom (at the tipping point). Further zooming out would have decreased the bar widths until they reach the minimum size again - at which point the next LOD level would have been used.

Clicking on a bar will select that entry in the
*
Function Profile
*
 tree view tab. Focus is also moved to the tree view, so you can press
*
space
*
 to untick and hide that bar quickly.

This is useful for removing profiling noise, such as MT's EndFrame sync or irrelevant function spikes - in turn, for each bar that you want to remove, then click on the bar and press
*
space.
*

##
Hovering

A vertical red line clips to the nearest frame and a tooltip will follow your cursor over the window giving details about nearby items.

[Image: /docs/static/attachments/26965069]

-
The top line shows, for the current frame:

-
Frame number

-
Game time (or 0 if not available)

-
Current y-value in plot space

-
The Second line details what item you're hovering over (if your mouse is covering 2 or more items they will also be listed here)

-
The third line details the time it's taken in ms

##
Axes/Target lines

On the left and right hand sides are colored numbers that correspond to horizontal lines across the plot window. These allow for easy visual comparison with targets.

For instance, in the screenshot below fps markers are displayed on the left and draw calls on the right. You can specify which target lines are displayed in
*
Target lines
*
 (top right tab group (see below)).

[Image: /docs/static/attachments/26965070]

##
X Scale

This is controlled by a radio button (top right) - changing it will reset the view to fit the window.

By default, the x-axis is linear in the number of frames. This is a useful default (for function profiling) as it makes all the bars the same width. However, sometimes it is more meaningful to have it linear in time. Note there won't be a large difference, unless that is, the framerate is changing significantly.

[Image: /docs/static/attachments/26965071]

##
Y Scale

It is also useful to be able to compare those stats of widely differing sizes, for e.g. RT load (10's of ms) or the number of draw calls (1000's).

To ensure that the lines are not a long way apart, then some of the larger valued stats, for e.g. draw calls and tri counts are artificially scaled when plotted. Note the values you see in the tooltip will still be the original un-scaled ones.
