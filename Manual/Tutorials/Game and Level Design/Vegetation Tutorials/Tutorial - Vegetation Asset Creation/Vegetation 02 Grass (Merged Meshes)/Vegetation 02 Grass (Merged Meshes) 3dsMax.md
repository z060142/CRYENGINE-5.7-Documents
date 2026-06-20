# Vegetation 02 Grass (Merged Meshes) 3dsMax

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/24285890
- Page ID: 24285890
- Breadcrumb: Tutorials > Game and Level Design > Vegetation Tutorials > Tutorial - Vegetation Asset Creation > Vegetation 02 Grass (Merged Meshes) > Vegetation 02 Grass (Merged Meshes) 3dsMax
- Parent: Vegetation 02 Grass (Merged Meshes)

## Content

##
Overview

In this tutorial, we will be using our Merged Mesh system and show you the process of how to setup bendable grass blades. Merged Meshes are mainly used to handle areas with dense numbers of vegetation objects like big fields of grass. Merged Meshes also allow the usage of a rope based bending effect. Ropes get generated for each asset instance that bends upon impact.

Contrary to bone based setups like Touch Bending, ropes can be cheaper and get affected through the global wind and our Breeze Generation system. Large fields of grass are perfect examples to showcase this type of technology since each asset instance can be merged into bigger clusters through the merged mesh system. So for this tutorial, we will create two simple grass plane assets as a base for a dense overgrown grass field.

*
[Image: /docs/static/attachments/24157040]

Pic1: Dense grass field affected through wind
*

*
[Image: /docs/static/attachments/24157041]

Pic2: 2 assets that this entire grass field contains
*

##
Tutorial Files

Source 3dsMax scene with exported CRYENGINE files:

**
[/docs/static/attachments/25523835](
GameSDK_vegtut02_files.zip
)
**

##
Pre-requisites for this Tutorial

Before you continue with this tutorial, make sure to have read and understood the following topics;

-
[/docs/static/engines/cryengine-5/categories/23756816/pages/44963469](
How to Install CryMaxTools
)

-
[/docs/static/engines/cryengine-5/categories/23756816/pages/25528753](
The Basic CRYENGINE 3dsMax Workflow
)

-
[/docs/static/engines/cryengine-5/categories/23756816/pages/13205563](
CRYENGINE Exporter
)

-
[/docs/static/engines/cryengine-5/categories/23756816/pages/23308289](
3dsMax Unit Scale to Match up With CRYENGINE Unit System
)

##
Helpful Information

Make sure to keep the following things in mind while you work on your asset:

-
Align your dummies to your geometry surface; snapping to individual vertices is not necessary.

-
Dummies need to follow the naming convention rules for Merged Meshes to recognize them.

-
Do not scale or reset XForm your dummies.

-
It's useful to keep the amount of different materials for merged meshes as low as possible, to keep the memory usage low for console systems. Use one large texture sheet containing multiple variations.

-
Keep your geometry simple and planar.

-
Collision proxies are not needed so do not create any custom ones.

-
The grass blades should be as low-poly as possible for consoles, to guarantee that they don't have to stream in and merge large amounts of mesh data. You can also disable vertex colors for these, while exporting to decrease the size further.

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
**
Instance merging to clusters
**
**
 |
Yes
 |
No
 |

**
**
Influenced by Wind
**
**
 |
Yes
 |
No
 |

**
**
Influenced by Breeze gen
**
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
**
Bone parenting support
**
**
 |
No
 |
Yes
 |

**
**
Proxy support
**
**
 |
No
 |
Yes
 |

**
**
**
UV instancing for bones
**
**
**
 |
No
 |
Yes
 |

##
Initial 3dsMax setup

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
So to begin with, save your max scene to this location. All our exported assets will be saved in there. Some of the textures which we use will come from an already existing asset and we will point you to the directory where they are later in this tutorial.

We will continue with the assumption that you have already created the asset, since this is not a 3dsMax modeling tutorial. We will begin with preparing the asset ready for CRYENGINE, assigning SubIds to the relevant polygons and configuring the material.

*
[Image: /docs/static/attachments/24157042]

*
Pic3: 3dsMax overview of the finished model
*
*

##
Material

First, we will configure the material for the object. In 3dsMax, open the
**
Material Editor,
**
 and create a new
**
Multi-SubObject
**
 material with one
**
SubId
**
 called
**
tutorial_merged_mesh
**

Even though, we are using one material SubID, it is better if you follow the standard convention with all our other asset setups, of using a Multi-SubObject material.

Load in your diffuse map which
 should contain an alpha channel for the opacity.

The example file refers to the following provided tutorial texture:

