# CryMaxTools - Phys Proxy Tool

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/23308297
- Page ID: 23308297
- Breadcrumb: CRYENGINE - Getting Started > Installing CRYENGINE > CRYENGINE Plugins and Tools > Installing the 3ds Max Tools > CryMaxTools - Phys Proxy Tool
- Parent: Installing the 3ds Max Tools

## Content

##
Overview

Creating and fitting physics proxies is usually a cumbersome and time-consuming process. To speed up the process, we created a maxscript tool that will autonomously create a box-proxy and attempt to fit it to the render-geometry as tightly as possible. The CryToolBox is installed automatically when you select 3dsMax from the menu when running the
**
CryToolsInstaller.exe
**
 from the tools folder.

##
First Steps

-
Launch the CryMaxTools, open the Model tab and navigate to the Phys Proxy Tool rollout:

[Image: /docs/static/attachments/23996891]

-
Set the
**
Material ID
**
 spinner to the number of the sub-material that you want the proxy to use:

[Image: /docs/static/attachments/23996890]

-
Select the Objects or SubObjects that you want to create a physics proxy for.

-
Hit one of the buttons in the row of the
**
Box
**
 button to create proxies.

[Image: /docs/static/attachments/23996889]

##
Parameters and Characteristics

Parameters

 |
Description

 |

**
Name
**

 |
Base name for the proxies to be created. "$physics_proxy" is the current engine-default.

 |

**
UDPs
**

 |
Additional user string for the Proxy's User Defined Properties. Separate by spaces.
[/docs/static/engines/cryengine-5/categories/23756816/pages/23308017](
**
See here for details
**
.
)

 |

**
Material ID
**

 |
Sets the Material ID that will be applied to the Box Proxy.

 |

**
Proxy per Element
**

 |
When enabled, the tool will create a separate Proxy for each Element of the Editable Poly.

 |

**
Size Bias
**

 |
Enlarge created proxy by so many centimeters on each axis. Use to compensate for imprecision, to ensure that the render mesh is fully encapsulated.

 |

**
Error Threshold
**

 |
The script will stop refining the box alignment when the last iteration shrunk the box's diagonal by less than "so" many centimeters.

 |

**
Realtime Preview
**

 |
When on, a semi-transparent box will be displayed to visualize how the script refines its alignment to find the smallest possible box. It can be fun to watch, but will also slow down the process.

 |

##
Known Limitations and Characteristics:

-
The Tool will only accept Editable Poly objects - everything else will be ignored.

-
If multiple Objects are selected, the tool will create a separate Phys Proxy for each of object selected.

-
The
**
Box
**
 button will create a box around the Render Geometry without any rotation. It's a simple Axis Aligned Bounding Box.

-
The
**
Aligned
**
 button will create a box that fits the Render Geometry as tightly as possible. It's an Object Aligned Bounding Box. This one works best in most cases.

-
The
**
X
**
,
**
Y
**
 and
**
Z
**
 buttons work similar to the
**
Aligned
**
 button, but will allow the box to only rotate around one axis. This can be helpful when one wants to 'lock' the box to one axis.

-
The Algorithm used to find the minimum volume bounding box, is not 100% accurate. The script will literally rotate the box around until it's the smallest. While doing so, it tries to narrow down to the sweet-spot by continuously refining the search range. This can result in very few cases where it won't find the optimal aligned bounding box. Also very few cases may have multiple optimal orientations. In those cases, it can help to work with sub-object selections and the
**
X
**
,
**
Y
**
,
**
Z
**
 buttons.

-
The buttons for Capsule, Cylinder, Sphere and Convex Hull are currently disabled. These features might be added later.

-
The tool currently does not support undo/redo, so the user will need to delete the box manually if it's not satisfying.

-
When working with complex objects, it's best to work with sub-object selection to create multiple proxies, see image below:

[Image: /docs/static/attachments/23996892]
[#first-steps](
First Steps
)
[#parameters-and-characteristics](
Parameters and Characteristics
)
[#known-limitations-and-characteristics](
Known Limitations and Characteristics:
)
