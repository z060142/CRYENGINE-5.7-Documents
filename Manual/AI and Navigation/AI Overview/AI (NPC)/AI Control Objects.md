# AI Control Objects

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/25535410
- Page ID: 25535410
- Breadcrumb: AI and Navigation > AI Overview > AI (NPC) > AI Control Objects
- Parent: AI (NPC)

## Content

[Image: /docs/static/attachments/29933204]

##
Overview

AI control objects are used to control AI entities and their behaviors in the game world. They define a specific behavior for an AI with reference to its location.

In addition, AI control objects define navigation paths or an area for the AI on the terrain, including boundaries and forbidden areas. The objects can be used by AI actors to perform a specific action or event, such as an animation or behavior.

The AI control objects are mostly used with the flow graph scripting feature to design level concepts and scripted or triggered events.

##
Sections

[#sections](
Sections
)
[#aianchor](
AIAnchor
)
[#aihorizontalocclusionplane](
AIHorizontalOcclusionPlane
)
[#ainavigationmodifier-obsolete](
AINavigationModifier (Obsolete)
)
[#aipath](
AIPath
)
[#aiperceptionmodifier](
AIPerceptionModifier
)
[#aipoint-obsolete](
AIPoint (Obsolete)
)
[#aireinforcementspot](
AIReinforcementSpot
)
[#aishape](
AIShape
)
[#coversurface](
CoverSurface
)
[#navigationarea](
NavigationArea
)
[#navigationseedpoint](
NavigationSeedPoint
)
[#smartobject](
SmartObject
)
[#tagpoint](
Tagpoint
)
[#forbidden-area-obsolete](
Forbidden Area (Obsolete)
)
[#forbidden-boundary-obsolete](
Forbidden Boundary (Obsolete)
)

##
AIAnchor

An AI Anchor is a positional point object that can be used to define specific behaviors for an AI with reference to the location and/or direction of the anchor.

**
Property
**

 |
**
Description
**

 |

**
AnchorType
**

 |
Used to affect AI behavior. A type must be chosen from the browse list when clicking within the anchor type box.

The function of a type depends on what a specific AI behavior requires (i.e. SNIPER_SPOT: the AI sniper finds this anchor nearby and goes there to camp).

 |

**
Enabled
**

 |
Specifies if this point is turned on or off.

 |

**
GroupId
**

 |
Specifies the AI group that will be able to use this anchor.

 |

**
Radius
**

 |
When set, a radius in meters around the anchor is used, and can serve various purposes dependent on the anchor type (i.e. the AI finds a SNIPER_SPOT within its radius).

 |

**
SmartObjectClass
**

 |
When set, the anchor becomes a Smart Object, which will interact with other SOs according to SO system rules.

 |

In general, Smart Objects are a more complex resource for the game engine to process, so where it is possible use
**
AnchorType
**
 objects.

##
AIHorizontalOcclusionPlane

AI above and below an AI Horizontal Occlusion Plane will not be able to see through it. It can be used for example, to restrict an AI on a high ledge from being able to see below the ledge.

**
Property
**

 |
**
Description
**

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
The height of the area

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
Specifies the AI group that will be able to use this Occlusion Plane

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
Should be set to closed

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

 |

##
AINavigationModifier (Obsolete)

Obsolete
See
[/docs/static/engines/cryengine-3/categories/1114113/pages/1048583](
Multi-Layer Navigation Areas
)
 for more information.
The AINavigationModifier is used to alter the navigation setup of a level for special navigational setup, such as internal areas, flight navigation, and water navigation.

In certain situations, it is used in conjunction with other AI objects such as overlapping with forbidden areas for internal sections of buildings, or with AI points for internal navigation.

**
Property
**

 |
**
Description
**

 |

**
NavType
**

 |
Sets the navigation type for the area, for example flight will generate navigation for air based AI, and Human Waypoint will be used for internal waypoint areas for human AI.

 |

**
WayPointConnections
**

 |
When Human Waypoint is set, this ensures that the waypoint links are auto-generated.

 |

**
NodeAutoConnectDistance
**

 |
The distance at which a point must be to be auto connected with other points when generating navigation.

 |

**
Calculate3DNav
**

 |
When turned off, data will not be generated for Volume modifiers.

 |

**
ThreeDNavVolumeRadius
**

 |
The radius of the sphere volumes used in 3d navigation areas. The smaller the radius, the more accurate the representation of the environment is.

 |

