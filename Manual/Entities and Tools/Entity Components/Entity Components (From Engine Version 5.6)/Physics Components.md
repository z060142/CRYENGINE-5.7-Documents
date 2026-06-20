# Physics Components

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/51347735
- Page ID: 51347735
- Breadcrumb: Entities and Tools > Entity Components > Entity Components (From Engine Version 5.6) > Physics Components
- Parent: Entity Components (From Engine Version 5.6)

## Content

##
Area

Creates a physical area with a primitive shape with custom gravity/buoyancy settings.

Property
 |
Description
 |

**
Area Settings
**
 |

-
**
Type -
**
The shape of the physics area. This can be a box, sphere, cylinder, capsule, geometry or spline.
 |

**
Shape properties
**
 |
Based on the Type selection, following options might appear on the panel:

Setting
 |
Description
 |

**
Radius
**
 |
Radius of the shape (for sphere, capsule, and cylinder).
 |

**
Height
**
 |
Height of the cylindrical portion of the shape (for cylinders and capsules).
 |

**
Size
**
 |
Size (x, y, z) of the box shape.
 |

**
Custom Gravity
**
 |
Whether to apply custom gravity in this area.

 |

**
Gravity
**
 |
Gravity that overrides global/outer gravity for entities inside the area. This is
 an acceleration vector in Si.
 |

 |

**
Buoyancy Parameters
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
Type of buoyancy to apply.

-
**
Disabled
**
 -
Doesn't apply buoyancy.

-
**
Air
**
 -
Sets buoyancy type to air. Buoyancy type only affects how overlapping areas are handled: air areas are all applied, while water areas only apply the smallest (i.e. the innermost) one.

-
**
Water
**
 -
Sets buoyancy type to water.
 |

**
Flow
**
 |
The flow of the air or water, in meters per second.

 |

**
Density
**
 |
Density of the medium; reference water is 1000, reference air is about 1.
 |

**
Resistance
**
 |
Resistance of the medium (reference water is 1000). This is
 a force that resists the motion (relative to the flow speed).
 |

 |

**
Uniform
**
 |
Flow and/or gravity is uniform rather than based on the position relative to the shape.
 |

**
Falloff Start
**
 |
For non-uniform shapes, start of falloff (1 = shape boundary).

 |

##
Box Collider

Adds a physical box part to the physics only (without any StatObj). It still uses an entity slot

These colliders will not be rendered (except as helpers when the entity is selected in the editor), which can be desirable in some cases, such as ragdoll actors, invisible walls, or general collision adjustments.

Property
 |
Description
 |

**
Box Collider Settings
**
 |

-
**
Size -
**
Size of the box.
 |

**
Physics Settings
**
 |
Setting
 |
Description
 |

**
Weight Type
**
 |
Determines whether to use Mass, Density as the weight type of the mesh. It also allows the user to make the mesh immovable when physicalized.

-
**
Mass -
**
Mass of the object in kg.

-
**
Density-
**
Density of the object
 in Kg/m
3
.

-
**
Immovable -
**
Prevents the mesh entity from moving it is physicalized.
 |

**
Mass (pre-scale)
**
 |
Appears when
**
Mass
**
 is selected on the Weight Type list. It pre-scales the mass of the object in kg.

 |

**
Density
**
 |
Appears when
**
Density
**
 is selected on the Weight Type list. Results in the mass being calculated based on the volume of the object.
 |

**
Surface Type
**
 |
Surface type assigned to this object - determines its physical properties.
 |

**
React to Collisions
**
 |
Defines if the collider should send collision events.
 |

 |

##
Capsule Collider

Adds a physical capsule part to the physics only (without any StatObj). It still uses an entity slot.

These colliders will not be rendered (except as helpers when the entity is selected in the editor), which can be desirable in some cases, such as ragdoll actors, invisible walls, or general collision adjustments.

Property
 |
Description
 |

**
Capsule Collider Settings
**
 |
Setting
 |
Description
 |

**
Radius
**
 |
Radius of the capsule.
 |

**
Height
**
 |
Height of the capsule.
 |

 |

**
Physics Settings
**
 |
Setting
 |
Description
 |

**
Weight Type
**
 |
Determines whether to use Mass, Density as the weight type of the mesh. It also allows the user to make the mesh immovable when physicalized.

