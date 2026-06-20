# Road Tool

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/36867810
- Page ID: 36867810
- Breadcrumb: Editor Tools > Level Editor Tab > Create Object > Misc Objects > Road Tool
- Parent: Misc Objects

## Child Pages

- [Road Tool How-To](Road%20Tool/Road%20Tool%20How-To.md)
- [Road and Decal Sorting Priority](Road%20Tool/Road%20and%20Decal%20Sorting%20Priority.md)

## Content

##
Overview

The Road Tool uses a series of points to shape terrain and/or apply a texture on top of the terrain texture. Its use is not limited to designing roads in the traditional sense, but can also be used generally to shape terrain.

After the road is placed, the points in the road can be edited, and the terrain can be aligned to the height and curvature of the road.

Depending on the purpose of the road, it may be useful to first place a vehicle in the level so that the width, curvature, and slope of the road can be tested.

Be sure to also take a look at the
[Road and Decal Sorting Priority](Road%20Tool/Road%20and%20Decal%20Sorting%20Priority.md)
 article as it contains helpful information for road setup.

##
Modifying the Road's Properties

With the road selected, look on the entity's
**
Properties
**
 panel
 to see the road's properties. Here the width of the road and a number of other properties can be adjusted.

After adjusting the width of the road, make sure to re-align the heightmap in order to take into account the additional width of the road. Also note that increasing the width will stretch the texture if it is not designed for the specified width.

Changing the road parameters can make the road look even better.

##
Road Properties

Property

 |
Description

 |

**
Width
**

 |
The width of the road.

 |

**
Border Width
**

 |
Only used for the Align Height Map function, this will make a smooth edge on the terrain geometry if the
Border Width
 value is higher than the Width value.

 |

**
Erase Veg Width
**

 |
Specifies how far from the road the vegetation will be erased. This only applies to vegetation painted with the Vegetation Editor.

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
Smaller Step Size will increase the poly count used for the road surface, so for roads with smooth corners, use a lower value than the default 4.

 |

**
View Dist Radio
**

 |
Specifies how far the road entity will be rendered.

 |

**
Tile Length
**

 |
The Length of the Road Texture. Tweak this in combination with
Step Size
 to avoid stretching textures.

 |

##
Spline Properties

Property

 |
Description
 |

**
Width
**

 |
The width of the road.

 |

**
Border Width
**

 |
Only used for the Align Height Map function, this will make a smooth edge on the terrain geometry if the Border Width value is higher than the Width value.

 |

**
Erase Veg Width
**

 |
Specifies how far from the road the vegetation will be erased. This only applies to vegetation painted with the Vegetation Editor.

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
Smaller Step Size will increase the poly count used for the road surface, so for roads with smooth corners, use a lower value than the default 4.

 |

**
Sort Priority
**

 |
This setting can be used if a specific road should be drawn above another road. For more information, see
[Road and Decal Sorting Priority](Road%20Tool/Road%20and%20Decal%20Sorting%20Priority.md)
.

 |

**
Ignore Terrain Holes
**

 |
If set to true, this will allow the road texture to be rendered over terrain holes.

 |

**
Physicalize
**

 |
Defines whether the entity is affected by physics elements such as gravity.

 |

**
Operators
**

 |

-
**
Align Height Map
**
 - Aligns the height map with the road, raising and lowering the terrain to make sure the road rests on it.

-
**
Erase Vegetation
**
 - Erases the terrain around the road according to the Erase Veg Width parameter.
 |

[Modifying the Road's Properties](#modifying-the-roads-properties)
[Road Properties](#road-properties)
[Spline Properties](#spline-properties)
