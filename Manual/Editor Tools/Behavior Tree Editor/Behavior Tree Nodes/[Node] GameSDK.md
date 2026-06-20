# [Node] GameSDK

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/36869482
- Page ID: 36869482
- Breadcrumb: Editor Tools > Behavior Tree Editor > Behavior Tree Nodes > [Node] GameSDK
- Parent: Behavior Tree Nodes

## Content

##
GameSDK Nodes

The nodes within this section are included in the GameSDK sample project by default.

Since the following nodes are dependent on GameSDK, it is not recommended that they be used in the development of your game projects. These nodes have been included simply for understanding and testing the Behavior Tree Editor.

##
Adjust Cover Stance

**
Description
**

 |
Changes the stance of an AI agent based on the maximum height of its current cover, such that its cover remains effective.

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
Duration
**

 |
The duration of time, in seconds, for which the node must be executed before stopping and yielding success as its result.

 |
Accepts a floating point value greater than or equal to 0, which represents the
**
Duration
**
 in seconds.

 |

**
Variation
**

 |
Applies a variation to the
**
Duration
**
 value specified above, such that the node is processed for a duration ranging between the values
**
Duration
**
 and
**
Duration+Variation.
**

 |
Accepts a floating point value greater than or equal to 0, which represents the
**
Variation
**
 in seconds.

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
If the AI agent remains in cover the specified
**
Duration
**
, with
**
Variation
**
 included.

 |

**
Failure
**

 |
If the AI agent isn't in cover.

 |

 |

**
Additional Information
**

 |
None.

 |

##
Aim

**
Description
**

 |
Causes an AI agent to aim at a specified Target or Reference Point for a specified duration of time. This direction of aim is cleared once the node completes execution.

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
Angle Threshold
**

 |
Specifies the degree of error that is allowed between the agent's actual direction of aim and the specified Target/Reference Point.

 |
Accepts a floating point value, representing the
**
Angle Threshold
**
 in degrees.

 |

**
Duration Once Within Threshold
**

 |
The time, in seconds, after which the execution of a node must end to yield success as its result

 |
Accepts a floating point value greater than or equal to 0, representing the time in seconds.

 |

**
Aim At Reference Point
**

 |
Causes the AI Agent to aim at a Reference Point when enabled, or aim at a Target when disabled.

 |
Boolean; a ticked checkbox will cause the AI agent to aim at a Reference Point.

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
When the AI agent aims at the specified Target/Reference Point, within the specified
**
A
**
**
ngle Threshold
**
, for the specified
**
Duration.
**

 |

**
Failure
**

 |
Never.

 |

 |

**
Additional Information
**

 |
None.

 |

##
Animate

**
Description
**

 |
Causes an AI agent to play a specific animation.

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
Name
**

 |
Name of the
[Fragment](../../Animation%20Tab/Mannequin%20Editor/Mannequin%20Concepts/Mannequin%20Fragments.md)
 containing that animation which must be played by the agent.

 |
Accepts a string value representing the FragmentID.

The specified FragmentID and the animation it links to however must already exist.

Please refer to the
[Mannequin Fragments](../../Animation%20Tab/Mannequin%20Editor/Mannequin%20Concepts/Mannequin%20Fragments.md)
 page for more information on creating and editing Fragments.

 |

**
Play Mode
**

 |
States if the animation must be played once or loop infinitely.

 |
**
PlayOnce
**

 |
The animation is played once.

 |

**
InfiniteLoop
**

 |
The animation is played in a loop, infinitely.

 |

 |

**
Urgent
**

 |
When enabled, the specified animation is given a higher priority which will cause it to be played before other animations that may be queued.

 |
Boolean; ticking the checkbox marks the animation as urgent.

 |

**
Set Body Direction Towards Attention Target
**

 |
Orients the body of the AI agent to face the attention target.

 |
Boolean; a ticked checkbox will set the agent's body to face the attention target.

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
When the specified animation is played once, if
**
Play Mode
**
 is set to
**
PlayOnce.
**

-
If the specified animation fails to play.
 |

**
Failure
**

 |
Never.

 |

 |

**
Additional Information
**

 |
None.

 |

##
Assert Lua

**
Description
**

 |
