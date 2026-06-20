# [Node] Flow

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/36869467
- Page ID: 36869467
- Breadcrumb: Editor Tools > Behavior Tree Editor > Behavior Tree Nodes > [Node] Flow
- Parent: Behavior Tree Nodes

## Content

##
Flow Nodes

Flow nodes contain at least one child node, and control the execution of a behavior tree by describing the rules by which each of their children nodes must be executed. The different types of Flow nodes are as follows.

##
Sequence

**
Description
**

 |
Executes each of its children nodes in the order that they're defined, one at a time, until one child fails or all children nodes succeed.

 |

**
Parameters Accepted
**

 |
None.

 |

**
Results
**

 |
Outcome

 |
Criteria

 |

**
Success
**

 |
When all its children nodes returns a successful result.

 |

**
Failure
**

 |
When a child node fails.

 |

 |

**
Additional Information
**

 |

-
Must have at least one child node specified.

-
Maximum number of children nodes: 255.
 |

##
Selector

**
Description
**

 |
Executes each of its children nodes in the order that they're defined, one at a time, until a child node succeeds.

 |

**
Parameters Accepted
**

 |
None.

 |

**
Results
**

 |
Outcome

 |
Criteria

 |

**
Success
**

 |
As soon as one of it children nodes returns a successful result.

 |

**
Failure
**

 |
If all of its children nodes return a failure.

 |

 |

**
Additional Information
**

 |
Must have at least one child node specified.

 |

##
Priority

**
Description
**

 |
Executes each of its children nodes in decreasing order of their priority, one at a time; each child node is assigned a priority level (the top-most/first child being of the highest priority) and a condition that is evaluated dynamically.

This means that a child node is executed only if its associated condition is satisfied; as soon as a node fails its condition check, the conditions of lower priority children nodes are re-evaluated.

Execution then resumes at the node with the highest priority and a satisfied condition.

 |

**
Parameters Accepted
**

 |
Parameter Name

 |
Description

 |
Value

 |

**
Condition
**

 |
Specifies the condition that needs to be satisfied for a child node to be executed.

 |
Boolean; an empty field will always be evaluated as true.

 |

 |

**
Results
**

 |
Outcome

 |
Criteria

 |

**
Success
**

 |
If the child node that is currently being processed returns a successful result.

 |

**
Failure
**

 |
If the current child node returns a failure.

 |

 |

**
Additional Information
**

 |
The last child node of a Priority node must be defined with an empty condition, that always yields a successful result.

This node acts as a "fallback", representing the default behavior that must be carried out if all higher priority children of the Priority node have failed.

 |

##
Parallel

**
Description
**

 |
Executes its children nodes in parallel.

 |

**
Parameters Accepted
**

 |
Parameter Name

 |
Description

 |
Value

 |

**
Success
**
**
/ Failure Mode
**

 |
Specifies how the Parallel node's children influence its result of success and failure as stated below.

 |

-
**
All
**

-
**
Any
**
**

**

 |

 |

**
Results
**

 |
Outcome

 |
Criteria

 |

**
Success
**

 |

-
If all children nodes return a successful result when the
**
Success Mode
**
 parameter has been set to
**
All
**
.

-
If at least one of its child nodes returns success when the
**
Success Mode
**
 parameter has been set to
**
Any
**
.
 |

**
Failure
**

 |

-
If all children nodes return success when the
**
Failure Mode
**
 has been set to
**
All
**
.

-
If at least one of its child nodes returns failure when the
**
Failure Mode
**
 has been set to
**
Any.
**
 |

 |

**
Additional Information
**

 |
Maximum number of parallel children nodes: 32.

 |

##
Loop

**
Description
**

 |
Has only a single child node, which it executes either a fixed number of times, infinitely or until the child fails.

 |

**
Parameters Accepted
**

 |
Parameter Name

 |
Description

 |
Value

 |

**
Repeat Count
**

 |
Specifies the number of times the node must loop the execution of its child node.

 |
Integer. Loops infinitely when set to 0.

 |

 |

**
Results
**

 |
