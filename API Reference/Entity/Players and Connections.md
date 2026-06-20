# Players and Connections

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/26216222
- Page ID: 26216222
- Breadcrumb: Entity > Players and Connections
- Parent: Entity

## Content

##
Overview

In CRYENGINE, each player is represented by an entity instance - created by game code when clients connect to the server.

Custom code can listen for client connection events by implementing
[INetworkedClientListener](/docs/static/engines/cryengine-5/categories/28704770/pages/29797329)
.
 This allows the creation of entities from the game side whenever a client connects, starting gameplay after the player finishes connecting, and finally exposes a disconnection event to allow removal of any entities spawned for a particular client.

[Example](/docs/static/engines/cryengine-5/categories/28704770/pages/29797329)

##
Table of Contents

[API Types](#api-types)
[Local Player](#local-player)
[Channel Identifiers](#channel-identifiers)
[Conclusion](#conclusion)

##
API Types

-

[INetworkedClientListener](/docs/static/engines/cryengine-5/categories/28704770/pages/29797329)

##
Local Player

The engine currently assumes that the local player entity is always spawned with the id of 30583, defined via
LOCAL_PLAYER_ENTITY_ID
. This is covered in the networked client listener example above. In addition, local players must  set the
ENTITY_FLAG_LOCAL_PLAYER
 entity flag.

##
Channel Identifiers

The client connection events are primarily only sent to the server, and identify each player by channel identifiers. For more information, see
[Networking](Networking.md#Networking-Channels)
.

##
Conclusion

This concludes the article on Players and Client Connections, you may be interested in:

-
[Networking](Networking.md)

-
[Physics and Movement](Physics%20and%20Movement.md)

-
[Input and Action Mapping](Input%20and%20Action%20Mapping.md)

-
[Execution Order and Lifecycle](Execution%20Order%20and%20Lifecycle.md)

-
[Characters and Animations](Characters%20and%20Animations.md)
