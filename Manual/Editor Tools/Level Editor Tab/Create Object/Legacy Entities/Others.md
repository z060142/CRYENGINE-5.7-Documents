# Others

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/29796941
- Page ID: 29796941
- Breadcrumb: Editor Tools > Level Editor Tab > Create Object > Legacy Entities > Others
- Parent: Legacy Entities

## Content

##
Overview

The "Others" entity category contains entities that don't fit into existing categories or are used across multiple categories.

##
CameraShake

A camera shake entity is an object that can be triggered in script to make the player's view shake when within the object's sphere of influence.

**
Property
**

 |
**
Description
**

 |

**
Duration
**

 |
How long the shake lasts for, in seconds.

 |

**
Frequency
**

 |
How often the camera shakes, in Hz.

 |

**
Position
**

 |
The position of the source of the camera shake. If left at 0,0,0 the position of the entity will be used.

The strength of the camera shake is strongest at the source and gradually drops as it reaches the edge of the radius.

 |

**
Radius
**

 |
The size of the radius of the sphere of influence of the shape object.

 |

**
Strength
**

 |
How violent the camera shake is.

 |

##
CameraSource

A Camera Source entity is the reference position for a scripted camera view to look from. The point at which the camera points is defined in the Entity Links dialog.

Click on "Pick Target", then on the object you wish to target to create a link.

##
CloneFactory

The main purpose is to reduce the number of inactive AI in your level. You only need one AI-Character somewhere disabled and hidden in your level in a visarea (not under terrain) which will be used as your base.

Through flowgraph, this base can be cloned unlimited from now on.

Property

 |
Description

 |

**
CloneEvents
**

 |

 |

**
CloneProperties
**

 |

 |

**
ClonePropertiesInstance
**

 |

 |

**
ConnectOnDeath
**

 |

 |

**
groupid
**

 |
Sets the groupID of the cloned AI; if this is -1, then the groupid will not be changed.

 |

**
Material
**

 |

 |

**
Radius
**

 |
Sets the safety radius of the CloneFactory. This is also used for randomizing the position of the entity slightly,

so (especially if the safety lock is off) you can set the entity to spawn in some region of space.

 |

**
SafetyLock
**

 |
If true, the CloneFactory won't clone if there is any entity in the radius which you setup above.

 |

**
strDestEntity
**

 |
Write here the name of the AI which gets cloned. It is now able to follow tagpoints due to its given name.

If this is left empty, the entity is named the same as strSourceEntity, and on the first move, the source entity will be moved.

 |

**
strSourceEntity
**

 |
Write here the name of the AI which should get clones. This is the name of the base AI-Character explained above.

 |

##
DecalPlacer

The Decal Placer Entity will place decals perpendicular to it's defined normal. It's meant to be used as a means to dynamically place decals through Flow Graphs and cut-scenes. It can also be attached to other entities.

**
Property
**

 |
**
Description
**

 |

**
Angle
**

 |
The angle the decal will have when placed.

 |

**
FileName
**

 |
Texture or material to be used as decal.

 |

**
LifeTime
**

 |
The decal's life time.

 |

**
Material
**

 |
This should be set if the
**
FileName
**
 parameter specifies a material.

 |

**
Normal Axis
**

 |
The normal axis for the decal. A ray will be traced against this axis to find the proper surface alignment. Can be x, -x, y, -y, z, or -z.

 |

**
Place
**

 |
When set, the entity will attempt to place a decal during initialization.

 |

**
Size
**

 |
The size of the decal.

 |

**
SnapDistance
**

 |
This is the max distance to ray trace against the normal axis. If no surface is found, no decal will be placed.

 |

##
EntityFlashTag

The EntityFlashTag entity is currently used for the name display above characters heads in multiplayer.

A flat plane .cgf model is used and a
[/docs/static/engines/cryengine-5/categories/23756816/pages/25535439](
Flash material
)
 is applied to the model which then is able to display the username of the player.

Property

 |
Description

 |

**
AutoGenAIHideParts
**

 |
Not used.

 |

**
Model
**

 |
Specifies the geometry to be used for the entity.

 |

**
Scale
**

 |
Scale of the model.

 |

**
SmartObjectClass
**

 |
Not used.

 |

##
Fan

A fan entity is used to simulate a ceiling mounted fan. The same functionality can be achieved using a simple flowgraph.