Executes a piece of Lua code, returning success/failure as its result depending on whether the code yields true/false.

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
Code
**

 |
The Lua code that must be executed by the node.

 |
Accepts a Lua compatible code that returns a boolean true/false value as its result.

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
If execution of the Lua code returns true as its result.

 |

**
Failure
**

 |
If the code yields failure.

 |

 |

**
Additional Information
**

 |
None.

 |

##
Bubble

**
Description
**

 |
Displays a specified message in a speech bubble above an AI agent.

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
Message
**

 |
The message that must be displayed in the speech bubble.

 |
Accepts a string value.

 |

**
Duration
**

 |
The duration of time, in seconds, for which the message should last.

 |
Accepts a floating point value.

 |

**
Balloon Flag
**

 |
When enabled, the
**
Message
**
 is displayed in a speech bubble over the AI agent.

 |
Boolean; ticking the checkbox will display the
**
Message
**
 in a bubble.

 |

**
Log Flag
**

 |
When enabled, the message will be written to the general purpose log.

 |
Boolean; a ticked checkbox will enable the
**
Log Flag
**
 option.

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
After the message has been sent by the node, displayed in a speech bubble and/or written to log as required, independent of the specified
**
Duration
**
.

 |

**
Failure
**

 |
Never.

 |

 |

**
Additional Information
**

 |
None.

 |

##
Clear Targets

**
Description
**

 |
Clears the AI agent's list of targets.

 |

**
Parameters accepted
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
When the agent's list of targets have been cleared.

 |

**
Failure
**

 |
Never.

 |

 |

**
Additional Information
**

 |
None.

 |

##
Communicate

**
Description
**

 |
Requests the Communication Manager to play a specified Communication (event, sound/voice, or animation) for the AI agent, in response to an in-game event. For example, causing the agent to yell "
*
I'm hurt!"
*
 in response to a player attack.

 |

**
Parameters Accepted
**

 |
**
Parameter Name
**

 |
Description

 |
Value

 |

**
Communication Name
**

 |
Name of the AI Communication that must be played by the node.

 |
Accepts a string value.

The Communication must already exist.

 |

**
Channel Name
**

 |
The name of the Channel on which Communication must be set.

The specified Communication can only be played if the Channel is not 'occupied' or clear.

 |
Accepts a string value.

The name of the Channel must already exist.

 |

**
Timeout
**

 |
Specifies the duration of time, in seconds, after which the node ends its execution.

 |
Accepts a floating point value, representing the duration of time in seconds.

 |

**
Expiry
**

 |
Specifies the duration of time, in seconds, the specified Communication is permitted to wait until the Channel is clear.

 |
Accepts a floating point value, representing the expiry time in seconds.

 |

**
Minimum Silence
**

 |
The number of seconds for which the Channel is silenced after the specified Communication is played.

 |
Accepts a floating point value, representing the
**
Minimum Silence
**
 time in seconds.

 |

**
Wait Until Finished
**

 |
When enabled, the
**
Communicate
**
 node waits for the Communication to end before yielding a successful result.

 |
Boolean; a ticked checkbox enables the
**
Wait Until Finished
**
 option.

 |

**
Ignore Sound
**

 |
When enabled, the sound component of the specified Communication is ignored.

 |
Boolean; a ticked checkbox enables the
**
Ignore Sound
**
 option.

 |

**
Ignore Animation
**

 |
When enabled, the animation component of the Communication is ignored.

 |
Boolean; a ticked checkbox enables the
**
Ignore Animation
**
 option.

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
If the specified Communication ends, and the
**
Wait Until Finished
**
 option is enabled.

-
If the execution time of the node exceeds the specified
**
Timeout
**
.

-
If no
**
Timeout
**
is specified and the
**
Wait Until Finished
**
 option is disabled.
 |

**
Failure
**

 |
Never.

 |

 |

**
Additional Information
**

 |
More information on Communications and Communication Channels can be found in the
[Technical Documentation](../../../../API%20Reference/CRYENGINE%20Engine%20Code/Engine%20Modules/CryAISystem/AI%20Communication.md)
.

 |

##
Execute Lua

**
Description
**

 |
Executes a piece of Lua code.

 |

**
Parameters Accepted
**

 |
**
Parameter Name
**

 |
Description

 |
Value

 |

