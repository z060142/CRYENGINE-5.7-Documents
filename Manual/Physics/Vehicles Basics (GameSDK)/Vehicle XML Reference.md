# Vehicle XML Reference

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/29798907
- Page ID: 29798907
- Breadcrumb: Physics > Vehicles Basics (GameSDK) > Vehicle XML Reference
- Parent: Vehicles Basics (GameSDK)

## Content

This page holds the reference for the vehicle's XML definition file.

It lists the properties and tables that can be used to implement a vehicle class. Vehicle implementations are placed in
`
'Scripts/Entities/Vehicles/Implementations'
`
. Please note that new definition files will only be recognized by the editor after restarting. However, for edits to an already existing xml file, 'Reload Scripts' will suffice.

Example base content for a vehicle xml implementation file:

`
<
`
`
Vehicle
`

`
name
`
`
=
`
`
"MyVehicle"
`

`
... >
`
`

`
`
<
`
`
Physics
`

`
mass
`
`
=
`
`
"2500"
`

`
pushable
`
`
=
`
`
"0"
`
`
>
`
`

`
`
<
`
`
Buoyancy
`

`
waterDensity
`
`
=
`
`
"30"
`

`
... />
`
`

`
`
`
`
Physics
`
`
>
`
`

`
`
<
`
`
Parts
`
`
>
`
`

`
`
<
`
`
Part
`
`
 ...
`
`

`
`
<
`
`
Part
`
`
 ...
`
`

`
`
...
`
`
`
`
Vehicle
`
`
>
`
 |

##
Global vehicle properties

 Used as attributes for the
 tag.

Attribute

 |
Optional

 |
Type

 |
Default Value

 |
Description

 |

name

 |
Yes

 |
string

 |
-

 |
 |

show

 |
Yes

 |
bool

 |
1 (true)

 |
If false, the car can not be viewed or manually placed in the editor

 |

actionMap

 |
Yes

 |
string

 |
-

 |
Action map for this vehicle. Action maps can also be defined per seat

 |

viewDistRatio

 |
Yes

 |
int

 |
50

 |
 |

isDestroyable

 |
Yes

 |
bool

 |
1 (true)

 |
Determines if a vehicle gets destroyed after being damaged

 |

*
isOld *
*

 |
*
Yes
*

 |
*
bool
*

 |
*
0 (false)
*

 |
*
Here for compatibility, will be removed in the next major release
*

 |

* This attribute is deprecated, it will be removed in the next major version

##
Physics

This is a table nested under
`
`
, it should be used as
 tags with the properties described below.

Attribute

 |
Optional

 |
Type

 |
Default Value

 |
Description

 |

mass

 |
Yes

 |
float

 |
-

 |
mass in kg

 |

damping

 |
Yes

 |
float

 |
-

 |
physics damping

 |

dampingFreefall

 |
Yes

 |
float

 |
-

 |
physics damping for freefall

 |

gravityFreefall

 |
Yes

 |
vec3

 |
-

 |
gravity used for freefall

 |

pushable

 |
Yes

 |
bool

 |
-

 |
Whether the vehicle is pushable by players

 |

retainGravity

 |
Yes

 |
bool

 |
-

 |
If true, the gravity set at physicalization will be retained, overwriting e.g. gravity areas

 |

##
Buoyancy

This is a table nested under
`
`
, it should be used as
 tags with the properties described below.

Attribute

 |
Optional

 |
Type

 |
Default Value

 |
Description

 |

waterDensity

 |
Yes

 |
float

 |
-

 |
Specific water density

 |

waterResistance

 |
Yes

 |
float

 |
-

 |
Precise water resistance

 |

waterDamping

 |
Yes

 |
float

 |
-

 |
Simplified water damping

 |

##
Simulation

This is a table nested under
`
`
, it should be used as
 tags with the properties described below.

Attribute

 |
Optional

 |
Type

 |
Default Value

 |
Description

 |

maxTimeStep

 |
Yes

 |
float

 |
-

 |
 |

minEnergy

 |
Yes

 |
float

 |
-

 |
 |

maxLoggedCollisions

 |
Yes

 |
int

 |
-

 |
 |

##
Components

This is an array table nested under
`
`
, it should be used as
 tags with child tags
 which of which have the properties described below.

Attribute

 |
Optional

 |
Type

 |
Default Value

 |
Description

 |

name

 |
Yes

 |
string

 |
-

 |
Name of the component, it will serve as an identifier, it must exist and be unique

 |

position

 |
Yes

 |
vec3

 |
-

 |
Position and size should be supplied together to define the box shaped area of the component

 |

size

 |
Yes

 |
vec3

 |
-

 |
 |

*
minBound *
*

 |
*
Yes
*

 |
*
vec3
*

 |
*
-
*

 |
*
'minBound' and 'maxBound' have been replaced by 'position' and 'size'.
*

 |

*
maxBound *
*

 |
*
Yes
*

 |
*
vec3
*

 |
*
-
*

 |
*
'minBound' and 'maxBound' have been replaced by 'position' and 'size'.
*

 |

useBoundsFromParts

 |
Yes

 |
bool

 |
0 (false)

 |
 |

useDamageLevels

 |
Yes

 |
bool

 |
1 (true)

 |
When hit, only triggers the DamageBehaviors of this component when there is a change in the damage level. A component has 4 damage levels plus a '100% destroyed' level. Set to false to disable.

 |

damageMax

 |
Yes

 |
float

 |
0.0

 |
 |

hullAffection

 |
Yes

 |
float

 |
1.0

 |
Amount of damage that affects the main hull when this component is hit

 |

major

 |
Yes

 |
bool

 |
1 (true)

 |
If disabled, it does not consider this component for the overall health of the vehicle and for some damage calculations/display

 |

isOnlyDamageableByPlayer

 |
Yes

 |
bool

 |
0 (false)

 |
 |

* This attribute is deprecated, it will be removed in the next major version

##
DamageMultipliers