**
Property
**

 |
**
Description
**

 |

**
DestroyedSubObject
**

 |
When set, any destroyed version of the fan object will remain after the fan is destroyed.

 |

**
Health
**

 |
The amount of damage the fan can take before it is destroyed.

 |

**
MaxSpeed
**

 |
Maximum rotation speed.

 |

**
Model
**

 |
Specifies the geometry to be used for the object.

 |

**
ModelDestroyed
**

 |
The name of the destroyed version of the geometry used for the fan.

 |

**
ModelSubObject
**

 |
When the model has Main/Remains setup the Main object has to be defined here.

 |

**
TurnedOn
**

 |
When set, the fan starts in an active state.

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
Specifies the force emanated from the object when it explodes, affecting any nearby objects.

 |

**
LifeTime
**

 |
Sets the lifetime of the destruction particles.

 |

**
SurfaceEffects
**

 |
When disabled no destruction particles will be spawned.

 |

**
Destruction
**

 |
 |

**
Damage
**

 |
Damage entities in range will get when the entity is being destroyed.

 |

**
Decal
**

 |
The decal set here will be placed on the ground when the entity is destroyed.

 |

**
Effect
**

 |
Specifies a particle effect which will play when the interactive entity is destroyed.

 |

**
EffectScale
**

 |
The scale of the effect played when the interactive entity is destroyed.

 |

**
Explode
**

 |
When set, the interactive entity will explode when destroyed.

 |

**
Pressure
**

 |
Sets the strength of the physical impulse applied to entities in range of the explosion.

 |

**
Radius
**

 |
Radius of the explosion.

 |

**
Direction
**

 |
Direction vector of the explosion.

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
Sets the density of the entity.

 |

**
Mass
**

 |
Sets the mass of the entity.

 |

**
Resting
**

 |
When set, the entity is not activated when entering game.

 |

**
RigidBody
**

 |
When set, the entity will have a rigid physics body.

 |

**
RigidBodyActive
**

 |
When set, the rigid body will be active.

 |

**
RigidBodyAfterDeath
**

 |
When set, the rigid body will be active after the object is destroyed.

 |

##
Hazard

The hazard entity deals damage to entities entering any areas that are linked to it. The damage received by entities is dealt per second and can be set up in the properties. The hazard entity is used by linking areas to it that will trigger the damage when entered, similar to an area trigger.

In addition, a damage type can be set in the properties that determines the kind of screen effect the player will get when entering the area of the hazard entity. The damage type determines what kind of post processing effect will be applied on the screen. If the damage type is set to frost for example the screen will slowly start to freeze while the player is taking damage. There are three damage types currently: frost, fire and electricity.

The hazard entity is set up the same way as an area trigger: Create an area shape and pick the hazard entity as a target.

**
Property
**

 |
**
Description
**

 |

**
Enabled
**

 |
When set, the object is active on game startup.

 |

**
Damage
**

 |
Sets the amount of damage any entity entering the area of a hazard entity will take. The damage is applied per second.

 |

**
HazardType
**

 |
Sets the damage type of the entity (None, Frost, Fire, Electricity).

 |

**
OnlyPlayer
**

 |
When set, this object will only affect the player, and not other objects.

 |

**
SuitMultipliers
**

 |
Allows the hazard entity to do different proportions of damage depending on the player's active suit mode (Crysis only).

 |

##
InteractiveEntity

The interactive entity is used as a base to create interactive objects in the world. It is a user entity for creating things like televisions, computers, vending machines, etc.

The functionality of the entity can be set up in the properties with a lot of different options. One use for the entity is to spawn particles, play sound events, or even to spawn new entities.

**
Property
**

 |
**
Description
**

 |

**
DestroyedSubObject
**

 |
When the model has Main/Remains setup the Remain object has to be defined here.

 |

**
Health
**

 |
Sets the total damage the entity can take before it is destroyed.

 |

**
Model
**

 |
Sets the non-destroyed geometry for the entity.

 |

**
ModelDestroyed
**

 |
Sets the destroyed geometry for the entity.

 |

**
ModelSubObject
**

 |
When the model has Main/Remains setup the Main object has to be defined here.

 |

**
Pickable
**

 |
See
[/docs/static/engines/cryengine-3/categories/1114113/pages/1048651](
Common Entity Parameters
)
.

 |

**
TurnedOn
**

 |