**
Code
**

 |
The Lua code that must be executed.

 |
Accepts a Lua compatible code.

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
When the Lua code completes execution.

 |

**
Failure
**

 |
Never.

 |

 |

**
Additional Information
**

 |
None.

 |

##
Group Scope

**
Description
**

 |
Creates a fixed-size group and attempts to enter the AI agent into that group.

The node's child is then executed if the agent is successfully incorporated into the group. A
**
Group Scope
**
 node can have only one child.

 |

**
Parameters Accepted
**

 |
**
Parameter Name
**

 |
Description

 |
Value

 |

**
Name
**

 |
Name of the group.

 |
Accepts a string value.

 |

**
Allows Concurrent Users
**

**

**

 |
The maximum number of users the group can have.

 |
Accepts an integer value.

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
If the AI agent was successfully included in the group, and execution of its child node succeeds.

 |

**
Failure
**

 |

-
If the AI agent cannot be included in the group.

-
If the
**
Group Scope
**
's child node fails.

 |

 |

**
Additional Information
**

 |
None.

 |

##
Look

**
Description
**

 |
Causes the target to look at either an Attention Target, the closest member of its group, or at a Reference Point as specified.

Once the node completes execution, its specified
**
Look At
**
 location is cleared.

 |

**
Parameters Accepted
**

 |
**
Parameter Name
**

 |
Description

 |
Value

 |

**
At
**

 |
Specifies what the target must look at.

 |
**
AttentionTarget
**

 |
The current Attention Target.

 |

**
ClosestGroupMember
**

 |
The closest member of the AI agent's group.

 |

**
ReferencePoint
**

 |
The current Reference position.

 |

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
Never.

 |

**
Failure
**

 |
Never.
 |

 |

**
Additional Information
**

 |
The
**
ReferencePoint
**
 can be set by performing a Tactical Position System query via the
[Query TPS]()
 node, and storing the result in the
**
RefPoint
**
 register.

 |

##
Lua Behavior (DEPRECATED)

**
Description
**

 |
Runs a specified Lua behavior.

 |

**
Parameters Accepted
**

 |
**
Parameter Name
**

 |
Description

 |
Value

 |

**
Name
**

 |
The name of the Lua behavior that must be run.

 |
Accepts a string value that can be compiled in Lua.

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
When the Lua behavior runs successfully.

-
If no Lua behavior of the specified
**
Name
**
 exists.

 |

**
Failure
**

 |
Never.

 |

 |

**
Additional Information
**

 |
None.

 |

##
Lua Gate

**
Description
**

 |
Has only one child, which it executes when "open".

A Lua Gate is "open" when the code snippet associated with it yields True.

 |

**
Parameters Accepted
**

 |
**
Parameter Name
**

 |
Description

 |
Value

 |

**
Code
**

 |
The Lua code that must be executed as a condition check for the gate.

 |
Accepts a Lua compatible code that returns a boolean true/false value.

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
If the gate is "open" and execution of its child succeeds.

 |

**
Failure
**

 |

-
If the gate is not "open".

-
If the gate is "open" and execution of its child node fails.
 |

 |

**
Additional Information
**

 |
None.

 |

##
Move

**
Description
**

 |
Moves the AI agent from its current position to a specified destination.

If this final destination is a target, it is updated as the target moves.

 |

**
Parameters Accepted
**

 |
**
Parameter Name
**

 |
Description

 |
Value

 |

**
Stop Within Distance
**

 |
The minimum distance from the destination after which the AI agent stops moving.

 |
Accepts a floating point value, representing the distance in meters.

 |

**
Stop Within Distance Variation
**

 |
Applies a variation to the
**
Stop Within Distance
**
 parameter, such that the minimum distance at which the AI agent stops moving falls between the values
**
Stop Within Distance Variation
**
and
**
Stop Within Distance
**
 +
**
Stop Within Distance Variation.
**

 |
Accepts a floating point value, representing the variation in meters.

 |

**
Length to Trim from the Path End
**

 |
Specifies a measure by which, the length of the AI agent's path to its destination must be trimmed.

The length of this path can be trimmed from either its start or end.

 |
Accepts a floating point value.

A negative value will trim the path's length from the start, while a positive value will trim it from its end.

 |

