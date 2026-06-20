# Create A Simple AI Behavior

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/23306478
- Page ID: 23306478
- Breadcrumb: CRYENGINE Engine Code > Engine Modules > CryAISystem > Obsolete AI Documentation > Obsolete AI Scripting Documentation > Behavior Selection Trees > Create A Simple AI Behavior
- Parent: Behavior Selection Trees

## Content

This article is for CRYENGINE 3.4 or earlier. The Behavior Selection Tree was deprecated in favor of the Modular Behavior Tree in CRYENGINE 3.5 and beyond.

### Overview

This article will show you how to create a new simple Selection Tree from scratch with related XML goal pipes and TPS queries.

### Introduction

This tutorial assumes a basic knowledge of AI behavior trees and state machines. For those with no experience or knowledge of behavior selection trees, a good introduction can be found . There are also numerous resources on the internet that cover using behavior trees for AI characters in computer games and countless sources relating to state machines.
This tutorial will cover:

- Creating new AI behavior selection tree.
- AI Signals.
- Core AI engine functions.
- AI goal pipes.
- Grouping the behaviors together into an AI "Personality".

Every AI agent has a "personality" or "type"; in a simple action game we might want a leader and a squad member, further still we might want different types of squad members such as a basic soldier and a sniper.

These AI characters will all have different personalities and thus different behaviors.

In this simple example we'll create a basic AI character that will keep a certain distance from the player and that will shoot at the player whenever it's in a certain range. We'll call this new personality "fog of war".

This is the states diagram for this personality.

