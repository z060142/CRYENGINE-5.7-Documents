# Vehicle Entity

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/29798905
- Page ID: 29798905
- Breadcrumb: Physics > Vehicles Basics (GameSDK) > Vehicle Entity
- Parent: Vehicles Basics (GameSDK)

## Content

### Overview

There is a basic entity for each type of movement (land, sea, and air). Each entity type can be tweaked so that it is possible to simulate any kind of drivable machine.

The vehicle entity tool can be found in the **Rollup Bar** > ** Entity** > ** Vehicles**.

Having different types of vehicles makes levels more fun to play as they provide new ways of navigating terrain and allow the use of vehicle weapons game play.

### Entity Properties2

Param | Description
--- | ---
**AutoDisable** | If set to false AI is never disabled, no matter how far it is from the player. Should be used for special cases like patrols coming from far away. Normally, this should be true (default value).
**Behavior** | Sets the starting behavior of the AI. The behavior "job_standidle" is the default one, and should be used most of the time, as designers can set certain actions for the AI using the flowgraph.
**CircularPath** |
**FormationType** |
**groupid** |
**PathName** |
**triggerRadius** |
AITerritoryAndWave |
**Territory** |
**Wave** |
Interest |
**Action** |
**Interesting** |
**InterestLevel** |
**OverrideArchetype** |
**Pause** |
**Radius** |
**Shared** |

### Entity Properties

Param | Description
--- | ---
**AutoGenAIHidePts** |
**BehaviorSelectionTree** |
**character** |
**commrange** |
**DamageOnFlipped** |
**DisableEngine** |
**followDistance** |
**Frozen** |
**FrozenModel** |
**HeavyObject** |
**HidesPLayer** |
**leaderName** |
**Modification** | Sets vehicle to use a modification version, created in the vehicle script.
**NavigationType** | For use with [Multi-layer Navigation](../../AI%20and%20Navigation/AI%20Overview/Navigation%20(MNM).md).
**Paint** | Sets vehicle to use a paint version, created in the vehicle script.
**ProvideAICover** |
**SmartObjectClass** |
**SpawnedEntityName** |
**SpeciesHostility** |
**teamName** |
Interest |
**Action** |
**Interesting** |
**InterestLevel** |
**Pause** |
**Radius** |
**Shared** |
**vOffset** |
Perception |
**audioScale** | *Deprecated*
**camoScale** | "How well others see me". Determines how visible the AI is. Scales visibility when other AI's are looking at this agent. For camouflaged agents this value should be less than 1. The more stealthy/camouflage this agent is, the smaller this value should be. 0.0 will make this AI invisible.
**collisionReactionScale** | *Deprecated*
**FOVPrimary** | Normal field of view of the AI.
**FOVSecondary** | Peripheral field of view of the AI.
**heatScale** | *Deprecated*
**minAlarmLevel** | *Deprecated*
**persistence** | This parameter controls how often targets can be switched. The value corresponds to minimum amount of time the agent will hold acquired target before selecting another one.
**sightrange** | How far away the AI can see enemies. Edge to edge radius around vehicle, measured in meters.
**sightrangeVehicle** | Same as **sightrange** but for targets of vehicle type.
**stanceScale** | Controls how the current height of the target affects visibility of the target. Height of target changes with stance change (prone/crouch/stand).
**stuntReactionTimeOut** | *Deprecated*
**ThermalVision** | *Deprecated*
**velBase** | Movement related parameter. Current visibility priority value of the target gets multiplied by (velBase + velScale CurrentVel^2). Allows creating AI agents that are able to see only moving targets, or only static targets, and all values in between.
**velScale** | Movement related parameter, see velBase.
**classThreat** (TargetTracks) |
**targetLimit** (TargetTracks) |
Respawn |
**Abandon** | Specifies if the vehicle should explode after a specified amount of time (used to avoid too many abandoned vehicles, which waste CPU resources).
**AbandonTimer** | Specifies in seconds when the abandon feature should be executed.
**Respawn** | Respawns another vehicle.
**Timer** | Specifies when the vehicle should be respawned.
**Unique** | Makes each vehicle entity unique.
