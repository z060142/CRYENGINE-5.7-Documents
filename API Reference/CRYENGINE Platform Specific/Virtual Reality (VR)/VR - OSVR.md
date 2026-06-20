# VR - OSVR

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/23309878
- Page ID: 23309878
- Breadcrumb: CRYENGINE Platform Specific > Virtual Reality (VR) > VR - OSVR
- Parent: Virtual Reality (VR)

## Content

##
Overview

For those developers using the
**
[http://osvr.github.io/whitepapers/introduction_to_osvr/](
OSVR open source platform
)
**
 then CRYENGINE can be setup so that the OSVR SDK is used and an HMD connects to CRYENGINE.

Chapters:

[#osvr-and-cryengine](
OSVR and CRYENGINE
)
[#osvr-setup-for-cryengine](
OSVR Setup for CRYENGINE
)

##
OSVR and CRYENGINE

OSVR requires an OSVR Server to be running in order for CRYENGINE to connect to the HMD. The easiest way to acquire the server and to test it is to download and install the OSVR Render Manager from

**
[http://osvr.github.io/using/](
here.
)
**

After installation, Render Manager creates a series of shortcuts to the start menu. To start the server, click on the corresponding server shortcut:

-
osvr_server OSVR HDK1.3 directmode if you have HDK 1.3

-
osvr_server OSVR HDK1.2 directmode if you have HDK 1.2
Pay attention to what the server prints. It should report that it has found your HMD device. If not, check that you have plugged in the HMD correctly.

Next, verify that the directmode works. Run one of the examples that comes with the Render Manager, for example RenderManagerD3DExample3D. If the example fails to start and closes without showing anything on the screen, then this means that the directmode didn’t work correctly. Refer to the readme.txt provided with the Render Manager to check what driver version etc. is required.

Once the Server is running and you have verified that the directmode works you are all set to use the OSVR with CRYENGINE.

**
NOTE:
**

The OSVR server can also be run without the directmode. Just select the non-directmode config and start the server. This will create a separate window to show the HMD output, but you can still use the HMD to change head orientation etc.

##
OSVR Setup for CRYENGINE

If you have enabled VR support CVar
**
sys_vr_support=1
**
 and use the default value for CVar
**
hmd_driver=0
**
 CRYENGINE will try to automatically detect and activate one of the supported VR SDK's.

However, if you want to force CRYENGINE to use the OSVR SDK, then set the CVar
**
hmd_driver=3
**
