# Entity

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/26216196
- Page ID: 26216196
- Breadcrumb: Entity

## Child Pages

- [Components](Entity/Components.md)
- [Slots, Geometry and Effects](Entity/Slots, Geometry and Effects.md)
- [Physics and Movement](Entity/Physics and Movement.md)
- [Characters and Animations](Entity/Characters and Animations.md)
- [Players and Connections](Entity/Players and Connections.md)
- [Networking](Entity/Networking.md)
- [Audio](Entity/Audio.md)
- [Execution Order and Lifecycle](Entity/Execution Order and Lifecycle.md)
- [Areas and Triggers](Entity/Areas and Triggers.md)
- [Input and Action Mapping](Entity/Input and Action Mapping.md)
- [Cameras](Entity/Cameras.md)

## Content

##
Overview

**
Entities
**
 represent elements in the world that can move, act and behave logically in the world - as opposed to a rock that won't change over time. Entities by themselves do not contain logic, but can contain
**
Components
**
 - user-authored bits of code that can manipulate their parent entity at run time. Examples include light sources, physicalized objects (such as bullets), and players.

**

**

Entities were previously known as Game Objects, and Entity Components were referred to as "Game Object Extensions".

[/docs/static/engines/cryengine-5/categories/23756816/pages/26870341](
Blue
SWITCH TO MANUAL
)

##
Table of Contents

[#api-types](
API Types
)
[#components](
Components
)
[#identifiers](
Identifiers
)
[#transform-and-parent-child-hierarchy](
Transform & Parent / Child Hierarchy
)
[#slots-entity-geometry](
Slots / Entity Geometry
)
[#conclusion](
Conclusion
)

##
API Types

-
[/docs/static/engines/cryengine-5/categories/28704770/pages/29797278](
IEntitySystem
)

-
[/docs/static/engines/cryengine-5/categories/28704770/pages/29797019](
IEntity
)

##
Components

Entities themselves cannot contain custom logic. Instead, they can contain
**
Components
**
. For example, a Camera component could be attached to an entity, exposing functionality for rendering a specific viewpoint in the level:

[Image: /docs/static/attachments/29919088]

Entities are stored and managed in the
**
Entity System
**
, represented by the
[/docs/static/engines/cryengine-5/categories/28704770/pages/29797278](
IEntitySystem
)
 interface, and accessible through
*
gEnv->pEntitySystem
*
. The system is responsible for spawning, managing entities throughout their lifetime, and finally removing them. See
[/docs/static/engines/cryengine-5/categories/28704770/pages/29797278](
IEntitySystem::SpawnEntity
)
 for an example on how to spawn entities.

[/docs/static/engines/cryengine-5/categories/28704770/pages/29797278](
SpawnEntity Example
)

##
Identifiers

After being spawned, each entity is assigned an entity
**
identifier
**
, represented by the
*
EntityId
*
 type definition. Entity identifiers are 32-bit and consist of two parts: a 16-bit
**
salt
**
, used to facilitate re-use of each index without resulting in Entity Identifiers being reused over the lifetime of the application, and a 16-bit
**
index
**
, representing the
**
position
**
 of the entity in the entity system’s internal storage. This allows for constant-time retrieval of an entity, as we can simply look up an entity by index in contiguous storage.

[Image: /docs/static/attachments/29923925]

This means that despite being a 32-bit unsigned integer, the index is only 16 bits – resulting in a max limit of 65533 entities in the world at any given time
(0 and 65534+ are reserved).
Any game expecting to exceed this number would need to stream in logical entities using a custom setup tailored for the project.

##
Globally Unique Identifier

Entities are also assigned globally unique identifiers, noted by the
EntityGUID
 type definition. These identifiers differ from entity IDs in that they are guaranteed to be the same when saving and loading entities – allowing the Editor and other systems to track which entity belongs where.

EntityId
s are
**
not
**
 unique across sessions or over the network. The same entity in a multiplayer match is very likely to have different identifiers on two clients.

The multiplayer aspect of this applies to
EntityGUID
s as well – please see Entity Networking to find out how entities can be identified over the network.

##
Transform & Parent / Child Hierarchy

Entities in CRYENGINE have a
**
transform
**
 by default, meaning they have
**
location
**
,
**
orientation
**
 and
**
scale
**
 in relation to their
**
parent
**
 (and if no parent, to the
**
world
**
). We can retrieve the world transformation through the following functions:

[/docs/static/engines/cryengine-5/categories/28704770/pages/29797019](
IEntity::GetWorldTM
)

[/docs/static/engines/cryengine-5/categories/28704770/pages/29797019](
IEntity::GetWorldPos
)

[/docs/static/engines/cryengine-5/categories/28704770/pages/29797019](
IEntity::GetWorldRotation
)

[/docs/static/engines/cryengine-5/categories/28704770/pages/29797019](
IEntity::GetWorldScale
)
Similarly, we can change the world transformation easily using

[/docs/static/engines/cryengine-5/categories/28704770/pages/29797019](
IEntity::SetWorldTM
)

##
Hierarchy

Entities can be
**
linked
**
 together in a hierarchy, ensuring that the entity's position is relative to the parent. This is useful to pair entities together in a parent / child relationship where the child should always follow its parent.

An entity can be linked to a parent at
[/docs/static/engines/cryengine-5/categories/28704770/pages/29797259](
spawn time
)
, or at any point during an
[/docs/static/engines/cryengine-5/categories/28704770/pages/29797019](
during an instance's lifetime
)
.

Once linked, we can retrieve the local-space transformation (relative to the parent) of the entity through the following functions:

[/docs/static/engines/cryengine-5/categories/28704770/pages/29797019](
IEntity::GetLocalTM
)
[/docs/static/engines/cryengine-5/categories/28704770/pages/29797019](
IEntity::GetPos
)
[/docs/static/engines/cryengine-5/categories/28704770/pages/29797019](
IEntity::GetRotation
)
[/docs/static/engines/cryengine-5/categories/28704770/pages/29797019](
IEntity::GetScale
)
The local transformation can be modified using

[/docs/static/engines/cryengine-5/categories/28704770/pages/29797019](
IEntity::SetLocalTM
)

##
Slots / Entity Geometry

For more information, see
[/docs/static/engines/cryengine-5/categories/23756813/pages/26216230](
Slots, Geometry and Effects
)
.

##
Conclusion

This concludes the article on entities. You may also be interested in:

-
[/docs/static/engines/cryengine-5/categories/23756813/pages/26871489](
Components
)

-
[/docs/static/engines/cryengine-5/categories/23756813/pages/28184910](
Execution Order and Lifecycle
)

-
[/docs/static/engines/cryengine-5/categories/23756813/pages/26216232](
Networking
)
