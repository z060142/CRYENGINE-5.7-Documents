# Limb IK Technical

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/23306440
- Page ID: 23306440
- Breadcrumb: CRYENGINE Engine Code > Engine Modules > CryAnimation > Limb IK Technical
- Parent: CryAnimation

## Content

### Overview

CRYENGINE's animation system allows to setup IK chains for characters.

When an IK chain is active, the system figures out the values for the joints that are part of the chain so that the end effector reaches the provided target position.

### Setup

The IK chains are defined in data, in the [chrparams file](/docs/static/engines/cryengine-3/categories/1114113/pages/1310814).

For detailed information on how to create the Limb IK chains refer to the dedicated [Limb IK](/docs/static/engines/cryengine-3/categories/1114113/pages/1310803) setup document.

### Using LimbIK from Code

To activate a LimbIK chain from outside CryAnimation use the SetHumanLimbIK function, accessible through the ISkeletonPose interface.

The SetHumanLimbIK function needs to be called each frame we want the IK chain to be active.

The name of the LimbIK chain is defined in the chrparams file:

```
ISkeletonPose& skeletonPose = ...;
skeletonPose.SetHumanLimbIK(targetPositionWorldSpace, "RgtArm01");
```
