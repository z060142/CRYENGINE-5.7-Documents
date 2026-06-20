# Procedural Clip Directory

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/29798726
- Page ID: 29798726
- Breadcrumb: Editor Tools > Animation Tab > Mannequin Editor > Mannequin Concepts > Mannequin Procedural Clips > Procedural Clip Directory
- Parent: Mannequin Procedural Clips

## Content

[Image: /docs/static/attachments/29934029]

##
Overview

This is a list of types of
[/docs/static/engines/cryengine-5/categories/23756816/pages/29450878](
Procedural Clips
)
 present in the engine as well as in the GameSDK sample.

##
Engine (CryAction)

##
ActionEvent

Sends a CryMannequin event to the action controlling this fragment. (for programmers: calls IAction::OnActionEvent)

**
Event Name
**
 |
The name of the event to send.
 |

##
AimPose

Low level procedural clip to start an
[/docs/static/engines/cryengine-5/categories/23756816/pages/23308006](
aimpose
)
 asset. This is
**
*
NOT
*

**
related to the Aiming/Looking setup described in the tutorial
[/docs/static/engines/cryengine-5/categories/23756816/pages/23308487](
Tutorial - Controlling Looking (and Aiming) for AI in Mannequin
)
.

**
Animation
**
 |
The aimpose asset
 |

**
Blend
**
 |
The fade-in duration
 |

**
Blend Time
**
 |
The "smoothing time" for the spherical coordinates (the higher the number the quicker the longitude/latitude will smoothly move towards the target)
 |

**
Animation Layer
**
 |
The CryAnimation layer (0-16) to play the aimpose on

This works differently than the layer parameter inside the AimPose procedural clip, which is a layer index relative to the scope's first animation layer.
 |

Uses the
[/docs/static/engines/cryengine-5/categories/23756816/pages/29450867](
parameter
)
 called "AimTarget" as the target, if it exists. If not specified the target is 10m in front of the entity.

##
AISignal

Sends an AI signal directly to the AI actor interface of the entity on which the clip is playing.

**
EnterAndExitSignalNames
**
 |
Signal names sent on Enter and Exit (start and finish) of this procedural clip, separated by a '|' character
 |

##
AttachEntity

Attaches an entity to a specific attachment point (and detaches it on exit)

**
Attachment Name
**
 |
The name of the attachment point
 |

**
Param Name with EntityId
**
 |
The name of the
[/docs/static/engines/cryengine-5/categories/23756816/pages/29450867](
parameter
)
 which stores the EntityID of the entity to attach
 |

##
AttachProp

Attaches a chr, skel or cga to a specific attachment point (and detaches on exit)

**
Object Filename
**
 |
Name of the chr, skel or cga to attach
 |

**
Attachment Name
**
 |
The name of the attachment point
 |

##
Audio

(new since CRYENGINE 3.7)

Execute audio translation layer (ATL) triggers.

**
Start Trigger
**
 |
(optional) ATL trigger to execute at the start
 |

**
Stop Trigger
**
 |
(optional) ATL trigger to execute at the end
 |

**
Attachment Joint
**
 |
(optional) Name of a joint where to execute the trigger
 |

**
AI Radius
**
 |
(not implemented in 3.7.0)
 |

**
Is Voice
**
 |
(not implemented in 3.7.0)
 |

**
Play Facial
**
 |
Request facial animation to match the sound
 |

**
Sound Flags
**
 |
(reserved)
 |

##
ForceFeedback

Plays a forcefeedback effect.

**
ForceFeedbackID
**
 |

 |

**
Scale
**
 |

 |

**
Delay
**
 |

 |

**
OnlyLocal
**
 |
Trigger force feedback only locally (not on remote players)
 |

##
FlowGraphEvent

(new since CRYENGINE 3.7)

Sends events to the flownode
`
Actor ProcClipEventListener
`
.

**
Enter Event Name
**
 |
Name of event to send at start
 |

**
Exit Event Name
**
 |
Name of event to send at end
 |

##
HideAttachment

(new since CRYENGINE 3.7)

Hides an attachment for the duration of the clip.

