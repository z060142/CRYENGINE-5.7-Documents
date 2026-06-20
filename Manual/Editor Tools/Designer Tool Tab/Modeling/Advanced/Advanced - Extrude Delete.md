# Advanced - Extrude/Delete

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/29450453
- Page ID: 29450453
- Breadcrumb: Editor Tools > Designer Tool Tab > Modeling > Advanced > Advanced - Extrude/Delete
- Parent: Advanced

## Content

##
Overview

The Extrude/Delete section shows the following tools:

*
[Image: /docs/static/attachments/28900666]
*

*

*

##
Extrude

This tool provides a powerful function to push or pull the selected face so you can expand a 2D surface to a 3D shape.

##
How it Works

Place a cursor on a polygon which you would like to push or pull:

[Image: /docs/static/attachments/28900665]

Drag the mouse holding
**
LMB
**
 in the direction of the  normal of the selected polygon:

[Image: /docs/static/attachments/28900664]

[Image: /docs/static/attachments/28900663]

Release
**
LMB
**
 to finish the extrusion.

##
Tips

##
Automatic boundary checks

-
While you push or pull the selected face and it get to the point where it can't be pushed any further back because there is nothing behind it, the polygon will be removed when you release
**
LMB
**
:

[Image: /docs/static/attachments/28900662]

[Image: /docs/static/attachments/28900661]

-
If you extrude a polygon up to the point where it meets another one, the extrusion will stop.

[Image: /docs/static/attachments/28900659]

[Image: /docs/static/attachments/28900660]

-
While the selected polygon is extruded and it reaches the edge of another polygon which is next to the selected one and has the same normal direction, the extrusion will be stopped:

[Image: /docs/static/attachments/28900658]

[Image: /docs/static/attachments/28900657]

For both point 2 and 3, if you want to extrude the polygon beyond this point, simply let go of
**
LMB
**
 and extrude it again.

##
Alignment with an another polygon that has the same normal direction

Holding
**
SHIFT
**
 while extruding and moving the mouse cursor onto a polygon with the same normal direction as the selected polygon will make the polygon that's being extruded snap to the same height as the one under the mouse cursor:

[Image: /docs/static/attachments/28900656]

[Image: /docs/static/attachments/28900655]

##
Resizing the selected face before starting an extrusion

Before starting on extrusion, you can resize the selected face holding SHIFT and moving a mouse and then push or pull it as follows:

*
[Image: /docs/static/attachments/28900605]

[Image: /docs/static/attachments/28900604]

[Image: /docs/static/attachments/28900603]
*

##
Repeating the previous extrusion

If you hold
**
Alt
**
 and click a polygon, the previous push or pull behavior will be repeated:

[Image: /docs/static/attachments/28900607]

[Image: /docs/static/attachments/28900606]

This first selected polygon was pulled by dragging the mouse. The second selected polygon was pulled by holding
**
Alt
**
 and clicking
**
LMB
**
 on it.

##
Extrude Multiple

The
**
Extrude
**
 tool mentioned above is one of the most frequently used tools within the Designer tool but it allows only one polygon to be extruded at a time.

We can use the
**
Extrude Multiple
**
 tool to extrude multiple polygons in individual normal directions, average or x/y/z direction.

The direction they are extruded can be chosen by:

-
Choosing an
**
Extrude Axis
**
 in the Extrude Multiple properties that appear when the
**
Extrude Multiple
**
 button is selected.

[Image: /docs/static/attachments/28900654]

-
Dragging the common normal line
- not one of the polygons - as shown here:
[Image: /docs/static/attachments/76447828]

The common normal line can be either black or white. It should not be confused with the Designer tool's colored axis lines.

*
Extruding Multiple -  Average

*

[Image: /docs/static/attachments/76447822]

*
Extruding Multiple - Individual

[Image: /docs/static/attachments/76447819]
*

*
Extrude Multiple - X

[Image: /docs/static/attachments/76447821]
*

*
Extrude Multiple - Y

[Image: /docs/static/attachments/76447820]
*

*
*
Extrude Multiple - Z

[Image: /docs/static/attachments/76447825]
*
*

