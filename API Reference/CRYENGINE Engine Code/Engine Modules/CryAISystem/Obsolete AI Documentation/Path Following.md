# Path Following

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/23306473
- Page ID: 23306473
- Breadcrumb: CRYENGINE Engine Code > Engine Modules > CryAISystem > Obsolete AI Documentation > Path Following
- Parent: Obsolete AI Documentation

## Content

##
Overview

Here are a few high-level insights on how path following is done in CryENGINE. For simplicity, let's consider the path following of Racing HMMWV's, since it is not very sophisticated.

In fact, it is the classical path following, straight from the classical AI texts, which works as follows:

-
Get the closest (to the AI actor) point on path.

-
Get the path parameter of this point. (Paths usually have some kind of parametrization,
*
t
*
 -> (
*
x
*
,
*
y
*
,
*
z
*
).)

-
Add a certain value (usually called
**
lookahead
**
) to this parameter

-
Get the path point that corresponds to this new parameter. This is called look-ahead position.

-
Use this point as the navigation target.

-
If the vehicle is stuck, beam it straight to the closest point on the path.

##
Goalop "Followpath"

To instruct an AI actor to follow a path, goalop "followpath" is usually used. So, to get a better idea of what is going on under hood, setting a breakpoint at the beginning of
**
COPFollowPath::Execute
**
 is a good idea.

You can then see from the Call Stack window in the Visual Studio that, as part of the AI System update procedure, Update methods of all (active) AIs are called. This in turn calls the Execute methods of currently active goalops that the AI in question is running.

Basically,
**
COPFollowPath::Execute
**
 does the following:

-
Finds a path to the beginning of the path (or the closest point on the path), if requested (using a parameter passed to the "followpath" goalop), using goalop "pathfind".

-
Traces the path, i.e. actually follows it, using goalop "trace".

-
Makes sure the AI agent is not stuck. If it is, is receives signal "OnPathFollowingStuck".
Using goalops "pathfind" and "trace" is common for navigational goalops, including "approach" and "stick".

To get more details about path following, let's examine method
**
COPTrace::Execute
**
.

##
COPTrace::Execute and COPTrace::ExecuteTrace

**
COPTrace::Execute
**
 does little more than just calling
**
COPTrace::ExecuteTrace
**
 and politely cleaning up things. It also sends signal "OnEndWithinLookAheadDistance" to the AI that is following the path, when its lookahead position hits the end of the path. This allows our racing HMMWVs to start looking for a new path to follow, while still moving along this path. We also used the following in the Lua script to keep moving. Normally, AIs stop when path following completes):

```

`
AI.SetContinuousMotion(vehicle.id, true);
`

```

**
COPTrace::ExecuteTrace
**
 does a lot of work, including handling edge cases and smart objects, but the central point of it is here:

```

`
IPathFollower* pPathFollower = gAIEnv.CVars.PredictivePathFollowing ? pPipeUser->GetPathFollower() : 0;
bTraceFinished = pPathFollower ? ExecutePathFollower(pPipeUser, bFullUpdate, pPathFollower) : Execute2D(pPipeUser, bFullUpdate);
`

```

If the AI actor (CPipeUser, at least) has its path follower, it is used. Otherwise,
**
COPTrace::Execute2D
**
 is used as a fallback. Let's look at it more closely.

##
COPTrace::Execute2D

Basically,
**
COPTrace::Execute2D
**
 does the following:

-
Gets the lookahead (future) path position and the path direction at this position.

-
Executes a maneuver, if necessary. For example, it makes cars go backwards to make a U-turn.

-
Considers a number of reasons to slow down, including:

-
The angle between current and desired (aforementioned path direction) directions.

-
The curvature of the path.

-
Approaching the end of the path.

-
Approaching the top of a hill.
It then sets members fDesiredSpeed and vMoveDir of the AI agent's SOBJECTSTATE structure, which are brought to the game code later. For an example of how these data can be used for actual steering, you could take a look at
**
CVehicleMovementArcadeWheeled::ProcessAI
**
.

Note that
**
COPTrace::Execute2D
**
 is not the only method that sets vMoveDir. For example, obstacle avoidance code can overwrite it.
