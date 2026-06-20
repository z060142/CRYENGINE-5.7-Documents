# Refpoints

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/23306490
- Page ID: 23306490
- Breadcrumb: CRYENGINE Engine Code > Engine Modules > CryAISystem > Obsolete AI Documentation > Refpoints
- Parent: Obsolete AI Documentation

## Content

##
Overview

Refpoint ("reference point") is a special AI object intended to be used by goalpipes. Basically, only its position and - if necessary - direction are used.

##
Example 1

```

`
ACT_GOTO = function(self, entity, sender, data)
  if (data and data.point) then
    AI.SetRefPointPosition(entity.id, data.point);

    -- use dynamically created goal pipe to set approach distance
    g_StringTemp1 = "action_goto"..data.fValue;
    AI.CreateGoalPipe(g_StringTemp1);
    AI.PushGoal(g_StringTemp1, "locate", 0, "refpoint");
    AI.PushGoal(g_StringTemp1, "+stick", 1, data.point2.x, AILASTOPRES_USE, 1, data.fValue); -- noncontinuous stick
    AI.PushGoal(g_StringTemp1, "signal", 0, 1, "VEHICLE_GOTO_DONE", SIGNALFILTER_SENDER);
    entity:InsertSubpipe(AIGOALPIPE_SAMEPRIORITY, g_StringTemp1, nil, data.iValue);
  end
end,
`

```

In this example:

-
The position of the refpoint is set

-
Based on the refpoint, goalop "locate" sets the LASTOP

-
Goalop "stick" uses this LASTOP as the destination.
Note '+' in "+stick". It makes goalop "stick" group with the previous goalop ("locate"). So if a subgoalpipe is inserted which interrupts goalop "stick", the original goalpipe will resume from goalop "locate" (the first in the group), not "stick". It is necessary because the subgoalpipe might change the LASTOP, in which case goalop "stick" will direct the AI actor to a wrong destination.

##
Example 2

```

`
  OnBiomassDetected = function(self, entity, sender, data)
    entity:SetTargetBiomass(sender);
    entity:SelectPipe(0, "AlienTick_ReachBiomass");
  end,
`

```

```

`
function AlienTick_x:SetTargetBiomass(biomass)
  self.AI.targetBiomassId = biomass.id;
  AI.SetRefPointPosition(self.id, biomass:GetWorldPos());
  AI.SetRefPointDirection(self.id, biomass:GetDirectionVector(1));
end
`

```

```

`
  <GoalPipe name="AlienTick_ReachBiomass">
    <Speed id="Walk"/>
    <Locate name="refpoint"/>
    <Stick distance="0.3" useLastOp="true"/>
    <Signal name="OnBiomassReached"/>
  </GoalPipe>
`

```

```

`
  OnBiomassReached = function(self, entity)
    entity.actor:SetForcedLookDir(AI.GetRefPointDirection(entity.id));
    entity:SelectPipe(0, "AlienTick_CollectBiomass");
  end,
`

```

In this example,

-
**
OnBiomassDetected
**
 is called - presumably by the Smart Object System, which spotted a relevant AI Anchor, so the parameter
**
sender
**
 refers to this AI Anchor.

-
**
SetTargetBiomass
**
 uses this AI Anchor to set both the position and direction of the refpoint.

-
AI walks to the refpoint, assumes the desired direction, and in turn selects the next goalpipe.
Note that tag <Group> was not used in this example because this particular goalpipe was not intended to be interrupted (which is
*
not
*
 the case in general).
