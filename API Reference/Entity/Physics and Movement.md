# Physics and Movement

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/26216224
- Page ID: 26216224
- Breadcrumb: Entity > Physics and Movement
- Parent: Entity

## Content

##
Overview

After loading geometry into a
[Slot](Slots%2C%20Geometry%20and%20Effects.md)
, we can create a physical entity (represented by the
[IPhysicalEntity](/docs/static/engines/cryengine-5/categories/28704770/pages/29797108)
interface) and add the physical geometry from the slots. This results in a physical representation of the entity that can interact with the world.

To physicalize an entity, we can call
[IEntity::Physicalize](/docs/static/engines/cryengine-5/categories/28704770/pages/29797019)
 (example contained within). This will create a physical entity for the entity of the specified type, and optionally create physical parts for individual or all entity slots. Note that physicalization of slots assumes the existence of a
**
physics proxy
**
, set up by the author in the DCC tool.

[Physicalize Example](/docs/static/engines/cryengine-5/categories/28704770/pages/29797019)
To query the physical entity of an entity, use
[IEntity::GetPhysicalEntity](/docs/static/engines/cryengine-5/categories/28704770/pages/29797019)
.

Once an entity is physicalized, we can optionally add physical parts for individual entity slots by calling
[IEntity::PhysicalizeSlot](/docs/static/engines/cryengine-5/categories/28704770/pages/29797019)
.

[Physicalize Slot Example](/docs/static/engines/cryengine-5/categories/28704770/pages/29797019)

##
Table of Contents

