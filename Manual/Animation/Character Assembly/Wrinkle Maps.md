# Wrinkle Maps

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/25535282
- Page ID: 25535282
- Breadcrumb: Animation > Character Assembly > Wrinkle Maps
- Parent: Character Assembly

## Content

![Image](https://www.cryengine.com/docs/static/attachments/29933229)

##
Wrinkle Map Setup in CRYENGINE

The following steps show you how to create a material for wrinkle maps in the CRYENGINE Material Editor and add an "AnimObject" in the Sandbox Editor.

-
Because the four "blend_control_01" to "..04" helper joints have been added, the skeleton *.CHR, *.SKIN and *.I_CAF files need to be re-exported. Also, check whether you need to re-export the material as well. Optionally, the "sdk_wrinkle_tutorial" material can be replaced with a new wrinkle material later on or you can change the "head_a.mtl" to work as a wrinkle material and assign the head to that material - choose what you favor most.

-
Open the CRYENGINE Sandbox Editor and go into the Character Tool and add a new skeleton to the SkeletonList. Don't forget to save the SkeletonList!

Take special care with your skeleton name and *.CHR file so that they differ from the names used in the Animated Blendshape Tutorial (if you coming from the former tutorial scene).

-
Create a new CDF and name it "sdk_wrinkle_tutorial.cdf"

-
Add the "*.CHR" to the skeleton box and add a "Skin Attachment" pointing to the "*.SKIN" file that you exported. Don't forget to activate Software Skinning!

-
Click on the shown *.CHR file to configure the "*.CHRPARAMS" file. Add and point to the directory containing the "default" animation that you have exported

-
Once the "default" animation shows up on the left pane of the Character Tool, create and save the new "*.ANIMSETTINGS" file. Skip and press "OK" in the error window (missing "Anim Events") when prompted

-
You may have to save all, exit and restart the Sandbox Editor and then re-open your new wrinkle tutorial *.CDF

-
Wrinkle Map effect is not yet supported in the Viewport of the Character Tool (CRYENIGINE 3.8.4). Hence, you will need to create a new demo level or use an existing demo level in the Sandbox Editor:

![Image](https://www.cryengine.com/docs/static/attachments/23998834)

-
You will need to place an "Anim Entity" into the scene. Drag and click the "AnimObject" from the "RollupBar" into the scene:

![Image](https://www.cryengine.com/docs/static/attachments/23998835)

-
Replace the windsock.cga in "Model" with the "sdk_wrinkle_tutorial.cdf":

![Image](https://www.cryengine.com/docs/static/attachments/23998836)

-
Inside the "AnimObject" properties, scroll down to "Rendering" and tick the checkbox for "WrinkleMap". Also, check that "Animation" is set to "default" and the "Loop" checkbox is checked (green areas in the screenshot below). Finally, when you have exported the name of your animation as "default", this will save you from typing in the right name:

![Image](https://www.cryengine.com/docs/static/attachments/23998837)

-
Finally, you now have to create the wrinkle map material. Go to the Material Editor and set up the material you have exported for the character ("sdk_wrinkle.skin"). Some options will open up first, if you have already set the "Humanskin" shader and added the "Wrinkle Normal Map" and the "Wrinkle Mask Texture" in the two "Custom" slots of the "Texture Maps" section!:

![Image](https://www.cryengine.com/docs/static/attachments/23998838)

-
You might want to tweak the "Specular" (map) settings and "Smoothness" if you want to augment the bumps.

This is not a tutorial to the "Humanskin" Shader. Please look for this very special shader in the CRYENGINE docs!

-
In addition, you should add some light. Add a CRYENGINE "EnvironmentProbe" and change the "Time Of Day" to better visualize the wrinkle map effect, otherwise the character head mesh might be badly lit:

![Image](https://www.cryengine.com/docs/static/attachments/23998840)
 |
![Image](https://www.cryengine.com/docs/static/attachments/23998841)
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

In this tutorial you have:

-
Combined your wrinkle normal maps (forehead wrinkle, eye squint wrinkle, etc.) into one
**
wrinkle normal map
**

-
Painted your wrinkle masks (forehead area, left lower eye area, etc...) into a composed
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
Setup a wrinkle map material in the "
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
