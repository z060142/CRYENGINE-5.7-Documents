# Tutorial - Wrinkle Map Setup

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/44959598
- Page ID: 44959598
- Breadcrumb: Tutorials > Digital Content Creation > Tutorial - Wrinkle Map Setup
- Parent: Digital Content Creation

## Content

##
Overview

This article continues from where we left off in the Animated Blendshapes Tutorial. It covers how to set up wrinkle maps to enhance an existing animated blendshape scene in Maya and export to CRYENGINE. It relies on the knowledge acquired in the
[/docs/static/engines/cryengine-3/categories/1114113/pages/21268612](
**
Animated Blendshapes tutorial
**
,
)
 which is a necessary precursor to this Wrinkle Maps tutorial.

[Image: /docs/static/attachments/44959632]

Normally, wrinkle maps are added to a blendshape animation to add details to a human face. CRYENGINE currently supports 12 wrinkle masks and 1 wrinkle normal map that are controlled by 4 "blend_control_01" to "..04" joints (as helper objects to hold the animated data when a wrinkle area blends in and out).

CRYENGINE looks for the exported joints "
**
blend_control_01
**
" to "..
**
04
**
" and their "
**
.translate
**
"
**
attribute
**
 and blends the wrinkle masks in and out.

##
Tutorial Files

Source Maya ASCII scenes with exported CRYENGINE files:

**
[/docs/static/attachments/44959635](
sdk_wrinkle_map_tutorial.zip
)
**
 (39mb)

(Do remember that you still need to have a modified "SkeletonList.xml" where you have added the skeleton CHR from this tutorial. Just in case you want to skip all these steps and want to open the character in CE Character Tool:
**
[/docs/static/attachments/44959636](
SkeletonList.zip
)
**
 )

From engine version 5.6 onwards, the skeleton list is not used anymore, which means that you
 can ignore any references to it on this page.

Backup your "SkeletonList.xml" before overwriting it!

##
Setup Your Wrinkle Normal Map

This is not an in-depth tutorial on how to sculpt your high resolution and in-game meshes! Normally, your high resolution wrinkle sculptures would be based on your neutral-posed sculpture in ZBrush, MudBox or 3d-Coat. After that, you have to bake the wrinkle normal maps. What is shown in this article are the results you need and the current way that CRYENGINE handles the base Normal Map (left image below) and the Wrinkle Normal Map (right image below):

[Image: /docs/static/attachments/44959628]

[Image: /docs/static/attachments/44959629]

Depending on your workflow, you must combine the different wrinkle normal maps onto the base normal map.

Before you blend normal map layers in Photoshop using the "Overlay" blend mode, you may want to search Google for how to correctly combine normal maps.

This tutorial is designed to demonstrate the tech, hence some elements shown such as a perfect wrinkle normal map may not be as they would be in a game production environment.

##
Setting Up Wrinkle Masks

The mask texture being used to define the areas and ranges to be influenced by wrinkles is an 8-bit per channel, 32-bit *.tif file (this includes the alpha channel).

The different channels, red, green, blue and the alpha channel, have been split into ranges so that more than 3 or 4 channels can be addressed independently and drive different areas on the face. Therefore,
you have 12 wrinkle areas that you can control.

Presently this is "hardcoded", so if you use more than 3 Channels per map channel, code changes will be necessary.

The different ranges are evenly distributed on the channels - from 0 to 255 with a gap of 20 in between the first and second ranges and a gap of 10 in between the second and third ranges. This prevents the channels from mixing into each other.

##
Setup Tables

The 1st column depends on your preferences and how you as a Setup Artist want to drive the blend_control_01 - 04 helper joints.
**
CRYENGINE just reads the
translate values
 of
blend_control_01 to 04
 to drive the wrinkle mask.
**
This is all that CRYENIGNE needs, however make sure that you map the driver attribute to the range of values [0.. 100], such as using a "multiplyDivide" node as in the former Animated Blendshape Tutorial:

