# Projects and Plug-ins

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/26874870
- Page ID: 26874870
- Breadcrumb: Projects and Plug-ins

## Child Pages

- [GamePlatform Plugin](Projects%20and%20Plug-ins/GamePlatform%20Plugin.md)

## Content

##
Overview

Projects in CRYENGINE are managed by
[IProjectManager](/docs/static/engines/cryengine-5/categories/28704770/pages/29797401)
, each project being represented by a
.cryproject
 file. The concept of a project exists in order to create a clear separation between an engine installation, and engine assets.

Each project specifies the plug-ins it requires, these are then loaded at startup. The CRYENGINE Launcher automatically installs a shell extension for Windows users, resulting in a few shortcuts being added to the shell menu when a .cryproject file is right-clicked in the Explorer:

![Image](https://www.cryengine.com/docs/static/attachments/32179243)

##
Table of Contents

[API Types](#api-types)
[Project File](#project-file)
[Project Actions](#project-actions)
[Project File Structure](#project-file-structure)
[The Project & Asset Folder](#the-project-and-asset-folder)
[Engine folder contents](#engine-folder-contents)
[Project Source Code](#project-source-code)
[Conclusion](#conclusion)

##
API Types

-
[IProjectManager](/docs/static/engines/cryengine-5/categories/28704770/pages/29797401)

-
[Cry::IEnginePlugin](/docs/static/engines/cryengine-5/categories/28704770/pages/29797056)

##
Project File

The project file defines what assets and binaries to load for a project - in addition to configuring CVars and more. This is read by the engine extremely early at  startup as a change of project can drastically affect how the engine initializes itself.

The project can be specified to the engine using the '-project' switch. For example:

```

`
<engine folder>/bin/win_x64/Sandbox.exe -project MyProject.cryproject
`

```

The path to the project can be either relative to engine root, or an absolute path.

If the '-project' switch is not used, the engine will attempt to load a file called
**
Game.cryproject
**
 in the engine root. This behavior can be changed by modifying the
**
sys_project
**
 CVar's value in system.cfg, for example:

```

`
sys_project=MyProject.cryproject
`

```

##
Project Actions

Right-clicking the .cryproject file will give you a number of options that can perform various actions regarding your project:

![Image](https://www.cryengine.com/docs/static/attachments/32179244)

The available options do the following:

Option
 |
Description
 |

**
Launch editor
**
 |
Launches the Sandbox Editor associated with the project. You can then open a level from your project by going to
**
File -> Open
**
.

 |

**
Launch game
**
 |
Launches Game Mode for this project.

 |

**
Launch dedicated server
**
 |
Launches the dedicated server associated with this project.

 |

**
Package Build
**
 |
Packages the project to a standalone build. All files that are required for the GameLauncher are moved into the build folder, together with the assets which are filtered and packaged into .pak files.

Make sure to compile the code and export the levels of your project to the Engine first. This function will not export the levels to the Engine, and it will not compile the code of your project. It will only package what is already available when you select the option
**
Launch game
**
.

 |

**
Generate/repair metadata
**
 |
Generates the metadata (.cryasset files) for the assets of the project.

 |

**
Generate solution
**
 |
Generates your code solution for C++ and C#. The solution will need to be regenerated if the project is moved to a new hard drive location.

For C++ projects this requires you to install Visual Studio and to create a C++ project in Visual Studio so that the C++ compiler is installed.

For C# projects you need the
[Xamarin Studio with the CRYENGINE plugin](CRYENGINE%20Code%20Tutorials/C%23%20Programming.md)
 in order to be able to open the solution.

 |

**
Open CMake GUI
**
 |
Opens the CMake GUI at the location of the project. This requires a CMakelist.txt file to be in the code folder of the project. This can be used to adjust the CMake settings when generating the solution.

 |

**
Switch engine version
**
 |
Lets you change the Engine version you use for the project.

The Engine versions that appear in the drop-down menu are the versions that you have installed.

If you have downloaded an Engine version from GitHub, you can select it here by choosing
**
 Switch engine version
**
 and clicking the
**
Browse
**
button in the menu that appears:

*
![Image](https://www.cryengine.com/docs/static/attachments/32179245)

*

You can then browse to the location where you've saved that Engine version. This simply needs to point to the
*
root folder
*
 of that CRYENGINE version.

This will only work with Engine versions from 5.2.0 and later.

 |

**
Backup Project
**
 |
Creates a backup of your project.
 |

##
Project File Structure

An example of a .cryproject can be seen below:

```

`
{
  "version": 3,
    "content": {
        "assets": [ "Assets" ],
        "code": [ "Code" ]
    },
    "info": {
        "guid": "b8c1c46b-a63e-d4af-9025-0770e4d43048",
        "name": "My Game"
    },
    "require": {
        "engine": "{7893db92-d8c1-4ae5-b3e2-2ce0a0e77782}",
        "plugins": [
            {
                "path": "CryDefaultEntities",
                "type": "EPluginType::Native"
            }
        ]
    },
    "console_variables": [],
  "console_commands": []
}
`

```

##
JSON Breakdown

##
"version"

Defines the version of the project syntax that the project was exported with. This is used to support automatic migration to newer versions, while maintaining backwards compatibility.

##
"content"

Defines where content for the project resides.

##
"assets"

Name of the Assets directory, not required for plug-ins.

##
"code"

Name of the Code directory, not required.

##
"info"

Defines project properties.

##
"guid"

Globally unique identifier used to identify the project.

##
"name"

Name of the project, used to set the title of the window on Desktop platforms.

##
"require"

Defines dependencies for the project.

##
"engine"

The engine that this project depends on, usually a GUID when using the CryVersionSelector. This can also be set to "." to indicate that the engine is present in the same directory as the project.

Engines are registered in
`
%PROGRAMDATA%\Crytek\CRYENGINE\cryengine.json
`
, and is automatically performed when a .cryengine file is double-clicked.

##
"plugins"

Defines plug-ins that should be loaded when this project starts.
Plug-ins in CRYENGINE are represented by the
[Cry::IEnginePlugin](/docs/static/engines/cryengine-5/categories/28704770/pages/29797056)
 interface, and are typically loaded from disk as a dynamic library (.dll on Windows). The introduction of game code is always done through a plug-in, allowing the addition of components and other logic with relative ease.

The .cryproject file is responsible for defining which plug-ins to load, for reference take a look at a snippet from the example we posted earlier:

```

`
"plugins": [
    {
        "path": "CryDefaultEntities",
        "type": "EPluginType::Native"
    }
]
`

```

First, this defines which engine to load from the engine registry - this is automatically populated when an engine is downloaded through the Launcher, but can also be added to by right-clicking a .cryengine file. The registry is currently located in
*
<ProgramData>\Crytek\CRYENGINE\cryengine.json
*
.

The "plugins" array can then contain an array of objects defining which plug-ins to load. In our case we choose to load the default "CryDefaultEntities" plug-in included with the engine, which includes the default entity components.

The search pattern for plug-ins is:

-
Project directory

-
Engine binary directory
The final option "type" specifies what type of plug-in we are loading - C# or C++. This can be represented by one of two values:

Name
 |
Description
 |

**
EPluginType::Native
**
 |
Informs the system that we are loading a C++ plug-in
 |

**
EPluginType::Managed
**
 |
Indicates that we are loading a C# plug-in
 |

##
"console_variables"

Console variables that should be set at startup. If a console variable is not registered during startup, the value is saved and is set immediately when (and if) a console variable with that name is registered.  For example:

```

`
"console_variables": [
  {
        "name": "sys_target_platforms",
        "value": "pc,ps4,xboxone,linux"
    }
],
`

```

This would result in the sys_target_platforms CVar being set as early as possible during engine startup time.

##
"console_commands"

Console commands that should be executed at startup. If a console command is not registered during startup, the value is saved and is set immediately when (and if) a console command with that name is registered. For example:

```

`
"console_commands": [
  {
        "name": "map",
        "value": "MyMap"
    }
],
`

```

This would result in the "map" command being executed, resulting in the level "MyMap" being loaded immediately after start up.

##
The Project & Asset Folder

The project folder is where your .cryproject resides, and will also contain your assets folder. The assets folder is where the engine will load all data such as levels, models and scripts from. The vast majority of
[Filesystem](Filesystem_.md)
 functions will be relative to this directory, instead of requiring an absolute path. This also ensures that the game will continue to function regardless of where the assets folder is, or what it is named.

##
Project Folder contents

Name
 |
Description
 |

**
bin/
**
 |
Contains the project's binary files, if any.
 |

**
Assets/
**
 |
Contains the project assets, note that this folder can be named differently depending on the project - name is specified in the .cryproject file.
 |

**
Code/
**
 |
Source code for the project that build the project binaries, if any.
 |

**
Game.cryproject
**
 |
Main project configuration file, determines where assets, binaries and code are loaded from.
 |

##
Temporary Files

The engine will also generate temporary files and directory at run-time, however these do not need to be checked into version control and can be deleted safely.

Name
 |
Description
 |

**
LogBackups/
**
 |
Existing log files are moved into this directory upon Engine startup.
 |

**
Solutions/
**
 |
Created when a solution is created from the CMakeLists.txt in your Code directory.
 |

**
USER/
**
 |
Created on engine startup to store compiled shaders and other temporary data. If two or more engine instances are running, a User(N) folder will be used instead.
 |

**
game.log
**
 |
Created by the engine when running the Launcher, containing the main log text.
 |

**
editor.log
**
 |
Created by the engine when running the Editor, containing the main log text.
 |

**
error.log
**
 |
Created by the engine upon crashing, containing a callstack.
 |

**
error.dmp
**
 |
Created by the engine upon crashing, can be used to debug the crash in Visual Studio.
 |

##
Engine folder contents

**
Name
**
 |
Description
 |

**
bin/
**
 |
Contains the engine binaries
 |

**
Editor/
**
 |
Editor-only assets, should
**
not
**
 be shipped with games
 |

**
Engine/
**
 |
Includes core assets required by the engine, such as shaders and default textures.
 |

**
Tools/
**
 |
Includes tools required for the engine to run, such as CryVersionSelector and the Resource Compiler. Should
**
not
**
 be shipped with final games.
 |

##
Authoring a custom plug-in

The Launcher provides a default template for plug-in creation, and this can also be seen in
*
<engine directory>\Code\GameTemplates\cpp\Plugin
*
. For a simple example of how
[Cry::IEnginePlugin](/docs/static/engines/cryengine-5/categories/28704770/pages/29797056)
 can be implemented, see
[here](/docs/static/engines/cryengine-5/categories/28704770/pages/29797056)
.

##
Receiving Updates

Plug-ins are able to subscribe to updates, receiving callbacks every frame to do any custom work on a per-frame basis. In the simplest case, we can simply override the
[Cry::IEnginePlugin::MainUpdate](/docs/static/engines/cryengine-5/categories/28704770/pages/29797056)

 function, and then call
[Cry::IEnginePlugin::EnableUpdate](/docs/static/engines/cryengine-5/categories/28704770/pages/29797056)
 to make sure that it is called every frame.

##
Project Source Code

Assuming that a code folder was specified in your .cryproject file's .json, we can use the
**
Generate solution
**
 option in the menu that appears when a .cryproject file is right-clicked in the Windows Explorer:

![Image](https://www.cryengine.com/docs/static/attachments/32179243)

This results in a
*
CMakeLists.txt
*

file being generated in the
*
Code
*

folder set to automatically compile any C++ source files contained in the Code folder or its subdirectories.

We can at any point regenerate the solution, for example this might be used when new source files are added to the Code folder.

##
The CMake GUI

For more advanced customization of our builds, we can utilize the
*
'Open CMake GUI'
*
 option in the context menu. This will bring up the CMake GUI as shown below:

![Image](https://www.cryengine.com/docs/static/attachments/29923923)

This GUI can be used to toggle options in the categories at any time. Clicking
**
Generate
**
 afterwards would then re-create your Visual Studio solution.

For example, we can enable 'OPTION_ENGINE' in projects to build the full engine alongside the project - directly to the project directory.

The OPTION_ENGINE option can only be used if full source code is available in your engine installation - this is not the case by default with Launcher installations. Please download source code from our GitHub repository.

##
Conclusion

This concludes the article on Projects and Plug-ins, you may be interested in:

-
[Introduction to the Engine API](/docs/static/engines/cryengine-5/categories/23756813/pages/26874885)

-
[Entity](Entity.md)

-
[Building the Engine from Source Code](/docs/static/engines/cryengine-5/categories/23756813/pages/26216218)
