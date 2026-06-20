# Host Migration

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/23306389
- Page ID: 23306389
- Breadcrumb: CRYENGINE Engine Code > Engine Modules > CryNetwork > Host Migration
- Parent: CryNetwork

## Content

### Overview

Host migration is the process of transferring ownership of the game from one host to another. This can happen in a variety of ways, that fall broadly into three categories:

- **Lobby migration**: the current host determines that a client in the lobby is a more suitable candidate, prior to commencing the game.
- **Controlled migration**: the current host quits the game in a controlled manner, i.e. through the in-game menus.
- **Catastrophic migration**: the current host loses connection to the internet, crashes or suffers a power outage.

CRYENGINE handles all three cases, with a degree of programmer control. In addition, the host migration process is monitored so that if the new host quits, crashes or suffers a power loss, another host is chosen until either there are no more clients in the game or the host migration time-limit is reached (known as a multi-migration event).

### Host Migration is Session Based

Host migration is session based, and each session can migrate independently (and concurrently). Sessions need to be created as migratable (or not) by supplying the **CRYSESSION_CREATE_FLAG_MIGRATABLE** flag to ** ICryMatchMaking::SessionCreate()**.

### Host Migration is a Lobby Service

It is also a controllable feature of the lobby service; an individual lobby service can be configured to ***not*** support host migration (the default is to support it, via the ** eCLSF_SupportHostMigration** flag) so that a game title can support host migration only on selected platforms if required (e.g. host migration only makes sense in a peer hosted environment; if one platform is using dedicated servers, then it can be prevented from migrating sessions). A lobby service can be queried for host migration support as follows:

```
bool hostMigrationSupported = gEnv->pNetwork->GetLobby()->GetLobbyServiceFlag(<lobby_service_type>, eCLSF_SupportHostMigration);
```

where <lobby_service_type> is eCLS_LAN or eCLS_Online.

### Determination of the New Host

The determination of the 'best' host is decided by hints that are synchronised between all clients in a game. The criteria for determining the best host are as follows:

