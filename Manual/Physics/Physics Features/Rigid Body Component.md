# Rigid Body Component

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/56656025
- Page ID: 56656025
- Breadcrumb: Physics > Physics Features > Rigid Body Component
- Parent: Physics Features

## Content

RigidBody is the base physics component. It physicalizes an entity as either RigidBody or static, meaning that even if you need a static physical entity, you'd have to use a RigidBody component (an alternative is to use a brush, which can only be static).

An engine entity can only have a single physical entity, so components that set physical entity type (RigidBody, Ragdoll, PhysParticle, Vehicle, Cloth, PhysArea) are mutually exclusive. There are some "exceptions" to this, namely an alive skeleton, possibly with auxiliary rope physics, can be attached to an actor entity, but in this case the character system will be owning the extra physical entities.

##
Rigid Body & Other Components

The RigidBody component alone doesn't have any "physical presence" in the world; it needs parts for that. Physicalized parts can be physics collider components (box/capsule/cylinder/sphere) or static mesh components. In the latter case the corresponding static object (cgf) must have physics proxies. Physics proxy type is important for performance. Primitives (box/capsule/cylinder/sphere) are much more efficient, but meshes can also be a viable option (unless you are doing stress tests). Meshes don't have to be convex (convex ones can perform a bit better, but only marginally so).

"Primitive" doesn't necessarily mean a corresponding primitive component, as cgfs can have proxies consisting of one or several primitives. To see which proxies an object has you can enable physics helpers or click on the object with the Physics Tool.

##
Most Important Properties

Apart from shape, the other main property of a part is
**
Mass
**
, which is set per individual part (i.e. static mesh or primitive component).
**
Mass
**
 (found in the properties of the Geometry (i.e. Static Mesh or Collider) component) can be set either directly, or via Density, in which case it will be computed as [Density] * [geometry volume].

Both ways still set the same property (mass). Using Density can be more convenient when you know that the object is solid and know the density of its material (see sample table below), or to better control buoyancy behavior (separate section about that below). All values are set in SI, i.e. mass is in kg, density is in kg/m
3
.

Click to expand sample table...
**
Reference Density Values (in kg/m^3):
**

**
Material
**

 |
**
Density (kg/m3)
**

 |

**
Wood
**

 |
500-700

 |

**
Ice
**

 |
900

 |

**
Water
**

 |
1000

 |

**
Rubber
**

 |
1500

 |

**
Glass
**

 |
2600

 |

**
Iron
**

 |
7500

 |

**
Lead
**

 |
11400

 |

**
Gold
**

 |
19300

 |

**
Dry static friction reference table:
**

**
Material pair
**

 |
**
μ
**

 |

**
Aluminium/aluminium
**

 |
1.9

 |

**
Aluminium/steel
**

 |
0.61

 |

**
Brick/brick
**

 |
0.65

 |

**
Diamond/diamond
**

 |
0.1

 |

**
Glass/glass
**

 |
0.94

 |

**
Glass/metal
**

 |
0.5-0.7

 |

**
Gold/gold
**

 |
2.5-4.0

 |

**
Ice/ice
**

 |
0.1

 |

**
Rubber/concrete
**

 |
1.0-4.0

 |

**
Steel/steel
**

 |
0.74

 |

**
Wood/stone
**

 |
0.4

 |

**
Wood/wood
**

 |
0.25-0.5

 |

**
Stone/stone
**

 |
0.4-0.7

 |

Another important option is
**
"immovable" mass
**
. Immovable rigidbodies are "kinematic", i.e. the physics doesn't change their velocity and velocity is supposed to be set from outside. Using immovable rigidbodies instead of statics for externally animated objects is preferable, since in that case the physics knows that the object is moving with a specific velocity and can resolve collisions with other object better.

##
Important Properties Set Elsewhere

because different parts, and even different sections of the same part, can have different surface types, and thus different friction/elasticity, RigidBody's friction and elasticity (bounciness) are set via
[/docs/static/engines/cryengine-5/categories/23756816/pages/29448756](
surface types
)
. Surfacetype is set in cgf's material properties (via the Material Editor), or directly for primitive components. Each surfacetype has fixed friction and elasticity values, and friction and elasticity at a specific contact point are set to be the average of those values of the two involved surface types. Sample friction values can be taken from
[/docs/static/engines/cryengine-5/categories/23756816/pages/29796943#PhysicsEntities-ReferenceValues](
the same place as densities
)
.

