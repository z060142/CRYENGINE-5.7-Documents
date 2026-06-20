# Weapon Aiming

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/25535363
- Page ID: 25535363
- Breadcrumb: Animation > Character Assembly > Weapon Aiming
- Parent: Character Assembly

## Content

![Image](https://www.cryengine.com/docs/static/attachments/29933228)

[![Image](https://www.cryengine.com/docs/static/attachments/26952088)](https://www.cryengine.com/get-cryengine/memberships)

## Overview

Having a character aim or look towards a point in the 3d world is a common feature required by many games.

In some simple cases this can be achieved by manually manipulating some specific joints of a character. For example, a simple head look ik system could just grab the head joint and change its orientation after all animation has been processed to point in a certain direction.

With more complex scenarios this might be much trickier to achieve. For example, aiming with a weapon might require the weapon pointing at some specific location, the hands of the character firmly holding the weapon, and the character looking through the scope at all times. In many cases we want to add some flavor or style when the character is aiming. We usually also want to retain as much style as possible from the animations playing underneath to make it look as natural as possible. This involves a bit more effort than simply rotating a single joint.

For the more complex cases of looking and aiming, CRYENGINE provides a parametric directional blending system that allow animators or technical artists to provide a set of sample poses of characters looking and aiming in different directions. At run-time we blend those poses together and put them on top of the currently playing animation so that the character looks or aims towards a point in space requested by the game code, whilst retaining the style present in the original authored poses as much as possible.

Our current implementation is designed with characters that exhibit a range of motion similar to human characters in mind (eg. it doesn't support continuous 360 degrees aiming around a pivot point, like a mechanical turret would rotate)

## Chapters:

[Chapters:](#chapters)[Aim IK Setup](#aim-ik-setup)[Common Pitfalls](#common-pitfalls)
![Image](https://www.cryengine.com/docs/static/attachments/26952868)

### Aim IK Setup

#### Animation File Setup

The system requires a number of poses of our character aiming in several directions so that it can blend between them to aim in any intermediate direction. It works with exactly 9 or 15 poses.

The poses are exported as an animation file, with a pose per frame. The naming of this file is important. Some part of its name should match the AnimToken provided in the definition.

The order of the poses in the animation is also important.

![Image](https://www.cryengine.com/docs/static/attachments/35400831)![Image](https://www.cryengine.com/docs/static/attachments/35400832)

How this could really look for the 9 poses case:

![Image](https://www.cryengine.com/docs/static/attachments/35400833)

While 9 poses might be enough for many cases, it is recommended to use 15 poses for better visual results, since when providing 9 poses the system currently extrapolates the provided ones to create 15 poses.

When creating aim or look poses it is common to use an underlying animation pose as a starting point (eg. standing idle). The aimposes created from such a starting animation must be applied on top of similar animations.

If the underlying animation currently playing for a character is different enough (eg. crouching) it might be necessary to create aimposes for that specific case to achieve a better quality.

It is not supported to have AimPose or LookPose animations in DBA files.

#### ChrParams File Setup

The main configuration for a character to be able to use aim and look poses is specified in the chrparams file for its skeleton

It is important that this is the skeleton used by the RC to process the animation since aimposes are processed by the RC.

##### AimIK

The specific structure in the chrparams file looks like the following:

```
<Params>
<IK_Definition>
<AimIK_Definition>
<DirectionalBlends>
<Joint AnimToken="AimPoses" ParameterJoint="Bip01 CustomAim" StartJoint="Bip01 CustomAimStart" ReferenceJoint="Bip01 Pelvis"/>
</DirectionalBlends>
<RotationList>
<Rotation Additive="1" Primary="1" JointName="Bip01 Pelvis"/>
<Rotation Additive="1" Primary="1" JointName="Bip01 Spine"/>
<Rotation Additive="1" Primary="1" JointName="Bip01 Spine1"/>
<Rotation Additive="1" Primary="1" JointName="Bip01 Spine2" />
<Rotation Additive="0" Primary="1" JointName="Bip01 CustomAim" />
<Rotation Additive="0" Primary="1" JointName="Bip01 CustomAimStart" />
<Rotation Additive="0" Primary="0" JointName="Bip01 LHand2Aim_IKTarget" />
<Rotation Additive="0" Primary="0" JointName="Bip01 LHand2Aim_IKBlend" />
...
<Rotation Additive="0" Primary="0" JointName="Bip01 RHand2Weapon_IKBlend" />
</RotationList>
<PositionList>
<Position Additive="1" JointName="Bip01 Pelvis"/>
<Position Additive="0" JointName="Bip01 CustomAim" />
...
<Position Additive="0" JointName="Bip01 RHand2Weapon_IKBlend"/>
</PositionList>
</AimIK_Definition>
</IK_Definition>
...
<Params>
```

**DirectionalBlends**

The DirectionalBlends specifies a combination of parameter, start and reference joints to use for aimposes. An animation is processed as an aimpose with this specific configuration when the AnimToken is found somehwere in its name (in this example, any animation processed for this skeleton that contains the sub-string "AimPoses" anywhere in its path will be considered an aimpose with "Bip01 CustomAim" as the parameter joint, "Bip01 CustomAimStart" as the start joint and "Bip01 Pelvis" as the reference joint).

AnimToken | Sub-string that needs to be matched to some part of the name of an animation in order to be processed as an aimpose with the current configuration for parameter, start and reference joints.
--- | ---
ParameterJoint | Name of the parameter joint.
StartJoint | Name of the start joint.
ReferenceJoint | Name of the reference joint.

It is possible to specify more than one DirectionalBlends section.

**RotationList**

This list is used by the run-time code to know the joints that contribute with their orientation to aimposes. Any joint not in this list will be ignored for the purposes of calculating and blending the aimpose.

JointName | Name of the joint
--- | ---
Additive | Specifies the blend mode. 1 -> Additive blending 0 -> Override blending
Primary | Specifies if it is part of the hierarchical chain that goes from the root joint up to the parameter joint

Primary joints should be specified at the start of the rotation list.

Currently it is necessary to have all primary joints appear before any of their children that are also marked as primary.

AimPoses can only have one rotation list, so all joints used by all aimposes should appear in it, and it should be valid for all of them.

**PositionList**

This list is used by the run-time code to know the joints that contribute with their position to aimposes. Any joint not in this list will be ignored for the purposes of calculating and blending the aimpose.

JointName | Name of the joint
--- | ---
Additive | Specifies the blend mode. 1 -> Additive blending 0 -> Override blending

AimPoses can only have one position list, so all joints used by all aimposes should appear in it.

### Common Pitfalls

Aim and look poses are processed by the Resource Compiler (RC) as part of the animation folder processing step. As a result of this process, the RC writes the DirectionalBlends.img file.

DirectionalBlends.img contains, for all aim and look poses found during processing, the information that the run-time needs to figure out how each of the poses need to be blended together so that characters look or aim precisely in the requested directions. This information is calculated from the pose data found in the CAF file and the AimIK and LookIK definitions in the chrparams file.

By default, when running Sandbox or the game, the animation system just loads this preprocessed information from DirectionalBlends.img file instead of recalculating it for each aim or look pose that is loaded because it considerably reduces load times.

When working on aim or look pose CAF files, or editing the AimIK or LookIK definition in the chrparams file, we usually do not want to have to recreate this file, since it requires that we have all the source animation files locally and it usually takes some time for the RC to process the full animations folder (creating DirectionalBlends.img isn't the only thing it does). In such cases, it's best to disable the loading of DirectionalBlends.img and have the engine recalculate the information it needs during load time, so the local changes can be picked up correctly.

To let the engine know that we do not want to load the DirectionalBlends.img file we must **set the "ca_useIMG_AIM" cvar to 0 before starting the Sandbox or the game** (eg. in the user.cfg file). Now, when loading an aim or look pose, the information that used to be in DirectionalBlends.img will be recalculated.
