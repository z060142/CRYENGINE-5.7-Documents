# LocalGrids Component

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/56656236
- Page ID: 56656236
- Breadcrumb: Physics > Physics Features > LocalGrids Component
- Parent: Physics Features

## Content

The LocalGrid component provides a way to create a local simulation sub-space in the physical world. It allows simulating objects inside that space as if they were in a static room, even if the space is attached to a moving entity in the global world. Theoretically, simulation-wise such space is equivalent to the global space only if it moves linearly without acceleration (according to Galileo's relativity principle), and otherwise the acceleration is 'felt' in it as an external force (similar to gravity).

With the LocalGrid component, you can set a threshold for this acceleration. Values below this threshold are suppressed and not applied to the grid objects. The main advantage is that objects in such a quasi-static space are much more stable to simulate, and they can fall asleep when their velocities become close to local 0.

However, local grids can also be statically placed in the world in order to optimize broad-phase collision detection. For instance, a global grid can have rather large cells, optimized for relatively sparse, but ubiquitous vegetation, and a building with lots of objects inside it can have a local grid that's optimal for its interior (if it's multi-story, there can even be a separate grid for each floor). LocalGrids can be nested, if necessary.

##
How It Acts

The LocalGrid acts as the 'main entity physics', so it must be added as a sole physics component (i.e. it's mutually exclusive with rigidbody, ragdoll, particle, area, vehicle, and cloth). Internally, it implements a small subset of the physical entity interface functionality. LocalGrid's entity can then be attached as a child to another physicalized 'host' entity, for instance a rigidbody train carriage. Upon game (or ai/physics) start, objects that have their bounding box centers inside the grid's bounds will be automatically assigned to the grid. They will be returned to the global space upon exiting the mode.

It doesn't apply to the host entity, so typically a local grid will have at least a single entity for static interior collisions (global terrain and ocean don't 'exist' in local grids).

##
Inside the LocalGrid

Objects inside local grids can interact with objects in the outer grid (and vice versa) via portals. Also, ray traces that originate in one grid can leave it through a portal. Objects that have their bounding boxes overlap with a portal's
*
oriented
*
 bounding box can interact with objects from the grid on the other side of the portal. In order to set up a portal an entity with some physicalized geometry must be created and
*
linked
*
 to the corresponding LocalGrid entity (note that entity linking is not the same thing as parent/child attachment).

##
Example

A simple example might be a rigidbody component with static physics and a box collider. For consistent simulation, all possible exits from a grid's interior geometry must be covered by portals. It's ok if a portal is larger than the actual hole geometry – it just means that sometimes entities will do more collision checks than absolutely necessary. It's even possible to have portal geometry that's only used for portal raytracing by using ray collision flag in the geometry's surface type. For instance, the first geometry in a portal can be a crude box without ray collisions, and the second one can be a more specialized ray-colliding mesh.

Whenever an object touches a portal, it decides whether to register itself in inside or outside grid by checking if its center belongs to a special 'inside check' geometry. This should be a representation of the grid's interior (ideally as simple as possible). A physicalized entity with such geometry must be linked to a portal entity.

It's possible to have a single 'inside check' entity to be linked to several portals, and in general any number of inside check entities linked to any number of portals. If a portal isn't linked to any inside check geometry, it'll use its own geometry for containment check.

##
Setup

Below is a visualization of how a LocalGrid can be set up:

[Image: /docs/static/attachments/56656257]

*
Local Grid visualization
*

Image above: outer gray – host entity (such as a train carriage), yellow grid – LocalGrid entity, blue walls – static collision entities inside the grid, translucent red rectangles – portals, dashed outline – 'inside check' entity, red arrow – child->parent attachment, green arrow – entity linking
