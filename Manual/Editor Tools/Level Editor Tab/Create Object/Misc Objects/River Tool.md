# River Tool

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/36867737
- Page ID: 36867737
- Breadcrumb: Editor Tools > Level Editor Tab > Create Object > Misc Objects > River Tool
- Parent: Misc Objects

## Child Pages

- [River Tool How-To](River%20Tool/River%20Tool%20How-To.md)

## Content

##
Overview

The River Tool functions similarly to the Road Tool, but is preferable for setting up rivers as it contains several more, and very important, parameters needed for creating realistic looking rivers.

##
Uses for the River Tool

The River Tool is used to create rivers. The limitation of the River Tool is that it is essentially 2D. That means it is difficult to create rivers that flow down mountains and it is not possible to create waterfalls with the River Tool. To create rivers that run downhill, it is best to use a series of rivers along with intermittent waterfalls. The careful use of particles is particularly important for this to look convincing. It is possible to create a flat river, and then rotate it slightly along the
X
 axis, however, this should only be used to create a very slight incline.

For waterfalls, particle effects can be used, as well as a DCC tool to create a waterfall. To do this, a simple geometry that follows the terrain geometry is needed with a material that has the Illum shader assigned to it, set to be a decal, and with a texture map with alpha channel in the diffuse slot with oscillation animation on it.

![Image](https://www.cryengine.com/docs/static/attachments/44970936)

*
River in level
*

##
Adjusting the River's Parameters

In addition to the Shader Parameters mentioned earlier (which can be adjusted in the Material Editor), the River Tool entity also has parameters that can be adjusted through the River entity's Properties Panel.

In the Properties panel, several settings for the river can be changed, including how the material tiles, fog coloring, caustics settings and more.

Also, the Speed parameter of the river can be adjusted here. This is the speed at which physicalized objects will float down the river; it doesn't affect the look of the river itself. The visual speed of the river is controlled in with the
Flow Speed
 parameter in the Material Shader Params.

The properties for rivers are split into two types: River and Spline. River properties are specific to the river itself, whereas the Spline properties change the shape of the river.

##
River Properties

Property

 |
Description

 |

**
Width
**

 |
The Width of the river. (Usually set much wider than the actual river width, as the visual river width is defined by its surrounding terrain.

 |

**
Border Width
**

 |
Only used for the Align Height Map function, this will make a smooth edge on the terrain geometry if the
Border Width
 Value is higher than the
Width
 value.

 |

**
Step Size
**

 |
Sets the distance between each step along the spline. Smaller value will increase the poly count used for the river surface, but will also smooth out corners.

 |

**
Erase Veg Width
**

 |
Specifies how far from the river the vegetation will be erased. This only applies to vegetation painted with the Vegetation Editor.

 |

**
Erase Veg Width Var
**

 |
Sets in how far the distance of the Erase Veg Width will vary.

 |

**
Step Size
**

 |

Smaller Step Size will increase the poly count used for the river surface, so for rivers with smooth corners, use a lower value than the default 4.

 |

**
View Dist Radio
**

 |
Specifies how far the river entity will be rendered.

 |

**
Tile Length
**

 |
The length of the river texture. Tweak this in combination with Step Size to avoid stretching textures.

 |

**
Operators
**

 |

-
**
Align Height Map
**
 - Aligns the height map with the river, raising and lowering the terrain around it.

-
**
Erase Vegetation
**
 - Erases the terrain around the river according to the Erase Veg Width parameter.
 |

##
River Spline Properties

Property

 |
Description

 |

**
Depth
**

 |
Specifies the Depth of the River.

 |

**
Speed
**

 |
This is the speed at which physicalized objects will float down the river; it doesn't affect the look of the river itself. The visual speed of the river is controlled in with the
Flow Speed
 parameter in the Material Shader Params.

Use negative values to move in the opposite direction.

 |

**
Fog Density
**

 |
Specifies how dense the fog appears. A larger number will result in "thicker" fog.

 |

**
Fog Color
**

 |
Sets the fog color.

 |

**
Fog Color Multiplier
**

 |
Defines how bright the fog color is.

 |

**
Fog Color Affected By Sun
**

 |
If true, Sun Color value (See Environment Editor) will affect fog color of the river.

 |

**
Fog Shadowing
**

 |
If enabled, the surface of the river will receive shadows. You can control the shadow darkness, valid input 0-1.

*
r_FogShadowsWater
*
 needs to be set to '1' for this to function, which is currently only enabled on Very High Spec.

If you use Vol Fog Shadows in the Environment Editor, you lose control of shadow darkness (automatically set to full).

The benefit here is that the fog in the Water Volume will receive volumetric shadows. See below for comparisons.

 |

**
Cap Fog At Volume Depth
**

 |
If false, fog will continue to render below the specified Depth of the river.

 |

**
U Scale
**

 |
Sets the Texture tiling on the U Axis.

 |

**
V Scale
**

 |
Sets the Texture tiling on the V Axis.

 |

**
Caustics
**

 |
See
[Water Caustics](../../../../Post-processing/Water%20Caustics.md)
 for more information.

 |

**
Caustic Intensity
**

 |
See
[Water Caustics](../../../../Post-processing/Water%20Caustics.md)
 for more information.

 |

**
Caustic Tiling
**

 |
See
[Water Caustics](../../../../Post-processing/Water%20Caustics.md)
 for more information.

 |

**
Caustic Height
**

 |
See
[Water Caustics](../../../../Post-processing/Water%20Caustics.md)
 for more information.

 |

##
Additional settings

##
Shape Editing

The
**
 Edit
**
 button will allow modifying, adding (
**
CTRL + click
**
 on a line) or deleting (double-click on a point) of points on the line of the river shape.

##
Width

Sets the Width of the river per point along the spline.

##
Align Height Map

Will modify the terrain geometry based on the shape of the river and its border width parameter.

[Uses for the River Tool](#uses-for-the-river-tool)
[Adjusting the River's Parameters](#adjusting-the-rivers-parameters)
[River Properties](#river-properties)
[River Spline Properties](#river-spline-properties)
[Additional settings](#additional-settings)
