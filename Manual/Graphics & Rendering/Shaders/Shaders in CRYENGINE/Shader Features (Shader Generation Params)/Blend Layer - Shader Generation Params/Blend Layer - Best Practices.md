# Blend Layer - Best Practices

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/29450138
- Page ID: 29450138
- Breadcrumb: Graphics & Rendering > Shaders > Shaders in CRYENGINE > Shader Features (Shader Generation Params) > Blend Layer - Shader Generation Params > Blend Layer - Best Practices
- Parent: Blend Layer - Shader Generation Params

## Content

## Overview

Blend mapping is one of the key features in CRYENGINE. With blend mapping you are able to blend two different textures. It is very useful to break up the repeating when you're using two tileable textures. It can also serve to give localized dirt, wear, tear, etc.

Once the basics on how blend mapping works are known, the use can be limitless and give the artist a lot of freedom to make a great looking asset spectacular with little use of resources.

In the following tutorial we will explain the basics of blend mapping and what to look out for when using it.

### How to Use Blend Mapping

We will be blending these two textures on a flat plane.

![Image](https://www.cryengine.com/docs/static/attachments/28898780)![Image](https://www.cryengine.com/docs/static/attachments/28898781)

### Creating Geometry for Blend Mapping

The first thing we need to do before we can blend map is prepare our geometry correctly. One caveat of blend mapping is that is it tied to our vertices in the geometry. That means that we have to add more geometry in places we usually wouldn't. It also means that we need to model very clean and neat, because the more even the subdivisions are, the better result we'll be able to achieve when blend mapping. Also: the more subdivisions we add, the more accurate we'll be able to tell where to blend and where not.

In modern game development geometry is a little bit cheaper than using lots of textures. As long as we keep our vertices count reasonable it should be OK.

Below we created a poly plane with subdivisions:

![Image](https://www.cryengine.com/docs/static/attachments/28898777)

### Painting the Vertex Alpha

To control the blend and where it's going to show on our asset, we need to paint our Vertex Alpha. The range in our spectrum is 0-255, with 0 being black and 255 being white.

If the vertex alpha is 255 (pure white) on our asset it means that only the original texture will show up. On the other end of the spectrum if the value on the vertex alpha is 0 (pure black) the blend will show up.

Since we have a range from 0 to 255, we can use the full spectrum and decide how much and where we want the blend to show through.

![Image](https://www.cryengine.com/docs/static/attachments/28898778)

### Making the Blend Mask

To further break up the tiling and have even more control over how our textures are going to blend, we have the blend mask. The blend mask acts like an alpha. With that we can have parts our original texture show through even if we have that part of our vertex alpha on the geometry painted black.

Since our blend mask acts like an alpha all the white parts will be displaying our blend texture all the black parts will displaying the original texture.

As you can see down below we have taken the brick pattern and added some noise. We also, in order to increase believability, made the grout in some places black, so the original grout from the bricks will show through.

![Image](https://www.cryengine.com/docs/static/attachments/28898779)

### 3ds Max Asset Setup

Add a vertex paint modifier to the stack and change the channel to vertex alpha. This is very important to separate, as you must use vertex alpha for this feature and not vertex color.

Open the objects property window of the asset and enable vertex color display, but change the display to vertex alpha. To be sure that you don't paint the wrong channel you can always switch back and forth to vertex color preview.

All the textures are tiled and do not use unique UV shells. You cannot use a baked ambient OCC map in this case, but it is still possible to use baked vertex color shadows on the asset.

![Image](https://www.cryengine.com/docs/static/attachments/23993875)

You can use our blend shader for 3ds Max not just for previewing the result but also to paint your vertex alpha in real time.

Open up the Material Editor and switch the standard material to a DirectX shader where you can load the blend layer shader instead and get all the similar parameters of the sandbox editor to tweak the values.

![Image](https://www.cryengine.com/docs/static/attachments/23993878)

### Material Setup in CRYENGINE for Blend Mapping

Once you have your textures, it's time to bring the asset into CRYENGINE. After the asset is in the engine and the shader assigned, we need to activate the blend layer.

To do this:

- In the Material Editor, open the **Shader Generation Params** tab
- Click on the **Blendlayer** checkbox
- New slots have become available

The extra slots are named:

- Blending Map (your blend mask gets loaded in here).
- Second Diffuse Map (your blend diffuse gets loaded in here).
- Second Bump Map (your blend normal map/original normal map gets loaded in here).

In those we'll load in our blend textures.

One good tip is to load the same normal map from the original texture, this way it will give the blend texture the brick pattern.

This is on a case to case basis, but if you're doing dirt, paint, etc. which doesn't have a unique surface property it is a good idea to reuse the same normal map.
![Image](https://www.cryengine.com/docs/static/attachments/28898770)

### Tweaking the Blends in CRYENGINE

The blend has two settings that need to be tweaked to give a good result. You can find those in the **Shader Params**.

They are as followed:

- Blend Factor
- Blend Falloff

By tweaking the **Blend Factor** we can adjust how much of the blend texture gets blended in. In other words it acts as an opacity slider in Photoshop.

**![Image](https://www.cryengine.com/docs/static/attachments/28898769)**

By tweaking the **Blend Falloff** we can adjust how harsh the contrast between the blend texture and the original texture is.

In other terms we are adjusting the feathering of the blend mask. This means the higher the value, the softer our alpha gets (which in this case is the blend mask).

![Image](https://www.cryengine.com/docs/static/attachments/28898771)

Once you have tweaked everything you should get a result like this:

![Image](https://www.cryengine.com/docs/static/attachments/28898772)![Image](https://www.cryengine.com/docs/static/attachments/28898773)

As you can see the bottom right corner is completely free of the blend, since this is the part that we left white and only the original texture is coming through.

You can also see as opposing the bottom left corner is fully blended. But you can also see that the grout is the original one coming through, since our blend mask we left that black.

[How to Use Blend Mapping](#how-to-use-blend-mapping)[Creating Geometry for Blend Mapping](#creating-geometry-for-blend-mapping)[Painting the Vertex Alpha](#painting-the-vertex-alpha)[Making the Blend Mask](#making-the-blend-mask)[3ds Max Asset Setup](#3ds-max-asset-setup)[Material Setup in CRYENGINE for Blend Mapping](#material-setup-in-cryengine-for-blend-mapping)[Tweaking the Blends in CRYENGINE](#tweaking-the-blends-in-cryengine)
