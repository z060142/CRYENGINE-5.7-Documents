# Physics Entities

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/29796943
- Page ID: 29796943
- Breadcrumb: Editor Tools > Level Editor Tab > Create Object > Legacy Entities > Physics Entities
- Parent: Legacy Entities

## Content

##
Overview

Physics entities are modifiers used to simulate physical events such as explosions, gravity fields or wind, or to physicalize objects such as cloth, breakable entities or ropes. Physical entities which are related to a body instead of an event need to be connected to an object in order to be selectable. If no objects is attached, entities can be selected in the editor by holding the space bar. On the other hand, events are represented by a selectable icon.

Physics entities can be found in
**
Create Object → Legacy Entities → Physics
**

##
AnimObject

An AnimObject extends the functionality of a BasicEntity by the ability of playing pre-baked animations and physicalizing parts of the object afterwards.

**
Property
**

 |
**
Description
**

 |

**
ActivatePhysicsDist
**

 |
Used for objects with pre-baked physical animations (requires Articulated to be on and ActivatePhysicsThreshold to be greater than 0).

Specifies the distance from the pivot after which parts automatically detach themselves from the animation and become fully physicalized. 0 disables distance-based detachment.

 |

**
ActivatePhysicsThreshold
**

 |
Greater than 0 values are used for objects with pre-baked physical animations (requires Articulated to be on).

Specifies the amount of force (in fractions of gravity) that needs to be exerted on a part for it to become detached and fully controlled by the physics.

 |

**
CanTriggerAreas
**

 |
See
[/docs/static/engines/cryengine-5/categories/23756816/pages/29796943#PhysicsEntities-BasicEntity](
)
.

 |

**
DmgFactorWhenCollidingAI
**

 |
See
[/docs/static/engines/cryengine-5/categories/23756816/pages/29796943#PhysicsEntities-BasicEntity](
)
.

 |

**
ExcludeCover
**

 |
See
[/docs/static/engines/cryengine-5/categories/23756816/pages/29796943#PhysicsEntities-BasicEntity](
)
.

 |

**
Faction
**

 |
See
[/docs/static/engines/cryengine-5/categories/23756816/pages/29796951](
Common Entity Parameters
)
.

 |

**
HeavyObject
**

 |
See
[/docs/static/engines/cryengine-5/categories/23756816/pages/29796951](
Common Entity Parameters
)
.

 |

**
InteractLargeObject
**

 |
See
[/docs/static/engines/cryengine-5/categories/23756816/pages/29796951](
Common Entity Parameters
)
.

 |

**
MissionCritical
**

 |
See
[/docs/static/engines/cryengine-5/categories/23756816/pages/29796943#PhysicsEntities-BasicEntity](
)
.

 |

**
Model
**

 |
Defines the model to be used.

 |

**
NoFriendlyFire
**

 |

 |

**
Pickable
**

 |
See
[/docs/static/engines/cryengine-5/categories/23756816/pages/29796951](
Common Entity Parameters
)
.

 |

**
SmartObjectClass
**

 |
See
[/docs/static/engines/cryengine-5/categories/23756816/pages/29796951](
Common Entity Parameters
)
.

 |

**
Usable
**

 |
See
[/docs/static/engines/cryengine-5/categories/23756816/pages/29796951](
Common Entity Parameters
)
.

 |

**
UseMessage
**

 |
See
[/docs/static/engines/cryengine-5/categories/23756816/pages/29796951](
Common Entity Parameters
)
.

 |

**
Animation
**

 |
 |

**
AlwaysUpdate
**

 |
 |

**
Animation
**

 |
Defines the animation to be played.

 |

**
Loop
**

 |
Defines whether the animation is looped.

 |

**
PhysicalizeAfterAnimation
**

 |
Defines whether the object is physicalized after the animation has reached its end.

 |

**
playerAnimationState
**

 |
**
Obsolete
**

 |

**
Playing
**

 |
If set, the animation will play immediately.

 |

**
Speed
**

 |
Playback speed of the animation sequence.

 |

Cinematic

 |

 |

**
OnDemandModelLoad
**

 |

 |

**
RenderAlways
**

 |

 |

Health

 |

 |

**
Invulnerable
**

 |
See
[/docs/static/engines/cryengine-3/categories/1114113/pages/1048651](
Common Entity Parameters
)
.

 |

**
MaxHealth
**

 |
See
[/docs/static/engines/cryengine-5/categories/23756816/pages/29796951](
Common Entity Parameters
)
.

 |

**
OnlyEnemyFire
**

 |
See
[/docs/static/engines/cryengine-5/categories/23756816/pages/29796951](
Common Entity Parameters
)
.

 |

MultiplayerOptions

 |

 |

**
Networked
**

 |
See
[/docs/static/engines/cryengine-5/categories/23756816/pages/29796951](
Common Entity Parameters
)
.

 |

**
Physics
**

 |
 |

**
Articulated
**

 |
Physicalizes the character as an articulated physical entity (i.e., with bendable joints).

 |

**
BulletCollisionEnabled
**

 |

 |

**
Density
**

 |
See
[/docs/static/engines/cryengine-5/categories/23756816/pages/29796943#PhysicsEntities-BasicEntity](
)
.

 |

**
Mass
**

 |
See
[/docs/static/engines/cryengine-5/categories/23756816/pages/29796943#PhysicsEntities-BasicEntity](
)
.

 |

**
Physicalize
**

 |
See
[/docs/static/engines/cryengine-5/categories/23756816/pages/29796943#PhysicsEntities-BasicEntity](
)
.

 |

**
PushableByPlayers
**

 |
See
[/docs/static/engines/cryengine-5/categories/23756816/pages/29796943#PhysicsEntities-BasicEntity](
)
.

 |

**
RigidBody
**

 |
See
[/docs/static/engines/cryengine-5/categories/23756816/pages/29796943#PhysicsEntities-BasicEntity](
)
.

 |

**
CollisionFiltering
**

 |
See
[/docs/static/engines/cryengine-3/categories/1638401/pages/5145585](
Collision Classes
)
 for more information.

 |

**
Rendering
**

 |

 |

**
WrinkleMap
**

 |

 |

##
BasicEntity

A BasicEntity provides the simplest way of controlling objects physically. Once a model has been set, several properties can be set, defining it's physical behavior. It is possible to specify either density or mass of the object. If one is specified, the other one must be set to a negative value (-1, or -0.01). Mass and density affect the way objects interact with other objects and float in the water (they sink if their density is more than that of the water). A zero-mass rigid body (with both mass and density 0) is a special case which means an "animated" rigid body (moved from outside the physics system).

