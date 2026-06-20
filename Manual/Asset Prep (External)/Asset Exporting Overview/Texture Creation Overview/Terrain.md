# Terrain*

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/25534105
- Page ID: 25534105
- Breadcrumb: Asset Prep (External) > Asset Exporting Overview > Texture Creation Overview > Terrain*
- Parent: Texture Creation Overview

## Content

![Image](https://www.cryengine.com/docs/static/attachments/29933578)

## Overview

## Sections

In this tutorial you'll learn how to work with terrain textures from start to finish in CRYENGINE.

You'll find out how to setup your texture, material and level settings to get the best results from recommended workflows.

[Sections](#sections)[Texture Setup](#texture-setup)[Material Setup](#material-setup)[Sandbox Setup](#sandbox-setup)[Results](#results)

### Texture Setup

First, we need a nice terrain texture to work with. We'll use this nice tiling texture of stones and grass for this example.

As mentioned in the [Terrain.Layer Shader](/docs/static/engines/cryengine-3/categories/1114113/pages/1048772) article, all terrain textures should be high-passed in order to work with the terrain.layer shader correctly.

Since CryEngine 5.4.0, it is no longer necessary to modify terrain textures to be high-passed before importing them into CryEngine. This process is now handled automatically within the engine.

|
--- | ---
Source Image | High-Pass Filtered

There's also a normal map and a displacement map to go with it.

|
--- | ---
Normal Map | Displacement Map

### Material Setup

Open the Material Editor (press 'M' on the keyboard while the perspective view is active) or click on the material sphere button in the toolbar, or via **View -> Open View Pane -> Material Editor**.

With the Material Editor open, we can now create a new material for our terrain textures.

Click on the **Add New Item** button in the toolbar.

Now select an appropriate folder where you want to save the material file. In order to keep things consistent, lets save it alongside our existing terrain materials.

By default, the location of these materials won't be visible in the file dialog because they're zipped up inside the [GameData.pak](/docs/static/engines/cryengine-3/categories/1638401/pages/1605746). But we can manually create the path: `<root>/GameSDK/Materials/terrain/grass_with_stones.mtl`

After you save the material, the Material Editor will automatically select your new material and apply default settings to it to get you started.

Lets start customizing this new material by [adding the Diffuse texture](/docs/static/engines/cryengine-3/categories/1114113/pages/1048667) which we created earlier in the Texture Setup section.

Now we want to select the [Terrain.Layer Shader](/docs/static/engines/cryengine-3/categories/1114113/pages/1048772) for our **Shader type**.

As mentioned earlier, the Terrain system uses a specialized shader to deliver the best results, so make sure you're not trying to use Illum or a different shader on terrain.

You may notice the preview image is a bit blurry, this is because the texture is new and the Resource Compiler is compiling the textures, including Mips. This should clean itself up after a few more adjustments or a reboot of the Editor if necessary.

Next we'll select the "Grass" **Surface Type**. We could maybe select a Soil surface type, whichever you feel gives the best representation of the surface.

For now we'll leave the rest of the settings as-is. We'll come back and tweak these further after we've painted some terrain and can see the direct results in the level.

### Sandbox Setup

Open Sandbox and [create a new level](/docs/static/engines/cryengine-3/categories/1114113/pages/1048859).

As we've got a new, empty level, we're going to need some terrain to test our new material on.

#### Terrain Setup

Open the Terrain Editor from the button on the toolbar, or via the**Terrain -> Edit Terrain** menu option.

For simplicity and speed, we're going to auto-generate some terrain but in order to get more usable results for a level this size, let's drop the Terrain Max Height down to 128m.

In the Terrain Editor, click on **Modify -> Set Terrain Max Height**, set the number to 128 and click OK.

Now click on the Generate Terrain button in the toolbar, or **Tools -> Generate Terrain**.

The default settings should be fine as they are, and now click OK.

Now you should have something like this:

#### Terrain Textures Setup

Open the Terrain Textures tool via the toolbar (next to the Terrain button) or via **Terrain -> Terrain Texture Layers** menu option.

The default setup should look something like this:

Instead of overwriting the "Default" layer, let's create a new Layer to work with.

Click the **Add Layer** button in the "Layer Tasks" menu on the left. A new row will appear.

Now, click on the default material which is highlighted in red below. This will open up the Material Editor so that you can select a material to use.

Once you've selected your new terrain material "grass_with_stones" in the Material Editor, simply click **Assign Material** in the "Layer Tasks" menu on the left side of the Terrain Texture Layers tool.

You should then see the material link for this layer now shows "Materials/terrain/grass_with_stones". Great, that's our "Layer Material" now setup.

The next step is to select the "Layer Texture" we want to use because the default one won't give us very nice results as it's a debugging texture!

The texture chosen should be low resolution as it will only be visible from a distance, unlike the Layer Material, which is visible from up-close.

On the left side of the Terrain Texture Layers tool where the preview image is, click **Change Layer Texture** and navigate to the texture you wish to use.

We recommend using the `Textures/defaults/grey.dds` texture as it gives the most flexibility with color, being 128 neutral grey.

You'll notice the preview window updates to a simple grey image which is correct for our simple grey texture.

We should now give our new layer a custom name so that it is easily recognizable.

#### Layer Painter Setup

Now that our Layer is all setup we can start working with the Layer Painter tool in the RollupBar.

To get to the Layer Painter Tool, click on the second "Environment" tab in the RollupBar then "Layer Painter".

We can see our "grass_stones" layer is visible down the bottom.

First thing you'll want to do next is click **Reset** in the "Filter" section. This should bring the brightness slider up to the center.

Now set the color for the layer. This is why we use a 128 grey texture so that the color information specified here is not interfered with by the Layer Texture.

It will probably take a few trial paintings to get the results you're after, as the result can vary greatly from texture and lighting conditions.

As an example, this was too much green for this texture, which made the stone green, so it was changed back to almost grey in order to get nice results.

It's a good idea to put familiar objects into your level for scale reference.
You may notice the tiling is too high, because by default it's set to 1x. For terrain layers you want to get somewhere between 0.25 - 0.5 tiling, but this of course varies on your setup, texture type, scene, etc.

Tiling is done in the **Diffuse** texture slot, the Spec/Normal/Displacement will tile the same automatically.

While we're tweaking the tiling settings, let's also remove most of the color information from the Filter settings:

Now let's repaint the area with the new settings.

This tiling is much better and the color is much more natural now.

Let's add the Normal map in now to get some lighting information and finally, the Displacement Map with some Parallax Occlusion Mapping for added 'pop'.

|
--- | ---
Normal Map | Displacement Map

### Results

Now that you've created a new terrain material from scratch, you have the knowledge to build a library of materials to give your levels a truly unique look.

Try blending different layers together to give nice transitions and variety to your terrain.
