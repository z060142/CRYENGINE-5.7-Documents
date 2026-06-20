# Physical Breakage Systems

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/24282347
- Page ID: 24282347
- Breadcrumb: CRYENGINE Engine Code > Engine Modules > CryPhysics > Physical Breakage Systems
- Parent: CryPhysics

## Content

There are 4 breakability systems in the engine: breakable joints, Boolean subtraction, procedural triangulation for flat objects, and cloth slicing. Another mesh-updating system is deformable objects.

##
Breakable Joints

A physical entity with multiple parts can have breakable joints between them (added with pe_params_structural_joint). Whenever an impulse is applied to some part (from any source - bullet hit, collision with other objects, explosions, even water interactions), it will be re-distributed internally among all entity's parts via the joints that connect them. Any joint that is required to transmit more impulse than its set maximum is considered broken and gets removed. After that new part connectivity is computed and parts that are no longer connected to the rest separate and form new rigid body entities. The rest of the engine gets notified about that using events (
*
EventPhysCreateEntityPart
*
,
*
EventPhysRemoveEntityParts
*
,
*
EventPhysRevealEntityParts
*
,
*
EventPhysJointBroken
*
), so that corresponding engine entities can be created and associated with the new physical entities. Parts with 0 masses will always remain in the original entity, thus in order to support breakability even static entities must also have parts with valid non-0 masses.

To optimize handling of breakable objects with large amounts of parts,
*
hierarchical breaking
*
 can be used. It allows breakable parts to have "parents" and remain hidden until any part inside said parent breaks off. Once this happens, the parent is removed and all its children become revealed. The children are hidden both in the physic and during the rendering, but any impulses applied to the parent are translated to the children and are redistributed through their joints.

In the assets, joints can be set up either manually, via helper nodes with special names and user-defined properties, or using
[automatic joint generation in the Sandbox](/docs/static/engines/cryengine-3/categories/1114113)

##
Boolean Subtraction

Mesh geometries in physical entity parts can be modified by subtracting other meshes ("explosion shapes" or "cut shapes") from them. If it happens, mesh connectivity is re-computed and isolated mesh pieces are moved to new rigid body entities. The system can work in tandem with breakable joints, meaning that joints can be attached to modifiable parts and follow their pieces.

Boolean deformation can be triggered by
[physical explosions](Physical%20Explosions.md)
 (in explosion parameters), however the most commonly used way is to mark parts with
*
geom_manually_breakable
*
 flag and let external systems (such as CryAction) request the break.

There's a pretty involved process of synchronizing the results of Boolean operations on physical meshes with their renderable counterparts, since the latter can have multiple vertices assigned to a single physical vertex (if they need to have different normals or texture coordinates, for instance). It's facilitated by
*
EventPhysUpdateMesh
*
 events and uses a log of physical mesh updates, replicating them on the render mesh inside a 3dEngine's
*
StaticObject
*
.

##
Planar Breaking

Pipeline-wise, planar breaking is similar to "external" Boolean breaking, i.e. CryAction listens to collision events and requests breakage when necessary. The affected geometry is then projected onto a planar randomly jittered grid (distance to the plane is preserved for each grid vertex, so the geometry can retain a certain amount of curvature), and islands of broken cells are formed randomly in the breakage area. The damaged mesh is reconstructed from the modified grid, and broken pieces are used in new entities, which can be physicalized as either rigid bodies or particles.

##
Cloth Slicing

Cloth objects (technically,
constraint-based soft bodies) support slicing by a triangle (via
*
pe_action_slice
*
). This doesn't just separate the affected triangles, but splits the mesh, creating new vertices along the slice's edge. This can cause parts of the cloth to become separated, however, they will still remain inside the same cloth object and will be simulated together with the remaining vertices (just without any forces pulling them back).

Slicing can also be applied to ropes. Unlike cloth though, they do not create new vertices at the exact slice point but separate at the nearest vertex. Also unlike cloth, a new rope entity gets created for the cut piece.

##
Deformable Objects

Related to breaking are
*
deformable objects
*
. Any physical entity part with a
triangle mesh in it
can act as a deformable "skeleton" for another part ("skinned" by this skeleton). In this case the part is removed from all direct interactions with the world and an internal constraint-based ("cloth-like") softbody is created for it. Then whenever a strong enough impulse is applied to the skinned part, softbody is activated, the impulse gets transferred to it, and it's simulated for one or more frames internally, independently from the rest of the world. During the simulation it can optionally have collisions with the world and other parts of the same entity. After that the deformed mesh is used to skin the "skinned" part, and an
*
EventPhysUpdateMesh
*
 is sent. The event listener then applies the skeleton to the render
*
StatObj
*
 associated with it.