See
[shared reference.](#VehicleSetup-Damages-DamageMultipliers)

##
DamageBehaviors

See
[shared reference.](#VehicleSetup-Damages-DamagesGroups-DamagesSubGroups-DamageBehaviors)

##
Parts

This is an array table nested under
`
`
, it should be used as
 tags with child tags
 which of which have the properties described below.

 A Part must define a 'class' property. According to the specified class, there are different properties and subtables that can be used to configure the part.

Attribute

 |
Optional

 |
Type

 |
Default Value

 |
Description

 |

class

 |
Yes

 |
string

 |
-

 |
The type of the part. Part types follow an hierarchical structure, extending each other meaning that e.g. a 'SubPartWheel' has its own attributes and also the ones of a 'SubPart' and a 'Base'. A class may not actually use an attribute from the base. Class can be one of the following:

-
'Base' (all other parts are also Base)

-
'Static'

-
'Animated'

-
'AnimatedChar' (is an Animated)

-
'AnimatedJoint'

-
'Entity'

-
'EntityDelayedDetach' (is an Entity)

-
'EntityAttachment'

-
'SubPart'

-
'SubPartWheel' (is a SubPart)

-
'SuspensionPart' (is a SubPart)

-
'MassBox'

-
'ParticleEffect'

-
'Light'

-
'PulsingLight' (is a Light)

-
'Tread'

-
'WaterRipplesGenerator'
 |

##
Class Base

Attribute

 |
Optional

 |
Type

 |
Default Value

 |
Description

 |

name

 |
Yes

 |
string

 |
-

 |
Name of the part, must exist and be unique, it will be used as an identifier

 |

helper

 |
Yes

 |
string

 |
-

 |
Helper where the part will be positioned. Only used by Static, Attachment, SubParts and WaterRipplesGenerator. For SubParts 'position' takes precedence over 'helper'

 |

position

 |
Yes

 |
vec3

 |
0,0,0

 |
Position for this part in entity space. Only used by MassBox and SubParts. For SubParts 'position' takes precedence over 'helper'

 |

useOption

 |
Yes

 |
int

 |
-1

 |
Only used by AnimatedJoint. Index of optional part to be used, if available

 |

isHidden

 |
Yes

 |
bool

 |
0 (false)

 |
Hides the part from rendering

 |

disableCollision

 |
Yes

 |
bool

 |
0 (false)

 |
Disables all collisions, useful e.g. for MassBox

 |

disablePhysics

 |
Yes

 |
bool

 |
0 (false)

 |
Prevents the part from being physicalized as rigid

 |

mass

 |
Yes

 |
float

 |
0.0

 |
Mass of this part, contributes for the overall mass of the vehicle, however the most common setup is to have only one part (hull, mass box) with mass assigned

 |

density

 |
Yes

 |
float

 |
-1.0

 |
 |

filename

 |
Yes

 |
string

 |
Geometry or character filename to load

 |
 |

component

 |
Yes

 |
string

 |
-

 |
Component this part belongs to. A part can belong to multiple components, in that case use a 'Components' subtable

 |

Components

This is an array table nested under
`
`
, it should be used as
 tags with child tags
 which of which have the properties described below.

Attribute

 |
Optional

 |
Type

 |
Default Value

 |
Description

 |

value

 |
Yes

 |
string

 |
-

 |
Component name

 |

##
Class Static

Static

This is a table nested under
`
`
, it should be used as
 tags with the properties described below.

Attribute

 |
Optional

 |
Type

 |
Default Value

 |
Description

 |

filename

 |
Yes

 |
string

 |
-

 |
 |

filenameDestroyed

 |
Yes

 |
string

 |
-

 |
 |

geometry

 |
Yes

 |
string

 |
-

 |
 |

##
Class Animated

Animated

This is a table nested under
`
`
, it should be used as
 tags with the properties described below.

Attribute

 |
Optional

 |
Type

 |
Default Value

 |
Description

 |

filename

 |
Yes

 |
string

 |
-

 |
 |

filenameDestroyed

 |
Yes

 |
string

 |
-

 |
 |

destroyedSuffix

 |
Yes

 |
string

 |
-

 |
 |

ignoreDestroyedState

 |
Yes

 |
bool

 |
0 (false)

 |
 |

##
Class AnimatedChar

empty - no specific attributes

##
Class AnimatedJoint

AnimatedJoint

This is a table nested under
`
`
, it should be used as
 tags with the properties described below.

Attribute

 |
Optional

 |
Type

 |
Default Value

 |
Description

 |

detachBaseForce

 |
Yes

 |
vec3

 |
0.0, 0.0, 0.0

 |
 |

detachProbability

 |
Yes

 |
float

 |
0.0

 |
 |

Dials

This is a table nested under
`
`
, it should be used as
 tags with the properties described below.

Attribute

 |
Optional

 |
Type

 |
Default Value

 |
Description

 |

rotationMax

 |
Yes

 |
float

 |
0.0

 |
Rotation max

 |

ofs

 |
Yes

 |
float

 |
0.0

 |
Rotation offset for dials

 |

##
Class Entity

Entity

This is a table nested under
`
`
, it should be used as
 tags with the properties described below.

Attribute

 |
Optional

 |
Type

 |
Default Value

 |
Description

 |

index

 |
Yes

 |
int

 |
-

 |
 |

id

 |
Yes

 |
int

 |
-

 |
Same as 'index', used if 'index' is not found

 |

name

 |
Yes

 |
string

 |
-

 |
 |

archetype

 |
Yes

 |
string

 |
-

 |
 |

helper

 |
Yes

 |
string

 |
-

 |
 |

collideWithParent

 |
Yes

 |
bool

 |
1 (true)

 |
 |

detachInsteadOfDestroy

 |
Yes

 |
bool

 |
0 (false)

 |
 |

##
Class EntityDelayedDetach

empty - no specific attributes

##
Class EntityAttachment

empty - no specific attributes

##
Class SubPart

SubPart

This is a table nested under
`
`
, it should be used as
 tags with the properties described below.

Attribute

 |
Optional

 |
Type

 |
Default Value

 |
Description

 |

filename

 |
Yes

 |
string

 |
-

 |
 |

geometryname

 |
Yes

 |
string

 |
-

 |
 |

##
Class SubPartWheel

SubPartWheel

This is a table nested under
`
`
, it should be used as
 tags with the properties described below.

Attribute

 |
Optional

 |
Type

 |
Default Value

 |
Description

 |

suspLenght

 |
Yes

 |
float

 |
0.0

 |
Suspension lenght

 |

slipFrictionMod

 |
Yes

 |
float

 |
0.0

 |
 |

slipSlope

 |
Yes

 |
float

 |
1.0

 |
 |

rimRadius

 |
Yes

 |
float

 |
0.0

 |
 |

torqueScale

 |
Yes

 |
float

 |
1.0

 |
 |

axle

 |
Yes

 |
int

 |
-

 |
Unused

 |

density

 |
Yes

 |
float

 |
-

 |
 |

damping

 |
Yes

 |
float

 |
-

 |
suspension damping, if 0 calculate as -kdamping*(approximate zero oscillations damping)

 |

lenInit

 |
Yes

 |
float

 |
-

 |
current suspension length (assumed to be length in rest state)

 |

lenMax

 |
Yes

 |
float

 |
-

 |
relaxed suspension length

 |

maxFriction

 |
Yes

 |
float

 |
-

 |
additional friction limits for tire friction

 |

minFriction

 |
Yes

 |
float

 |
-

 |
additional friction limits for tire friction

 |

latFriction

 |
Yes

 |
float

 |
-

 |
coefficient for lateral friction

 |

stiffness

 |
Yes

 |
float

 |
-

 |
suspension stiffness, if 0 calculate from lenMax, lenInit and vehicle mass and geometry

 |

surfaceId

 |
Yes

 |
float

 |
-

 |
surface identifier (used if corresponding CGeometry does not contain materials)

 |

stiffnessWeight

 |
Yes

 |
float

 |
1.0

 |
When autocalculating stiffness use this weight for this wheel. Note that weights for wheels in front of the centre of mass do not influence the weights of wheels behind the centre of mass

 |

canBrake

 |
Yes

 |
int

 |
1

 |
whether the wheel is locked during handbrakes

 |

canSteer

 |
Yes

 |
int

 |
1

 |
whether the wheel can be steered by the driving wheel

 |

driving

 |
Yes

 |
int

 |
0

 |
whether wheel is driving

 |

rayCast

 |
Yes

 |
int

 |
0

 |
whether the wheel use simple raycasting instead of geometry sweep check

 |

##
Class Suspension Part

SubPart

This is a table nested under
`
`
, it should be used as
 tags with the properties described below.

Attribute

 |
Optional

 |
Type

 |
Default Value

 |
Description

 |

geometryname

 |
Yes

 |
string

 |
-

 |
The name of the parent AnimatedPart. SuspensionPart needs to have an AnimatedPart as a parent

 |

IK

This is a table nested under
`
`
, it should be used as
 tags with the properties described below.

Attribute

 |
Optional

 |
Type

 |
Default Value

 |
Description

 |

target

 |
Yes

 |
string

 |
-

 |
 |

targetHelper

 |
Yes

 |
string

 |
-

 |
 |

offset

 |
Yes

 |
vec3

 |
-

 |
 |

mode

 |
Yes

 |
string

 |
stretch

 |
 Possible values are: {'rotate', 'stretch', 'snap', }

 |

ignoreTargetRotation

 |
Yes

 |
bool

 |
0 (false)

 |
Set to 1 to not use the target's rotation (i.e. for wheels)

 |

##
Class MassBox

MassBox

This is a table nested under
`
`
, it should be used as
 tags with the properties described below.

Attribute

 |
Optional

 |
Type

 |
Default Value

 |
Description

 |

size

 |
Yes

 |
vec3

 |
1.0, 2.0, 0.75

 |
 |

drivingOffset

 |
Yes

 |
float

 |
0.0

 |
Offset used in the Z axis while driving

 |

##
Class ParticleEffect

ParticleEffect

This is a table nested under
`
`
, it should be used as
 tags with the properties described below.

Attribute

 |
Optional

 |
Type

 |
Default Value

 |
Description

 |

id

 |
Yes

 |
int

 |
-

 |
 |

particleEffect

 |
Yes

 |
string

 |
-

 |
 |

helper

 |
Yes

 |
string

 |
-

 |
 |

##
Class Light

Light

This is a table nested under
`
`
, it should be used as
 tags with the properties described below.

Attribute

 |
Optional

 |
Type

 |
Default Value

 |
Description

 |

type

 |
Yes

 |
string

 |
-

 |
See the definition files in Scripts/Entities/Vehicles/Lights for more info. Possible values are: {'"Brake"', '"Brake_Flare"', '"Reverse"', '"Park"', '"Headlight"', '"HeadlightFill"', '"HeadlightFillSmall"', '"HeadLightBeam"', '"Headlight_Flare"', '"WarningLight"', '"BoatNavGreen"', '"BoatNavGreen_Surround"', '"HeliGreen"', '"HeliWhite"', '"HeliWhiteFlash"', '"HeliRed"', '"HeliRedFlash"', }

 |

##
Class PulsingLight

PulsingLight

This is a table nested under
`
`
, it should be used as
 tags with the properties described below.

Attribute

 |
Optional

 |
Type

 |
Default Value

 |
Description

 |

minColorMult

 |
Yes

 |
float

 |
-

 |
 |

toggleOnMinDamageRatio

 |
Yes

 |
float

 |
-

 |
 |

colorMultSpeed

 |
Yes

 |
float

 |
-

 |
 |

toggleStageTwoMinDamageRatio

 |
Yes

 |
float

 |
-

 |
 |

colorMultSpeedStageTwo

 |
Yes

 |
float

 |
-

 |
 |

##
Class Tread

Attribute

 |
Optional

 |
Type

 |
Default Value

 |
Description

 |

component

 |
Yes

 |
string

 |
-

 |
 |

Tread

This is a table nested under
`
`
, it should be used as
 tags with the properties described below.

Attribute

 |
Optional

 |
Type

 |
Default Value

 |
Description

 |

filename

 |
Yes

 |
string

 |
-

 |
 |

uvSpeedMultiplier

 |
Yes

 |
float

 |
0.0

 |
 |

materialName

 |
Yes

 |
string

 |
-

 |
 |

##
Class WaterRipplesGenerator

WaterRipplesGen

This is a table nested under
`
`
, it should be used as
 tags with the properties described below.

Attribute

 |
Optional

 |
Type

 |
Default Value

 |
Description

 |

scale

 |
Yes

 |
float

 |
1.0

 |
 |

strength

 |
Yes

 |
float

 |
1.0

 |
 |

minMovementSpeed

 |
Yes

 |
float

 |
1.0

 |
 |

moveForwardOnly

 |
Yes

 |
bool

 |
0 (false)

 |
 |

##
Helpers

This is an array table nested under
`
`
, it should be used as
 tags with child tags
 which of which have the properties described below.

Attribute

 |
Optional

 |
Type

 |
Default Value

 |
Description

 |

name

 |
Yes

 |
string

 |
-

 |
Helper name that will serve as identifier, it must be unique. If empty or repeated, the helper will be ignored.

 |

position

 |
Yes

 |
vec3

 |
0,0,0

 |
Helper position relative to the vehicle pivot

 |

direction

 |
Yes

 |
vec3

 |
0,0,0

 |
Helper direction

 |

part

 |
Yes

 |
string

 |
-

 |
Vehicle part to attach this helper to. If empty or if the part with the specified name can not be found, the helper will be ignored.

 |

##
Actions

This is an array table nested under
`
`
, it should be used as
 tags with child tags
 which of which have the properties described below.

 An Action must have a 'class' with one of the following values. All classes support common attributes as part of the Action tag,
			and *must* have a child tag with the name of the class, except for 'Flip' and 'AutoAimTarget'.

Attribute

 |
Optional

 |
Type

 |
Default Value

 |
Description

 |

class

 |
Yes

 |
string

 |
-

 |
If not supplied, this action will be ignored. Possible values are:

-
'AutoAimTarget' ( Makes the vehicle a target for auto assist )

-
'AutomaticDoor'

-
'Enter'

-
'EntityAttachment'

-
'Flip' ( Action to recover a vehicle by flipping it over )

-
'LandingGears'
 |

 Common to all
 tags:

##
Activations

This is an array table nested under
`
`
, it should be used as
 tags with child tags
 which of which have the properties described below.

Attribute

 |
Optional

 |
Type

 |
Default Value

 |
Description

 |

type

 |
Yes

 |
string

 |
-

 |
Activation type: {'OnGroundCollision', 'OnUsed', }

 |

param1

 |
Yes

 |
string

 |
-

 |
 Possible values are: {'part', 'component', }

 |

param2

 |
Yes

 |
string

 |
-

 |
The name of the component or part

 |

distance

 |
Yes

 |
float

 |
1.5

 |
 |

 Class specific:

##
Class AutoAimTarget

Attribute

 |
Optional

 |
Type

 |
Default Value

 |
Description

 |

PrimaryBoneName

 |
Yes

 |
string

 |
-

 |
 |

SecondaryBoneName

 |
Yes

 |
string

 |
-

 |
 |

PhysicsBoneName

 |
Yes

 |
string

 |
-

 |
 |

FallbackOffset

 |
Yes

 |
float

 |
1.2

 |
 |

InnerRadius

 |
Yes

 |
float

 |
0.4

 |
 |

OuterRadius

 |
Yes

 |
float

 |
0.8

 |
 |

SnapRadius

 |
Yes

 |
float

 |
2.0

 |
 |

SnapRadiusTagged

 |
Yes

 |
float

 |
2.0

 |
 |

##
Class AutomaticDoor

AutomaticDoor

This is a table nested under
`
`
, it should be used as
 tags with the properties described below.

Attribute

 |
Optional

 |
Type

 |
Default Value

 |
Description

 |

animation

 |
Yes

 |
string

 |
-

 |
 |

timeMax

 |
Yes

 |
float

 |
-

 |
 |

disabled

 |
Yes

 |
bool

 |
0 (false)

 |
 |

##
Class Enter

Enter

This is a table nested under
`
`
, it should be used as
 tags with the properties described below.

Action to enter a vehicle seat.

Seats

This is an array table nested under
`
`
, it should be used as
 tags with child tags
 which of which have the properties described below.

Attribute

 |
Optional

 |
Type

 |
Default Value

 |
Description

 |

value

 |
Yes

 |
string

 |
-

 |
Seat name

 |

##
Class EntityAttachment

EntityAttachment

This is a table nested under
`
`
, it should be used as
 tags with the properties described below.

Attribute

 |
Optional

 |
Type

 |
Default Value

 |
Description

 |

helper

 |
Yes

 |
string

 |
-

 |
 |

class

 |
Yes

 |
string

 |
-

 |
Class of the entity to spawn

 |

##
Class Flip

empty - no specific attributes

##
Class LandingGears

LandingGears

This is a table nested under
`
`
, it should be used as
 tags with the properties described below.

Attribute

 |
Optional

 |
Type

 |
Default Value

 |
Description

 |

altitudeToRetractGears

 |
Yes

 |
float

 |
0.0

 |
 |

landingDamages

 |
Yes

 |
float

 |
0.0

 |
 |

velocityMax

 |
Yes

 |
float

 |
0.0

 |
 |

blockPartRotation

 |
Yes

 |
string

 |
-

 |
 |

isOnlyAutoForPlayer

 |
Yes

 |
bool

 |
0 (false)

 |
 |

##
Seats

This is an array table nested under
`
`
, it should be used as
 tags with child tags
 which of which have the properties described below.

Attribute

 |
Optional

 |
Type

 |
Default Value

 |
Description

 |

name

 |
Yes

 |
string

 |
-

 |
Seat name, it must exist and be unique.

 |

actionMap

 |
Yes

 |
string

 |
-

 |
 |

locked

 |
Yes

 |
string

 |
Unlocked

 |
Locks the seat to a specific condition, eg. disallow AI to use this seat. Possible values are: {'Unlocked', 'AI', 'Players', 'All', }

 |

seatGroupIndex

 |
Yes

 |
int

 |
1

 |
 |

isDriver

 |
Yes

 |
bool

 |
0 (false)

 |
If true, this seat is the driver seat

 |

isRemoteControlled

 |
Yes

 |
bool

 |
0 (false)

 |
 |

isPassengerShielded

 |
Yes

 |
bool

 |
0 (false)

 |
If set, the passenger always takes 0 damage

 |

isPassengerExposed

 |
Yes

 |
bool

 |
0 (false)

 |
If set, the passenger is killed when vehicle flips over (AI or player) or with direct explosion hits (AI only)

 |

isPassengerHidden

 |
Yes

 |
bool

 |
0 (false)

 |
 |

TransformViewOnExit

 |
Yes

 |
bool

 |
1 (true)

 |
 |

enterInFirstPerson

 |
Yes

 |
bool

 |
1 (true)

 |
 |

exitInFirstPerson

 |
Yes

 |
bool

 |
1 (true)

 |
 |

movePassengerOnExit

 |
Yes

 |
bool

 |
1 (true)

 |
 |

ragdollOnDeath

 |
Yes

 |
bool

 |
0 (false)

 |
 |

disableStopAllAnimationsOnEnter

 |
Yes

 |
bool

 |
0 (false)

 |
 |

exitOffsetPlayer

 |
Yes

 |
vec3

 |
0,0,0

 |
Optional offset for player exiting, added to regular exit pos

 |

usesSeatForEntering

 |
Yes

 |
string

 |
-

 |
 |

remotelyUseActionsFromSeat

 |
Yes

 |
string

 |
-

 |
Allow the passenger to remotely use seat actions from another seat when no one uses that other seat.

 |

explosionShakeMult

 |
Yes

 |
float

 |
1.0

 |
Multiplier for explosion camera shakes

 |

AimPart

 |
Yes

 |
string

 |
-

 |
If set, the view follows this part.

 |

AutoAim

 |
Yes

 |
bool

 |
0 (false)

 |
 |

updatePassengerTM

 |
Yes

 |
bool

 |
1 (true)

 |
Allow seat to update passenger's transform matrix.

 |

sitHelper

 |
Yes

 |
string

 |
-

 |
Sit position

 |

enterHelper

 |
Yes

 |
string

 |
-

 |
Helper for entering position

 |

exitHelper

 |
Yes

 |
string

 |
-

 |
Optional helper for seperate exit position

 |

aiVisionHelper

 |
Yes

 |
string

 |
-

 |
Position where AI begin their vision raytracing

 |

*
part *
*

 |
*
Yes
*

 |
*
string
*

 |
*
-
*

 |
*
Optional part this seat is attached to
*

 |

*
useBoundsForEntering *
*

 |
*
No
*

 |
*
??
*

 |
*
-
*

 |
*

*

 |

*
agVehicleName *
*

 |
*
No
*

 |
*
??
*

 |
*
-
*

 |
*

*

 |

*
agSeatNumber *
*

 |
*
No
*

 |
*
??
*

 |
*
-
*

 |
*

*

 |

* This attribute is deprecated, it will be removed in the next major version

##
aimPartHands (deprecated)

This is an array table nested under
`
`
, however it is deprecated and it should no longer be used.

##
Views

This is an array table nested under
`
`
, it should be used as
 tags with child tags
 which of which have the properties described below.

 A View must have a 'class' with one of the following values. All view classes suport common attributes as part of the View tag
			and *must* have a child tag with the name of the class.

Attribute

 |
Optional

 |
Type

 |
Default Value

 |
Description

 |

class

 |
Yes

 |
string

 |
-

 |
 Possible values are:

-
'FirstPerson'

-
'ThirdPerson'

-
'ActionThirdPerson'

-
'SteerThirdPerson'
 |

 Common properties to all
 tags:

Attribute

 |
Optional

 |
Type

 |
Default Value

 |
Description

 |

rotationBoundsActionMult

 |
Yes

 |
float

 |
0.0

 |
When this feature is used, actions are created using this multiplier when the view rotation is pushing its boundaries

 |

canRotate

 |
Yes

 |
bool

 |
false

 |
If true, the view can be rotated

 |

rotationInit

 |
Yes

 |
vec3

 |
0,0,0

 |
around the x, y and z axis in degrees

 |

rotationMax

 |
Yes

 |
vec3

 |
0,0,0 or 85,0,85 if it is third person

 |
Max rotation around the x, y and z axes in degrees. eg. last (z) value represents max rotation to the left

 |

rotationMin

 |
Yes

 |
vec3

 |
0,0,0 or -max

 |
Max rotation in inverse direction around the x, y and z axes in degrees eg. last (z) value represents max rotation to the right. It is suggested to not specify this field, so that it will mirror automatically the Max setting. The rotationMax must be set for Min to work

 |

delayTimeMax

 |
Yes

 |
float

 |
0.3

 |
 |

relaxTimeMax

 |
Yes

 |
float

 |
0.4

 |
 |

rotationVelMax

 |
Yes

 |
float

 |
1.0

 |
 |

rotationVelMin

 |
Yes

 |
float

 |
1.0

 |
 |

hidePlayer

 |
Yes

 |
bool

 |
false

 |
 |

isAvailableRemotely

 |
Yes

 |
bool

 |
false

 |
 |

relaxEnabled

 |
Yes

 |
bool

 |
false

 |
 |

##
HideParts

This is an array table nested under
`
`
, it should be used as
 tags with child tags
 which of which have the properties described below.

Attribute

 |
Optional

 |
Type

 |
Default Value

 |
Description

 |

value

 |
Yes

 |
string

 |
-

 |
Name of the part to hide

 |

 Properties for each specific View class child tag:

##
Class FirstPerson

FirstPerson

This is a table nested under
`
`
, it should be used as
 tags with the properties described below.

Attribute

 |
Optional

 |
Type

 |
Default Value

 |
Description

 |

offset

 |
Yes

 |
vec3

 |
0,0,0

 |
 |

hidePlayer

 |
Yes

 |
bool

 |
false or set on View

 |
Disable vehicle rendering of the player, always enabled when hideVehicle is enabled.

 |

hideVehicle

 |
Yes

 |
bool

 |
false

 |
Disable vehicle rendering on the client, hides player as well.

 |

relativeToHorizon

 |
Yes

 |
float

 |
0.0

 |
 |

followSpeed

 |
Yes

 |
float

 |
4.0

 |
 |

fov

 |
Yes

 |
float

 |
55.0

 |
Camera Field Of View, in degrees

 |

helper

 |
Yes

 |
string

 |
-

 |
A helper to attach the camera to. If named 'auto', creates and uses a helper 0.625 above the seat helper

 |

characterBone

 |
Yes

 |
string

 |
-

 |
 |

frameObject

 |
Yes

 |
string

 |
-

 |
Load a geometry or character object

 |

frameObjectOffset

 |
Yes

 |
string

 |
0,0.18,0.01

 |
 |

##
Class ThirdPerson

ThirdPerson

This is a table nested under
`
`
, it should be used as
 tags with the properties described below.

Attribute

 |
Optional

 |
Type

 |
Default Value

 |
Description

 |

distance

 |
Yes

 |
float

 |
0.0

 |
 |

speed

 |
Yes

 |
float

 |
5.0

 |
 |

heightOffset

 |
Yes

 |
float

 |
1.5

 |
 |

##
Class ActionThirdPerson

ActionThirdPerson

This is a table nested under
`
`
, it should be used as
 tags with the properties described below.

Attribute

 |
Optional

 |
Type

 |
Default Value

 |
Description

 |

heightAboveWater

 |
Yes

 |
float

 |
0.0

 |
 |

heightOffset

 |
Yes

 |
float

 |
1.5

 |
 |

cameraAimOffset

 |
Yes

 |
vec3

 |
0,0,0

 |
 |

cameraPosOffset

 |
Yes

 |
vec3

 |
0,0,0

 |
 |

lagSpeed

 |
Yes

 |
float

 |
1.0

 |
 |

velocityMult

 |
Yes

 |
vec3

 |
0,0,0

 |
 |

verticalFilter

 |
Yes

 |
float

 |
0.2

 |
 |

verticalFilterOffset

 |
Yes

 |
float

 |
0.0

 |
 |

##
Class SteerThirdPerson

SteerThirdPerson

This is a table nested under
`
`
, it should be used as
 tags with the properties described below.

Pos

This is a table nested under
`
`
, it should be used as
 tags with the properties described below.

Settings for the view position.

Attribute

 |
Optional

 |
Type

 |
Default Value

 |
Description

 |

aim

 |
Yes

 |
vec3

 |
0,0,0

 |
Camera aim position relative to the vehicle

 |

offset

 |
Yes

 |
vec3

 |
0,0,0

 |
Camera position relative to the aim location

 |

pivotOffset

 |
Yes

 |
float

 |
0.0

 |
Offset the aim pivot points in the z direction

 |

Rotation

This is a table nested under
`
`
, it should be used as
 tags with the properties described below.

Settings for the view rotation.

Attribute

 |
Optional

 |
Type

 |
Default Value

 |
Description

 |

canRotate

 |
Yes

 |
bool

 |
1 (true)

 |
If set the false, the view can not be rotated. This view does not respond to the common canRotate View attribute

 |

rotationMax

 |
Yes

 |
vec3

 |
10,0,90

 |
Rotation limit around x, y and z, in degrees, for zero and low speeds. The value is applied in both directions, eg. if the z component is 90, the rotation will be limited to 90 degrees to the right and another 90 to the left. This view never rotates around y and it does not use the common attribute for rotationMax and rotationMin

 |

rotationMax2

 |
Yes

 |
vec3

 |
one third of rotationMax

 |
Rotation limit around x, y and z axes in degrees for max speed. In-between speeds will have a blended maximum rotation

 |

stickSensitivity

 |
Yes

 |
vec3

 |
0.5,0.5,0.5

 |
Joystick sensitivity for rotating the view at zero and low speeds. The y component has no effect

 |

stickSensitivity2

 |
Yes

 |
vec3

 |
0.5,0.5,0.5

 |
Joystick sensitivity for rotating the view at high speed. Intermediate speeds will have a blended value of sensitivity

 |

inheritedElev

 |
Yes

 |
float

 |
0.2

 |
How much to inherit from the target's elevation angle

 |

Motion

This is a table nested under
`
`
, it should be used as
 tags with the properties described below.

Settings for the view's angular spring as response to rotation.

Attribute

 |
Optional

 |
Type

 |
Default Value

 |
Description

 |

returnSpeed

 |
Yes

 |
float

 |
0.0

 |
Angular spring back to default at zero and low speeds.

 |

returnSpeed2

 |
Yes

 |
float

 |
0.0

 |
Angular spring back to default at high speed. Intermediate speeds will have a blended value

 |

angFollow

 |
Yes

 |
float

 |
0.0

 |
Angular speed for the correction

 |

Radius

This is a table nested under
`
`
, it should be used as
 tags with the properties described below.

Settings for the inertia spring, as response to acceleration.

Attribute

 |
Optional

 |
Type

 |
Default Value

 |
Description

 |

min

 |
Yes

 |
float

 |
0.9

 |
Minimum distance for inertia spring (maximum compression). The value is a fraction to the default radius

 |

max

 |
Yes

 |
float

 |
1.1

 |
Maximum distance for inertia spring (maximum extension). The value is a fraction to the default radius

 |

relaxRate

 |
Yes

 |
float

 |
10.0

 |
Rate at which to relax back into the default radius

 |

dampRate

 |
Yes

 |
float

 |
1.0

 |
Damp rate for the inertia spring

 |

velInfluence

 |
Yes

 |
float

 |
0.1

 |
Influence that the velocity has in the inertia spring. Should be between 0 and 1

 |

Backwards

This is a table nested under
`
`
, it should be used as
 tags with the properties described below.

Settings for when driving backwards.

Attribute

 |
Optional

 |
Type

 |
Default Value

 |
Description

 |

clamp

 |
Yes

 |
bool

 |
1 (true)

 |
Set to false to disable rotation limits when going backwards

 |

returnSpring

 |
Yes

 |
bool

 |
1 (true)

 |
Set to false to disable the rotation return spring when going backwards

 |

##
Transitions

This is a table nested under
`
`
, it should be used as
 tags with the properties described below.

TODO

##
SeatActions

This is an array table nested under
`
`
, it should be used as
 tags with child tags
 which of which have the properties described below.

 A SeatAction must have a 'class' with one of the following values. All classes suport common attributes as part of the SeatAction tag
			and have related child properties and tables

Attribute

 |
Optional

 |
Type

 |
Default Value

 |
Description

 |

class

 |
Yes

 |
string

 |
-

 |
If not supplied, this action will be ignored. Possible values are:

-
'Animation'

-
'DeployRope'

-
'Lights'

-
'Movement'

-
'OrientateBoneToView'

-
'OrientatePartToView'

-
'PassengerIK'

-
'PassiveAnimation'

-
'RotateBone'

-
'RotateTurret'

-
'ShakeParts'

-
'Sound'

-
'SteeringWheel'

-
'WeaponsBone'

-
'Weapons'
 |

 Common properties to all
 tags:

Attribute

 |
Optional

 |
Type

 |
Default Value

 |
Description

 |

name

 |
Yes

 |
string

 |
-

 |
The name of the action, necessary for DisableSeatAction damage behavior

 |

isAvailableRemotely

 |
Yes

 |
bool

 |
-

 |
Used to enable remote usability of the SeatAction

 |

 Class specific properties:

##
Class Animation

Animation

This is a table nested under
`
`
, it should be used as
 tags with the properties described below.

Attribute

 |
Optional

 |
Type

 |
Default Value

 |
Description

 |

vehicleAnimation

 |
Yes

 |
string

 |
-

 |
 |

control

 |
Yes

 |
string

 |
-

 |
 Possible values are: {'roll', }

 |

manualUpdate

 |
Yes

 |
bool

 |
1 (true)

 |
 |

speed

 |
Yes

 |
float

 |
1.0

 |
 |

##
Class PassiveAnimation

Attribute

 |
Optional

 |
Type

 |
Default Value

 |
Description

 |

FragmentID

 |
Yes

 |
string

 |
-

 |
 |

##
Class DeployRope

DeployRope

This is a table nested under
`
`
, it should be used as
 tags with the properties described below.

Attribute

 |
Optional

 |
Type

 |
Default Value

 |
Description

 |

animation

 |
Yes

 |
string

 |
-

 |
 |

helper

 |
Yes

 |
string

 |
-

 |
 |

##
Class Lights

Lights

This is a table nested under
`
`
, it should be used as
 tags with the properties described below.

Attribute

 |
Optional

 |
Type

 |
Default Value

 |
Description

 |

activation

 |
Yes

 |
string

 |
-

 |
 Possible values are: {'toggle', 'brake', 'reverse', }

 |

sound

 |
Yes

 |
int

 |
1

 |
For toggle action, used for on and off

 |

onSound

 |
Yes

 |
int

 |
1

 |
For brake or reverse

 |

offSound

 |
Yes

 |
int

 |
1

 |
For brake or reverse

 |

LightParts

This is an array table nested under
`
`
, it should be used as
 tags with child tags
 which of which have the properties described below.

Attribute

 |
Optional

 |
Type

 |
Default Value

 |
Description

 |

value

 |
Yes

 |
string

 |
-

 |
Name of the light part

 |

##
Class OrientateBoneToView

Attribute

 |
Optional

 |
Type

 |
Default Value

 |
Description

 |

MoveBone

 |
Yes

 |
string

 |
-

 |
 |

LookBone

 |
Yes

 |
string

 |
-

 |
 |

Sluggishness

 |
Yes

 |
float

 |
0.0

 |
 |

MoveBoneBaseOrientation

This is a table nested under
`
`
, it should be used as
 tags with the properties described below.

Attribute

 |
Optional

 |
Type

 |
Default Value

 |
Description

 |

x

 |
Yes

 |
float

 |
-

 |
x,y,z rotation

 |

y

 |
Yes

 |
float

 |
-

 |
x,y,z rotation

 |

z

 |
Yes

 |
float

 |
-

 |
x,y,z rotation

 |

##
Class OrientatePartToView

Parts

This is an array table nested under
`
`
, it should be used as
 tags with child tags
 which of which have the properties described below.

Attribute

 |
Optional

 |
Type

 |
Default Value

 |
Description

 |

name

 |
Yes

 |
string

 |
-

 |
 |

orientationAxis

 |
Yes

 |
vec3

 |
1.0,1.0,1.0

 |
 |

##
Class RotateBone

Attribute

 |
Optional

 |
Type

 |
Default Value

 |
Description

 |

AutoAimStrengthMultiplier

 |
Yes

 |
float

 |
-

 |
 |

NetworkSluggishness

 |
Yes

 |
float

 |
-

 |
 |

SpeedMultiplier

 |
Yes

 |
float

 |
-

 |
 |

soundFP

 |
Yes

 |
string

 |
-

 |
 |

soundTP

 |
Yes

 |
string

 |
-

 |
 |

soundParam

 |
Yes

 |
string

 |
-

 |
 |

idealRotationSpeedForSound

 |
Yes

 |
float

 |
180.0

 |
 |

soundRotSpeedSmoothTime

 |
Yes

 |
float

 |
-

 |
 |

settlePitch

 |
Yes

 |
float

 |
-

 |
 |

settleDelay

 |
Yes

 |
float

 |
-

 |
 |

settleTime

 |
Yes

 |
float

 |
-

 |
 |

MoveBone

 |
Yes

 |
string

 |
-

 |
 |

MoveBoneBaseOrientation

This is a table nested under
`
`
, it should be used as
 tags with the properties described below.

Attribute

 |
Optional

 |
Type

 |
Default Value

 |
Description

 |

x

 |
Yes

 |
float

 |
-

 |
x,y,z rotation

 |

y

 |
Yes

 |
float

 |
-

 |
x,y,z rotation

 |

z

 |
Yes

 |
float

 |
-

 |
x,y,z rotation

 |

PitchLimit

This is a table nested under
`
`
, it should be used as
 tags with the properties described below.

Attribute

 |
Optional

 |
Type

 |
Default Value

 |
Description

 |

min

 |
Yes

 |
float

 |
-

 |
 |

max

 |
Yes

 |
float

 |
-

 |
 |

##
Class RotateTurret

RotateTurret

This is a table nested under
`
`
, it should be used as
 tags with the properties described below.

Pitch

This is a table nested under
`
`
, it should be used as
 tags with the properties described below.

Attribute

 |
Optional

 |
Type

 |
Default Value

 |
Description

 |

part

 |
No

 |
string

 |
-

 |
Vehicle part to rotate (pitch)

 |

speed

 |
Yes

 |
float

 |
-

 |
Rotation speed

 |

accel

 |
Yes

 |
float

 |
-

 |
Rotation acceleration

 |

worldSpace

 |
Yes

 |
bool

 |
-

 |
Use world space rotations

 |

Limits

This is an array table nested under
`
`
, it should be used as
 tags with child tags
 which of which have the properties described below.

Min/Max limits for rotation.

Sound

This is a table nested under
`
`
, it should be used as
 tags with the properties described below.

Attribute

 |
Optional

 |
Type

 |
Default Value

 |
Description

 |

event

 |
No

 |
string

 |
-

 |
sound event name

 |

eventDamage

 |
Yes

 |
string

 |
-

 |
event name for damage sound

 |

helper

 |
Yes

 |
string

 |
-

 |
sound helper

 |

param

 |
Yes

 |
string

 |
-

 |
sound param name

 |

Yaw

This is a table nested under
`
`
, it should be used as
 tags with the properties described below.

Attribute

 |
Optional

 |
Type

 |
Default Value

 |
Description

 |

part

 |
No

 |
string

 |
-

 |
Vehicle part to rotate (yaw)

 |

speed

 |
Yes

 |
float

 |
-

 |
Rotation speed

 |

accel

 |
Yes

 |
float

 |
-

 |
Rotation acceleration

 |

worldSpace

 |
Yes

 |
bool

 |
-

 |
Use world space rotations

 |

Limits

This is an array table nested under
`
`
, it should be used as
 tags with child tags
 which of which have the properties described below.

Min/Max limits for rotation.

Sound

This is a table nested under
`
`
, it should be used as
 tags with the properties described below.

Attribute

 |
Optional

 |
Type

 |
Default Value

 |
Description

 |

event

 |
No

 |
string

 |
-

 |
sound event name

 |

eventDamage

 |
Yes

 |
string

 |
-

 |
event name for damage sound

 |

helper

 |
Yes

 |
string

 |
-

 |
sound helper

 |

param

 |
Yes

 |
string

 |
-

 |
sound param name

 |

RotationTest

This is a table nested under
`
`
, it should be used as
 tags with the properties described below.

Attribute

 |
Optional

 |
Type

 |
Default Value

 |
Description

 |

helper1

 |
Yes

 |
string

 |
-

 |
 |

helper2

 |
Yes

 |
string

 |
-

 |
 |

radius

 |
Yes

 |
float

 |
-

 |
 |

##
Class ShakeParts

Parts

This is an array table nested under
`
`
, it should be used as
 tags with child tags
 which of which have the properties described below.

Attribute

 |
Optional

 |
Type

 |
Default Value

 |
Description

 |

name

 |
Yes

 |
string

 |
-

 |
 |

amp

 |
Yes

 |
??

 |
0.0

 |
 |

ampRot

 |
Yes

 |
??

 |
0.0

 |
 |

freq

 |
Yes

 |
??

 |
0.0

 |
 |

suspensionAmp

 |
Yes

 |
??

 |
0.0

 |
 |

suspensionResponse

 |
Yes

 |
??

 |
0.0

 |
 |

suspensionSharpness

 |
Yes

 |
??

 |
0.0

 |
 |

##
Class PassengerIK

PassengerIK

This is a table nested under
`
`
, it should be used as
 tags with the properties described below.

Attribute

 |
Optional

 |
Type

 |
Default Value

 |
Description

 |

waitShortlyBeforeStarting

 |
Yes

 |
float

 |
0

 |
 |

Limbs

This is an array table nested under
`
`
, it should be used as
 tags with child tags
 which of which have the properties described below.

Attribute

 |
Optional

 |
Type

 |
Default Value

 |
Description

 |

limb

 |
Yes

 |
string

 |
-

 |
limb name

 |

helper

 |
Yes

 |
string

 |
-

 |
 |

##
Class Sound

Audio

This is a table nested under
`
`
, it should be used as
 tags with the properties described below.

Attribute

 |
Optional

 |
Type

 |
Default Value

 |
Description

 |

startTrigger

 |
Yes

 |
string

 |
-

 |
 |

stopTrigger

 |
Yes

 |
string

 |
-

 |
 |

helper

 |
Yes

 |
string

 |
-

 |
 |

##
Class SteeringWheel

SteeringWheel

This is a table nested under
`
`
, it should be used as
 tags with the properties described below.

 This table must have subtable 'Car' *or* 'Actions'.

Actions

This is a table nested under
`
`
, it should be used as
 tags with the properties described below.

Attribute

 |
Optional

 |
Type

 |
Default Value

 |
Description

 |

steeringRelaxMult

 |
Yes

 |
float

 |
1.0

 |
 |

steeringForce

 |
Yes

 |
float

 |
1.0

 |
 |

Car

This is a table nested under
`
`
, it should be used as
 tags with the properties described below.

Attribute

 |
Optional

 |
Type

 |
Default Value

 |
Description

 |

jitterFreqLow

 |
Yes

 |
float

 |
0.0

 |
 |

jitterFreqHi

 |
Yes

 |
float

 |
0.0

 |
 |

jitterAmpLow

 |
Yes

 |
float

 |
0.0

 |
 |

jitterAmpHi

 |
Yes

 |
float

 |
0.0

 |
 |

jitterSuspAmp

 |
Yes

 |
float

 |
0.0

 |
 |

jitterSuspResponse

 |
Yes

 |
float

 |
0.0

 |
 |

##
Class Weapons

Weapons

This is a table nested under
`
`
, it should be used as
 tags with the properties described below.

Attribute

 |
Optional

 |
Type

 |
Default Value

 |
Description

 |

respawnTime

 |
Yes

 |
float

 |
-

 |
 |

isSecondary

 |
Yes

 |
bool

 |
-

 |
 |

mounted

 |
Yes

 |
bool

 |
-

 |
 |

shotDelay

 |
Yes

 |
float

 |
-

 |
 |

disablesShootToCrosshair

 |
Yes

 |
bool

 |
-

 |
 |

attackInput

 |
Yes

 |
string

 |
-

 |
 Possible values are: {'primary', 'secondary', }

 |

Weapons

This is an array table nested under
`
`
, it should be used as
 tags with child tags
 which of which have the properties described below.

Attribute

 |
Optional

 |
Type

 |
Default Value

 |
Description

 |

class

 |
Yes

 |
string

 |
-

 |
 |

part

 |
Yes

 |
string

 |
-

 |
 |

inheritVelocity

 |
Yes

 |
bool

 |
-

 |
 |

animSubContext

 |
Yes

 |
string

 |
-

 |
 |

Helpers

This is an array table nested under
`
`
, it should be used as
 tags with child tags
 which of which have the properties described below.

Attribute

 |
Optional

 |
Type

 |
Default Value

 |
Description

 |

value

 |
Yes

 |
string

 |
-

 |
Helper name

 |

Actions

This is an array table nested under
`
`
, it should be used as
 tags with child tags
 which of which have the properties described below.

Attribute

 |
Optional

 |
Type

 |
Default Value

 |
Description

 |

name

 |
Yes

 |
string

 |
-

 |
 |

Animations

This is an array table nested under
`
`
, it should be used as
 tags with child tags
 which of which have the properties described below.

Attribute

 |
Optional

 |
Type

 |
Default Value

 |
Description

 |

name

 |
Yes

 |
string

 |
-

 |
 |

##
Mannequin

This is a table nested under
`
`
, it should be used as
 tags with the properties described below.

 This table needs a controller defined in the external Mannequin tag, outside Seats.

Attribute

 |
Optional

 |
Type

 |
Default Value

 |
Description

 |

Idle

 |
Yes

 |
string

 |
-

 |
 |

ExitOffset

 |
Yes

 |
string

 |
-

 |
 |

##
Animations

This is a table nested under
`
`
, it should be used as
 tags with the properties described below.

TODO

##
Sounds

This is a table nested under
`
`
, it should be used as
 tags with the properties described below.

TODO

##
SeatGroups

This is an array table nested under
`
`
, it should be used as
 tags with child tags
 which of which have the properties described below.

Attribute

 |
Optional

 |
Type

 |
Default Value

 |
Description

 |

keepEngineWarm

 |
Yes

 |
bool

 |
0 (false)

 |
Allows player to switch seat from driver while keeping the car working

 |

##
Seats

This is an array table nested under
`
`
, it should be used as
 tags with child tags
 which of which have the properties described below.

Attribute

 |
Optional

 |
Type

 |
Default Value

 |
Description

 |

value

 |
Yes

 |
string

 |
-

 |
Name of the seat

 |

##
MovementParams

This is a table nested under
`
`
, it should be used as
 tags with the properties described below.

 This table defines the movement type of the Vehicle, it requires a child tag named after a valid movement type, e.g.
 ...

 Valid movement types are:

-
StdWheeled

-
ArcadeWheeled

-
StdTank

-
Tank

-
StdBoat

-
Helicopter

-
MPVTOL

-
DummyMovement

##
StdWheeled

This is a table nested under
`
`
, it should be used as
 tags with the properties described below.

 Following are the common properties to all movement types except 'DummyMovement'. They must be inside the movement type tag.

Attribute

 |
Optional

 |
Type

 |
Default Value

 |
Description

 |

keepEngineOn

 |
Yes

 |
bool

 |
0 (false)

 |
If set to true, the engine will not turn of when the driver leaves

 |

engineIgnitionTime

 |
Yes

 |
float

 |
1.6

 |
 |

##
Animations

This is a table nested under
`
`
, it should be used as
 tags with the properties described below.

Attribute

 |
Optional

 |
Type

 |
Default Value

 |
Description

 |

engine

 |
No

 |
string

 |
-

 |
 |

##
SoundParams

This is a table nested under
`
`
, it should be used as
 tags with the properties described below.

 Common to all:

Attribute

 |
Optional

 |
Type

 |
Default Value

 |
Description

 |

engineSoundPosition

 |
Yes

 |
string

 |
-

 |
Helper name for the position used to emit the engine sound

 |

rpmPitchSpeed

 |
Yes

 |
float

 |
-

 |
Speed for rpm interpolation, usually used with pedal

 |

runSoundDelay

 |
Yes

 |
float

 |
-

 |
Delay for start of run/ambient sound

 |

 Specific to StdWheeled:

Attribute

 |
Optional

 |
Type

 |
Default Value

 |
Description

 |

roadBumpMinSusp

 |
Yes

 |
float

 |
-

 |
Threshold in suspension compression for bump sounds

 |

roadBumpMinSpeed

 |
Yes

 |
float

 |
-

 |
Vehicle min speed for bump sounds

 |

roadBumpIntensity

 |
Yes

 |
float

 |
-

 |
sound param

 |

airbrake

 |
Yes

 |
float

 |
-

 |
braking time threshold for airbrake sound

 |

##
Boost

This is a table nested under
`
`
, it should be used as
 tags with the properties described below.

Attribute

 |
Optional

 |
Type

 |
Default Value

 |
Description

 |

endurance

 |
Yes

 |
float

 |
-

 |
 |

regeneration

 |
Yes

 |
float

 |
-

 |
 |

strength

 |
Yes

 |
float

 |
-

 |
 |

##
AirDamp

This is a table nested under
`
`
, it should be used as
 tags with the properties described below.

Attribute

 |
Optional

 |
Type

 |
Default Value

 |
Description

 |

dampAngle

 |
Yes

 |
vec3

 |
-

 |
Angle correction when in midair

 |

dampAngVel

 |
Yes

 |
vec3

 |
-

 |
Angular velocity damping when in midair

 |

##
Eject

This is a table nested under
`
`
, it should be used as
 tags with the properties described below.

Attribute

 |
Optional

 |
Type

 |
Default Value

 |
Description

 |

maxTippingAngle

 |
No

 |
float

 |
-

 |
Vehicle angle at which players are ejected (0 = don't eject)

 |

timer

 |
No

 |
float

 |
-

 |
Time vehicle has to be at that angle before ejecting players

 |

 Following are the properties specific to StdWheeled:

Attribute

 |
Optional

 |
Type

 |
Default Value

 |
Description

 |

steerSpeed

 |
No

 |
float

 |
-

 |
Turn speed for wheels at vMax

 |

steerSpeedMin

 |
No

 |
float

 |
-

 |
Initial turn speed for wheels

 |

steerSpeedScale

 |
No

 |
float

 |
-

 |
[deprecated]

 |

steerSpeedScaleMin

 |
No

 |
float

 |
-

 |
[deprecated]

 |

kvSteerMax

 |
No

 |
float

 |
-

 |
Steering angle gets reduced by this amount

 |

v0SteerMax

 |
No

 |
float

 |
-

 |
Max steering angle for wheels

 |

steerRelaxation

 |
No

 |
float

 |
-

 |
Relaxation speed

 |

vMaxSteerMax

 |
No

 |
float

 |
-

 |
Speed where steering angle is reduced by full kvSteerMax

 |

pedalLimitMax

 |
No

 |
float

 |
-

 |
Additional pedal limitation at maximum steer

 |

rpmInterpSpeed

 |
Yes

 |
float

 |
-

 |
speed for RPM interpolation

 |

rpmRelaxSpeed

 |
Yes

 |
float

 |
-

 |
speed for RPM relaxing to idle

 |

rpmGearShiftSpeed

 |
Yes

 |
float

 |
-

 |
speed for RPM relaxing during gearshifts

 |

isBreakingOnIdle

 |
Yes

 |
bool

 |
-

 |
 |

##
Wheeled

This is a table nested under
`
`
, it should be used as
 tags with the properties described below.

Attribute

 |
Optional

 |
Type

 |
Default Value

 |
Description

 |

axleFriction

 |
No

 |
int

 |
-

 |
Torque caused by internal friction in axle and gearbox, during driving

 |

axleFrictionMax

 |
Yes

 |
int

 |
-

 |
Torque caused by internal friction in axle and gearbox, during idle

 |

brakeTorque

 |
No

 |
int

 |
-

 |
Torque used when pedal is applied in reverse direction

 |

brakeImpulse

 |
Yes

 |
float

 |
-

 |
Impulse applied when pedal is applied in reverse direction

 |

clutchSpeed

 |
No

 |
float

 |
-

 |
Speed for clutch releasing

 |

damping

 |
No

 |
float

 |
-

 |
Overall damping in physics, 0 or very small usually

 |

engineIdleRPM

 |
No

 |
int

 |
-

 |
RPM when engine is idle

 |

engineMaxRPM

 |
No

 |
int

 |
-

 |
Maximum engine RPM

 |

engineMinRPM

 |
No

 |
int

 |
-

 |
Minimum engine RPM before engine stalls

 |

enginePower

 |
No

 |
int

 |
-

 |
Power in kW

 |

engineShiftDownRPM

 |
No

 |
int

 |
-

 |
Highest RPM where engine can shift down

 |

engineShiftUpRPM

 |
No

 |
int

 |
-

 |
Smallest RPM where engine can shift up

 |

engineStartRPM

 |
No

 |
int

 |
-

 |
RPM after engine started

 |

integrationType

 |
Yes

 |
float

 |
0.0

 |
Overall damping in physics, 0 or very small usually

 |

stabilizer

 |
No

 |
float

 |
-

 |
Multiplier for suspension force when opposite susps have different lengths

 |

minBrakingFriction

 |
Yes

 |
float

 |
-

 |
Minimum friction during handbrakes

 |

maxSteer

 |
No

 |
float

 |
-

 |
Maximum steering angle in radians

 |

maxTimeStep

 |
No

 |
float

 |
-

 |
Max timestep that the entity is allowed to make

 |

minEnergy

 |
No

 |
float

 |
-

 |
Minimum energy before the entity can be put asleep

 |

slipThreshold

 |
No

 |
float

 |
-

 |
Ratio at which wheels are considered slipping

 |

gearDirSwitchRPM

 |
No

 |
int

 |
-

 |
Maximum wheel rpm at which gear direction can be changed

 |

dynFriction

 |
No

 |
float

 |
-

 |
Multiplier for dynamic friction

 |

latFriction

 |
Yes

 |
float

 |
-

 |
Lateral friction multiplier

 |

steerTrackNeutralTurn

 |
Yes

 |
float

 |
-

 |
Neutral turn steering angle for tanks, should be same as maxSteer currently

 |

suspDampingMin

 |
Yes

 |
float

 |
-

 |
Suspension damping at zero speed

 |

suspDampingMax

 |
Yes

 |
float

 |
-

 |
Suspension damping at max speed

 |

suspDampingMaxSpeed

 |
Yes

 |
float

 |
-

 |
Max speed for susp damping increasing

 |

stabiMin

 |
Yes

 |
float

 |
-

 |
Stabi at 0 speed

 |

stabiMax

 |
Yes

 |
float

 |
-

 |
Stabi at max speed

 |

maxSpeed

 |
Yes

 |
float

 |
-

 |
Approximated maximum speed

 |

maxGear

 |
Yes

 |
int

 |
-

 |
Max forward gear to use

 |

maxBrakingFriction

 |
Yes

 |
float

 |
-

 |
Maximum friction during handbrakes

 |

pullTilt

 |
Yes

 |
float

 |
-

 |
Angle that driving force is tilted downwards

 |

##
gearRatios

This is an array table nested under
`
`
, it should be used as
 tags with child tags
 which of which have the properties described below.

Gear ratios. 1 backward, 2 neutral, 3 to n forward.

##
ArcadeWheeled

This is a table nested under
`
`
, it should be used as
 tags with the properties described below.

Attribute

 |
Optional

 |
Type

 |
Default Value

 |
Description

 |

isBreakingOnIdle

 |
Yes

 |
bool

 |
-

 |
 |

steerSpeed

 |
Yes

 |
float

 |
-

 |
Speed at which the wheels reach full turning lock at vMaxSteerMax

 |

steerSpeedMin

 |
Yes

 |
float

 |
-

 |
Speed at which the wheels reach full turning lock at zero speed

 |

steerSpeedScale

 |
Yes

 |
float

 |
-

 |
Scale for steering sensitivity at vMaxSteerMax

 |

steerSpeedScaleMin

 |
Yes

 |
float

 |
-

 |
Scale for steering sensitivity at zero speed

 |

kvSteerMax

 |
Yes

 |
float

 |
-

 |
Amount of steering, in degrees, subtracted from v0SteerMax when vehicle speed reaches vMaxSteerMax

 |

v0SteerMax

 |
Yes

 |
float

 |
-

 |
Maximum steering angle, in degrees, at zero speed

 |

steerRelaxation

 |
Yes

 |
float

 |
-

 |
The speed at which the wheels return to center after finishing turning

 |

vMaxSteerMax

 |
Yes

 |
float

 |
-

 |
Vehicle speed at which entire kvSteerMax is subtracted from v0SteerMax

 |

pedalLimitMax

 |
Yes

 |
float

 |
-

 |
At vMaxSteerMax pedal is clamped to 1-pedalLimitMax

 |

rpmGearShiftSpeed

 |
No

 |
float

 |
-

 |
Speed for RPM relaxing during gearshifts

 |

##
Wheeled

This is a table nested under
`
`
, it should be used as
 tags with the properties described below.

 This table can equally be called WheeledLegacy.

Attribute

 |
Optional

 |
Type

 |
Default Value

 |
Description

 |

suspDampingMin

 |
Yes

 |
float

 |
0.0

 |
Suspension damping at zero speed

 |

suspDampingMax

 |
Yes

 |
float

 |
0.0

 |
Suspension damping at max speed

 |

suspDampingMaxSpeed

 |
Yes

 |
float

 |
0.0

 |
Max speed for susp damping increasing

 |

stabiMin

 |
Yes

 |
float

 |
0.0

 |
For suspension: Stabi at 0 speed

 |

stabiMax

 |
Yes

 |
float

 |
0.0

 |
For suspension: Stabi at max speed

 |

damagedWheelSpeedInfluenceFactor

 |
Yes

 |
float

 |
0.5

 |
Factor to influence the calculation of average wheel condition. Wheel condition is a linear porportion of wheels that were not blown weighted by this factor. Sensible values range from 0 to 1. A value of 0 will result in a 'perfect' condition regardless of the number of blow wheels.

 |

damping

 |
Yes

 |
float

 |
0.0

 |
Overall damping in physics, 0 or very small usually

 |

engineIdleRPM

 |
Yes

 |
int

 |
0.0

 |
RPM when engine is idle

 |

engineMaxRPM

 |
Yes

 |
int

 |
0.0

 |
Maximum engine RPM

 |

engineMinRPM

 |
Yes

 |
int

 |
0.0

 |
Minimum engine RPM before engine stalls

 |

stabilizer

 |
Yes

 |
float

 |
0.0

 |
Multiplier for suspension force when opposite susps have different lengths

 |

integrationType

 |
Yes

 |
float

 |
0.0

 |
Overall damping in physics, 0 or very small usually

 |

maxTimeStep

 |
Yes

 |
float

 |
0.0

 |
Max timestep that the entity is allowed to make

 |

minEnergy

 |
Yes

 |
float

 |
0.0

 |
Minimum energy before the entity can be put asleep

 |

##
ViewAdjustment

This is a table nested under
`
`
, it should be used as
 tags with the properties described below.

TODO

##
ViewAdjustmentPowerLock

This is a table nested under
`
`
, it should be used as
 tags with the properties described below.

TODO

##
FakeGears

This is a table nested under
`
`
, it should be used as
 tags with the properties described below.

Attribute

 |
Optional

 |
Type

 |
Default Value

 |
Description

 |

minChangeUpTime

 |
No

 |
float

 |
-

 |
The min. time that must be spent in a gear before allowed to change up

 |

minChangeDownTime

 |
No

 |
float

 |
-

 |
The min. time that must be spent in a gear before allowed to change down

 |

rpmInterpSpeed

 |
Yes

 |
float

 |
-

 |
speed for RPM interpolation

 |

rpmRelaxSpeed

 |
Yes

 |
float

 |
-

 |
speed for RPM relaxing to idle (no throttle)

 |

gearOscillationFrequency

 |
Yes

 |
float

 |
-

 |
 |

gearOscillationAmp

 |
Yes

 |
float

 |
-

 |
 |

gearOscillationAmp2

 |
Yes

 |
float

 |
-

 |
 |

gearChangeSpeed

 |
Yes

 |
float

 |
-

 |
 |

gearChangeSpeed2

 |
Yes

 |
float

 |
-

 |
 |

rpmLoadChangeSpeedUp

 |
Yes

 |
float

 |
-

 |
RPM strain/load. How quickly to change the strain upwards

 |

rpmLoadChangeSpeedDown

 |
Yes

 |
float

 |
-

 |
RPM strain/load. How quickly to change the strain downwards

 |

rpmLoadFactor

 |
Yes

 |
float

 |
-

 |
RPM strain/load. How much rpm changes affect engine load

 |

rpmLoadFromBraking

 |
Yes

 |
float

 |
-

 |
RPM strain/load. How much the brake (alone) affects the engine load

 |

rpmLoadFromThrottle

 |
Yes

 |
float

 |
-

 |
RPM strain/load. How much the throttle (alone) affects the engine load

 |

##
Ratios

This is an array table nested under
`
`
, it should be used as
 tags with child tags
 which of which have the properties described below.

Gear ratios, specified as a fraction of the top speed (No need to specify reverse and neutral).

Attribute

 |
Optional

 |
Type

 |
Default Value

 |
Description

 |

value

 |
Yes

 |
float

 |
-

 |
 |

minChangeDownTime

 |
Yes

 |
float

 |
-

 |
 |

minChangeUpTime

 |
Yes

 |
float

 |
-

 |
 |

##
Handling

This is a table nested under
`
`
, it should be used as
 tags with the properties described below.

##
Power

This is a table nested under
`
`
, it should be used as
 tags with the properties described below.

Attribute

 |
Optional

 |
Type

 |
Default Value

 |
Description

 |

acceleration

 |
No

 |
float

 |
-

 |
Rate of acceleration

 |

decceleration

 |
No

 |
float

 |
-

 |
Rate of natural deceleration with no throttle/brake applied

 |

topSpeed

 |
No

 |
float

 |
-

 |
Top speed in meters per second

 |

reverseSpeed

 |
No

 |
float

 |
-

 |
Reversing speed in meters per second

 |

boostTopSpeed

 |
No

 |
float

 |
-

 |
 |

boostAcceleration

 |
No

 |
float

 |
-

 |
 |

##
SpeedReduction

This is a table nested under
`
`
, it should be used as
 tags with the properties described below.

Attribute

 |
Optional

 |
Type

 |
Default Value

 |
Description

 |

reductionAmount

 |
No

 |
float

 |
-

 |
Reduce top speed fractionally by this amount when steering is at steer max

 |

reductionRate

 |
No

 |
float

 |
-

 |
Rate at which to reduce the speed by

 |

##
Compression

This is a table nested under
`
`
, it should be used as
 tags with the properties described below.

Attribute

 |
Optional

 |
Type

 |
Default Value

 |
Description

 |

frictionBoost

 |
No

 |
float

 |
-

 |
Increase friction when suspension becomes compressed

 |

frictionBoostHandBrake

 |
No

 |
float

 |
-

 |
Same as frictionBoost but for when hand brake is pressed

 |

##
Friction

This is a table nested under
`
`
, it should be used as
 tags with the properties described below.

Attribute

 |
Optional

 |
Type

 |
Default Value

 |
Description

 |

back

 |
No

 |
float

 |
-

 |
Lateral friction of the back wheels

 |

front

 |
No

 |
float

 |
-

 |
Lateral friction of the front wheels (note the forward friction is internally calculated)

 |

offset

 |
No

 |
float

 |
-

 |
Vertical positional offset, where handling forces are applied for forwards and lateral friction relative to the mass box

 |

##
PowerSlide

This is a table nested under
`
`
, it should be used as
 tags with the properties described below.

Attribute

 |
Optional

 |
Type

 |
Default Value

 |
Description

 |

lateralSpeedFraction

 |
No

 |
float

 |
-

 |
 |

lateralSpeedFractionHB

 |
No

 |
float

 |
-

 |
 |

spring

 |
No

 |
float

 |
-

 |
 |

##
WheelSpin

This is a table nested under
`
`
, it should be used as
 tags with the properties described below.

Attribute

 |
Optional

 |
Type

 |
Default Value

 |
Description

 |

grip1

 |
Yes

 |
float

 |
-

 |
Grip fraction when at zero slip speed (set this to less than 1.0)

 |

grip2

 |
Yes

 |
float

 |
-

 |
Grip fraction when at high slip speed (usually 1.0, you should have grip2 > grip1)

 |

gripRecoverSpeed

 |
Yes

 |
float

 |
-

 |
Exponential slip speed needed to go from grip1 to grip2

 |

accelMultiplier1

 |
Yes

 |
float

 |
-

 |
Acceleration multiplier at zero speed (make > 1.0 for wheel spin)

 |

accelMultiplier2

 |
Yes

 |
float

 |
-

 |
Acceleration multiplier at top speed (should make this is less than 1.0)

 |

##
HandBrake

This is a table nested under
`
`
, it should be used as
 tags with the properties described below.

Attribute

 |
Optional

 |
Type

 |
Default Value

 |
Description

 |

decceleration

 |
No

 |
float

 |
-

 |
How much deceleration should the full hand brake provide

 |

deccelerationPowerLock

 |
No

 |
float

 |
-

 |
How much deceleration should the hand brake provide when the accelerator is also still pressed

 |

lockBack

 |
No

 |
bool

 |
-

 |
Should the back wheels lock

 |

lockFront

 |
No

 |
bool

 |
-

 |
Should the front wheels lock

 |

frontFrictionScale

 |
No

 |
float

 |
-

 |
How much to scale the lateral friction by, of the front wheels, when the hand brake is pressed

 |

backFrictionScale

 |
No

 |
float

 |
-

 |
How much to scale the lateral friction by, of the back wheels, when the hand brake is pressed

 |

angCorrectionScale

 |
No

 |
float

 |
-

 |
How much to scale the angSpring value by when the hand brake is pressed

 |

latCorrectionScale

 |
Yes

 |
float

 |
-

 |
How much to scale the lateralSpring value by when the hand brake is pressed

 |

##
Correction

This is a table nested under
`
`
, it should be used as
 tags with the properties described below.

Attribute

 |
Optional

 |
Type

 |
Default Value

 |
Description

 |

lateralSpring

 |
No

 |
float

 |
-

 |
Lateral damping value

 |

angSpring

 |
No

 |
float

 |
-

 |
Angular correction value

 |

##
Stabilisation

This is a table nested under
`
`
, it should be used as
 tags with the properties described below.

Attribute

 |
Optional

 |
Type

 |
Default Value

 |
Description

 |

angDamping

 |
No

 |
float

 |
-

 |
 |

rollDamping

 |
No

 |
float

 |
-

 |
 |

rollfixAir

 |
No

 |
float

 |
-

 |
 |

upDamping

 |
No

 |
float

 |
-

 |
 |

maxTiltAngleAir

 |
No

 |
float

 |
-

 |
 |

##
Inertia

This is a table nested under
`
`
, it should be used as
 tags with the properties described below.

Attribute

 |
Optional

 |
Type

 |
Default Value

 |
Description

 |

radius

 |
No

 |
float

 |
-

 |
Effect radius of the chassis. Larger values would simulate physics similar to a truck, for example.

 |

##
TankHandling

This is a table nested under
`
`
, it should be used as
 tags with the properties described below.

Attribute

 |
Optional

 |
Type

 |
Default Value

 |
Description

 |

additionalSteeringStationary

 |
Yes

 |
float

 |
-

 |
 |

additionalSteeringAtMaxSpeed

 |
Yes

 |
float

 |
-

 |
 |

additionalTilt

 |
Yes

 |
float

 |
-

 |
 |

##
keepEngineOn

See
[shared reference.](#VehicleSetup-MovementParams-StdWheeled-keepEngineOn)

##
engineIgnitionTime

See
[shared reference.](#VehicleSetup-MovementParams-StdWheeled-engineIgnitionTime)

##
Animations

See
[shared reference.](#VehicleSetup-MovementParams-StdWheeled-Animations)

##
SoundParams

This is a table nested under
`
`
, it should be used as
 tags with the properties described below.

 The common table is extended with the following params:

Attribute

 |
Optional

 |
Type

 |
Default Value

 |
Description

 |

roadBumpMinSusp

 |
Yes

 |
float

 |
-

 |
Threshold in suspension compression for bump sounds

 |

roadBumpMinSpeed

 |
Yes

 |
float

 |
-

 |
Vehicle min speed for bump sounds

 |

roadBumpIntensity

 |
Yes

 |
float

 |
-

 |
sound param

 |

airbrake

 |
Yes

 |
float

 |
-

 |
braking time threshold for airbrake sound

 |

##
Skidding

This is a table nested under
`
`
, it should be used as
 tags with the properties described below.

Attribute

 |
Optional

 |
Type

 |
Default Value

 |
Description

 |

skidLerpSpeed

 |
Yes

 |
float

 |
-

 |
How quickly to change the skid sound value

 |

skidCentrifugalFactor

 |
Yes

 |
float

 |
-

 |
Effect from centrifugal force

 |

skidBrakeFactor

 |
Yes

 |
float

 |
-

 |
Change due to braking alone

 |

skidPowerLockFactor

 |
Yes

 |
float

 |
-

 |
Change due to handbrake whilst accelerating (power-lock)

 |

skidForwardFactor

 |
Yes

 |
float

 |
-

 |
How much wheel forward slipping affects the skidding

 |

skidLateralfactor

 |
Yes

 |
float

 |
-

 |
How much wheel side slipping affects the skidding

 |

See the
[common table reference](#VehicleSetup-MovementParams-StdWheeled-SoundParams)
.

##
Boost

See
[shared reference.](#VehicleSetup-MovementParams-StdWheeled-Boost)

##
AirDamp

See
[shared reference.](#VehicleSetup-MovementParams-StdWheeled-AirDamp)

##
StdTank

This is a table nested under
`
`
, it should be used as
 tags with the properties described below.

Extension of the StdWheeled movement type.

TODO

##
Tank

This is a table nested under
`
`
, it should be used as
 tags with the properties described below.

TODO

##
StdBoat

This is a table nested under
`
`
, it should be used as
 tags with the properties described below.

Attribute

 |
Optional

 |
Type

 |
Default Value

 |
Description

 |

velMax

 |
Yes

 |
float

 |
15.0

 |
 |

velMaxReverse

 |
Yes

 |
float

 |
5.0

 |
 |

acceleration

 |
Yes

 |
float

 |
5.0

 |
 |

accelerationVelMax

 |
Yes

 |
float

 |
-

 |
 |

accelerationMultiplier

 |
Yes

 |
float

 |
2.0

 |
 |

pushTilt

 |
Yes

 |
float

 |
0.0

 |
 |

turnRateMax

 |
Yes

 |
float

 |
1.0

 |
 |

turnAccel

 |
Yes

 |
float

 |
1.0

 |
 |

cornerForce

 |
Yes

 |
float

 |
1.0

 |
 |

cornerTilt

 |
Yes

 |
float

 |
0.0

 |
 |

turnDamping

 |
Yes

 |
float

 |
0.0

 |
 |

turnAccelMultiplier

 |
Yes

 |
float

 |
2.0

 |
 |

rollAccel

 |
Yes

 |
float

 |
0.0

 |
 |

pedalLimitReverse

 |
Yes

 |
float

 |
1.0

 |
 |

turnVelocityMult

 |
Yes

 |
float

 |
1.0

 |
 |

velLift

 |
Yes

 |
float

 |
0.0

 |
 |

lateralDamping

 |
Yes

 |
float

 |
0.0

 |
 |

waveIdleStrength

 |
Yes

 |
vec3

 |
0.0, 0.0, 0.0

 |
 |

waveSpeedMult

 |
Yes

 |
float

 |
0.0

 |
 |

cornerHelper

 |
Yes

 |
string

 |
-

 |
 |

pushHelper

 |
Yes

 |
string

 |
-

 |
 |

waveEffect

 |
Yes

 |
string

 |
-

 |
 |

##
keepEngineOn

See
[shared reference.](#VehicleSetup-MovementParams-StdWheeled-keepEngineOn)

##
engineIgnitionTime

See
[shared reference.](#VehicleSetup-MovementParams-StdWheeled-engineIgnitionTime)

##
Animations

See
[shared reference.](#VehicleSetup-MovementParams-StdWheeled-Animations)

##
SoundParams

See
[shared reference.](#VehicleSetup-MovementParams-StdWheeled-SoundParams)

##
Boost

See
[shared reference.](#VehicleSetup-MovementParams-StdWheeled-Boost)

##
AirDamp

See
[shared reference.](#VehicleSetup-MovementParams-StdWheeled-AirDamp)

##
Helicopter

This is a table nested under
`
`
, it should be used as
 tags with the properties described below.

TODO

##
DummyMovement

This is a table nested under
`
`
, it should be used as
 tags with the properties described below.

empty - no specific attributes. Note: 'DummyMovement' also does not read the common movement properties

##
Damages

This is a table nested under
`
`
, it should be used as
 tags with the properties described below.

Attribute

 |
Optional

 |
Type

 |
Default Value

 |
Description

 |

submergedRatioMax

 |
Yes

 |
float

 |
-

 |
 |

submergedDamageMult

 |
Yes

 |
float

 |
-

 |
 |

collDamageThreshold

 |
Yes

 |
float

 |
50.0

 |
Is subtracted from collision damage before it is applied

 |

groundCollisionMinMult

 |
Yes

 |
float

 |
-

 |
Increases damage when falling onto ground. Use together with minSpeed and maxSpeed

 |

groundCollisionMaxMult

 |
Yes

 |
float

 |
-

 |
 |

groundCollisionMinSpeed

 |
Yes

 |
float

 |
-

 |
 |

groundCollisionMaxSpeed

 |
Yes

 |
float

 |
-

 |
 |

vehicleCollisionDestructionSpeed

 |
Yes

 |
float

 |
-

 |
If colliding with another vehicle with closing speed above this, self will be destroyed

 |

aiKillPlayerSpeed

 |
Yes

 |
float

 |
-

 |
AI driven vehicles kill players if colliding above this speed

 |

playerKillAISpeed

 |
Yes

 |
float

 |
-

 |
Player driven vehicles kill AI if colliding above this speed

 |

aiKillAISpeed

 |
Yes

 |
float

 |
-

 |
AI driven vehicles kill AI of other factions if colliding above this speed

 |

##
DamageMultipliers

This is an array table nested under
`
`
, it should be used as
 tags with child tags
 which of which have the properties described below.

Attribute

 |
Optional

 |
Type

 |
Default Value

 |
Description

 |

damageType

 |
Yes

 |
string

 |
-

 |
Supply damage or ammoType and the multplier and splash value

 |

ammoType

 |
Yes

 |
string

 |
-

 |
Supply damage or ammoType and the multplier and splash value

 |

multiplier

 |
Yes

 |
float

 |
-

 |
 |

splash

 |
Yes

 |
float

 |
-

 |
 |

##
DamagesGroups

This is an array table nested under
`
`
, it should be used as
 tags with child tags
 which of which have the properties described below.

Attribute

 |
Optional

 |
Type

 |
Default Value

 |
Description

 |

name

 |
Yes

 |
string

 |
-

 |
Used as identifier, must be unique

 |

useTemplate

 |
Yes

 |
string

 |
-

 |
Template name from one defined in DefaultVehicleDamages.xml or in another file in the same folder. Templates define DamagesSubGroups and can use templates themselves, forming the final array of SubGroups with DamageBehaviors.

 |

##
DamagesSubGroups

This is an array table nested under
`
`
, it should be used as
 tags with child tags
 which of which have the properties described below.

Attribute

 |
Optional

 |
Type

 |
Default Value

 |
Description

 |

delay

 |
Yes

 |
float

 |
0.0

 |
 |

randomness

 |
Yes

 |
float

 |
0.0

 |
 |

##
DamageBehaviors

This is an array table nested under
`
`
, it should be used as
 tags with child tags
 which of which have the properties described below.

 A DamageBehavior must define a 'class' property. According to the specified class, there are different properties and subtables that can be used to configure it.

Attribute

 |
Optional

 |
Type

 |
Default Value

 |
Description

 |

class

 |
Yes

 |
string

 |
-

 |
 Possible values are:

-
'AISignal'

-
'Destroy'

-
'DetachPart'

-
'DisableSeatAction'

-
'Effect'

-
'Group'

-
'HitPassenger'

-
'Impulse'

-
'Indicator'

-
'MovementNotification'

-
'Sink'

-
'SpawnDebris'

-
'AudioFeedback'

-
'Burn'

-
'CameraShake'

-
'Explosion'

-
'BlowTire'
 |

 Common to all
 tags:

Attribute

 |
Optional

 |
Type

 |
Default Value

 |
Description

 |

damageRatioMin

 |
Yes

 |
float

 |
1.0

 |
The damage behavior will only be triggered when the damage ratio is between damageRatioMin and damageRatioMax, e.g. to only trigger the behavior when the vehicle is more than half destroyed, set this value to 0.5

 |

damageRatioMax

 |
Yes

 |
float

 |
0.0

 |
This damage behavior will apply when the damage ratio is between damageRatioMin and damageRatioMax. When the vehicle has more damage than damageRatioMax, the behavior is cut short.

 |

ignoreVehicleDestruction

 |
Yes

 |
bool

 |
0 (false)

 |
Do not react to vehicle destruction

 |

 Class specific properties:

##
Class AISignal

AISignal

This is a table nested under
`
`
, it should be used as
 tags with the properties described below.

Sends a signal to the AI system and a free signal to the vehicles entity AI on hit.

Attribute

 |
Optional

 |
Type

 |
Default Value

 |
Description

 |

signalId

 |
Yes

 |
int

 |
-

 |
 |

signalText

 |
Yes

 |
string

 |
-

 |
 |

freeSignalText

 |
Yes

 |
string

 |
-

 |
 |

freeSignalRadius

 |
Yes

 |
float

 |
15.0

 |
 |

freeSignalRepeat

 |
Yes

 |
bool

 |
0 (false)

 |
 |

##
Class Destroy

 Notifies all vehicle systems and components of a vehicle destruction event. This behavior triggers other damage behaviors that react to vehicle destruction and hooks with
					the lua 'OnVehicleDestroyed' function. Destroy also adds a 'DetachPart' damage behavior to all vehicle parts of type 'AnimatedJoint'.

Attribute

 |
Optional

 |
Type

 |
Default Value

 |
Description

 |

effect

 |
Yes

 |
string

 |
-

 |
Name of the particle effect used for the 'DetachPart' behavior generated for AnimatedJoint parts

 |

##
Class DetachPart

DetachPart

This is a table nested under
`
`
, it should be used as
 tags with the properties described below.

Detaches this part and its children from the vehicle with an impulse. The behavior is applicable to any part type as long as it has static geometry and is subject to some randomness for variability.

Attribute

 |
Optional

 |
Type

 |
Default Value

 |
Description

 |

part

 |
Yes

 |
string

 |
-

 |
Name of the part to detach

 |

notifyMovement

 |
Yes

 |
bool

 |
0 (false)

 |
Notifies the vehicles active movement type of the detached part

 |

effect

 |
Yes

 |
string

 |
-

 |
Name of the effect to find in the ParticleManager

 |

pickable

 |
Yes

 |
bool

 |
0 (false)

 |
If the part will be pickable after it has been detached

 |

##
Class DisableSeatAction

DisableSeatAction

This is a table nested under
`
`
, it should be used as
 tags with the properties described below.

Disables all actions or a specific action on a seat.

Attribute

 |
Optional

 |
Type

 |
Default Value

 |
Description

 |

seat

 |
Yes

 |
string

 |
-

 |
The name of the seat holding the action to be disabled

 |

actionName

 |
Yes

 |
string

 |
-

 |
The name of the action to be disabled, or 'all'

 |

##
Class Effect

 Spawn a particle effect

Effect

This is a table nested under
`
`
, it should be used as
 tags with the properties described below.

Attribute

 |
Optional

 |
Type

 |
Default Value

 |
Description

 |

effect

 |
Yes

 |
string

 |
-

 |
Name of the particle effect

 |

disableAfterExplosion

 |
Yes

 |
string

 |
0

 |
Set to true if the effect should stop after the vehicle explodes when destroyed

 |

updateFromHelper

 |
Yes

 |
string

 |
0

 |
Set to true if the effect needs an update tick

 |

##
Class Group

Group

This is a table nested under
`
`
, it should be used as
 tags with the properties described below.

Broadcast damage event to a Damage Group. This is useful to trigger already setup damage groups from different components and other groups.

Attribute

 |
Optional

 |
Type

 |
Default Value

 |
Description

 |

name

 |
Yes

 |
string

 |
-

 |
Name of the damage group to broadcast the damage event to

 |

##
Class HitPassenger

HitPassenger

This is a table nested under
`
`
, it should be used as
 tags with the properties described below.

Applies damage to all actors seating in the vehicle for every hit the vehicle receives.

Attribute

 |
Optional

 |
Type

 |
Default Value

 |
Description

 |

damage

 |
Yes

 |
int

 |
0

 |
Damage value to apply to all actors seating in the vehicle

 |

isDamagePercent

 |
Yes

 |
bool

 |
0 (false)

 |
If damage is in absolute values or a percentage of the actor's health

 |

##
Class Impulse

Impulse

This is a table nested under
`
`
, it should be used as
 tags with the properties described below.

Applies a physics impulse to the vehicle.

Attribute

 |
Optional

 |
Type

 |
Default Value

 |
Description

 |

forceMin

 |
Yes

 |
float

 |
0.0

 |
The impulse's force will be randomly generated from an interval between forceMin and forceMax

 |

forceMax

 |
Yes

 |
float

 |
0.0

 |
The impulse's force will be randomly generated from an interval between forceMin and forceMax

 |

direction

 |
Yes

 |
vec3

 |
0.0, 0.0, 0.0

 |
Direction of the impulse applied to the vehicle

 |

momentum

 |
Yes

 |
vec3

 |
0.0, 0.0, 0.0

 |
Angular impulse

 |

worldSpace

 |
Yes

 |
bool

 |
0 (false)

 |
If the impulse's direction and momentum is already in world space of if it is relative to the vehicle

 |

helper

 |
Yes

 |
string

 |
-

 |
Name of the helper to position the impulse

 |

##
Class Indicator

Indicator

This is a table nested under
`
`
, it should be used as
 tags with the properties described below.

Light or sound indicator according to damage ratio.

Light

This is a table nested under
`
`
, it should be used as
 tags with the properties described below.

Attribute

 |
Optional

 |
Type

 |
Default Value

 |
Description

 |

material

 |
Yes

 |
string

 |
-

 |
 |

sound

 |
Yes

 |
string

 |
-

 |
 |

soundRatioMin

 |
Yes

 |
float

 |
-

 |
 |

helper

 |
Yes

 |
string

 |
-

 |
 |

##
Class MovementNotification

MovementNotification

This is a table nested under
`
`
, it should be used as
 tags with the properties described below.

Sends a notification to the active movement type on Hit and Repair.

Attribute

 |
Optional

 |
Type

 |
Default Value

 |
Description

 |

isSteering

 |
Yes

 |
bool

 |
0 (false)

 |
Information to pass to the active movement type. If steering is involved

 |

isFatal

 |
Yes

 |
bool

 |
1 (true)

 |
Information to pass to the active movement type. If the damage is fatal

 |

param

 |
Yes

 |
int

 |
0

 |
Information to pass to the active movement type.

 |

isDamageAlwaysFull

 |
Yes

 |
bool

 |
0 (false)

 |
If true, the behavior acts as if the damage value was 100%

 |

##
Class Sink

 Sinks the vehicle if on water (typically a boat). This behavior is applied when the vehicle is destroyed.

empty - no specific attributes

##
Class SpawnDebris

SpawnDebris

This is a table nested under
`
`
, it should be used as
 tags with the properties described below.

This a behavior applied to the entire vehicle on destruction. When triggered, this behavior spawns geometry with a randomized impulse and an optional particle effect. The debris is automatically generated from all the vehicle animated parts that have a configured destroyed geometry. The geometry will be spawned from the joint the part is attached to.

Attribute

 |
Optional

 |
Type

 |
Default Value

 |
Description

 |

pickable

 |
Yes

 |
bool

 |
0 (false)

 |
If the part will be pickable after it has been detached

 |

effect

 |
Yes

 |
string

 |
-

 |
Name of the effect to find in the ParticleManager

 |

##
Class AudioFeedback

Sound

This is a table nested under
`
`
, it should be used as
 tags with the properties described below.

Attribute

 |
Optional

 |
Type

 |
Default Value

 |
Description

 |

firstPersonSignal

 |
Yes

 |
string

 |
-

 |
Name of the signal to be played when the player is in first person

 |

thirdPersonSignal

 |
Yes

 |
string

 |
-

 |
Name of the signal to be played when the player is in third person

 |

##
Class Burn

Burn

This is a table nested under
`
`
, it should be used as
 tags with the properties described below.

Generates a controlled explosion during 60sec that will apply damage to nearby actors.

Attribute

 |
Optional

 |
Type

 |
Default Value

 |
Description

 |

helper

 |
Yes

 |
string

 |
-

 |
 |

damage

 |
Yes

 |
float

 |
0.0

 |
 |

selfDamage

 |
Yes

 |
float

 |
0.0

 |
 |

radius

 |
Yes

 |
float

 |
0.0

 |
 |

interval

 |
Yes

 |
float

 |
0.0

 |
 |

##
Class CameraShake

 Shakes the passenger's camera on hit.

empty - no specific attributes

##
Class Explosion

Explosion

This is a table nested under
`
`
, it should be used as
 tags with the properties described below.

Generate an explosion on vehicle destruction.

Attribute

 |
Optional

 |
Type

 |
Default Value

 |
Description

 |

helper

 |
Yes

 |
string

 |
-

 |
 |

damage

 |
Yes

 |
float

 |
0.0

 |
 |

radius

 |
Yes

 |
float

 |
0.0

 |
 |

minRadius

 |
Yes

 |
float

 |
half of 'radius'

 |
 |

physRadius

 |
Yes

 |
float

 |
the smallest value between 'radius' or 5.0

 |
 |

minPhysRadius

 |
Yes

 |
float

 |
half of 'phyRadius'

 |
 |

pressure

 |
Yes

 |
float

 |
0.0

 |
 |

soundRadius

 |
Yes

 |
float

 |
0.0

 |
 |

##
Class BlowTire

 Makes a wheel disappear with particle effects and a physics impulse. Use on a component which belongs to a SubPartWheel part for full effect.

empty - no specific attributes

##
Particles

This is a table nested under
`
`
, it should be used as
 tags with the properties described below.

Attribute

 |
Optional

 |
Type

 |
Default Value

 |
Description

 |

mfxRow

 |
Yes

 |
string

 |
vfx_VEHICLECLASSNAME

 |
The rowname to use for environment layer effects in MaterialEffects.xml

 |

##
Exhaust

This is a table nested under
`
`
, it should be used as
 tags with the properties described below.

Attribute

 |
Optional

 |
Type

 |
Default Value

 |
Description

 |

insideWater

 |
Yes

 |
bool

 |
0 (false)

 |
If true, exhaust is spawned when helper position is inside water

 |

outsideWater

 |
Yes

 |
bool

 |
1 (true)

 |
If true, exhaust is spawned when helper position is outside water

 |

##
Helpers

This is an array table nested under
`
`
, it should be used as
 tags with child tags
 which of which have the properties described below.

1 or more helpers where exhaust is spawned.

Attribute

 |
Optional

 |
Type

 |
Default Value

 |
Description

 |

value

 |
Yes

 |
string

 |
-

 |
Name of the helper

 |

##
EngineStart

This is a table nested under
`
`
, it should be used as
 tags with the properties described below.

Attribute

 |
Optional

 |
Type

 |
Default Value

 |
Description

 |

effect

 |
No

 |
string

 |
-

 |
Name of particle effect (e.g. vehicle_fx.exhaust.smoke_start)

 |

##
EngineStop

This is a table nested under
`
`
, it should be used as
 tags with the properties described below.

Attribute

 |
Optional

 |
Type

 |
Default Value

 |
Description

 |

effect

 |
No

 |
string

 |
-

 |
Name of particle effect (e.g. vehicle_fx.exhaust.smoke_stop)

 |

##
EngineRunning

This is a table nested under
`
`
, it should be used as
 tags with the properties described below.

Attribute

 |
Optional

 |
Type

 |
Default Value

 |
Description

 |

effect

 |
Yes

 |
string

 |
-

 |
Name of particle effect (e.g. vehicle_fx.exhaust.smoke_running)

 |

boostEffect

 |
Yes

 |
string

 |
-

 |
Additional effect for boost mode

 |

baseSizeScale

 |
Yes

 |
float

 |
-

 |
Base scale applied to the effect

 |

minSpeed

 |
Yes

 |
float

 |
-

 |
Minimum vehicle speed necessary for exhaust spawn

 |

minSpeedSizeScale

 |
Yes

 |
float

 |
-

 |
Size scale multiplier at minimum speed

 |

minSpeedCountScale

 |
Yes

 |
float

 |
-

 |
Count scale multiplier at minimum speed

 |

minSpeedSpeedScale

 |
Yes

 |
float

 |
-

 |
Emitter speed scale multiplier at minimum speed

 |

maxSpeed

 |
Yes

 |
float

 |
-

 |
Maximum vehicle speed allowed for exhaust spawn

 |

maxSpeedSizeScale

 |
Yes

 |
float

 |
-

 |
Size scale multiplier at max speed

 |

maxSpeedCountScale

 |
Yes

 |
float

 |
-

 |
Count scale multiplier at max speed

 |

maxSpeedSpeedScale

 |
Yes

 |
float

 |
-

 |
Emitter speed scale multiplier at max speed

 |

minPower

 |
Yes

 |
float

 |
-

 |
Min power (ie. pedal/load) necessary for spawn

 |

minPowerSizeScale

 |
Yes

 |
float

 |
-

 |
Size scale multiplier at min power

 |

minPowerCountScale

 |
Yes

 |
float

 |
-

 |
Count scale multiplier at min power

 |

minPowerSpeedScale

 |
Yes

 |
float

 |
-

 |
Emitter speed scale multiplier at min power

 |

maxPower

 |
Yes

 |
float

 |
-

 |
Max power (ie. load/pedal) allowed for spawn

 |

maxPowerSizeScale

 |
Yes

 |
float

 |
-

 |
Size scale multiplier at max power

 |

maxPowerCountScale

 |
Yes

 |
float

 |
-

 |
Count scale multiplier at min power

 |

maxPowerSpeedScale

 |
Yes

 |
float

 |
-

 |
Emitter speed scale multiplier at max power

 |

disableWithNegativePower

 |
Yes

 |
bool

 |
-

 |
Since the power params are applied on an absolute power value, this option can be used to turn off the exhaust when used with negative power value

 |

##
DamageEffects

This is an array table nested under
`
`
, it should be used as
 tags with child tags
 which of which have the properties described below.

Attribute

 |
Optional

 |
Type

 |
Default Value

 |
Description

 |

name

 |
Yes

 |
string

 |
-

 |
 |

effect

 |
Yes

 |
string

 |
-

 |
 |

helper

 |
Yes

 |
string

 |
-

 |
 |

gravityDirection

 |
Yes

 |
vec3

 |
-

 |
 |

pulsePeriod

 |
Yes

 |
float

 |
-

 |
 |

*
scaleMax *
*

 |
*
No
*

 |
*
float
*

 |
*
-
*

 |
*

*

 |

* This attribute is deprecated, it will be removed in the next major version

##
EnvironmentLayers

This is an array table nested under
`
`
, it should be used as
 tags with child tags
 which of which have the properties described below.

Attribute

 |
Optional

 |
Type

 |
Default Value

 |
Description

 |

name

 |
Yes

 |
string

 |
-

 |
Optional layer name. Possible values are: {'slip', 'spray', 'rims', }

 |

active

 |
Yes

 |
bool

 |
1 (true)

 |
Initial active state

 |

minSpeed

 |
Yes

 |
float

 |
0.0

 |
Minimum driving speed

 |

minSpeedSizeScale

 |
Yes

 |
float

 |
10.0

 |
Size scale at min speed

 |

minSpeedCountScale

 |
Yes

 |
float

 |
1.0

 |
Count scale at min speed

 |

minSpeedSpeedScale

 |
Yes

 |
float

 |
1.0

 |
Emitter speed scale at min speed

 |

maxSpeed

 |
Yes

 |
float

 |
1.0

 |
Speed at which particle scale reaches maxSpeed scale parameters

 |

maxSpeedSizeScale

 |
Yes

 |
float

 |
1.0

 |
Size scale at max speed

 |

maxSpeedCountScale

 |
Yes

 |
float

 |
1.0

 |
Count scale at max speed

 |

maxSpeedSpeedScale

 |
Yes

 |
float

 |
1.0

 |
Emitter speed scale at max speed

 |

minPowerSizeScale

 |
Yes

 |
float

 |
1.0

 |
Size scale multiplier at min power

 |

minPowerCountScale

 |
Yes

 |
float

 |
1.0

 |
Count scale multiplier at min power

 |

minPowerSpeedScale

 |
Yes

 |
float

 |
1.0

 |
Emitter speed scale multiplier at min power

 |

maxPowerSizeScale

 |
Yes

 |
float

 |
1.0

 |
Size scale multiplier at max power

 |

maxPowerCountScale

 |
Yes

 |
float

 |
1.0

 |
Count scale multiplier at max power

 |

maxPowerSpeedScale

 |
Yes

 |
float

 |
1.0

 |
Emitter speed scale multiplier at max power

 |

##
Alignment

This is a table nested under
`
`
, it should be used as
 tags with the properties described below.

Attribute

 |
Optional

 |
Type

 |
Default Value

 |
Description

 |

alignGroundHeight

 |
Yes

 |
float

 |
-

 |
If this is greater 0, the effect will align to the terrain (and water) and spawn up to the specified height

 |

maxHeightSizeScale

 |
No

 |
float

 |
-

 |
 |

maxHeightCountScale

 |
No

 |
float

 |
-

 |
 |

alignToWater

 |
No

 |
bool

 |
-

 |
If true, effect will always be spawned at water level

 |

##
Emitters

This is an array table nested under
`
`
, it should be used as
 tags with child tags
 which of which have the properties described below.

Each helper specifies one emitter position. Note that WheelGroups overwrite this, and ground-aligned effects always use the entity center.

Attribute

 |
Optional

 |
Type

 |
Default Value

 |
Description

 |

value

 |
Yes

 |
string

 |
-

 |
 |

##
Wheels

This is a table nested under
`
`
, it should be used as
 tags with the properties described below.

Attribute

 |
Optional

 |
Type

 |
Default Value

 |
Description

 |

all

 |
Yes

 |
bool

 |
0 (false)

 |
Generate groups for all wheels (In this case, do not specify WheelGroups)

 |

allActive

 |
Yes

 |
bool

 |
1 (true)

 |
Initial active state for all WheelGroups in case 'all' parameter is used

 |

##
WheelGroups

This is an array table nested under
`
`
, it should be used as
 tags with child tags
 which of which have the properties described below.

A group can contain one or more wheel indices. Each group receives one emitter.

Attribute

 |
Optional

 |
Type

 |
Default Value

 |
Description

 |

active

 |
Yes

 |
bool

 |
1 (true)

 |
Initial active state for the group

 |

##
Wheels

This is an array table nested under
`
`
, it should be used as
 tags with child tags
 which of which have the properties described below.

Attribute

 |
Optional

 |
Type

 |
Default Value

 |
Description

 |

value

 |
Yes

 |
int

 |
0

 |
 |

##
Splashes (deprecated)

This is a table nested under
`
`
, however it is deprecated and it should no longer be used.

##
Animations

This is an array table nested under
`
`
, it should be used as
 tags with child tags
 which of which have the properties described below.

Attribute

 |
Optional

 |
Type

 |
Default Value

 |
Description

 |

name

 |
Yes

 |
string

 |
-

 |
 |

part

 |
Yes

 |
string

 |
-

 |
Name of the part, it must be of type Animated or AnimatedChar

 |

##
States

This is an array table nested under
`
`
, it should be used as
 tags with child tags
 which of which have the properties described below.

Attribute

 |
Optional

 |
Type

 |
Default Value

 |
Description

 |

name

 |
Yes

 |
string

 |
-

 |
 |

animation

 |
Yes

 |
string

 |
-

 |
 |

sound

 |
Yes

 |
string

 |
-

 |
 |

soundHelper

 |
Yes

 |
string

 |
-

 |
 |

isLooped

 |
Yes

 |
bool

 |
-

 |
 |

isLoopedEx

 |
Yes

 |
bool

 |
false

 |
 |

speedDefault

 |
Yes

 |
float

 |
-

 |
 |

speedMin

 |
Yes

 |
float

 |
-

 |
 |

speedMax

 |
Yes

 |
float

 |
-

 |
 |

##
Materials

This is an array table nested under
`
`
, it should be used as
 tags with child tags
 which of which have the properties described below.

Attribute

 |
Optional

 |
Type

 |
Default Value

 |
Description

 |

name

 |
Yes

 |
string

 |
-

 |
 |

setting

 |
Yes

 |
string

 |
-

 |
 |

min

 |
Yes

 |
float

 |
0.001

 |
 |

max

 |
Yes

 |
float

 |
0.999

 |
 |

invertValue

 |
Yes

 |
bool

 |
-

 |
 |

##
Mannequin

This is a table nested under
`
`
, it should be used as
 tags with the properties described below.

Attribute

 |
Optional

 |
Type

 |
Default Value

 |
Description

 |

tag

 |
Yes

 |
string

 |
-

 |
 |

controllerDef

 |
Yes

 |
string

 |
-

 |
 |

vehicleADB

 |
Yes

 |
string

 |
-

 |
 |

passengerADB

 |
Yes

 |
string

 |
-

 |
 |

##
Paints

This is an array table nested under
`
`
, it should be used as
 tags with child tags
 which of which have the properties described below.

Attribute

 |
Optional

 |
Type

 |
Default Value

 |
Description

 |

name

 |
Yes

 |
string

 |
-

 |
Name for the paint, this will be used as an identifier. It must be supplied and unique

 |

material

 |
Yes

 |
string

 |
-

 |
Material to apply to the vehicle

 |

materialDestroyed

 |
Yes

 |
string

 |
-

 |
Material to use for the destroyed vehicle

 |

##
Modifications

This is an array table nested under
`
`
, it should be used as
 tags with child tags
 which of which have the properties described below.

Attribute

 |
Optional

 |
Type

 |
Default Value

 |
Description

 |

name

 |
Yes

 |
string

 |
-

 |
Name for the modification, this will be used as an identifier. It must be supplied and unique

 |

parent

 |
Yes

 |
string

 |
-

 |
Name of another modification to be applied as well. This allows the creation of hierarchies of base and specialized modifications

 |

##
Elems

This is an array table nested under
`
`
, it should be used as
 tags with child tags
 which of which have the properties described below.

Attribute

 |
Optional

 |
Type

 |
Default Value

 |
Description

 |

idRef

 |
Yes

 |
string

 |
-

 |
Id of the part to modify

 |

name

 |
Yes

 |
string

 |
-

 |
Name of the attribute to modify

 |

value

 |
Yes

 |
string

 |
-

 |
Value to set the attribute to. The use of this parameter is required, but it can still have an empty value to, for eg. unload a .cgf

 |

##
Inventory

This is a table nested under
`
`
, it should be used as
 tags with the properties described below.

##
AmmoTypes

This is an array table nested under
`
`
, it should be used as
 tags with child tags
 which of which have the properties described below.

Attribute

 |
Optional

 |
Type

 |
Default Value

 |
Description

 |

type

 |
Yes

 |
string

 |
-

 |
 |

capacity

 |
Yes

 |
int

 |
0

 |
 |

##
Materials (deprecated)

This is a table nested under
`
`
, however it is deprecated and it should no longer be used.

 Use instead the 'Paints' system to modify the look of the vehicle.

##
WheelMaster (deprecated)

This is a table nested under
`
`
, however it is deprecated and it should no longer be used.

##
DamageExtensions (deprecated)

This is a table nested under
`
`
, however it is deprecated and it should no longer be used.

##
SpecialLocations (deprecated)

This is an array table nested under
`
`
, however it is deprecated and it should no longer be used.

[Global vehicle properties](#global-vehicle-properties)
[Physics](#physics)
[Components](#components)
[Parts](#parts)
[Helpers](#helpers)
[Actions](#actions)
[Seats](#seats)
[SeatGroups](#seatgroups)
[MovementParams](#movementparams)
[Damages](#damages)
[Particles](#particles)
[Animations](#animations)
[Mannequin](#mannequin)
[Paints](#paints)
[Modifications](#modifications)
[Inventory](#inventory)
[Materials (deprecated)](#materials-deprecated)
[WheelMaster (deprecated)](#wheelmaster-deprecated)
[DamageExtensions (deprecated)](#damageextensions-deprecated)
[SpecialLocations (deprecated)](#speciallocations-deprecated)