[Image: /docs/static/attachments/44959604]

##
Setup Table for the Maya Setup Artist

Maya (blendShape) Node Driver Attribute

 |
Maya Helper Joint Name

 |
Joint Attribute

 |

forehead

 |
blend_control_01

 |
.translateX

 |

glabella (nose bridge area)

 |
"

 |
.translateY

 |

left cheek (smile)

 |
"

 |
.translateZ

 |

left lower eye squint

 |
blend_control_02

 |
.translateX

 |

left crow's feet wrinkles

 |
"

 |
.translateY

 |

... (whatever face area)

 |
"

 |
.translateZ

 |

...

 |
blend_control_03

 |
.
translateX

 |

...

 |
"

 |
.
translateY

 |

...

 |
"

 |
.
translateZ

 |

...

 |
blend_control_04

 |
.
translateX

 |

...

 |
"

 |
.translateY

 |

...

 |
"

 |
.
translateZ

 |

##
Setup Table for the Photoshop/Texture Artist

Maya (blendShape) Node Driver Attribute

 |
RGB Colors as Mask

 |

forehead

 |
Red: 0-75

 |

glabella

 |
Red: 95-170

 |

left cheek (smile)

 |
Red: 180-255

 |

left lower eye squint

 |
Green:
0-75

 |

left crow's feet wrinkles

 |
Green:
95-170

 |

... (whatever face area)

 |
Green:
180-255

 |

...

 |
Blue:
0-75

 |

...

 |
Blue:
95-170

 |

...

 |
Blue:
180-255

 |

...

 |
Alpha:
0-75

 |

...

 |
Alpha:
95 - 170

 |

...

 |
Alpha:
180 - 255

 |

##
Setup the Content in Photoshop

Open Photoshop and paint the masks according to the color ranges in the setup table for Photoshop/Texture Artist. For the mask in this tutorial Red 255 has been used for the cheek mask, a Red 170 for the nose wrinkle mask and a Red 75 for the forehead mask.

Don't blur the wrinkle mask edges against an incorrect colored background!

Set the right background color displayed below when you paint the fade in/out mask edges:

-
**
**
Red 180-255:
**
**
use an RGB (180,0,0) colored background layer

-
**
**
Red 95-170:
**
**
use an RGB (95,0,0) colored background layer

-
**
Red 0-75:
**
use an RGB (0,0,0) colored background layer

-
Repeat this for the Green, Blue & Alpha ranges and merge the color masks to their individual RGBA channels in Photoshop

##
How to Paint the Mask Ranges in Photoshop:

-
For each of the four channels (RGBA) create three pairs of foreground (FG) and background (BG) layers - this is a total of six layers for each channel (the red channel is listed below:

**
Pair Red 1:
**

FG layer with Red Value -> 255

BG layer with Red Value -> 180

**
Pair Red 2:
**

FG layer with Red Value -> 170

BG layer with Red Value -> 95

**
Pair Red 3:
**

FG layer with Red Value -> 75

BG layer with Red Value -> 0

[Image: /docs/static/attachments/44959624]

-
Repeat the above process for the green, blue and alpha channels.

-
On the FG layer "lasso-select" the wrinkle area, e.g. the forehead wrinkle area and then use the selection as a mask.

-
Add an "Inner Glow" Layer Style F/x. In the "Inner Glow" pick the corresponding BG red color and set up the other options as shown below, however feel free to change things as you desire. However, the result should be a smooth "blend in" edge:

[Image: /docs/static/attachments/44959623]

-
Copy the FG and BG pair RED layers and collapse them. Re-apply the corresponding mask from the selection and move it to a new group folder:

[Image: /docs/static/attachments/44959621]

-
Repeat this process for the other two RED ranged areas plus the green, blue and alpha ranges as well.

-
At this point you might want to shift the order of the collapsed layers.
If you're having problems removing the sharp edges of the mask (you'll notice them later on in CRYENGINE), then reduce the image resolution of the mask texture, e.g. Wrinkle Normal Map: 2048 x 2048 -> Wrinkle Mask: 512 x 512.
This is what the final result for the RED masked area looks like in Photoshop:

