# Flow Graph Entity Containers

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/29450531
- Page ID: 29450531
- Breadcrumb: Scripting > Flow Graph Overview > Flow Graph Entity Containers
- Parent: Flow Graph Overview

## Content

Entity Containers are a system to manage and operate on sets of entities within the FlowGraph logic.

![Image](https://www.cryengine.com/docs/static/attachments/44971126)

### Overview

An Entity Container is a way to define a set/list/group of entities that can then be dynamically changed and used with FlowGraph logic.

Common useful operations that can be applied to the containers are to add/remove entities, query if entities are in a container, listen, iterate over the container entities and apply an action to them, such as hiding or unhiding.

### Setting up an Entity Container

An Entity Container is itself an entity. To configure one:

- Add an entity of type Entity Container to a level
- Set its initial contents by [linking entities](../../Editor%20Tools/Level%20Editor%20Tab/Level%20Explorer/Object%20Linking.md) in the Properties tab.

![Image](https://www.cryengine.com/docs/static/attachments/44971127)

### Using Entity Containers

The entity containers are meant to be used via FlowGraph with the nodes in the category **GameEntity:Containers**. A container can be identified by its Entity ID.

![Image](https://www.cryengine.com/docs/static/attachments/35395043)

The available nodes allow:

- editing the container.
- operations between different containers.
- querying if an entity is in the container.
- querying and ordering the container entities by proximity to another entity.
- listening for events of the entities in the container.
- applying an action to all entities of a container by iterating with a combination of "QueryContainerSize" and "QueryEntityByIndex" or with the "Actions" node by running a [Flow Graph Module](/docs) on each entity.

[Setting up an Entity Container](#setting-up-an-entity-container)[Using Entity Containers](#using-entity-containers)
