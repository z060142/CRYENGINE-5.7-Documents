# Vegetation 01 Grass (Patch) Maya

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/24285887
- Page ID: 24285887
- Breadcrumb: Tutorials > Game and Level Design > Vegetation Tutorials > Tutorial - Vegetation Asset Creation > Vegetation 01 Grass (Patch) > Vegetation 01 Grass (Patch) Maya
- Parent: Vegetation 01 Grass (Patch)

## Content

##
Overview

This tutorial takes you through the process of creating the simplest vegetation asset; grass patches. It covers the basics of the vegetation shader parameters and introduces you to the Vegetation Tool in CRYENGINE. Grass patches is the former method that we used to make grass assets for the ENGINE. While this method is still valid and worth knowing our preferred and current method for creating grass is to use the Merged Mesh (MM) technology.

[Image: /docs/static/attachments/26509313]

*
Pic1: Finished scene using grass patches.
*

The below example (
*
Pic2
*
) depicts the creation of grass patches using the vegetation tool. The one on the right is shown in a highlighted planes view.

[Image: /docs/static/attachments/26509314]

*
Pic2: Grass objects in normal and highlighted planes view.
*

##
Tutorial Files

Source Maya scene with exported CRYENGINE files:

[/docs/static/attachments/25523834](
GameSDK_vegtut01_files.zip
)

##
Prerequisites for this Tutorial

Before you continue with this tutorial, make sure to have read and understood the following topics:

-

-
[/docs/static/engines/cryengine-5/categories/23756816/pages/44963475](
How to Install CryMayaTools
)

-
[/docs/static/engines/cryengine-5/categories/23756816/pages/23308292](
The Basic CRYENGINE Maya Workflow
)

-
[/docs/static/engines/cryengine-5/categories/23756816/pages/13205569](
CRYENGINE Exporter
)

-
[/docs/static/engines/cryengine-5/categories/23756816/pages/23308289](
Maya Unit Scale to Match up With CRYENGINE Unit System
)

##
Helpful Information

Keep the following things in mind while working on your asset:

-
Usually, the merged mesh and grass patches versions does not require a physics proxy.

-
If you enable the 'grass' flag in the shader generation parameters, then you do not need a normalmap (optimization).

-
Each grass patch placed has its own set of drawcalls. Merged mesh grass does not - it batches together chunks.

-
Do not exceed a diameter of 8 meters for large grass patches. This size has proved to provide a good balance between performance and ground coverage.

-
Use as few polygons as possible while making a repeating asset such as grass. It will improve performance significantly.

-
Add LOD's to the asset. Reduce the polygon count by 50% (if possible) to each LOD step.

##
Initial Maya Setup

For this tutorial the asset has been created in the following directory:

-
`
<
`
*
Your_Project
*
>\Assets\
`
Objects\tutorial\vegetation\01\grass_patch\
`

-
To begin with, save the Maya scene to this location.

-
All exported assets will also be saved in this directory.

-
Some of the textures used in this tutorial are derived from an existing asset in the GameSDK folder. In this case, we point you to the directory where they are stored later in this tutorial.

##
Material

Initially, we need to prepare the material that will be applied to the object. This enables us to give a visual reference to the texture that you are using when modeling or shaping the geometry planes for the grass patch.
For the individual grass and the grass patches,
you only require one material SubID for the visible portion of the mesh. Also, a physics proxy is not required on the object as the player is supposed to pass straight through the object without hindrance.

You can add a proxy to the object, but it is not recommended for grass patches.
Under the Crytek shelf you installed, click the
**
MAT.ED
**
 tab. In the
**
Material Groups
**
 window, create a new Material Group and add a standard Phong shader to this Material Group. To create a new shader, open Maya's
**
HyperShade
**
 to create a standard Phong shader. It does not matter if you choose a Phong, Blinn, or Lambert shader. You still need to set up the vegetation material in the
**
Sandbox Material Editor
**
 later.

[Image: /docs/static/attachments/24157007]

*
Pic3: Creating a new Material Group.
*

##
Export the Material

After you have added the new Material Group with one sub-material, you can open up the Maya and export an *.MTL material file using the CRYENGINE Exporter.

[Image: /docs/static/attachments/24157008]

*
Pic4: Exporting the generated material files.
*

This will be saved into the same directory as the Maya source scene:

-
`
<
`
*
Your_Project
*
>\Assets\
`
Objects\tutorial\vegetation\01\grass_patch\
`
**
tutorial_grass_patch.mtl
**
**

**

##
Object Setup

For a grass patch, we define the object by a series of simple planes rotated in random directions and with variations in scale to achieve a dense look with minimal geometry. The idea is to make it look solid from every direction, i.e. in the X, Y and Z.

-
Create a polygon plane and apply the material
**
tutorial_grass_patch
**
 to it.

-
Name the polygon object
**
grass_patch.
**

-
Use Maya modeling tools to split edges, so you roughly get the shape shown below in
*
Pic5.
*

-
Open the
**
UV Editor
**
 window with the geometry selected to adjust the UV of the single grass patch object to only fit around on the texture.

[Image: /docs/static/attachments/24157009]

*
Pic5: Modified poly plane with UVs edited
*

-
Using this setup, duplicate the polygons and distribute them around the area you would like the patch to cover. Apply random rotation and scale to the patch to break up the uniformity of the object (be careful to not over modify and start to stretch the textures!)

-
Try to end up with a rough hexagon shape for the entire patch. This works the best in most situations.

-
Once you have finished the geometry distribution
**
Combine
**
 all individual planes together into the one base object and
