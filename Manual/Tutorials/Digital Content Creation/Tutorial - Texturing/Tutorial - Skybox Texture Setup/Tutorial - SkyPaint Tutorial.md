# Tutorial - SkyPaint Tutorial

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/23308606
- Page ID: 23308606
- Breadcrumb: Tutorials > Digital Content Creation > Tutorial - Texturing > Tutorial - Skybox Texture Setup > Tutorial - SkyPaint Tutorial
- Parent: Tutorial - Skybox Texture Setup

## Content

##
Overview

After completing this tutorial, you will be able to create a skybox with SkyPaint, but the textures themselves will still need to be organized a certain way in order to be recognized in Sandbox correctly.

##
Getting Started

While it is possible to create a skybox using 3ds Max, this tutorial only describes the use of the SkyPaint tool for creating skyboxes.

The first step is to install
[SkyPaint](http://www.skypaint.com)
 and its Photoshop plugin in the right directory.

The Photoshop plugin is required, as SkyPaint itself is nothing more than a viewer/projector for the image files, which exports/exchanges everything with Photoshop.

SkyPaint will project planes properly onto a cube, stretching and distorting the planes like a lens so that it is impossible to spot the seams at the edges of the box. Skybox shows a globe, while it is in fact just a distorted cube.

To help you get an impression of how it works, look at the following picture:

![Image](https://www.cryengine.com/docs/static/attachments/23999867)

The upper two shots are the 2D planes/faces that get exported from SkyPaint. As you can easily see, they are distorted at the outer edges, especially near the corners.

The lower screen shows the same area as a projected cubemap. It should be visible that the projection helped make this cubemap not look so cubic, so you can rotate around and won't recognize the corner areas.

The big problem with the projection based system is that the more often the view is changed and projected, the more blurry it will get. So, try to limit the use of it, and finish your work while avoiding moving between SkyPaint and Photoshop. If you really need to, you can avoid blurring by using bigger sized working files (2048x2048 per face).

##
Preparing the Cubemap

Open SkyPaint and select file/new to generate a new skymap. It will ask you about the size and you can assign some predefined templates.

Change this size to 2048x2048 and press
**
enter
**
 (no need for a template). Now select
**
file/save as
**
 and save it as a targa (.tga) file, under a name that is easy to remember.

SkyPaint now creates 6 different pictures for each side of a cube with a specific name. As soon as it's saved, close SkyPaint.

Now open Photoshop and create a new image with a height of 1024 and a width of 2048. Fill this image up with red color. Now, extend the canvas to a height of 2048 and color the new part with black.

![Image](https://www.cryengine.com/docs/static/attachments/23999868)

You now have an image split into 2 equal parts. The line where both parts touch is the horizon and more or less the area where you should start to work on.

Now save this image over all tga´s with "_LF","_FR", "_RT" "_BK" in their names. You have now replaced the 4 sides (left, front, right, back) of the cubemap. Now re-color your image fully red and save it as "_UP", for the top part of your cubemap.

Just keep the original "_DN.tga" as it is so that you can easily see the corners while watching the skybox with SkyPaint.

You now have the perfect base for starting to work on your skybox.

While you're working, you should have Photoshop and SkyPaint running at the same time.

##
Using SkyPaint and Photoshop

Start SkyPaint and open your saved file, and you will see the skybox.

![Image](https://www.cryengine.com/docs/static/attachments/23999866)

If you click and keep holding the left mouse button at the viewport window you can move around and change the view. The arrow buttons have the same functionality.

As soon as you have found the area where you want to work on, click on the painting icon (or hit the enter key) on top of the viewport. You will be prompted to give dimensions for the projection. Type in 2048x2048 and proceed with
**
OK
**
. SkyPaint will transfer the bitmap data over to Photoshop. Photoshop will pop up and you can continue working there.

Now, you can paint freely, insert photos, apply gradients and all the other things that you will need to do to create your sky. The only limitation is that you need to collapse all your layers as soon as you are finished because SkyPaint will only accept the background layer for the transfer back.

You can transfer your work back to SkyPaint by starting the SkyPaint plugin using the filter menu of Photoshop. Now the bitmap data gets transferred back to SkyPaint and you can see the result.

You will have to constantly switch between both programs, changing the view with SkyPaint and painting in Photoshop on the target area.

##
Preparing for use in Sandbox

In order for your skybox to properly be recognized in Sandbox you will need to save the files in a certain way, please refer to
[Skybox Texture Setup](/docs/static/engines/cryengine-5/categories/23756816)
 for more information.
