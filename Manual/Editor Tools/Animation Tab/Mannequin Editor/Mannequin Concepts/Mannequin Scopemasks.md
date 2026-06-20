# Mannequin Scopemasks

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/29450861
- Page ID: 29450861
- Breadcrumb: Editor Tools > Animation Tab > Mannequin Editor > Mannequin Concepts > Mannequin Scopemasks
- Parent: Mannequin Concepts

## Content

[Image: /docs/static/attachments/29934024]

##
Overview

##
Sections

A scopemask is how we call the set of
[/docs/static/engines/cryengine-5/categories/23756816/pages/29450859](
scopes
)
 that a
[/docs/static/engines/cryengine-5/categories/23756816/pages/23308474](
fragmentID
)
 (more correctly: an
[/docs/static/engines/cryengine-5/categories/23756816/pages/23308467](
action
)
) will run on.

[#sections](
Sections
)
[#scopemask-examples](
Scopemask Examples
)
[#managing-scopemasks](
Managing Scopemasks
)

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
[/docs/static/engines/cryengine-5/categories/23756816/pages/23308487](
Tutorial - Controlling Looking (and Aiming) for AI in Mannequin
)
.

##
Managing Scopemasks

Typically the scope mask is determined by the
[/docs/static/engines/cryengine-5/categories/23756816/pages/23308474](
FragmentID
)
. Each fragmentID has a scopemask associated to it. (this is set up using the
[/docs/static/engines/cryengine-5/categories/23756816/pages/23308446](
FragmentID Editor
)
 and stored in the
[/docs/static/engines/cryengine-5/categories/23756816/pages/23308471](
controller definition
)
)

It is possible to specify 'overrides' and select different scopemasks based on the
[/docs/static/engines/cryengine-5/categories/23756816/pages/23308435](
global tagstate
)
 and requested fragtags. See the file format section in the article on the
[/docs/static/engines/cryengine-3/categories/1114113/pages/15011270](
controller definition file
)
 for more on how this is set up.

Optionally the scopemask and the overrides are overridden by the 'forced scopemask' that can be specified by the action itself.

When an action requests a fragmentID and is installed, the action will own the scopes in the fragmentID's scopemask. The system will then start playing fragments on these scopes. See
[/docs/static/engines/cryengine-5/categories/23756816/pages/23308439](
Fragment Selection Process
)
 for more information.

For programmers: a scopemask has the type ActionScopes which currently is just a uint32 in which each bit represents a scope. This determines the maximum number of scopes.
