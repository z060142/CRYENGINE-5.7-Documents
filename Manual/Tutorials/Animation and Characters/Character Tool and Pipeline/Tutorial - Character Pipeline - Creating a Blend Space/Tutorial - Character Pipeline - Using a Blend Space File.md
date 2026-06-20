# Tutorial - Character Pipeline - Using a Blend Space File

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/69468585
- Page ID: 69468585
- Breadcrumb: Tutorials > Animation and Characters > Character Tool and Pipeline > Tutorial - Character Pipeline - Creating a Blend Space > Tutorial - Character Pipeline - Using a Blend Space File
- Parent: Tutorial - Character Pipeline - Creating a Blend Space

## Content

##
Overview

The following tutorial will walk you through using an example blend space file and adding your own animations to it.

##
Prerequisites

-
Familiarity with creating and assigning blend spaces to your character. See
[Tutorial - Character Pipeline - Creating a Blend Space](../Tutorial%20-%20Character%20Pipeline%20-%20Creating%20a%20Blend%20Space.md)
.

-
A Mixamo character with a skeleton, mesh, and the following locomotion animations set up: Falling Idle, Idle, Jump, Left Strafe Walk, Right Strafe Walk, Left Strafe Run, Right Strafe Run, Left Turn 90 Degrees, Right Turn 90 Degrees, Running, Slow Jog Backwards, Walking. The character and its animations should be imported into your CRYENGINE project.

For more information on creating a Mixamo character from scratch, refer to our step-by-step
[tutorial blog](https://www.cryengine.com/news/view/cryengine-summer-academy-creating-a-character)
.

-
A copy of the following blend space example file:

[locomotion.bspace](/docs/static/attachments/69468587)

##
Loading the Example Blend Space File

-
Navigate to the sub-folder that contains your character file and it's animations in your CRYENGINE project's directory; this is typically,
*
Assets/Objects/Characters/<your character>.
*

-
Create a folder called
*
blendspace
*
 in your character's folder and place the provided blend space example file within it.

-
In the Sandbox Editor, open the Character Tool (
**
Tools → Animation → Character Tool
**
) from the main menu.

-
In the Assets panel of the Character Tool, locate your character's .cdf file under the
**
Characters
**
 folder and double click to open it.

At this point, in the Character Tool's Properties panel, you should see information related to the various attachments that make up your character.

-
Under
**
Animations
**
 in the Assets panel, you should now see a folder called
*
blendspace.
*
Within it, locate the
*
locomotion.bspace
*
 file you saved in step 2 and click it to open it.

##
Visualizing Blend Spaces

To visualize the blend spaces we create in the Character Tool, select the
**
View → Blend Space Preview
**
option from the
![Image](https://www.cryengine.com/docs/static/attachments/56659447)
 menu in the top-right corner of the tool to open the Belnd Space Preview panel.

Under
**
Examples
**
 in the Properties panel, you'll find that each of the examples show the following error due to the Engine being unable to locate the placeholder animations.

![Image](https://www.cryengine.com/docs/static/attachments/69468592)

*
Examples error
*

To fix this:

-
Replace each placeholder animation by clicking
![Image](https://www.cryengine.com/docs/static/attachments/44966234)
 icon beside an example, and selecting your own animation from the Animation Alias Selection window that opens up.

Make sure to stick to the original order of examples while assigning animations; the
**
Idle
**
example must have an idle animation assigned to it, walking animations should be assigned to the
**
Walking
**
example, and so forth.

-
Save your changes by clicking the icon at the top of the Properties panel.

Your blend space file is now successfully set up. The next step is to set up your animations in the Mannequin Editor; see
[Tutorial - Character Pipeline - Mannequin Setup](../../Mannequin%20Editor/Tutorial%20-%20Character%20Pipeline%20-%20Mannequin%20Setup.md)
 for more information.

##
Video Tutorial

[Embed: https://www.youtube.com/watch?v=vzOoLNFD83s]

[Prerequisites](#prerequisites)
[Loading the Example Blend Space File](#loading-the-example-blend-space-file)
[Visualizing Blend Spaces](#visualizing-blend-spaces)
[Video Tutorial](#video-tutorial)
