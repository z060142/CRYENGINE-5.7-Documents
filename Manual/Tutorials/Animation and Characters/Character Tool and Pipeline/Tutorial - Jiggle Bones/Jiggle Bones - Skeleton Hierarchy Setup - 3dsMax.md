# Jiggle Bones - Skeleton Hierarchy Setup - 3dsMax

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/23310611
- Page ID: 23310611
- Breadcrumb: Tutorials > Animation and Characters > Character Tool and Pipeline > Tutorial - Jiggle Bones > Jiggle Bones - Skeleton Hierarchy Setup - 3dsMax
- Parent: Tutorial - Jiggle Bones

## Content

##
Overview

##
Tutorial Files

If you want some files for reference, please download and unzip the tutorial files as described on
**
[/docs/static/engines/cryengine-5/categories/23756816/pages/44959301](
this page
)
**
.

##
Prerequisites for this Tutorial

Before you continue with this tutorial, make sure to have read and understood the following:

-

-
[/docs/static/engines/cryengine-5/categories/23756816/pages/44963469](
How to Install CryMaxTools
)

-
[/docs/static/engines/cryengine-5/categories/23756816/pages/25528753](
The Basic CRYENGINE 3dsMax Workflow
)

-
[/docs/static/engines/cryengine-5/categories/23756816/pages/13205563](
CRYENGINE Exporter
)

-
[/docs/static/engines/cryengine-5/categories/23756816/pages/23308289](
3dsMax Unit Scale to Match up With CRYENGINE Unit System
)

##
Setting Up the 3ds Max Scene and Exporting to CRYENGINE

The goal of this section is to create a poly cylinder and a dummy triangle poly mesh and two skeleton hierarchies in 3ds Max. In contrast to the Maya pipeline, we can leave the scene hierarchy as is, without re-organizing our scene into groups and cryExportNodes. We can immediately export to the CRYENGINE specific file types (CHR and SKIN) at the end.

The poly cylinder we make acts as the pony tail geometry which is skinned to a bone chain. The other bone hierarchy acts as a simplified character skeleton where the bone hierarchy with pony tail mesh will be attached to. In the end, we have a
**
secondary
**

pony tail bone chain

**
extending
**
 the
**
primary
**

character skeleton
.

##
3ds Max Scene File Location

Set up your 3ds Max scene and save it to an appropriate directory, for example YOUR_PROJECT_FOLDER\Assets\Objects\current_tutorial. Be sure that the folder contains the 3ds Max scene and exported files for CRYENGINE is a
**
sub-folder of your project folder
**
. In our case, we saved the 3ds Max scene files in this directory:

**
YOUR_PROJECT_FOLDER\Assets\
Objects\jigglebone_tutorial_max
**

##
Create The Two Hierarchies and  Skin the Geometry Objects to Them

For this tutorial we will create a poly cylinder and skin it to a bone hierarchy. This bone hierarchy can be used for
**
two very distinct use cases
**
:

-
**
loosely hanging down, bendy bone hierarchy:
**

- a long pony tail coming from the back of a head,

- a rubber hose or anything rope-like,

- iron chain with several links,

etc.

-> bones that bend/rotate during simulation

-
**
a cartoony, stretching bone hierarchy:
**

- an antenna sticking out of a robot's head or insect,

- tied-up hair that is short,

- a bouquet of flowers,

etc.

-> bones that stretch/translate during simulation

We assume you to have at least some experience with 3ds Max. Below, you'll see some images showing the interim steps and the final resulting scene.

##
I. Creating the pony tail bone hierarchy and a poly cylinder:

-
Let's start by creating the secondary skeleton, the pony tail bones. First switch to the orthogonal Front Viewport of 3ds Max by pressing
**
F
**
. Use 3ds Max's Bone System to make a straight hierarchy pointing downwards (world negative Z). We chose to use 7 bones (and the end bone node), so we'll have 7 bones in the bone list of the Skin modifier later. Rename the bones for a clean hierarchy.

-
(
*
File: ponytail_skeleton_start.max
*
)

[Image: /docs/static/attachments/25521848]

*
Pic1: A clean named bone hierarchy
*

-
3ds Max will orient your bones as shown in the picture below if you draw the bones from the orthogonal Front Viewport. In the associated source file. We also added some tripod helper objects to visualize the local axis rotation of each bone object. You can ignore the tripod helper objects or delete them if you find the scene to be cluttered.

(
*
File: ponytail_skeleton_step01.max
*
)

[Image: /docs/static/attachments/25521849]

*
Pic2: Image showing the pony tail hierarchy, with a custom made tripod helper objects
*

-
Create a poly cylinder
**

**
with enough subdivision for good deformation. This is the pony tail geometry which will be added a "Skin" modifier in a later step.

(
*
File: ponytail_skeleton_step02.max
*
)

[Image: /docs/static/attachments/25521850]

