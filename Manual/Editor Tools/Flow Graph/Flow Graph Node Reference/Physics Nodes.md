# Physics Nodes

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/29450624
- Page ID: 29450624
- Breadcrumb: Editor Tools > Flow Graph > Flow Graph Node Reference > Physics Nodes
- Parent: Flow Graph Node Reference

## Content

##
ActionImpulse

Applies an impulse to an entity.

##
Awake

Awakes an entity or sends it to rest.

[Image: /docs/static/attachments/29687992]

##
CameraProxy

Used to create an entity camera proxy.

[Image: /docs/static/attachments/29687991]

**
Inputs
**

Port
 |
Type
 |
Description
 |

**
Create
**
 |
Any
 |
Creates a physicalized camera proxy if one does not exist
 |

**
EntityHost
**
 |
Any
 |
Syncs proxy rotation with the current view camera
 |

**
Outputs
**

Port
 |
Type
 |
Description
 |

**
EntityCamera
**
 |
Integer
 |
Retrieves the camera proxy
 |

##
CollisionListener

Used to setup physics collision listeners.

[Image: /docs/static/attachments/29687990]

**
Inputs
**

Port
 |
Type
 |
Description
 |

**
AddListener
**
 |
Any
 |
Adds collision listener
 |

**
IgnoreSameNode
**
 |
Boolean
 |
Suppresses events if both colliders are registered via the same node
 |

**
RemoveListener
**
 |
Any
 |
Removes collision listener
 |

**
Remove All
**
 |
Any
 |
Removes all
 |

**
Outputs
**

Port
 |
Type
 |
Description
 |

**
IdA
**
 |
Any
 |
ID of the first colliding entity
 |

**
PartIdA
**
 |
Integer
 |
Part ID inside the first colliding entity
 |

**
IdB
**
 |
Any
 |
ID of the second colliding entity
 |

**
PartIdB
**
 |
Integer
 |
Part ID inside the second colliding entity
 |

**
Point
**
 |
Vec3
 |
Location of colision point
 |

**
Normal
**
 |
Vec3
 |
Collision normal
 |

**
SurfacetypeA
**
 |
String
 |
Surface type of the first colliding entity
 |

**
SurfacetypeB
**
 |
String
 |
Surface type of the second colliding entity
 |

**
HitImpulse
**
 |
Float
 |
Collision impulse along the normal
 |

##
Constraint

Used to create a physics constraint.

[Image: /docs/static/attachments/29687989]

**
Inputs
**

Port
 |
Type
 |
Description
 |

**
Create
**
 |
Any
 |
Creates the constraint
 |

**
Break
**
 |
Any
 |
Breaks the constraint
 |

**
Id
**
 |
Integer
 |
Constraint ID
 |

**
EntityA
**
 |
Any
 |
Constraint owner entity
 |

**
PartIdA
**
 |
Integer
 |
Part ID to attach to
 |

**
EntityB
**
 |
Any
 |
Constraint buddy entity
 |

**
PartIdB
**
 |
Integer
 |
Part ID to attach to
 |

**
Point
**
 |
Vec3
 |
Connection point in worldspace
 |

**
IgnoreCollisions
**
 |
Boolean
 |
Disables collisions between constrained entities
 |

**
Breakable
**
 |
Boolean
 |
Break if force limit is reached
 |

**
ForceAwake
**
 |
Boolean
 |
Make entity B always awake; restores previous sleep parameters
 |

**
MaxForce
**
 |
Float
 |
Force limit
 |

**
MaxTorque
**
 |
Float
 |
Rotational force (torque) force limit
 |

**
MaxForceRelative
**
 |
Any
 |
Make limits relative to entity B's mass
 |

**
TwistAxis
**
 |
Boolean
 |
Main rotation axis in worldspace
 |

**
MinTwist
**
 |
Float
 |
Lower rotation limit around TwistAxis
 |

