# Individual AI

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/23306462
- Page ID: 23306462
- Breadcrumb: CRYENGINE Engine Code > Engine Modules > CryAISystem > Obsolete AI Documentation > AI System Overview > Individual AI
- Parent: AI System Overview

## Content

Some parts of this article referring to Behavior Selection Trees and old-style behavior scripts are for CRYENGINE 3.4 or earlier. The Behavior Selection Tree and old-style behavior scripts were deprecated in favor of the Modular Behavior Tree in CRYENGINE 3.5 and beyond.

### Overview

### Dynamic covers, generated offline and adjusted during run time

#### Example: CoverSurface and HMMWV

![Image](https://www.cryengine.com/docs/static/attachments/23461217)

(Here **ai_DebugDraw=1**, ** ai_DebugDrawCover=2**, and **[AI/Physics]** is on.)

### Dynamic tactical points

#### Example: A very shy civilian who always wants to hide from the player

- TPS query:
```
AI.RegisterTacticalPointQuery({
Name = "Civilian_HideFromEnemy",
{
Generation =
{
cover_from_attentionTarget_around_puppet = 25
},
Conditions =
{
reachable = true,
},
Weights =
{
distance_from_puppet = -1,
},
},
});
```

- TPS query referenced in a goalpipe:
```
<GoalPipes>
<GoalPipe name="Civilian_HideFromEnemy">
<TacticalPos name="Civilian_HideFromEnemy"/>
</GoalPipe>
</GoalPipes>
```

- Goalpipe selected in a behavior:
```
local Behavior = CreateAIBehavior("CivilianIdle",
{
Alertness = 0,

OnEnemySeen = function(self, entity, distance)
entity:SelectPipe(0, "Civilian_HideFromEnemy");
end,

OnTPSDestReached = function(self, entity)
entity:SelectPipe(0, "_first_");
end,
})
```

- Grunt's properties:

![Image](https://www.cryengine.com/docs/static/attachments/23461218)

- Useful AI debug draw:
- **ai_DebugTacticalPoints=1**
- **ai_StatsTarget=Grunt1**
- **ai_TacticalPointsDebugTime=10**

- For more realism, add the following before goalop **TacticalPos**:
```
<Speed id="Sprint"/>
```

### Behavior trees

#### Example: A civilian who hides from the shooting player

- New Civilian behavior:
```
<?xml version="1.0" encoding="utf-8"?>
<SelectionTrees>
<SelectionTree name="Civilian" type="BehaviorSelectionTree">

<Variables>
<Variable name="alerted"/>
</Variables>

<SignalVariables>
<Signal name="OnNoTarget" variable="alerted" value="false"/>
</SignalVariables>

<LeafTranslations>
<Map node="Alerted" target="CivilianAlerted"/>
<Map node="Idle" target="CivilianIdle"/>
</LeafTranslations>

<Priority name="Root">
<Leaf name="Alerted" condition="alerted"/>
<Leaf name="Idle"/>
</Priority>

</SelectionTree>
</SelectionTrees>
```

- Idle behavior:
```
local Behavior = CreateAIBehavior("CivilianIdle",
{
Alertness = 0,

OnBulletRain = function(self, entity, sender, data)
entity.AI.hostileId = data.id;
AI.AddPersonallyHostile(entity.id, entity.AI.hostileId);
AI.SetBehaviorVariable(entity.id, "alerted", true);
end,

OnTPSDestReached = function(self, entity)
entity:SelectPipe(0, "_first_");
end,
});
```

- Alerted behavior:
```
local Behavior = CreateAIBehavior("CivilianAlerted", "CivilianIdle",
{
Alertness = 2,
Constructor = function(self, entity)
entity:SelectPipe(0, "Civilian_HideFromEnemy");
end,

Destructor = function(self, entity)
AI.RemovePersonallyHostile(entity.id, entity.AI.hostileId);
end,
});
```

- Civilian's properties:

![Image](https://www.cryengine.com/docs/static/attachments/23461219)

- Useful AI debug draw:
- **ai_DebugTargetTracksAgent=Grunt1**

- Check out Views:
- AI Debugger
- Behavior Selection Tree Editor

[Dynamic covers, generated offline and adjusted during run time](#dynamic-covers-generated-offline-and-adjusted-during-run-time)[Dynamic tactical points](#dynamic-tactical-points)[Behavior trees](#behavior-trees)
