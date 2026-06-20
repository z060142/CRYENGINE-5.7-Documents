# Execution Order and Lifecycle

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/28184910
- Page ID: 28184910
- Breadcrumb: Entity > Execution Order and Lifecycle
- Parent: Entity

## Content

## Overview

This article aims to give an understanding of the order in which entities are updated, and when specific events are fired.

## Table of Contents

[Update and Execution Order](#update-and-execution-order)[Lifecycle](#lifecycle)[Conclusion](#conclusion)

## Update and Execution Order

Entities can receive three events tied to the main engine update:

Name | Description | Use case
--- | --- | ---
ENTITY_EVENT_PREPHYSICSUPDATE | Sent before a new physics step is started (note that the physics step itself will occur on a different thread). | Send physics requests to process with the next tick, causing minimal delay.
ENTITY_EVENT_COLLISION | Sent when collisions from the previous physics tick are being logged. | Handle collision events from Physics, for example to detect if a bullet hit an object.
ENTITY_EVENT_UPDATE | Occurs during the main update, where entities should execute main logic such as moving around. | The main update for entities, this is where we can interact with other entities or move our own entity instance (assuming it does not have a physical representation).

The order in which these are received is visualized below:

## Lifecycle

On the lowest level, an entity is created with [IEntitySystem::SpawnEntity](/docs/static/engines/cryengine-5/categories/28704770/pages/29797278), initialized with [IEntitySystem::InitEntity](/docs/static/engines/cryengine-5/categories/28704770/pages/29797278) (automatically done by SpawnEntity if not otherwise specified) and persists in the game world until it is removed by calling [IEntitySystem::RemoveEntity](/docs/static/engines/cryengine-5/categories/28704770/pages/29797278).

However, if an entity is not removed during the time a level is loaded - it will automatically be removed when the entity system unloads (see [IEntitySystem::Unload](http://docs.cryengine.com/pages/viewpage.action?pageId=29449832)), in the typical scenario whenever the level itself is unloaded.

The whole existence flow of an entity has been visualized below, and is combined with a series of events being fired as the level is loaded and the player is able to play:

## Conclusion

This concludes this article on the Execution Order of Entities. You may be interested in:

- [Networking](Networking.md)
- [Input and Action Mapping](Input%20and%20Action%20Mapping.md)
- [Physics and Movement](Physics%20and%20Movement.md)
