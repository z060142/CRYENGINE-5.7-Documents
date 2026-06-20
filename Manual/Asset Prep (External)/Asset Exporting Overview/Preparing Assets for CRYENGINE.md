# Preparing Assets for CRYENGINE

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/23308291
- Page ID: 23308291
- Breadcrumb: Asset Prep (External) > Asset Exporting Overview > Preparing Assets for CRYENGINE
- Parent: Asset Exporting Overview

## Child Pages

- [Basic Asset Setup and Export - 3ds Max](Preparing Assets for CRYENGINE/Basic Asset Setup and Export - 3ds Max.md)
- [Basic Asset Setup and Export - Maya](Preparing Assets for CRYENGINE/Basic Asset Setup and Export - Maya.md)
- [Export Assets - FBX Importer](Preparing Assets for CRYENGINE/Export Assets - FBX Importer.md)

## Content

##
Overview

Basic (or static) geometry are used as various objects in the environment that do not have any special properties assigned to them. For example, a rock would be considered static geometry because generally speaking it would not have any breakable proxies or rigs attached to it.

##
General Setup in DCC Tools

**
3ds Max
**

**
[/docs/static/engines/cryengine-5/categories/23756816/pages/25528753](
This tutorial
)

**
assumes that users understand the basics of 3ds Max, such as the user interface and the creation of simple geometry, and can place objects in the Sandbox Editor. From there it will discuss how to prepare your assets from within 3ds Max in order to get them into the Sandbox Editor as well.

**
Maya
**

**
[/docs/static/engines/cryengine-5/categories/23756816/pages/23308292](
This tutorial
)
**
 assumes that users understand the basics of Maya, such as the user interface and the creation of simple geometry, and can place objects in the Sandbox Editor. From there it will discuss how to prepare your assets from within Maya in order to get them into the Sandbox Editor as well.

**
FBX
**

**
[/docs/static/engines/cryengine-5/categories/23756816/pages/25529353](
This page
)
**
 shows you how to import your asset via the FBX Importer tool. It assumes you have followed the 3dsMax or Maya page to correctly configure your asset, and details how to import that asset into CRYENGINE via FBX, instead of using the tool specific exporters.

##
Viewing the Object in Sandbox

Start
**
Sandbox
**
 and load an existing level. Click the
**
Brush
**
 button in the
**
Create Object
**
 tool and locate the object.

Drag the object into the level.

[Image: /docs/static/attachments/25037457]

##
Fetching and Assigning Materials

You can view the object's material by opening the
**
Material Editor
**
 (
**
Tools -> Material Editor
**
).

Click the
**
Get Properties from Selection
**
 button in the toolbar of the Material Editor window. This gets the material of the selected object:

[Image: /docs/static/attachments/25037458]

You can assign any material to the object by selecting the material (always select the parent, not a sub-material) and clicking the leftmost button in the Material Editor toolbar (the
**
Assign material to selection
**
 button).

Assigning random materials to objects that are not specifically set up for the object can throw up some issues.  These issues can arise when the Materials SubID structure is different from the asset you are trying to assign it to.
Example problems;

-
Assigning a single SubID material to an object with multiple SubIDs will assign the first ID to every surface, because it doesn't have the info for the other IDs.

-
The Physics Proxy ID could be assigned to a different ID than what is specified in the object.

-
Different UV layouts.
The best practice for assigning or overriding the default material on an object is to make variations on the theme when creating the asset.

Example use cases for material variations:

-
The base asset is a rock with a dry looking material.

-
Make another material specific to that object with a wet variation.

-
Or another with moss growing on the sides.

-
etc.
Since you are creating the rock asset, make the variations at the same time. Since you know the structure and layout of the SubID assignment, their variations will all follow the same convention (ID1 = proxy ID2 = rock etc.) and be in the correct place when assigned.

##
Testing the Object

You can jump into the game by pressing
**
Ctrl+G
**
 when in the Perspective viewport, or from the
**
Game
**
 menu.

If you clicked the
**
Physicalize
**
 button in 3dsMax on the proxy SubID of the material (assuming that you created a proxy), any other characters/physicalized rigid bodies will collide with the object.

*
Reloading the *.cgf file in the properties panel
*

[Image: /docs/static/attachments/25501318]

You may find sometimes that the physicalized geometry does not get updated (if it was changed) after clicking
**
Reload
**
. You can get around this by deleting the object and using Undo (
**
Ctrl
**
**
+Z
**
 or the Undo button). The physicalized geometry is also automatically updated when the asset is loaded again.
**
p_draw_helpers
**

```

Same as p_draw_helpers_num, but encoded in letters
Usage [Entity_Types]_[Helper_Types] - [t|s|r|R|l|i|g|a|y|e]_[g|c|b|l|t(#)]
Entity Types:
t - show terrain
s - show static entities
r - show sleeping rigid bodies
R - show active rigid bodies
l - show living entities
i - show independent entities
g - show triggers
a - show areas
y - show rays in RayWorldIntersection
e - show explosion occlusion maps
Helper Types
g - show geometry
c - show contact points
b - show bounding boxes
l - show tetrahedra lattices for breakable objects
j - show structural joints (will force translucency on the main geometry)
t(#) - show bounding volume trees up to the level #
f(#) - only show geometries with this bit flag set (multiple f's stack)
Example: p_draw_helpers larRis_g - show geometry for static, sleeping, active, independent entities and areas

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

[#general-setup-in-dcc-tools](
General Setup in DCC Tools
)
[#viewing-the-object-in-sandbox](
Viewing the Object in Sandbox
)
[#fetching-and-assigning-materials](
Fetching and Assigning Materials
)
[#testing-the-object](
Testing the Object
)