If set the entity will be in the 'On' state initially.

 |

**
TwoState
**

 |
If set the entity has two states (On/Off) which are switched between when used.

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
Breakage
**

 |
 |

**
ExplodeImpulse
**

 |
Sets the impulse with which the destruction particles will be spawned.

 |

**
LifeTime
**

 |
Sets the lifetime of the destruction particles.

 |

**
SurfaceEffects
**

 |
When disabled no destruction particles will be spawned.

 |

**
ChangeMaterial
**

 |
 |

**
Duration
**

 |
When ChangeMatOnUse is set this number will set how long the material will be changed.

 |

**
Material
**

 |
When ChangeMatOnUse is set the material set here will be applied to the object.

 |

**
Destruction
**

 |
**
These properties define the explosion when the interactive entity is destroyed.
**

 |

**
Damage
**

 |
Damage entities in range will get when the entity is being destroyed.

 |

**
Decal
**

 |
The decal set here will be placed on the ground when the entity is destroyed.

 |

**
Effect
**

 |
Specifies a particle effect which will play when the interactive entity is destroyed.

 |

**
EffectScale
**

 |
The scale of the effect played when the interactive entity is destroyed.

 |

**
Explode
**

 |
When set, the interactive entity will explode when destroyed.

 |

**
Pressure
**

 |
Sets the strength of the physical impulse applied to entities in range of the explosion.

 |

**
Radius
**

 |
Radius of the explosion.

 |

**
Direction
**

 |
Direction vector of the explosion.

 |

**
vOffset
**

 |
Offset of the explosion relative to the pivot of the entity.

 |

**
Effect
**

 |
**
These properties defined the particle effect that will be spawned on use.
**

 |

**
AttachForm
**

 |
Linked particle emitters use this to determine how to spawn particles from the interactive object. Vertices, Edges, Surface or Volume.

 |

**
AttachType
**

 |
Tells which mesh the Attachform should spawn from. BoundingBox, Physics or Render.

 |

**
CountPerUnit
**

 |
Sets the particle count per unit.

 |

**
CountScale
**

 |
Sets the particle count for the effect

 |

**
ParticleEffect
**

 |
Defines the particle effect to be used.

 |

**
Prime
**

 |
If set the effect is already 'alive' when activated.

 |

**
PulsePeriod
**

 |
Sets the pulse period of the effect.

 |

**
Scale
**

 |
Sets the scale of the effect.

 |

**
SpawnPeriod
**

 |
Sets the spawn period of the effect.

 |

**
vOffset
**

 |
Offset of the effect relative to the objects pivot.

 |

**
vRotation
**

 |
Rotation vector of the effect.

 |

**
OnUse
**

 |
 |

**
ChangeMatOnUse
**

 |
When set, the material used on the interactive entity change when the player actions the entity.

 |

**
CoolDownTime
**

 |
This time defines how long the entity will be unusable after it has been used.

 |

**
EffectOnUse
**

 |
When set, the interactive entity will play a particle effect when the player actions the entity.

 |

**
SoundOnUse
**

 |
When set, the interactive entity will play a sound when the player actions the entity.

 |

**
SpawnOnUse
**

 |
When set, the interactive entity will spawn an object when the player actions the entity.

 |

**
UseDelay
**

 |
Specifies a delay between when the player actions the object, and when the object activates.

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
Sets the density of the entity.

 |

**
Mass
**

 |
Sets the mass of the entity.

 |

**
Resting
**

 |
When set, the entity is not activated when entering game.

 |

**
RigidBody
**

 |
When set, the entity will have a rigid physics body.

 |

**
RigidBodyActive
**

 |
When set, the rigid body will be active.

 |

**
StaticInDX9Multiplayer
**

 |
When set, the entity will be static in DX9 multiplayer games.

 |

**
Bouyancy
**

 |
Sets the buoyancy of the entity.

 |

**
ScreenFunctions
**

 |
**
When a flash material is used on the entity these properties are used to access it.
**

 |

**
FlashMatId
**

 |
Number of the flash material on the entity material.

 |

**
HasScreenFunction
**

 |
If checked the entity will perform a screen function.

 |

**
Type
**

 |
Defines the type of screenfunction the flash material has.

 |

**
Sound
**

 |
 |

**
Sound
**

 |
The looping sound of the object.

 |

**
TurnOffSound
**

 |