**
MaxTwist
**
 |
Float
 |
Upper rotation limit around TwistAxis
 |

**
MaxBend
**
 |
Float
 |
Maximum bend of the TwistAxis
 |

**
Outputs
**

Port
 |
Type
 |
Description
 |

**
Id
**
 |
Integer
 |
Constraint ID
 |

**
Broken
**
 |
Boolean
 |
Triggered when the constraint breaks
 |

##
Dynamics

Dynamic physical state of an entity. See output mouse-over helpers for output description help.

##
GetPhysId

Returns ID of a physical entity associated with EntityId (-1 if none).

[Image: /docs/static/attachments/29687988]

##
GetSkeleton

Returns a temporary entity id that can be used to access character skeleton physics.

[Image: /docs/static/attachments/29687986]

##
ObjTypeSelection

Lets you specify the type of object selected.

[Image: /docs/static/attachments/29687987]

##
Params

##
ArticulatedBody

Used to set physical parameters for Articulated body.

[Image: /docs/static/attachments/29687983]

Port
 |
Description
 |

**
Set
**
 |
Triggers the Node
 |

**
LyingModeNcolls
**
 |
Number of contacts that triggers 'lying mode'
 |

**
LyingDamping
**
 |
Damping override
 |

**
IsGrounded
**
 |
Whether body's pivot is firmly attached to something or free
 |

**
CheckCollisions
**
 |
Only works with
bCollisionResp
 set
 |

**
SimType
**
 |
Simulation type: 0-'joint-based', 1-'body-based'; fast motion forces joint-based mode automatically
 |

**
LyingSimType
**
 |
Simulation type override
 |

##
AutoDetachment

Used to set physical parameters for Autodetachment.

[Image: /docs/static/attachments/29687982]

##
Buoyancy

Used to set physical parameters for Buoyancy.

[Image: /docs/static/attachments/29687981]

Port
 |
Description
 |

**
WaterDensity

**
 |
Overrides water density from the current water volume for an entity; sets for water areas.
 |

**
WaterDamping
**
 |
Uniform damping while submerged, will be scaled with
submerged
 fraction.
 |

**
WaterResistance
**
 |
Water's medium resistance; same comments on water and
kwater
 apply.
 |

##
Cloth

Used to set physical parameters for Cloth.

[Image: /docs/static/attachments/29687980]

Port
 |
Description
 |

**
Thickness
**
 |
Thickness for collisions
 |

**
MaxSafeStep
**
 |
Time step cap
 |

**
Hardness
**
 |
Stiffness against stretching (for soft bodies, <0 means fraction of maximum stable)
 |

**
DampingRatio
**
 |
Damping in stretch direction, in fractions of 0-oscillation damping
 |

**
AirResistance
**
 |
Wind in addition to phys area wind
 |

**
WindVariance
**
 |
Wind variance, in fractions of 1 (currently changes 4 times/sec)
 |

**
MaxIters
**
 |
Tweak for the solver (complexity = O(nMaxIters*numVertices))
 |

**
Accuracy
**
 |
Accuracy for the solver (velocity)
 |

**
Friction
**
 |
Overrides material friction
 |

**
ImpulseScale
**
 |
Scale general incoming impulses
 |

**
ExplosionScale
**
 |
Scale impulses from explosions
 |

**
CollisionImpulseScale
**
 |
Not used
 |

**
MaxCollisionImpulse
**
 |
Not used
 |

**
CollisionMask
**
 |
Combination of ent_... flags
 |

**
MassDecay
**
 |
Decreases mass from attached points to free ends; mass_free = mass_attached/(1+decay) (can impove stability)
 |

**
StiffnessNorm
**
 |
Resistance to bending
 |

**
StiffnessTang
**
 |
Resistance to shearing
 |

##
CollisionClass

Used to set physical parameters for
CollisionClass
.

[Image: /docs/static/attachments/29687979]

Port
 |
