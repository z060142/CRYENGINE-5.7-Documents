# Getting Started with Engine Code

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/23306505
- Page ID: 23306505
- Breadcrumb: CRYENGINE Engine Code > Getting Started with Engine Code
- Parent: CRYENGINE Engine Code

## Content

##
Overview

*
Before 3.6.2:
*
 To compile the code provided, you need to have Microsoft Visual C++ 2010 installed.

*
Starting with 3.6.2:
*
 To compile the code provided, you need to have Microsoft Visual C++ 2012 installed.

*
Starting with 3.8.4
*
: Refer to
**
[/docs/static/engines/cryengine-5/categories/23756813/pages/23306511](
Visual Studio Supported Versions_dup
)
**
.

In addition, depending on the targets you want to support as well as the kinds of customizations required, you might need to install the SDKs listed below.

Chapters:

Children:

Related Pages:

[#3rd-party-sdk-dependencies](
3rd party SDK dependencies
)
[#solution-files](
Solution Files
)
[#compilation-configurations](
Compilation Configurations
)

##
3rd party SDK dependencies

In this section, all SDKs that are not included in the code package are listed, with some comments.

From this, you can create the list of SDKs required for a project, given what parts you want to use pre-compiled binaries for, and which parts you want to rebuild.

The code shipped in the CRYENGINE packages makes certain assumptions about the location of 3rd party SDKs relative to the Code folder.

It's easiest to put the SDKs you require in the same location, so you don't have to reconfigure the project include and library paths.

##
Engine

The engine consumes SDKs from the
`
Code\SDKs
`
 folder.

The following SDKs are required for the PC platform:

Dependency

 |
Version

 |
Path

 |
Notes

 |

**
Cinemizer
**

 |
*
Before 3.8.1:
*
 3.0.0

*
*
*
*
Starting with
*
*
*
3.8.1:
*
 No longer used

 |
`
Code\SDKs\Cinemizer
`

 |
*
Before 3.8.1:
*
 Optional, controlled by
**
EXCLUDE_CINEMIZER_SDK
**

By default, this SDK is not used.

*
*
*
*
Starting with
*
*
*
3.8.1:
*
 No longer used.

 |

**
DirectX SDK
**

 |
*
Before 3.7.0
*
: June 2010

*
*
*
*
Starting with
*
*
*
 3.7.0:
*
 No longer used

 |
`
Code\SDKs\DXSDK
`

 |
*
Before 3.7.0
*
: Required.

*
*
*
*
Starting with
*
*
*
3.7.0
*
: No longer used

**
[http://www.microsoft.com/en-us/download/details.aspx?id=6812](
Download Link
)

**

 |

**
Intel GPA
**

 |
*
Before 3.6.1
*
: 2012 R15

*
*
*
*
Starting with
*
*
*
3.6.1
*
: 2014 R2

 |
`
Code\SDKs\GPA
`

 |
Optional, controlled by
**
CRY_PROFILE_MARKERS_USE_GPA
**

By default, this SDK is used.

**
[http://registrationcenter-download.intel.com/akdlm/irc_nas/4211/gpa_14.2_release_225646_windows.exe](
Download Link
)

**

 |

**
Oculus
**

 |
*
Before 3.8.1
*
: 0.1.5

*
*
*
*
Starting with
*
*
*
3.8.1
*
: 0.6.0

*
*
*
*
Starting with
*
*
*
 5.0.0:
*
 0.8.0

*
*
*
*
Starting with
*
*
*
5.1.0:
*
 1.3.0 (included by default)

 |
`
Code\SDKs\OculusSDK
`

 |
Optional, controlled by
**
EXCLUDE_OCULUS_SDK
**

By default, this SDK is used (starting with 3.8.1)

 |

**
OpenVR
**

 |
*
*
*
*
Starting with
*
*
*
5.0.0:
*
 0.9.17
(included by default)

*
*
*
*
*
Starting with
*
*
*

*
5.2.0:
*
 1.0.1 (included by default)

 |
`
Code\SDKs\OpenVR
`

 |
Optional, presence automatically detected by WAF.

 |

**
OSVR
**

 |
*
*
*
*
Starting with
*
*
*
5.0.0
*
: 0.6

*
*
*
*
Starting with
*
*
*
 5.1.0:
*
 Included by default

 |
`
Code\SDKs\OSVR
`

 |
Optional, presence automatically detected by WAF.

 |

**
SteamWorks
**

 |
*
Before 5.0.0:
*
 1.28

*
*
*
*
*
*
Starting with
*
*
*