##
Offset

This tool takes a polygon and creates an offset of the selected
polygon
in an easy way.

##
How it Works

##
Basic

You can make an offset right in the
*
middle
*
 of a polygon easily by selecting it and then clicking
**
LMB
**
 again:

*
Offset in the middle
*

[Image: /docs/static/attachments/28900649]

[Image: /docs/static/attachments/28900648]

You can also determine exactly where the offset will be placed. You do this by clicking the polygon on which you want to create the offset, and then clicking again and dragging
**
LMB
**
 up and down on the polygon. To confirm the position of the offset, let go of
**
LMB
**
.

[Image: /docs/static/attachments/28900645]

[Image: /docs/static/attachments/28900646]

##
Bridge Edges

With
**
Bridge Edges
**
 checked on the property panel, the vertex pairs between each vertex of the selected polygon and corresponding vertex of the offset polygon will be connected.

[Image: /docs/static/attachments/28900643]

When using this on the top polygon of the cylinder we used before, this will result in the following:

[Image: /docs/static/attachments/28900644]

##
Repeating the Previous Action

**
Alt+LMB
**
 on a polygon will repeat the previous action. Continuing from the previous picture, the following would happen when doing this repeatedly:

[Image: /docs/static/attachments/28900642]

##
Multiple Offset

In the Offset properties, there is also the option
**
Multiple Offset
**
:

[Image: /docs/static/attachments/28900641]

Checking this box, the offset can be applied to multiple polygons by selecting the polygons you want to apply the offset to and then either clicking on one of them once (to create offsets in the middle of the selected polygons) or clicking and dragging on one of the polygons (to determine the exact position of the offsets):

[Image: /docs/static/attachments/28900640]

[Image: /docs/static/attachments/28900639]

##
Weld

This tool is used to merge two selected vertices by moving the first vertex to the second vertex.

##
How it Works

First, select two vertices with the
**
Vertex
**
 tool under the
**
Selection
**
 section:

Click the
**
Weld
**
 button. The vertex you selected first will then move to the second vertex:

[Image: /docs/static/attachments/28900638]

[Image: /docs/static/attachments/28900637]

##
Collapse

With this tool, connected edges will be collapsed to a position exactly in the center.

##
How it Works

Select edges with the
**
Edge
**
 tool in the
**
Selection
**
 section and click
**
Collapse
**
 button:

[Image: /docs/static/attachments/28900636]

[Image: /docs/static/attachments/28900635]

You can also select multiple edge groups as follows. Each edge group will be collapsed to the center of each group in this case.

[Image: /docs/static/attachments/28900634]

[Image: /docs/static/attachments/28900633]

##
Fill

The Fill tool is used to fill a space based on selected edges or vertices. If no elements (edges or vertices) are selected when clicking the
**
Fill
**
 button,, the tool will search for holes in the designer object so that you can fill them easily.

This tool will be very useful to correct a geometry.

##
How it Works

##
From the Selected Edges

-
Two opposite, unconnected edges

If you want to fill a space between two opposite edges, first select the two edges with the
**
Edge
**
 tool in the
**
Selection
**
 section:

[Image: /docs/static/attachments/28900631]

Then click the
**
Fill
**
 button and the space between the two edges will be filled:

[Image: /docs/static/attachments/28900630]

-
More than two connected edges

You can also fill a space by selecting the edges around it with the help of the
**
Loop
**
 tool in the
**
Selection
**
 section and then clicking the
**
Fill
**
 button.

After selecting connected edges, click the
**
Fill
**
 button and the space will be filled:

[Image: /docs/static/attachments/28900629]

[Image: /docs/static/attachments/28900628]

In order to fill a space looking like a polygon consisting of
*
n
*
 edges, you can choose
*
n-1
*
 edges as well as
*
n
*
 edges:

[Image: /docs/static/attachments/28900627]

[Image: /docs/static/attachments/28900626]

##
From Selected Vertices

At least 3 vertices should be selected to fill a space.

**
[Image: /docs/static/attachments/28900625]
**

