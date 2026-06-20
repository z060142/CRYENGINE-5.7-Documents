# RMI Functions

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/23306395
- Page ID: 23306395
- Breadcrumb: CRYENGINE Engine Code > Engine Modules > CryNetwork > RMI Functions
- Parent: CryNetwork

## Content

### Overview

RMIs are either sent by the function *InvokeRMI*, or if the RMI is dependent on another entity, by the function * InvokeRMIWithDependentObject*. * InvokeRMIWithDependentObject* is used to delay an RMI until the dependent object is known or updated to a specific state on the target machine.

For example, if a new entity is being spawned and an RMI is called on another entity with this new entities ID as a parameter, the network system will wait until the remote machine knows about the new entity and then send the RMI.

### Ordering

##### Available Flags

In file **IGameObject.h**, there are macros for declaring RMI classes (e.g. ** DECLARE_SERVER_RMI_...**). The following different declaration types exist:

- **PREATTACH:** The RMI is attached at the top of the data update for the object. This can be * used to prepare the remote entity for incoming new data.
- **POSTATTACH:** The RMI is attached at the bottom of the data update, so it will be called after the data has been serialized. This can be used to do something with the new data.
- **NOATTACH:** The RMI is not attached to any data update and thus can't rely on it. Can be used for calls that don't rely on data. It is recommended to prefer ** NOATTACH** RMI's as they are much easier to schedule due to their lower latency.
- **FAST:** The RMI Is being transfered immediately without waiting for a frame update. It is recommended to avoid this flag as it uses a lot of CPU to get a lower latency.

In order to forward RMI's to specific clients only, **InvokeRMI** can be called with the flag ** ERMInvocation::eRMI_ToClientChannel**.

##### Rules with Ordering

The ordering for RMI's is only applicable within the object and attachment type set.

For example:

- PLAYER RMI 1
- PLAYER RMI 2
- ITEM RMI 1
- PLAYER RMI 3

Assuming all are ordered, it is ensured that *PLAYER RMI 1-3* will arrive in that order, but * ITEM RMI 1* may arrive before or after the * PLAYER RMIs*.

Things are complicated further with **PREATTACH**, ** NOATTACH** and ** POSTATTACH**.

- All **PREATTACH** messages are ordered within themselves. As are ** NOATTACH** and ** POSTATTACH**.
- **NOATTACH** can fall either side of the below, but never inbetween.

![Image](https://www.cryengine.com/docs/static/attachments/23461154)

### Invoking a RMI function

The following functions in the **CGameObject** interface should be used to invoke an RMI call.

```
void InvokeRMI( const MI method, const T& params, unsigned where, int channel = -1 );
void InvokeRMIWithDependentObject( const MI method, const T& params, unsigned where, EntityId ent, int channel = -1 );
```

The *InvokeRMIWithDependentObject()* function will guarantees that a given entity exists on the other end. It can be used for messages involving multiple entities (i.e. Invoke a player RMI to pick up an item).

The where parameter should be one of the following flags.

Server RMIs

- **eRMI_ToClientChannel**: Specify destination channel as flag_specific_param
- **eRMI_ToOtherClients**: Specify client to ignore as flag_specific_param
- **eRMI_ToAllClients**:
- **eRMI_ToRemoteClients**: Will ignore local client

CLIENT RMIs

- **eRMI_ToServer**

### Examples

To define a function to be implemented as RMI, the **IMPLEMENT_RMI** #define from ** IGameObject.h** should be used.

```
#define IMPLEMENT_RMI(cls, name)
```

The following example implements a new function called ClEMP in the CPlayer class:

```
IMPLEMENT_RMI(CPlayer, ClEMP)
{
SNanoSuitEvent suitEvent;
suitEvent.event = eNanoSuitEvent_EMP_DISCHARGE;
suitEvent.fParam = params.time;  // params == EMPParams

this->SendActorSuitEvent(suitEvent);

return true;  // Always return true - false will drop connection
}
```

The following line will invoke the function:

```
pPlayer->GetGameObject()->InvokeRMI(CPlayer::ClEMP(), CPlayer::EMPParams(time), eRMI_ToClientChannel, pPlayer->GetChannelId());
```
