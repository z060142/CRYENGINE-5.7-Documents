# Mannequin Fragments

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/29450856
- Page ID: 29450856
- Breadcrumb: Editor Tools > Animation Tab > Mannequin Editor > Mannequin Concepts > Mannequin Fragments
- Parent: Mannequin Concepts

## Child Pages

- [Fragment Selection Order](Mannequin%20Fragments/Fragment%20Selection%20Order.md)

## Content

![Image](https://www.cryengine.com/docs/static/attachments/29934021)

## Overview

## Sections

*Fragments* are the basic building block of interactive animation in CryMannequin. You play an animation by wrapping it in a fragment, and then play the fragment instead. More specifically fragments are layered sequences of animation clips & [Procedural Clips](Mannequin%20Procedural%20Clips.md). This means that you can lay out a couple of animation clips in a sequence, or layer them on top of each other, and treat them as * one*. Fragments are referred to by a [FragmentID](FragmentIDs.md) and [Tags](Mannequin%20Tags%20%26%20Tag%20Definitions.md). Multiple fragments can have the same fragmentID and tags, then we say that there are multiple * options.*

Fragments play on [Scopes](Mannequin%20Scopes.md). (there can only be one fragment playing on a scope at a time)

When going from one fragment to another, [Transitions](Mannequin%20Transitions.md) are used.

[Sections](#sections)[Creating and Editing Fragments](#creating-and-editing-fragments)[Storage](#storage)[Fragment ID Description](#fragment-id-description)[FragmentID or Transition?](#fragmentid-or-transition)[Creating & Editing FragmentIDs](#creating-and-editing-fragmentids)[Storage](#storage)

### Creating and Editing Fragments

Fragments are created in the [Mannequin Fragment Browser](../../Mannequin%20Editor.md#MannequinEditor-FragmentBrowser) and edited in the [Mannequin Fragment Editor](../../Mannequin%20Editor.md#MannequinEditor-FragmentEditor).

### Storage

Fragments are stored in an [Animation Database File (ADB)](../Mannequin%20Files/Animation%20Database%20(ADB).md).

Which ADB file a fragment you edit ends up in is determined as follows:

- First the system looks at the [scope](Mannequin%20Scopes.md) you are editing a fragment on. (e.g. FullBody).
- This scope has a certain [scope context](Mannequin%20Scopes/Mannequin%20Scope%20Contexts.md). This is defined in the [controller definition](../Mannequin%20Files/Controller%20Definition%20File%20(xxxControllerDefs.xml).md) (e.g. the FullBody scope might work on the MainCharacter scope context).
- Then the system looks at which ADB file is assigned to this scope context in the current [preview setup](../Mannequin%20Files/Preview%20Setup%20File%20(xxxPreview.xml).md), which is edited in the [context editor](../Mannequin%20Context%20Editor.md) (e.g. the MainCharacter scope context has MainCharacterAnims.adb assigned to it).
- The fragment will end up in this ADB file. It is possible for this ADB file to have optional rules that move the fragment into another ADB file, a sub-ADB. This is edited in the [animation DB editor](../Mannequin%20Animation%20DB%20Editor.md) (e.g. there might be a rule that moves fragments for the "hit" FragmentID into the sub-adb MainCharacterHitAnims.adb).

### Fragment ID Description

A *FragmentID* is the main label under which a fragment is stored.

The FragmentID represents an animation state like "Moving", "Idling", "Reloading", "Firing", etc... The game requests fragments by specifying this FragmentID. Contrary to what the name 'FragmentID' might suggest there are typically many fragments that fall under the same FragmentID. For example you can have many different "Moving" fragments: they represent either random variations or context-specific variations (moving while crouched, moving while standing, etc).

Typically a programmer defines a FragmentID for every basic animation state and then animators can create fragments for those FragmentIDs.

### FragmentID or Transition?

A good rule of thumb to define what should be a FragmentID: Reduce the states to the minimum, logically required to control the flow of the system. These are all the code needs to drive and can be taken as your key FragmentIDs.

For example this is how a Weapon Crafting feature could look like:

![Image](https://www.cryengine.com/docs/static/attachments/23998278)

If we need animations *between* FragmentIDs these are best handled as [Transitions](Mannequin%20Transitions.md). This reduces code and makes the system easier to modify purely through data:

![Image](https://www.cryengine.com/docs/static/attachments/23998279)

A grey area is the customization step. The swapping of a part needs to sequence removing a specific old part and inserting the new (left of the picture).

Or we could just request an alternate customize stance (change a tag specifying the stance and request a new fragment) and then let the transition system handle removing the old part and apply the new part. This would also let the animators drop in a single animation to do both steps if they wished.

![Image](https://www.cryengine.com/docs/static/attachments/23998280)

### Creating & Editing FragmentIDs

FragmentIDs are created, renamed and deleted in the Mannequin Fragment Browser.

You edit them in the [Mannequin FragmentID Editor](../Mannequin%20FragmentID%20Editor.md).

### Storage

FragmentIDs are stored in a [FragmentID Definition File (xxxActions.xml)](../Mannequin%20Files/FragmentID%20Definition%20File%20(xxxActions.xml).md), which is referred to from the main character setup, the [Controller Definition File (xxxControllerDefs.xml)](../Mannequin%20Files/Controller%20Definition%20File%20(xxxControllerDefs.xml).md).
