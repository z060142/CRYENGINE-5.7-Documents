# Modular Behavior Tree Nodes

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/23306489
- Page ID: 23306489
- Breadcrumb: CRYENGINE Engine Code > Engine Modules > CryAISystem > Modular Behavior Tree > Modular Behavior Tree Nodes
- Parent: Modular Behavior Tree

## Content

##
Introduction

It's possible to expose Modular Behavior Tree Nodes from withing the whole CryENGINE code.

This brings to a grouping of the nodes related to the system they are defined into:

-
[Generic](Modular%20Behavior%20Tree%20Nodes.md#ModularBehaviorTreeNodes-generic)

-
[AI System](Modular%20Behavior%20Tree%20Nodes.md#ModularBehaviorTreeNodes-aisystem)

-
[CryAction](Modular%20Behavior%20Tree%20Nodes.md#ModularBehaviorTreeNodes-cryaction)

-
[Game](Modular%20Behavior%20Tree%20Nodes.md#ModularBehaviorTreeNodes-game)

-
[Helicopter](Modular%20Behavior%20Tree%20Nodes.md#ModularBehaviorTreeNodes-helicopter)

##
General information

Each node can have parameters to configure the behavior of its execution. When passing an unacceptable value the parsing of the node could fail and an error message could be found inside the
**
Editor.log
**
 or
**
Game.log
**
.

##
Node index

##
- Generic nodes -

-
[Loop](Modular%20Behavior%20Tree%20Nodes.md#ModularBehaviorTreeNodes-loop)

-
[LoopUntilSuccess](Modular%20Behavior%20Tree%20Nodes.md#ModularBehaviorTreeNodes-loopuntilsuccess)

-
[Parallel](Modular%20Behavior%20Tree%20Nodes.md#ModularBehaviorTreeNodes-parallel)

-
[Selector](Modular%20Behavior%20Tree%20Nodes.md#ModularBehaviorTreeNodes-selector)

-
[Sequence](Modular%20Behavior%20Tree%20Nodes.md#ModularBehaviorTreeNodes-sequence)

-
[StateMachine](Modular%20Behavior%20Tree%20Nodes.md#ModularBehaviorTreeNodes-statemachine)

-
[State](Modular%20Behavior%20Tree%20Nodes.md#ModularBehaviorTreeNodes-state)

-
[SuppressFailure](Modular%20Behavior%20Tree%20Nodes.md#ModularBehaviorTreeNodes-suppressfailure)

-
[Timeout](Modular%20Behavior%20Tree%20Nodes.md#ModularBehaviorTreeNodes-timeout)

-
[Wait](Modular%20Behavior%20Tree%20Nodes.md#ModularBehaviorTreeNodes-wait)

##
- AI System nodes -

-
[Bubble](Modular%20Behavior%20Tree%20Nodes.md#ModularBehaviorTreeNodes-bubble)

-
[GoalPipe](Modular%20Behavior%20Tree%20Nodes.md#ModularBehaviorTreeNodes-goalpipe)

-
[LuaBehavior](Modular%20Behavior%20Tree%20Nodes.md#ModularBehaviorTreeNodes-luabehavior)

-
[Move](Modular%20Behavior%20Tree%20Nodes.md#ModularBehaviorTreeNodes-move)

-
[QueryTPS](Modular%20Behavior%20Tree%20Nodes.md#ModularBehaviorTreeNodes-querytps)

-
[IfTime](Modular%20Behavior%20Tree%20Nodes.md#ModularBehaviorTreeNodes-IfTime)

-
[WaitUntilTime](Modular%20Behavior%20Tree%20Nodes.md#ModularBehaviorTreeNodes-WaitUntilTime)

-
[AssertTime](Modular%20Behavior%20Tree%20Nodes.md#ModularBehaviorTreeNodes-AssertTime)

-
[Priority](Modular%20Behavior%20Tree%20Nodes.md#ModularBehaviorTreeNodes-Priority)

-
[Case](Modular%20Behavior%20Tree%20Nodes.md#ModularBehaviorTreeNodes-Case)

-
[LuaGate](Modular%20Behavior%20Tree%20Nodes.md#ModularBehaviorTreeNodes-LuaGate)

-
[RandomGate](Modular%20Behavior%20Tree%20Nodes.md#ModularBehaviorTreeNodes-RandomGate)

-
[AdjustCoverStance](Modular%20Behavior%20Tree%20Nodes.md#ModularBehaviorTreeNodes-AdjustCoverStance)

-
[SetAlertness](Modular%20Behavior%20Tree%20Nodes.md#ModularBehaviorTreeNodes-SetAlertness)

-
[Log](Modular%20Behavior%20Tree%20Nodes.md#ModularBehaviorTreeNodes-Log)

-
[Communicate](Modular%20Behavior%20Tree%20Nodes.md#ModularBehaviorTreeNodes-Communicate)

-
[Animate](Modular%20Behavior%20Tree%20Nodes.md#ModularBehaviorTreeNodes-Animate)

-
[Signal](Modular%20Behavior%20Tree%20Nodes.md#ModularBehaviorTreeNodes-Signal)

-
[SendTransitionSignal](Modular%20Behavior%20Tree%20Nodes.md#ModularBehaviorTreeNodes-SendTransitionSignal)

-
[Stance](Modular%20Behavior%20Tree%20Nodes.md#ModularBehaviorTreeNodes-Stance)

-
[IfCondition](Modular%20Behavior%20Tree%20Nodes.md#ModularBehaviorTreeNodes-IfCondition)

-
[AssertCondition](Modular%20Behavior%20Tree%20Nodes.md#ModularBehaviorTreeNodes-AssertCondition)

-
[LuaWrapper](Modular%20Behavior%20Tree%20Nodes.md#ModularBehaviorTreeNodes-LuaWrapper)

-
[ExecuteLua](Modular%20Behavior%20Tree%20Nodes.md#ModularBehaviorTreeNodes-ExecuteLua)

-
[AssertLua](Modular%20Behavior%20Tree%20Nodes.md#ModularBehaviorTreeNodes-AssertLua)

-
[GroupScope](Modular%20Behavior%20Tree%20Nodes.md#ModularBehaviorTreeNodes-GroupScope)

-
[Look](Modular%20Behavior%20Tree%20Nodes.md#ModularBehaviorTreeNodes-Look)

-
[Aim](Modular%20Behavior%20Tree%20Nodes.md#ModularBehaviorTreeNodes-Aim)

-
[AimAroundWhileUsingAMachingGun](Modular%20Behavior%20Tree%20Nodes.md#ModularBehaviorTreeNodes-AimAroundWhileUsingAMachingGun)

-
[ClearTargets](Modular%20Behavior%20Tree%20Nodes.md#ModularBehaviorTreeNodes-ClearTargets)

-
[TurnBody](Modular%20Behavior%20Tree%20Nodes.md#ModularBehaviorTreeNodes-turnbody)

-
[StopMovement](Modular%20Behavior%20Tree%20Nodes.md#ModularBehaviorTreeNodes-stopmovement)

-
[Teleport](Modular%20Behavior%20Tree%20Nodes.md#ModularBehaviorTreeNodes-Teleport)

-
[SmartObjectStatesWrapper](Modular%20Behavior%20Tree%20Nodes.md#ModularBehaviorTreeNodes-SmartObjectStatesWrapper)

-
[CheckIfTargetCanBeReached](Modular%20Behavior%20Tree%20Nodes.md#ModularBehaviorTreeNodes-CheckIfTargetCanBeReached)

-
[MonitorCondition](Modular%20Behavior%20Tree%20Nodes.md#ModularBehaviorTreeNodes-MonitorCondition)

-
[AnimationTagWrapper](Modular%20Behavior%20Tree%20Nodes.md#ModularBehaviorTreeNodes-AnimationTagWrapper)

-
[ShootFromCover](Modular%20Behavior%20Tree%20Nodes.md#ModularBehaviorTreeNodes-ShootFromCover)

-
[Shoot](Modular%20Behavior%20Tree%20Nodes.md#ModularBehaviorTreeNodes-Shoot)

-
[ThrowGrenade](Modular%20Behavior%20Tree%20Nodes.md#ModularBehaviorTreeNodes-ThrowGrenade)

-
[PullDownThreatLevel](Modular%20Behavior%20Tree%20Nodes.md#ModularBehaviorTreeNodes-PullDownThreatLevel)

##
- CryAction nodes -

-
[AnimateFragment](Modular%20Behavior%20Tree%20Nodes.md#ModularBehaviorTreeNodes-animatefragment)

##
- Game nodes-

-
[Melee](Modular%20Behavior%20Tree%20Nodes.md#ModularBehaviorTreeNodes-melee)

-
[KeepTargetAtADistance](Modular%20Behavior%20Tree%20Nodes.md#ModularBehaviorTreeNodes-keeptargetatadistance)

-
[SuppressHitReactions](Modular%20Behavior%20Tree%20Nodes.md#ModularBehaviorTreeNodes-suppresshitreaction)

-
[InflateAgentCollisionRadiusUsingPhysicsTrick](Modular%20Behavior%20Tree%20Nodes.md#ModularBehaviorTreeNodes-inflateagentcollisionradiususingphysicstrick)

-
[HoldFormation](Modular%20Behavior%20Tree%20Nodes.md#ModularBehaviorTreeNodes-holdformation)

-
[JoinFormation](Modular%20Behavior%20Tree%20Nodes.md#ModularBehaviorTreeNodes-joinformation)

-
[ScorcherDeploy](Modular%20Behavior%20Tree%20Nodes.md#ModularBehaviorTreeNodes-scorcherdeploy)

-
[RunWhileDeploying](Modular%20Behavior%20Tree%20Nodes.md#ModularBehaviorTreeNodes-runwhiledeploying)

-
[RunWhileDeployed](Modular%20Behavior%20Tree%20Nodes.md#ModularBehaviorTreeNodes-runwhiledeployed)

-
[HeavyShootMortar](Modular%20Behavior%20Tree%20Nodes.md#ModularBehaviorTreeNodes-heavyshootmortar)

-
[SquadScope](Modular%20Behavior%20Tree%20Nodes.md#ModularBehaviorTreeNodes-squadscope)

-
[SendSquadEvent](Modular%20Behavior%20Tree%20Nodes.md#ModularBehaviorTreeNodes-sendsquadevent)

-
[IfSquadCount](Modular%20Behavior%20Tree%20Nodes.md#ModularBehaviorTreeNodes-ifsquadcount)

##
Generic Nodes

These nodes are defined in CryCommon because they provide some basic functionality of the Modular Behavior Tree.

This nodes can be found into the folder
`
Code\CryEngine\CryCommon\BehaviorTree\
`

##
Loop

##
Description

The
**
Loop
**
 node allows to execute
**
one
**
 child a multiple number of times n (if n is not specified then it's considered to be infinite) or until the child
*
FAILS
*
 its execution.

##
Parameters

Parameter name

 |
Parameter description

 |

count

 |
The maximum amount of time the child of the Loop node will be executed

 |

##
Success/Failure

The node
*
SUCCEEDS
*
 if the maximum amount of repetition is reached.

 The node
*
FAILS
*
 if the child
*
FAILS
*
.

##
Usage example

```

`
<Loop count="3">
 <SomeChildNode />
</Loop>

`

```

##
LoopUntilSuccess

##
Description

The
**
LoopUntilSuccess
**
 node allows to execute
**
one
**
 child until it
*
SUCCEEDS
*
. A maximum number of attempts can be specified. If no maximum number of attempts is specified or if it's set to <= 0, then this node will try to run its child over and over again until the child succeeds.

##
Parameters

Parameter name

 |
Parameter description

 |

attemptCount

 |
The maximum amount of possible attempts to make the child succeeding.

 |

##
Success/Failure

The node
*
SUCCEEDS
*
 if the child
*
SUCCEEDS
*
.

 The node
*
FAILS
*
 if the maximum amount of allowed attempts is reached.

##
Usage example

```

`
<LoopUntilSuccess attemptCount="5">
 <SomeChildNode />
</LoopUntilSuccess>

`

```

##
Parallel

##
Description

The
**
Parallel
**
 node executes its children in parallel.

##
Parameters

Parameter name

 |
Parameter description

 |

failureMode

 |
The mode used to evaluate when the node fails. Accepted values are
**
any
**
 or
**
all
**
.
**
any
**
 is the default value.

 |

successMode

 |
The mode used to evaluate when the node succeeds. Accepted values are
**
any
**
 or
**
all
**
.
**
all
**
 is the default value.

 |

##
Success/Failure

When
**
successMode
**
 is set to
**
all
**
 the node
*
SUCCEEDS
*
 if all the children
*
SUCCEED
*
.

 When
**
successMode
**
 is set to
**
any
**
 the node
*
SUCCEEDS
*
 if any of the children
*
SUCCEEDS
*
.

 When
**
failureMode
**
 is set to
**
any
**
 the node
*
FAILS
*
 if any of the children
*
FAILS
*
.

 When
**
failureMode
**
 is set to
**
all
**
 the node
*
FAILS
*
 if all of the children
*
FAIL
*
.

##
Usage example

```

`
<Parallel successMode="any" failureMode="all">
 <SomeChildNode1 />
 <SomeChildNode2 />
 <SomeChildNode3 />
</Parallel>

`

```

##
Additional information/topics

-
*
In the current implementation a maximum amount of 32 children is allowed.
*

-
*
In case the SUCCESS and FAILURE limits are reached at the same time, the Parallel will SUCCEED.
*

##
Selector

##
Description

The
**
Selector
**
 node executes its children one at a time, stopping at the first one that succeeds.

##
Parameters

The
**
Selector
**
 node doesn't support any parameters.

##
Success/Failure

The node executes the children in sequential order and
*
SUCCEEDS
*
 as soon as one of the child
*
SUCCEEDS
*
. The children that follows the succeeding one are not executed.

 The node
*
FAILS
*
 if all the children
*
FAIL
*
.

##
Usage example

```

`
<Selector>
 <SomeChildNode1 />
 <SomeChildNode2ToExecuteIfSomeChildNode1Fails />
 <SomeChildNode3ToExecuteIfSomeChildNode2Fails />
</Selector>

`

```

##
Sequence

##
Description

The
**
Sequence
**
 node executes its children one at a time in order.

##
Parameters

The
**
Sequence
**
 node doesn't support any parameters.

##
Success/Failure

The node
*
SUCCEEDS
*
 if
**
all
**
 the children
*
SUCCEED
*
.

 The node
*
FAILS
*
 if
**
any
**
 of the children
*
FAILS
*
.

##
Usage example

```

`
<Sequence>
 <SomeChildNode1 />
 <SomeChildNode2 />
 <SomeChildNode3 />
</Sequence>

`

```

##
Additional information/topics

*
In the current implementation the maximum allowed amount of children is 255.
*

##
StateMachine

##
Description

The
**
StateMachine
**
 is a
*
composite node
*
 allowed to have one or more children.

 The children of a
**
StateMachine
**
 node
MUST
 be of the type
**
State
**
.

 Only one child at any given time is allowed to be executed and the first one defined is the first one to be executed.

 The current status of a
**
StateMachine
**
 node is the same as the one of the child that is currently selected to be executed.

##
State

##
Description

The
**
State
**
 node is the basic block of a
**
StateMachine
**
 node.

 Each
**
State
**
 node MUST have a
**
BehaviorTree
**
 node.

 Each
**
State
**
 node MAY have a
**
Transitions
**
 block.

 A State node executes the content of its
**
BehaviorTree
**
 node and it can transition to another state (or itself) as described into the
**
Transitions
**
 block.

**
Note that if a state is told to transition into itself while running, it will first be terminated and then re-initialized and then updated again.
**

##
Parameters

Parameter name

 |
Parameter description

 |

name

 |
The name of the state. It MUST be unique in the scope of the StateMachine.

 |

**
Transitions
**

 The
**
Transitions
**
 are described inside the
**
State
**
 node as follows.

```

`
 <Transitions>
  <Transition onEvent="EventOrTransitionSignalName" to="OtherStateName"/>
 </Transitions>

`

```

Inside the <Transitions></Transitions> tag we can specify as many transitions as we want.

 Each Transition must have the following parameters

-
**
onEvent
**
 identifies the string name of the event that could cause the transition to happen.

-
**
to
**
 identifies the state name where transitioning to.

##
Success/Failure

The node
*
SUCCEEDS
*
 if the content of the
**
BehaviorTree
**
 node
*
SUCCEEDS
*
.

 The node
*
FAILS
*
 if the content of the
**
BehaviorTree
**
 node
*
FAILS
*
.

##
Usage example

```

`
<State name="StateName">
 <Transitions>
  <Transition onEvent="EventOrTransitionSignalName" to="OtherStateName" />
 </Transitions>
 <BehaviorTree>
  <SomeChildNode />
 </BehaviorTree>
</State>

`

```

##
Additional information/topics

*
The xml tag
*

**
*
Transitions
*
**

*
and its children
*

**
*
Transition(s)
*
**

*
are not ModularBehaviorTree nodes.
*
*
If a transition specifies a destination state that doesn't existing an error message will be displayed when parsing the MBT
*
*
In the current implementation of the MBT, the events are AISignals.
*

##
Parameters

The
**
StateMachine
**
 node doesn't support any parameters.

##
Success/Failure

The node
*
SUCCEEDS
*
 if the current
**
State
**
 child node
*
SUCCEEDS
*
.

 The node
*
FAILS
*
 if the current
**
State
**
 child node
*
FAILS
*
.

##
Usage example

```

`
<StateMachine>
 <State />
 <State name="State1" />
 <State name="State2" />
</StateMachine>

`

```

##
SuppressFailure

##
Description

The
**
SuppressFailure
**
 node owns and executes
**
one
**
 child. It will
*
SUCCEED
*
 irregardless of the result of the child's execution.

##
Parameters

The
**
SuppressFailure
**
 node doesn't support any parameters.

##
Success/Failure

The node
*
SUCCEEDS
*
 as soon as the child execution finishes.

##
Usage example

```

`
<SuppressFailure>
 <SomeChildThatCanFail />
</SuppressFailure>

`

```

##
Timeout

##
Description

The
**
Timeout
**
 node
*
FAILS
*
 after a certain amount of time has passed.

##
Parameters

Parameter name

 |
Parameter description

 |

duration

 |
The amount of seconds before the failure of the node occurs.

 |

##
Success/Failure

The node
*
FAILS
*
 if it runs for more than the amount of time specified by the
**
duration
**
 parameter.

##
Usage example

```

`
<Timeout duration=5" />

`

```

##
Wait

##
Description

The
**
Wait
**
 node
*
SUCCEEDS
*
 after a certain amount of time has passed.

##
Parameters

Parameter name

 |
Parameter description

 |

duration

 |
The amount of seconds before the failure of the node occurs.

 |

variation

 |
The extra amount of time that will be added on top of the specified duration, in the range
. This allows to have random variations between different executions of the node.

 |

##
Success/Failure

The node
*
SUCCEEDS
*
 as soon as it runs for more than the amount of time specified by the
**
duration
**
 parameter (plus the random variation).

##
Usage example

```

`
<Wait duration="5" variation="1" />

`

```

##
AI System Nodes

These nodes are defined into the file
**
BehaviorTreeNodes_AI.cpp
**
.

##
Bubble

##
Description

The
**
Bubble
**
 node displays a message in a 'speech bubble' above the agent.

##
Parameters

Parameter name

 |
Parameter description

 |

message

 |
The message that should be shown in the 'speech bubble'.

 |

duration

 |
The amount of seconds to show the message (defaults to: 0.0).

 |

balloon

 |
**
1
**
 will show the message in a 'balloon' above the agent;
**
0
**
 will not (defaults to:
**
1
**
).

 |

log

 |
**
1
**
 will write the message in the general purpose log;
**
0
**
 will not (defaults to:
**
1
**
).

 |

##
Success/Failure

The node
*
SUCCEEDS
*
 immediately after having queued the message to be displayed.

##
Usage example

```

`
<Bubble message="MessageToBeDisplayedAndOrLogged" duration="5.0" balloon="true" log="true" />

`

```

##
Additional information/topics

*
More information about the
*

**
*
AI Bubble System
*
**

*
can be found in Confluence.
*

##
GoalPipe

##
Description

**
Deprecated
**
: The
**
GoalPipe
**
 node executes a custom defined GoalPipe.

##
Parameters

Parameter name

 |
Parameter description

 |

name

 |
The name of the Goal Pipe.

 |

##
Success/Failure

The node
*
SUCCEEDS
*
 when the goal pipe ends its execution.

##
Usage example

```

`
<GoalPipe name="GoalpipeName">
  <SomeGoalPipeXMLTags />
</GoalPipe>

`

```

##
Additional information/topics

-
Should only be used for backwards compatibility.

-
The XML children that this node contains are not Module Behavior Tree nodes, but xml tags that are defined by the
[Goal Pipes system](../Obsolete%20AI%20Documentation/Obsolete%20AI%20Scripting%20Documentation/Goal%20Pipes.md)
.

##
LuaBehavior

##
Description

Deprecated: The
**
LuaBehavior
**
 node executes a Lua behavior.

##
Parameters

Parameter name

 |
Parameter description

 |

name

 |
The name of the behavior.

 |

##
Success/Failure

The node
*
SUCCEEDS
*
 if the behavior finished running or if no behavior with the given name exists.

##
Usage example

```

`
<LuaBehavior name="NameOfTheLuaBehavior" />

`

```

##
Additional information/topics

-
Should only be used for backwards compatibility.

-
For more information about behaviors, see
.

##
Move

##
Description

The
**
Move
**
 node is responsible to move the agent from his current position to the specified destination.

 If the destination is a target then the end position is updated if not reached while the target moves.

##
Parameters

Parameter name

 |
Parameter description

 |

speed

 |
Movement style: the movement speed, which can be any of the following:
**
Walk
**
,
**
Run
**
, or
**
Sprint
**
.

 |

stance

 |
Movement style: the stance, which can be any of the following:
**
Relaxed
**
,
**
Alerted
**
, or
**
Stand
**
 (defaults to:
**
Stand
**
).

 |

bodyOrientation

 |
Movement style: the body orientation, which can be any of the following:
**
FullyTowardsMovementDirection
**
,
**
FullyTowardsAimOrLook
**
, or
**
HalfwayTowardsAimOrLook
**
 (defaults to:
**
HalfwayTowardsAimOrLook
**
).

 |

moveToCover

 |
Movement style:
**
true
**
 if the agent is moving into cover; otherwise
**
false
**
 (defaults to:
**
false
**
).

 |

turnTowardsMovementDirectionBeforeMoving

 |
Movement style:
**
true
**
 if the agent should first turn into the direction of movement before actually moving;
**
false
**
 if not (defaults to:
**
false
**
).

 |

strafe

 |
Movement style:
**
true
**
 if the agent is allowed to strafe;
**
false
**
 it not (defaults to:
**
false
**
).

 |

glanceInMovementDirection

 |
Movement style:
**
true
**
 if the agent is allowed to glance in the direction of movement;
**
false
**
 if it should always look at its look-at target (defaults to:
**
false
**
).

 |

to

 |
The movement destination, which can be one of the following:
**
Target
**
,
**
Cover
**
,
**
RefPoint
**
 or
**
LastOp
**
.

 |

stopWithinDistance

 |
If within this distance from the target, we can stop moving (defaults to 0.0) .

 |

stopDistanceVariation

 |
Additional random stopping distance (defaults to 0.0).

 |

fireMode

 |
The fire mode while moving:
**
Off
**
,
**
Burst
**
,
**
Continuous
**
,
**
Forced
**
,
**
Aim
**
,
**
Secondary
**
,
**
SecondarySmoke
**
,
**
Melee
**
,
**
Kill
**
,
**
BurstWhileMoving
**
,
**
PanicSpread
**
,
**
BurstDrawFire
**
,
**
MeleeForced
**
,
**
BurstSnipe
**
,
**
AimSweep
**
, or
**
BurstOnce
**
 (defaults to
**
Off
**
).

 |

avoidDangers

 |
**
1
**
 if dangers should be avoided while moving,
**
0
**
 if they can be ignored (defaults to:
**
1
**
).

 |

avoidGroupMates

 |
**
1
**
 if group mates should be avoided while moving,
**
0
**
 if they can be ignored (defaults to:
**
1
**
).

 |

considerActorsAsPathObstacles

 |
**
1
**
 if any actor should be considered a path obstacle that the path-finder should avoid,
**
0
**
 if they can be ignored (defaults to:
**
0
**
).

 |

lengthToTrimFromThePathEnd

 |
The resulting path-finder path will be trimmed by the specified amount of distance. Positive values will trim from the end of the path; negative values will trim from the start of the path (defaults to: 0.0).

 |

##
Success/Failure

The node
*
SUCCEEDS
*
 if the destination is reached.

 The node
*
FAILS
*
 if the destination is deemed unreachable.

##
Usage example

```

`
<Move to="DestinationType" stance="StanceName" fireMode="FiremodeName" speed="SpeedName" stopWithinDistance="3" />

`

```

##
Additional information/topics

Destination tag

 |
Description

 |

**
Target
**

 |
The current attention target.

 |

**
Cover
**

 |
The current cover position.

 |

**
RefPoint
**

 |
The current reference position.

 |

**
LastOp
**

 |
The position of the last successful position related operation.

 |

Fire mode tag

 |
Description

 |

**
Off
**

 |
Do not fire.

 |

**
Burst
**

 |
Fire in bursts - living targets only.

 |

**
Continuous
**

 |
Fire continuously - living targets only.

 |

**
Forced
**

 |
Fire continuously - allow any target.

 |

**
Aim
**

 |
Aim target only - allow any target.

 |

**
Secondary
**

 |
Fire secondary weapon (grenades, ....).

 |

**
SecondarySmoke
**

 |
Fire smoke grenade.

 |

**
Melee
**

 |
Melee.

 |

**
Kill
**

 |
No missing, shoot directly at the target, no matter what aggression/attackRange/accuracy is.

 |

**
BurstWhileMoving
**

 |
Fire in bursts, while moving and too far away from the target.

 |

**
PanicSpread
**

 |
Fire randomly in the general direction of the target.

 |

**
BurstDrawFire
**

 |
Fire in bursts, in an attempt to draw enemy fire.

 |

**
MeleeForced
**

 |
Melee, without distance restrictions.

 |

**
BurstSwipe
**

 |
Fire in burst, aiming for a head-shot.

 |

**
AimSweep
**

 |
Keep aiming at the target, but not allowed to fire.

 |
 |

**
BurstOnce
**

 |
Fire a single burst.

 |

##
QueryTPS

##
Description

The
**
QueryTPS
**
 node performs a Tactical Position System query and waits for a result.

##
Parameters

Parameter name

 |
Parameter description

 |

name

 |
The name of the TPS query to use.

 |

register

 |
Where to store result of the TPS query:
**
RefPoint
**
 or
**
Cover
**
 (defaults to:
**
Cover
**
 ).

 |

##
Success/Failure

The node
*
SUCCEEDS
*
 if the TPS returns a tactical position.

 The node
*
FAILS
*
 if the TPS does not find a tactical position.

##
Usage example

```

`
<QueryTPS name="NameOfTheQuery" register="NameOfTheRegister" />

`

```

##
Additional information/topics

_For more information about the
**
Tactical Point System
**
 you can go
[Tactical Point System](../Tactical%20Point%20System.md)

##
IfTime

##
Description

The IfTime node executes the child node if the time condition is satisfied.

##
Parameters

Parameter name

 |
Parameter description

 |

since

 |
Name of the time stamp used for the condition.

 |

isMoreThan

 |
Defines the condition to be a comparison if the value of the time stamp is more than this value. (Exclusive with the parameter 'isLessThan')

 |

isLessThan

 |
Defines the condition to be a comparison if the value of the time stamp is less than this value. (Exclusive with the parameter 'isMoreThan')

 |

orNeverBeenSet

 |
(Optional) Changes the behavior of the node in case the time stamp was never set, instead of failing the node will succeed.

 |

##
Success/Failure

The node
*
FAILS
*
 if the time condition is not satisfied.

 The node
*
FAILS
*
 if the time stamp was not previously set, unless the parameter 'orNeverBeenSet' is true, making the node
*
SUCCEED
*
 instead.

 Otherwise, the node returns the result of the execution of its child node.

##
Usage examples

```

`
<IfTime since="FragGrenadeThrownInGroup" isMoreThan="5.0" orNeverBeenSet="1">
  <ThrowGrenade type="frag" />
</IfTime>

`

```

##
WaitUntilTime

##
Description

The WaitUntilTime node executes until the time condition is satisfied.

##
Parameters

Parameter name

 |
Parameter description

 |

since

 |
Name of the time stamp used for the condition.

 |

isMoreThan

 |
Defines the condition to be a comparison if the value of the time stamp is more than this value. (Exclusive with the parameter 'isLessThan')

 |

isLessThan

 |
Defines the condition to be a comparison if the value of the time stamp is less than this value. (Exclusive with the parameter 'isMoreThan')

 |

succeedIfNeverBeenSet

 |
(Optional) Changes the behavior of the node in case the time stamp was never set, instead of failing the node will succeed.

 |

##
Success/Failure

The node
*
SUCCEEDS
*
 if the time stamp was not set previously set and the parameter 'succeedIfNeverBeenSet' is true.

 Otherwise, the node returns the result of the execution of its child node.

##
Usage examples

```

`
<WaitUntilTime since="BeingShotAt" isMoreThan="7" />

`

```

##
AssertTime

##
Description

The AssertTime node succeeds if the time condition is satisfied.

##
Parameters

Parameter name

 |
Parameter description

 |

since

 |
Name of the time stamp used for the condition.

 |

isMoreThan

 |
Defines the condition to be a comparison if the value of the time stamp is more than this value. (Exclusive with the parameter 'isLessThan')

 |

isLessThan

 |
Defines the condition to be a comparison if the value of the time stamp is less than this value. (Exclusive with the parameter 'isMoreThan')

 |

orNeverBeenSet

 |
(Optional) Changes the behavior of the node in case the time stamp was never set, instead of failing the node will succeed.

 |

##
Success/Failure

The node
*
SUCCEEDS
*
 if the time condition is true, if not then it
*
FAILS
*
.

 The node
*
FAILS
*
 if the time stamp was not previously set, unless the parameter 'orNeverBeenSet' is true, making the node
*
SUCCEED
*
 instead.

##
Usage examples

```

`
<AssertTime since="GroupLostSightOfTarget" isLessThan="10" orNeverBeenSet="1" />

`

```

##
Priority & Case

##
Description

Executes the child with the current highest priority.

 The priorities are derived from the order in which the children are defined and the satisfaction of their individual conditions, so that the highest priority goes to the first child to have its condition met.

 The children's conditions must be specified with the use of Case nodes with the exception of the last child which is considered to be the default case, meaning that its condition is always true and cannot be specified.

##
Parameters

Parameter name

 |
Parameter description

 |

condition

 |
Specifies the condition of the child.

 |

##
Success/Failure

The node returns the result of the execution of the child node.

##
Usage examples

```

`
<Priority>
  <Case condition="TargetInCloseRange and TargetVisible">
    <Melee target="AttentionTarget" />
  </Case>
  <Case>
    <Look at="Target" />
  </Case>
</Priority>

`

```

##
LuaGate

##
Description

Executes the child node if the result from running a lua snippet is true.

##
Parameters

Parameter name

 |
Parameter description

 |

code

 |
The lua code to be executed.

 |

##
Success/Failure

The node
*
FAILS
*
 if the lua code returns a value different from true.

 Otherwise, the node returns the result of the execution of its child node.

##
Usage examples

```

`
<LuaGate code="return AI.GetGroupScopeUserCount(entity.id, 'DeadBodyInvestigator') == 0">

`

```

##
RandomGate

##
Description

Executes or not the child node based on a random chance.

##
Parameters

Parameter name

 |
Parameter description

 |

opensWithChance

 |
The chance of executing the child node [0.0 - 1.0].

 |

##
Success/Failure

The node
*
FAILS
*
 if the child is not executed.

 Otherwise, the node returns the result of the execution of its child node.

##
Usage examples

```

`
<RandomGate opensWithChance="0.5">

`

```

##
AdjustCoverStance

##
Description

Updates the agent's cover stance based on the maximum height in which his current cover is still effective.

##
Parameters

Parameter name

 |
Parameter description

 |

duration

 |
(Optional) The amount of seconds the node will execute. Use 'continuous' for unlimited time.

 |

variation

 |
(Optional) The extra random amount of seconds that will be added on top of the specified duration, in the range [0, variation].

 |

##
Success/Failure

The node
*
SUCCEEDS
*
 if the duration of execution elapses.

 The node
*
FAILS
*
 if the child is not in cover.

##
Usage examples

```

`
<AdjustCoverStance duration="5.0" variation="1.0"/>

`

```

##
SetAlertness

##
Description

Sets the agent's alertness value.

##
Parameters

Parameter name

 |
Parameter description

 |

value

 |
The alertness value [0-2].

 |

##
Success/Failure

The node
*
SUCCEEDS
*
 immediately.

##
Usage examples

```

`
<SetAlertness value="1" />

`

```

##
Log

##
Description

Adds a message to the agent's personal log.

##
Parameters

Parameter name

 |
Parameter description

 |

message

 |
The message to be logged.

 |

##
Success/Failure

The node
*
SUCCEEDS
*
 immediately.

##
Usage examples

```

`
<Log message="Investigating suspicious activity." />

`

```

##
Communicate

##
Description

Request the communication manager to play one of the agent's readabilities.

##
Parameters

Parameter name

 |
Parameter description

 |

name

 |
The name of the communication to be played.

 |

channel

 |
The channel on which the communication is to be set.

 |

waitUntilFinished

 |
(Optional) Specifies if the execution should wait for the end of the communication before finishing.

 |

timeout

 |
(Optional) The threshold defining the maximum amount of seconds the node will wait.

 |

expiry

 |
(Optional) The amount of seconds the communication can wait for the channel to be clear.

 |

minSilence

 |
(Optional) The amount of seconds the channel will be silenced after the communication is played.

 |

ignoreSound

 |
(Optional) Sets the sound component of the communication to be ignored.

 |

ignoreAnim

 |
(Optional) Sets the animation component of the communication to be ignored.

 |

##
Success/Failure

The node
*
SUCCEEDS
*
 if the timeout elapses or when the readability is complete if the node is set to wait until the communication is finished.

##
Usage examples

```

`
<Communicate name="Advancing" channel="Tactic" expiry="1.0" waitUntilFinished="0" />

`

```

##
Animate

##
Description

Sets the agent to play an animation.

##
Parameters

Parameter name

 |
Parameter description

 |

name

 |
The name of the animation to be played.

 |

urgent

 |
(Optional) Adds the urgent flag to the animation.

 |

loop

 |
(Optional) Adds the loop flag to the animation.

 |

setBodyDirectionTowardsAttentionTarget

 |
(Optional) Changes the body target direction to be facing the attention target.

 |

##
Success/Failure

The node
*
SUCCEEDS
*
 if the animation failed to be initialized or when it is finished.

##
Usage examples

```

`
<Animate name="LookAround" loop="1"/>

`

```

##
Signal

##
Description

Sends a signal to the AI system.

##
Parameters

Parameter name

 |
Parameter description

 |

name

 |
The name of the signal to be sent.

 |

filter

 |
(Optional) The filter to be applied to the signal in the AI system.

 |

##
Success/Failure

The node
*
SUCCEEDS
*
 immediately.

##
Usage examples

```

`
<Signal name="StartedJumpAttack" />

`

```

##
SendTransitionSignal

##
Description

Sends a signal destined for a state machine node on the behavior tree, with the explicit intent of causing a change of state.

##
Parameters

Parameter name

 |
Parameter description

 |

name

 |
The name of the signal to be sent.

 |

##
Success/Failure

This node does not succeed or fail.

##
Usage examples

```

`
<SendTransitionSignal name="LeaveSearch" />

`

```

##
Stance

##
Description

Sets the stance of the agent.

##
Parameters

Parameter name

 |
Parameter description

 |

name

 |
The name of the stance to be set. [Relaxed, Alerted, Crouch, Stand]

 |

stanceToUseIfSlopeIsTooSteep

 |
(Optional) The alternative stance to be used in case the slope is too steep.

 |

allowedSlopeNormalDeviationFromUpInDegrees

 |
(Optional) Defines how steep can the slope be for this stance.

 |

##
Success/Failure

The node
*
SUCCEEDS
*
 immediately.

##
Usage examples

```

`
<Stance name="Crouch" allowedSlopeNormalDeviationFromUpInDegrees="30" stanceToUseIfSlopeIsTooSteep="Stand" />

`

```

##
IfCondition

##
Description

Executes the child node if the specified condition is satisfied.

##
Parameters

Parameter name

 |
Parameter description

 |

condition

 |
Specifies the condition to be checked.

 |

##
Success/Failure

The node returns the result of the child's execution if the condition is true, otherwise it
*
FAILS
*
.

##
Usage examples

```

`
<IfCondition condition="TargetVisible">
  <Communicate name="AttackNoise" channel="BattleChatter" expiry="2.0" waitUntilFinished="1" />
</IfCondition>

`

```

##
AssertCondition

##
Description

Succeeds if the specified condition is satisfied.

##
Parameters

Parameter name

 |
Parameter description

 |

condition

 |
Specifies the condition to be checked.

 |

##
Success/Failure

The node
*
SUCCEEDS
*
 if the condition is true, otherwise it
*
FAILS
*
.

##
Usage examples

```

`
<AssertCondition condition="HasTarget" />

`

```

##
LuaWrapper

##
Description

Executes the child node with the additional option of running a lua script on the start and/or end of that execution.

##
Parameters

Parameter name

 |
Parameter description

 |

onEnter

 |
(Optional) The code to be executed at the start.

 |

onExit

 |
(Optional) The code to be executed at the end.

 |

##
Success/Failure

The node returns the result of the child's execution.

##
Usage examples

```

`
<LuaWrapper onEnter="entity:EnableSearchModule()" onExit="entity:DisableSearchModule()">
  <Animate name="AI_SearchLookAround" />
</LuaWrapper>

`

```

##
ExecuteLua

##
Description

Executes a lua script.

##
Parameters

Parameter name

 |
Parameter description

 |

code

 |
The code to be executed.

 |

##
Success/Failure

The node always
*
SUCCEEDS
*
.

##
Usage examples

```

`
<ExecuteLua code="entity:SetEyeColor(entity.EyeColors.Relaxed)" />

`

```

##
AssertLua

##
Description

Executes Lua code and translates the return value of that code from true/false to success/failure. It can then be used to build preconditions in the modular behavior tree.

##
Parameters

Parameter name

 |
Parameter description

 |

code

 |
The code to be executed.

 |

##
Success/Failure

The node
*
SUCCEEDS
*
 if the lua code returns value is true, otherwise it
*
FAILS
*
.

##
Usage examples

```

`
<AssertLua code="return entity:IsClosestToTargetInGroup()" />

`

```

##
GroupScope

##
Description

Tries to enter the agent in a group scope, which is limited by the specified amount of concurrent users. If the node succeeds to do that, then the child node is executed.

##
Parameters

Parameter name

 |
Parameter description

 |

name

 |
The name of the group scope to be entered.

 |

allowedConcurrentUsers

 |
(Optional) The maximum number of simultaneous users of that can be in the specified group scope.

 |

##
Success/Failure

The node
*
FAILS
*
 the agent could not enter the group scope, otherwise returns the result of the execution of the child.

##
Usage examples

```

`
<GroupScope name="DeadBodyInvestigator" allowedConcurrentUsers="1">
  <SendTransitionSignal name="GoToPrepareToInvestigateDeadBody" />
</GroupScope>

`

```

##
Look

##
Description

Adds a location for the agent to look at and clears it the when the node stops executing.

##
Parameters

Parameter name

 |
Parameter description

 |

at

 |
The location to look at [ClosestGroupMember,RefPoint,Target].

 |

##
Success/Failure

This node does not succeed or fail.

##
Usage examples

```

`
<Look at="ClosestGroupMember" />

`

```

##
Aim

##
Description

Sets the location where the agent should to aim at, clearing it the when the node stops executing.

##
Parameters

Parameter name

 |
Parameter description

 |

at

 |
The location to look at [RefPoint,Target].

 |

angleThreshold

 |
(Optional) The tolerance angle for the agent to be considered aiming in the desired direction.

 |

durationOnceWithinThreshold

 |
(Optional) The amount of seconds to keep on aiming.

 |

##
Success/Failure

The node
*
SUCCEEDS
*
 after aiming in the desired direction for the specified time, if the location is not valid or if the timeout elapses.

##
Usage examples

```

`
<Aim at="Target" durationOnceWithinThreshold="2.0" />

`

```

##
AimAroundWhileUsingAMachingGun

##
Description

Updates the aim direction of the agent for when he is using a mounted machine gun.

##
Parameters

Parameter name

 |
Parameter description

 |

maxAngleRange

 |
(Optional) The maximum amount to deviate from the original position.

 |

minSecondsBeweenUpdates

 |
(Optional) The minimum amount of delay between updates.

 |

useReferencePointForInitialDirectionAndPivotPosition

 |
 |

##
Success/Failure

The node does not succeed or fail.

##
Usage examples

```

`
<AimAroundWhileUsingAMachingGun minSecondsBeweenUpdates="2.5" maxAngleRange="30" useReferencePointForInitialDirectionAndPivotPosition="1"/>

`

```

##
ClearTargets

##
Description

Clears the agent's targets information.

##
Success/Failure

The
*
SUCCEEDS
*
 immediately.

##
Usage examples

```

`
<ClearTargets />

`

```

##
StopMovement

##
Description

The
**
StopMovement
**
 node sends a request to the Movement System to stop all the movements.

##
Parameters

Parameter name

 |
Parameter description

 |

waitUntilStopped

 |
**
1
**
 if the node should wait for the Movement System to have processed the request;
**
0
**
 if not.

 |

waitUntilIdleAnimation

 |
**
1
**
 if the node should wait until the
*
Motion_Idle
*
 animation fragment started running in Mannequin,
**
0
**
 if not.

 |

##
Success/Failure

The node
*
SUCCEEDS
*
 if the stop request has been completed.

##
Usage example

```

`
<StopMovement waitUntilStopped="1" waitUntilIdleAnimation="0" />

`

```

##
Additional information/topics

*
Note that this may not always immediately physically stop the agent! The Movement System may be dependent on the influence of animations and physics, for example, which may result in a 'natural' stop and not an immediate stop.
*

##
Teleport

##
Description

Teleport the character when the destination point and the source point are both outside of the camera view.

##
Success/Failure

The node
*
SUCCEEDS
*
 after the character is teleported.

##
Usage examples

```

`
<Teleport />

`

```

##
SmartObjectStatesWrapper

##
Description

Executes the child node with the additional option of setting certain smart objects states on the start and/or end of that execution.

##
Parameters

Parameter name

 |
Parameter description

 |

onEnter

 |
(Optional) The smart object states to set at the start of the child's execution.

 |

onExit

 |
(Optional) The smart object states to set at the end of the child's execution.

 |

##
Success/Failure

The node returns the result of the execution of its child node.

##
Usage examples

```

`
<SmartObjectStatesWrapper onEnter="InSearch" onExit="-InSearch">
  <Animate name="LookAround" />
</SmartObjectStatesWrapper>

`

```

##
CheckIfTargetCanBeReached

##
Description

Checks if the agent's attention target can be reached.

##
Parameters

Parameter name

 |
Parameter description

 |

mode

 |
Defines the target to use. [UseLiveTarget,UseAttentionTarget]

 |

##
Success/Failure

The node
*
SUCCEEDS
*
 if it can reach the target, otherwise it
*
FAILS
*
.

##
Usage examples

```

`
<CheckIfTargetCanBeReached mode="UseLiveTarget" />

`

```

##
MonitorCondition

##
Description

Continuously check for the state of a specified condition.

##
Parameters

Parameter name

 |
Parameter description

 |

condition

 |
Specifies the condition to be checked.

 |

##
Success/Failure

The node
*
SUCCEEDS
*
 when the condition is satisfied.

##
Usage examples

```

`
<MonitorCondition condition="TargetVisible" />

`

```

##
AnimationTagWrapper

##
Description

Executes the child node, adding an animation tag for the agent on the beginning of that execution and clearing it on the end.

##
Parameters

Parameter name

 |
Parameter description

 |

name

 |
The animation tag to be set.

 |

##
Success/Failure

The node returns the result of the execution of its child node.

##
Usage examples

```

`
<AnimationTagWrapper name="ShootFromHip">
  <Shoot at="Target" stance="Stand" duration="5" fireMode="Burst" />
</AnimationTagWrapper>

`

```

##
ShootFromCover

##
Description

Sets the agent to shoot at the target from cover and adjusts his stance accordingly.

##
Parameters

Parameter name

 |
Parameter description

 |

duration

 |
The amount of seconds the node should execute.

 |

fireMode

 |
The firemode to be used for shooting.

 |

aimObstructedTimeout

 |
(Optional) The amount of seconds the aim is allowed to be obstructed.

 |

##
Success/Failure

The node
*
SUCCEEDS
*
 if the duration of execution elapses.

 The node
*
FAILS
*
 if the agent is not in cover, if there's no shoot posture or if the aim obstructed timeout elapses.

##
Usage examples

```

`
<ShootFromCover duration="10" fireMode="Burst" aimObstructedTimeout="3" />

`

```

##
Shoot

##
Description

Sets the agent to shoot at a target or a location.

##
Parameters

Parameter name

 |
Parameter description

 |

duration

 |
The amount of seconds the node should execute.

 |

at

 |
The location to shoot at [AttentionTarget, ReferencePoint, LocalSpacePosition].

 |

fireMode

 |
The firemode to be used for shooting.

 |

stance

 |
The stance to be set while shooting [Relaxed, Alerted, Crouch, Stand].

 |

position

 |
(Mandatory only if the target is a local space position) The local space position to be used as the target.

 |

stanceToUseIfSlopeIsTooSteep

 |
(Optional) The alternative stance to be used in case the slope is too steep.

 |

allowedSlopeNormalDeviationFromUpInDegrees

 |
(Optional) Defines how steep can the slope be for this stance.

 |

aimObstructedTimeout

 |
(Optional) The amount of seconds the aim is allowed to be obstructed.

 |

##
Success/Failure

The node
*
SUCCEEDS
*
 if the duration of execution elapses.

 The node
*
FAILS
*
 if the aim obstructed timeout elapses.

##
Usage examples

```

`
<Shoot at="Target" stance="Crouch" fireMode="Burst" duration="5" allowedSlopeNormalDeviationFromUpInDegrees="30" stanceToUseIfSlopeIsTooSteep="Stand" />

`

```

##
ThrowGrenade

##
Description

Sets the agent to attempt a grenade throw.

##
Parameters

Parameter name

 |
Parameter description

 |

timeout

 |
The maximum amount of seconds the node will wait for the grenade to be thrown.

 |

type

 |
The type of grenade [emp, frag, smoke].

 |

##
Success/Failure

The node
*
SUCCEEDS
*
 if a grenade is thrown before it timeouts, otherwise The node
*
FAILS
*
.

##
Usage examples

```

`
<ThrowGrenade type="emp" timeout="3" />

`

```

##
PullDownThreatLevel

##
Description

Sets the agent to lower his notion the target's threat.

##
Success/Failure

The node
*
SUCCEEDS
*
 immediately.

##
Usage examples

```

`
<PullDownThreatLevel to="Suspect" />

`

```

##
CryAction Nodes

These nodes are defined into the file
**
BehaviorTreeNodes_Action.cpp
**
.

##
AnimateFragment

##
Description

The
**
AnimateFragment
**
 node plays an Mannequin animation fragment and waits until the animation finishes.

##
Parameters

Parameter name

 |
Parameter description

 |

name

 |
The name of the fragment we want to play.

 |

##
Success/Failure

The node
*
SUCCEEDS
*
 if the animations is correctly played or if no operation was needed.

 The node
*
FAILS
*
 if an error occurs while trying to queue the request to play the specified fragment.

##
Usage example

```

`
<AnimateFragment name="SomeFragmentName" />

`

```

##
Additional information/topics

*
To have a better understanding of Mannequin you can search in Confluence more information about it.
*

##
Game Nodes

These nodes are mostly used and created to offer some game specific functionality. Each type of game has usually multiple characters of different types and each one may need to trigger specific logic to perform action in the game using his peculiarities.

 Keep in mind that game specific nodes are really likely to not be good for "general use" and that may need to be tweaked to fit the needs of the game you want to develop.

##
Melee

##
Description

The
**
Melee
**
 node is responsible to trigger a melee attack against the agent target. The
**
Melee
**
 node
*
SUCCEEDS
*
 irregardless the fact the melee attack can/cannot be performed and damages or not the target.

 A melee attack is performed is the following condition are satisfied:

-
If the failIfTargetNotInNavigationMesh is set, the target MUST be on a valid walkable position. Some melee animations could move the character pushing him outside the navigable area if trying to melee a target outside the MNM.

-
If the target is not in between the threshold angle specified by the entity lua value melee.angleThreshold

##
Parameters

Parameter name

 |
Parameter description

 |

target

 |
The target of the melee. This parameter could be set as
**
AttentionTarget
**
 or a generic
**
RefPoint
**

 |

cylinderRadius

 |
The radius of the cylinder used for the collision check of the hit

 |

hitType

 |
The type of the hit that will be sent to the game rules. Default is
**
CGameRules::EHitType::Melee
**

 |

failIfTargetNotInNavigationMesh

 |
It defines if the node should not try to melee a target that is outside the navigation mesh. This will only produce the actual melee attack to not be performed, the Melee node will still
*
SUCCEEDS
*
.

 |

materialEffect

 |
The material effect name used when the melee attack hits the target.

 |

##
Success/Failure

The node
*
SUCCEEDS
*
 irregardless of the actual execution of the melee attack.

##
Usage example

```

`
<Melee target="AttentionTarget" cylinderRadius="1.5" hitType="hitTypeName" materialEffect="materialEffectName" />

`

```

##
Additional information/topics

*
At first glance it can sound strange the node always succeeds even if the actual attack fails or can't be performed. This is due to the fact that a failure in this node is not necessary of interest for the Behavior Tree Logic. A fail option can be added in case your game has to react to this particular situation.
*

*
In the lua file that define the specific character in use you can find the lua table
*

**
*
melee
*
**

*
that can look similar to the following one.
*

```

`
melee =
{
  damage = 400,
  damageOffset = {x=0, y=2, z=0}; -- deprecated
  damageRadius = 1.8, -- deprecated
  damageRadiusShort = 1.5, -- deprecated
  hitRange = 1.8,
  knockdownChance = 0.1,
  impulse = 600,
  angleThreshold = 180,
},

`

```

*
Here you can find an explanation of the used parameter
*

Parameter name

 |
Parameter description

 |

damage

 |
This parameter defines the amount of damage the melee attack inflicts to the target.

 |

damageOffset

 |
Deprecated parameter

 |

damageRadius

 |
Deprecated parameter

 |

damageRadiusShort

 |
Deprecated parameter

 |

hitRange

 |
This parameter defines the height of the cylinder using to check if the melee attack can hit the target.

 |

knockdownChance

 |
This parameter defined the probability that a successful melee attack knows down the player.

 |

impulse

 |
This parameter defined the amount of the impulse that is applied to the player in case of a successful melee attack.

 |

angleThreshold

 |
This is the threshold between the agent direction and the direction between the agent and the target to allow a melee attack to be attempted.

 |

##
KeepTargetAtADistance

##
Description

The
**
KeepTargetAtADistance
**
 keeps the live target at a distance by physically pushing the target away if it is within the deined minimum distance.

##
Parameters

Parameter name

 |
Parameter description

 |

distance

 |
The minimum distance allowed between the player and the agent.

 |

impulsePower

 |
The power of the impulse used to keep the player at least at the minimum distance.

 |

##
Success/Failure

The node never
*
SUCCEEDS
*
 or
*
FAILS
*
, once executed is always running until is out of the scope of the executed nodes.

##
Usage example

```

`
<KeepTargetAtADistance distance="1.8" impulsePower="1.5" />

`

```

##
Additional information/topics

*
This is useful when there's some sort of action close to the player for instance and you want to avoid clipping through the camera.
*
*
Prefer this instead of increasing the capsule size since that will affect how the character can fit through tight passages.
*
*
This node is mostly used in parallel with some other actions that needs to be performed while the player cannot come too close to the agent (Imagine playing a specific animation on the spot that can move the agent without moving the locator causing camera clipping)
*

##
SuppressHitReactions

##
Description

The node
**
SuppressHitReactions
**
 enables/disables the hit reaction system for the agent during its execution.

##
Parameters

The
**
SuppressHitReactions
**
 node doesn't support any parameters.

##
Success/Failure

The node
*
SUCCEEDS
*
 if its child
*
SUCCEEDS
*
.

 The node
*
FAILS
*
 if its child
*
FAILS
*
.

##
Usage example

```

`
<SuppressHitReactions>
 <SomeChildNode />
</SuppressHitReactions>

`

```

##
Additional information/topics

*
To have more information about the Hit/Reaction System you can search in Confluence for more details.
*

##
InflateAgentCollisionRadiusUsingPhysicsTrick

##
Description

The
**
InflateAgentCollisionRadiusUsingPhysicsTrick
**
 node utilizes a trick in the physics system to inflate the capsule of the agent such that it has one radius for collisions with the player, and one radius for collisions with the world.

##
Parameters

Parameter name

 |
Parameter description

 |

radiusForAgentVsPlayer

 |
The radius we want to use to calculate the collision between the agent and the player.

 |

radiusForAgentVsWorld

 |
The radius we want to use to calculate the collision between the agent and the world.

 |

##
Success/Failure

The node never
*
SUCCEEDS
*
 or
*
FAILS
*
 but always run.

##
Usage example

```

`
<InflateAgentCollisionRadiusUsingPhysicsTrick radiusForAgentVsPlayer="1.0" radiusForAgentVsWorld="0.5" />

`

```

##
Additional information/topics

*
The trick is entirely isolated within this node.
*
_ Warning! This node does not properly clean up after itself, so the capsule will remain inflated after it has been used._

*
STEP 1
*
*
The idea of the trick is to set the player dimensions up with the agent-vs-player collision radius. Let it simmer for a while; the physics system is multi-threaded so we have to wait until the player dimensions have been committed.
*
*
STEP 2
*
*
Every now and then we inspect the player dimensions to see if our agent-vs-player collision radius has been committed successfully. It could be that the agent was in a tight spot and couldn't inflate and will therefore sometimes end up unchanged.
*
*
STEP 3
*
_Once the agent-vs-player collision radius has been committed successfully we then go into the geometry and set the capsule's radius in place, using the agent-vs-world radius. This will not update the player dimensions - which is used for collision between living entities.

##
HoldFormation

##
Description

Deprecated: The
**
HoldFormation
**
 node creates the specified formation for the specific agent. The agent becomes the leader of the formation.

##
Parameters

Parameter name

 |
Parameter description

 |

name

 |
The name of the formation.

 |

##
Success/Failure

The node never
*
SUCCEEDS
*
.

 The node
*
FAILS
*
 if the child
*
FAILS
*
 or if the specified formation couldn't be created.

##
Usage example

```

`
<HoldFormation name="FormationName">
 <SomeChildNode />
</HoldFormation>

`

```

##
JoinFormation

##
Description

Deprecated: The
**
JoinFormation
**
 node tries to join the formation that one of the squad members holds.

##
Parameters

Parameter name

 |
Parameter description

 |

name

 |
The name of the formation.

 |

##
Success/Failure

The node never
*
SUCCEEDS
*
.

 The node
*
FAILS
*
 if there is no formation to join in a squad.

##
Usage example

```

`
<JoinFormation />

`

```

##
ScorcherDeploy

##
Description

A 'fancy' decorator node that the Scorcher uses to have him deploy and undeploy as part of his shooting phase.

 The main reason for creating a special node for it was to be able to hide common functionality.

 The node does still rely on some external Lua scripts and various signals to work properly though; but this way we don't have to explicitly expose more functionality from the AI libraries.

The node encapsulates the following child nodes:
**
RunWhileDeploying
**
 and
**
RunWhileDeployed
**
.

##
RunWhileDeploying

##
Description

This node must contain exactly one child node and runs while the Scorcher is in the processes of deploying himself, getting ready for an attack.

 It can be used, for example, to control aiming before actually shooting.

##
Parameters

The
**
RunWhileDeploying
**
 node doesn't support any parameters.

##
Success/Failure

The node
*
SUCCEEDS
*
 if the child node
*
SUCCEEDS
*
.

 The node
*
FAILS
*
 if the child node
*
FAILS
*
.

##
Additional information/topics

The node will receive ticks until:

-
The following signals have been received:

-
The ScorcherFriendlyFireWarningModule sends the following signal to the entity: "OnScorchAreaClear" or OnScorchAreaNotClearTimeOut".

-
The "ScorcherDeployed" signal has been received from Mannequin animation sequence (also see below).

-
Or an internal time-out.
After that, the node will be forcefully stopped if it were still running. The node is also allowed to
*
SUCCEED
*
 prematurely.

##
RunWhileDeployed

##
Description

This node must contain exactly one child node that controls the actual aiming and firing.

##
Parameters

The RunWhileDeploying node doesn't support any parameters.

##
Success/Failure

The node
*
SUCCEEDS
*
 if the child node
*
SUCCEEDS
*
. This will make the parent node start the undeploying sequence.

 The node
*
FAILS
*
 if the child node
*
FAILS
*
.

##
Additional information/topics

The duration and actual execution of the attack is controlled via this node.

##
Parameters

Parameter name

 |
Parameter description

 |

maxDeployDuration

 |
How long to allow the "RunWhileDeploying" child node to run in seconds (defaults to: 2.0)

 |

##
Success/Failure

The node
*
SUCCEEDS
*
 if the entire deploy and undeploy sequence was completed.

 The node
*
FAILS
*
 if either the
**
RunWhileDploying
**
 or
**
RunWhileDeployed
**
 nodes
*
FAILED
*
.

##
Usage example

```

`
<ScorcherDeploy maxDeployDuration="1.0">
  <RunWhileDeploying>
    <SomeChildNode>
  </RunWhileDeploying>
  <RunWhileDeployed>
    <SomeOtherChildNode>
  </RunWhileDeployed>
</ScorcherDeploy>

`

```

##
Additional information/topics

Before and after the node is running, the following Lua functions are called on the agent: EnterScorchTargetPhase() and LeaveScorchTargetPhase().

When the node starts running, the "ScorcherScorch" tag is requested to Mannequin.

 If the node stops normally, the "ScorcherNormal" tag is requested again.

 If the node is terminated prematurely, then it is up to the Behavior Tree script itself to define a proper exit strategy elsewhere (e.g.: immediately request the "ScorcherTurtle" tag).

Upon requesting the animation tags, the node will wait for the following animation events to be received (this is to make sure the transition blend animations are not interrupted):

-
"ScorcherDeployed": When the Scorcher is ready to start firing.

-
"ScorcherUndeployed": When the Scorcher is again ready to walk around.
Note: There are safety time-outs in place, in case hit-reactions might have interrupted a blend.

##
Helicopter Nodes

These nodes were created specifically with flying vehicles in mind.

 These nodes can be found in BehaviorTreeNodes_Helicopter.h/.cpp

##
Hover

##
Description

Let a flying agent hover at its current position.

##
Parameters

The
**
Hover
**
 node doesn't support any parameters.

##
Success/Failure

The node never finishes by itself and will continue to hover the agent until it is forced to terminate.

##
Usage example

```

`
<Hover />

`

```

##
FlyShoot

##
Description

Let a flying agent shoot at its attention target, when possible from its current position.

##
Parameters

Parameter name

 |
Parameter description

 |

useSecondaryWeapon

 |
**
1
**
 if the secondary weapon system should be used (these are often rocket launchers);
**
0
**
 if not (defaults to:
**
0
**
).

 |

##
Success/Failure

The node never finishes by itself and the agent will continue shoot until it is forced to terminate.

##
Usage example

```

`
<FlyShoot useSecondaryWeapon="1" />

`

```

##
Additional information/topics

If the secondary weapon system is used, then the node will only open fire if the weapons are deemed to be able to hit close enough to the target.

 Otherwise normal firing rules will be applied.

##
WaitAlignedWithAttentionTarget

##
Description

Wait until the agent is facing its attention target.

##
Parameters

Parameter name

 |
Parameter description

 |

toleranceDegrees

 |
The maximum allowed angle between the attention target and the forward direction of the agent, in the range of 0.0 to 180.0 degrees (defaults to:
**
20.0
**
).

 |

##
Success/Failure

The node
*
SUCCEEDS
*
 if the angle between the agent's forward direction and its attention target is small enough.

 The node
*
FAILS
*
 if the agent has no attention target.

##
Usage example

```

`
<WaitAlignedWithAttentionTarget toleranceDegrees="40" />

`

```

##
Fly

##
Description

Let an agent fly around by following a path.

##
Parameters

Parameter name

 |
Parameter description

 |

desiredSpeed

 |
The desired speed to move along the path in meters / second (defaults to:
**
15.0
**
).

 |

pathRadius

 |
The radius of the path in meters. The agent will try to stay within this distance from the line segments of the path (defaults to:
**
1.0
**
).

 |

lookAheadDistance

 |
How far long the path, in meters, to 'look ahead' for generating 'attractor points' to fly to (defaults to:
**
3.0
**
 ).

 |

decelerateDistance

 |
When nearing the end of the path, the agent will start to decelerate at the specified distance in meters (defaults to:
**
10.0
**
).

 |

maxStartDistanceAlongNonLoopingPath

 |
When linking up with a non-looping path, this is the maximum distance in meters, that the node is allowed to 'scan ahead' to find the closest point to the path where to start at. This can be useful, for example, to prevent the agent from 'snapping' to the path at a position that is seemingly closer but is actually behind a wall after a U-turn (defaults to:
**
30.0
**
).

 |

loopAlongPath

 |
**
1
**
 if the agent should follow the path in an endless loop;
**
0
**
 if not (defaults to:
**
0
**
).

 |

startPathFromClosestLocation

 |
**
1
**
 if the agent should start following the path at its closest position;
**
0
**
 if it should start following it from the very first path way-point (defaults to:
**
0
**
).

 |

pathEndDistance

 |
The distance towards the end of the path at which the node should start sending some arrival notification events, also see below (defaults to:
**
1.0
**
).

 |

goToRefPoint

 |
**
1
**
 if the current reference point should be appended to the end of the path;
**
0
**
 if not (defaults to:
**
0
**
).

 |

##
Success/Failure

The node
*
SUCCEEDS
*
 if the agent arrived at the end of the path.

 The node
*
FAILS
*
 if no valid path was assigned to the agent.

##
Usage example

```

`
<Fly lookaheadDistance="25.0" pathRadius="10.0" decelerateDistance="20.0" pathEndDistance="1" desiredSpeed="15" maxStartDistanceAlongNonLoopingPath="30" loopAlongPath="0" goToRefPoint="1" startPathFromClosestLocation="1" />

`

```

##
Additional information/topics

-
Paths should be assigned to the agent via FlowGraph.

-
The following properties in the agent's Lua script table can override the default XML tags. This will allow for changes to be made at run-time through (FlowGraph) scripting:

When

 |
Lua variable

 |
Overriden XML tag

 |

Node activation

 |
Helicopter_Loop

 |
loopAlongPath

 |

Node activation

 |
Helicopter_StartFromClosestLocation

 |
startPathFromClosestLocation

 |

Each node tick

 |
Helicopter_Speed

 |
desiredSpeed

 |

-
Upon arrival, the following events will be emitted:

-
ArrivedCloseToPathEnd

-
ArrivedAtPathEnd

##
FlyForceAttentionTarget

##
Description

Keep forcing an attention target onto a flying vehicle.

##
Parameters

The
**
FlyForceAttentionTarget
**
 node doesn't support any parameters.

##
Success/Failure

The node never finishes by itself and keeps forcing the attention target onto the agent.

##
Usage example

```

`
<FlyForceAttentionTarget />

`

```

##
Additional information/topics

-
The attention target that should be enforced, is acquired during each tick of the node from the
*
Helicopter_ForcedTargetId
*
 Lua script variable.

-
When the node is deactivated again, the "ForceAttentionTargetFinished" event is emitted.

##
FlyAimAtCombatTarget

##
Description

Aim a flying agent at its target, taking into account special aiming adjustments for weapons.

##
Parameters

The
**
FlyAimAtCombatTarget
**
 node doesn't support any parameters.

##
Success/Failure

The node never finishes by itself and keeps forcing agent to rotate its body towards its attention target.

##
Usage example

```

`
<FlyAimAtCombatTarget />

`

```

##
HeavyShootMortar

##
Description

This node is resposible to control the shooting of the Heavy Mortar. It tries to simplify and to centralize the check of pre-condition and the initialization of the weapon plus the re-selection of the primary weapon.

##
Parameters

Parameter name

 |
Parameter description

 |

to

 |
(Optional) Defines the target of the shooting. Possible values:
**
Target
**
 or
**
RefPoint
**
. Default is
**
Target
**

 |

firemode

 |
(Optional) The Heavy X-Pak (or Mortar) has two different firemodes. Possible values:
**
Charge
**
 or
**
BurstMortar
**
. Default is
**
Charge
**

 |

timeout

 |
(Optional) Defines the maximum time the node can try to perform the shooting. Default value is
**
5.0 seconds
**
.

 |

aimingTimeBeforeShooting

 |
(Optional) Defines the time in which the Heavy will aim before starting the shooting. Default is
**
1.0 seconds
**
. This amount of time must be bigger than the global timeout.

 |

minAllowedDistanceFromTarget

 |
(Optional) Defines the minimum distance from the Target to allow the shooting. Default is
**
10.0 m
**

 |

##
Success/Failure

The node
*
FAILS
*
 if the Heavy is closer to the Target than the minAllowedDistanceFromTarget.

 The node
*
FAILS
*
 if there are obstructions 2 meters in front of the Heavy (A cylinder check is done to avoid that in front of the mortar there is an object the Heavy tries to shoot to.)

 The node _FAILS if the timeout is reached.

 The node
*
SUCCEEDS
*
 when the shooting
*
SUCCEEDS
*
.

##
Usage example

```

`
<HeavyShootMortar to="RefPoint" fireMode="Charge" aimingTimeBeforeShooting="2" timeout="7" />

`

```

##
SquadScope

##
Description

The node
**
SquadScope
**
 tries to enter a squad scope, which is limited by the specified amount of concurrent users. If the node succeeds to do that, then the child node is executed.

##
Parameters

Parameter name

 |
Parameter description

 |

name

 |
The name of the squad scope to enter.

 |

allowedConcurrentUsers

 |
(Optional) Number of the allowed concurrent users in the specified scope. Default
**
1
**
.

 |

##
Success/Failure

The node
*
SUCCEEDS
*
 when the child
*
SUCCEEDS
*
.

 The node
*
FAILS
*
 if it can't enter the specified scope or if the child
*
FAILS
*
.

##
Usage example

```

`
<SquadScope name="ANameForTheScope" allowedConcurrentUsers="5">
 <SomeChildNode />
</SquadScope>

`

```

##
Additional information/topics

Extra information about the squads will be available on Confluence. The
**
Dynamic Squad System
**
 uses the
**
Cluster Detector
**
 contained into the
**
AI System
**
.

##
SendSquadEvent

##
Description

The
**
SendSquadEvent
**
 node is responsible to send an event only to the squad members.

##
Parameters

Parameter name

 |
Parameter description

 |

name

 |
Name of the event to be sent.

 |

##
Success/Failure

The node
*
SUCCEEDS
*
 after having sent the event and
**
never
**
 _FAILS.

##
Usage example

```

`
<SendSquadEvent name="ANameForTheEvent" />

`

```

##
Additional information/topics

Extra information about the squads will be available on Confluence. The
**
Dynamic Squad System
**
 uses the
**
Cluster Detector
**
 contained into the
**
AI System
**
.

##
IfSquadCount

##
Description

The node
**
IfSquadCount
**
 checks if a squad contains a specific amount of members and if so executes its child.

##
Parameters

Parameter name

 |
Parameter description

 |

isGreaterThan

 |
(Optional) To succeed the node will check if the amount of members is greater than the specified amount.

 |

isLesserThan

 |
(Optional) To succeed the node will check if the amount of members is lesser than the specified amount.

 |

equals

 |
(Optional) To succeed the node will check if the amount of members is equal to the specified amount.

 |

**
Note
**
: one of the parameter
**
isGreaterThan
**
,
**
isLesserThan
**
 or
**
equals
**
 MUST be specified.

##
Success/Failure

The node
*
SUCCEEDS
*
 if the amount of members in the squad satisfies the specified comparison.

 The node
*
FAILS
*
 otherwise.

##
Usage example

```

`
<IfSquadCount isGreaterThan="1">
 <SomeChildNode />
</IfSquadCount>

`

```

##
Additional information/topics

Extra information about the squads will be available on Confluence. The
**
Dynamic Squad System
**
 uses the
**
Cluster Detector
**
 contained into the
**
AI System
**
.

##
Template to define new descriptions

##
Summary

[ModularBehaviorTreeNodeName_Template](Modular%20Behavior%20Tree%20Nodes.md#ModularBehaviorTreeNodes-modularbehaviortreenodename_template)

##
ModularBehaviorTreeNodeName_Template

##
Description

##
Parameters

Parameter name

 |
Parameter description

 |

...

 |
This parameter defines ...

 |

##
Success/Failure

The node
*
SUCCEEDS
*
 if

 The node
*
FAILS
*
 if

##
Additional information/topics

##
Appendix

##
Acronims

**
MBT
**
 = Modular Behavior Tree

**
TPS
**
 = Tactical Point System