Description
 |

**
CollisionClass
**
 |
Sets CollisionClass type
 |

**
CollisionClassIgnore
**
 |
Sets CollisionClass ignore
 |

**
CollisionClassUNSET
**
 |
Clears CollisionClass type
 |

**
CollisionClassIgnoreUNSET
**
 |
Clears CollisionClass ignore
 |

##
Constraint

Used to set physical parameters for Constraints.

[Image: /docs/static/attachments/29687978]

Port
 |
Description
 |

**
PhysEntityId
**
 |
Phys entity id of the first entity (not the same as entity id)
 |

**
Id
**
 |
If not set, will be auto-assigned; return value of Action().  Doesn't have to be unique - can update several constraints with one id; if not set, updates all constraints
 |

**
EntityPartId1
**
 |
If not set, the first part is assumed
 |

**
EntityPartId2
**
 |
If not set, the first part is assumed
 |

**
Xmin
**
 |
Rotation limits around
x axis
 ("twist"); if xlimits[0]>=[1],
x axis
 is locked
 |

**
Xmax
**
 |
Rotation limits around
x axis
 ("twist"); if xlimits[0]>=[1],
x axis
 is locked
 |

**
Yzmin

**
 |
Combined
yz
-rotation - "bending" of
x axis
; yzlimits[0] is ignored and assumed to be 0 during simulation
 |

**
Yzmax
**
 |
Combined
yz
-rotation - "bending" of
x axis
; yzlimits[0] is ignored and assumed to be 0 during simulation
 |

**
Damping
**
 |
Internal constraint damping
 |

**
SensorSize
**
 |
Used for sampling environment and re-attaching the constraint when something breaks
 |

**
HardnessLin
**
 |
Sets how fast the solver tries to resolve positional and rotational drift
 |

**
HardnessAng
**
 |
Sets how fast the solver tries to resolve positional and rotational drift
 |

**
MaxPullForce
**
 |
Positional and rotational force limits
 |

**
MaxBendTorque
**
 |
Positional and rotational force limits
 |

**
Full
**
 |
Fully locked
 |

##
ConstraintRemove

Used to set physical parameters for Cloth.

[Image: /docs/static/attachments/29687977]

##
Flags

Used to set physical parameters for Cloth.

[Image: /docs/static/attachments/29687975]

##
GroundPlane

Used to set physical parameters for Cloth.

[Image: /docs/static/attachments/29687976]

##
PartFlags

Used to set physical parameters for Cloth.

[Image: /docs/static/attachments/29687974]

##
Particle

[Image: /docs/static/attachments/29687973]

Port
 |
Description
 |

**
Flags
**
 |
Same as entity flags
 |

**
Mass and Size
**
 |
Pseudo-radius
 |

**
Heading
**
 |
Normalized heading vector
 |

**
InitialVelocity
**
 |
Velocity along "heading"
 |

**
kAirResistance

**
 |
Air resistance
koefficient
, F =
kv
 |

**
kWaterResistance
**
 |
Same for water
 |

**
AccThrust
**
 |
Acceleration along direction of movement
 |

**
AccLift

**
 |
Acceleration that lifts particle with the current speed
 |

**
MinBounceVel
**
 |
Velocity threshold for bouncing->sliding switch
 |

**
SurfaceIdx
**
 |
Angular velocity
 |

**
Pierceability
**
 |
Pierceability for ray tests; pierceable hits slow the particle down, but don't stop it
 |

**
Normal
**
 |
Aligns this direction with the surface normal when sliding
 |

PlayerDimensions

Used to set physical parameters for Cloth.

[Image: /docs/static/attachments/29687972]

##
PlayerDynamics

Used to set physical parameters for Cloth.

[Image: /docs/static/attachments/29687971]

##
Rope

Used to set physical parameters for Cloth.

[Image: /docs/static/attachments/29687970]

Port
 |
Description
 |

