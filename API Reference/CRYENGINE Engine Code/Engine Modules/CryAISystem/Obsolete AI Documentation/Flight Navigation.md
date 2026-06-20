# Flight Navigation

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/23306467
- Page ID: 23306467
- Breadcrumb: CRYENGINE Engine Code > Engine Modules > CryAISystem > Obsolete AI Documentation > Flight Navigation
- Parent: Obsolete AI Documentation

## Content

##
Overview

##
Current Situation

Historically the path finding and navigation in CryENGINE has been based on triangulated representation of the obstacles on the level. The obstacles can either be points or areas. In addition to that there is a general system to extend the navigation by creating the navigation graph by hand and encapsulating that into a navigation modifier. The system scales well from vast outdoor to tight indoor navigation for agents which move on ground.

For the game Crysis, the system was extended to include a Volume Navigation Region, which allows the AI entities to navigate in full closed 3D environment. The system is heavily biased towards swimming or flying type of navigation. The Volume Navigation Region is very computationally expensive and requires a long pre-processing phase.

##
Problem Description

The design requirements for the game Crysis introduced a wide range of air based vehicles, ranging from a small flying drone to a VTOL to massive flying Alien Ships. The Volume Navigation Region would be too heavy to use in large outdoor areas, and the original navigation system based on triangulation could not cope such task, as it assumes the navigating agent is moving on ground. None of the system also does not allow to take account the special requirements of the air combat.

##
Necessity

Flight navigation has some special requirements and optimizations which can be better described using a separate system. For example in contrast to the Volume Navigation Region, where movement in each dimension has to be taken care of, the Flight Navigation can assume that it is working under gravity, solving a lot of problems simply on a height field. Especially when working on algorithms to handle the air based combat strategy and tactics.

##
Solutions

Describe possible solutions.

##
Solution A

Create a system which extends the idea of the triangulation, basically describing the environment using layers of extruded triangles, or prisms. The obstacles would be sampled at certain heights, and the intersection would be added to the new triangulation layer.

This was the original idea, but was dropped early during the design phase.

##
Solution B

Create a system which is based on coarse height field representation of the terrain and the static obstacles over the terrain. The Volume Navigation would be used to allow to "carve out" space from the height field to allow the agents to under bridges or other obstacles.

This solution was dropped because it seemed overly complex one of the main concerns was path beautification/smoothing, interfacing the different navigation methods, and the extra calculations required for the Volume Navigation calculations.

##
Solution C

Variation of the Solution B without using the Volume navigation, but allow one level of subdivision to cope better with the surroundings of complex obstacles. Allow designer placed paths to cope with overhangs and other special environment features.

This solution was chosen to be prototyped. The simple layout of the data allows really fast calculations during pre-calculation and runtime. The additional pros were the ability to create simple path beautification algorithm, and possibility to derive tactical information (exposure, etc) from the data representation.

##
Solution D

Variation of solution C using voxel spans instead of the height field to allow automatic generation of the overhangs and other layered information.

This solution was chose as the final implementation. The solution C had some problems around the most complex objects, but otherwise the solution turned out to be very robust and simple.

##
Final Resolution

The Solution C was chosen to be implemented as a prototype. After the initial implementation the system maws chose to be extended with the additions in Solution D.

*Picture 1.
*
Left
*
: The original terrain.
*
Right
*
: The span height field that is build from the collision geometry.

##
Span Height Field

The core of the Flight Navigation system is the span height field representation of the environment, as illustrated in Picture 1. The height of each cell in the height field is calculated by taking the maximum terrain height and the maximum static obstacle height at the area of the cell. If required the cell can be subdivided into 4x4 sub-cells to get more accuracy in areas where it is needed.

The Solution D expands this algorithm by handling each cell as a span buffer instead of just one height value. The spans are calculated by sampling the minimum and maximum of each obstacle at the resolution of the subdivided cells, and combining the overlapping spans or spans that are too close to each other to be navigable.

Once the span height field is calculated a navigation graph node is created at each cell and span of the height field. The larger cells are connected in 8 directions to all neighbor cells, while the sub divided cells are only connected to the 4 neighbors in main directions. The visibility between neighbor spans is checked before linking.

**
Picture 2.
**

*
Left:
*
 the node arrangement from top on cells, and the links to neighbor nodes,
*
Right:
*
 the node placement from side, the nodes are place on top of the spans.

**
Note:
**
 Only the minimum and maximum of each object is sampled! If it is desired to navigate through a hole in an object, the object must consist of multiple objects.

**
Picture 3.
**

*
Left:
*
 the original path via all the visited nodes,
*
Right:
*
 the smoothed path.

##
Navigation

When an agent requests a path from the navigation system, first the start and end cells are found. The grid layout allows very simple and fast search to find the right cell, then the right span is found. Each span stores a pointer to the node that is associated with it. Using the start and end nodes, A* algorithm is used to find the correct path along the cells (Picture 3, left).

Usually the cost at each node is calculated based on the distance, making the most optimal routes. Depending on the behavior of the agent, the path finding purpose may be altered. For example the grid allows to calculate the exposure potential field, so that the A* will result most covered path. The type of the terrain or obstacle can also add extra const to the path. An example could be that certain unit could only fly 2 meters above rigid group. This would add extra cost if the obstacle at the cell would be vegetation.

##
Path Smoothing

A general assumption about flying agents is that they move smoothly. The path the path finder computes is very coarse and sharp. Another interesting problem the flying agents create is that most of the time the path direction at the start and end of the path has to be something specific. One reason can be that a continuity of the path has to be kept, or that the target of the path has to be reached at certain angle.

The basic navigation system based on the triangulation smooths the paths by cutting the corners of the path as far as possible. This does not guarantee that the path is smooth, it is rather more optimal.

To create truly fluent path, the Fly Navigation uses a simple particle system. First the initial path between the nodes is subdivided to provide enough particles for the calculation. Then each that is inside a span is moved to the closest surface outside the span.

When all the particles are laid out, 10 iterations of following algorithm is run to the points (the number of iterations is still to be tweaked). The smoothed path may deviate from the original cells, but transforming the height field by the path cost modifier prevents the particles leaking to non wanted areas (
*
Picture 4 and 5
*
).

**
Picture 4.
**
 The path smoothed by trying to minimize the distance and curvature of the particles.

**
Picture 5.
**
 The height field used for the collision detection of the particles scaled to prevent the particles to flow to the exposed area.

```

`
For each particle
{
   Prev = previous particle, Cur = current particle, Next = next particle
   Add forces to Cur, Next to minimize the distance between them
   Add forces to Prev, Next to minimize the curvature the at Cur
   Integrate Cur
   Damp the Cur velocity by factor of 0.4
}

For each particle

   Cur = current particle
   Collide Cur against the spans and cells

`

```

##
The Designer Created Paths

To over come the limitation how the objects are sampled when creating the spans, a method is provided to allow correct the mistakes the system failed to recognize.

The designers can create navigation modifiers in the editor which are carved out from the span height field. This allows great range of tuning, ranging from tunnels to simple objects with holes.

**
Picture 6.
**
 Designer has created path through a hole in an obstacle. The volume of the area the designer created is subtracted from the automatically generated height field.

[#current-situation](
Current Situation
)
[#problem-description](
Problem Description
)
[#necessity](
Necessity
)
[#solution-a](
Solution A
)
[#solution-b](
Solution B
)
[#solution-c](
Solution C
)
[#solution-d](
Solution D
)
[#span-height-field](
Span Height Field
)
