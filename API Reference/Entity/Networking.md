# Networking

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/26216232
- Page ID: 26216232
- Breadcrumb: Entity > Networking
- Parent: Entity

## Content

## Overview

Networking in the engine is made possible by the **CryNetwork** module, and is exposed to entities via the [INetEntity](/docs/static/engines/cryengine-5/categories/28704770/pages/29797256)interface - accessible via [IEntity::GetNetEntity](/docs/static/engines/cryengine-5/categories/28704770/pages/29797019). Entities are by default not networked, but can be bound to the network during spawning - if a component calls [INetEntity::BindToNetwork](/docs/static/engines/cryengine-5/categories/28704770/pages/29797256) before [IEntitySystem::InitEntity](/docs/static/engines/cryengine-5/categories/28704770/pages/29797278) is called on the entity.

Once bound to the network, entities are assigned an network object identifier ([SNetObjectID](/docs/static/engines/cryengine-5/categories/28704770/pages/29797372)), that is used to uniquely identify the entity over the network.

Entity identifiers are **not** guaranteed to be the same over the network, and can therefore not be sent without being converted. See the [Compression Policies](Networking.md#Networking-CompressionPolicies) section below.

## Table of Contents

[API Types](#api-types)[Channels](#channels)[Compression Policies](#compression-policies)[Scheduling](#scheduling)[Remote Method Invocations](#remote-method-invocations)[Network Serialization and Aspects](#network-serialization-and-aspects)[Spawn Replication Serialization](#spawn-replication-serialization)[Packet Rate & Bandwidth](#packet-rate-and-bandwidth)[Conclusion](#conclusion)

## API Types

- [INetwork](/docs/static/engines/cryengine-5/categories/28704770/pages/29797379)
- [INetEntity](/docs/static/engines/cryengine-5/categories/28704770/pages/29797256)
- [INetContext](/docs/static/engines/cryengine-5/categories/28704770/pages/29797328)
- [SNetObjectID](/docs/static/engines/cryengine-5/categories/28704770/pages/29797372)
- [ISerialize](/docs/static/engines/cryengine-5/categories/28704770/pages/29797419)
- [SRmi](/docs/static/engines/cryengine-5/categories/28704770/pages/29797556)

## Channels

A channel represents a connection to another engine instance, and is known in code as [INetChannel](/docs/static/engines/cryengine-5/categories/28704770/pages/29797324). By default, the server has one net channel per client, and each client has a single net channel to communicate with the server.

Each channel has a unique identifier that is used to identify the connection, and is commonly used during connections for example to identify a player on the server. However, keep in mind that the channel identifier is not networked so this should not be serialized over the network as with entity identifiers.

## Compression Policies

All networked data is serialized through the [ISerialize](/docs/static/engines/cryengine-5/categories/28704770/pages/29797419) construct, specifically through the ISerialize::Value function. A very important aspect of this function is the ability to provide the optional third parameter to specify a **compression policy**. Compression policies allow specifying size and ranges of data that is transferred over the network, ensuring that we keep used bandwidth as low as possible.

The default compression policies can be seen in Engine/Config/DefaultScripts/CompressionPolicy.xml. For example, the 'eid' policy is used to automatically convert entity identifiers across the networks to their remote equivalents. This is useful since entity identifiers are not guaranteed to be the same on different instances of the game. For example:

```
ser.Value("myEntityId", myEntityId, 'eid');
```

This would, when writing read the value of 'myEntityId', look up its internal [SNetObjectID](/docs/static/engines/cryengine-5/categories/28704770/pages/29797372) and serialize it over the network. The receiving instance of the engine would then deserialize the local equivalent into 'myEntityId', ensuring that we are referring to the same entity instance across machines.

Have a look at the different compression policies that are available, compressing data over the network can be crucial to keep both client and server bandwidth usage within sustainable levels. It is also possible to add custom policies, or override default ones, by adding a Scripts/Network/CompressionPolicy.xml file to your assets directory. We can then use the same format from the default XML mentioned above.

It is recommended to use compression policies from the very beginning of writing networked code. It will always be easier to think about usage upfront rather than going through an entire code base to optimize bandwidth later during production.

### Commonly used default compression policies

Seen below is a table of the most commonly used compression policies included with the engine by default, as well as their bandwidth usage and limits. Keep in mind that the use of history delta (see Aspects below) may decrease bandwidth usage further.

Identifier | Description | Maximum Bandwidth Usage | Limits
--- | --- | --- | ---
'eid' | Used to automatically convert a local entity identifier to the remote equivalent. | Adaptive | N/A
'wrld' | Represents a world coordinate. | 72 bits | 0 to 4096 for X and Y axes, 0 to 1023 for the Z axis
'lwld' | Represents a world or local coordinate. | 72 bits | -20 to 4096 for X and Y axis, -20 to 1023 for the Z axis
'wrl2' | Represents a world coordinate, adaptive by assuming a probable height of 1024. | 72 bits | 0 to 4096 for the X and Y axes, 0 to 2047 for the Z axis
'wrl3' | Represents a world coordinate that can be outside of terrain bounds, adaptive by assuming a probable height of 1024. | 88 bits | -2045 to 6145 for the X and Y axes, -2095 to 6145 for the Z axis
'frad' | Commonly used to represent radians as float. | 12 bits | -4 to 4
'rpos' | Represents a relative position. | 30 bits | -10 to 10
'smal' | Represents a small float. | 8 bits | 0 to 16
'sone' | Represents a normalized float. | 10 bits | -1 to 1
'tod' | Represents a time of day. | 11 bits | 0 to 24
'i8' | Signed 8-bit number. | 8 bits | -128 to 127
'i16' | Signed 16-bit number. | 16 bits | -32768 to 32767
'i32' | Signed 32-bit number. | 32 bits | -2147483647 to 2147483647
'ui2' | Unsigned 2-bit number. | 2 bits | 0 to 3
'ui3' | Unsigned 3-bit number. | 3 bits | 0 to 7
'ui4' | Unsigned 4-bit number. | 4 bits | 0 to 15
'ui5' | Unsigned 5-bit number. | 5 bits | 0 to 31
'ui6' | Unsigned 6-bit number. | 6 bits | 0 to 63
'ui8' | Unsigned 8-bit number. | 8 bits | 0 to 255
'ui9' | Unsigned 9-bit number. | 9 bits | 0 to 511
'ui10' | Unsigned 11-bit number. | 10 bits | 0 to 1023
'ui16' | Unsigned 16-bit number. | 16 bits | 0 to 65535
'ui32' | Unsigned 32-bit number. | 32 bits | 0 to 4294967294
'bool' | Boolean (true / false). | 1 bit | 0 to 1
'ori1' | Normalized orientation / Quaternion. | 8 bits | -1 to 1
'ori3' | Normalized orientation / Quaternion (higher precision than 'ori1'). | 12 bits | -1 to 1
'dir0' | Normalized vector / direction. | 10 bits | -1 to 1
'dir1' | Normalized vector / direction (higher precision than 'dir0'). | 12 bits | -1 to 1
'dir2' | Normalized vector / direction (higher precision than 'dir1'). | 16 bits | -1 to 1
'dir3' | Normalized vector / direction (higher precision than 'dir2'). | 24 bits | -1 to 1
'mat' | Surface type identifier. | 9 bits | -1 to 255

## Scheduling

In addition to compression policies, it is also possible to customize the scheduling priority of packets on a per-entity basis. For example, this allows us to prioritize players over other entities. An example of the default scheduler setup can be seen in Engine/Config/DefaultScripts/Scheduler.xml.

## Remote Method Invocations

Remote Method Invocations (RMIs) allow for executing functions remotely between a client and a server. Note that RMIs can **not** be used to communicate between multiple clients. They are represented in code by the [SRmi](/docs/static/engines/cryengine-5/categories/28704770/pages/29797556) structure. Each remote method can contain a set of parameters that need to be serialized with the same ISerialize interface and structure that is used for aspect serialization.

[Example](/docs/static/engines/cryengine-5/categories/28704770/pages/29797556)

## Network Serialization and Aspects

Each networked entity is able to serialize data over the network whenever a specific **aspect** (see EEntityAspects) is changed. For example, assuming we had a boolean named m_bWalking, we could serialize this over the network to make sure that all clients and the server know the current synchronized state. Each entity can have up to 32 aspects which are independently serialized whenever it is marked "dirty" by game code.

There is no overhead on using all aspects, it can often be useful to split serialization into multiple aspects in order to reduce bandwidth usage.

It is recommended to group variables in aspects based on rate of change, as they will need to be serialized at the same time. For example, position and rotation are commonly serialized together - while health is independent.

When handling serialized data we first have to pick a unique aspect that we want to transmit data with. For example, assuming that we want to serialize data from clients to the server and other clients, we could choose eEA_GameClientD. Any time the data we last sent over the network is changed, we’ll need to call IGameObject::ChangedNetworkState, effectively marking the aspect as dirty resulting in [IEntity::NetSerialize](/docs/static/engines/cryengine-5/categories/28704770/pages/29797021) being called to read the data.

[Example](/docs/static/engines/cryengine-5/categories/28704770/pages/29797021)

### Aspect History and Deltas

The biggest benefit aspects have over RMIs is the built-in handling of aspect history. This means that both server and client will remember what was last sent to the remote side, allowing us to use delta compression to only send changed data to the network - instead of requiring a full refresh of each aspect every time it is marked dirty.

This is an efficient tool for optimizing your bandwidth usage, and should be relied upon as much as possible. Keep in mind that the deserialization call will always override data with what was on the server, even if delta compression was used to lower amount that had to be sent. This means that the non-authoritative client cannot modify serialized values freely without it potentially being overridden on deserialization.

### Aspect Delegation

Typically (and by default), entities are controlled by the server. However, in certain cases it is necessary to delegate control of an aspect to the client. Usually, this is done to improve responsiveness on the client, but requires trusting the client - which can lead to cheats being developed with relative ease.

In order to enable delegation of a specific aspect on an entity, we first need to call [INetEntity::EnableDelegatableAspect:](/docs/static/engines/cryengine-5/categories/28704770/pages/29797256) We can then call [INetContext::DelegateAuthority](/docs/static/engines/cryengine-5/categories/28704770/pages/29797328).

[Example](/docs/static/engines/cryengine-5/categories/28704770/pages/29797328)

## Spawn Replication Serialization

It can often be useful to serialize data on an entity at spawn-time. This is used to spawn an entity with predefined components and data on the server side, and automatically deserialize that particular set of data when the entity is spawned on the remote client(s).

This is achieved by overriding the [IEntityComponent::NetReplicateSerialize](/docs/static/engines/cryengine-5/categories/28704770/pages/29797021) function, and attaching components to an entity before IEntitySystem::Init is called.

[Example](/docs/static/engines/cryengine-5/categories/28704770/pages/29797021)

## Packet Rate & Bandwidth

The networking system exposes a set of [CVars](../_Console.md) with which we can increase packet rate or bandwidth for both server and client:

Name | Description
--- | ---
net_defaultPacketRate | The desired packet rate
net_availableBandwidthServer | The available bandwidth for the server
net_availableBandwidthClient | The available bandwidth for the local client
sv_DedicatedMaxRate | The simulation rate for the dedicated server, caps the maximum number of "frames" / engine ticks to this value. Equivalent to 'sys_maxfps' on a client.

## Conclusion

That concludes the article on Networking. You may be interested in:

- [Execution Order and Lifecycle](Execution%20Order%20and%20Lifecycle.md)