**
Attachment Name
**
 |
Name of the character attachment to hide
 |

##
IKLayerWeight

(new since CRYENGINE 3.7)

Controls the weight of a CryAnimation layer by a joint's x value. This might be following along with a joint driving an animation driven IK, hence the name of this clip.

**
Joint Name
**
 |
The joint whose x value will be controlling the layer weight
 |

**
Scope Layer
**
 |
The index of the layer within this scope that this clip should control
 |

**
Invert
**
 |
Use one minus the value as the weight
 |

##
JointAdjust

(new since CRYENGINE 3.7)

Adjust a joint's position. (under the hood this uses an operatorqueue pose modifier)

**
Joint Name
**
 |
The joint to adjust
 |

**
Scope Layer
**
 |
The index of the layer within this scope before which you want to execute this adjustment
 |

**
Additive
**
 |

 |

**
Relative to Parent
**
 |

 |

**
Position
**
 |

 |

##
LayerAnimSpeed

Controls the
*
speed
*
 of an animation that is playing in the same scope as this procedural clip through code.

**
LayerAnimSpeedParam
**
 |
The name of the floating point
[/docs/static/engines/cryengine-5/categories/23756816/pages/29450867](
parameter
)
 which stores the speed value (0 by default)
 |

**
ScopeLayer
**
 |
The layer index within the scope of the animation you want to control
 |

**
Invert
**
 |
Check to use one minus the parameter value as speed
 |

Note that the Blend value is not used.

##
LayerManualUpdate

Controls the
*
time
*
(normalized time) of an animation that is playing in the same scope as this procedural clip through code.

**
Param Name
**
 |
The name of the floating point
[/docs/static/engines/cryengine-5/categories/23756816/pages/29450867](
parameter
)
 which stores the normalized time value (0 by default)
 |

**
Scope Layer
**
 |
The layer index within the scope of the animation you want to control.
 |

**
Invert
**
 |
Check to use one minus the parameter value as normalized time.
 |

##
LayerWeight

Controls the weight of a CryAnimation layer through code.

**
Layer Weight Param
**
 |
The name of the floating point
[/docs/static/engines/cryengine-5/categories/23756816/pages/29450867](
parameter
)
 which stores the weight to apply to the layer
 |

**
Scope Layer
**
 |
The layer index within the scope of the layer you want to control.
 |

**
Invert
**
 |
Check to use one minus the parameter value as weight.
 |

##
LookPose

Low level procedural clip to start an
[/docs/static/engines/cryengine-5/categories/23756816/pages/23308005](
lookpose
)
 asset. This is
**
*
NOT
*

**
related to the Aiming/Looking setup described in the tutorial
[/docs/static/engines/cryengine-5/categories/23756816/pages/23308487](
Tutorial - Controlling Looking (and Aiming) for AI in Mannequin
)
.

**
Animation
**
 |
The lookpose asset
 |

**
Blend
**
 |
The fade-in duration
 |

**
Blend Time
**
 |
The "smoothing time" for the spherical coordinates (the higher the number the quicker the longitude/latitude will smoothly move towards the target)
 |

**
Scope Layer
**
 |
The layer to play the lookpose on, relative to the scope's first animation layer.

This works differently than the layer parameter inside the AimPose procedural clip, which is the actual layer number (0 - 16)
 |

Uses the
[/docs/static/engines/cryengine-5/categories/23756816/pages/29450867](
parameter
)
 called "LookTarget" as target, if it exists. If not specified the target is 10m in front of the entity.

##
ManualUpdateList

Controls the
*
time
*
(normalized time) of animations playing in multiple layers through code.

**
Param Name
**
 |
The name of the
[/docs/static/engines/cryengine-5/categories/23756816/pages/29450867](
parameter
)
 of type SWeightData (4 weights, each a floating point number, next to each other) which stores the
*
segment
*
 normalized time values for the layers
 |

**
Scope Layer
**
 |
The layer index within the scope of the
*
first
*
 layer that contains the animation you want to control. All layers after that within this scope are also controlled (up to 4 layers)
 |

**
Invert
**
 |
