# Vegetation

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/25534107
- Page ID: 25534107
- Breadcrumb: Asset Prep (External) > Asset Exporting Overview > Texture Creation Overview > Vegetation
- Parent: Texture Creation Overview

## Content

[Image: /docs/static/attachments/29933577]

##
Overview

##
Section

The vegetation shader provides special features for foliage and grass, most notably translucency (light transmittance).

To open the material dialog for vegetation objects, right-click on your object in the vegetation list and press "Go To Object Material". For more information on vegetation please visit the
[/docs/static/engines/cryengine-3/categories/1114113/pages/1310884](
Vegetation
)
 section.

[#section](
Section
)
[#textures](
Textures
)
[#shader-parameters](
Shader Parameters
)
[#shader-generation-parameters](
Shader Generation Parameters
)

##
Textures

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

[Image: /docs/static/attachments/28898612]

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
[/docs/static/engines/cryengine-3/categories/1114113/pages/1048776](
Tessellation and Displacement
)
 for more information.

 |

**
Detail
**

 |
See
[/docs/static/engines/cryengine-3/categories/1114113/pages/1048715](
Unified Detail Mapping
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
[/docs/static/engines/cryengine-3/categories/1114113/pages/1048616](
Blend Layer
)
 for more information.

 |

**
Second Gloss Map
**

 |
See
[/docs/static/engines/cryengine-3/categories/1114113/pages/1048616](
Blend Layer
)
 for more information.

 |

**
Second Height Map
**

 |
See
[/docs/static/engines/cryengine-3/categories/1114113/pages/1048616](
Blend Layer
)
 for more information.

 |

**
Second Diffuse Map
**

 |
See
[/docs/static/engines/cryengine-3/categories/1114113/pages/1048616](
Blend Layer
)
 for more information.

 |

**
Second Bump Map
**

 |
See
[/docs/static/engines/cryengine-3/categories/1114113/pages/1048616](
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
Bending branch amplitude
**

 |
Defines the movement of blue color in the in the complex bending setup.

 |
All

 |

**
Bending edges amplitude
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
See
[/docs/static/engines/cryengine-3/categories/1114113/pages/1048616](
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
See
[/docs/static/engines/cryengine-3/categories/1114113/pages/1048616](
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
See
[/docs/static/engines/cryengine-3/categories/1114113/pages/1048616](
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
See
[/docs/static/engines/cryengine-3/categories/1114113/pages/1048616](
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
Cap opacity fall off
**

 |
Controls how strongly vegetation polygons fade out when looking at them at a steep angle. This helps to disguise the plane shape of vegetation geometry.

 |
Leaves

 |

**
Detail Bending frequency
**

 |
Defines the bending speed for complex (wind) bending. Always make sure that this is in the right proportion to the wind in your level.

 |
All

 |

**
Indirect bounce color
**

 |
See
[/docs/static/engines/cryengine-3/categories/1114113/pages/1048911](
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
Detail bending
**

 |
Detail bending simulating wind on vegetation objects.

 |

**
Detail mapping
**

 |
See
[/docs/static/engines/cryengine-3/categories/1114113/pages/1048715](
Unified Detail Mapping
)
 for more information.

 |

**
Blendlayer
**

 |
**
DEPRECATED (Prefer Illum shader for surfaces that require the blend layer)
**

See
[/docs/static/engines/cryengine-3/categories/1114113/pages/1048616](
Blend Layer
)
 for more information.

 |

**
Displacement mapping
**

 |
See
[/docs/static/engines/cryengine-3/categories/1114113/pages/1048911](
Illum Shader
)
 for more information.

 |

**
Phong tessellation
**

 |
See
[/docs/static/engines/cryengine-3/categories/1114113/pages/1048911](
Illum Shader
)
 for more information.

 |

**
PN triangles tessellation
**

 |
See
[/docs/static/engines/cryengine-3/categories/1114113/pages/1048911](
Illum Shader
)
 for more information.

 |
