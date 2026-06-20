# Signal Reference

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/23306493
- Page ID: 23306493
- Breadcrumb: CRYENGINE Engine Code > Engine Modules > CryAISystem > Signals > Signal Reference
- Parent: Signals

## Content

##
Overview

Typical signal handler looks something like this:

```

`
OnEnemySeen = function(self, entity, distance)
  -- called when the AI sees a living enemy
end,

`

```

Parameters
**
self
**
 (behavior table) and
**
entity
**
 (entity table) are passed to every signal handler, so they are omitted below in the lists of parameters.

See also:
`
\Game\Scripts\AI\Behaviors\Template.lua
`
.

##
Perception

The following signals are sent to AIs when perception types of their attention targets change.

Note that AITHREAT_SUSPECT < AITHREAT_INTERESTING < AITHREAT_THREATENING < AITHREAT_AGGRESSIVE.

##
No Target

Name

 |
Parameters

 |
Description

 |

**
OnNoTarget
**

 |
 |
Attention target is lost

 |

##
Sound

Sound heard (no visible target).

Name

 |
Description

 |

**
OnSuspectedSoundHeard
**

 |
Threat is AITHREAT_SUSPECT

 |

**
OnInterestingSoundHeard
**

 |
Threat is AITHREAT_INTERESTING

 |

**
OnThreateningSoundHeard
**

 |
Threat is AITHREAT_THREATENING

 |

**
OnEnemyHeard
**

 |
Threat is AITHREAT_AGGRESSIVE

 |

##
Memory

The target is not visible and is in memory.

Name

 |
Description

 |

**
OnEnemyMemory
**

 |
Threat is AITHREAT_THREATENING

 |

**
OnLostSightOfTarget
**

 |
Threat is AITHREAT_AGGRESSIVE

 |

Name

 |
Description

 |

**
OnMemoryMoved
**

 |
Threat is AITHREAT_AGGRESSIVE and its location or owner has changed

 |

##
Visual

The target is visible.

Name

 |
Parameters

 |
Description

 |

**
OnSuspectedSeen
**

 |
 |
Threat is AITHREAT_SUSPECT

 |

**
OnSomethingSeen
**

 |
 |
Threat is AITHREAT_INTERESTING

 |

**
OnThreateningSeen
**

 |
 |
Threat is AITHREAT_THREATENING

 |

**
OnEnemySeen
**

 |
distance

 |
Threat is AITHREAT_AGGRESSIVE

 |

Name

 |
Parameters

 |
Description

 |

**
OnObjectSeen
**

 |
distance, data

 |
AI sees an object registered for this signal. data.iValue = AI object type (e.g. AIOBJECT_GRENADE or AIOBJECT_RPG)

 |

Name

 |
Parameters

 |
Description

 |

**
OnExposedToExplosion
**

 |
data

 |
AI is affected by explosion at data.point

 |

**
OnExplosionDanger
**

 |
 |
Destroyable object explodes

 |

##
Awareness of Player

Name

 |
Parameters

 |
Description

 |

**
OnPlayerLooking
**

 |
sender, data

 |
Player is looking at the AI for entity.Properties.awarenessOfPlayer seconds. data.fValue = player distance

 |

**
OnPlayerSticking
**

 |
sender

 |
Player is staying close to the AI since <entity.Properties.awarenessOfPlayer> seconds

 |

**
OnPlayerLookingAway
**

 |
sender

 |
Player has just stopped looking at the AI

 |

**
OnPlayerGoingAway
**

 |
sender

 |
Player has just stopped staying close to the AI

 |

##
Awareness of Attention Target

Name

 |

**
OnTargetApproaching
**

 |

**
OnTargetFleeing
**

 |

**
OnNewAttentionTarget
**

 |

**
OnAttentionTargetThreatChanged
**

 |

**
OnNoTargetVisible
**

 |

**
OnNoTargetAwareness
**

 |

Name

 |
Parameters

 |
Description

 |

**
OnSeenByEnemy
**

 |
sender

 |
AI is seen by the enemy

 |

##
Weapon Damage

Name

 |
Parameters

 |
Description

 |

**
OnBulletRain
**

 |
sender

 |
Enemy is shooting

 |

**
OnDamage
**

 |
sender, data

 |
AI was damaged by another friendly/unknown AI. data.id = damaging AI's entity id

 |

