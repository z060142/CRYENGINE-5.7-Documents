# Export Textures with CryTIF - Photoshop

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/23308299
- Page ID: 23308299
- Breadcrumb: CRYENGINE - Getting Started > Installing CRYENGINE > CRYENGINE Plugins and Tools > Installing CryTIF Plugin for Photoshop > Export Textures with CryTIF - Photoshop
- Parent: Installing CryTIF Plugin for Photoshop

## Content

## Overview

The primary function of the texture dialog is to add meta data to the texture, which the Resource Compiler can later use to create a texture tailored for the target platform. Several settings like compression scheme, mipmap generation parameters, and also normalmap/alpha map combinations can be configured in the dialog. The user interface is a part of the Resource Compiler and is launched when saving a file as CryTIF from Photoshop.

The CryTIF (*.tif) format is used as an intermediate file format, based on the TIFF format, which contains the uncompressed texture as well as the different settings for the Resource Compiler stored as meta information. Whenever saving a texture as a *.tif (CryTIF) file, the plugin sends the texture to the Resource Compiler, creating a texture in the file format specifically for the target platform. By using presets on an uncompressed texture, the final output format can be specified in a very flexible way. Engineers can easily instruct the Resource Compiler to create a PC and console texture with optimal settings specific to the target platform from a single source file.

Please note that the TIF is not reloaded after its meta data was modified in the RC user dialog. So if the file is saved again in Photoshop without having been reloaded before, the settings need to be specified again.

Creating *.dds files directly without the Resource Compiler is not recommended or supported.

In order to save a texture in Photoshop, go to the **File** menu, click ** Save**. When the file dialog shows up, choose ** CryTIF** as the format, choose a name and save. After the *.tif file has been written to disk, the texture dialog of the Resource Compiler will show up.

### Texture Compilation

In order to use a source texture (.tif) in CRYENGINE, the Resource Compiler must be invoked to compile the texture to a more optimized format that can be loaded efficiently by the engine (usually *.dds).

When a *.tif file is saved with the **CryTIF Plugin** for Photoshop, the plugin opens the texture dialog of the Resource Compiler where specific settings for the texture can be made.

### Preview Window

In the upper area you can see two images, the original image on the left, and a preview of the processed image using the preset on the right.

If the dimensions of the Photoshop image that you are trying to save are not a power of two (i.e. 256x256, 512x512, 1024x1024), you will see a warning text instead of a preview.

Directly below the preview images, you can see different image properties such as resolution, number of mip maps, texture format, and memory. The original values are displayed on the left, the values on the right are based on the chosen preset or the custom settings.

