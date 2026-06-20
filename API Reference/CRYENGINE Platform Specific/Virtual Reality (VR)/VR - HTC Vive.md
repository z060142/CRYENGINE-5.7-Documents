# VR - HTC Vive

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/25536775
- Page ID: 25536775
- Breadcrumb: CRYENGINE Platform Specific > Virtual Reality (VR) > VR - HTC Vive
- Parent: Virtual Reality (VR)

## Content

##
Overview

HTC Vive support is now included in CRYENGINE. This article covers the programming side of interacting with a Vive headset. For information on the basics of HTC Vive use, see
[HTC Vive](../../../Manual/Virtual%20Reality/HTC%20Vive.md)
.

Chapters:

[Code](#code)
[Check VR Setup](#check-vr-setup)
[Get HMD Device Tracking State](#get-hmd-device-tracking-state)
[Get Controller Tracking State](#get-controller-tracking-state)
[React to Controller Input](#react-to-controller-input)

##
Code

This section describes how to access VR in general, but specifically the HTC Vive from Game Code.

##
Check VR Setup

In order to check if the current VR setup is valid, you can check if the VR related pointers are set and valid:

```

`
if (IHmdManager* pHmdManager = gEnv->pSystem->GetHmdManager()) // Check, if the HMD Manager exists
{
  if (IHmdDevice* pDevice = pHmdManager->GetHmdDevice()) // Check, if a valid HMD device is connected
  {
    if (pDevice->GetClass() == EHmdClass::eHmdClass_OpenVR) // Check, if the connected device is an OpenVR device (HTC Vive)
    {
      //your code
    }
  }
}
`

```

```

`
IHmdManager pHmdManager = Global.gEnv.pSystem.GetHmdManager ();
if (pHmdManager != null) { // Check, if the HMD Manager exists
  IHmdDevice pDevice = pHmdManager.GetHmdDevice ();
  if (pDevice != null && pDevice.GetClass() == EHmdClass.eHmdClass_OpenVR) { // Check, if a valid OpenVR device (HTC Vive) is connected
    // your code
  }
}
`

```

##
Get HMD Device Tracking State

You can retrieve the position and rotation of the HMD device. While the camera will usually be controlled by the ViewSystem directly, it might be useful to setup additional checks and game-play logic that takes the user's head position into consideration. In the following code samples we will assume pDevice to be set according to 'Check VR Support':

```

`
// Get the current tracking state
HmdTrackingState state = pDevice->GetLocalTrackingState();
// Either use orientation and position directly, or build a TransformationMatrix from them
Matrix34 HMDtm = Matrix34(Vec3(1, 1, 1), state.pose.orientation, state.pose.position);
// You could not apply the values to an entity. For example, to position the entity 'pEntity' relative to the entity 'pReference':
pEntity->SetWorldTM(pReference->GetWorldTM() * HMDtm);
pEntity->InvalidateTM();
`

```

```

`
HmdTrackingState state = pDevice.GetLocalTrackingState();
// Either use orientation and position directly, or build a TransformationMatrix from them
Matrix34 HMDtm = new Matrix34(new Vec3(1, 1, 1), state.pose.orientation, state.pose.position);
// You could not apply the values to an entity. For example, to position the entity 'pEntity' relative to the entity 'pReference':
pEntity.SetWorldTM(pReference.GetWorldTM() * HMDtm);
pEntity.InvalidateTM();
`

```

##
Get Controller Tracking State

You can get the controller's tracking states similar to the HMD's tracking state.

```

`
// The IHmdController is handling all VR controllers associated with the current VR device.
const IHmdController* pController = pDevice->GetController();
// Make sure the desired controller is connected (the OpenVR implementation in CRYENGINE currently supports controller ID 1 and 2)
if (pController->IsConnected(eHmdController_OpenVR_1))
{
  // Get the current tracking state
  HmdTrackingState state = pController->GetLocalTrackingState(eHmdController_OpenVR_1);
  // either use orientation and position directly, or build a TransformationMatrix from them
  Matrix34 controllerTM = Matrix34(Vec3(1, 1, 1), state.pose.orientation, state.pose.position);
  // You could not apply the values to an entity. For example, to position the entity 'pEntity' relative to the entity 'pReference':
  pEntity->SetWorldTM(pReference->GetWorldTM() * controllerTM);
  pEntity->InvalidateTM();
}
`

```

```

`
// The IHmdController is handling all VR controllers associated with the current VR device.
IHmdController pController = pDevice.GetController();
// Make sure the desired controller is connected (the OpenVR implementation in CRYENGINE currently supports controller ID 1 and 2)
if (pController.IsConnected(EHmdController.eHmdController_OpenVR_1))
{
  // Get the current tracking state
  HmdTrackingState state = pController.GetLocalTrackingState(EHmdController.eHmdController_OpenVR_1);
  // either use orientation and position directly, or build a TransformationMatrix from them
  Matrix34 controllerTM = new Matrix34(new Vec3(1, 1, 1), state.pose.orientation, state.pose.position);
  // You could not apply the values to an entity. For example, to position the entity 'pEntity' relative to the entity 'pReference':
  pEntity.SetWorldTM(pReference.GetWorldTM() * controllerTM);
  pEntity.InvalidateTM();
}
`

```

##
React to Controller Input

The controller of the HTC Vive provides more than just tracking information. It has some buttons, a trigger and a touchpad, and you have several options should you want to react to inputs other than just tracking information:

-
**
Action Maps:
**
 Please read
**
[Setting Up Controls and Action Maps](../../CRYENGINE%20Game%20Code/Miscellaneous%20Game%20Code/Setting%20Up%20Controls%20and%20Action%20Maps.md)
.
**
 The relevant button names are:
Name
 |
Type
 |
Description
 |

**
openvr_system
**
 |
Button
 |
**
RESERVED!
**
 This button opens the SteamVR Dashboard.
 |

**
openvr_appmenu
**
 |
Button
 |
Application menu button
 |

**
openvr_grip
**
 |
Button
 |
Grip button
 |

**
openvr_touch_x
**
 |
Axis
 |
Horizontal axis of the touchpad
 |

**
openvr_touch_y
**
 |
Axis
 |
Vertical axis of the touchpad
 |

**
openvr_trigger
**
 |
Trigger
 |
Analog trigger value
 |

**
openvr_trigger_btn
**
 |
Button
 |
Binary trigger value (true, if more than half pressed)
 |

**
openvr_touch_btn
**
 |
Button
 |
Pressed if the user is not just touching, but pressing the touchpad
 |

-
**
InputListener:
**
 Please read
**
[CryInput](../../CRYENGINE%20Engine%20Code/Engine%20Modules/CryInput.md)
.
**
 Check for DeviceType
**
eIDT_MotionController
**
and KeyIds:

-
eKI_Motion_OpenVR_System

-

eKI_Motion_OpenVR_ApplicationMenu

-
eKI_Motion_OpenVR_Grip

-
eKI_Motion_OpenVR_TouchPad_X

-
eKI_Motion_OpenVR_TouchPad_Y

-
eKI_Motion_OpenVR_Trigger

-
eKI_Motion_OpenVR_TriggerBtn

-
eKI_Motion_OpenVR_TouchPadBtn

-
**
Polling:
**
 Additionally, you can poll the current controller state. A nice bonus of this approach, is that you will not only get the information if a button is pressed, but also (in most cases) if the button is just touched:

```

`
// The IHmdController is handling all VR controllers associated with the current VR device.
const IHmdController* pController = pDevice->GetController();
// Make sure the desired controller is connected (the OpenVR implementation in CRYENGINE currently supports controller ID 1 and 2)
if (pController->IsConnected(eHmdController_OpenVR_1))
{
  // Is the Application Menu button pressed?
  bool bAppMenuPressed = pController->IsButtonPressed(eHmdController_OpenVR_1, eKI_Motion_OpenVR_ApplicationMenu);
  // or is it touched?
  bool bAppMenuTouched = pController->IsButtonTouched(eHmdController_OpenVR_1, eKI_Motion_OpenVR_ApplicationMenu);
  // Is the Grip pressed?
  bool bGripPressed = pController->IsButtonPressed(eHmdController_OpenVR_1, eKI_Motion_OpenVR_Grip);
  // or is it touched?
  bool bGripTouched = pController->IsButtonTouched(eHmdController_OpenVR_1, eKI_Motion_OpenVR_Grip);
  // Get Trigger value
  float fTrigger = pController->GetTriggerValue(eHmdController_OpenVR_1, eKI_Motion_OpenVR_Trigger); // the provided KeyID is irrelevant!
  // Get the Touch Pad coordinates
  Vec2 vTouchPad = pController->GetThumbStickValue(eHmdController_OpenVR_1, eKI_Motion_OpenVR_TouchPad_X); // the provided KeyID is irrelevant!
}
`

```

```

`
// The IHmdController is handling all VR controllers associated with the current VR device.
IHmdController pController = pDevice.GetController();
// Make sure the desired controller is connected (the OpenVR implementation in CRYENGINE currently supports controller ID 1 and 2)
if (pController.IsConnected(EHmdController.eHmdController_OpenVR_1))
{
  // Is the Application Menu button pressed?
  bool bAppMenuPressed = pController.IsButtonPressed(EHmdController.eHmdController_OpenVR_1, EKeyId.eKI_Motion_OpenVR_ApplicationMenu);
  // or is it touched?
  bool bAppMenuTouched = pController.IsButtonTouched(EHmdController.eHmdController_OpenVR_1, EKeyId.eKI_Motion_OpenVR_ApplicationMenu);
  // Is the Grip pressed?
  bool bGripPressed = pController.IsButtonPressed(EHmdController.eHmdController_OpenVR_1, EKeyId.eKI_Motion_OpenVR_Grip);
  // or is it touched?
  bool bGripTouched = pController.IsButtonTouched(EHmdController.eHmdController_OpenVR_1, EKeyId.eKI_Motion_OpenVR_Grip);
  // Get Trigger value
  float fTrigger = pController.GetTriggerValue(EHmdController.eHmdController_OpenVR_1, EKeyId.eKI_Motion_OpenVR_Trigger); // the provided KeyID is irrelevant!
  // Get the Touch Pad coordinates
  Vec2 vTouchPad = pController.GetThumbStickValue(EHmdController.eHmdController_OpenVR_1, EKeyId.eKI_Motion_OpenVR_TouchPad_X); // the provided KeyID is irrelevant!

`

```