Check to use one minus the parameter value
 |

##
ParticleEffect

Plays a particle effect.

**
Effect Name
**
 |
Name of the particle effect to spawn
 |

**
Joint Name
**
 |
Optional joint to attach the emitter to
 |

**
Attachment Name
**
 |
Optional attachment interface name to attach the emitter to
 |

**
Position Offset, Rotation Offset
**
 |
Local-space offset of the emitter. If no "Joint Name" or "Attachment Name" is given, the offset is relative to the host entity
 |

**
Clone Attachment
**
 |
(default: off) If "Attachment Name" is given, create a copy of the given interface instead of using it directly. This allows for more than one effect to play on the same attachment
 |

**
Kill on Exit
**
 |
(default: off) Explicitly remove the particle effect. This will remove all spawned particles instead of letting them 'die out' on their own
 |

**
Keep Emitter Active
**
 |
(default: off)
Keep emitter alive even after the procedural clip has ended

This feature should be used with great care. It assumes that the particle effect will go away on its own. There is no other way to get rid of the effect after it started.
 |

CRYENGINE 3.6
This clip changed quite a bit in CRYENGINE 3.7. This is how it looked in CRYENGINE 3.6:

**
Effect
**
 |
Name of the particle effect to spawn
 |

**
referenceBone
**
 |
Optional joint or attachment interface to attach the emitter to
 |

**
posOffset, rotOffset
**
 |
Local-space offset of the emitter. If no "referenceBone" is given, the offset is relative to the host entity
 |

**
cloneAttachment
**
 |
If "referenceBone" refers to an attachment interface, create a copy of the given interface instead of using it directly
 |

##
PlaySound

In CRYENGINE 3.7: See
[/docs/static/engines/cryengine-5/categories/23756816/pages/29798726#ProceduralClipDirectory-Audio](
Audio
)
. (PlaySound is the same as Audio)

CRYENGINE 3.6 PlaySound
Plays a sound.

**
Sound
**
 |
The sound to add
 |

**
AttachmentJoint
**
 |
Optional joint name to attach the sound to
 |

**
radius
**
 |
Describes the radius within AI will be alerted
 |

**
synchedStop
**
 |
If set to 1 the sound will stop at the next marker position. Helpful for weapon fire loops.
 |

**
forceStopOnExit
**
 |
Stops the sound when the animation finishes or another sound clip (can be empty) is triggered on the same proc layer
 |

The procedural clip will also take care of setting Sound Parameters. Programmers simply need to set a standard
[/docs/static/engines/cryengine-5/categories/23756816/pages/29450867](
parameter
)
 with the same name of a sound parameter, its value will get passed along to the sound system.

##
PositionAdjust

Procedurally move the entity towards a target position over time.

The target position/rotation is taken from the
[/docs/static/engines/cryengine-5/categories/23756816/pages/29450867](
parameter
)

called "TargetPos". This parameter has to be set for the clip to work.

This procedural clip is typically used to align characters to ledges/vault locations.

**
Blend
**
 |
Duration of the adjustment
 |

**
Offset, Yaw
**
 |
Additional offset on top of the target position
 |

**
Ignore Rotation
**
 |
Check to ignore rotation
 |

**
Ignore Position
**
 |
Check to ignore position
 |

##
PositionAdjustAnimPos

Procedurally move the entity such that whatever was the 'startlocation' of the animation becomes equal to the target position. The startlocation is the location that was the
*
origin
*
 location in the content creation tool where the animation comes from.

If the animation contains movement this clip might not behave as expected (as the 'delta' is only calculated at the start of the animation) and you should use PositionAdjustAnimPosContinuously.

The target position/rotation is taken from the
[/docs/static/engines/cryengine-5/categories/23756816/pages/29450867](
parameter
)
 specified using Param Name.

**
Blend
**
 |
Duration of the adjustment
 |

**
Param Name
**
 |
(optional) Name of the parameter to use. If not specified, uses the parameter called "TargetPos".
 |

**
Ignore Rotation
**
 |
Check to ignore rotation
 |

**
Ignore Position
**
 |
