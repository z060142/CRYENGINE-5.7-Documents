# Bone Requirements

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/23308001
- Page ID: 23308001
- Breadcrumb: Asset Prep (External) > Asset Exporting Overview > Geometry Creation Overview > Animated Geometry > Character (animated) > Engine Setup (animated) > Character Parameters File (chrparams) > Bone Requirements
- Parent: Character Parameters File (chrparams)

## Content

Since SDK release 3.5 the hardcoded joints names referred to in this document are not required or replaced by entries in the chrparams file.

### Overview

CRYENGINE was originally developed to work only with Biped skeletons for humanoid characters. This has caused some hard-coded bone name requirements inside the engine for various systems (for example Look IK or GroundAlignment).

Through the introduction of the.chrparams file, which allows the specification of bone names for specific features, these requirements are being removed. This process is however not yet complete and some bone name requirements remain for certain features to work properly.

### Look IK

Two additional bones are required for the character in order to make sure that Look IK actually works.

##### Left Eye

**eye_left_bone** – placed where the pivots of the left eye should be.

##### Right Eye

**eye_right_bone** – placed where the pivots of the right eye should be.

### Footsteps

Three additional bones per leg are required to identify the character as a human character model and to make sure footsteps work.

##### Left Leg

**Bip01 L Heel** – This bone needs to be placed at the base of the foot in the location where the heel of the character should be. ** Bip01 L Toe0** – This bone is used for the front part of the foot/toes. ** Bip01 L Toe0Nub** – This bone is placed as a terminator to the toe bone (standard CS Biped includes this by default).

##### Right Leg

**Bip01 R Heel** – This bone needs to be placed at the base of the foot in the location where the heel of the character should be. ** Bip01 R Toe0** – This bone is used for the front part of the foot/toes. ** Bip01 R Toe0Nub** – This bone is placed as a terminator to the toe bone (standard CS Biped includes this by default).

[Look IK](#look-ik)[Left Eye](#left-eye)[Right Eye](#right-eye)[Footsteps](#footsteps)[Left Leg](#left-leg)[Right Leg](#right-leg)