**
Length
**
 |
Specifies the 'target' length; 0 is allowed for ropes with dynamic subdivision
 |

**
Mass
**
 |
Thickness for collisions
 |

**
CollDist
**
 |
Thickness for collisions
 |

**
SurfaceIdx
**
 |
Used for collision reports; friction is overriden
 |

**
Friction
**
 |
Friction for free state and lateral friction in strained state
 |

**
FrictionPull
**
 |
Friction in pull direction in strained state
 |

**
Wind
**
 |
Wind vector, in addition to any environmental wind
 |

**
WindVariance
**
 |
Variance (applied to local only)
 |

**
AirResistance
**
 |
Needs to be >0 in order to be affetcted by the wind
 |

**
SensorSize
**
 |
Size of the sensor used to re-attach the rope if the host entity breaks
 |

**
MaxForce
**
 |
Force limit; when breached, the rope will detach itself unless rope_no_tears is set
 |

**
NumSegs
**
 |
Segment count, changin will reset vertex positions
 |

**
NumSubvtx
**
 |
Maximum internal vertices per segment in subdivision mode
 |

**
PoseStiffness
**
 |
Shape-preservation stiffness
 |

**
PoseDamping
**
 |
Damping for shape preservation forces
 |

**
PoseType
**
 |
0-no target pose (no shape-preservation stiffness),
 |

**
UnprojLimit
**
 |
Rotational unprojection limit per frame (no-subdivision mode)
 |

**
Stiffness
**
 |