Check to ignore position
 |

##
PositionAdjustAnimPosContinuously

Procedurally move the entity such that whatever was the 'startlocation' of the animation becomes equal to the target position. The startlocation is the location that was the
*
origin
*
 location in the content creation tool where the animation comes from.

The target position/rotation is taken from the
[/docs/static/engines/cryengine-5/categories/23756816/pages/29450867](
parameter
)
 called "TargetPos". This parameter has to be set for the clip to work.

**
Blend
**
 |
Duration of the adjustment
 |

##
PositionAdjustTargetLocator

Takes the character assigned to the specified scope, typically a 'slave' scope, and moves the entity towards the location of a specific joint of this character.

**
Blend
**
 |
Duration of the adjustment
 |

**
Target Joint Name
**
 |
Name of the joint to align to
 |

**
Target Scope Name
**
 |
The scope that has the 'slave' character attached you want to align to
 |

**
Target State Name
**
 |
Not used
 |

##
RandomAimAround

Low level procedural clip to start an
[/docs/static/engines/cryengine-5/categories/23756816/pages/23308006](
aimpose
)
 asset and randomly aim around. This is
**
*
NOT
*

**
related to the Aiming/Looking setup described in the tutorial
[/docs/static/engines/cryengine-5/categories/23756816/pages/23308487](
Tutorial - Controlling Looking (and Aiming) for AI in Mannequin
)
.

**
Animation
**
 |
The aimpose asset
 |

**
Blend
**
 |
The fade-in duration
 |

**
Smooth Time
**
 |
The "smoothing time" for the spherical coordinates (the higher the number the quicker the longitude/latitude will smoothly move towards the target)
 |

**
Scope Layer
**
 |
The layer within the scope to play the aimpose on
 |

**
Yaw Min, Yaw Max
**
 |

 |

**
Pitch Min, Pitch Max
**
 |

 |

**
Time Min, Time Max
**
 |

 |

##
RandomLookAround

Low level procedural clip to start a
[/docs/static/engines/cryengine-5/categories/23756816/pages/23308005](
lookpose
)
 asset and randomly aim around. This is
**
*
NOT
*

**
related to the Aiming/Looking setup described in the tutorial
[/docs/static/engines/cryengine-5/categories/23756816/pages/23308487](
Tutorial - Controlling Looking (and Aiming) for AI in Mannequin
)
.

**
Animation
**
 |
The lookpose asset
 |

**
Blend
**
 |
The fade-in duration
 |

**
Smooth Time
**
 |
The "smoothing time" for the spherical coordinates (the higher the number the quicker the longitude/latitude will smoothly move towards the target)
 |

**
Scope Layer
**
 |
The layer within the scope to play the aimpose on
 |

**
Yaw Min, Yaw Max
**
 |

 |

**
Pitch Min, Pitch Max
**
 |

 |

**
Time Min, Time Max
**
 |

 |

##
SetParam

(new since CRYENGINE 3.7)

Set a mannequin (float) parameter to a certain value.

**
Param Name
**
 |
The name of the
[/docs/static/engines/cryengine-5/categories/23756816/pages/29450867](
parameter
)
 |

**
Blend
**
 |
The time it takes to reach the target value
 |

**
Target
**
 |
Target value
 |

**
Exit Target
**
 |
Value to go to after the proc clip ended
 |

##
SwapAttachment

(new since CRYENGINE 3.7)

**
Attachment Name Old
**
 |

 |

**
Attachment Name New
**
 |

 |

**
Reset on Exit
**
 |

 |

**
Clear on Exit
**
 |

 |

##
WeightedList

Control the
*
weight
*
 of multiple consecutive CryAnimation layers through code.

**
Param Name
**
 |
The name of the
[/docs/static/engines/cryengine-5/categories/23756816/pages/29450867](
parameter
)
 of type SWeightData (4 weights, each a floating point number, next to each other) which stores the weights
*

*
for the layers
 |

**
Scope Layer
**
 |
The layer index within the scope of the
*
first
*
 layer that you want to control. All layers after that within this scope are also controlled (up to 4 layers)
 |

