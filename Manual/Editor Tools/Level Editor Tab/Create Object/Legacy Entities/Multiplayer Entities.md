# Multiplayer Entities

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/29796939
- Page ID: 29796939
- Breadcrumb: Editor Tools > Level Editor Tab > Create Object > Legacy Entities > Multiplayer Entities
- Parent: Legacy Entities

## Content

##
Overview

Multiplayer entities are used to set up the game rules within a multiplayer level. The multiplayer entities can be found in the
**
Create Object → Legacy Entities → Multiplayer
**
.

##
AmmoCrateMP

Property

 |
Description

 |

**
audioSignal
**

 |

 |

**
Enabled
**

 |
Specifies if this Ammo crate is enabled or not.

 |

**
GroupId
**

 |
**
Deprecated
**

 |

**
ModelOverride
**

 |
Override the default model (*.cgf) specified in the script here.

 |

**
NumUsagesPerPlayer
**

 |
How many times a player can use the Ammo Crate.

 |

**
teamId
**

 |
Setting this to 0 = teams are ignored.

 |

**
Usable
**

 |
See
[/docs/static/engines/cryengine-3/categories/1114113/pages/1048651](
Common Entity Parameters
)
.

 |

**
UseMessage
**

 |
See
[/docs/static/engines/cryengine-3/categories/1114113/pages/1048651](
Common Entity Parameters
)
.

 |

**
FragGrenades
**

 |
Specify the amount of Frag grenades to supply when used.

 |

**
GiveClips
**

 |
Specify the amount of Magazines to supply when used.

 |

**
RefillWeaponAmmo
**

 |
Refill with the currently selected weapons ammo.

 |

**
RefillWithCurrentGrenades
**

 |
Rather than just giving frags.

 |

##
AssaultIntel

Property

 |
Description

 |

**
ControlHeight
**

 |

 |

**
ControlOffsetZ
**

 |

 |

**
ControlRadius
**

 |

 |

**
DebugDraw
**

 |

 |

**
ModelOverride
**

 |

 |

**
teamName
**

 |

 |

##
BTBBombBase

Property

 |
Description

 |

**
Model
**

 |

 |

**
ModelSubObject
**

 |

 |

**
Radius
**

 |

 |

##
BTBBombSite

Property

 |
Description

 |

**
Model
**

 |

 |

**
ModelSubObject
**

 |

 |

**
Radius
**

 |

 |

**
teamName
**

 |

 |

**
Damage
**

 |

 |

**
Decal
**

 |

 |

**
DecalScale
**

 |

 |

**
Effect
**

 |

 |

**
EffectScale
**

 |

 |

**
Pressure
**

 |

 |

**
Radius
**

 |

 |

**
Direction
**

 |

 |

##
CTFBase

Property

 |
Description

 |

**
ModelOverride
**

 |

 |

**
ModelSubObject
**

 |

 |

**
Radius
**

 |

 |

**
teamName
**

 |

 |

##
CameraPoint

Property

 |
Description

 |

**
Enabled
**

 |

 |

**
PitchLimits
**

 |

 |

**
YawLimits
**

 |

 |

##
DangerousRigidBody

Property

 |
Description

 |

**
CanTriggerAreas
**

 |
See
[/docs/static/engines/cryengine-5/categories/23756816/pages/29796943#PhysicsEntities-BasicEntity](
BasicEntity
)
.

 |

**
CurrentlyDealingDamage
**

 |
If true the entity will start in a state where it deals damage on contact, otherwise it must first be activated using the ‘MakeDangerous’ event in Flowgraph.

 |

**
DamagesPlayerOnCollisionSP
**

 |
If true the entity will deal damage on contact with the player (in single player only).

 |

**
DamageToDeal
**

 |
Amount of damage to deal.

 |

**
DmgFactorWhenCollidingAI
**

 |
See
[/docs/static/engines/cryengine-5/categories/23756816/pages/29796943#PhysicsEntities-BasicEntity](
BasicEntity
)
.

 |

**
DoesFriendlyFireDamage
**

 |
**
Deprecated
**

 |

**
ExcludeCover
**

 |
See
[/docs/static/engines/cryengine-5/categories/23756816/pages/29796943#PhysicsEntities-BasicEntity](
BasicEntity
)
.

 |

**
Faction
**

 |
See
[/docs/static/engines/cryengine-5/categories/23756816/pages/29796951](
Common Entity Parameters
)
.

 |

**
HeavyObject
**

 |
See
[/docs/static/engines/cryengine-5/categories/23756816/pages/29796951](
Common Entity Parameters
)
.

 |

**
InteractLargeObject
**

 |
See
[/docs/static/engines/cryengine-5/categories/23756816/pages/29796951](
Common Entity Parameters
)
.

 |

**
MissionCritical
**

 |
