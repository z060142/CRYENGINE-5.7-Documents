# Oculus Rift

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/25534187
- Page ID: 25534187
- Breadcrumb: Virtual Reality > Oculus Rift
- Parent: Virtual Reality

## Content

![Image](https://www.cryengine.com/docs/static/attachments/29933316)
[![Image](https://www.cryengine.com/docs/static/attachments/44968359)](https://www.cryengine.com/support)

##
Overview

Oculus Rift support is now included with CRYENGINE. This article will guide you through setting up VR and also includes important information that you should know before getting started.

##
Chapters:

[Chapters:](#chapters)
[Getting Started](#getting-started)
[Input Configuration](#input-configuration)
[Flow Graph](#flow-graph)
[Oculus Rift-Specific Console Commands and Variables](#oculus-rift-specific-console-commands-and-variables)
[Possible Issues You Can Encounter](#possible-issues-you-can-encounter)

##
Getting Started

-
**
Drivers:

**
Install the most up to date drivers -

**
[Available from Oculus](https://developer.oculus.com/downloads/)
**
. We currently support version

**
1.3 Beta.
**

-
**
Oculus Documentation:
**

Please read the documentation regarding device setup and configuration -

**
[Available from Oculus](https://developer.oculus.com/documentation/)
**
.

-
**
Health and Safety:

**
Please carefully read the H&S information -

**
[Available from Oculus](http://static.oculus.com/sdk-downloads/documents/Oculus_Health_and_Safety_Warnings_0.5.0.pdf)
**
.

-
**
Video Drivers
**
: Update your Video Card Driver(s) and ensure that you are running the most recent revision that supports Oculus Rift.

-
**
Recommended PC Specs:
**

Information regarding hardware requirements -

**
[Available from Oculus](https://www.oculus.com/en-us/blog/the-rifts-recommended-spec-pc-sdk-0-6-released-and-mobile-vr-jam-voting/)
**
.
Help with installation and setup
For help with configuring your device, please use the official Oculus application and documentation in the link above.

##
Starting the Engine with the Oculus Rift Enabled (Game Mode)

To enable VR in CRYENGINE then follow the steps below:

-
Connect the device to your computer

-
Make sure the vendor runtime/application recognizes your headset as ready for use

-
Install the OculusVR plugin by adding the following line to the plugin section of your .cryproject file

*
{ "type": "EPluginType::Native", "path": "CryOculusVR" }
*

-
In the Oculus client enable Unknown Sources

-
Add 'sys_vr_support=1' to your system.cfg or user.cfg file

-
Launch the Engine
Once launched, the Engine should be rendering to your head-mounted device.

![Image](https://www.cryengine.com/docs/static/attachments/44968360)

##
Making Changes to a Level (Edit Mode)

If you want to make changes to a level i.e. edit your game then you will need to disable VR.

-
Remove all VR plugins from your .cryproject for e.g.
*
{ "type": "EPluginType::Native", "path": "CryOculusVR" }
*
.
**
NOTE:
**
This includes VR plugins related to HMD's from all other manufacturers, not just the Oculus Rift
*

*

-
Remove
*
sys_vr_support
*
from your system.cfg or .cryproject

-
Ensure that any other VR specific features are disabled
Reverting back to Game Mode
When reverting back to game mode then all of the above steps/any changes made must be reverted

308 admin error
Launch the Engine as admin if you encounter error 308

##
Input Configuration

If so desired you can bind this directly to a key/gamepad button. This can be achieved via Flow Graph using the Debug:
**
InputKey
**
 node.

Alternatively, you could modify the
`
<game_folder>\Libs\Config\DefaultProfile.xml
`
 file and assign a button there.

See
**
[Setting up Controls & Actionmaps](../../API%20Reference/CRYENGINE%20Game%20Code/Miscellaneous%20Game%20Code/Setting%20Up%20Controls%20and%20Action%20Maps.md)
**
 for more information.

##
Flow Graph

We have exposed some controls/functions that are related to the HMD device and the Motion Controllers. This can be accessed through Flow Graph.

-
**
VR:TransformInfo
**

**
![Image](https://www.cryengine.com/docs/static/attachments/56000784)
**

*
VR:TransformInfo node
*
Allows quick access to position and rotation information related to the VR device.

-
**
VR:Tools
**

**
![Image](https://www.cryengine.com/docs/static/attachments/56000785)

**
*
VR:Tools node
*
Allows you to hookup an input to trigger the RecenterPose command.

-
**
VR:ControllerTracking
**

**
![Image](https://www.cryengine.com/docs/static/attachments/56000787)

**
*
VR:ControllerTracking node
*
**

**
Similar to the VR:TransformInfo node. This node will allow you to access position and rotation information of a controller. Additionally, you can provide a scaling value as well as a reference entity.

Oculus Rift use
FlowNodes below are Device/Platform specific. This is subject to change (Layer implementations are WIP on other devices), while others, like Device-specific Controller maps are such by design and are only meant for the specific device concerned.

-
**
VR:OculusController
**

**
![Image](https://www.cryengine.com/docs/static/attachments/56000788)

**
*
VR:OculusController node
*
**

**
Allows you to retrieve the button states as well as the trigger, thumbstick and gesture values of the given Touch Controller. (Index should usually be either 0 or 1).

-
**
VR:QuadRenderLayer
**

**
![Image](https://www.cryengine.com/docs/static/attachments/56000789)

**
*
VR:QuadRenderLayer node
*
**

**
Lets you access properties of the Quad Render Layers of the HMD. Node allows modifying position, scaling and orientation of the layer (specified by Layer input) in World Space.

-
**
VR:RenderLayerTexture
**

**
![Image](https://www.cryengine.com/docs/static/attachments/56000791)

**
*
VR:RenderLayerTexture node
*
**

**
Lets you access properties of the Render Layer textures of the Layer specified with QuadLayerID.

##
Oculus Rift-Specific Console Commands and Variables

Name
 |
Type
 |
Default
 |
Description
 |

**
hmd_ipd
**
 |
Variable
 |
-1
 |
HMD IPD override (in meters, floating point)

    -1 - Use system provided value
 |

**
hmd_low_persistence
**
 |
Variable
 |
0
 |
Deprecated
 |

**
hmd_dynamic_prediction
**
 |
Variable
 |
0
 |
Deprecated
 |

**
hmd_queue_ahead
**
 |
Variable
 |
0
 |
Deprecated
 |

**
hmd_projection
**
 |
Variable
 |
0
 |
Selects the way the image is projected into the HMD:
0 - normal stereoscopic mode

1 - monoscopic (cinema-like)

2 - monoscopic (head-locked)

**
*
Used with Oculus SDK 1.2 or above only
*
**
 |

**
hmd_perf_hud
**
 |
Variable
 |
0
 |
Performance HUD Display for HMD's
0 - off

1 - Summary

2 - Latency timing

3 - App Render timing

4 - Compositor Render timing

5 - Version Info

**
*
**
*
Used with
*
**
Oculus SDK 1.2 or above only
*
**
 |

**
hmd_projection_screen_dist
**
 |
Variable
 |
0
 |
If >0 it forces the 'cinema screen' distance to the HMD when using 'monoscopic (cinema-like)' projection

*
**
**
*
Used with
*
**
Oculus SDK 1.2 or above only
**
*
 |

##
Possible Issues You Can Encounter

##
The Sandbox Editor fails to run after enabling VR

Solution:

-
Remove any VR plugins from your .cryproject for e.g.

*
{ "type": "EPluginType::Native", "path": "CryOculusVR" }
*
.

-
Remove

*
sys_vr_support
*
from your system.cfg or .cryproject

-
Ensure that any other VR specific features are disabled
When reverting back to game mode then all of the above steps/any changes made must be reverted.

##
Running the Sandbox Editor with the user.cfg

This will try to enable VR in Editor Mode which it will attempt but can't do.

**
Solution:
**

Rename the user.cfg to something else such as _user.cfg

This will bypass the file being read on loading of the Sandbox Editor.

Make sure to change the name back to user.cfg when you want to use VR again in the Launcher.

##
In some instances the Launcher (GameSDK.exe) boots to a black screen

The game is active in the background but nothing is visually represented on screen.

Solution: Delete the the user folder in the root of the build. Then relaunch the GameSDK.exe.

##
In some instances the Launcher (GameSDK.exe) boots to an orange screen

In some extreme instances the screen can boot to an orange screen detailing "Application is paused while an old SDK application is rendering".

**
Solution:
**
 Try stopping then restarting the Oculus service through the

**
Oculus Configuration Utility (found
**
under the

**
Tools
**

menu).