##
RigidBody in Water

RigidBody's behavior in water (rivers, water volumes, global ocean) depends on its geometry and mass. Specifically, a RigidBody will float if its density (i.e. [mass] / [geometry's volume]) is less than that of the water (1000), and sink otherwise.

**
Resistance
**
 sets how strongly the water will try to force its own flow velocity onto the object (or simply slow it down if the flow is 0). Normally, water parameters are taken from the corresponding area, but it's possible to change them per RigidBody by setting the corresponding values in the
**
Buoyancy
**
 section.

This doesn't change the
*
object's
*
 density, instead it changes the density of the surrounding water, i.e. an object with density 100 can still sink if the surrounding water density is 99.

Also, this override is stored as a scale to the default 1000/1000 density/resistance values (e.g. if a RigidBody with 900 density in the buoyancy section is placed in a water volume with density 100, the latter will be assumed to be 90).

This can be useful to simulate non-watertight objects. For instance, a cage mesh can have a simple cube proxy, but in order for it to sink its density must be >1000, which can result in it having a very large mass.

Since non-watertight objects don't use their full volume to generate the displacement force, water density should be set to lower values on them. Normally objects don't need buoyancy damping (since resistance does the same thing more precisely), but in some cases (spheres in particular) it can be useful to damp the movement faster.

Typically water parameters (Density, Resistance, Fow, and Surface Place Orientation) are sampled once per entity, but it's possible to make that sampling per-part with "per part sampling" flag.

##
RigidBody in Air

Finally, everything that's been said about water also applies to air, except air density is 1 (by default) instead of 1000.

Air includes wind areas and global wind. For optimization purposes, the latter is turned off, i.e. effectively has 0 density, if the global wind vector is exactly (0,0,0). As another optimization, air and water resistance are only applied if they exceed certain thresholds, e.g. wind can move a lighter object, but will be completely skipped for a heavier one.

In addition to air resistance, free falling objects have an extra "freefall damping" (0.1 by default; currently only changeable from code).

##
Simulation Parameters

**
Maximum Time Step
**
 is a common property most physical entity types have. It makes sure the object never makes a time step longer than this value, and if game frame time is larger than this, it'll be split into several substeps. The maximum amount of substeps per object group is set in C++ via p_max_substeps. Smaller time steps can be needed for "degenerate" objects (very long/thin ones), or to generally improve simulation's fidelity, but they obviously make those objects (and objects they collide with) more expensive.

**
Sleep Speed
**
 sets velocity threshold after which the object will be put to sleep (deactivated).

**
Floor Damping
**
 is uniform damping applied to the object when it's not in freefall. Normally objects don't need it, but it can be useful in some cases, such as when a perfectly round object rolls over a perfect plane (it'll never stop without extra damping).

**
Maximum Rotational Velocity
**
 is a safety limit on rotational velocity (spinning), which can be changed if necessary.

##
CVars

RigidBody, vehicle, and ragdoll collisions are resolved in inter-colliding groups (also called "islands"). This works best when objects have masses of the same order of magnitude, but several solver tweaks can be made for different scenarios:

*
p_max_mc_iters
*
 – sets the iteration limit for the main solver (more iters = better quality, but slower).

*
p_mass_decay
*
 – enables dynamic mass adjustment in the solver to improve stability of tall stacks or piles (there's a feature page about it).

*
p_max_mc_mass_ratio
*
 – flags the island as needing an additional global matrix-based solver ('LCPCG') if lighter bodies (by at least this ratio) are trapped between heavier ones.

*
p_max_mc_vel
*
 – flags the island as needing LCPCG solver if objects with velocities higher than this are involved.

*
p_max_LCPCG_contacts
*
 – disables LCPCG for islands that have more contacts than this, even if they are flagged as needing LCPCG.

*
p_max_LCPCG_subiters/p_max_LCPCG_subiters_final
*
 – set the precision of the LCPCG solver.
