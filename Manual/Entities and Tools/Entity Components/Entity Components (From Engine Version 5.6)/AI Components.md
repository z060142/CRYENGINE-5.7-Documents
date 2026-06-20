# AI Components

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/44966037
- Page ID: 44966037
- Breadcrumb: Entities and Tools > Entity Components > Entity Components (From Engine Version 5.6) > AI Components
- Parent: Entity Components (From Engine Version 5.6)

## Content

##
AI Behavior Tree

Allows users to specify, from a dropdown menu, the Behavior Tree an Entity should run.

![Image](https://www.cryengine.com/docs/static/attachments/44966039)

*
Behavior Tree component
*

For Behavior Trees to appear within the dropdown menu however, they need to be saved under the

*
Scripts/AI/BehaviorTrees
*
 directory of your project.
Please refer to the

[Implementing The Behavior Tree in The Behavior Tree Editor](../../../Tutorials/AI/Tutorial%20-%20Getting%20Started%20With%20The%20Behavior%20Tree%20Editor/Implementing%20The%20Behavior%20Tree%20in%20The%20Behavior%20Tree%20Editor.md)

section for an example.

Setting
 |
Description
 |

**
Name
**
 |
Name of the behavior tree saved under the

*
Scripts/AI/BehaviorTrees
*
 directory of your project.
 |

##
AI Cover User

The Cover User component works together with movement system and provides an ability to use covers for the entity. Covers are user designed objects (Cover Surface) placed in Sandbox.

Setting
 |
Description
 |

**
Min Effective Cover Height
**
 |
Minimal effective height for the cover to be usable by the cover user and not to be compromised.
 |

**
In Cover Radius
**
 |
Radius used to block nearby cover locations when the agent is in cover.
 |

**
Distance To Cover
**
 |
How far the cover user can be from the exact cover location.
 |

**
Blacklist Time
**
 |
How long the compromised cover location will be considered as not valid for further cover queries.
 |

##
AI Faction

The Faction component stores the faction of the entity. Factions and their relations are defined in the Faction Map (
*
Scripts/AI/Factions.xml
*
).

Setting
 |
Description
 |

**
Faction
**
 |
Here you can choose the faction your entity belongs to.
 |

##
AI Listener

The Listener component registers the entity to AuditionMap and makes it able to perceive sound stimuli. The component is notified when any interesting stimuli is heard.

Property/Setting
 |
Description
 |

**
Factions To Listen To
**
 |
Only sound stimuli whose source entities belong to these factions will be processed.

 |

**
Listening Distance Scale
**

 |
An optional scale that can be applied to increase or reduce the listening distance.

 |

**
Ear Locations
**

 |
A collection of locations that will determine if the entity is within hearing range of sound stimuli. Can also be used to cast rays to these locations to determine sound obstruction fall-offs and such.

Setting
 |
Description
 |

**
Location type
**
 |
Pivot or Bone.
 |

**
Bone Name
**
 |
(if Location type is 'Bone') The name of the bone/joint from which to take the position
 |

**
Offset
**
 |
X, Y and Z coordinates for fixed offset from position.
 |

 |

**
Use Custom Filter
**

 |
Whether the custom condition filter should be used (Schematyc 'ListenerCustomFilter' signal).

 |

##
AI Navigation Agent

The Navigation Agent component gives the ability to navigate in space, finding paths to desired destinations, following them, and also trying to avoid collisions with other agents.

Property
 |
Description
 |

**
Navigation Agent Type
**
 |
Type of the navigation agent, specifying which NavMesh will be used by the agent (agent types are defined in
*
Scripts/AI/Navigation.xml
*
).
 |

**
Update Transformation
**
 |
When set to true, the Navigation Component automatically updates the entity's transformation by computed requested velocity (position and rotation). When false, the requested velocity should be passed to other systems.
 |

**
Movement
**

 |
Setting
 |
Description
 |

**
Normal Speed
**
 |
Normal entity speed.
 |

**
Min Speed
**
 |
Minimal output speed.
 |

**
Max Speed
**
 |
Maximal output speed.
 |

**
Max Acceleration
**
 |
Maximum acceleration of the entity.
 |

**
Max Deceleration
**
 |
Minimal acceleration of the entity.
 |

**
Look Ahead Distance
**
 |
How far the entity looks ahead along the path.
 |

**
Stop At End
**
 |
Aim to finish the path by reaching the end position (stationary) or simply overshoot.
 |

 |

**
Collision Avoidance
**

 |
Setting
 |
Description
 |

**
Type
**
 |

-
**
None
**

**
-
**
 A
gent doesn't contribute to collision avoidance.

-
**
Passive
**

**
-
**
 A
gent isn't trying to avoid obstacles but other agents consider him as an obstacle.

-
**
Active
**

**
-
**
 A
gent is actively trying to avoid obstacles.
 |

**
Radius
**
 |
Radius of the colliding agent.
 |

**
Height
**
 |
Height of the colliding agent.
 |

 |

**
Navigation Query Filter
**

 |
Setting
 |
Description
 |

**
Area Costs
**
 |

-
**
Default -
**
 Costs multipliers set per each of the area types. During path-finding, paths that lead through triangles with lower costs are preferred.
 |

**
Include Flags
**
 |
Specifies which flags are accessible. At least one of these flags must be set in triangle to be accepted.

-
**
All -
**
 Selects all flags listed in this section.

-
**
None -
**
 Deselects all listed flags.

-
**
Walkable -
**
 Created by the Navigation System by default, this flag is set upon all triangles in the NavMesh, when no special area type is specified within the NavMesh.

-
**
Inaccessible -
**
 Created by the Navigation System by default, this flag is set upon all triangles in the NavMesh that aren't accessible from any seed points placed in a map.
Custom flags must be defined in the
*
Navigation.xml
*
 file located under
*
ProjectFolder/Scripts/AI/.
*

 |

**
Exclude Flags
**
 |
Specifies which flags are forbidden. None of these flags must be set in triangle to be accepted.

-
**
All -
**
 Selects all flags listed in this section.

-
**
None -
**
 Deselects all listed flags.

-
**
Walkable -
**
 Created by the Navigation System by default, this flag is set upon all triangles in the NavMesh, when no special area type is specified within the NavMesh.

-
**
Inaccessible -
**
 Created by the Navigation System by default, this flag is set upon all triangles in the NavMesh that aren't accessible from any seed points placed in a map.
Custom flags must be defined in the
*
Navigation.xml
*
 file located under
*
ProjectFolder/Scripts/AI/.
*

 |

 |

##
AI Navigation Markup Shape

The Navigation Markup Shape component is used to create markup shapes, allowing to 'mark' triangles in the NavMesh with various annotations (area types and flags). Annotations can be set in the
*
Scripts/AI/Navigation.xml
*
 config file.

Property
 |
Description
 |

**
Ignore Geometry in MNM
**
 |
When activated, the Entity's geometry is ignored in NavMesh generation.
 |

**
Shapes
**
 |
Clicking on the dropdown menu icon next to the Shapes section will reveal a list including the following options:

Option
 |
Description
 |

**
Insert
**
 |
Adds a new Shape on top of the list.
 |

**
Add
**
 |
Adds a new Shape at the bottom of the list.
 |

**
Remove All
**
 |
Removes all the Shapes that has been previously added to the list.
 |

When a new Shape is added, following settings will appear on the Properties panel:

Setting
 |
Description
 |

**
Shapes Parameters
**
 |

-
**
Name -
**
Name of the shape. Needs to be unique among all defined shapes.

-
**
Position -
**
Position offset of the shape relative to the owning entity's pivot.

-
**
Rotation -
**
Rotation angles around axes in local space.

-
**
Area Type -
**
Area type that should be applied to NavMesh. All flags defined for the area type are applied as well.
 |

**
Affected Agent Types
**
 |
Defines what
[agent type](../../../AI%20and%20Navigation/AI%20Overview/Navigation%20(MNM)/Navigation%20Configuration.md)
's NavMeshes should be affected by the Markup Shape. There are currently two agent types that can be affected by the Markup Shape, namely
**
MediumSizedCharacters
**
and
**
VehicleMedium
**
.

-
**
Size -
**
Size of the rectangular shape in X, Y and Z coordinates.

-
**
Static -
**
Set to true if the markup shape's triangles' annotation doesn't need to be modified at runtime.

-
**
Expand By Agent Radius -
**

True if the marked area on NavMesh should be expanded by the agent radius.
 |

 |

##
AI Observable

The observable component registers the entity to VisionMap and makes it able to be "seen" by other entities that are registered as
**
Observers
**
.

Property
 |
Description
 |

**
Vision Map Type
**
 |
Combination of flags to identify the type of the observable.
 |

**
Observable Locations
**

 |
Positions, offset from the pivot or bones, that are checked for visibilty by Observers.

Setting
 |
Description
 |

**
Location type
**
 |
Defines if the location is set on
**
Pivot
**
 or
**
Bone
**
.
 |

**
Offset
**
 |
X, Y and Z coordinates for fixed offset from position.
 |

**
Bone Name
**
 |
Available when the Location type is set to
**
Bone
**
. Sets the name of the bone/joint from which to take the position.
 |

 |

##
AI Observer

The observer component registers the entity to VisionMap and makes it able to see other entities that are registered as Observables.

Setting
 |
Description
 |

**
Vision Map Type
**
 |
Combination of flags to identify the type of the observer.

 |

**
Vision

**
 |
Configuration of the vision sensor with which the entity can observe the world.

Setting
 |
Description
 |

**
Field of View
**
 |
Field of view in degrees.
 |

**
Sight Range
**
 |
The maximum sight distance from the eye point to an observable location on an entity.
 |

 |

**
Location
**
 |
Location of the eye sensor; offset from
**
Pivot
**
 or
**
Bone
**
 position).