-
**
Mass -
**
Mass of the object in kg.

-
**
Density -
**
Density of the object in Kg/m
3
**
.
**

-
**
Immovable -
**
Prevents the mesh entity from moving it is physicalized
.
 |

**
Mass (pre-scale)
**
 |
Appears when
**
Mass
**
 is selected on the Weight Type list. It pre-scales the mass of the object in kg.
 |

**
Density
**
 |
Appears when
**
Density
**
 is selected on the Weight Type list. Results in the mass being calculated based on the volume of the object.
 |

**
Surface Type
**
 |
Surface type assigned to this object - determines its physical properties.
 |

**
React to Collisions
**
 |
Defines if the collider should send collision events.
 |

 |

##
Character Controller

Functionality for a standard FPS / TPS style walking character.

Property
 |
Description
 |

**
Character Controller Setting
**
 |

-
**
Networked Synced -
**
Syncs the physical entity over the network and keeps it in sync with the server.
 |

**
Physics
**
 |
Setting
 |
Description
 |

**
Mass
**
 |
Mass of the character in kg.
 |

**
Collider Radius
**
 |
Radius of the default capsule or cylinder.
 |

**
Collider Height
**
 |
Height of the default capsule or cylinder.
 |

**
Use Capsule
**
 |
Whether or not to use a capsule as the main collider. If disabled, will use a cylinder.

 |

**
Ground Contact Epsilon
**
 |
The amount of distance that the player needs to move upwards (in meters) before the ground contact is lost.
 |

**
Send Collision Signal
**
 |
Whether or not this component should listen for collisions and report them.
 |

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
Air Control Ratio
**
 |
Indicates how much the character can move in the air, 0 = no movement, 1 = full control.
 |

**
Air Resistance
**
 |
The amount of friction (force opposed to movement) received when airborne.

(dampens velocity when airborne).
 |

**
Inertia Coefficient
**
 |
Sets how fast the character will be able to achieve the desired velocity. Higher values correspond to more responsive movement. 0 is a special value, meaning full control / instant velocity switch.
 |

**
Inertia Acceleration Coefficient
**
 |
Same as inertia, but used when the character is accelerating (i.e. its desired velocity is non-0).
 |

**
Maximum Climb Angle
**
 |
Maximum angle of inclination at which the character can climb.

 |

**
Maximum Jump Angle
**
 |
Maximum angle of inclination at which the character can jump.
 |

**
Minimum Angle For Slide
**
 |
Angle below which the player starts sliding down.

 |

**
Minimum Angle For Fall
**
 |
Angle below which the character starts falling.

 |

**
Maximum Surface Velocity
**
 |
Maximum velocity with which a character can keep walking on a surface, before they are considered airborne and slide off.

 |

 |

##
Cloth

Physicalizes mesh as cloth/soft object.

Property

 |
Description

 |

**
File
**

 |
Determines the CGF to load.

 |

**
Material
**

 |
Specifies the override material for the selected object.

 |

**
Cast Shadows
**

 |
Sets whether the cloth will cast shadows.

 |

**
Mass
**

 |
Mass of the cloth object (only useful for lighter than air closed objects).

 |

**
Density
**

 |
Density of cloth's vertices (only affects floating in water). Unlike rigid bodies, cloth can have independent mass and density settings.

 |

**
Thickness
**

 |
Used for collision detection. Every cloth vertex is surrounded by a colliding sphere with this radius.

 |

**
Mass Decay
**

 |
Sets by how much vertex mass decreases at cloth's free ends compared to attached ones. Higher values improve solver and stretch enforcement quality, but it should be 0 for unattached cloth (such as pressurized).

 |

**
Friction
**

 |
Friction at collision points.

 |

**
Air Resistance
**

 |
Sets how strongly cloth is affected by the wind.

 |

**
Wind
**

 |
Extra wind added to this cloth, on top of the global/physical areas.

 |

**
Wind Variance
**

 |
Adds a random variance to the wind to make the cloth more flappy.

 |

**
Pressure
**

 |
Internal pressure for closed cloth.

 |

**
Density Inside
**

 |
Density of the medium inside the cloth. Can be used to adjust buoyancy, by having cloth objects filled with lighter-than-air mediums for instance (i.e. <1 density).

