# AI Human

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/26215396
- Page ID: 26215396
- Breadcrumb: AI and Navigation > AI Overview > AI (NPC) > AI Human
- Parent: AI (NPC)

## Content

[Image: /docs/static/attachments/29933198]

##
Overview

This page covers the properties and options available for the
Entity -> AI -> Characters -> Human
 entity, which is the base character included in the CRYENGINE SDK.

##
Sections

[#sections](
Sections
)
[#human-entity-reference](
Human Entity Reference
)
[#entity-properties2](
Entity Properties2
)
[#entity-properties](
Entity Properties
)

##
Human Entity Reference

The Human entity is used for AI characters. For reference, this entity used to be called "Grunt". The Entity has property options like Sight, Accuracy and Faction, so that designers can create custom enemy or friendly characters.

An AI Human entity has built in AI behaviors (via the ModularBehaviorTree), meaning they can be placed into the level with relatively little behavioral scripting and still function.

Basic functions like weapon firing are built into the entity scripts. Advanced behavioral scripting can be set up using Flow Graph.

Property

 |
Description

 |

##
Entity Properties2

 |

Alarmed

 |
When ticked, AI reacts faster to enemies. (Attention! They will still remain in Idle pose when spawned, so it's not the same as being alerted.)

 |

AutoDisable

 |
If set to false – AI is never disabled, no matter how far it is from the player. Should be used for special cases - like patrols coming from far away, etc... Normally, this should be true (default value).

 |

groupID

 |
id of the group for this AI, used by some group behaviors.

 |

SmartObjectClass

 |
Smart object class(es) assigned to this entity.

 |

Variation

 |
Select the variation of the model you want to use.

 |

AI

 |
 |

GoBackToStartOnIdle

 |
When ticked, AI will go back to the position where they first started.

(Warning! If you have this checked for humans coming into the scene in vehicles, they will try to go back to their initial spawn position as soon as they leave the vehicle.)

 |

Gunner

 |
Deprecated

 |

HostileIfAttacked

 |
If set to true, an AI character that belongs to a friendly faction will turn hostile if attacked.

 |

AI Territory And Wave

 |
 |

Territory

 |
Assign the AI to a territory from a list of available territories.

 |

Wave

 |
Assign the AI to a wave from a list of available waves attached to selected territory.

 |

Interest

 |
 |

Angle

 |
The "Vision Cone" that AI will search, for objects marked as interesting using the interest system.

 |

Interested

 |
Set to true to make the AI aware of Interest Objects or false to have the AI ignore Interest Objects.

 |

MinInterestLevel

 |
The minimum Object Interest level the AI will consider. Any objects set with an interest level lower than this value will be ignored by the AI.

 |

OverrideArchetype

 |
Turns on to have those values override archetype values.

 |

Readability

 |

 |

IgnoreAnimations

 |
When triggering communications (from inside the AI system or manually via flow graph) the animations will be ignored for the communications. (Voice will still play as intended.)

 |

IgnoreVoice

 |
When triggering communications (from inside the AI system or manually via flow graph) the voice will be ignored for the communications. (Animations will still play as intended.)

 |

OverrideArchetype

 |
Turns on to have those values override archetype values.

 |

##
Entity Properties

 |
 |

awarenessOfplayer

 |
This needs to be set for certain characters, so that they can react when the player is looking at them. This represents the timeout before AI starts to react on player looking.

When used (not 0) normally should be 1 (meaning one second delay), but can be any value. Introduces some extra ray-trace checks, so should not be used unless really needed

 |

BehaviorSelection

 |
Deprecated

 |

BehaviorSelectionTree

 |
This is the main property used to set the behavior of the AI. Example AI behaviors are included in the SDK.

 |

Behavior

 |
Deprecated

 |

character

 |
Deprecated

 |

ColliderMode

 |
Sets Physical collision properties on the AI.

 |

CommConfig

 |
Name of communication configuration (see
[/docs/static/engines/cryengine-3/categories/1638401/pages/1933379](
AI Communication
)
).

 |

commrange

 |
Deprecated

 |

EquipmentPack

 |
The inventory of the enemy needs to be selected here. Usually there is a weapon inside the equipment pack so the AI can shoot. Note: The AI has unlimited ammo.

 |

Faction

 |
Specify the
[/docs/static/engines/cryengine-3/categories/1638401/pages/13205553](
Faction
)
 which the AI belongs to.

 |

FactionHostility

 |
Switch on/off the faction hostility settings set on the AI. If this is set to false the AI will not react to other AI entities or players.

 |

FmodCharacterTypeParam

 |
See
[/docs/static/engines/cryengine-3/categories/1114113/pages/11240792](
Character Type Filter Parameter
)
 for more information.

 |

HitDeathReactionsParamsDataFile

 |
Points to the file describing how an AI should react to impacts and death.

 |

Invulnerable

 |
Makes AI invulnerable.

 |

Model

 |
The character 3D model used for rendering.

 |

ModelVariations

 |
Specifies how many model variations an archetype has.

 |

ModularBehaviorTree

 |
Name of behavior tree.

 |

NavigationType

 |
Select a suitable size of the entity, for use with
[/docs/static/engines/cryengine-3/categories/1114113/pages/1048689](
MNM
)
.

 |

OverrideAllowLookAimStrafing

 |
Override allowLookAimStrafing flag from base actor parameters (see Scripts\Entities\AI\Characters\Human_x.lua).

When allowLookAimStrafing is enabled the actor’s body will turn slightly towards the look direction.

 |

physicMassMult

 |
Indicates the Mass multiplier.

 |

SmartObjectClass

 |
Smart Object class.

 |

SpawnedEntityName

 |
Name to be used when this entity is used as a prototype for spawning.

 |

Spawner

 |
Deprecated

 |

TagList

 |
List of CryMannequin tags to set for this entity.

 |

Usable

 |
If Usable is True, the player can click the Use button on this AI.

 |

UseFacialFrameRateLimiting

 |
Set to limit frame rate of facial animations.

 |

UseMessage

 |
Deprecated - Text to be displayed on screen to show that the Use button can be used there.

 |

useSpecialMovementTransitions

 |
Enable custom movement transitions (see Libs/MovementTransitions/MovementTransitions_Human.xml).

 |

Voice

 |
Sound pack used for this character, american human, english human etc.

 |

AI

 |

 |

DeathSound

 |
Sound effect to play when character dies.

 |

PlayDeathSound

 |
Enable/disable death sound effect. Please note: a known issue causes death sounds to play regardless of the value of PlayDeathSound, but you can work around this by simply not setting DeathSound.

 |

UseRadioChatter

 |
Enable/disable radio chatter. Radio chatter plays sounds through the character's intercom at random when other characters are nearby.

 |

AIBehaviorFlags

 |

 |

Grenadier

 |
Deprecated

 |

Sniper

 |
Deprecated

 |

CharacterSounds

 |

 |

foleyEffect

 |
Foley signal effect name.

 |

footstepEffect

 |
Footstep mfx library to use.

 |

FootstepGearEffect

 |
This plays a sound from MaterialFX.

 |

footstepIndGearAudioSignal_Run

 |
This directly plays the specified audiosignal on every footstep of the Run animation cycle.

 |

footstepIndGearAudioSignal_Walk

 |
This directly plays the specified audiosignal on every footstep of the Walk animation cycle.

 |

remoteFootstepEffect

 |
Footstep MaterialFX library to use for the 3rd person character.

 |

Damage

 |
 |

BodyDamage

 |
Specifies XML file containing information about BodyDamage.

 |

BodyDamageParts

 |
Specifies XML file containing information about BodyDamage.

 |

BodyDestructibility

 |
Specifies XML file containing information about BodyDestructibility.

 |

CanFall

 |
Can use fall and play (fall down in ragdoll mode and then stand up.)

 |

FallSleepTime

 |
How long does it stay in fall-and-play before waking up.

 |

health

 |
Initial amount of health.

 |

heatAbsobsion

 |
Deprecated

 |

heatDissipation

 |
Deprecated

 |

LogDamages

 |
Allows for logging the damage in the log file.

 |

minHeatDamage

 |
Deprecated

 |

Interest

 |
 |

Angle

 |
The "Vision Cone" that AI will search, for objects marked as interesting using the interest system.

 |

Interested

 |
Set to true to make the AI aware of Interest Objects or false to have the AI ignore Interest Objects.

 |

MinInterestLevel

 |
The minimum Object Interest level the AI will consider. Any objects set with an interest level lower than this value will be ignored by the AI.

 |

Perception

 |
 |

audioScale

 |
Scaling audio perception of this AI.

 |

cloakMaxDistCrouchedAndMoving

 |
Deprecated

 |

cloakMaxDistCrouchedAndStill

 |
Deprecated

 |

cloakMaxDistMoving

 |
Deprecated

 |

cloakMaxDistStill

 |
Deprecated

 |

collisionReactionScale

 |
Scales explosions radius for AI to receive "OnExposedToExplosion" signal. Also affects distances for AI reaction on players action (PlayerStuntActions).

 |

config

 |
New Perception System. Select the perception configuration file to use for the AI.

 |

FOVPrimary

 |
Normal field of view (no peripheral vision) of this AI, in degrees. Negative value would mean unlimited FOV. Angular visibility multiplier fades from 1 (inside of FOVPrimary) to 0 (outside of FOVSecondary).

 |

FOVSecondary

 |
"Peripheral" field of view of this AI. Negative value means unlimited FOV.

 |

IsAffectedByLight

 |
Indicates if the AI's detection of danger is based on Light Level. Meaning a target would be harder to detect if it is in a dark place, and vice-versa. See
[/docs/static/engines/cryengine-3/categories/1114113/pages/17829009](
AI Perception
)
.

 |

minAlarmLevel

 |
Value between 0 and 1, indicating the minimum alarm level. Default is 0. If the AI needs to be highly alerted from the beginning, this should be set to a value larger than 0.

 |

minDistanceToSpotDeadBodies

 |
Actor will be alerted to dead bodies within this range.

 |

persistence

 |
This parameter controls how often targets can be switched. The value corresponds to the minimum amount of time the agent will hold acquired target before selecting another one. Default value is 0.

 |

sightrange

 |
How far this AI can see enemies. Targets out of sight range cannot be seen; visibility of a target fades as a quadratic function.

 |

sightrangeVehicle

 |
Same as sightrange but for targets of vehicle type.

 |

stanceScale

 |
Controls how the current height of the target affects visibility of this target. Height of target changes with stance change (prone/crouch/stand).

 |

stuntReactionTimeOut

 |
Controls how long the attention target have had to be invisible to make the player stunts effective again. Default value is 3 sec/

 |

TargetTracks

 |
 |

classThreat

 |
Indicates the Initial class threat (Track System term) value for the AI.

 |

targetLimit

 |
Indicates the number of agents who can target the AI at any given time (0 for infinite).

 |

Physics

 |

 |

CollisionFiltering

 |
Configure entity’s collision type and ignore collisions with specific classes of physics object.

 |

PlayerInteractions

 |

 |

CanBeGrabbed

 |
If true AI can be grabbed.

 |

GrabType

 |
What kind of grabbing move (for alien or human, etc).

 |

StealthKill

 |
Can be stealth killed by player.

 |

RateOfDeath

 |
 |

accuracy

 |
Indicates the accuracy of the AI's firing (1 = 100 %) when in attackrange.

This is tied to and affected by the Rate of Death system. If an AI had an Accuracy of 0.5 it will double the base time (=AI_RODAliveTime) the player can survive under fire.

 |

attackrange

 |
Indicates in meters how close the AI needs to be from its target before it can fire with accuracy.

This is tied to and affected by the Rate of Death system: combat zone distance = attackrange x AI_RODCombatRangeMod (CVar)

 |

reactionTime

 |
Indicates how long it will take between the AI getting alerted and engaging its target.

 |

Readability

 |
 |

IgnoreAnimations

 |
Turn On/Off AI readability animations that convey AI events and states to the player.

 |

IgnoreVoice

 |
Turn On/Off AI readability audio that convey AI events and states to the player.

 |

Rendering

 |

 |

WrinkleMap

 |
See:
[/docs/static/engines/cryengine-3/categories/1114113/pages/1310791](
Wrinkle Map Setup
)

 |
