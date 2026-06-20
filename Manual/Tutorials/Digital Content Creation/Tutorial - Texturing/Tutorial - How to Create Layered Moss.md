# Tutorial - How to Create Layered Moss

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/23308599
- Page ID: 23308599
- Breadcrumb: Tutorials > Digital Content Creation > Tutorial - Texturing > Tutorial - How to Create Layered Moss
- Parent: Tutorial - Texturing

## Content

### Overview

This tutorial will explain how the moss in Ryse was made 3D and having depth to it.

Contrary to beliefs there was no custom shader used, but in fact it was an old technique used to create the effect of a fluffy, 3D surface with depth. A very similar technique was used on The Shadow of Colossus for PS2.

![Image](https://www.cryengine.com/docs/static/attachments/23999623)

Breaking down the moss, one sees that it is made up of 4 polygon layers hovering one above the other. The UVs of those poly layers are in a different section of the moss texture.

![Image](https://www.cryengine.com/docs/static/attachments/23999634)

### Preparing the Texture

Looking at the moss texture we see that the**texture is divided up in 4 sections**. In the diffuse section we see that it is always the same texture just with different kinds of values. From the top left section is being the brightest, to the bottom right the darkest.

When creating the alpha for the texture we have on the top left the most transparent (lot's of black and dark grey values) and the bottom right the most opaque (lot's of whites and light greys almost no black values).

Having this kind of setup allows us to look through the sparseness top layer onto all the other layers below it, with the densest layer being at the bottom which serves as the base, this will allow us to fake some depth and make the whole moss look 3D, whilst retaining the fuzzy effect moss is known for.

The way the texture will be used is by putting the dark opaque part of the diffuse as the base polygon layer of the moss, and the brightest most transparent part for the top polygon layer, with in between in accordance to our values the other two sections.

![Image](https://www.cryengine.com/docs/static/attachments/23999637)

![Image](https://www.cryengine.com/docs/static/attachments/23999638)

![Image](https://www.cryengine.com/docs/static/attachments/23999639)

To get the best results we will achieve by creating a 2k moss texture, then editing it and tweaking it's brightness variation and alphas accordingly until having a good result.

By dividing the texture into four sections, every individual section has a final resolution of 1024x1024.

To see how the moss looks in engine, we have applied the texture to a simple plane.

![Image](https://www.cryengine.com/docs/static/attachments/23999640)

### Preparing the Geometry

For display purposes we are using a simple rock mesh. The 3D moss should be used mostly you want your moss on objects like stones, rocks, trunks, walls etc.

If a more flexible use is desired, moss chunks can be created as standalone assets as well, rather than being a custom part the asset.

![Image](https://www.cryengine.com/docs/static/attachments/23999641)

Looking at the rock we see that's it's been triangulated. We would be able to determine the location of our moss, but by duplicating those faces we would waste a lot of geometry.

So we're going to re topolgize that part of the rock. By doing that it will give us greater control of the edge and UV flow.

To do that quickly and efficient 3DS max offers some tools. By using Freeform -> Polydraw a quick area can be covered on the rock with a basic polygon shape.

This newly created polygon plane will serve as the base and most bottom layer of the moss. It's ok, if the original rock mesh sticks out of the polygon plane since this will be tweaked later on.

We should have a result looking like in the image below.

![Image](https://www.cryengine.com/docs/static/attachments/23999642)

![Image](https://www.cryengine.com/docs/static/attachments/23999643)

To create the layering effect we are applying following modifiers to our polygon plane:

- Convert the poly plane to an editable polygon by using "Editable Poly".
- After that the "Unwrap UVW" modifier is applied to the stack, so in every single layer we're able to move the UV shells up, down, right or left by exactly 0.5 in U & V space to be able to cover all four sections of our texture.
- The fist "Push" modifier is now added to the stack, this push modifier affects the entire shape, so the final distances between all the polygon layers can be adjusted.
- Once we have moved the polygon plane to the right distance we select the vertices on the border of the plane and apply another "Editable Poly".
- Now we need to apply the second "Push" modifier to the vertices. The border needs to be pushed back into the rock, otherwise we end up with a harsh transition from the rock to the moss, since there's going to be a clear visible border. Once all the four layers have been created and all of them having sequentially their borders push back, a fuzzy and 3D transition will be created towards the rock.
- The last "Edit Poly" that is applied, serves the purpose to alter all the poly planes at the same time in the end and make final adjustments to the overall shape.

Please do not collapse the modifier stack!

![Image](https://www.cryengine.com/docs/static/attachments/23999624)

After being done with our base polygon plane we start repeating the same steps for the following three remaining planes.

Here's a detail breakdown:

![Image](https://www.cryengine.com/docs/static/attachments/23999625)

![Image](https://www.cryengine.com/docs/static/attachments/23999626)

![Image](https://www.cryengine.com/docs/static/attachments/23999627)

![Image](https://www.cryengine.com/docs/static/attachments/23999628)

![Image](https://www.cryengine.com/docs/static/attachments/23999630)

![Image](https://www.cryengine.com/docs/static/attachments/23999629)

In summary to create the polygon planes and layer them:

- Clone to create a new polygon plane from the base polygon plane.
- Edit UV’s for the shell and determine their new position from the duplicated polygon shell.
- Move out the new polygon plane with the "Push" modifier.
- Click on the "Edit poly" modifier to select border vertices.
- Use the "Push" modifier on the border vertices to push them back into the rock.
- Select the "Edit Poly" modifier again to tweak all moss layers later.

### Adjusting the moss layers and using vertex paint to create a smooth transition

After duplicating our polygon planes, moving the UVs and moving them, we export the rock into CRYENGINE. And our result looks currently like the image below

![Image](https://www.cryengine.com/docs/static/attachments/23999631)

Looking at the moss within CRYENGINE we can see the moss. But in reality moss seeps in and out of cracks and right now it looks to even. To fix that we use the last **"Edit Poly"** modifier, since we didn't collapse them. That way you can alter all vertices at the same time.

Try to follow real world reference by raising some vertices and lowering others.

![Image](https://www.cryengine.com/docs/static/attachments/23999632)

After exporting the rock into CRYENGINE the result looks like in the image below:

![Image](https://www.cryengine.com/docs/static/attachments/23999633)

As we can see the transitions between the rock and moss are a bit harsh right now. To fix that we're going to apply some vertex blending to smooth out the transitions and give some detail to our rock.

Some things should be considered when using this technique. The layered moss technique can be super expensive in terms of polygons, so it should be used only for LOD0.

To avoid a visible swapping, when the assets is lodding between LOD0 and LOD1, paint the blend of the moss on LOD1 where the original layered moss was in LOD0. That way the swap between LOD0 and LOD1 is almost unnoticeable.

![Image](https://www.cryengine.com/docs/static/attachments/23999635)

![Image](https://www.cryengine.com/docs/static/attachments/23999636)
