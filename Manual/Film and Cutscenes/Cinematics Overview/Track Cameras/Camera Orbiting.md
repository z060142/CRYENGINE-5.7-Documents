# Camera Orbiting

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/26874173
- Page ID: 26874173
- Breadcrumb: Film and Cutscenes > Cinematics Overview > Track Cameras > Camera Orbiting
- Parent: Track Cameras

## Content

##
Overview

To make a simple orbiting camera that follows an object, link the camera to a TagPoint and then link the TagPoint to the object. This way the TagPoint entity can act as a pivot, animating its rotation in Track View will make the camera rotate around your object.

*
Link the entities together in this order.
*

*
Afterwards move the TagPoint to 0,0,0 in local space.
*

##
Potential Problems with Rotation

The rotation of your target entity (e.g. a helicopter) itself might cause unwanted effects on the orbit camera.

##
Solution 1: Adjusting Pivot Rotation

One solution to counter-balance these problems by adjusting the pivot's rotation. For example, if the helicopter has a X rotation of -15, setting the pivot's X rotation to 15 will make the values cancel each other out.

As a result, the helicopter will appear tilted, but the horizon will be parallel to the screen.

##
Solution 2: Using a Different Setup

Another solution would be to change the setup to make the TagPoint's rotation independent of the object we want to follow.

To do so, use one root TagPoint that will be used to animate the position. Link your target entity to it (e.g. a helicopter) and only animate its rotation. Then link the pivot TagPoint and the attached camera to the root TagPoint as well.

Now you can rotate your target and the orbit pivot independently of each other.

The drawback of this solution is that the setup gets much more complicated. For this reason it should only be used if absolutely necessary.

##
Using an Orbit Camera for Reference

In case you want to make a camera that transitions out of an orbit movement and generally is more flexible, use the setup as reference only.

Use another (non-linked) camera and align it to the orbit camera at different points in time (use
**
Align to Object
**
). Even with a small number of keys you can easily recreate the orbit movement.

[#potential-problems-with-rotation](
Potential Problems with Rotation
)
[#solution-1-adjusting-pivot-rotation](
Solution 1: Adjusting Pivot Rotation
)
[#solution-2-using-a-different-setup](
Solution 2: Using a Different Setup
)
[#using-an-orbit-camera-for-reference](
Using an Orbit Camera for Reference
)