The sound played when the object is deactivated.

 |

**
TurnOnSound
**

 |
The sound played when the object is activated.

 |

**
SpawnEntity
**

 |
**
These properties define how a spawned entity behaves when spawned.
**

 |

**
Archetype
**

 |
Specifies the archetype of any object spawned.

 |

**
Impulse
**

 |
When spawned the spawned entity will get the physics impulse set here.

 |

**
SpawnLimit
**

 |
Specifies the maximum number of spawned objects that can be spawned.

 |

**
vImpulseDir
**

 |
Direction of the physics impulse spawned entities will get applied.

 |

**
vOffset
**

 |
Offset of the pivot of the entity. This defines where the entity will be spawned.

 |

**
vRotation
**

 |
Sets orientation of the spawned entity.

 |

**
Vulnerability
**

 |
 |

**
Bullet
**

 |
When set, the object will take damage from bullets.

 |

**
Collision
**

 |
When set, the object will take damage from impact with other objects.

 |

**
DamageThreshhold
**

 |
Damage below the threshold set here will be ignored.

 |

**
Explosion
**

 |
When set, the object will take damage from explosions.

 |

**
Melee
**

 |
When set, the object will take damage from melee hits.

 |

**
Other
**

 |
When set, the object will take damage from other damage sources.

 |

##
Ladder

Property

 |
Description

 |

**
approachAngle
**

 |
Angle which the player can approach the ladder from and be allowed to use it.

 |

**
approachAngleTop
**

 |
 |

**
height
**

 |
Height of the ladder. The top blue debug cylinder should be inline with the top rung.

 |

**
Model
**

 |
Specifies the geometry to be used for the entity.

 |

**
TopBlocked
**

 |
Prevents the player from accessing the top of the ladder.

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

Camera

 |

 |

**
cameraAnimFraction_getOff
**

 |
Fraction of animated camera position/rotation to use when getting off the ladder.

 |

**
cameraAnimFraction_getOn
**

 |
Fraction of animated camera position/rotation to use when getting onto the ladder.

 |

**
cameraAnimFraction_onLadder
**

 |
Fraction of animated camera position/rotation to use when staying on the ladder.

 |

**
distanceBetweenRungs
**

 |
Distance in meters between the rungs of the ladder. Tweak to suit the asset.

 |

**
RenderLast
**

 |
Render Ladder in front of other geometry (including player).

 |

**
UseThirdPersonCamera
**

 |
If true, camera will automatically switch to 3rd person on use.

 |

Movement

 |

 |

**
movementAcceleration
**

 |
How much speed the player can gain in a second.

 |

**
movementInertiaDecayRate
**

 |
Speed at which player input inertia returns to 0 when player releases the up/down input.

 |

**
movementSettleSpeed
**

 |
Speed at which player settles on a rung when stopping part-way up/down a ladder.

 |

**
movementSpeedDownwards
**

 |
Speed (rungs/second) at which the player moves down ladders.

 |

**
movementSpeedUpwards
**

 |
Speed (rungs/second) at which the player moves up ladders.

 |

Offsets

 |

 |

**
getOnDistanceAwayBottom
**

 |
Player starts this far away from ladder climb position when getting on at bottom.

 |

**
getonDistanceAwayTop
**

 |
Player starts this far away from ladder climb position when getting on at top.

 |

**
playerHorizontalOffset
**

 |
Horizontal distance from ladder entity position to player entity position.

 |

**
stopClimbDistanceFromBottom
**

 |
Distance from the bottom of a ladder at which the player stops climbing down (and triggers the get-off-at-the-bottom animation).

 |

**
stopClimbDistanceFromTop
**

 |
Distance from the top of a ladder at which the player stops climbing up (and triggers the get-off-at-the-top animation).

 |

ViewLimits

 |

 |

**
horizontalViewLimit
**

 |
Horizontal view limit while climbing ladders. A setting of 30 means player can look 30 degrees left/right.

 |

**
verticalDownViewLimit
**

 |
Vertical view limit for looking down while climbing ladders.

 |

**
VerticalUpViewLimit
**

 |
Vertical view limit for looking up while climbing ladders.

 |

##
Mine

A mine entity is an object that will mimic the behavior of an explosive mine. The size of the explosion, delay between trigger and explosion, and various other settings can be altered.

**
Property
**

 |
**
Description
**

 |

