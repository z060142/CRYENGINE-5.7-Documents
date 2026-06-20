# Designer Tool

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/36869859
- Page ID: 36869859
- Breadcrumb: Editor Tools > Level Editor Tab > Create Object > Designer Tool
- Parent: Create Object

## Content

## Overview

The Designer option in the Create Object tool is used to add simple geometric shapes to a level, a shape(s) can then be edited using the Designer Tool which is found under the Tools Menu. The following options are available:

- **Designer Box**
- **Designer Cone**
- **Designer Cylinder**
- **Designer Sphere**

![Image](https://www.cryengine.com/docs/static/attachments/44966507)

To modify an object, click the **Edit** button under the Designer's Properties panel. For more information, please refer to [Designer Tool Tab](../../Designer%20Tool%20Tab.md).

### Properties

To access the Designer's properties, make sure to select the Designer Entities from the Create Object tab and drop them into the level.

Property | Description
--- | ---
**Cast Shadows** | When this option is set, the object will cast shadows onto other geometry/terrain/etc.
**Global Illumination** | Enables/disables voxelization for GI (this affects indirect occlusion from an object).
**Support Second VisArea** | Normally, objects are considered to be in only one VisArea. This option allows them to be added to multiple VisAreas (if their bounding box overlaps them), this does have a performance cost. Without this option, some large objects may not be displayed when viewed through portals (in certain situations).
**Outdoor** | When enabled, the entity ignores the use of VisAreas in the level. Multiple Vis Areas can be combined to define the points from where the would be visible/invisible. For more information, please see the [Vis Area](Area/Vis%20Area.md) page.
**Rain Occluder** | Set the brush to occlude rain, this works in conjunction with the Rain Entity. If your level does contain rain, you should set this wisely as there is a limit of 512 objects that can occlude at any given time.
**View Distance Ratio** | Defines how far from the current camera position the object can be seen.
**Exclude From Navigation** | When this option is set, the object will not be considered as a part of the AI triangulation system. This ensures that the geometry of the object will not contribute to NavMesh generation and it will not generate any NavMesh on top of the object, or any hole in the NavMesh where the object is placed.
**AI Hideable** | When this option is set, AI will use this object as a hiding spot (using the specified hide point type).
**No Dynamic Water** | Avoids boolean-merge on any surrounding static that intersects with the first vessel.
**No Static Decals** | When this option is set, decals will not project onto the object.
**Occluder** | Used for the construction of a level occlusion mesh.
**Ignore Terrain Layer Blend** | Controls blending with terrain layers. For more information, please refer to the [Terrain Layer Blending into Objects](../../../Materials/Terrain%20Layer%20Blending%20into%20Objects.md) page.
**Ignore Decal Blend** | Controls blending with decals. For more information about Decals, please refer to the [Decal](Misc%20Objects/Decal%20Entity.md) page.
**Edit** | Lets you open the **Designer Tool** to edit the Designer Entity.
