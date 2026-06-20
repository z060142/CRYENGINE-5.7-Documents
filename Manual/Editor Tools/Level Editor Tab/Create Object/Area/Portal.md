# Portal

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/36869900
- Page ID: 36869900
- Breadcrumb: Editor Tools > Level Editor Tab > Create Object > Area > Portal
- Parent: Area

## Content

##
Overview

With Portals holes can be cut inside the VisAreas to create an "entrance". Portals have to be smaller than the VisArea Shape but thick enough to protrude both the inside and outside of the VisArea, like a door.

Portals
can be enabled and disabled
 via FlowGraph and can have multiple Portals in one VisArea.

##
Properties

**
Property
**

 |
**
Description
**

 |

**
Height
**

 |
Specifies how high the portal is.

 |

**
Display Filled
**

 |
Just for visibility in the editor this option defines if the area should be rendered as filled or not.

 |

**
Affected By Sun
**

 |
Specifies if shadows from the world outside the visarea can travel inside.

 |

**
Ignore Sky Color
**

 |
If this option is turned off the ambient color (sky color in time of day window) is not used indoors.

 |

**
Ignore GI
**

 |
If true, Global Illumination won't be used inside this object.

 |

**
View Dist Ratio
**

 |
Specifies how far the visarea is rendered.

 |

**
Sky Only
**

 |
Ensures that only the skybox can be seen when looked outside the visarea.

If the terrain and the outside brushes are not rendered, the performance can be faster, meaning that this option should be used when it is appropriate.

 |

**
Ocean Is Visible
**

 |
Specifies if the ocean rendering should be visible inside the visarea.

 |

**
Ignore Outdoor AO
**

 |
Ignores the outdoor
Ambient Occlusion.

 |

##
Setting Up Portals

Portals are used to add a visual "entrance" into the
[Vis Area](Vis%20Area.md)
 and allows users to view and seamlessly transition in and out of a Vis Area.

-
Create the portal shape according to the size of the entrance.

-
Keep the size as small as possible (also the size of the portal can't be bigger then the Vis Area itself).
![Image](https://www.cryengine.com/docs/static/attachments/44969529)

-
The Portal has to be half inside the Vis Area (usingin the Top and Front viewports helps).
![Image](https://www.cryengine.com/docs/static/attachments/44969530)

##
Enabling and Disabling Portals via Flow Graph

In Flow Graph, a node to enable/disable portals can be found under
**
 Engine → PortalSwitch
**
.

-
If a door is available in the level, the Portal can be disabled when the door is closed to save resources.

-
The Portal itself cannot be assigned to this node; instead, the door
which is inside the portal
 should be assigned.

-
The state of the door can be checked and according to this enable and disable the Portal.
When editing a shape or area, it is possible to snap a vertex to terrain or physicalized objects using
**
Ctrl + Shift + LMB
**
.

This is true for all Area objects, except Occluders.

[Properties](#properties)
[Setting Up Portals](#setting-up-portals)
[Enabling and Disabling Portals via Flow Graph](#enabling-and-disabling-portals-via-flow-graph)