See
[/docs/static/engines/cryengine-5/categories/23756816/pages/29796943#PhysicsEntities-BasicEntity](
BasicEntity
)
.

 |

**
Model
**

 |
Defines the model to be used.

 |

**
Pickable
**

 |
See
[/docs/static/engines/cryengine-5/categories/23756816/pages/29796951](
Common Entity Parameters
)
.

 |

**
Serialize
**

 |
See
[/docs/static/engines/cryengine-5/categories/23756816/pages/29796951](
Common Entity Parameters
)
.

 |

**
SmartObjectClass
**

 |
See
[/docs/static/engines/cryengine-5/categories/23756816/pages/29796951](
Common Entity Parameters
)
.

 |

**
TimeBetweenHits
**

 |
Delay (in seconds) after dealing damage before entity can deal more damage.

 |

**
Usable
**

 |
See
[/docs/static/engines/cryengine-5/categories/23756816/pages/29796951](
Common Entity Parameters
)
.

 |

**
UseMessage
**

 |
See
[/docs/static/engines/cryengine-5/categories/23756816/pages/29796951](
Common Entity Parameters
)
.

 |

**
UsedAsDynamicObstacle
**

 |
See
[/docs/static/engines/cryengine-5/categories/23756816/pages/29796943#PhysicsEntities-RigidBodyEx](
RigidBodyEX
)
.

 |

Health

 |

 |

**
Invulnerable
**

 |
See
[/docs/static/engines/cryengine-5/categories/23756816/pages/29796951](
Common Entity Parameters
)
.

 |

**
MaxHealth
**

 |
See
[/docs/static/engines/cryengine-5/categories/23756816/pages/29796951](
Common Entity Parameters
)
.

 |

**
OnlyEnemyFire
**

 |
See
[/docs/static/engines/cryengine-5/categories/23756816/pages/29796951](
Common Entity Parameters
)
.

 |

MultiplayerOptions

 |

 |

**
Networked
**

 |
See
[/docs/static/engines/cryengine-5/categories/23756816/pages/29796951](
Common Entity Parameters
)
.

 |

**
ActivateOnDamage
**

 |
If true physics will activate when damage is received.

 |

**
CanBreakOthers
**

 |
See
[/docs/static/engines/cryengine-5/categories/23756816/pages/29796951](
Common Entity Parameters
)
.

 |

##
EnvironmentalWeapon

Property

 |
Description

 |

**
classification
**

 |

 |

**
collisionDamageScale
**

 |

 |

**
damageable
**

 |

 |

**
explosionMinDamageToDestroy
**

 |

 |

**
idleKillTime
**

 |

 |

**
initialHealth
**

 |

 |

**
InitiallyRooted
**

 |

 |

**
ModelOverride
**

 |

 |

**
Pickable
**

 |
See
[/docs/static/engines/cryengine-5/categories/23756816/pages/29796951](
Common Entity Parameters
)
.

 |

**
RagdollPostMeleeImpactSpeed
**

 |

 |

**
RagdollPostThrowImpactSpeed
**

 |

 |

**
RootedAngleMax
**

 |

 |

**
RootedAngleMin
**

 |

 |

**
shieldsFromExplosionConeAngle
**

 |

 |

**
szGrabAnimTagOverride
**

 |

 |

**
szMFXLibrary
**

 |

 |

**
szRootedGrabAnimTagOverride
**

 |

 |

**
szUseMessage
**

 |

 |

**
States
**

 |

 |

##
ExtractionPoint

Property

 |
Description

 |

**
ModelOverride
**

 |

 |

**
OpenRange
**

 |

 |

**
Radius
**

 |

 |

##
ExtractionWeaponSpawn

Property

 |
Description

 |

**
ModelOverride
**

 |

 |

**
Radius
**

 |

 |

##
ForbiddenArea

**
Property
**

 |
**
Description
**

 |

**
DamagePerSecond
**

 |
Specifies the amount of damage per second taken by the player when he is inside the forbidden area.

 |

**
DamageType
**

 |

 |

**
Delay
**

 |
Specifies the delay in seconds until the player takes damage inside the forbidden area.

 |

**
Enabled
**

 |
Specifies if the forbidden area is enabled or not.

 |

**
InfiniteFall
**

 |

 |

**
overrideTimerLength
**

 |

 |

**
ResetsObjects
**

 |

 |

**
Reversed
**

 |
Specifies if the player takes damage inside or outside of the area (inside {{ reversed false, outside }} reversed true).

 |

**
ShowWarning
**

 |
Specifies if a warning message is displayed on the HUD when a player enters a forbidden area. (If a delay is set, there will be also a countdown in this message).

 |

**
teamName
**

 |
Specifies to which team the ForbiddenArea belongs (Team US {{ black, Team NK }} tan, neutral = leave field free) The opposite team will take damage when a teamname is set. If no teamname is set, every player will take damage.

 |