- NAT type (open is better than moderate, which is better than strict, with unknown NAT's being considered the worst).
- The number of active peer connections for this client (more connections means more clients can be 'pulled' onto the new host).
- In the event of two clients being deemed equal in terms of NAT type and number of connections, the unique network channel identifier is used. This is purely to impose a completely deterministic heuristic on all clients.

The hint list is maintained by the current host for as long as the session is active (and supports host migration), and propagated to all clients.

### Host Migration Console Variables

There are a number of console variables that can be used both to control host migration, and to show information about the hint list and status of each machine:

- **net_migrate_timeout** - this is the total amount of time allowed for migration events to complete (default is 30 seconds). All migration(s) must occur for the session within this time frame or host migration will terminated.
- **net_automigrate_host** - toggles whether automatic migration is attempted when connection to the host is lost (default is 1 = on). This can be used to guard sections of code when you don't want host migration to occur, but you still want the facility to be supported.
- **net_show_host_identificiation** - toggles whether host identification is displayed on screen (default is 0 = off). This shows the status of any given machine in all its participating sessions, and will show either 'HOST', 'ANTICIPATED NEW HOST' or 'MEMBER'.
- **net_show_new_host_hinting** - toggles whether the host hint list is displayed on screen (default is 0 = off). This shows the hint list of any given machine in all its participating sessions. The host will have a hint for every client in the game (excluding themselves), and each client will have a hint for each peer connected client (excluding themselves and the host). So, in a fully connected game with four participants, the host would see three hints (one for each client), and the clients would each see two hints (one for each client excluding the host).
- **net_hostHintingNATTypeOverride** - overrides the reported NAT type (default is 0 = off; 1 = open, 2 = moderate, 3 = strict, 255 = unknown). This command is useful for creating, or repeating test situations. Obviously it doesn't actually change the NAT type, only what's reported in the hint, and is used to ensure a particular machine is either excluded as a host candidate (by reporting a more strict NAT type) or preferentially chosen (by reporting a more open NAT type).
- **net_hostHintingActiveConnectionsOverride** - overrides the reported number of active connections (default is 0 = off). This command is useful for creating, or repeating test situations. Obviously it doesn't actually change the number of active connections, only what's reported in the hint, and is used to ensure a particular machine is either excluded as a host candidate (by reporting a lower number of connections) or preferentially chosen (by reporting a higher number of connections; up to 255).

### Host Migration Flow

The host migration process passes through a number of stages, and at each stage certain actions must be performed. To facilitate this, classes can register interest in host migration events by way of a listener interface pattern.

Firstly, your class must inherit from IHostMigrationEventListener (defined in INetwork.h):

```
struct IHostMigrationEventListener
{
virtual void OnInitiate(SHostMigrationInfo& hostMigrationInfo, uint32& state) = 0;
virtual void OnDisconnectClient(SHostMigrationInfo& hostMigrationInfo, uint32& state) = 0;
virtual void OnDemoteToClient(SHostMigrationInfo& hostMigrationInfo, uint32& state) = 0;
virtual void OnPromoteToServer(SHostMigrationInfo& hostMigrationInfo, uint32& state) = 0;
virtual void OnReconnectClient(SHostMigrationInfo& hostMigrationInfo, uint32& state) = 0;
virtual void OnFinalise(SHostMigrationInfo& hostMigrationInfo, uint32& state) = 0;
virtual void OnTerminate(SHostMigrationInfo& hostMigrationInfo, uint32& state) = 0;
virtual void OnReset(SHostMigrationInfo& hostMigrationInfo, uint32& state) = 0;
};
```

Secondly your class must register itself with the network layer. This is best done in the constructor of the class with the following:

```
gEnv->pNetwork->AddHostMigrationEventListener(this, "<your_class_name>");
```

where <your_class_name> is just a text string that's used to aid debugging listeners.

A corresponding call to unregister your class should go in its destructor:

```
gEnv->pNetwork->RemoveHostMigrationEventListener(this);
```

Once registered, your class will have the methods defined in IHostMigrationEventListener invoked during a host migration event. Each method takes two parameters (supplied by the network layer), namely a reference to a SHostMigrationInfo structure which contains information for this host migration event, and a reference to the internal state of the listener (see below). The methods are called in the order they are declared in the interface:

- **OnInitiate()** is called at the start of a host migration event. It is the responsibility of this method to store any pertinent information required to persist across the migration (e.g. player inventories)
- **OnDisconnectClient()** is called when the client disconnects from the original host. It is entirely possible for the old host to have this method called (in the event of a lobby migration).
- **OnDemoteToClient()** is called on each client who is ** not** the new host - this means that clients remaining as clients will have this method called. It is entirely possible for the old host to have this method called (in the event of a lobby migration) as it might have to adjust internal state to become a client.
- **OnPromoteToServer()** is called ** only** on the anticipated new host of the session.
- **OnReconnectClient()** is called on all clients, whether they were the old host, the new host or remaining a client.
- **OnFinalise()** is called on all clients, whether they were the old host, the new host or remaining client. This is used to release temporary assets that may have been allocated in OnInitialise().
- **OnTerminate()** is called in the event of an error (which could happen at any point in the host migration process, so make sure any clean-up done in OnFinalise() is also done here).
- **OnReset()** is called when the anticipated new host leaves part way through the host migration process. Note that the host migration internal state machine will go back to OnDisconnectClient() after this method, ** not** OnInitiate().

Each method returns a boolean, with **true** meaning 'all processing for this stage is complete', and ** false** meaning 'more processing is required'. Only when all the registered listeners for a given state have returned ** true** does the host migration process move onto the next state. This allows asynchronous tasks such as disconnecting or reconnecting to fully complete before moving onto the next state (the passed reference '** state**' is guaranteed to be 0 the first time the listener is invoked, and will persist its value on subsequent invocations, until the listener completes - useful for controlling switch based state machines).

### Game Rsponsibilities for Host Migration

CRYENGINE handles most of the work required to migrate a session to a new host, but the game will have some responsibilities.

Firstly, after a client connects to the host there is a period of time where the newly connected client simply doesn't have enough information to assume host responsibilities, should the host leave or fail catastrophically. To mitigate this, all clients will initially report that they are unsuitable as a host of any session they connect to, by way of reporting undesirable host hint information to the current host. Once the game deems that the client has sufficient information to be able to assume host responsibilities for the session, the game must at least do the following:

```
ICryMatchMaking* pMatchMaking = gEnv->pNetwork->GetLobby()->GetLobbyService()->GetMatchMaking();
pMatchMaking->SessionSetLocalFlags(<game_session_handle>, CRYSESSION_LOCAL_FLAG_HOST_MIGRATION_CAN_BE_HOST, NULL, NULL, NULL);
```

where <game_session_handle> is the session handle that was returned in the callback from SessionCreate(). The NULL parameters in the example code are the normal lobby/matchmaking callback parameters, namely a CryLobbyTaskID*, CryMatchmakingFlagsCallback and void* callback argument, and are omitted here for brevity. It is important to note that this must be done for each session that the game controls and wishes this client to be considered as host if a host migration event is triggered.

During a migration event for a game that is in progress, clients go through several of the context establishment tasks that are required when connecting to a new server, however they skip the tear-down stages. It is therefore up to the game to decide what is no longer needed, and to throw it away as necessary. This should be done by creating a list of entities that will no longer be needed post-migration in the **OnDemoteToClient()** listener, and then removing these in the ** OnFinalise()** listener. Note that with a migration event, it is possible for a client to start migrating to a new host (remaining a client) but for that host to leave (either in a controlled or catastrophic manner) and for this client to subsequently become the host (a multi-migrate event). This is an important point to remember as it means that during a multi-migrate event, the list of entities created in the ** OnDemoteToClient()** listener ** mustn't** be deleted until the ** OnFinalise()** listener (which is the point when host migration has essentially completed) otherwise the client who is becoming the host will have no knowledge of the entities which it is supposed to assume control of. This also means that the entity list on any client who remains a client during a multi-migrate event might gain duplicate entries as the ** OnDemoteToClient()** listener will be called more than once. In this situation, it is safe to immediately discard the duplicates.

The game is also responsible for making sure that reconnecting clients are given the correct actor. This is done inside **CGameRules::SetChannelForMigratingPlayer()** and ** CGameRules::OnClientConnect()**:

- **SetChannelForMigratingPlayer()** should return the ** EntityId** which corresponds to the actor being assigned to that channel.
- **OnClientConnect()** would normally be responsible for creating an actor for the new client, but in the case of host migration it needs to use the cached ** EntityId** from ** SetChannelForMigratingPlayer()**, as this actor entity already exists.

During a migration event on Xbox LIVE, the **SessionID** is changed, and this will cause the **.m_SID** component of the ** SConnectionUID** for all lobby connections to be changed. In order to match an update to it's associated player, ** SConnectionUID**s should only use the **.m_UID** component for comparison purposes.
