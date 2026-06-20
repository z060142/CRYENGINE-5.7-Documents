# Creating Character Definition - Character Tool

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/44959476
- Page ID: 44959476
- Breadcrumb: Editor Tools > Animation Tab > Character Tool > Creating Character Definition - Character Tool
- Parent: Character Tool

## Content

##
Overview

The Character Tool makes it possible to create a character definition through UI without manual XML editing.

##
Prerequisites

Before proceeding, make sure that you have following content:

-
Ready to use character skeleton (CHR file)

-
Some skinned geometry (SKIN file)

-
Animations
These are usually created in a DCC tool and are exported from there.

##
Character Definition Structure

Each character definition (CDF) consists of a reference to the skeleton (CHR) and a set of attachments.

Each skeleton has associated skeleton parameters (CHRPARAMS). It is used to define the animation list of the character.

Attachments can be of different types; the most important ones are:

-
Skin attachments - allows to add skinned geometry to the skeleton.

-
Joint attachments - used to attach rigid geometry or other characters (e.g. weapons) to one of the joints.

##
Steps

-
Create CDF

-
Go to menu
**
 File -> New Character...
**

-
Select a location for the newly created CDF file.

-
Select skeleton

-
In the
**
Properties
**
 panel - click on the
**
Folder
**
 icon next to the parameter
**
Skeleton
**
.

-
Locate skeleton file (CHR).

-
To make sure that the skeleton is properly loaded enable
**
Skeleton
**
 in
**
Display Options
**
 (above top right corner of the viewport).

-
Define animation list

-
Now click on the button next to the
**
Skeleton
**
 parameter. This will select the Skeleton and show its parameters (content of CHRPARAMS file).

-
Click on the
**
number button
**
 next to
**
Animation Set Filter
**
and choose
**
Add
**
.

-
Click on the
**
folder
**
 icon, next to the newly added filter line, select a folder that contains animations for this character.

-
Click the
**
Save
**
 button in the
**
Properties
**
 panel (or choose
**
Save
**
 in the asset context menu).

-
If you haven't imported your animations yet follow these steps:
[/docs/static/engines/cryengine-5/categories/23756816/pages/29450427](
Animation Import
)
.

-
Add SKIN attachment

-
Now go back to the CDF. You can either use the
**
Back
**
 button in the location toolbar, or press on the button next to the
**
Character
**
 parameter in
**
Scene Parameters
**
.

-
Use the
**
number button
**
 next to the
**
Attachments
**
 list to add a new attachment.

-
Within the attachment make sure that the type of the attachment is
**
Skin
**
 and click on the
**
folder
**
 icon next to the
**
Geometry
**
 parameter to locate the SKIN file. You can read more on attachments here:
[/docs/static/engines/cryengine-5/categories/23756816/pages/36869398](
Character Attachments
)
.

-
From now on you should see the character geometry in the viewport.
