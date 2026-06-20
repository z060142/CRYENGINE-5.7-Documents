# Creating a NavMesh in Sandbox

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/24281122
- Page ID: 24281122
- Breadcrumb: CRYENGINE Engine Code > Engine Modules > CryAISystem > Multi-Layer Navigation Mesh (MNM) > Creating a NavMesh in Sandbox
- Parent: Multi-Layer Navigation Mesh (MNM)

## Content

##
Creating the NavMesh shape

To create a NavMesh shape, go to the RollupBar in Sandbox, and choose "AI" and then "Navigation Area":

[Image: /docs/static/attachments/24150057]

You can then draw the shape of the NavMesh like any other shape in Sandbox:

[Image: /docs/static/attachments/24150056]

##
Agent types

Depending on your game, you might have to support characters of different sizes that all need to traverse the same NavMesh. In order to accomplish this, you need to specify so called "Agents" and their properties in the
`
.\Scripts\AI\Navigation.xml
`
 file. It's possible to have multiple agent types defined, each representing a separate "layer" in the MNM. This example comes with 2 agent types:

[Image: /docs/static/attachments/24150067]

Attribute
 |
Type
 |
Default value
 |
Description
 |

voxelSize
 |
Vec3
 |
0.1, 0.1, 0.1
 |
Size of a single voxel in all 3 dimensions in meters. This defines the unit for all other attributes.
 |

radius
 |
uint16
 |
4
 |
Radius of the agent in voxels.
 |

height
 |
uint16
 |
18
 |
Height of the agent in voxels.
 |

climbableHeight
 |
uint16
 |
4
 |
Staircase height in voxels that the agent can walk up.
 |

climbableInclineGradient
 |
float
 |
1.0
 |
The steepness of a surface to still be climbable. The higher the value, the steeper a surface can be for traversing it.
 |

maxWaterDepth
 |
uint16
 |
0
 |
How far the generated nav mesh will reach below the water surface in voxels. Used to get the AI's feet wet, but prevents them from walking deeper and deeper into the water.
 |

```

`
<SmartObjectUserClasses>
     <class name="Human" />
</SmartObjectUserClasses>
`

```

The
`
<SmartObjectUserClasses>
`
 element is optional and can contain an arbitrary number of
`
<class>
`
 sub-elements. In the context of OffMesh-Links, they specify which SmartObjects an Agent can use to traverse otherwise disconnected areas.

Visualization of the NavMesh for a specific Agent type is done in Sandbox via
`
AI -> Debug Agent Type
`
.

##
Exclusion areas

In order to explicitly carve out regions of an NavMesh where no navigable space is desired, place another smaller NavMesh in the world and ensure the "Exclusion [x]" property of that NavMesh is checked:

[Image: /docs/static/attachments/24150064]

[Image: /docs/static/attachments/24150065]

[Image: /docs/static/attachments/24150066]
