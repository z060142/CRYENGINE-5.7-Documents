# Jiggle Bones - Skeleton Hierarchy Setup - Maya

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/23310603
- Page ID: 23310603
- Breadcrumb: Tutorials > Animation and Characters > Character Tool and Pipeline > Tutorial - Jiggle Bones > Jiggle Bones - Skeleton Hierarchy Setup - Maya
- Parent: Tutorial - Jiggle Bones

## Content

##
Overview

##
Tutorial Files

If you want some files for reference
, please download and unzip the tutorial files as described on
**
[/docs/static/engines/cryengine-5/categories/23756816/pages/44959301](
this page
)
**
.

##
Prerequisites for this Tutorial

Before you continue with this tutorial, make sure to have read and understood the following

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
Setting Up the Maya Scene

The goal of this section is to create a poly cylinder and a dummy triangle poly mesh and two joint hierarchies in Maya.

The poly cylinder acts as the pony tail geometry which is bound to a joint chain. The other joint hierarchy acts as a simplified character skeleton where the first joint chain with pony tail polymesh will be attached to. In the end, we have a
**
secondary
**

pony tail joint chain

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
Maya scene file location:

Set up your Maya scene and save it to an appropriate directory, for example YOUR_PROJECT_FOLDER\Assets\Objects\current_tutorial. Be sure that the folder containing the Maya scene and exported files for CRYENGINE is a
**
sub-folder of your project folder
**
. In our case, we saved the Maya scene files in this directory:

**
YOUR_PROJECT_FOLDER\Assets\Objects\jigglebone_tutorial_maya
**

##
Create the joint hierarchies and smooth skin two geometry object to them:

For this tutorial we will create a poly cylinder skinned to a joint chain. This joint chain can be used for
**
two very distinct use cases
**
:

-
**
loosely hanging down, bendy joint chain:
**

- a long pony tail coming from the back of a head,

- a rubber hose or anything rope-like,

- iron chain with several links,

etc.

-> joints that bends/rotate during simulation

-
**
a cartoony, stretching joint chain:
**

- an antenna sticking out of a robot's head or insect,

- tied-up hair that is short,

- a bouquet of flowers,

etc.

-> joints that stretch/translate during simulation

We assume you to have at least some experience with Maya. We will post some images showing the interim steps and the final resulting scene.

##
I. Creating the pony tail joint hierarchy and a poly cylinder:

-
Let's start by creating the secondary skeleton, the pony tail joints. Use Maya's "Joint Tool" to make a straight joint chain pointing downwards (world negative Y). We chose to use 8 joints, the last joint will not be accounted for deformation, so you will have 7 joints bound to the skinCluster node later. Rename the joints for a clean hierarchy.

-
Re-orient the joint "Local Rotation Axes" with Maya's
**
"
**
Orient Joint
**
"
**
 tool.

(
*
File: ponytail_skeleton_start.ma
*
)

[Image: /docs/static/attachments/25501476]

*
Pic1: A clean named joint hierarchy with all local axis correctly orientated
*

-
Make sure your "Joint Orient" attribute is all zero'd out, except the very first joint. That one has a -90 deg value in its Z-Axis.

[Image: /docs/static/attachments/25501477]

*
Pic2: Image showing the parent joint of the pony tail hierarchy and its "Joint Orient" attribute
*

-
Create a poly cylinder
**

**
with enough subdivision for good deformation. This is the pony tail geometry which will be smooth bind to the pony tail skeleton and later be exported as the CRYENGINE *.SKIN file.

(
*
File: ponytail_skeleton_step01.ma
*
)

[Image: /docs/static/attachments/25501478]

*
Pic3: Shown are the creation parameters for the dummy pony tail geometry. Nothing to show off your amazing modeling skills ;-) !
*

##
II. Creating a simplified target (primary) skeleton to link the pony tail (secondary) skeleton to:

-
For the primary joint hierarchy, create a new joint hierarchy with Maya's "Joint Tool". We want to keep this primary skeleton as abstract as possible.