**
ExtraLinkCostFactor
**

 |
Increases the cost of the links in the area, making it a less preferable choice for AI navigation. When this value is high, AI will have a higher chance to take an alternative route to their destination.

 |

**
TriangulationSize
**

 |
Specifies the size of the navigational triangles used to create dynamic object navigation.

 |

**
VehiclesInHumanNav
**

 |
Affects the pass radius of links, if set to true - will make the radius bigger.

 |

**
LightLevel
**

 |
Affects AI's ability to see (including sight range and speed of detection).

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
The height of the area.

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
Specifies if the area is a closed loop or not. Navigation Modifier should always be closed.

 |

**
ObstructRoof
**

 |
 |

**
ObstructFloor
**

 |
 |

**
DisplayFilled
**

 |
When checked, all closed sides of the area are filled with color.

 |

##
AIPath

An AI path is an object which can be used to guide your AI along a specific route from point to point in your level.

AI paths can be used to affect all kinds of AI, including air and ground based vehicles.

Ensure you
**
Export to Engine
**
 or
**
Generate All AI
**
when using AI Paths, as these paths will not become available to the AI navigation system unless this step is done.

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
Defines if the path is to be used by vehicles as a preferred path

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
Sets an AI behavior for any AI using the path

 |

**
ValidatePath
**

 |
Used for 3D Volume paths only, checks and displays path validity in the editor

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
Specifies the AI group that will be able to use this path

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
Specifies if the path is a loop or not

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

 |

##
AIPerceptionModifier

Control AI perception

Property
 |
Description
 |

**
ReductionPerMetre
**
 |

 |

**
ReductionMax
**
 |

 |

**
Height
**
 |

 |

**
Closed
**
 |

 |

**
DisplayFilled
**
 |

 |

##
AIPoint (Obsolete)

Obsolete
See
[/docs/static/engines/cryengine-3/categories/1114113/pages/1048583](
Multi-Layer Navigation Areas
)
 for more information.
An AI Point is an object used within a Navigation Modifier, which is to generate points for the AI to navigate between.

**
Property
**
 |
**
Description
**
 |

**
Type
**
 |
 |

**
Waypoint
**

 |
Sets the AI Point type to waypoint so it can be used for navigation around the nav area

 |

**
Hide
**

 |
Sets the AI Point type so AI can use it to hide

 |

**
Sec Hide
**

 |
Sets the AI Point type so that AI can use it as a secondary, less preferred point to hide

 |

**
Entry/Exit
**

 |
Sets the AI Point type so that AI can use it to enter and exit a nav area from this point to terrain

 |

**
Exit-Only
**

 |
Sets the AI Point type so that AI can use it to exit a nav area from this point to terrain

 |

Nav Type
 |
 |

**
Human
**

 |
Sets the navigation type to be compatible with human based characters

 |

**
3D Surface
**

 |
Used for navigating 3D (i.e. vertical, upside-down, etc) surfaces

 |

AIPoint Parameters
 |
 |

**
Removable
**

 |
Points with this flag can be disabled by using ISYSEVENT_DISABLEMODIFYER flowgraph event

 |

**
Regen Links
**

 |
Regenerates the waypoint links for the area

 |

Linked Waypoints
 |
 |

**
Pick
**

 |
Allows the user to pick a second waypoint to create a permanent AI link

 |

**
Pick Impass
**

 |
Allows the user to pick a second waypoint to create a perminant non-passable link

 |

**
Select
**

 |
Selects the currently highlighted link in the linked waypoints box

 |

**
Remove
**

 |
Removes the currently highlighted waypoint links

 |

**
Remove all
**

 |
Removes all waypoint links from the AI Point

 |

**
Remove all in area
**

 |
Removes all waypoint links in the nav area

 |

##
AIReinforcementSpot

Defines a point at which any relevant AI can use to trigger their reinforcement behavior.

**
Property
**

 |
**
Description
**

 |

**
AvoidWhenTargetInRadius
**

 |
When the target is within this radius from the point, it will not attempt to use the point

 |

**
Enabled
**

 |
Specifies if this point is turned on or off

 |

**
GroupBodyCount
**

 |
When set to greater than 0, the reinforcement call can be performed if the number of deaths in the group is less than the defined number

 |

**
groupid
**

 |
Specifies the AI group that will be able to use this point

 |

**
radius
**

 |
AI within this radius will react to the point

 |

