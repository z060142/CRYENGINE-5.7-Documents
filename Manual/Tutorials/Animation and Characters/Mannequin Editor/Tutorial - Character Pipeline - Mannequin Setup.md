# Tutorial - Character Pipeline - Mannequin Setup

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/65438020
- Page ID: 65438020
- Breadcrumb: Tutorials > Animation and Characters > Mannequin Editor* > Tutorial - Character Pipeline - Mannequin Setup
- Parent: Mannequin Editor*

## Content

##
Overview

This tutorial will explain how to set up animations in Mannequin.

##
Steps

-
Open the Sandbox Editor and open a new or existing level that you want to check your character in;

-
Open the Mannequin Editor by going to
**
Tools → Animation → Mannequin Editor
**
;

-
In the Mannequin Editor, go to
**
File → Load Preview Setup...
**
, navigate to
**
Animations → Mannequin → Preview
**
 and open
*
Player.xml;
*

-
In the Fragment Editor, you should see your character in T-pose:

[Image: /docs/static/attachments/65438027]

*
Loaded character in T-pose
*

-
In the Fragments panel, expand all options under
**
Idle
**
and double-click on
**
Option 1
**
:

[Image: /docs/static/attachments/65438029]

*
Idle Option 1
*

-
In the bottom right, there are two Animation Layers, one for First Person (FirstPerson(FirstPerson)) and one for Third Person (ThirdPerson(ThirdPerson)), both with an animation already set up for them:

[Image: /docs/static/attachments/65438030]

*
Animation Layers for Idle fragment
*

As this tutorial assumes you're doing a third-person project, click on the
**
Animation Layer
**
 for
*
ThirdPerson
*
 (the colored bar), then click on
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
[Image: /docs/static/attachments/65438025]
 on the right and choose the walk animation for your character;

-
As this is an animation that needs to keep playing the whole time the character is standing still, enable
**
Looping
**
 in the
**
Anim Clip Properties
**
;

-
Repeat these steps for your Walk animation under
**
Walk → <default> → Option 1
**
, and
**
Looping
**
 and
**
Time Warping
**
;

If you have a blend space (see
[/docs/static/engines/cryengine-5/categories/23756816/pages/65437964](
previous tutorial
)
), choose the blend space instead of the walk animation.

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
If you did not assign a blend space for your Walk animation, you will notice that the character will jump back to the T-pose when rotating. This is because no rotation animation was assigned.

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
