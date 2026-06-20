# Creating and Importing a Heightmap Using World Machine

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/25534772
- Page ID: 25534772
- Breadcrumb: Asset Prep (External) > Asset Exporting Overview > Geometry Creation Overview > Static Geometry > Creating and Importing a Heightmap Using World Machine
- Parent: Static Geometry

## Content

[Image: /docs/static/attachments/29934046]

##
Overview

##
Sections

This tutorial will show you how to create a terrain heightmap and colormap with
World Machine and
and use it in CRYENGINE.

We will use the Free version of
[http://www.world-machine.com/](
World Machine
)
 (WM) to create the content so everyone can see the process in action. The free version is limited to export out a max 512x512 image, so we will stick with these dimensions.

This tutorial is not provided to teach you World Machine, which is one procedural terrain tool on the market, but focuses on the workflow of exporting a terrain from WM to CRYENGINE.

The CRYENGINE part of this tutorial relies on textures used in the GameSDK Sample Project. We recommend that you download this from the
[https://www.cryengine.com/marketplace/product/crytek/cryengine-gamesdk-sample-project](
Asset Database
)
, import it into your Launcher, start it from there and then create a new level.

See
[/docs/static/engines/cryengine-5/categories/23756816/pages/36870288](
this page
)
 to find out how to import a project to your Launcher. (The default folder for the GameSDK Sample Project when downloaded is
`
C:\Program Files (x86)\Crytek\CRYENGINE Launcher\Crytek\gamesdk_<XXX>\GameSDK
`
)

[#sections](
Sections
)
[#tutorial-files](
Tutorial Files
)
[#setting-up-world-machine](
Setting Up World Machine
)
[#creating-the-heightmap](
Creating the Heightmap
)
[#creating-the-colormap](
Creating the Colormap
)
[#setting-up-the-level-in-cryengine](
Setting Up the Level in CRYENGINE
)
[#importing-the-heightmap](
Importing the Heightmap
)
[#importing-the-colormap](
Importing the Colormap
)
[#finishing-off](
Finishing Off
)

##
Tutorial Files

[/docs/static/attachments/23997162](
wm_to_ce_tutorial.rar
)

##
Setting Up World Machine

First off, let's set the scale in World Machine under
World Commands -> Project World Parameters
.

Because CRYENGINE supports the standard power of 2 resolution sizes (256, 512, 1024, 2048, 4096, etc.),
**
uncheck
**
 the (+1) checkbox to make the map size 512x512.

*
Pic1: Setting the map size to 512x512 in World Machine
*

[Image: /docs/static/attachments/25523523]

With it now displaying 512 x 512 resolution, click
OK
 to save and close the dialog.

##
Creating the Heightmap

Double click the
Height Output
 node on the WM graph (red box on the right). This is where we are going to pick the output file type.

CRYENGINE supports 4 of the different file types that you can directly export out from WM. One low precision 8-bit BMP, and three higher precision 16-bit images RAW16, PGM and TIFF.

Always use 16-bit variations, as they give much better terrain quality than 8-bit BMP format, which suffers from a lot from "
[http://en.wikipedia.org/wiki/Terrace_%28agriculture%29](
terracing
)
".
*
Pic2: Supported file types
*

[Image: /docs/static/attachments/25523524]

