# Leg and Foot Ground Alignment

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/23308004
- Page ID: 23308004
- Breadcrumb: Asset Prep (External) > Asset Exporting Overview > Geometry Creation Overview > Animated Geometry > Character (animated) > Engine Setup (animated) > Character Parameters File (chrparams) > Leg and Foot Ground Alignment
- Parent: Character Parameters File (chrparams)

## Content

##
Overview

CRYENGINE can automatically adjust the character's legs and feet to match the surface of the terrain or ground he is standing on.

This includes the foot aligning to the direct of the slope in addition to the leg adjusting to different heights.

[Image: /docs/static/attachments/23994477]

##
Setup in CRYENGINE 3.0.x-3.4.x

Animated Character must be used for ground alignment and foot / leg IK to function. This means that simple entities like the animobj entity and others will not use this function. The character must be a live animated character, which can be accomplished by using the default player class or default AI classes such as human.

The character's skeleton needs to have certain bones and names in order to make the groundAlignment work. This setup needs to be done in the character's
[/docs/static/engines/cryengine-5/categories/23756816/pages/23307999](
.chrparams
)
 file. Setups for both legs must be added to the file:

```

`
     <LimbIK_Definition>
        <IK EndEffector="Bip01 R Foot" Handle="RgtLeg01" Root="Bip01 R Thigh" Solver="2BIK"/>
        <IK EndEffector="Bip01 L Foot" Handle="LftLeg01" Root="Bip01 L Thigh" Solver="2BIK"/>
     </LimbIK_Definition>

`

```

To find the surface beneath the character's feet, rays are cast from a place above his heel bone to find a collision with the surface. The foot is also aligned to the surface. The character's skeleton must provide the following bones:

-
Bip01 L Calf

-
Bip01 R Calf

-
Bip01 L Heel

-
Bip01 R Heel

-
Bip01 L Foot

-
Bip01 R Foot

-
Bip01 L Toe0

-
Bip01 R Toe0

##
Setup in 3.5.x

As with previous versions of the engine, animated character classes must be used if you wish to have the adaption, using the animobj entity or something similar will not function.

Within 3.5 there are a few less specific naming conventions that must be followed, however, the setup is similar to 3.4

**
1. Setup the required naming conventions that are written in C++ within the InitializePoseAlignerBipedHuman function.
**

-
Bip01 Pelvis

-
Bip01 planeTargetLeft

-
Bip01 planeWeightLeft

-
Bip01 planeTargetRight

-
Bip01 planeWeightRight
**
2. Define the joints that will be affected in the .chrparams
**
[/docs/static/engines/cryengine-5/categories/23756816/pages/23307999](

)
**
file.
**

```

`
     <LimbIK_Definition>
        <IK EndEffector="Right_Foot" Handle="RgtLeg01" Root="Right_Thigh" Solver="2BIK"/>
        <IK EndEffector="Left_Foot" Handle="LftLeg01" Root="Left_Thigh" Solver="2BIK"/>
     </LimbIK_Definition>

`

```

You can have any name set for the calf, foot and thigh of your character as long as it's defined in the .chrparams, but make sure that the handle name is "RgtLeg01" for the right leg and "LftLeg01" for the left leg.
**
3. Setting up the Bip01 PlaneTarget and PlaneWeight bones.
**

The plane target and plane weight bones are setup in the rig to give the system an absolute offset limit. The pose aligned drives the plane target node to align to the plane weight node and no further.

-
Bip01 planeWeightLeft (This bone needs to be a child of the foot and share the same X,Y location as the foot but approximately 100cm above the foot bone)

-
Bip01 planeTargetLeft (This bone needs to be the same on the X and Y, but aligned to 0 on the Z, also a child to the Foot)

-
Bip01 planeWeightRight (This bone needs to be a child of the foot and sharing the same X,Y location but approximately 100cm above the foot on the Z)

-
Bip01 planeTargetRight (This bone needs to be the same on the X and Y, but aligned to 0 on the Z, also a child to the Foot)
[Image: /docs/static/attachments/23994481]

*
Plane Target Node in Center of Foot
*

[Image: /docs/static/attachments/23994480]

*
Plane Weight Node Aligned to Pelvis on Z , Zero on Y and Over the foot on X.
*

[Image: /docs/static/attachments/23994479]

*
Hierarchy setup display
*

**
4. Debugging
**

Here are some very useful console variables to see that the pose aligner is active:

-
**
a_poseAlignerEnable = 1
**
 - Enables the Pose Aligner

-
**
a_poseAlignerDebugDraw = 1
**
 Enables Debug drawing of plane weight, target and root offsets

-
**
a_poseAlignerForceWeightOne = 1
**
 Forces weight to 1 which causes the limb to always adjust
[Image: /docs/static/attachments/23994482]

##
Using GroundAlignment (3.0.x-3.4.x)

##
GroundAlignment in the game

##
CVar Control

Use ca_groundAlignment to turn on and off the automatic ground alignment on all characters globally. By default this value is set to 1, which means it is active.

##
Flow Graph Node

The Flow Graph node
**
Animations::GroundAlignment
**
 can be used to enable or disable this feature during the game.

This gives designers control over turning ground alignment on/off for individual characters at run-time.

[Image: /docs/static/attachments/23994476]

##
Code

Like the Flow Graph node described above, this feature can be disabled/enabled for individual characters at run-time via code as well.

The interface function is declared in ISkeletonPose:

```

`
SkeletonPose::
virtual void EnableFootGroundAlignment(bool enable);

`

```

To activate or deactivate the alignment from within the game dll actor or player implementation, use this code:

```

`
GetEntity()->GetCharacter(0)->GetISkeletonPose()->EnableFootGroundAlignment(true);

`

```

[#setup-in-cryengine-30x-34x](
Setup in CRYENGINE 3.0.x-3.4.x
)
[#setup-in-35x](
Setup in 3.5.x
)
[#using-groundalignment-30x-34x](
Using GroundAlignment (3.0.x-3.4.x)
)
