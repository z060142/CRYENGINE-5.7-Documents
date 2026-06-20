# GameZero Programming

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/23309014
- Page ID: 23309014
- Breadcrumb: CRYENGINE Game Code > GameZero Programming
- Parent: CRYENGINE Game Code

## Content

##
Building GameZero

Assuming you are familiar with the
[Getting Started with Game Code](Getting%20Started%20with%20Game%20Code.md)
 guide and the basic concept behind
[GameZero](/docs/static/engines/cryengine-5/categories/23756813)
, select
**
[GameZero] Profile, x64
**
 from the configuration settings to compile
**
CryGameZero.dll
**

![Image](https://www.cryengine.com/docs/static/attachments/25495641)

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
![Image](https://www.cryengine.com/docs/static/attachments/25495640)
