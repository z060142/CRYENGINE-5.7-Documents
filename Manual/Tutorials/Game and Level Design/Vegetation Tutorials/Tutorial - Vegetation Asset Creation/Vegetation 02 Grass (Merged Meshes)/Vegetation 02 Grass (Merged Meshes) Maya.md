# Vegetation 02 Grass (Merged Meshes) Maya

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/24285891
- Page ID: 24285891
- Breadcrumb: Tutorials > Game and Level Design > Vegetation Tutorials > Tutorial - Vegetation Asset Creation > Vegetation 02 Grass (Merged Meshes) > Vegetation 02 Grass (Merged Meshes) Maya
- Parent: Vegetation 02 Grass (Merged Meshes)

## Content

##
Overview

In this tutorial, we will be using our Merged Mesh system and show you the process of how to setup bendable grass blades. Merged Meshes are mainly used to handle areas with dense numbers of vegetation objects like big fields of grass. Merged Meshes also allows the usage of a rope based bending effect. Ropes get generated for each asset instance to bend it upon impact.

Contrary to bone based setups like Touch Bending, ropes can be cheaper and get affected through the global wind and our Breeze Generation system. Large fields of grass are perfect examples to showcase this type of technology since each asset instance can be merged into bigger clusters through the merged mesh system. So for this tutorial, we will create two simple grass plane assets as a base for a dense overgrown grass field.

