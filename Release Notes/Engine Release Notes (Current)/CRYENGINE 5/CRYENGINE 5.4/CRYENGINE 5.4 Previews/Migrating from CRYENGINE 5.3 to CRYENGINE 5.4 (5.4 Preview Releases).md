# Migrating from CRYENGINE 5.3 to CRYENGINE 5.4 (5.4 Preview Releases)

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/47316993/pages/44962700
- Page ID: 44962700
- Breadcrumb: Engine Release Notes (Current) > CRYENGINE 5 > CRYENGINE 5.4 > CRYENGINE 5.4 Previews > Migrating from CRYENGINE 5.3 to CRYENGINE 5.4 (5.4 Preview Releases)
- Parent: CRYENGINE 5.4 Previews

## Content

## Overview

This article is aimed at easing the migration of projects from CRYENGINE 5.3 to CRYENGINE 5.4 and it focus's on the changes made to CRYENGINE's source code format.

### Deprecated Features

Over time, and as we introduce new features we will deprecate the older ones and plan to remove them in future Engine releases.

For 5.4.0, the following features have been deprecated:

- Game Objects (Only exposed to C++)
- Lua - Replaced with C#
- Actor System - Replaced with Entity Components
- Game Rules System - Replaced with Entity Components and Networked Client Listeners
- Standard Entities - Recently introduced with CRYENGINE 5.3.0, but now deprecated in favor of the new Standard Components

Additionally, the following features were already deprecated and have been removed from Engine source code and thus will no longer function:

- Clouds - Superseded by Volumetric Clouds
- Volume Objects - Superseded by Volumetric Clouds

Finally, the OpenGL Renderer is no longer supported. Source code is still shipped with the Engine, however Vulkan is considered an effective replacement.

### New Project CMakeLists setup

The project system has been refactored to automatically generate the CMake setup (CMakeLists.txt) whenever the 'Generate Solution' option is used.

This is done by automatically detecting **.cpp** and **.h** files inside the Code directory, and adding them to the solution. This means that any customizations you have made in CMakeLists.txt will be removed upon generating solution, because of this we ** strongly recommend** backing up this file before upgrading.

It is still possible to customize the CMakeLists file using the BEGIN-CUSTOM and END-CUSTOM helpers:

```
#BEGIN-CUSTOM
# Custom changes in here
#END-CUSTOM
```

Anything contained between the custom helpers will be automatically migrated to the newly generated CMakeLists.txt file.

It is additionally also possible to use pure CMake workflow by not using the 'Generate Solution' option beyond the first generation, and then running CMake GUI directly.

It is not recommended to migrate existing projects to the preview build, as it is not a full release build and many aspects of it still contain (sometimes serious) bugs.

### How to Migrate a Project from CRYENGINE 5.3 to CRYENGINE 5.4 (Preview)

- Open the CRYENGINE 5.4 installation directory and navigate to *Tools/CryVersionSelector*.
- Press **S****hift** and **Right-click** in the installation folder to select **Open PowerShell Window here** or **Open Command Line Window here**.
- Enter the command "*cryselect.exe install"* in the command line window or "*.\cryselect.exe install*" in PowerShell, and then press **Enter**.
- Now, open the 5.3 project's directory and right-click the **.cryproject* file to select **Switch engine version** from the menu.
- In the pop-up window, press the Browse (…) button, and navigate to the CRYENGINE 5.4 installation directory and then press **OK**(If the engine is already registered, the engine can be selected from the dropdown menu instead, and this step can be skipped).
- In the pop-up window, press **OK** to initiate the switching process.
- If the version of the project changes, a pop-up will notify the user to make a backup of the project first.
- If the switch was successful, the user will be notified to generate the solution and rebuild the project.
- Now, right click on the **.cryproject* file, and click **Generate solution** from the menu.
- If it is a **C++** project, CMake will build the solution in * Solutions/Game.win_x64* directory. If it's a **C#** project, the solution will be generated in the code folder. The solution will be named ***Game.sln***.
- When an error occurs in CMake while generating the solution, make sure that Visual Studio is installed with support for C++ projects.
- The user can now open the solution. For C++ projects,  the solution can be opened in Visual Studio. For C# projects, it can be opened with Xamarin Studio if it has the CRYENGINE add-in installed.
For more information, see [http://docs.cryengine.com/display/CEPROG/C%23+Programming](../../../../../API%20Reference/CRYENGINE%20Code%20Tutorials/C%23%20Programming.md).
- Now, build the solution by pressing **Build/Build solution** in Visual Studio, or **Build/Build all** in Xamarin Studio.
- During Build process if any errors are encountered then they need to be fixed manually by the user.
- If the solution has built successfully, the user can now run CRYENGINE and game launcher.

### Necessary code changes to build against CRYENGINE 5.4

If you are using any of the macros listed below, then you will have to update your code to reflect the changes that we have made in the Engine code.

Old Macro (up to 5.4 Preview) | New Macro (5.4 onwards)
--- | ---
`CRY_ENTITY_COMPONENT_CLASS` | `CRY_ENTITY_COMPONENT_CLASS_GUID`
`CRY_ENTITY_COMPONENT_INTERFACE` | `CRY_ENTITY_COMPONENT_INTERFACE_GUID`
`CRYGENERATE_CLASS` | `CRYGENERATE_CLASS_GUID`
`CRYGENERATE_CLASS_FROM_INTERFACE` | `CRYGENERATE_CLASS_FROM_INTERFACE_GUID`
`CRYGENERATE_SINGLETONCLASS` | `CRYGENERATE_SINGLETONCLASS_GUID`
`CRYINTERFACE_DECLARE` | `CRYINTERFACE_DECLARE_GUID`
`_ENFORCE_CRYFACTORY_USAGE` | `_ENFORCE_CRYFACTORY_USAGE_GUID`

You will need to replace all occurrences of the old macros with their new form - this also requires you to update the parameters. The old macros took two unsigned 64-bit integers, whereas the new ones expect a `CryGUID`. Converting your integers into the corresponding ` CryGUID` is fairly straightforward providing you know the hexadecimal representation and can be done as follows:

Assuming that your integer values were `0x0111111123334555` and ` 0xabbbcddddddddddd`, the new ` CryGUID` looks like this: `"01111111-2333-4555-abbb-cddddddddddd"_cry_guid`.
