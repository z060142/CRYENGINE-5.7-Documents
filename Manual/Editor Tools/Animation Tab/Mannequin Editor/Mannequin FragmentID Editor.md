# Mannequin FragmentID Editor

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/23308446
- Page ID: 23308446
- Breadcrumb: Editor Tools > Animation Tab > Mannequin Editor > Mannequin FragmentID Editor
- Parent: Mannequin Editor

## Content

##
Overview

[Image: /docs/static/attachments/23998311]

The
[/docs/static/engines/cryengine-5/categories/23756816/pages/23308432](
FragmentID
)
editor is used to edit a fragmentID's name as well as the fragment definition properties that are stored in the
[/docs/static/engines/cryengine-5/categories/23756816/pages/23308471](
Controller Definition File (xxxControllerDefs.xml)
)
.

For a very simple example of its use see the
[/docs/static/engines/cryengine-5/categories/23756816/pages/23308483](
Mannequin Editor Tutorial 1 - Preview Setup, Fragments and Saving
)
.

##
Functions

-
*
Fragment ID Name
*
:  the name of this fragmentID.

-
*
Tags Definition
*
: The tag definition file containing the
[/docs/static/engines/cryengine-5/categories/23756816/pages/23308434](
FragmentID-specific Tags (fragtags)
)
 for this fragmentID.

-
*
Edit
*
: Edit the selected tag definition file in the
[/docs/static/engines/cryengine-5/categories/23756816/pages/23308456](
Mannequin Tag Definition Editor
)
.

-
*
Database File
*
:

-
*
New
*
: Move this fragment into a new sub-ADB file.

-
*
Persistent
*
: Forces the action to keep playing, even when the fragment that is playing is not looping and has ended.

-
*
Auto Update
*
: When this fragmentID is installed in the game, it constantly checks whether there is a fragment available that matches the current
[/docs/static/engines/cryengine-5/categories/23756816/pages/23308435](
Mannequin TagState
)
 better than the current one. If so, the system will push the new, better matching fragment for you. Useful for basic 'idling' actions. Typically used together with the "Persistent" flag.

-
*
Default Scopes
*
: The default
[/docs/static/engines/cryengine-5/categories/23756816/pages/29450861](
scopemask
)
assigned to this fragmentID. (it is called 'default' as it can be overridden by the programmer)

-
*
OK/Cancel
*
: Apply/Cancel changes.
