# Tutorial - Making Your Character a Playable Character

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/65437937
- Page ID: 65437937
- Breadcrumb: Tutorials > Game Logic > Programming Tutorials > Tutorial - Making Your Character a Playable Character
- Parent: Programming Tutorials

## Content

##
Overview

Now that you have imported your character into CRYENGINE, you may want to use it as the playable character. Follow the steps below to find out how to do this.

##
Prerequisites

-
A character with a skeleton, mesh and animations imported into CRYENGINE (see previous tutorials)

-
Visual Studio (if you can't afford the full version, there is a free community version available
[here](https://visualstudio.microsoft.com/downloads/)
.)

##
Generating a New Solution

-
In the CRYENGINE Launcher, click on the gear icon
![Image](https://www.cryengine.com/docs/static/attachments/65437939)
 next to the project you want to add the character to (in our previous tutorials in this series, this was a 3rd-person project) and choose
**
Reveal in Explorer
**
;

-
Right-click on the
*
Game.cryproject
*
 file and choose
**
Generate Solution
**
. A command prompt window will pop up that will perform several actions. This will take a while to complete.

It will be complete when the command prompt has closed.

##
Opening the Game Solution

-
A new
*
solutions
*
 folder should have appeared after the previous steps. In this
*
solutions
*
 folder, open the
*
win64
*
 subfolder and double-click on the
*
Game.sln
*
 file. This should open this file in Visual Studio;

-
When this is opened, in the Solution Explorer, navigate to
**
Project → Game → Components
**
 and open
*
Player.cpp
*
;

You can also use the Search Solution Explorer bar at the top of the Solution Explorer to search for Player.cpp.

Importing your Animations

If you haven't already, import your animations into CRYENGINE. This is part of the Export & Import workflow explained in the
[previous tutorial](../../Animation%20and%20Characters/3DS%20Max/Tutorial%20-%20Character%20Pipeline%20-%20Export%20%26%20Import%20with%203ds%20Max%2C%20Maya%20and%20Blender.md)
.

##
Check in Character Tool

To make sure the animations are working correctly, you can check them in the Character Tool:

-
Open the Character Tool by going to
**
Tools → Animation → Character Tool
**
;

-
In the Assets Panel, under Characters, navigate to and open your character;

-
By clicking on the animations listed under Animations, you can check the animations you imported.

##
Changing Code in Visual Studio

-
Maximize Visual Studio;

-
In
*
Player.cpp
*
, look for the line that mentions
*
SetCharacterFile
*
 and change the path to the path and file name of your character;

This should typically be around line 37-40, but this can change depending on any updates that may be made to this file.

It will, however, follow the comment
`
 // Set the player geometry, this also triggers physics proxy creation
`
.

-
Close CRYENGINE;

-
In the main menu in Visual Studio, click
**
Build → Build Solution
**
or
**
Build Game
**
;

B
If other projects rely on the project you want to build, it is recommended to use Build Solution instead of Build Game.

-
When this process if finished, save and close Visual Studio.

##
Changing the Preview File

-
In your project folder, navigate to
**
Assets → Animations → Mannequin → Preview
**
;

-
Open the
*
Player.xml
*
 file with Notepad, Notepad++ or other software that lets you read and edit .xml files;

-
Just like you did in Visual Studio, change the path of the model to the path where your character resides. In the accompanying video tutorial series, a third-person game is made, so you'd have to change the ThirdPersonCharacter model:

![Image](https://www.cryengine.com/docs/static/attachments/65437951)

*
Preview file
*

-
Save and close the file. Your character will now be set as the playable character.

##
Checking the Character in Game

-
Open CRYENGINE and create a new level or open an existing one;

-
Jump into game with
**
Ctrl + G
**
;

-
You should now see your character in T-pose;

##
Mannequin Setup

Although your character will now be the playable character, its animations have not been assigned to it yet, so all you will see is your character in T-pose.

-
Open the Mannequin Editor by going to
**
Tools → Animation → Mannequin Editor
**
;

-
In the Mannequin Editor, go to
**
File → Load Preview Setup..
**
., navigate to
**
Animations → Mannequin → Preview
**
 and open
*
Player.xml;
*

-
In the Fragments panel, expand all options under
**
Walk
**
 and double-click on
**
Option 1
**
:

![Image](https://www.cryengine.com/docs/static/attachments/65437955)

*
Walk Option 1
*

-
In the bottom right, there are two Animation Layers, one for First Person (FirstPerson(FirstPerson) and one for Third Person (ThirdPerson(ThirdPerson), both with an animation already set up for them. As this tutorial assumes you're doing a third-person project, click on the Animation Layer for ThirdPerson (the colored bar), then click on
**
Animation
**
 in the
**
Anim Clip Properties
**
, click on the
**
 browse
**
button
![Image](https://www.cryengine.com/docs/static/attachments/65437956)
 on the right and choose the walk animation for your character;

-
Repeat steps 3 and 4 for your Idle animation under
**
Idle → <default> → Option 1
**
;

For more variation in for example your Idle animations, you can set up multiple animation clips for the same situation.

1. In the
**
Fragments
**
 panel, select the
*
<default>
*
 folder for the Idle or Walk animations (depending on where you want to add an animation clip);

2. Click
**
New
**
 at the bottom of the panel;

3. A new Option will appear under the <default> folder. Repeat steps 3 and 4 to add another animation clip. The Engine will automatically choose between the two animation clips when the character is Idle or Walking, depending on where you added the animation clip.

**
NOTE:
**
 You may have to add an Animation Layer in the bottom right. You do this by right-clicking on the
**
ThirdPerson(ThirdPerson)
**
 text and choosing
**
Add Layer → Animation Layer
**
.

-
Save all your changes by going to
**
File → Save Changes
**
.

-
Jump into the game with
**
Ctrl + G
**
 and check your animations by walking around with your character.

You will notice that the character will jump back to the T-pose when rotating. This is because no rotation animation was assigned.

-
If you don't have a specific rotation animation, you can just use the Walk animation for now:

In the
**
Fragments
**
 panel, navigate to
**
 Idle → Rotate → Option 1
**
 and select the
**
Idle
**
animation as done before in step 3 and 4.
To have proper rotations set up, you'll have to set up blend spaces. Follow the next tutorial to find out how to do this.

##
Video Tutorial

[Embed: https://www.youtube.com/watch?v=VB-P7xtXoWY&feature=youtu.be]
[Prerequisites](#prerequisites)
[Generating a New Solution](#generating-a-new-solution)
[Opening the Game Solution](#opening-the-game-solution)
[Changing Code in Visual Studio](#changing-code-in-visual-studio)
[Changing the Preview File](#changing-the-preview-file)
[Checking the Character in Game](#checking-the-character-in-game)
[Mannequin Setup](#mannequin-setup)
[Video Tutorial](#video-tutorial)
