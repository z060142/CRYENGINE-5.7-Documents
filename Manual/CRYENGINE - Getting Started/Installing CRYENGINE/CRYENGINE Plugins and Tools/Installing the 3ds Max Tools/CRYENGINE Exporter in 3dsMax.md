# CRYENGINE Exporter in 3dsMax

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/13205563
- Page ID: 13205563
- Breadcrumb: CRYENGINE - Getting Started > Installing CRYENGINE > CRYENGINE Plugins and Tools > Installing the 3ds Max Tools > CRYENGINE Exporter in 3dsMax
- Parent: Installing the 3ds Max Tools

## Content

##
Overview

This article covers the usage of CRYENGINE Exporter UI in 3ds Max.

##
Geometry Export

The
**
Geometry Export
**
 panel contains options for specifying which nodes in the scene need to be exported, as well as other options regarding how they will be exported. Most of these options are relevant only if the geometry is being exported (they are not important while exporting animations).

The most important control is the node list. This option is located at the top of the panel and shows the nodes that have been selected for exporting. To add a node to the list, select the
**
node
**
 and click
**
Add Selected
**
. Note that if the nodes in the list have any children, they will also be exported.

Underneath the node list, there is a drop-down list labelled
**
Export Format
**
 which allows the user to select the type of file to be exported. There are some other options in the Geometry Export panel.

[Image: /docs/static/attachments/25498031]

Option

 |
Description

 |

**
Pick
**
 |
Lets you pick the nodes individually from the viewport.

 |

**
Remove
**
 |
Lets you remove the nodes from the node list.

 |

**
Add Selected
**
 |
Lets you add the selected nodes from the viewport. You can also select the entire object and add all the nodes to the
selection window.

 |

**
Clear List
**
 |
Clears all the nodes from the list.

 |

**
Select in Viewport
**
 |
Highlights the selected nodes in scene. You need to select a node in the
node list to highlight it.

 |

**
Export Format
**
 |
Let you to save the nodes in the following formats:

-
Geometry
(*.cgf)

-
Character
(*.chr)

-
Character Skeleton
(*.skel)

-
Character Skin
(*.skin)

-
Animated Geometry
(*.cga)

-
Animation for CGA (*.anm)
 |

**
Export File per Node
**
 |
Exports each node in the export list as a separate file. The file name is generated from the node name.

 |

**
Custom Filename
**
 |
Overrides the default export file name. Does not work if the
**
Export file per node
**
 check box is enabled.

 |

**
Merge All Nodes
**
 |
Compiles all the geometry from the different nodes into a single node which improves the efficiency. It's supported
only
for non-skinned geometry. For more information on Merge All Nodes, please refer
**
[/docs/static/engines/cryengine-5/categories/23756816/pages/29799063](
here
)
**
.

 |

**
Vertex Colors
**
 |
Enables the vertex colors to be saved.

 |

**
Custom normals
**
 |
Uses Mikktspace for tangent space calculation when selected.

 |

**
Share mesh instances
**
 |
Enables the
nodes to share a mesh in CGF w
hen two nodes share a mesh in Max.

 |

**
Use 32bit precision
**
 |
Stores vertex positions using 32 bit per coordinate.
 |

**
8 weights per vertex
**
 |
Enables the vertex to be influenced by 8 bones.
**

**
 |

**
Morph target pos. threshold
**
 |
Ignores the vertices that do not move the distance (in meters) specified in this field when the morph target is exported.
 |

##
Animation Export

This panel contains the settings for the model's skeleton. This is important in both the cases of exporting skinned models and for their animations. In particular, it contains a control that lists the bones of the skeleton. Note that any children of the bones in this list are automatically exported; therefore, only the root bones need to be displayed.

Normally, when a node is added to the node list, its skeleton root bone is added to the bones list. This means that it is normally not necessary to deal with the Animation Export panel. However, sometimes it is helpful to be able to directly manipulate this; for instance, when a user wants to export animations for only the upper body.

The other options in this panel are the parameters for exporting animations. The following image displays the Bone Export panel.

[Image: /docs/static/attachments/25497761]

Option

 |
Description

 |

**
Ignore dummies
**

 |
Prevents any dummies that are in the bone hierarchy from being exported.

 |

**
Animation range
**

 |
Allows you to select an
entire
range or enter a custom range to be exported.

 |

##
Miscellaneous Settings and Tools

The following images display the available miscellaneous settings and tools.

[Image: /docs/static/attachments/25497762]

Option

 |
Description

 |

**
Sync Material
**

 |
Updates the settings in the 3ds Max material to match those in the engine material (.mtl file) used for this object.

 |

**
Create Material
**

 |
Creates an MTL file with settings that match those used in the 3ds Max material.

 |

[Image: /docs/static/attachments/25497763]

Option
 |
Description
 |

**
Degenerate UVW
**
 |
Checks for degenerate texture coordinates and issues a warning if they exist.
Degenerate coordinates are when two vertices on a triangle have the same (or very nearly the same) UVs.
 |

**
Off-axis scaling
**
 |
Checks whether the node is scaled along a non-primary axis. The node can still be exported, but the scale will not match the object in 3ds Max.
 |

**
Confirm File Overwrite
**
 |
Displays a warning to the user that they are about to overwrite the existing file.
 |

**
Keep Uncompiled Files
**
 |
Lets you save the uncompiled *.cgf files as a separate file.
 |

**
CRYENGINE Settings
**
 |
Launches the CRYENGINE Settings Manager.
 |

**
Show Log
**
 |
Launches the log window.
 |

These panes control various other aspects of the export process. Usually, they can be left at their default values. Some of their applications are listed in the individual export procedures described below.

You will also want to refer to
**
[/docs/static/engines/cryengine-5/categories/23756816/pages/23308297](
Phys Proxy Tool
)
**
 which is an additional tool available to 3ds Max users.

##
Showing the CRYENGINE Exporter

In order for the CRYENGINE Exporter to be visible in Max, you need to configure the button sets to show the exporter.

In the
**
Utilities
**
 tab, click on the
**
 Configure Button Sets
**
icon, and assign a button to the
**
CRYENGINE Exporter
**
 in the
**
Configure Button Sets
**
 window
.

*
Configuring CRYENGINE Exporter
*

[Image: /docs/static/attachments/25506741]

When you have installed the Exporter
(
using the
**
[/docs/static/engines/cryengine-3/categories/1114113/pages/17826148](
CryToolsInstaller
)
**
), the CRYENGINE exporter should appear at the bottom of the list.

[Image: /docs/static/attachments/25506743]

Simply drag it from the list on the left and add into the
**
Utilities
**
list on the right. You can add,  delete, or rearrange the buttons.

Note the
**
Total Buttons
**
 may need to be increased if you're already reached the maximum number of buttons allowed.

[#geometry-export](
Geometry Export
)
[#animation-export](
Animation Export
)
[#miscellaneous-settings-and-tools](
Miscellaneous Settings and Tools
)
[#showing-the-cryengine-exporter](
Showing the CRYENGINE Exporter
)
