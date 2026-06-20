# Aim IK (aimposes)

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/23308006
- Page ID: 23308006
- Breadcrumb: Asset Prep (External) > Asset Exporting Overview > Geometry Creation Overview > Animated Geometry > Character (animated) > Engine Setup (animated) > Character Parameters File (chrparams) > Aim IK (aimposes)
- Parent: Character Parameters File (chrparams)

## Content

### Overview

Aim poses are used at run time to create complex IK-effects. To map the aim poses to the right bones, it is necessary that the following bone names are included in the skeleton.

If the bones are not part of the skeleton, the aim-pose can't be activated and used at run time.

Try and make the poses as extreme as possible, even though they may look unnatural. Limits can then be set using the game code. The middle pose (frame 4) needs to point forward. The other poses are centered around the middle pose. The angle between the middle pose and the remaining aim poses is supposed to be approximately 70 degrees. If you draw the aim-poses with **ca_DrawAimPoses 3** then, the aim cone is supposed to have a diamond shape.

### Setup

### Animating Aim Poses

#### Creating Aim Poses with the Aim Pose Creator (CryMaxTools)

The Aim Pose Creator is used to create all the Aim Poses based on templates and will create automatically frames with right angles and poses.

![Image](https://www.cryengine.com/docs/static/attachments/23994496)

Create the base pose from which all the aim poses will be derived. we will et up a forward aiming pose first and will create all the other aim poses based on our main pose.

Make sure that your weapon bone and the weapon are aligned and both are pointing straight Y forward.

![Image](https://www.cryengine.com/docs/static/attachments/23994495)

Select now all the upper parts of the body starting from the Bip01 Pelvis and open up the Aim pose Creator to create the poses.

![Image](https://www.cryengine.com/docs/static/attachments/23994494)

- Template for biped human and the template for the pose angles and the count.
- There you can define the influences of each bone for the motion of the aim pose for tweaking.
- Aim pose interface lets you switch immediately between each pose by pressing the buttons and the Create Poses button is also located there.
- Sometimes you will get strange rotations and twists after creating all the aim poses, the reason for that is that you did not update the offsets. Press the update button for all bones or the selected bones.
- Gives you the option to setup IKs.

The Aim Pose Creator is already setup to a default working template which can be used right away and if there is something that you dont like in one of the frames you can easily tweak the frames manually.

Update all the Offsets for the bones and press the Create Poses button.

### Troubleshooting

**Aim Poses jitter or Aim Poses have no finger animation**

Most likely the Aim Poses are not specifically treated by the resource compiler and compressed like any other animation. Check if there is an entry in the cba file for the aim poses that points to the folder you are exporting to.

**Aim Poses are affected by other animations, for example a breathing additive**

The Aim IK is evaluated inside a layer like other animations. Animations in higher layers will influence or overwrite the result of the Aim IK. To set the layer in which the Aim IK is to be evaluated to a higher layer call this function:

```
CSkeletonPose::SetAimIKLayer(uint32 nLayer)
```

**Aim Poses work, but the Animation Driven IK Targets are not evaluated**

If you want to use the Animation Driven (Limb Retargetting) IK inside an Aim Pose to glue the front hand to the weapon for example (attach blend bone and target to the weapon bone) you need to make sure that both, the blend bone AND the target bone have at least one rotation key set on them. The Aiming system disregards bones without rotation controllers as an optimization. The blend bones can be freely rotated anyway, since only his translation is relevant. See [Animation Driven IK](Animation%20Driven%20IK.md) for more information.

[Setup](#setup)[Animating Aim Poses](#animating-aim-poses)[Troubleshooting](#troubleshooting)