**
AdjustToTerrain
**

 |
If set the mine will be placed on the exact height of the terrain.

 |

**
Model
**

 |
Specifies the geometry to be used for the entity.

 |

**
Radius
**

 |
Trigger radius of the mine.

 |

**
Claymore
**

 |
 |

**
CenterExplosion
**

 |
When set, an additional explosion at the center of the entity will be spawned.

 |

**
Cone
**

 |
Specifies the radius of the cone of damage for the mine, in degrees.

 |

**
Damage
**

 |
The damage done by the explosion.

 |

**
IsClaymore
**

 |
If set, the mine will only explode in a specific direction.

 |

**
Destruction
**

 |
 |

**
Damage
**

 |
Damage entities in range will get when the entity is being destroyed.

 |

**
Decal
**

 |
The decal set here will be placed on the ground when the entity is destroyed.

 |

**
DecalScale
**

 |
Sets the scale of the decal placed on destruction.

 |

**
Effect
**

 |
Specifies a particle effect which will play when the fan is destroyed.

 |

**
EffectScale
**

 |
The scale of the effect played when the fan is destroyed.

 |

**
Pressure
**

 |
Sets the strength of the physical impulse applied to entities in range of the explosion.

 |

**
Radius
**

 |
Radius of the explosion.

 |

**
Direction
**

 |
Direction vector of the explosion.

 |

**
FrogMine
**

 |
 |

**
DetonationDelay
**

 |
Specifies the time delay between triggering the mine and its activation.

 |

**
IsFrogMine
**

 |
When set, the mine will jump the specified height when triggered.

 |

**
JumpHeight
**

 |
Specifies the height the mine will jump into the air, when activated.

 |

**
JumpWhenShot
**

 |
When set, the mine will jump when shot.

 |

**
Options
**

 |
 |

**
DisarmDistance
**

 |
Specifies the distance at which the player can disarm the mine from.

 |

**
MinTriggerWeight
**

 |
Specifies the minimum weight required to trigger the mine.

 |

**
NoVehicles
**

 |
When set, vehicles will not trigger the mine.

 |

**
WaterMine
**

 |
When set, this mine can be used against boats on water.

 |

**
Vulnerability
**

 |
 |

**
Bullet
**

 |
When set, the object will take damage from bullets.

 |

**
Collision
**

 |
When set, the object will take damage from impact with other objects.

 |

**
DamageThreshhold
**

 |
Sets the minimum damage required to register a hit on the entity.

 |

**
Explosion
**

 |
When set, the object will take damage from explosions.

 |

**
Melee
**

 |
When set, the object will take damage from melee hits.

 |

**
Other
**

 |
When set, the object will take damage from other damage sources.

 |

##
MissionObjective

A Mission Objective entity is an object that is used to define the position of the player's goals in the level, and the text associated with each goal.

A mission object can reference another object as a target for the mission, for example, a moving target requiring player interaction.

**
Property
**

 |
**
Description
**

 |

**
MissionID
**

 |
The reference name of the objective, taken from the external Objectives.xml file.

 |

**
ShowOnRadar
**

 |
When set, the position of the objective will show on the player's radar.

 |

**
TrackedEntityName
**

 |
When set, defines an alternative entity on the radar as a positional marker for the objective.

 |

##
PrecacheCamera

The Precache Camera entity is used by the level precache system. Right after a level is loaded the engine will internally draw the level using camera positions and orientations specified by these entities.

This solution is used in order to pre-activate all render resources and in this way minimize stalls during game-play. Level precache may be activated by using the
**
e_PrecacheLevel
**
 variable.

##
Rigid Body

DEPRECATED (Use
[/docs/static/engines/cryengine-5/categories/23756816/pages/29796943#PhysicsEntities-RigidBodyEx](
RigidBodyEx
)
 instead)

A Rigid Body Entity is a solid object with additional associated physics simulation parameters.

**
Property
**

 |
**
Description
**

 |

**
ActivateOnRocketDamage
**

 |
When set, the object physics simulation will become active when the object is within the damage radius of a rocket.

 |

**
AutoGenAIHidePoints
**

 |
When set, the object will automatically generate places for AI to hide with, around the object.

 |

**
Damping
**

 |
Values of 0.5 and higher appear visually as overdamping. Note that when several objects are in contact, the highest damping is used for the entire group.

 |

