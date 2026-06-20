# Tutorial - Ambient Occlusion with Mental Ray

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/23308602
- Page ID: 23308602
- Breadcrumb: Tutorials > Digital Content Creation > Tutorial - Texturing > Tutorial - Ambient Occlusion with Mental Ray
- Parent: Tutorial - Texturing

## Content

##
Ambient Occlusion with Mental Ray

Objects with their own texture should always have some radiosity baked in. You can do this with a skylight, but this renders very slowly and always has a light direction in it.

With Ambient Occlusion, on the other hand, the areas occluding each other are rendered more darkly and independently of a lightsource.

[Image: /docs/static/attachments/23999836]

You can use the render to texture function to bake the occlusion.

First, open your render settings and set the renderers to mental ray:

[Image: /docs/static/attachments/23999841]

Then, create a material with a mental ray shader:

[Image: /docs/static/attachments/23999842]

Assign Ambient / Reflective Occlusion to the Surface Shader Slot of the mental ray material.

[Image: /docs/static/attachments/23999835]

Adjust the parameters of the shader to get good results. The number of ray samples is the most important.

Now, create an omni light. Go into its parameters and set "Affect Surfaces" to "Ambient Only" (under "Advanced Effects).

Then enable the mental may light shader and instance the material surface shader on it (drag & drop):

[Image: /docs/static/attachments/23999840]

Open the render to texture dialog ("0"). Select the object you want to bake. If it has overlapping UVs resulting from different material IDs, detach these parts before you proceed.

Toggle Projection Mapping off and add a "LightingMap" under "Output". Select the desired texture resolution.

[Image: /docs/static/attachments/23999839]

Don't apply the mental ray material to the object on which you want to bake the texture. Instead, apply a standard material to the object. The material is only created to instance the shader to the omni light, so you can modify the settings later.
If you want to render the scene with a camera, apply the mental ray material to the object and you will see the ambient occlusion in the rendered image.

Click
**
render
**
, ignore all the mental ray warnings, and wait for the map to be finished. With low resolutions and ray samples, the texture for a medium-poly object are rendered in under a couple of minutes. With high quality settings it can take much longer.

This is the resulting "Dirtmap". Multiply it over your diffuse map to get a convincing radiosity effect. It is also very useful as a layer mask for dirt or rust, since it tends to accumulate at the occluded parts of an object.

[Image: /docs/static/attachments/23999837]

If your texture renders out black, make sure that you assigned the correct renderer, and that all the settings are correct.

Example object with dirtmap and 100% self illumination:

[Image: /docs/static/attachments/23999838]
