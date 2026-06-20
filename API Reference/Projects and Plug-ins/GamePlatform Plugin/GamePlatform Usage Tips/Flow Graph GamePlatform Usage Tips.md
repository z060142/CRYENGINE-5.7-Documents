# Flow Graph GamePlatform Usage Tips

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/76448709
- Page ID: 76448709
- Breadcrumb: Projects and Plug-ins > GamePlatform Plugin > GamePlatform Usage Tips > Flow Graph GamePlatform Usage Tips
- Parent: GamePlatform Usage Tips

## Content

##
Overview

Flow Graph nodes can be used at any time, as long as the plugins are loaded. This means you can tie them into the System Events and Actions such as level loading or UI procedures.

##
Flow Graph Architecture Limitations

Due to the architecture of the Flow Graph system, the following limits effective interaction with the GamePlatform system:

-
Data types are limited to Strings, 32-bit integers and Booleans.

-
Execution should be handled during a Flow Graph update tick. Event nodes are not triggered immediately, but are queued until the next tick (frame).

-
Containers are limited, which makes array data difficult to handle.

##
Data Types

Most identifiers used by the GamePlatform services are variations of 64 bit types.

Since Flow Graph doesn't natively support 64 bit types, convert them to strings for Flow Graph, and then back into 64 bit types for execution on the service APIs. Here is an example of an identifier being implicitly converted to a string:

[Image: /docs/static/attachments/76448711]

*
The "Account Id" pins are strings, converted from the underlying data type of the Account Identifier. For Steam, this would be the Steam 64 Id, a 64bit number
*

##
Event Handling

Almost all GamePlatform events are queued in nodes called Listeners. Some things to note about listener nodes:

-
Each individual Flow Graph node of the same event duplicates the event data. If you have 2 nodes of the same event, handling an event from one node will not remove it from any other.

-
Each Flow Graph Listener node can queue several events before execution is passed to it. You should pull all events, if there are any; instead of pulling one event per frame, pull as many as there are or you may fall behind.

-
Some Listener nodes will make use of special Container nodes which are explained further below in more detail.
It is recommended to only have a single event node for each unique event you are listening to at a time, as there is also no guarantee which node will execute first.

Here is an example of handling events with a Listener node:

[Image: /docs/static/attachments/76448713]

*
*
The "Get Next Event" input on the Listener node is triggered as long as there are events left to consume
*
*

##
Container-based Event Data

Some Listener nodes will provide a "
*
Container Id
*
" that can be used to access array data.

These are required in some cases for functions that require an array as input; for example, getting details on multiple Catalog items. Some details to mention regarding the special containers:

-
Each Container is unique and accessible from any graph. (Similar to System Containers).

-
All Containers are persistent and must be deleted manually.

-
Each Container is specialized and must be accessed by the respective Container node.

-
An event will be sent to every event node of the event type in any active Flow Graph. When each event node receives the event, a unique container is created for each node (in the backend) which can then be accessed using the Container nodes. This means that data will be duplicated.

-
Some functions require these Containers so that you can pass all the elements from one event into the function of another directly.
Here is an example of handling a Container-based event:

[Image: /docs/static/attachments/76448714]

*
For each event, each item in the Container is looped. The Container is deleted when there are no elements left
*

Since multiple events can be queued, there may be multiple Containers waiting to be pulled.

The following is an example of a function that uses the Container created by an event node:

[Image: /docs/static/attachments/76448715]

*
The deletion of the container is not shown here, as the event node for the function called should handle the deletion of the Container that was used to generate it
*

##
Simplified Array Results

Container nodes are used when a function node requires an array input. As this is not the case for all data that can be received from a function or event node, some nodes allow you to iterate over each item directly.

The following an example of a node that lists each item individually without a Container node:

[Image: /docs/static/attachments/76448716]

*
There is no Container node to manage.
*
Each call to the Retrieve input will overwrite the elements that will be output by the node. Get Next is used to get each item sequentially and can be handled directly.
*
*

[#flow-graph-architecture-limitations](
Flow Graph Architecture Limitations
)
[#data-types](
Data Types
)
[#event-handling](
Event Handling
)
[#container-based-event-data](
Container-based Event Data
)
[#simplified-array-results](
Simplified Array Results
)
