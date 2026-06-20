# Characters and Animations

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/26216226
- Page ID: 26216226
- Breadcrumb: Entity > Characters and Animations
- Parent: Entity

## Content

##
Overview

For a simple example of how to load a character into an entity slot, see
[/docs/static/engines/cryengine-5/categories/28704770/pages/29797019](
IEntity::LoadCharacter
)
.

[/docs/static/engines/cryengine-5/categories/28704770/pages/29797019](
Example
)

##
Table of Contents

[#api-types](
API Types
)
[#low-level-caf-animation-playback](
Low-level .caf Animation Playback
)
[#complex-animation-playback-using-mannequin](
Complex Animation Playback using Mannequin
)
[#blend-spaces-motion-parameters](
Blend spaces / Motion parameters
)
[#inverse-kinematics-and-pose-modifiers](
Inverse Kinematics and Pose Modifiers
)
[#retrieving-joint-transformations](
Retrieving Joint Transformations
)
[#conclusion](
Conclusion
)

##
API Types

-
[/docs/static/engines/cryengine-5/categories/28704770/pages/29797017](
ICharacterInstance
)

-
[/docs/static/engines/cryengine-5/categories/28704770/pages/29797201](
ISkeletonAnim
)

-
[/docs/static/engines/cryengine-5/categories/28704770/pages/29797206](
ISkeletonPose
)

-
[/docs/static/engines/cryengine-5/categories/28704770/pages/29797199](
IAnimationPoseModifier
)

-
[/docs/static/engines/cryengine-5/categories/28704770/pages/29797023](
IMannequin
)

-
[/docs/static/engines/cryengine-5/categories/28704770/pages/29797013](
IActionController
)

-
[/docs/static/engines/cryengine-5/categories/28704770/pages/29797015](
IAction
)

##
Character File Formats

The table below describes the different types of file formats that the engine can handle:

File Format
 |
Description
 |

**
CDF
**
 |
Character Definition File – Created with the Character Tool in the Editor, and combines a skeleton with several attachments of any object type (
**
CGA
**
,
**
CHR
**
,
**
SKIN
**
,
**
CGF
**
) – note that it is also possible for attachments to be recursive, meaning a
**
CDF
**
 could contain another
**
CDF
**
.
 |

**
CHR
**
 |
Represents a character created
with
a DCC (Max, Maya) tool. Skeletons will be created with this (or its pseudonym,
**
SKEL
**
) format.
 |

**
SKIN
**
 |
Skinned geometry exported
with
a DCC (Max, Maya) tool.
 |

**
CGA
**
 |
A combination of multiple
**
CGF
**
 files that allow for animating simpler objects.
 |

##
Animation Events

For the designer documentation, see
[/docs/static/engines/cryengine-5/categories/23756816/pages/25535608](
Animation Events
)
. In code, we can receive the animation events that occur using the ENTITY_EVENT_ANIM_EVENT event - and use this to trigger game-specific code, such as emitting particles at certain points in time.

For a brief example, see
[/docs/static/engines/cryengine-5/categories/28704770/pages/29797013](
IActionController::Overestimation
)
.

[/docs/static/engines/cryengine-5/categories/28704770/pages/29797013](
Example
)

##
Low-level .caf Animation Playback

The primary purpose of the character system is to allow for animating characters to add true life to a scene. At the lowest level, characters can play raw CAF (CRYENGINE Animation Format) files exported directly from an animator’s DCC tool and the engine’s exporters.

For playback of complex animations such as a complete player character, see
[/docs/static/engines/cryengine-5/categories/23756813/pages/26216226#CharactersandAnimations-ComplexAnimationPlaybackusingMannequin](
Complex Animation Playback using Mannequin
)
.

Low-level animation playback is managed by the
[/docs/static/engines/cryengine-5/categories/28704770/pages/29797201](
ISkeletonAnim
)
 interface, which can be obtained via the
[/docs/static/engines/cryengine-5/categories/28704770/pages/29797017](
ICharacterInstance::GetISkeletonAnim
)
 function.

For an example of how to start an animation, see
[/docs/static/engines/cryengine-5/categories/28704770/pages/29797201](
ISkeletonAnim::StartAnimation
)
. Keep in mind that animations are managed on layers, so it would be possible to play multiple animations simultaneously – some specific types such as
**
additive
**
 animations rely on this setup, modifying the previous layers by adding the position and rotational changes on top.

We can change the animation layer by modifying
CryCharAnimationParams::m_nLayerID
. The current max number of layers is 32. Keep in mind that each used layer will require additional processing.

[/docs/static/engines/cryengine-5/categories/28704770/pages/29797201](
Example
)

##
Complex Animation Playback using Mannequin

The engine also provides Mannequin – an abstraction of the lower level
**
CryAnimation
**
 module, made available through the
[/docs/static/engines/cryengine-5/categories/28704770/pages/29797023](
IMannequin
)
 interface. This system allows for simplifying the efforts of animating more complex characters that need a lot of animations, blending, options and more.

Keep in mind to be selective of going for Mannequin as opposed to playing back low-level .caf animations – Mannequin does introduce overhead, and should only be used for mission critical elements. For simpler elements, such as animating a static drill – just use the low-level API for optimal performance.

The Mannequin state of an entity is managed by the
[/docs/static/engines/cryengine-5/categories/28704770/pages/29797013](
IActionController
)
 interface, and is the first step towards creating a Mannequin setup for our entity. To start, have a look at the example in