![Image](https://www.cryengine.com/docs/static/attachments/23461248)

### Create a new selection tree

First of all we need to create the new selection tree file FogOfWar.xml inside: `<root>\Game\Scripts\AI\SelectionTrees`

Inside the file we can add this code:

```
<SelectionTrees>
<SelectionTree name="FogOfWar" type="BehaviorSelectionTree">
<Variables>
<Variable name="IsFar"/>
<Variable name="IsClose"/>
<Variable name="AwareOfPlayer"/>
</Variables>

<SignalVariables>
<Signal name="OnEnemySeen" variable="AwareOfPlayer" value="true" />
<Signal name="OnNoTarget" variable="AwareOfPlayer" value="false" />
<Signal name="OnLostSightOfTarget" variable="AwareOfPlayer" value="false" />
</SignalVariables>

<Priority name="Root">
<Leaf name="FogOfWarSeekST" condition="IsFar" />
<Leaf name="FogOfWarEscapeST" condition="IsClose" />
<Leaf name="FogOfWarAttackST" condition="AwareOfPlayer" />
<Leaf name="FogOfWarIdleST" />
</Priority>
</SelectionTree>
</SelectionTrees>
```

As you can see from the XML structure, we have 3 different blocks contained into the <SelectionTree> tag (The <SelectionTrees> tag is only used to group different selection trees in one file, but keeping one tree per file allows the system to be more readable):

- **Variables**
- This blocks specifies the variables used to define what we will call the knowledge of the AI agent. They are conceptual switches between the different states of the behavior selection tree.
- **SignalVariables**
- It's a list of signals that when triggered will set the corresponding variable value to the one specified.
- **Priority**
- The <Priority> tag describes the actual selection tree. It can contains several <Leaf> or <Prioriy> nodes. The Priority node is evaluated from the first child to the next one, and the evaluation stops as soon as a the SelectionTreeManager in the C++ code find a true condition. At that point the correspondent behavior will be executed.

Let's describe the different behaviors we want to model:

Behavior name | Description
--- | ---
**FogOfWarIdleST** | Basic behavior, active as default. If none of the conditions are evaluated as true, then this is the fall back behavior.
**FogOfWarAttackST** | This is the behavior that manages the attack actions of the AI agent. It will make the AI agent start shooting if its in a specific range of the player.
**FogOfWarSeekST** | When the AI agent is too far from the player, this state will make it run in the direction of the player until a defined distance.
**FogOfWarEscapeST** | When the AI agent is too close to the player, this state will make it move away from the player until it reaches a "safe" distance, it will regularly recheck if it's far enough away.

We'll now need to create the different behaviors that will be executed during game play.

### Creating a new Goal pipe file that will contain all the goal pipes for the desired behavior.

To achieve this result, we first create a file called GoalPipesFogOfWar.xml into the folder: `<root>\Game\Scripts\AI\GoalPipes`

We will define the empty file as follows:

```
<GoalPipes>
</GoalPipes>
```

Then inside the file: `<root>\Game\Scripts\AI\GoalPipe\PipeManager.lua`

We will need to add the function call to reload our user defined goal pipes list as follows:

```
function PipeManager:CreateGoalPipes()
{
[...]
AI.LoadGoalPipes("Scripts/AI/GoalPipes/GoalPipesFogOfWar.xml");
[...]
}
```

To read more about XML goal pipes you can click [here](../Goal%20Pipes.md).

### Creating the different states for the FogOfWar personality and related goalpipes

##### FogOfWarIdleST

**Behavior Script**

The **FogOfWarIdleST** state is the basic behaviour that the AI is going to use when it's in the idle state (for example just after entering game mode).

We will now create the file FogOfWarIdle.lua inside the folder `<root>\Game\Scripts\AI\Behaviors\Personalities\FogOfWarST`

Inside this file we will add the following code:

```
local Behavior = CreateAIBehavior("FogOfWarIdleST",
{
Alertness = 0,

Constructor = function (self, entity)
Log("Idling...");
AI.SetBehaviorVariable(entity.id, "AwareOfPlayer", false);
entity:SelectPipe(0,"fow_idle_st");
end,

Destructor = function(self, entity)
end,

})
```

As we can see we initially define the behavior with the name **FogOfWarIdleST** to match the state name. The function ** CreateAIBehavior** is taking care of creating and storing the behavior into the local ** Behavior** variable.

The constructor is just logging some text and selecting the pipe "fow_idle_st" to clean the goals the AI has whenever it will fall back into the idle state (SelectPipe is always cleaning the previously selected pipe).

**XML Goalpipe**

We now need to define the "fow_idle_st" goal pipe. In the idle behavior we just want that the AI agent will try to locate the player. We can then open the file **GoalPipesFogOfWar.xml** and add the following lines:

```
<GoalPipe name="fow_idle_st">
<Locate name="player" />
</GoalPipe>
```

We define a new goal pipe through the tag <GoalPipe>, we specify the name and then we use the tag <Locate> which is connected to the locate goal op. Some of the possible target name strings to be located can be:

Possible target to locate | Description
--- | ---
**player** | It's the local player.
**attarget** | The current attention target for the AI agent.
**refpoint** | It's a point in the world stored as a reference point.
**probtarget** | It's the most probable target for the AI agent.

###### FogOfWarAttackST

**Behavior Script**

The FogOfWarAttackST is the main behavior state. It will check the distance of the agent from the target and, depending on it, it will start seeking or escaping from the player to keep a certain distance.

The code contained in this file is the following:

```
local Behavior = CreateAIBehavior("FogOfWarAttackST",
{
Alertness = 2,

Constructor = function (self, entity)
entity:MakeAlerted();
entity:DrawWeaponNow();
self:AnalyzeSituation(entity);
end,

Destructor = function(self, entity)
end,

AnalyzeSituation = function (self, entity, sender, data)
local min_dist = 10.0;
local range = 5.0;
if(AI.GetAttentionTargetDistance(entity.id) < min_dist) then
Log("Too close!!!!");
AI.SetBehaviorVariable(entity.id, "IsClose", true);
AI.SetBehaviorVariable(entity.id, "IsFar", false);
return;
elseif(AI.GetAttentionTargetDistance(entity.id) > min_dist + range) then
Log("Too far!!!");
AI.SetBehaviorVariable(entity.id, "IsFar", true);
AI.SetBehaviorVariable(entity.id, "IsClose", false);
return;
end
Log("Attack!!!!!")
entity:SelectPipe(0, "fow_fire_st");
end,
})
```

In the constructor we make the entity alerted and we draw the weapon. Then we call the function **AnalyzeSituation()** to perform the actual calculation of the distance between the AI agent and his attention target.

**AnalyzeSituation** stores the min_dist and the range values and it checks the distance between the AI agent and the attention target (the player). At this point we use the function ** AI.SetBehaviorVariable(...)** to modify the agent knowledge and make the SelectionTreeManager select the right behavior on the next tree evaluation. The function ** AI.SetBehaviorVariable** is defined as:

```
AI.SetBehaviorVariable(entityId, variableName, variableValue)
```

Where **entityId** is the Id of the entity you want to modify the knowledge of, ** variableName** is the string name of the variable we want to change and ** variableValue** is the new value we want to store.

If the distance between the player and the AI is less than the minimum distance acceptable, we will set the **IsFar** variable to * false* and the **IsClose** variable to * true*.

If the distance between the player and the AI is greater than the minimum distance plus a certain range, we will set the **IsFar** variable to * true* and the **IsClose** variable to * false*.

Also we select the **fow_fire_st** goal pipe that will perform firing operations.

**XML Goalpipe**

We can now define the fow_fire_st inside the file GoalPipesFogOfWar.xml as follows:

```
<GoalPipe name="fow_fire_st">
<Locate name="player" />
<FireCmd useLastOp="true" blocking="true" mode="Burst" />
<Timeout blocking="true" intervalMin="1" intervalMax="1"/>
<FireCmd mode="Off"/>
<Script code="entity.Behavior:AnalyzeSituation(entity);" />
</GoalPipe>
```

The defined sequence of operation can be described as follows:

- Locate the player.
- Shoot at the located player with Burst mode. This operation is a blocking op.
- Wait for 1 second.
- Stop shooting.
- Check the situation of the world again (distance of AI agent/player).

###### FogOfWarEscapeST

**Behavior Script**

This state makes the AI agent run away from the player and then evaluate the distance between the grunt and the player again.

The code is the following:

```
local Behavior = CreateAIBehavior("FogOfWarEscapeST",
{
Alertness = 2,

Constructor = function (self, entity)
Log("Running away!");
entity:SelectPipe(0, "fow_escape_st");
end,

Destructor = function(self, entity)
end,

AnalyzeSituation = function (self, entity, sender, data)
local min_dist = 10.0;
local range = 5.0;
local distance = AI.GetAttentionTargetDistance(entity.id);
if(distance > min_dist and distance < (min_dist + range)) then
AI.SetBehaviorVariable(entity.id, "IsClose", false);
elseif(distance > (min_dist + range)) then
AI.SetBehaviorVariable(entity.id, "IsFar", true);
AI.SetBehaviorVariable(entity.id, "IsClose", false);
end
end,

})
```

In the constructor of the player we just select the goal pipe **fow_escape_st**. In the script we also define the function AnalyzeSituation that checks the distance between the player and the AI agent.

**XML Goalpipe**

Inside the **GoalPipesFogOfWar.xml** we can now define the goal pipe ** fow_escape_st**:

```
<GoalPipe name="fow_escape_st">
<Speed id="Run"/>
<Locate name="player" />
<TacticalPos name="FogOfWarEscapeCoverQuery" register="Cover"/>
<If IF_LASTOP_SUCCEED="">
<Hide register="Cover"/>
<Else/>
<Script code="AI.SetBehaviorVariable(entity.id, 'IsClose', false)" />
</If>
<Script code="entity.Behavior:AnalyzeSituation(entity);" />
</GoalPipe>
```

The defined sequence of operation can be described as follows:

- We set the speed to the Run mode.
- We locate the player.
- We search for a cover point querying the **Tactical Point System** through the query ** FogOfWarEscapeCoverQuery** (To read more about the TPS you can click).
- If the query returned a valid point then we hide at the point stored in the *Cover* reference otherwise we considered ourself not close to the player any more.
- We analyze the situation again.

In this goal pipe example we can highlight the use of the **<If...> <Else/> </If>** structure and the **<TacticalPos>** goal op that we are going to explain in more detail.

**Tactical Point System query**

We can define customized Tactical Point System query for our behaviors. We can add the customized queries into any of the pre-existing TPS queries file or write a new file. In this example we will create the new **FogOfWarQueries.lua** inside the folder: `<root>\Game\Scripts\AI\TPS`

The content of that file will then be:

```
AI.TacticalPositionManager.Grunt = AI.TacticalPositionManager.Grunt or {};

function AI.TacticalPositionManager.Grunt:OnInit()

AI.RegisterTacticalPointQuery({
Name = "FogOfWarEscapeCoverQuery",
{
Generation =
{
hidespots_from_attentionTarget_around_puppet = 25,
},
Conditions =
{
min_distance_to_attentionTarget = 10.0,
canReachBefore_the_attentionTarget = true,
hasShootingPosture_to_attentionTarget = true,
},
Weights =
{
distance_to_puppet = 0.1,
distance_to_attentionTarget = 0.9,
},
},
});

end
```

We basically want to generate a set of **hidespots** from the ** attention target** contained in a circular area with a diameter of 25 meters. The points need to be at a minimum distance from the ** attention target** of 10m, they have to be ** reachable** by the AI agent before the attention target and they must allow for a ** shooting posture** to the attention target. Also we will prefer to use the points that are closer to the puppet than the ones closer to the attention target using weights.

###### FogOfWarSeekST

**Behavior Script**

This state makes the AI agent approach the player until a certain safe distance is reached. The code is the following:

```
local Behavior = CreateAIBehavior("FogOfWarSeekST",
{
Alertness = 1,

Constructor = function (self, entity)
Log("Approaching!");
entity:SelectPipe(0, "fow_seek_st");
end,

Destructor = function(self, entity)
end,

AnalyzeSituation = function (self, entity, sender, data)
local min_dist = 10.0;
local range = 5.0;
local distance = AI.GetAttentionTargetDistance(entity.id);
if(distance > (min_dist + range)) then
AI.SetBehaviorVariable(entity.id, "IsFar", true);
elseif(distance < (min_dist + range)) then
AI.SetBehaviorVariable(entity.id, "IsFar", false);
end
end,
})
```

Also in this case the only thing we do when we construct the behavior is to select the fow_seek_st goal pipe. We then define the Analyze function for this behavior.

**XML Goalpipe**

In the **fow_seek_st** goal pipe we can find the following code:

```
<GoalPipe name="fow_seek_st">
<Locate name="player" />
<Speed id="Run"/>
<Stick blocking="true" distance="10" useLastOp="true" />
<Script code="entity.Behavior:AnalyzeSituation(entity);" />
</GoalPipe>
```

The defined sequence of operation can be described as follows:

- We locate the player.
- We set the movement speed to Run.
- We try and stick to a distance of 10 meters to the point stored as a result of the last operation (In this case Locate wrote into the shared location).
- We analyze the situation.

### Conclusions and future improvements

Prototyping a new behavior or also scripting a full new behavior for your game it's pretty easy, in this example we covered:

- Selection Trees.
- XML Goal pipes.
- Tactical Point System queries.

One improvement for this behavior could be to move the common part of the **AnalyzeSituation()** function to an external utility script file to make easier the modification of that block of code and minimize the duplication of the behavior logic.

[Introduction](#introduction)[Create a new selection tree](#create-a-new-selection-tree)[Creating a new Goal pipe file that will contain all the goal pipes for the desired behavior.](#creating-a-new-goal-pipe-file-that-will-contain-all-the-goal-pipes-for-the-desired-behavior)[Creating the different states for the FogOfWar personality and related goalpipes](#creating-the-different-states-for-the-fogofwar-personality-and-related-goalpipes)[Conclusions and future improvements](#conclusions-and-future-improvements)
