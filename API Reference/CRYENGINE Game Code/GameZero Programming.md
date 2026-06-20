# GameZero Programming

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/23309014
- Page ID: 23309014
- Breadcrumb: CRYENGINE Game Code > GameZero Programming
- Parent: CRYENGINE Game Code

## Content

##
Building GameZero

Assuming you are familiar with the
[/docs/static/engines/cryengine-5/categories/23756813/pages/23306497](
Getting Started with Game Code
)
 guide and the basic concept behind
[/docs/static/engines/cryengine-5/categories/23756813](
GameZero
)
, select
**
[GameZero] Profile, x64
**
 from the configuration settings to compile
**
CryGameZero.dll
**

[Image: /docs/static/attachments/25495641]

##
Loading procedure

-
Sandbox/Launcher reads from
**
system.cfg
**
 which game folder has to be loaded -
**
sys_game_folder=GameZero
**

-
**
game.cfg
**
 inside game folder specifies which game DLL has to be loaded -
**
sys_dll_game = CryGameZero
**

-
DLL Loading pipeline is triggered as illustrated below
[Image: /docs/static/attachments/25495640]