[/docs/static/engines/cryengine-5/categories/28704770/pages/29797023](
IMannequin::CreateActionController
)
.

[/docs/static/engines/cryengine-5/categories/28704770/pages/29797023](
Initialize Mannequin Example
)
In Mannequin, animations are abstracted away into
**
Fragments
**
 (referred to as
[/docs/static/engines/cryengine-5/categories/28704770/pages/29797015](
IAction
)
 in code). A fragment is something that can be played back, for example a fragment could contain and play back just one raw animation file. Fragments can also be much more complex, in that one fragment can play two animations after another – or play animations on two separate layers without needing to do extra work. It is also possible to run procedural effects and play sounds from fragments. To queue / play a fragment in code, see
[/docs/static/engines/cryengine-5/categories/28704770/pages/29797013](
IActionController::Queue
)
.

[/docs/static/engines/cryengine-5/categories/28704770/pages/29797013](
Queue Action Example
)
Mannequin also introduces the concept of
**
tags
**
. Tags are essentially conditional values that we can set later in code, for example
“IsTurningLeft”
 would be a tag, we could then have an
“Idle”
 fragment with two options inside it – one that plays by default, and another that plays when
“IsTurningLeft”
 is true. This brings in the difference of changing options through tags, or queuing another fragment. In the same way, we could have a continuously looping Idle fragment, we could also simply queue a
“TurnLeft”
 fragment that would play after Idle is completed, and then either persist or blend out and return to Idle. To set a tag, see
[/docs/static/engines/cryengine-5/categories/28704770/pages/29797012](
CTagState::Set
)
.

[/docs/static/engines/cryengine-5/categories/28704770/pages/29797012](
Set Tag Example
)
To forward animation events to Mannequin, see
[/docs/static/engines/cryengine-5/categories/28704770/pages/29797013](
IActionController::OnAnimationEvent
)
.

[/docs/static/engines/cryengine-5/categories/28704770/pages/29797013](
Animation Event Example
)

##
Blend spaces / Motion parameters

[/docs/static/engines/cryengine-5/categories/23756816/pages/26873837](
Blend spaces
)
 are an engine feature allowing for the dynamic blending between animations based on real-time values such as movement speed. The simplest example of this would be the blending of an animation representing idle standing, and another for walk forward. Blend spaces would support blending linearly between the two based on movement speed – giving a dynamic feel to the animation as it adapts to the entity moving.

More complex blend spaces can utilize multiple variables and animations, for example handling turning, slopes and much more. Overall it is a very powerful system that allows for truly making characters feel life-like.

Playing back a blend space is possible just as with regular animations, either by name via the low-level animation playback API, or inside Mannequin fragments.

Once a blend space is being played, we can utilize the
[/docs/static/engines/cryengine-5/categories/28704770/pages/29797201](
ISkeletonAnim::SetDesiredMotionParam
)
function, automatically resulting in the correct animations being blended together to the desired end result.

[/docs/static/engines/cryengine-5/categories/28704770/pages/29797201](
Example
)

##
Inverse Kinematics and Pose Modifiers

The animation system provides the concept of
**
Pose Modifiers
**
, in code known as
[/docs/static/engines/cryengine-5/categories/28704770/pages/29797199](
IAnimationPoseModifier
)
. The pose modifiers allow for changing the animated poses based on gameplay logic, in simple cases to offset joints and in more complex cases affect entire IK chains based on gameplay needs.

Pose modifier interface name
 |
Description
 |

[/docs/static/engines/cryengine-5/categories/28704770/pages/29797205](
IAnimationPoseBlenderDir
)
 |
Allows for directing a joint at a target position for aim and look IK. See
[/docs/static/engines/cryengine-5/categories/28704770/pages/29797206](
ISkeletonPose::GetIPoseBlenderAim
)
 (
[/docs/static/engines/cryengine-5/categories/23756816/pages/25535363](
Weapon Aiming
)
) and
[/docs/static/engines/cryengine-5/categories/28704770/pages/29797206](
ISkeletonPose::GetIPoseBlenderLook
)
 (
[/docs/static/engines/cryengine-5/categories/23756816/pages/26873927](
Look IK
)
).
 |

[/docs/static/engines/cryengine-5/categories/28704770/pages/29797198](
IAnimationOperatorQueue
)
 |
Allows overriding / appending the orientation of individual joints.
 |

[/docs/static/engines/cryengine-5/categories/28704770/pages/29797203](
IAnimationPoseAlignerChain
)
 |
Used to process more complex pose modifiers such as feet ground alignment.
 |

[/docs/static/engines/cryengine-5/categories/28704770/pages/29797208](
IAnimationPoseMatching
)
 |
Used to support blending from one state (such as ragdoll) to an animated pose
 |

##
Retrieving Joint Transformations

We can use
[/docs/static/engines/cryengine-5/categories/28704770/pages/29797206](
ISkeletonPose::GetAbsJointByID
)
 to retrieve the location of a specific joint in world-space. This gets the location of the joint in the runtime pose as of this frame.

[/docs/static/engines/cryengine-5/categories/28704770/pages/29797206](
Example
)

##
Conclusion

This concludes the article on Characters and Animations. You may be interested in:

-
[/docs/static/engines/cryengine-5/categories/23756813/pages/26216224](
Physics and Movement
)
