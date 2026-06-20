# Basic Asset Setup and Export - 3ds Max

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/25528753
- Page ID: 25528753
- Breadcrumb: Asset Prep (External) > Asset Exporting Overview > Preparing Assets for CRYENGINE > Basic Asset Setup and Export - 3ds Max
- Parent: Preparing Assets for CRYENGINE

## Content

##
Overview

In the following documentation you'll find how to set up a mesh with a the correct shader in 3ds Max and how to export this asset. Once you're working in the engine, this document will explain how to assign the materials, textures and what to look out for. This document will also include a link for how to use the Physically Based Shaders correctly. Please read this carefully since the whole game and look will be based upon this concept.

![Image](https://www.cryengine.com/docs/static/attachments/25499852)

##
Tutorial Files

Source 3ds Max scene with exported CRYENGINE files:

**
[material_sphere_max.zip](/docs/static/attachments/25501533)
**

##
Helpful Information

*

*
Make sure to keep the following things in mind while you work on your asset:

-
The pivot of the object in 3ds Max corresponds to the pivot of the object in the engine.

-
Make sure that the object has smoothing groups assigned to it. The engine will assign a smoothing group for any polygons that lack one, which will usually result in undesirable visual results.

-
Make sure that the object has UVW mapping.

-
You are free to keep any modifier stacks on the object as they won't affect exporting and the object will appear in the engine as you see it in 3ds Max.

-
The more polygons the object has, the longer it will take to be exported; although, the exporting time is generally very quick. (Less than 1 second).

-
The object should either be an editable poly or an editable mesh.

-
CRYENGINE uses the metric system for measuring distances so this should be adopted in your software as well.

##
Initial Setup

For this tutorial the asset has been created in the following folder:

-
`
<GameFolder>\Objects\tutorial\material_sphere
`
To begin with, save the 3ds Max scene to this location.

All exported assets will also be saved in this folder.

Before working with the scene we have to make sure that we have the right setup. For a better overview we are setting up some layers.

It's very easy to set up a layer in 3ds Max and it will help to keep the scene clean and export the right objects from it. It will also help to hide things that we don't want to see (like proxies, test geometry, etc).

In 3ds Max click on the upper tab on the icon named
**
Manage Layers
**
. A new window will open, the
**
Layer Editor
**
. By default you'll have the default layer there. This layer can't be removed so you have to leave it in and add the other layers. To add another layer,
in the Layer Editor,
click on the
**
Create New Layer
**
 icon. To change the name of it, right click on it and scroll to
**
Rename Layer
**
.

Besides the default layer, y
ou should have a minimum of
three more layers in the Layer Editor:

-
lod

-
mesh

-
proxy
*
Simple layer structure in 3ds Max scene

![Image](https://www.cryengine.com/docs/static/attachments/25499853)
*

Additionally we should have more layers for each LOD step (if available) to keep the scene clean

##
Mesh setup in 3ds Max

Load the tutorial file, or open up your own asset and save your 3ds Max scene to this location.

-
`
<GameFolder>\Objects\tutorial\material_sphere
`

##
Asset components

The scene contains the material sphere mesh, 2 LOD´s and one physics proxy. We want so show the process of exporting a games asset into the engine. In most cases an assets will have more than one material ID, it will use LOD´s (Level of Detail meshes) and a physics proxy mesh for the hit detection or the ability to interact with the player or game environment.

-
Main Mesh (LOD0)

-
LOD1

-
LOD2

-
Physics Proxy
*
Overview of the nodes that make up a CRYENGINE asset
*

![Image](https://www.cryengine.com/docs/static/attachments/25499854)

In the final scene all meshes should have the same pivot point all all sitting at (0,0,0) overlayed on top of each other:

![Image](https://www.cryengine.com/docs/static/attachments/25499865)

It's possible to export an asset without this advanced setup, but this is not recommended. We will go over this in the Export to CRYENGINE section in this tutorial later on.

##
LOD Geometry

For LODs we use a special naming convention. We prefix our LODs with
**
$LOD
**
 as follows:

-
$LOD1_my_object

-
$LOD2_my_object

-
$LOD3_my_object

-
etc.
CRYENGINE will automatically handle these meshes as LODs because of the numbering system within the name, it will use the required mesh at the appropriate distance.

As a rule of thumb, we generally aim to reduce the polygon count on each LOD step by approx 50%.

##
Proxy Geometry

Practically all objects exported to the engine should contain a physics proxy mesh. There are very few cases where this isn't required (distant background geometry the player will never get to, or small pebbles/rocks that are so small they wouldn't require it).

Again the reason why we have separate geometry is because we want to simplify the mesh as much as possible. The less polygons within the physics proxy the more efficiently the physics system can use the object. So using the visible mesh as a proxy (with typically a high poly count) wouldn't be very efficient in the physics system. So that is why we separate it out into its own geometry.

To visualize the physics system in the engine, either use the CVar
**
p_draw_helpers = 1
**
, or when in-game press
**
F10
**
 to enable the physics debug mode.
Below you can see the Simplified Physics geometry (red) compared to the main visible mesh (note the underlying higher poly visible mesh blue/grey)

![Image](https://www.cryengine.com/docs/static/attachments/25499865)

##
Linking nodes in 3ds Max

The next step is to link the nodes to the Root Mesh in this case the Material sphere mesh. Go to the schematic view in 3ds Max and select both LODs. Go to the link tool icon and link these two LODs to the main mesh (the material sphere mesh).

![Image](https://www.cryengine.com/docs/static/attachments/25499866)

The last thing we have to do is to link the physics proxy to the main mesh. Still in the schematic view, select the
**
collision_mesh
**
 node and link this to the root material sphere mesh as well.

![Image](https://www.cryengine.com/docs/static/attachments/25499868)

To link correctly, drag from the child nodes to the parent to set the hierarchy correctly.
Now we are ready to set up our materials.

##
Material setup in 3ds Max

For this object we need a Multi/Sub-Object material with 3 SubID´s: the first will be our Proxy material, the second one will be the dark grey plastic for the outside, the third one for the light blue plastic in the middle and the platform.

-
ID1: Proxy

-
ID2: Outside (grey)

-
ID3: Inside (Blue)
It's advisable to create all materials as Multi/Sub-Object materials, as this makes life easier down the line when you want to add additional SubIDs to the meshes.
*
Material SubID setup
*

![Image](https://www.cryengine.com/docs/static/attachments/25499870)

##
Configure the Multi/Sub-Object Material

Open the Material Editor in 3ds Max.

Select a fresh material, click the Standard slot, and then change the material type to Multi/Sub-Object. Set the sub-material count to 3 (amount required for this asset). The engine supports up to 32 sub-materials.

*
Converting the material into a Multi/Sub-Object Material
*

![Image](https://www.cryengine.com/docs/static/attachments/25505554)

The more sub-materials the object uses, the more drawcalls it will use, reducing performance. Therefore, it's best to find ways to keep the sub-material count as low as possible.
Make sure that all materials'
**
SubIDs
**
 are set as
**
Standard
**
 (not Multi/Sub-Object) and give the material and all sub-materials a specific name that reflects its purpose (e.g.: proxy). When you create the material file, these names will be transferred to CRYENGINE.

Name the material "material_sphere".

When exporting the material (*.mtl), it must be named exactly as
the material assigned to the mesh in 3ds Max, because CRYENGINE is expecting this material name within the *.cgf. If it doesn't match, you'll get ReplaceMe material on the object when you drag it into the scene.
Please make sure that you delete unused slots since these will increase the file size and also decrease the performance in game since it needs to process more data.

##
Sub-Material Setup (Overview)

Open each sub-material and in the
**
Shader Basic Parameters
**
 section change the shader type to
**
Crytek Shader
**
. You should only use the Crytek Shader for the objects. The other shader types will not work correctly when exported.

![Image](https://www.cryengine.com/docs/static/attachments/25499873)

You'll notice a new drop-down list next to
**
Physicalization
**
. This list contains presets for the way the material interacts in the engine. For now, you only need to worry about two of these:
**
Default
**
 and
**
Physical Proxy (NoDraw)
**
.

*

![Image](https://www.cryengine.com/docs/static/attachments/25505556)
*

-
**
Default
**
 is a normal material. You'll use this for the material's "visible" SubIDs. It has no special properties.

-
**
Physical proxy (NoDraw)
**
 is a special material property that you use for hiding the proxy geometry. This is to be used in conjunction with the physicalized checkbox.

##
SubID 1 - Physical Proxy (Collision)

The first sub-material should be a physics proxy material for the collision mesh.

-
Go to this sub-material and change the physicalization type to Physical Proxy (NoDraw). This will set the geometry to not be rendered in the engine.

-
Tick the
**
Physicalize
**
 checkbox. This will physicalize the material in the engine.
If this box is not checked, the object will not be physicalized and it will not physically interact with anything in the game world. If the object has a separate physics proxy, the rendered geometry should not be physicalized.
*
Physicalizing the proxy material SubID
*

![Image](https://www.cryengine.com/docs/static/attachments/25499876)

A workflow tip is to color the proxy geometry red with an opacity of 50%. This helps identify the proxy geometry apart from the visible geometry. It's not required but helpful when working within a scene.

Please remember to create your Physical Proxy to use (if possible) primitive geometry and in cases where you can't achieve it with primitives, please use very low geometry and be smart about it (for example if your character won't come in contact with the top of a tall water tower, no proxy is required there, so you could skip adding one there).

Assets can support multiple proxy geometries as well, which you can use to break your model down into simpler primitive shapes. Taking this model as an example, we could break this object down into 3 separate proxies:

-
a short fat cylinder for the base

-
a thin cylinder for the stand

-
a sphere for the main ball
Make sure that each of these proxies have their pivot point matching that of the main mesh (coordinates 0,0,0).

For more information on the physics setup for assets and engine debugging tools please see
**
[here](../../../Physics.md)
.
**

##
SubID 2 & 3 - Visible meshes

The following SubIDs in this material are for the two visible meshes: the grey outer shell, and the inner blue surface.

The material setup is slightly different here, where we use the Crytek Shader as before, then select
**
Default
**
 from the drop down list. Note that this time we are
**
not checking the box
**
 for
**
Physicalize
**
 here, as this option is for the collision proxy only.

![Image](https://www.cryengine.com/docs/static/attachments/25499877)

##
Exporting to Engine - Model

Before exporting the asset to CRYENGINE we need to double-check we saved it in the right folder and with the right naming conventions. For the correct workflow save all the final textures and cleaned up 3ds Max file into the same folder.

Your exported files (*.cgf,
*.
cga, etc.) will be exported to the same folder as the *.max scene.
To export the asset, click on the
**
Utilities
**
 Button (the icon with the hammer) and then finally click on
**
CRYENGINE Exporter
**
.

If you don´t have the
CRYENGINE
Exporter in your Utilities list, please read
**
[here](/docs/static/engines/cryengine-5/categories/23756816)
**
 how to install the required CRYENGINE tools and exporters.

In the main viewport window select your mesh, in this case the material_sphere mesh and click
**
Add Selected
**
 in the
**
CRYENGINE Exporter
**
 and it will add the asset to the export list.

![Image](https://www.cryengine.com/docs/static/attachments/25499939)

Please make sure that the checkbox
**
Export File per Node
**
 is checked, since if not it will export all the nodes in the scene as one file (example: if you have a building made of
different pieces &
you want to export them separately and not as one big object, make sure that
**
Export File per Node
**
 is checked).

Finally click
**
Export Nodes
**
 to export out the items you added to the export list earlier (material_sphere). The exporter will automatically put the *.cfg file in the same folder location as the scene was saved in.

After that is done we still need to export the material since the only thing that was exported is the geometry but not the material set up.

##
Exporting to Engine - Material

In the
CRYENGINE
exporter there is a
**
Material
**
 section. This is where we will create our material. Make sure that you're currently at the parent or root level of the material, not inside a SubID.

Select your Multi/Sub-Object material in the 3ds Max Material Editor and in the CRYENGINE exporter click on
**
Create Material
**
.

If there isn't an instance of CRYENGINE Sandbox running, it will automatically launch for you.
*
Exporting the selected material from 3ds Max
*

![Image](https://www.cryengine.com/docs/static/attachments/25499940)

The Material Editor will open up along with a
**
Save As
**
 dialog window. You will be asked to enter a filename for the new *.mtl file.

Make sure that the name you enter
**
is exactly the same
**
 as the name of the material in 3ds Max. Conveniently the material will be exported to the same folder the mesh exported to. Please keep your model *.cgf and your material *.mtl in the same location, otherwise you'll get the ReplaceMe texture all over the object because the engine is expecting a specific filename that you didn't supply. (material_sphere in this case).

*
Saving the material file. Make sure to save it to the same location as the asset
*

![Image](https://www.cryengine.com/docs/static/attachments/25499941)

##
Testing in CRYENGINE

After opening the CRYENGINE Sandbox editor, open an existing level or create a new level.

Once the level is opened, go to
**
Create Object -> Brush
**
.

To find our asset we type the name that it was exported as in the Search field or you can navigate though the folders to the assets location.

![Image](https://www.cryengine.com/docs/static/attachments/25499946)

You will find your asset in the
`
**
gamesdk\objects\material_sphere\
**
`
 folder (if you followed our save locations exactly). If you can't find your exported asset in the browser list, click the top folder again and let the engine update.

Drag and drop the asset in the scene.

![Image](https://www.cryengine.com/docs/static/attachments/25500570)

If you still cannot find your asset in the game folder, please check the export log in the CRYENGINE Exporter inside 3ds Max for details of what could have possibly gone wrong during export.

*
Show Log button in CRYENGINE Exporter
*

![Image](https://www.cryengine.com/docs/static/attachments/25499947)

##
Most common export errors out of 3ds Max

There are a few common export errors that can be fixed. To see which they are and how to fix them see:

**
[Common 3ds Max Export Errors](../Troubleshooting%20and%20Debugging%20Assets/Common%203ds%20Max%20Export%20Errors.md)
.
**

##
Syncing Materials back to 3ds Max

If you've already created a material before and made changes to it in the CRYENGINE Sandbox Editor, you can sync these changes back to 3ds Max by clicking the
**
Sync Material
**
 button.

To use this feature:

-
Select the material you want to sync back to 3ds Max in the Sandbox Material Editor

-
Then back inside 3ds Max, click
**
Sync Material
**
.

-
This will then ask you a few questions about finding the material in the scene, and local file paths

-
Click
**
OK
**
 and sync back the selected material to the 3ds Max Material Editor
This operation will sync the material from CRYENGINE back to 3ds Max to the
**
highlighted material slot
**
 in the 3ds Max Material Editor. Be careful that you don't overwrite an existing material setup in 3ds Max that you need. Make sure to sync back to the correct material, or select an un-used slot to sync to in 3ds Max.

Also make sure to check the paths for the texture maps. These can sometimes return the full path e.g.: C:\CRYENGINE\GameSDK\Objects\...

##
Physically Based Shaders

The following page give you more information on how to use Physically Based Shaders correctly:
**
[Physically Based Shading (PBS)](../../../Graphics%20%26%20Rendering/Shaders/Physically%20Based%20Shading%20(PBS).md)
**
.

[Tutorial Files](#tutorial-files)
[Helpful Information](#helpful-information)
[Initial Setup](#initial-setup)
[Mesh setup in 3ds Max](#mesh-setup-in-3ds-max)
[Material setup in 3ds Max](#material-setup-in-3ds-max)
[Exporting to Engine - Model](#exporting-to-engine-model)
[Exporting to Engine - Material](#exporting-to-engine-material)
[Testing in CRYENGINE](#testing-in-cryengine)
[Most common export errors out of 3ds Max](#most-common-export-errors-out-of-3ds-max)
[Syncing Materials back to 3ds Max](#syncing-materials-back-to-3ds-max)
[Physically Based Shaders](#physically-based-shaders)