[API Types](#api-types)
[Physical Types](#physical-types)
[IPhysicalEntity functionality](#iphysicalentity-functionality)
[Listening to Collision Events](#listening-to-collision-events)
[Raycasts](#raycasts)
[Impulses](#impulses)
[Explosions](#explosions)
[Walking Characters](#walking-characters)
[Conclusion](#conclusion)

##
API Types

-
[IPhysicalWorld](/docs/static/engines/cryengine-5/categories/28704770/pages/29797387)

-
[IPhysicalEntity](/docs/static/engines/cryengine-5/categories/28704770/pages/29797108)

##
Physical Types

CRYENGINE provides many different
[IPhysicalEntity](/docs/static/engines/cryengine-5/categories/28704770/pages/29797108)
 implementations, represented by the pe_type enum:

Enum Entry
 |
Description
 |

PE_NONE
 |
Represents an entity with no physics type – physicalizing with this type will remove the existing physical entity attached to the entity.
 |

PE_STATIC
 |
Static object that other geometry can collide with, and will respond to queries – but cannot move on its own.
 |

PE_RIGID
 |
Dynamic object in the world that has a mass and can move around freely.
 |

PE_WHEELEDVEHICLE
 |
Specialization based on the rigid entity that allows for wheeled vehicle movements. Requires setting
pe_params_car
 at physicalization time.
 |

PE_LIVING
 |
Completely specialized class meant for walking FPS style actors – operates by casting a ray downwards every time step.
 |

PE_PARTICLE
 |
Used for simulating basic particles, such as gun tracers.
 |

PE_ARTICULATED
 |
Specialized implementation for ragdoll simulation.
 |

PE_ROPE
 |
Implementation that supports physicalized ropes with complex tension simulation.
 |

PE_SOFT
 |
Real-time cloth simulation type – please note that this type can easily become very costly on the CPU.
 |

PE_AREA
 |
Specialized setup that allows tracking entities inside a physical shape to create gravity and wind modifiers.
 |

##
IPhysicalEntity functionality

Once an entity has been physicalized, we can use the
[IPhysicalEntity](/docs/static/engines/cryengine-5/categories/28704770/pages/29797108)
interface directly to manipulate its physical behavior. The interface exposes, among others, four functions that are crucial to interacting with the physics at run-time:

##
IPhysicalEntity::SetParams

Used to set parameters implementing the
pe_params
 structure, will be queued and executed next time step unless executed on the physics thread with
bThreadSafe
 set to true.

[Example](/docs/static/engines/cryengine-5/categories/28704770/pages/29797108)

##
IPhysicalEntity::GetParams

Used to get parameters implementing the
pe_params
 structure. This will always execute immediately using locks, potentially interrupting the main and physics threads until done.

[Example](/docs/static/engines/cryengine-5/categories/28704770/pages/29797108)

##
IPhysicalEntity::GetStatus

Used to get status of the entity, implementing the pe_status structure. As with
[IPhysicalEntity::GetParams](/docs/static/engines/cryengine-5/categories/28704770/pages/29797108)
, this will always execute immediately using locks.

[Example](/docs/static/engines/cryengine-5/categories/28704770/pages/29797108)

##
IPhysicalEntity::Action

Executes an action, implementing the
pe_action
 structure. As with
[IPhysicalEntity::SetParams](/docs/static/engines/cryengine-5/categories/28704770/pages/29797108)
[this is queued by default.](/docs/static/engines/cryengine-5/categories/28704770/pages/29797108)

[Example](/docs/static/engines/cryengine-5/categories/28704770/pages/29797108)
The physics simulation is run on a different thread, this means that any attempt at setting data will be delayed until the next thread sync unless 'bThreadSafe' is set to true. This can be used if handling immediate events (such as ENTITY_EVENT_COLLISION_IMMEDIATE) that come directly from the physics thread, to avoid the request being queued.

Get functionality will always execute immediately without queuing.

##
Listening to Collision Events

Components can listen to collision events logged by physics by processing
[Cry::Entity::EEvent::PhysicsCollision (ENTITY_EVENT_COLLISION)](/docs/static/engines/cryengine-5/categories/28704770/pages/29797082)
. This event is fired the next frame after the collision was processed on the physics thread, and provides data through the EventPhysCollision structure - detailing the collision that occurred.

[Example](/docs/static/engines/cryengine-5/categories/28704770/pages/29797082)

##
Raycasts

It is often useful to trace a ray through the physical world, for example to let the user mouse-over or click on in-world objects. This is possible through the
[IPhysicalWorld::RayWorldIntersection](/docs/static/engines/cryengine-5/categories/28704770/pages/29797387)
 function.

[Example](/docs/static/engines/cryengine-5/categories/28704770/pages/29797387)

##
Impulses

Impulses can be triggered on individual physical entities using the
[pe_action_impulse](/docs/static/engines/cryengine-5/categories/28704770/pages/29797388)
 structure.

[Example](/docs/static/engines/cryengine-5/categories/28704770/pages/29797388)

##
Explosions

By using the
[IPhysicalWorld::SimulateExplosion](/docs/static/engines/cryengine-5/categories/28704770/pages/29797387)
 function we can enhance gameplay logic by supporting grenades and more things – effectively adding impulses to nearby entities based on a force and an origin point:

After done, any dynamic entities in the vicinity of the explosion point and radius will be impacted by the impulse.

[Example](/docs/static/engines/cryengine-5/categories/28704770/pages/29797387)

##
Walking Characters

As mentioned in the parent page, the
PE_LIVING
 physical entity type is specialized for walking type actors, specifically developed for games such as Far Cry and Crysis. Physicalizing a living entity is more intricate than static and rigid entities, as it requires setup with the
[pe_player_dimensions](/docs/static/engines/cryengine-5/categories/28704770/pages/29797495)
 and
[pe_player_dynamics](/docs/static/engines/cryengine-5/categories/28704770/pages/29797496)
 structures.

Once done, the entity will be physicalized and start casting a ray down every step to check if the player is on ground or not.

[Example](/docs/static/engines/cryengine-5/categories/28704770/pages/29797495)

##
Sending Movement Requests

The living entity will only move when a movement request is sent to it via the
[pe_action_move](/docs/static/engines/cryengine-5/categories/28704770/pages/29797494)
 structure. For example, to make the player move forward:

```

`
pe_action_move moveAction;
// Apply movement request directly to velocity
moveAction.iJump = 2;
moveAction.dir = Vec3(0, 1, 0);
physicalEntity.Action(&moveAction);
`

```

After that, the player will move forward – as if velocity was always 1m/s in the forward axis. This can for example be used to make the player jump and strafe.

##
Getting the Entity Status

We can query the living entity's status using the pe_status_living structure, in addition to
[pe_status_dynamics](/docs/static/engines/cryengine-5/categories/28704770/pages/29797507)
. For example:

```

`
pe_status_living livingStatus;
if (pPhysicalEntity->GetStatus(&livingStatus) != 0)
{
  const bool isOnGround = !livingStatus.bFlying;
  // Store the ground normal in case it is needed
  // Note that users have to check if we're on ground before using, is considered invalid in air.
  const Vec3& groundNormal = livingStatus.groundSlope;
}

// Get the player's velocity from physics
pe_status_dynamics playerDynamics;
if (pPhysicalEntity->GetStatus(&playerDynamics) != 0)
{
  const Vec3& velocity = playerDynamics.v;
}
`

```

Note that walking character handling is automated by the Character Controller Component in the default components plug-in, see
Cry::DefaultComponents::CCharacterControllerComponent
.

##
Conclusion

This concludes the article on Physics and Movement, you may be interested in:

-
[Characters and Animations](Characters%20and%20Animations.md)

-
[Networking](Networking.md)
