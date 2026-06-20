# Physical Explosions

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/24282320
- Page ID: 24282320
- Breadcrumb: CRYENGINE Engine Code > Engine Modules > CryPhysics > Physical Explosions
- Parent: CryPhysics

## Content

The function
`
SimulateExplosion
`
 is used to simulate explosions in the physical world. The main effect of explosions inside the physics system are impulses that are added to the affected objects (as a consequence, explosions can also cause
[/docs/static/engines/cryengine-5/categories/23756813/pages/24282347](
physical breakage
)
). Explosion's impulse is calculated by integrating impulsive pressure over the affected geometries/entity parts. Impulsive pressure has a falloff proportional to
*
1/distance
2
*
. If
*
distance
*
 is smaller than
*
rmin
*
, it is clamped to
*
rmin
*
.
*
impulsivePressureAtR
*
 is the impulsive pressure at distance
*
r
*
.

`
SimulateExplosion
`
 can optionally build an occlusion cubemap to find entities occluded from the explosion (if cubemap linear resolution is set in
*
nOccRes
*
). First static entities are drawn into the cubemap and then dynamic entities (of the types specified in
*
iTypes
*
) are tested vs. this map (thus, dynamic entities never occlude each other).
*
nOccRes
*
 can have the special value -1 that tells the function to reuse the cubemap from the last call and process only dynamic entities that were not processed during that call. This is useful when the code that creates the explosion decides to spawn new entities afterwards, such as debris or dead bodies, and wants to add explosion impulses to them without recomputing the occlusion map. Due to the projective nature of the cubemap, small objects very close to the epicenter can occlude more than they normally would. To ignore those objects
a small virtual cube can be subtracted from the environment when building the occlusion map (the cube's size is set in rminOcc). The downside is that it can make explosions go through thin walls, so some compromise value should be used.
*
nGrow
*
specifies the number of occlusion cubemap cells (in one dimension) that dynamic entities are inflated with. This can help explosions to reach around corners in a controllable way.

After a call to
`
SimulateExplosion
`
, the physics system can return how much a particular entity was affected by it (based on cubemap information) via a call to
`
IsAffectedByExplosion
`
 (returns fraction that was affected, 0..1). This function just performs a lookup into a stored entity list; the cubemap is not recomputed.

Explosion epicenter that's used for generating impulses can be made different from the one used to build the cubemap. One example of using this is creating explosions slightly below the ground to make things go up instead of just sidewards. Note that only parts with
*
geom_colltype_explosion
*
 are affected by explosions.