**
Speed
**

 |
Sets the speed of the AI agent in traversing the path to its destination.

This maximum speed however may be limited by the agent's current
**
Stance
**
 value.

 |
**
Walk
**

 |

**
Run
**

 |

**
Sprint
**

 |

 |

**
Stance
**

 |
The agent's default body stance.

 |
**
Relaxed
**

 |

**
Alerted
**

 |

**
Stand
**

 |

**
Crouch
**

 |

 |

**
Body Orientation
**

 |
The orientation of the agent's body.

 |
**
FullyTowardsMovingDirection
**

 |

**
FullyTowardsAimOrLook
**

 |

**
HalfwayTowardsAimOrLook
**

 |

 |

**
To
**

 |
The destination of the AI agent.

 |
**
Target
**

 |
The current Attention Target.

 |

**
Cover
**

 |
The current Cover position.

 |

**
RefPoint
**

 |
The current Reference position.

 |

**
LastOp
**

 |
The position of the last successful position-related operation.

 |

**
InitialPosition
**

 |
The initial position of the AI agent.

 |

 |

**
Fire Mode
**

 |
The AI agent's mode of fire as it moves towards its destination.

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
Fire in bursts at living targets only.

 |

**
Continuous
**

 |
Fire continuously at living targets only.

 |

**
Forced
**

 |
Fire continuously at any target.

 |

**
Aim
**

 |
Aim only, at any target.

 |

**
Secondary
**

 |
Fire secondary weapons such as grenades.

 |

**
Secondary Smoke
**

 |
Fire smoke grenades.

 |

**
Melee
**

 |
Melee attacks.

 |

**
Kill
**

 |
Shoot directly at the target without missing.

 |

**
BurstWhileMoving
**

 |
Fire in bursts when moving, even when too far from the target.

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
Fire in bursts in an attempt to draw enemy fire.

 |

**
MeleeForced
**

 |
Melee attacks, regardless of the distance from the target.

 |

**
BurstSnipe
**

 |
Fire in bursts, aiming for a head shot.

 |

**
AimSweep
**

 |
Keep aiming at the target without firing.

 |

**
BurstOnce
**

 |
Fire a single burst.

 |

 |

**
Avoid Dangers
**

 |
When enabled, the agent avoids areas flagged as "dangerous" in its path-finding operation.

 |
Boolean; a ticked checkbox enables this option.

 |

**
Avoid Group Mates
**

 |
Causes the AI agent to avoid other agents in its group when path-finding.

 |
Boolean; a ticked checkbox enables this option.

 |

**
Turn Towards Movement Direction Before Moving
**

 |
Has the agent turn towards its direction of movement before actually moving to its destination.

 |
Boolean; a ticked checkbox enables this option.

 |

**
Strafe
**

 |
Causes the agent to strafe while moving towards its destination.

 |
Boolean; a ticked checkbox enables this option.

 |

**
Glance in Movement Direction
**

 |
Has the agent glance in the direction of its path to the destination.

 |
Boolean; a ticked checkbox enables this option.

 |

**
Consider Actors as Path Obstacles
**

 |
Makes the agent regard other actors as "obstacles", which it then avoids while path-finding to avoid collisions.

 |
Boolean; a ticked checkbox enables this option.

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
When the agent is within the
**
Stop Within Distance
**
, inclusive of the
**
Stop Within Distance Variation
**
.
 |

**
Failure
**

 |
If the specified destination is unreachable by the agent.
 |

 |

**
Additional Information
**

 |
The
**
 Cover
**
 or
**
RefPoint
**
 values can be set by performing a Tactical Position System query via the
[Query TPS]()

node, and storing the result in the
**
Cover
**
 or
**
RefPoint
**
 registers respectively.

 |

##
Pull Down Threat Level

**
Description
**

 |
Minimizes the AI agent's threat level.

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
When the agent's threat level has been minimized.
 |

**
Failure
**

 |
Never.
 |

 |

**
Additional Information
**

 |
None.

 |

##
Query TPS

**
Description
**

 |
Executes a Tactical Point System (TPS) query and stores its result in a specified register.

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
Name
**

 |
Name of the TPS query to be executed.

 |
Accepts a string value.

The TPS query must already exist.

 |

**
Register
**

 |
