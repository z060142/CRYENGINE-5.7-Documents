# Game Executable Command-line Arguments

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/25535471
- Page ID: 25535471
- Breadcrumb: Packaging and Deployment > Game Executable Command-line Arguments
- Parent: Packaging and Deployment

## Content

##
Overview

Sandbox accepts most of the same command line arguments as
[Launcher.exe](/docs/static/engines/cryengine-3/categories/1638401/pages/1605722)
, and also has the additional ability of loading
*
.cry
*
 files parsed in the first parameter.

##
Command Line Arguments Example

The following input:

```

`
Launcher.exe -Arg1 -Arg2 ParamOfArg2 +Arg3 Param1OfArg3 Param2OfArg3 +Arg4 "ParamOfArg4" +Arg5 4-3+2 -Arg6
`

```

... will result in the following pre-commands (starting with a minus symbol (-); modify the startup behavior):

```

`
Arg1 Arg2 ParamOfArg2 Arg6
`

```

... and the following post-commands (starting with plus symbol (+); executed as console commands after initialization; all in the same frame):

```

`
Arg3 Param1OfArg3 Param2OfArg3
Arg4 "ParamOfArg4"
Arg5 4-3+2
`

```

##
Recognized Pre and Post Commands

Below you'll find two lists of command-line arguments; one with CLAs that apply to the game or game launcher and one with CLAs that apply to the Sandbox Editor.

If you have Engine and Game code, searching for "eCLAT_Pre" and "eCLAT_Post" should give you all of the available arguments.
Command-Line Arguments for the Game/Game Launcher

PRE Commands

 |
Usage (Prefixed with "-")

 |
Description

 |

**
DEVMODE
**

 |
Game.exe -DEVMODE

 |
**
DEPRECATED -
**
 Devmode is enabled by default in all modes except for Release Pure-Game.

In DEVMODE, the lua debugger is disabled and the pak file system now prefers files outside the pak files.

The LUA command execution in the console is now allowed (by using the # prefix). CVars marked with the Cheat flag can be changed.

 |

**
nodevmode
**

 |
Game.exe -nodevmode

 |
Disable devmode in pure-game mode, even in non-release builds.

 |

**
DX11
**

 |
Game.exe -DX11

 |
Use Direct3D 11 renderer (override the system.cfg setting).

 |

**
GL
**

 |
Game.exe -GL

 |
Use GL renderer (override the system.cfg setting).

 |

**
MOD
**

 |
Game.exe -MOD MyMod

 |
Loads a MOD DLL, instead of the standard game code. Adds the folder of the MOD to the data directories to search in.

MODs must be located in the
`
<root>\Mods
`
 directory.

 |

**
root
**

 |
Game.exe -root RootFolder

 |
Overrides the default folder for log files (also, LogBackups), cfg files (for the exec command), and level rotation files.

This command line option is mostly used for 3rd party hosting, with multiple instances on the same machine support.

 |

**
nomouse
**

 |
Game.exe -nomouse

 |
Disable mouse input.

 |

**
noprompt
**

 |
Game.exe -noprompt

 |
Disable the message box.

 |

**
autodetect
**

 |
Game.exe -autodetect

 |
Auto-detect system spec (overrides profile settings).

 |

**
anycpu
**

 |
Game.exe -anycpu

 |
If CRYENGINE detects an unsupported CPU, you can specify whether to allow continued use or not.

 |

**
anygpu
**

 |
Game.exe -anygpu

 |
If CRYENGINE detects an unsupported GPU, you can specify whether to allow continued use or not.

 |

**
LvlRes
**

 |
Game.exe -LvlRes

 |
All assets since executable start are recorded.

 |

**
pakalias
**

 |
Game.exe -pakalias Folder1,FolderNew,Textures,TestBuildTextures

 |
This is a list of pairs separated by commas. Paths that include aliases will be string substituted during file look up.

 |

**
dedicated
**

 |
Game.exe -dedicated

 |
Launch game as dedicated server.

 |

**
dedicatedarbitrator
**

 |
Game.exe -dedicatedarbitrator

 |
Launch game as dedicated arbitrator server.

 |

**
daemon
**

 |
Game.exe -deamon

 |

 |

**
simple_console
**

 |
Game.exe -simple_console

 |
Use simple light-weight console implementation

 |

**
logfile
**

 |
Game.exe -logfile game.log

 |
Override default file name of logfile

 |

**
ResetProfile
**

 |
Game.exe -ResetProfile

 |

 |

**
useamblecfg
**

 |
Game.exe -useamblecfg

 |
Loads amble.cfg file for Stats Agent.

 |

**
nodlc
**

 |
Game.exe -nodlc

 |
Don't load DLC content.

 |

**
g_multiplayerDefault
**

 |
Game.exe -g_multiplayerDefault 1

 |
Set Multiplayer as the default game mode.

 |

**
sv_bind
**

 |
Game.exe -sv_bind <IP>

 |

 |

**
lt_pipename
**

 |
Game.exe -lt_pipename pipename

 |
Create pipe for Stats Agent.

 |

**
skip_unit_tests
**

 |
Game.exe -skip_unit_tests

 |

 |

**
use_unit_test_excel_reporter
**

 |
Game.exe -use_unit_test_excel_reporter

 |

 |

POST Commands

 |
Usage (Prefixed with "+")

 |
Description

 |

**
sys_no_crash_dialog
**

 |
Launcher.exe +sys_no_crash_dialog

 |

 |

**
map
**

 |
Launcher.exe +map Forest

 |
Load a level automatically after system finishes initializing.

 |

**
connect
**

 |
Launcher.exe +connect <IP>

 |
Connect to an IP address for multiplayer use.

 |

**
client
**

 |

 |

 |

##
Typical Use Cases

-
Set a console variable and load a map:
**
Launcher.exe +r_displayinfo 1 +map Forest
**

-
Call a lua command:
**
Launcher.exe +#System.DumpMemStats()
**

-
Run the game in a specific spec and set a CVar (console variables and commands are not case sensitive):
**
Launcher.exe +loadconfig lowspec +r_displayinfo 1
**

Useful Console Variables

**
hud_startPaused
**

```

The game starts paused, waiting for user input.

```

**
fg_abortOnLoadError
**

```

Abort on load error of flowgraphs
2:abort, 1:dialog, 0:log only

```
