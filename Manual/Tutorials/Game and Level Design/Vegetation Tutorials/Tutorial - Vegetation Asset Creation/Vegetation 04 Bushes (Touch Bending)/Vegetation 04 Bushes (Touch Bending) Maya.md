# Vegetation 04 Bushes (Touch Bending) Maya

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/24285899
- Page ID: 24285899
- Breadcrumb: Tutorials > Game and Level Design > Vegetation Tutorials > Tutorial - Vegetation Asset Creation > Vegetation 04 Bushes (Touch Bending) > Vegetation 04 Bushes (Touch Bending) Maya
- Parent: Vegetation 04 Bushes (Touch Bending)

## Content

## Overview

This page will cover the Maya pipeline for getting vegetation assets with touch bending into CRYENGINE.

The touch bending system is used to simulate deforming vegetation. It is required that your geometry should have clean UVs laid out. Touch bending physics relies on simulated joint chains or branches which are marked by locators snapped onto the vertices (and its UVs) of the vegetation geometry, e.g. the leaves. Whenever the leaf geometry (along with its Uvs) is duplicated, the topology has not changed. So, each duplicated leaf can use the same deforming joint chain/branch. This saves you a lot of effort in the rigging process of the leaves/branches.

![Image](https://www.cryengine.com/docs/static/attachments/26510091) *Pic1: Touch Bending in action (with physics debug info displayed: F10 or p_draw_helper=1)*

### Tutorial Files

Source Maya scene with exported CRYENGINE files:

**[GameSDK_vegtut04_files.zip](/docs/static/attachments/25523840)**

### Prerequisites for this Tutorial

Before you continue with this tutorial, make sure to have read and understood the following:

- [How to Install CryMayaTools](../../../../../CRYENGINE%20-%20Getting%20Started/Installing%20CRYENGINE/CRYENGINE%20Plugins%20and%20Tools/Installing%20the%20Maya%20Tools.md)
- [The Basic CRYENGINE Maya Workflow](../../../../../Asset%20Prep%20(External)/Asset%20Exporting%20Overview/Preparing%20Assets%20for%20CRYENGINE/Basic%20Asset%20Setup%20and%20Export%20-%20Maya.md)
- [CRYENGINE Exporter](../../../../../CRYENGINE%20-%20Getting%20Started/Installing%20CRYENGINE/CRYENGINE%20Plugins%20and%20Tools/Installing%20the%20Maya%20Tools/CRYENGINE%20User%20Interface%20in%20Maya.md)
- [Maya Unit Scale to Match up With CRYENGINE Unit System](../../../../../Asset%20Prep%20(External)/Measurement%20Reference%20-%20(DCC%20Unit%20Setup).md)

### Helpful Information

Make sure to keep the following things in mind while you work on your asset:

- You can mix the vegetation system to have **Touch Bending** and ** Detail Bending** along with being affected by the ** Environment Wind** system.
- **Touch Bending** should only be used on bigger assets (bushes, ferns, trees, etc.). It enables the outstanding vegetation to interact with the player and other AI.
- A **no-collide proxy** and a proper material setup are necessary for this system to work.
- Touch Bending can only be activated within the no-collide volume (will deactivate after approx. 5 seconds if no AI/Player interaction happens)
- The locators for the touch bending bones only work when:
- They follow the naming convention from the **Merged Mesh** tutorial: ** branch1_1**to** branch1_#, branch2_1 to branch2_#**, etc. for each leaf/branch. Replace the **#** sign by a number.
- They must be parented under each leaf mesh.
- They are snapped to vertices of the leaf geometry (Press and hold **V**-key in Maya).
- The order of your export hierarchy matters. Do not place the **touch bending proxy** in front of your leaf meshes, but it should be the last in hierarchy.
- Do not **Freeze transformation** on the leaf mesh objects. It prevents the CRYENGINE from determining the instancing (duplication) of the leaf. You can freely translate/rotate/scale the meshes or use any Maya deformers to create varieties.
- You have to use a minimum of three dummies for each branch. Try to not exceed that number since three is enough for almost all situations.
- Use the CVar **p_draw_helpers=1** or ** F10** in-game to visualize the physics debug info.

### Initial Maya setup

For this tutorial, we will be creating our asset in the following directory.

- `<GameFolder>\Objects\tutorial\vegetation\04\touch_bending\`

To begin with, we save our Maya scene to this location. All our exported assets will be saved in there.Some of the textures that we use comes from an existing asset and the location of the existing asset will be provided later in the tutorial.

We will continue with the assumption that you have already created the basics of the asset, since this is not a Maya modeling tutorial. We will begin with preparing the asset ready for CRYENGINE, assigning shaders to the relevant polygons.

You may also use the tutorial scene files from the previous vegetation (detail bending) tutorial. You may mix the detail bending with touch bending which we are going to set up.

### Material

As in the previous vegetation tutorials, we must create an empty **Material Group** and have Maya shaders assigned to it. We need two shaders this time, one for the vegetation and one for the activation proxy mesh. Provide the Material Group and its shader some appropriate names, so you can locate them later using that name. You may want to reduce the opacity of your proxy shader to easily spot it.

![Image](https://www.cryengine.com/docs/static/attachments/24157172) *Pic2: Material Setup*

#### fern leaves ID "01" shader setup

Your shader with **ID 01** is the material for fern leaves. A detailed material setup will be shown in the next tutorial section where we will discuss about the setup in CRYENGINE. You may load these two textures into your color texture map slot for visual feedback in your Maya 3d viewport. The following textures are already provided within the CRYENGINE build:

- `<Your_Project>\Assets\objects\natural\bushes\ground_cover_fern\ground_cover_fernbush_diff.tif>`
- `<Your_Project>\Assets\objects\natural\bushes\ground_cover_fern\ground_cover_fernbush_ddna.tif>`

#### touch_bending_proxy ID "02" shader setup

For the activation of touch bending vegetation, we usually create a proxy mesh with a special material. In Maya, we need to add an **Extra Attribute** to your proxy shader (** ID 02**).

- Go to the **Crytek** shelf, press the ** Export** shelf icon to open the ** CryMayaExporter**.
- Select the **ID 02** shader.
- On the top, select the **Add Attribute** button which will add the ** Physicalize Extra Attribute** for CRYENGINE material meta data.
- Open Maya's **Attribute Editor** (** CTRL-A**) with the ** ID 02** shader selected. On the bottom section, there you will find the ** Extra Attribute -> Physicalize: NoCollide**.

![Image](https://www.cryengine.com/docs/static/attachments/24157173) *Pic3: Proxy shader setup to activate touch bending*

Unlike the other physicalization option you might be familiar with, **Physicalize: NoCollide**, this does not block the player, it only detects if something is inside.

#### Export the Material

If you still have the **CryMayaExporter** window open, please click on the ** Generate Material Files** button to export the CRYENGINE ***.MTL** file.

*![Image](https://www.cryengine.com/docs/static/attachments/24157174) Pic4: Export Material to CRYENGINE*

### Geometry

Since we have the two materials/shaders created, we can step into the process of making geometries:

- Duplicating the leaf mesh from a reference leaf.
- Creating an activation proxy mesh for touch bending.

#### Touch Bending Explanation

- As already outlined in the Helpful Information above, CRYENGINE takes one or more referenced leaf mesh with snapped locators onto their vertices (and corresponding UVs) to build the touch bending vegetation. This reference mesh object is picked from the hierarchy based on its **branch#_#** child locators. Under your Maya cryExportNode, you are allowed to have several reference leaf meshes with same/different number of ** branch#_#** locators.
- You can duplicate your reference as many times as you wish, but never **Freeze Transform** the duplicated leaf meshes. You may use any means, Maya allows you to shape the duplicated leaves (Lattice, Sculpt, Non-linear, etc. and ** deformers + Delete History** after you have shaped) to create variety.
- You need to create the **branch#_#** locators for your reference leaf mesh only once. Whenever you create a new ** branch2_1** to ** branch2_3**, CRYENGINE will consider this as a new reference leaf mesh.
- Deformation (bending of the joint chain) only occurs when AI, physicalized objects or the player moves into the boundary of the proxy mesh.
- No environmental effect will trigger the deformation except AI, the player or any physicalized objects.

The engine considers duplicates of your leaf as instances while they are part of the whole object. All leaf meshes with the same UV shell, which do not have their own child branch locators, will get the same bone setup as the reference leaf.
CRYENGINE searches for all dummies and the vertices they are snapped onto. It then marks the UV coordinates of those vertices. Each additional geometry element with its own UV shell gets instanced as soon as parts of it cover those three marked UV space locations.

#### Branch Naming Convention

As already mentioned,

- Rename the locators to **branch1_1** to ** branch1_#**, where **#** is at least 3. Theses locators will form the touch bending joint chain which deforms the leaf mesh.
- Each new branch number, e.g. starting with **branch#_1**, will make a new reference leaf. Hence, you need to create the ** branch1_1** to ** branch1_#** child locators for the reference leaf only once.

*![Image](https://www.cryengine.com/docs/static/attachments/24157176) Pic5: One example of a final exportable hierarchy in Maya*

#### Add the reference leaf mesh object and create UVs

Using the provided fern diffuse texture and/or the leaf mesh from the previous vegetation tutorial (detail bending), you can easily model the geometry and layout the fern leaf UVs correctly.

![Image](https://www.cryengine.com/docs/static/attachments/24157177) *Pic6: A simple leaf mesh*

#### Adding and snapping the Locators to the vertices of the reference leaf object.

Create three **Locators** and vertex snap one locator (keep the ** V** key pressed in Maya while moving the Locators) to a vertex on bottom, in the center and on the top of the leaf mesh. Rename the Locators to ** branch1_1** (bottom), ** branch1_2** (center), ** branch1_3** (top). As mentioned before, you must have at least three ** Locators** for the ** branch** spline/bone chain generation. Adding more Locators will improve the deformation, but in most cases, three locators will suffice.

![Image](https://www.cryengine.com/docs/static/attachments/24157179) *Pic7: vertex snap locators to the mesh vertices and use the "branch#_#" naming convention*

#### Duplicate the Leaf to Build the Bush

You need to duplicate the reference leaf mesh to shape a fern bush. You are allowed to move, rotate and scale the duplicated mesh, as long as you do not change their topology and their UVs. So, you may use any Maya **Deformers** (Non-Linear deformers, Wire, Lattice, Soft Modification) on the duplicated leaves. In our case, we have only used the three standard transforms.

![Image](https://www.cryengine.com/docs/static/attachments/24157178) *Pic8: duplicated leaf meshes including their child locators*

#### Adding Variation to the Leaves Geometry

##### Modifications without losing instancing:

There are ways to make variations of your reference leaf without losing the benefit of instancing in CRYENGINE:

- Using Maya deformers and standard transforms (translate/rotate/scale) to change shape of the leaf.
- Moving single vertices of the duplicated leaf meshes to create new shape without changing their UVs. However, this will lead to texture stretching, if you are not careful.
- Deleting few faces of the duplicated leaves are allowed, as long as you do not go overboard, like breaking the UV shell into parts. Their UV shells should be still in the same UV space.

If you completely break the leaves geometry (remove all the polygons in the middle) for making two separate UV islands, this will also break the touch bending for that leaf.

##### Modifications which will break the instancing:

With these modifications you will lose the performance benefit of instancing from a reference leaf mesh. With these changes you can either create a new branch or your leaf mesh will not get touch bending, it stays static.

- Moving/rotating/scaling the UVs will break the instancing. If you still want the touch bending, you are required to add new **branch#_#** child locators.
- Because of the modelling modifications, you want to add more **branch#_#** locators, so that the generated joint chain/rope better fits the new shape of the leaf. Here you must increment the branch index, e.g. ** branch1_#** should be renamed to ** branch2_#**.
- Adding/Removing/Collapsing new vertices/edges/faces, so that the UVs of the leaf are changed.

Below we will show you some useful examples how you can add more variety to your touch bending vegetation.

*![Image](https://www.cryengine.com/docs/static/attachments/24157180) Pic9: Example of non-destructive modifications to instancing: deleting faces*

**![Image](https://www.cryengine.com/docs/static/attachments/24157181) Pic10: Example of non-destructive modifications to instancing: standard transforms (transloate/rotate/scale)**

****![Image](https://www.cryengine.com/docs/static/attachments/24157182) Pic11: Example of non-destructive modifications to instancing: Bend deformer & standard transforms (transloate/rotate/scale)****

In cases where you want to add texture variations to your leaf, you are forced to make a new reference leaf mesh. If you do not want it to be static, then you need to add new **branch#_#** locators.

Because of the texture variation, you have to move the UVs to a new texture space. In the provided fern texture map, we have six texture variations. In addition, you may also have to create a new mesh topology andd UVs. Consider creating the **branch#_#** child locators and parent them under the new reference leaf mesh node. Otherwise, these leaves will not get any touch bending.

*![Image](https://www.cryengine.com/docs/static/attachments/24157183) Pic12: Example of modifications where you lose instancing: adding more "branch#_#" locators and/or moving UVs*

#### Adding the Touch Bending Proxy Geometry (tb_proxy)

The touch bending uses a proxy geometry to get activated when a AI, the player or any physicalized objects is within its boundary. We have already created a shader with a **Physicalize: NoCollide** under ** Extra Attribute**. To finish the proxy creation, we will make a box as tight as possible to cover vegetation geometry.

- Assign the proxy shader created before to the touch bending proxy mesh.
- Group the proxy geometry under the ***_group** node. It's best to move it to the last in hierarchy as shown in the picture * Pic5.*

*![Image](https://www.cryengine.com/docs/static/attachments/24157184) Pic12: Proxy geometry to trigger touch bending physics*

In the above picture, note how the **touch_bending_proxy** geometry is not completely covering all of the leaves. This is on purpose. This is an optimization where we allow the player to get close to the bush, but not activate the leaves with touch bending.

Remember that the player has to enter the **tb_proxy** to activate the touch bending. This is not a required step, it's optional, but in our practice we found this to be the optimal setup in the asset creation.

#### Adjusting the vegetation geometry location

To help the bush fit into the scene when we move the vegetation object to a level, it is recommended to move the vegetation up slightly, so that the base of the plant actually sits underneath the terrain. This avoids the possibility of seeing the bottom of the bush hovering in the air.

*![Image](https://www.cryengine.com/docs/static/attachments/24157187) Pic13: Placing the asset into the scene*

#### Adding Additional Leaves Without Touch Bending

As a further optimization within the bush asset, not every leaf should be associated with a branch. In general, we try to aim for around a 50 / 50 mix of physicalized branches and non-physicalized ones. But it all depends on how the asset looks. Preferably the less physicalized branches the better (less CPU load) but you want enough in there to make the asset look realistic and behave nicely. It's based on your judgement on how many leaves you physicalize within the asset.

When you refer about leaf variations, we already mentioned how you can get static leaves without touch bending. You just have to move the UVs of these leaves to a new UV/texture space without creating new **branch#_#** locators. Make sure when transforming the UVs they match the new fern texture on your map.

Try to keep the non-physicalized leaves closer to the ground so their non-interactivity is hidden under the physicalized ones. This way it is less noticeable and looks more realistic.
*![Image](https://www.cryengine.com/docs/static/attachments/24157185) Pic14: No touch bending because of different UV coordinates and no branch locators*

#### Export the Geometry

Go to the **Crytek** shelf in Maya and run the ** Tool** shelf icon. You can create the ** cryExportNodes** and its groups with this ** Tool** script, or you just create empty groups, name them yourself. Ensure that you have a correctly named ** cryExportNode_*** and a child ***_group** where the asterisk ***** is the name of your asset.

We have also included the detail bending feature from the last vegetation tutorial in our final export scene.

Here is an example of how your final asset may look like.

![Image](https://www.cryengine.com/docs/static/attachments/24157186) *Pic15: Final asset*

### Continue to CRYENGINE

We have now finished the setup for the 3dsMax portion of the tutorial. To continue, move to the next page where we configure the material and use the Vegetation Tool to place down some of these touch bending assets.

- **[Vegetation 04 Bushes (Touch Bending) CRYENGINE](Vegetation%2004%20Bushes%20(Touch%20Bending)%20CRYENGINE.md)**

[Tutorial Files](#tutorial-files)[Prerequisites for this Tutorial](#prerequisites-for-this-tutorial)[Helpful Information](#helpful-information)[Initial Maya setup](#initial-maya-setup)[Material](#material)[Geometry](#geometry)[Continue to CRYENGINE](#continue-to-cryengine)