[Image: /docs/static/attachments/44959626]

##
Export to CryTif:

-
Next, export the mask texture as a CryTif.

Be careful to choose the correct CryTif export preset. You must export the wrinkle mask in
**
linear color space
**
to CRYENGINE. Use the "
**
WrinkleMask_Linear
**
" preset in CryTif.
At the time of writing the Preset is not yet submitted. Replace your "rc.ini" (use Search inside your CRYENGINE root directory) with this one:
**
[/docs/static/attachments/44959638](
rc.ini
)
**
or add these lines to the bottom of your
**
rc.ini
**
:

[WrinkleMask_Linear]

pixelformat=A8R8G8B8

powof2=1

mipmaps=1

colorspace=linear,linear

 |

-
The images below are a sample image (i.e. if you used all 12 masks). The right image only displays the RED channel:

[Image: /docs/static/attachments/44959637]

[Image: /docs/static/attachments/44959634]

##
Setup the Content in Maya

-
In Maya you need to create four "blend_control_01" to "blend_control_04" joints. Parent them under the "root" joint of the export hierarchy as shown below:

[Image: /docs/static/attachments/44959630]

-
If you are coming from the Animated Blendshape Tutorial, you must rename your two "cryExportNode" and the underlying "_group" accordingly. This avoids a collision with the name of the former skeleton *.CHR:

[Image: /docs/static/attachments/44959631]

-
These joints have input connections into their respective ".translate" attributes. The attributes may be fed by any node output, normally the ".weights" attribute of a blendShape node or some "Set Driven Keys". The ".translate" attribute values are to be mapped from [0.. 1] to [0 to 100] and back to [0.. 1] as shown below. ("blend_control_02" to "blend_control_04") are left untouched because we only have 3 blendshapes plugged into "blend_control_01.translateX", ".translateY" and ".translateZ" ). Finally, you have to create the multiplyDivide nodes and the connections in the Node Editor as shown in the screenshot below:

[Image: /docs/static/attachments/44959633]

Check the bookmarks of Maya Node Editor where the upper graph layout has been saved.

-
If you want to set up all 12 wrinkle mask area, you need to create the other three multiplyDivide nodes and plug them to "blend_control_02" ".tx" to ".tz" attribute.

The following steps (5-8) are not necessary for CRYENGINE wrinkle maps to work - they are for previewing your animation. Therefore, you may want to jump to step 9 of this section where the final wrinkle map scene is exported from Maya.

-
Before moving on to the shader elements in Maya, make sure that you are set to Maya's "Viewport 2.0". Load the "dx11shader" and "shaderFX" plugins, set the rendering engine to "DirectX 11" and the viewport renderer to "Viewport 2.0". (You must restart Maya after these steps!):

[Image: /docs/static/attachments/44959618]

[Image: /docs/static/attachments/44959622]

[Image: /docs/static/attachments/44959619]

[Image: /docs/static/attachments/44959620]

-
Open Maya's HyperShade. In order to help visualize the wrinkle map effect being animated a "Shaderfx" and "dx11Shader" material has been created for Maya 2015+. Search for the Shaderfx material and use the Attribute Editor to open the Shaderfx Window:

[Image: /docs/static/attachments/44959616]

-
The Shaderfx material only has 3 wrinkle masks. These are extracted from the mask layers that were created in Photoshop earlier, however you can duplicate the "Texture Map", "Float", "Multiply" and "Add" nodes and add more masks and reconnect them to the node graph yourself:

[Image: /docs/static/attachments/44959627]

Some notes regarding the ShaderFX wrinkle shader:

-

