# Blend Layer - Shader Generation Params

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/29450135
- Page ID: 29450135
- Breadcrumb: Graphics & Rendering > Shaders > Shaders in CRYENGINE > Shader Features (Shader Generation Params) > Blend Layer - Shader Generation Params
- Parent: Shader Features (Shader Generation Params)

## Child Pages

- [Blend Layer - Best Practices](Blend%20Layer%20-%20Shader%20Generation%20Params/Blend%20Layer%20-%20Best%20Practices.md)

## Content

Overview

The blend layer feature allows mixing a second set of textures with the base set to get more variation on tiled surfaces.

The blending is primarily based on the vertex alpha channel and a generic blend map. The vertex alpha determines where the blend layer should be visible on the surface of the mesh.

Independent from the geometry tessellation, you can achieve smooth as well as very sharp transitions between the layers. A low number of vertices is sufficient for good looking results.

A very useful feature of the blend layer is that a heightmap can be used as blend map. This makes the blending follow the structure of the base texture.

*Example of the blend layer in an indoor environment*![Image](https://www.cryengine.com/docs/static/attachments/35395665)

*Example of the blend layer on a brick wall with green moss*![Image](https://www.cryengine.com/docs/static/attachments/35395666)

*In game asset with Illum shader and blend layer feature enabled*![Image](https://www.cryengine.com/docs/static/attachments/28898750)

The blend layer feature does not combine two generic materials, it rather blends specific textures of a single material. This means that the basic material settings apply to both layers.

The blend layer can have an individual diffuse map, a specular mask (in the alpha channel of the diffuse map) and a separate normal map.

Usually, this gives enough control to get great results with good performance. Shader values (spec intensity, glossiness) are applied to both layers (the base and the blend layer).

### Sandbox Material Setup

The blending can be enabled with the Blendlayer checkbox. Once active, several new shader parameters will show up:

Shader Param | Description
--- | ---
Blend Factor | Changes the overall blend factor. Use this to fade in and out the blend layer.
Blend Falloff | Specifies how smooth the transition between the layers should be. Use a high value for a sharp transition.
Blend Layer 2 Tiling | Change tiling of second blend layer.
Blend Mask Tiling | DEPRECATED - Specifies how often the blend layer textures are repeated (tiled). If you use heightmap that aligns with your base normal map, this parameter should usually be set to exactly 1.0, otherwise, the blend layer textures are rotated to make them appear less repetitive.
Blend Mask Rotation | DEPRECATED - Change rotation of blend mask.

Once Blendlayer is enabled, the available texture slots will update:

Texture Map | Description
--- | ---
Second Diffuse Map | Diffuse map of blend layer (with the specular mask in alpha). *In CRYENGINE 3.4 or earlier, this is the "Custom" slot.*
Second Bump Map | Normal map of blend layer. *In CRYENGINE 3.4 or earlier, this is the "[1] Custom" slot.*
Second Height Map | Displacement map of the blend layer.
Blending Map | The blend map (a generic grayscale texture, e.g. a noise texture, or a heightmap). *In CRYENGINE 3.4 or earlier, this is the "Opacity" slot.*

The blend map can be interpreted as if it would specify some height. This way you can have moss growing between the bricks.

If the blend factor is increased, by changing the vertex alpha, blend map or strength slider, the moss will slowly begin to cover the surface of the bricks.

*Example of Blend Layer setup in the Sandbox Material Editor*![Image](https://www.cryengine.com/docs/static/attachments/28898754)

The falloff can be useful to simulate different material types. With a high falloff value, you can get a hard blend to simulate for example rust on a metal surface. A low value gives a much smoother transition, as you would have it for snow on the ground.

The blend factor should normally be set to 16. If you want to tweak the blending, you should do it in 3ds Max via the Vertex Alpha. If you lower the blend factor you will lose range and control. A blend factor below 16 never allows you to reach the maximum blending.

### See Also

[Blend Layer - Best Practices](Blend%20Layer%20-%20Shader%20Generation%20Params/Blend%20Layer%20-%20Best%20Practices.md)

[Sandbox Material Setup](#sandbox-material-setup)[See Also](#see-also)