**
Density
**

 |
Density affect the way objects interact with other objects and float in the water (they sink if their density is more than that of the water).

 |

**
Mass
**

 |
Mass is the weight of the object (the density of the object multiplied by its volume).

 |

**
Max_time_step
**

 |
Specifies the time between physics updates on the object. When multiple objects with different time steps interact, the smallest time step is used for all.

 |

**
Model
**

 |
Specifies the geometry to be used for the entity.

 |

**
Resting
**

 |
The rigid body's initial state is sleeping (resting). It needs to be awoken by an external stimulus (bullet hit, explosion, collision, player interaction, etc) in order to start being simulated.

 |

**
RigidBodyActive
**

 |
When set, the object will behave as a simulated physics rigid body. When unset, the object will remain static.

 |

**
Sleep_speed
**

 |
If the object's kinetic energy falls below some limit over several frames, the object is considered sleeping.

This limit is proportional to the square of the sleep speed value. A sleep speed of 0.01 loosely corresponds to the object's center moving at a velocity of the order of 1 cm/s.

 |

**
SmartObjectClass
**

 |
Sets the smart object type of the entity, allowing interaction with AI.

 |

**
Visible
**

 |
When set, the object will be visible in your level.

 |

**
Water_damping
**

 |
Specifies how objects are generally slowed by water.

 |

**
Water_resistance
**

 |
Specifies an additional speed of slowdown when an object interacts with water. Can be useful for stopping light objects bouncing when they enter water.

 |

**
Impulse
**

 |
When the object has its physics simulation activated, it will be pushed by the force defined here.

 |

##
Shooting Target

DEPRECATED

A shooting target entity is an object which can be used to create a shooting range. It is able to count hits and output a score.

Property

 |
Description

 |

**
IntervalMax
**

 |
The maximum time between becoming inactive and turning.

 |

**
IntervalMin
**

 |
The minimum time between becoming inactive and turning.

 |

**
LightUpTime
**

 |
How long the entity remains active.

 |

**
Model
**

 |
Specifies the geometry to be used for the entity.

 |

**
SmartObjectClass
**

 |
Sets the smart object type of the entity, allowing interaction with AI.

 |

**
TurningMode
**

 |
If set, the entity will enter a turning behavior. This behavior will begin in an inactive state, and intermittently turn to

an active state, allowing a hit to be registered, and score taken. When hit, the entity will revert to inactive state.

 |

**
TurnSpeed
**

 |
The speed at which the entity rotates to and from active mode, if entity is in turning mode.

 |

##
Sound Suppressor

A sound suppressor is an entity used by the AI system to reduce the apparent volume of sounds within its radius area to AI characters, meaning these sounds are less likely to be noticed and reacted to. Used in conjunction with Flowgraph.

**
Property
**

 |
**
Description
**

 |

**
radius
**

 |
Specifies the radius of the effect of the entity.

 |

##
SpawnPoint

A Singleplayer or Multiplayer spawn point which defines a players start point. If you don't use a SpawnPoint in your level, the player will spawn at 0,0,0 coordinates. It is not recommended to have spawn points closer than 4m apart.

Property

 |
Description

 |

**
DoVisTest
**

 |
If enabled, the engine will attempt to spawn the player at a different spawn point if the current spawn point is in line of sight of an enemy player (prevents spawn camping).

If spawns are grouped together, only one needs to have this checked.

 |

**
Enabled
**

 |
When set, this point is available for spawning. Using devmode F2 to cycle spawns ignores this value.

 |

**
groupName
**

 |
Enter a string name of your choice to allow specific entities to be activated together with matching spawnpoints.

For example, in Gladiator game mode, spawnpoint and ammo crate have groupName/GroupID of "myspawn1", these items will spawn together.

 |

**
InitialSpawn
**

 |
When set, players will spawn at this spawn point on their first, initial spawn. Following spawns will be randomized.

 |

**
teamName
**

 |
In multiplayer, defines the team which will use this spawn point. Valid team names are defined in the game rules.

 |

##
Switch

A switch entity is an object with an on/off state, used for simulating light switches and other switches. It has various flow graph ports exposed to allow its activity to be checked.

**
Property
**

 |
**
Description
**

 |

**
Destroyable
**

 |
Specify whether the object can be destroyed or not.

 |

**
DestroyedSubObject
**

 |
