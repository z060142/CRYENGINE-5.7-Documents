# Jiggle Bones Physics

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/23307982
- Page ID: 23307982
- Breadcrumb: Asset Prep (External) > Asset Exporting Overview > Geometry Creation Overview > Animated Geometry > Basics (animated) > Physics (animated) > Jiggle Bones Physics
- Parent: Physics (animated)

## Content

##
Jiggle Bones (Based on Flex)

Go to
**
Create Panel ->
**
Systems
**
 ->
**
Bones and create a bone chain. Use
**
SplineIKSolver
**
 as Solver and make sure
**
Assign to Children
**
 /
**
Assign to Root
**
 is selected.

Create your bonechain by clicking left.

![Image](https://www.cryengine.com/docs/static/attachments/23994267)

It is important that the bonechain is a precise, even line because it defines the
**
standard-pose
**
. Use snap to grid.

![Image](https://www.cryengine.com/docs/static/attachments/23994268)

When you complete the chain by clicking the right mouse button a dialog opens. Make sure
**
Auto Create Spline
**
 and
**
Create Helpers
**
 is active. You also need to check if the checkbox
**
"Box"
**
 under display is active.

After clicking
**
OK
**
, the Spline will be automatically created.

![Image](https://www.cryengine.com/docs/static/attachments/23994269)

Create a sphere or something you want to have as the base for the system. Make sure your first point of the SplineIK is inside the object you just created. Then link only the first control box of the Spline-IK to the base, which in this case, is the sphere.

![Image](https://www.cryengine.com/docs/static/attachments/23994270)

Apply a Flex-Modifier to the Spline and adjust the values.

Good settings to start with are:

-
**
Flex:
**
 2

-
**
Strength:
**
 1

-
**
Sway:
**
 7

-
**
Use Weights:
**
 ON

-
**
Solver:
**
 Runge-Kutta4

-
**
Samples:
**
 2
![Image](https://www.cryengine.com/docs/static/attachments/23994271)

Go to
**
Create Panel -> Space Warps -> Forces
**
 and create a Gravity Node.

![Image](https://www.cryengine.com/docs/static/attachments/23994272)

Select your Spline again and in the Rollout
**
Forces and Deflectors
**
 add the Gravity node to the list. Adjust the other modifiers.

![Image](https://www.cryengine.com/docs/static/attachments/23994273)

In the Rollout Advanced Springs on the bottom, check
**
Enable Advanced Springs
**
.

On the bottom press
**
Hold Length
**
 and set it how you want it. (0 is maximum stretching and 100 is no stretching)

Click
**
Options
**
 and click
**
Hold Shape Springs
**
. Tweak the Hold Shape Radius (good radius value might be the Average Edge Length which you can see in the bottom line)

![Image](https://www.cryengine.com/docs/static/attachments/23994274)

In the Flex Modifier expand the branch and select Edge Vertices. Then select the first vertex in the Spline which is placed inside the base object (Sphere).

Finally you just need to animate the Base (Sphere). Play the animation and see your bones jiggling.