A root, a pelvis and the animated head joint will be created in this section. Also, we will add a "zero'd out" joint as the pony tail parent by duplicating the pony tail parent joint and re-parenting to itself. For clarity's sake, we hid the pony tail skeleton and mesh.

(
*
File: ponytail_skeleton_step02.ma
*
)

-
As mentioned before with the pony tail joint hierarchy, you should rename the joints and check them for a proper local axis rotation. Display the joints Local Rotation Axis and use the "Orient Joint" tool.

[Image: /docs/static/attachments/25501479]

*
Pic4: Image showing the orientation of the primary skeleton root joint and the attachment joint of the pony tail
*

-
Create a triangle mesh object. This is the dummy triangle object for a CRYENGINE *.CHR file. This one holds all hierarchy data of the base skeleton.

(
*
File:  ponytail_skeleton_step03.ma
*
)

*
[Image: /docs/static/attachments/25501480]

Pic5: Primary skeleton and its to be bound geometry, a dummy triangle

*
*

*

##
III. Smooth Bind the poly geometries to its skeletons:

-
With Maya's "Bind Skin" tool, smooth bind the the poly cylinder mesh to the (secondary) pony tail skeleton: First select the poly cylinder and then the pony tail joint no. 1 till no. 7 and choose Maya's "Bind Skin" Tool from the "Skin" menu from the Rigging Menu set (in Maya press F-3).

(
*
File: ponytail_skeleton_step04.ma
*
)

[Image: /docs/static/attachments/25501481]

*
Pic6: Smooth bind the pony tail geometry
*

-
Before we bind the triangle dummy to the primary character skeleton, we duplicate the skeleton first. Select the target skeleton root joint and press
**
CTRL-D
**
 to duplicate.

Later we we will parent the pony tail hierarchy to this duplicated one. You may ask why we do this. That is because of the requirement in Maya to CRYENGINE export for an extending *.SKIN file to a base *.CHR skeleton. In Maya, you must include at least the following joints of your base/primary character's skeleton you want to extend to your secondary extending skeleton:

What joints to include in your extending/secondary skeleton
**
1. The root skin/influence joint which is in your skinCluster, mostly the first "deforming" skeleton joint, e.g. the pelvis of a humanoid character.
**

**
2. The target joint of your primary/base skeleton which you want your extending/secondary skeleton be attached to.
**

**
3. A root joint which meets the CRYENGINE requirement of being a zero'd out root node.: x-axis pointing to the right, y-axis pointing to the top when looked from a top viewport.
**

Or you just include the complete base/primary skeleton hierarchy you want to extend.

[Image: /docs/static/attachments/25501482]

*
Pic7: Duplicate the primary skeleton for parenting the pony tail skeleton to it
*

*

*

-
Parent the pony tail skeleton to the last joint of the duplicated hierarchy.

[Image: /docs/static/attachments/25501483]

*
Pic8: Include the primary/base skeleton into the (secondary) skeleton of the pony tail
*

-
This is how the two joint hierarchies have to look like for export:

[Image: /docs/static/attachments/25501484]

*
Pic9: Remember that we have duplicate names issue for root joints of the primary and secondary skeleton. We must swap their names each time we export or put the them in two Maya scene files and export from there:
*

-
Before we go to the export steps, we still have to finish the base *.chr skeleton. The primary skeleton needs to be bound to the first deforming joint of the hierarchy: here it is the second joint in hierarchy, the pelvis joint. Select the triangle dummy mesh and the pelvis joint and use Maya's "Bind Skin" tool.

[Image: /docs/static/attachments/25501485]

*
Pic10: Bind triangle dummy to target primary/base skeleton, the CHR skeleton:
*

##
IV. Add some animation to the primary skeleton you want to extend:

We want to animate the "head" joint of the base skeleton, so that later when we add the physics procedural/secondary animation, it is derived from this (head) joint movement. Press the
**
Play
**
 button in Maya to see the results