When the model has Main/Remains setup the Remain object has to be defined here.

 |

**
Health
**

 |
Sets the total damage the entity can take before it is destroyed.

 |

**
Model
**

 |
Sets the non-destroyed geometry for the entity.

 |

**
ModelDestroyed
**

 |
Sets the destroyed geometry for the entity.

 |

**
ModelSubObject
**

 |
When the model has Main/Remains setup the Main object has to be defined here.

 |

**
Switch
**

 |
Specifies an Entity Archetype (Basic Entity) to be used for the moving part of the switch.

See the
*
Props_Interactive.Switches.light_switch
*
 setup for an example implementation.

 |

**
TurnedOn
**

 |
If set the entity will be in the 'On' state initially.

 |

**
Usable
**

 |
When set, the object will activate when actioned by the player.

 |

**
UseMessage
**

 |
Display a message when the object is in range of the player to be used. Can be a localization string.

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
Sets the impulse with which the destruction particles will be spawned.

 |

**
LifeTime
**

 |
Sets the lifetime of the destruction particles.

 |

**
SurfaceEffects
**

 |
When disabled no destruction particles will be spawned.

 |

**
Destruction
**

 |
 |

**
Damage
**

 |
Damage entities in range will get when the entity is being destroyed.

 |

**
Decal
**

 |
The decal set here will be placed on the ground when the entity is destroyed.

 |

**
Effect
**

 |
Specifies a particle effect which will play when the interactive entity is destroyed.

 |

**
EffectScale
**

 |
The scale of the effect played when the interactive entity is destroyed.

 |

**
Explode
**

 |
When set, the interactive entity will explode when destroyed.

 |

**
Pressure
**

 |
Sets the strength of the physical impulse applied to entities in range of the explosion.

 |

**
Radius
**

 |
Radius of the explosion.

 |

**
Direction
**

 |
Direction vector of the explosion.

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
Sets the density of the entity.

 |

**
Mass
**

 |
Sets the mass of the entity.

 |

**
Resting
**

 |
When set, the entity is not activated when entering game.

 |

**
RigidBody
**

 |
When set, the entity will have a rigid physics body.

 |

**
RigidBodyActive
**

 |
When set, the rigid body will be active.

 |

**
RigidBodyAfterDeath
**

 |
When set, the rigid body will be active after death.

 |

**
SmartSwitch
**

 |
 |

**
Entity
**

 |
**
DEPRECATED
**

 |

**
TurnedOffEvent
**

 |
**
DEPRECATED
**

 |

**
TurnedOnEvent
**

 |
**
DEPRECATED
**

 |

**
UseSmartSwitch
**

 |
**
DEPRECATED
**

 |

**
Sound
**

 |
 |

**
TurnOffSound
**

 |
The sound used when the switch is turned to an Off state.

 |

**
TurnOnSound
**

 |
The sound used when the switch is turned to an On state.

 |

**
SwitchPos
**

 |
 |

**
Off
**

 |
Sets the degrees rotation of the switch in the Off state.

 |

**
On
**

 |
Sets the degrees rotation of the switch in the On state.

 |

**
ShowSwitch
**

 |
When set, the moving part of the switch is shown.

 |

##
UIEntity

UIEntities are used in the HUD prefab to create the 3D HUD elements. You can specify the model used to display the UI material on.

In the case of the HUD, these models are from:
`
GameSDK/Objects/hud/HUD_Plane_x.cgf
`

Property

 |
Description

 |

**
Model
**

 |
Specifies the geometry to be used for the entity.

 |

**
SmartObjectClass
**

 |
Not used.

 |

[#camerashake](
CameraShake
)
[#camerasource](
CameraSource
)
[#clonefactory](
CloneFactory
)
[#decalplacer](
DecalPlacer
)
[#entityflashtag](
EntityFlashTag
)
[#fan](
Fan
)
[#hazard](
Hazard
)
[#interactiveentity](
InteractiveEntity
)
[#ladder](
Ladder
)
[#mine](
Mine
)
[#missionobjective](
MissionObjective
)
[#precachecamera](
PrecacheCamera
)
[#rigid-body](
Rigid Body
)
[#shooting-target](
Shooting Target
)
[#sound-suppressor](
Sound Suppressor
)
[#spawnpoint](
SpawnPoint
)
[#switch](
Switch
)
[#uientity](
UIEntity
)
