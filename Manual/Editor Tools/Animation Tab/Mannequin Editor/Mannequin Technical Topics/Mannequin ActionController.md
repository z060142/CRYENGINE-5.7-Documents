# Mannequin ActionController

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/23308466
- Page ID: 23308466
- Breadcrumb: Editor Tools > Animation Tab > Mannequin Editor > Mannequin Technical Topics > Mannequin ActionController
- Parent: Mannequin Technical Topics

## Content

##
Overview

The ActionController (IActionController) is the root object controlling mannequin for a character. It is configured using a
[controller definition](../Mannequin%20Files/Controller%20Definition%20File%20(xxxControllerDefs.xml).md)
 (defining the
[fragmentIDs](../Mannequin%20Concepts/FragmentIDs.md)
,
[scopes](../Mannequin%20Concepts/Mannequin%20Scopes.md)
,
[scope contexts](../Mannequin%20Concepts/Mannequin%20Scopes/Mannequin%20Scope%20Contexts.md)
, etc). It schedules
[actions](Mannequin%20Actions.md)
 onto
[scopes](../Mannequin%20Concepts/Mannequin%20Scopes.md)
 and holds the
[global tagstate](../Mannequin%20Concepts/Mannequin%20TagState.md)
.

For more technical information on how to create and use an actioncontroller see
[Entity Setup From Scratch](Entity%20Setup%20From%20Scratch.md)
.
