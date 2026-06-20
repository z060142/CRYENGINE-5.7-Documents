# Goalop Reference

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/23306485
- Page ID: 23306485
- Breadcrumb: CRYENGINE Engine Code > Engine Modules > CryAISystem > Obsolete AI Documentation > Obsolete AI Scripting Documentation > Goal Pipes > Goalop Reference
- Parent: Goal Pipes

## Content

### Introduction

A *goalpipe* is a sequence of tasks/commands (* goalops*) to be performed by an AI. In effect, it is a simple virtual machine which allows you to put together building blocks of actions and execute them over a number of frames.

Note that although important goalops can represent a goal (such as sticking to a target), they are not goals in any sense of planning or logic. However, where you create a goalop that causes AI to perform a clear action, do consider it in terms of a clear goal that it is trying to achieve.

The goalops are (usually) atomic units, written in C++ with a simple interface. Since they can persist over multiple frames they are useful for real actions that take finite time to complete (such as running to a point), and/or to allow timesliced or asynchronous processing to be exploited.

Goalops operate on various data in the puppets, but two of the most important are:

- LastOp – any AI object returned by the previous goalop

- AttentionTarget ("atttarget") – the focus of attention of the puppet

Goalpipes can be created dynamically, but are usually created once while initializing. They can be executed once, or allowed to loop. During goalpipe creation, when goals are added to a pipe using AI.PushGoal, they can be made *blocking* or * non-blocking*. If a goal is blocking, it is executed until completion every frame, without the goal pipe executing subsequent goals. Non-blocking goal does not prevent the next goal of the goalpipe from executing, possibly resulting in concurrently running goals. Property "blocking" is set by the 2nd parameter to AI.PushGoal, for example:

```
AI.CreateGoalPipe("backoff_from");
AI.PushGoal("backoff_from", "run", 0, 1);
AI.PushGoal("backoff_from", "bodypos", 0, BODYPOS_STAND);
AI.PushGoal("backoff_from", "backoff", 1, 5, 2);
```

Here, goalops "run" and "bodypos" are added to the goalpipe "backoff_from" as non-blocking, whereas goalop "backoff" is added as blocking.

AI.SelectPipe is preferred, as it clears any existing goalpipes, but implies goalpipe may loop. In many cases, the pipe will anyway be allowed to run until it causes a signal, so this works fine in practice.

AI.InsertPipe allows recursive nesting of pipes. This can be useful but is hard to work with. Best used upon an empty goalpipe to execute something just once, or in some cases to insert a short action in an existing sequence.

- AI.SelectPipe

- If selecting a different goalpipe, clear the old one first
- Reselecting the current goalpipe does nothing (it does not reset it)
- Arguments can be given

- AI.InsertSubPipe

- Insert a sub-goalpipe within that currently executing
- Interacts with + syntax to avoid inserting within blocks of ops that should be atomic

There is a simple method of branching to labels within a goalpipe, using an implicit goalop "branch". Various test conditions are available. However, this fine a grain of control is rarely needed and most decisions are best made at the FSM level.

### Goalop Reference

Default values for parameters are typed in **bold**. Optional parameters are in * italic*. Goalop parameter "blocking" should either be 0 or 1 in Lua, or * false* or ***true*** (default) in XML.

#### acqtarget

Acquire an AI object as attention target.

