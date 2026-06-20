# Camera First Person

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/26874157
- Page ID: 26874157
- Breadcrumb: Film and Cutscenes > Cinematics Overview > Track Cameras > Camera First Person
- Parent: Track Cameras

## Content

##
Overview

Different ways of setting up first person camera:

-
Link the camera to the character.

-
Link the camera to the character's camera bone.

-
Link the camera to the TagPoint.

##
Link the camera to the character

The method of linking the camera to the character works fine for
**
rough blocking
**
 where the actor has no animation applied in the Track View. By attaching the camera to the character and positioning it close to the camera bone (eye level), we can do rough blocking or experiment on the character's point of view and the pace of the scene.

Caution
This method is only good for doing rough blocking. However, it is
**
NOT
**
 the best way to carry this method until the final process unless the character is being animated in trackview only (f.ex. vehicle moving, and the camera is mimicking the front seat viewport).

##
Link the camera to the character's camera bone

Another possibility to create the first person camera is to attach the camera to the actor's camera bone. In theory, this method may sound easiest when the actor has animation applied into the trackview. You can attach a camera to the actor's camera bone so that the camera will follow the camera bone of the character. The fact is, this is not the best method of creating first person camera at all. It is good for referencing, but not for the final process since the information of camera bone can be very rigid and often clip through the actor's body especially if that animation is from mocap. Furthermore, it is impossible to manipulate.

##
Link the camera to the tagpoint

The best way of setting up the camera is to attach both actor and the camera to the tagpoint. This way the camera and the character can be animated independently. The tagpoint act as an anchor that hold both actor and camera together, make this easy when you need to move the actor around even after you have finished adjusting the scene. With the combination of one extra camera linking to the actor's camera bone, you can easily match your main camera to the reference camera to get the right movement, but it is also easily adjustable and able to improve the camera.

##
How to set up the camera

First, link the actor and the main camera (this is the first person camera) with a tagpoint.

Then create another camera. This is the reference camera. Link this camera to the actor's camera bone.

At this point, you are having 2 cameras, one is the main camera which is going to be used in the final scene, the other one that is attach to the actor's camerabone is the reference camera, tracking information of the actor's animation head movement.

Align the reference camera to the camera bone by position the camera to 0, 0, 0

When assigning animation onto the actor in the trackview sequence, you will see the reference camera is tracking the movement of the actor's camerabone. Assign the maincamera in the trackview, and start aligns the main camera to the reference camera.

[#link-the-camera-to-the-character](
Link the camera to the character
)
[#link-the-camera-to-the-characters-camera-bone](
Link the camera to the character's camera bone
)
[#link-the-camera-to-the-tagpoint](
Link the camera to the tagpoint
)
[#link-the-camera-to-the-character](
Link the camera to the character
)
[#link-the-camera-to-the-characters-camera-bone](
Link the camera to the character's camera bone
)
[#link-the-camera-to-the-tagpoint](
Link the camera to the tagpoint
)

##
Overview

Different ways of setting up first person camera:

-
Link the camera to the character.

-
Link the camera to the character's camera bone.

-
Link the camera to the TagPoint.

##
Link the camera to the character

The method of linking the camera to the character works fine for
**
rough blocking
**
 where the actor has no animation applied in the Track View. By attaching the camera to the character and positioning it close to the camera bone (eye level), we can do rough blocking or experiment on the character's point of view and the pace of the scene.

Caution
This method is only good for doing rough blocking. However, it is
**
NOT
**
 the best way to carry this method until the final process unless the character is being animated in trackview only (f.ex. vehicle moving, and the camera is mimicking the front seat viewport).

##
Link the camera to the character's camera bone

Another possibility to create the first person camera is to attach the camera to the actor's camera bone. In theory, this method may sound easiest when the actor has animation applied into the trackview. You can attach a camera to the actor's camera bone so that the camera will follow the camera bone of the character. The fact is, this is not the best method of creating first person camera at all. It is good for referencing, but not for the final process since the information of camera bone can be very rigid and often clip through the actor's body especially if that animation is from mocap. Furthermore, it is impossible to manipulate.

##
Link the camera to the tagpoint

The best way of setting up the camera is to attach both actor and the camera to the tagpoint. This way the camera and the character can be animated independently. The tagpoint act as an anchor that hold both actor and camera together, make this easy when you need to move the actor around even after you have finished adjusting the scene. With the combination of one extra camera linking to the actor's camera bone, you can easily match your main camera to the reference camera to get the right movement, but it is also easily adjustable and able to improve the camera.

##
How to set up the camera

First, link the actor and the main camera (this is the first person camera) with a tagpoint.

Then create another camera. This is the reference camera. Link this camera to the actor's camera bone.

At this point, you are having 2 cameras, one is the main camera which is going to be used in the final scene, the other one that is attach to the actor's camerabone is the reference camera, tracking information of the actor's animation head movement.

Align the reference camera to the camera bone by position the camera to 0, 0, 0

When assigning animation onto the actor in the trackview sequence, you will see the reference camera is tracking the movement of the actor's camerabone. Assign the maincamera in the trackview, and start aligns the main camera to the reference camera.
