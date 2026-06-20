# Blendshape/Morph

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/25535266
- Page ID: 25535266
- Breadcrumb: Animation > Character Assembly > Blendshape/Morph
- Parent: Character Assembly

## Content

[Image: /docs/static/attachments/29933223]

##
Overview

##
Sections

This section will now continue with the CRYENGINE portion of getting your assets imported from either the 3dsMax or Maya pipeline. Within this document we will explain how to add a new character into the engine using the Character Tool.

[#sections](
Sections
)
[#creating-the-character](
Creating the Character
)
[#assigning-the-material](
Assigning the Material
)
[#assigning-the-animations](
Assigning the Animations
)
[#summary](
Summary
)
[#engine-cvars](
Engine CVars
)
[#tangent-updates](
Tangent Updates
)

##
Creating the Character

Open the Sandbox Editor from your CRYENGINE folder, this will be located in:

-
**
`
<Build>\bin\win_x64\Sandbox.exe
`
**
Open the Character Tool:

-
`
**
Tools -> Animation -> Character Tool
**

`

-
The screenshot below shows the left pane split into two vertical layouts, this is activated using the icon highlighted by the red arrow and provides two viewing filters. You might want to set the lower pane to the filter "Animation" in the course of this tutorial.

[Image: /docs/static/attachments/24156142]

-
First add the new skeleton to the SkeletonList:

[Image: /docs/static/attachments/24156129]

-
At the bottom of the list, browse for the *.CHR file you have exported from Maya and give it a name. Press the save icon to save the SkeletonList.xml. You should notice the asterisk will go away ( "*Skeleton List" becomes "Skeleton List" again ).

[Image: /docs/static/attachments/24156130]

-
Create a new *.CDF file and give the CRYENGINE character an appropriate name:

[Image: /docs/static/attachments/24156126]

-
Assign your exported skeleton ".CHR" file in the skeleton section. The yellow warning boxes will help you fix what is missing to get a correct CRYENGINE character setup.

[Image: /docs/static/attachments/24156131]

-
Add a skin attachment to the skeleton *.CHR file.

[Image: /docs/static/attachments/24156134]

-
By default the Character Tool will add a "Joint Attachment". Change this to a "Skin Attachment" and browse for the *.CHR file you exported earlier.

[Image: /docs/static/attachments/24156135]

##
Assigning the Material

-
This will be the current configuration of the character. Now assign the material you have exported. We will fix the black shaded material for the head in the last step. This is because we assigned it a dx11Shader in Maya, which CRYENGINE doesn't support.

Activate the "Software Skinning" option for the blendshapes to work!
[Image: /docs/static/attachments/24156136]

##
Assigning the Animations

-
The Character Tool is missing the location of the animations (and more). A *.CHRPARAMS file will handle this. To create a new *.CHRPARAMS for this character, click on the Skeleton field - this is the area marked in red (screenshot above) and that is loaded with the *.CHR.

[Image: /docs/static/attachments/24156137]

-
Add an "Animation Set Filter" and point to the directory of your exported "default.i_caf" animation file. The *.I_CAF file is an intermediate format before compression. If you wish, you can add a new "Animation Events" after this step to get rid of the yellow warning box - just select the animation folder of the *.I_CAF.

[Image: /docs/static/attachments/24156138]

-
Browse the directory containing the *.I_CAF file(s):

[Image: /docs/static/attachments/24156139]

-
On the left you will find the associated animations with the skeleton *.CHR.

[Image: /docs/static/attachments/24156140]

-
Select the "default" animation from the left pane. You now need to add a new *.ANIMSETTINGS file and save it:

[Image: /docs/static/attachments/24156143]

-
In order for the the Character Tool to update your blendshape animation, go to the left pane - switch by double-clicking LMB on any existing *.CDF and then go back to this tutorial's *.CDF that you created. (You might need to exit and restart the Sandbox Editor and then go back to the Character Tool).

-
Browse the left pane for the saved character (sdk_blendshape_tutorial.cdf ). Select and double-click "default" animation from the bottom left (or press spacebar). You should see both the skeletal animation of the head/neck joint AND the blendshape animation playing as well:

