# Blend Layers

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/25534113
- Page ID: 25534113
- Breadcrumb: Asset Prep (External) > Asset Exporting Overview > Texture Creation Overview > Blend Layers
- Parent: Texture Creation Overview

## Content

[Image: /docs/static/attachments/29933275]

##
Overview

##
Sections

The blend layer feature allows mixing a second set of textures with the base set to get more variation on tiled surfaces. The blending is primarily based on the vertex alpha channel and a generic blend map. The vertex alpha determines where the blend layer should be visible on the surface of the mesh. Independent from the geometry tessellation, you can achieve smooth as well as very sharp transitions between the layers. A low number of vertices is sufficient for good looking results.

A very useful feature of the blend layer is that a heightmap can be used as blend map. This makes the blending follow the structure of the base texture.

[#sections](
Sections
)
[#3ds-max-asset-setup](
3ds Max Asset Setup
)

##
3ds Max Asset Setup

Add a vertex paint modifier to the stack and change the channel to vertex alpha. This is very important to separate, as you must use vertex alpha for this feature and not vertex color.

Open the objects property window of the asset and enable vertex color display, but change the display to vertex alpha. To be sure that you don't paint the wrong channel you can always switch back and forth to vertex color preview.

All the textures are tiled and do not use unique UV shells. You cannot use a baked ambient OCC map in this case, but it is still possible to use baked vertex color shadows on the asset.

*
Vertex alpha setup in 3ds Max.
*

You can use our blend shader for 3ds Max not just for previewing the result but also to paint your vertex alpha in real time.

Open up the material editor and switch the standard material to a DirectX shader where you can load the blend layer shader instead and get all the similar parameters of the sandbox editor to tweak the values.

*
Layer blend shader for preview in 3ds Max.
*
