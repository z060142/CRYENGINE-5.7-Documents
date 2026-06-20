# OSVR

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/25534189
- Page ID: 25534189
- Breadcrumb: Virtual Reality > OSVR
- Parent: Virtual Reality

## Content

![Image](https://www.cryengine.com/docs/static/attachments/29933317)
[![Image](https://www.cryengine.com/docs/static/attachments/26955867)](https://docs.cryengine.com/pages/resumedraft.action?draftId=44108071&draftShareId=040eee24-d8d3-4296-90e0-42298fc4240a&)

## Overview

For those developers using the **[OSVR open source platform](http://osvr.github.io/whitepapers/introduction_to_osvr/)** then CRYENGINE can be setup so that the OSVR SDK is used and an HMD connects to CRYENGINE.

## Chapters:

[Chapters:](#chapters)[OSVR and CRYENGINE](#osvr-and-cryengine)[Starting the Engine with the Headset Enabled (Game Mode)](#starting-the-engine-with-the-headset-enabled-game-mode)

### OSVR and CRYENGINE

OSVR requires an OSVR Server to be running in order for CRYENGINE to connect to the HMD. The easiest way to acquire the server and to test it is to download and install the OSVR Render Manager from **[here.](http://osvr.github.io/using/)**

After installation, Render Manager creates a series of shortcuts to the start menu. To start the server, click on the corresponding server shortcut:

- osvr_server OSVR HDK1.3 directmode if you have HDK 1.3
- osvr_server OSVR HDK1.2 directmode if you have HDK 1.2

Pay attention to what the server prints. It should report that it has found your HMD device. If not, check that you have plugged in the HMD correctly.

Next, verify that the directmode works. Run one of the examples that comes with the Render Manager, for example RenderManagerD3DExample3D. If the example fails to start and closes without showing anything on the screen, then this means that the directmode didn’t work correctly. Refer to the readme.txt provided with the Render Manager to check what driver version etc. is required.

Once the Server is running and you have verified that the directmode works you are all set to use the OSVR with CRYENGINE.

**NOTE:** The OSVR server can also be run without the directmode. Just select the non-directmode config and start the server. This will create a separate window to show the HMD output, but you can still use the HMD to change head orientation etc.

### Starting the Engine with the Headset Enabled (Game Mode)

To enable VR in CRYENGINE then follow the steps below:

- Connect the device to your computer
- Make sure the vendor runtime/application recognizes your headset as ready for use
- Install the OpenVR plugin by adding the following line to the plugin section of your .cryproject file
*{ "type": "EPluginType::Native", "path": "CryOpenVR" }*
- Add 'sys_vr_support=1' to your system.cfg or user.cfg file
- Launch the Engine

Once launched, the Engine should be rendering to your head-mounted device.

#### Making Changes to a Level (Edit Mode)

If you want to make changes to a level i.e. edit your game then you will need to disable VR.

- Remove all VR plugins from your.cryproject for e.g. *{ "type": "EPluginType::Native", "path": "CryOpenVR" }.***NOTE:** This includes VR plugins related to all HMD's and from all manufacturers
- Remove *sys_vr_support* from your system.cfg or.cryproject
- Ensure that any other VR specific features are disabled

Reverting back to Game Mode
When reverting back to game mode then all of the above steps/any changes made must be reverted

308 admin error
Launch the Engine as admin if you encounter error 308
