# Engine Nodes

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/44959022
- Page ID: 44959022
- Breadcrumb: Editor Tools > Flow Graph > Flow Graph Node Reference > Engine Nodes
- Parent: Flow Graph Node Reference

## Content

##
LayerSwitch

Activate/Deactivate objects in the layer.

![Image](https://www.cryengine.com/docs/static/attachments/44959024)
'

**
Inputs
**

Port
 |
Type
 |
Description
 |

**
Layer
**
 |
String
 |
Name of the layer
 |

**
Hide
**
 |
Any
 |
Hides objects in the layer
 |

**
Unhide
**
 |
Any
 |
Shows objects in the layer
 |

**
EnableSerialization
**
 |
Any
 |
Enables objects in the layer
 |

**
DisableSerialization
**
 |
Any
 |
Disables objects in the layer
 |

**
Outputs
**

Port
 |
Type
 |
Description
 |

**
Hidden
**
 |
Any
 |
Triggered if hidden
 |

**
Unhidden
**
 |
Any
 |
Triggered if visible
 |

##
LayerSetSwitch

This node lets you change the visibility of multiple layers at once, allowing for better organization of layers that belong together, and simpler Flow Graph structures to perform such layer switches. Visibility of layers can optionally be limited to a given scope.

![Image](https://www.cryengine.com/docs/static/attachments/44959032)

**
Inputs
**

**
Port
**
 |
Type
 |
Description
 |

**
Set
**
 |
Void
 |
Trigger to perform the layer set switch.
 |

**
Layer Set Name
**

 |
String
 |
Allows the user to select, from a dropdown list, which layer visibility preset should be applied to that scope.
 |

**
Layer Set Scope Name
**

 |
String
 |
Allows the user to select, from a dropdown list, which layer visibility preset should be used to define the scope. If a scope is not applicable, leave this field empty.
 |

**
Serialize
**
 |
Int (as Boolean)
 |
Specifies whether calls to this node need to be serialized.
 |

**
Outputs
**

**
Port
**
 |
Type
 |
**
Description
**
 |

**
Done
**
 |
Void
 |
Triggers upon completion of the layer switch.
 |

**
Failed
**
 |
Void
 |
Triggers upon failure. This might occur, for instance, when the selected Layer Set cannot be found.
 |

##
OcclusionAreaSwitch

Used to switch the OcclusionArea on or off.

![Image](https://www.cryengine.com/docs/static/attachments/44959023)

**
Inputs
**

Port
 |
Type
 |
Description
 |

**
Activate
**
 |
Any
 |
Activates the OcclusionArea switch
 |

**
Deactivate
**
 |
Any
 |
Deactivates the
OcclusionArea
 switch
 |

##
PortalSwitch

Used to switch the portal on or off.

![Image](https://www.cryengine.com/docs/static/attachments/44959028)

**
Inputs
**

Port
 |
Type
 |
Description
 |

**
Activate
**
 |
Any
 |
Activates the portal switch
 |

**
Deactivate
**
 |
Any
 |
Deactivates the portal switch
 |

##
PrecacheArea

Precache area at a specified position.

![Image](https://www.cryengine.com/docs/static/attachments/44959027)

**
Inputs
**

Port
 |
Type
 |
Description
 |

**
Position
**
 |
Vec3
 |
Location of the area to be precached
 |

**
Timeout
**
 |
Float
 |
Timeout interval in seconds
 |

**
Activate
**
 |
Any
 |
Activates the node
 |

##
ShadowChacheParams

Used to specify the shadow cache parameters.

![Image](https://www.cryengine.com/docs/static/attachments/44959025)

##
Viewport

Gets current rendering viewport information.

![Image](https://www.cryengine.com/docs/static/attachments/44959026)

**
Inputs
**

Port
 |
Type
 |
Description
 |

**
Get
**
 |
Any
 |
Gets the current viewport information
 |

**
Outputs
**

Port
 |
Type
 |
Description
 |

**
x
**
 |
Integer
 |
Outputs the top left X position of the viewport
 |

**
y
**
 |
Integer
 |
Outputs the top left Y position of the viewport
 |

**
width
**
 |
Integer
 |
Outputs the width of the viewport
 |

**
height
**
 |
Integer
 |
Outputs the height of the viewport
 |

##
Deprecated Nodes

-
Engine:MaterialParam

-
Engine:OceanSwitch

-
Engine:PortalSwitch

-
Engine:PrecacheArea

-
Engine:SetObjectMaterial

-
Engine:SkyboxSwitch

-
Engine:Viewport
[LayerSwitch](#layerswitch)
[LayerSetSwitch](#layersetswitch)
[OcclusionAreaSwitch](#occlusionareaswitch)
[PortalSwitch](#portalswitch)
[PrecacheArea](#precachearea)
[ShadowChacheParams](#shadowchacheparams)
[Viewport](#viewport)
[Deprecated Nodes](#deprecated-nodes)
