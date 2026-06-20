# Transforming Objects

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/23308620
- Page ID: 23308620
- Breadcrumb: CRYENGINE - Getting Started > For New CRYENGINE Users > CRYENGINE V Basics > Transforming Objects
- Parent: CRYENGINE V Basics

## Content

##
Overview

The CRYENGINE contains a variety of ways to transform objects. On this page, you will read the basics of how to use the different modes that are at your disposal.

##
Axis Gizmo

The Axis Gizmo is the interface to transform objects in the scene. It has handles for the 3 axes and planes, and the tips of the handles change shape depending on the mode selected. What it looks like and what it does depends on the mode selected.

##
Select Mode

The Select mode lets you select objects in the scene without accidentally moving them.

*
[Image: /docs/static/attachments/25501274]

*

This can be done by simply clicking on an object to select only that specific one, holding
**
Ctrl
**
 and selecting any number of separate objects or clicking and dragging the cursor in the Viewport window to create a selection box and select every object within it.

Select mode can be activated by clicking on the button in the toolbar, using the Keyboard Shortcut '
**
4
**
', or via
**
Edit -> Editing Mode -> Select Mode
**
.

In Select mode, the Axis Gizmo has nothing on the end of each axis:

*
[Image: /docs/static/attachments/25523786]

*

##
Move Mode

The
**
Move
**
 mode lets you select objects and move them around in the level.

[Image: /docs/static/attachments/25501275]

Move mode can be activated by clicking on the  button in the toolbar, using the Keyboard Shortcut '
**
1
**
', or via
**
Edit -> Editing Mode -> Move
**
.

In Move mode, the Axis Gizmo has an arrow on the end of each axis.

[Image: /docs/static/attachments/25523787]

You can click and drag the arrows to move the object in one direction, or you can click and drag one of the square-shaped plane gizmos between the axis gizmos to move the object along two axes at the same time.

Finally, you can click and drag the white sphere in the middle to move the object around horizontally and vertically in screen space.

The arrow gizmos will display a dotted line connecting the initial and final position. The plane gizmos will display lines that help the user discern where the plane of motion is located.
In order to fine-tune the interactive translation, you can activate
**
[/docs/static/engines/cryengine-5/categories/23756816/pages/44960236](
Grid snapping
)
**
,
[/docs/static/engines/cryengine-5/categories/23756816/pages/44960236](
**
Snap to Terrain/Snap to Geometry
**
)
,
Axis Constraints
 (see below)
, or adjust the
**
[/docs/static/engines/cryengine-5/categories/23756816/pages/23308619](
Coordinate System
)
**
 you want to use for the translation.

##
Rotate Mode

Rotate mode lets you select objects and rotate them interactively in the Viewport window.

*
[Image: /docs/static/attachments/25523792]

*

Rotate mode can be activated by clicking on the button, using the Keyboard Shortcut '
**
2
**
', or via
**
Edit -> Editing Mode -> Rotate
**
.

In Rotate mode, the Axis Gizmo consists of several arcs and a white circle:

[Image: /docs/static/attachments/25523789]

The red, green and blue wheel gizmos correspond to the X, Y and Z axes, while the white wheel will always rotate the object in screen space.

The white ball in the middle allows you to tweak rotation on two axes of the object at the same time.

When you use the wheel gizmos to rotate the object, you can also view the angle of rotation at which the object is being rotated:

[Image: /docs/static/attachments/25523790]

By enabling
**
Toggle snapping to angle
**
 option in the perspective window, you view the markers that allows you to rotate the object accurately.

##
Changing Rotation Interaction

You can choose between a linear dial style and a linear interaction style when interacting with rotation gizmos. You can change this style in
**
Edit -> Preferences

-> Viewport -> Gizmo -> Axis Gizmo -> Interaction for Rotation Gizmo
**
.

##
Dial

When the dial interaction style is active, you rotate the object by rotating your mouse cursor around the center of the gizmo. The distance between the center of the circle and the mouse cursor determines how much the object will rotate; the further away from the center, the more accurately you can rotate the object.

The black arrows will show you where your mouse cursor is.

*
[Image: /docs/static/attachments/26938232]

*

##
Linear

When the linear interaction style is active, select a rotation plane and drag the mouse cursor to rotate your object. The arrows on the outside of the circle indicate the directions that allow you to drag your mouse for optimal control.

*
[Image: /docs/static/attachments/26938233]

*

##
Scale Mode

Scale mode lets you select objects and scale them interactively in the Viewport window.

[Image: /docs/static/attachments/25523793]

Scale mode can be activated by clicking on the  button in the toolbar, using the Keyboard Shortcut '
**
3
**
', or via
**
Edit -> Editing Mode -> Scale
**
.

In Scale mode, the Axis Gizmo has a cube on the end of each axis:

[Image: /docs/static/attachments/25523791]

Similar to Move Mode, you can click and drag the cubes to scale the object in one direction, or you can click and drag one of the square-shaped plane gizmos between the axis gizmos to move the scale along two axes at the same time.

Be cautious when doing this, though, as non-uniform scaling does not affect the physics mesh. Player collision or hit detection might not work as expected anymore.
Finally, you can click and drag the white cube in the middle to scale the object along all three axes at the same time.

When you scale an object, the gizmo displays how much the object is scaled compared to the original size.
In Move, Rotate and Scale mode, you can also click and drag on the object's mesh to perform these actions. The object will then move, rotate or scale along the axes selected in the Axis Constraints toolbar (see below).

##
Axis Constraints

There are four Axis Constraint buttons on the toolbar:

*
[Image: /docs/static/attachments/25501278]

*

The Axis Constraint toolbar is not shown by default. To show this toolbar, right-click in the toolbar area and click
**
Constraints
**
.

When dragging an object, each icon restrains the object to move in only the direction that you select.

Clicking an axis on the Axis Gizmo will change the constraint as well.

This functionality is most powerful when used together with
**
Lock Selection
**
 (
**
Level -> Selection -> Lock Selection
**
). The object can then be moved, rotated or scaled by clicking and dragging anywhere in the Viewport, not just directly on the Gizmo handles.

[#axis-gizmo](
Axis Gizmo
)
[#select-mode](
Select Mode
)
[#move-mode](
Move Mode
)
[#rotate-mode](
Rotate Mode
)
[#scale-mode](
Scale Mode
)
[#axis-constraints](
Axis Constraints
)
