# _Console

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/29791867
- Page ID: 29791867
- Breadcrumb: _Console

## Content

##
Overview

The engine exposes the console as a means for the user to set and store values of
**
console variables
**
, in order to manipulate the state of the game and engine without requiring source code modifications. Additionally, the console allows for
**
console commands
**
, similar to variables but execute a function whenever it is executed by the user.

The console can be manipulated either through code, or by pressing the tilde key in-game.

##
Table of Contents

[#api-types](
API Types
)
[#console-variables](
Console Variables
)
[#console-commands](
Console Commands
)
[#conclusion](
Conclusion
)

##
API Types

-
[/docs/static/engines/cryengine-5/categories/28704770/pages/29797230](
IConsole
)

-
[/docs/static/engines/cryengine-5/categories/28704770/pages/29797231](
ICVar
)

-
[/docs/static/engines/cryengine-5/categories/28704770/pages/29797234](
IConsoleCmdArgs
)

-
[/docs/static/engines/cryengine-5/categories/28704770/pages/29797232](
IConsoleArgumentAutoComplete
)

##
Console Variables

Often referred to as
**
CVars
**
, console variables can be registered in code in order to expose a global variable that can be tweaked by designers without modifying code later on.
CVars are represented by the
[/docs/static/engines/cryengine-5/categories/28704770/pages/29797231](
ICVar
)
 interface in code. For an example of how to create a CVar, see
[/docs/static/engines/cryengine-5/categories/28704770/pages/29797230](
IConsole::Register
)
.

[/docs/static/engines/cryengine-5/categories/28704770/pages/29797230](
Example
)

Adding a CVar can be done in many ways:

-
Through
[/docs/static/engines/cryengine-5/categories/28704770/pages/29797230](
IConsole::GetCVar
)
 and
[/docs/static/engines/cryengine-5/categories/28704770/pages/29797231](
ICVar::Set
)

-
By adding the CVar and its desired value to your .cryproject

-
By modifying a .cfg file

##
Console Variable Groups

Console variable groups provide a convenient way to apply predefined settings to multiple console variables at once, and are commonly referred to as
**
CVarGroup
**
. The main use case for CVarGroups is for changing the graphical spec, using the "sys_spec" CVar.

##
Registering a new variable group

To register a new variable group, add a new .cfg text file to the
*
`
Config/CVarGroups
`
*
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
Console Commands

Similarly to Console Variables, Console Commands are referred to as
**
CCommands
**
 and provide support for executing a function whenever the specified command is executed. For an example of how to create your own console commands, see
[/docs/static/engines/cryengine-5/categories/28704770/pages/29797230](
IConsole::AddCommand
)
.

[/docs/static/engines/cryengine-5/categories/28704770/pages/29797230](
Example
)

##
Conclusion

This concludes the article on the console. You may be interested in:

-
[/docs/static/engines/cryengine-5/categories/23756813/pages/26874879](
Filesystem_
)

-
[/docs/static/engines/cryengine-5/categories/23756813/pages/28184591](
Profiling and Debugging
)

-
[/docs/static/engines/cryengine-5/categories/23756813/pages/26216243](
_Shaders
)