**
OnEnemyDamage
**

 |
sender, data

 |
AI was damaged by an enemy AI. data.id = damaging enemy's entity id

 |

##
Proximity

Name

 |
Description

 |

**
OnCloseContact
**

 |
enemy gets at a close distance to an AI (defined by Lua Property "damageRadius" of this AI)

 |

**
OnCloseCollision
**

 |
 |

##
Vehicles

Name

 |
Parameters

 |
Description

 |

**
OnVehicleDanger
**

 |
sender, data

 |
vehicle is going towards the AI. data.point = vehicle movement direction, data.point2 = AI direction with respect to vehicle

 |

**
OnEndVehicleDanger
**

 |
 |
 |

Name

 |
Parameters

 |
Description

 |

**
OnTargetTooClose
**

 |
sender, data

 |
attention target is too close for the current weapon range (it works only if AI is a vehicle)

 |

**
OnTargetTooFar
**

 |
sender, data

 |
attention target is too close for the current weapon range (it works only if AI is a vehicle)

 |

**
OnTargetDead
**

 |
 |
 |

##
User-defined

Custom signals can be sent when an attention target enters or leaves certain ranges. This is configured using the following Lua functions:

```

`
AI.ResetRanges(entityID);
AI.AddRange(entityID, range, enterSignal, leaveSignal);
AI.GetRangeState(entityID, rangeID);
AI.ChangeRange(entityID, rangeID, distance);
`

```

##
Weapon-related

Name

 |
Description

 |

**
OnLowAmmo
**

 |
 |

**
OnMeleeExecuted
**

 |
 |

**
OnOutOfAmmo
**

 |
 |

**
OnReload
**

 |
AI goes into automatic reload after its clip is empty

 |

**
OnReloadDone
**

 |
reload is done

 |

**
OnReloaded
**

 |
 |

##
Navigation

##
Pathfinding

Name

 |
Parameters

 |
Description

 |

**
OnEndPathOffset
**

 |
sender

 |
AI has requested a path and the end of path is far from the desired destination

 |

**
OnNoPathFound
**

 |
sender

 |
AI has requested a path which is not possible

 |

**
OnPathFindAtStart
**

 |
 |
 |

**
OnBackOffFailed
**

 |
sender

 |
AI tried to execute a "backoff" goal which failed

 |

**
OnPathFound
**

 |
sender

 |
AI has requested a path and it's been computed successfully

 |

##
Steering

Name

 |

**
OnSteerFailed
**

 |

##
Smart Objects

Name

 |

**
OnEnterNavSO
**

 |

**
OnLeaveNavSO
**

 |

**
OnUseSmartObject
**

 |

##
Navigation Shapes

Name

 |

**
OnShapeEnabled
**

 |

**
OnShapeDisabled
**

 |

##
Tactics

##
Tactical Point System

Name

 |

**
OnTPSDestNotFound
**

 |

**
OnTPSDestFound
**

 |

**
OnTPSDestReached
**

 |

##
Cover

Name

 |

**
OnHighCover
**

 |

**
OnLowCover
**

 |

**
OnMovingToCover
**

 |

**
OnMovingInCover
**

 |

**
OnEnterCover
**

 |

**
OnLeaveCover
**

 |

**
OnCoverCompromised
**

 |

##
Hidespots (deprecated)

Name

 |
Parameters

 |
Description

 |

**
OnNoHidingPlace
**

 |
sender, data

 |
no hiding place can be found with the specified parameters. data.fValue = distance at which the hidespot has been searched

 |

**
OnBadHideSpot
**

 |
sender

 |
AI reaches a hidespot which proves to not hide correctly

 |

**
OnCoverReached
**

 |
sender

 |
AI reached the hidespot and is now well hidden

 |

**
OnRightLean
**

 |
sender

 |
A bad hidespot is reached, and AI can lean on the right

 |

**
OnLeftLean
**

 |
sender

 |
A bad hidespot is reached, and AI can lean on the left

 |

**
OnLowHideSpot
**

 |
sender

 |
AI reaches a hidespot which is too low to fit when standing up

 |

**
OnSameHidespotAgain
**

 |
 |
 |

##
Groups

Name

 |

**
OnGroupChanged
**

 |

**
OnGroupMemberMutilated
**

 |

**
OnGroupMemberDiedNearest
**

 |