(
*
File: ponytail_skeleton_step06.ma
*
)

*
[Image: /docs/static/attachments/25501486]

Pic11:
*
Animated primary skeleton that will drive the pony tail physics later in CRYENGINE's Character Tool
*
*

##
Prepare the Maya Scene to export to CRYENGINE

The goal of this section is to show you how to create the necessary nodes for CRYENGINE *.chr, *.skin & an *.i_caf animation file export.

(
*
File: ponytail_skeleton_final.ma
*
)

[Image: /docs/static/attachments/25501487]

*
Pic12: This is what the final hierarchy looks like
*

##
Create the cryExportNodes for the CHR base skeleton and the SKIN pony tail extension:

In this section we need to create the cryExportNodes, materials, etc. for the Maya to CRYENGINE Export and create the *.chr and the *.skin file in the final location of any CRYENGINE asset.

-
For the base CHR skeleton, create the
**
cryExportNodes
**
 by using the "Tools" icon from the installed Crytek shelf.

[Image: /docs/static/attachments/25501488]

*
Pic13: Set up the cryExportNode of the base character, in our case called "ponytail_SKEL"
*

-
For the the pony tail geometry, the poly cylinder, we will export it as *.SKIN attachment to CRYENGINE's Character Tool. Add the cryExportNode according to the image below:

[Image: /docs/static/attachments/25501489]

*
Pic14: Set up the cryExportNode of the extending pony tail mesh, we name it "ponytail_MSH":
*

##
Material setup for CRYENGINE in Maya

Use the standard workflow to create a Material Group (a Maya Set) with sub shaders parented to it. We will define some random colors to a standard Blinn shader and add it to a CRYENGINE Material group. Don't forget to export the material to a *.mtl file in your project folder.

[Image: /docs/static/attachments/25501490]

*
Pic15: Overview of a standard Blinn material applied to a scene ready for CRYENGINE export
*

##
Split the CHR and SKIN cryExportNode into Two Maya Scene Files

We still have the name clashing issue for the root joint of the primary base skeleton (character CHR file) and the secondary extending skeleton (pony tail SKIN file).

[Image: /docs/static/attachments/25501491]

*
Pic16: When we try to give both nodes the same name, Maya automatically renames one of them, because of clashing names.
*

To solve this we will remove the duplicates and save each cryExportNode and its skeleton hierarchy to a new file, so we end up with two files harboring a CHR and a SKIN cryExportNode.

##
I. CHR base skeleton scene

Start by loading the "
**
ponytail_skeleton_final.ma
**
" file. There we we remove all pony tail SKIN related nodes and save the scene to a new file. From here we export the CHR file and also the "default" animations show below. Use the
**
Crytek shelf -> Export
**
 button to export your *.CHR file.

*
[Image: /docs/static/attachments/25501492]

Pic17: cryExportNode hierarchy of the animated primary skeleton CHR
*

##
II. SKIN attachment scene

We load up the "
**
ponytail_skeleton_final.ma
**
" file again. Then we remove all the base skeleton related nodes and save the scene to a new file. From here we export the *.SKIN file. Use
**
Crytek shelf -> Export
**
to export your *.SKIN file.

*

*
*
[Image: /docs/static/attachments/25501494]

Pic18: CryExportNode hierarchy for the SKIN attachment
*

*

*

This concludes the Maya section. In the next section we will start CRYENGINE's Character Tool to set up the pony tail.

[/docs/static/engines/cryengine-5/categories/23756816/pages/44959430](
[Image: /docs/static/attachments/24151097]
)

[#tutorial-files](
Tutorial Files
)
[#prerequisites-for-this-tutorial](
Prerequisites for this Tutorial
)
[#setting-up-the-maya-scene](
Setting Up the Maya Scene
)
[#prepare-the-maya-scene-to-export-to-cryengine](
Prepare the Maya Scene to export to CRYENGINE
)
