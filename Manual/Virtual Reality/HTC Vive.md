# HTC Vive

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/25534185
- Page ID: 25534185
- Breadcrumb: Virtual Reality > HTC Vive
- Parent: Virtual Reality

## Content

[Image: /docs/static/attachments/29933306]
[https://www.cryengine.com/support](
[Image: /docs/static/attachments/44968372]
)

##
Overview

HTC Vive support is now included with CRYENGINE. This article will guide you through setting up VR and also includes important information that you should know before getting started.

##
Chapters:

[#chapters](
Chapters:
)
[#getting-started](
Getting Started
)
[#input-configuration](
Input Configuration
)
[#flow-graph](
Flow Graph
)
[#frames-per-second](
Frames per Second
)
[#possible-issues-you-can-encounter](
Possible Issues You Can Encounter
)

##
Getting Started

-
**
Runtime:
**
I
n order to use the HTC Vive you need to install

**
[http://store.steampowered.com/about/](
Steam
)
.
**

-
**
HTC Vive Documentation:
**

Please read the documentation regarding device setup and configuration -

**
[https://support.steampowered.com/kb_cat.php?id=111](
Available from Steam
)
.
**

-
**
Video Drivers:
**

Update your Video Card Driver(s) and ensure that you are running the most recent revision that supports the HTC Vive.

-
**
Recommended PC Spec:
**

Information regarding hardware requirements -

**
[https://www.vive.com/us/support/vive-pro-hmd/category_howto/what-are-the-system-requirements.html](
Available from HTC
)
.
**
Help with installation and Setup
For help in configuring your device, please use the official HTC Vive application and documentation (available in the link above).

##
Starting the Engine with the Vive Enabled (Game Mode)

To enable VR in CRYENGINE then follow the steps below:

-
Connect the device to your computer

-
Make sure the vendor runtime/application recognizes your headset as ready for use

-
Install the OpenVR plugin by adding the following line to the plugin section of your .cryproject file

*
{ "type": "EPluginType::Native", "path": "CryOpenVR" }
*

*

*

-
Add 'sys_vr_support=1' to your system.cfg or user.cfg file

-
Launch the Engine (as admin)
Once launched, the Engine should be rendering to your head-mounted device.

##
Making Changes to a Level (Edit Mode)

If you want to make changes to a level i.e. edit your game then you will need to disable VR.

-
Remove all VR plugins from your .cryproject for e.g.
*
{ "type": "EPluginType::Native", "path": "CryOpenVR" }.

*
**
NOTE:
**
This includes VR plugins related to HMD's from all other manufacturers, not just the HTC Vive
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
When reverting back to game mode then all of the above steps/any changes made for edit mode must be reverted

Launch the Engine as admin if you encounter error 308.

##
Input Configuration

If so desired you can bind this directly to a key/gamepad button. This can be achieved via

Flow Graph using the Debug:
**
InputKey
**

node.

Alternatively, you could modify the

`
<game_folder>\Libs\Config\DefaultProfile.xml
`

file

and assign a button there.

See

**
[/docs/static/engines/cryengine-5/categories/23756813/pages/23306384](
Setting up Controls & Actionmaps
)
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
[Image: /docs/static/attachments/44968376]
**
**

**
Allows quick access to position and rotation information related to the VR device.

**

**

-
**
VR:Tools
**

**
[Image: /docs/static/attachments/44968384]

**
Allows you to hook up an input to trigger the RecenterPose command.

-
**
VR:ControllerTracking
**

**
[Image: /docs/static/attachments/44968385]

**
Similar to the VR:TransformInfo node. This node will allow you to access position and rotation information of a controller. Additionally, you can provide a scaling value as well as a reference entity.

HTC Vive use
FlowNodes below are Device/Platform specific, exposed for solely for the purposes of device specific interaction, and not interoperability.

-
**
VR:OpenVRController
**

**
[Image: /docs/static/attachments/44968386]

**
Allows you to retrieve the button states as well as the trigger and touchpad values of the given Controller. (Index should usually be either 0 or 1).

##
Frames per Second

The HTC Vive will play your game at exactly 90 FPS if you can make it run at exactly 90 FPS or above.

If at any point your game runs at a fraction less than 90 FPS, it will temporarily default down to 45 FPS until 90 FPS is restored.

Please keep in mind that anything less than 90 FPS is generally not considered to be a pleasant experience in VR.

##
Possible Issues You Can Encounter

##
The Sandbox Editor fails to run after enabling VR

Solution:

-
Remove any VR plugins from your .cryproject for e.g.

*
{ "type": "EPluginType::Native", "path": "CryOpenVR" }
*

-
Remove

*
sys_vr_support
*
from your system.cfg or .cryproject

-
Ensure that any other VR specific features are disabled
**
NOTE:
**

When reverting back to game mode then all of the above steps/any changes made must be reverted

##
Running the Sandbox Editor with the user.cfg

This will try to enable VR in Editor Mode which it will attempt, but can't do.

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
