# LODs

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/26215356
- Page ID: 26215356
- Breadcrumb: Asset Prep (External) > Asset Exporting Overview > Geometry Creation Overview > LODs
- Parent: Geometry Creation Overview

## Content

![Image](https://www.cryengine.com/docs/static/attachments/29934004)

##
Overview

##
Sections

Level of Detail objects are used to improve the rendering performance of objects located far away from the camera picture plane.

![Image](https://www.cryengine.com/docs/static/attachments/35400699)

[Sections](#sections)
[General Guidelines](#general-guidelines)
[3DS Max Specific Setup](#3ds-max-specific-setup)
[Maya Specific Setup](#maya-specific-setup)
[Setup in Sandbox](#setup-in-sandbox)

##
General Guidelines

-
The Base mesh (LOD 0) has no prefix/suffix. Every successive LOD should be a separate object that is linked/parented to the base mesh and named
$lod1
,
$lod2
, etc.

-
For clarity, you can also add more information the name of the LOD node, i.e.
_lod1_sphere
 or
_lod2_justforfun
. The engine only takes the first 5 characters into account.

-
Reduce the amount of material IDs as much as possible, as this will decrease the amount of drawcalls your LOD produces. Ideally, the last LOD should only have one render material ID assigned. The
r_Stats 6
 CVar will allow you to view how many Drawcalls your objects are producing.

-
Each successive LOD step should save 50% of triangles. (i.e. 1200 -> 600 -> 300 triangles) or have the amount of rendering materials reduced. A warning message will be displayed during export if the triangle reduction is above 66%.

-
Currently up to 6 LOD's are supported. This number is hard-coded and may change in the future. The
 e_LodMin/Max
 CVars will allow control over which LODs are used on a global scale.

-
Objects can have LOD's for every sub node. LOD's must be linked/parented to the nodes they should substitute during rendering.

##
3DS Max Specific Setup

-
Create reduced versions of the object with the exact same pivot position and translation/scale values.

-
Name them
$lod1
,
$lod2
,

$lod3
 in 3ds Max.

-
Link/parent each LOD to the parent render mesh.

-
Export the base mesh with the CRYENGINE Exporter. The exporter will recognize the linked LOD's and will include them in the .cgf.
Example for linked LOD's:

![Image](https://www.cryengine.com/docs/static/attachments/35400700)

Additionally, you can make the LOD names more specific by adding a space/underscore and a descriptive name after the "$lod1"; i.e. "$lod1 box", "lod2 box".

Naming them specifically can help locating problematic assets which may be highlighted by the
[Resource Compiler](../../../System%20Utilities/System%20Utilities%20Overview/Resource%20Compiler.md)
 during the build process. So long as the node begins with $lod<number>, the rest of the name shouldn't matter.

In the Schematic View mode of 3ds Max it will look like:

![Image](https://www.cryengine.com/docs/static/attachments/35400701)

LOD's can also be created for and linked to sub-objects of complex assets, i.e. breakable objects, cars, tanks.

The engine will automatically detect the correct LOD step for the sub-objects based on distance/size/triangle count of the object.

Example of LOD's for sub-objects:

![Image](https://www.cryengine.com/docs/static/attachments/35400702)

##
Export

When linked correctly, the LOD's do not need to be added to the list window of the exporter.

"Merge all Nodes" needs to be
unchecked
 in the exporter settings.

When you export your .cgf from Max, the LOD's are embedded inside the .cgf. The engine is able to then pull these LOD's from the one .cgf at run time, but for a final released build, the Resource Compiler should be setup to extract the LODs from the base .cgf (with the /splitlods command) and create separate LOD .cgf's from them. If you look inside the shipped GameSDK .pak files, you'll see _lod1.cgf, _lod2.cgf assets alongside their parent .cgf.

##
Old LOD Setup in 3D Packages

Kept for backwards compatibility - You can also create a separate .cgf object with the same object name plus the post fix
_lod1
,
_lod2
, etc.

The engine will automatically use these external LOD's. But this method is not recommended and might be removed in future releases.

Examples:

-
ball.cgf

-
ball_LOD1.cgf

-
ball_LOD2.cgf

##
Maya Specific Setup

1. Create a group called 'cryexportnode_@' replacing the '@' with the filename to export to.

![Image](https://www.cryengine.com/docs/static/attachments/35400703)

2. Group the highest detail mesh (lod0) under a new group named '#_group' replacing the '#' with the name of the model you are exporting.

3. Group the '#_group' for LOD0 under the 'cryexportnode'.

![Image](https://www.cryengine.com/docs/static/attachments/35400704)

4. For each additional LOD level create a group using the naming convention in step 5.

5. Make sure the LODs are using the following naming convention '
*
lod#
*
@_group' replacing the '@' with the mesh name of your choice, replace the # with the lod ID. Ensure the same for all the LOD levels eg _lod1_mayalod_group, _lod2_mayalod_group.

6. Group the geometry for each LOD under the nodes we created in step 4.

![Image](https://www.cryengine.com/docs/static/attachments/35400705)

7. Select the 'cryexportnode' group.

8. Click the export button on the 'Crytek' toolbar to open the 'Crytek Export' dialog.

9. Click the 'Add Attributes' button.

10. Ensure that 'Do Not Merge Nodes' is ticked.

11. Click the 'Export' button on the 'Crytek Export' dialog.

![Image](https://www.cryengine.com/docs/static/attachments/35400706)

An example Maya scene for setting up LODing geometry can be downloaded
[here](https://docs.cryengine.com/download/attachments/1310765/lodtest.mb?version=1&modificationDate=1259664377000&api=v2)
.

##
Setup in Sandbox

There is no special setup needed. The engine will automatically detect LOD's and use them if available.

##
Debugging LOD's

There are various console commands which help debugging LOD's in Sandbox of in game mode.

**
e_Lods
**

```

Load and use LOD models for static geometry

```

**
e_LodMin
**

```

Min LOD for objects

```

**
e_LodMax
**

```

Max LOD for objects

```

**
e_DebugDraw
**

```

Draw helpers with information for each object (same number negative hides the text)
 1: Name of the used cgf, polycount, used LOD
 2: Color coded polygon count
 3: Show color coded LODs count, flashing color indicates no Lod
 4: Display object texture memory usage
 5: Display color coded number of render materials
 6: Display ambient color
 7: Display tri count, number of render materials, texture memory
 8: RenderWorld statistics (with view cones)
 9: RenderWorld statistics (with view cones without lights)
10: Render geometry with simple lines and triangles
11: Render occlusion geometry additionally
12: Render occlusion geometry without render geometry
13: Display occlusion amount (used during AO computations). Warning: can take a long time to calculate, depending on level size!
15: Display helpers
16: Display debug gun
17: Streaming info (buffer sizes)
18: Streaming info (required streaming speed)
19: Physics proxy triangle count
20: Display object instant texture memory usage
21: Display animated object distance to camera
22: Display object's current LOD vertex count

```
