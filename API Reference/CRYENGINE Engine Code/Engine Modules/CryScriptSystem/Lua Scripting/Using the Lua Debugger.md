# Using the Lua Debugger

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/23306631
- Page ID: 23306631
- Breadcrumb: CRYENGINE Engine Code > Engine Modules > CryScriptSystem > Lua Scripting > Using the Lua Debugger
- Parent: Lua Scripting

## Content

##
Overview

CRYENGINE includes a visual LUA script debugger. The debugger is embedded in CryScriptSystem making it accessible both from Sandbox and also the Launcher.

![Image](https://www.cryengine.com/docs/static/attachments/23461424)

##
Using the Debugger

The script debugging functionality needs to be enabled by setting the
**
lua_debugger
**
 CVar to 1 or 2.

-
lua_debugger 1 - The debugger will break on both breakpoints and script errors.

-
lua_debugger 2 - The debugger will break only on script errors.
The debugger tool can be opened by typing the following command inside the in-game console:

```

`
lua_debugger_show

`

```

Please note that any code modification done within the debugger window won't have any impact on the loaded script and, more importantly, any change will be discarded once the window is closed.

The debugger window can reload scripts at any time by choosing the Reload option in the File menu.

It's also possible to invoke the debugger window from a Lua script which has the same effect as a breakpoint, but gives you more control.

```

`
System.ShowDebugger()

`

```

##
Using Breakpoints

In the debugger window menu, you can see which mode is currently selected and change it. Also the breakpoints change color - red indicates they are active, gray that they are disabled.

-
**
F5
**
 - Continue.

-
**
F9
**
 - Toggle a breakpoint.

-
**
F10
**
 - Step over.

-
**
F11
**
 - Step into.
Note that the callstack always shows Lua calls but initially does not show C/C++ calls. This can be enabled in the menu and may cause an initial stall of around 10 seconds for necessary initialization.

Other useful menu item: Reset All Panels to bring the window layout back to sensible settings.
