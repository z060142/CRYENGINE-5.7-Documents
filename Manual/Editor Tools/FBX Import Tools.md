# FBX Import Tools

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/44966294
- Page ID: 44966294
- Breadcrumb: Editor Tools > FBX Import Tools
- Parent: Editor Tools

## Content

##
Overview

The FBX  Importer loads
**

**
animations, skeletons skins and
static geometry meshes
. The currently supported input formats are
**
.fbx
**
,
**
.dxf
**
,
**
.dae
**
,
**
.obj
**
, and
**
.3ds
**
 (however,
**
.fbx
**
 is the preferred interchange format). In addition, the FBX Importer provides a graphical interface to change properties before they are imported to a CRYENGINE format.

The existing content pipeline, consisting of the 3ds Max and Maya exporters, still works. The FBX Importer, however, makes CRYENGINE more accessible to a greater variety of DCC tools, like Blender, so that artists can continue to use their favorite workflow.

The different importers can be found under
**
Tools → FBX Import
**
.

Importing the animation, skeleton, skin or static geometry is very easy; you can just open the respective tool and
**
drag & drop
**
 an
**
.fbx
**
 file from a folder in the Windows Explorer onto one of the tools.

Alternatively, you can also click
**
File → Import
**
 or use the
**
Import
**
 button in the toolbar.

Even easier than using the FBX Import tools is to simply drag & drop your assets into the Asset Browser, which is the recommended workflow.

For more information about importing assets through the Asset Browser, see
[here](Asset%20Browser.md)
.

##
Basic Workflow of All Tools

The FBX Importer tools are typically used as follows:

-
Open a source
**
.fbx
**
 (or other compatible) file. This can be done in one of three ways:

- Going to
**
File → Import
**

- Clicking the
**
 Import file
**
 button in the toolbar

- Dragging & dropping a compatible file from the Windows Explorer onto the viewport of the tool you want to use

-
Inspect the source scene and decide which meshes or nodes you want to export to the the output
**
.cgf
**
 file.

-
When you're satisfied, click on
**
File → Save as
**
 (or click the
**
Save as
**
 button in the toolbar) and save the file to the game folder.

-
You will then be able to place it in your level by opening the
**
Create Object
**
 tool and adding it in the way that you want, like for example a Brush or a Geom Entity, depending on what kind of asset you've made.
A
**
.cgf
**
 file must always be in the same folder as the
**
.fbx
**
 (or any compatible) file. The
**
.cgf
**
 references the
**
.fbx
**
 (or other compatible) file by name, not by path. The FBX Importer will automatically create a copy of the
**
.fbx
**
 file in the game folder, along with the output
**
.cgf
**
 file, when you click
**
Save as...
**

The
**
.cgf
**
 file essentially stores all the settings you make in the MI and also a reference to the
**
.fbx
**
 file.

Load a level for proper lighting.

To import an entire asset including skin, animations and skeleton, you'll need to drag it onto the viewport of the
[Character Tool](Animation%20Tab/Character%20Tool.md)
.

##
Animation

This will import the animations attached to the
**
.fbx
**
 file.