-
The three "Float" value nodes (named as <WRINKLE_NAME> + "_Amount") on the left side of the ShaderFX window of Maya have been exposed. They will be driven by the ("blend_control_01" + ".translate") attribute

-

-
The color/diffuse/specular related nodes can be replaced by a simple grey color if you just want to focus on the wrinkle stuff

-
A "Float" node named "Global_Wrinkles_Amount" has been added to control all wrinkles globally

-
All normal values have been clamped in the range of [0.. 1]

-
In some cases you must re-direct all texture maps in the Shaderfx graph. Browse for the three wrinkle masks, the normal map, the wrinkle normal map, the diffuse and the specular map(s)

-
When the Shaderfx material has been completed re-import it back as a dx11Shader

-
Scrub the Maya timeline to see how the wrinkle map effect blends in and out. The screenshots below are samples from the provided Maya scene:

[Image: /docs/static/attachments/44959617]

 |
[Image: /docs/static/attachments/44959614]

 |

blendshape
*
OFF
*

diffuse map
*
ON
*

normal map
*
ON
*

**
wrinkle map
**

*
OFF
*

 |
blendshape
*
ON
*

diffuse map
*
ON
*

normal map
*
ON
*

wrinkle map
*
ON
*

 |

[Image: /docs/static/attachments/44959615]

 |
[Image: /docs/static/attachments/44959611]
 |

**
blendshape
*
OFF
*
**

**
diffuse map
*
OFF
*
**

**
normal map
*
ON
*
**

**
wrinkle map
*
OFF
*
**

 |
**
blendshape
*
OFF
*
**

**
diffuse map
*
OFF
*
**

**
normal map
*
ON
*
**

**
wrinkle map
*
ON
*
**

 |

-
Now it's time to export the assets to CRYENGINE. Open the Export tool from the Crytek shelf. Export the two crytekExportNodes, the material and the animation in crytek shelf. The screenshot below (with the red marked areas) will help you to get things exported correctly, otherwise, just open the "*_end" Maya tutorial scene:

[Image: /docs/static/attachments/44959612]

##
Setting Up the Content in CRYENGINE

The following steps show you how to create a material for wrinkle maps in the CRYENGINE Material Editor and add an "AnimObject" in the Sandbox Editor.

This tutorial relies on assets used in the GameSDK Sample Project. We recommend that you download this from the
[https://www.cryengine.com/marketplace/product/crytek/cryengine-gamesdk-sample-project](
Asset Database
)
, import it into your Launcher, start it from there and then create a new level.

See
**
[/docs/static/engines/cryengine-5/categories/23756816/pages/36870288](
this page
)
**
 to find out how to import a project to your Launcher. (The default folder for the GameSDK Sample Project when downloaded is
`
**
C:\Program Files (x86)\Crytek\CRYENGINE Launcher\Crytek\gamesdk_<XXX>\GameSDK
**
`
).

This folder will be referred to in this tutorial as the "GameSDK folder".

-
Because the four "blend_control_01" to "..04" helper joints have been added, the
skeleton *.CHR, *.SKIN and *.I_CAF files need to be re-exported. Also, check whether you need to re-export the material as well. Optionally, the "sdk_wrinkle_tutorial" material can be replaced with a new wrinkle material later or you can change the "head_a.mtl" to work as a wrinkle material and assign the head to that material - choose what you favor most.

-
Open CRYENGINE Sandbox Editor and go into the Character Tool and add a new skeleton to the SkeletonList. Don't forget to save the SkeletonList!

