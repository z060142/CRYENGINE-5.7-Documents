# Rope Setup

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/23307980
- Page ID: 23307980
- Breadcrumb: Asset Prep (External) > Asset Exporting Overview > Geometry Creation Overview > Animated Geometry > Basics (animated) > Physics (animated) > Rope Setup
- Parent: Physics (animated)

## Content

![Image](https://www.cryengine.com/docs/static/attachments/29934061)

## Overview

## Sections

Ropes (or Character Ropes) have many purposes but are mainly used for attaching cloth, hair, or ropes to a character so that the objects can dangle, shake and deform realistically against the player and other objects.

[Sections](#sections)[Example Files](#example-files)[General Setup](#general-setup)[Setup in Sandbox](#setup-in-sandbox)[Properties](#properties)

### Example Files

- [chr_rope.rar](/docs/static/attachments/23994256): This package includes example files for Max and Maya as well as a pre-defined.cdf file.

### General Setup

The only important thing is to have bone names start with 'rope'. Everything from the word 'rope' up to the next space constitutes the rope's name, which should be entered in the editor properties. If several ropes are present in the file, they should be named ropeXXX1/2/3 etc... so that the script can iterate through them while setting properties.

- Bone should be named as follows: "Rope<number> Seg<number>".
- The segments of the same cloth should have the same "Rope" number.
- The segments of the same cloth should be named sequentially starting with "Seg01" being the very first bone to be simulated.
- The hierarchy of the joints should be going from top to bottom as in a regular bone chain.
- The last bone being simulated in each strand should never be the last bone in the strands hierarchy. It always needs a terminating bone. The terminating bone should still be following the naming convention of the strand-bones (i.e. Rope1 Seg04 in the picture above is the last bone simulated in the first strand. The terminating bone is Rope1 Seg05. The next strand continues by starting with the bone Rope1 Seg06.

**For Max Users**: By indexing the Chainname, it is possible to use several chains/rope objects in one file. It is useful to double-click select the root bone of the chain (will select all children) and use the 3ds Max Renaming Tool.

**For Maya Users**: Be sure to parent a polygon to the root of the rope with a proxy no draw material assigned to it and the following naming conventions: Rope1_Seg01_physShape

### Setup in Sandbox

- Open the character you are using in the Character Editor and add a new attachment and set the asset as your Ragdoll.
- To simulate: Click 'AI/PHYSICS' on the bottom of the screen.
- Further tweaking should be made through a.cdf file made from the.chr file. This will allow in-depth customization of the simulation. Load the.chr file into the character editor and create a new bone attachment with the rope root set as the attachment, then select the box at the bottom labeled "PhysPropsAlive..."

![Image](https://www.cryengine.com/docs/static/attachments/23994261)

### Properties

Here is a list of what the properties mean in the Rope Alive tab of the character editor:

- Gravity - whether gravity will be applied on top of the initial pose (meaning that when on, the rope's stable simulated pose will be lower than the target pose from the animation.)
- 0 disables gravity, values over 90 are not practical.
- JointLimit - per-segment bending limit in angles.
- JointLimitIncrease - how much JointLimit increases towards the end (in fractions of 1). So, if JointLimit is 10 and JointLimitIncrease is 0.8, the limit will be 10 at the base, and 18 at the last segment
- Multiply JointLimit by 1+ this variable to get the limit at the end to see if it makes sense.
- MaxTimeStep - time step granularity. smaller timesteps produce smoother results, but are more expensive. Normally you don't need any substeps for ropes, so you can set it to large values like 0.05 or even 1 (unless you use very stiff or long ropes.)
- 0.01 for really complex ropes, 0.05 for simple. typically don’t need to go higher than your 1/framerate
- SimpleBlending - when on, target pose matching will be done by using independent linear spring targets at each rope vertex. When off - by properly applying angular forces at joints. The first method is more controllable/predictable (especially on longer ropes), the second is more realistic.
- Generally about 10 in no-simple-blending, can be 100 in simple, but overall very flexible.
- Stiffness - affects the speed with which the rope returns to the target pose. 10 is a good starting point for tweaking. higher values can compromise simulation stability (might need lower MaxTimeStep), though SimpleBlending mode is less susceptible to that. Note that 0 means a fully animated rope, to make a very limp rope use a small but non-0 number (like 0.01)
- StiffnessDecay - how much Stiffness decreases towards the end of the rope. 1 means full decay (100%), a completely limp segment.
- Numbers should be on a scale of 0-1.
- Damping - dampens the rope's oscillations created by stiffness. so, it should be tweaked in conjunction with the latter. The default 1 is a good starting point for adjustments. It's better to start with an under-damped state and gradually go up, since over-damped simulations are harder to spot, so they might look "ok-ish" while in fact being rather sub-optimal.
- 0-1 is weak, 1-3 is average, 3+ is strong.
- Friction - sliding friction at collision points. 0 means no friction, 1 is "somewhat average".
- About 0.4 is ok for characters, 2+ is super-sticky.
- Mass - only affects how much velocity the rope gets from external impulses (heavier ropes are affected less).
- Anything which is not 0 is sufficient.
- Thickness - radius of the rope for the simulation. When collisions are on, it's better not to use excessively thick ropes (keep radius below 10% of a segment's length - although it's a very "soft" restriction)
- StiffnessControlBone - when it's set to a non-0 integer value N, the code will scale the current stiffness and damping with the rotation of a bone named "rope_stiffness_controller_N" (100 angles rotation = *1.0)
- BodyCollisions - enables collisions with the character skeleton
- EnvCollisions - enables collisions with the world
- HingeY,HingeZ - restricts rotation to either Y or Z axis (not recommended for ropes with world collisions)
