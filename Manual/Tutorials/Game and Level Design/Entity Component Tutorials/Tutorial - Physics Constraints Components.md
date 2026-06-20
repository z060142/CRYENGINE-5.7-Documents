# Tutorial - Physics Constraints Components

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/56655890
- Page ID: 56655890
- Breadcrumb: Tutorials > Game and Level Design > Entity Component Tutorials > Tutorial - Physics Constraints Components
- Parent: Entity Component Tutorials

## Content

Physics constraints can be used by adding components to your entity. This is done by selecting your entity and going to
**
Properties → Add Component
**
.

Before you start, please consider the following:

-
Constraints are only relevant for physicalized entities, which is why in these examples, the entity has a rigidbody component.

-
Constraints are only visible if Helpers are enabled.

##
Point Constraints

Adding a Point Constraint to your entity will add it at the pivot. It appears as a yellow sphere:

![Image](https://www.cryengine.com/docs/static/attachments/56655894)

*
Point Constraint added
*

To see the Constraint helper better, you can turn on Wireframe view with
**
ALT + W
**
or by typing
*
viewport.toggle_wireframe_mode
*
 in the Console.

Depending on where the point that your entity moves around should be, you can move it with the Point Constraint's
**
Transform → Translation
**
 options:

![Image](https://www.cryengine.com/docs/static/attachments/56655896)

*
Moving the Point Constraint
*

 You can now enable physics (1) and pull the entity around with the Physics Tool (2):

![Image](https://www.cryengine.com/docs/static/attachments/56655898)

*
Physics Tool & Enable Physics
*

You will notice that the entity will keep swinging back and forth with the same speed, over the same distance. To make sure it slows down, which is the natural behavior, you can change the
**
Damping
**
 property. 01 to 0.4 is a common range to use.

Adding a Point Constraint prevents the entity from moving from its position (as long as
**
Free Position
**
 is disabled), while allowing it to rotate in any direction (with the default values of
**
0
**
 assigned to
**
Minimum X Angle
**
 and
**
Maximum X Angle
**
).

##
Making the Entity Swing

If you just want your entity to swing along one axis like a pendulum, tweak the following parameters:

-
Minimum X Angle

-
Maximum X Angle
Note that the default values of zero on constraints don't mean the object has zero degrees of movement; it means
*
unlimited
*
 movement. To allow a specific range of movement, use non-zero values. Generally, you'll want to set the
**
Minimum X Angle
**
 to a negative value, like -40, and the
**
Maximum X Angle
**
 to same value in the positive range, like 40. You'll then get this effect:

![Image](https://www.cryengine.com/docs/static/attachments/56655900)

*
Point Constraint pendulum
*

##
Twisting

You'll have noticed that the entity now doesn't twist around anymore. If you still want to give it a bit of a twist, you can change
**
Maximum YZ Angle
**
. When you pull the entity, you'll then see a cone attached to the constraint, indicating how much it will twist around it:

![Image](https://www.cryengine.com/docs/static/attachments/56655901)

*
Twist cone
*

If you want to make it swing along another axis with the same range and twist, simply change the
**
Axis
**
.

It is also possible to offset the Constraint from the entity by changing the
**
Translation
**
 values so it swings in an arc around the Point Constraint:

![Image](https://www.cryengine.com/docs/static/attachments/56655904)

*
Point Constraint offset
*

##
Line Constraints

Adding a Line Constraint to your entity will add it at the pivot, just like the Point Constraint. It is constrained along the Z-axis by default.

This will make the attached entity move along a straight line, like so:

*
![Image](https://www.cryengine.com/docs/static/attachments/56655908)

Line Constraint example
*

The yellow line you can see in the .gif above is the Line Constraint.

To make it go along a different axis, set the
**
Z
**
 axis to
**
0
**
 and the other axis to
**
1
**
. In the example above, the axes were set up as follows:

![Image](https://www.cryengine.com/docs/static/attachments/56655910)

*
Axes setup example
*

##
Changing the Range

To change how far the entity moves to either side of the entity (along the Line Constraint, of course), change the
**
Minimum Limit
**
 and
**
Maximum Limit
**
. Remember that the default values of zero on constraints don't mean the object cannot move; rather, it means
*
unlimited
*
 movement. To allow a specific range of movement, use non-zero values.

##
Rotating the Line Constraint

Rotating the Line Constraint is not done by changing the Rotation properties, but by changing the Axes properties.

Keep in mind though, that when more than one of these axes is set to a positive value, the Line Constraint will calculate an average between the two and draw the Line Constraint along that line.

For example, setting both
**
X
**
 and
**
Y
**
 to
**
1
**
 will change them both to
**
0.7071
**
, which equates to a 45° angle along the X and Y axes:

![Image](https://www.cryengine.com/docs/static/attachments/56655912)

*
45 degree angle
*

Making one of these negative will turn the Line Constraint 180°.

You can even rotate the Line Constraint on 3 axes this way:

![Image](https://www.cryengine.com/docs/static/attachments/56655916)

*
Rotated in 3 dimensions
*

##
Plane Constraints

Plane Constraints make your entity move parallel to a flat surface, like the ground.

Plane Constraints don't have to be horizontal, they can also be at an angle, so the entity goes up and down a hill, for example. This is done with the
**
Rotation
**
 property.

##
Spinning Around

By default,
**
Twist Rotation Min Angle
**
 and
**
Twist Rotation Max Angle
**
 are set to -360 and 360 respectively. This means the entity is allowed to spin around its Z-axis freely:

![Image](https://www.cryengine.com/docs/static/attachments/56655923)

*
Spinning around Z-axis
*

Setting these to 0 will make sure the entity always faces the same way, or a range of values can be used to limit the degree of rotation.

##
Wobbling

If instead of spinning, you want your entity to wobble around its axis from the point where the Plane Constraint intersects the line on its perpendicular axis, enter a value in the
**
Bend Max Angle
**
 property. When pulling it around with the Physics Tool, it will display a cone on this intersection, showing the angle of movement:

![Image](https://www.cryengine.com/docs/static/attachments/56655924)

*
Wobbling
*

##
Video Tutorial

To watch a video tutorial about these Constraints, see below.

[Embed: https://www.youtube.com/watch?v=eYZa3vaoVn4]
[Point Constraints](#point-constraints)
[Line Constraints](#line-constraints)
[Plane Constraints](#plane-constraints)
[Video Tutorial](#video-tutorial)