**
ReinforcementType
**

 |
The behavior which the AI will use when they activate the point

 |

**
WhenAllAlerted
**

 |
The reinforcement call can be performed if all the AIs in the group are alerted (alertness yellow or more)

 |

**
WhenInCombat
**

 |
The reinforcement call can be performed if all the AIs are in combat status (alertness red)

 |

##
AIShape

An AI shape is an object which can be used to define an area which AI will use for combat and will search for anchors within.

**
Property
**

 |
**
Description
**

 |

**
AnchorType
**

 |
Affects AI behaviors in the same way as the anchors do

The main usage is to check if a point (AI position, target position, etc) is inside a shape of a given AnchorType, in the same way as checking the proximity to an anchor of a given type

 |

**
LightLevel
**

 |
Affects AI's ability to see (including sight range and speed of detection)

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
The height of the area

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
Specifies the AI group that will be able to use this Shape

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
Specifies if the path is a loop or not

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

 |

##
CoverSurface

Cover surfaces can be used to allow the AI to take cover in combat situations. Cover surfaces can be found in
**
 RollupBar -> AI -> CoverSurface
**
.

To create a valid cover surface, drag it close to nearby solid geometry:

If it's too far away from solid geometry or not properly rotated to face geometry, it can easily become invalid:

Property

 |
Description

 |

**
Sampler
**

 |

 |

**
Limit Left
**

 |
The generated cover path to the left side of the cover surface object will be limited to this length

 |

**
Limit Right
**

 |
The generated cover path to the right side of the cover surface object will be limited to this length

 |

**
Limit Depth
**

 |

 |

**
Limit Height
**

 |
The resulting height of all cover surfaces will be limited to this value

 |

**
Sample Width
**

 |

 |

**
Sample Height
**

 |

 |

**
Max Start Height
**

 |

 |

**
Simplification Threshold
**

 |

 |

 |
 |

Limit Right = 2.35
 |
Limit Right = 4.75
 |

 |
 |

Limit Height = 0.7
 |
Limit Height = 1.6
 |

##
NavigationArea

See
[/docs/static/engines/cryengine-3/categories/1114113/pages/1048583](
Multi-Layer Navigation Areas
)
 for more information.

##
NavigationSeedPoint

See
[/docs/static/engines/cryengine-3/categories/1114113/pages/1048583](
Multi-Layer Navigation Areas
)
 for more information.

##
SmartObject

An AI Anchor is a point or collection of points which can be used by AI to perform a specific action or event, such as an animation or behavior.

Certain smart objects can have special geometry assigned to them, to assist with object placement.

*
A smart object.
*

*
A smart object with an additional placement guide.
*

**
Property
**

 |
**
Description
**

 |

**
SmartObjectClass
**

 |
Specifies the smart object logical ruleset which will be used by this object

 |

##
Tagpoint

An AI Tagpoint is an object used to define a location, used in AI scripting.

An AI Tagpoint does not have any object-specific parameters.

##
Forbidden Area (Obsolete)

Obsolete
See
[/docs/static/engines/cryengine-3/categories/1114113/pages/1048583](
Multi-Layer Navigation Areas
)
 for more information.
A forbidden area a shape type object, which is projected onto the terrain, defining areas in the level in which AI will not go into and will try and avoid.

AI Navigation Modifiers can be used in conjunction with Forbidden Areas to allow AI access to them when required.

**
Property
**

 |
**
Description
**

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
Specifies if the area is a closed loop or not. Forbidden areas should be closed

 |

**
ObstructRoof
**

 |
 |

**
ObstructFloor
**

 |
 |

**
DisplayFilled
**

 |
When checked, all closed sides of the area are filled with color.

 |

##
Forbidden Boundary (Obsolete)

Obsolete
See
[/docs/static/engines/cryengine-3/categories/1114113/pages/1048583](
Multi-Layer Navigation Areas
)
 for more information.
A forbidden boundary is a shape type object, which can be used to define borders in your level which AI will not cross over. Unlike a Forbidden Area, an AI character will not try and leave the area inside a forbidden boundary.

**
Property
**

 |
**
Description
**

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
Specifies the AI group that will be affected by this boundary

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
Specifies if the area is a closed loop or not

 |

**
ObstructRoof
**

 |
 |

**
ObstructFloor
**

 |
 |

**
DisplayFilled
**

 |
When checked, all closed sides of the area are filled with color

 |