The name of the register that must store the result of the executed TPS query.

 |
**
Cover
**

 |
The tactical position returned by the TPS query is stored in the
**
Cover
**
 register.

 |

**
RefPoint
**

 |
The resulting tactical position is stored in the
**
RefPoint
**
 register.

 |

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
If the TPS query executes successfully.

 |

**
Failure
**

 |
If the TPS query fails.

 |

 |

**
Additional Information
**

 |
Please refer to the
[Technical Documentation](../../../../API%20Reference/CRYENGINE%20Engine%20Code/Engine%20Modules/CryAISystem/Tactical%20Point%20System.md)
 on the Tactical Point System for more information on TPS queries.

 |

##
Send Transition Signal

**
Description
**

 |
Sends a transition signal/Event destined for a
[State Machine]()
 node on the behavior tree, with special intent of causing a change in its State.

Execution of the tree is put on hold until the signal is received, and execution resumes in the new State.

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
Name
**

 |
Name of the transition signal/Event to be sent by the node.

 |
Accepts a string value.

The Event must be previously defined in the Data Definitions block of the Behavior Tree Editor.

 |

**
Register
**

 |
The filter that must be used by the node when sending the specified signal/Event.
 |
**
Sender
**

 |
The transition signal/Event is sent only to the current agent.

 |

**
Group
**

 |
The signal/Event is sent to the current agent and all the others in its Group.

 |

**
GroupExcludingSender
**

 |
The signal/Event is not sent to the current agent, only to the others in its Group.

 |

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
Never.

 |

**
Failure
**

 |
Never.

 |

 |

**
Additional Information
**

 |
This node has been included for backward compatibility reasons and when possible, the
**
Flow → State Machine → Send Transition Event
**
 node must be used in its place.

This is because the
**
Send Transition Event
**
requires users to pick the transition signal/Event from a dropdown menu, which only contains predefined Events, and is hence less prone to user error.

The
**
Send Transition Signal
**
 node however requires the name of the transition signal/Event to be entered within a text box; if the entered name of the signal/Event is incorrect or doesn't exist, execution of the behavior tree would be permanently halted.

 |

##
Set Alertness

**
Description
**

 |
Sets/updates the the value of the agent's alertness.

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
Value
**

 |
Specifies the degree of the agent's alertness.

 |
Accepts an integer value in the range [0,2].

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
When the alertness of the AI agent has been updated with the specified
**
Value.
**

 |

**
Failure
**

 |
Never.

 |

 |

**
Additional Information
**

 |
None.

 |

##
Shoot

**
Description
**

 |
Causes the AI agent to shoot at an Attention Target, Reference Point or a specific position in the in-game world.

 |

**
Parameters Accepted
**

 |
**
Parameter Name
**

 |
Description

 |
Value

 |

**
At
**

 |
Specifies if the AI agent must shoot at an Attention Target, Reference Point or Local Space Position.

 |
**
AttentionT
**
**
arget
**

 |
Shoot at the current Attention Target.

 |

**
ReferencePosition
**

 |
Shoot at the current Reference Position.

 |

**
LocalSpacePosition
**

 |
Shoot at a user defined position in the in-game world.

 |

 |

**
Fire Mode
**

 |
Sets the agent's mode of fire during this node's execution.

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
Fire in bursts at living targets only.

 |

**
Continuous
**

 |
Fire continuously at living targets only.

 |

**
Forced
**

 |
Fire continuously at any target.

 |

**
Aim
**

 |
Aim only, at any target.

 |

**
Secondary
**

 |
Fire secondary weapons such as grenades.

 |

**
Secondary Smoke
**

 |
Fire smoke grenades.

 |

**
Melee
**

 |
Melee attacks.

 |

**
Kill
**

 |
Shoot directly at the target without missing.

 |

**
BurstWhileMoving
**

 |
Fire in bursts when moving, even when too far from the target.

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
Fire in bursts in an attempt to draw enemy fire.

 |

**
MeleeForced
**

 |
Melee attacks, regardless of the distance from the target.

 |

**
BurstSnipe
**

 |
Fire in bursts, aiming for a head shot.

 |

**
AimSweep
**

 |
Keep aiming at the target without firing.

 |

**
BurstOnce
**

 |
