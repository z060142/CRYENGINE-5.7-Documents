# Mannequin Scopes

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/29450859
- Page ID: 29450859
- Breadcrumb: Editor Tools > Animation Tab > Mannequin Editor > Mannequin Concepts > Mannequin Scopes
- Parent: Mannequin Concepts

## Child Pages

- [Mannequin Scope Contexts](Mannequin%20Scopes/Mannequin%20Scope%20Contexts.md)

## Content

![Image](https://www.cryengine.com/docs/static/attachments/29934025)

## Overview

## Sections

A scope (also known as an [Action](../Mannequin%20Technical%20Topics/Mannequin%20Actions.md) Scope) is a high level animation *channel*.

Fragments are played on scopes. (and more technical: [actions](../Mannequin%20Technical%20Topics/Mannequin%20Actions.md) control scopes)

A scope represents where fragments get triggered. Scopes can be used to drive:

- Different parts of the body (Base body, Torso, Legs)

- Different entities that are synchronized to the main entity (Weapon, Attachments, Target Player)

They can also represent more abstract channels:

- Systemic animation (ProceduralLooking, ProceduralWeaponMovement,...)
- Systems not directly related to animation (ForceFeedback, WeaponSound,...)

[Sections](#sections)[Scope Structure](#scope-structure)[Example](#example)[Creating & Editing Scopes](#creating-and-editing-scopes)

### Scope Structure

To do this, each scope has:

- A [scope context](Mannequin%20Scopes/Mannequin%20Scope%20Contexts.md), which contains:
- an Entity, the entity this scope plays on. Typically a scope plays on a main entity, but it can also play on attached entities like weapons or other entities or characters that this character interacts with.
- (optional) a Character in that Entity (entities can have multiple characters attached to them, so you need to specify which one)
- an [Animation Database](../Mannequin%20Files/Animation%20Database%20(ADB).md), containing the fragments to play on this scope.
- A range of [animation layers](../Mannequin%20Animation%20Layers.md) to play animations on. Any animation clips in fragments that are playing on this scope will end up on those layers. You can also specify that this scope refers to no layers at all, which is useful for the more abstract scopes that only use [procedural clips](Mannequin%20Procedural%20Clips.md).
- (optional) [Scope Tags](Mannequin%20TagState.md), to make sure only fragments with those tags are played on this scope (needed to play different fragments on different scopes that use the same scope context)

### Example

Here we see a screenshot of the [Mannequin Fragment Editor](../../Mannequin%20Editor.md#MannequinEditor-FragmentEditor).

To the left you see a list of the scopes available in this mannequin setup. The four scopes with the movie icon (FullBody3P, Looking, AimPose, Aiming) are part of the scope mask, and we can edit the fragments on those scopes.

We opened up the fragmentID "CoverAction" (see top left), with tags "CoverHigh" and fragtags "CoverLftShoot". This opened up **four** fragments. The ones on the FullBody3P, AimPose and Aiming scope are clearly visible. The one on the Looking scope is also there, but empty. This also means that when an action plays this combination of fragmentID & tags, there will be nothing playing on the Looking scope.

To understand this example setup, read the tutorial [Tutorial - Controlling Looking (and Aiming) for AI in Mannequin](../../../../Tutorials/Animation%20and%20Characters/Mannequin%20Editor/Tutorial%20-%20Controlling%20Looking%20(and%20Aiming)%20for%20AI%20in%20Mannequin.md).

### Creating & Editing Scopes

Scopes are created and edited by editing the [Controller Definition File (xxxControllerDefs.xml)](../Mannequin%20Files/Controller%20Definition%20File%20(xxxControllerDefs.xml).md).
