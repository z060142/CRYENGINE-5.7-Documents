# Mannequin Scopemasks

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/29450861
- Page ID: 29450861
- Breadcrumb: Editor Tools > Animation Tab > Mannequin Editor > Mannequin Concepts > Mannequin Scopemasks
- Parent: Mannequin Concepts

## Content

![Image](https://www.cryengine.com/docs/static/attachments/29934024)

##
Overview

##
Sections

A scopemask is how we call the set of
[scopes](Mannequin%20Scopes.md)
 that a
[fragmentID](../Mannequin%20Files/FragmentID%20Definition%20File%20(xxxActions.xml).md)
 (more correctly: an
[action](../Mannequin%20Technical%20Topics/Mannequin%20Actions.md)
) will run on.

[Sections](#sections)
[Scopemask Examples](#scopemask-examples)
[Managing Scopemasks](#managing-scopemasks)

##
Scopemask Examples

-
A FireWeapon fragmentID could have a scopemask containing the Weapon scope (for animating the weapon) as well as the scope representing the Torso of the character. It doesn't need to contain the other scopes of the character because it can control the torso independently of the rest of the body using additive & partial body animation.

-
Standard movement fragmentIDs typically need control of the Base of the character, but nothing else. Head movement & weapon animation could be done independently.

-
A fragmentID used during a fully scripted action might need full control of the body, weapon and torso included. It typically contains
*
all
*
 scopes in the scopemask. Exceptions to this rule might be fully systemic scopes like the LookPose, described in the tutorial
[Tutorial - Controlling Looking (and Aiming) for AI in Mannequin](../../../../Tutorials/Animation%20and%20Characters/Mannequin%20Editor/Tutorial%20-%20Controlling%20Looking%20(and%20Aiming)%20for%20AI%20in%20Mannequin.md)
.

##
Managing Scopemasks

Typically the scope mask is determined by the
[FragmentID](../Mannequin%20Files/FragmentID%20Definition%20File%20(xxxActions.xml).md)
. Each fragmentID has a scopemask associated to it. (this is set up using the
[FragmentID Editor](../Mannequin%20FragmentID%20Editor.md)
 and stored in the
[controller definition](../Mannequin%20Files/Controller%20Definition%20File%20(xxxControllerDefs.xml).md)
)

It is possible to specify 'overrides' and select different scopemasks based on the
[global tagstate](Mannequin%20TagState.md)
 and requested fragtags. See the file format section in the article on the
[controller definition file](/docs/static/engines/cryengine-3/categories/1114113/pages/15011270)
 for more on how this is set up.

Optionally the scopemask and the overrides are overridden by the 'forced scopemask' that can be specified by the action itself.

When an action requests a fragmentID and is installed, the action will own the scopes in the fragmentID's scopemask. The system will then start playing fragments on these scopes. See
[Fragment Selection Process](Fragment%20Selection%20Process.md)
 for more information.

For programmers: a scopemask has the type ActionScopes which currently is just a uint32 in which each bit represents a scope. This determines the maximum number of scopes.
