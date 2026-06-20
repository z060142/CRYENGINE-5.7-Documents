# Fall and Play

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/23306436
- Page ID: 23306436
- Breadcrumb: CRYENGINE Engine Code > Engine Modules > CryAnimation > Fall and Play
- Parent: CryAnimation

## Content

##
Overview

"Fall-and-Play" is activated when a character is ragdollized (on in interface level, it is called
*
RelinquishCharacterPhysics
*
) with a >0 stiffness. This will activate angular springs in the physical ragdoll that will attempt to bring the joints to the angles specified in the current animation frame. The character will also try to select an animation internally based on the current f'n'p stage. If there are none, or very few, physical contacts, this will be a falling animation, otherwise it will be the first frame of a standup animation that corresponds to the current body orientation.

Standup is initiated from outside the animation system through the appropriately named function. During the standup, the character physics is switched back into an alive mode and his final physical pose is blended into a corresponding standup animation. This, again, is selected from a standup anims list to best match this pose.

There are a filename covention for standup animations. When there is an animation with which name starts with "standup", it's registered as a standup animation. Also there is a type system which categorizes standup animations by the string between "standup_" and some keywords("back", "stomach", "side"). And you can control which type to use by _CSkeletonPose::SetFnPAnimGroup()_methods. Then on run-time, the engine checks the most similar standup animation registered to the current lying pose and starts blending to it.

You can name stand-up animations as follows, for example.

-
*
standUp_toCombat_nw_back_01
*

-
*
standUp_toCombat_nw_stomach_01
*
At any moment when the character is still a ragdoll it's also possible to turn the stiffness off with a
*
GoLimp
*
 method.