**Lua:** AI.PushGoal("acqtarget", blocking, * AI object's name or a* *[SpecialAIobject](Goalop%20Reference.md#GoalopReference-SpecialAIobject)*)

**C++:** class COPAcqTarget

**XML:** <AcqTarget * name="AI object's name or a* *[SpecialAIobject](Goalop%20Reference.md#GoalopReference-SpecialAIobject)"*/>

**Parameter:** AI object's name: named AI object or a [SpecialAIobject](Goalop%20Reference.md#GoalopReference-SpecialAIobject); ** empty string** means "use the LastOp"

*Examples:*

```
AI.PushGoal("acqtarget", 0, "");
--
AI.PushGoal("acqtarget", 0, "refpoint");
```

#### adjustaim

Aiming/hiding around obstacles.

**Lua:** AI.PushGoal("adjustaim", blocking, * aim / hide, use LastOp as backup, allow prone, timeout*)

**C++:** class COPCrysis2AdjustAim

**XML:** <AdjustAim * useLastOpResultAsBackup="****false****/true"* * allowProne="****false****/true"* * timeout="timeout"* * timeoutRandomness="timeout randomness"*/>

**Parameters:** * aim / hide*: **0** to aim (default), 1 to hide * use LastOp as backup*: **0** (don't use) by default * allow prone*: **0** (don't allow) by default * timeout*: **0** (no timeout) by default

*Example:*

```
AI.PushGoal("adjustaim", 0, 0, 1);
```

#### animation

Perform an animation.

**Lua:** AI.PushGoal("animation", blocking, mode, name)

**C++:** class COPAnimation

**XML:** <Animation mode="Action/Signal" name="name"/>

**Parameters:** mode: AIANIM_SIGNAL (to play one-shot animations) or AIANIM_ACTION (to play looping animations) name: name of animation action or signal to set

*Example:*

```
AI.PushGoal("animation", 1, AIANIM_SIGNAL, "salute");
```

#### animtarget

The goalop for using animation targets, e.g. when executing smart objects.

**Lua:** AI.PushGoal("animtarget", blocking, mode, name, start radius, direction tolerance, target radius)

**C++:** class COPAnimTarget

**XML:** <AnimTarget mode="Action/Signal" name="name" startWidth="number" directionTolerance="number" startArcAngle="number" * approachRadius="number (default is* ***0****, i.e. "not used")"*/>

**Parameters:** mode: AIANIM_SIGNAL (to play one-shot animations) or AIANIM_ACTION (to play looping animations) name: name of animation action or signal to set startWidth, directionTolerance, startArcAngle, approachRadius (** 0** by default): please see documentation on navigational smart objects for details.

*Example:*

```
AI.PushGoal("+animtarget", 0, 0, "callReinforcementsWave", 0.5, 5, 0.5);
```

#### approach

Approach to a given distance of a target. Uses goalops Pathfind and Trace. Very common.

**Lua:** AI.PushGoal("approach", blocking, approach distance or time, * flags, end accuracy*)

**C++:** class COPApproach

**XML:** <Approach distance="number" or time="number" * useLastOp="****false****/true"* * lookAtLastOp="****false****/true"* * requestPartialPath="****false****/true"* * stopOnAnimationStart="****false****/true"* * endAccuracy="number"*/>

**Parameters:** approach distance / time: use flag AI_USE_TIME to specify time, rather than distance * flags* (**0** by default): AILASTOPRES_USE, AILASTOPRES_LOOKAT, AI_USE_TIME, AI_REQUEST_PARTIAL_PATH, AI_STOP_ON_ANIMATION_START * end accuracy*: (**0** by default) allowable movement end accuracy

*Examples:*

```
AI.PushGoal("approach", 0, entity.AI.myDistance, AILASTOPRES_USE);
--
AI.PushGoal("approach", 1, 3, AILASTOPRES_USE, 1);
--
AI.PushGoal("approach", 1, 0.4, AILASTOPRES_USE + AI_REQUEST_PARTIAL_PATH);
```

#### backoff

Deprecated. You are encouraged to use goalop "tacticalpos" instead.

Make a small evasive movement – back, left, right, etc. Make sure this one is reset, don't allow it to loop.

**Lua:** AI.PushGoal("backoff", blocking, distance, * max duration, options*)

**C++:** class COPBackoff

**XML:** <BackOff distance="number" * maxDuration="number"* * minDistance="number"*

*moveForward="****false****/true"* * moveBackward="****false****/true"* * moveLeft="****false****/true"* * moveRight="****false****/true"* * moveBackLeft="****false****/true"* * moveBackRight="****false****/true"* * moveTowardsGroup="****false****/true"* * useLastOp="****false****/true"* * lookForward="****false****/true"* * backOffFromTarget="****false****/true"* * randomOrder="****false****/true"* * checkSlopeDistance="****false****/true"*/>

**Parameters:** * options* (can be combined): AILASTOPRES_USE, AI_MOVE_FORWARD, AI_MOVE_BACKWARD, AI_MOVE_LEFT, AI_MOVE_RIGHT, AI_MOVE_BACKLEFT, AI_MOVE_BACKRIGHT, AI_BACKOFF_FROM_TARGET, AI_MOVE_TOWARDS_GROUP, AI_CHECK_SLOPE_DISTANCE, AI_RANDOM_ORDER

*Examples:*

```
AI.PushGoal("backoff", 1, 2, 0, AI_MOVE_RIGHT);
--
AI.PushGoal("backoff", 1, 2, 1, AI_BACKOFF_FROM_TARGET);
--
AI.PushGoal("backoff", 1, 16, 10, AI_MOVE_BACKWARD + AI_MOVE_BACKRIGHT + AI_MOVE_BACKLEFT + AI_MOVE_LEFT + AI_MOVE_RIGHT);
--
AI.PushGoal("backoff", 1, 6, 4, AI_BACKOFF_FROM_TARGET + AI_MOVE_LEFT + AI_MOVE_RIGHT + AI_MOVE_BACKWARD + AI_MOVE_BACKLEFT + AI_MOVE_BACKRIGHT + AI_RANDOM_ORDER);
--
AI.PushGoal("backoff", 1, 14, 8, AILASTOPRES_USE + AI_MOVE_BACKWARD + AI_MOVE_BACKLEFT + AI_MOVE_BACKRIGHT);
```

#### bodypos

(Alias: stance) Set stance – crouch, stand, stealth, etc. It affects movement speeds, animations, etc.

**Lua:** AI.PushGoal("bodypos", blocking, body state, * delayed*)

**C++:** class COPBodyCmd

**XML:** <BodyPos id="see the table below" * delayed="****false****/true"*/>

**Parameters:** body state:

Lua | XML
--- | ---
STANCE_NULL | Null
STANCE_STAND | Stand
STANCE_CROUCH | Crouch
STANCE_PRONE | Prone
STANCE_RELAXED | Relaxed
STANCE_STEALTH | Stealth
STANCE_LOW_COVER | LowCover
STANCE_ALERTED | Alerted
STANCE_HIGH_COVER | HighCover
STANCE_SWIM | Swim
STANCE_ZEROG | ZeroG

*delayed*: **0** (false) by default

*Examples:*

```
AI.PushGoal("bodypos", 1, BODYPOS_STEALTH);
--
AI.PushGoal("bodypos", 1, BODYPOS_STAND, 1);
```

#### charge

Deprecated.

#### clear

Deprecated.

#### communicate

Trigger a communication (sound/voice and/or animation) event. See [AI Communication](../../../AI%20Communication.md) for more details.

**Lua:** AI.PushGoal("communicate", blocking, communication name, channel name, * expirity, minSilence, timeout, ignoreSound, ignoreAnim*)

**C++:** class COPCommunication

**XML:** <Communicate name="communication name" channel="channel name" * timeout="number (****8*** * by default)" expirity="number (****0*** * by default)" minSilence="number (****-1*** * be default) ignoreSound="****false****/true" ignoreAnim="****false****/true" ordered="****false****/true"*/>

**Parameters:** communication name: the name of the actual communication. Possible communications are defined by the XML file that the property * CommConfig* of this AI's Lua script refers to. channel name: the name of the communication channel this AI is using. The channel should be defined in any XML file which resides in * Game/Scripts/AI/Communication*. * expirity* (expiry): (**0** by default) maximum allowable delay in triggering this communication (when the communication channel is temporarily occupied). If the communication couldn't be triggered within this time period, it is discarded. * minSilence*: (**-1** by default, which means "use the default value set for the communication channel used") minimum time (in seconds) for which the channel remains occupied after the communication has completed * timeout*: (**8** by default) maximum time this goalop is allowed to execute * ignoreSound*: (**false** by default) disable sound * ignoreAnim*: (**false** by default) disable playing animation * ordered*: (**false** by default) ordered requests get serviced before unordered ones

*Example:*

```
<GoalPipe name="Cover2_Communicate">
<Communicate name="alerted" channel="Search" expirity="0.5"/>
</GoalPipe>
```

#### companionstick

Deprecated.

#### continuous

Deprecated.

#### devalue

Devalue a target (a point) for a short period of time so that it is not selected as an attention target (and/or doesn't participate in some other calculations). If choosing between targets is a problem, you can try this.

**Lua:** AI.PushGoal("devalue", blocking, * also devalue puppets, clear [the list of] "devalued"*)

**C++:** class COPDeValue

**XML:** <Devalue * devaluePuppets="****false****/true" clearDevalued="****false****/true"*/>

**Parameters:** * devalue puppets*: **0** (default) / 1 * clear "devalued"*: **0** (default) / 1

*Example:*

```
AI.CreateGoalPipe("tank_fire_stop");
AI.PushGoal("tank_fire_stop", "firecmd", 0, 0);
AI.PushGoal("tank_fire_stop", "locate", 0, "atttarget");
AI.PushGoal("tank_fire_stop", "lookat", 0, 0, 0, true, 1);
--
AI.PushGoal("tank_fire_stop", "devalue", 1, 0, 1);
```

#### dodge

Deprecated

#### firecmd

Set firing mode: hold fire, single-shot, full-auto, etc. Firing is handled in this simple manner at this level; decisions on individual shots happen in C++.

**Lua:** AI.PushGoal("firecmd", blocking, fire mode, * use LastOp, min timeout, max timeout*)

**C++:** class COPFireCmd

**XML:** <FireCmd mode="see the table below" * useLastOp="****false****/true" timeout="number" or timeoutMin="number" timeoutMax="number"*/>

**Parameters:** * fire mode*:

Lua | XML | Comment
--- | --- | ---
FIREMODE_OFF | Off | Do not fire
FIREMODE_BURST | Burst | Fire in bursts - living targets only
FIREMODE_CONTINUOUS | Continuous | Fire continuously - living targets only
FIREMODE_FORCED | Forced | Fire continuously - allow any target
FIREMODE_AIM | Aim | Aim target only - allow any target
FIREMODE_SECONDARY | Secondary | Fire secondary weapon (grenades,...)
FIREMODE_SECONDARY_SMOKE | SecondarySmoke | Fire smoke grenade
FIREMODE_MELEE | Melee | Melee
FIREMODE_KILL | Kill | No missing, shoot directly at the target, no matter what aggression/attackRange/accuracy is
FIREMODE_BURST_WHILE_MOVING | BurstWhileMoving |
FIREMODE_PANIC_SPREAD | PanicSpread |
FIREMODE_BURST_DRAWFIRE | BurstDrawFire |
FIREMODE_MELEE_FORCED | MeleeForced | Melee, without distance restrictions
FIREMODE_BURST_SNIPE | BurstSnipe |
FIREMODE_AIM_SWEEP | AimSweep |
FIREMODE_BURST_ONCE | BurstOnce |

*use LastOp*: **0** (default) or AILASTOPRES_USE * min timeout*: **-1** (i.e. no timeout) by default * max timeout*: **-1** (i.e. no timeout) by default

*Example:*

```
AI.PushGoal("HeliFireStartRef", "firecmd", 0, FIREMODE_CONTINUOUS, AILASTOPRES_USE);
```

#### followpath

Reach and then follow a designer-created path.

**Lua:** AI.PushGoal("followpath", blocking, pathfind to start, reverse path, start nearest, number of loops, * end accuracy, use point list, avoid dynamic obstacles*)

**C++:** class COPFollowPath

**XML:** <FollowPath loops="number" * pathFindToStart="false/****true****" reversePath="false/****true****" startNearest="false/****true****" usePointList="****false****/true" endAccuracy="number"*/>

**Parameters:** pathfind to start: false (go to the start of the path in a straight line) or true reverse path: false or true (navigate the path from the last point to the first) start nearest: false (start from the * first* point of the path) or true (start from the * nearest* point of the path) * end accuracy*: (**0** by default) allowable movement end accuracy * use point list*: **false** (default) or true * avoid dynamic obstacles*: false or **true** (default)

*Examples:*

```
AI.PushGoal("tankclose_gotopathsub", "followpath", 0, false, bReverse, true, 3, 0, false);
--
AI.PushGoal("heliDamageAction", "followpath", 0, false, false, false, 0, 10, true);
```

#### form

Deprecated.

#### hide

Deprecated.

Find a hidepoint according to given criteria and move there. Core to behaviors.

**Lua:** AI.PushGoal("hide", blocking, search distance, hide method, * exactly, min distance, look at LastOp*)

**C++:** class COPHide

**XML:** <Hide * searchDistance="number (****10*** * by default)"* * evaluationMethod="number (see Lua section)"* * minDistance="number (****0*** * by default)"* * lookAtHide="false/****true****"* * lookAtLastOp="false/****true****"*/>

**Parameters:** search distance: distance within which to search for a hide (hide method: one of the following:

Lua only
---
HM_NEAREST
HM_NEAREST_TO_ME
HM_FARTHEST_FROM_TARGET
HM_NEAREST_TO_TARGET
HM_NEAREST_BACKWARDS
HM_NEAREST_TOWARDS_TARGET
HM_FARTHEST_FROM_GROUP
HM_NEAREST_TO_GROUP
HM_LEFTMOST_FROM_TARGET
HM_RIGHTMOST_FROM_TARGET
HM_RANDOM
HM_FRONTLEFTMOST_FROM_TARGET
HM_FRONTRIGHTMOST_FROM_TARGET
HM_NEAREST_TO_FORMATION
HM_FARTHEST_FROM_FORMATION
HM_NEAREST_TO_LASTOPRESULT
HM_RANDOM_AROUND_LASTOPRESULT
HM_USEREFPOINT
HM_ASKLEADER
HM_ASKLEADER_NOSAME
HM_BEHIND_VEHICLES
HM_NEAREST_PREFER_SIDES
HM_NEAREST_TOWARDS_TARGET_PREFER_SIDES
HM_NEAREST_TOWARDS_TARGET_LEFT_PREFER_SIDES
HM_NEAREST_TOWARDS_TARGET_RIGHT_PREFER_SIDES
HM_NEAREST_TOWARDS_REFPOINT

Possibly combined with:

HM_INCLUDE_SOFTCOVERS
---
HM_IGNORE_ENEMIES
HM_BACK
HM_AROUND_LASTOP
HM_FROM_LASTOP
HM_USE_LASTOP_RADIUS
HM_ON_SIDE

*look at LastOp*: 0 or AILASTOPRES_LOOKAT

*Examples:*

```
AI.PushGoal("hide", 1, 10, HM_NEAREST_TOWARDS_REFPOINT, 0, 3);
--
AI.PushGoal("hide", 1, 30, HM_NEAREST + HM_INCLUDE_SOFTCOVERS);
--
AI.PushGoal("hide", 1, 6, HM_NEAREST_TOWARDS_TARGET_PREFER_SIDES + HM_INCLUDE_SOFTCOVERS, 0, 0);
```

#### ignoreall

Ignore signals. Not recommended, there are usually better ways.

**Lua:** AI.PushGoal("ignoreall", blocking, false/** true**)

**C++:** class COPIgnoreAll

**XML:** <IgnoreAll id="false/** true**"/>

#### locate

Find a special object – e.g. probtarget, atttarget, refpoint – or a named AI object, and set as LastOp, within a given (if given) *range*. Commonly followed by AcqTarget to gain as attention target.

**Lua:** AI.PushGoal("locate", blocking, AI object type name or ID or [SpecialAIobject](Goalop%20Reference.md#GoalopReference-SpecialAIobject), * range*)

**C++:** class COPLocate

**XML:** <Locate name="AI object's name or a [SpecialAIobject](Goalop%20Reference.md#GoalopReference-SpecialAIobject)" or type="AI object's type" * range="number (default is* ***0*** * i.e. "not used")"* * warnIfFailed="false/****true****"*/>

*Example:*

```
AI.PushGoal("look_at_player_5sec", "locate", 0, "player");
AI.PushGoal("look_at_player_5sec", "+lookat", 0, 0, 0, true);
```

#### lookaround

Look around.

**Lua:** AI.PushGoal("lookaround", blocking, look around range, * scan range, interval* * min, interval max, flags*)

**C++:** class COPLookAround

**XML:** <LookAround lookAroundRange="number"

*scanRange="number"* * useLastOp="****false****/true"* * breakOnLiveTarget="****false****/true"* * bodyTurn="false/****true****"* * checkForObstacles="****false****/true"* * interval="number" or intervalMin="number"* * intervalMax="number"*/>

**Parameters:** * scan range*: **-1** (not used) by default * interval min*: **-1** (not used) by default * interval max*: **-1** (not used) by default * flags*: **0** (default), either of the following can be set: AI_BREAK_ON_LIVE_TARGET, AILASTOPRES_USE

*Examples:*

```
AI.PushGoal("lookaround", 1, 90, 3, 3, 5, AI_BREAK_ON_LIVE_TARGET);
--
AI.PushGoal("lookaround", 1, 30, 2.2, 10005, 10010, AI_BREAK_ON_LIVE_TARGET + AILASTOPRES_USE);
```

#### lookat

Look at LastOp or look around a range, rather than default behavior of looking at attention target.

**Lua:** AI.PushGoal("lookat", blocking, start angle, end angle, * use LastOp, flags*)

**C++:** class COPLookAt

**XML:** <LookAt * startAngle="number (default is* ***0****)"* * endAngle="number (default is* ***0****)"* * angleThreshold="number (default is* ***0****)"* * useLastOp="****false****/true"* * bodyTurn="false/****true****"* * continuous="****false****/true"* * yawOnly="****false****/true"* * useBodyDir="****false****/true"*/>

**Parameters:** * use LastOp*: **0** (default) or 1 * flags*: **0** (default), either of the following can be set: AI_LOOKAT_CONTINUOUS, AI_LOOKAT_USE_BODYDIR

*Examples:*

```
AI.PushGoal("tr_lookaround_30seconds", "lookat", 1, -90, 90);
--
-- Look at lastop
AI.PushGoal("gr_lookat_interested", "lookat", 0, 0, 0, 1);
--
-- Reset look at
AI.PushGoal("reset_lookat", "lookat", 1, -500);
```

#### move

Deprecated.

#### movetowards

Deprecated

#### pathfind

Perform pathfinding on a puppet to an objects. Usually employed internally by other goalops, not directly in behavior scripts.

**Lua:** AI.PushGoal("pathfind", blocking, * AI object's name or a* *[SpecialAIobject](Goalop%20Reference.md#GoalopReference-SpecialAIobject)**, end tolerance (****0*** * by default), end distance (****0*** * by default), direction only distance (****0*** * by default), high priority (****false*** * by default)*)

**C++:** class COPPathFind

**XML:** <Pathfind target="target AI object's name or a [SpecialAIobject](Goalop%20Reference.md#GoalopReference-SpecialAIobject)" * endTolerance="number (default is* ***0****)"* * endDistance="number (default is* ***0****)"* * directionOnlyDistance="number (default is* ***0****)"* * highPriority="****false****/true"*/>

**Parameters:** * AI object name*: none by default highPriority: (**false** by default) place the pathfinding request at the beginning of the request queue - can be useful e.g. for running away from grenades.

*Example:*

```
AI.PushGoal("pathfind", 1, "refpoint");
```

#### proximity

Send signal on proximity to an object. Usually this isn't necessary since other logic is better for monitoring distances.

**Lua:** AI.PushGoal("proximity", blocking, radius, signal name, * flags*)

**C++:** class COPProximity

**XML:** <Proximity radius="number" signal="signal name" * signalWhenDisabled="****false****/true" visibleTargetOnly="****false****/true"*/>

**Parameters:** * flags*: **0** (default), AIPROX_VISIBLE_TARGET_ONLY, AIPROX_SIGNAL_ON_OBJ_DISABLE

*Examples:*

```
AI.PushGoal("proximity", 0, 20, "TARGET_CLOSE", AIPROX_VISIBLE_TARGET_ONLY);
--
AI.PushGoal("proximity", 0, -1, "TARGET_TOO_CLOSE", AIPROX_SIGNAL_ON_OBJ_DISABLE + AIPROX_VISIBLE_TARGET_ONLY);
```

#### run

(Alias: speed) Set movement speed – walk, run, sprint etc. If *"max length"* is given, "urgency" becomes scaled based on "length" and *"max length"*.

**Lua:** AI.PushGoal("run", blocking, max urgency, * min urgency, max length*)

**C++:** class COPRunCmd

**XML:** <Run * urgency= or maxUrgency= or id="****Zero****/Slow/Walk/Run/Sprint"*/>

**Parameters:** * min urgency*: **0** by default

*Example:*

```
-- boss suit over
AI.BeginGoalPipe("sn_advance_group_PROTO");
AI.PushGoal("firecmd", 0, FIREMODE_BURST_WHILE_MOVING);
AI.PushGoal("bodypos", 0, BODYPOS_STAND);
--
AI.PushGoal("run", 0, 2, 0, 20);
--
AI.PushGoal("strafe", 0, 2, 2);
AI.PushGoal("locate", 0, "refpoint");
AI.PushGoal("+approach", 1, 0, AILASTOPRES_USE, 4);
AI.PushGoal("signal", 0, 1, "COVER_NORMALATTACK", 0);
AI.EndGoalPipe();
```

#### script

Execute Lua code.

**C++:** class COPScript

**XML:** <Script code="Lua code"/>

#### seekcover

Look for nearby locations where line of sight to the target is obstructed – effectively finding adhoc cover from any object – and move there.

**Lua:** AI.PushGoal("seekcover", blocking, hide / unhide, radius, * iterations, LastOp options*)

**C++:** class COPSeekCover

**XML:** <SeekCover radius="number"

*minRadius="number (default is* ***0*** * i.e. "not used")"* * iterations="number (****3*** * by default)"* * hide="false/****true****"* * useLastOpAsBackup="false/****true****"* * towardsLastOpResult="false/****true****"*/>

**Parameters:** hide / unhide: COVER_HIDE / COVER_UNHIDE radius: seek the locations within this distance * iterations*: (**3** by default) the number of iterations * LastOp options* (**0** by default): 1 (set bit '0') to use LastOp if the attention target does not exists; add 2 (set bit '1') to prefer areas towards LastOp

*Example:*

```
AI.PushGoal("seekcover", 1, COVER_UNHIDE, 3, 2, 1);
```

#### signal

Send a signal to yourself, your group, those in range... Commonly used by decision logic in behaviour scripts to trigger a state change.

**Lua:** AI.PushGoal("signal", blocking, signal ID, * signal text, destination filter,* * extra signal data*)

**C++:** class COPSignal

**XML:** <Signal * name="signal name (empty string by default)"* * id="signal id (****1*** * by default)"* * data="data (****0*** * by default)"* * filter="see the table below (****Sender*** * by default)"*/>

**Parameters:** * signal text*: empty string by default

*destination filter*: one of the following:

Lua | XML
--- | ---
SIGNALFILTER_SENDER | Sender
SIGNALFILTER_LASTOP | LastOp
SIGNALFILTER_GROUPONLY | GroupOnly
SIGNALFILTER_FACTIONONLY | FactionOnly
SIGNALFILTER_ANYONEINCOMM | AnyoneInComm
SIGNALFILTER_TARGET | Target
SIGNALFILTER_SUPERGROUP | SuperGroup
SIGNALFILTER_SUPERFACTION | SuperFaction
SIGNALFILTER_SUPERTARGET | SuperTarget
SIGNALFILTER_NEARESTGROUP | NearestGroup
SIGNALFILTER_NEARESTSPECIES | NearestSpecies
SIGNALFILTER_NEARESTINCOMM | NearestInComm
SIGNALFILTER_HALFOFGROUP | HalfOfGroup
SIGNALFILTER_LEADER | Leader
SIGNALFILTER_GROUPONLY_EXCEPT | GroupOnlyExcept
SIGNALFILTER_ANYONEINCOMM_EXCEPT | AnyoneInCommExcept
SIGNALFILTER_LEADERENTITY | LeaderEntity
SIGNALFILTER_NEARESTINCOMM_FACTION | NearestInCommFaction
SIGNALFILTER_NEARESTINCOMM_LOOKING | NearestInCommLooking
SIGNALFILTER_FORMATION | Formation
SIGNALFILTER_FORMATION_EXCEPT | FormationExcept
SIGNALFILTER_READIBILITY | Readability
SIGNALFILTER_READIBILITYAT (readability anticipation) | ReadabilityAnticipation
SIGNALFILTER_READIBILITYRESPONSE (readability response) | ReadabilityResponse

*extra signal data*: 0 by default

*Example:*

```
AI.PushGoal("tank_attack_start", "signal", 0, 1, "TO_TANK_ALERT", SIGNALFILTER_ANYONEINCOMM);
```

#### speed

Same as "run".

#### stance

Same as "bodypos".

#### stick

Approach a target and try to maintain a given distance from it. This goalop will keep running until interrupted. Very commonly used.

**Lua:** AI.PushGoal("stick", blocking, stick distance or duration (controlled by * flags*), * flags, stick flags, end accuracy, end distance variation*)

**C++:** class COPStick

**XML:** <Stick duration="number" or distance="number"

*endAccuracy="number (****0*** * by default)"* * distanceVariation="number (default is* ***0*** * i.e. "not used")"* * useLastOp="****false****/true"* * lookAtLastOp="****false****/true"* * continuous="****false****/true"* * tryShortcutNavigation="****false****/true"* * requestPartialPath="****false****/true"* * stopOnAnimationStart="****false****/true"* * alignBeforeMove="****false****/true"* * locateName="AI object's name or a* *[SpecialAIobject](Goalop%20Reference.md#GoalopReference-SpecialAIobject); default is empty string"* * alignBeforeMove="****false****/true"* * constantSpeed="****false****/true"* * adjustSpeed="****false****/true"* * regenDistThreshold="number (default is* ***1****)"*/>

**Parameters:** stick distance or time: use flag AI_USE_TIME to specify time, rather than distance * flags* (**0** by default): AILASTOPRES_USE, AILASTOPRES_LOOKAT, AI_USE_TIME, AI_REQUEST_PARTIAL_PATH, AI_STOP_ON_ANIMATION_START, AI_DONT_STEER_AROUND_TARGET, AI_CONSTANT_SPEED, AI_ADJUST_SPEED

*stick flags*: (**0** by default) use STICK_BREAK for "non-continuous", rather than "continuous" stick; use STICK_SHORTCUTNAV to try shortcut navigation (i.e. direct connection)

*end accuracy*: (default is the value of the **distance**) allowable movement end accuracy * end distance variation*: **0** by default

*Examples:*

```
AI.PushGoal("stick", 0, 1, AI_DONT_STEER_AROUND_TARGET + AI_CONSTANT_SPEED, STICK_BREAK + STICK_SHORTCUTNAV);
--
AI.PushGoal("locate", 0, "atttarget");
AI.PushGoal("stick", 1, 10, AILASTOPRES_USE, STICK_BREAK);
```

#### strafe

Allow puppet to strafe while executing other movement commands. Works by specifying a distance at the start and end of the path that may employ strafing. Reset by SelectPipe. Very commonly used when moving while firing at a target.

**Lua:** AI.PushGoal("strafe", blocking, distance start, * distance end, strafe while moving*)

**C++:** class COPStrafe

**XML:** <Strafe * strafeWhileMoving="****false****/true" distance= or distanceStart="number (default is* ***0****)" distanceEnd="number"*/>

**Parameters:** distance start: strafe from the beginning up to this length of the path * distance end*: (**0** by default) strafe within this distance from the end of the path * strafe while moving*: **0** (default) or 1

*Examples:*

```
AI.PushGoal("bodypos", 0, BODYPOS_STAND, 1);
AI.PushGoal("strafe", 0, 2, 2);
AI.PushGoal("run", 0, 1);
--
AI.BeginGoalPipe("su_fast_bullet_reaction");
AI.PushGoal("bodypos", 1, BODYPOS_STAND, 1);
-- Be able to shoot while going anywhere
-- 100 (meters) result in "strafe all the way"
--
AI.PushGoal("strafe", 0, 100, 100);
--
AI.PushGoal("firecmd", 0, FIREMODE_BURST_DRAWFIRE);
AI.PushGoal("locate", 0, "probtarget");
AI.PushGoal("+seekcover",1, COVER_HIDE, 3, 2, 1);
AI.PushGoal("signal", 1, 1, "COVER_NORMALATTACK", 0);
AI.EndGoalPipe();
```

#### tacticalpos

See [Tactical Point System](../../../Tactical%20Point%20System.md).

#### timeout

Wait for a short time, randomly chosen within an interval.

**Lua:** AI.PushGoal("timeout", blocking, min time, * max time*)

**C++:** class COPTimeout

**XML:** <Timeout interval= or intervalMin="number" * intervalMax="number (default is* ***-1*** * i.e. "not used")"*/>

**Parameters:** * max time*: **0** (not used) by default

*Example:*

```
AI.PushGoal("timeout", 1, 2, 6);
```

#### trace

Perform path tracing to cause a puppet to reach a target, given a path. Usually employed internally by other goalops, not directly in behavior scripts.

**Lua:** AI.PushGoal("trace", blocking, * follow exactly*)

**C++:** class COPTrace

**XML:** <Trace endAccuracy="number (default is ** 0**)" * exactFollow="****false****/true"* * forceReturnPartialPath="****false****/true"* * stopOnAnimationStart="****false****/true"*/>

**Parameters:** * follow exactly*: 0 (default) / 1 (follow the path exactly, possibly looking at the target all the time) end accuracy: (default is **0**) allowable movement end accuracy

*Example:*

```
AI.PushGoal("pathfind", 1, "refpoint");
AI.PushGoal("branch", 1, "PATH_FOUND", NOT + IF_NO_PATH);
AI.PushGoal("signal", 0, 1, "OnUnitStop", SIGNALFILTER_LEADER);
AI.PushGoal("branch", 1, "DONE", BRANCH_ALWAYS);
AI.PushLabel("PATH_FOUND");
AI.PushGoal("signal", 0, 1, "OnUnitMoving", SIGNALFILTER_LEADER);
AI.PushGoal("trace", 1, 1);
...
AI.PushLabel("DONE");
```

#### usecover

Not supported.

When located at cover, analyze it and use it.

**Lua:** AI.PushGoal("usecover", blocking, hide / unhide, min time, * max time,* * use LastOp as backup*)

**C++:** class COPUseCover

**XML:** <UseCover/>

**Parameters:** hide / unhide: COVER_HIDE / COVER_UNHIDE * max time*: 0 by default * use LastOp as backup*: 0 by default

*Example:*

```
AI.PushGoal("locate", 0, "probtarget");
*AI.PushGoal("usecover", 1, COVER_UNHIDE, 5, 7, 1);*
*AI.PushGoal("usecover", 1, COVER_HIDE, 0.1, 0.3, 1);*
```

#### wait

Wait for a number of non-blocking goals to complete. This is rarely required in practice.

**Lua:** AI.PushGoal("wait", blocking, whom)

**C++:** class COPWait

**XML:** <Wait * for="****All****/Any/Any2"*/>

**Parameters:** whom: ** WAIT_ALL**, WAIT_ANY, or WAIT_ANY_2.

*Example:*

```
AI.BeginGoalPipe("tr_melee");
AI.BeginGroup();
AI.PushGoal("animation", 0, AIANIM_SIGNAL, "meleeAttack");
AI.PushGoal("timeout", 0, 1.4);
AI.EndGroup();
--
AI.PushGoal("wait", 1, WAIT_ANY);
--
AI.PushGoal("signal", 1, 1, "END_MELEE", SIGNALFILTER_SENDER);
AI.EndGoalPipe();
```

#### waitsignal

Wait for a certain signal to be received. Useful in simple cases, but usually better to take another approach – an FSM state, or two goalpipes, etc.

**Lua:** AI.PushGoal("waitsignal", blocking, signal to wait, signal data)

**C++:** class COPWaitSignal

**XML:** <WaitSignal name="signal name" * timeout="number (default is* ***0*** * i.e. "not used")"*/>

*Example:*

```
AI.BeginGoalPipe("tr_jump_fire_left");
AI.PushGoal("strafe", 0, 8);
AI.PushGoal("firecmd", 1, FIREMODE_CONTINUOUS);
--
-- Wait for the execution of OnLand signal
AI.PushGoal("waitsignal", 1, "OnLand", nil, 4);
AI.PushGoal("firecmd", 1, 0);
AI.EndGoalPipe();
```

### Special AI object

Some goalops (e.g. acqtarget or locate) allow to specify not only concrete AI object's name, but also a special object:

- animtarget

- atttarget

- atttarget_in_territory

- atttarget_in_refshape

- atttarget_in_territory_and_refshape

- beacon

- formation

- formation_id

- formation_special

- group_tac_pos

- group_tac_look

- hidepoint_lastop

- last_hideobject

- lookat_target

- player

- probtarget

- probtarget_in_territory

- probtarget_in_refshape

- probtarget_in_territory_and_refshape

- refpoint

- self

- vehicle_avoid

[Introduction](#introduction)[Goalop Reference](#goalop-reference)[Special AI object](#special-ai-object)
