# Posing Ragdolls

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/36869922
- Page ID: 36869922
- Breadcrumb: Physics > Posing Ragdolls
- Parent: Physics

## Content

##
Overview

This feature allows using the Physics Tool in the Sandbox to pose ragdoll entities when the simulation is not running. Collisions and additional constraints are supported. The pose can then be used as a starting state for the
**
Simulate Objects
**
 feature, or saved as a physics state directly.

Two IK modes are supported, one only minimizes kinetic energy change, and the other is a mix between energy minimization and pose preservation.

Since the Physics tool is used in its entirety in the PhysDebugger, the feature is available there as well.

##
Modes

There are two different modes:

##
Default mode

Measures the effects of each rotation angle on each body's velocity using vector sums, which makes it a precise estimate.

[Image: /docs/static/attachments/36849733]

##
Stiff mode

In Stiff mode, each rotation is weighted assuming that its children are immovable, so it tends to preserve the pose more.

[Image: /docs/static/attachments/36849734]

There is a command that can be added to toolbars for the Stiff mode called
**
Use Stiff IK Mode
**
. For more information about how to customize toolbars, see
[/docs/static/engines/cryengine-5/categories/23756816/pages/36870764](
Customizing ToolBars
)
.

##
Usage

To pose deadbody entities:

-
Add a deadbody entity into the level from
**
Create Object -> Legacy Entities -> Physics -> DeadBody
**
 (maybe add some geometry for it to fall onto if desired)

-
Turn on
[/docs/static/engines/cryengine-5/categories/23756816/pages/24283805](
Physics tool mode
)

This toolbar is not displayed by default

-
Enable the desired mode (Default or Stiff mode) by using the CVar
*
ed_PhysToolIKStiffMode
*
. For Default mode, set this to
**
0
**
, for Stiff mode, set to
**
1
**
.

-
Move the deadbody around

-
Use
**
Ctrl + LMB
**
 to drag the deadbody around and lock the dragged part's orientation.

-
Each move is automatically saved as a physics state, as if
**
Get Physics State
**
were used.

-
Choose
**
Simulate Objects
**
 if the ragdoll is non-sleeping and you want to simulate it further. Once the ragdoll goes to rest it'll save its state.

##
Collisions and Constraints

The ragdoll's limbs will be moved if it collides with the terrain or objects.

It is also possible to add constraints, so that the ragdoll will not move that specific part of its body.

Use
**
Shift + LMB
**
 to create
*
point constraints
*
 or
**
Shift + Ctrl + LMB
**
 for
*
"full"
*

*
constraints (position and rotation).
*
**
Shift + Alt + LMB
**
creates an Alignment constraint to align a bone with the surface that the normal of its largest bounding box's face points to. A common use of this constraint could be aligning a foot with the ground below it. This constraint only works on terminal bones.

Holding
**
Shift
**
 while dragging will cancel the dragging as soon as any collision is encountered (note that
**
Shift
**
 will have to be pressed
*
after
*
 the
**
LMB
**
, since otherwise the
**
LMB
**
 will create a constraint instead of entering drag mode). This can be useful if you want the ragdoll just touching something without trying to accommodate for the collision by pushing its bones back/aside, etc.

[Image: /docs/static/attachments/36849735]

*
Constraints
*

##
CVars

 The following CVars are related to this feature:

CVar/Command

 |
Description

 |
Comments
 |

**
ed_PhysToolIKStiffMode
**

 |
Selects the IK mode that is a mix of pose preservation and energy minimization.

 |
0 = default mode, 1 = stiff mode.
 |

**
ed_PhysToolIKPrec
**

 |
The precision (i.e. allowed error) with which the constraints are resolved (this includes both fixed constraints and the drag constraints that you pick objects with).

 |
In meters. It is recommended that this value be kept small, somewhere between 0.001 and 0.01.
 |

[#modes](
Modes
)
[#usage](
Usage
)
[#collisions-and-constraints](
Collisions and Constraints
)
[#cvars](
CVars
)
