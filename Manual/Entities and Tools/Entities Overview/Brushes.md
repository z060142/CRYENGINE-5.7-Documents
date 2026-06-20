# Brushes

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/27593400
- Page ID: 27593400
- Breadcrumb: Entities and Tools > Entities Overview > Brushes
- Parent: Entities Overview

## Content

![Image](https://www.cryengine.com/docs/static/attachments/29933295)

##
Overview

##
Sections

Brushes are solid objects that cannot be modified or moved dynamically during gameplay, except if they have a break-point specified in the asset file, for example a breakable wooden shack.

Typically brushes are static objects placed in the world. They are one of the cheapest rendered objects in the world as they don't have any of the entity or physics overhead of other objects.

A large percentage of the visual structures in your worlds will probably be constructed using brushes.

[Sections](#sections)
[Object Browser and Preview](#object-browser-and-preview)
[Brush Params](#brush-params)
[Debugging](#debugging)

##
Object Browser and Preview

The Browser pane shows the contents of the
`
<root>\GameSDK\Objects.pak
`
 file (or more precisely, the
`
<root>\GameSDK\Objects\*.*
`
 folder) and contains objects such as weapons, vehicles, and props.

The total number of files is listed at the bottom of the pane.

##
Filter

The Filter text box enables you to display objects with a selected keyword in the title. To use it, simply start typing into the filter box and the browser list will filter out any objects that don't match the current search.

The number of files matching the search will be displayed under the Filter text box.

##
Reload

Click
Reload
 when you add a new object to the library, when you change an object in the DCC package and want the geometry to be updated, or to make the filter take effect.

##
Object Preview

A preview of the selected object will be displayed in this section.

##
Brush Params

Once you have placed a Brush in the level, select it to view its properties.

Brush Params are a basic set of parameters shared by all Brushes.

Parameter

 |
Description

 |

Geometry

 |
This option specifies the geometry that needs to be used for the object.

 |

NoCollision

 |
Deprecated, see CollisionFiltering -
 Turn On/Off physical collision for the brush.

 |

CollisionFiltering Type

 |
See
[Collision Classes](../../../API%20Reference/CRYENGINE%20Engine%20Code/Engine%20Modules/CryPhysics/Collision%20Classes.md)
 for more information.

 |

CollisionFiltering Ignore

 |
See
[Collision Classes](../../../API%20Reference/CRYENGINE%20Engine%20Code/Engine%20Modules/CryPhysics/Collision%20Classes.md)
 for more information.

 |

OutdoorOnly

 |
When this option is set, the object will not be rendered when inside a visarea.

 |

CastShadowMaps

 |
When this option is set, the object will cast shadows onto other geometry/terrain/etc.

 |

RainOccluder

 |
Set the brush to occlude rain, this works in conjunction with Rain Entity.

If your level does contain rain, you should set this wisely, as there is a limit of 512 objects that can occlude at any given time.

 |

SupportSecondVisarea

 |
Normally, objects are considered to be in only one visarea.

This option allows them to be added to multiple visareas if their bounding box overlaps them, at the cost of some performance.

Without this option, some large objects may not be displayed when viewed through portals in certain situations.

 |

Hideable

 |
When this option is set, AI will use this object as a hiding spot, using the specified hide point type.

 |

LodRatio

 |
Defines how far from the current camera position, the different Level Of Detail models for the object are used.

 |

ViewDistRatio

 |
Defines how far from the current camera position, the object can be seen.

 |

MeshIntegrationType

 |
Deprecated

 |

NotTriangulate

 |
Deprecated, Pre-
[MNM](../../AI%20and%20Navigation/AI%20Overview/Navigation%20(MNM).md)
 - When this option is set, this object will not be considered part of the AI triangulation system.

 |

AIRadius

 |
Deprecated, Pre-
[MNM](../../AI%20and%20Navigation/AI%20Overview/Navigation%20(MNM).md)
 - This option specifies the radius that will be used for the object by the AI triangulation system.

 |

NoStaticDecals

 |
When this option is set, decals will not project onto the object.

 |

NoAmnbShadowCaster

 |
When this option is set, no ambient shadows will be cast.

 |

RecvWind

 |
When this option is set, the object will be affected by the level wind.

 |

Bending

 |
When RecvWind is checked and wind is setup in the level, this will define how much the brush is affected by wind.

 |

Occluder

 |
Used for the construction of a level occlusion mesh.

 |

DrawLast

 |
This function is exposed to give per-object control over alpha-sorting issues. An example can be seen below.

 |

##
DrawLast

The DrawLast checkbox gives designers per-object control over alpha-sorting issues such as particle effects in front of glass objects.

In the example seen below, the background glass dome panels use 50% opacity and are incorrectly rendered in front of the particle effect.

By setting DrawLast to true for the background dome object, the engine knows that any alpha based objects rendered between the player and itself should take ordering priority.

 |
 |

DrawLast False
 |
DrawLast True
 |

##
Debugging

There are various console commands which help debugging LOD's in Sandbox of in game mode.

**
e_Lods
**

```

Load and use LOD models for static geometry

```

**
e_LodMin
**

```

Min LOD for objects

```

**
e_LodMax
**

```

Max LOD for objects

```

**
e_DebugDraw
**

```

Draw helpers with information for each object (same number negative hides the text)
 1: Name of the used cgf, polycount, used LOD
 2: Color coded polygon count
 3: Show color coded LODs count, flashing color indicates no Lod
 4: Display object texture memory usage
 5: Display color coded number of render materials
 6: Display ambient color
 7: Display tri count, number of render materials, texture memory
 8: RenderWorld statistics (with view cones)
 9: RenderWorld statistics (with view cones without lights)
10: Render geometry with simple lines and triangles
11: Render occlusion geometry additionally
12: Render occlusion geometry without render geometry
13: Display occlusion amount (used during AO computations). Warning: can take a long time to calculate, depending on level size!
15: Display helpers
16: Display debug gun
17: Streaming info (buffer sizes)
18: Streaming info (required streaming speed)
19: Physics proxy triangle count
20: Display object instant texture memory usage
21: Display animated object distance to camera
22: Display object's current LOD vertex count

```
