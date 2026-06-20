# Vegetation 06 Trees (Deform) 3dsMax

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/24285906
- Page ID: 24285906
- Breadcrumb: Tutorials > Game and Level Design > Vegetation Tutorials > Tutorial - Vegetation Asset Creation > Vegetation 06 Trees (Deform) > Vegetation 06 Trees (Deform) 3dsMax
- Parent: Vegetation 06 Trees (Deform)

## Content

##
Overview

In this tutorial, we will show you the process of how to setup physical interactions between the hanging leaves on a willow tree asset and any other physicalized object in the level (such as the player). To achieve this, we will be using our Merged Mesh Deform system and show you how to set it up in CRYENGINE.

Merged Mesh Deform Cloth is an improved and optimized system over the cloth entity. Through this system, it is possible to set up assets with cloth behavior as static brushes and vegetation objects. Contrary to cloth entities assets, the Merged Mesh Deform Cloth can have solid geometry and deformable cloth geometry stored within them at the same time.

This method works great for hanging vegetation like swamp moss or willow tree leaves.

*
[Image: /docs/static/attachments/25495412]

*
Pic1: Merged Mesh Deform in action (with activated wind)
*
*

##
Tutorial Files

Source 3dsMax scene with exported CRYENGINE files:

**
[/docs/static/attachments/25523843](
GameSDK_vegtut06_files.zip
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
Your cloth nodes need to be linked to a mesh acting as the main object.  Dummies and helpers do not work as main object.

-
The cloth nodes need to follow a naming convention:
**
bendable
**
,
**
bendable00
**
,
**
bendable01,
**
 etc.

-
The vertex color channel is used change the cloths stiffness and to fix your vertices on a location.

-
Keep the cloths wireframe irregular instead of planar to avoid quick settlement.

-
User Defined Properties need to be set up for the engine to recognize the mesh as cloth.

-
The SPU will calculate the nodes simultaneously in multiple threads. Up to ten nodes per object can be used to stay SPU friendly.

-
Do not use too many different material IDs for the cloth nodes of your object. The cloth nodes get merged into one large single object in the engine whereas every material ID gets its own merged object. Therefore try to have as less single cloth objects as possible in the engine.

-
At least one black vertex has to be defined, to avoid that the cloth falls down.

##
Initial 3dsMax setup

For this tutorial, we will be creating our asset in the following directory.

-
`
<YOUR_PROJECT_FOLDER>\Assets\Objects\tutorial\vegetation\06\tree\merged_mesh_deform\
`
So to being with, save your 3dsMax scene to this location. All our exported assets will be saved in there. Some of the textures which we will use are derived from an already existing asset and we will point you to the directory later in the tutorial.

We will continue with the assumption that you have already created the asset, since this isn't a 3dsMax modelling tutorial. We will begin with preparing the asset ready for CRYENGINE, assigning SubIds to the relevant polygons and configuring the material.

*
[Image: /docs/static/attachments/25495411]

*
Pic2: 3dsMax overview of the finished model
*
*

##
Material

First, we will configure the material for the object. In 3dsMax, open the
**
Material Editor
**
 and create a new multi-material called
**
tutorial_merged_mesh_deform
**
**

**
with three sub-materials.

Name the first SubId as
**
trunk
**
, the second one as
**
leaves
**
 and the third one as
**
proxy
**
. See
*
Pic2
*
 and note the
multi-material
setup in the 3dsMax's
**
Material Editor
**
.

##
Trunk Id Setup

Open the trunk sub-material (SubId1).
Load in your diffuse map and normal map to the material paths.
 The normal map should also contain an alpha map for the PBS smoothness value.

The example file refers to the following provided tutorial textures:

-
`
<YOUR_PROJECT_FOLDER>\Assets\
Objects\tutorial\vegetation\06\tree\merged_mesh_deform\tutorial_merged_mesh_deform_trunk_diff.tif>
`

-
`
<YOUR_PROJECT_FOLDER>\Assets\
Objects\tutorial\vegetation\06\tree\merged_mesh_deform\tutorial_
merged_mesh_deform_trunk_ddna.tif
>
`
*
*
[Image: /docs/static/attachments/25495413]

Pic3: Trunk SubId1 shader parameters setup
*
*

In the
**
Shader Basic Parameters
**
 window:

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
 section, do not check the
**
Physicalize
**
 check-box, and in the next drop-down menu select
**
Default.
**

##
Leaves Id Setup

Open the leaves sub-material (SubId2).
Load in your diffuse map and normal map to the material paths.
The diffuse map should contain an alpha map for the opacity. The normal map should also contain an alpha map for the PBS smoothness value.

The example file refers to the following provided tutorial textures:

-
<YOUR_PROJECT_FOLDER>\Assets\
Objects\tutorial\vegetation\06\tree\merged_mesh_deform\tutorial_merged_mesh_deform_leaves_diff.tif>

-
<YOUR_PROJECT_FOLDER>\Assets\
Objects\tutorial\vegetation\06\tree\merged_mesh_deform\
tutorial_merged_mesh_deform_leaves_ddna.tif
>
*
*
[Image: /docs/static/attachments/25495414]

Pic4: Leaves SubId2 shader parameters setup
*
*

In the
**
Shader Basic Parameters
**
 window:

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
 section, do not check the
**
Physicalize
**
 check-box.

-
In the next drop-down menu select the
**
Default
**
 option.

-
Set
**
Alpha Test
**
 to 25.

##
Proxy Id Setup

Open the proxy sub-material (SubId3). This material will be used for the proxy volume and defines the properties for this object. The Physical Proxy (NoDraw) and the Physicalize parameter allow the object to have an invisible collision mesh.

*
*
[Image: /docs/static/attachments/25495415]

*
Pic5: Proxy SubId3 shader parameters setup
*
*
*

In the
**
Shader Basic Parameters
**
 window:

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
 section, check the
**
Physicalize
**
 check-box.

-
In the next drop-down menu, select the
**
Physical Proxy (NoDraw)
**
 option.
In the
**
Crytek Shader Basic Parameters
**
 section, set the diffuse color to red and reduce the opacity to 15 - 30%. Even though it is not mandatory, but helps the user identify quickly the proxy geometry within the asset.

Export out the material

Now, we have configured the material for the object with three SubIds, the visible materials (leaves and trunk) and the physicalized collision material (proxy).

-
Make sure you have the correct material selected in the material editor.

-
In the
**
CRYENGINE Exporter
**
, click the
**
Create Material
**
 button. Save this into the same directory as the object:
`
<
`
*
Your_Project
*
>\Assets\
`
Objects\tutorial\vegetation\06\tree\merged_mesh_deform\
**
tutorial_merged_mesh_deform.mtl
**
>
`

*
*
[Image: /docs/static/attachments/25495424]

Pic6: Selecting the correct material for the texture export
*
*

##
Geometry

Our geometry for this tutorial is going to be a willow tree. With its hanging leaves this type of tree is perfect for showcasing cloth physics on an otherwise static object. For this feature to work, the deformable leaf patches need to to be their own objects linked to a static main geometry object acting as the root.

To begin with, we need to set up the trunk as the root object for our hierarchy setup.
A
pply the material
*
(tutorial_merged_mesh_deform.mtl)
*
that we just created
to it
 and make sure that its SubId is set to 1. Use the
**
Unwrap UVW modifier
**
 to unfold its UV shell. Name the object
*
tutorial_merged_mesh_deform
*
. Create a proxy for the trunk, apply the same material to it, set its SubId to 3 (proxy) and name it
*
proxy
*
.

*
*

[Image: /docs/static/attachments/26512564]

Pic6: Geometry of the trunk and its proxy

*
*

Set up a plane for the leaves
and
 apply the recently created material. C
hange the material SubId to 2 (leaves).
Finally u
se the
**
Unwrap UVW modifier
**
 to adjust the UV shell to only fit around one of the leaf patches on the texture. For some variation, copy your leaf geometry two more times and adjust each UV shell to another leaf patch.

*
*
[Image: /docs/static/attachments/25495422]

Pic7: Geometry of all three tree leaf patches
*
*

*
*
[Image: /docs/static/attachments/25495436]

Pic8: UV Layout of the leaves in 3dsMax. Note the leaf UVs matching the underlying texture
*
*

##
Applying Vertex Color

Before we continue creating the rest of the tree by duplicating the leaves, we will paint vertex color on our assets. This should be done now to avoid repeating the same process over and over again for each duplicate. You can also paint them at the end once the tree crown geometry is complete. It doesn't matter in which order you do this, we are doing it now because there are less objects on screen. Green color allows vertices to move freely upon impact whereas black color fixates vertices to their location. Shades of green define the intensity of their stiffness. Paint all three leave patches green and overpaint their top row vertices with black to fixate them in the air.

*
*
*
[Image: /docs/static/attachments/25495419]

Pic9: Adding vertex color via the vertex paint modifier to the geometry
*
*
*

**
Note:
**
 You can also use white instead of green. We use green so that the blue and red channel are free for other usages.

##
Naming convention

The name of your root object will define the name of your asset. Therefore the name
*
tutorial_merged_mesh_deform
*
.

Bendable objects need to go with the following naming convention:
*
 bendable00, bendable01, bendable02,
*
 etc.

##
Available User Defined Properties

In order to activate the Cloth Merged Mesh Deform system for the engine, go into the UDPs for each leaf patch and type in "mergedmesh_deform".

*
[Image: /docs/static/attachments/25495417]

Pic10: UDP dialog with mergedmesh_deform to enable the system
*

There are several other available parameters that define the whole geometry to behave in a certain way
*
:
*

UDP

 |
Description

 |

**
mergedmesh_deform
**

 |
Needed to enable mergedmesh deform cloth physics for this node.

 |

**
mergedmesh_deform_stiffness
**

 |
Defines how stiff the deformable is, between 0.0 and 1.0.

 |

**
mergedmesh_deform_damping
**

 |
Controls how quickly the deformable will settle, between 0.0 and infinity.

 |

**
mergedmesh_deform_variance
**

 |
Controls how much randomness is in the wind sampling algorithm, between 0.0 and infinity.

 |

**
mergedmesh_deform_air_resistance
**

 |
Scales the wind influence, multiplied with the levels wind force.

 |

**
mergedmesh_deform_air_frequency
**

 |
Cosines modulated speed of wind per vertex, between 0.0 and infinity.

 |

**
mergedmesh_deform_air_modulation
**

 |
Cosines modulated speed of wind per wind-force, between 0.0 and infinity.

 |

**
mergedmesh_deform_max_iter
**

 |
Amount of simulation iterations, between 1 and 12, 3 is default, the higher the more expensive.

 |

Type in the following values to get a proper behavior for your leaf patches.

*
[Image: /docs/static/attachments/25495418]

Pic11: UDP dialog with several values
*

##
Duplicate the leaves

For the next step, the leaves need to be scattered around the tree trunks branches. Afterwards you should start to merge some of the cloth patches together until there are ten or less leaf objects left. This will avoid big performance impacts on the SPU. Make sure to keep their naming convention correct.

*
[Image: /docs/static/attachments/25495423]

Pic12: Merged leaf patches together with trunk
*

##
Hierarchy setup

Now it is time to link all the objects to the trunk. Select
*

*
the
*
 proxy
*
 and
*
bendable00
*
,
*
bendable01
*
,
*
bendable02
*
 etc. and link them to
*
tutorial_merged_mesh_deform
*
.

*
[Image: /docs/static/attachments/25495421]

*
Pic13: Hierarchy shown in schematic view
*
*

##
Export the Geometry

We are now ready to export our geometry to the engine. In the CRYENGINE exporter:

-
Add the root node of the asset to the export list (in this case it's called
*
tutorial_merged_mesh_deform
*
)

-
Select
**
Geometry (*.cgf)
**
 from the
**
Export format
**
 drop down list.

-
Press the
**
Export Nodes
**
 button.
[Image: /docs/static/attachments/25495420]

*
Pic14: Adding the asset to the exporter
*

##
Continue to CRYENGINE

We have now finished the setup for the 3dsMax portion of the tutorial. To continue move to the next page where we configure the material and use the Vegetation Editor to place down some of these Touch Bending assets.

-
**
[/docs/static/engines/cryengine-5/categories/23756816/pages/24285908](
Vegetation 06 Trees (Deform) CRYENGINE
)
**

[#tutorial-files](
Tutorial Files
)
[#pre-requisites-for-this-tutorial](
Pre-requisites for this Tutorial
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
