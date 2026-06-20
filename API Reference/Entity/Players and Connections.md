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
[/docs/static/engines/cryengine-5/categories/28704770/pages/29797329](
INetworkedClientListener
)
.
 This allows the creation of entities from the game side whenever a client connects, starting gameplay after the player finishes connecting, and finally exposes a disconnection event to allow removal of any entities spawned for a particular client.

[/docs/static/engines/cryengine-5/categories/28704770/pages/29797329](
Example
)

##
Table of Contents

[#api-types](
API Types
)
[#local-player](
Local Player
)
[#channel-identifiers](
Channel Identifiers
)
[#conclusion](
Conclusion
)

##
API Types

-

[/docs/static/engines/cryengine-5/categories/28704770/pages/29797329](
INetworkedClientListener
)

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
[/docs/static/engines/cryengine-5/categories/23756813/pages/26216232#Networking-Channels](
Networking
)
.

##
Conclusion

This concludes the article on Players and Client Connections, you may be interested in:

-
[/docs/static/engines/cryengine-5/categories/23756813/pages/26216232](
Networking
)

-
[/docs/static/engines/cryengine-5/categories/23756813/pages/26216224](
Physics and Movement
)

-
[/docs/static/engines/cryengine-5/categories/23756813/pages/29428286](
Input and Action Mapping
)

-
[/docs/static/engines/cryengine-5/categories/23756813/pages/28184910](
Execution Order and Lifecycle
)

-
[/docs/static/engines/cryengine-5/categories/23756813/pages/26216226](
Characters and Animations
)
