# Terrain Object Blending

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/29799251
- Page ID: 29799251
- Breadcrumb: Editor Tools > Terrain Editor > Terrain Object Blending
- Parent: Terrain Editor

## Content

![Image](https://www.cryengine.com/docs/static/attachments/29933263)

##
Overview

In CRYENGINE you can mark entities with a Mesh component to become a part of the terrain mesh. This dramatically extends the possibilities of current terrain editing tools, and thus allows for a much higher level of realism, overhanging materials and therefore much greater levels of flexibility.

![Image](https://www.cryengine.com/docs/static/attachments/36308969)

The object meshes can be copied
 into the heightmap mesh
at an early stage and become part of the terrain mesh that supports most of the heightmap properties, for example 3D terrain materials.

This only works for entities with a Mesh component attached, so an Empty Entity that you add a Mesh component to, or a Static Mesh Entity.

To activate this functionality, enable the
**
Integrate Objects
**
 option under the
**
Terrain
**
section of the
**
 Level Settings
**
.

![Image](https://www.cryengine.com/docs/static/attachments/36308970)

Now go to the
**
Properties
**
 of the entity and set the
GI and Usage Mode
to
**
Integrate into Terrain
**
.

![Image](https://www.cryengine.com/docs/static/attachments/36308971)

##
Console Variables

CVar/Command
 |
Description
 |
Comment and examples
 |

*
e_TerrainIntegrateObjectsMaxVerticesNum
*
 |
Preallocates a specified number of vertices to be used for the object's integration into terrain (per terrain sector)
0 - disables the feature completely

 |
Default is 30000 vertices
 |
