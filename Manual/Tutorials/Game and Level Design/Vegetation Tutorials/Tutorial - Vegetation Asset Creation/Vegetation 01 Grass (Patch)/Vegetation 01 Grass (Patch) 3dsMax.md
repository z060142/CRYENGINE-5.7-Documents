# Vegetation 01 Grass (Patch) 3dsMax

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/24285886
- Page ID: 24285886
- Breadcrumb: Tutorials > Game and Level Design > Vegetation Tutorials > Tutorial - Vegetation Asset Creation > Vegetation 01 Grass (Patch) > Vegetation 01 Grass (Patch) 3dsMax
- Parent: Vegetation 01 Grass (Patch)

## Content

## Overview

This tutorial takes you through the process of creating the simplest vegetation asset; grass patches. It covers the basics of the vegetation shader parameters and introduces you to the Vegetation Editor in CRYENGINE. Grass patches is the former method that we used to create grass assets for the ENGINE. Even though this method is still valid and worth knowing, our preferred method for creating grass is to use the Merged Mesh (MM) technology.

![Image](https://www.cryengine.com/docs/static/attachments/24157002) *Pic1: Finished scene using grass patches.*

The below example (*Pic2*) depicts the creation of grass patches using the vegetation Editor. The one on the right is shown in a highlighted planes view.

![Image](https://www.cryengine.com/docs/static/attachments/24157003) *Pic2: Grass objects in normal and highlighted planes view.*

### Tutorial Files

Source 3dsMax scene with exported CRYENGINE files:

**[GameSDK_vegtut01_files.zip](/docs/static/attachments/25523833)**

### Prerequisites for this Tutorial

Before you continue with this tutorial, make sure to have read and understood the following topics:

- [How to install CryMaxTools](../../../../../CRYENGINE%20-%20Getting%20Started/Installing%20CRYENGINE/CRYENGINE%20Plugins%20and%20Tools/Installing%20the%203ds%20Max%20Tools.md)
- [The basic CRYENGINE 3dsMax workflow](../../../../../Asset%20Prep%20(External)/Asset%20Exporting%20Overview/Preparing%20Assets%20for%20CRYENGINE/Basic%20Asset%20Setup%20and%20Export%20-%203ds%20Max.md)
- [CRYENGINE Exporter](../../../../../CRYENGINE%20-%20Getting%20Started/Installing%20CRYENGINE/CRYENGINE%20Plugins%20and%20Tools/Installing%20the%203ds%20Max%20Tools/CRYENGINE%20Exporter%20in%203dsMax.md)
- [3dsMax unit scale to match up with CRYENGINE unit system](../../../../../Asset%20Prep%20(External)/Measurement%20Reference%20-%20(DCC%20Unit%20Setup).md)

### Helpful Information

Keep the following things in mind while working on your assets:

- Usually, the merged mesh and grass patches versions does not require a physics proxy.
- If you enable the *grass* flag in the Shader Generation Parameters, then you do not need a normalmap (optimization).
- Each grass patch placed has its own set of drawcalls. Merged mesh grass does not - it batches chunks together.
- Do not exceed a diameter of 8 meters for large grass patches. This size has proved to provide a good balance between performance and ground coverage.
- Use as few polygons as possible while making a repeating asset such as grass. It will improve performance significantly.
- Add LOD's to the asset. Reduce the polygon count by 50% (if possible) on each LOD step.

### Initial 3dsMax Setup

For this tutorial the asset has been created in the following directory:

- `<Your_Project>\Assets\Objects\tutorial\vegetation\01\grass_patch\`

- To begin with, save the **3dsMax** scene to this location.
- All exported assets will also be saved in this directory.
- Some of the textures used in this tutorial are derived an existing asset. In this case, we point you to the directory where they are stored later in this tutorial.

### Material

Initially, we need to prepare the material that will be applied to the object. This enables us to provide a visual reference to the texture that you are using when modeling or shaping the geometry planes for the grass patch. For the individual grass and the grass patches, you only require one material *SubID* for the visible portion of the mesh. Also, a physics proxy is not required on the object as the player is supposed to pass straight through the object without hindrance.

You can add a proxy to the object, but it is not recommended for grass patches.

*![Image](https://www.cryengine.com/docs/static/attachments/24157004) Pic3: Material setup in 3dsMax, left is the top level of the multi-material, on the right the SubID's properties.*

Default settings for the SubID's properties in the Material Editor

- In the screenshot (*Pic3*) on the above, on the right side, note under the **Shader Basic Parameters** that the ** Crytek Shader** has been selected from the drop down list.
- In the **Crytek****Shader Basic Parameters** section, ** Default** has been selected from the drop down list.
- Since we are not physicalizing the object, the **Physicalize** checkbox has ** not** been checked.

In order for the Diffuse and the Specular colors to align with the PBS model they are set as follows:

- Diffuse = 255,255,255
- Specular between the 40,40,40 -> 60,60,60 range

The example file refers to the following texture that is already provided within the build. Link to this in the Diffuse Color map:

- `<Your_Project>\Assets\Objects\natural\ground\grass\textures\grass_mix_diff.tif>`

We are not adding a normalmap (ddna). This is intentional, since we want our grass asset to be as cheap as possible and we achieve this by enabling the **grass** flag in the ** Shader Params** section. The ** grass** flag runs the shader through a cheaper pipeline and the main benefit of this is that it does not need a normalmap.

Even though you will be able to add one, but it won't be used. Hence, it's a waste if grass is ticked in the **Shader Generation** params.

#### Export the Material

Now we have configured the material for the object with one SubID.

![Image](https://www.cryengine.com/docs/static/attachments/24156990) *Pic4: Selecting the top level of the material (not a SubID) to export.*

Ensure you follow the following prerequisites:

- Make sure you have the correct material selected in the **Material Editor** (you need to be at the materials root level, not inside a SubID).
- In the **CRYENGINE Exporter** tab, click the ** Create Material** button. Save this into the same directory as the object:

- `<Your_Project>\Assets\Objects\tutorial\vegetation\01\grass_patch\`**tutorial_grass_patch.mtl**

### Object Setup

For a grass patch, we define the object by a series of simple planes, rotated in random directions and with variations in scale to achieve a dense look with minimal geometry. The idea is to make it look solid from every direction, such as in the X, Y and Z direction.

Steps for setting up an object:

- Create a polygon plane and apply the material **tutorial_grass_patch** to it.
- Make sure that the SubID is set to ID 1.
- Name the polygon object **tutorial_grass_patch.**
- Use the **Unwrap UVW modifier** to adjust your UV shell to only fit around one of the grass patches on the texture.
![Image](https://www.cryengine.com/docs/static/attachments/24156998)
*Pic5: Arrange the UVs of the polygons to fit one of the grass textures.*
- Using this setup, duplicate the polygons and distribute them around the area which you would like the patch to cover. Apply random rotation and scale to the patch to break up the uniformity of the object (Make sure you do not over modify which may start to stretch the textures).
- Try to end up with a rough hexagon shape for the entire patch. This works the best in most situations.
*![Image](https://www.cryengine.com/docs/static/attachments/24156994)![Image](https://www.cryengine.com/docs/static/attachments/24156995)*
*![Image](https://www.cryengine.com/docs/static/attachments/24156996)![Image](https://www.cryengine.com/docs/static/attachments/24156997) Pic: 6, 7, 8, 9: Example grass patch geometry build up.*
- After you have finished the geometry distribution attach all the individual planes together into a single base object (tutorial_grass_patch).

#### Tweaking the Pivot Location

Make sure that the pivot of the object is roughly in the center and slightly up from the absolute bottom of the object. This slight vertical offset of the pivot allows the geometry to be slightly sunken into the floor which is useful in aligning according to the terrain function in the Vegetation Editor. When used in this way, it will average out (as best it can) to fit with the variation in terrain height. This helps to avoid a gap underneath the grass patch and prevents it floating in space.

Make sure you do not set the pivot too high, otherwise you will lose the bottom of the geometry into the terrain.

*![Image](https://www.cryengine.com/docs/static/attachments/24157005) Pic10: Pivot location slightly higher than the base of the object.*

#### Apply Vertex Color (to control material Vertex Deformation)

This is an optional feature that can be applied to the asset. It is not required unless you use the asset with a specific material setup, such as Vertex Deformation. Without the vertex coloring in the asset, the simplified movement you get when using vertex deformation is **applied across the entire geometry**.

By default, the vertex color of the asset is white (full movement), but when you apply black to the base vertices (where the grass will be rooted to the floor), then only the tips of the grass will move (since they are colored white). This gives a much more realistic and believable looking asset.

Unlike the bending parameter that can be applied inside the Vegetation Editor and it automatically fixes the base of the grass to the floor. Vertex color is used to control the movement when you apply the movement via the vertex deformation within the material.

Inside 3dsMax, configure the asset to display the vertex colors. Right click on the model and select **Object Properties**. Enable the checkbox to display vertex channel display and ensure that vertex color is selected from the drop down list.

![Image](https://www.cryengine.com/docs/static/attachments/24156991) *Pic11: Enabling vertex color display on the asset.*

With the asset selected, add a vertex paint modifier to the stack.

To help visualize where you are assigning colors to, apply a different standard material (a spare empty material with the flat grey color) to better see colors on the vertices. However, do not forget to return it to the correct material after you have finished the vertex painting.
![Image](https://www.cryengine.com/docs/static/attachments/24156992) *Pic12: Apply the vertex colors, black = no movement, white = maximum movement.*

Process for applying vertex colors:

- Apply a default material to better see (optional).
- Add the vertex paint modifier to the object.
- Select all the bottom vertices in the **Viewport**.
- Pick the color for the bottom vertices (black).
- Use the **Paint all** button to flood the black color onto the selected bottom vertices.
- Collapse the modifier stack.
- Re-apply the correct grass material (if it was changed).

When we progress to the CRYENGINE portion of this tutorial, we will continue with the use cases for vertex color within the asset. For now, continue on to create the rest of the asset.

#### Add Some LOD's to the Grass

Even though this grass object is a very simple geometry with a total of 600+ polygons, it still makes sense to add LOD's to the object - so we can lose some of the extra polygons at distance.

To add LOD's make sure the following rules are set:

- Use the $LOD prefix to the LOD's name (e.g. $LOD1, $LOD2 etc...). The naming convention of $LODxxx to inform the Engine that this is an LOD.
- Try to reduce the polygon count by approximately 50% per LOD step (if possible) while still preserving the overall shape.

![Image](https://www.cryengine.com/docs/static/attachments/24157000) *Pic13: Overview of the LOD chain.*

In this example, we are using two LOD's for this asset. The naming convention and polygon count are as follows.

Name | LOD | Description | Polygon Count
--- | --- | --- | ---
tutorial_grass_patch | LOD0 | Main mesh you'll see up close | 652
$LOD1_tutorial_grass_patch | LOD1 | First LOD | 412
$LOD2_tutorial_grass_patch | LOD2 | Second LOD | 212

Note, there is an approximate 50% drop in polygons as we step down the LOD chain. It is not a hard rule to follow, but we recommend you to aim for that level of optimization when switching LOD's. It is of course down to a per-asset basis as to how many polygons you can safely remove without destroying the look of the asset.

When you link the LOD's to the parent object (dummy helper or in this instance the main mesh) all the LOD's must connect directly to the parent.

![Image](https://www.cryengine.com/docs/static/attachments/24157001) *Pic14: Schematic view of the hierarchy that all LOD's are siblings of each other and linked to the parent.*

#### Export the Geometry

We are now ready to export our geometry to the Engine.

In 3dsMax go to the 6th tab (Utilities) and in the CRYENGINE exporter:

- Add the root node of the geometry asset to the export list (in this case it is called "**tutorial_grass_patch**").
- Select 'Geometry (*.cgf)' from the **Export format** drop down list.
- Press the **Export Nodes** button.

*![Image](https://www.cryengine.com/docs/static/attachments/24156989) Pic15: Exporting the asset.*

![Image](https://www.cryengine.com/docs/static/attachments/24156993) *Pic16: Successful export log.*

### Continue to CRYENGINE

We have now finished the setup for the 3dsMax portion of the tutorial. To continue, move onto the next page where we configure the material and use the Vegetation Editor to place down some grass assets.

[Vegetation 01 Grass (Patch) CRYENGINE](Vegetation%2001%20Grass%20(Patch)%20CRYENGINE.md)

[Tutorial Files](#tutorial-files)[Prerequisites for this Tutorial](#prerequisites-for-this-tutorial)[Helpful Information](#helpful-information)[Initial 3dsMax Setup](#initial-3dsmax-setup)[Material](#material)[Object Setup](#object-setup)[Continue to CRYENGINE](#continue-to-cryengine)
