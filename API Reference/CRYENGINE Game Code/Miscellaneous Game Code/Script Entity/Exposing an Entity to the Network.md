# Exposing an Entity to the Network

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/23306593
- Page ID: 23306593
- Breadcrumb: CRYENGINE Game Code > Miscellaneous Game Code > Script Entity > Exposing an Entity to the Network
- Parent: Script Entity

## Content

##
Overview

Script Entity can serialized value on the network. The approach is done by setting the values on the server and having these automatically synchronized on all the clients. It's also possible to invoke client/server RMI functions.

Keep in mind the following limitations:

-
No notification that a serialized value has changed.

-
Server controlled only, there is no way to set values to be client.

##
Exposing a Script Entity to CryNetwork

The ScriptBind function
*
Net.Expose()
*
 required to be called to define the network features of the entity.

The following code demonstrate how to call the
*
Net.Expose()
*
 function. It should be written inside the .lua script within the global space rather than in a function.

```

`
Net.Expose {
  Class = DeathMatch,
  ClientMethods = {
    ClVictory              = { RELIABLE_ORDERED, POST_ATTACH, ENTITYID, },
    ClNoWinner             = { RELIABLE_ORDERED, POST_ATTACH, },

    ClClientConnect        = { RELIABLE_UNORDERED, POST_ATTACH, STRING, BOOL },
    ClClientDisconnect     = { RELIABLE_UNORDERED, POST_ATTACH, STRING, },
    ClClientEnteredGame    = { RELIABLE_UNORDERED, POST_ATTACH, STRING, },
  },
  ServerMethods = {
    RequestRevive          = { RELIABLE_UNORDERED, POST_ATTACH, ENTITYID, },
    RequestSpectatorTarget = { RELIABLE_UNORDERED, POST_ATTACH, ENTITYID, INT8 },
  },
  ServerProperties = {
    busy   = BOOL,
  },
};

`

```

##
RMI functions

The RMI function should be defined in either the ClientMethods and ServerMethods tables passed to the
*
Net.Expose()
*
 function.

Order flag

 |
Description

 |

**
UNRELIABLE_ORDERED
**

 |
 |

**
RELIABLE_ORDERED
**

 |
 |

**
RELIABLE_UNORDERED
**

 |
 |

These descriptors control how the RMI is scheduled within the serialization data.

RMI attach flag

 |
Description

 |

**
NO_ATTACH
**

 |
No special control (preferred)

 |

**
PRE_ATTACH
**

 |
Call should come before the serialized data

 |

**
POST_ATTACH
**

 |
Call should come after the serialized data

 |

The functions can be declared like this:

```

`
function DeathMatch.Client:ClClientConnect(name, reconnect)

`

```

It can then be called like one of the the three following examples:

```

`
self.allClients:ClVictory( winningPlayerId );

`

```

```

`
self.otherClients:ClClientConnect( channelId, player:GetName(), reconnect );

`

```

```

`
self.onClient:ClClientConnect( channelId, player:GetName(), reconnect );

`

```

More information on RMI functions can be found in the Technical Documentation
[/docs/static/engines/cryengine-5/categories/23756813/pages/23306395](
RMI Functions
)
.

Note: Script networking doesn't have an equivalent to the dependent object RMIs.

##
ServerProperties

Inside the entity table, there should be a ServerProperties table that indicate which property need to be synchronized. This is also the place to define the variable type of the value.

##
Exposing a Script Entity to CryAction with a GameObject

It is also needed to create a GameObject in CryAction and to bind this new GameObject to the network game session. Ideally the following code should be placed in the
*
OnSpawn()
*
 function.

```

`
CryAction.CreateGameObjectForEntity(self.id);
CryAction.BindGameObjectToNetwork(self.id);

`

```

It's also possible to instruct the GameObject to receive a per frame update callback.

The following function call to CryAction will enable the update callback:

```

`
CryAction.ForceGameObjectUpdate(self.id, true);

`

```

The script entity will receive the
*
OnUpdate
*
 function callback of its Server table.

```

`
function Door.Server:OnUpdate(frameTime)
-- some code
end

`

```

Be very careful when adding update callback code to your script entity since it can easily decrease the performance of a game.
