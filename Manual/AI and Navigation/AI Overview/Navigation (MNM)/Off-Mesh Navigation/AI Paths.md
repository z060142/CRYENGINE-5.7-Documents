# AI Paths

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/25534852
- Page ID: 25534852
- Breadcrumb: AI and Navigation > AI Overview > Navigation (MNM) > Off-Mesh Navigation > AI Paths
- Parent: Off-Mesh Navigation

## Content

![Image](https://www.cryengine.com/docs/static/attachments/29933213)

##
Overview

##
Sections

An AI path is an object which can be used to guide your AI along a specific route from point to point in your level.

AI paths can be used to affect all kinds of AI, including air and ground based vehicles.

[Sections](#sections)
[AIPath](#aipath)
[AIPath Properties](#aipath-properties)

##
AIPath

The AI path is a tool that is located in the Create Object window. It will allow for not only a single AI Entity to traverse across the navmesh, but also vehicles that an AI is driving.

Ensure you
**
Export to Engine
**
 or
**
Generate All AI
**
when using AI Paths, as these paths will not become available to the AI navigation system unless this step is done.

##
AIPath Properties

**
Property
**

 |
**
Description
**

 |

**
Road
**

 |
Defines if the path is to be used by vehicles as a preferred path.

 |

**
PathNavType
**

 |
Sets the AI navigation type of the path. Types of paths available:

-
Flight

-
Free 2D

-
Road

-
Smart Object

-
Triangular

-
Unset

-
Volume

-
Waypoint 3D Surface

-
Waypoint Human
 |

**
AnchorType
**

 |
Sets an AI behavior for any AI using the path.

 |

**
ValidatePath
**

 |
Used for 3D Volume paths only, checks and displays path validity in the editor.

 |

**
Width
**

 |
 |

**
Height
**

 |
 |

**
AreaId
**

 |
 |

**
GroupId
**

 |
Specifies the AI group that will be able to use this path.

 |

**
Priority
**

 |
 |

**
Closed
**

 |
Specifies if the path is a loop or not.

 |

**
DisplayFilled
**

 |
 |

**
DisplaySoundInfo
**

 |
 |

**
Agent_height

**

 |
 |

**
Agent_width
**

 |

 |

**
Render_voxel_grid
**

 |
 |

**
voxel_offset_x
**

 |

 |

**
voxel_offset_y
**

 |
