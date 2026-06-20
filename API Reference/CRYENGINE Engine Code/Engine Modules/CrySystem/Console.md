# Console

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/23306428
- Page ID: 23306428
- Breadcrumb: CRYENGINE Engine Code > Engine Modules > CrySystem > Console
- Parent: CrySystem

## Child Pages

- [CVar Tutorial](Console/CVar Tutorial.md)

## Content

##
Overview

The console is a user interface system which handles console commands and console variables.
 It is also used to output log messages and stores the input and output history.

##
Color coding

The game console supports color coding by using the color indices
**
0..9
**
 with a leading
**
$
**
 character. The code is hidden in the text outputted on the console. Simple log messages through the
**
 ILog
**
 interface can be used to send text to the console.

```

`
This is normal $1one$2two$3three and so on

`

```

This is normal
one
two
three and so on.

##
Dumping all console commands and variables

Using the command
**
DumpCommandsVars
**
, all console commands and console variables can be logged to a file (consolecommandsandvars.txt by default).

A parameter can be passed to restrict the variables that should be dumped. For example, the command:

```

`
DumpCommandsVars i_
`

```

... would log all commands and variables that begin if the sub-string
**
i_
**
 like
**
i_giveallitems
**
 and
**
i_debug_projectiles
**
 .

##
Console Variables

Console variables provide a convenient way to expose variables which can be modified easily by the user either by being entered in the console during runtime or by passing it as command-line argument before launching the application.

More information on how to use command-line arguments can be found in the
[/docs/static/engines/cryengine-3/categories/1114113/pages/12746775](
Command Line Arguments
)
 article.

Console variables are commonly referred to as
**
CVar
**
 in the code base.

##
Registering new console variables

For integer or float based console variable, it is recommended to use the
**
IConsole::Register()
**
 function for exposing a C++ variable as a console variable.

To declare a new string console variable, the
**
IConsole::RegisterString()
**
 function can be used.

##
Accessing console variables from C++

Console variables are exposed using the
**
ICVar
**
 interface. To retrieve this interface, the
**
IConsole::GetCVar()
**
 function should be used.

The most efficient way to read the console variable value is to access directly the C++ variable bound to the console variable proxy.

##
Adding New Console Commands

The console can easily be extended with new console commands. A new console command can be implemented in C++ as a static function which follows the ConsoleCommandFunc type. Arguments for this console command are passed using the
**
IConsoleCmdArgs
**
 interface.

The following code shows the skeleton implementation of a console command:

```

`
static void RequestLoadMod(IConsoleCmdArgs* pCmdArgs);

void RequestLoadMod(IConsoleCmdArgs* pCmdArgs)
{
  if (pCmdArgs->GetArgCount() == 2)
  {
   const char* pName = pCmdArgs->GetArg(1);
   // ...
  }
  else
  {
   CryLog("Error, correct syntax is: g_loadMod modname");
  }
}

`

```

The following code will register the command with the console system:

```

`
IConsole* pConsole = gEnv->pSystem->GetIConsole();
pConsole->AddCommand("g_loadMod", RequestLoadMod);

`

```

More information can be found about the IConsole::AddCommand() function.

##
Console Variable Groups

Console variable groups provide a convenient way to apply predefined settings to multiple console variables at once.

Console variables are commonly referred to as
**
CVarGroup
**
 in the code base. Console variable groups can modify other console variables so they can be used to build bigger hierarchies.

Warning
Cycles in the assignments are not detected and can cause crashes.

##
Registering a new variable group

To register a new variable group, add a new .cfg text file to the
`
GameSDK\config\CVarGroups
`
 directory.

```

`
[default]
; default of this CVarGroup
= 4
e_particles_lod=1
e_particles_max_emitter_draw_screen=64

[1]
e_particles_lod=0.75
e_particles_max_emitter_draw_screen=1

[2]
e_particles_max_emitter_draw_screen=4

[3]
e_particles_max_emitter_draw_screen=16

`

```

This creates a new console variable group named "sys_spec_Particles" that behaves like an integer console variable. By default, this variable has the state 4 (set through the line following the comment).

