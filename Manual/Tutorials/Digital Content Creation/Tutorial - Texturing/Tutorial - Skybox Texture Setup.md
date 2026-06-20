# Tutorial - Skybox Texture Setup

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/23308605
- Page ID: 23308605
- Breadcrumb: Tutorials > Digital Content Creation > Tutorial - Texturing > Tutorial - Skybox Texture Setup
- Parent: Tutorial - Texturing

## Child Pages

- [Tutorial - SkyPaint Tutorial](Tutorial%20-%20Skybox%20Texture%20Setup/Tutorial%20-%20SkyPaint%20Tutorial.md)

## Content

##
Overview

A Skybox is a cube without the bottom side which contains the environment around a scene, for example the sky or distant mountains. The cube is viewed from inside and usually only the upper half of the cube is seen, so it is enough that the upper half of the cube sides is textured.

In CryENGINE three square textures are used to define the cube sides. One for the top cube face (using suffix _
*
5
*
 in the filename) and two textures which contain the images of the four side faces (using prefixes _
*
12
*
 and _
*
34
*
).

The following images show the required layout of the sky textures:

![Image](https://www.cryengine.com/docs/static/attachments/23999861)

*
skybox_
**
12
**
.tif
*
 (front and right faces)

![Image](https://www.cryengine.com/docs/static/attachments/23999863)

*
skybox_
**
34
**
.tif
*
 (back and left faces)

![Image](https://www.cryengine.com/docs/static/attachments/23999864)

*
skybox_
**
5
**
.tif
*
 (the top face)

![Image](https://www.cryengine.com/docs/static/attachments/23999862)

*
Resulting hemisphere layout (looking upward into the sky)
*

Final result should look like this (without the letters):

![Image](https://www.cryengine.com/docs/static/attachments/23999865)

##
Using a Static Skybox

In order to use a skybox instead of the dynamic HDR sky, go to the
**
Environment
**
 tab in Sandbox and select a material in the SkyBox section which uses the Sky shader (not SkyHDR, as this will use the dynamic HDR sky).

You can apply any of the three skybox textures to the diffuse texture slot of the material. Because this is a simple cube texture rendering, the majority of shader/material options will have no effect on the skybox rendered. Just 100% opacity and a diffuse texture is all that is needed.

Please note that in contrast to the HDR sky, a skybox is static and does not work with changing time of day settings.

##
Tips

-
Very soft gradients suffer from DXT compression a lot. Either you avoid compression (much more texture memory required) or you add some noise to the image. That can also benefit uncompressed textures.

-
Painting textures with very soft gradients should be done with higher precision (e.g. Photoshop 16bit instead of 8bit).

-
Based on memory constraints and target resolution, you should carefully decide on the compression format, whether mipmaps are on or off and the texture resolution.

-
The rendering assumes that the pixels on the edges and corners are replicated on the other side. DXT compression is done for a 4x4 pixel block and that can cause further issues. Often this can be fixed by an artist.

-
If your skybox textures are showing up very blurry when applied to your sky that is likely because they have mips applied. Be sure that you are saving your textures without any mip mapping applied.

-
To learn how to create textures for a new skybox, see the
.