**
Invert
**
 |
Check to use one minus the parameter value
 |

##
GameSDK Sample

##
Aiming

Relies on Aimpose/Aiming scope setup as in the standard GameDLL example for a human AI and described in the tutorial
[/docs/static/engines/cryengine-5/categories/23756816/pages/23308487](
Tutorial - Controlling Looking (and Aiming) for AI in Mannequin
)
.

Request the aimpose to be enabled.

**
Blend
**
 |
Fade-in duration for the aimpose
 |

##
AimSmoothing

Relies on Aimpose/Aiming scope setup as in the standard GameDLL example for a human AI and described in the tutorial
[/docs/static/engines/cryengine-5/categories/23756816/pages/23308487](
Tutorial - Controlling Looking (and Aiming) for AI in Mannequin
)
.

Controls smoothing parameters for the polar coordinates while moving towards a target (or following a target).

**
Smooth Time Seconds
**
 |
The "smoothing time" for the spherical coordinates (the higher the number the quicker the longitude/latitude will smoothly move towards the target)
 |

**
Max Yaw Degrees Per Second
**
 |
Maximum degrees per second in yaw direction
 |

**
Max Pitch Degrees Per Second
**
 |
Maximum degrees per second in pitch direction
 |

##
AttachPnt

Tell the "pick and throw weapon" (assuming it is currently equipped) to "attach".

**
Attachment Point
**
 |
Name of the attachment interface to use
 |

##
ColliderMode

Overrides the collidermode for the character.

**
Mode
**
 |
Allowed values:

-
Undefined (give up control)

-
Disabled (no collisions)

-
GroundedOnly

-
Pushable

-
NonPushable

-
PushesPlayersOnly

-
Spectator
 |

##
CompromiseCover

Tells the AI system that cover has been compromised.

##
CopyNormalizedTime

Synchronizes animation within two layers by automatically copying over the segment normalized time from an animation in one layer to an animation in another layer.

**
Source Scope
**
 |
The scope from which to copy
 |

**
Source Layer
**
 |
The layer within that scope to look for the source animation
 |

**
Layer
**
 |
The layer within the current scope that contains the animation you want to synchronize
 |

##
FacialSequence

Plays a facial sequence.

**
Filename
**
 |
The sequence (fsq) file to play
 |

**
Continue After Exit
**
 |
Whether or not to continue playing the sequence after the procedural clip exited. Ignored when looping the sequence, in that case the default behavior is used, so the sequence stops playing when the clip exits.
 |

**
Looping
**
 |
Whether or not to loop the sequence.
 |

##
Looking

Relies on Lookpose/Looking scope setup as in the standard GameDLL example for a human AI and described in the tutorial
[/docs/static/engines/cryengine-5/categories/23756816/pages/23308487](
Tutorial - Controlling Looking (and Aiming) for AI in Mannequin
)

Request the lookpose to be enabled. Blend-in time is used as fade-in time for the lookpose.

**
Blend
**
 |
Fade-in duration for the lookpose
 |

##
MovementControlMethod

Override the movement control method of the character.

**
Horizontal
**
 |
Horizontal movement control method. Allowed values:

-
0: Undefined (no override)

-
1: Entity driven

-
2: Animation driven (aka Data Driven)

-
3: Animation driven with collision in the horizontal plane
 |

**
Vertical
**
 |
Vertical movement control method. Allowed values:

-
0: Undefined (no override)

-
1: Entity driven

-
2: Animation driven (aka Data Driven)
 |

##
Ragdoll

Makes a character turn into a ragdoll and optionally blend him back to animation.

**
Blend
**
 |
This defines the time range during which the character will start randomizing at a
*
random
*
 |

**
Sleep
**
 |
When 0, you want the AI to ragdoll & die. When 1, you want the AI to stay alive during the ragdoll phase and blend back to animation

