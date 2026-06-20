# Cameras

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/26871553
- Page ID: 26871553
- Breadcrumb: Entity > Cameras
- Parent: Entity

## Content

##
Overview

Cameras in CRYENGINE are represented by the
[CCamera](/docs/static/engines/cryengine-5/categories/28704770/pages/29796988)
 structure, and represent a view into the world. The main camera needs to be set by calling
[ISystem::SetViewCamera](/docs/static/engines/cryengine-5/categories/28704770/pages/29797143)
 at any point before
[UpdateBeforeFinalizeCamera](/docs/static/engines/cryengine-5/categories/28704770/pages/29797056)
,

A camera is commonly initialized with
[CCamera::SetFrustum](/docs/static/engines/cryengine-5/categories/28704770/pages/29796988)
, specifying resolution, field of view, near plane and the far plane, in addition to
[CCamera::SetMatrix](/docs/static/engines/cryengine-5/categories/28704770/pages/29796988)
 being used to set the world transformation of the specified camera.

Note that camera handling is automated by the Camera Component in the default components plug-in, see
Cry::DefaultComponents::CCameraComponent
.

##
Table of Contents

[API Types](#api-types)
[Audio Listeners](#audio-listeners)
[Asynchronous Camera Injection (VR)](#asynchronous-camera-injection-vr)
[Conclusion](#conclusion)

##
API Types

-
[CCamera](/docs/static/engines/cryengine-5/categories/28704770/pages/29796988)

-
[UpdateBeforeFinalizeCamera](/docs/static/engines/cryengine-5/categories/28704770/pages/29797056)

##
Audio Listeners

Cameras will need to maintain an audio listener in order for audio to be played at the camera origin. Keep in mind that this is automated in the Camera Component mentioned above. For more information, see
[Audio Listeners](Audio.md#Audio-Listeners)
.

##
Asynchronous Camera Injection (VR)

A big problem in Virtual Reality is the latency between the user moving the tracked headset, and the rendered picture on screen. Besides rendering as fast as possible, CRYENGINE uses late-stage camera injection in order to update the camera pose as late as possible in order to avoid a mismatch between the rendered frame and the new location of the headset.

This is achieved using
[IHmdDevice::IAsyncCameraCallback](/docs/static/engines/cryengine-5/categories/28704770/pages/29797340)
. Note that this is handled by default in the Camera Component mentioned in the Overview above, in addition to the Room Scale Camera Component.

[Example](/docs/static/engines/cryengine-5/categories/28704770/pages/29797340)

##
Conclusion

This concludes the article on Cameras, you may be interested in:

-
[Execution Order and Lifecycle](Execution%20Order%20and%20Lifecycle.md)

-
[Input and Action Mapping](Input%20and%20Action%20Mapping.md)