The difference from a static entity is that the physics will be aware that this object is actually dynamic, although it cannot simulate it directly. Note that both values describe the same physical property. When you specify mass, density will be computed automatically and vice versa. The relationship mass = density x volume is used. These computations imply that the object is solid. If a box is used to model an empty crate, one can assume that its density is a weighted average between wood density and inside air density.

*
Example of a BasicEntity with a barrel model, set to half of the density of water.
*

##
Reference Values

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

**
Property
**

 |
**
Description
**

 |

**
CanTriggerAreas
**

 |
If true areas will trigger when this entity enters/exits them. Only applicable to AreaTriggers, ProximityTriggers will trigger regardless.

 |

**
DmgFactorWhenCollidingAI
**

 |
Multiplier applied when dealing damage to AI.

 |

**
ExcludeCover
**

 |
**
Deprecated
**

 |

**
Faction
**

 |
See
[/docs/static/engines/cryengine-5/categories/23756816/pages/29796951](
Common Entity Parameters
)
.

 |

**
HeavyObject
**

 |
See
[/docs/static/engines/cryengine-5/categories/23756816/pages/29796951](
Common Entity Parameters
)
.

 |

**
InteractLargeObject
**

 |
See
[/docs/static/engines/cryengine-5/categories/23756816/pages/29796951](
Common Entity Parameters
)
.

 |

**
MissionCritical
**

 |
If true, entity will not be hidden by explosions.

The threshold for hiding/removal is defined via the CVar g_ec_removeThreshold which is set to 20 by default.

If an explosion occurs and more than 20 entities are hit by it, it will keep 20 and hide the rest for better performance.

See GameRulesClientServer.cpp for more information.

 |

**
Model
**

 |
Defines the model to be used.

 |

**
Pickable
**

 |
See
[/docs/static/engines/cryengine-5/categories/23756816/pages/29796951](
Common Entity Parameters
)
.

 |

**
SmartObjectClass
**

 |
Can be used to define AI interaction capabilities on code-side.

 |

**
Usable
**

 |
See
[/docs/static/engines/cryengine-5/categories/23756816/pages/29796951](
Common Entity Parameters
)
.

 |

**
UseMessage
**

 |
See
[/docs/static/engines/cryengine-5/categories/23756816/pages/29796951](
Common Entity Parameters
)
.

 |

Health

 |

 |

**
Invulnerable
**

 |
See
[/docs/static/engines/cryengine-5/categories/23756816/pages/29796951](
Common Entity Parameters
)
.

 |

**
MaxHealth
**

 |
See
[/docs/static/engines/cryengine-5/categories/23756816/pages/29796951](
Common Entity Parameters
)
.

 |

**
OnlyEnemyFire
**

 |
See
[/docs/static/engines/cryengine-5/categories/23756816/pages/29796951](
Common Entity Parameters
)
.

 |

MultiplayerOptions

 |

 |

**
Networked
**

 |
See
[/docs/static/engines/cryengine-5/categories/23756816/pages/29796951](
Common Entity Parameters
)
.

 |

**
Physics
**

 |
 |

**
Density
**

 |
(= Volume / Mass) Density affects the way objects interact with other objects and float in the water (they sink if their density is more than that of the water).

Note that both density and mass can be overridden in the asset file.

 |

**
Mass
**

 |
(= Density * Volume) Mass is the weight of the object (the density of the object multiplied by its volume).

 |

**
Physicalize
**

 |
If false, the object will not be taken into account by physics.

 |

**
PushableByPlayers
**

 |
It true, the player will be able to push the object by walking/running into it.

 |

**
RigidBody
**

 |
False means a static entity, true - a simulated rigid body. Note that a rigid body can still behave like a static entity if it has mass 0 (set either explicitly or by unchecking RigidBodyActive).

The main difference between these rigid bodies and pure statics is that the physics system knows that they can be moved by some other means (such as the trackview) and expects them to do so.

This means that objects that are supposed to be externally animated should be mass-0 rigid bodies in order to interact properly with pure physicalized entities.

 |

**
CollisionFiltering
**

 |
See
[/docs/static/engines/cryengine-3/categories/1638401/pages/5145585](
Collision Classes
)
 for more information.

 |

##
BreakableObject

**
Property
**

 |
**
Description
**

 |

**
BreakableType
**

 |
 |

**
Density
**

 |
See
[/docs/static/engines/cryengine-5/categories/23756816/pages/29796943#PhysicsEntities-BasicEntity](
)
.

 |

**
Faction
**

 |
See
[/docs/static/engines/cryengine-5/categories/23756816/pages/29796951](
Common Entity Parameters
)
.

 |

**
Mass
**

 |
See
[/docs/static/engines/cryengine-5/categories/23756816/pages/29796943#PhysicsEntities-BasicEntity](
)
.

 |

**
Model
**

 |
The CGF model to use; if separate broken and unbroken models are used, this will be the unbroken model.

 |

**
Pickable
**

 |
See
[/docs/static/engines/cryengine-5/categories/23756816/pages/29796951](
Common Entity Parameters
)
.

 |

**
Resting
**

 |
See
[/docs/static/engines/cryengine-5/categories/23756816/pages/29796951](
Common Entity Parameters
)
.

 |

**
RigidBody
**

 |
Whether the original "Main" object is physicalized; if not, it's static.

 |

**
Usable
**

 |
See
[/docs/static/engines/cryengine-5/categories/23756816/pages/29796951](
Common Entity Parameters
)
.

 |

**
UseMessage
**

 |
See
[/docs/static/engines/cryengine-5/categories/23756816/pages/29796951](
Common Entity Parameters
)
.

 |

Health

 |

 |

**
Invulnerable
**

 |
See
[/docs/static/engines/cryengine-5/categories/23756816/pages/29796951](
Common Entity Parameters
)
.

 |

**
MaxHealth
**

 |
See
[/docs/static/engines/cryengine-5/categories/23756816/pages/29796951](
Common Entity Parameters
)
.

 |

**
OnlyEnemyFire
**

 |
See
[/docs/static/engines/cryengine-5/categories/23756816/pages/29796951](
Common Entity Parameters
)
.

 |

**
PhysicsBreakable
**

 |
 |

**
crack_weaken
**

 |
 |

**
max_bend_torque
**

 |
 |

**
max_pull_force
**

 |
 |

**
max_push_force
**

 |
 |

**
max_shift_force
**

 |
 |

**
max_twist_torque
**

 |
 |

**
GroundPlanes
**

 |
 |

**
PhysicsBouyancy
**

 |
 |

**
water_damping
**

 |
See
[/docs/static/engines/cryengine-5/categories/23756816/pages/29796943#PhysicsEntities-RigidBodyEx](
)
.

 |

