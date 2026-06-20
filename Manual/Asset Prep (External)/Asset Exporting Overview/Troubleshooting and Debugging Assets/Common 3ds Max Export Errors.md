# Common 3ds Max Export Errors

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/23308046
- Page ID: 23308046
- Breadcrumb: Asset Prep (External) > Asset Exporting Overview > Troubleshooting and Debugging Assets > Common 3ds Max Export Errors
- Parent: Troubleshooting and Debugging Assets

## Content

## Overview

### Asset Has No Crytek Shader Assigned

**Issue:** When some faces or objects in your scene have no Crytek shader assigned to it, you will get the following error: * The following material is not set to the Crytek Shader: Face*. **Resolution**: To fix this error, select the object or faces and in the Material Editor and change the Shader Type to ** Crytek Shader**.

*Pic1: "The following material is not set to the Crytek Shader: Face" error.*![Image](https://www.cryengine.com/docs/static/attachments/23994952)

*Pic2: Changing shader to Crytek Shader.*![Image](https://www.cryengine.com/docs/static/attachments/25505552)

### Multiple Assets Get Exported As One Big Single Mesh Instead of Separate Ones

**Issue:** When you export multiple assets in your scene from 3DS Max, and import it into CRYENGINE, you can see all the assets are with one node and only as one file.

**Resolution:** You need to make sure that the checkbox ** Export file per node** is checked to avoid exporting multiple dummy nodes as as single file. For example, if you have different pieces of a building that you need to export into the CRYENGINE.

*Pic3: Enabling the Export file per node checkbox.*![Image](https://www.cryengine.com/docs/static/attachments/25506098)

### 3DS Max Crashes Instantly During Export

**Issue:** 3DS Max crashes instantly, while exporting your assets. One of the main reasons could be that the LODs have been linked under the dummy node.

*Pic4: Linking LODs under the dummy node.*![Image](https://www.cryengine.com/docs/static/attachments/25506102)

**Resolution**: You need to link the LODs under the main mesh node.

*Pic5: Linking LODs under the main mesh node.*![Image](https://www.cryengine.com/docs/static/attachments/25506105)

### More Than Two Triangles Share an Edge

**Issue:** The following error is displayed when you export assets in the CRYENGINE Exporter window, "* Failed to compile geometry in node......- More than two triangles share an edge*". It means that you might have double faces attached to each other or two faces which are attached sharing the same edge but the vertices are not welded.

*Pic6: CRYENGINE Exporter log window.*![Image](https://www.cryengine.com/docs/static/attachments/23994956)

**Resolution:** Click on the ** Modify** tab, and then under Modifier List drop down menu, select ** STL Check**.

*Pic7: Selecting STL Check from the modifier list.*![Image](https://www.cryengine.com/docs/static/attachments/25506340)

Once the STL modifier is activated, it will highlight those faces in red which needs to be fixed.

*Pic8: Highlighting edges shared in the geometry.*![Image](https://www.cryengine.com/docs/static/attachments/23994957)

### Bloated *.cgf File Size

**Issue:** When you export your asset out of 3ds Max and the exported *.cgf file size is very high.

**Resolution:** You should check if the vertex animation is turned on for the scene. If it is turned on, make sure to uncheck the box and export the asset again.

Very important! You will get no export error for that, so please check your file size.

*Pic9: Ensuring Vertex animation is turned off.*![Image](https://www.cryengine.com/docs/static/attachments/23994955)

### Degenerate Faces and Invalid Tangent-Matrix Error

When the exporter and/or editor log reports errors like these:

- [\Warning] Invalid tangent-matrix in model: objects/characters/alien/grunt/grunt_body.chr; tangent and binormal are parallel, vertex 2663 of 3545, position x=0.000000;y=-0.055068;z=1.489441
- Tangent Space Generation failed!

*Pic10: Error messages for degenerate texture.*![Image](https://www.cryengine.com/docs/static/attachments/25506110)

The errors messages mentioned above are most likely related to so called *degenerate faces*. Degenerated faces are triangles where all edges lie over each other, which looks like the triangle has no face area.

*Pic11: An overview of degenerate faces.*![Image](https://www.cryengine.com/docs/static/attachments/23994942)

For these triangles no tangent space matrix can be calculated which is necessary for all shading computations in our engine, normal mapping in particular. Also meshes with only degenerate triangles will cause problems with texture streaming because the engine cannot calculate its texel-density.

#### How to fix Degenerate Faces and Invalid Tangent-Matrix Error

To solve that problem, you need to remove such triangles from your mesh. The tricky part is that they are not always apparent, because they look like a normal edge.

In Max, we have the cryMaxTools which can find such triangles and mark them.

**To fix the errors:**

- Select the meshes that you would like to check, and then under the CryMaxTools menu, select **ToolBox.** This opens a new window with the meshes selected,

*Pic12: Selecting CryMaxTools in 3ds Max.*![Image](https://www.cryengine.com/docs/static/attachments/25506191)

2. Click on the **CryModeling** tab and then under ** Poly Tools** select** Mark Degenerated Triangles**. The tool will go through all selected objects to find degenerate triangles, and place a point helper on them.

*Pic13: Marking Degenerated Triangles in CryMaxTools.*![Image](https://www.cryengine.com/docs/static/attachments/25506339)

Also the point helper will be linked to the corresponding object and added to a new layer that contains only such degenerate triangle markers.

*Pic14: Placing point helper for the object.*![Image](https://www.cryengine.com/docs/static/attachments/23994946)

Now you can go through the point helpers one by one and resolve the degenerate triangles.

*Pic15: Few examples forresolving the degenerate triangles.*![Image](https://www.cryengine.com/docs/static/attachments/23994944)![Image](https://www.cryengine.com/docs/static/attachments/23994945)

#### More Helpful Hints

- The bounding box of a helper node is always as long as the broken face, so you get an idea of what you're looking for.
- There will always be as many helpers as degenerate triangles - having 3 helpers on the same spot, means that there are 3 degenerate triangles.
- Degenerate faces may be part of a polygon. In particular polygons with more than 4 vertices can be problematic, because 3dsmax auto triangulates them so pay attention to triangulation.

*Pic16: An overview of degenerate face in a polygon.*![Image](https://www.cryengine.com/docs/static/attachments/23994947)

Unfortunately the script cannot fully capture the behavior of the RC, so the is a small chance that it will not find all the degenerate triangles as effectively as RC.

[Asset Has No Crytek Shader Assigned](#asset-has-no-crytek-shader-assigned)[Multiple Assets Get Exported As One Big Single Mesh Instead of Separate Ones](#multiple-assets-get-exported-as-one-big-single-mesh-instead-of-separate-ones)[3DS Max Crashes Instantly During Export](#3ds-max-crashes-instantly-during-export)[More Than Two Triangles Share an Edge](#more-than-two-triangles-share-an-edge)[Bloated *.cgf File Size](#bloated-cgf-file-size)[Degenerate Faces and Invalid Tangent-Matrix Error](#degenerate-faces-and-invalid-tangent-matrix-error)