We will use the
RAW16
( or "
.r16
" in Windows Explorer) file type.

Specify the location where you want to save it and click the
"W
rite output to disk!"
button to create the file. We are now ready to create the colormap.

##
Creating the Colormap

Next we are going to have to add a few more nodes into the WM graph. These will allow us to save out the file, color the colormap and preview the data in WM before we export.

-
First we will add the
Bitmap Output
 node to export out the image we want. This can be found in
Devices -> Output -> Bitmap Output
.

-
Then we also need a
Colorizer
node. This allows you to select from a bunch of presets that will distribute the color over the terrain. To add this, go to
Devices -> Converters -> Colorizer
.

-
Finally we have the
Overlay View
node. While it's not required, it helps you visualize the height and color maps together inside WM. This is also found in
Devices -> Output -> Overlay View.
Connect them up as shown below, with the logic coming out of the back of the Terrace node.

*
Pic3: Node connections
*

[Image: /docs/static/attachments/25523525]

##
Colorizer Node

Inside the colorizer node (double-click to open) you can pick one of the presets from the drop-down list to get you started. This is enough for now to apply some color onto the terrain.

*
Pic4: Picking preset in colorizer node
*

[Image: /docs/static/attachments/25523526]

##
Bitmap Output Node

Double-click the
Bitmap Output
node to open its properties. The file type that CRYENGINE accepts for the terrain colormap is
BMP
.

Set the File Format to BMP. Click the
**
W
**
**
rite output to disk!
**

button to create the file then click OK.

*
Pic5: Bitmap Output properties
*

[Image: /docs/static/attachments/25523529]

##
Overlay Node

This last node doesn't create any files for CRYENGINE to use, but is very helpful in WM to visualize what you are creating. It overlays the colormap onto your heightmap (if you set it up that way), to give you a preview of the terrain you are creating.

Simply add the HM (heightmap) and CM (colormap) to the inputs of the node (they will only go in one way). Now press
F8
 (3D View) to see the terrain rendered with the colormap applied on top.

Now is a good time to
save
 your World Machine project.

You have now created all the files you need for CRYENGINE; we have created from World Machine:

-
image.bmp
 (8bit colormap)

-
output.r16
 (16bit heightmap)

-
project.tmd
 (World Machine file)

##
Setting Up the Level in CRYENGINE

##
Open Sandbox and Create a New Level

In Sandbox, create a new level (
File -> New
) and select from the settings a terrain resolution of
512x512
 to match the terrain size we just exported from World Machine.

Also set the
Meters Per Unit
 value to 1 (this is the multiplier we use to make a terrain bigger than the imported source image).

*
Pic6: Creating a new level
*

[Image: /docs/static/attachments/26512231]

Heightmap size

 |
Multiplier

 |
Resulting terrain size

 |

512

 |
1

 |
512m x 512m

 |

1024

 |
1

 |
1024m x 1024m

 |

2048

 |
1

 |
2048m x 2048m

 |

512

 |
2

 |
1024m x 1024m

 |

1024

 |
2

 |
2048m x 2048m

 |

2048

 |
2

 |
4096m x 4096m

 |

What this means is that on a multiplier of x1 level, the distance between each point on the HM is 1 meter. On a x2 level, the distance is 2 meters per vertex. So as you increase this multiplier, you are spreading out the vertices on the HM, and it is trading off its detail vs space covered.

##
Importing the Heightmap

##
Import the heightmap

Open the
Terrain Editor
 (On the right of the viewport in the default UI, or in
Tools -> Terrain Editor
). Then inside the Terrain editor go to
File -> Import Heightmap
.

Pick the heightmap (hm.r16) file we just created from WM (by default it should be in:
`
 Documents\World Machine Documents
`
) and click
OK
.

Now you probably can't see it, you will have to fly out to see more of the level, but eventually you will see something like this:

*
Pic7: Imported heightmap
*

[Image: /docs/static/attachments/25523531]

The terrain above is the heightmap included in the sample files; the one you made in WM earlier will most likely look different.

##
Set Terrain Max Height

What has happened here is that the XY dimensions are correct (we set them to 512x512). But the Z value is too high.

To get this into a more usable heightmap, we need to go to the
Terrain Editor
 and choose
Edit -> Set Terrain Max Height
.

Give it a low value of
128
. The top of the terrain will clip off, in the 3D viewport, but this is OK as we are about to re-import it again.

What this is doing is setting the white point (255) of the greyscale heightmap to a maximum of 128m in the engine.

Now re-import the heightmap again and notice how we have lost the huge cliff faces and acquired a flatter landscape, due to setting a reasonable value for the height.

*
Pic8: Re-imported heightmap
*

[Image: /docs/static/attachments/25523533]

Jump in game and try it out (
Ctrl+G
). This is the best way to get an idea of the scale of the world you are creating.

##
Importing the Colormap

Currently we are using the default terrain material (black and white checkbox). To change the terrain texture, we need to change two things: the
low detail
 and the
high detail
 texture and materials. See
[/docs/static/engines/cryengine-5/categories/23756816/pages/35849146](
Terrain Editor
)
 for more information.

-
Low Detail
 - This is what you see in the distance when looking at your terrain. It is based off of the colormap.

-
High Detail
 - This is what you see close to the camera. When you look at the floor, you will see nice high detail textures. The engine handles the transition between the two textures, based on distance from the camera.

##
The Low Detail Texture

First we will replace the low detail texture.

In the Terrain Editor, go to
File -> Export/Import Terrain Texture
. This opens up a new window with a top-down overview of the entire level.

*
Pic9: Importing Terrain Texture

*
[Image: /docs/static/attachments/26512232]

-
Click on the image (with 256 in the middle). This is one terrain texture tile, currently set to
256
 which is ½ of our terrain texture resolution. Click the
Change Tile Resolution
 button and pick
512x512
 from the drop-down list. If nothing happens, make sure you have highlighted the tile by clicking on it (it will show as grey when selected).

-
This has now set our terrain texture resolution to the same as our heightmap and also the same size as the texture we exported out from WM. You must make sure that the texture dimensions are the same as the tile resolution, otherwise it will produce an error.

-
With the tile still selected, click
Import
 and select your terrain texture created from WM. Once selected, click
Close
on the

Import tool and the terrain color will update. Fly up high and check the alignment of the colormap on the terrain. Is it rotated? Does the snowy part follow the highest ridge in the map? If not rotate the image 90 degrees clockwise in Photoshop.
Now your terrain should look something like this:

*
Pic10: Colormap imported
*

[Image: /docs/static/attachments/25523535]

You may notice the current output is too bright. To darken, simply adjust the Colorizer node settings in WM.

##
The High Detail Texture

In the Terrain Editor, click the Paint button at the top:

*
Pic11:
*
Paint button
*
*

[Image: /docs/static/attachments/25497055]

This is where you set and assign the different grasses, rocks, earth textures to be seen up close by the player.

What makes a material a "terrain material" is the applied shader. Every material in the included
`
Materials/terrain
`
 folder uses the
Terrain.layer
 shader. You can only apply these materials to the terrain layers.

If you create your own terrain textures/materials, make sure you set the shader type to
Terrain.layer
 from the default
 Illum Shader.

We will add two layers to the terrain texture. One to cover the flat areas (grass). And another to deal with slopes (rock faces). These can all be defined here. We'll also apply a set of rules to each terrain layer such as min/max angle and min/max height.

-
Select and highlight the first layer in the list (default) and click the
Folder
 button next to
Material
 at the bottom:
*
Pic12: Material folder button
*

[Image: /docs/static/attachments/25497057]

-
This will let you select a material for your layer. Browse under the
`
Materials\terrain
`
 folder and you can see the available terrain materials.

-
Select or highlight in the material editor
grass_1
 and click
Open
. This will apply that material to the terrain layer.

-
Double-click on the name of the layer at the top of the Terrain Editor (currently "Default") and give it a name that represents the material applied to the layer, like "Grass". This is only for your benefit when you come to painting with these layers later on.

-
Now we will define some rules to this terrain layer. We will only change the
Max Angle
 here to
30
 degrees, so when we paint with this layer later, it will not try to paint on any surface slope that is greater than 30 degrees.
As this material was applied to the default terrain layer, this has now flooded the entire terrain with this material. As a good workflow practice, make sure to pick a generic texture such as grass or mud that will be seen everywhere, until you paint down the new texture you want in its place.

-
Next we will add another Terrain Layer. Right-click in the section of the Terrain Editor where your "Grass" layer is and choose
Create Layer
. Give it the name "Rock".

-
Click once again on the
Folder
 button and pick a rock material like
cliff_island_3d
.

-
Define the rules once again, but this time set the
Min Angle
 to
30
 degrees.

-
Right click on the name of the layer at the top of the Terrain Editor and select
Flood Layer
.
So to recap... grass covers 0-30 degrees, and the rock material covers 30-90 degrees. Without overwriting each other.

##
Painting Terrain Layers

In the lower half of the Terrain Editor, you can click the Paint button to activate terrain painting mode:

*
Pic13: Terrain Paint button
*

[Image: /docs/static/attachments/25497058]

At the top of the panel, you can see a list of the terrain layers, "Grass" and "Rock". As you click between the two layers, you will notice the Slope Rules change between the different layers (what we just set up):

*
Pic14: Layer painter
*

[Image: /docs/static/attachments/25523536]

By default, the Layer Painter will paint both the High and Low terrain textures at once. Since we created our low detail texture in WM we do not want this to happen.

There are 3 ways to apply the terrain textures inside this tool.

-
Paint both high and low detail at once (Default mode).

-
Paint high detail only.

-
Paint low detail only.

##
Painting High detail Only

This is the method we want to use as we do not want to paint the low detail texture, as this was created in WM (the colormap).

To achieve this, set the
Hardness Slider
down to
 0
.

This will then only paint the high detail textures (the materials we assigned earlier (
grass_01
 and
cliff_island_3d
).

Now you can paint down the terrain layer safely without overwriting the texture we imported from WM.

##
Painting low detail Only

To overwrite the texture we imported from WM, without adding the high detail,
uncheck
 the
Paint Layer Id
checkbox
.

Also set the
Hardness Slider
back to
 1
. Or if you just need to adjust the texture slightly, set the slider to something in-between 0 - 1 depending on how much you want to overwrite (think opacity).

Now using the
Paint High Detail Only Method
 above, select the "Rock" layer and set the brush radius to something big and paint over the entire terrain in 1 go.

This has now obeyed:

-
The slope rules set down earlier.

-
Only detail texture painted down.

##
Finishing Off

To complete this tutorial and make this playable in the game launcher, we will do a few more things.

##
Generate the Terrain Texture

Now we have our terrain Heightmap and Colormap in the engine, we just need to generate the terrain surface texture and we are done.

To do this, in the
Terrain Editor
, go to
File -> Generate Terrain Texture
:

*
Pic15: Generating the terrain texture
*

[Image: /docs/static/attachments/25523538]

[Image: /docs/static/attachments/25523539]

Accept the defaults. Click
OK
 and it will generate the texture.

##
Export to Engine

Now you are finished importing a terrain heightmap and Colormap from WM to CRYENGINE.

File -> Save
 your work, then
File -> Export to Engine
.

##
Result

Now with some quick vegetation distribution, some Environment Editor tweaks, adding a skydome and you should have something like this:

*
Pic17: End result
*

[Image: /docs/static/attachments/25523543]

The aforementioned grass material was switched out for a more 'dry/dirt' material to suit the brown colormap.