**
water_density
**

 |
See
[/docs/static/engines/cryengine-5/categories/23756816/pages/29796943#PhysicsEntities-RigidBodyEx](
)
.

 |

**
water_resistance
**

 |
See
[/docs/static/engines/cryengine-5/categories/23756816/pages/29796943#PhysicsEntities-RigidBodyEx](
)
.

 |

**
PhysicsSimulation
**

 |
 |

**
damping
**

 |
(0..3) This sets the strength of damping on an object's movement. Most objects can work with 0 damping; if an object has trouble coming to rest, try values like 0.2-0.3.

Values of 0.5 and higher appear (visually) as overdamping. Note that when several objects are in contact, the highest damping is used for the entire group.

 |

**
max_time_step
**

 |
(0.005..0.1) This sets the maximum time step the entity is allowed to make (defaults to 0.02). Smaller time steps increase stability (can be required for long and thin objects, for instance), but are more expensive (generally, *0.5 time step is 2x more expensive).

Each time the physical world is requested to make a step, the objects that have their maxsteps smaller than the requested one, slice the big step into smaller chunks and perform several substeps. If several objects are in contact, the smallest max_time_step is used.

 |

**
sleep_speed
**

 |
(0.01..0.3) If the object's kinetic energy falls below some limit over several frames, the object is considered to be sleeping. This limit is proportional to the square of the sleep speed value.

A sleep speed of 0.01 loosely corresponds to the object's center moving at a velocity of the order of 1 cm/s.

 |

##
Cloth

The
**
Cloth
**
 entity represents a class of physicalized objects consisting of point masses with internal constraints. The most typical example is, of course, a sheet of cloth, but the topology of the object can theoretically be arbitrary. The ClothEntity's model file must be a cgf with its render geometry fully physicalized, and in such a way that there's no vertex duplication for rendering. Vertex duplication occurs when one vertex has different render parameters in different triangles it is used by, such as different texture coordinates or normals, and thus these cases should be avoided. Vertices that are supposed to be firmly attached to the environment should be marked by black vertex color, free vertices should remain white.

**
Sample setup files:
**

-
[/docs/static/attachments/1214108](
Cloth_Export_Test.ma
)

-
[/docs/static/attachments/1212600](
XSIClothSample.scn
)
It is important to use the "Use 32bit precision" checkbox in the exporter window to prevent any issues with the simulation of the cloth asset.

*
Sample of cloth bending around a barrel.
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
accuracy
**

 |
(0.001-1-...),
**
max_iters
**
 (1-100-...) The constraint solver stops when either all vertices are within the
**
accuracy
**
 range velocity-wise, or
**
max_iters
**
 iterations over the entire set were made.

Lower accuracy values and higher max_iters values make the solution more accurate but also more expensive (and in some cases excessive iterations can even hurt the perceived quality).

 |

**
air_resistance
**

 |
(0...10) Specifies how strongly the vertices are affected by the wind. Note that the default is 0, so when setting the wind property this one should also be changed.

 |

**
attach_radius
**

 |
If greater than 0, the entity will sample a sphere with this radius around its pivot and the cloth object will be attached to the geometry it collides with.

It is also possible to attach cloth to a specific entity explicitly, by creating an entity link to it named
**
AttachedTo
**
. Currently it's the only way to attach cloth to rope entities.
**
Update
**
: since 3.8.3 it's possible to physically attach cloth to other entities using standard entity linking.

 |

**
CollideWith...
**

 |
Enables/disables collision with different types of entities.

 |

**
collision_impulse_scale
**

 |
Scales the impulse that the cloth entity applies back to the objects it interacts with. Currently this feature is disabled.

 |

**
damping
**

 |
(0...1...10) Uniform damping applied to the points, in addition to any air or water resistance it might have.

 |

**
density
**

 |
Chiefly used to specify the behavior in the water (density greater than water density will make the cloth sink, less than that – float; water density is 1000 by default).

 |

**
explosion_scale
**

 |
Scales the impulse the cloth object receives from explosions.

 |

**
friction
**

 |
(0...2...10...) Friction of colliding points, currently independent of the material.

 |

**
hardness
**

 |
(1...20...100...) General stiffness of the constraints. Higher values will make the cloth stretch less, but can cause more oscillations or similar effects.

 |

**
impulse_scale
**

 |
(0...) Scales general impulses, such as bullet hits. Typically it's a good idea to prevent the cloth from receiving very strong impulses.

 |

**
mass
**

 |
Mass of the cloth object, which will be distributed among the vertices. Affects how much velocity the cloth receives from impulses and how much it affects other objects (the latter is currently turned off).

 |

**
mass_decay
**

 |
(0...1...10...) When 0, mass will be uniformly distributed among the vertices, values greater than 0 will make vertices lighter the further they are from attached points

(for instance, 1 will make the vertices on the edge 2 times lighter than the attached ones).

