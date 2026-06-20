# Tutorial - Dedicated Server

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/44967553
- Page ID: 44967553
- Breadcrumb: Tutorials > Game and Level Design > Multiplayer and Networking Tutorials > Tutorial - Multiplayer Networking > Tutorial - Dedicated Server
- Parent: Tutorial - Multiplayer Networking

## Content

### Running The Arbitrator

Due to security reasons, the Dedicated Server will, by default, not run if it is started with root privileges. If necessary, this behavior can be changed by toggling OPTION_ALLOW_RUNNING_SERVER_AS_ROOT in CMake, although it is preferable to change the user that runs the game server.

This is how to run the dedicated server arbitrator:

- Go to the build root folder.
- Set **net_dedicatedServerArbitratorPort=<port>** in system.cfg to a sensible value.
- Go in to the **Bin32** or** Bin64**folder and double click on ** DedicatedArbitrator.exe**.
- The Dedicated Arbitrator window will pop up, allow the application a few seconds to load fully.
- The arbitrator can now be left running in the background

### Registering a Dedicated Server With The Arbitrator

This is how to register a dedicated server with the arbitrator:

- Set **net_dedicatedServerArbitratorIP=<address>** to the arbitrator's IP address.
- Set **net_dedicatedServerArbitratorPort=<port>** to the arbitrators listen port.
- Set **gl_serverIsAllocatedFromDedicatedServerArbitrator=1** to inform the lobby it is an arbitrated server.
- Run the server, registration will happen automatically and should be ready to go.

### Requesting a Dedicated Server From The Arbitrator

This is how to request a dedicated server from the arbitrator:

- Set **net_dedicatedServerArbitratorIP=<address>** to the arbitrator's IP address.
- Set **net_dedicatedServerArbitratorPort=<port>** to the arbitrators listen port.
- Set **gl_getServerFromDedicatedServerArbitrator=1** to inform the lobby that it should request a server from the arbitrator on Start Match.
- Run the game, you should now be able create and host sessions as before, the server will be requested for use when the match starts.

### Arbitrator Commands

Commands that may be useful when running an arbitrator:

- **net_dedicatedServerArbitratorListFreeServers** - list servers the arbitrator has to allocate.

### Known Issues

- If a **levelrotation.xml** is present when the arbitrator is run, it will load, create and advertise it's own session using this, try to avoid this.
- This goes for the dedicated server too.