*
*
5.0.0:
*
 1.33b

 |
`
Code\SDKs\Steamworks
`

 |
Optional, controlled by
**
USE_STEAM

**
By default, this SDK is not used.

 |

**
WWISE
**

 |
*
Before 3.6.8:
*
2013.2.7

*
Before 3.7.0:
*
2014.1.1
*

Before 3.7.0:
*
 2014.1.2

*
*
*
*
Starting with
*
*
*
 3.8.1:
*
 2014.1.4

*
*
*
Starting with
*
*
3.8.2:
*
 2015.1

*
*
Starting with
*
5.2.0:
*
 2016.1

 |
Before 5.2.0:
`
 Code\SDKs\Audio\AK

`
Starting with 5.2.0:
`
 Code\SDKs\Audio\wwise
`

Oculus support, starting with 5.0.0:

`
Code\SDKs\audio\oculus\wwise
`

 |
*
In 3.6.X, for FMOD packages:
*
Not used
*

In 3.6.X, for WWISE packages
*
: Required for the default implementation

*
*
*
*
Starting with
*
*
*
 3.7.0
*
: Required for the default implementation.

*
*
*
*
Starting with
*
*
*
 5.0.0:
*
 On Windows, requires a matching WWISE SDK for Oculus.

 |

**
FMOD Studio
**

 |
*
*
Starting with
*
5.0.0:
*
 1.08.00

*
*
Starting with
*
5.1.0:
*
 1.08.02

*
*
Starting with
*
 5.2.0:
*
 1.08.07

 |
`
Code\SDKs\Audio\fmod
`

 |
Optional, presence automatically detected by WAF.

 |

**
AMD GPU Services
**

 |
*
*
Starting with
*
 3.8.1
*
: 2.1

 |
`
Code\SDKs\AMD\AGS Lib

`
Extra, s
tarting with
 5.0.0:
`

Code\SDKs\AMD\AMD_Extensions
`

 |
**
[http://developer.amd.com/tools-and-sdks/graphics-development/amd-gpu-services-ags-library/](
Download Link
)

**

*
Starting with 5.0.0:
*
 The AMD_Extensions folder can be obtained within an AMD Code sample:
**
[http://developer.amd.com/wordpress/media/2013/05/DepthBoundsTest11_v1.0.zip](
Download Link
)
**

 |

**
NVAPI
**

 |
*
*
Starting with
*
3.8.1
*
: r343

 |
`
Code\SDKs\NVAPI
`

 |
**
[https://developer.nvidia.com/nvapi](
Download Link
)
**

 |

The following SDKs are required for building binaries for a specific platforms:

Dependency

 |
Version

 |
Path

 |
Notes

 |

**
X360 XDK
**

 |

 |
`
Code\SDKs\XenonSDK
`

 |
Only required when targeting XBox 360.

*
*
*
*
Starting with
*
*
*
 3.8.1:
*
 Not supported.

 |

**
PS3 Cell SDK
**

 |
420.001

 |
`
Code\SDKs\PS3\cell
`

 |
Only required when targeting PS3.

*
*
*
*
Starting with
*
*
*
 3.8.1:
*
 Not supported.

 |

**
XOne XDK
**

 |
*
Please check
**
[/docs/static/engines/cryengine-5/categories/23756813/pages/23306689](
Xbox One Supported Versions
)
**
*
**

**

 |
`
Code\SDKs\DurangoSDK
`

 |
Only required when targeting XBox One.

 |

**
PS4 SDK
**

 |
*
Please check
**
[/docs/static/engines/cryengine-5/categories/23756813/pages/23306679](
PS4 SDK versions
)
**
*

 |
`
Code\SDKs\Orbis
`

 |
Only required when targeting PS4.

 |

**
PS4 Pad Support
**

 |
*
Please check
**
[/docs/static/engines/cryengine-5/categories/23756813/pages/23306679](
PS4 SDK versions
)
**
*

 |
`
Code\SDKs\OrbisPad
`

 |
*
Starting with 3.6.4:
*
Only required when targeting Win64

while having your SDK configured with PS4 support

 |

**
Android SDK/NDK
**

 |
Android SDK API-19

Android NDK R10c

JDK 7.0.45

Apache Ant 1.8.2

 |
`
Code\SDKs\android-sdk
`

`
Code\SDKs\android-ndk
`

`
Code\SDKs\jdk
`

`
Code\SDKs\apache-ant
`

 |
*
Starting with 3.7.0
*
:

Only required when targeting Android

 |