##
Formation

Name

 |
Parameters

 |
Description

 |

**
OnNoFormationPoint
**

 |
sender

 |
AI couldn't find a formation point

 |

**
OnFormationPointReached
**

 |
 |
 |

**
OnGetToFormationPointFailed
**

 |
 |
 |

##
Group Coordination

Group target is the most threatening target of the group.

Name

 |

OnGroupTargetNone

 |

OnGroupTargetSound

 |

OnGroupTargetMemory

 |

OnGroupTargetVisual

 |

Name

 |

**
PerformingRole
**

 |

##
Flow Graph

These are signals sent by corresponding Flow Graph nodes when they are activated.

Name

 |
Sent by

 |

**
ACT_AIMAT
**

 |
AI:AIShootAt

 |

**
ACT_ALERTED
**

 |
AI:AIAlertMe

 |

**
ACT_ANIM
**

 |
AI:AIAnim

 |

**
ACT_ANIMEX
**

 |
AI:AIAnimEx

 |

**
ACT_CHASETARGET
**

 |
Vehicle:ChaseTarget

 |

**
ACT_DIALOG
**

 |
AI:ReadabilityDialog (also sent by Dialog System)

 |

**
ACT_DIALOG_OVER
**

 |
Sent by Dialog System

 |

**
ACT_DUMMY
**

 |
 |

**
ACT_DROP_OBJECT
**

 |
AI:AIDropObject

 |

**
ACT_ENTERVEHICLE
**

 |
Vehicle:Enter

 |

**
ACT_EXECUTE
**

 |
AI:AIExecute

 |

**
ACT_EXITVEHICLE
**

 |
Vehicle:Exit, Vehicle:Unload

 |

**
ACT_FOLLOW
**

 |
AI:AIFollow

 |

**
ACT_FOLLOWPATH
**

 |
AI:AIFollowPath, AI:AIFollowPathSpeedStance, Vehicle:FollowPath

 |

**
ACT_GRAB_OBJECT
**

 |
AI:AIGrabObject

 |

**
ACT_GOTO
**

 |
AI:AIGoto, AI:AIGotoSpeedStance, and the AI Debugger when the user clicks the middle mouse button.

 |

**
ACT_JOINFORMATION
**

 |
AI:AIFormationJoin

 |

**
ACT_SHOOTAT
**

 |
AI:AIShootAt

 |

**
ACT_USEOBJECT
**

 |
AI:AIUseObject

 |

**
ACT_VEHICLESTICKPATH
**

 |
Vehicle:StickPath

 |

**
ACT_WEAPONDRAW
**

 |
AI:AIWeaponDraw

 |

**
ACT_WEAPONHOLSTER
**

 |
AI:AIWeaponHolster

 |

**
ACT_WEAPONSELECT
**

 |
AI:AIWeaponSelect

 |

##
Other Signals

##
Forced Execute

Name

 |

**
OnForcedExecute
**

 |

**
OnForcedExecuteComplete
**

 |

##
Animation

Name

 |

**
AnimationCanceled
**

 |

##
Game

Name

 |

**
OnFallAndPlay
**

 |

##
Vehicle-related

Name

 |
Description

 |

**
OnActorSitDown
**

 |
Actor has entered a vehicle

 |

##
Squads

Name

 |

**
OnSomebodyDied
**

 |

**
OnBodyFallSound
**

 |

**
OnBodyFallSound
**

 |

**
OnUnitDied
**

 |

**
OnSquadmateDied
**

 |

**
OnPlayerTeamKill
**

 |

**
OnUnitBusy
**

 |

**
OnPlayerDied
**

 |

Name

 |
Parameters

 |
Description

 |

**
OnFriendInWay
**

 |
sender

 |
AI is trying to fire and another friendly AI is on his line of fire

 |

**
URPRISE_ACTION
**

 |
 |
 |

**
OnActionDone
**

 |
data

 |
AI action of this agent was finished. data.ObjectName is the action name, data.iValue is 0 if action was cancelled or 1 if it was finished normally, data.id is the entity id of "the object" of the AI action

 |

[Perception](#perception)
[Weapon-related](#weapon-related)
[Navigation](#navigation)
[Tactics](#tactics)
[Groups](#groups)
[Flow Graph](#flow-graph)
[Other Signals](#other-signals)