[Image: /docs/static/attachments/24156144]

**
Tip:
**
 Check for the red marked areas (screenshot above). The options identified will help you inspect the scene you have created.

-
You may also want to correct the "sdk_player_head" material. Open the Material Editor from the Sandbox Editor and edit the material to something more useful. The Character Tool window will update the changes made:

[Image: /docs/static/attachments/24156141]

##
Summary

To conclude this tutorial, here is a list of the files you created in Maya and exported to CRYENGINE: (replace the file name if you chose to use different names):

-
saved your Maya scene file as a Maya ASCII file before export

-
exported a
**
*.SKIN
**
 file:
sdk_player_head.skin
 containing the model with skeleton and skinning data

-
exported a
**
*.CHR
**
 file:
sdk_player_head_skel.chr
 containing the skeleton hierarchy

-
**
*.CHR
**
 and
**
*.SKIN
**
 requires you to
**
export from the bind/dag pose frame
**

-
exported a
**
*.I_CAF
**
 file:
default.i_caf
 containing the animation data

-
exported a
**
*.MTL
**
 file:
sdk_player_head.mt
l containing the CE material info

In the CRYENGINE Character Tool you edited/created the following files (either by yourself or automatically by the CRYENGINE Character Tool):

-
In the default
**
SkeletonList.xml
**
in "<CRYENGINE_ROOT_FOLDER>\GameSDK\Animations" folder you added your new skeleton

-
created a
**
*.CDF
**
 file:
sdk_player_head_blendshape_tutorial.cdf
 which defines the animated CRYENGINE character

-
created a
**
*.CHRPARAMS
**
 file:
sdk_player_head_skel.chrparams
 containing the location of the related animation
**
.i_caf
**
/
**
.caf
**
files

-
created a
**
*.ANIMSETTINGS
**
 file:
default.animsettings
 containing the compression ratio for your animation

As a follow-up to this blendshape tutorial we will continue with a wrinkle map setup which will add more detail:
[/docs/static/engines/cryengine-5/categories/23756816](
Wrinkle Maps Tutorial
)

More advanced information regarding blendshape animation inside CRYENGINE can be found below - these are mostly used for debugging purposes.

##
Engine CVars

##
General CVars:

-
**
ca_vaBlendEnable
**
 1/0 - general CVar to enable/disable blend shapes on CPU.
**
default: 1
**

-
**
ca_vaEnable
**
1/0 - general CVar to enable/disable all CPU based vertex animation (including linear skinning on CPU).
**
default: 1
**

-
**
ca_vaScaleFactor
**
 1 - a multiplier scalar applied on top of the deltas.
**
default: 1
**

-
**
ca_vaProfile
**
 0/1 - displays information about the current blend vertices.
**
default: 0
**

##
Blend Culling CVars:

-
**
ca_vaBlendCullingThreshold
**
 - the higher the number then the more blend shapes will be culled (based on how many pixels they cover).
**
default: 1.0
**

-
**
ca_vaBlendCullingDebug
**
 0/1 - set to 1 to show the difference between 'with' and 'without' blend culling (by toggling the feature every other frame).
**
default: 0
**

-
**
ca_vaBlendPostSkinning
**
 0/1 - perform vertex animation blends post skinning (instead of pre-skinning).
**
default: 0
**

##
Tangent Updates

Non-rigid deformation requires tangent updates in order to obtain the correct shading. Geometric real-time tangent updates are expensive, so in order to minimize CPU cost we use vertex colors to transfer a blue (0,0,255) painted mask inside Maya that marks the most important facial parts. The budget for XBox One was ~2K vertices.

Tangent updates only work with 8 weights skinning and software skinning (Flags=8) in the .cdf file.

To enable/disable/preview the triangles marked by the mask in the ENGINE use the following CVars:

-
**
ca_vaUpdateTangents
**
 0/1

-
**
ca_debugSWSkinning
**
 3 (to display the triangles that get updated)
[Image: /docs/static/attachments/19347721]