When developing for one of the above platforms, please update the firmware as well as development environment to match the SDK version.

##
Sandbox

The Sandbox consumes
SDKs from the
`
Code\SDKs
`
 folder. Before 3.8.0, the
`
Code\Sandbox\SDKs
`
 folder is also used.

Rebuilding of the Sandbox is not required as long as the interfaces declared in CryCommon are not changed. In that case, you can use the pre-built binaries from the CRYENGINE SDK package.

If this doesn't happen during development, you wont need to rebuild the Sandbox, and the SDKs listed here needn't be obtained.

Dependency

 |
Version

 |
Path

 |
Notes

 |

**
FbxSdk
**

 |
*
Before 3.6.2
*
: 2013.3

*
Starting with 3.6.2
*
: 2014.2

*
Starting with 3.8.4
*
: 2016.1

 |
*
Before 3.6.2
`
:
`
*
`
Code\SDKs\FbxSdk\2013.3

`
*
Starting with 3.6.2:
*
`
 Code\SDKs\FbxSdk
`

 |
Required.

Also used by Resource Compiler.

**
[http://usa.autodesk.com/adsk/servlet/pc/item?siteID=123112&id=10775892](
Download Link
)

**

 |

**
Xtreme ToolkitPro
**

 |
13.4.0

 |
`
Code\SDKs\XT_13_4
`

 |
Required.
**
[/docs/static/engines/cryengine-5/categories/23756813](
Note on building XT Toolkit
)
**
.

Can be purchased from
[http://www.codejock.com/](
**
CodeJock
**
.
)

 |

##
Sandbox Plugins

The Sandbox plugins consume SDKs from the
`
Code\SDKs
`
 folder. Before 3.8.0, the
`
Code\Sandbox\SDKs
`
 folder is also used.

Rebuilding of the Sandbox plugins is not required unless you wish to customize them. Instead, you can use the pre-built binaries from the CRYENGINE SDK package.

If there is no need for customization, you wont need to rebuild the Sandbox plugins, and the SDKs listed here needn't be obtained.

Dependency

 |
Version

 |
Path

 |
Notes

 |

**
Perforce API
**

 |
*
Starting with 3.6.2
*
: 2014.1

*
Starting with 3.8.5
*
: 2015.1

 |
`
Code\SDKs\p4api
`

 |
Required only for PerforcePlugin.

 |

**
FbxSdk
**

 |
*
Before 3.6.2
*
: 2012.1

*
Starting with 3.6.2
*
: 2014.2

*
Starting with 3.8.4
*
: 2016.1

 |
*
Before 3.6.2:
*
`
 Code\Sandbox\SDKs\FbxSdk

`
*
Starting with 3.6.2:
*
`
 Code\SDKs\FbxSdk
`

 |
Required only for FBXPlugin.

Also used by RC.

**
[http://usa.autodesk.com/adsk/servlet/pc/item?siteID=123112&id=10775892](
Download Link
)

**

 |

##
Resource Compiler

The resource compiler consumes SDKs from the
`
Code\SDKs
`
 folder. Before 3.7.1, the
`
Code\Tools\SDKs
`
 folder is also used.

The resource compiler is built from the
`
Code\Solutions\Pipeline.sln
`
 solution file

Rebuilding of the Resource Compiler is not required unless you wish to customize it. Instead, you can use the pre-built binaries from the CRYENGINE SDK package.

If there is no need for customization, you wont need to rebuild the Resource Compiler, and the SDKs listed here needn't be obtained.

Dependency

 |
Version

 |
Path

 |
Notes

 |

**
FbxSdk
**

 |
*
Before 3.6.2:
*
 2013.3

*
Starting with 3.6.2:
*
 2014.2

*
Starting with 3.8.4
*
: 2016.1

 |
*
Before 3.6.2:
*

`
Code\SDKs\FbxSdk\2013.3

`
*
Starting with 3.6.2:
*

`
Code\SDKs\FbxSdk
`

 |
Required.

Also used by Sandbox.

**
[http://usa.autodesk.com/adsk/servlet/pc/item?siteID=123112&id=10775892](
Download Link
)

**

 |

**
CUDA
**

 |
*
Before 3.6.2:
*
 4.2

*
Starting with 3.6.2:
*
 No longer used

 |
`
Code\Tools\SDKs\NVIDIA\CUDA-4.2
`

 |
*
Before 3.6.2:
*
 Required.

 |

**
PowerVR Tex Lib
**

 |
*
Starting with 3.7.0
*
: 3.3

*
Starting with 3.8.2
*
: 3.5

 |