Raising this value will make it easier for the solver and will usually make the object settle faster (at the expense of toning down the swaying of lower parts.

 |

**
max_collision_impulse
**

 |
Limits the impulse applied back to the object the cloth collides with. Currently this feature is disabled.

 |

**
max_iters
**

 |
(1-100-...) See description of accuracy.

 |

**
max_time_step
**

 |
(...0.01...0.02...) Caps the maximum time step the object can make (larger world steps will be subdivided). Works the same way as the general max_time_step physical property.

 |

**
Model
**

 |
Cloth model to be simulated.

 |

**
RigidCore
**

 |

 |

**
sleep_speed
**

 |
(0...0.01...) The object will come to rest when all vertices fall below this velocity threshold. 0 will effectively make the object always simulated.

 |

**
thickness
**

 |
Cloth points are simulated as spheres with this radius. Increase to make sure that the cloth drapes over sharp edges, but very high values (comparable to the cell size and more) are not recommended.

 |

**
water_resistance
**

 |
Specifies how strongly the cloth points are affected by the water.

 |

**
wind_variance
**

 |
(0...1...) Sets the randomness of the wind, in fractions of unity

 |

**
gravity

**

 |
 |

**
XYZ
**

 |
Vector of gravity applied to the entity.

 |

**
MultiplayerOptions
**

 |

 |

**
Networked
**

 |
See
[/docs/static/engines/cryengine-5/categories/23756816/pages/29796951](
Common Entity Parameters
)
.

 |

**
wind

**

 |
 |

**
 XYZ
**

 |
Sets wind that acts in addition to any physical wind already present in the vicinity.

 |

**
wind_event

**

 |
 |

**
XYZ
**

 |
Vector of uniform wind, applied to the entity on a onWindOn event.

 |

##
Constraint

A constraint entity can create a physical constraint between two objects. The objects will be selected automatically during the first update, by sampling the environment in a sphere around the constraint object's world position with a specified radius. The "first" object (the one that will own the constraint information internally) is the lightest among the found objects, and the second is the second lightest (static objects are assumed to have infinite mass, so a static object is always heavier than a rigid body).

Constraints operate in a special "constraint frame". It can be set to be either the frame of the first constraint object (if UseEntityFrame is checked), or the frame of the constraint entity itself. In that frame, the constraint can operate either as a hinge around the x axis, or as a ball-in-a-socket around y and z axes (i.e., with the x axis as the socket's normal). If x limits are set to a valid range (max>min) and the yz limits are identical (such as both ends are 0), it is the former and if the yz limits are set and not x limits, it's the latter. If all limits are identical (remain 0, for instance), the constraint operates in a 3 degrees of freedom mode (i.e. doesn't constrain any rotational axes). If all limits are set, no axes are locked initially, but there are rotational limits for them.

In the following picture, Sandbags are hung with a constraint entity and dangle as a result.

**
Property
**

 |
**
Description
**

 |

**
ConstrainFully
**

 |

 |

**
ConstrainToLine
**

 |

 |

**
ConstrainToPlane
**

 |

 |

**
damping
**

 |
Sets the strength of the damping on an object's movement. Most objects can work with 0 damping; if an object has trouble coming to rest, try values like 0.2-0.3.

Values of 0.5 and higher appear visually as overdamping. Note that when several objects are in contact, the highest damping is used for the entire group.

 |

**
max_bend_torque
**

 |
The maximum bending torque (Currently it's only checked against for hinge constraints that have reached one of the x limits).

 |

**
max_pull_force
**

 |
Specifies the maximum stretching force the constraint can withstand.

 |

**
NoRotation
**

 |

 |

**
NoSelfCollisions
**

 |
Disables collision checks between the constrained objects (To be used if the constraint is enough to prevent inter-penetrations).

 |

**
radius
**

 |
Defines spherical area to search for attachable objects.

 |

**
UseEntityFrame
**

 |
Defines whether to use the first found object or the constraint itself as a constraint frame.

 |

**
Limits
**

 |
 |

**
x_max
**

 |
If set greater than x_min, the constraint will only rotate the object along its x-axis within the defined angle.

 |

**
x_min
**

 |
See x_max.

 |

**
yz_max
**

 |
If set greater than yz_min, the constraint will only rotate the object along its yz-axis within the defined angle.

 |

**
yz_min
**

 |
See yz_max.

 |

##
DeadBody

A DeadBody entity can ragdollize characters assigned to it. As soon as a character is intended not to act any more, but to only react passively on external impacts, as if it were dead, this physical entity provides the necessary model.

A typical usage is to create the entity as non-resting, simulate it in the editor, and then save the settled physics state. Note that the entity will not react to collisions with the player, bullets or explosions.

This functionality has been disabled on code-side due to restrictions of the German law (of course, it can be disabled if necessary).

*
A picture of a DeadBody Entity hit by a Barrel.
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
CollidesWithPlayers
**

 |
Defines whether the ragdoll of the entity may collide with the player (does not override the non-interactive ragdoll legal restriction)

 |

**
ExtraStiff
**

 |
Uses the main solver to apply stiffness instead of joint springs. It can handle a lot higher stiffness values, but the downside is that the same stiffness is applied to all joint axes, including locked and limited ones.

 |

**
lying_damping
**

 |
(0..1..10) Defines damping in the "lying" mode (which is when the ragdoll has enough contacts with the ground).

Note that this is an overall damping, and there also exist per-joint dampings, set based on the asset.

 |

**
Mass
**

 |
See
[/docs/static/engines/cryengine-5/categories/23756816/pages/29796943#PhysicsEntities-BasicEntity](
)
.

 |

**
MaxTimeStep
**

 |
As with other entities, decreasing it makes the simulation more stable, but makes this entity and all all entities it contacts with more expensive to simulate. Can be especially useful when higher stiffness is needed.

 |

**
Model
**

 |
Character model to be physicalized.

 |

**
NoFriendlyFire
**

 |
If set, the entity will not react on bullet impacts from friendly units.

 |

**
PoseAnim
**

 |
Allows to use the first frame of the specified animation as an initial pose

 |

**
PushableByPlayers
**

 |
See
[/docs/static/engines/cryengine-5/categories/23756816/pages/29796943#PhysicsEntities-BasicEntity](
)
 (does not override the non-interactive ragdoll legal restriction)

 |

**
Resting
**

 |
See
[/docs/static/engines/cryengine-5/categories/23756816/pages/29796951](
Common Entity Parameters
)
.

 |

**
SmartObjectClass
**

 |
See
[/docs/static/engines/cryengine-5/categories/23756816/pages/29796951](
Common Entity Parameters
)
.

 |

**
Stiffness
**

 |
Stiffness with which the ragdoll will try to maintain the original pose (set either in the model or from PoseAnim). For SDK character values around 2000 are practical. Higher values can lead to stability issues, which can be overcome by either decreasing MaxTimeStep (which makes it more expensive to simulate), or using ExtraStiff mode.

 |

**
Bouyancy
**

 |
 |

**
water_damping
**

 |
See
[/docs/static/engines/cryengine-5/categories/23756816/pages/29796943#PhysicsEntities-RigidBodyEx](
)
.

 |

**
water_density
**

 |
See
[/docs/static/engines/cryengine-5/categories/23756816/pages/29796943#PhysicsEntities-RigidBodyEx](
)
.

 |

**
water_resistance
**

 |
See
[/docs/static/engines/cryengine-5/categories/23756816/pages/29796943#PhysicsEntities-RigidBodyEx](
)
.

 |

**
TacticalInfo
**

 |

 |

**
LookupName
**

 |

 |

**
Scannable
**

 |

 |

##
Destroyable Object

**
Property
**

 |
**
Description
**

 |

**
AutoGenAIHidePts
**

 |
Defines whether or not the object is taken into account for automatic AI hide point generation.

 |

**
DamageTreshold
**

 |
Damage value counted down until the object will be destroyed.

 |

**
DestroyedSubObject
**

 |
Specifies the unbroken piece name; it should always be Remain.

 |

**
DmgFactorWhenCollidingAI
**

 |

 |

**
Explode
**

 |
Determines whether or not to generate an explosion event on destruction.

 |

**
Faction
**

 |
See
[/docs/static/engines/cryengine-5/categories/23756816/pages/29796951](
Common Entity Parameters
)
.

 |

**
InteractLargeObject
**

 |
See
[/docs/static/engines/cryengine-5/categories/23756816/pages/29796951](
Common Entity Parameters
)
.

 |

**
Model
**

 |
The CGF model to use; if separate broken and unbroken models are used, this will be the unbroken model.

 |

**
ModelDestroyed
**

 |
The CGF model for the broken pieces, if it is different from the main model; otherwise, it will be blank.

 |

**
ModelSubObject
**

 |
If the model has sub-models, this specifies the unbroken piece name; it should always be Main.

 |

**
OnlyAllowPlayerToFullyDestroyObject
**

 |

 |

**
Pickable
**

 |
See
[/docs/static/engines/cryengine-5/categories/23756816/pages/29796951](
Common Entity Parameters
)
.

 |

**
PlayerOnly
**

 |
Defines whether or not only the player can injure the object.

 |

**
SmartObjectClass
**

 |
See
[/docs/static/engines/cryengine-5/categories/23756816/pages/29796951](
Common Entity Parameters
)
.

 |

**
Usable
**

 |
See
[/docs/static/engines/cryengine-5/categories/23756816/pages/29796951](
Common Entity Parameters
)
.

 |

**
UseMessage
**

 |
See
[/docs/static/engines/cryengine-5/categories/23756816/pages/29796951](
Common Entity Parameters
)
.

 |

AutoAimTarget

 |

 |

**
AfterThrownTargetableTime
**

 |

 |

**
InnerRadiusVolumeFactor
**

 |

 |

**
MakeTargetableOnThrown
**

 |

 |

**
OuterRadiusVolumeFactor
**

 |

 |

**
SnapRadiusVolumeFactor
**

 |

 |

**
Breakage
**

 |
 |

**
ExplodeImpulse
**

 |
Strength of the outward impulse that needs to be applied to the pieces as they break apart.

Note: Any impulse from a projectile hit will also be applied to the pieces.

 |

**
LifeTime
**

 |
Average lifetime of particle (non-entity) pieces.

 |

**
SurfaceEffects
**

 |
Whether or not to spawn the secondary breakage and destroy particle effects.

 |

**
DamageMultiplier
**

 |
 |

**
Bullet
**

 |
Multiplies the amount of damage dealt by a bullet.

 |

**
Collision
**

 |
Multiplies the amount of damage dealt by a collision.

 |

**
ProjectileClass
**

 |

 |

**
Explosion
**

 |
 |

**
Damage
**

 |
Damage dealt to nearby objects.

 |

**
Delay
**

 |
Time to wait until the effect is played.

 |

**
EffectScale
**

 |
Size of the effect.

 |

**
MinPhysRadius
**

 |
Lower boundary of the explosion falloff effects for physical objects that are not players/AI.

 |

**
MinRadius
**

 |
Lower boundary of the explosion falloff effects for players/AI.

 |

**
ParticleEffect
**

 |
Name of the effect to be played if the object is destroyed.

 |

**
PhysRadius
**

 |
Upper boundary of the explosion falloff effects for physical objects that are not players/AI.

 |

**
Pressure
**

 |
Used for physical simulation of the explosion.

 |

**
Radius
**

 |
Upper boundary of the explosion falloff effects for players/AI.

 |

**
SoundRadius
**

 |

 |

**
DelayEffect
**

 |
 |

**
HasDelayEffect
**

 |
If selected, the delayed effect will be played.

 |

**
ParticleEffect
**

 |
An effect that may be played after a while.

 |

**
Params
**

 |

 |

**
vOffset
**

 |

 |

**
Rotation
**

 |

 |

**
Direction XYZ

**

 |
Unit vector defining the direction that the effect points to.

 |

**
vOffset XYZ

**

 |
Unit vector defining the direction that the effect points to.

 |

Health

 |

 |

**
Invulnerable
**

 |
See
[/docs/static/engines/cryengine-5/categories/23756816/pages/29796951](
Common Entity Parameters
)
.

 |

**
MaxHealth
**

 |
See
[/docs/static/engines/cryengine-5/categories/23756816/pages/29796951](
Common Entity Parameters
)
.

 |

**
OnlyEnemyFire
**

 |
See
[/docs/static/engines/cryengine-5/categories/23756816/pages/29796951](
Common Entity Parameters
)
.

 |

**
Physics
**

 |
 |

**
ActivateOnDamage
**

 |
Activates a rigid body with RigidBodyActive=0, when it receives damage.

 |

**
CanBreakOthers
**

 |
True if the entity can break jointed objects by colliding with them (provided they overcome the strength limit); BasicEntities have this flag off, unconditionally.

 |

**
Density
**

 |
See
[/docs/static/engines/cryengine-5/categories/23756816/pages/29796943#PhysicsEntities-BasicEntity](
)
.

 |

**
Mass
**

 |
See
[/docs/static/engines/cryengine-5/categories/23756816/pages/29796943#PhysicsEntities-BasicEntity](
)
.

 |

**
PushableByPlayers
**

 |
See
[/docs/static/engines/cryengine-5/categories/23756816/pages/29796943#PhysicsEntities-BasicEntity](
)
.

 |

**
RigidBody
**

 |
Whether the original "Main" object is physicalized; if not, it's static.

 |

**
RigidBodyActive
**

 |
Indicates that the object is a RigidBody, but initially it is immovable; instead, it can be later activated by an event.

 |

**
RigidBodyAfterDeath
**

 |
Whether the remaining "Remain" object is physicalized; if not, it's static.

 |

**
MP
**

 |

 |

**
DontSyncPos
**

 |

 |

**
Simulation
**

 |
 |

**
damping
**

 |
(0..3) This sets the strength of damping on an object's movement. Most objects can work with 0 damping; if an object has trouble coming to rest, try values like 0.2-0.3.

Values of 0.5 and higher appear (visually) as overdamping. Note that when several objects are in contact, the highest damping is used for the entire group.

 |

**
max_time_step
**

 |
(0.005..0.1) This sets the maximum time step the entity is allowed to make (defaults to 0.01). Smaller time steps increase stability (can be required for long and thin objects, for instance), but are more expensive.

Each time the physical world is requested to make a step, the objects that have their maxsteps smaller than the requested one, slice the big step into smaller chunks and perform several substeps.

If several objects are in contact, the smallest max_time_step is used.

 |

**
sleep_speed
**

 |
(0.01..0.3) If the object's kinetic energy falls below some limit over several frames, the object is considered to be sleeping. This limit is proportional to the square of the sleep speed value.

A sleep speed of 0.01 loosely corresponds to the object's center moving at a velocity of the order of 1 cm/s.

 |

**
Sounds
**

 |
 |

**
AISoundRadius
**

 |
Units to which distance the sounds can be heard.

 |

**
Alive
**

 |
Sound event to be played as long as the object is in the "Alive" state.

 |

**
Dead
**

 |
Sound event to be played as long as the object is in the "Dead" state.

 |

**
Dying
**

 |
Sound event to be played if the object is changed from the "Alive" state to the "Dead" state.

 |

**
Vulnerability
**

 |
Defines whether or not the object can be damaged by different object hits.

 |

**
TacticalInfo
**

 |

 |

**
LookupName
**

 |

 |

**
Scannable
**

 |

 |

Vulnerability

 |

 |

##
Explosion

An explosion entity encapsulates a particle effect into a logically controllable frame. It may be controlled via FlowGraph and has properties describing the physical impacts of an explosion.

**
Property
**

 |
**
Description
**

 |

**
Active
**

 |
If not set, the entity will not react.

 |

**
SmartObjectClass
**

 |
Class which can be used to control this object.

 |

**
Explosion
**

 |
 |

**
Damage
**

 |
Damage dealt to entities standing close to an explosion. The damage falls off linearly according to the radius of the explosion. Physical obstruction is taken into account as well.

 |

**
EffectScale
**

 |
Scaling factor, the effect is drawn with.

 |

**
MinPhysRadius
**

 |

 |

**
MinRadius
**

 |

 |

**
ParticleEffect
**

 |
Particle effect to be played.

 |

**
PhysRadius
**

 |

 |

**
Pressure
**

 |
Used for physical calculations.

 |

**
Radius
**

 |
Defines the size of the explosion.

 |

**
Direction XYZ

**

 |
Vector of the direction of the explosion.

 |

##
GravityBox

Property

 |
Description

 |

**
Active
**

 |

 |

**
FalloffInner
**

 |

 |

**
Uniform
**

 |

 |

**
BoxMax XYZ
**

 |

 |

**
BoxMin XYZ
**

 |

 |

**
Gravity
**

 |

 |

##
GravitySphere

A GravitySphere is a spherical area, which replaces the gravitational parameters of the environment. Objects reaching this area moved along the entities' Gravity vector and their own physical impact can be damped by a certain factor.

**
Property
**

 |
**
Description
**

 |

**
Active
**

 |
Defines whether the entity affects its environment.

 |

**
Damping
**

 |
Damps physical impact of entities inside the sphere.

 |

**
Ellipsoidal
**

 |

 |

**
FalloffInner
**

 |

 |

**
Radius
**

 |
Size of the sphere.

 |

**
Uniform
**

 |
 |

**
Gravity XYZ

**

 |
Vector of the gravity applied to objects within the sphere.

 |

##
GravityValve

A GravityValve entity performs an additional gravity into an upwards showing direction, relative to the entity.

**
Property
**

 |
**
Description
**

 |

**
Active
**

 |
Defines whether the entity affects its environment.

 |

**
Radius
**

 |
Size of the affected area.

 |

**
Spline
**

 |
 |

**
Strength
**

 |
Gravitational force.

 |

##
JointGen

See
[/docs/static/engines/cryengine-5/categories/23756816/pages/23308033](
Automatic Generation of Breakable Joints in Sandbox
)

##
PressurizedObject

A PressurizedObject represents an entity that can suddenly deal a high amount of damage and apply force to nearby objects if it is damaged by definable impacts like bullets.

**
Property
**

 |
**
Description
**

 |

**
AutoGenAIHidePts
**

 |
Defines whether object is taken into account for automatic AI hide point generation.

 |

**
CanBreakOthers
**

 |
True if the entity can break jointed objects by colliding with them (provided they overcome the strength limit). BasicEntities have this flag off unconditionally.

 |

**
DamageTreshold
**

 |
Damage value counted down until the object will be destroyed.

 |

**
Density
**

 |
See
[/docs/static/engines/cryengine-5/categories/23756816/pages/29796943#PhysicsEntities-BasicEntity](
)
.

 |

**
Mass
**

 |
See
[/docs/static/engines/cryengine-5/categories/23756816/pages/29796943#PhysicsEntities-BasicEntity](
)
.

 |

**
Model
**

 |
Defines the model to be used.

 |

**
Pickable
**

 |
See
[/docs/static/engines/cryengine-5/categories/23756816/pages/29796951](
Common Entity Parameters
)
.

 |

**
PlayerOnly
**

 |
Defines whether the object can be destroyed be the player only.

 |

**
PushableByPlayers
**

 |
See
[/docs/static/engines/cryengine-5/categories/23756816/pages/29796943#PhysicsEntities-BasicEntity](
)
.

 |

**
Resting
**

 |
See
[/docs/static/engines/cryengine-5/categories/23756816/pages/29796951](
Common Entity Parameters
)
.

 |

**
RigidBody
**

 |
See
[/docs/static/engines/cryengine-5/categories/23756816/pages/29796943#PhysicsEntities-BasicEntity](
)
.

 |

**
Usable
**

 |
See
[/docs/static/engines/cryengine-5/categories/23756816/pages/29796951](
Common Entity Parameters
)
.

 |

**
UseMessage
**

 |
See
[/docs/static/engines/cryengine-5/categories/23756816/pages/29796951](
Common Entity Parameters
)
.

 |

**
DamageMultipliers
**

 |
 |

**
Bullet
**

 |
Multiplies the amount of damage dealt by a bullet.

 |

**
Collision
**

 |
Multiplies the amount of damage dealt by a collision.

 |

**
Leak
**

 |
 |

**
Damage
**

 |
Defines how much damage is dealt to entities near the explosion of this object.

 |

**
DamageHitType
**

 |
The type of damage dealt defines how entities react on damage (fire, cold, electrical, acid, magical, divine and negative/positive energy).

 |

**
DamageRange
**

 |
Range, objects are affected in.

 |

**
ImpulseScale
**

 |
 |

**
MaxLeaks
**

 |
 |

**
Pressure
**

 |
 |

**
PressureDecay
**

 |
 |

**
PressureImpulse
**

 |
 |

**
Volume
**

 |
 |

**
VolumeDecay
**

 |
 |

**
Effect
**

 |
 |

**
AttachForm
**

 |
 |

**
AttachType
**

 |
 |

**
CountPerUnit
**

 |
 |

**
CountScale
**

 |
 |

**
Effect
**

 |
Name of the particle effect to be played if the object is destroyed.

 |

**
Prime
**

 |
 |

**
Scale
**

 |
Scale of the effect.

 |

**
SizePerUnit
**

 |
 |

**
SpawnPeriod
**

 |
 |

**
PhysicsBuoyancy
**

 |
 |

**
water_damping
**

 |
See
[/docs/static/engines/cryengine-5/categories/23756816/pages/29796943#PhysicsEntities-RigidBodyEx](
)
.

 |

**
water_density
**

 |
See
[/docs/static/engines/cryengine-5/categories/23756816/pages/29796943#PhysicsEntities-RigidBodyEx](
)
.

 |

**
water_resistance
**

 |
See
[/docs/static/engines/cryengine-5/categories/23756816/pages/29796943#PhysicsEntities-RigidBodyEx](
)
.

 |

**
PhysicsSimulation
**

 |
 |

**
damping
**

 |
(0..3) Sets the strength of the damping on an object's movement. Most objects can work with 0 damping; if an object has trouble coming to rest, try values like 0.2-0.3.

Values of 0.5 and higher appear visually as overdamping. Note that when several objects are in contact, the highest damping is used for the entire group.

 |

**
max_time_step
**

 |
(0.005..0.1) Sets the maximum time step the entity is allowed to make (defaults to 0.01). Smaller time steps increase stability (can be required for long and thin objects, for instance), but are more expensive.

Each time the physical world is requested to make a step, the objects that have their maxsteps smaller than the requested one slice the big step into smaller chunks and perform several substeps.

If several objects are in contact, the smallest max_time_step is used.

 |

**
sleep_speed
**

 |
(0.01..0.3) If the object's kinetic energy falls below some limit over several frames, the object is considered sleeping. This limit is proportional to the square of the sleep speed value.

A sleep speed of 0.01 loosely corresponds to the object's center moving at a velocity of the order of 1 cm/s.

 |

**
Vulnerability
**

 |
Defines whether the object can be damaged by a specific object.

 |

##
RigidBodyEx

The RigidBodyEx entity is an extension to the BasicEntity that reacts more realistically with other entities and water. The attached object can break other objects and has more options as to when and how to react.

The object may behave differently when underwater than above water, simulating leaking geometry.

A detailed description how to set up physicalized objects via RigidBodyEx can be found
**
[/docs/static/engines/cryengine-3/categories/1114113/pages/21267011](
H E R E
)
**
.

**
Property
**

 |
**
Description
**

 |

**
CanTriggerAreas
**

 |
See
[/docs/static/engines/cryengine-5/categories/23756816/pages/29796943#PhysicsEntities-BasicEntity](
)
.

 |

**
DamagesPlayerOnCollisionSP
**

 |

 |

**
DmgFactorWhenCollidingAI
**

 |
See
[/docs/static/engines/cryengine-5/categories/23756816/pages/29796943#PhysicsEntities-BasicEntity](
)
.

 |

**
ExcludeCover
**

 |
See
[/docs/static/engines/cryengine-5/categories/23756816/pages/29796943#PhysicsEntities-BasicEntity](
)
.

 |

**
Faction
**

 |
See
[/docs/static/engines/cryengine-5/categories/23756816/pages/29796951](
Common Entity Parameters
)
.

 |

**
HeavyObject
**

 |
See
[/docs/static/engines/cryengine-5/categories/23756816/pages/29796951](
Common Entity Parameters
)
.

 |

**
InteractLargeObject
**

 |
See
[/docs/static/engines/cryengine-5/categories/23756816/pages/29796951](
Common Entity Parameters
)
.

 |

**
MissionCritical
**

 |
See
[/docs/static/engines/cryengine-5/categories/23756816/pages/29796943#PhysicsEntities-BasicEntity](
)
.

 |

**
Model
**

 |
Defines the model to be used.

 |

**
Pickable
**

 |
See
[/docs/static/engines/cryengine-5/categories/23756816/pages/29796951](
Common Entity Parameters
)
.

 |

**
Serialize
**

 |
See
[/docs/static/engines/cryengine-5/categories/23756816/pages/29796951](
Common Entity Parameters
)
.

 |

**
SmartObjectClass
**

 |
See
[/docs/static/engines/cryengine-5/categories/23756816/pages/29796951](
Common Entity Parameters
)
.

 |

**
Usable
**

 |
See
[/docs/static/engines/cryengine-5/categories/23756816/pages/29796951](
Common Entity Parameters
)
.

 |

**
UseMessage
**

 |
See
[/docs/static/engines/cryengine-5/categories/23756816/pages/29796951](
Common Entity Parameters
)
.

 |

AI

 |

 |

**
UsedAsDynamicObstacle
**

 |
If true the entity will be treated as a dynamic obstacle by the AI pathfinding system.

 |

Health

 |

 |

**
Invulnerable
**

 |
See
[/docs/static/engines/cryengine-5/categories/23756816/pages/29796951](
Common Entity Parameters
)
.

 |

**
MaxHealth
**

 |
See
[/docs/static/engines/cryengine-5/categories/23756816/pages/29796951](
Common Entity Parameters
)
.

 |

**
OnlyEnemyFire
**

 |
See
[/docs/static/engines/cryengine-5/categories/23756816/pages/29796951](
Common Entity Parameters
)
.

 |

**
MultiplayerOptions
**

 |

 |

**
Networked
**

 |
See
[/docs/static/engines/cryengine-5/categories/23756816/pages/29796951](
Common Entity Parameters
)
.

 |

**
Physics
**

 |
 |

**
ActivateOnDamage
**

 |
Tells that an inactive rigid body (RigidBodyActive=0) should be activated on damage.

 |

**
CanBreakOthers
**

 |
See
[/docs/static/engines/cryengine-5/categories/23756816/pages/29796951](
Common Entity Parameters
)
.

 |

**
Density
**

 |
See
[/docs/static/engines/cryengine-5/categories/23756816/pages/29796943#PhysicsEntities-BasicEntity](
)
.

 |

**
Mass
**

 |
See
[/docs/static/engines/cryengine-5/categories/23756816/pages/29796943#PhysicsEntities-BasicEntity](
)
.

 |

**
Physicalize
**

 |
See
[/docs/static/engines/cryengine-5/categories/23756816/pages/29796943#PhysicsEntities-BasicEntity](
)
.

 |

**
PushableByPlayers
**

 |
See
[/docs/static/engines/cryengine-5/categories/23756816/pages/29796943#PhysicsEntities-BasicEntity](
)
.

 |

**
Resting
**

 |
See
[/docs/static/engines/cryengine-5/categories/23756816/pages/29796951](
Common Entity Parameters
)
.

 |

**
RigidBody
**

 |
See
[/docs/static/engines/cryengine-5/categories/23756816/pages/29796943#PhysicsEntities-BasicEntity](
)
.

 |

**
RigidBodyActive
**

 |
This property indicates that the object is a rigidbody, but initially it is immovable. Instead it can be activated by an event later.

 |

**
Buoyancy
**

 |
 |

**
water_damping
**

 |
A cheaper alternative/addition to water resistance (applies uniform damping when in water).

Sets the strength of the damping on an object's movement is soon as it is situated underwater. Most objects can work with 0 damping; if an object has trouble coming to rest, try values like 0.2-0.3.

Values of 0.5 and higher appear visually as overdamping. Note that when several objects are in contact, the highest damping is used for the entire group.

 |

**
water_density
**

 |
Can be used to override the default water density (1000). Lower values assume that the body is floating in the water that's less dense than it actually is, and thus it will sink easier.

(100..1000) This parameter could be used to specify that the object's physical geometry can leak. For instance, ground vehicles usually have quite large geometry volumes, but they are not waterproof, thus Archimedean force acting on them will be less than submerged_volume 1000 (with 1000 being the actual water density).

Decreasing per-object effective water density will allow such objects to sink (as they would in reality) while still having large-volume physical geometry.

Important note: if you are changing the default value (1000), it is highly recommended that you also change water_resistance in the same way (a rule of thumb might be to always keep them equal).

 |

**
water_resistance
**

 |
Can be used to override the default water resistance (1000). Sets how strongly the water affects the body (this applies to both water flow and neutral state).

(0..2000) Water resistance coefficient. If non-0, precise water resistance is calculated. Otherwise only water_damping (proportional to the submerged volume) is used to uniformly damp the movement. The former is somewhat slower, but not prohibitively, so it is advised to always set the water resistance.

Although water resistance is not too visible on a general object, setting it to a suitable value will prevent very light objects from jumping in the water, and water flow will affect things more realistically.

Note that water damping is used regardless of whether water resistance is 0, so it is better to set damping to 0 when resistance is turned on.

 |

**
CGFPropsOverride
**

 |

 |

**
CollisionFiltering
**

 |
See
[/docs/static/engines/cryengine-3/categories/1638401/pages/5145585](
Collision Classes
)
 for more information.

 |

**
ForeignData
**

 |

 |

**
Moving Platform
**

 |

 |

**
Simulation
**

 |
 |

**
damping
**

 |
(0..3) Sets the strength of the damping on an object's movement. Most objects can work with 0 damping; if an object has trouble coming to rest, try values like 0.2-0.3. Values of 0.5 and higher appear visually as overdamping.

Note that when several objects are in contact, the highest damping is used for the entire group.

 |

**
FixedDamping
**

 |
(true/false) When true, this object will force its damping to the entire colliding group (use it when you don't want a particular object being slowed by a highly damped entity, like a dead body).

 |

**
max_time_step
**

 |
(0.005..0.1) Sets the maximum time step the entity is allowed to make (defaults to 0.01). Smaller time steps increase stability (can be required for long and thin objects, for instance), but are more expensive.

Each time the physical world is requested to make a step, the objects that have their maxsteps smaller than the requested one slice the big step into smaller chunks and perform several substeps.

If several objects are in contact, the smallest max_time_step is used.

 |

**
sleep_speed
**

 |
(0.01..0.3) If the object's kinetic energy falls below some limit over several frames, the object is considered sleeping. This limit is proportional to the square of the sleep speed value.

A sleep speed of 0.01 loosely corresponds to the object's center moving at a velocity of the order of 1 cm/s.

 |

**
UseSimpleSolver
**

 |
**
Deprecated
**

 |

##
Wind

A wind entity is used to simulate wind in a local position. This should not be used to create the global wind in your level.

**
Property
**

 |
**
Description
**

 |

**
Fade Time
**

 |
The time the wind entity will use to fade between disabled and enabled states.

 |

**
Velocity XYZ

**

 |
This vector sets the direction and strength of the wind.

 |

##
WindArea

A WindArea simulates air moving with an arbitrary speed in a specific direction. It affects the flow direction of all objects and aero-form substances within the defined area, as well as vegetation bending depending on density and resistance values.

If no direction is set, the wind-source moves omni-directionally from the center of the WindArea.

In the following picture palm trees bend as a result of an omni-directional WindArea:

**
Property
**

 |
**
Description
**

 |

**
Active
**

 |
Defines whether wind is blowing or not.

 |

**
AirDensity
**

 |
Causes very light physicalised objects to experience a buoyancy force, if >0.

 |

**
AirResistance
**

 |
Causes physicalised objects moving through the air to slow down, if >0.

 |

**
Ellipsoidal
**

 |
Forces an ellipsoidal falloff.

 |

**
FalloffInner
**

 |
Distance after which the distance-based falloff begins.

 |

**
Speed
**

 |
Wind-speed in units per second.

 |

**
Dir XYZ

**

 |
Axis of normalized wind direction.

 |

**
Size XYZ

**

 |
Size of affected area.

 |

##
Useful Console Variables

**
p_draw_helpers
**

```

Same as p_draw_helpers_num, but encoded in letters
Usage [Entity_Types]_[Helper_Types] - [t|s|r|R|l|i|g|a|y|e]_[g|c|b|l|t(#)]
Entity Types:
t - show terrain
s - show static entities
r - show sleeping rigid bodies
R - show active rigid bodies
l - show living entities
i - show independent entities
g - show triggers
a - show areas
y - show rays in RayWorldIntersection
e - show explosion occlusion maps
Helper Types
g - show geometry
c - show contact points
b - show bounding boxes
l - show tetrahedra lattices for breakable objects
j - show structural joints (will force translucency on the main geometry)
t(#) - show bounding volume trees up to the level #
f(#) - only show geometries with this bit flag set (multiple f's stack)
Example: p_draw_helpers larRis_g - show geometry for static, sleeping, active, independent entities and areas

```

**
p_debug_joints
**

```

If set, breakable objects will log tensions at the weakest spots

```

##
Related Topics

[#animobject](
AnimObject
)
[#basicentity](
BasicEntity
)
[#breakableobject](
BreakableObject
)
[#cloth](
Cloth
)
[#constraint](
Constraint
)
[#deadbody](
DeadBody
)
[#destroyable-object](
Destroyable Object
)
[#explosion](
Explosion
)
[#gravitybox](
GravityBox
)
[#gravitysphere](
GravitySphere
)
[#gravityvalve](
GravityValve
)
[#jointgen](
JointGen
)
[#pressurizedobject](
PressurizedObject
)
[#rigidbodyex](
RigidBodyEx
)
[#wind](
Wind
)
[#windarea](
WindArea
)
[#useful-console-variables](
Useful Console Variables
)
[#related-topics](
Related Topics
)