On changing the variable, the new state is applied. Console variables not specified in the .cfg file are not set. All desired console variables need to be part of the default section. An error message is output in case of violation of this rule.

If a console variable is not specified in a custom section, the value specified in the default section is applied.

##
Console variable group documentation

The documentation of the console variable group is generated automatically.

```

`
Console variable group to apply settings to multiple variables

sys_spec_Particles [1/2/3/4/x]:
 ... e_particles_lod = 0.75/1/1/1/1
 ... e_particles_max_screen_fill = 16/32/64/128/128
 ... e_particles_object_collisions = 0/1/1/1/1
 ... e_particles_quality = 1/2/3/4/4
 ... e_water_ocean_soft_particles = 0/1/1/1/1
 ... r_UseSoftParticles = 0/1/1/1/1

`

```

##
Checking if a console variable group value represents the state of the variables it controls

##
From console

In the console you can type in the console variable group name and press tab. If the variable value it not representative, it will print the real state or custom besides the usual information.

```

`
sys_spec_Particles=2 [REQUIRE_NET_SYNC] RealState=3
sys_spec_Sound=1 [REQUIRE_NET_SYNC] RealState=CUSTOM
sys_spec_Texture=1 [REQUIRE_NET_SYNC]

`

```

By calling the console command
**
sys_RestoreSpec
**
 you can check why the
**
sys_spec_
**
 variables don't represent the right states.

##
From C++ code

From the code you can use the member function
**
GetRealIVal()
**
 and compare its return value against the result of
**
GetIVal()
**
 in
**
ICVar
**
 .

##
Deferred execution of command line console commands

The commands that are passed via the command line by using the + prefix (ex.
*
crysis.exe +map island
*
) are stored in a separate list as opposed to the rest of the console commands.

This list allows the application to distribute the execution of those commands over several frames rather than executing everything at once.

##
Example

As an example consider this command line:

```

`
--- autotest.cfg --
hud_startPaused = "0"
wait_frames 100
screenshot autotestFrames
wait_seconds 5.0
screenshot autotestTime

-- console --
crysis.exe -devmode +map island +exec autotest +quit

`

```

The following operations were performed:

-
Load the island map.

-
Wait for 100 frames.

-
Take a screenshot called autotestFrames.

-
Wait for 5 seconds.

-
Take a screenshot called autotestTime.

-
Quit the application.

##
Details

Two categories of commands are defined:
*
blocker
*
 and
*
normal
*
.

Each frame, the deferred command list is processed as a fifo. Elements of this list are consumed as long as
*
normal
*
 commands are encountered.

When a
*
blocker
*
 is consumed from the list and executed, the process is delayed until the next frame. For instance, commands like
**
map
**
 and
**
screenshot
**
 are blockers.

A console command (either command or variable) can be tagged as a blocker during it's declaration using the
**
VF_BLOCKFRAME
**
 flag.

The following synchronization commands are supported:

**
Command
**

 |
Type

 |
Description

 |

**
wait_frames
**

*
num
*
:

 |
<int>

 |
wait for
*
num
*
 frames before the exeution of the list is resumed.

 |

**
wait_seconds
**

*
sec
*
:

 |
<float>

 |
wait for
*
sec
*
 seconds before the exeution of the list is resumed.

 |

##
Disabling the console in release builds

The console can be disabled in release builds. To do this, open
**
ProjectDefines.h
**
 (located in
`
Code\CryEngine\CryCommon\CryCore\Project)
`
 and comment out or delete the line containing
**
#define ENABLE_DEVELOPER_CONSOLE_IN_RELEASE
**
 and recompile the engine.

[#color-coding](
Color coding
)
[#dumping-all-console-commands-and-variables](
Dumping all console commands and variables
)
[#registering-new-console-variables](
Registering new console variables
)
[#accessing-console-variables-from-c](
Accessing console variables from C++
)
[#registering-a-new-variable-group](
Registering a new variable group
)
[#console-variable-group-documentation](
Console variable group documentation
)
[#checking-if-a-console-variable-group-value-represents-the-state-of-the-variables-it-controls](
Checking if a console variable group value represents the state of the variables it controls
)
[#example](
Example
)
[#details](
Details
)
