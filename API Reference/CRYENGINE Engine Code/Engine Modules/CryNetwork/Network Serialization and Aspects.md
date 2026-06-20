# Network Serialization and Aspects

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/26874253
- Page ID: 26874253
- Breadcrumb: CRYENGINE Engine Code > Engine Modules > CryNetwork > Network Serialization and Aspects
- Parent: CryNetwork

## Content

### Overview

Network serialization in the CryEngine happens at the entity level. Entities that should be synchronized have to be bound to network by calling **GetNetEntity()->BindToNetwork().**

To serialize the data of an entity on a regular basis, do either of the following:

- Provide **IEntityComponent::NetSerialize()** implementation if you're using the newer entity system and entity components.
This function uses a TSerialize object of type ISerialize to transform relevant data to a stream.
- Override **IGameObjectExtension::NetSerialize()** if you're still on gameobject extensions. Keep in mind that this is going to be deprecated and you should probably migrate to IEntityComponents at some point.

In either case, also provide a **GetNetSerializeAspectMask()** implementation in the respective class to let CryNetwork know the bitmask of active aspects for this component/extension.

The serialization follow different aspects and profiles to distinguish the types of stream.

Important
Serialized data for a given aspect and profile must remain fixed. In example, if you serialized four floats, you must always serialize four floats.

CryNetwork doesn't keep track of the serializable data that is changed during the game, so you need to tell CryNetwork explicitly when to synchronize an aspect by calling either **IEntityComponent::NetMarkAspectsDirty** or ** CGameObject::MarkAspectsDirty**.

### Aspects

Aspects should be used to group data that logically belongs together, especially important given the constraints of compression.

Information about GameObjects is being propagated through the network by the function *RequestRemoteUpdate()* which takes * EEntityAspects* flags as a parameter to determine how the update should be performed.

The aspects are defined as follows:

- **eEA_GameClient**: Information that gets sent from the client to the server if the client has authority over the object. Originally, only players and vehicles driven by the player will ever send data on this aspect.
- **eEA_GameServer:** The normal server to client data stream.
- **...Dynamic/Static**: Usually every data which is constantly changing should go into the Dynamic aspect and objects which change rarely should go on the Static aspect. The idea is that updates are not sent if just one value changes.
- **eEA_Script**: Used where script network data is transported, including any Script-RMI calls.
- **eEA_Physics**: Used where physics data is being transported. It is not divided into Client/Server because it is always using the same path: *(Controlling-client) -> Server -> Other clients*

### Profiles

Profiles allow particular aspects fixed format data to be different. There are potentially 8 profiles per aspect. Usually they are only used for physics aspects (i.e. switching between ragdoll and living entity). Profiles requires the aspect to be setup using the *eAF_ServerManagedProfile* flag.

### Compression

The network layer takes care of compression and quantization based on the usage of Tserialize::Value. The quantization and/or compression can be controlled via a compression policy.

The different quantization and compression types are defined inside the XML file: `Game/Scripts/Network/CompressionPolicy.xml`. A 4 character code will be assigned to the type.

Here is an entry example:

```
<policy name="team" impl="RangedInt">
<params min="0" max="7" />
</policy>
```

The policy implementation are written in C++ and can be found within the CryNetwork project.

Here is the list of policies currently implemented:

- AdaptiveBool (CAdaptiveBoolPolicy)
- AdaptiveBool2 (CAdaptiveBoolPolicy2)
- AdaptiveFloat (CAdaptiveFloatPolicy)
- AdaptiveOrientation (CAdaptiveOrientationPolicy)
- AdaptiveUnitVec3 (CAdaptiveUnitVec3Policy)
- AdaptiveVec3 (CAdaptiveVec3Policy)
- AdaptiveVelocity (CAdaptiveVelocityPolicy)
- Velocity (CAdaptiveVelocityPolicy)
- BiggerOrSmaller (CBiggerOrSmallerPolicy)
- Default (CDefaultPolicy)
- EntityId (CEntityIdPolicy)
- SimpleEntityId (CSimpleEntityIdPolicy)
- FloatAsInt (CFloatAsIntPolicy)
- Jumpy (CJumpyPolicy)
- NoSend (CNoSendPolicy)
- QuantizedVec3 (CQuantizedVec3Policy)
- RangedInt (CRangedIntPolicy)
- StringTable (CStringTablePolicy)
- Time (CTimePolicy)
- TableDirVec3 (TTableDirVec3)

It's possible to implement a new policy inside CryNetwork by deriving the *ICompressionPolicy* interface and calling the * REGISTER_COMPRESSION_POLICY(class, name)* macro.