*
Pic3: Shown are the creation parameters for the dummy pony tail geometry. Nothing to show off your amazing modeling skills ;-) !
*

##
II. Creating a simplified target (primary) skeleton to be extended by the pony tail (secondary) skeleton:

-
We want to keep our primary skeleton as abstract as possible. Create 3 objects: a root, a pelvis and a head bone object. Rename the bone objects and orient them to the sample scene / image shown below. We created some tripod helper objects for you to see their final local orientation.

The root of any skinned hierarchy must match the default world orientation. (Go to Top View, the positive X-axis must point to the right, the positive Y-axis must point to the top.)
[Image: /docs/static/attachments/24150908]

[Image: /docs/static/attachments/24150910]

*
Pic4a & b: Root matching the default world orientation before export
*

If the orientation of your skinned object does not meet CRYENGINE requirements, it will not complain, until you try to load it as a CHR in Character Tool.

-
 Create a triangle mesh object. This is the dummy triangle object for a CRYENGINE *.CHR file. This one holds all hierarchy data of the base skeleton.

(
*
File: ponytail_skeleton_step03.max
*
)

[Image: /docs/static/attachments/24004015]

*
Pic5: Primary / base skeleton for the pony tail to be attached to. The dummy triangle mesh is also shown
*

-
Go to the Modify Panel and add a "Skin" modifier to the dummy triangle mesh and include just the "pelvis" bone to its bone list.

(
*
File: ponytail_skeleton_step03.max
*
)

*
[Image: /docs/static/attachments/24004026]

Pic6: Skinned triangle dummy mesh as CRYENGINE CHR object

*
*

*

-
 Export the triangle dummy mesh, we gave it the name "ponytail_SKEL" as a CRYENGINE *.CHR file type.

*
(File: ponytail_skeleton_step03.max or ponytail_skeleton_CHR_export.max)

*
*
*
[Image: /docs/static/attachments/24004029]

Pic7: Export the base skeleton to a *.CHR file

*
*
*

*

-
We made a simple loop animation for the primary skeleton to drive the pony tail physics. Refer to Autodesk 3ds Max help & tutorials for how to make animations.

*
(
*
File: ponytail_skeleton_CHR_export.max)

*

*
[Image: /docs/static/attachments/24004035]

*
Pic8: Export a "default" animation to *.I_CAF / *.CAF file
*

*

*
In the next steps we will switch back to the pony tail and make it export-ready.

##
III. Add Skin modifier to the poly cylinder and skin the pony tail bone hierarchy to it

-
Open the File
*
 ponytail_skeleton_step02.max.
*

-
Select the cylinder / pony tail mesh and add a Skin modifier. Add the 7 pony tail bones to bone list of its "Skin" modifier.

[Image: /docs/static/attachments/24004030]

*
Pic9: Skin the "pony tail" / poly cylinder mesh
*

-
Tweak the skin weights by moving the Envelopes and their radii or use 3ds Max 2016+ "Voxel" / "Heat Map" feature in the Skin modifier to make a quick skin weights distribution.

(
*
File: ponytail_skeleton_step04.max)
*

[Image: /docs/static/attachments/24004031]

*
Pic10: Skin Weights
*

-
We will merge the base skeleton scene into our pony tail scene and link the secondary skeleton to the base skeleton. This is how you normally work when you build a secondary skeleton to extend your base, keeping both skeletons in two files and not mixing them. Open the
*
File: ponytail_skeleton_step04.max
*
 and "Merge" the base skeleton from
*
File: ponytail_skeleton_CHR_export.max
*
 to it:

[Image: /docs/static/attachments/24004032]

*
Pic
*
11
*
: Use Merge and just overwrite everything if you are prompted
*

-
Since we use a "Skin Attachment" for the pony tail geometry, we must somehow tell CRYENGINE where the extending skeleton is going to be attached to the base CHR skeleton:

Link up the pony tail root joint to the attachment node of the base skeleton:

[Image: /docs/static/attachments/24004033]

*
Pic12: Link the two hierarchies together
*

[Image: /docs/static/attachments/24150939]

*
Pic13: Schematic view of the two linked hierarchies
*

-
Export the pony tail mesh to a CRYENGINE *.SKIN file with the following settings:

(
*
File: ponytail_skeleton_SKIN_export.max
*
)

[Image: /docs/static/attachments/24004034]

*
Pic14: Export File Type must be set to *.SKIN
*

This concludes this 3ds Max section. The next steps will be how to import the assets into CRYENGINE's Character Tool.

[/docs/static/engines/cryengine-5/categories/23756816/pages/44959430](
[Image: /docs/static/attachments/24151097]
)

[#tutorial-files](
Tutorial Files
)
[#prerequisites-for-this-tutorial](
Prerequisites for this Tutorial
)
[#setting-up-the-3ds-max-scene-and-exporting-to-cryengine](
Setting Up the 3ds Max Scene and Exporting to CRYENGINE
)