**
Delete History
**
 (renamed grass_patch to tutorial_grass_patch_big).

[Image: /docs/static/attachments/24157010]

*
Pic6: Randomly distributed grass patch objects combined to one single mesh.
*

##
Tweaking the Pivot Location

Make sure that the pivot of the object is roughly in the center and slightly up from the absolute bottom of the object. This slight vertical offset of the pivot allows the geometry to be slightly sunken into the floor which is useful in aligning to terrain function in the Vegetation tool. When used in this way, it will average out (as best it can) to fit with the variation in terrain height. This helps to avoid a gap underneath the grass patch and prevents it floating in space.

Make sure you do not set the pivot too high, otherwise you will lose the bottom of the geometry into the terrain.

[Image: /docs/static/attachments/24157011]

*
Pic7: Pivot location, hit the Insert key to offset any pivots in Maya and keep X key pressed to snap to the grid.
*

[/docs/static/engines/cryengine-5/categories/23756816/pages/24285886](
Apply Vertex Color (to control material Vertex Deformation)
)
This is an optional feature that can be applied to the asset. It is not required unless you use the asset with a specific material setup, such as Vertex Deformation. Without the vertex coloring in the asset, the simplified movement you get when using vertex deformation is
**
applied across the entire geometry
**
.

By default, the vertex color of the asset is white (full movement), but when you apply black to the base vertices (where the grass will be rooted to the floor), then only the tips of the grass will move (because they are colored white). This gives a much more realistic and believable looking asset.

Unlike the bending parameter that can be applied inside the vegetation tool and that automatically fixes the base of the grass to the floor. Vertex color is used to control the movement when you apply the movement via the vertex deformation within the material.

To modify any vertex color in your geometry, press
**
F2
**
 to go to the Maya's Modeling menu. Under
**
Mesh Display
**
 ->
**
Apply Color
**
 or
**
Paint Vertex Color Tool
**
, you add vertex colors. Instead of painting, it is easier to just select the bottom vertices and give them a black color which is interpreted as non-moving vertices in the vegetation tool settings later. Redo with white color for the top vertices. This will let them move freely.

[Image: /docs/static/attachments/24157012]

*
Pic8:
*
*
Applying the vertex colors.
*

When we progress to the CRYENGINE portion of this tutorial we will continue with the use cases for vertex color within the asset. For now, continue on to create the rest of the asset.

##
Add Some LOD's to the Grass

Even though this grass object is a very simple geometry with a total of 600+ polygons, it still makes sense to add LOD's to the object - so we can lose some of the extra polygons at distance.

##
Preparing the Maya scene to export

If you are familiar with the 3ds Max to CRYENGINE workflow, you will notice that for the export from Maya, we must always:

-
Re-order nodes

-
Create empty groups

-
Parent them in the right order

-
Give them correct names

-
Orient each group, so it matches CRYENGINE requirements.
When it comes to adding LODs it becomes even a bit more complicated. These are the rules:

-

-
Create one cryExportNode using the Crytek shelf tool icons to hold the grass patch.

-
Keep each LOD mesh object(s) under an LOD group node following this naming convention:

-
Use the "
**
_lod#
**
" prefix for the LOD group nodes. Replace the #-symbol with the LOD number. The word "LOD" is not case-sensitive, you can mix the upper and lower cases as you wish. But you must include an underscore "_" symbol as the first character, followed by the word "lod" followed by a number. Add the suffix "_group" to finalize the name: e.g. _lod1_grass_patch_group

-
Parent the lower LODs under the full render mesh ( you can say, this is the "lod0" mesh ).

-
Re-orient the all group nodes which will get child mesh objects to match CRYENGINE requirement: Go to a Top view, any group positive X-Axis must point to the right, the positive Y-Axis must point to the top.
This will result into an exportable hierarchy shown in the below image:

[Image: /docs/static/attachments/24157013]

*
Pic9: LOD group nodes for the meshes
*
.

To fill in the empty LOD group, use any means you have in Maya or external programs to reduce the different LOD mesh complexity. You can simply delete some grass patch faces or you could also use the
**
Mesh
**
 ->
**
Reduce
**
 tool to let Maya do the work. It's up to you. There is a guideline however, if you want to follow it:

-
Try to reduce the polygon count by approximately 50% per LOD step (if possible) while still preserving the overall shape
Group the reduced LOD meshes under their respective group nodes, until you get this:

[Image: /docs/static/attachments/24157014]

*
Pic10: Grouped LOD group nodes
*
.

##
Export the Geometry

Since we already did the preparations of our export scene to include LOD groups, we only need to click the
**
Export
**
 button to export the grass patch as *.CGF file. Click on the cryExportNode and go to the
**
Attribute Editor
**
 if you need to re-evaluate the export settings shown below:

[Image: /docs/static/attachments/24157015]

*
Pic11: Exporting the geometry and its settings.
*

##
Continue to CRYENGINE

We have now finished the setup for the Maya portion of the tutorial. To continue, move onto the next page where we configure the material and use the Vegetation Tool to place down some grass assets.

[/docs/static/engines/cryengine-5/categories/23756816/pages/24285888](
Vegetation 01 Grass (Patch) CRYENGINE
)

[#tutorial-files](
Tutorial Files
)
[#prerequisites-for-this-tutorial](
Prerequisites for this Tutorial
)
[#helpful-information](
Helpful Information
)
[#initial-maya-setup](
Initial Maya Setup
)
[#material](
Material
)
[#object-setup](
Object Setup
)
[#continue-to-cryengine](
Continue to CRYENGINE
)
