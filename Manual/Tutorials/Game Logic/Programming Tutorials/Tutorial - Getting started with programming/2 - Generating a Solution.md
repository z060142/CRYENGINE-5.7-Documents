# 2 - Generating a Solution

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/27592191
- Page ID: 27592191
- Breadcrumb: Tutorials > Game Logic > Programming Tutorials > Tutorial - Getting started with programming > 2 - Generating a Solution
- Parent: Tutorial - Getting started with programming

## Content

In order to start generating a Visual Studio solution, we need to go to our project directory. This was configured in the previous step in the
**
Create Project
**
 screen.

It is also possible to open the project directory using the Launcher
by clicking on the
**
gear
**
 icon and choosing
**
Reveal in Explorer
**
.

Generating a Visual Studio Solution

You need to follow these below mentioned steps to import a game project:

-
Right click the
*
Game.cryproject
*
 file and select
**
 Generate Solution
**

-
Navigate to your
**
Solutions
**
 directory in the same directory. Open the
**
win64
**
 directory, containing
**
Game.sln
**

-
Double click
your
**
Game.sln
**
 file to
 open the solution with Visual Studio. Once opened, you should have a view similar to image 2 below.

##
   Conclusion

This presents us with our project;
**
Game
**
 (seen under the
**
Project
**
folder in the
**
Solution Explorer
**
), this contains all C++ source files contained in our game plug-in.

Even game projects are represented as plug-ins in CRYENGINE. This means that any game code you write is technically a plug-in for the engine.

In addition, we are presented with three
**
Launchers
**
:

-
**
GameLauncher
**
 - Used to play your game as an end-user would.

-
**
GameServer
**
 - Used to start a dedicated server running your project.

-
**
Sandbox
**
 - Used to open the CRYENGINE Editor to create levels for your project.
By default, the GameLauncher is selected. This means that if we press
**
F5
**
, the project will be built and launched in a pure game context:

##
Step 1

##
Step 2
