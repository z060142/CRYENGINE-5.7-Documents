# Selection

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/29450449
- Page ID: 29450449
- Breadcrumb: Editor Tools > Designer Tool Tab > Modeling > Selection
- Parent: Modeling

## Content

##
Overview

The
**
Selection
**
**

**
section of the Designer tool lets you edit the basic shapes that you made with the tools in the Shapes section.

*
[Image: /docs/static/attachments/28900539]

*

As shown above, this section contains several different tools to chose from.

##
Vertex/Edge/Polygon

The Vertex/Edge/Polygon tools provide easy ways not only to select vertices, edges and polygons but also to move those elements. A vertex, an edge or a polygon is usually called an
*
element
*
.

More than two buttons among Vertex, Edge and Polygon buttons can be selected at the same time by pressing the each button holding
**
Ctrl
**
 and clicking the buttons.

There are 3 ways to select elements:

-
By clicking
**
LMB
**
 on an element.

This way allows you to select an element and deselect any currently selected elements.

-
By clicking
**
LMB + Ctrl
**
 on an element or dragging
**
LMB + Ctrl
**
 from an element.

This way allows you to select an element keeping the existing elements.

-
By dragging the mouse holding
LMB
 or
LMB + Ctrl
 from no element.

This way allows you to select elements within a selection box.

If you are holding
Ctrl
, the existing selected polygons will remain selected. If not, they will be deselected.

##
Transformation

You can transform Designer objects by using the
**
Vertex
**
,
**
Edge
**
 and
**
Polygon
**
 tools in different ways:

-
By clicking on and element and dragging
**
LMB
**
.

The selected elements will follow the mouse cursor on the screen without the help of the gizmos.

Holding
**
SHIFT
**
, the selected polygons will be detached from the adjacent polygons when they are moved.

-
By manipulating Gizmos.

For fine-tuning, you can use
**
View
**
,
**
Local
**
,
**
Parent
**
,
**
World
**
 and
**
Custom
**
 coordinates. For more information on the Coordinate System, please see
[/docs/static/engines/cryengine-5/categories/23756816/pages/23308619](
this page
)
.

Holding
**
SHIFT
**
, the selected polygons will be detached from the adjacent polygons when they are moved.
**
Move
**
 mode - moves the elements:

[Image: /docs/static/attachments/28900586]
[Image: /docs/static/attachments/28900585]

**
Rotate
**
 mode - rotates the elements:

[Image: /docs/static/attachments/28900584]
[Image: /docs/static/attachments/28900583]

**
Scale
**
 mode - scales the elements:

[Image: /docs/static/attachments/28900582]
[Image: /docs/static/attachments/28900581]

##
Pivot

This tool provides a convenient way to change the pivot position to where you want it to be.

##
How it Works

First, choose if you want the pivot to be positioned on a vertex of the bound box or the mesh. You do this in the Pivot properties:

[Image: /docs/static/attachments/28900580]

##
BoundBox

You can select a pivot among 27 vertices consisting of the bound box:

[Image: /docs/static/attachments/28900579]

##
Mesh

This mode allows you to select a pivot among all vertices of the designer object:

[Image: /docs/static/attachments/28900578]

You can then click on any of the points shown to move the pivot point:

[Image: /docs/static/attachments/28900577]

##
AllNone

Using this tool, you will be able to select or deselect all elements with just one click.

##
How it Works

When no elements are selected and you press the
**
AllNone
**
 button, all elements will be selected:

##
Vertex mode

*
No vs. all vertices selected
*

[Image: /docs/static/attachments/28900576]

[Image: /docs/static/attachments/28900575]

##
Edge mode

*
No vs. all edges selected

*
[Image: /docs/static/attachments/28900574]

[Image: /docs/static/attachments/28900573]

##
Polygon mode

*
No vs. all polygons selected

*
[Image: /docs/static/attachments/28900572]

[Image: /docs/static/attachments/28900571]

When not all elements are selected, all the selected elements will be deselected when clicking the
**
AllNone
**
 button.

##
Connected

