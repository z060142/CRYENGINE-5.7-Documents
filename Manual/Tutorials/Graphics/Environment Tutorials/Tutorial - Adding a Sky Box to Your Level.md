# Tutorial - Adding a Sky Box to Your Level

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/56656571
- Page ID: 56656571
- Breadcrumb: Tutorials > Graphics > Environment Tutorials > Tutorial - Adding a Sky Box to Your Level
- Parent: Environment Tutorials

## Content

##
Overview

For skies, you can use low-resolution textures (LDR) and high-resolution textures (HDR). The process to add these to your level are very similar.

##
Prerequisites for this Tutorial

-
A working version of Photoshop

-
A sky texture, either LDR or HDR

These can be downloaded from websites like
[http://www.cgskies.com](
www.cgskies.com
)
 or
[http://www.hdri-skies.com.](
www.hdri-skies.com
)
.

Save the Texture

It is also recommended to make sure the Resource Compiler is up to date and the CRYENGINE plugin for Photoshop is installed. To do this:

-
Go to
*
<engine folder>\Tools
*
and run
*
CryToolsInstaller.exe
*
.

-
If you get a Settings Manager Error about the build path not corresponding with the current build path, choose
**
Change build path to this build and install tools
**
and click
**
Continue
**
.

-
Choose
**
Install
**
.

-
Make sure the
**
Adobe Photoshop
**
 box is ticked.

-
Click
**
Next
**
.

-
When finished, close the window.

-
Open the sky texture you downloaded into Photoshop.

-
**
Save As → Format → CryTIFPlugin
**

-
Under
**
Preset
**
, choose
**
SkyboxHDR
**
 (or
**
SkyboxLDR
**
 if it is not an HDR texture).

In version 5.6 and earlier, the Resource Compiler states that the Presets used above require the texture to be a "power of 2", i.e. 1000 x 500, even when they actually are. This will then cause the RC to not complete the process of saving your texture.

This will be fixed soon, but for the moment, please use the following workaround:

-
Go to
*
<engine folder>\Tools\rc
*
 and open
*
rc.ini
*
.

-
Look for either
*
; LDR skybox textures
*
 or
*
; HDR skybox textures
*
, depending on whether you're using the LDR or HDR preset.

-
In these text blocks, change
*
powof2=1
*
 to
*
powof2=0
*
.

-
Save rc.ini.

-
Save it somewhere it makes sense, e.g. under
*
Assets/Textures/skies
*
.

If CRYENGINE is open while you save the texture, CRYENGINE will automatically compile the textures if the file is saved in the Assets folder.

If CRYENGINE is not open, you can always drag & drop the .tif file into the Asset Browser to make CRYENGINE compile the texture.

-
Wait a little while.

##
Creating a Material

-
- In the Asset Browser, create a folder (e.g.
*
Assets/Materials/Sky
*
)

- Open the folder, right-click on the
**
New Asset → Material
**
.

- Name this material (e.g. "sky").

-
Open this material and set
**
Material Settings → Shader
**
 to
**
Skyhdr
**
.

-
Assign the texture you just saved (in step 4) to
**
Texture Maps → Diffuse
**
.

-
Save the material.

-
Now, create a new Environment:

- In the
**
Asset Browser
**
, right-click and choose
**
New Asset → Environment
**
.

- Name it, e.g. "sky".

- Open this Environment, navigate to
**
Constants → Skybox
**
 and assign the material created in step 4 to
**
Material
**
 (default-spec).
Under
**
Variables → Skybox
**
, you can tweak the sky in various ways:

-
**
Rotation
**
: rotates the skybox around the X and Y axes.

-
**
Vertical
**

**
Stretch
**
: stretches the material vertically.

-
**
Color
**
: simply colors the sky texture.

-
**
Intensity
**
: takes the brightest point in the data of the texture and adjusts it to the correct brightness (brightness you would have in comparison to the sun lux intensity) compared to the brightness of the sun.

Some textures come with a recommended lux intensity that is mentioned on the website. You can simply copy and paste that value into this field.

-
**
Filter
**
: filters the colors from the sky texture and preserves them, i.e. if you choose red, this color will be preserved and all the other colors diminished.

-
**
Opacity:
**
 opacity of the texture. If you want to let something shine through the texture, e.g. the stars from the night sky, you can lower this value.

You can add volumetric clouds to your level beneath the skybox.

To activate volumetric clouds, go to the Console and type
*
r_volumetricclouds 1
*
.

##
Video Tutorial

This tutorial is also available in video form on our YouTube channel
[https://www.youtube.com/watch?v=LAnb0EjV3g4](
here
)
.

[#prerequisites-for-this-tutorial](
Prerequisites for this Tutorial
)
[#creating-a-material](
Creating a Material
)
[#video-tutorial](
Video Tutorial
)