*
![Image](https://www.cryengine.com/docs/static/attachments/26509595)

Pic1: Dense grass field affected through wind
*

*
![Image](https://www.cryengine.com/docs/static/attachments/26509594)

Pic2: Two assets that this entire grass field contains
*

##
Tutorial Files

Source Maya scene with exported CRYENGINE files:

**
[GameSDK_vegtut02_files.zip](/docs/static/attachments/25523836)
**

##
Pre-requisites for this Tutorial

Before you continue with this tutorial, make sure to have read and understood the following:

-
[How to Install CryMayaTools](../../../../../CRYENGINE%20-%20Getting%20Started/Installing%20CRYENGINE/CRYENGINE%20Plugins%20and%20Tools/Installing%20the%20Maya%20Tools.md)

-
[The Basic CRYENGINE Maya Workflow](../../../../../Asset%20Prep%20(External)/Asset%20Exporting%20Overview/Preparing%20Assets%20for%20CRYENGINE/Basic%20Asset%20Setup%20and%20Export%20-%20Maya.md)

-
[CRYENGINE Exporter](../../../../../CRYENGINE%20-%20Getting%20Started/Installing%20CRYENGINE/CRYENGINE%20Plugins%20and%20Tools/Installing%20the%20Maya%20Tools/CRYENGINE%20User%20Interface%20in%20Maya.md)

-
[Maya Unit Scale to Match up With CRYENGINE Unit System](../../../../../Asset%20Prep%20(External)/Measurement%20Reference%20-%20(DCC%20Unit%20Setup).md)

##
Helpful Information

Make sure to keep the following things in mind while you work on your assets:

-
Align your locators to your geometry surface; snapping to individual vertices is not necessary, these locators are the anchor points for CRYENGINE to create a linear spline, which it uses to bend the grass blades.

-
The three locators need to follow the naming convention rules for Merged Mesh to recognize them: "
**
branch1_1" (bottom), "branch1_2" (mid) and "branch1_3"
**
 (top).

-
Use the
**
Local Scale
**
 attribute in the shape node of your locator if you want to change their display size.

-
It's useful to keep the amount of different materials for merged meshes as low as possible, to keep the memory usage low for console systems. Use one large texture sheet that contains multiple variations.

-
Keep your geometry simple and planar.

-
Collision proxies are not needed so do not create any custom ones.

-
The grass blades should be as low-poly as possible for consoles, to guarantee that they do not have to stream in and merge large amounts of mesh data. You can also disable vertex colors for these, while exporting to decrease the size further.

-
You do not need to make LODs for assets using this system. The Merged Meshes technology batches together the vegetation into 16m cells that internally LODs itself, by removing items as the camera gets further away from the "sector".
Merged Meshes has some improvements but also some missing features compared to Touch Bending. This table gives you an overview about the differences between those two systems. Use this to decide which type of feature works best for your asset.

**
Description
**
 |
**
Merged Mesh
**
 |
**
**
Touch Bending
**
**
 |

**
Type of bending
**
 |
Ropes
 |
Bones
 |

**
Instance merging to clusters
**
 |
Yes
 |
No
 |

**
Influenced by Wind
**
 |
Yes
 |
No
 |

**
Influenced by Breeze gen
**
 |
Yes
 |
No
 |

**
**
**
Requires simplified geometry (low poly count)
**
**

**
 |
No
 |
Yes
 |

**
Bone parenting support
**
 |
No
 |
Yes
 |

**
Proxy support
**
 |
No
 |
Yes
 |

**
UV instancing for bones
**
 |
No
 |
Yes
 |

##
Initial Maya setup

For this tutorial, we will be creating our asset in the following directory.

-
`
<
`
*
Your_Project
*
>\Assets\
`
Objects\tutorial\vegetation\02\grass\merged_mesh\
`
So to begin with, save your Maya scene to this location. All our exported assets will be saved in there. Some of the textures we will use comes from an already existing asset and we will point you to the directory where they are later in the tutorial.

We will continue with the assumption that you have already created the asset, since this is not a Maya modeling tutorial. We will begin with preparing the asset ready for CRYENGINE and configuring the material.

![Image](https://www.cryengine.com/docs/static/attachments/24157054)

*
Pic3: This is the final exportable scene hierarchy
*

##
Material

To have an exportable scene from Maya, you are required to give the geometry under your cryExportNodes some materials. So, create a new
**
Material Group
**
 and one shader, and assign the shader to this Material Group. This shader should point to the diffuse texture you want to use for the grass blades. Use the
**
MAT.ED
**
 shelf icon from your installed Crytek shelf:

![Image](https://www.cryengine.com/docs/static/attachments/24157055)

*
Pic4: Setting a new Material Group and adding a shader to this material group
*

##
Export out the material

Your exported CRYENGINE material file should be located here:

-
`
<
`
*
Your_Project
*
>\Assets\
`
Objects\tutorial\vegetation\02\grass\merged_mesh\
**
**
tutorial_merged_meshMAT
**
.mtl
**
>
`
![Image](https://www.cryengine.com/docs/static/attachments/24157056)

*
*
Pic5: Generate a standard material for export. This will be finalized inside CRYENGINE material editor later
*
*

##
Geometry

Our geometry for this tutorial is going to be two patches of grass blades. Keep in mind that we will place several hundred thousand instances of those two assets throughout our scene so keep your triangle count as low as possible.

Note how the examples below only contain either 4 or 5 polygons. This is enough mesh detail to work with this system.

##
Create the Meshes

Create a single plane mesh for your first grass patch, divide up the shape into a similar polygon configuration and apply the material we just created to it (tutorial_merged_mesh_SUB). With the grass blade geometry selected, open the Maya's
**
UV Editor
**
 to adjust its UV shell to only fit around one of the grass patches on the texture. Create a copy of your mesh and move its UV shell to a different grass patch

Adapt the shape of both meshes to their applied textures. Finally name your two grass objects as:

-
tutorial_merged_mesh_a

-
tutorial_merged_mesh_b
![Image](https://www.cryengine.com/docs/static/attachments/24157057)

*
Pic6: grass blade geometry with their UVs tweaked to match the grass texture
*

##
Adding the Locators for the bending spline

As you have seen in the images before, we already have some locators created. For CRYENGINE's vegetation system to see it as Merged Mesh and being bendable by the environment wind system, we must create three
**
Locators
**
, which should be placed one at the bottom, one in the mid section and one at the top of the grass blade. Their names must follow this convention:

-
**
branch1_1
**
 - bottom locator

-
**
branch1_2
**
 - mid locator

-
**
branch1_3
**
 - top locator

The above names uses the same naming convention as the Touch Bending system, which will be shown in the next vegetation tutorial.
Note how we do not have to
**
snap
**
 the locators exactly onto a vertex like the touch bending setup. You can if you want, but it is not required by the merged mesh system.

##
Export the Geometry

As with all Maya to CRYENGINE exports, you must create a separate cryExportNode for each asset. Since we are using two variations of grass blades, we should create two cryExportNodes. Move the locators for the Merged Mesh vegetation under their respective parent geometry as shown here:

![Image](https://www.cryengine.com/docs/static/attachments/24157058)

*
Pic7: Export ready scene hierarchy
*

##
Continue to CRYENGINE

We have now finished the setup for the Maya portion of the tutorial. To continue, move to the next page where we configure the material and use the Vegetation Tool to place down some of these Merged Mesh assets.

[Vegetation 02 Grass (Merged Meshes) CRYENGINE](Vegetation%2002%20Grass%20(Merged%20Meshes)%20CRYENGINE.md)

[Tutorial Files](#tutorial-files)
[Pre-requisites for this Tutorial](#pre-requisites-for-this-tutorial)
[Helpful Information](#helpful-information)
[Initial Maya setup](#initial-maya-setup)
[Material](#material)
[Geometry](#geometry)
[Continue to CRYENGINE](#continue-to-cryengine)
