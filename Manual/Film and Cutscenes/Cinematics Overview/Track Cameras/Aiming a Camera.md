# Aiming a Camera

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/26874164
- Page ID: 26874164
- Breadcrumb: Film and Cutscenes > Cinematics Overview > Track Cameras > Aiming a Camera
- Parent: Track Cameras

## Content

##
Overview

A Camera can be created together with a CameraTarget entity which the Camera will then always point at.

CameraTarget entities can only be created when adding a new Camera.

To add a Camera with a CameraTarget entity:

-
In the RollupBar, open the Objects tab.

-
Select Misc.

-
In the
*
Object Type
*
 panel, click the
*
Camera
*
 button.

-
Click at the location in the 3D view where you want to place the Camera
**
and keep the mouse button pressed
**
.

-
While keeping the mouse button pressed, move the cursor away from the Camera entity in the 3D view. You'll see that this will create another entity.

-
Release the mouse button.
The second entity that got created is the CameraTarget. It can be animated in Track View and the camera will always point at its position. In turn, the Camera's rotation can't be modified on its own anymore.

##
Flowgraph-based Solution

If you want a camera to point at the player, an AI entity or something similar, use the attached flowgraph:
[/docs/static/attachments/1212676](
Tracking Camera.xml
)

[#flowgraph-based-solution](
Flowgraph-based Solution
)
