# Ray Traced Shadows

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/36339974
- Page ID: 36339974
- Breadcrumb: Graphics & Rendering > Lighting > Lighting Overview > Voxel-Based Global Illumination (SVOGI) > Ray Traced Shadows
- Parent: Voxel-Based Global Illumination (SVOGI)

## Content

##
Overview

Ray traced shadows calculate the path of individual light rays from their source (the light) to their destination.

Ray traced shadows produce more physically accurate shadows, so turning this feature on makes shadows much more realistic.

Ray Traced Shadows in CRYENGINE can be broken down into two components.

##
 SVO Ray Traced Sun Shadows

This feature can be considered as an alternative for cached shadow maps.

![Image](https://www.cryengine.com/docs/static/attachments/36309126)

If SVOGI is already used in a level, this feature allows calculating shadows from the static world without the following known overheads of (cached) shadow maps:

-
No additional CPU side work

-
Performance is independent from scene complexity

-
Transparent shadows from transparent objects, soft volumetric shadow from leaves instead of detailed shadow map shadows that are too noisy

-
No additional allocations of huge cached shadow maps on GPU

-
No requirement for heavy shadow map updates when the sun is moving
SVO shadows also provide a soft penumbra without expensive filtering required for traditional shadow maps.

The most practical use case now is to limit number of sun shadow cascades to 2 and enable SVO traced shadows.

The drawback is the shadows are too soft in some cases mainly because softness depends from resolution of voxels.

##
Implementation

To turn this feature on, go to
**
Environment Editor -> Properties Panel -> Constants - Total Illumination Advanced
**
 and switch on
**
Shadows from Sun
**
.

When enabled, the GI system calculates an additional shadow mask containing shadows from all voxelized objects.

This mask is then combined with rest of the shadows. When not using this feature, the clouds shadow pass is used for that.

##
Ray Traced Shadows from Terrain Heightmap

This feature allows shadow casting from the entire height map, even at a distance of 8 km.

![Image](https://www.cryengine.com/docs/static/attachments/36309123)

This is a simple alternative to the traditional shadow mapping approach for distant shadows from big mountains.

Compared to shadow maps the advantages are:

-
No additional memory on GPU (textures and meshes) and system RAM (meshes)

-
No CPU side-processing; everything runs entirely on GPU

-
Soft shadow with very big penumbra is possible without heavy pixel shaders
For tracing the height map textures that are already allocated for terrain rendering are used.

Shadows are generated at a low screen resolution and then up-scaled using the SVOGI dual depth up-scale system.

##
Implementation

To turn this feature on, go to
**
Environment Editor -> Properties Panel -> Constants - Total Illumination Advanced
**
 and switch on
**
Shadows from Heightmap
**
.

This will only have any effect if
Shadows From Sun
 (see above) is also turned on.

##
CVars

Cvar/Command
 |
Description
 |

e_svoTI_ShadowsFromHeightmap
 |
Can be used to temporary disable/enable the feature
 |

[SVO Ray Traced Sun Shadows](#svo-ray-traced-sun-shadows)
[Implementation](#implementation)
[Ray Traced Shadows from Terrain Heightmap](#ray-traced-shadows-from-terrain-heightmap)
[Implementation](#implementation)
[CVars](#cvars)
