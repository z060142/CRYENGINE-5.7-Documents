# Vegetation 05 Trees (Breakable) Maya

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/25530784
- Page ID: 25530784
- Breadcrumb: Tutorials > Game and Level Design > Vegetation Tutorials > Tutorial - Vegetation Asset Creation > Vegetation 05 Trees (Breakable) > Vegetation 05 Trees (Breakable) Maya
- Parent: Vegetation 05 Trees (Breakable)

## Content

## Overview

This page will cover the Maya pipeline for getting vegetation assets with Boolean Destruction into CRYENGINE.

*![Image](https://www.cryengine.com/docs/static/attachments/25505560) Pic1: Boolean Destruction in action (with physics debug info displayed: F10 or p_draw_helper=1)*

### Tutorial Files

Source Maya scene with exported CRYENGINE files:

**[GameSDK_vegtut05_files.zip](/docs/static/attachments/25523842)**

### Prerequisites for this Tutorial

Before you continue with this tutorial, make sure to have read and understood the following:

- - [How to Install CryMayaTools](../../../../../CRYENGINE%20-%20Getting%20Started/Installing%20CRYENGINE/CRYENGINE%20Plugins%20and%20Tools/Installing%20the%20Maya%20Tools.md)
- [The Basic CRYENGINE Maya Workflow](../../../../../Asset%20Prep%20(External)/Asset%20Exporting%20Overview/Preparing%20Assets%20for%20CRYENGINE/Basic%20Asset%20Setup%20and%20Export%20-%20Maya.md)
- [CRYENGINE Exporter](../../../../../CRYENGINE%20-%20Getting%20Started/Installing%20CRYENGINE/CRYENGINE%20Plugins%20and%20Tools/Installing%20the%20Maya%20Tools/CRYENGINE%20User%20Interface%20in%20Maya.md)
- [Maya Unit Scale to Match up With CRYENGINE Unit System](../../../../../Asset%20Prep%20(External)/Measurement%20Reference%20-%20(DCC%20Unit%20Setup).md)

### Preliminary Information

Make sure to keep the following things in mind while you work on your asset:

- Don't create any additional proxy objects for parts you want to be breakable; just physicalize the visible mesh SubID for the breakable parts.
- Make sure to avoid gaps/holes and close your procedural breakable mesh (a sealed, watertight proxy).
- In contrast to the 3dsMax workflow, you need not combine everything to one mesh object. You may separate and parent the vegetation mesh parts (trunk, branches and leaves) under the "_group" node. It's up to you.
- In CRYENGINE Sandbox, the material for your breakable object needs to have the Surface_Type: "wood_breakable" assigned in order for the engine to activate Boolean Destruction for the geometry.
- Boolean Destruction can be fairly performance heavy depending on different factors:
- Geometric complexity of the Boolean shape.
- Geometric complexity of the breakable asset.
- The number of breakable objects used in the level.
- The number of successive Booleans applied to the breakable object.

### Initial Maya setup

For this tutorial, we will be creating our asset in the following directory. We also included the initial and final Maya scene in there: (<GameFolder> is usually the path to "<YOUR_CRYENGINE_FOLDER>\GameSDK\")

- `<GameFolder>\Objects\tutorial\vegetation\05\tree\boolean_destruction\maya\`

All our exported assets will be saved in this project folder. Some of the textures we will use will come from an already existing asset and we will point you to the directory where they are when the time comes in the tutorial.

We will continue with the assumption that you have already created the basics of the asset, since this isn't a Maya modelling tutorial. We will begin with preparing the asset ready for CRYENGINE, assigning (sub-)material of the Material Group to the relevant polygons and configuring the material.

To start with you may choose to open the tutorial Maya scene with just only the geometry assets created: "**palm_tree_start.ma**"

If you want to see what you are suppose to create in the next 15 - 30 minutes, you may choose to open the final Maya scene: "**palm_tree_final.ma**"

![Image](https://www.cryengine.com/docs/static/attachments/25511214) *Pic2: Maya overview of the finished model including the visible(render) meshes, the "no_collide" and "obstruct" mesh*

### Material Creation

#### Add Material Group and include the Maya shaders

As in the previous vegetation tutorials, we must create an empty **Material Group** with the shelf button "** MAT.ED**" from the installed ** crytek** shelf:

*![Image](https://www.cryengine.com/docs/static/attachments/25511215) Pic03a: Maya material setup workflow for CRYENGINE*

Inside this group we have to included standard Maya shaders to form the material group. Choose a Blinn/Phong shader. Four shaders are needed this time:

- (ID 01): one shader for the leaves,
- (ID 02): one for the breakable tree trunk,
- (ID 03): one for the touch bending activation proxy
- (ID 04): one for the tree top simulation when the tree breaks apart

First, we will create the shaders for the vegetation object parts. In Maya, open the "**HyperShade**". Create a new material group called "tutorial_boolean_destruction_maya". Then create four shaders which we need to add as sub-materials to the material group. Name the first SubId "leaves_SUB", the second one "trunk_SUB", the third SubId "touchbending_proxy_SUB" and the fourth one "obstruct_SUB".

The names of the shaders are not important. Just name them something meaningful to their purpose, so you can distinguish them them easily. You may want to reduce the opacity of your "touch bending activation mesh" shader to see through it and spot the leaves.

#### Add "Physicalize" Extra Attribute to Shaders

Key to success of setting up **Boolean destructible vegetation** is having the correct "** Physicalize"** extra attribute for the material/shader.

Use the "**Add Attribute**" button of the Maya to CRYENGINE Exporter to add this "Physicalize" attribute to the shaders.

When it comes to the material creation process in Maya to CRYENGINE, we must add the "Physicalize" extra attribute to the shaders. In "**crytek**" shelf open the "** Export Tool**", with your shaders selected please click on the "** Add Attribute**" button.

Remember that you won't get any feedback by the "**Add Attribute**" button in any way, you have to check the "** Extra Attribute"** section of the Maya Material, Joint or Geometry.

*![Image](https://www.cryengine.com/docs/static/attachments/25515608) Pic03b: Extra attribute "Physicalize".*

#### "leaves_SUB" shader Setup

Open the *leaves_SUB* shader (ID: 01) in Maya's Attribute Editor.

Set the extra attributes you added as "**Physicalize: None**"

*![Image](https://www.cryengine.com/docs/static/attachments/25523666) Pic04: Set the Physicalize extra attribute for sub material ID 01*

*Optional: Assign the texture map files to the Color texture slots to s* how textures in Maya's viewport.

Load in your diffuse map and normal map

The example file refers to the following textures already provided within the tutorial files:

- `<Your_Project>\Assets\Objects\tutorial\vegetation\05\tree\boolean_destruction\maya\tutorial_boolean_leaf_diff.tif>`
- `<Your_Project>\Assets\Objects\tutorial\vegetation\05\tree\boolean_destruction\maya\tutorial_boolean_leaf_ddna.tif>`

#### "trunk_SUB" shader Setup

Open the *trunk_SUB* shader (ID: 02) in Maya's Attribute Editor.

Set the extra attributes you added as "**Physicalize: Default**"

**![Image](https://www.cryengine.com/docs/static/attachments/25523667) * Pic05: Set the Physicalize extra attribute for sub material ID 02***

*Optional: Assign the texture map files to the Color texture slots to s* how textures in Maya's viewport.

Load in your diffuse map and normal map to the material paths. The normal map should also contain an alpha map for the PBS smoothness value.

The example file refers to the following textures already provided within the tutorial files:

- `<Your_Project>\Assets\Objects\tutorial\vegetation\05\tree\boolean_destruction\maya\tutorial_boolean_trunk_diff.tif>`
- `<Your_Project>\Assets\Objects\tutorial\vegetation\05\tree\boolean_destruction\maya\tutorial_boolean_trunk_ddna.tif>`

For Boolean Destruction to work additional proxy geometry is not needed. The material for the trunk needs to physicalize the rendermesh making sure that the trunk will be solid and breakable.

There are two reasons why additional proxy geometry does not work with Boolean Destruction:

- Precision: The boolean system uses exact hit detection. This makes a rough physics proxy obsolete and the physicalization of the rendermesh necessary.
- Performance: As soon as the first impact causes a hole through a boolean substraction the shape and geometry of the rendermesh changes. An additional physics proxy would mean that a second object needs to be cut as well in order for the next bullet to travel through the newly created empty space.

#### "touchbending_proxy_SUB" shader Setup

Open the *touchbending_proxy_SUB* shader (ID: 03) in Maya's Attribute Editor.

Set the extra attributes you added as "**Physicalize: NoCollide**"

***![Image](https://www.cryengine.com/docs/static/attachments/25523668) Pic06: * Set the Physicalize extra attribute for sub material ID 03****

For the **Touch Bending** setup of the leaves, you must pay attention to the correct ** naming**of the** branch helpers** on the surface of the leaves.

In addition to this, your leaves geometry should have a good non-overlapping UV layout.

This sub-material material is used for the Touch Bending setup on the leaves. For more information on the Touch Bending setup, please go [**HERE**](../Vegetation%2004%20Bushes%20(Touch%20Bending).md)for a full explanation.

#### "obstruct_SUB" shader Setup

Open the *obstruct_SUB* shader (ID: 04) in Maya's Attribute Editor.

Set the extra attributes you added as "**Physicalize: Obstruct**"

****![Image](https://www.cryengine.com/docs/static/attachments/25523670) Pic07: * Set the Physicalize extra attribute for sub material ID 04*****

This physics obstruct parameter in the sub-material is used to define how much air resistance this object has. The amount of air resistance is defined through the size of the obstruct volume. The larger the obstruct volume, the slower the tree will fall.

Examples:

- If you break the tree trunk and you find the upper part if falling too slowly, this means your obstruct proxy is too big. Reduce the size of the obstruct volume.
- If you break the tree trunk and you find the upper part if falling too fast, increase the size of the obstruct volume.

In the **Crytek Shader Basic Parameters** section, set the diffuse color to green and reduce the opacity to 15 - 30%. This isn't required, but helps the user to quickly identify the obstruct geometry within the asset.

#### Export the Material

Now we have configured the material for the object with four SubIds, two for the visible parts of the material (leaves & trunk) and the other two to control the activation of the Touch Bending (tb_proxy) and to define the air resistance (obstruct).

Finally, we will export an **.MTL* file to our project folder to finish our material setup part to this path:

`<Your_Project>\Assets\Objects\tutorial\vegetation\05\tree\boolean_destruction\maya\tutorial_boolean_destruction.mtl`

*![Image](https://www.cryengine.com/docs/static/attachments/25523671) Pic08a: Create *.MTL material file from the Maya to CRYENGINE exporter*

### Geometry

Use the following geometry creation process described below as a guideline. You need not to follow it as the geometry objects are already done and provided by the Maya tutorial files in the Tutorial Files section.

Our geometry for this tutorial is going to be a palm tree. This plant is perfect for explaining this type of technology since its trunk is thin enough to break in a believable way through a boolean destruction operation. On top of that the leaf crown is a good example on how obstruct volumes work when it comes to air resistance on pieces that will fall down afterwards.

#### Creating the Trunk

Create your tree trunk geometry and apply the material (*tutorial_boolean_destruction.mtl*) we just created to it. Change its material SubId to 2 ("trunk"). Finally use the **Unwrap UVW** modifier to adjust its UV shell.

This section of our geometry will be the destructible part. Make sure to avoid holes in your mesh. A boolean operation can only successfully applied to fully closed geometry.

The default boolean cut shape has a predefined width so keep the trunk radius on a reasonable value in order to get clean cuts through the whole mesh. The trunk will only break when this operation cuts completely through it.

*![Image](https://www.cryengine.com/docs/static/attachments/25505563) Pic8: Geometry of the palm tree trunk*

#### Creating the Leaf Crown

Next create a single big leaf mesh for your palm tree and apply the material (*tutorial_boolean_destruction.mtl*) we just created to it. Change its material SubId to 1 ("leaves"). Finally use the "Unwrap UVW" modifier to adjust its UV shell to only fit around one of the leaves on the texture.

##### Adding Touch Bending

For this example, the tree crown will use two sets of bendable leaves. This will add more believability to the breaking process. With Touch Bending the leaves will be get physicalized as soon as they fall to the ground when the tree gets destroyed. First copy your leaf and move the UV shell of your copy to another leaf texture. Now create two touch bending setups for both leaves.

For more information on the Touch Bending setup, please go [**HERE**](../Vegetation%2004%20Bushes%20(Touch%20Bending).md)for a full explanation.
Don't copy your leaves or add a Touch Bending proxy yet until we are start with the next step.

![Image](https://www.cryengine.com/docs/static/attachments/25505562) *Pic9: Both leaves with Touch Bending dummies*

##### Adding Detail Bending

To achieve even more believability to our asset we will be using our Detail Bending system. This will allow us to add varied movements to the leaves.

For more information on the Detail Bending setup, please go [**HERE**](../Vegetation%2003%20Bushes%20(Detail%20Bending).md)for a full explanation.

Throughout this process you can finish your leaf crown geometry and add a proper Touch Bending proxy to it at the end.

*![Image](https://www.cryengine.com/docs/static/attachments/25505565) Pic10: Geometry of the palm tree crown using a Touch Bending and Detail Bending setup*

#### Adding Air Resistance Geometry (obstruct)

For this functionality you need to set up a single piece of geometry to define proper air resistance. The bigger its volume the slower the top piece will fall down after you shoot the tree. This helps the tree to fall down in a more believable way. Create a simple low poly sphere with a radius of roughly 1m and put it right in the middle of the leaf crown.

*![Image](https://www.cryengine.com/docs/static/attachments/25505570) Pic11: Additional obstruct geometry within the leaf crown*

#### Export the Geometry

We are now ready to export our geometry to the engine. This is the export hierarchy we must create:

*![Image](https://www.cryengine.com/docs/static/attachments/25511214) Pic01: Final export hierarchy from this doc page Initial Maya Setup section.*

Using CRYENGINE exporter to export the Maya files:

- Add the *cryExportRoot* node using the "**Tools**" shelf button from the **crytek** **shelf** or create an empty group and name it to "cryExportNode_**palm_tree**".
The **bold** sub-string part is the file name it gets created. So the *.CGF file is named "palm_tree.cgf".
- Create under this root export node a group named "**boolean_destructible_tree**_group". The ** bold** sub-string part becomes the asset name shown in CRYENGINE Sandbox: ** boolean_destructible_tree**
- Parent all **branch#_# locators**, the leaf and trunk meshes, proxy/obstruct mesh geometries all under the "** boolean_destructible_tree**_group" node.
- Select "**boolean_destructible_tree**_group" node and go down to its extra attribute section and mark this group to be exported as *.CGF format.
- Press the "**Export All" / "Export Selected**" button in the Maya to CRYENGINE exporter window.

*![Image](https://www.cryengine.com/docs/static/attachments/25523678) Pic13: Export Boolean destructible palm tree as *.CGF*

### Continue to CRYENGINE

We have now finished the setup for the Maya portion of the tutorial. To continue move to the next page where we configure the material and use the Vegetation Tool to place down some of these Touch Bending assets.

- [Vegetation 05 Trees (Breakable) CRYENGINE](Vegetation%2005%20Trees%20(Breakable)%20CRYENGINE.md)

[Tutorial Files](#tutorial-files)[Prerequisites for this Tutorial](#prerequisites-for-this-tutorial)[Preliminary Information](#preliminary-information)[Initial Maya setup](#initial-maya-setup)[Material Creation](#material-creation)[Geometry](#geometry)[Continue to CRYENGINE](#continue-to-cryengine)
