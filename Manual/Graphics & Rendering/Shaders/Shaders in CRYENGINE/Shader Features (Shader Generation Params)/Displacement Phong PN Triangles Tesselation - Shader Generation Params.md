# Displacement/Phong/PN Triangles Tesselation - Shader Generation Params

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/29450127
- Page ID: 29450127
- Breadcrumb: Graphics & Rendering > Shaders > Shaders in CRYENGINE > Shader Features (Shader Generation Params) > Displacement/Phong/PN Triangles Tesselation - Shader Generation Params
- Parent: Shader Features (Shader Generation Params)

## Content

##
Overview

No pre-tessellated meshes are needed for this feature; essentially all you need to do is load a model and set up your material by enabling tessellation and/or displacement mapping.

This allows the artists to add definition into models like never before. The
**
Illum
**
,
**
 HumanSkin
**
 and
**
Vegetation
**
 shaders support Tessellation.

##
Supported Tessellation Schemes

Three types of Tessellation are supported:
**
Displacement
**
,
**
PN Triangles
**
 and
**
Phong
**
.

##
Displacement

![Image](https://www.cryengine.com/docs/static/attachments/28898718)

 |
![Image](https://www.cryengine.com/docs/static/attachments/28898709)

 |
![Image](https://www.cryengine.com/docs/static/attachments/28898711)

 |

Tessellation Factor 0
 |
Tessellation Factor 1
 |
Tessellation Factor 3
 |

##
PN Triangles

![Image](https://www.cryengine.com/docs/static/attachments/28898717)

 |
![Image](https://www.cryengine.com/docs/static/attachments/28898716)

 |

PN Triangles Enabled
 |
PN Triangles Disabled
 |

##
Phong

*
Phong Tessellation Scheme

*
![Image](https://www.cryengine.com/docs/static/attachments/28898712)

##
Tessellation / Displacement Shader Parameters

![Image](https://www.cryengine.com/docs/static/attachments/35397330)

Shader Gen Param

 |
Description

 |

**
Displacement mapping
**

 |
Scalar displacement stored in alpha channel of a
**
_displ
**
 texture.

 |

**
Phong Tessellation
**

 |
Very approximate smoothing based on normals, suffers from 'inflation', i.e. surface is not perfectly smooth across patch boundaries, looks a bit inflated.

Can be combined with displacement map.

 |

**
PN Triangles Tesselation
**

 |
Similar to Phong tessellation but slower with better approximation.

Can be combined with displacement map.

 |

![Image](https://www.cryengine.com/docs/static/attachments/35397330)

Shader Param

 |
Description

 |
Shader Gen Option

 |

**
Displacement Bias
**

 |
Allows you to move the plane from where the displacement is applied.

This is good for getting rid of gaps in meshes or preventing tessellated geometry to displace into other objects that are placed on top of them.

 |
Displacement

 |

**
Displacement Height Scale
**

 |
Allows you to change the height of the displacement.

 |
Displacement

 |

**
Tessellation Face Cull
**

 |
Defines the extent at which vertices are culled, this is used for 2-sided sorting of polygons (2 Sided must also be checked).

This is because tessellation has its own face culling, basically it takes the original (non-tessellated) triangle and checks if it's facing the camera; if not it throws it away.

The problem is when there is displacement which is visible from the camera even if the triangle is facing away (imagine spike from one side of the cube, if you rotate it the side is not facing camera but you still see the spike for a while).

So this param means no face culling at all for 0 and cull anything not facing camera when set to 1.

 |
PN / Phong

 |

**
Tessellation Factor
**

 |
Controls the density of the mesh triangles.

 |
 PN / Phong

 |

**
Tessellation Factor Min/Max
**

 |
In some cases (like a cutscene) where you know the object will be at a certain distance from camera (or fixed range) you can clamp the factor to get rid of view dependent tessellation factor which can result in geometry 'popping' artifacts. So for general cases you can just increase the factor, in special cases you can clamp it.

Setting min factor to 1 means that it will be always tessellated at level1 even if it's far away from camera.

 |
 PN / Phong

 |

##
Seams/Crack Fixing

There are two types of cracks that can become noticeable when using tessellation:

##
1. UV Seams

This occurs when two adjacent triangles share an edge but in fact they use separate vertices with different UV's.

This edge will then have different displacement on each side due to sampling different places in displacement map (even tiny differences in UV can cause visible cracks).

This is automatically fixed by the engine if there is no tiling otherwise the artist has to change the UV mapping to hide such artifacts if possible.

There is no such thing as UV seams for Phong tessellation or PN triangles as they do not use any UV mapping.

These approximate surface smoothing methods won't work properly if shared vertices of adjacent triangles have different normals (ie. normals are not smooth).

##
2. Border Seams

This occurs when different meshes placed close to each other (water tight) or a mesh consisting of sub-meshes can cause unpleasant cracks because of using different materials with different displacement (or even same displacement maps, slightly different UV mapping).

This is more tricky to fix automatically as the engine would have to check the world space position of all meshes, that's why the solution used in earlier builds was forcing to disable displacement on all (sub)mesh boundaries.

##
Manual Solution

Artist places meshes carefully and/or fades out displacement himself by modifying a displacement map where needed.

All of the tessellation schemes are enabled through the material editor and on a per material basis. This means that all objects with this material applied will be affected.

##
Automatic Solution

RC adds special flag to all boundary vertices, these are then not displaced at all. *This feature is currently disabled in the Resource Compiler*.

##
Troubleshooting

-
Height maps have to be explicitly stored using the _displ suffix, i.e. road_displ.tif. Save the displacement map in the alpha channel of your _displ texture. The RGB channels can be left empty.

-
Do NOT attach the height map as an alpha channel of the normal map. Using the alpha channel of the Normal map has been deprecated and will no longer work.

-
You must save your _displ texture using the CryTIF Photoshop plugin. The will write the correct meta data onto a .tif file for it to be converted to a .dds at run-time. In some cases you may need to click 'Generate Output' in the CryTIF dialogue.

-
When saving in CryTIF use the
**
DisplacementMap
**
 preset to store _displ textures. Height maps will be converted to A8 (BC4 for 3.7) textures.

-
If you don't see any displacement, double check the format in the Editor's texture file dialog preview. If it isn't A8/BC4, fix the preset then save and reload.

-
Set the Diffuse and Normal map textures as usual in the Material Editor. Also set the _displ texture in the
**
Heightmap
**
 slot.

-
Ensure you are in
**
Very High spec
**
 (CVar: sys_spec=4).

-
To enable tessellated shadows for tessellated Geom Entities, use
**
e_ShadowsTessellateCascades=1
**
, but keep in mind this comes at a performance cost.
[Supported Tessellation Schemes](#supported-tessellation-schemes)
[Tessellation / Displacement Shader Parameters](#tessellation-displacement-shader-parameters)
[Seams/Crack Fixing](#seamscrack-fixing)
[Troubleshooting](#troubleshooting)