Take special care with your skeleton name and *.CHR file so they differ from the names used in the Animated Blendshape Tutorial (if you're coming from the former tutorial scene).

-
Create a new CDF and name it "sdk_wrinkle_tutorial.cdf"

-
Add the "*.CHR" to the skeleton box and add a "Skin Attachment" pointing to the "*.SKIN" file that you exported. Don't forget to activate "Software Skinning"!

-
Click on the shown *.CHR file to configure the "*.CHRPARAMS" file. Add and point to the directory containing the "default" animation that you have exported

-
Once the "default" animation shows up on the left pane of the Character Tool, create and save the new "*.ANIMSETTINGS" file. Skip and press "OK" in the error window (missing "Anim Events") when prompted

-
You may have to save all, exit and restart the Sandbox Editor and then re-open your new wrinkle tutorial *.CDF

-
Wrinkle Map effect is not yet supported in the Viewport of the Character Tool.
 Hence, you will need to create a new demo level or use an existing demo level in the Sandbox Editor:

[Image: /docs/static/attachments/44959602]

-
You will need to place an "Anim Entity" into the scene. Drag and click the "AnimObject" from the Create Object tool into the scene:

[Image: /docs/static/attachments/44959601]

-
Replace the windsock.cga in "Model" with the "sdk_wrinkle_tutorial.cdf":

[Image: /docs/static/attachments/44959600]

-
Inside the "AnimObject" properties, scroll down to "Rendering" and check the checkbox for "WrinkleMap".
Also, check that "Animation" is set to "default" and the "Loop" checkbox is checked (green areas in the screenshot below). Finally, when you have exported the name of your animation as "default", then this will save you from typing in the right name
:

[Image: /docs/static/attachments/44959599]

-
You now have to create the wrinkle map material. Go to the Material Editor and set up the material you have exported for the character ("sdk_wrinkle.skin"). Some options will open up first, if you have already set the "Humanskin" shader and added the "Wrinkle Normal Map" and the "Wrinkle Mask Texture" in the two "Custom" slots of the "Texture Maps" section:

[Image: /docs/static/attachments/44959608]

-
You might want to tweak the "Specular" (map) settings and "Smoothness" if you want to augment the bumps.

This is not a tutorial to the "Humanskin" Shader. Please look for this very special shader in the CRYENGINE docs!

-
In addition, you should add some light. Add a CRYENGINE "EnvironmentProbe" and change the "Time Of Day" to better visualize the wrinkle map effect, otherwise the character head mesh might be badly lit:

[Image: /docs/static/attachments/44959606]
 |
[Image: /docs/static/attachments/44959603]
 |

**
wrinkle maps
*
ON
*
**
 |
**
wrinkle maps
*
OFF
*
**
 |

##
Summary

In this tutorial you have;

-
Combined your wrinkle normal maps (forehead wrinkle, eye squint wrinkle, etc.) into one
**
wrinkle normal map
**

-
Painted your wrinkle masks (forehead area, left lower eye area, etc.) into a composed
**
wrinkle mask
**
 texture map

-
Exported the wrinkle mask texture using a
**
linear color space export
**
 preset

-
Created four "
**
blend_control_01
**
" to "..
**
04
**
"
**
joints
**
 to control the wrinkles

-
Exported the animation to an
**
*
.I_CAF
**
 file to incorporate the "blend_control_01" to "..04" animations

-
Exported the
**
*.SKIN
**
 file (to incorporate the "blend_control_01" to "..04" joints)

-
Exported the
**
*.CHR
**
 file (to incorporate the "blend_control_01" to "..04" joints)

-
Set up a wrinkle map material in the "
**
Humanskin
**
"
**
shader
**
 of CRYENGINE

-
Added an "
**
AnimObject
**
" entity in the Sandbox Editor where you activated the wrinkle map effect

[#tutorial-files](
Tutorial Files
)
[#setup-your-wrinkle-normal-map](
Setup Your Wrinkle Normal Map
)
[#setting-up-wrinkle-masks](
Setting Up Wrinkle Masks
)
[#setup-the-content-in-photoshop](
Setup the Content in Photoshop
)
[#setup-the-content-in-maya](
Setup the Content in Maya
)
[#setting-up-the-content-in-cryengine](
Setting Up the Content in CRYENGINE
)
[#summary](
Summary
)
