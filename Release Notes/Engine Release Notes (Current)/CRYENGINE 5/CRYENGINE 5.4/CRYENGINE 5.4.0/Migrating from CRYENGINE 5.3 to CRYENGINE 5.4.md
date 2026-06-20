# Migrating from CRYENGINE 5.3 to CRYENGINE 5.4

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/47316993/pages/44962697
- Page ID: 44962697
- Breadcrumb: Engine Release Notes (Current) > CRYENGINE 5 > CRYENGINE 5.4 > CRYENGINE 5.4.0 > Migrating from CRYENGINE 5.3 to CRYENGINE 5.4
- Parent: CRYENGINE 5.4.0

## Content

##
Overview

This article is aimed at easing the migration of projects from CRYENGINE 5.3 to CRYENGINE 5.4 and it focuses on the changes made to CRYENGINE's source code format.

##
Deprecated Features

Over time, and as we introduce new features, then we will deprecate the older ones and they will be removed in future Engine releases.

For 5.4.0 the following features have been deprecated:

-
Game Objects (Only exposed to C++)

-
Lua - Replaced with C#

-
Actor System - Replaced with Entity Components

-
Game Rules System - Replaced with Entity Components and Networked Client Listeners

-
Standard Entities - Recently introduced with CRYENGINE 5.3.0, but now deprecated in favor of the new Standard Components
Additionally, the following features were already deprecated and have been removed from Engine source code and thus will no longer function:

-
Clouds - Superseded by Volumetric Clouds

-
Volume Objects - Superseded by Volumetric Clouds
Finally, the OpenGL Renderer is no longer supported, however source code is still shipped with the Engine - Vulkan is now considered as an effective replacement.

##
New Project CMakeLists Setup

The project system has been refactored to automatically generate the CMake setup (
CMakeLists.txt
) whenever the 'Generate Solution' option is used.

This is achieved by automatically detecting .cpp and .h files inside the Code directory and adding them to the solution. This means that any customizations you have made in CMakeLists.txt will be removed upon generating the solution, and because of this we strongly recommend backing up this file before upgrading.

It is still possible to customize the CMakeLists file using the BEGIN-CUSTOM and END-CUSTOM helpers:

```

`
#BEGIN-CUSTOM
# Custom changes in here
#END-CUSTOM
`

```

Anything contained between the custom helpers will be automatically migrated to the newly generated CMakeLists.txt file.

Additionally, it is also possible to use pure CMake workflow by not using the 'Generate Solution' option beyond the first generation and then running CMake GUI directly.

##
How to Migrate a Project from CRYENGINE 5.3 to CRYENGINE 5.4

-
Open your 5.3 project, right-click on the CryEngine project (this is the *.cryproject file), then click on Switch engine version.

-
In the pop-up window select CRYENGINE 5.4 (using the drop-down menu) and then click the OK button.

-
In the pop-up window, press OK to initiate the switching process.

-
If the version of the project changes, a pop-up will tell you to make a backup of the project first.

-
If the switch was successful, another pop-up will tell to generate the solution and rebuild the project.

-
Now, right click on the *.cryproject file, and click Generate solution from the menu.

-
If it is a C++ project, CMake will build the solution in Solutions/win_x64 directory. If it's a C# project, the solution will be generated in the code folder. The solution will be named Game.sln.

-
If an error occurs in CMake while generating the solution, then make sure that Visual Studio is installed with support for C++ projects.

-
The solution can now be opened. For C++ projects the solution can be opened in Visual Studio. For C# projects, then it can be opened with Xamarin Studio if it has the CRYENGINE add-in installed. For more information see
[C# Programming](../../../../../API%20Reference/CRYENGINE%20Code%20Tutorials/C%23%20Programming.md)
.

-
Next build the solution by pressing Build/Build solution in Visual Studio, or Build/Build all in Xamarin Studio.

-
The API has changed between CRYENGINE 5.3 and 5.4, so it’s possible that errors will be encountered during the build process - these errors need to be fixed manually. More information about the code changes can be found in the
[Important CRYENGINE 5.4 Data and Code Changes](Important%20CRYENGINE%205.4%20Data%20and%20Code%20Changes.md)
.

-
If the solution has built successfully, the GameLauncher and the Sandbox Editor can be run. In Visual Studio this can be done by setting the GameLauncher, GameServer or the Sandbox Editor as the startup project in the Solution Explorer. In Xamarin Studio there is a drop-down menu (top-left) where the preferred launcher can be selected. Once a launcher is selected it can be run by pressing F5.

##
Necessary Code Changes to Build Against CRYENGINE 5.4

If you are using any of the macros listed below, then you will have to update your code to reflect the changes that we have made in the Engine code.

Old Macro (up to 5.4 Preview)
 |
New Macro (5.4 onwards)
 |

`
CRY_ENTITY_COMPONENT_CLASS
`
 |
`
CRY_ENTITY_COMPONENT_CLASS_GUID
`
 |

`
CRY_ENTITY_COMPONENT_INTERFACE
`
 |
`
CRY_ENTITY_COMPONENT_INTERFACE_GUID
`
 |

`
CRYGENERATE_CLASS
`
 |
`
CRYGENERATE_CLASS_GUID
`
 |

`
CRYGENERATE_CLASS_FROM_INTERFACE
`
 |
`
CRYGENERATE_CLASS_FROM_INTERFACE_GUID
`
 |

`
CRYGENERATE_SINGLETONCLASS
`
 |
`
CRYGENERATE_SINGLETONCLASS_GUID
`
 |

`
CRYINTERFACE_DECLARE
`
 |
`
CRYINTERFACE_DECLARE_GUID
`
 |

`
_ENFORCE_CRYFACTORY_USAGE
`
 |
`
_ENFORCE_CRYFACTORY_USAGE_GUID
`
 |

You will need to replace all occurrences of the old macros with their new form - this also requires you to update the parameters. The old macros took two unsigned 64-bit integers, whereas the new ones expect a
`
CryGUID
`
. Converting your integers into the corresponding
`
CryGUID
`
 is fairly straightforward providing you know the hexadecimal representation, this can be done as follows:

Assuming that your integer values were
`
0x0111111123334555
`

and
`
0xabbbcddddddddddd
`
, the new
`
CryGUID
`
 looks like this:
`
"01111111-2333-4555-abbb-cddddddddddd"_cry_guid
`
.