Stiffness against stretching (used in the solver; it's *not* a spring, though)
 |

**
Hardness
**
 |
Used for the solver in strained state with subdivision on
 |

##
Simulation

Used to set physical parameters for Cloth.

[Image: /docs/static/attachments/29687969]

Port
 |
Description
 |

**
MaxTimeStep
**
 |
Maximum time step that entity can accept (larger steps will be split).
 |

**
Damping
**
 |
Damped velocity = oridinal velocity * (1 - damping*time interval).
 |

**
FreefallDamping
**
 |
Damping and gravity used when there are no collisions.
 |

**
Mass
**
 |
Damped velocity = oridinal velocity * (1 - damping*time interval).
 |

**
Density
**
 |
Maximum EventPhysCollisions reported per frame (only supported by rigid bodies/ragdolls/vehicles).
 |

**
MinEnergy
**
 |
Minimun of kinetic energy below which entity falls asleep (divided by mass).
 |

**
MaxLoggedCollisions
**
 |
Maximum EventPhysCollisions reported per frame (only supported by rigid bodies/ragdolls/vehicles).
 |

##
Vehicle

Used to set physical parameters for Vehicle.

[Image: /docs/static/attachments/29687968]

Port
 |
Description
 |

**
AxleFriction
**
 |
Friction torque at axes divided by mass of vehicle
 |

**
EnginePower
**
 |
Power of engine (about 10,000 - 100,000)
 |

**
MaxSteer
**
 |
Maximum steering angle
 |

**
EngineMaxrpm
**
 |
Engine torque decreases to 0 after reaching this rotation speed
 |

**
IntergrationType
**
 |
Used for suspensions; 0-explicit Euler, 1-implicit Euler
 |

**
MaxTimeStepVehicle
**
 |
Maximum time step when vehicle has only wheel contacts
 |

**
DampingVehicle
**
 |
Damping when vehicle has only wheel contacts
 |

**
MaxBrakingFriction
**
 |
Limits the the tire friction when handbraked
 |

**
EngineMinRPM
**
 |
Disengages the clutch when falling behind this limit, if braking with the engine
 |

**
EngineIdleRPM
**
 |
RPM for idle state
 |

**
EngineShiftupRPM
**
 |
RPM threshold for for automatic gear switching
 |

**
EngineShiftdownRPM
**
 |
RPM for idle state
 |

**
Stabilizer
**
 |
Stabilizer force, as a multiplier for kStiffness of respective suspensions
 |

**
ClutchSpeed
**
 |
Clutch engagement/disengagement speed
 |

**
BrakeTorque
**
 |
Torque applied when breaking using the engine
 |

**
DynFrictionRatio
**
 |
Friction modifier for sliping wheels
 |

**
GearDirSwitchRPM
**
 |
RPM threshold for switching back and forward gears
 |

**
SlipThreshold
**
 |
Lateral speed threshold for switchig a wheel to a 'slipping' mode
 |

**
EngineStartRPM
**
 |
Sets this RPM when activating the engine
 |

**
MinGear
**
 |
Additional gear index clamping
 |

**
MaxGear
**
 |
Additional gear index clamping

 |

##
Velocity

Used to set physical parameters for Velocity.

[Image: /docs/static/attachments/29687967]

##
Wheel

[Image: /docs/static/attachments/29687966]

Port
 |
Description
 |

**
Wheel
**
 |
Wheels on the same axle align their coordinates (if only slightly misaligned)
 |

**
IsDriving
**
 |
Enabled when the wheel is driving
 |

**
SuspLen
**
 |
Full suspension length (relaxed)
 |

**
MaxFriction
**
 |
Surface friction is cropped to this min-max range
 |

**
MinFriction
**
 |

**
SurfaceIdx
**
 |
Uses raycasts instead of cylinders
 |

**
CanBrake
**
 |
Handbrake applies
 |

##
PartIDConversion

[Image: /docs/static/attachments/29687985]

##
PhysicsEnable

Enables/Disables Physics.

##
PhysicsSleepQuery

Node that returns the sleeping state of the physics of a given entity.

##
RayCast

Used to perform a raycast relative to an entity.

[Image: /docs/static/attachments/29687965]

**
Inputs
**

Port
 |
Type
 |
Description
 |

**
Go
**
 |
Any
 |
Activates the node
 |

**
Direction
**
 |
Vec3
 |
Direction of the raycast
 |

**
MaxLength
**
 |
Float
 |
Maximum length of the raycast
 |

**
Position
**
 |
Vec3
 |
Ray start position relative to the entity
 |

**
TransformDir
**
 |
Boolean
 |
Transforms direction by entity orientation
 |

**
Outputs
**

Port
 |
Type
 |
Description
 |

**
NoHit
**
 |
Any
 |
Triggered if no object was hit by the raycast
 |

**
Hit
**
 |
Any
 |
Triggered if an object was hit by the raycast
 |

**
Direction
**
 |
Vec3
 |
Direction of the cast ray
 |

**
Distance
**
 |
Float
 |
Distance to the hit object
 |

**
HitPoint
**
 |
Vec3
 |
Position of the hit
 |

**
Normal
**
 |
Vec3
 |
Normal of the suirface at the HitPoint
 |

**
SurfaceType
**
 |
Integer
 |
Surface type index of the surface hit
 |

**
Entity
**
 |
Any
 |
ID of the entity that was hit
 |

##
RayCastCamera

Perform a raycast relative to the camera.

##
SetParams

Sets various physical parameters that are exposed to scripts.

[Image: /docs/static/attachments/29687984]

[#actionimpulse](
ActionImpulse
)
[#awake](
Awake
)
[#cameraproxy](
CameraProxy
)
[#collisionlistener](
CollisionListener
)
[#constraint](
Constraint
)
[#dynamics](
Dynamics
)
[#getphysid](
GetPhysId
)
[#getskeleton](
GetSkeleton
)
[#objtypeselection](
ObjTypeSelection
)
[#params](
Params
)
[#partidconversion](
PartIDConversion
)
[#physicsenable](
PhysicsEnable
)
[#physicssleepquery](
PhysicsSleepQuery
)
[#raycast](
RayCast
)
[#raycastcamera](
RayCastCamera
)
[#setparams](
SetParams
)
