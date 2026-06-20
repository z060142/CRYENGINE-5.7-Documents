# Vegetation Shader

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/29449329
- Page ID: 29449329
- Breadcrumb: Graphics & Rendering > Shaders > Shaders in CRYENGINE > Shader Reference > Vegetation Shader
- Parent: Shader Reference

## Content

##
Overview

Vegetation shader provides special features for foliage and grass, most notably translucency (light transmittance). To open the material dialog for vegetation objects, right-click on your object in the vegetation list and press "Go To Object Material".

For more information on vegetation, please visit the
[/docs/static/engines/cryengine-5/categories/23756816/pages/36865590](
Vegetation Editor
)
 section.

##
Textures Maps

The Vegetation shader texture setup is very close to Illum with some additional vegetation-specific features.

Texture Slot

 |
Description

 |

**
Diffuse

**

 |
RGB contains diffuse color. Alpha should contain opacity (used for alpha test).

[Image: /docs/static/attachments/35402186]

 |

**
Specular
**

 |
RGB contains specular color. Specular is not used with the 'Grass' option enabled.

With PBR, using a constant specular color instead of a map is enough in most cases.

 |

**
Bumpmap
**

 |
RGB contains normal map. DDNA Alpha contains smoothness map.

 |

**
Heightmap
**

 |
See
[/docs/static/engines/cryengine-5/categories/23756816/pages/29450127](
Displacement/Phong/PN Triangles Tesselation - Shader Generation Params
)
 for more information.

 |

**
Detail
**

 |
See
[/docs/static/engines/cryengine-5/categories/23756816/pages/29449936](
Detail Mapping - Shader Generation Params
)
 for more information.

 |

**
Opacity

**

 |
Grayscale map that defines the thickness of foliage and how much light can pass through from the backside (transmittance).

[Image: /docs/static/attachments/28898610]

 |

**
Blending Map
**

 |
See
[/docs/static/engines/cryengine-5/categories/23756816/pages/29450135](
Blend Layer
)
 for more information.

 |

**
Second Gloss Map
**

 |
See
[/docs/static/engines/cryengine-5/categories/23756816/pages/29450135](
Blend Layer
)
 for more information.

 |

**
Second Height Map
**

 |
See
[/docs/static/engines/cryengine-5/categories/23756816/pages/29450135](
Blend Layer
)
 for more information.

 |

**
Second Diffuse Map
**

 |
See
[/docs/static/engines/cryengine-5/categories/23756816/pages/29450135](
Blend Layer
)
 for more information.

 |

**
Second Bump Map
**

 |
See
[/docs/static/engines/cryengine-5/categories/23756816/pages/29450135](
Blend Layer
)
 for more information.

 |

##
Shader Parameters

**
Shader Params
**

 |
**
Description
**

 |
**
Shader Gen Requirement
**

 |

**
Bending Branch Amplitude
**

 |
Defines the movement of blue color in the in the complex bending setup.

 |
All

 |

**
Bending Edges Amplitude
**

 |
Defines the movement of red color in the in the complex bending setup.

 |
All

 |

**
Blend Factor
**

 |
Changes visibility of blending layer.
**
Blendlayer
**
 generation parameter must be enabled first.
See
[/docs/static/engines/cryengine-5/categories/23756816/pages/29450135](
Blend Layer
)
 for more information.

 |
Blend Layer

 |

**
Blend Falloff
**

 |
Changes the fall off of blending.
See
[/docs/static/engines/cryengine-5/categories/23756816/pages/29450135](
Blend Layer
)
 for more information.

 |
Blend Layer

 |

**
Blend Layer 2 Spec
**

 |
Changes specular intensity of second blend layer.
**
Blendlayer
**
 generation parameter must be enabled first.
See
[/docs/static/engines/cryengine-5/categories/23756816/pages/29450135](
Blend Layer
)
 for more information.

 |
Blend Layer

 |

**
Blend Layer 2 Tiling
**

 |
Changes tiling of second blend layer.
**
Blendlayer
**
 generation parameter must be enabled first.