Set to -1 to assume the same density as outside.

 |

**
Impulse Scale
**
 |
Scales hit impulses applied to the cloth (to avoid excessive reaction)

 |

**
Explosion Scale
**

 |
Explosion impulses applied to the cloth (to avoid excessive reaction). This lets you have visible deformations from bullet impacts, but without vastly distorting the object too far with explosions.

 |

Simulation Parameters

 |

**
Maximum Time Step
**

 |
The largest time step that the entity can make before splitting. Smaller time steps increase the stability (can be required for long and thin objects, for instance), but are more expensive.

 |

**
Sleep Speed
**

 |
An object is considered sleeping if its kinetic energy falls below a limit over several frames. This option defines that limit.

The limit is proportional to
**
Sleep Speed
**
2
.

 |

**
Damping
**

 |
A cheaper alternative/addition to water resistance (applies uniform damping when in water).

Sets the strength of the damping on an object's movement as soon as it is situated underwater. Most objects can work with 0 damping; if an object has trouble coming to rest, try values like 0.2-0.3.

Values of 0.5 and higher appear visually as overdamping. Note that when several objects are in contact, the highest damping is used for the entire group.

 |

**
Hardness
**

 |
Strength of connections between cloth's vertices.

 |

**
Max Iters
**

 |
Amount of iterations to solve cloth's constraints (affects the cloth solver speed).

 |

**
Accuracy
**

 |
Accuracy (allowed velocity error per frame) of the cloth solver.

 |

**
Max Stretch
**

 |
Maximum allowed streching before positional enforcement is activated, in fractions of 1 (i.e. 0.05=5%). Smaller values to be used to remove stretching even with low Max Iters. It's a cheaper, but less physically accurate way.

 |

**
Bend Stiffness
**

 |
Stiffness against bending - smaller values indicate less stiffness, larger values indicate stronger stiffness.

Set to 0.0 to disable.

 |

**
Shear Stiffness
**

 |
Strength against shearing - smaller values indicate less stiffness, larger values indicate stronger stiffness.

Set to 0.0 to disable.

 |

**
Terrain Collisions
**

 |
Enables collisions with the main terrain.

 |

**
Static Collisions
**

 |
Enables collisions with static objects.

 |

**
Dynamic Collisions
**

 |
Enables collisions with 'normal' physical object, i.e. rigid bodies, ragdolls, vehicles.

 |

**
Player Collisions
**

 |
Enables collisions with legacy-style players (PE_LIVING).

 |

##
Cylinder Collider

Adds a physical cylinder part to the physics only (without any StatObj). It still uses an entity slot.

These colliders will not be rendered (except as helpers when the entity is selected in the editor), which can be desirable in some cases, such as ragdoll actors, invisible walls, or general collision adjustments.

Property
 |
Description
 |

**
Cylinder Collider Settings
**
 |
Setting
 |
Description
 |

**
Radius
**
 |
Radius of the cylinder.
 |

**
Height
**
 |
Height of the cylinder.
 |

 |

**
Physics Settings
**
 |
Setting
 |
Description
 |

**
Weight Type
**
 |
Determines whether to use Mass, Density as the weight type of the mesh. It also allows the user to make the mesh immovable when physicalized.

-
**
Mass -
**
Mass of the object in kg.

-
**
Density -
**
Density of the object in Kg/m
3
**
.
**

-
**
Immovable -
**
Prevents the mesh entity from moving it is physicalized.
 |

**
Mass (pre-scale)
**
 |
Appears when
**
Mass
**
 is selected on the Weight Type list. It pre-scales the mass of the object in kg.
 |

**
Density
**
 |
Appears when
**
Density
**
 is selected on the Weight Type list. Results in the mass being calculated based on the volume of the object.
 |

**
Surface Type
**
 |
Surface type assigned to this object - determines its physical properties.
 |

**
React to Collisions
**
 |
Defines if the collider should send collision events.
 |

 |

##
Local Grid

Local Grid allows entities to be attached to larger hosts and be physically simulated within its local environment at the same time.
An interior of a moving train or a spaceship are some of the examples where a Local Grid can be used to define a local environment.