Fire a single burst.

 |

 |

**
Stance
**

 |
Defines the agent's default stance.

 |
**
Stand
**

 |

**
Crouch
**

 |

**
Relaxed
**

 |

**
Alerted
**

 |

 |

**
Stance to Use If Slope Is Too Steep
**

 |
Defines the stance the AI agent must adopt if the terrain is too steep.

 |
**
Stand
**

 |

**
Crouch
**

 |

**
Relaxed
**

 |

**
Alerted
**

 |

 |

**
Allowed Slope Normal Deviation from up in Degrees
**

 |
If the actual steepness of the terrain is less than this value, the AI agent will adopt the default
**
Stance
**
.

If the terrain is steeper than this value however, the agent will adopt the stance specified by the
**
Stance to Use If Slope Is Too Steep
**
 parameter.

 |
Accepts a floating point value, representing the angle of deviation in degrees.
 |

**
Duration
**

 |
Specifies the duration of time, in seconds, for which the node is executed.

 |
Accepts a floating point value representing the duration of time in seconds.

 |

**
Aim Obstructed Timeout
**

 |
The maximum duration of time for which an agent's aim may be obstructed, before execution of the node ends with a failure.

 |
Accepts a floating point value, such that
**
-1
**
 will cause the node to execute infinitely.
 |

**
Position
**

**

**

 |
Defines the coordinates of the in-game world position the agent must shoot at.

This option is only available when the
**
At
**
 field has been set to
**
LocalSpacePosition
**
.

 |
Accepts a three dimensional vector, denoting the x, y and z values of the desired position.

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
When the agent shoots for the specified
**
Duration
**
.

 |

**
Failure
**

 |
If the agent's aim has been obstructed beyond the specified
**
Aim Obstructed Timeout
**
.

 |

 |

**
Additional Information
**

 |
None.

 |

##
Shoot From Cover

**
Description
**

 |
Causes the agent to shoot from cover for a specific duration of time.

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
Duration
**

 |
Specifies the duration of time, in seconds, for which the agent shoots from cover, before the node ends execution.

 |
Accepts a floating point value, representing the duration of time in seconds.

 |

**
Aim Obstructed Timeout
**

 |
The maximum duration of time for which an agent's aim may be obstructed, before execution of the node ends with a failure.

 |
Accepts a floating point value, such that
**
-1
**
 will cause the node to execute infinitely.

 |

**
Fire Mode
**

 |
Sets the agent's mode of fire during the execution of this node.

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
Fire in bursts at living targets only.

 |

**
Continuous
**

 |
Fire continuously at living targets only.

 |

**
Forced
**

 |
Fire continuously at any target.

 |

**
Aim
**

 |
Aim only, at any target.

 |

**
Secondary
**

 |
Fire secondary weapons such as grenades.

 |

**
Secondary Smoke
**

 |
Fire smoke grenades.

 |

**
Melee
**

 |
Melee attacks.

 |

**
Kill
**

 |
Shoot directly at the target without missing.

 |

**
BurstWhileMoving
**

 |
Fire in bursts when moving, even when too far from the target.

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
Fire in bursts in an attempt to draw enemy fire.

 |

**
MeleeForced
**

 |
Melee attacks, regardless of the distance from the target.

 |

**
BurstSnipe
**

 |
Fire in bursts, aiming for a head shot.

 |

**
AimSweep
**

 |
Keep aiming at the target without firing.

 |

**
BurstOnce
**

 |
Fire a single burst.

 |

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
When the agent shoots from cover for the specified
**
Duration
**
.

 |

**
Failure
**

 |

-
When the agent is no longer in cover.

-
When the agent is in cover, but its
aim has been obstructed beyond the specified
**
Aim Obstructed Timeout
**
.
 |

 |

**
Additional Information
**

 |
None.

 |

##
Send Signal

**
Description
**

 |
Sends a transition signal/Event,

However unlike the
**
[Send Transition Signal]()

**
node,
the execution of behavior tree is not stopped until this signal/Event is handled somewhere else.

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
Name
**

 |
Name of the transition signal/Event to be sent by the node.

 |
Accepts a string value.

The signal/Event must be previously defined in the Data Definitions block.

 |

**
Filter
**

 |