Setting
 |
Description
 |

**
Location type
**
 |
Whether the eye sensor is attached to a
**
Bone
**
 or a
**
Pivot
**
.
 |

**
Offset
**
 |
Fixed offset from position.

 |

**
Bone Name
**
 |
When the Location type is
**
Bone
**
, defines the name of the bone/joint from which to take the position.
 |

 |

**
Vision Blocking
**
 |
Setting
 |
Description
 |

**
Blocked By Solids
**
 |
If enabled, vision ray-casts cannot pass through colliders that are part of solid objects that sometimes also denoted as hard cover.
 |

**
Blocked By Soft Cover
**
 |
If enabled, vision ray-casts cannot pass through colliders marked as soft cover. These are colliders that only block vision but you can still sit inside them. e.g. bushes, tall grasses, etc.
 |

 |

**
Types To Observe
**
 |
Only entities that belong to these vision map types will be processed for sight.

 |

**
Factions To Observe
**
 |
Only entities that belong to these factions will be processed for sight.

 |

**
Use Custom Filter
**
 |
Whether the custom condition filter should be used or not such as Schematyc's
**
ObserverCustomFilter
**
 signal.
 |

[AI Behavior Tree](#ai-behavior-tree)
[AI Cover User](#ai-cover-user)
[AI Faction](#ai-faction)
[AI Listener](#ai-listener)
[AI Navigation Agent](#ai-navigation-agent)
[AI Navigation Markup Shape](#ai-navigation-markup-shape)
[AI Observable](#ai-observable)
[AI Observer](#ai-observer)
