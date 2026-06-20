# Tutorial - Ambient Occlusion and Normal map bake using Xnormal

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/23308596
- Page ID: 23308596
- Breadcrumb: Tutorials > Digital Content Creation > Tutorial - Texturing > Tutorial - Ambient Occlusion and Normal map bake using Xnormal
- Parent: Tutorial - Texturing

## Content

##
Overview

##
What is xNormal

xNormal is a program that is widely used in the industry for baking down your high res sculpts/ high geometry meshes out of programs like zBrush, Mudbox, etc. to you low res and game ready mesh, maintaining all the detail from your high sculpt/ geometry.

The program is free available and you can download it by visiting:
[http://www.xnormal.net/Downloads.aspx](http://www.xnormal.net/Downloads.aspx)

##
How to use xNormal for normal map bakes and getting the best results

The challenge in using xNormal is to be able to get all the detail of your high res mesh onto your low res, game ready mesh and make your lower res game usable mesh appear like the high res mesh.

The defaults results will give you a pretty average result in giving you a lot of double projections and bad seams or simply that the rays won't hit your geometry at all during the bake.

By following this simple rules you'll be able to get all of your detail to your low res game ready mesh, while making it appear like the high res mesh.

##
Making sure that the low res geometry isn't too low and being able to catch all the rays from the bake

When you're creating your low res mesh, don't go too low on geometry. Always make sure that low res will catch all the curves and angles.

As a practical example, if you have a high res cylinder with 64 spans, you will get a bad bake if your low res cylinder is being only 4 spans. You low res cylinder in this example is so low that almost all the rays will miss it and giving you a very jaggy and bad bake.

Down below is an example of how low res looks like to get a nice bake.

![Image](https://www.cryengine.com/docs/static/attachments/23999585)

##
Adjusting the ray distance and default mesh scale in xNormal

Since there are a multiple of 3D software packages in the industry and being used the scale from each to the next can be very different (for an example a grid unit in Maya is different that a grid unit in 3DS Max).

To get the best result in xNormal and making sure the rays hit a big enough mesh we should set the default mesh scale in xNormal to 16. This way we make sure the mesh is big enough to catch all the rays.

We should also set the ray distance to a higher value then the default one. The default value in xNormal is 0.5 which is too low and a lot of rays miss the target and double projections occur. A good value to start out with is to set our ray distance to 50 and tweak it from there.

![Image](https://www.cryengine.com/docs/static/attachments/23999586)

![Image](https://www.cryengine.com/docs/static/attachments/23999587)

##
Baking out separate pieces of your geometry

If you're still getting double projections and bad seams, one option to fix it is to bake out separate pieces of your mesh.

The issue that arises when you bake your whole mesh at once is that the edge padding will "bleed" over into other parts of your texture map and in some cases xNormal doesn't know the differences and it projects one piece over the other. This will especially happen if you got a tight packed UV map layout.

It is a bit more of a laborious task to break up your mesh into several pieces, bake them individually and then cut and composite those in Photoshop, but it will give you a nice clean bake with no double projections and edges "bleeding" into your other parts of the texture map.

![Image](https://www.cryengine.com/docs/static/attachments/23999578)

![Image](https://www.cryengine.com/docs/static/attachments/23999579)

##
Inverting the Y- value/ green channel of the bake for CRYENGINE

In the regular normal map bake settings for xNormal, the Y channel (or green channel in Photoshop) is set to Y+. CRYENGINE and Max use the inverse, meaning a value of Y-. There are two ways to fix that problem.

The first is to go to the settings in xNormal and set the Y+ value to Y- so we'll get the right bake out of it. Many artists want to read the normal map bake with it's normal settings to understand and see where eventually issues are. Reversing the Y- in xNormal makes it hard to understand.

So the second way is to bake it out normally from xNormal and then once everything is ok, to go to the green channel in Photoshop and reverse it manually. Both ways are viable and up to personal preference..

![Image](https://www.cryengine.com/docs/static/attachments/23999597)

![Image](https://www.cryengine.com/docs/static/attachments/23999580)

![Image](https://www.cryengine.com/docs/static/attachments/23999581)

##
Using xNormal for baking out your Ambient Occlusion

With xNormal we are also able to bake out our Ambient Occlusion. To get a nice AO bake we have to tweak some settings. Preferably we want to set our Occlusion rays to 256 or higher. 256 is a good value for a 2048 x2048 image.

The higher the number on the occlusion rays the smoother and softer the AO will be, exponentially your render time will double. If you have a bigger size image like a 4096 x 4096 it is recommended that you set your occlusion rays potentially to 512, depending on how large your surfaces are.

If you have lots of smaller pieces and surfaces setting your occlusion rays to 512 won't give you much of a difference as compared to 256.

The next setting we have to adjust is the spread angle. The maximum value is 179.50. With a higher spread angle we make sure that the AO rays get wider spread hitting also the smallest gaps in our mesh and ensuring we get a nice smooth AO in those.

![Image](https://www.cryengine.com/docs/static/attachments/23999588)

##
Setting the correct Bucket size and Antialising settings

The next setting we want to change is our bucket size. Normally we used to have the smallest bucket size (16) because the general impression was that it would be more detailed because it does 16 pixels per CPU core but after doing some research we found out that the highest (512) is faster. So if you use 512 and have a quad core with 8 threads, you will see 8 render blocks trying to render 512 pixels each in one go. What we don't want set higher is our AA setting. 1x AA is enough and the difference to a 4x AA is minimal.

The same image has been rendered once with an AA setting of 1x the other of 4x. The 4x AA took 43 minutes to render! The 1x AA took only roughly 3 minutes. The difference is minimal and doesn't justify the time. Plus also once our map gets reduced in size, like from a 2048 map to a 1024 Photoshop applies AA to image as it gets scaled down.

![Image](https://www.cryengine.com/docs/static/attachments/23999591)

![Image](https://www.cryengine.com/docs/static/attachments/23999584)

![Image](https://www.cryengine.com/docs/static/attachments/23999589)

![Image](https://www.cryengine.com/docs/static/attachments/23999590)

##
Curvature Map

The best use for having a good gloss map, render a curvature map  and that use as an absolute base for the gloss map.

It provides a mid gray image with every edge highlighted where a curve is.

![Image](https://www.cryengine.com/docs/static/attachments/23999592)

To get it to render like this, you need to set up options like the image down below

![Image](https://www.cryengine.com/docs/static/attachments/23999593)

The amount of rays you should set are the same as the AO and also their spread angle is the same.

To get it to render a grey image, change the "Tone Mapping" setting to monochrome.

##
ZBrush polypaint/Vertex Colour

Some people prefer to use ZBrush polypaint to texture assets. It is important to keep in mind when you do this that the mesh be as dense as possible considering it is vertex colour based. If the high poly mesh is too low, the texturing will turn out blurry and will look very low res.

To be able to render the polypaint/vertex color it is important to turn off the "ignore per vertex color" tick box on your high poly mesh. As the option suggest, if you don't, it will completely ignore it and show you a black render.

![Image](https://www.cryengine.com/docs/static/attachments/23999594)

Now turn on the "Bake Highpoly's Vertex Colour" and asset is ready to render.

![Image](https://www.cryengine.com/docs/static/attachments/23999595)

##
Texture Baking/UV transfer

You can use Xnormal as a "render to texture" tool with the "Bake Base Texture" option.

![Image](https://www.cryengine.com/docs/static/attachments/23999596)

[What is xNormal](#what-is-xnormal)
[How to use xNormal for normal map bakes and getting the best results](#how-to-use-xnormal-for-normal-map-bakes-and-getting-the-best-results)
[Making sure that the low res geometry isn't too low and being able to catch all the rays from the bake](#making-sure-that-the-low-res-geometry-isnt-too-low-and-being-able-to-catch-all-the-rays-from-the-bake)
[Adjusting the ray distance and default mesh scale in xNormal](#adjusting-the-ray-distance-and-default-mesh-scale-in-xnormal)
[Baking out separate pieces of your geometry](#baking-out-separate-pieces-of-your-geometry)
[Inverting the Y- value/ green channel of the bake for CRYENGINE](#inverting-the-y-value-green-channel-of-the-bake-for-cryengine)
[Using xNormal for baking out your Ambient Occlusion](#using-xnormal-for-baking-out-your-ambient-occlusion)
[Setting the correct Bucket size and Antialising settings](#setting-the-correct-bucket-size-and-antialising-settings)
[Curvature Map](#curvature-map)
[ZBrush polypaint/Vertex Colour](#zbrush-polypaintvertex-colour)
[Texture Baking/UV transfer](#texture-bakinguv-transfer)