![Image](https://www.cryengine.com/docs/static/attachments/44967745)

##
1. Menu

The Menu can be accessed via the
![Image](https://www.cryengine.com/docs/static/attachments/44967749)
 icon on the top-right corner of the tool. When clicked, it reveals the following
**

**
sub-menus:

##
File

Option
 |
Description
 |

**
Open...
**
 |
Restores the FBX Importer dialog. This means the source
**
.fbx
**
 file is imported and the settings stored in the
**
.cgf
**
 file are applied. Works only with
**
.cgf
**
 files that have been written by the FBX Importer.
 |

**
Close
**
 |
Closes the currently open file.
 |

**
Save
**
 |
Overwrites the current output file. (The current output file is the
**
.cgf
**
 file most recently written with
**
Save as...
**
 or loaded with
**
Open CGF
**
). This option is disabled if no current output file exists.
 |

**
Save As...
**
 |
Always shows a file dialog to specify the file path of the
**
.cgf
**
 file in the game folder. Also saves a copy of the source *.fbx (or other compatible) file to that same game folder, in which changes will be saved.

The FBX Importer will notify you if you attempt to overwrite a different *.fbx with the same filename this way.
 |

**
Import
**
 |
Imports a
**
.fbx
**
,
**
.dxf
**
,
**
.dae
**
,
**
.obj
**
 or
**
.3ds
**
 file.
 |

**
Reimport
**
 |
Reimports the current file if the user wants to revert the changes that has been made after the file was first imported.
 |

**
Recent Files...
**
 |
Lists the recently used files.
 |

##
Toolbars

Option

 |
Description

 |

**
Customize...
**

 |
Opens the toolbar customization window allowing users to customize existing toolbars, and/or create new toolbars within this tool.
 |

**
Lock Toolbars
**

 |
When disabled, the positions of toolbars and spacers within this tool can be changed by drag and drop.
 |

**
Spacers
**

 |
The following options allow users to use spacers in positioning their toolbars.

**
Insert Expanding Spacer
**
 |
Adds an expanding spacer to the toolbar layout; an expanding spacer pushes all elements situated at its ends to the edge of a panel.
 |

**
Insert Fixed Spacer
**
 |
Adds a fixed spacer, which has a fixed size of one icon.
 |

The
**
Spacers
**

menu options are only available when

**
Toolbars → Lock Toolbars
**

is disabled.
 |

**
Toolbars
**
 |
Lists all default and custom toolbars (if any) created for this tool, allowing users to select which toolbar they'd like to hide or display.
 |

When a tool has a toolbar, whether this is a default one or a custom one, the options above are also available when right-clicking in the toolbar area (only when a toolbar is already displayed).

##
Help

Opens the documentation page for this tool.

##
2. Toolbar

The toolbar has the following buttons:

Button
 |
Description
 |

![Image](https://www.cryengine.com/docs/static/attachments/44967746)

 |
See above under File.
 |

![Image](https://www.cryengine.com/docs/static/attachments/44967747)

 |
See above under File.
 |

##
3. Clips/Root Motion Panel

##
Clips

Here you can decide which animations to import or even add animations.

By clicking the button next to
**
Animation clips
**
, you can add new animations or remove all of the existing ones.

Removing a single animation clip is done by right-clicking on the number of the animation on the left and choosing
**
Remove
**
.

By clicking
**
Preview this
**
, you'll see the animation played out in the viewport.

##
Root Motion

By clicking Root motion, a node view appears.
In this view you can optionally select a single node. if a node is selected, it acts as the ,"locomotion locator". See
**

**
[Setting up Locomotion Locator in 3ds Max](../Asset%20Prep%20(External)/Asset%20Exporting%20Overview/Geometry%20Creation%20Overview/Animated%20Geometry/Basics%20(animated)/Rigging%20(animated)/Locomotion%20Locator.md)
.

##
4. Viewport

Here you'll see the graphical representation of the animation you're importing. There's one dropdown menu in the top-left corner of this panel:

Option
 |
Description
 |

**
Show all meshes
**
 |
Shows all meshes.
 |

**
Show selected node
**
 |
Shows only the meshes belonging to the node selected in the node list.
 |

**
Show selected subtree
**
 |
Shows only the meshes belonging to the subtree selected in the
 node list.
 |

##
5. Display Options

In the top-right corner of the viewport is the
**
Display Options
**
 button. Pressing this will open the Display Options menu.

This menu contains the following options:

##
View

Option
 |
Descripiton
 |

**
Joint names
**
 |
Shows/hides the names of the joints in the viewport.
 |

##
Debug

Option
 |
Descripiton
 |

**
Wireframe
**
 |
Shows/hides the wireframe of the asset.
 |

**
Framerate
**
 |
Shows/hides the framerate in the viewports.
 |

##
Camera

Option
 |
Description
 |

**
Show Viewport Orientation
**
 |
Shows an axis gizmo in the bottom-left corner of the viewports showing the orientation of the asset.
 |

**
FOV
**
 |
Changes the Field of View.

 |

**
Near Clip
**
 |
A higher value means a larger distance of the near clipping plane to the camera. Increase this value if you experience depth buffer artifacts on objects further away from the camera. Decrease this value if objects appear to be cut off near the camera.
 |

**
Move Speed
**
 |
Changes the movement speed in left and right direction. Forward and back is always speed 0.7.

 |

**
Rotation Speed
**
 |
Changes the rotation speed of the camera.
 |

##
Movement Smoothing

Option
 |
Description
 |

**
Position
**
 |
Basically "smears" translation of camera over time. Used to do smooth camera movements. A larger value means smoother transition over greater time span.

 |

**
Rotation
**
 |
Same as Position. Smoother camera rotations.

 |

##
Grid

Option
 |
Description
 |

**
Show Grid
**
 |
Shows/hides the grid.
 |

**
Main Color
**
 |
Lets you change the color of the main grid lines.
 |

**
Middle Color
**
 |
Lets you change the color of the middle grid lines.
 |

**
Spacing
**
 |
Changes the distance between the grid lines.
 |

**
Main Lines
**
 |
Changes the number of main grid lines.

 |

**
Middle Lines
**
 |
Changes the number of middle grid lines.
 |

**
Origin
**
 |
Draws a gizmo in the origin (position 0, 0, 0). Try it with an empty scene or wireframe mode to see the effect.
 |

##
Lighting

Option
 |
Description
 |

**
Brightness
**
 |
Changes the brightness of the ambient light on the asset.
 |

**
Ambient Color
**
 |
Changes the color of the ambient light on the asset.
 |

**
Rotate Light
**
 |
Turns continuous rotation of the directional light source on/off.
 |

**
Light Multiplier
**
 |
Used to dim or brighten the directional light.

 |

**
Light Spec Multiplier
**
 |
Changes specular highlight on object from directional light.

 |

**
Directional Light Color
**
 |
Sets the color of directional light.
 |

##
Background

Option
 |
Description
 |

**
Use Gradient
**
 |
Toggles between a gradient background and an evenly colored one.
 |

**
Top Color
**
 |
Changes the top color of the gradient background (if Use Gradient is unchecked, this will be the only color).
 |

**
Bottom Color
**
 |
Changes the bottom color of the gradient background.
 |

##
Skeleton

This will import the skeleton attached to the
**
.fbx
**
 file.

![Image](https://www.cryengine.com/docs/static/attachments/44968645)

##
1. Menu

For more information about the Menu options, please
[see here](FBX%20Import%20Tools.md#FBXImportTools-FileMenu)
.

##
2. Toolbar

For more information about the Toolbar buttons and their functionalities, please
[see here](FBX%20Import%20Tools.md#FBXImportTools-FileMenu)
.

##
3. Node List

In the Node List you can select which subtree or single node you want to import.

It also has a search bar at the top to quickly search for a specific node in case the asset has so many of them that it's hard to keep a good overview.

##
4. Viewport

Here you'll see the graphical representation of the skeleton you're importing. There's one dropdown menu in the top-left corner of this panel:

Option
 |
Description
 |

**
Show all meshes
**
 |
[See here.](FBX%20Import%20Tools.md#FBXImportTools-Viewport)
 |

**
Show selected node
**
 |
[See here.](FBX%20Import%20Tools.md#FBXImportTools-Viewport)
 |

**
Show selected subtree
**
 |
[See here.](FBX%20Import%20Tools.md#FBXImportTools-Viewport)
 |

##
5. Display Options

[See here](FBX%20Import%20Tools.md#FBXImportTools-DisplayOptions)
 for more information about the Display Options.

##
6. Properties

For more information, please refer to the
[Properties](FBX%20Import%20Tools.md#FBXImportTools-Properties)
section on this page.

##
Mesh

This part of the importer lets you import
**
meshes and skins
**
. The currently supported input formats are
**
.fbx
**
,
**
.dxf
**
,
**
.dae
**
,
**
.obj
**
, and
**
.3ds
**
 (however,
**
.fbx
**
 is the preferred format). In addition, the FBX Importer provides a graphical interface to change properties of the geometry that are specific to CRYENGINE, such as level of detail settings (LOD) and
[User-Defined Properties (UDP)](../Asset%20Prep%20(External)/Asset%20Exporting%20Overview/Geometry%20Creation%20Overview/Geometry%20Metadata%20(UDP).md)
.

![Image](https://www.cryengine.com/docs/static/attachments/44968182)

##
1. Menu

For more information about the Menu options, please
[see here](FBX%20Import%20Tools.md#FBXImportTools-FileMenu)
.

##
2. Toolbar

The Toolbar options provide a shortcut to the File options. For more information, please
[see here](FBX%20Import%20Tools.md#FBXImportTools-FileMenu)
.

In the Settings view, you'll find general settings and settings related to the conversion of your scene.

##
3. Settings View

##
General Settings

Setting
 |
Description
 |

**
Input filename
**
 |
Name of the file that was imported
 |

**
Output filename
**
 |
This is the file that will be overwritten when you click
**
Save
**
.

It's either the last file you saved with
**
Save as..
**
 or the file that you have opened with
**
Open CGF
**
.

 |

##
Static Mesh Settings

Setting
 |
Description
 |

**
Merge all nodes
**
 |
Combines all meshes on the same LOD to a single mesh.

**
NOTE:
**
 this is a rendering optimization and does not affect the pivots of the meshes.

 |

**
Scene origin
**
 |
By default, the RC ignores the local transformations of root nodes, which means that their pivots are placed at the world origin and meshes are translated accordingly. When
**
Scene origin
**
 is enabled, the local transformation is applied and root nodes keep their world space position.

 |

##
Conversion Settings

The
**
conversion settings
**
 control the scale and orientation of the CGF mesh. Use these settings for example if the coordinate system of the DCC tool used to create the source file is different from CRYENGINE's coordinate system (in Maya, Y = up instead of Z).

Setting
 |
Decription
 |

**
Unit
**
 |
Changes the unit of measurement in the mesh.
 |

**
Scale
**
 |
Changes the scale of the object.
 |

**
Forward
**
 |
Changes which axis points forward.
 |

**
Up
**
 |
Changes which axis points upward.
 |

##
Output Settings

Setting
 |
Description
 |

**
Use 32bit precision
**
 |
If enabled, vertex coordinates are stored with 32bit precision. If not enabled, they will be stored with 16bit precision.
 |

##
4. Source/Target View

This panel can be changed between two different views, the Source view and the Target view, by clicking the buttons at the top.

##
Source View

![Image](https://www.cryengine.com/docs/static/attachments/44966296)

The Source view shows the node hierarchy, a list of materials in the source scene and a list of textures used. Essentially, it reflects the scene setup in the source file. Selecting any item displays its properties in the
**
Properties
**
panel (7).

Below the Search bar, this panel has two columns, Name and Type:

Column
 |
Description
 |

**
Name
**
 |
Shows the name of the node.
 |

**
Type
**
 |
Shows whether the node is an LOD, Physics Proxy or Skin and in the case of an LOD or Physics Proxy, lets you change which LOD it is or change it into a (invisible) physics proxy.

If possible, the LOD of a node can be changed by clicking in this column. Changing the LOD of a node is possible if it is a leaf node and the child of a mesh node.

If a node does not have a drop-down menu, it does not qualify as an LOD.
 |

##
**
Right-Click Menus
**

When right-clicking on the column headers (Name, LOD), you can choose to show or hide either of these columns.

When right-clicking on a node, you get the following options:

Option
 |
Description
 |

**
Include this node
**
 |
Includes the node in the exported
**
.cgf
**
 file.
 |

**
Exclude this node
**
 |
Excludes the node from the exported
**
.cgf
**
 file.
 |

**
Select materials used by mesh
**
 |
In the material list on the right column, selects all the materials used by the currently selected mesh.
 |

**
Auto Add Proxies
**
 |
Automatically adds proxies to your mesh.
[See here](FBX%20Import%20Tools.md#FBXImportTools-AutoAddProxies)
 for more information about this feature.
 |

**
Expand child nodes
**
 |
Expands all child nodes of the currently selected node.
 |

**
Collapse child nodes
**
 |
Collapses all child nodes of the currently selected node.
 |

**
Expand all nodes
**
 |
Expands the list of nodes.
 |

**
Collapse all nodes
**
 |
Collapses the entire list of nodes.
 |

**
Show only skins
**
 |
Shows only skin nodes.

**
NOTE:
**
 this simply does a search for "skin". To show other nodes again, delete the text from the Search bar.
 |

**
Including and Excluding Nodes
**

By default, every node in the hierarchy is also included in the
**
.cgf
**
 file, indicated by the ticked box next to its name. You can exclude a node in the properties panel, or by
**
right-clicking
**
 it in the node list. Conversely, if you untick a node, then its mesh will not appear in the
**
.cgf
**
 file.

Excluding a node excludes all of its children (so its entire subtree).

Example: consider a hierarchy A → B → C, where A is the root and a parent of B, and B is a parent of C. When you exclude B, then C is also excluded.

**
Importing Skin
**

Through the Import Mesh tool you can also import skins for your assets. However, it is a case of either/or: you either import the mesh or you import the skin.

The skins can be found in the Source tab:

![Image](https://www.cryengine.com/docs/static/attachments/44968654)

Simply tick the box in front of the skin you want to import and click the
**
Save
**
 button (or
**
File -> Save
**
) to import this skin.

You can only import one skin at a time.

##
Target View

The Target view shows the node hierarchy of the output
**
.cgf
**
 file. Here you see the effect of the
**
Merge all nodes
**
 option.

![Image](https://www.cryengine.com/docs/static/attachments/44966295)

##
5. Viewport

Here you'll see the graphical representation of the animation you're importing. There's one dropdown menu in the top-left corner of this panel:

Option
 |
Description
 |

**
Show all meshes
**
 |
[See here.](FBX%20Import%20Tools.md#FBXImportTools-Viewport)
 |

**
Show selected node
**
 |
[See here.](FBX%20Import%20Tools.md#FBXImportTools-Viewport)
 |

**
Show selected subtree
**
 |
[See here.](FBX%20Import%20Tools.md#FBXImportTools-Viewport)
 |

##
6. Display Options

##
View

Option
 |
Description
 |

**
Show Edges
**
 |
Shows/hides Edges in the bottom half of the viewport when Show RC Mesh is enabled.
 |

**
Show Proxies
**
 |
In Game viewport, shows proxy materials and proxy nodes in transparent blue.

 |

**
Show Size
**
 |
Shows two boxes. The white one is the actual mesh bounding box. The grey one is a 1x1x1 cube to give some hint for the relative size of the mesh.

 |

**
Show Pivots
**
 |
Draws a line from the center of a mesh bounding box to its origin. Makes it obvious if a cube, for example, is modeled around 0, or offset by some amount. Interesting if relative translation of meshes is off.

 |

**
Viewport Mode
**
 |

-
**
Game -
**
Shows the final game mesh in the viewport
.

-
**
Source -
**
Fast-to-compute preview which does not involve the RC. It might give you a chance to debug the
**
.fbx
**
 file in case the RC fails an the console output is insufficient.

-
**
Game and Source -
**
Opens both a Game and a Source viewport in the viewport area.
 |

**
Show LOD
**
 |
Only useful if the
**
.cgf
**
 contains LODs (level of details). By setting this to N, it shows you what mesh the engine chooses for LOD N. When you have no LODs specified, then the mesh is the same for all levels.

 |

For a description of the rest of the Display Options,
[click here.](FBX%20Import%20Tools.md#FBXImportTools-DisplayOptions)

##
7. Properties/Material Panel

This panel can either show the properties of the node selected in the Source view.

##
Properties Panel

Depending on whether the whole scene, a sub-tree or a single node is selected in the Node List, the following options appear:

![Image](https://www.cryengine.com/docs/static/attachments/44966309)

Option
 |
Description
 |

**
Included in Export
**
 |

-
**
Excluded
**
 - excludes the selected node or sub-tree from export.

-
**
Included
**
 - includes the selected node or sub-tree in the export.
 |

**
Physics Proxy
**
 |
Toggles some UDP options which only make sense for proxies.

 |

##
Physical Options

Option
 |
Description
 |

**
Jointed Breakable
**
 |
This option only appears when non-mesh nodes are selected. When activated, the following options appear:

-
**
Gameplay Critical -
**
Joints in the entire entity will break, even if jointed breaking is disabled overall. For example, if a level uses many breakable objects, but has disabled breaking (they don't want them to break), but they <do> want certain specific objects to break for gameplay reasons -- then only those objects with
*
gameplay_critical
*
 will be breakable.

-
**
Player Can Break -
**
Joints in the entire breakable entity can be broken by the player bumping into them.
**

**

-
**
Limit -
**
Limit is a general value for several different kind of forces applied to the joint. It contains a combination of the values below.

**
ATTENTION!
**
 - This value
**
needs
**
 to be defined, otherwise the simulation will not work correctly.

Crysis Example values: 100 - 500 can be broken by a bullet; 10000 can be broken by the impact of a driving vehicle or a big explosion.

-
**
Bend -
**
Maximum torque around an axis perpendicular to the normal.

-
**
Twist -
**
Maximum torque around the normal.

-
**
Pull -
**
Maximum force applied to the joint's 1st object against the joint normal (the parts are "pulled together" as a reaction to external forces pulling them apart).

-
**
Push -
**
Maximum force applied to the joint's 1st object (i.e. the one whose name is listed first in the joint's name, or if the names were not specified, the object the joint's z axis points towards) along the joint normal; joint normal is the joint's z axis, so for this value to actually be "push apart" (as a reaction to external forces pressing the parts together), this axis must be directed inside the 1st object.

-
**
Shift -
**
Maximum force in the direction perpendicular to normal.

-
**
Constraint Limit -
**
Force limit for the newly created constraint, is checked when the constraint hits a rotation limit and is being pushed further.

-
**
Constraint Min Ang -
**
Rotation limits for the constraint (the interpretation is the same as in standalone constraints). The default is no limits.

-
**
Constraint Max Ang -
**
Rotation limits for the constraint (the interpretation is the same as in standalone constraints). The default is no limits.

-
**
Constraint Damping -
**
Angular damping (default 0).

-
**
Constraint Collides -
**
Whether the constraint parts will ignore collisions with each other (default 1).
 |

**
Mass
**
 |
Mass defines the weight of an object based on real world physics in kg.
**
mass=0
**
 sets the object to "unmovable".

This is used on your base piece that will never move, e.g: on the basement of a house for example or the sign pole which should not be movable and always stay in the original position.

When used in brushes and Geom Entities, this is the remaining part's mass. When used in regular Entities, all parts masses are scaled so that their total mass gives the mass specified in the entity properties.

**
CAUTION
**
 - You must either define this value or density to ensure the simulation is working correctly.
 |

**
Density
**
 |
The engine automatically calculates the mass for an object based on the density and the bounding box of an object.  Can be used alternatively to
*
mass
*
.
 |

**
No Hit Refinement
**
 |
Do not perform hit-refinement at the rendermesh level – only use the phys proxy's surface type (but decals/effects will still be projected back to the rendermesh). If this is used, then the rendermesh doesn't have to have a surface type assigned – only the phys proxy material(s) should have surface types.

By default, hit-refinement on the rendermesh is always performed, unless this string is set. Another way of having more precise ray traces is to have a dedicated 'no-collide' or 'obstruct' proxy.
 |

**
Dynamically Breakable
**
 |
This is a special-case string for dynamically breakable meshes (i.e. glass) – this string flags the object as "dynamically breakable".

However this string is not required on Glass, Trees, or Cloth, as these are already flagged automatically by the engine (through surface-type system). This should only be used on new types of dynamically-breakable meshes.
 |

**
Spawn As Entity
**
 |
If the render geometry properties include "entity", the object will not fade out after being disconnected from the main object.
**

**
 |

**
Pieces
**
 |
Instead of disconnecting the piece when the joint is broken, it will instantly disappear spawning a particle effect depending on the surfacetype of the proxy.
 |

**
Deformable
**
 |

-
**
Stiffness -
**
 Resilience to bending and shearing (default 10).

-
**
Hardness -
**
Resilience to stretching (default 10).

-
**
Max Stretch
**
 -
**
**
If any edge is stretched more than that, it's length is re-enforced. max_stretch = 0.3 means stretched to 130% of its original length (or by 30% wrt to its original length). Default 0.01.

-
**
Max Impulse
**
 -
**
**
 Upper limit on all applied impulses. Default skeleton's mass*100.

-
**
Skin Distance
**
 -
**
**
 Sphere radius in skinning assignment. Default is the minimum of the main mesh's bounding box's dimensions.

-
**
Thickness
**
 -
**
**
Sets the collision thickness for the skeleton. The skeleton collides as a cloth object, i.e. it has virtual spheres with this radius around each vertex, and it has less priority than the geometries it collides with (it'll un-project itself unconditionally from them). It collides with static and rigid body objects only. It will collide with parts of the same entity it belongs to, except the one it skins (this way it's possible to set up safety shells inside the object to prevent excessive deformations). Setting thickness to 0 disables all collisions.

-
**
Explosion Scale
**
 -
**
**
Used to scale down the effect of explosions on the deformable. This lets you have visible deformations from bullet impacts, but without vastly distorting the object too far with explosions.
 |

**
Primitive
**
 |
Force this proxy to be a primitive in the engine.
 |

**
No Explosion Occlusion
**
 |
Will allow the force /damage of an explosion to penetrate through the physics proxy.
 |

**
*

*
Custom Properties
**

Option
 |
Description
 |

**
Custom
**
 |
Here you can add UDPs as key=value pairs, just as in the DCC tools. You can add UDPs for which
extra widgets
 are not
 or
 can't be
provided (think of game-specific UDPs).
**

**

 |

**
Node information
**

Both node and mesh information are mainly for debugging. They show transformations read from the
**
.fbx
**
 file.

Node transformations are typically the transformations set in the DCC tool and might be different from 0,0,0.

Option
 |
Description
 |

**
Translation
**
 |
Shows the translation of the selected node in the source file.
 |

**
Rotation
**
 |
Shows the rotation
of the selected node
 in the source file.
 |

**
Uniform Scale
**
 |
Shows the scale of the X, Y, and Z axis. If the scaling is the same on all three axis, we simplify the output and write a single value for "uniform scale" instead.
 |

**
Number of child meshes
**
 |
Shows the number of child meshes the node has.
 Nodes may have more than one mesh attached. Internally, we merge them to a single mesh per node.

 |

**
Attributes
**
 |
Mainly for debugging. A list of node attributes we read from the FBX. Shows what type this node is (examples: Camera, Light, Mesh).

 |

**
Mesh Information
**

Meshes might have their own transformations, which is an offset from their node, but this is usually 0,0,0.   Otherwise, same as "node information".

Option
 |
Description
 |

**
Translation
**
 |
Shows the translation of the selected mesh in the source file.
 |

**
Rotation
**
 |
Shows the rotation of the selected mesh in the mesh file.
 |

**
Uniform Scale
**
 |
Shows the scale of the X, Y, and Z axis. If the scaling is the same on all three axis, we simplify the output and write a single value for "uniform scale" instead.
 |

**
Number of triangles
**
 |
Number of triangles the selected mesh has.
 |

**
Number of vertices
**
 |
Number of vertices the selected mesh has.
 |

##
Material Panel

The Material panel shows all the materials present in the source file. Each source material has a
**
Sub-material
**
ID,
**
Physicalization
**
 setting and
**
Color
**
.

*
![Image](https://www.cryengine.com/docs/static/attachments/44966308)

*

About materials: We call the materials in the
**
.fbx
**
 file source materials. These are the materials you set up in the DCC tool. The engine material is the one you create in the Sandbox material editor. The engine material may have sub-materials. Purpose of the material list is to map source materials to engine sub-materials. When you have a source material with name "HeadDiff" and you assign it sub-material id 2, you say "All the vertices using material HeadDiff should use the
third

sub-material of the engine material" because we start counting with id 0. (sub-material 0 is the first one).
**
Settings
**

Option
 |
Description
 |

**
Material
**
 |
Shows the material used in the scene.
**

**
Each CGF has a reference to a single material. With this material picker you set the material of the output CGF.
**

**
 |

![Image](https://www.cryengine.com/docs/static/attachments/44966307)
 |
Opens the Material Editor (only works if a material has been assigned)
 |

![Image](https://www.cryengine.com/docs/static/attachments/44966306)
 |
Assigns a material to the scene.
 |

##
Material List

The top half of the Material panel shows the materials used in the source scene.

Column
 |
Description
 |

**
Material name
**
 |
 Shows the name of the material.
 |

**
Sub-material
**
 |
Maps a source material to a slot of the engine material that can be assigned in the
**
Settings view
**
. The Sub-material can be changed by clicking in the
**
 Sub-material
**
 column and choosing a sub-material from the drop-down menu that appears
 |

**
Physicalization
**
 |
The
**
Physicalization
**
 setting is the same as in the DCC exporters.
If you set the physicalization setting of a material, it also sets the same setting for all other materials with the same sub-material id.

**
NOTE:
**
 This setting can be changed the same way as the Sub-material: by clicking in the
**
 Physicalization
**
column and choosing a sub-material from the drop-down menu that appears.
 |

**
Color
**
 |
The
**
Color
**
 of a source material is for previewing purposes only. Setting a source material color helps finding all vertices using this material in the preview viewport, but does not affect the color of the exported
**
.cgf
**
 file in any way.
 |

**
Right-Click Menus
**

When right-clicking on the
*
column headers
*
 (Material name, Sub-material, Physicalization, Color), you can choose to show or hide these columns.

When right-clicking on a
*
material
*
, you get the following options:

Option
 |
Description
 |

**
Select meshes using this material
**
 |
Selects nodes in the Node List that use the selected material.
**
**

**
**
 |

**
Select sub-material color
**
 |
Lets you select the color shown in the viewport for the selected material.
 |

**
Generate Material
**

Click on
**
Generate material
**
 on the right hand side

if you want to generate a material from the FBX
. Alternatively, you can browse for an already created material.

##
Texture List

The Texture List underneath the Material List shows all the textures used in the source object. This panel has four columns:
**
Filename
**
,
**
Exists
**
,
**
TIF exists
**
 and
**
RC Defaults
**
.

Column
 |
Description
 |

**
Filename
**
 |
Shows the filename of the textures used.

 |

**
Type
**
 |
Lets you choose the type of the texture (diffuse, bumpmap or specular). This essentially sets the preset setting for the RC when converting to CryTif.

 |

##
Adding Auto Proxies

In the Mesh Importer, you can add proxy meshes to static meshes with only a few clicks. The shapes for the proxy meshes are automatically generated.

This is done in the
**
Source
**
 tab in the bottom left corner. Simply right click on the Scene node or any of the sub-nodes and choose
**
Add Auto Proxies
**
.

*
![Image](https://www.cryengine.com/docs/static/attachments/44966324)
*

When you've added these Auto Proxies, you'll see the render mesh that will be used to generate proxies from. If it has several components, you can select which ones you want to use by clicking on them (a component - also called an "island" - is a part of the mesh that's not connected to the rest; for scene proxies each node will be a separate component, but it's also possible for nodes to have sub-components based on mesh connectivity). If you remove some components from an auto-proxies node, you can add them to a new auto-proxies node by going to the parent's menu again and selecting "Add remaining proxies".

The proxies are generated by voxelizing the render mesh, locating parts of it that can be reasonably approximated by primitives, and building simplified meshes from the remaining voxels.

When selecting the
**
Auto Proxies
**
 parent node in the
**
Source
**
 tab, you'll see several buttons and tick boxes in the Properties panel:

![Image](https://www.cryengine.com/docs/static/attachments/44966323)

Button
 |
Description (only active before the proxies have been generated)
 |

**
Close Holes
**
 |
Closes holes on the mesh used for voxelization. Open holes can result in voxels "spilling" through them.
 |

**
Reopen Holes
**
 |
Reopens the holes closed with the Close Holes button.
 |

**
All
**
 |
Selects all components for generation.
 |

**
None
**
 |
De-selects all components.
 |

**
Generate
**
 |
Generates the proxies for the components you have selected. New sub-nodes for every proxy mesh shape will now appear under the
**
Auto Proxies
**
 parent node.
 |

**
Reset
**
 |
Removes all the generated proxies, letting you start the process again.
 |

**
Source Mesh
**
 |
Shows/hides the mesh of the source object. There are three degrees to which the source mesh can be shown:

-
**
Solid -
**
 Makes the source mesh appear solid.

-
**
Transparent -
**
 Makes the source mesh appear solid.

-
**
Hidden -
**
 Hides the source mesh completely.
 |

**
Proxy Mesh
**
 |
Shows/hides the generated proxy meshes. There are three degrees to which the proxy meshes can be shown:

-
**
Solid -
**
 Makes the proxy meshes appear solid.

-
**
Transparent -
**
 Makes the proxy meshes appear solid.

-
**
Hidden -
**
 Hides the proxy meshes completely.

 |

**
Primitives
**
 |
Shows/hides the generated primitive proxies. There are three degrees to which the generated primitive proxies can be shown:

-
**
Solid -
**
 Makes the generated primitive proxies appear solid.

-
**
Transparent -
**
 Makes the generated primitive proxies appear solid.

-
**
Hidden -
**
 Hides the generated primitive proxies completely.
 |

**
Voxels
**
 |
Shows/hides the source mesh voxelization. There are two degrees to which the source mesh voxelization can be shown:

-
**
Solid -
**
 Makes the source mesh voxelization appear solid.

-
**
Hidden -
**
 Hides the source mesh voxelization completely.
Showing the voxels will help you edit the proxy shape; you can click a voxel in the viewport and that point will be connected to the rest of the proxy mesh.
 |

The final proxy of your asset will be based on the
**
Proxy Mesh
**
 and the
**
Primitives
**
 mentioned above. The
**
Source Mesh
**
 only serves as a way to see if the proxy is similar to the object and the Voxels are only the base on which the rest is built, as well as helping you to edit the proxy shape (see above).

##
Deselecting Components

Before you Generate your auto proxies, you can deselect any components you don't want to include in the proxy. To do this, you simply click on them in the viewport. They will then appear transparent, meaning that they will not be generated:

![Image](https://www.cryengine.com/docs/static/attachments/44966326)

![Image](https://www.cryengine.com/docs/static/attachments/44966325)

If you have deselected some components, they can be re-added after generation by right clicking the
**
Scene
**
 node and choosing
**
Add Remaining Auto Proxies
**
. A new group of nodes will then be created. Select the parent node of this new group and click
**
Generate
**
 to generate the missing auto proxies.

##
Properties

When selecting the automatically generated proxies in the
**
Source
**
 tab, you can get a variety of properties in the
**
Properties
**
 panel. These are different depending on what kind of proxy you have selected.

##
Auto Proxies (parent, all sources)

Property
 |
Description
 |

**
Merge islands
**
 |
Selects whether to build a separate voxelization for each island (component), or use a combined one.
 |

**
Axis-aligned voxels
**
 |
Use axis-aligned voxels or try to find the "best fitting" bounding box orientation.
 |

**
Force single box
**
 |
Forces a single bounding box as the proxy.
 |

**
Convex hull
**
 |
Make convex hull of the source mesh before voxelization.
 |

**
Detect primitive surfaces
**
 |
Detect boxes and cylinders in the voxelization.
 |

**
Detect primitive rods
**
 |
Detect capsules and longer cylinders in the voxelization.
 |

**
Voxel cell number
**
 |
Sets the voxelization resolution (along the longest dimension).
 |

**
Mesh smoothing passes
**
 |
Amount of normal smoothing applied to voxels left approximating with meshes. More smoothing means simpler proxies, but can lead to losing too many details.
 |

Advanced settings
 |

**
Use in and max normals as mesh vertices
**
 |
Check if proxy meshes lose too many important features.
 |

**
Inflate primitives
**
 |
Size inflation applied to detected primitives.
 |

**
Inflate meshes
**
 |
Size inflation applied to detected meshes.
 |

**
Minimal rod primitive volume efficiency
**
 |
Threshold ratio of volume covered by voxels / total primitive volume. Primitive rods (long capsules and cylinders) with ratios lower than this are discarded.
 |

**
Minimal surface primitive volume efficiency
**
 |
Threshold ratio of volume covered by voxels / total primitive volume. Primitive surfaces (boxes and cylinders) with ratios lower than this are discarded.
 |

**
Height/radius threshold for capsule/cylinder rods
**
 |
Rods with height/radius ration higher than this are set to be capsules.
 |

**
Merge primitive surfaces threshold (in voxels)
**
 |
Merges initial surface approximation candidate areas within this distance.
 |

**
Surface detection smoothing iterations
**
 |
Generally more iterations leads to fewer/larger surface primitives.
 |

**
Surface flatness threshold
**
 |
Sets how flat a region should be to be considered a surface primitive candidate.
 |

**
Surface alignment with mesh normal threshold
**
 |
Sets how closely the principal surface primitive alignment should coincide with the source mesh.
 |

**
Rod candidates merge threshold (in voxels)
**
 |
Merges initial rod approximation candidate areas within this distance.
 |

**
Rod candidates curvature threshold
**
 |
Bending limit for areas considered for rod approximation.
 |

**
Inflate primitives for voxel removal (in cells)
**
 |
Once a primitive is detected, the voxels contained in it are removed. This parameter sets how much to inflate the primitive for voxel removal (it has to be removed at least a little to avoid stray voxel noise on the surface)
 |

**
Primitives holes refill ratio
**
 |
Sets how strongly to refill holes caused by primitive removal from the voxelization (larger values can lead to "bulging")
 |

**
Required primitive exposed area
**
 |
Minimal primitive area that should not be covered by other voxels.
 |

**
Minimal surface primitive voxels number
**
 |
Minimal amount of voxels in surface primitive candidate regions.
 |

**
Minimal rod primitive voxels number
**
 |
Minimal amount of voxels in rod primitive candidate regions.
 |

**
Minimal mesh voxels number
**
 |
Minimal amount of voxels in islands left for mesh approximation.
 |

**
Refine voxels with source mesh
**
 |
Align proxy mesh vertices (based on voxels) with the source mesh. Generally recommended, unless the source mesh is too detailed or noisy.
 |

If you select a generated proxy in the
**
Source
**
 tab, you can set the submaterial index assigned to it and its Crytek proxy type (
**
Solid
**
/
**
Obstruct
**
/
**
NoCollide
**
). For primitives
**
dimensions
**
 and
**
orientation
**
 can be manually edited, and for meshes it's possible to click on individual voxels to trigger them being a proxy mesh vertex (initially only a small fraction of voxels are selected as vertices, based mainly on the "mesh smoothing passes" setting). Note that the latter doesn't require the corresponding mesh proxy to be selected.

##
Setting up FBX Skeleton Proxies and Ragdoll Limits

This feature enables the creation of physicalized characters through the FBX pipeline, which requires the specification of bone proxy geometries and bone ragdoll limits.

##
Setting Skeleton Proxies

From CRYENGINE 5.3, bones can be assigned in mesh nodes as proxies. This means that the FBX must already contain all the proxy geometries. The mesh nodes that are used as proxies are not required to conform to any hierarchy.

If you have followed the Max or Maya naming conventions (for example, a bone is named "
*
Bone
*
", its proxy has name "
*
Bone phys
*
" or "
*
Bone_phys
*
"), mesh nodes are automatically assigned to the bones.

![Image](https://www.cryengine.com/docs/static/attachments/44966321)

##
Setting Ragdoll Limits

The ragdoll limit's properties contains a matrix with 6 entries: each of the three axes X,Y, and Z; there can be a minimum and maximum constraint. The constraint values are relative to a bone's bind pose rotation (They are added to a bone's local transformation when written to .chr file).

The matrix contains four controls for each constraint. Besides a spinbox for the actual value, there are two buttons and a checkbox. The checkbox can be used to disable or enable a constraint. The left and right buttons are used to copy the constraint from and to the current pose, respectively.

A bone can be posed with the controls above the IK limits. This pose is mostly used for previewing only. The typical workflow for setting IK constraints is by posing a bone in an extreme position and then copying that pose to a constraint.

![Image](https://www.cryengine.com/docs/static/attachments/44966327)

##
3. Settings View

In the Settings view, you'll find general settings and settings related to the conversion of your scene.

##
General settings

Setting
 |
Description
 |

**
Input filename
**
 |
Name of the file that was imported.

 |

**
Output filename
**
 |
This is the file that will be overwritten when you click
**
Save
**
.

It's either the last file you saved with
**
Save as...
**
 or the file that you have opened with
**
Open CGF
**
.

 |

##
Static Mesh Settings

Setting
 |
Description
 |

**
Merge all nodes
**
 |
Combines all meshes on the same LOD to a single mesh.

**
NOTE:
**
 this is a rendering optimization and does not affect the pivots of the meshes.

 |

**
Scene origin
**
 |
By default, the RC ignores the local transformations of root nodes, which means that their pivots are placed at the world origin and meshes are translated accordingly. When
**
Scene origin
**
 is enabled, the local transformation is applied and root nodes keep their world space position.

 |

##
Conversion Settings

The
**
conversion settings
**
 control the scale and orientation of the CGF mesh. Use these settings for example if the coordinate system of the DCC tool used to create the source file is different from CRYENGINE's coordinate system (in Maya, Y = up instead of Z).

Setting
 |
Description
 |

**
Unit
**
 |
Changes the unit of measurement in the mesh.
 |

**
Scale
**
 |
Changes the scale of the object.
 |

**
Forward
**
 |
Changes which axis points forward.
 |

**
Up
**
 |
Changes which axis points upward.
 |

##
Output Settings

Settings
 |
Description
 |

**
Use 32bit precision
**
 |
If enabled, vertex coordinates are stored with 32bit precision. If not enabled, they will be stored with 16bit precision.
 |

[Basic Workflow of All Tools](#basic-workflow-of-all-tools)
[Animation](#animation)
[Skeleton](#skeleton)
[Mesh](#mesh)
[Adding Auto Proxies](#adding-auto-proxies)
[Setting up FBX Skeleton Proxies and Ragdoll Limits](#setting-up-fbx-skeleton-proxies-and-ragdoll-limits)
