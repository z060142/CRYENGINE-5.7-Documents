# Tutorial - Character Pipeline - Creating a Blend Space

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/65437964
- Page ID: 65437964
- Breadcrumb: Tutorials > Animation and Characters > Character Tool and Pipeline > Tutorial - Character Pipeline - Creating a Blend Space
- Parent: Character Tool and Pipeline

## Child Pages

- [Tutorial - Character Pipeline - Using a Blend Space File](Tutorial - Character Pipeline - Creating a Blend Space/Tutorial - Character Pipeline - Using a Blend Space File.md)

## Content

##
Overview

Following the previous tutorial, your character will just have standard animations. To ensure that the animations change dynamically depending on the direction or speed of the character, blend spaces are needed.

##
Prerequisites

-
A character with a skeleton, mesh and animations imported into CRYENGINE (see previous tutorials).

##
Creating and Opening a Blend Space File

-
In the folder where your character is;

-
Create a folder called
*
blendspace
*
;

-
In this folder, create a textfile and rename it to
*
<name>.bspace
*
, so for example
*
locomotion_bs.bspace
*
;

The file should not have the .txt extension anymore.

You'll get a warning that the file may become unusable, but that is fine.

-
Open CRYENGINE and open the Character Tool (
**
Tools → Animation → Character Tool
**
);

-
In the Character Tool, find your character under
**
Characters
**
 in the
**
Assets
**
 panel and double-click it to open it;

-
Under Animations in the Assets panel, you should now see a folder called
*
blendspace
*
. Open it and click on the blend space file you created earlier to open it.

##
Blend Space Preview

You'll see that a number of options appeared in the Properties on the right side:

[Image: /docs/static/attachments/65437993]

*
Blend space properties
*

To understand what these do, you'll need to open the Blend Space Preview under
**
menu
**
[Image: /docs/static/attachments/65437994]
 (top right)
**
→ View → Blend Space Preview
**
. A new panel will open in the Character Tool:

[Image: /docs/static/attachments/65437995]

*
Blend Space Preview panel
*

You can dock and resize this panel however you want, or even open it on a second monitor.

##
Adding Dimensions

Now you'll need to add the Dimensions. How many depends on the number of dimensions your animations go in; if you're only doing a walking blend space, which we'll do in this tutorial, you only need two dimensions:
**
Travel Speed
**
 and
**
Travel Angle
**
.

-
In the
**
Properties
**
 panel, click on the
**
dropdown button
**

[Image: /docs/static/attachments/65437996]
 next to Dimensions and choose
**
Add
**
;

-
Click the large button next to 0. and choose
**
Travel Speed
**
;
**

**
Set the
**
Max
**
 value to
**
7.5
**
 and
**
Cell Count
**
to
**
10
**
;

-
Repeat step 2 and choose
**
Travel Angle.
**
 Set its
**
Cell Count
**
 to
**
5
**
 and the
**
Min
**
 and
**
Max
**
 value to
**
3.14
**
;

The Cell Count values represent the lines on the mesh that the animations are placed on. How many you need, depends on optimization. For this tutorial, a value between 5 and 10 is fine.

**

**

The animations used in this tutorial cover 360 degrees of movement (i.e. a circle), so using radians as a scale is the easiest way to make sure everything works out the way you want it to. That is why 3.14 (Pi) is used for Travel Angle.

-
Next, you need to add Examples. In the Properties Panel, click the
**
dropdown button
**

[Image: /docs/static/attachments/65437996]
 next to
**
Examples
**
 and choose
**
Add
**
;

-
It's best to start with the Idle animation, which will need be put on the back line of the grid. Click the large button next to 0. and choose your Idle animation;

-
Do this again and add a second Idle animation. This one will need to move over to the next corner a bit, so change the Travel Angle until it's on the corner;

-
Repeat steps 4-6 until all corners on the back line have Idle animations on the corners;

As you set the Travel Angle to -3.14 and +3.14, this should be the values for respectively the animation on the right edge and the left edge.

-
On the next row, start with a backwards walking animation on the right;

-
Second from the right, add a right strafe walking animation;

-
In the middle of this row, add the forward walking animation;

-
Next, to the left of the forward walking animation, add a left strafe walking animation;

-
On the far left, add the same backwards walking animation as in step 8;

-
In the next row, add a right strafe
*
running
*
 animation and make sure it is in front of the right strafe walking animation (6);

-
Then, add the (forward) running animation. This should be positioned right in the middle, one box ahead of the right strafe running animation;

-
Add the left strafe running animation on the left, the same way as the right strafe running animation in step 13.

##
Annotations

Now you'll need to connect the animations together, so the Engine knows which ones need to be blended. To do this, you need to add Annotations in so-called "quads".

However, first save and restart the Engine.

-
In the Properties Panel, click the
**
dropdown button
**

[Image: /docs/static/attachments/65437996]
 next to
**
Annotations
**
and choose
**
Add
**
;

-
In the
**
dropdown button
**

[Image: /docs/static/attachments/65437996]
 next to
**
0.
**
, choose
**
4
**
 as this first group needs to consist of 4 animations;

-
These animations need to be added counter-clockwise, beginning at the bottom right, so add 0, 5, 6 and 1 in that order;

-
Do the same for 1, 6, 7 and 2, 2, 7, 8 and 3, and 3, 8, 9 and 4.

-
repeat step 2 and 3, but as the next group would only consist of 3 animations, choose 3 instead of 4 animations.

The first group will be 5, 10 and 6;

-
The next two groups after that would have 4 animations again: 6, 10, 11 and 7, and 7, 11, 12 and 8;

-
The last group is 3 animations again: 8, 12 and 9.

-
Save everything.

##
Assigning the Blend Space to the Character

The blend space has now been created, but not assigned to the (playable) character yet. To do this:

-
Open the Mannequin Editor (
**
Tools → Animation → Mannequin Editor
**
);

-
Go to
**
File → Load Preview Setup...
**
 and choose your character (this should be the
*
Player.xml
*
 if you followed the previous tutorials and set up this character as the playable character);

-
In the
**
Assets
**
 panel, expand the
*
Walk
*
folder and assign the blend space you created as the walk animation (for instructions on how to do this, read the
[/docs/static/engines/cryengine-5/categories/23756816/pages/65437937#Tutorial-MakingYourCharacteraPlayableCharacter-AssignAnim](
previous tutorial
)
);

-
You're done!

##
Video Tutorial

[#prerequisites](
Prerequisites
)
[#creating-and-opening-a-blend-space-file](
Creating and Opening a Blend Space File
)
[#blend-space-preview](
Blend Space Preview
)
[#adding-dimensions](
Adding Dimensions
)
[#annotations](
Annotations
)
[#assigning-the-blend-space-to-the-character](
Assigning the Blend Space to the Character
)
[#video-tutorial](
Video Tutorial
)