This selection tool is useful if you want to select all faces connecting one another from the selected face.

##
How it Works

The sphere and the other shape in the following image is in one designer object but they are not connected with each other.

[Image: /docs/static/attachments/28900570]

With a polygon of the sphere selected, if you press the
**
Connected
**
 button, all the polygons of the sphere will be selected, but the polygons in the other shape won't be, because the other shape isn't connected to the sphere with any edges:

[Image: /docs/static/attachments/28900569]

[Image: /docs/static/attachments/28900568]

##
Grow

This tool provides a easy way of expanding a selection based on the current selected polygons.

##
How it Works

Select a polygon and click the
**
Grow
**
 button. Every time you click the button, the adjacent polygons will be selected as well as the already selected ones:

[Image: /docs/static/attachments/28900567]

[Image: /docs/static/attachments/28900566]

[Image: /docs/static/attachments/28900565]

##
Loop

With the
**
Loop
**
 tool, you can select serial linked edges or faces which form a loop from selected edges or faces.

##
How it Works

##
Edge Loop Selection

Select an edge and click the
**
Loop
**
 button to select successive edges from the selected edges as follows.

The left image shows selected edges or selected edges and the right images is the results after clicking
**
Loop
**
 button:

[Image: /docs/static/attachments/28900564]

[Image: /docs/static/attachments/28900563]

Of course, this does not only work for horizontal edges, but also for vertical ones:

[Image: /docs/static/attachments/28900562]

[Image: /docs/static/attachments/28900561]

You can even select different horizontal and vertical edges and it will loop around the shape when you click the
**
Loop
**
 button:

[Image: /docs/static/attachments/28900560]

[Image: /docs/static/attachments/28900559]

##
Polygon Loop Selection

This loop function also works for Polygons, however, this requires two polygons to be selected (by holding
**
Ctrl
**
 while selecting two polygons) before clicking the Loop button to determine the direction of the loop:

[Image: /docs/static/attachments/28900558]

[Image: /docs/static/attachments/28900557]

As with Edge loops, this also works vertically:

[Image: /docs/static/attachments/28900556]

[Image: /docs/static/attachments/28900555]

##
Ring

The Ring tool is similar to the Loop tool, but differs in that it selects edges or polygons in a loop which are
*
not
*
 connected.

##
How it Works

##
Edge Ring Selection

Select an edge or edges and click the
**
Ring
**
 button:

[Image: /docs/static/attachments/28900554]

[Image: /docs/static/attachments/28900553]

As before, this also works with vertical edges:

[Image: /docs/static/attachments/28900551]

[Image: /docs/static/attachments/28900552]

And you can also select multiple edges and create several rings by clicking the
**
Ring
**
 button:

[Image: /docs/static/attachments/28900544]

[Image: /docs/static/attachments/28900543]

##
Polygon Ring Selection

As with the
**
Loop
**
 tool, you can select two or more polygons as follows and click the
**
Ring
**
 button. As the
**
Ring
**
 button makes a ring with polygons that are
*
not
*
 connected, it will have the opposite effect to the
**
Loop
**
 tool:

[Image: /docs/static/attachments/28900548]

[Image: /docs/static/attachments/28900547]

And again, you can make more than one ring:

[Image: /docs/static/attachments/28900546]

[Image: /docs/static/attachments/28900545]

##
Invert

With the Invert tool you can invert the selection of polygons.

This will not work when selecting Edges. If you select a number of Edges and then click Invert, it will simply select all edges and therefore work like the AllNone tool.

##
How it Works

Select the polygons you want to invert and click the
**
Invert
**
 button:

[Image: /docs/static/attachments/28900542]

[Image: /docs/static/attachments/28900541]

[#vertexedgepolygon](
Vertex/Edge/Polygon
)
[#pivot](
Pivot
)
[#allnone](
AllNone
)
[#connected](
Connected
)
[#grow](
Grow
)
[#loop](
Loop
)
[#ring](
Ring
)
[#invert](
Invert
)
[#how-it-works](
How it Works
)
