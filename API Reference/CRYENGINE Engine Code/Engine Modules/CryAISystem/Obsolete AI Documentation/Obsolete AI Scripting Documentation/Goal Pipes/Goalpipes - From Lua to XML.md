# Goalpipes - From Lua to XML

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/23306484
- Page ID: 23306484
- Breadcrumb: CRYENGINE Engine Code > Engine Modules > CryAISystem > Obsolete AI Documentation > Obsolete AI Scripting Documentation > Goal Pipes > Goalpipes - From Lua to XML
- Parent: Goal Pipes

## Content

##
Example 1.

```

`
  <!--
    AI.BeginGoalPipe("DoNothing");
      AI.PushGoal("firecmd", 1, FIREMODE_OFF);
      AI.PushGoal("stance", 1, STANCE_RELAXED);
    AI.EndGoalPipe();
  -->
  <GoalPipe name="DoNothing">
    <FireCmd mode="Off"/>
    <Stance id="Relaxed"/>
  </GoalPipe>

`

```

AI.BeginGoalPipe and AI.EndGoalPipe are naturally replaced by tag <GoalPipe>. Keep in mind that XML goalops are
**
blocking
**
 by default, so there is no need to add attribute
**
blocking="true"
**
 to each blocking goalop.

##
Example 2.

```

`
  <!--
    AI.BeginGoalPipe("HideUnderPressure");
      AI.PushGoal("strafe", 0, 99, 99, 1);
      AI.PushGoal("usecover", 1, USECOVER_HIDE, COVERLOCATION_AUTOMATIC);
    AI.EndGoalPipe();
  -->
  <GoalPipe name="HideUnderPressure">
    <Strafe blocking="false" distance="99" strafeWhileMoving="true"/>
    <UseCover location="Automatic"/>
  </GoalPipe>

`

```

Note that if attributes "distanceStart" and "distanceEnd" of tag <Strafe> (goalop Strafe) have same values, you can use a single attribute "distance" instead. The same applies to tags like <Timeout intervalMin="0.25" intervalMax="1"/>, i.e. you can use attribute "interval" instead if the values are the same. Also note that with tag <UseCover> (which is actually deprecated!), it is natural to have attribute hide="true" by default.

##
Example 3.

```

`
  <!--
    AI.BeginGoalPipe("SearchApproachCautiously");
      AI.PushGoal("tacticalpos", 1, "ApproachHidespotQuery", AI_REG_REFPOINT);
      AI.PushGoal("branch", 0, "QuerySucceed", IF_LASTOP_SUCCEED);
      AI.PushGoal("signal", 0, 1, "OnTPSQueryFail", SIGNALFILTER_SENDER);
      AI.PushGoal("branch", 0, "End", BRANCH_ALWAYS);
      AI.PushLabel("QuerySucceed");
      AI.PushGoal("SearchWalkToReferencePoint");
      AI.PushLabel("End");
    AI.EndGoalPipe();
  -->
  <GoalPipe name="SearchApproachCautiously">
    <TacticalPos name="ApproachHidespotQuery" register="RefPoint"/>
    <If IF_LASTOP_SUCCEED="">
      <SubGoalPipe name="SearchWalkToReferencePoint"/>
    <Else/>
      <Signal blocking="false" name="OnTPSQueryFail"/>
    </If>
  </GoalPipe>

`

```

There's no need to exercise your low-level assembly language skills to model If-Then-Else constructs. Note the attribute of tag <If>. For now, valid attributes are identical to those already used in Lua. You can prepend them with "NOT_". <If> is the same as <IfAnd>.

Also note that by default signal ID is 1 and signal filter is SIGNALFILTER_SENDER. This makes sense in the vast majority of cases.

##
Example 4.

```

`
  <!--
    AI.BeginGoalPipe("SearchLookAround");
      AI.PushGoal("speed", 0, SPEED_WALK);
      AI.PushGoal("strafe", 0, 99, 99, 1);
      AI.PushGoal("stance", 0, STANCE_STAND);
      AI.PushLabel("LOOK_LOOP");
      AI.PushGoal("lookaround", 1, 360, 5, 60, 60, AI_BREAK_ON_LIVE_TARGET, 0);
      AI.PushGoal("branch", 1, "LOOK_LOOP", BRANCH_ALWAYS);
    AI.EndGoalPipe();
  -->
  <GoalPipe name="SearchLookAround">
    <Speed blocking="false" id="Walk"/>
    <Strafe blocking="false" distance="99"/>
    <Stance blocking="false" id="Stand"/>
    <Loop>
      <LookAround lookAroundRange="360" scanRange="5" interval="60" breakOnLiveTarget="true"/>
    </Loop>
  </GoalPipe>

`

```

Note tag <Loop>.
