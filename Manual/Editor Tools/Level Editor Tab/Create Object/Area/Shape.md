# Shape

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/36869902
- Page ID: 36869902
- Breadcrumb: Editor Tools > Level Editor Tab > Create Object > Area > Shape
- Parent: Area

## Content

##
Overview

This object is used to create a shape to which triggers, and other entities that should be enabled when the player enters or leaves the area shape, can be linked.

This shape can have any number of points; just double-click when finished shaping and that point will be the last one in the shape.

**
Parameters
**

 |
**
Descriptions
**

 |

**
Width
**

 |
Specifies how wide the entity is.

 |

**
Height
**

 |
Specifies how high the shape area should be, 0 being the infinite height.

 |

**
Inner Fade Distance
**

 |
This value, specified in meters, determines how far an ambiance sound can blend into the shape with higher priority.

 |

**
Area Id
**

 |
Sets up the ID of the area, so areas with another ID can overlap.

 |

**
Group Id
**

 |
Sets up the Group ID of the area, so areas with another group ID can overlap.

 |

**
Priority
**

 |
Defines the Priority so areas with a higher priority will be processed first.

 |

**
Closed
**

 |
Sets if the area should be closed or if it should be just a line.

 |

**
Display Filled
**

 |
Just for visibility in the editor this option defines if the area should be rendered as filled or not.

 |

**
Display Sound Info
**

 |
Enable to expand
[/docs/static/engines/cryengine-5/categories/23756816/pages/44964914](
Sound Obstruction
)
 options.

 |

**
Agent Height
**

 |
When Render Voxel Grid is enabled this determines the height, along the Y axis, of the grid cells rendered.

 |

**
Agent Width
**

 |
When Render Voxel Grid is enabled this determines the height, along the X axis, of the grid cells rendered.

 |

**
Render Voxel Grid
**

 |
If true, Voxel Grid will be rendered when helpers are enabled.

 |

**
Voxel Offset X
**

 |
Offset Voxel Grid on the X axis.

 |

**
Voxel Offset Y
**

 |
Offset Voxel Grid on the Y axis.

 |

When editing a shape or area, it is possible to snap a vertex to terrain or physicalized objects using
**
Ctrl + Shift + LMB
**
.

This is true for all Area objects, except Occluders.
