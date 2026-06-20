# Tutorial - Vegetation Asset Creation

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/24285884
- Page ID: 24285884
- Breadcrumb: Tutorials > Game and Level Design > Vegetation Tutorials > Tutorial - Vegetation Asset Creation
- Parent: Vegetation Tutorials

## Child Pages

- [Vegetation 01 Grass (Patch)](Tutorial - Vegetation Asset Creation/Vegetation 01 Grass (Patch).md)
- [Vegetation 02 Grass (Merged Meshes)](Tutorial - Vegetation Asset Creation/Vegetation 02 Grass (Merged Meshes).md)
- [Vegetation 03 Bushes (Detail Bending)](Tutorial - Vegetation Asset Creation/Vegetation 03 Bushes (Detail Bending).md)
- [Vegetation 04 Bushes (Touch Bending)](Tutorial - Vegetation Asset Creation/Vegetation 04 Bushes (Touch Bending).md)
- [Vegetation 05 Trees (Breakable)](Tutorial - Vegetation Asset Creation/Vegetation 05 Trees (Breakable).md)
- [Vegetation 06 Trees (Deform)](Tutorial - Vegetation Asset Creation/Vegetation 06 Trees (Deform).md)

## Content

##
Overview

This section covers the creation pipeline for moving your vegetation assets into CRYENGINE. It has been broken down into different sections, depending on the type of vegetation you want to create. There will be a dedicated category for detailing that pipeline.

For more information on using the Vegetation Editor, please refer
**
[/docs/static/engines/cryengine-5/categories/23756816/pages/36865590](
HERE
)
**
. This section deals with the asset creation pipeline.

[Image: /docs/static/attachments/24156982]

The major categories are:

-
[/docs/static/engines/cryengine-5/categories/23756816/pages/24285885](
Grass (patches) multi-plane geometry
)

-
[/docs/static/engines/cryengine-5/categories/23756816/pages/24285889](
Grass (merged mesh) simple geometry
)

-
[/docs/static/engines/cryengine-5/categories/23756816/pages/24285893](
Bushes (detail bending) applying noise to simulate movement
)

-
[/docs/static/engines/cryengine-5/categories/23756816/pages/24285898](
Bushes (touch bending) allows interaction with other physicalized entities
)

-
[/docs/static/engines/cryengine-5/categories/23756816/pages/24285901](
Trees (Boolean breakable)
)

-
[/docs/static/engines/cryengine-5/categories/23756816/pages/24285905](
Trees (Deform)
)
Few technologies that we use in our vegetation system, for example: detail bending, is not restricted to the bushes. You can apply the same technology on trees since they can be modified with simulating vegetation movement.
