# Vegetation 01 Grass (Patch)

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/24285885
- Page ID: 24285885
- Breadcrumb: Tutorials > Game and Level Design > Vegetation Tutorials > Tutorial - Vegetation Asset Creation > Vegetation 01 Grass (Patch)
- Parent: Tutorial - Vegetation Asset Creation

## Child Pages

- [Vegetation 01 Grass (Patch) 3dsMax](Vegetation%2001%20Grass%20(Patch)/Vegetation%2001%20Grass%20(Patch)%203dsMax.md)
- [Vegetation 01 Grass (Patch) Maya](Vegetation%2001%20Grass%20(Patch)/Vegetation%2001%20Grass%20(Patch)%20Maya.md)
- [Vegetation 01 Grass (Patch) CRYENGINE](Vegetation%2001%20Grass%20(Patch)/Vegetation%2001%20Grass%20(Patch)%20CRYENGINE.md)

## Content

##
Overview

To begin with, we shall start off with a basic grass patch asset. When we declare a grass asset to be a patch, we are actually referring to it as being a collection of randomly rotated planes of various sizes that are all baked into a single *.cgf file. The idea behind this setup is to have a single CGF file to cover a wide area (approximately 8m), hence to fill an area with grass you need less vegetation asset instances to completely cover the area.

For more information about using the Vegetation Editor in CRYENGINE, please go
**
[HERE.](../../../../Editor%20Tools/Vegetation%20Editor.md)
**

![Image](https://www.cryengine.com/docs/static/attachments/24156983)

*
Pic 1: Example of 3 grass patch models, a dense, medium and light variation.
*

![Image](https://www.cryengine.com/docs/static/attachments/24156984)

*
Pic 2: Example using the grass patches to fill an area with vegetation.
*

##
Helpful Information

Keep the following things in mind while working on your asset:

-
Usually, the grass patches version and the merged mesh version does not require a physics proxy.

-
If you enable the
*
grass
*
 flag in the Shader Generation Parameters, then you do not need a normalmap (optimization).

-
Each grass patch placed has its own set of drawcalls. Merged Mesh grass does not - it batches the chunks together.

-
Do not exceed a diameter of 8 meters for large grass patches. This size has proved to provide a good balance between performance and ground coverage.

-
Use minimum amount of polygons as possible while making a repetitive asset, such as grass. It will improve performance significantly.

-
Add LODs to the asset. Reduce the polygon count by 50% (if possible) on each LOD step.

##
Limitations of Grass Patches

##
Cannot Handle Big Changes in Terrain Angles

Grass patches are good for most use cases, although there are few instances where this is not the case. Since a patch covers a large portion of space (recommended to be approximately 8 meters), it is still considered as a flat plane. Hence, when you encounter variation in the terrain (different heights) some variation can be dealt with, however when extreme angles are encountered then it will adjust itself to be aligned perpendicular to the terrain. Since the patch is large, this can cause over flow into empty spaces.

In the example below
*
(Pic 3: Grass patch
*
limitation
*
*
), the grass is shown growing at an extreme angle (an unrealistic condition) which demonstrates the limitation of the grass patch. In this case, use the Merged Mesh Grass due to its smaller footprint.

![Image](https://www.cryengine.com/docs/static/attachments/24156985)

*
Pic 3:
*
Grass patch limitation
*
.
*

##
Doesn't Support Merged Mesh (MM) Technology

Due to the nature of Merged Mesh (MM) technology (which requires a very simple geometry setup of just 4 to 8 polys), when a geometry layout which consist of multiple mesh planes aligned at random angles, it becomes too complex to take advantage of this technology.

##
Tutorials

The following topics below explains the pipeline depending on the DCC tool you use, followed by the final CRYENGINE setup.

-
[Vegetation 01 Grass (Patch) 3dsMax](Vegetation%2001%20Grass%20(Patch)/Vegetation%2001%20Grass%20(Patch)%203dsMax.md)

-
[Vegetation 01 Grass (Patch) Maya](Vegetation%2001%20Grass%20(Patch)/Vegetation%2001%20Grass%20(Patch)%20Maya.md)

-
[Vegetation 01 Grass (Patch) CRYENGINE](Vegetation%2001%20Grass%20(Patch)/Vegetation%2001%20Grass%20(Patch)%20CRYENGINE.md)
[Helpful Information](#helpful-information)
[Limitations of Grass Patches](#limitations-of-grass-patches)
[Tutorials](#tutorials)