![Image](https://www.cryengine.com/docs/static/attachments/25505572)

Number | Description
--- | ---
**1** | Preview Options - **Zoom In**/** Zoom Out -** Changes the preview size of the textures in the previews. This enables you to see details and how they are affected by the compression. You can pan the images by clicking in the preview area and dragging your mouse. - **Tiled -** Enables/disables tiling of the texture if the display size is smaller than the original texture size. - ** Bilinear -** Enables/disables bi-linear filtering. Simulates the appearance of the texture inside the game engine. - ** Channel drop-down list -** ** Several features can be previewed using this drop-down list. Below the list is an explanation of what is being displayed in the preview window. (Doesn't change when changing options; should it?)** - ** RGB:** Displays the RGB Color channels (Default mode) - ** Alpha:** Previews the alpha channel in grayscale (no gamma correction). - ** RGB Alpha:** Alpha blended with the background (no gamma correction). - ** AlphaTestBlend:** Shows the Alpha Channel visualized with an AlphaTest threshold of 0.5 while smoothly blending values beyond. - ** AlphaTestNoBlend:** Shows the Alpha Channel visualized with an AlphaTest threshold of 0.5 without any blending.
**2** | Preset selection - **List all presets -** Show all available presets instead of just the ones relevant for the current texture (determined by file name suffix). - ** Presets drop-down menu -** See below under Presets for detailed descriptions. - ** Show preset info -** Show the technical parameters of the selected preset as defined in the preset config.
**3** | Additional settings, Resolution reduction control

**Mouse Navigation** | **Description**
--- | ---
**Mouse Wheel** | Zoom in/out.
**Mouse Button Click+Move** | Move texture.

### Presets

The presets define how a texture gets compiled for in-game usage.

*![Image](https://www.cryengine.com/docs/static/attachments/25505574)*

This drop-down list holds the presets that you can assign to a texture. By default, the RC tries to identify the texture type by looking at the file name suffix (e.g. _ddn, _ddna) and displays only the presets relevant for that type.

The texture compiled using the preset settings is automatically displayed in the preview window on the right. Texture properties are also updated.

The list below describes the full set of available texture presets. It can be extended by adding new entries to the RC config file located at `Tools/rc/rc.ini`.

Preset | Description / Use
--- | ---
**Albedo** | Used for Albedo/Diffuse maps that don't need an alpha channel.
**AlbedoWithOpacity** | Used for Albedo/Diffuse maps with alpha channel that stores transparency for alpha blending.
**AlbedoWithCoverage** | Used for Albedo/Diffuse maps with alpha channel that is used for alpha testing.
**AlbedoWithGenericAlpha** | Used for Albedo/Diffuse maps with generic alpha values.
**Reflectance** | Used for Reflectance/Specular maps that are in sRGB space (recommended).
**Reflectance_Linear** | Used for Reflectance/Specular maps that are stored in linear space (mostly legacy).
**ReflectanceWithSmoothness_Legacy** | Used for Reflectance/Specular maps that store gloss in the alpha channel (legacy).
**Normals** | Used for Normal maps without smoothness/gloss.
**NormalsWithSmoothness** | Used for Normal maps where smoothness/gloss is stored in the alpha channel (recommended).
**NormalsWithSmoothness_Legacy** | Used for legacy Normal maps where smoothness/gloss is stored in the alpha channel. This preset should be used for assets that were authored using our legacy gloss distribution (before CE 3.8).
**NormalsFromDisplacement** | Generates a Normal map from an input Height/Displacement map.
**Displacement** | Grey-scale Alpha channel use only. Used for [Displacement Maps](../../../../Graphics%20%26%20Rendering/Shaders/Shaders%20in%20CRYENGINE/Shader%20Features%20(Shader%20Generation%20Params)/Displacement%20Phong%20PN%20Triangles%20Tesselation%20-%20Shader%20Generation%20Params.md) textures.
**Terrain_Albedo** | For use with the **[Terrain.Layer Shader](../../../../Graphics%20%26%20Rendering/Shaders/Shaders%20in%20CRYENGINE/Shader%20Reference/Terrain.Layer%20Shader.md)**. Automatically applies a high-pass filter to remove low frequency colors.
**Terrain_Albedo_HighPassed** | This preset should be used instead of Terrain_Albedo, if the texture is already high-passed.
**Decal_AlbedoWithOpacity** |
**Detail_MergedAlbedoNormalsSmoothness** | For use with **[Detail Mapping](../../../../Graphics%20%26%20Rendering/Shaders/Shaders%20in%20CRYENGINE/Shader%20Features%20(Shader%20Generation%20Params)/Detail%20Mapping%20-%20Shader%20Generation%20Params.md)**.
**Detail_MergedAlbedoNormalsSmoothness_Lossless** | For use with **[Detail Mapping](../../../../Graphics%20%26%20Rendering/Shaders/Shaders%20in%20CRYENGINE/Shader%20Features%20(Shader%20Generation%20Params)/Detail%20Mapping%20-%20Shader%20Generation%20Params.md)**. No compression.
**CloudShadows** |
**EnvironmentProbeHDR** | Used for Environment Probe specular cubemap.
**EnvironmentProbeHDR_Irradiance** | Used for Environment Probe diffuse cubemap.
**SkyboxLDR** | Used for simple non-HDR Skybox textures.
**SkyboxHDR** | Used for High-Dynamic Range Skybox textures.
**ColorChart** | For use with ColorChart textures. See **[Tutorial - Color Grading](../../../../Post-processing/Tutorial%20-%20Color%20Grading.md)** for more information.
**Gradient** |
**Greyscale** | Similar to Gradient preset but uses BC4 compression and mipmaps. Automatically selected for *_mask* texture filenames.![Image](https://www.cryengine.com/docs/static/attachments/44972224)![Image](https://www.cryengine.com/docs/static/attachments/44972226)***Diffuse_HighQ** on the left - ** Greyscale** on the right*
**LensOptics** | For use with **[Lens Flare Editor](../../../../Editor%20Tools/Lens%20Flare%20Editor.md)** textures. No mips will prevent blurry results.
**LightProjector** | For use with Textures that will be projected from lights and lightbeams. Uncompressed format.
**LoadingScreen** | **DEPRECATED** Use "SF_Image" for Scaleform UI.
**Minimap** |
**Muzzleflash** |
**Opacity** | Used for generic single-channel grayscale textures.
**Uncompressed** |
**ReferenceImage** |
**ReferenceImage_Linear** |
**WrinkleMask_Linear** |
**UserInteface_Lossless** |
**UserInterface_Compressed** |
**LUT_RGBA8** |
**LUT_RG8** |
**LUT_RG16** |
**SF_Image** | This preset should be used for textures used by Scaleform, such as loading screens.
**SF_Image_nonpower2** |
**SF_Gradient** |
**SF_Font** |

### Resolution Tab

![Image](https://www.cryengine.com/docs/static/attachments/23996895)

**Reduce Resolution drop-down list** lets you select different resolution adjustments. Useful if you keep the source file in a huge resolution, although you know it will appear in a much smaller size in the game (i.e. a texture used for promotion and for the final game asset).

Amount | Result
--- | ---
**0** | Keeps the texture at its original size (default).
**1** | Reduces the texture resolution by 1/2,reduces the memory consumption to 1/4 of the original memory.
**2** | Reduces the texture resolution by 1/4,reduces the memory consumption to 1/16 of the original memory.
**3** | Reduces the texture resolution by 1/8,reduces the memory consumption to 1/64 of the original memory.
**-1** | Increases the texture resolution by factor 2, increases the memory consumption to 4 times the original memory.
**-2** | Increases the texture resolution by factor 4, increases the memory consumption to 16 times the original memory.

There might be automatic texture resizing processes inside the engine in place. Please check with your programmers, if they enabled such optimizations for your development environment. Additionally the Resolution tab features optimization and exception functions.

- **Suppress engine reduce:** If you're switching from high to low spec, the textures are automatically scaled down to allow them to be loaded into the graphics card memory. This flag overwrites all the RC settings and keeps the original size throughout all the different quality settings. This should be used for textures that feature text. When this is enabled, the flag "/ser=1" will be added into the TIF meta data.

### MIP Control Tab

The controls allow the manual adjustment of the Alpha channel mip maps. This is especially useful when the texture contains fine details, like in a chain link fence.

You can shift the alphatest bias in the different mip levels using the sliders. The value of the texture is adjusted and assuming a constant alphatest value you can tweak the result.

![Image](https://www.cryengine.com/docs/static/attachments/23996896)

The lowest slider, which you see when you scroll down, controls the mip sharpening. This is a sharpness filter that is applied to the mip maps to counteract the blur that naturally occurs when down-scaling the textures during mip map generation. This feature can greatly improve image quality. The default value is 35.

**Mip maps drop-down list** |
--- | ---
**None (0)** | Does not create mip maps.
**max, tiled (1)** | Default Setting. Creates the maximum number of mip maps possible.

**Maintain alpha test coverage** tries to preserve the alpha coverage of the original alpha channel. This is particularly useful for vegetation to prevent leaves from thinning out in the distance.

The**Mip filter method** allows to change the downsampling algorithm used to generate the mip maps.

### RGB to Normal Tab

![Image](https://www.cryengine.com/docs/static/attachments/23996894)

The CryTIF plugin can convert a grayscale bumpmap into a normal map. To activate the feature, select a Filter Type other than ***None (off)***.

Parameter | Description
--- | ---
**Filter Type** | Changes the filter used for processing the texture.
**Strength** | Defines the strength of the bumps. This can be used as additional compensation, but you normally have better control over this by editing the grayscale texture in Photoshop (Range 0 – 15; Default 5).
**Blur** | Blurs the texture (Range 0 – 10; Default 0).
**Invert** | Inverts the height map. Whites are then interpreted as pits and blacks as bumps.

### A to Normal Tab (Deprecated)

In the production process, you sometimes need to blend a low frequency normal map with a second high frequency normal map to create a variation of the original low frequency version. If you did this in Photoshop directly, you would loose intricate detail when scaling the texture during the conversion process. This would come with a loss of detail in the high frequency part of the texture and possibly wrong normals. This function converts the high frequency greyscale alpha channel of a normal map and combines it with the normal RGB channels of the normal map.

As this function is done after scaling and using a proprietary sharpening algorithm, as well as a normalization pass on the low frequency normal map, the detail is better than in the traditional approach. It also allows it to be tweaked much more easily. To enable this feature, select a Filter Type other than ***None (off)***.

The preview window should change now to indicate the change.

Please note that with PBR in CRYENGINE, the alpha channel of the normal map usually contains the smoothness already, so this feature has to be considered as deprecated.

![Image](https://www.cryengine.com/docs/static/attachments/23996906)

### Generate Output

![Image](https://www.cryengine.com/docs/static/attachments/23996908)

Pressing the **Generate Output** button forces an immediate conversion to the target output format without closing the CryTIF dialog box.

It is then possible to switch to CRYENGINE and look at the results of the settings that you have changed (Sandbox automatically reloads/updates changed textures). This is useful for quickly testing compression settings without re-saving or reopening the dialog box every time you make a change.

### Troubleshooting

Please note that the TIF is not reloaded after its meta data was modified in the RC user dialog. So if the file is saved again in Photoshop without having been reloaded before, the settings need to be specified again.

In order to run the RC, the CryTIF plugin needs to know the path where the RC is located. This can be configured in Photoshop under **Help -> About Plugin -> CryTIFPlugin**. If the RC executable cannot be found, the configuration dialog is opened automatically.

[Texture Compilation](#texture-compilation)[Preview Window](#preview-window)[Presets](#presets)[Resolution Tab](#resolution-tab)[MIP Control Tab](#mip-control-tab)[RGB to Normal Tab](#rgb-to-normal-tab)[A to Normal Tab (Deprecated)](#a-to-normal-tab-deprecated)[Generate Output](#generate-output)[Troubleshooting](#troubleshooting)
