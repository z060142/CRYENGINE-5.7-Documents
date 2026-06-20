# Concepts Overview

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/23306390
- Page ID: 23306390
- Breadcrumb: CRYENGINE Engine Code > Engine Modules > CryNetwork > Concepts Overview
- Parent: CryNetwork

## Content

##
Overview

CryNetwork separates object management from communication. The heart of the communication system is the Nub, and the heart of the object management system is the
*
NetContext
*
. All communication is handled by packets, containing one message, each with a header and a payload. Messages are being sent in an independent thread to decouple the game frame rate from the speed of the network connection (see
[#Multithreading](Concepts%20Overview.md#ConceptsOverview-Multithreading)
). All non critical information is transferred through UDP (see
[#Message Queuing](Concepts%20Overview.md#ConceptsOverview-MessageQueuing)
).

A Server uses class
*
INetNub
*
 to hold a collection of net channels and one socket for communication (the socket is shared with all channels). All classes in the subfolder
*
Context
*
 of CryNetwork deal with object replication, while
*
Context/NetContext
*
 is the root class for reflection into CryNetwork of all the game states.
*
Context/NetContextState
*
 is the net context for one level. There may be more than one around for the case that some clients are slow switching levels. Every
*
INetChannel
*
 object contains a class of type
*
Context/ContextView
*
 which is the base class for an updatable view into the net context. To summarize, each game session introduces one
*
NetNub
*
, one
*
NetContext
*
 and a
*
NetContextState
*
 per level. Each connection gets a
*
NetChannel
*
 and a
*
ContextView
*
.

Every synchronized
*
GameObject
*
 has its own
*
NetObjectID
*
 to communicate through messages, as EntityIDs are not necessarily equal on Server and Client. Therefore the 'eid' serialization protocol is mapping between entity IDs and net object IDs. In addition to that, players get a channel ID which is an index into the Nub, to get the channel to communicate over to that player. A channel is represented by class
*
INetChannel
*
 which manages everything required to communicate with one partner (i.e. the server has one net channel per client; every client has a single net channel for the server). Channels can be setup individually in terms of limiting bandwidth. In module
*
CryAction
*
 classes
*
CGameClientChannel
*
 and
*
CServerChannel
*
 setup channels with default values through console variables
*
cl_packetRate
*
,
*
cl_bandwidth
*
,
*
sv_packetRate
*
 and
*
sv_bandwidth
*
.

Increasing or decreasing the frequency of object updates can be handled through the files
*
scheduler.xml
*
 and
*
entityscheduler.xml
*
. For a more detailed explanation of channel prioritization, see chapter
[#Messaging System](Concepts%20Overview.md#ConceptsOverview-MessagingSystem)
. If traffic rates are intended to be changed, the console variable
*
net_enable_tfrc
*
 (tcp friendly rate control) must be disabled.

Most of the messages being sent are object updates or remote method invocations (RMIs). Messages can be setup to depend on each other. Thus messages which depend on one successor, such as the ones updating an entity object, are called streams. This system allows for a potentially infinite number of concurrent independent streams.

In order to make sure that clients are only updating information which is supposed to be passed within one frame, the method
*
SyncWithGame()
*
 is being called at the beginning of each game frame update.

##
Protocol Library

##
Nubs and Channels

A Nub is the core communication object in CryNetwork. It consists of a port (or several ports) for packet based communication and a collection of Channels.

A Channel is CryNetwork's representation of a connection between two machines. Over a channel one can send and receive messages. To facilitate communication about abstract game state, a channel usually has a context view to observe and help replicate the net context state that is currently active.

Channels and Nubs each have a game-side and a CryNetwork-side implementation. The game-side implementation is available so that the (hidden) CryNetwork implementation can be easily extended by different games having different requirements.

##
Channel Protocol Definition

At the start of any connection, higher level code is queried as to what protocol the channel will implement. A protocol consists of a set of messages which can be sent and a set of messages that can be received. It is the higher level code's responsibility that these are matched at each end of the connection (what is sent should be received remotely, and what is received should be sent remotely).

Classes that can receive messages are derived from
*
CNetMessageSinkHelpers
*
, with the requirement that the T_Parent template parameter is some class that has
*
INetMessageSink
*
 as a parent class (or that it is
*
INetMessageSink
*
.) After both the game side and the
*
CryNetwork
*
 side of the channel have been created, the
*
CNetChannel
*
 implementation of
*
DefineProtocol()
*
 is called. This function is then called recursively through the channel structure, until all parts of that channel have had their
*
DefineProtocol
*
 function called. Each part should call
*
AddMessageSink
*
 with what messages it will send and receive; these should be defined as null terminated arrays of
*
SNetMessageDef
*
 pointers. The
*
CNetMessageSinkHelper
*
 class defines logic so that the various message declaration macros can build this array automatically and
*
DefineProtocol()
*
 can retrieve it simply by calling
*
GetProtocolDef()
*
.

##
Connection Establishment

There are a number of steps that need to be taken before a full connection is established. These are performed by the Nub before the Channel is created.

 The following steps are performed (labelled as client->server, but they could easily be labelled Peer 1 -> Peer 2.)

-
Client sends a 'connection request' packet to the server with the client version number, a protocol version number, some flags and a game defined connection string.

-
Upon receiving, the server responds with part 1 of a Diffie-Hellman handshake and some additional flags.

-
The client responds with part 2 of a Diffie-Hellman handshake and creates its channel.

-
The server can now additionally create its channel.

##
Base Services

This section describes at a high level the basic libraries used by all CryNetwork components.

##
Memory Management

CryNetwork utilizes a separate single-threaded memory heap per channel and per network context state. These heaps are managed by the class
*
CMementoMemoryManager
*
. Each channel/context view/context state/etc. holds a smart pointer to this memory manager; when this smart pointer reaches a zero reference count, the memory manager is deleted, forcing all allocated pools to be returned to the system memory manager. This prevents any gradual memory leaks from affecting the server but means that one must be careful that all memory is allocated from the correct pool.

Since small chunks of memory are more or less continuously allocated, it would be a high overhead for every allocation to store its memory manager. For this reason, we use the concept of regions. Each time a function is entered in an object that has a memory manager, a call to the
*
MMM_REGION()
*
 macro is made with a pointer to the memory allocator for that object. This macro sets up a scoped object that will set the current memory manager until the basic block is exited. At any point, the active memory manager can be retrieved with the global
*
MMM()
*
 function.

STL containers can use the standard allocator in which case they will lock every time they need to access main memory - this is probably ok for relatively static vectors, but otherwise can present a problem). Alternatively, the
*
STLMementoAllocator
*
 allocator implementation can be used in all STL containers. It will check the currently active memory manager (using
*
MMM()
*
 as described above) and store a smart pointer to this memory manager, using it for all container requested allocations.

The memento memory manager can work in one of two modes: handle based and pointer based. Handle based allocation will keep the size and the address of a pointer private (the pointer MAY change between frames, although in the current implementation this is not the case.) At any point, the pointer and the size of a handle can be queried with
*
PinHdl
*
 and
*
GetHdlSize
*
 from the memento manager class (obtained by
*
MMM()
*
). Pointer based memory does not store the size of an object, and consequently it is up to the user of this memory to supply the size to the FreePtr function later.

##
Multithreading

CryNetwork is run on a separate thread from the main game. The reason for this is to allow data to be received and sent independently from the main game loop which may stall for large amounts of time (especially during level loading but sometimes at other points due to shader compilation for example.)

Execution is primarily guarded by a single global lock, although some subsystems have separate locks for special purposes. The global lock is taken by placing SCOPED_GLOBAL_LOCK at the top of a basic block. Since we would like to avoid locking wherever possible and to simplify the programming model as well as provide frame coherency with the view provided by the network system of the game, the majority of CryNetwork calls are queued into one of a group of global queues. Calls from the game code to the network code are placed into the FROM_GAME queue and things from the network code to the game are placed in the TO_GAME queue. Asynchronous callbacks from net code to net code are possible using the NET_TO_NET queue (and will be executed on the next frame.)

Calls from the TO_GAME queue are executed with the global lock taken. In order to execute code without the lock taken, the special TO_GAME_LAZY queue should be used instead.

These queues are in fact macros which take as parameters the callback function, the object to call that function on and any parameters that must be passed to the function. Since things are executed later, a copy must be made and function parameters may not be references.

##
Timers

Many things in a network system need to execute with some fixed frequency. Since we execute the network code in a background thread that is intended to have a very low CPU cost, it is required that these frequent callbacks are scheduled using a callback timer. The network system contains logic to sleep its thread in between callbacks. The timer system is implemented by
*
CNetTimer
*
 and is globally accessible from the TIMER macro.

##
Messaging System

The messaging system provides the basic mechanism to communicate over a channel to another machine. The basic format of a CryNetwork packet is (abstractly):

-
Basis sequence number byte (doubles as the packet type header)

-
Current sequence number

-
Acknowledgement/Non-acknowledgement information for previous packets

-
Message header 1 followed by message payload 1

-
Message header 2 followed by message payload 2

-
... etc ...

-
End of packet message (necessary for the encode format)

-
Footer information
Messages are serialized into the main body. As described by the previous list, they contain a header (where to dispatch this message) and a payload - the data that is really interesting about this message. It is the responsibility of the message implementations to encode and decode this payload correctly.

##
Message Prioritization

Since there are usually too many queued messages than can fit in a single update packet, a prioritization system is employed to decide which messages to send and when. This prioritization system will never override the message DAG but may be modified by the DAG (as described in
[#Message Queuing](Concepts%20Overview.md#ConceptsOverview-MessageQueuing)
).

The instantaneous message priority is a number between 0 and 16, with 16 being the highest possible priority and 0 being the lowest. Each frame the instantaneous priority of each message is recalculated and a running integration of priority 2 is kept. It is this running integration that determines the message priority, meaning that longer delayed messages still have a chance to be sent eventually.

Setting instantaneous message priorities is core to getting good interactive performance from the CryNetwork engine. Since there are many different parameters for this, we separate the declaration of priorities from messages by letting the message simply declare an accounting group and using an XML file (game/scripts/network/scheduler.xml) to specify what those groups mean.

The parameters available for message prioritization (specified in the scheduler.xml file) include:

-
A base priority which is a number between 0 and 16 and sets the start of where all deltas described below are offset from. This is the priority parameter in the xml.

-
An optional distance prioritization. Both a maximum increment (close in the xml) and a maximum decrement (far) to the priority can be specified. Additionally, a "normal" distance can be specified (normalDistance in the xml). Objects at the normal distance from the observer will have no change from the base priority. Objects further away will decrease their priority up to the maximum decrement and at infinity will decrease by the maximum decrement. Objects closer to the observer will increase their priority up to the maximum increment which is reached when the object and the observer are coincident. The change in prioritization is always smooth.

-
An optional field of influence prioritization. This works like the distance prioritization, except that an angle (representing a field of influence - the angle at which this object begins to enter the field of view) is specified as foi in the xml. Here the maximum increment (front) is received when the object is directly in front of the observer and the maximum decrement (back) when the object is directly behind. No change is applied when the object is on the FOI cone itself. Again, the change in prioritization is smoothly blended throughout all angles.

-
An optional set of pulses. These pulses can be sent from the game code; upon being received they set an internal timer (which answers the question: when was I last pulsed?). From that point on the pulse enters an exponential decay. Both the half-life of the decay and the size of the initial pulse can be configured.

-
An optional draw distance culling, for things that are visible. If an object is beyond the distance where the 3D engine would draw it, then its priority (after all previous considerations have been taken into account) is set to zero. Enable this by setting drawn in the xml to 1.
Additionally, each accounting group specifies some network behaviors:

-
A maximum total bandwidth (bandwidth) specified. This value is in bits per second and will never be exceeded.

-
Two latency parameters are defined. latency specifies how long (in seconds) a message can be kept in the queue; after this time it gets prioritized above any other messages, disregarding any other prioritization. Additionally, discardLatency specifies a time after which it's no longer useful to send this message, and so it should be dropped.

##
Message Queuing

Reliably ordered messages are implemented in CryNetwork using a ping-pong style protocol (the next message is not sent until the previous message has been acknowledged). However, there are several optimizations in the general architecture that make this efficient.

The primary optimization is that we don't have a single 'reliable ordered' stream, as is traditional. Instead, when each new message is queued its dependencies are listed. The message is then guaranteed to be delivered after the dependent messages have been delivered. This creates a DAG of messages that need to be sent. If a high priority message is dependent on lower priority messages, then those low priority messages automatically have their priority increased.

As we process messages in the DAG, if we send message A that has dependent messages B and C, then B and C are allowed to be sent during that same packet. This allows us to bypass the requirement to wait for an acknowledgement of A (since if the packet is received, all of the packet will be received and there is no way that the ordering can be broken). Since we have the ability to list all of the dependent messages explicitly (and we do not rely on an implicit ordering mechanism), chains of dependent messages tend to be short and so it is the usual case that we never need to wait for acknowledgements before allowing a message to be sent.

##
Addition/Substitution/Removal from the Queue

Some messages are only valid for a short amount of time and past that time there is no need to send them (for instance, voice fragments.) These messages can be queued and each queued message returns (optionally) a handle that refers to it. This handle can be removed from the queue at any time:

-
if it has already been sent and acknowledged, this is a no-op;

-
if it has been sent but not acknowledged, and later the packet is nacked, the message will not be present;

-
and if the packet has not been sent, it will be removed from the queue, and any dependencies patched.
Additionally, some message types need to be constantly removed and re-added (especially status update messages). For this reason, there is a separate substitute message path with the same signature as the add message call. In this case, if an output handle is provided, it is an in-out parameter, and the in part is expected to be the 'current' (possibly null) message handle and the out part being the new handle. Possibly the old message was already sent, in which case the new message will be added. If the old message was not sent, then just the pointer to the old message is deleted and the new message is inserted. This also gives us the advantage that the old priority integration is maintained, so there is no prioritization disadvantage to doing this.
