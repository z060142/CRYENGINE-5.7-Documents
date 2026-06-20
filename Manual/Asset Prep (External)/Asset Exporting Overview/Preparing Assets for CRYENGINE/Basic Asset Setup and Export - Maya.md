# Basic Asset Setup and Export - Maya

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/23308292
- Page ID: 23308292
- Breadcrumb: Asset Prep (External) > Asset Exporting Overview > Preparing Assets for CRYENGINE > Basic Asset Setup and Export - Maya
- Parent: Preparing Assets for CRYENGINE

## Content

##
Overview

This tutorial explains on how to setup assets, and export them from Maya into the CRYENGINE using the
Crytools
 that are available. Before getting started, you should familiarize yourself with the
**
[Installing the Maya Tools](../../../CRYENGINE%20-%20Getting%20Started/Installing%20CRYENGINE/CRYENGINE%20Plugins%20and%20Tools/Installing%20the%20Maya%20Tools.md)

**
and
[CRYENGINE UI in Maya](../../../CRYENGINE%20-%20Getting%20Started/Installing%20CRYENGINE/CRYENGINE%20Plugins%20and%20Tools/Installing%20the%20Maya%20Tools/CRYENGINE%20User%20Interface%20in%20Maya.md)
 articles.

![Image](https://www.cryengine.com/docs/static/attachments/25501310)

##
Tutorial Files

Source Maya scene with exported CRYENGINE files:

**
[basic_export_maya.zip](/docs/static/attachments/25501319)
**

##
Prerequisites for this Tutorial

Before you continue with this tutorial, make sure to have read and understood the following topics:

-

-
**
[How to Install CryMayaTools](../../../CRYENGINE%20-%20Getting%20Started/Installing%20CRYENGINE/CRYENGINE%20Plugins%20and%20Tools/Installing%20the%20Maya%20Tools.md)
**

-
**
[CRYENGINE Exporter](../../../CRYENGINE%20-%20Getting%20Started/Installing%20CRYENGINE/CRYENGINE%20Plugins%20and%20Tools/Installing%20the%20Maya%20Tools/CRYENGINE%20User%20Interface%20in%20Maya.md)
**

-
**
[Maya Unit Scale to Match up With CRYENGINE Unit System](../../Measurement%20Reference%20-%20(DCC%20Unit%20Setup).md)
**

##
Getting Started

*

*
Make sure to keep the following things in mind while
create the minimum elements in a Maya to CRYENGINE scene:

-
Units must be set to centimeters, and FPS set to 30.

-
At least one world level group named
*
cryExportNode_<filename>
*
should be available.
*
<filename>
*
will be the filename of the exported asset.

-
Make sure you add the
*
<cryengine_asset_name>_group
*
 as parent under the
**
cryExportNode
**
.
*
<cryengine_asset_name>
*
 is the name of the asset when you add CRYENGINE file.

-
Create
**
Material Group
**
 with a shader assigned to the exported geometry.

-
Set the desired CRYENGINE file format, which depends on the purpose of the asset. The most basic one is the
*
**
*.CGF
**
*
 geometry format.

-
Optional: LODs and Proxy setup (steps outlined in the tutorial section below)
After having finished modeling and texturing our geometry and assigned our shaders, proxy geometry are needed for collision detection. Right now the proxy geometry has just a standard Lambert assigned. We have also created LODs (LOD1 and LOD2), those are the same asset with lower polygon counts, which then will be swapped out automatically by the CRYENGINE based on how far the asset are placed with respect to the camera in order to save performance.

Any Maya shader can be assigned to your CRYENGINE asset. They only work in Maya, and you must replace it by a CRYENGINE material in Sandbox later. The
**
 Phong
**
 shader is arguably the best choice at the moment.

It is very important that you name your geometry correctly. Maya identifies all scene nodes by its case-sensitive name string. CRYENGINE will auto-convert the names to lowercase. Thus, it is not recommended to use same name for two objects with different cases, For example, Propeller for the geometry and propeller for its shader.

Naming for CRYENGINE assets
CRYENGINE assets uses lower-case naming. But Maya identifies its nodes by case-sensitive name strings. So, please avoid case-sensitive distinction of objects in your Maya scene. Also, do not name any world level nodes as
**
cryExportNode
**
, since this is the entry identifier for the Maya to CRYENGINE exporter.

The below image shows a shaderball example geometry (LOD0 or render mesh) with two LODs and the physics/collision proxy. In the below image, we have intentionally moved the LOD 1 and 2, and the proxy to the left and right for better distinction. We have to align them back to the LOD0 of the shaderball before advancing the tutorial.

*
A sample shaderball geometry with LOD and proxy distinguished

![Image](https://www.cryengine.com/docs/static/attachments/25500557)

*

The current scene in Outliner. Notice everything is still in a flat hierarchy in world space. We use a *
*
_MSH
*
 suffix for polygonal geometry as naming convention. Name of the objects does matter, when we start making the
*
cryExportNode
*
 groups.

*
Pic3: An example of naming convention for polygonal geometry.

![Image](https://www.cryengine.com/docs/static/attachments/25500558)

*

##
Building a Basic Export Hierarchy with a CryExportNode

To create the CryExportNode within Maya, we need to select the geometry first, and then select the
**
 Crytek
**
 tool shelf and click on the
**
Tools
**
shelf icon
**
.
**
 That will open up the
**
Cry Tools
**
window
**
.
**

*
Selecting the LOD0 / render mesh of the shaderball and starting the Tools option from Crytek shelf

![Image](https://www.cryengine.com/docs/static/attachments/25500562)

*

Now click on
**
Create CryExportNode,
**
 this will create the
**
CrytekExportNode
**
and open the window
**
 Create CrytekExportNode
**
. Now, name our asset to create a
*
*.cgf
*
 file. We make sure that the file type
**

**
is set to
**
 Geometry (.CGF)
**
 and then click on the
**
 Create
**
button in that window.

The
**
Create CryExportNode
**
 button will create an empty transform node and an empty group with the suffix of the name of the selected object.

![Image](https://www.cryengine.com/docs/static/attachments/25500565)

By default, it will also create the next subgroup which prefixes with shaderball geometry name string. The CRYENGINE default export format is a
**
*.CGF
**
 file, a geometry format.

![Image](https://www.cryengine.com/docs/static/attachments/25500567)

If we look in the
**
 Outliner,
**
 we'll see that a
**
 cryExportNode_<name_of_file>
**
has been created
**
.
**
 By expanding the
**
 cryExportNode,
**
 we see that there's another group below. We may
**

**
select the asset and move it (by using Middle-Mouse-Button and dragging) into the group that is parented under the "cryExportNode" if you forgot to have the geometry selected in the first place.

![Image](https://www.cryengine.com/docs/static/attachments/25500569)

##
Extending the Basic Export Hierarchy with a Collision Proxy

To have the LOD0/render mesh geometry to interact with Physics events in CRYENGINE, we need a collision proxy. The proxy geometry should be built with great care to approximate and encompass the shape of your render mesh. Its intention is to be a replacement geometry to reduce physics calculations needed between the render mesh and the environment. Thus, keeping the complexity of your proxy geometry as low as possible. As an option, CRYENGINE provides you with the means to use proxy primitives to improve physics performance.

The most common way to set up proxy mesh is:

-
Parenting the proxy geometry under the
*
<your_asset_name>_group
*
.

-
Assigning a shader to the proxy geometry, which has an extra attribute called
**
Physicalized
**
, normally
**
Physicalized: ProxyNoDraw
**
.

-
Optional: adding a UDP, which is also an extra attribute, that allows your proxy mesh to be marked and it will be replaced by a CRYENGINE proxy primitive (box, cube, sphere, cylinder, or capsule).
We have already included a proxy mesh for the shaderball in this tutorial. To correctly set up our collision proxy geometry, first we need to select it in the
**
Outliner
**
, move it into the same group under the
**
 cryExportNode
**
 since our main geometry is parented.

![Image](https://www.cryengine.com/docs/static/attachments/25500571)

*
cryExportNode hierarchy including a proxy mesh.

![Image](https://www.cryengine.com/docs/static/attachments/25500572)

*

##
Collision Proxy Material Setup

As a next step, we open up the
**
 Hypershade
**
 and create a
**
Phong
**
shader. We name the shader
**

**
as
**
 proxy_SUB
**
. Now open the
**
 shader attributes
**
 and set the color to red and its transparency to perhaps 80%. Once this is done, we can assign this shader to our
**
 Proxy
**
geometry.

**
Note:
**
 Any shading parameter changes here is only meant for your Maya scene.
The CRYENGINE Exporter translates only the setups with shader assignments to your geometry (objects or faces), and they ignore any other material setups created using Maya.

*
Using red transparent proxy shader for better distinction in Maya

![Image](https://www.cryengine.com/docs/static/attachments/25500574)

*

*
Assigning a material to a geometry selection (individual faces or the whole geometry object)

![Image](https://www.cryengine.com/docs/static/attachments/25500576)

*

##
Physicalized Extra Attributes for Proxy Material

The proxy material still needs to be tagged as such for CRYENGINE. This is done by adding an
**
Extra Attribute
**
to a Maya shader.

To add an extra attribute to the shader.

-
Open the Exporter from
**
Crytek
**
 Shelf ->
**
EXPORT
**
 shelf icon. Have your shader or any object, with the proxy material assigned, selected.

-
On top of the Exporter window, click on the ominous
**
Add Attributes
**
 button. This button will add some
**
Extra Attributes
**
 depending on your selected type of objects. If it is geometry or shader, then the shader will get the
**
Physicalize
**
 attribute. If it is a joint, it will get Extra Attributes for setting the ragdoll rotation limits and rotational damping.

-
Now, open the
**
Hypershade
**
and select the shader that you have assigned to your proxy objects and the
**
 Attribute
**

**
Editor
**
 of our proxy material.

-
Once the Attribute Editor is open, scroll down to
**
Extra Attributes
**
tab and expand it
**
.
**
 Using the drop down menu right next to the
**
Physicalize
**
, set it to
**
 ProxyNoDraw
**
. Now our proxy material is tagged for CRYENGINE.
![Image](https://www.cryengine.com/docs/static/attachments/25498208)

*
Using Attribute Editor tab to tag the proxy material

![Image](https://www.cryengine.com/docs/static/attachments/25500579)

*

##
Proxy Primitive UDPs

For better performance, you should only use CRYENGINE (collision/physics) proxy primitives. You need to create your own custom proxy objects if you really need them. All non-primitives/custom physics proxies should have a reasonably amount of polygons. To declare our Proxy geometry as a
**
 primitive
**
 (only primitive geometry like cubes, cylinders ,capsules and spheres can be used for that, and we can have as much geometry primitives as we need to):

-
Click in the
**
Crytek
**
 tool shelf,
**

**
and then click on the button labeled
**
 UDP
**
 (User Defined Properties). This will open up another window, and enter the type of proxy primitive that we want it to be (Cube/Box, Cylinder, Sphere or Capsule). Leave it blank if you don't want to use proxy primitives.

-
Now, click on
**
Save
**
and close the window. Now our Proxy geometry has been defined as a Proxy collision primitive and will be displayed and used as such.
![Image](https://www.cryengine.com/docs/static/attachments/25500573)

Below is a video showing you how to set up collision proxies in Maya:

[Embed: https://www.youtube.com/watch?v=ucKEV4JKZwA]

##
Set up the Material Groups

To
**
export
**
the asset successfully from Maya into CRYENGINE, we need to set up a
**
 Material Group.
**
 A material group contains all the materials assigned to the geometry and the materials are numbered. Since the legacy of CRYENGINE is strongly linked to 3ds Max, we see the material group as a Multi/SubMaterial and the shaders grouped under it as SubMaterials. This affects the proxy material setup too as we have to include it to the material group.

To setup the material group:

-
Select our main geometry and proxy geometry. With our geometry selected, click the
**
 Crytek
**
shelf and then click on the
**
 MAT.ED
**
 shelf icon. That opens the
**
Material Groups
**
 window.

-
In the Material Group window, click on
**
Create Group
**
 and name the material group. The group name should be similar to the name in the
**
 cryExportNode,
**
and then click
**
Ok
**
. Now you can see the name of the shading group on the left column under
**
Material Groups
**
.

-
To load in the shaders that are currently assigned to the geometry, click on the right column
**
Shaders
**
 on the
**
Add Shaders From Selected Geom
**
. As you can see it loads the materials assigned to our geometry and provides them with IDs.

-
To re-order the materials, you have to select the material in the
**
Shaders
**
 window, and click on the buttons
**
Move Shaders Up/Move Shaders Down.
**
![Image](https://www.cryengine.com/docs/static/attachments/25500580)

*
Final view of the newly created material group.

*
![Image](https://www.cryengine.com/docs/static/attachments/25500581)

##
Creating the LOD groups

To create the LOD groups, first create an empty group under the node that is parented to the
**
cryExportNode
**
 and name it
**

**
as
**
 _lod1_assetName_group.
**
 For subsequent LODs , you can name them as
**
_lod2_assetName_group
**
,
**
_lod3_assetName_group,
**
and etc. In Maya, you can create an empty group by going to the menu
**
Create -> Empty Group
**
 and rename it afterwards.

Once we have our LOD groups, parent the LOD geometry under their respective group. As you can see, only the name of the parent group node is important to be marked as an LOD, not the mesh node itself.

*
Placing empty LOD1 and LOD2 parent groups under world space

*
![Image](https://www.cryengine.com/docs/static/attachments/25500818)

*
Selecting LOD1 and LOD2 groups and the parented LOD mesh nodes under them

*
![Image](https://www.cryengine.com/docs/static/attachments/25500819)

*
Placing the LOD groups under the cryExportNode Sub-Group

*
![Image](https://www.cryengine.com/docs/static/attachments/25500820)

##
Exporting the Asset from Maya

Now that we have all set up, we're going to export the asset from Maya. To do that go to
**
Crytek
**
 shelf, and then click on the
**
 Export
**
 shelf icon to open the
**
Crytek Export
**
window. The Exporter will automatically look for any root level groups named
**
cryExportNode_*
**
 and display the groups in the list. You have more functions when you right click on the list, like refresh manually the list after changes.

Click on the
**
Export Selected
**
button
. Now the geometry asset will be exported into the same location as our saved Maya scene file.

*
Exporting the shaderball cryExportNode to a *.CGF file.

![Image](https://www.cryengine.com/docs/static/attachments/25501031)

*

In the Exporter, click on
**
Generate Material Files
**
button, this will save the CRYENGINE
**
 *.MTL
**
 file in the same location as you have saved your Maya scene file. It's recommended to keep the name of the material similar to your asset, for example, a
*
shaderball.cgf
*
 geometry should be accompanied by a
*
shaderball.mtl
*
 material file.

*
Exporting the shaderball material to a
**
*.MTL
**
 file.

![Image](https://www.cryengine.com/docs/static/attachments/25501039)

*

##
Loading and checking the Asset in CRYENGINE

Open
**
Sandbox.exe
**
 from the installed CRYENGINE folder, and create an empty level or open a level that you have worked on before.

##
Create Object

To load the asset into Sandbox:

-
Go to the
**
Create Object
**
 sub-window.

-
Select the exported CGF asset and drag it into the level.

-
If you have closed
**
Create Object
**
 window, you can navigate to it using the main menu bar:
**
Tools
**
 ->
**
Level Editor
**
 ->
**
Create Object
**
.
![Image](https://www.cryengine.com/docs/static/attachments/25501311)

*
Viewing the
*
exported shaderball asset

*
*
![Image](https://www.cryengine.com/docs/static/attachments/25501314)

##
Material Editor

To check if everything is exported correctly, open up the Material Editor. In the editor, the main Material (Shading Group) and all the sub-materials (the materials that were assigned to our geometry) should be visible. The
**
Proxy Material
**
 should be in the first slot.

You won't see the material since it was set to noDraw so it's invisible. Select each sub-material and load the correct textures into the right slots. As you can see the proxy is also present and defined as a CRYENGINE primitive
**
.
**

![Image](https://www.cryengine.com/docs/static/attachments/25501317)

##
Proxy Display Option

CRYENGINE proxy primitive and non-primitive
True CRYENGINE proxy primitives are displayed in gray shading with no triangulated face edges. Non-primitives/custom proxy object have a wireframe displayed on top of the gray shading.

*
Displaying the collision proxies in the viewport

![Image](https://www.cryengine.com/docs/static/attachments/25501315)

*

Proxy geometry are usually shaded in grey. However, if you see the proxies slowly blinking between red and grey, you are advised to reduce the polycount or rebuild your proxy geometry (made of several elements) into one continuous piece. Although this is not mandatory, you might encounter some cases where Physics events do not behave correctly.

[Tutorial Files](#tutorial-files)
[Prerequisites for this Tutorial](#prerequisites-for-this-tutorial)
[Getting Started](#getting-started)
[Building a Basic Export Hierarchy with a CryExportNode](#building-a-basic-export-hierarchy-with-a-cryexportnode)
[Extending the Basic Export Hierarchy with a Collision Proxy](#extending-the-basic-export-hierarchy-with-a-collision-proxy)
[Set up the Material Groups](#set-up-the-material-groups)
[Creating the LOD groups](#creating-the-lod-groups)
[Exporting the Asset from Maya](#exporting-the-asset-from-maya)
[Loading and checking the Asset in CRYENGINE](#loading-and-checking-the-asset-in-cryengine)