More related information can be found on the
[/docs/static/engines/cryengine-5/categories/23756813/pages/28182887](
Local Simulation Grids
)
 Technical Documentation page.

Property
 |
Description
 |

**
Number Of Cells X
**
 |
Number of cells that appear on the X axis.
 |

**
Number Of Cells Y
**
 |
Number of cells that appear on the Y axis.
 |

**
Cell Size
**
 |
Each field in this option defines the size of the cells on the X and Y axes respectively.
 |

**
Height
**
 |
Sets the height of the grid area.
 |

**
Acceleration Threshold
**
 |
Minimal host acceleration that is applied to objects inside the grid.
 |

##
PhysParticle

Physicalizes the entity as a particle.

Property
 |
Description
 |

**
Mass
**
 |
Mass of the entity in kg.

 |

**
Size
**
 |
'Size' in the direction of movement. If the particle is imagined as a sphere, 'size' is its diameter.
 |

**
Thickness
**
 |
Size along the normal when lying (can be different from size in the direction of movement)
 |

**
Normal
**
 |
Direction in the entity space that gets aligned with the surface normal when lying.

 |

**
Roll Axis
**
 |
Roll axis in the entity space.
 |

**
Thrust
**
 |
Acceleration in the direction movement.
 |

**
Lift
**
 |
Acceleration along the entity 'up' direction.
 |

**
Gravity Scale
**
 |
Particle's acceleration due to gravity = world gravity * this scale.

**
A value of 0
**
 will disable gravity completely, while
**
a value of 1
**
 means full gravity acceleration.

 |

**
Water Gravity Scale
**
 |
World gravity scaling coefficient when in water.
 |

**
Air Resistance Scale
**
 |
Scale to the global air resistance coefficient.

 |

**
Water Resistance Scale
**
 |
Scale to the global water resistance coefficient.
 |

**
Bounce Speed Threshold
**
 |
Minimal approach velocity (along the normal) that results in a bounce.
 |

**
Sleep Threshold
**
 |
Sends the particle to sleep if its speed falls below this threshold.
 |

**
Awake
**
 |
By default, the object is in a sleep mode so that it doesn't use any resources from the physics engine until it is required to do so. You can make the object to be "awake" by default when the game starts by checking this parameter.

 |

**
Network Synced
**
 |
Syncs the physical entity over the network and keeps it in sync with the server.

 |

**
Send Collision Signal
**
 |
Whether or not this component should listen for collisions to generate a signal.

 |

**
Traceable
**
 |
Particle is registered in the entity grid and can be seen by raytracing end entities-in-box queries.
 |

**
Single Contact
**
 |
Stops the particle after its first contact.

 |

**
Constant Orientation
**
 |
The particle never changes rotation on its own.

 |

**
No Roll
**
 |
The particle slides on the ground instead of rolling (which also triggers ground alignment along 'normal').
 |

**
No Spin
**
 |
The particle doesn't spin when flying.

 |

**
No Path Alignment
**
 |
The particle doesn't align its (0,1,0) axis with the movement direction.

 |

**
No Self Collisions
**
 |
The particle doesn't collide with other particles with the same flag.

 |

**
No Impulse
**
 |
The particle doesn't add impulse on contact.
 |

**
Surface Type
**
 |
The particle's surface type (used for bounciness, friction, and particle effects).

 |

##
Ragdoll

Physicalizes a single animated mesh or advanced animation component as a ragdoll, or a set of static meshes as an articulation.

Property
 |
Description
 |

**
Ragdoll Settings
**
 |
Property
 |
Description
 |

**
Network Synced
**
 |
Syncs the physical entity over the network and keeps it in sync with the server.
 |

**
Resting
**
 |
If the entity is resting it only starts to simulate on interaction with other physical entities. For example a barrel which normally is just static in the level but as soon as the player starts to shoot it, starts to be simulated by physics.
 |

 |

**
Buoyancy Parameters
**
 |
Fluid behavior related to this entity.

Property
 |
Description
 |

**
Damping
**
 |
A cheaper alternative/addition to water resistance (applies uniform damping when in water).

Sets the strength of the damping on an object's movement as soon as it is situated underwater. Most objects can work with 0 damping; if an object has trouble coming to rest, try values like 0.2-0.3.

