# Turret Entity

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/29796949
- Page ID: 29796949
- Breadcrumb: Editor Tools > Level Editor Tab > Create Object > Legacy Entities > Turret Entity
- Parent: Legacy Entities

## Content

##
Overview

The Turret Entity in CRYENGINE allows you to setup static, or dynamic turrets which can be used for defense or offense gameplay. Protect an important location or used in an AI assault against the player, there are plenty of tunable options for the Turret entity to get it to do what you want!

##
Parameters

Param

 |
Description

 |

**
CloakDetectionDistance
**

 |
 |

**
groupId
**

 |
 |

**
Faction
**

 |
 |

**
Model
**

 |
Define the CDF model to be used for the turret.

 |

**
PrimaryWeapon
**

 |
Primary weapon script that the turret will use for firing.

 |

**
PrimaryWeaponFOVDegrees
**

 |
Field of View for the primary weapon.

 |

**
PrimaryWeaponJointName
**

 |
 |

**
PrimaryWeaponRangeCheckOffset
**

 |
 |

**
TurretState
**

 |
 |

**
Usable
**

 |
Specifies if the object is usable.

 |

**
UsableOnlyOnce
**

 |
If true, the object can only be used once.

 |

**
UseMessage
**

 |
Display a message when the object is in range of the player to be used. Can be a localization string.

 |

AutoAimTargetParams

 |
 |

**
fallbackOffset
**

 |
 |

**
innerRadius
**

 |
 |

**
outRadius
**

 |
 |

**
physicsTargetBone
**

 |
 |

**
primaryTargetBone
**

 |
 |

**
secondaryTargetBone
**

 |
 |

**
snapRadius
**

 |
 |

**
snapRadiusTagged
**

 |
 |

Behavior

 |
 |

**
MaxStopFireSeconds
**

 |
 |

**
MinStopFireSeconds
**

 |
 |

**
AimVerticalOffset
**

 |
 |

**
MaxStartFireDelaySeconds
**

 |
 |

**
MinStartFireDelaySeconds
**

 |
 |

**
PredictionDelaySeconds
**

 |
 |

**
ReevaluateTargetSeconds
**

 |
 |

**
BackToSearchSeconds
**

 |
 |

**
DampenVelocityTimeSeconds
**

 |
 |

**
LastVelocityValueWeight
**

 |
 |

**
Distance
**

 |
 |

**
Height
**

 |
 |

**
RandomOffsetRange
**

 |
 |

**
RandomOffsetSeconds
**

 |
 |

**
YawDegreesHalfLimit
**

 |
 |

**
YawDegreesPerSecond
**

 |
 |

**
LimitPauseSeconds
**

 |
 |

**
RandomOffsetRange
**

 |
 |

**
RandomOffsetSeconds
**

 |
 |

**
IsThreat
**

 |
 |

Damage

 |
 |

**
BodyDamage
**

 |
Location for the BodyDamage script file.

 |

**
BodyDamageParts
**

 |
Location for the BodyDamageParts script file.

 |

**
BodyDestructibility
**

 |
Location for the Destructability script file.

 |

**
health
**

 |
Sets the total damage the entity can take before it is destroyed.

 |

Laser

 |
 |

**
DotEffect
**

 |
Particle to be used for the laser dot effect.

 |

**
Enabled
**

 |
Set to false if you don't want to use a laser dot effect.

 |

**
Geometry
**

 |
Geometry file for the laser beam effect.

 |

**
JointName
**

 |
 |

**
OffsetX
**

 |
Offset the laser effect in X/Y/Z space.

 |

**
OffsetY
**

 |
Offset the laser effect in X/Y/Z space.

 |

**
OffsetZ
**

 |
Offset the laser effect in X/Y/Z space.

 |

**
Range
**

 |
Maximum Range for the laser effect to be displayed.

 |

**
ShowDot
**

 |
Specify if you want to show the dot effect or not (while still displaying the geometry).

 |

**
SourceEffect
**

 |
Particle to be used if the laser targets the player in the eyes, typically a glare/blinding type of effect.

 |

**
Thickness
**

 |
Overall thickness of the laser effect.

 |

Mannequin

 |
 |

**
AnimationDatabase
**

 |
Location for the .adb Mannequin file.

 |

**
ControllerDef
**

 |
Location for the ControllerDef Mannequin file.

 |

RateOfDeath

 |
 |

**
attackRange
**

 |
Distance used to calculate (in conjunction with some CVars from the AI system) the zone a target is in (kill zone, near combat, far combat)

 |

**
hitMaxRange
**

 |
Multiplier ranges used when calculating the random target offset. Different values for when we should be missing or hitting the target.

 |

**
hitMinRange
**

 |
Multiplier ranges used when calculating the random target offset. Different values for when we should be missing or hitting the target.

 |

**
hitOffsetIntervalSeconds
**

 |
Time in seconds before each update of the target offset. Different values for when we should be missing or hitting the target.

 |

**
missMaxRange
**

 |
Multiplier ranges used when calculating the random target offset. Different values for when we should be missing or hitting the target.

 |

**
missMineRange
**

 |
Multiplier ranges used when calculating the random target offset. Different values for when we should be missing or hitting the target.

 |

**
missOffsetIntervalSeconds
**

 |
Time in seconds before each update of the target offset. Different values for when we should be missing or hitting the target.

 |

Sound

 |
 |

**
Alerted
**

 |
Sound to be used if the turret locates the player.

 |

**
AlertedTimeoutSeconds
**

 |
Time, in seconds, for the turret to forget they spotted the player.

 |

**
GameHintName
**

 |
 |

**
HorizontalJointName
**

 |
 |

**
HorizontalLoopingSoundDelaySeconds
**

 |
Time, in seconds, to delay the horizontal movement loop sound.

 |

**
HorizontalMovementLoop
**

 |
Sound to be used and during the horizontal movement action.

 |

**
HorizontalMovementStart
**

 |
Sound to be used when starting the horizontal movement action.

 |

**
HorizontalMovementStop
**

 |
Sound to be used when stopping the horizontal movement action.

 |

**
LockedOnTarget
**

 |
Sound to be used if the turret successfully locks onto the player.

 |

**
LockedOnTargetSeconds
**

 |
 |

**
MovementStartSoundThresholdDegreesSecond
**

 |
 |

**
MovementStopSoundThresholdDegreesSecond
**

 |
 |

**
VerticalJointName
**

 |
 |

**
VerticalLoopingSoundDelaySeconds
**

 |
Time, in seconds, to delay the vertical movement loop sound.

 |

**
VerticalMovementLoop
**

 |
Sound to be used and during the vertical movement action.

 |

**
VeritcalMovementStart
**

 |
Sound to be used when starting the vertical movement action.

 |

**
VerticalMovementStop
**

 |
Sound to be used when stopping the vertical movement action.

 |

Vision

 |
 |

**
CloakDetectionDistance
**

 |
**
DEPRECATED
**
 - Minimum distance the player can get from the turret before detection, while in cloak.

 |

**
EyeFov
**

 |
Field of View for targeting.

 |

**
EyeJointName
**

 |
 |

**
EyeRange
**

 |
Maximum range, in meters, that the turret can see through the "eye".

 |

**
RadarFov
**

 |
Field of View for radar.

 |

**
RadarRange
**

 |
Maximum range, in meters, that the turret can detect enemies via radar.

 |

**
RadarVerticalOffset
**

 |
 |

[#parameters](
Parameters
)