This flag is currently only used by the blend-from-ragdoll game code, which is triggered by calling CActor::Fall(). See the humanpreview setup. First this triggers the
CAnimActionBlendFromRagdollSleep, which makes the character ragdollize and 'sleep': It plays the fragment with fragmentID "BlendRagdoll" and tags containing "standup+blendin+ragdoll". This fragment has to contain a Ragdoll procclip with the sleep value set to 1.
 For standing up, a CAnimActionBlendFromRagdoll is started after the sleeping ended. This action relies on all possible standup animations to be in options for the fragmentID "BlendRagdoll" and tags containing "standup+blendout". The 'best matching' animation is chosen based upon the first frame of these.
 |

**
Stiffness
**
 |
Determines how much the ragdoll follows the animation
 |

##
SetStance

Tell an AI character it
*
is
*
 in a certain stance. It specifically does
*
not
*
 trigger stance change animation.

This is useful to annotate animation that ends up in another stance than it started in, for example during a scripted sequence that can be interrupted.

When the sequence is interrupted, the game knows the AI is in another stance.

**
Stance
**
 |
Stance name. The values recognized are currently:

-
Null

-
Stand

-
Crouch

-
Prone

-
Relaxed

-
Stealth

-
Alerted

-
LowCover

-
HighCover

-
Swim

-
Zero-G

But the SDK example only supports a couple of those: Crouch, Stand and Swim.
 |

##
SwapHand

Temporarily move the attachment from the right hand into the left hand (hardcoded to use attachment names "weapon" and "left_weapon").

##
TurretAimPose

Controls aiming & aimpose of the turret entity. This is
**
*
NOT
*

**
related to the Aiming/Looking setup described in the tutorial
[/docs/static/engines/cryengine-5/categories/23756816/pages/23308487](
Tutorial - Controlling Looking (and Aiming) for AI in Mannequin
)
.

**
Blend
**
 |
The fade in time of the aimpose
 |

**
Animation
**
 |
The aimpose asset to use
 |

**
Blend Time
**
 |
unused
 |

**
HorizontalAimSmoothTime
**
 |
The "smoothing time" for the yaw direction
 |

**
VerticalAimSmoothtime
**
 |
The "smoothing time" for the pitch direction
 |

**
Max Yaw Degrees Per Second
**
 |
Maximum degrees per second the turret rotates in the yaw direction
 |

**
Max Pitch Degrees Per Second
**
 |
Maximum degrees per second the turret rotates in the pitch direction
 |

##
WeaponBump

First person weapon bump animation when the player lands.

**
Time
**
 |
The amount of time the bump animation plays
 |

**
Shift
**
 |
How much the weapon moves on screen after player lands
 |

**
Rotation
**
 |
How much the weapon rotates
 |

WeaponPose

Places the weapon on a specific location on the screen. It has 3 modes: right hand, left hand and zoom. Only one of these modes can be active at a time. However, more than one WeaponPose clip can run in parallel.

**
Pose Type
**
 |
Use this to tell what the weapon offset will influence. The default is 0 which means right hand. This will change the weapon's position on screen starting from the idle pose position.

1 Means zoom, which will place the weapon on the screen when the player decides to zoom in and 2 means left hand which can be used to modify the original base pose to accommodate under barrel attachments
 |

**
Zoom Transition Angle
**
 |
default set to 0, defines the angle that the weapon will rotate during a zoom transition. Is only read if pose_type is set to 1 (zoom) otherwise this parameter is totally ignored
 |

**
Position, Rotation
**
 |
defines the pose itself as an offset to the base pose. Rotation is defined in angles.
 |

WeaponRecoil

Activates the recoil behavior on the weapon. It will trigger a recoil animation every time the weapon fires.

**
Damp Strength
**
 |
How quick the weapon comes back to rest pose after a kick
 |

**
Fire Recoil Time
**
 |
Attack time of the recoil kick. A value of 0 will make the kick be applied in a single frame which is not recommended since it can make an animation look jerky
 |

**
Fire Recoil Strength First, Fire Recoil Strength
**
 |
The kick strength. Fire Recoil Strength First has the same behavior as Fire Recoil Strength but it is applied for the first shot only.

For rapid fire modes is highly recommended Fire Recoil Strength First to be much higher than Fire Recoil Strength
 |

**
Angle Recoil Strength
**
 |