After selecting vertices, press the
**
Fill
**
 button too then the space defining the vertices will be filled.

[Image: /docs/static/attachments/28900624]

##
By Selecting a hole

If you click the
**
Fill
**
 button without selecting any edges or vertices, the Fill tool will search for holes existing in the designer object.

When you mouse over a hole, the hole will be highlighted:

[Image: /docs/static/attachments/28900623]

You can then fill the highlighted hole by clicking
**
LMB:
**

[Image: /docs/static/attachments/28900622]

Holes in the internal space of a polygon will not be found by the Fill tool.

[Image: /docs/static/attachments/28900621]

In this case you should select edges or vertices as follows to fill the space:

[Image: /docs/static/attachments/28900620]

[Image: /docs/static/attachments/28900619]

[Image: /docs/static/attachments/28900618]

And then click the
**
Fill
**
 button:

[Image: /docs/static/attachments/28900617]

##
Flip

This tool flips a polygon around 180 degrees so the texture is visible on the other side. (only polygons?)

##
How it Works

In the
**
Selection
**
 section of the Designer Tool, click
**
Polygon
**
. Then select a polygon from an object and click the
**
Flip
**
 button:

[Image: /docs/static/attachments/28900615]

[Image: /docs/static/attachments/28900616]

If you look at the polygon from the other side, you'll see the texture:

[Image: /docs/static/attachments/28900614]

##
Merge

This tool can be used for merging multiple designer objects or connected faces to an object or a face.

##
How it Works

##
Object

You can merge objects that are separate Designer Objects into the same Designer Object. You do this by selecting all the different objects and clicking the
**
Merge
**
 button:

[Image: /docs/static/attachments/28900612]

[Image: /docs/static/attachments/28900613]

As you can see from the second picture, when the objects are merged, there will be a box around them.

##
Polygon

The following object, created with the Cube Editor, has many polygons, some of which have a different material assigned to them:

You can merge polygons with the same material by selecting some of them:

And then clicking the
**
Merge
**
 button. The polygons which are connected to the selected ones, have same material ID and are on the same plane will be merged to form one polygon:

##
Separate

Separates selected polygons from the object and turns them into a separate object.

##
How it Works

First, select the polygons you want to separate (hold Ctrl and click LMB on those polygons). Then click the Separate button. You can now for example move these polygons around on their own as a new object:

[Image: /docs/static/attachments/28900590]

[Image: /docs/static/attachments/28900589]

##
Remove

Using the Remove tool, edges and polygons can be deleted.

##
How it Works

##
Edges

In the Selection section of the Designer tool, click the
**
Edge
**
 button. Then select the Edge you want to delete (hold
**
Ctrl
**
 to select more than one Edge). Lastly, click the Remove button to remove the selected Edges:

[Image: /docs/static/attachments/28900611]

[Image: /docs/static/attachments/28900610]

[Image: /docs/static/attachments/28900609]

The Remove tool can be used to merge regions sharing an edge or remove unnecessary edges. After doing this, you can do whatever you want with your newly created polygon, like extrude it:

[Image: /docs/static/attachments/28900608]

##
Copy

**
Copy
**
 lets you make a copy of any elements in an object.

To do this, you select the elements you want to copy, like some polygons and click the
**
Copy
**
 button. The copy will be right on top of the selected elements, so change to Move mode and move the copy away:

**
[Image: /docs/static/attachments/28900592]

[Image: /docs/static/attachments/28900591]

**

##
Remove Doubles

Similar to
[/docs/static/engines/cryengine-5/categories/23756816/pages/29450453#Advanced-Extrude/Delete-Merge](
Merge
)
, but M
erge works on selection, whereas Remove Doubles acts according to threshold and has its own selection.

[#extrude](
Extrude
)
[#extrude-multiple](
Extrude Multiple
)
[#offset](
Offset
)
[#weld](
Weld
)
[#collapse](
Collapse
)
[#fill](
Fill
)
[#flip](
Flip
)
[#merge](
Merge
)
[#separate](
Separate
)
[#remove](
Remove
)
[#copy](
Copy
)
[#remove-doubles](
Remove Doubles
)