Outcome

 |
Criteria

 |

**
Success
**

 |
If the loop of execution runs for the specified
**
Repeat Count.
**

 |

**
Failure
**

 |
If the Loop node's child fails.

 |

 |

**
Additional Information
**

 |
None.

 |

##
Loop Until Success

**
Description
**

 |
Has only a single child node which it executes either a fixed number of times, infinitely or until the child succeeds.

 |

**
Parameters Accepted
**

 |
Parameter Name

 |
Description

 |
Value

 |

**
Repeat Count
**

 |
Specifies the number of times the node must loop the execution of its child node.

 |
Integer. Loops infinitely when set to 0.

 |

 |

**
Results
**

 |
Outcome

 |
Criteria

 |

**
Success
**

 |
If the node's child returns a successful result.

 |

**
Failure
**

 |
If the node's child fails even after the loop of execution runs for the specified
**
Repeat Count.
**

 |

 |

**
Additional Information
**

 |
None.

 |

##
State Machine

**
Description
**

 |
Has one or more
**
States
**
 as its children that are executed in the order they are defined, one at a time. At any time, the state of a State Machine node is the same as the state of its child that is currently being executed.

Every
**
State
**
 must have as part of its definition:

-
**
Transitions
**
, that specify the events under which the
**
State
**
 transitions to another State.

-
**
A root node
**
 that begins a separate behavior tree that must be executed when the current
**
State
**
 is active.
 |

**
Parameters Accepted
**

 |
**
States
**

Parameter Name

 |
Description

 |
Value

 |

**
State Name
**

 |
Allows users to specify a custom name for the created State.

 |
Must be a unique string value for the current State Machine node.

 |

**
Transitions
**

Parameter Name

 |
Description

 |
Value

 |

**
Trigger Event
**

 |
Specifies the Event upon which the current
**
State
**
 transitions to a
**
Destination State
**
.

 |
Accepts any
**
Built-in
**
 or
**
Game
**
 event from a dropdown menu.

 |

**
Destination State
**

 |
Defines the
**
State
**

**
Name
**
 the current
**
State
**
must transition to upon the occurrence of the above
**
Trigger Event.
**

 |
Accepts any created
**
State
**
 as its value.

If the
**
Destination State
**
 is the current
**
State
**
 itself, the current State will first be terminated and re-initialized before being updated again.

 |

 |

**
Results
**

 |
Outcome

 |
Criteria

 |

**
Success
**

 |
If the State child node that is currently being processed succeeds.

 |

**
Failure
**

 |
If the current State child node fails.

 |

 |

**
Additional Information
**

 |
None.

 |

##
Send Transition Event

**
Description
**

 |
Allows Events to be sent from within a defined
**
State
**
 of the parent State Machine node, hence triggering a transition to the
**
Destination State
**
 of the State Machine.

Send Transition Event nodes are used in conjunction with State Machine nodes, to trigger transitions from one State of the State Machine node to another.

 |

**
Parameters accepted
**

 |
Parameter Name

 |
Description

 |
Value

 |

**
Event
**

 |
Specifies the Event that needs to be sent by the defined
**
State
**
of the
**
State Machine
**
 node.

 |
Accepts any
**
Built-in
**
 or
**
Game
**
 Event as its value.

However the Event must be previously specified in the
**
Trigger Event
**
 field of the parent
**
State machine
**
 node.

 |

 |

**
Results
**

 |
Outcome

 |
Criteria

 |

**
Success
**

 |
If the defined transition
**
Event
**
was sent successfully.

 |

**
Failure
**

 |
If the transition
**
Event
**
 wasn't sent successfully.

 |

 |

**
Additional Information
**

 |
None.

 |

[#flow-nodes](
Flow Nodes
)
[#sequence](
Sequence
)
[#selector](
Selector
)
[#priority](
Priority
)
[#parallel](
Parallel
)
[#loop](
Loop
)
[#loop-until-success](
Loop Until Success
)
[#state-machine](
State Machine
)
[#send-transition-event](
Send Transition Event
)
