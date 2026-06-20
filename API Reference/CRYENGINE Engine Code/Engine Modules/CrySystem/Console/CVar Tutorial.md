# CVar Tutorial

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/23306429
- Page ID: 23306429
- Breadcrumb: CRYENGINE Engine Code > Engine Modules > CrySystem > Console > CVar Tutorial
- Parent: Console

## Content

##
Overview

In this tutorial you will learn how to modify existing and create new CVars (Console Variables).

These  variables can be used to control many configurable behaviors in CRYENGINE, and can also be used in your game.

This tutorial is targeted at programmers, most of the contents deals with code.

##
Creating New CVars

In your code IDE, open up the
`
Code\GameSDK\GameDll\GameCVars.h
`
file, this file declares all the game-specific CVars.

Locate the
`
SCVars
`
 struct, and inside the struct declare a new variable:

```

`
struct SCVars
{
  int g_tutorialVar; //add this line

  //... pre-existing code ...
};
`

```

 You can also add a variable of float type, if you need to store fractional numbers
The variable you added will be used to store the current value of the variable.

Now, the CVar needs to be registered in the engine, so it's value can be changed through the console

Open up the
`
Code\GameSDK\GameDll\GameCVars.cpp
`
 file, and locate the
`
InitCVars
`
 function:

```

`
void SCVars::InitCVars(IConsole *pConsole)
{
  m_releaseConstants.Init( pConsole );

  REGISTER_CVAR(g_tutorialVar, 42, VF_NULL, "This CVar was added using the tutorial on CVars"); //add this line

    //... pre-existing code ...
}
`

```

In the above example, we specify the default value
**
42
**
 for the variable, and we add some help text that can be shown to other users.

You can initialize the variable to any value that is valid for the variable's type as declared in the header file.

Don't forget to also un-register the variable when your game is unloaded, in the same .cpp file locate the
`
ReleaseCVars
`
 function:

```

`
void SCVars::ReleaseCVars()
{
  IConsole* pConsole = gEnv->pConsole;

  pConsole->UnregisterVariable("g_tutorialVar", true); //add this line

  //... pre-existing code ...
}
`

```

After you finish making code changes, make sure to compile your changes!

##
Using the CVar

You can now write some code that uses the value of the CVar.

In your game-code you can now access the value through the
`
g_pGameCVars
`
 pointer

```

`
int myTutorialVar = g_pGameCVars->g_tutorialVar;
`

```

Ofcourse, since the variable is now a CVar, you can also bring up the console and access the value there.

Open up the console and type the following to set the value of the variable to
**
1337
**
:

```

`
g_tutorialVar = 1337
`

```

It's also possible to change the CVar value from one of the
`
.cfg
`
 files to change the default value.

Whenever the value of a CVar is assigned to, the previous value is discarded. Therefore, the last assignment is the one that will be visible.

Therefore, it's important to know the order of initialization for a CVar. From first to last, the order is:

-
The value specified in the
`
GameCVars.cpp
`
 file when REGISTER_CVAR is used.

-
The value specified in
`
system.cfg.
`

-
The value specified in the user's
`
user.cfg.
`

-
Any value assigned at game runtime.
To change the default value of an existing CVar without having to compile, you can add a line to
`
system.cfg
`
 to override the default.
