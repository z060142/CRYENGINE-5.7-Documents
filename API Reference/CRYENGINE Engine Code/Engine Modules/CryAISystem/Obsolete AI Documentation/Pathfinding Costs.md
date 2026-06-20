# Pathfinding Costs

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/23306457
- Page ID: 23306457
- Breadcrumb: CRYENGINE Engine Code > Engine Modules > CryAISystem > Obsolete AI Documentation > Pathfinding Costs
- Parent: Obsolete AI Documentation

## Content

### Overview

#### Current Situation

The pathfinding system uses A* to find minimal-cost paths. The cost of a path is given by the sum of the costs of the links that make up that path.

Currently the cost traversing a link in the navigation graph is normally simply the physical (3D) length of that link. However, the A* implementation makes it easy (i.e. simple code changes are needed to extend the current system) for the requester modify these distance-based costs. For example, the cost of traveling between two road nodes is scaled by a factor of 0.1 so that road-traveling agents have a strong preference for finding road-based paths.

In general the cost of a path link connecting two graph nodes should be determined by two things:

- The properties of the link, including how long it is.
- The properties of the pathfinding agent in relation to the properties of the link - for example a stealthy agent might evaluate a link passing through trees as having a lower cost-per-unit-length than one passing along a road. However, the same agent might reach a different conclusion if he was leading a convoy containing vehicles.

In general the cost of a link will be given by the product of these two factors - i.e. the link-length multiplied by a relative cost-per-unit-length. The latter is what needs to be determined.

#### Problem Description

We want to use the same navigation graph for different kinds of agents. This means that the link cost needs to be calculated at run-time by combining the inherent link properties with the agent properties.

The following properties need to be associated with each link:

Property | Description
--- | ---
**Link.Length** | Length of the link (in meters).
**Link.Resistance** | The links resistance to traversal. A road would be close to 0, off-road would be larger, water deep enough to require swimming might be close to 1.
**Link.Exposure** | How exposed the link is. Trees and dense vegetation would be close to 0, low vegetation would be larger, and a road/open space would be close to 1.
**Link.DeepWaterFraction** | Fraction of the link that contains deep water (e.g. > 1.5m).
**Link.DestinationDanger** | Additional "danger value" associated with the destination node - e.g. a dead body would be 1 (this can actually be stored in the destination node itself to save memory).

The following properties need to be associated with each agent pathfinder request:

Property | Description
--- | ---
**Agent.TriangularResistanceFactor** | The extra link cost factor for when the link is of type Triangular and its resistance is 1.
**Agent.WaypointResistanceFactor** | The extra link cost factor for when the link is of type Waypoint and its resistance is 1.
**Agent.RoadResistanceFactor** | The extra link cost factor for when the link is of type Road and its resistance is 1.

Similarly for other link types - note that if the link has different start/end node types the result will be obtained by averaging.

Property | Description
--- | ---
**Agent.SwimResistanceFactor** | The extra link cost factor for when the link deep water fraction is 1.
**Agent.ExposureFactor** | The extra link cost factor for when the link's exposure is 1.
**Agent.DangerCost** | The extra link cost for when the link danger value is 1.

The following properties need to be associated with each agent (normally set when the agent is created):

Property | Description
--- | ---
**Agent.CanTraverseTriangular** | True/false - if the agent can traverse triangular nodes.
**Agent.CantTraversseWaypoint** | True/false - if the agent can traverse triangular nodes.

Similarly for other node types:

Property | Description
--- | ---
**Agent.CanSwim** | True/false - indicates if the agent can swim.

All the link properties except for Link.DestinationDanger will be calculated when the triangulation is generated. Link.DestinationDanger will be calculated as the game runs (initially it is 0) - for example whenever a character dies each link going into the death node will have its DestinationdangerCost incremented by 1, This would mean that pathfinding by an agent with Agent.DangerCost = 100 would prefer paths up to 100m longer (assuming no other path cost differences) to avoid this death node. These link modifications will need to be serialized to support load/save.

In addition, extra costs can be calculated at run-time. For example, an extra cost associated with exposure could be added when the agent wishes to find a path that avoids the player, by doing raycasts in the A* callback that calculates costs.

There are two problems that need to be solved:

- How should the link properties be calculated?
- How should the link and agent properties be combined to give a numerical cost for traversing each graph link?

One additional problem is that the link properties will represent the average nature of the environment over the length of the link. If the region has not been triangulated reasonably finely then this may result in paths that are not particularly good. It may be necessary to add additional triangulation points to deal with this if it turns into a practical problem.

**Questions:** Should we differentiate between night/day (or fog/no fog)? That would involve splitting the link exposure into terms derived from physical cover and shadow cover - and I'm concerned about adding too much info to the link (there are a lot of links. Perhaps a solution is that at night maybe the requester would just be less likely to request a stealthy path, or the agent's ExposureFactor would be lower.

#### Necessity

In order that agents behaviors be believable they need to find paths that are appropriate for their current state. Sometimes these paths will be the most direct possible, and sometimes these will be longer paths, but ones that are more appropriate because they maximize use of roads, cover, or some other properties of the environment. The current system needs to be extended to support this.

### Solution

#### Calculation of link properties

The link resistance is only dependant on the actual type of nodes involved in the link, so may as well be stored in a lookup table. For example

**Node type** | **Resistance**
--- | ---
**Triangular-no-water** | 0.5
**Triangular-water** | 1.0
**Waypoint** | 0.6
**Road** | 0
**Flight/Volume** | 0 (maybe also an underwater version where the resistance would be higher)

When there is a link between nodes of different types averages can be used

The Link.Exposure value, stored in the link, needs to be determined by the environment properties sampled over the length of the link. For Triangular, Waypoint and Volume navigation regions this can be done by firing rays (using IPhysicalWorld::RayWorldIntersection and checking for HIT_COVER | HIT_SOFT_COVER with COVER_OBJECT_TYPES) from points along the link. It does not make sense to try to get a really accurate value, because in practice the beautified path will not follow the link directly.

#### Combining link and agent properties

If the agent cannot swim and the link is marked as containing deep water then it will be treated as impassable.

A factor (any value > 0) representing the extra costs associated with travel resistance and exposure will be calculated, and the total link cost will be set to

```
Cost = Link.DestinationDanger * Agent.DangerCost + (1 + Factor) * Link.Length
```

where

```
Factor = Agent.[Link-type]ResistanceFactor * Link. [Link-type]Resistance + Agent.ExposureFactor * Link.Exposure
```

Thus, in the absence of exposure/destination costs and assuming that road links have Link.Resistance {{ 0 and off-road links have Link.Resistance }} 0.5, then in order to make road travel ten times more attractive (e.g. if the agent is a car) than off-road, the agent could have Agent.TriangularResistanceFactor {{ (10 - 1) / 0.5 }} 18 and Agent.RoadResistanceFactor = 0.

If the agent is a human character that always moves at about the same speed whether or not it is on/off road, then it could have Agent.TriangularResistanceFactor {{ 0 and Agent.RoadResistanceFactor }} 0.

Assuming the agent can traverse deep water, if it is not affected by water (e.g. a hovercraft) it would set Agent.SwimResistanceFactor = 0.0. A human might set this factor to a value such as 3.0 so that it would take significant detours to avoid swimming across a river.
