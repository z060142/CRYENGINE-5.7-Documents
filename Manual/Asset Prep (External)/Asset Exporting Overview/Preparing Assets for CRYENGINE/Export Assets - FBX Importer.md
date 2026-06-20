# Export Assets - FBX Importer

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/25529353
- Page ID: 25529353
- Breadcrumb: Asset Prep (External) > Asset Exporting Overview > Preparing Assets for CRYENGINE > Export Assets - FBX Importer
- Parent: Preparing Assets for CRYENGINE

## Content

## Overview

In this page, we will go over the process of using the FBX Importer inside CRYENGINE to import assets into a level using the FBX format. This pipeline effectively bridges the gap between other DCC tools, besides 3DS Max and Maya, allowing users to continue using their preferred 3D application to create content usable in CRYENGINE.

Please note that the FBX Importer supports other formats like DXF, DAE, OBJ, and 3DS, however FBX is the preferred interchange format and we will only be focusing on that.

Besides being an alternative for exporting files, the FBX Importer also offers the ability to create multiple CGF files from the same FBX file by using the exclude/include nodes functionality. In other words, you can use the same FBX file to export multiple assets.

### Helpful Information

Please note that the FBX Importer does not eliminate the need for the assets to be properly setup:

- Pivots need to be set properly.
- The geometry requires smoothing groups; otherwise, the engine will assign them for you, most likely producing undesired results.
- Proper UV mapping is necessary for any game ready asset.
- The measurement units in your preferred DCC tool must be set to use the metric system to ensure consistency with CRYENGINE units.

### Asset Setup - DCC tool

Prior to importing your asset using the FBX Importer, there are still a few steps required regardless of the 3D application you are using. Apart from a few very specific scenarios, most assets need to have LODs, proxy meshes (otherwise known as collision meshes) as well as a proper hierarchy setup between these different elements.

#### Level of detail (LOD)

For LODs, the name of the asset determines the order in which they get swapped by the engine based on distance. The parent mesh doesn't need a specific name and will always be used as LOD0. As for the other LOD meshes, CRYENGINE uses a specific naming convention such as:

- $LOD1_my_object
- $LOD2_my_object
- $LOD3_my_object

These objects should be linked to the main mesh.

Keep in mind that as opposed to the conventional export workflow, these names are not required. It is due to the fact that the FBX Importer provides the ability to flag objects as LODs as long as they are properly linked to the root object. However, using this naming convention will enable the tool to auto-detect and assign the appropriate LOD when importing an asset.

#### Proxy

As mentioned earlier, pretty much every asset needs a proxy mesh for proper collision detection inside CRYENGINE. This is usually a simplified version of your asset with a specific material assigned to it. This material should only be assigned to the meshes specifically designed as proxy meshes.

This mesh should be named in a logical way so it's easy to identify it once the asset is imported into the editor (for example My_object_proxy). As with the LOD meshes, this one should also be linked to the root object.

### Importing Static Geometry

After the initial setup is done, we are ready to use the FBX Importer to get our asset into the game. The tool is found under the **Tools** menu on the main Toolbar.

For a full description of the FBX Importer interface and functionality visit the page [FBX Import Tools](../../../Editor%20Tools/FBX%20Import%20Tools.md)**.**

To import the asset using FBX Importer:

- Go to**Tools -> FBX Import -> Static geometry**.
- In the **FBX Importer** window, go to the **File** menu and click on **Import file**.
This will open up a browser window in which you can navigate to your FBX file.
- After the file is selected, click on the **Import** button and this will load in your asset/assets and provide access to modify the objects within the file as well as a preview of the asset.

We can now continue with setting up our asset.

#### LODs

The example file doesn't use the specific naming convention for LODs so we can make use of the FBX Importer functionality to assign the appropriate value. In the LOD column (*Pic1*), select the LOD1 geometry from the drop-down list which allows you to specify the appropriate value, in our case LOD1.

Based on the above process, assign the right value to the LOD2 geometry. This is pretty much everything that you need to do in order to set your LODs properly.

*Assigning values for the LODs*![Image](https://www.cryengine.com/docs/static/attachments/25523814)

#### User Defined Properties

Most of the assets used in CRYENGINE require custom properties that enable the engine to apply certain functionalities to them. These properties are available on the right side of the FBX Importer window as soon as you select an object from the Scene explorer or viewport.

Similar to the CGF workflow, the proxy geometry needs to be physicalized in order for the engine to make use of it. We do that by selecting the corresponding proxy mesh for our asset and by enabling Physics Proxy in the Properties panel.

![Image](https://www.cryengine.com/docs/static/attachments/25523815)

#### Materials

The FBX Importer provides access to the material within the FBX file under the **Material** tab. You can change the ID for each individual sub-ID as well as its Physicalization type. In our example file, we need to select the proxy sub-ID and change its Physicalization type to **proxy only (no draw)**:

*![Image](https://www.cryengine.com/docs/static/attachments/25523818)*

The physicalization setting is the same as in the DCC exporters. If two or more source materials having different physicalization settings map to the same engine material slot, then the physicalization of that slot can be any of the two. Therefore, be careful to match the physicalization settings of materials mapping to the same slot.

It is also possible to load a custom **.mtl* file through the **Material** tab.

![Image](https://www.cryengine.com/docs/static/attachments/25523816)

The color of a source material is for previewing purposes only. Setting a source material color helps in finding vertices used in this material on the preview viewport, but does not affect the color of the exported CGF file in any way.

[Helpful Information](#helpful-information)[Asset Setup - DCC tool](#asset-setup-dcc-tool)[Importing Static Geometry](#importing-static-geometry)
