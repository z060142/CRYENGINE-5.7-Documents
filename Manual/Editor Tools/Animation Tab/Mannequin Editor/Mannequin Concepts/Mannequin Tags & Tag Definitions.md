# Mannequin Tags & Tag Definitions

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/29450874
- Page ID: 29450874
- Breadcrumb: Editor Tools > Animation Tab > Mannequin Editor > Mannequin Concepts > Mannequin Tags & Tag Definitions
- Parent: Mannequin Concepts

## Content

![Image](https://www.cryengine.com/docs/static/attachments/29934031)

## Overview

## Sections

A *Tag Definition* describes a collection of Tags. These tags are keywords used for labeling [fragments](Mannequin%20Fragments.md) (and [transitions](Mannequin%20Transitions.md)). To see how you assign tags to fragments and transitions, see the Mannequin Fragment Browser and [Mannequin Transition Browser](../../Mannequin%20Editor.md#MannequinEditor-TransitionBrowser) respectively.

Tags can have priorities associated with them. Tag priorities are used for ranking [TagStates](Mannequin%20TagState.md).

Tags can optionally be grouped together within Tag Groups, which are lists of tags that are mutually exclusive. For example you can have a group called "Weapon" which contains "Rifle", "Pistol" and "NoWeapon" tags. In this example you can never have both "Rifle" and "Pistol" tags set at the same time, which makes sense if you can only use one weapon at a time in your game.

Tag definition files can include other tag definition files hierarchically.

[Sections](#sections)[Creating Tag Definitions](#creating-tag-definitions)[Editing Tag Definitions](#editing-tag-definitions)[Associated File](#associated-file)[Code](#code)[TAG STATE](#tag-state)[Description](#description)[Global TagState](#global-tagstate)[Fragment Tagstate](#fragment-tagstate)[Scope Tags](#scope-tags)

### Creating Tag Definitions

You create Tag Definitions using the [Mannequin Tag Definition Editor](../Mannequin%20Tag%20Definition%20Editor.md).

### Editing Tag Definitions

You edit Tag Definitions using the [Mannequin Tag Definition Editor](../Mannequin%20Tag%20Definition%20Editor.md).

However, you cannot edit the hierarchical inclusion of other tag definition files in this editor. For this, you will need to manually edit the XML file. See the [Tag Definition File (xxxTags.xml)](../Mannequin%20Files/Tag%20Definition%20File%20(xxxTags.xml).md).

Each individual tag must have a unique name within a Tag Definition.

Casing of tags is ignored. So for example "rifle", "Rifle" and "RIFLE" are all seen as the same tag.

And even if tags are in different groups, they cannot be given the same name.

### Associated File

Tag definitions are stored in a [Tag Definition File (xxxTags.xml)](../Mannequin%20Files/Tag%20Definition%20File%20(xxxTags.xml).md).

### Code

In code, Tag Definitions are represented by a [Mannequin CTagDefinition](../Mannequin%20Technical%20Topics/Mannequin%20CTagDefinition.md).

### TAG STATE

### Description

A tagstate is a combination of tags from a [CRYENGINE V Manual](/docs/static/engines/cryengine-5/categories/23756816). Tagstates can be represented by a list of tags separated by "+" characters. For example "crouching+pistol" defines a tagstate combining the tags "crouching" and "pistol".

There are many different places where sets of tags like this come up. Here are the most used ones and how they are typically called:

### Global TagState

At any time the game can set global tags describing the current state of the character. These are called the global tagstate. They typically contain global state information like stance ("standing", "swimming" etc...), character type, which weapon is equipped, etc...

For programmers: the global tagstate is the *tags* member of the actioncontroller's * SAnimationContext*, which you can find with * IActionController::GetContext()*.

### Fragment Tagstate

Each fragment gets labeled with tags in the Mannequin Fragment Browser. Those can be either global tags or [FragmentID-specific Tags (fragtags)](FragmentID-specific%20Tags%20(fragtags).md).

They are used to find fragments during [fragment selection](Fragment%20Selection%20Process.md).

### Scope Tags

The tags associated with a scope, are configured in the [Controller Definition File (xxxControllerDefs.xml)](../Mannequin%20Files/Controller%20Definition%20File%20(xxxControllerDefs.xml).md). All fragments that play on this scope require these tags to be set. Typically this contains only one tag. It is recommended to use a specific naming convention for scope tags as opposed to other tags, for example prefixing them with the word "Scope".

See also [Fragment Selection Process](Fragment%20Selection%20Process.md).