Specifies the filter that must be used when sending the transition signal.

 |
**
Sender
**

 |
The transition signal/Event is sent only to the current agent.

 |

**
Group
**

 |
The signal/Event is sent to the current agent and all the others in its Group.

 |

**
GroupExcludingSender
**

 |
The signal/Event is not sent to the current agent, but only to the others in its Group.

 |

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
When the transition signal/Event is sent.

 |

**
Failure
**

 |
Never.

 |

 |

**
Additional Information
**

 |
This node has been included for backward compatibility reasons and when possible, the
**
**
Core → Send Event
**

**
node must be used in its place.

This is because the
**
Send Event
**
requires users to pick the transition signal/Event from a dropdown menu, which only contains predefined Events, and is hence less prone to user error.

The
**
Send Signal
**
 node however, requires the name of the transition signal/Event to be entered within a text box, which could create errors if the entered name of the signal/Event is incorrect or doesn't exist.

 |

##
Stance

**
Description
**

 |
Sets the stance of the AI agent.

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
Stance
**

 |
The default stance to be used by the agent.

 |
**
Stand
**

 |

**
Crouch
**

 |

**
Relaxed
**

 |

**
Alerted
**

**

**
 |

 |

**
Stance to Use If Slope Is Too Steep
**

 |
Specifies the stance to be used by the agent if the slope of the terrain is too steep.

 |
**
Stand
**

 |

**
Crouch
**

 |

**
Relaxed
**

 |

**
Alerted
**

**

**
 |

 |

**
Allows Slope Normal Deviation from up in Degrees
**

 |
If the actual steepness of the terrain is less than this value, the AI agent will adopt the default
**
Stance
**
.

If the terrain is steeper than this value however, the agent will adopt the stance specified by the
**
Stance to Use If Slope Is Too Steep
**
 parameter.

 |
Accepts a floating point value, representing the deviation in degrees.

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
Immediately after the agent changes its stance as per the parameters specified.

 |

**
Failure
**

 |
Never.

 |

 |

**
Additional Information
**

 |
None.

 |

##
Stop Movement

**
Description
**

 |
Stops movement of the agent.

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
Wait until Stopped
**

 |
When enabled, execution of the node completes after the agent's movement animation ends.

 |
Boolean; a ticked checkbox enables this option.

 |

**
Wait until Idle Animation
**

 |
When enabled, execution of the the node completes after the agent's idle animation begins.

Idle animations are contained within the
*
Motion_Idle
*

[FragmentID](../../Animation%20Tab/Mannequin%20Editor/Mannequin%20Concepts/Mannequin%20Fragments.md)
.

 |
Boolean; a ticked checkbox enables this option.
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
When the agent's movement animation stops, if
**
Wait until Stopped
**
 has been enabled.

-
When the agent's idle animation is running, if
**
Wait until Idle Animation
**
 has been enabled.
 |

**
Failure
**

 |
Never.

 |

 |

**
Additional Information
**

 |
Execution of this node might not always stop the agent's physical movement immediately.

The Movement System often relies on the influence of animation and physics, for example, which may result in the agent's movement being stopped over a period of time rather than immediately.

Please refer to the
[Technical Documentation](../../../../API%20Reference/CRYENGINE%20Engine%20Code/Engine%20Modules/CryAISystem/Movement%20System.md)
 for more information on the Movement System.

 |

[GameSDK Nodes](#gamesdk-nodes)
[Adjust Cover Stance](#adjust-cover-stance)
[Aim](#aim)
[Animate](#animate)
[Assert Lua](#assert-lua)
[Bubble](#bubble)
[Clear Targets](#clear-targets)
[Communicate](#communicate)
[Execute Lua](#execute-lua)
[Group Scope](#group-scope)
[Look](#look)
[Lua Behavior (DEPRECATED)](#lua-behavior-deprecated)
[Lua Gate](#lua-gate)
[Move](#move)
[Pull Down Threat Level](#pull-down-threat-level)
[Query TPS](#query-tps)
[Send Transition Signal](#send-transition-signal)
[Set Alertness](#set-alertness)
[Shoot](#shoot)
[Shoot From Cover](#shoot-from-cover)
[Send Signal](#send-signal)
[Stance](#stance)
[Stop Movement](#stop-movement)