MultiplayerOptions

 |

 |

**
Networked
**

 |
See
[/docs/static/engines/cryengine-5/categories/23756816/pages/29796951](
Common Entity Parameters
)
.

 |

##
SpawnGroup

**
Property
**

 |
**
Description
**

 |

**
Default
**

 |
Specifies if this Spawn Group is the default spawnpoint or not. Players would initially spawn there.

 |

**
Enabled
**

 |
Specifies if this Spawn Group is enabled or not.

 |

**
Model
**

 |
Specifies the model used for the Spawn Group.

 |

**
teamName
**

 |
Specifies to which team the Spawn Group belongs on game start (Team US {{ black, Team NK }} tan, neutral = leave field free).

 |

##
SpectatorPoint

**
Property
**

 |
**
Description
**

 |

**
Enabled
**

 |
Specifies if the spectator point is enabled or not.

 |

##
TagNamePoint

**
Property
**

 |
**
Description
**

 |

**
Enabled
**

 |
 |

##
TeamRandomSoundVolume

This entity is similar to the RandomSoundVolume entity, in the
[/docs/static/engines/cryengine-3/categories/1114113/pages/1048826](
Sound Entities (deprecated)
)
 page, except that it will play a different sound, according to which team owns the entity in a multiplayer game.

**
Property
**

 |
**
Description
**

 |

**
DiscRadius
**

 |
Defines the size of circle around the player at which distance the sound gets spawned.

 |

**
Enabled
**

 |
When set, the object will be enabled on level startup.

 |

**
IgnoreCulling
**

 |
When set, the sound will not be affected by visarea attenuation.

 |

**
IgnoreObstruction
**

 |
When set, sound will pass through geometric objects.

 |

**
LogBattleValue
**

 |
When set, the script will output debug information about the current battle noise level to the console.

 |

**
MaxWaitTime
**

 |
Defines the maximal time to wait before re-triggering the sound.

 |

**
MinWaitTime
**

 |
Defines the minimal time to wait before re-triggering the sound. Must be smaller than MaxWaitTime.

 |

**
RandomPosition
**

 |
When set, each new spawned sound is randomly placed on the discs defined with DiscRadius. The location of the script is used otherwise.

 |

**
SensitiveToBattle
**

 |
When set, the battle noise around the player is passed to the sound event. If this event has a "battle" parameter.

 |

**
TeamSound1 - TeamSound4
**

 |
 |

**
Name
**

 |
Sound to play for this team.

 |

**
teamName
**

 |
Name of this team.

 |

##
TeamSoundSpot

This entity is similar to the SoundSpot entity in the
[/docs/static/engines/cryengine-3/categories/1114113/pages/1048826](
Sound Entities (deprecated)
)
 page, except that it will play a different sound, according to which team owns the entity in a multiplayer game.

**
Property
**

 |
**
Description
**

 |

**
Enabled
**

 |
When set, the object will be enabled on level startup.

 |

**
IgnoreCulling
**

 |
When set, the sound will not be affected by visarea attenuation.

 |

**
IgnoreObstruction
**

 |
When set, sound will pass through geometric objects.

 |

**
MaxWaitTime
**

 |
Defines the maximal time to wait before re-triggering the sound.

 |

**
MinWaitTime
**

 |
Defines the minimal time to wait before re-triggering the sound. Must be smaller than MaxWaitTime.

 |

**
Once
**

 |
When set, the sound spot will only play once.

 |

**
Play
**

 |
When set, the entity will play on level startup.

 |

**
PlayOnX
**

 |

 |

**
PlayOnY
**

 |

 |

**
PlayOnZ
**

 |

 |

**
PlayRandom
**

 |

 |

**
Radius
**

 |

 |

**
TeamSound1 - TeamSound4
**

 |
 |

**
Name
**

 |
Sound to play for this team.

 |

**
teamName
**

 |
The name of the team.

 |

[#ammocratemp](
AmmoCrateMP
)
[#assaultintel](
AssaultIntel
)
[#btbbombbase](
BTBBombBase
)
[#btbbombsite](
BTBBombSite
)
[#ctfbase](
CTFBase
)
[#camerapoint](
CameraPoint
)
[#dangerousrigidbody](
DangerousRigidBody
)
[#environmentalweapon](
EnvironmentalWeapon
)
[#extractionpoint](
ExtractionPoint
)
[#extractionweaponspawn](
ExtractionWeaponSpawn
)
[#forbiddenarea](
ForbiddenArea
)
[#spawngroup](
SpawnGroup
)
[#spectatorpoint](
SpectatorPoint
)
[#tagnamepoint](
TagNamePoint
)
[#teamrandomsoundvolume](
TeamRandomSoundVolume
)
[#teamsoundspot](
TeamSoundSpot
)
