# Door Entities

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/29796928
- Page ID: 29796928
- Breadcrumb: Editor Tools > Level Editor Tab > Create Object > Legacy Entities > Door Entities
- Parent: Legacy Entities

## Content

## Overview

Door entities are used to create different types of doors. The door entities can be found in **Create Object → Legacy Entities → Doors**.

### Advanced Door

The Advanced Door entity has additional properties that allows the door to **receive damage** and be ** destroyed** appropriately. These are mostly controlled in the Breakage, Destruction and Vulnerability property tables.

The model required for an Advanced door to work fully is much the same as a destructible object, with the entity looking for specific sub-object names within the model file to use as normal and destroyed models of the door as well as any pieces that should be generated.

The door opens and closes based on simple rotation angles around the Z-axis, but as it is an advanced door, it will also physically interact with geometry and objects whilst opening and closing so it's possible to have entities blocking the path of the door.

**Properties** | **Description**
--- | ---
**Locked** | Is the door locked or not.
**DestroyedSubObject** | Will the sub object part of the door remain.
**Health** | Defines the health of the door.
**Mass** | Defines the mass of the door.
**Model** | Specifies the model of the door.
**ModelDestroyed** | Specifies the model of the door once it is destroyed.
**ModelSubObject** | Specifies the model of the sub-object of the door.
**SmartObjectClass** | See [Common Entity Parameters](BEGIN%20--%20Common%20Entity%20Parameters.md).
**UsePortal** | Specifies if the door uses portals or not.
**Breakage** |
**ExplodeImpulse** | Specifies the push back of the explosion should the door explode.
**LifeTime** | Specifies the lifetime of the object after it has been destroyed.
**SurfaceEffects** | Specifies if surface effects will be used when the object is destroyed.
**Destruction** |
**Damage** | Specifies how much damage the object does when it explodes.
**Decal** | Specifies the decal to use when the object is destroyed.
**EffectScale** | Specifies the scale of the effect.
**Explode** | Creates an explosion effect that can kill people.
**ParticleEffect** | Specifies an destruction effect.
**Pressure** | How much pressure does the object place on surrounding objects when it is destroyed.
**Radius** | Specifies the radius of the explosion.
**Direction** | Specifies the direction of the explosion in X/Y/Z coordinates.
**Limits** |
**AutoCloseTime** | Specifies how long the door will take to close automatically after been opened. Set to 0 to turn this feature off.
**Damping** | Specifies the damping on the door when it closes (how much it slows down when moving).
**InitialAngle** | Specifies the angle at which the door is initially set up.
**IsBreachable** | Specifies if the door can be breached.
**MaxBend** | Specifies how far the maximum that the door will bend.
**MaxForce** | Specifies how much force can be applied.
**OpenFromBack** | Specifies if the door opens from the back.
**OpenFromFront** | Specifies if the door opens from the front.
**OpeningRange** | Specifies how far the door opens.
**Speed** | Specifies how fast the door opens.
**UseDistance** | Specifies how far away the door can be used from.
**Sound** |
**CloseSound** | Specifies the sound used when the door is closed.
**LockedSound** | Specifies the sound used when the door is locked.
**OpenSound** | Specifies the sound used when the door is opened.
**Vulnerability** |
**Bullet** | Specifies if the door can be damaged by bullets.
**Collision** | Does the door have collision.
**DamageTreshold** | Specifies the damage required to open the door.
**Explosion** | Specifies if the door can be damaged by explosions.
**Melee** | Specifies if the door can be damaged by melee attacks.
**Other** | Specifies if "other" damage can damage the door.

### Anim Door

The Anim Door entity is another door entity available in the engine, the advantage of this entity is that you can use **animations** to control how the door opens and closes.

The Physics properties table also allows the Door to have physical properties though unlike the Advanced Door the Anim Door entity **cannot** be ** destroyed**.

If you do not require the Door to interact physically with the world it is best to set the **Physicalize**, ** PushableByPlayers** and ** RigidBody** flags to false as this will save on performance.

**Properties** | **Description**
--- | ---
**Activate Portal** | Specifies if the door activates a portal.
**Locked** | Specifies if the door is locked.
**Model** | Specifies which model the door will use.
**NoFriendlyFire** | Specifies if friendly fire affects the door.
**SmartObjectClass** | See [Common Entity Parameters](BEGIN%20--%20Common%20Entity%20Parameters.md).
**UseDistance** | Specifies how far away the door can be used from.
**Animation** |
**anim_Close** | Specifies the animation to use when the door is closed.
**anim_Open** | Specifies the animation to use when the door is opened.
**Physics** |
**Density** | Specifies the density of the door.
**Mass** | Specifies the mass of the door.
**Physicalize** | Specifies if the door is physicalized.
**PushableByPlayers** | Specifies if the door can be pushed by players or not.
**RigidBody** | Specifies if the door should use rigid body physics.
**Sounds** |
**Close** | Specifies the close sound.
**Open** | Specifies the open sound.

### Door

This is the simplest door entity available but still affords quite a large amount of control over the behavior of the door.

It is possible to use the Rotation or Slide parameters to control how the door opens and closes, for instance by changing the Axis parameter it's possible to create a door that rotates on the X or Y Axis.

This entity does **not** have any ** physical** interaction.

**Properties** | **Description**
--- | ---
**Activate Portal** | Specifies if the door activates a portal.
**Locked** | Specifies if the door is locked.
**Model** | Specifies which model the door will use.
**SmartObjectClass** | See [Common Entity Parameters](BEGIN%20--%20Common%20Entity%20Parameters.md).
**SquashPlayers** | Specifies if the door can squash and damage/kill the player.
**Usable** | See [Common Entity Parameters](BEGIN%20--%20Common%20Entity%20Parameters.md).
**UseDistance** | Specifies how far away the door can be used from.
**UseMessage** | See [Common Entity Parameters](BEGIN%20--%20Common%20Entity%20Parameters.md).
**Rotation** |
**Acceleration** | Specifies how fast the door will accelerate.
**Axis** | Specifies about which axis the door will rotate.
**FrontAxis** | Specifies the front axis of the door.
**Range** | Specifies how far the door will rotate.
**RelativeToUser** | Specifies if the door rotates in relation to the user.
**Speed** | Specifies the rotation speed of the door.
**StopTime** | Specifies how long the door takes to stop.
**Slide** |
**Acceleration** | Specifies how much the door accelerates when its sliding.
**Axis** | Specifies the axis in which the door slides.
**Range** | Specifies how far the door will slide.
**Speed** | Specifies how fast the door slides.
**StopTime** | Specifies how long the door takes to stop.
**Sounds** |
**Range** | Specifies how far the sound of the door can be heard from.
**SoundOnMove** | Specifies the sound to use when the door moves.
**SoundOnStop** | Specifies the sound to use when the door stops.
**SoundOnStopClosed** | Specifies the sound to use when the door stops closed.
**Volume** | Specifies the volume of the sound used.

[Advanced Door](#advanced-door)[Anim Door](#anim-door)[Door](#door)
