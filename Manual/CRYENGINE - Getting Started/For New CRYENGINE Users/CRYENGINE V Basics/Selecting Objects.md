# Selecting Objects

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/23308621
- Page ID: 23308621
- Breadcrumb: CRYENGINE - Getting Started > For New CRYENGINE Users > CRYENGINE V Basics > Selecting Objects
- Parent: CRYENGINE V Basics

## Content

##
Overview

Understanding concepts of selection inside CRYENGINE Sandbox is essential to successfully modify objects within your scene.

##
Select Mode

![Image](https://www.cryengine.com/docs/static/attachments/24152069)

In
**
Select
**
 mode, you can select single objects, a group of objects, or add to or subtract from the current selection in the Viewport window with simple mouse actions.
 (Select mode literally only selects the objects without moving them.)

##
Show / Hide Helpers

Helpers allow the user to make object selection easier in the 3D Viewport. Helpers can be activated by toggling the
**
H
**
 icon on top of the 3D Viewport window:

![Image](https://www.cryengine.com/docs/static/attachments/24152070)

##
Selecting a Single Object

Objects with physics meshes can be selected simply by hovering the mouse cursor over the object and clicking the Left Mouse Button (
**
LMB
**
).

Selecting 3D objects without physics mesh proxies built into the asset can be done either by moving the mouse cursor over the boundary edges of the Bounding Box, or more conveniently, by showing the object's Pivot by holding
**
Space Bar
**
. For this to work,
**
Show Helpers
**
 must be activated.

2D Elements like particle entities can be selected via a 2D helper icon displayed in the objects origin. These icons are toggled on/off with the
**
Show Helpers
**
 button.

##
Selecting Multiple Objects

To select multiple objects, drag a box around the objects that you want to select, and then release the mouse button when all the required objects are inside the selection box. When using drag select, it grabs everything within that 2D box to infinity. So in busy scenes with a lot of assets, it helps to angle the camera to reduce the amount of assets on screen (i.e. look towards the floor or sky).

The current version of the CRYENGINE lets you transform your selected objects using a single gizmo, even when you have selected multiple objects in the viewport. This helps in reducing the gizmo clutter when multiple objects are selected in the viewport. The gizmo will appear at the central point of the selected objects.

When local or parent coordinate frame is used, the transform gizmo will use the relevant coordinate frame of the last selected object.

Managing multiple objects selection using gizmos:

![Image](https://www.cryengine.com/docs/static/attachments/26526167)

##
Selection Outlines

![Image](https://www.cryengine.com/docs/static/attachments/27566948)

When you hover over or select an object, you'll see a highlight and an outline. The effect works as follows:

-
If an object is selected, it will get a selection color blended on top of it. Around its silhouette, there will be an outline with the same color.

-
If an object is highlighted, it will likewise get a highlight color.

-
If an object is both highlighted and selected, it will get a highlighted outline, and a selection color blended with it. This way it should be possible to tell that it is also selected.
A highlighted object's outline will be displayed along the edges of selected objects to make them easier to discern.

If a highlighted or selected object is partially hidden, a dimmed (ghost) outline will still appear so users can discern its location.

At the moment, this feature does not work for:

-
Grass/mergeable vegetation during vegetation editing

-
Attached weapons on animated characters
You can change the colors, outline width and other parameters concerning the selection outlines in the
**
[Preferences](Customizing%20CRYENGINE%20Sandbox/Changing%20Sandbox%20Preferences.md)
**
.

##
Adding and Removing Objects from Selection

-
Hold down
**
Ctrl
**
 and click the object you want to add to or remove from the selection.

-
Holding down
**
Alt
**
 while clicking on selected objects will only remove them from the current selection.

-
You can add and remove multiple objects at the same time by holding
**
Ctrl/Alt
**
 respectively while dragging a box around the objects.

Locking Selection

Locking the current selection by going to
**
Level -> Selection -> Lock Selection
**
 (or pressing
**
Ctrl+
**
**
Shift+Space Bar
**
) enables you to do transformations and other operations without worrying about deselecting the currently selected objects.

Level Explorer

The
**
Level Explorer
**
 window enables you to quickly search for objects, hide/unhide and freeze/unfreeze objects or entire layers in a list view. You can also browse through hidden or frozen objects without changing their state.
You can open the window via
**
Tools -> Level Editor -> Level Explorer
**
.

-
To hide/unhide an object through the Level Explorer, click on the eye icon in the left-most column.
Clicking this eye icon will change the state of that object to Hidden.

-
To freeze/unfreeze an object through the Level Explorer, click on the arrow icon in the second column from the left.

![Image](https://www.cryengine.com/docs/static/attachments/24151243)

The Level Explorer allows you to do more than just selecting, hiding/unhiding tools and layers and freezing/unfreezing them. For more information on this tool,
**
[click here](../../../Editor%20Tools/Level%20Editor%20Tab/Level%20Explorer.md)
**
.

Deep Selection

This functionality allows users to easily pick and select the correct object among multiple objects at the almost same location.

Normally, the selection operation is the same as before. However, if you want to select an object in a crowded area, you can simply click several times to cycle through all objects that are located within a certain number of pixels.

Using Deep Selection

To use Deep Selection, you have to use the Key Combos of:

-
**
TAB+Z+LMB.
**
 This will bring up a list of all the items under the mouse cursor. (list mode) see picture below.

-
**
TAB+LMB.
**
 This is the cycle mode (without the drop down list)

Deep Section in action TAB+Z+LMB (Range = 50m)

*
![Image](https://www.cryengine.com/docs/static/attachments/26526166)
*

The Deep Selection mode is activated only when multiple objects are in Deep Selection range.

The distance threshold value can be controlled in the
**
Preferences
**
 menu under
**
Edit -> Preferences -> General Settings -> General -> Deep Selection -> Range
**
. The default value is
**
1
**
. (Default setting of 1 meter. To use this effectively, increase the range to take more objects into account.)

[Select Mode](#select-mode)
[Show / Hide Helpers](#show-hide-helpers)
[Selecting a Single Object](#selecting-a-single-object)
[Selecting Multiple Objects](#selecting-multiple-objects)
[Selection Outlines](#selection-outlines)
[Adding and Removing Objects from Selection](#adding-and-removing-objects-from-selection)
