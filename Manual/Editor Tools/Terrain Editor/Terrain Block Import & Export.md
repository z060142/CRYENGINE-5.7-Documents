# Terrain Block Import & Export

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/25535304
- Page ID: 25535304
- Breadcrumb: Editor Tools > Terrain Editor > Terrain Block Import & Export
- Parent: Terrain Editor

## Content

![Image](https://www.cryengine.com/docs/static/attachments/29934092)

## Overview

Sandbox comes with a number of different options when it comes to terrain importing and exporting, including, but not limited to, exporting to FBX Terrain blocks.

[Selecting Terrain](#selecting-terrain)[Exporting To Terrain Block](#exporting-to-terrain-block)[Importing From Terrain Block](#importing-from-terrain-block)[Exporting Terrain To FBX/OBJ](#exporting-terrain-to-fbxobj)[Exporting Terrain and Objects to FBX/OBJ](#exporting-terrain-and-objects-to-fbxobj)

### Selecting Terrain

To get started, we'll select a small piece of terrain located within the Woodland sample level that ships with the CRYENGINE SDK.

To select terrain, click on the Terrain Editor on the right side of the screen. Then proceed to click **Edit->Select Terrain** to access the terrain tool.

Now, while avoiding selecting any entities/brushes in the level, drag your mouse across the terrain to form a shape.

![Image](https://www.cryengine.com/docs/static/attachments/27566828)

### Exporting To Terrain Block

As mentioned earlier, there are numerous different options available when dealing with terrain in CRYENGINE.

To get started, we're going to do the in-engine option which Exporting to a Terrain Block file (.trb). Exporting to Terrain Block will export both the terrain shape and vegetation objects within that terrain radius.

To export to Terrain Block, simply click on the "Terrain" menu and then "Export to Terrain Block". This will open up a file dialog where you can choose location and filename of your Terrain Block file.

One final step before we close Forest will be to export the terrain layers, the reason for this will be realized during the import phase. See [Layer Import and Export](/docs/static/engines/cryengine-3/categories/1114113/pages/14291305) for information on how to do this.

### Importing From Terrain Block

It is important to note that when you import a terrain block that the heightmap dimensions must match from source to destination levels.

To showcase this feature, we'll import our previously exported Terrain Block from Forest, into a brand new level.

Simply click on the Terrain menu and "Import Terrain Block" then select your.trb file which was exported in the previous section.

You'll notice by default, the terrain doesn't look quite right. This is because the terrain layers have not been imported into the new level.

If you followed the instructions earlier you should now be able to import the terrain layers and after some brief re-painting, you should have something a bit more like this:

### Exporting Terrain To FBX/OBJ

Following on from the Select Terrain section above, now that we have our terrain selected, lets export it so we can use it inside a DCC tool.

To do, click **File -> Export Terrain Area**

This will open a file dialog which allows you to save the selected terrain to either FBX or OBJ file formats.

Let's see how it looks inside 3ds Max!

### Exporting Terrain and Objects to FBX/OBJ

Similar to above, have your terrain area selected and then click **File -> Export Terrain Area with Objects**.

The difference with this method is not only will your terrain mesh be exported, but also any objects within the boundary of the area selection.

As you can see, in addition to the terrain mesh, assets within the bounds have also been saved to the FBX file, including the hemispherical skydome asset from the Forest level.
