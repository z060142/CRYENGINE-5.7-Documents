# Mannequin TagState

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/23308435
- Page ID: 23308435
- Breadcrumb: Editor Tools > Animation Tab > Mannequin Editor > Mannequin Concepts > Mannequin TagState
- Parent: Mannequin Concepts

## Content

##
Description

A tagstate is a combination of
[/docs/static/engines/cryengine-5/categories/23756816/pages/29450874](
tags
)
 from a
[/docs/static/engines/cryengine-5/categories/23756816/pages/29450874](
tag definition
)
. Tagstates can be represented by a list of tags separated by "+" characters. For example "crouching+pistol" defines a tagstate combining the tags "crouching" and "pistol".

There are many different places where sets of tags like this come up. Here are the most used ones and how they are typically called:

##
Global TagState

At any time the game can set global tags describing the current state of the character. These are called the global tagstate. They typically contain global state information like stance ("standing", "swimming", ..), character type, which weapon is equipped, etc.

For programmers: the global tagstate is the
*
tags
*
 member of the actioncontroller's
*
SAnimationContext
*
, which you can find with
*
IActionController::GetContext()
*
.

##
Fragment Tagstate

Each fragment gets labeled with tags in the
[/docs/static/engines/cryengine-5/categories/23756816/pages/27594502#MannequinEditor-Fragments](
Mannequin Fragment Browser
)
. Those can be either global tags or
[/docs/static/engines/cryengine-5/categories/23756816/pages/23308434](
FragmentID-specific Tags (fragtags)
)
.

They are used to find fragments during
[/docs/static/engines/cryengine-5/categories/23756816/pages/23308439](
fragment selection
)
.

##
Scope Tags

The tags associated with a scope, which is configured in the
[/docs/static/engines/cryengine-5/categories/23756816/pages/23308471](
Controller Definition File (xxxControllerDefs.xml)
)
. All fragments that play on this scope require these tags to be set. Typically this contains only one tag. It is recommended to use a specific naming convention for scope tags as opposed to other tags, for example prefixing them with the word "Scope".

See also
[/docs/static/engines/cryengine-5/categories/23756816/pages/23308439](
Fragment Selection Process
)
.
