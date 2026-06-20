# Vegetation 03 Bushes (Detail Bending) 3dsMax

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/24285894
- Page ID: 24285894
- Breadcrumb: Tutorials > Game and Level Design > Vegetation Tutorials > Tutorial - Vegetation Asset Creation > Vegetation 03 Bushes (Detail Bending) > Vegetation 03 Bushes (Detail Bending) 3dsMax
- Parent: Vegetation 03 Bushes (Detail Bending)

## Content

##
Overview

In this tutorial, we will be using our
**
Detail Bending
**
 system and show you the process of how to setup vertex movement through vertex paint. We will use all three vertex color channels to control different movement behaviors for the leaf geometry of our bush asset. This effect is meant to be used on vegetation objects and will help us to create a performance friendly bending effect on our bush asset. It works best for vegetation with big leaves like palm trees and fern bushes.

*
![Image](https://www.cryengine.com/docs/static/attachments/24157099)

Pic1: Final asset with underlying vertex color for this system to work
*

This system applies certain movement behaviors to vertices depending on the color you assign to them. You can change the intensity of those movement behaviors through shader parameters.
*

*

##
Tutorial Files

*

*
Source 3dsMax scene with exported CRYENGINE files:

**
[GameSDK_vegtut03_files.zip](/docs/static/attachments/25523837)
**
**
*

*
**

##
Pre-requisites for this Tutorial

Before you continue with this tutorial, make sure to have read and understood the following topics:

-

-
[How to Install CryMaxTools](../../../../../CRYENGINE%20-%20Getting%20Started/Installing%20CRYENGINE/CRYENGINE%20Plugins%20and%20Tools/Installing%20the%203ds%20Max%20Tools.md)

-
[The Basic CRYENGINE 3dsMax Workflow](../../../../../Asset%20Prep%20(External)/Asset%20Exporting%20Overview/Preparing%20Assets%20for%20CRYENGINE/Basic%20Asset%20Setup%20and%20Export%20-%203ds%20Max.md)

-
[CRYENGINE Exporter](../../../../../CRYENGINE%20-%20Getting%20Started/Installing%20CRYENGINE/CRYENGINE%20Plugins%20and%20Tools/Installing%20the%203ds%20Max%20Tools/CRYENGINE%20Exporter%20in%203dsMax.md)

-
[3dsMax Unit Scale to Match up With CRYENGINE Unit System](../../../../../Asset%20Prep%20(External)/Measurement%20Reference%20-%20(DCC%20Unit%20Setup).md)

##
Helpful Information

Make sure to keep the following things in mind while you work on your asset:
*

*

-
The distribution of polygons on the bending geometry should be as regular as possible to avoid bending artifacts.

-
All three vertex color channels have different influences on your leaf. Hence, it is crucial that they need to be viewed and edited separately.

-
Wind in CRYENGINE needs to be enabled since it influences the blue channel leaf bending and the red channel small bending amplitude. You can do this under
**
Environment
**
 in the
**
Rollupbar
**
 by changing the wind vector to something like 1,0,0.

-
Place the asset as a vegetation object through the
**
Vegetation
**
 tool.

-
Bending needs to be activated in the
**
Vegetation
**
 tool.

-
Detail Bending needs to be activated in the
**
Material Editor
**
.

-
Leaves should be a separate object and not multiple objects linked to one node.

-
When vertex painting make sure your cover every vertex with black color. Then apply the dedicated RGB color. This way you can assure every vertex is colored.
*

*

##
Initial 3dsMax setup

In this tutorial, we will be creating our asset in the following directory:
*

*

-
`
<
`
*
Your_Project
*
>\Assets\
`
Objects\tutorial\vegetation\03\bush\detail_bending\
`
To being with, save your 3dsMax scene to this location. All our exported assets will be saved in there. Some of the textures that we use comes from an existing asset and the location of the existing asset will be provided later in the tutorial.

We will continue with the assumption that you have already created the asset, since this is not a 3dsMax modeling tutorial. We will begin with preparing the asset ready for CRYENGINE, assigning SubIds to the relevant polygons and configuring the material.

*

*
*

*
*
![Image](https://www.cryengine.com/docs/static/attachments/24157104)

Pic2: 3dsMax overview of the finished model
*

##
Material

First, we will configure the material for the object. In 3dsMax, open the
**
Material Editor
**
, and create a new material called
**
tutorial_detail_bending
**
.

Load in the diffuse map and normal map to the material paths. The diffuse map should contain an alpha map for the opacity. The normal map should also contain an alpha map for the PBS smoothness value.

The example file refers to the following provided tutorial textures:
*

*

-
`
<
`
*
Your_Project
*
>\Assets\
`
objects\natural\bushes\ground_cover_fern\ground_cover_fernbush_diff.tif>
`

-
`
<
`
*
Your_Project
*
>\Assets\
`
objects\natural\bushes\ground_cover_fern\ground_cover_fernbush_ddna.tif>

`
*
![Image](https://www.cryengine.com/docs/static/attachments/24157109)

Pic3: Shader parameters setup
*

*

*
In the
**
Shader Basic Parameters
**
 section:
*

*

-
Select the
**
Crytek Shader
**
.

-
In the
**
Physicalization
**
 section, do not check the
**
Physicalize
**
 check-box.

-
In the next drop-down box, select
**
Default
**
.

-
Set
**
Alpha Test
**
 to 25.
*

*
See
*
Pic2
*
 above and note the material setup in the 3dsMax material editor.
*

*

##
Export out the material

*

*
Now we have configured the material for the object with its leaf properties.
*

*

-
Make sure you have the correct material selected in the material editor (and at the parent level).

-
In the CRYENGINE exporter, click the
**
Create Material
**
 button. Save this into the same directory as the object:
*

*

-
`
<
`
*
Your_Project
*
>\Assets\
`
Objects\tutorial\vegetation\03\bush\detail_bending\
**
**
tutorial_detail_bending
**
.mtl
**
>
`

*

*
*
![Image](https://www.cryengine.com/docs/static/attachments/24157108)

Pic4: Selecting the correct material for the .mtl export
*

##
Geometry

Our geometry for this tutorial is going to be a fern bush. This plant is perfect for explaining this type of technology. Create a single big leaf mesh for your fern bush and apply the material we just created to it (tutorial_detail_bending.mtl). Make sure that the geometry of your leaf is cleanly tessellated. Otherwise bending will break. Finally use the
**
Unwrap UVW
**
 modifier to adjust its UV shell to fit around one of the leaves on the texture.

*

*
*
![Image](https://www.cryengine.com/docs/static/attachments/24157102)

Pic5: Geometry of the leaf
*

*

*
*
![Image](https://www.cryengine.com/docs/static/attachments/24157111)

Pic6: UV Layout of the leaf in 3dsMax. Note the leaf UVs matching the underlying texture
*

##
Adding vertex color

*

*
The next step involves painting the vertex color on our geometry. We use all three vertex colors to control different movement behaviors for the leaf geometry.
*

*

Red
 |
Creates irregular and small bending at the outsides. Black means no bending and a full 255/0/0 red means the highest amount of bending. The movement of smaller shapes itself goes back and forth on the X axis.
 |

Blue
 |
Creates slow and regular bending. Black means the highest amount of bending and a full 0/0/255 blue means no bending at all. The movement of the big shapes itself goes back and forth on the Z axis.
 |

Green
 |
Delays the start of the movement. Each green shade starts the bending at a different time to create bending variations.
 |

*

*

Note the differences between the
**
Red
**
 and the
**
Blue
**
 channels. The black value (0,0,0) effects the influence in different ways.

##
Visualizing the Vertex colors

During painting of the leaf object its best if you show its vertex colors so that vertex color edits are visible. To see them, right click on your selected object and select the
**
Object Properties
**
.
*

*

*

*
*
![Image](https://www.cryengine.com/docs/static/attachments/24157105)

Pic7: Leaf object properties selected
*

Activate the
**
Vertex Channel Display
**
 check box under
**
Display Properties
**
within the
**
General
**
 Tab . Make sure to have
**
Vertex Color
**
 selected in the drop down menu. Click
**
OK
**
 to confirm those changes.
*

*

*

*
*
![Image](https://www.cryengine.com/docs/static/attachments/24157096)

Pic8: Leaf object properties, enabling vertex color preview
*

If you keep your
*
tutorial_detail_bending
*
 material assigned to your object, vertex color will multiply with your fern bush diffuse color. To avoid this, we recommend you to temporarily assign a white default material for a pure vertex color display.
*

*
*
![Image](https://www.cryengine.com/docs/static/attachments/24157097)

Pic9: Leaf showing vertex color with temporarily assigned default white material
*

##
Adding irregular micro bending (Red Channel)

Each color will be distributed through a separate
**
Vertex Paint modifier
**
. Even though there are no order in which the colors have to be painted, but make sure you use
**
Red -> Blue -> Green
**
.
*

*

To enable irregular micro bending:
*

*

-
Add a
**
Vertex Paint modifier
**
 to the asset.

-
Make sure
**
Vertex Color
**
 in the
**
Vertex Channel properties
**
 is selected.

-
Go to the
**
Vertex Selection Mode
**
, and select all the vertices.

-
Pick
**
Black
**
 color from the color picker.

-
Paint/fill all the vertices black.
*

*
*

*
*
![Image](https://www.cryengine.com/docs/static/attachments/24157103)

Pic10: Vertex Paint modifier properties
*

Select the outer vertices on both the sides of the leaf and paint them with a full 255 red. Those vertices will get a maximum bending amplitude. Then select the vertices in between the border and the center and apply a darker red for a lower bending effect closer to the stem. This enables you to achieve a bending amplitude falloff from the outside to the inside of the leaf. In this case we will use a
red with a value of
128 . Ensure that the middle line should always stay black. Small and irregular movement should only happen at the thinnest area of a leaf, its border.
Close the Vertex Paint modifier
.
*

*

*

*
*
![Image](https://www.cryengine.com/docs/static/attachments/24157106)

Pic11: Red vertex color on leaf
*

##
Duplicate the leaf geometry

*

*
In order to apply the upcoming blue and green colors, the geometry of your bush should have all of its leaves already in place. So start making copies of your leaf and place them around until you have a proper looking fern bush.
*

*

You are free to temporally assign the
**
tutorial_detail_bending
**
 material and deactivate the vertex color channel display mode while you create your bush.
*

*
*

*

You can also move UV shells to other leaves on your texture map as long as you do not change their geometry.
*

*

Creating and deleting individual vertices after a vertex paint increases the risk of information loss on those vertices.
*

*

As soon as you are finished with the geometry layout of your fern bush,  name it as
**
tutorial_detail_bending
**
.
*

*

![Image](https://www.cryengine.com/docs/static/attachments/24157100)
*

Pic12: Full fern bush with proper material assigned, vertex color deactivated and with 2 leaf UV shell variations

*

##
Adding regular macro bending (Blue Channel)

Now that we have all of our leaves with smaller edge bending applied to them, now
we can
add big leaf movements on top of that.
*

*

-
First make sure to apply a default grey material and to activate vertex color again (to help you visualize the vertex colors).

-
Add another new
**
Vertex Paint modifier
**
.

-
Again paint your entire object black (Black = Maximum movement in the blue channel).

-
Activate
**
Circular Selection Region
**
. Activate
**
Soft Selection
**
 to get a proper falloff selecting only at the middle vertices.

-
Set a 255 blue value. This will allow the leaves to move up and down but with a lower intensity towards their origin.
*

*
![Image](https://www.cryengine.com/docs/static/attachments/24157110)
*

Pic13: Bush with soft selected vertices in top view

*

*
![Image](https://www.cryengine.com/docs/static/attachments/24157095)

Pic14: Blue vertex color on leaves
*

To avoid overriding the red paint while collapsing the modifier, make sure to set its
**
layer mode
**
 in the vertex paint dialog to
**
add
**
 and then collapse the modifier.
*

*
*
![Image](https://www.cryengine.com/docs/static/attachments/24157094)

Pic15: Red color added to blue values
*

##
Adding movement variation (Green Channel)

*

*
This time through the green channel we will add time delays to the leaves movement to break up the regularity and add variation.
*

*

-
Add the last
**
Vertex Paint Modifier
**
 to your bush asset.

-
Paint your asset black and go to element mode.

-
Select the first leaf and paint it with a 255 green. Each leaf should get a different shade of green to avoid the movement for two leaves to start at the same time. Paint the next leaf in a 220 green, the one after that in a 190 green and so on. It's not neccessary to have these exact values, make sure you use different green shades for a good amount of variations.
*

*
*

*
*
![Image](https://www.cryengine.com/docs/static/attachments/24157101)

Pic16: Shades of green added to our fern bush
*

Now go to the Layer section of your Vertex Paint modifier and again select
**
add mode
**
 to combine the green vertex color with the other colors beneath. Your asset should now show all three vertex colors.
*

*

*

*
*
![Image](https://www.cryengine.com/docs/static/attachments/24157107)

Pic17: All three vertex color channels visible
*

Reassign
the
**
tutorial_detail_bending
**
 material to your object.
*

*

##
Export the Geometry

We are now ready to export our geometry to the engine. In the CRYENGINE exporter:
*

*

-
Add the root node of the asset to the export list (in this case its called
**
tutorial_detail_bending
**
).

-
Select
**
Geometry (*.cgf)
**
 from the
**
Export
**

**
format
**
 drop down list.

-
Make sure to check the box for
**
Vertex Colors.
**

-
Press the
**
Export Nodes
**
 button to export the asset into CRYENGINE.
*

*
*

*
*
![Image](https://www.cryengine.com/docs/static/attachments/24157098)

Pic18: Adding the asset to the exporter with the correct export flags checked
*

##
Continue to CRYENGINE

We have now finished the setup for the 3dsMax portion of the tutorial. To continue move to the next page where we configure the material and use the Vegetation Tool to place down some of these detail bending assets.

-
**
[Vegetation 03 Bushes (Detail Bending) CRYENGINE](Vegetation%2003%20Bushes%20(Detail%20Bending)%20CRYENGINE.md)
**
[Tutorial Files](#tutorial-files)
[Pre-requisites for this Tutorial](#pre-requisites-for-this-tutorial)
[Helpful Information](#helpful-information)
[Initial 3dsMax setup](#initial-3dsmax-setup)
[Material](#material)
[Geometry](#geometry)
[Continue to CRYENGINE](#continue-to-cryengine)
