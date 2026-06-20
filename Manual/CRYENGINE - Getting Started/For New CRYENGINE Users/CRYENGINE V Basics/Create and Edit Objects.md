# Create and Edit Objects

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/23308617
- Page ID: 23308617
- Breadcrumb: CRYENGINE - Getting Started > For New CRYENGINE Users > CRYENGINE V Basics > Create and Edit Objects
- Parent: CRYENGINE V Basics

## Content

##
Overview

Learn about adding objects to your scene and how to edit them.

##
Creating Objects

##
Brushes, Entities, Area Boxes, Particles

Objects which have a predefined setup can easily be created by opening the
**
Create Object
**
 tool, choosing a category and double-clicking on the object you want to place in your level. The newly created object will follow the mouse cursor once the mouse cursor is placed inside the main 3D Viewport.

**
Snap to Geometry
**
 will automatically be turned on to help you with placing the object in the scene.

You can also turn on
**
Grid Snapping
**
,
**
Angle Snapping
**
 and
**
 Rotate to Surface Normal
**
 to refine your placement.

**
[/docs/static/engines/cryengine-5/categories/23756816/pages/44960236](
Click here
)
**
 for more information on snapping.

Click the Left Mouse Button (
**
LMB
**
) to place the object in the level.

##
Area Shapes (and other poly-line based objects)

Area Shapes are custom shapes which need to be drawn in the level manually.

In the
**
Create Object
**
 tool, go to
**
Area -> Shape
**
 to activate the shape creation.

Once you move the mouse cursor into the main Viewport, a small box, called 'Point' (vertex) will be projected into the Viewport.

Placement can be controlled by enabling
**
constraints
**
,
**
Grid Snapping
**
,
**
Angle Snapping
**
,
**
Snap to Terrain
**
, and
**
Snap to Geometry
**
.

Double-click with the Left Mouse Button (
**
LMB
**
) to finalize the shape.

##
Modifying a Shape

Once you have created your shape, in the
**
Properties
**
 tool, you can enter the
**
Edit Shape
**
 mode and select, move, add, or remove vertices from the shape to configure it to fit the area you want.

-
Double-click on an existing vertex of the shape to remove it.

-
Press
**
 Ctrl+LMB
**
 to add a new Vertex into the shape (click along the shapes perimeter to add).

-
Use the
**
Split
**
 tool to break the shape into 2 pieces. Once activated, hover over the edge to select the first point where you want the cut to happen, followed by the second point to define the cut line. The result will be two new shapes that are completely enclosed.

##
Linking Entities to Shapes

The way we link shapes to other entities has changed slightly. Now we are using a more standardized system that follows the other tools. In the
**
Properties
**
 tool you can find the Operators section:

[Image: /docs/static/attachments/24151105]

-
Click the
**
0
**
 next to
**
Targets
**
 to open a menu and either Add or Insert a link.

-
Once the option has appeared, click inside the input field and it will ask you to Pick an Entity.
[Image: /docs/static/attachments/24151106]

-
Select the entity in the 3D Viewport to create the link to the shape.
[Image: /docs/static/attachments/24151107]

-
Now the Trigger Entity called
**
AB01_LS_trig
**
 is linked to this shape.

##
Duplicating Objects

Duplicate a selected object by pressing
**
Ctrl+D
**
. Move the mouse pointer to place the object, click
**
LMB
**
 to place the object.

Placement can be controlled by enabling
**
constraints
**
,
**
Grid Snapping
**
,
**
Angle Snapping
**
,
**
Snap to Terrain
**
, and
**
Snap to Geometry
**
.

You can also duplicate an object by going to the menu bar at the top of the screen:
**
Edit -> Duplicate
**
.

##
Deleting Objects

Use the
**
Delete
**
 button on your keyboard to delete selected objects.

If you want to undo the deletion, you can use the
**
Undo
**
 button or use the shortcut
**
Ctrl+Z
**
.

[#creating-objects](
Creating Objects
)
[#duplicating-objects](
Duplicating Objects
)
[#deleting-objects](
Deleting Objects
)