*
Before 3.6.2:
*
`

Code\SDKs\POWERVR\PVRTexLib_3.3

`
*
Starting with 3.8.2:
*
`

Code\SDKs\POWERVR\PVRTexLib_3.5
`

 |
Optional: Used when
`
TOOLS_SUPPORT_POWERVR
`
 is defined.

 |

**
Alembic
**

 |
*
Starting with 3.8.4
*
: 1.5.8

 |
*
Starting with 3.8.4:
*
`

Code\SDKs\Alembic
`

 |
Required.

**
[https://github.com/alembic/alembic/releases](
Download Link
)
**

 |

**
hdf5
**

 |
*
Starting with 3.8.4
*
: 1.8.15-patch1

 |
*
Starting with 3.8.4:
*
`

Code\SDKs\hdf5
`

 |
Required for Alembic.

**
[https://www.hdfgroup.org/ftp/HDF5/releases/hdf5-1.8.15-patch1/src/](
Download Link
)
**

 |

**
ilmbase
**

 |
*
Starting with 3.8.4
*
: 2.2.0

 |
*
Starting with 3.8.4:
*
`

Code\SDKs\ilmbase
`

 |
Required for Alembic
.

**
[http://www.openexr.com/downloads.html](
Download Link
)

**

 |

**
szip
**

 |
*
Starting with 3.8.4
*
: 2.1

 |
*
Starting with 3.8.4:
*
`

Code\SDKs\szip
`

 |
Required for hdf5
.

**
[https://www.hdfgroup.org/HDF5/release/obtain5.html#extlibs](
Download Link
)

**

 |

##
Asset Exporter Plugins

The asset exporter plugins are used to export assets for CRYENGINE from 3rd party applications such as Autodesk 3ds Max, Autodesk Maya, Autodesk MotionBuilder and Adobe Photoshop.

Rebuilding of the 3rd party plugins is not required unless you wish to customize them. Instead, you can use the pre-built binaries from the CRYENGINE SDK package.

If there is no need for customization, you wont need to rebuild the 3rd party plugins, and the SDKs listed here needn't be obtained.

Dependency

 |
Version

 |
Path

 |
Notes

 |

**
3ds Max SDK
**

 |
SDK 12 to 16 are supported (3ds Max 2010 to 2014)

*
Starting with 3.6.1
*
: SDK 17 is also supported (3ds Max 2015)

*
Starting with 3.8.1
*
: SDK 18 is also supported (3ds Max 2016)

*
Starting with 5.1.1:
*
 SDK 19 is also supported (3ds Max 2017)

 |
`
Code\Tools\SDKs\maxsdk\maxXX
`

(where XX is the 3ds Max version to build for)

 |
Only required for building 3ds Max plugins.

 |

**
Maya SDK
**

 |
2009 to 2014 are supported.

*
Starting with 3.6.1
*
: SDK 2015 is also supported

*
Starting with 3.8.1
*
: SDK 2016 is also supported

 |
`
Code\Tools\SDKs\Maya\MayaXXXX
`

(where XXXX is the Maya version to build for)

 |
Only required for building Maya plugins.

 |

**
MotionBuilder
**

 |
75, 2012, 2014 are supported.

*
Starting with 3.6.1
*
: SDK 2015 is also supported

*
Starting with 3.8.1
*
: SDK 2016 is also supported

 |
`
Code\Tools\SDKs\MotionBuilder\MBXXXX
`

(where XXXX is the MotionBuilder version to build for)

 |
Only required for building MotionBuilder plugins.

 |

**
Photoshop SDK
**

 |
CS4 Windows.

 |
`
Code\Tools\SDKs\Photoshop\adobe_photoshop_cs4_sdk_win
`

 |
Only required for building Photoshop plugins (aka CryTIFF plugin).

 |

##
Using STLport

STLport is an open source implementation of the Standard Template Library (STL) different from the default implementation shipping with Visual Studio.

Usage of STLport is no longer recommended since the improvements in the Visual Studio shipped STLs.

The STLport source code is included in the CRYENGINE SDK. However, Visual Studio needs to be set up to make use of STLport instead of the default STL implementation using the following steps:

-
Go to
**
Tools/Options
**
 in the main menu and select
**
VC++ Directories
**
 under
**
Projects and Solutions
**
.

-
Select
**
Platform Win32
**
 and add the path <CRY_SDK_ROOT>\Code\SDKs\STLPORT\stlport at the top of the
**
Include files
**
 and
**
Library files
**
 list. It is essential that the STLport path is above the default Visual Studio include and lib paths in the list.