Values of 0.5 and higher appear visually as overdamping. Note that when several objects are in contact, the highest damping is used for the entire group.
 |

**
Density
**
 |
(= Volume / Mass) Density affects the way objects interact with other objects and float in the water (they sink if their density is more than that of the water).

Note that both density and mass can be overridden in the asset file.

Density of the medium; reference water is 1000, reference air is about 1.

 |

**
Resistance
**
 |
Resistance of the medium (reference water is 1000). This is a force that resists the motion (relative to the flow speed).
 |

 |

**
Simulation Parameters
**
 |
Parameters related to the simulation of this entity.

Property
 |
Description
 |

**
Maximum Time Step
**
 |
The largest time step that the entity can make before splitting. Smaller time steps increase the stability (can be required for long and thin objects, for instance), but are more expensive.
 |

**
Sleep Speed
**
 |
An object is considered sleeping if its kinetic energy falls below a limit over several frames. This option defines that limit.

The limit is proportional to
**
Sleep Speed
**
2
.

 |

**
Damping
**
 |
Sets the strength of damping on an object's movement.

Most objects can work with 0 damping; if an object has trouble coming to rest, try values like 0.2-0.3.
 |

 |

**
Stiffness
**
 |
If >0, allows ragdoll to play animations by applying torques at joints.

 |

**
Extra Stiff Mode
**
 |
Much more stable with high stiffness values, but uses the same stiffness for playing animation and enforcing locked axes/limits.
 |

##
RigidBody

Physicalizes the entity as a rigidbody or a static (depending on the type). Adds mesh components and primitive collider components as parts. Note that those components alone will not physicalize the entity, they can only add parts to an entity that is physicalized through other means, such as RigidBody component.

Property
 |
Description
 |

**
Rigidbody Settings
**
 |
Setting
 |
Description
 |

**
Networked Synced
**
 |
Syncs the physical entity over the network and keeps it in sync with the server.
 |

**
Enabled by Default
**
 |
Whether the component is enabled by default.

 |

**
Resting
**
 |
If the body is resting it only starts to simulate on interaction with other physical entities. For example a barrel which normally is just static in the level but as soon as the player starts to shoot it, starts to be simulated by physics.
 |

**
Type
**
 |
Type of physicalized object to create.

-
**
Static
**
- don't move and always have "infinite" mass.

-
**
Rigid
**
- normal simulated objects. These
*
can
*
 have infinite mass as well, but the physics knows that they can move if the velocity is set manually.
 |

**
Send Collision Signal
**
 |
Whether or not this component should listen for collisions and report them.
 |

 |

**
Buoyancy Parameters
**
 |
Physical properties related to the behavior of this entity while submerged in fluid.

Setting
 |
Description
 |

**
Damping
**
 |
A cheaper alternative/addition to water resistance (applies uniform damping when in water).

Sets the strength of the damping on an object's movement as soon as it is situated underwater. Most objects can work with 0 damping; if an object has trouble coming to rest, try values like 0.2-0.3.

Values of 0.5 and higher appear visually as overdamping. Note that when several objects are in contact, the highest damping is used for the entire group.
 |

**
Density
**
 |
(= Volume / Mass) Density affects the way objects interact with other objects and float in the water (they sink if their density is more than that of the water).

Note that both density and mass can be overridden in the asset file.

Density of the medium (reference water is 1000, reference air is about 1).

 |

**
Resistance
**
 |
Resistance of the medium (reference water is 1000). This is
 a force that resists the motion (relative to the flow speed).
 |

 |

**
Simulation Parameters
**
 |
Parameters that can be used to adjust the simulation of this entity.

Setting
 |
Description
 |

**
Maximum Time Step
**
 |
The largest time step that the entity can make before splitting. Smaller time steps increase the stability (can be required for long and thin objects, for instance), but are more expensive.
 |

**
Sleep Speed
**
 |
An object is considered sleeping if its kinetic energy falls below a limit over several frames. This limit is proportional to the square of the sleep speed value. This option defines that limit.

The limit is proportional to
**
Sleep Speed
**
2
.
 |

**
Damping
**
 |
Sets the strength of damping on an object's movement.

Most objects can work with 0 damping; if an object has trouble coming to rest, try values like 0.2-0.3.
 |

 |

##
Sample Rigidbody Actor

