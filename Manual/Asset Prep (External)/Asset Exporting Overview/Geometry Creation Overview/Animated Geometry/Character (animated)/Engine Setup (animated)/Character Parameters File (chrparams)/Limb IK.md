# Limb IK

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/23308002
- Page ID: 23308002
- Breadcrumb: Asset Prep (External) > Asset Exporting Overview > Geometry Creation Overview > Animated Geometry > Character (animated) > Engine Setup (animated) > Character Parameters File (chrparams) > Limb IK
- Parent: Character Parameters File (chrparams)

## Content

##
Overview

CRYENGINE's animation system allows you to setup IK chains for characters.

When an IK chain is active, the system figures out the values for the joints that are part of the chain so that the end effector reaches the provided target position (if it's possible to reach it). The exact behavior for each chain and the amount of joints supported depends on the solver used.

[Image: /docs/static/attachments/23994450]

Examples of systems that currently use LimbIK chains:

-
[/docs/static/engines/cryengine-5/categories/23756816/pages/23308004](
Leg and Foot Ground Alignment
)

-
[/docs/static/engines/cryengine-5/categories/23756816/pages/23308003](
Animation Driven IK
)

##
Setup

IK chains are defined in the
[/docs/static/engines/cryengine-5/categories/23756816/pages/23307999](
chrparams file
)
 for a character

```

`
<Params>
  <IK_Definition>
    <LimbIK_Definition>
      <IK EndEffector="Bip01 R Hand" Handle="RgtArm01" Root="Bip01 R UpperArm" Solver="2BIK"/>
      ...
      <IK EndEffector="Bip01 L Foot" Handle="LftLeg01" Root="Bip01 L Thigh" Solver="2BIK"/>
    </LimbIK_Definition>
    ...
  </IK_Definition>
  ...
</Params>
`

```

The following summarizes the attributes that must be defined for each IK element.

EndEffector
 |
Name of the joint that will try to reach the target location
 |

Handle
 |
Name used to identify the LimbIk definition. No more than 8 characters allowed. No two LimbIK definitions for a character should have the same Handle.
 |

Root
 |
Name of the starting joint for the IK chain
 |

Solver
 |
Name of the solver used to calculate the joint values when the chain is active.
 |

These are the available solvers:

2BIK
 |
2 bone IK
 |

3BIK
 |
3 bone IK
 |

CCDX
 |
Cyclic Coordinate Descent with X joints
 |