-
Repeat the previous step for the x64 and other platforms, as required.

##
Autodesk Scaleform

The header files and static libraries are located in:

-
`
Code\SDKs\Scaleform\Include
`

-
`
Code\SDKs\Scaleform\Lib
`
Each Lib directory contains static libraries for Release, Profile and Debug configurations.

For certain CRYENGINE licensing packages that include Scaleform, Crytek may provide headers and library files directly.

Scaleform Video libraries need to be obtained directly from Autodesk.

To toggle Scaleform Video on/off can be done by changing the following define statement inside the file:

`
Code\CryEngine\CrySystem\Scaleform\ConfigScaleform.h:
`

```

`
#define ENABLE_GFX_VIDEO
`

```

##
Solution Files

The following table describes the various solution files supplied with the CRYENGINE SDK.

Starting with version 3.7.0, the WAF build system is used to generate solutions.

Projects and solutions are no longer shipped, you can now regenerate appropriate project files using WAF.

Some stand-alone tools still use solution and project files. In this case the appropriate project and/or solution files will be in the Tool's code folder.

It is currently not possible to build CRYENGINE with a root path containing a space character (e.g. C:\
**
Program Files
**
\CryENGINE would not work).

Solution file

 |
Description

 |

`
Code\Solutions\CryEngine.sln
`

 |
Engine and Sandbox.

 |

`
Code\Solutions\CryEngineTools.sln
`

 |
Additional Tools.

 |

`
Code\Solutions\Pipeline.sln
`

 |
Pipeline Tools (RC, CryTifPlugin etc).

 |

`
Code\Sandbox\Plugins\Plugins.sln
`

 |
Sandbox Plugins.

 |

##
Compilation Configurations

When compiling the engine from Visual Studio, you can pick between several configurations.

Each has different implications on compile-time and run-time performance.

Configuration

 |
Compilation Type

 |
Runtime Performance

 |
Use for

 |

Debug

 |
Dynamic libraries

 |
Slow

 |
Use the Debug configuration as a programmer if you need to debug code and require that no symbol is optimized away.

This configuration should only be used for debugging specific problems, because the run-time performance is very slow.

 |

Profile

 |
Dynamic libraries

 |
Good

 |
Use the Profile configuration for general development. Compiled code will be optimized ensuring good performance at run-time.

Because dynamic libraries are built, incremental compilation should allow for fast iteration.

 |

Release

 |
Static link

 |
Best

 |
Use the Release configuration for releasing to customers. Compiled code will be optimized for best run-time performance.

Because all code will be statically linked, the compilation time will be significant even for a small code change.

 |

Profile Server Only

 |
Dynamic libraries

 |
Good

 |
*
MSBuild solutions (before 3.8.1):
*
 This is the dedicated server version of Profile.

 |

Release Server Only

 |
Static link

 |
Best

 |
*
MSBuild solutions (before 3.8.1):
*
 The is the dedicated server version of Release.

 |

For the PS3 and PS4, all configurations will use static linking, regardless of the configuration setting.

Sometimes, as a programmer, you are working on a specific section of the engine code. In that case, you may want to mix Debug and Profile settings using the solution configuration.

Use the 'Profile' configuration for the projects you are not working on, and 'Debug' configuration for the one you are working on. This way, you'll have reasonable run-time performance as well as a good debugging experience.

##
Dedicated server

*
Versions 3.7.0 to 3.8.1
*
: WAF does not target dedicated folders, and this section does not apply to those builds.

For these versions, this section only applies to MSBuild-based builds.

Dedicated server binaries are stored in a folder bin/XX_dedicated (Before 3.8.4:
`
BinXX_Dedicated
`
), where XX is the platform on which the server is hosted.

It is possible for clients to connect to a server hosted on a different platform than the client is running on.

Even though some dedicated server binaries have the same name as the client binaries (such as CrySystem.dll), they are not interchangeable. Mixing the use of dedicated and non-dedicated binaries is NOT supported.

There are currently dedicated server configurations for the following platforms:

Platform

 |
Compiled using

 |
Location

 |

**
Windows, x86
**

 |
Visual Studio

 |
*
Before 3.8.4:
*
`
 Bin32_Dedicated

`
*
Starting with 3.8.4:
*
`

bin\win_x86_dedicated
`

 |

**
Windows, x64
**

 |
Visual Studio

 |
*
Before 3.8.4:
*
`
 Bin64_Dedicated
`

*
Starting with 3.8.4:
*
`

bin\win_x64_dedicated
`

 |
