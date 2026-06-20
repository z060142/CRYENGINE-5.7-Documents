# FragmentIDs

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/23308432
- Page ID: 23308432
- Breadcrumb: Editor Tools > Animation Tab > Mannequin Editor > Mannequin Concepts > FragmentIDs
- Parent: Mannequin Concepts

## Content

##
Description

A
*
FragmentID
*
 is the main label under which a fragment is stored.

The FragmentID represents an animation state like "Moving", "Idling", "Reloading", "Firing", etc. The game requests fragments by specifying this FragmentID. Contrary to what the name 'FragmentID' might suggest there are typically many fragments that fall under the same FragmentID. For example you can have many different "Moving" fragments: they represent either random variations or context-specific variations (moving while crouched, moving while standing, etc).

Typically a programmer defines a FragmentID for every basic animation state and then animators can create fragments for those FragmentIDs.

##
FragmentID or Transition?

A good rule of thumb to define what should be a FragmentID: Reduce the states to the minimum logically required to control the flow of the system. These are all the code needs to drive and can be taken as your key FragmentIDs.

For example this is how a Weapon Crafting feature could look like:

[Image: /docs/static/attachments/23998278]

If we need animations
*
between
*
 FragmentIDs these are best handled as
[/docs/static/engines/cryengine-5/categories/23756816/pages/29450872](
Transitions
)
. This reduces code and makes the system easier to modify purely through data:

[Image: /docs/static/attachments/23998279]

A grey area is the customization step. The swapping of a part needs to sequence removing a specific old part and inserting the new (left of the picture).

Or we could just request an alternate customize stance (change a tag specifying the stance and request a new fragment) and then let the transition system handle removing the old and applying the new part.
This would also let the animators drop in a single animation to do both steps if they wished.

[Image: /docs/static/attachments/23998280]

##
Creating & Editing FragmentIDs

FragmentIDs are created, renamed and deleted in the
[/docs/static/engines/cryengine-5/categories/23756816/pages/27594502#MannequinEditor-Fragments](
Mannequin Fragment Browser
)
.

You edit them in the
[/docs/static/engines/cryengine-5/categories/23756816/pages/23308446](
Mannequin FragmentID Editor
)
.

##
Storage

FragmentIDs are stored in a
[/docs/static/engines/cryengine-5/categories/23756816/pages/23308474](
FragmentID Definition File (xxxActions.xml)
)
, which is referred to from the main character setup, the
[/docs/static/engines/cryengine-5/categories/23756816/pages/23308471](
Controller Definition File (xxxControllerDefs.xml)
)
.
