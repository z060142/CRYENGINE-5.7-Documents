# Enabling Scaleform 4 for Projects and Custom Engine Builds

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/90833060
- Page ID: 90833060
- Breadcrumb: CRYENGINE Game Code > Miscellaneous Game Code > User Interface > Enabling Scaleform 4 for Projects and Custom Engine Builds
- Parent: User Interface

## Content

##
Overview

The integration of Scaleform 4 is optional and separate to Scaleform 3.

The following shows you how to choose between Scaleform 3 and Scaleform 4 in an Engine build obtained via the CRYENGINE Launcher, as well as copy the required binaries to a custom Engine build (i.e. built using source code obtained from
[GitHub](../../../CRYENGINE%20Build%20System/Accessing%20CE%20Source%20Code%20via%20GitHub.md)
) to enable Scaleform on them.

Additionally, this page also explains how to include the new Scaleform Schematyc (Experimental) nodes and Generated Components for either Scaleform 3 or 4 in your project.

##
Adding Scaleform Schematyc to Your Project

To include the Scaleform Schematyc (Experimental) nodes and Generated Components in your project, you will need to add the following plugin definition to your .cryproject file:

```

`
{ "guid": "", "type": "EType::Native", "path": "CryScaleformSchematyc" }
`

```

![Image](https://www.cryengine.com/docs/static/attachments/90833078)
*
Adding Scaleform Schematyc to your project
*

##
Selecting Scaleform 3 or 4

##
Scaleform 3

By default, the Engine will load Scaleform 3 if:

-
It is built into the CrySystem binary, or;

-
it is available via the
*
CryScaleformHelper.dll
*
 residing in the binary folder (i.e.
*
bin/win_x64)
*
 and there is no plugin definition for
CryScaleform
 in your
*
.cryproject
*
 file.

##
Scaleform 4

First make sure that the following DLL files reside in your binary folder (i.e.
*
bin/win_x64):
*

-
*
CryScaleform.dll
*

-
*
CryScaleformDX11.dll
*

-
*
CryScaleformDX12.dll
*

-
*
CryScaleformVulkan.dll
*
Then in your
*
.cryproject
*
 file, add the following plugin definition:

```

`
{ "guid": "", "type": "EType::Native", "path": "CryScaleform" }
`

```

![Image](https://www.cryengine.com/docs/static/attachments/90833080)
*
Loading Scaleform 4
*

##
Using Scaleform with a Custom Engine Build

Copy the following DLLs from the binary directory of the Launcher Engine (i.e., the Engine build obtained via the CE Launcher) to the binary directory of your custom Engine build:

-
*
CryScaleformHelper.dll
*

-
*
CryScaleform.dll
*

-
*
CryScaleformDX11.dll
*

-
*
CryScaleformDX12.dll
*

-
*
CryScaleformVulkan.dll
*
The version of your custom Engine must match with the Launcher Engine for compatibility.

The Engine binary directory is the
*
bin/win_x64
*
folder of your project.

![Image](https://www.cryengine.com/docs/static/attachments/90833081)

*
Dlls to copy to custom Engine binary directory
*

##
Related Information

[Tutorial - Introduction to Scaleform UI](../../../../Manual/Tutorials/Game%20and%20Level%20Design/UI/UI%20Design%20Tutorials/Tutorial%20-%20Introduction%20to%20Scaleform%20UI.md)

[Adding Scaleform Schematyc to Your Project](#adding-scaleform-schematyc-to-your-project)
[Selecting Scaleform 3 or 4](#selecting-scaleform-3-or-4)
[Using Scaleform with a Custom Engine Build](#using-scaleform-with-a-custom-engine-build)
[Related Information](#related-information)