Physicalizes the entity as PE_WALKING_RIGID, which is a suggested replacement for PE_LIVING. It has the same sweep-based main geometry movement, customizable set of ground sampling rays (as opposed to PE_LIVING fixed one at the center), and it's derived from PE_RIGID, meaning that it can seamlessly interact with other physicalized objects (the original PE_LIVINGs are simulated independently from normal physicalized objects, and thus their interactions are not as immediate and responsive). It naturally uses all geometries that were added to the entity, same as a RigidBody would (cgf's, physical colliders).

Setting
 |
Description
 |

**
Friction
**
 |
Friction of the sampling (leg) ray contacts that's used when the actor is not moving. Useful for standing on slopes (friction 1 can hold an object on a 45 degrees slope).
 |

**
Minimal Ground Mass
**
 |
Minimum mass that the objects must have to collide with the sampling rays (can be used to avoid standing on small debris pieces or props).
 |

**
Legs Stiffness
**
 |
Defines how strongly the character tries to restore fully upright position if leg ray contacts are compressed.
 |

**
Skeleton Stiffness
**
 |
Defines stiffness the attached alive skeleton of animated mesh components.
 |

##
Sphere Collider

Adds a physical sphere part to the physics only (without any StatObj). It still uses an entity slot.

These colliders will not be rendered (except as helpers when the entity is selected in the editor), which can be desirable in some cases, such as ragdoll actors, invisible walls, or general collision adjustments.

Property
 |
Description
 |

**
Sphere Collider Settings
**
 |

-
**
Radius -
**
Sets the radius of the sphere.
 |

**
Physics Settings
**
 |
Setting
 |
Description
 |

**
Weight Type
**
 |
Determines whether to use Mass, Density as the weight type of the mesh. It also allows the user to make the mesh immovable when physicalized.

-
**
Mass -

**
Mass of the object in kg.

-
**
Density -

**
Density of the object in Kg/m
3
**
.
**

-
**
Immovable -

**
Prevents the mesh entity from moving it is physicalized
.
 |

**
Mass (pre-scale)
**
 |
Appears when

**
Mass
**

is selected on the Weight Type list. It pre-scales the mass of the object in kg.
 |

**
Density
**
 |
Appears when

**
Density
**

is selected on the Weight Type list. Results in the mass being calculated based on the volume of the object.
 |

**
Surface Type
**
 |
Surface type assigned to this object, determines its physical properties.
 |

**
React to Collisions
**
 |
Defines if the collider should send collision events.
 |

 |

##
Thruster

The Thruster component is basically a way to add constant force to a physicalized object. It adds the force set in
**
Constant Thrust
**
 along the component’s z axis, at the component’s origin.

Setting
 |
Description
 |

**
Constant
**
 |
True if force is enabled.
 |

**
Constant Thrust
**
 |
Force that is applied. It's applied at the component's origin and the vector is in the entity space.
 |

##
VR Interaction

Creates physicalized hand objects and allows holding other physicalized objects with VR controllers by physically constraining them to "hands".

Setting
 |
Description
 |

**
Left Hand Model
**
 |
Model to use for the left hand. It it has physics, it will physically affect other physicalized objects when moving.
 |

**
Right Hand Model
**
 |
Same for the right hand.
 |

**
Release On Hold Release
**
 |
Whether to release the object when the key used to hold is released
 |

##
Vehicle Physics

Physicalizes the entity as PE_WHEELEDVEHICLE (a rigidbody-derived wheeled vehicle).

Property
 |
Description
 |

**
Engine Parameters
**
 |
Setting
 |
Description
 |

**
Power
**
 |
Power of the engine (about 10,000 - 100,000).
 |

**
Maximum RPM
**
 |
Engine torque decreases to 0 after reaching this rotation speed.

 |

**
Minimum RPM
**
 |
Disengages the clutch when falling behind this limit, if braking with the engine.

 |

**
Idle RPM
**
 |
Engine's RPM for the idle state.
 |

**
Start RPM
**
 |
Sets this RPM when starting the engine.
 |

 |

**
Gear Parameters
**
 |
Setting
 |
Description
 |

**
Gears 1,2,3, etc.
**
 |
Specifies number of gears.

