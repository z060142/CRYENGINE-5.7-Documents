# Cameras

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/26871553
- Page ID: 26871553
- Breadcrumb: Entity > Cameras
- Parent: Entity

## Content

##
Overview

Cameras in CRYENGINE are represented by the
[/docs/static/engines/cryengine-5/categories/28704770/pages/29796988](
CCamera
)
 structure, and represent a view into the world. The main camera needs to be set by calling
[/docs/static/engines/cryengine-5/categories/28704770/pages/29797143](
ISystem::SetViewCamera
)
 at any point before
[/docs/static/engines/cryengine-5/categories/28704770/pages/29797056](
UpdateBeforeFinalizeCamera
)
,

A camera is commonly initialized with
[/docs/static/engines/cryengine-5/categories/28704770/pages/29796988](
CCamera::SetFrustum
)
, specifying resolution, field of view, near plane and the far plane, in addition to
[/docs/static/engines/cryengine-5/categories/28704770/pages/29796988](
CCamera::SetMatrix
)
 being used to set the world transformation of the specified camera.

Note that camera handling is automated by the Camera Component in the default components plug-in, see
Cry::DefaultComponents::CCameraComponent
.

##
Table of Contents

[#api-types](
API Types
)
[#audio-listeners](
Audio Listeners
)
[#asynchronous-camera-injection-vr](
Asynchronous Camera Injection (VR)
)
[#conclusion](
Conclusion
)

##
API Types

-
[/docs/static/engines/cryengine-5/categories/28704770/pages/29796988](
CCamera
)

-
[/docs/static/engines/cryengine-5/categories/28704770/pages/29797056](
UpdateBeforeFinalizeCamera
)

##
Audio Listeners

Cameras will need to maintain an audio listener in order for audio to be played at the camera origin. Keep in mind that this is automated in the Camera Component mentioned above. For more information, see
[/docs/static/engines/cryengine-5/categories/23756813/pages/26871538#Audio-Listeners](
Audio Listeners
)
.

##
Asynchronous Camera Injection (VR)

A big problem in Virtual Reality is the latency between the user moving the tracked headset, and the rendered picture on screen. Besides rendering as fast as possible, CRYENGINE uses late-stage camera injection in order to update the camera pose as late as possible in order to avoid a mismatch between the rendered frame and the new location of the headset.

This is achieved using
[/docs/static/engines/cryengine-5/categories/28704770/pages/29797340](
IHmdDevice::IAsyncCameraCallback
)
. Note that this is handled by default in the Camera Component mentioned in the Overview above, in addition to the Room Scale Camera Component.

[/docs/static/engines/cryengine-5/categories/28704770/pages/29797340](
Example
)

##
Conclusion

This concludes the article on Cameras, you may be interested in:

-
[/docs/static/engines/cryengine-5/categories/23756813/pages/28184910](
Execution Order and Lifecycle
)

-
[/docs/static/engines/cryengine-5/categories/23756813/pages/29428286](
Input and Action Mapping
)
