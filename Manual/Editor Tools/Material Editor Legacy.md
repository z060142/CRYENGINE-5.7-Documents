# Material Editor Legacy

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/44967563
- Page ID: 44967563
- Breadcrumb: Editor Tools > Material Editor Legacy
- Parent: Editor Tools

## Content

## Overview

Inside the Material Editor you can browse, create, edit and assign materials to objects, terrain, etc.

It also allows you to copy existing materials and use them as a starting point for your specific material needs. Materials files (**.mtl**) are ideally located in the same folder as the object they were created for. However, as they can be freely assigned to any objects inside your game project, the only restriction is to place them inside the game project folder structure.

Editing materials not only allows you to choose textures and shaders, but also fine-tune placement, animation of textures and tweaking parameters relevant for a chosen shader type.

To open the legacy Material Editor, go to **Tools → Material Editor Legacy**.

![Image](https://www.cryengine.com/docs/static/attachments/44967609)

### 1. Menu

The Menu can be accessed via the![Image](https://www.cryengine.com/docs/static/attachments/44967610) icon on the top-right corner of the panel. When clicked, it reveals the **Help** sub-menu with the ** Go to documentation...** option that directs the user to the documentation page for this tool.

### 2. Toolbar

The toolbar at the top of the Material Editor window has shortcut buttons for frequently used actions.

![Image](https://www.cryengine.com/docs/static/attachments/44967583)

# | Button | Description
--- | --- | ---
**1** | **Assign Item to Selected Objects** | Assigns a material to the object that is selected in the main Viewport; overwrites the original material (i.e. for a CGF) for this copy of the object in the editor.
**2** | **Reset Material on Selection to Default** | Resets the selected object's material to default (or the material stored in the *.cgf file).
**3** | **Get Properties from Selection** | Selects the material which is assigned to the selected object.
**4** | **Pick Material from Object** | Interactively select a single Material or a sub-material of an object in the scene by using an eyedropper tool. The Editor highlights an object's polygons sharing the same sub-material when the eyedropper tool is moved over them. Click **LMB** to select the material/sub-material. Also provides info about the name of the material/sub-material and the surface type ID in the Viewport.
**5** | **Materials Library Browser** | Select a filter to display materials in the library. - **All materials** for example shows all materials that are in your working folder, no matter if they are checked in or not. - ** Used In level** shows just the materials which are used in your level.
**6** | **Add New Item** | Adds a new material to the library
**7** | **Save Item** | Saves the selected material (only works for materials outside of *.pak files)
**8** | **Remove Item** | Deletes the material. **CAUTION:** also deletes the *.mtl file. No Undo possible.
**9** | **Copy Material** | Copies the selected material.
**10** | **Paste Material** | Pastes the selected material.
**11** | **Open large material preview** | Opens a separate window which enables you to preview the material in more detail and from different angles.

### 3. Browser

The Material Browser lets you browse the library for materials, similar to Windows Explorer.

At the top of the folder structure you can find a quick search, which filters the materials in your library. You can use it to quickly locate a material you know the name of.

#### Context Menu

When right-clicking on items in the Material Browser, a context menu will be displayed. Which options are displayed depends on the kind of item you have clicked on:

Option | Description
--- | ---
**Cut** | Cuts the selected material and moves it to the clipboard.
**Copy** | Copies the selected material onto the clipboard.
**Paste** | Opens File dialog and allows paste copied earlier material to specified folder.
**Copy Name to Clipboard** | Copies the name and the path of the material onto the clipboard.
**Extract** | Extracts the selected material from the *.pak file into a folder with the same path as in *.pak file.
**Duplicate** | Duplicates the selected material and puts the duplicate into the same folder.
**Rename** | Lets you rename the selected material.
**Delete** | Deletes the selected material. When deleting the material this way, it will be deleted from your hard-drive.
**Reset** | Resets the selected material to its default settings.
**Assign to Selected Objects** | Assigns the material to the object you have selected in the Viewport.
**Select Assigned Objects** | Selects all objects the selected material has been assigned to.
**Convert To Multi Material** | Converts the selected material to a Multi Material.
**Add New Material** | Adds a new material in the active folder.
**Add New Multi Material** | Adds a new Multi Material in the active folder.

The padlock icon next to a material indicates that it is read-only. Any changes you make to a locked material will be lost, even if you save the level.

If you wish to edit an existing material, extract it from the *.pak file it's located in and ensure that read-only is not checked on the file properties.

### 4. Preview

In the Material Preview, you can see what the material you have selected looks like. You can also see the material on several predefined objects to get a better idea of what it would look like in-game.

When right-clicking on a preview, a context menu appears:

Option | Description
--- | ---
**Use Default Object** | Uses a default object for a preview of the selected material.
**Use Plane** | Uses a plane for a preview of the selected material.
**Use Box** | Uses a box for a preview of the selected material.
**Use Sphere** | Uses a sphere for a preview of the selected material.
**Use Teapot** | Uses a teapot for a preview of the selected material.
**Black Background** | Changes the background of the preview to black.
**Gray Background** | Changes the background of the preview to gray.
**White Background** | Changes the background of the preview to white.
**Texture Background** | Changes the background of the preview to textured.
**Use Back Light** | Enables back light for preview.

### 5. Parameters

The Material Editor has basic material parameters that are common to all materials, as well as shader parameters that can be adjusted if shaders are enabled.
Please see [Tutorial - Getting Started with the Material Editor](../Tutorials/Game%20and%20Level%20Design/Materials%20Tutorials/Tutorial%20-%20Getting%20Started%20with%20the%20Material%20Editor.md)to learn more about the basic of the Material Editor.

#### Material Settings

Setting | Description |
--- | --- | ---
**Template Material** | This function is **deprecated** and may not work as expected. |
**Shader** | Here you can select the shader you want to use. Generally you use illum/vegetation/glass shader. For more information on shaders, see [Shader Reference](../Graphics%20%26%20Rendering/Shaders/Shaders%20in%20CRYENGINE/Shader%20Reference.md). |
**Surface Type** | You can select a surface type for your material here. The surface type sets up what kind of sound will be played or what kind of particle effects will be spawned when you shoot the object. For an old wooden table you would choose something like "wood", or you could even create your own custom surface type through the Material Effects system. This can be applied to any object and will result in the associated particles, decals and sounds being played on that object, so yes, you can make a rock bleed!![Image](https://www.cryengine.com/docs/static/attachments/44967582) |![Image](https://www.cryengine.com/docs/static/attachments/44967581) |![Image](https://www.cryengine.com/docs/static/attachments/44967580) --- | --- | --- mat_wood | mat_rock | mat_flesh |
![Image](https://www.cryengine.com/docs/static/attachments/44967582) | ![Image](https://www.cryengine.com/docs/static/attachments/44967581) | ![Image](https://www.cryengine.com/docs/static/attachments/44967580)
mat_wood | mat_rock | mat_flesh

#### Opacity Settings

These settings are important if using alpha channels for transparency, for example when creating leaves and wire fences.

Setting | Description |
--- | --- | ---
**Opacity** | With the opacity value you can switch between **Alpha Blend** and ** Alpha Test**.![Image](https://www.cryengine.com/docs/static/attachments/44967579) ** Opacity value**: 0-99 -> alpha blend. ** Opacity value**: 100 -> alpha test. With alpha blend you can get very soft and semi transparent results, but it is more expensive than alpha test. |
**Alpha Test** | If you want to use alpha test, which is less expensive, set the opacity value to 100 and the AlphaTest value to 50.![Image](https://www.cryengine.com/docs/static/attachments/44967578)50 is the default value. A value below 50 tends more to the white color of the alpha map. A value above 50 tends more to the black color of the alpha map.![Image](https://www.cryengine.com/docs/static/attachments/44967607) |![Image](https://www.cryengine.com/docs/static/attachments/44967606) |![Image](https://www.cryengine.com/docs/static/attachments/44967605) --- | --- | --- Default alpha test = 50 | Alpha test = 10 | Alpha test = 90 |
![Image](https://www.cryengine.com/docs/static/attachments/44967607) | ![Image](https://www.cryengine.com/docs/static/attachments/44967606) | ![Image](https://www.cryengine.com/docs/static/attachments/44967605)
Default alpha test = 50 | Alpha test = 10 | Alpha test = 90
**Additive** | When using a semi-transparent material like glass, use the additive function. The material color will be added to the background color. The resulting color will the be brighter.![Image](https://www.cryengine.com/docs/static/attachments/44967577) |

#### Lighting Settings

This section controls the material color and specular settings.

Setting | Description
--- | ---
**Diffuse Color** | Controls the material diffuse color by double clicking the color square. The default RGB value is 255,255,255 and should usually be left at 255,255,255 for Physically Based Shading (PBS). Choose the color on the left side by clicking the desired color. To get the best quality rendering, it is recommended to always use 255,255,255 diffuse with no color input and adjust the diffuse texture accordingly. Using the slider next to the color you can control the brightness. You can also type in the RGB code in the fields underneath the color spectrum. There is also a color swatch available in the **Standard** tab.![Image](https://www.cryengine.com/docs/static/attachments/44967576)![Image](https://www.cryengine.com/docs/static/attachments/44967575)
**Specular Color** | The specular color is the reflective or shiny component of a material when light shines onto the object. To correctly set up PBS materials please see the documentation for [Physically Based Shading (PBS)](../Graphics%20%26%20Rendering/Shaders/Physically%20Based%20Shading%20(PBS).md). Specific metals reflect a certain color, e.g.: Gold =**255,219,145,** Silver =** 250,247,242,** Copper =** 250,209,194** (see the lookup table at the bottom of the [Texture and Material Setup for PBS](../Graphics%20%26%20Rendering/Shaders/Physically%20Based%20Shading%20(PBS)/Texture%20and%20Material%20Setup%20for%20PBS.md) page). All other non-metals should be within the sRGB color range of 40,40,40 -> 60,60,60. They should never be above 80,80,80! As long as you adhere to the PBS specular color guidelines, your materials should look 'physically plausible' no matter what the lighting conditions are (in images below, you'll see gold, silver and copper in different lighting conditions): * From left to right and top to bottom: midday, evening, night, neutral*![Image](https://www.cryengine.com/docs/static/attachments/44967574)![Image](https://www.cryengine.com/docs/static/attachments/44967573)![Image](https://www.cryengine.com/docs/static/attachments/44967572)![Image](https://www.cryengine.com/docs/static/attachments/44967571)
**Smoothness** | The smoothness defines how rough or glossy a surface is. To correctly set up PBS materials please see the documentation for [Physically Based Shading (PBS)](../Graphics%20%26%20Rendering/Shaders/Physically%20Based%20Shading%20(PBS).md). Think of it as defining the micro details on a surface, where the normal map defines the macro details. The smoothness map is stored inside the Alpha channel of the normal map (saved with the postfix _ddna). The higher the value you enter for the Smoothness, the tighter the specular highlight will be. In the following picture, from Left to right, we are decreasing the Smoothness value. - (Left: Smoothness = 255, very smooth surface, highly reflective, tight specular highlight) - (Right: Smoothness = 0, very rough surface, no reflection, wide specular highlight)![Image](https://www.cryengine.com/docs/static/attachments/44967597)
**Emissive Intensity (kcd/m2)** | The Emissive Intensity defines how much light gets emitted from the surface (previously known as 'glow'). The intensity is specified in kilonits (same as kcd/m2) which is the physical unit for Luminance. A candle flame has a typical Emissive Intensity of 10 kcd/m2. Please note that for surfaces, emittance is only supported by the Illum shader and is ignored by the Vegetation and HumanSkin shaders.
**Emissive Color** | The Emissive Color defines the color of the emitted light ("glow") when the Emissive Intensity is not zero. In case an emittance map is used, the emissive color gets multiplied with the emittance map color.

#### Advanced Settings

Setting | Description
--- | ---
**Allow layer activation** | Enabling this feature will load the material while the layer is loaded. When the layer is not loaded, the material will not be loaded either. For performance reasons, it is recommended to turn this on at all times.
**2 sided** | Both sides of the face the material is assigned to will be rendered by the engine. You normally use this for objects with alpha channels like leaves which have no thickness.
**No shadow** | Faces the material is assigned to will not cast a shadow.
**Use Scattering** | **Deprecated**
**Hide After Breaking** | This will make a subset disappear when the object it's attached to breaks procedurally. An example is a liana that disappears when the palm tree it hangs from breaks.
**Blend Terrain Color** | Color information is tinted based on the terrain color. For example, Grass inherits terrain albedo in a use case.
**Traceable Texture** | Material will be applied to Ray Traceable decals and will use an alpha map to verify the texture.
**Fur Amount** | **Deprecated**
**Voxel Coverage** | Allows you to control voxel opacity for SVOTI integration.
**Heat Amount** | Applies heat to the object to be used in conjunction with the thermal vision effect (r_NightVision=3).
**Cloak Amount** | **Deprecated**
**Link to Material** | **Deprecated**
**Propagate Options** | **Deprecated**

#### Texture Maps

In the material editor are different slots for texture maps. With texture maps, users can control different shader effects.

To add a texture to the material slot, click the "**...**" button on the right side or copy and paste the texture path into an empty slot.

![Image](https://www.cryengine.com/docs/static/attachments/44971434)

The Texture Map slot layout is fairly straightforward: the left column displays which type of texture map the slot is associated with, the middle column is where the texture map file is place and on the right there are three buttons:

Button | Description
--- | ---
![Image](https://www.cryengine.com/docs/static/attachments/44967570) | Opens the file browser dialog to select a texture.
![Image](https://www.cryengine.com/docs/static/attachments/44967569) | Opens the current texture's associated *.psd file in Photoshop (requires defining Texture Editor in **Preferences**).
![Image](https://www.cryengine.com/docs/static/attachments/44967568) | Opens the current texture's *.tif file (if available) in Photoshop (requires defining Texture Editor in **Preferences**).

Hovering over the name of the Diffuse texture gives you a preview of that texture.

The table below shows the textures available for the Illum shader. Some texture maps will only be available when certain materials or textures are selected, or upon activation of Shader Generation Parameters.

Texture Map | Filename Suffix | Channels | Description
--- | --- | --- | ---
Diffuse Map | _diff | RGBA | Defines the albedo color of the surface. Can also contain monochrome Alpha channel to describe alpha transparency.
Bumpmap | _ddna | RGBA | Special version of Normal maps. Additionally uses monochrome Alpha Channel (aka Gloss Map) to describe the Surface's Smoothness inside the Physical Based Rendering System.
Specular (Reflectance map) | _spec |  | The texture representing the specular intensity and color of material highlights defined as the "shininess" and color of specular reflections.
Environment Map | _cm | RGBA | Can be defined custom through slot input or can inherited from the "nearest cubemap."
Detail Map | _detail |  | The texture allowing you to add more details to surfaces. It works like the second material layer and it is not affected by the mapping of the model it is used for.
Heightmap | _displ |  | The texture which is utilized by POM/OBM/Tessellation to give more depth and definition to an object.
Dirt Map | _diff | RGBA | A decal that houses an alpha for laying over grime or moss on objects.
Custom | _sss | RGBA | The custom slot is generally used to expose common parameters such as SSS or opacity for opaque materials.
Emittance Map | _em |  | The Emittance map is used to control what portion of the texture will be set to glow or emit.

All of these Texture Maps have the following options when they're expanded:

Option | Description |
--- | --- | ---
**Tex Type** | Lets you select the following texture types: - 2D - Cube-Map - Dynamic 2D map - From User Params - Nearest cube-map probe for alpha blended |
**Filter** | These options are **deprecated**. |
**Is Projected Tex Gen** |  |
**Tex Gen Type** | Lets you select the following options: - **Camera** - ** Stream** - ** World** |
**Tiling** | Lets you select the following options: - **Is TileU** - ** Is TileV** - ** TileU**&** TileV** - You can tile your texture for the U and V axis separately by using the arrow button, the slider, or the text field. Note that you currently cannot tile normal or specular maps independently of the diffuse map. This is because of material instancing which saves many draw calls.![Image](https://www.cryengine.com/docs/static/attachments/44971442) |![Image](https://www.cryengine.com/docs/static/attachments/44971444) |![Image](https://www.cryengine.com/docs/static/attachments/44971443) --- | --- | --- Texture tiling 1, 1 | Texture tiling 5, 5 | Texture tiling 1, 3 - ** OffsetU** & ** OffsetV**- You can move the texture on the model in U and V direction separately. In the example below, the texture is moved 1.32 in U and 2.17 in V direction:![Image](https://www.cryengine.com/docs/static/attachments/44967567) - ** RotateU**, ** RotateV** & ** RotateW****-** You can rotate the texture on a model in U and V direction separately. In the example below, the texture is rotated about 45 degree into U and V direction: *![Image](https://www.cryengine.com/docs/static/attachments/44967566)* |
![Image](https://www.cryengine.com/docs/static/attachments/44971442) | ![Image](https://www.cryengine.com/docs/static/attachments/44971444) | ![Image](https://www.cryengine.com/docs/static/attachments/44971443)
Texture tiling 1, 1 | Texture tiling 5, 5 | Texture tiling 1, 3
**Rotator** | With the rotator you are able to create a rotating/shifting texture animation. Choose between three different types of rotation by clicking the option box. - **Type** - ** Constant Rotation -**Rotation is constant, rotating/shifting in one direction and back:![Image](https://www.cryengine.com/docs/static/attachments/44967565) - ** Fixed Rotation -** Static rotation with no animation. Similar to the rotation function of the tiling menu. - ** No Change -** Rotator is deactivated. - ** Oscillated Rotation -**Rotation oscillates from the minimum, to the maximum, and back:![Image](https://www.cryengine.com/docs/static/attachments/44967564) - ** Rate -** Defines the number of complete rotation cycles per unit of time. Or in the case of oscillating rotation, defines the rate of change of direction. - ** Phase -** The phase of an oscillation or wave is the fraction of a complete cycle corresponding to an offset in the displacement from a specified reference point in time t = 0. - ** Amplitude -** Defines the maximum value of an oscillation/wave. - ** CenterU and CenterV -** Centers the texture on the model in U and V direction separately. |
**Oscillator** | Like the rotator, the oscillator animates a texture. - **TypeU** - ** Constant Moving -**Texture shifts endlessly in the adjusted direction:![Image](https://www.cryengine.com/docs/static/attachments/44971436) - ** Fixed Moving -** Fixed moving is a static oscillation with no animation. - ** Jitter Moving -**Texture shifts endlessly in the adjusted direction with jittering added. Has a stroboscope effect: **![Image](https://www.cryengine.com/docs/static/attachments/44971437)** - ** No Change -** Oscillator is deactivated. - ** Pan Moving -**Texture shifts in the adjusted direction until the maximum amplitude is reached and back until the minimum amplitude is reached. Comparable to a pendulum movement: **![Image](https://www.cryengine.com/docs/static/attachments/44971438)** - ** Stretch Moving -**Similar to pen moving, but different in that the texture is stretched and not shifted to the adjusted direction until the maximum amplitude is reached and back until the minimum amplitude is reached: **![Image](https://www.cryengine.com/docs/static/attachments/44971439)** - ** Stretch-Repeat Moving -**Similar to stretch moving with the difference that the texture stretching restarts at 0 when the maximum amplitude is reached:![Image](https://www.cryengine.com/docs/static/attachments/44971440) - ** TypeV -** See TypeU - ** RateU & RateV** - ** PhaseU & PhaseV** - ** AmplitudeU & AmplitudeV** - ** AmplitudeV** |

The rotator and oscillator functions are only available for **diffuse** and ** decal** textures because of technical limitations.

You can create many interesting effects like animated glow by using the decal slot:

![Image](https://www.cryengine.com/docs/static/attachments/44971441)

#### Shader Params

A complete list of shader params will be added to the documentation soon.

#### Shader Generation Params

See [this page](../Graphics%20%26%20Rendering/Shaders/Shaders%20in%20CRYENGINE/Shader%20Features%20(Shader%20Generation%20Params).md) (and subpages).

#### Vertex Deformation

The **Vertex Deformation** function offers the opportunity to influence geometry.

A complete list of the Vertex Deformation params will be added to the documentation soon.

#### Layer Presets

The presets are a legacy feature and no longer supported.

### Usage

Below you will find some basic instructions on how to use the Material Editor Legacy.

#### Creating New Materials

New materials can be created in two ways:

- Pressing the Add New Item button on the [toolbar](Material%20Editor%20Legacy.md#MaterialEditorLegacy-Toolbar) while selecting the desired folder in the Browser;
- Right clicking on the desired folder and choosing Add New Material.
Adding a multi-material can only be done by using the second method.

#### Copying Material Parameters

Apart from copying an entire material, it is also possible to copy all parameters from a material and paste it into another material, essentially copying the material itself. This is especially useful when the second material has already been assigned to several objects and you want to change the material for all of those objects at the same time.

This also essentially creates two instances of the material that you can tweak separately.

To achieve this:

- Select the material you want to copy;
If you don't know the name of the material but do know an object that the material is assigned to, select the object, go to the Material Editor and click the **Get Properties from Selection** button.
Alternatively, you can start in the Material Editor by clicking the **Pick Material from Object** button and then clicking on the object in the viewport.
- Right click anywhere in the [Parameters](Material%20Editor%20Legacy.md#MaterialEditorLegacy-Parameters) panel;
- Select **Copy All**;
- Select the material you want to paste the parameters into;
- Again, right click in the Parameters panel,
- Select **Paste**.

[1. Menu](#1-menu)[2. Toolbar](#2-toolbar)[3. Browser](#3-browser)[4. Preview](#4-preview)[5. Parameters](#5-parameters)[Usage](#usage)
