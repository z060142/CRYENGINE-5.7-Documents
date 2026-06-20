# Using Flow Graph Modules

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/29450520
- Page ID: 29450520
- Breadcrumb: Scripting > Flow Graph Overview > Using Flow Graph Modules
- Parent: Flow Graph Overview

## Content

##
Overview

A FlowGraph Module is a way to encapsulate nodes as its own graph that can then be fetched from other graphs at runtime.

##
Making a New Module

Using Flow Graph Editor, you can create a new Module by selecting
**
File -> New FG Module -> Global/Level
**
.

![Image](https://www.cryengine.com/docs/static/attachments/44971095)

You can also create a new Module by right-clicking on the FG Modules entry.

![Image](https://www.cryengine.com/docs/static/attachments/44971094)

Existing logic can be converted to a module by selecting and copying the desired nodes, and then right-click to select
**
Paste With Links
**
 (
**
Ctrl + Shift + V
**
) option in a new module.

##
Module Types

There are two supported module types:

-
Global
: Modules which are used in multiple levels should be created as Global modules.
Saved in:
*
../GameSDK/Libs/FlowgraphModules
*

-
Level
: Modules only used in a specific level should be created as Level modules.
 Saved in:
*
../GameSDK/Levels/<levelfolder>/FlowgraphModules
*

##
Adding Custom Input/Output Ports

Custom Ports for Input and Output can be added via

**
Tools -> Edit Module
**
 when the module's graph is open in the main view:

![Image](https://www.cryengine.com/docs/static/attachments/44971092)

The Module Ports dialog can also be accessed by right-clicking on the module in the graphs list or by right-clicking its related nodes.

##
Using Modules

Modules are called from other graphs by using
Call Nodes
. Every module has its own call node named
*
Module:Call_<Module Name>
*
.

![Image](https://www.cryengine.com/docs/static/attachments/44971097)

Modules can be called independently by distinct Call Nodes and from different graphs. Every call to the module will generate a separate
Instance
 that runs independently from previous calls.

##
Instance IDs

The specific Instance associated to the Call node can be controlled with the 'InstanceID' port. This is useful to update the inputs or listen for outputs of a specific instance.

When you set the value as '
-1
', it will generate a new instance with an automatic ID. The Call Node will output for that instance until it is called again.

Subsequent triggers in a Call node with a specific instance ID will update the inputs of that instance and not generate a new one. The instance ID numbers are independent from module to module.

##
Running Modules on Entities

A Module Instance can run associated with an Entity by setting it in the
`
Choose Entity
`
 port. The Entity ID is available from within the module in the Start node's
`
EntityID
`
 port.

The Entity ID can be used to reference the same module instance to update its inputs and listen to outputs. The Instance ID should be kept at
*
 -1
*
.

Another way to run modules on entities is by using the node
*
GameEntity:Containers:Actions
*
:

![Image](https://www.cryengine.com/docs/static/attachments/35395036)

This node runs a module on all entities of an entity container where all instances will automatically have the correct Entity ID.

There is no way to pass in inputs with this method.

##
Continuous Input/Output options

Without the
**
`
Continuous Input
`

**
option (default), a module instance will only receive updated inputs when the
**
`
Call
`
**
port is triggered, which activates all the start node's ports even if the input values were not updated.

With the
`
Continuous Input
`
 option, single inputs will be passed into the start node as soon as they are triggered, which will also activate the start node's
`
Update
`
 port. If the Call node does not have a running Instance and an input is triggered, nothing happens.

For
`
Continuous Output,
`
 the Call Node will update its output ports as soon as they are activated from the return node.

Without
`
Continuous Output
`
 the Call Node's outputs will only activate when the Instance is successfully finished.

##
Global Controllers

The Call node can be set to
`
Global Controller
`
 mode. This is useful for either sending inputs to all instances of the module at once or for listening if any of the instances has triggered an output.

-
If multiple instances trigger outputs, the external outputs of the global node will trigger multiple times.

-
The
`
OnCalled
`
 port triggers with the InstanceIDs when an instance of the module is created.

-
In this mode, the node ignores both the InstanceID and EntityID port.

-
If the node is called and no instance exists, it will create a new one.

##
Module Utility Nodes

The following nodes are used as Module Utility Nodes:

-
Module:Utils:InstanceCountListener

-
Module:Utils:UserIDToModuleID

##
Module:Utils:InstanceCountListener

![Image](https://www.cryengine.com/docs/static/attachments/44971099)

Based on the name (or partial name) of a module, displays the module's Instances that are running.

##
Module:Utils:UserIDToModuleID

![Image](https://www.cryengine.com/docs/static/attachments/44971100)

This node is used to make a registry of Instance IDs of a module. Instance IDs for a Module can be stored (
`
Set
`
) along with an
`
UserID
`
 which can be anything that is useful and logical to associate. These connections can then be retrieved (
`
Get
`
) using that
`
User ID
`
. The node does not store any information by itself, all the associations are to be created and maintained by the designer.

##
Debugging Modules

It is possible to get an overview of actively running module instances in the game with the CVar
**
fg_debugmodules
**
.

![Image](https://www.cryengine.com/docs/static/attachments/44971101)

-
fg_debugmodules
 0/1/2:

-
0: Debug info disabled.

-
1: Shows the list of modules with the number of instances running per module.

-
2: Shows the list of modules also with detailed instance information.

-
fg_debugmodules_filter
 "filterstring"

-
Filter the list to display only modules which name matches the 'filterstring'.

##
Advanced

It is possible to call a module from within itself and also to listen for the module's own outputs inside its graph. While there are uses for this, beware that simply calling new instances of a module infinitely will eventually crash the engine.

Entities can also run multiple instances of the same module by specifying an Instance ID other than -1. Details on Instance IDs:

-
A Module runs a set of instances with unique IDs (IIDs) that are associated with an entity (or with invalid_entityid for no entity).

-
If a call node has a manually specified instance ID different from '-1', it will be used.

-
The first of the same specific IID to be called will create the instance which in turn will output all call nodes with that IID.

-
IIDs specified at runtime may refer to the manually specified IIDs.

-
An IID generated at runtime will not collide with one manually specified (the ID generator starts from the biggest manual ID found before the game starts).

-
An IID '-1' generates new instances on every call if there is no entity associated.

-
The call node will hold the outputs of the last generated instance until it is called again.

-
If there is an entity ID specified, the IID will refer within that entity, meaning entities can have their own separate instance 1,2,3.. of the same module.

-
An IID -1 with a specified entity ID will not generate new IID ('-1' is the instance ID).
[Making a New Module](#making-a-new-module)
[Module Types](#module-types)
[Adding Custom Input/Output Ports](#adding-custom-inputoutput-ports)
[Using Modules](#using-modules)
[Module Utility Nodes](#module-utility-nodes)
[Debugging Modules](#debugging-modules)
[Advanced](#advanced)