-
`
`
<
`
*
Your_Project
*
>\Assets\
`
objects\tutorial\vegetation\02\grass\merged_mesh\
**
tutorial_merged_mesh_diff.tif
**
`
>
`
*
*

*
*
[Image: /docs/static/attachments/24157052]

*
Pic3a: Shader parameters setup
*

In the SubID for the material:

-
Select the
**
Crytek Shader
**
.

-
In the
**
Physicalization
**
 section,
**
do not
**
 check the
**
Physicalize
**
 check-box.

-
In the next drop-down box select
**
Default
**
.

-
Set
**
Alpha Test
**
 to 40.

##
Export out the material

Now, we have configured the material for the object with its standard properties.

-
Make sure you have the correct material selected in the material editor.

-
And you are at the root level of the material (not inside the SubID).

-
In the
**
CRYENGINE exporter
**
, click the
**
Create Material
**
 button. Save this into the same directory as the object:

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
tutorial_merged_mesh
**
.mtl
**
>
`
*
*
[Image: /docs/static/attachments/24157053]

Pic4: Select the material to export and make sure you are at the top level, not inside a SubID
*
*

##
Geometry

Our geometry for this tutorial is going to be two patches of grass blades. Keep in mind that we will place several hundred thousand instances of those two assets throughout our scene so keep your triangle count as low as possible.

Note how the examples below only contain either 4 or 5 polygons. This is enough mesh detail to work with this system.

##
Create the Meshes

Create a single plane mesh for your first grass patch, divide up the shape into a similar polygon configuration (and assign ID1), and apply the material that we have just created to it (tutorial_merged_mesh.mtl). Use the
**
Unwrap UVW
**
 modifier to adjust its UV shell to only fit around one of the grass patches on the texture. Create a copy of your mesh and move its UV shell to a different grass patch through another
**
Unwrap UVW
**
 modifier (See
*
Pic5
*
 and
*
Pic6)
*
.

Adapt the shape of both meshes to their applied textures. Finally name your 2 grass objects as:

-
tutorial_merged_mesh_a

-
tutorial_merged_mesh_b
*
*
[Image: /docs/static/attachments/24157046]

Pic5: Geometry of the grass patches
*
*

*
*
*
[Image: /docs/static/attachments/24157047]

Pic6: UV Layout of both grass meshes in 3dsMax. Note the grass UVs are matching the underlying texture
*
*
*

##
Adding the Helper Dummies

Next let us add the dummies so that our grass can bend in the wind. Dummies are necessary for us to define a start, mid and end point of our rope chain. Create three dummies for both assets. Align them to the surface and place them roughly at the bottom, in the middle and the end of your grass geometry.

Using the same naming convention as the Touch Bending system, name the dummies as follows;

-
**
branch1_1
**
 - bottom dummy

-
**
branch1_2
**
 - mid dummy

-
**
branch1_3
**
 - top dummy

Note how we do not have to
**
snap
**
 the dummies exactly onto a vertex like the touch bending setup. You can if you want, but it is not required by the Merged Mesh system.

*
[Image: /docs/static/attachments/24157048]

Pic7: Geometry of the grass patches with aligned dummies
*

Next, open up the Schematic view and link both sets of dummies to their corresponding geometry. Make sure the correct branch chain is connected to the right geometry, since we are dealing with two assets at once here.

*
*
[Image: /docs/static/attachments/24157049]

Pic8: Schematic view of the assets hierarchy
*
*

##
Export the Geometry

We are now ready to export our geometry to the engine. In the
**
CRYENGINE exporter
**
:

-
Add the root node of the asset to the export list. In this case it is called
*
tutorial_merged_mesh (a & b)
*
.

-
Select
**
Geometry (*.cgf)
**
 from the
**
Export
**
 format drop down list.

-
Press the
**
Export Nodes
**
 button.
*
[Image: /docs/static/attachments/24157050]

Pic9: Adding the asset to the exporter
*

*
*
[Image: /docs/static/attachments/24157051]

Pic10: Successful export
*
*

##
Continue to CRYENGINE

We have now finished the setup for the 3dsMax portion of the tutorial. To continue, move to the next page where we configure the material and use the
**
Vegetation
**
 Tool to place down some of these Merged Mesh assets.

[/docs/static/engines/cryengine-5/categories/23756816/pages/24285892](
Vegetation 02 Grass (Merged Meshes) CRYENGINE
)

[#tutorial-files](
Tutorial Files
)
[#pre-requisites-for-this-tutorial](
Pre-requisites for this Tutorial
)
[#helpful-information](
Helpful Information
)
[#initial-3dsmax-setup](
Initial 3dsMax setup
)
[#material](
Material
)
[#geometry](
Geometry
)
[#continue-to-cryengine](
Continue to CRYENGINE
)
