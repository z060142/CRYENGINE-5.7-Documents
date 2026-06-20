# Adding Constraints for Animated Characters

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/25533917
- Page ID: 25533917
- Breadcrumb: CRYENGINE Game Code > Miscellaneous Game Code > Adding Constraints for Animated Characters
- Parent: Miscellaneous Game Code

## Content

## Overview

From CRYENGINE 5.2, one can now use constraints (including self-constraints) with character/live skeletons.

If the constraint is not supposed to affect the character's animation, the skeleton's mass must be set to 0.

The below video illustrates the usage of constraints with live character skeleton:

[character_constraint1.avi](/docs/static/attachments/25516158)
---

### Creating Constraints for live characters

You can use the following methods to create constraints for an animated object/ live skeleton:

- Lua Scripting
- C++

To quickly check the feature one can modify the constraint entity (Scripts/Entities/Physics/Constraint.lua) to allow it to auto-connect to alive skeletons, by adding ent_independent to the list of sampling entities:

```
local ents = Physics.SamplePhysEnvironment(self:GetPos(), self.Properties.radius, ent_static+ent_rigid+ent_sleeping_rigid+ent_independent+ent_sort_by_mass);
```
