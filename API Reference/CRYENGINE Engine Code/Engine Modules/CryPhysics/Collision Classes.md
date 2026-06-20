# Collision Classes

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/23306413
- Page ID: 23306413
- Breadcrumb: CRYENGINE Engine Code > Engine Modules > CryPhysics > Collision Classes
- Parent: CryPhysics

## Content

##
Overview

Collision classes are used for filtering collision between two physical-entities. A collision-class comprises two 32-bit uints, a
**
type
**
, and an
**
ignore
**
.

With Collision Classes you can define specific scenarios such as "player only collisions" which are objects passable by AI actors and impassable by players. This feature allows you to configure filtering of the collision between physical entities independently of their collision types.

##
Setup

Physical entities can be supplied with one or more collision class and can ignore one or more collision classes. A new physical attribute
**
ignore_collision
**
 is introduced to the
**
 surface type
**
 definition.

```

`
<SurfaceType name="mat_nodraw_ai_passable">
  <Physics friction="0" elasticity="0"  pierceability="15" ignore_collision="collision_class_ai"/>
</SurfaceType>

`

```

All physical entity types (LivingEntity, ParticleEntity, etc.) are supplied with default collision classes (collision_class_living, collision_class_particle, etc.). Living entity has one additional game specific collision class -
**
 collision_class_ai
**
 for AI actors or
**
collision_class_player
**
 for players.

```

`
Player = {
...
  physicsParams =
  {
    collisionClass=collision_class_player,
  },
...
}
`

```

```

`
BasicAI = {
...
  physicsParams =
  {
    collisionClass=collision_class_ai,
  },
...
}
`

```

##
Code

```

`
struct SCollisionClass
{
    uint32 type;     // collision_class flags to identify the entity
    uint32 ignore;   // another entity will be ignored if *any* of these bits are set in its type
};
`

```

The
**
type
**
 identifies which collision classes the pent belongs to.

There are some classes defined in CryPhysics, for example:

-
collision_class_terrain

-
collision_class_wheeled

-
collision_class_living

-
collision_class_articulated

-
collision_class_soft

-
collision_class_roped

-
collision_class_particle
... and some defined in
**
GamePhysicsSettings.h
**
, starting from the collision_class_game bit.

```

`
#define GAME_COLLISION_CLASSES(f) \
    f( gcc_player_capsule,     collision_class_game << 0) \
    f( gcc_player_body,        collision_class_game << 1) \
    f( gcc_pinger_capsule,     collision_class_game << 2) \
    f( gcc_pinger_body,        collision_class_game << 3) \
    f( gcc_vehicle,            collision_class_game << 4) \
    f( gcc_large_kickable,     collision_class_game << 5) \
    f( gcc_ragdoll,            collision_class_game << 6) \
    f( gcc_rigid,              collision_class_game << 7) \
    f( gcc_alien_drop_pod,     collision_class_game << 8) \
    f( gcc_vtol,               collision_class_game << 9) \
`

```

All these are automatically exposed to lua.
**
Brushes
**
, and most objects have the collision classes available in the properties through the editor.

##
Types

Types, you can set as many bits as you like or even zero.

For example, let's say you have these classes LIVING, PLAYER, TEAM1, TEAM2, AI, AI_1, AI_2.

```

`
SCollisionClass player1(0,0), player2(0,0), ai1(0,0), ai7(0,0), object1(0,0);

player1.type = LIVING|PLAYER|TEAM1;
player2.type = LIVING|PLAYER|TEAM2;
ai1.type = LIVING|AI|AI_1;
ai7.type = LIVING|AI|AI_2;
object1.type = 0;
`

```

**
player1
**
 belongs to the
*
living entity
*
 class, the
*
player
*
 class, and
*
team1
*
.

##
Filtering the collision

Filtering occurs by checking the
**
type
**
 of one entity against the
**
ignore
**
 of another entity.

This is done boths ways, and if an bits overlap then the collision is ignored. i.e:

```

`
bool ignoreCollision = (A->type & B->ignore) || (A->ignore & B->type);
`

```

So, if you want
*
ai7
*
 to ignore collisions with anything that has
*
AI_1
*
 set then you'd add
*
AI_1
*
 to the ignore flags. i.e:

ai7.ignore = AI_1

If you want object1 to ignore all living physical entities:

object1.ignore=LIVING

##
Interface

For code see
**
physinterface.h
**
 and
**
GamePhysicsSettings.h
**

*pe_collision_class

**
struct SCollisionClass
**

**
pe_params_collision_class
**
 - is used to access and set the collision classes on the physical-entity

GamePhysicsSettings.h has helpers for setting these and additional ignore maps.

In lua, see
**
SetupCollisionFiltering
**
 and
**
ApplyCollisionFiltering
**
. lua script-binding is done through
**
SetPhysicParams(PHYSICPARAM_COLLISION_CLASS)
**
