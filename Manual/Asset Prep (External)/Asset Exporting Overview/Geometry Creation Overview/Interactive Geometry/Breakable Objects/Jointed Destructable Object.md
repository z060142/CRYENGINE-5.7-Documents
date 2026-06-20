# Jointed Destructable Object

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/23308028
- Page ID: 23308028
- Breadcrumb: Asset Prep (External) > Asset Exporting Overview > Geometry Creation Overview > Interactive Geometry > Breakable Objects > Jointed Destructable Object
- Parent: Breakable Objects

## Content

##
Overview

Jointed Destructible Objects can be set up to break in to smaller pieces when being detached from the joint. For example a wooden sign falls off of the signpost
**
and
**
 breaks into several planks. The object properties must contain the information about the pieces used. The pieces need to be linked to the object that was formerly whole. The pieces must also be referenced in the Object properties/UDP of this object.

Before reading this topic, make sure you have gone through the documentation for creating
[/docs/static/engines/cryengine-5/categories/23756816](
Jointed Breakable Objects
)
.

##
Setup in 3ds Max

##
Sample 3ds Max file

-
[/docs/static/attachments/23994741](
jointedDestructable.rar
)

##
Basic setup and Naming

Beneath, is a simple scene with a sign post. The objects in blue are the pieces that will spawn when the red sign is hit with a force. Make sure that these also have their own phys proxies as well. As you may have read in the Breakable Objects documentation, the joints hold the sign in place until hit and the connection will break.

[Image: /docs/static/attachments/23994719]

##
Hierarchy

The pieces that spawn when the object is hit must be children of the original object, in this case the red sign. Everything else is a child of the export node (breakable_sign).

[Image: /docs/static/attachments/23994717]

##
Object Properties

You must specify the pieces that the red sign will spawn in the object properties like in the picture below. Also remember to assign properties to the individual pieces.

[Image: /docs/static/attachments/23994718]

Once this is all setup, export to a .cgf and check it in the engine

A full list of property strings can be found
.

##
Setup in Maya

##
Sample File

-
[/docs/static/attachments/23994722](
dissolve_breakable_maya.ma
)

##
Hierarchical Setup

The cryexportnode_filename is the top node that contains the export properties for the object. Select the cryexportnode, open up the exporter then click "Add Attributes". A new tab in the export window will appear. Choose the .cgf format for this asset.

[Image: /docs/static/attachments/23994744]

All the objects that you want to export have to be a child of this node. Below you can see the hierarchy of how the jointed parts of the sign have been setup:

[Image: /docs/static/attachments/23994724]

Joints are named _joint$$ ($$ is replaced with the joint number). To add the pieces that the specific jointed part will break into when disjointed, make them children of the jointed part. See the picture below for more clarity:

[Image: /docs/static/attachments/23994725]

Notice how the _piece01_group and _piece02_group are children of the sign_group. The naming convention has to be _piece$$_group ($$ is replaced with the piece number). So, the sign will break into these pieces after it's disjointed.

Here is a screenshot that shows how the pieces look:

[Image: /docs/static/attachments/23994726]

##
Custom Attributes

Each group node should have Extra Attributes. You can do this by selecting a group and in the Crytek tab, click UDP (User Defined Properties).

[Image: /docs/static/attachments/23994742]

Most of the group nodes should have a Mass/Density attribute except the groupnode filename_helper (in this example it's named signBreak_helper). If you want the pieces to remain after falling apart, make sure to type in 'entity'.

A full list of property strings can be found
.

For the object that dissolves into further pieces, you need to add a custom string attribute to its group node. In our example, select sign_group and click "Add Attributes". Choose a String data type with Long Name "pieces".

[Image: /docs/static/attachments/23994730]

Here you can specify the pieces that the
**
*
sign
*
**
 mesh object will break into:
**
pieces=_piece01_group, _piece02_group
**

Each _piece$$_group should have a mass. Also, each breakable joint should have limit.

Once done, you can export the cgf file and test it in game.

##
Setup in XSI

##
Sample XSI File

-
[/docs/static/attachments/23994720](
BreakableTable.scn
)

##
Hierarchical Setup

The CryExportNode is the top node that contains the export properties for the object.

[Image: /docs/static/attachments/23994731]

All the objects that you want to export have to be a children of this node.

Below you can see the hierarchy of how the jointed parts of the table have been setup:

[Image: /docs/static/attachments/23994732]

The naming convention is the same for creating the joints. To add the pieces that the specific jointed part will break into when disjointed, make them children of the jointed part. See the picture below for more clarity:

[Image: /docs/static/attachments/23994733]

Notice, the
**
*
Table_top
*
**
 mesh object has multiple mesh objects as its children. These are the pieces that the
**
*
Table_top
*
**
 mesh object will break into after it's disjointed.

Here is a screenshot that shows how the pieces look:

[Image: /docs/static/attachments/23994734]

##
Custom Properties

You need to add a Node User Properties to the
**
*
Table_top
*
**
 mesh object.

[Image: /docs/static/attachments/23994735]

Here you can specify the pieces that the
**
*
Table_top
*
**
 mesh object will break into:
**
pieces=_piece1,_piece2,_piece3,_piece4,_piece5,_piece6,_piece7,_piece8,_piece9,_piece10,_piece11,_piece12
**

For each piece, add a Node User Properties by selecting the mesh and going to
**
*
Crytek > Node User Properties
*
**
.

You can assign a mass to each piece.

[Image: /docs/static/attachments/23994736]

Each of these pieces need to have their own proxy mesh.

A full list of property strings can be found
.

##
Setup in Sandbox

Now, you can place the object in Sandbox as a breakable object and observe how the table breaks.

Start by placing a BreakableObject in your level from the
**
RollupBar > Entity > Physics
**
 directory.

[Image: /docs/static/attachments/23994737]

Then, with the BreakableObject selected, change the
**
Model
**
 from the Entity Properties.

[Image: /docs/static/attachments/23994738]

Now set up the table's textures in the Material Editor

[Image: /docs/static/attachments/23994739]

Finally, test the table by shooting in game mode.

[Image: /docs/static/attachments/23994740]

[#setup-in-3ds-max](
Setup in 3ds Max
)
[#setup-in-maya](
Setup in Maya
)
[#setup-in-xsi](
Setup in XSI
)
