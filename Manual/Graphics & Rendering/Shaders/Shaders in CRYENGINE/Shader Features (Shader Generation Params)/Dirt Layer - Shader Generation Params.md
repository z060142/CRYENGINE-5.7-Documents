# Dirt Layer - Shader Generation Params

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/29450133
- Page ID: 29450133
- Breadcrumb: Graphics & Rendering > Shaders > Shaders in CRYENGINE > Shader Features (Shader Generation Params) > Dirt Layer - Shader Generation Params
- Parent: Shader Features (Shader Generation Params)

## Content

The Dirt Layer function is deprecated in favor of the superior Blend Shader. It will be removed in future revisions of CRYENGINE.

Note that the Blend Shader has the ability to use both Vertex Alpha and/or a dedicated Blend mask texture which allows for much more refined blending.

##
Overview

The dirt layer allows you to blend another texture onto your base material in the same draw call without the need to place an extra decal. The blended texture itself supports an alpha channel, and the amount of blending is controlled through the vertex alpha in your mesh and a shader attribute. Additionally, you can specify the tiling and the alpha for your dirt texture. Since the dirt texture uses the same UVs as the base diffuse texture, you can counteract unwanted tiling with the tiling parameter.

For more information please refer to the
[/docs/static/engines/cryengine-5/categories/23756816/pages/29449070](
Illum Shader
)
 for more information.

##
Setup in 3ds Max

##
Applying the Dirt to the Object

To set up the asset, apply a VertexPaint modifier to your mesh and set its channel to Vertex Alpha. You can now paint the areas that are supposed to be affected by dirt. Black will set the opacity of your dirt layer to 100% and make the dirt fully visible, white will not show any dirt at all. Shades of gray will blend between both dirt and the base diffuse texture. You can also select a bunch of vertices and give them a typed-in vertex alpha value. The
**
Alpha Value
**
 can be set under the
**
 Vertex Properties
**
 tab when in
**
Vertex Selection Mode
**
.

[Image: /docs/static/attachments/35397190]

To only see the vertex alpha in the viewport,
**
right click
**
 on your object, check
**
Vertex Channel Display
**
, and set it to
**
Vertex Alpha
**
.

[Image: /docs/static/attachments/35397188]

##
Setup in XSI

##
XSI Workflow

-
Model and texture your object normally with standard materials and a diffuse texture.

-
Select your object and from
**
Render
**
 toolbar choose
**
Get –> Property –> Color
**
 at
**
Vertices Map
**
.

-
Go to
**
Camera Display Property Editor
**
 and set
**
Vertex Color Property Display
**
 to
**
Show Alpha
**
.

-
Press
**
Ctrl+W
**
 to open
**
Brush Properties
**
 property editor and set the
**
Color Paint Mode
**
 to
**
Alpha
**
.

-
To set the
**
Alpha
**
 value, you must use the
**
A slider
**
 in the palette controls' RGBA sliders.

-
Where your object has transparent vertices, there the dirt layer will be visible.

-
Export your object to CRYENGINE.

-
Set up dirt layer materials in CRYENGINE.

##
Usage in CRYENGINE

[Image: /docs/static/attachments/35397191]

The dirt layer currently only works with the Illum shader.

-
Load up your Dirt Texture in the Dirt Map slot of the shader.

-
Check Dirtlayer under Shader Generation Params to enable the Dirt layer parameters.
You must manually set up each Dirt layer to match the parameters you used in the Max DirectX Dirt layer:

-
**
Dirt Gloss
**
 allows you to set the glossiness of your Dirt texture.

-
**
Dirt Strength
**
 allows you to set the overall opacity of your Dirt texture.

-
**
Dirt Tiling
**
 allows you to set the scale of your Dirt texture.

-
**
Dirt Tint
**
 allows you to tint your texture. Set it to white for no tinting.

##
Using the Dirt Layer

The idea behind the dirt layer is to add detail to objects without having a heavy impact on performance. Since you are limited to small tiling textures and a few materials, the dirt layer allows you to add visual variety in objects while not adding too many new textures.

By using the vertex alpha you ensure that you can still use vertex colors to add additional shading information to our meshes.

Every dirt texture should be tillable and reusable on other assets. Your goal should be to create a library of textures to dirty up all of the base materials.

##
Chipped Paint

Here is a 256x256 tileable concrete texture as a base. The Dirt texture itself is a white concrete material with a mask in the alpha channel to create the "chipped paint" effect. The resolution of the Dirt texture is 512x512 in order to keep the mask crisp.

By using white as a base color, you can easily tint the Dirt texture through the tint attribute in the shader. By adding edges and modifying the vertex alpha, you can specify where you want your texture to be blended in.

[Image: /docs/static/attachments/28898741]

##
Walls and Other Objects

Here you can see how you can use the same dirt mask to dirty up different kind of materials.

[Image: /docs/static/attachments/28898742]

##
Adding Variation to Essential Objects

In some cases, it can be beneficial to create a dirt texture that is unique and not tiling.

For example, in the following examples there are a lot of metal planks that are used as roofing for buildings. This means that these objects are often visible and need to be visually interesting. In order to achieve that, you should define the shapes that you want for the metal planks.

In order to make the most of the textures, make sure that they use the available UV Space to the fullest extent. After creating the mask, specify which planks will be colored (and in what way) and build the objects with the predefined pieces.

[Image: /docs/static/attachments/35397192]

##
Making the Most of the Dirt Layer

Use a tiling base texture to start with. Create an interesting dirt texture in order to add variance to the base texture. Use vertex colors to add subtle color variation and basic ambient occlusion. Make sure to use all of these three elements whenever possible.

[Image: /docs/static/attachments/35397193]

##
Reusing the Dirt Textures

If you have a good base texture with a strong normalmap, it is worth trying to reuse existing dirt textures/masks on your material before creating a new one.

Often you can achieve the desired effect with already existing textures and the tinting functionality in the shader. This saves texture memory and time.

[Image: /docs/static/attachments/35397194]

[#setup-in-3ds-max](
Setup in 3ds Max
)
[#setup-in-xsi](
Setup in XSI
)
[#usage-in-cryengine](
Usage in CRYENGINE
)
[#using-the-dirt-layer](
Using the Dirt Layer
)
