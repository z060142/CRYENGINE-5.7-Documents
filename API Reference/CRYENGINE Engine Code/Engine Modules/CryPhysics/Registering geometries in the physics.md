# Registering geometries in the physics

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/24282097
- Page ID: 24282097
- Breadcrumb: CRYENGINE Engine Code > Engine Modules > CryPhysics > Registering geometries in the physics
- Parent: CryPhysics

## Content

Geometries are first created as independent objects so that they can be used alone via the
`
IGeometry
`
 interface and then they can be
**
physicalized
**
 and added to physical entities. Geometry physicalization means computing physical properties (volume, inertia tensor) and storing them in a special internal structure. Pointers to these structures can then be passed to physical entities.

Each physicalized geometry has a reference counter which is set to 1 during creation, incremented every time the geometry is added to an entity and decremented every time the geometry is removed or the entity is deleted. When the counter reaches 0, the physical geometry structure is deleted and the corresponding IGeometry object is released (it is, however, refcounted as well). There are several geometry management functions, listed below. They are accessible via the geometry manager, which is a part of physical world. The pointer to it is returned by the
`
GetGeomManager
`
 function.

**
CreateMesh:
**
 Creates a triangular mesh object from a set of vertices and indices (3 indices per triangle) and returns the corresponding IGeometry pointer.

-
The engine uses triangle connectivity information in many places, so it is strongly recommended to have meshes closed and manifold. The function is able to recognize different vertices that represent the same point in space for connectivity calculations (there is no tolerance though, it checks only for exact duplicates). Open edges are ok only for geometries that will not be used as parts of dynamic physical entities and only if there will be little or no interaction with them.

-
For collision detection the function can create either an OBB, or a memory-optimized AABB, or a single box bounding volume tree (specified via  a corresponding flag). If both AABB and OBB flags are specified, the function selects the tree that fits the geometry most tightly. Since an OBB tree typically tighter, priority of AABBs can be boosted to save memory (also, AABB checks are slightly faster if the trees are equally tight). The engine can either copy the vertex/index data or use it directly from the pointers provided.

-
The
**
mesh_multycontact flags
**
 give some hints on whether multiple contacts are possible. Specifying that multiple contacts are unlikely (
*
mesh_multycontact0
*
) can improve performance a bit at the expense of potentially missing multiple contacts if they do occur (note that it does not necessarily mean they will be missed, it is a hint for the algorithm to use some optimizations more aggressively).
*
mesh_multycontact2
*
 disables this optimization and ..1 is a recommended default setting. Convex geometries are detected and some additional optimizations are used for them, although internally there is no separate class for convex objects.

-
Meshes can have per-face materials. Materials are used to look up friction, bounciness, and pierceability coefficients and can be queried by the game as a part of collision detection output.

-
`
CreateMesh
`
 function is able to detect meshes that represent primitives (with the specified tolerance) and returns primitive objects instead. In order to activate this detection, the corresponding flags should be specified. Note that primitives can't store materials. They can only have one in the physical geometry structure, so this detection is not used when the material array has more than one material index in it.
**
CreatePrimitive:
**
 Creates a primitive geometry explicitly. The corresponding primitive (cylinder, sphere, box, heightfield, or ray) structure should be filled and passed as a parameter, along with its ::type.

IGeometry interface can be used to manually check collisions between geometries via
**
Intersect
**
 function. It gives back detailed intersection results, which include all intersection regions with their borders and "unprojection" vectors. An unprojection vector tells how far one geometry can be moved along it to fully resolve the contact. It can either be set explicitly via geometry "velocity" or computed automatically based on intersection region. Continuous linear ("sweep") checks along a specified direction are also supported. In many cases, putting the moving geometry into its final position and "unprojecting" it back will give the same results as a sweep check (only faster), but it doesn't guarantee that it'll unproject to the first contact in complex cases (several manual iterations might be required).

When geometries are unprojected to a single contact point, the contact can optionally be extended to an area, by searching, matching, uniting, and intersecting neighboring features (polygon and polyline areas are supported).

For general meshes collisions are detected by finding some intersecting triangles using bounding trees, and then tracing the intersection border through the meshes using neighborhood (topology) information. Since 5.7, if the engine detects that both meshes are convex, and the query is non-continuous and doesn’t request a border, it uses a dedicated convex-vs-convex intersection check with penetration depth (the implementation is inspired by the GJK algorithm, but it had to be extended to handle penetration depth).

Another notable member of IGeometry interface is
**
Subtract
**
, which performs Boolean subtraction of meshes.

**
RegisterGeometry:
**
 Physicalizes an IGeometry object by computing its physical properties and storing them in an auxiliary structure. Material index (surfaceidx) can be stored in it; it will be used if the geometry itself does not have any materials specified (such as if it is a primitive).
`
AddRefGeometry
`
 and
`
UnregisterGeometry
`
 comprise a reference "sandwich" for it. Note that the latter does not delete the object until its reference count becomes 0.

Geometries and physicalized geometries can be serialized. This allows to save time by avoiding computing bounding volume trees. Normally that computation is not prohibitively slow, but serialization is still faster.