How much deviation the weapon will suffer after each shot
 |

**
Randomness
**
 |
Overall 'organic' feeling of recoil animation
 |

WeaponSway

This clip activates the laziness effect on the player's hands while he moves. Careful set-up of the clip allows to simulate different weight feelings for different weapons.

After the clip is activated, it will start reading the player movement and compute weapon offsets in real time.

**
Ease Factor Inc, Ease Factor Dec
**
 |
How much it takes for the look poses to blend in (Inc) or out (Dec) when player looks around
 |

**
Strafe Scope Factor, Rotate Scope Factor
**
 |
Legacy, do not use
 |

**
Velocity Interpolation Multiplier
**
 |
Fine tune control for the strafe
 |

**
Velocity Low Pass Filter
**
 |
Filter applied to the player movement to make the sway more reactive or heavier
 |

**
Acceleration Smoothing
**
 |
Helps making strafe poses less linear and more 'organic'
 |

**
Acceleration Front Augmentation
**
 |
By how much the strafe poses are more sensible to move back and forth as opposed to left and right
 |

**
Vertical Velocity Scale
**
 |
Changes the look poses behavior when player is going up or down a ramp
 |

**
Sprint Camera Animation
**
 |
Legacy, do not use
 |

**
Look Offset
**
 |
How much the weapon moves around the screen when player looks around
 |

**
Horiz Look Rot
**
 |
Rotation applied to the weapon when player looks left and right
 |

**
Vert Look Rot
**
 |
Rotation applied to the weapon when player looks up and down
 |

**
Strafe Offset
**
 |
How much the weapon moves when player moves around
 |

**
Side Strafe Offset
**
 |
Rotation of the weapon when player starts strafing either to the left or to the right
 |

**
Front Strafe Rot
**
 |
Rotation of the weapon when player starts moving forward or backward
 |

WeaponWiggle

Activates weapon wiggling/shaking.

**
frequency
**
 |
Shake frequency
 |

**
intensity
**
 |
Shake intensity
 |

[#engine-cryaction](
Engine (CryAction)
)
[#actionevent](
ActionEvent
)
[#aimpose](
AimPose
)
[#aisignal](
AISignal
)
[#attachentity](
AttachEntity
)
[#attachprop](
AttachProp
)
[#audio](
Audio
)
[#forcefeedback](
ForceFeedback
)
[#flowgraphevent](
FlowGraphEvent
)
[#hideattachment](
HideAttachment
)
[#iklayerweight](
IKLayerWeight
)
[#jointadjust](
JointAdjust
)
[#layeranimspeed](
LayerAnimSpeed
)
[#layermanualupdate](
LayerManualUpdate
)
[#layerweight](
LayerWeight
)
[#lookpose](
LookPose
)
[#manualupdatelist](
ManualUpdateList
)
[#particleeffect](
ParticleEffect
)
[#playsound](
PlaySound
)
[#positionadjust](
PositionAdjust
)
[#positionadjustanimpos](
PositionAdjustAnimPos
)
[#positionadjustanimposcontinuously](
PositionAdjustAnimPosContinuously
)
[#positionadjusttargetlocator](
PositionAdjustTargetLocator
)
[#randomaimaround](
RandomAimAround
)
[#randomlookaround](
RandomLookAround
)
[#setparam](
SetParam
)
[#swapattachment](
SwapAttachment
)
[#weightedlist](
WeightedList
)
[#gamesdk-sample](
GameSDK Sample
)
[#aiming](
Aiming
)
[#aimsmoothing](
AimSmoothing
)
[#attachpnt](
AttachPnt
)
[#collidermode](
ColliderMode
)
[#compromisecover](
CompromiseCover
)
[#copynormalizedtime](
CopyNormalizedTime
)
[#facialsequence](
FacialSequence
)
[#looking](
Looking
)
[#movementcontrolmethod](
MovementControlMethod
)
[#ragdoll](
Ragdoll
)
[#setstance](
SetStance
)
[#swaphand](
SwapHand
)
[#turretaimpose](
TurretAimPose
)
[#weaponbump](
WeaponBump
)
