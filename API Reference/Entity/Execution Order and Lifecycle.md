# Execution Order and Lifecycle

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/28184910
- Page ID: 28184910
- Breadcrumb: Entity > Execution Order and Lifecycle
- Parent: Entity

## Content

##
Overview

This article aims to give an understanding of the order in which entities are updated, and when specific events are fired.

##
Table of Contents

[#update-and-execution-order](
Update and Execution Order
)
[#lifecycle](
Lifecycle
)
[#conclusion](
Conclusion
)

##
Update and Execution Order

Entities can receive three events tied to the main engine update:

Name
 |
Description
 |
Use case
 |

ENTITY_EVENT_PREPHYSICSUPDATE
 |
Sent before a new physics step is started (note that the physics step itself will occur on a different thread).
 |
Send physics requests to process with the next tick, causing minimal delay.
 |

ENTITY_EVENT_COLLISION
 |
Sent when collisions from the previous physics tick are being logged.
 |
Handle collision events from Physics, for example to detect if a bullet hit an object.
 |

ENTITY_EVENT_UPDATE
 |
Occurs during the main update, where entities should execute main logic such as moving around.
 |
The main update for entities, this is where we can interact with other entities or move our own entity instance (assuming it does not have a physical representation).
 |

The order in which these are received is visualized below:

##
Lifecycle

On the lowest level, an entity is created with
[/docs/static/engines/cryengine-5/categories/28704770/pages/29797278](
IEntitySystem::SpawnEntity
)
, initialized with
[/docs/static/engines/cryengine-5/categories/28704770/pages/29797278](
IEntitySystem::InitEntity
)
 (automatically done by SpawnEntity if not otherwise specified) and persists in the game world until it is removed by calling
[/docs/static/engines/cryengine-5/categories/28704770/pages/29797278](
IEntitySystem::RemoveEntity
)
.

However, if an entity is not removed during the time a level is loaded - it will automatically be removed when the entity system unloads (see
[http://docs.cryengine.com/pages/viewpage.action?pageId=29449832](
IEntitySystem::Unload
)
), in the typical scenario whenever the level itself is unloaded.

The whole existence flow of an entity has been visualized below, and is combined with a series of events being fired as the level is loaded and the player is able to play:

##
Conclusion

This concludes this article on the Execution Order of Entities. You may be interested in:

-
[/docs/static/engines/cryengine-5/categories/23756813/pages/26216232](
Networking
)

-
[/docs/static/engines/cryengine-5/categories/23756813/pages/29428286](
Input and Action Mapping
)

-
[/docs/static/engines/cryengine-5/categories/23756813/pages/26216224](
Physics and Movement
)