See
[/docs/static/engines/cryengine-5/categories/23756816/pages/29450135](
Blend Layer
)
 for more information.

 |
Blend Layer

 |

**
Blend Mask Tiling
**

 |
Change tiling of blend mask.

 |
Default

 |

**
Cap Opacity Falloff
**

 |
Controls how strongly vegetation polygons fade out when looking at them at a steep angle. This helps to disguise the plane shape of vegetation geometry.

 |
Leaves

 |

**
Detail Bending Frequency
**

 |
Defines the bending speed for complex (wind) bending. Always make sure that this is in the right proportion to the wind in your level.

 |
All

 |

**
Indirect Bounce Color
**

 |
Sets the amount of indirectly bounced color.
See
[/docs/static/engines/cryengine-5/categories/23756816/pages/29449070](
Illum Shader
)
 for more information.

 |
All

 |

**
Normal View Dependency
**

 |
Controls how strongly normals get oriented towards the viewer/camera. This helps to reduce an overly strong specular gain on vegetation planes. (0 = off, 1 = fully on)
 |
Leaves / Grass
 |

**
Terrain Color Blend
**

 |
Controls how much of the terrain color should be blended into the diffuse color when up close (0 = off, 1 = on).

You have to check "Use Terrain Color" for the specific vegetation object to enable the feature, except when using AutoMerge.

 |
All

 |

**
Terrain Color Blend Dist
**

 |
Controls how much of the terrain color should be blended into the diffuse color at a distance. This helps to make the vegetation merge visually with the terrain to make LOD popping and aliasing less apparent.

You have to check "Use Terrain Color" for the specific vegetation object to enable it, except when using AutoMerge.

 |
All

 |

**
Transmittance Color
**

 |
Color tint for transmitted light.

 |
Leaves / Grass

 |

**
Transmittance Multiplier
**

 |
Scale factor for opacity map values.

 |
Leaves / Grass
 |

**
Vtx Alpha Blend Factor
**

 |
Deprecated.
 |
Default

 |

##
Shader Generation Parameters

**
Shader Gen Params
**

 |
**
Description
**

 |

**
Leaves
**

 |
More complex shading for foliage. This will allow you to use an opacity map to control the translucency of the "leaves".

 |

**
Grass
**

 |
Cheap shading for grass which essentially ignores specular and normal map settings. Use Leaves option when higher shading quality is desired for grass.

 |

**
Detail Bending
**

 |
Detail bending simulating the wind on vegetation objects.

 |

**
Detail Mapping
**

 |
Enables detail mapping.
See
[/docs/static/engines/cryengine-5/categories/23756816/pages/29449936](
Detail Mapping - Shader Generation Params
)
 for more information.

 |

**
Blendlayer
**

 |
Enables normal-mapped diffuse layer blended on top of the base material.
See
[/docs/static/engines/cryengine-5/categories/23756816/pages/29450135](
Blend Layer
)
 for more information.

 |

**
Extended Bending
**

 |
Provides more control over detail bending. It allows not only small micro movement on leaves, but also whole branches of trees or chunks of grass, and also world-space mapped noise texture is used to simulate random breeze to add another variation to the movement.

Make sure, you activate the
**
Receive Wind
**
 option in the Object's Properties section before you enable this effect.

 |

**
Displacement Mapping
**

 |
Enables displacement mapping. Requires a height map.
See
[/docs/static/engines/cryengine-5/categories/23756816/pages/29449070](
Illum Shader
)
 for more information.

 |

**
Phong Tessellation
**

 |
Enables rough approximation of smooth surface subdivision..
See
[/docs/static/engines/cryengine-5/categories/23756816/pages/29449070](
Illum Shader
)
 for more information.

 |

**
PN Triangles Tessellation
**

 |
*
PN
(Point-Normal)
*
triangles tessellation e
*
*
nables rough approximation of surface subdivision in a
 low polygon mesh
.
See
[/docs/static/engines/cryengine-5/categories/23756816/pages/29449070](
Illum Shader
)
 for more information.

 |
