# Area Objects

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/27593384
- Page ID: 27593384
- Breadcrumb: Entities and Tools > Entities Overview > Area Objects
- Parent: Entities Overview

## Child Pages

- [Occlusion - Preparing a Level](Area%20Objects/Occlusion%20-%20Preparing%20a%20Level.md)
- [Solids](Area%20Objects/Solids.md)

## Content

![Image](https://www.cryengine.com/docs/static/attachments/29933296)

### Overview

The area objects are used to create three dimensional zones in the level that can be used to trigger events. Access the Area Objects via the [Create Object tool](../../Editor%20Tools/Level%20Editor%20Tab/Create%20Object.md).

### Box

This entity lets you create a box to which you can link triggers and other entities that should be enabled when the player enters or leaves the box.

**Params** | **Descriptions**
--- | ---
**AreaId** | Sets up the ID of the area, so areas with another ID can overlap.
**FadeInZone** | Specifies in meters how big the zone around the box is that is used to fade in the effect attached to the box. Only when the player is inside the box the effect is rendered at 100%, at the beginning of the FadeInZone its rendered at 0%.
**Width** | Specifies how wide the box is.
**Length** | Defines how long the box is.
**Height** | Specifies how high the shape area should be (0 means infinite height).
**GroupId** | Sets up the Group ID of the area, so areas with another group ID can overlap.
**Priority** | Defines the Priority so areas with a higher priority will be processed first.
**ObstructRoof** | **DEPRECATED -** This enables if the roof should be obstructed.
**ObstructFloor** | **DEPRECATED -** This enables if the floor should be obstructed.
**Filled** | Just for visibility in the editor this option defines if the area should be rendered as filled or not.
**DisplaySoundInfo** | Enable to expand Sound Obstruction options.

### Solid

Please see the [AreaSolid](/docs/static/engines/cryengine-3/categories/1114113/pages/1048858) documentation for more information.

### Sphere

To the AreaSphere you can link triggers and other entities that should be enabled when the player enters or leaves the sphere.

**Params** | **Descriptions**
--- | ---
**AreaId** | Sets up the ID of the area, so areas with another ID can overlap.
**FadeInZone** | Specifies in meters how big the zone around the box is that is used to fade in the effect attached to the box. Only when the player is inside the box the effect is rendered at 100%, at the beginning of the fadeinzone its rendered at 0%.
**Radius** | Specifies how big the sphere should be.
**GroupId** | Sets up the Group ID of the area, so areas with another group ID can overlap.
**Priority** | Defines the Priority so areas with a higher priority will be processed first.
**Filled** | Just for visibility in the editor this option defines if the area should be rendered as filled or not.

### OccluderArea

An Occluder Area allows you to create an occlusion plane out of a custom shape with multiple edges, unlike an Occluder Plane object which can only be a square shape.

The purpose of this object is to stop the engine from rendering everything that is behind it. It is used for performance optimization in areas where automatic occlusion from brushes and terrain don't work very well.

**Params** | **Descriptions**
--- | ---
**DisplayFilled** | Just for visibility in the editor this option defines if the area should be rendered as filled or not.
**CullDistRatio** | Specifies at what distance the culling effect should stop occurring.
**UseIndoors** | Specifies if the occluder area should be working inside an indoor visarea.

### OccluderPlane

An Occluder Plane can be used to occlude objects behind the plane. Like Occluder Area's, this typically isn't required because occlusion is done automatically through the assets, these can be used as a fallback method.

**Params** | **Descriptions**
--- | ---
**Height** | Specifies how high the occluder plane is.
**DisplayFilled** | Just for visibility in the editor this option defines if the plane should be rendered as filled or not.
**CullDistRatio** | Specifies at what distance the culling effect should stop occurring.
**UseIndoors** | Specifies if the occluder plane should work inside a visarea.
**DoubleSide** | Specifies if the occluder plane should work from both sides.

### Portal

Please see the [Vis Area](../../Editor%20Tools/Level%20Editor%20Tab/Create%20Object/Area/Vis%20Area.md) and [Portal](../../Editor%20Tools/Level%20Editor%20Tab/Create%20Object/Area/Portal.md)documentation pages for more information.

### Shape

This object lets you create a shape to which you can link triggers and other entities that should be enabled when the player enters or leaves the area shape.

**Params** | **Descriptions**
--- | ---
**Width** | Specifies how wide the entity is.
**Height** | Specifies how high the shape area should be (0 means infinite height).
**AreaId** | Sets up the ID of the area, so areas with another ID can overlap.
**GroupId** | Sets up the Group ID of the area, so areas with another group ID can overlap.
**Priority** | Defines the Priority so areas with a higher priority will be processed first.
**Closed** | Sets if the area should be closed or if it should be just a line.
**ObstructRoof** | **DEPRECATED -** This enables if the roof should be obstructed.
**ObstructFloor** | **DEPRECATED -** This enables if the floor should be obstructed.
**DisplayFilled** | Just for visibility in the editor this option defines if the area should be rendered as filled or not.
**DisplaySoundInfo** | Enable to expand Sound Obstruction options.
**Agent_height** | When Render_voxel_grid is enabled this determines the height - along the y axis - of the grid cells rendered.
**Agent_width** | When Render_voxel_grid is enabled this determines the height - along the x axis - of the grid cells rendered.
**Render_voxel_grid** | If true, voxel grid will be rendered when helpers are enabled.
**voxel_offset_x** | Offset voxel grid on the X axis.
**voxel_offset_y** | Offset voxel grid on the Y axis.

### Vis Area

Please see [Vis Area](../../Editor%20Tools/Level%20Editor%20Tab/Create%20Object/Area/Vis%20Area.md) and [Portal](../../Editor%20Tools/Level%20Editor%20Tab/Create%20Object/Area/Portal.md)documentations for more information.

### WaterVolume

Please see the [Water Volume](../../Editor%20Tools/Level%20Editor%20Tab/Create%20Object/Area/Water%20Volume.md) article for more information.

[Box](#box)[Solid](#solid)[Sphere](#sphere)[OccluderArea](#occluderarea)[OccluderPlane](#occluderplane)[Portal](#portal)[Shape](#shape)[Vis Area](#vis-area)[WaterVolume](#watervolume)