-
**
Ratio -
**
Ratio of the current gear. 0th gear is reverse, must be negative. 1st is reserved for neutral (and is normally unused). 2 and up are forward gears. Typically lower gears have >1 ratios, and upper ones <1.
 |

**
Shift Up RPM
**
 |
Engine's RPM threshold for for automatically switching to an upper gear.
 |

**
Shift Down RPM
**
 |
Engine's RPM threshold for for automatically switching to a lower gear.
 |

**
Direction Switch RPM
**
 |
Engine's RPM threshold for switching between back and forward gears.
 |

 |

**
Send Collision Signal
**
 |
Whether to listen to and report collision events.
 |

##
WaterVolume

This components attaches itself to a physicalized water volume on game start and allows changing some of its parameters dynamically.

This is a very simple and "technical" component. The main way to set up water volumes is via the corresponding built-in editor object. That object is not itself an entity, thus no components can be attached to it directly, but the water volume component can "associate" itself with it by sampling the physics environment in the specified radius, and then be used to change some of the water volume’s properties (such as the total volume) via component functions.

Property
 |
Description
 |

**
Attachment Distance
**
 |
Distance around the component's origin that gets sampled for water volume attachment.
 |

##
Wheel Collider

Adds a cylindrical wheel geometry with a suspension to the vehicle. The top of the suspension spring is the component's origin.

Property
 |
Description
 |

**
Transform
**
 |
Setting
 |
Description
 |

**
Radius
**
 |
Radius of the cylinder.

 |

**
Width
**
 |
Width of the cylinder.
 |

 |

**
Physics Settings
**
 |
Physical properties for the object, only used if a simple physics or character controller is applied to the entity.

Setting
 |
Description
 |

**
Weight Type
**
 |
Determines whether to use Mass or Density as the weight type of the mesh. It also allows the user to make the mesh immovable when physicalized.

-
**
Mass -
**
Mass of the object in kg.

-
**
Density -
**
Density of the object

in Kg/m
3
.

-
**
Immovable -
**
Prevents the mesh entity from moving when it is physicalized.
 |

**
Mass (pre-scale)
**
 |
Appears when

**
Mass
**

is selected on the Weight Type option. It pre-scales the mass of the wheel in kg.

 |

**
Density
**
 |
Appears when

**
Density
**

is selected on the Weight Type option. The weight is calculated based on wheel's volume, instead of its mass.
 |

**
Surface Type
**
 |
Surface type assigned to this object, determines its physical properties.

 |

**
Axle Index
**
 |
Used as a hint to group wheels; can be used to align wheels on opposite sides of the same axle if they differ only very slightly. An Axle Index value
**
lower than 0
**
 makes the wheel purely cosmetic, i.e. it will be aligned with the ground, but won't affect the vehicle movement.
 |

**
Driving
**
 |
Whether the wheel is driving.
 |

**
Hand Brake
**
 |
Whether the wheel is locked by hand brake or not.
 |

**
Suspension Length
**
 |
Length of the suspension spring in a fully extended (uncompressed) state.
 |

**
Initial (Compressed) Suspension Length
**
 |
Initial (compressed) length of the suspension.
 |

**
Suspension Pivot
**
 |
Suspension attachment point on the wheel, offset from the wheel's center in the entity space.

 |

**
Suspension Damping
**
 |
Damping of the suspension spring, normalized to 0..1 range.
 |

**
Ray Cast
**
 |
Whether to cast a ray downwards to find collisions and/or to check for mesh intersections.
 |

 |

[#area](
Area
)
[#box-collider](
Box Collider
)
[#capsule-collider](
Capsule Collider
)
[#character-controller](
Character Controller
)
[#cloth](
Cloth
)
[#cylinder-collider](
Cylinder Collider
)
[#local-grid](
Local Grid
)
[#physparticle](
PhysParticle
)
[#ragdoll](
Ragdoll
)
[#rigidbody](
RigidBody
)
[#sample-rigidbody-actor](
Sample Rigidbody Actor
)
[#sphere-collider](
Sphere Collider
)
[#thruster](
Thruster
)
[#vr-interaction](
VR Interaction
)
[#vehicle-physics](
Vehicle Physics
)
[#watervolume](
WaterVolume
)
[#wheel-collider](
Wheel Collider
)
