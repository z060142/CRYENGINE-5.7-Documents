# Tutorial - Using Decals for Destroyed Structures

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/23308604
- Page ID: 23308604
- Breadcrumb: Tutorials > Digital Content Creation > Tutorial - Texturing > Tutorial - Using Decals for Destroyed Structures
- Parent: Tutorial - Texturing

## Content

### Overview

This guide describes the process of using alpha-blended decals to create broken concrete pieces and building ruins of high visual quality.

In most games destroyed walls and other buildings structures are done by simply cutting into the geometry and applying a tiling concrete texture to the broken area.

While it is performance-effective and simple to do this, the disadvantage of this technique is that you are left with a very visible and sharp seam between the two materials. It is a more work-intensive but visually better solution to use decals with alpha-blending in order to avoid these seams.

While both solutions use two material IDs, the new technique introduces additional overdraw through the alpha-blending and thus is the more expensive method.

#### Traditional Technique

Note the sharp seam between the two materials (marked in orange).

![Image](https://www.cryengine.com/docs/static/attachments/23999850)

![Image](https://www.cryengine.com/docs/static/attachments/23999851)

#### Alpha-Blended Decals

Note the more believable transition between the two materials (marked in orange).

![Image](https://www.cryengine.com/docs/static/attachments/23999852)

The normal map used for this decal:

![Image](https://www.cryengine.com/docs/static/attachments/23999853)

Example for "chipped-off" pieces using alphablend decals:

![Image](https://www.cryengine.com/docs/static/attachments/23999854)

The normal map used for this decal:

![Image](https://www.cryengine.com/docs/static/attachments/23999855)

#### Using These Decals in a 3D Application

- Add an extra geometry element for the broken edge.
- Extrude the border edges of this element inwards so they overlap the other material.
- Adjust the UV mapping of the element to create the overlap.

Here you can see the extra geometry element following the edge of your broken piece of building:

![Image](https://www.cryengine.com/docs/static/attachments/23999856)

Here you can see how the UV mapping must be adjusted to create a convincing overlap of the two materials:

![Image](https://www.cryengine.com/docs/static/attachments/23999857)

Use the chipped-off looking edge decals by

- Duplicating the geometry of whichever edge you want to use them on
- Cutting out the part where the decal will be visible
- Adjusting the UV mapping to show the decal in the right position

Illustration of these steps:

![Image](https://www.cryengine.com/docs/static/attachments/23999859)

Another example:

![Image](https://www.cryengine.com/docs/static/attachments/23999858)

For the best results, use the low-res geometry you used for rendering the normal map, snap them on the edge of the object you are working on, and cut its shape out of the solid block using the knife tool together with vertex snapping.

Using this method, you will also have the correct silhouette.

![Image](https://www.cryengine.com/docs/static/attachments/23999860)

[Traditional Technique](#traditional-technique)[Alpha-Blended Decals](#alpha-blended-decals)[Using These Decals in a 3D Application](#using-these-decals-in-a-3d-application)
