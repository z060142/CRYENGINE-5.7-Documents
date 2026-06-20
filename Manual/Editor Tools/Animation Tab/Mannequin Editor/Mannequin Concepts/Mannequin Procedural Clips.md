# Mannequin Procedural Clips

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/29450878
- Page ID: 29450878
- Breadcrumb: Editor Tools > Animation Tab > Mannequin Editor > Mannequin Concepts > Mannequin Procedural Clips
- Parent: Mannequin Concepts

## Child Pages

- [Procedural Clip Directory](Mannequin%20Procedural%20Clips/Procedural%20Clip%20Directory.md)

## Content

![Image](https://www.cryengine.com/docs/static/attachments/29934027)

##
Overview

##
Sections

Procedural Clips are clips that can be placed in
[fragments](Mannequin%20Fragments.md)
 and allow to execute custom code in sync with the rest of the fragment. They are sequenced like other clips so are started (entered) and stopped (exited) for you, and can have custom parameters, trigger and blend duration timing.

We have Procedural Clips that range all the way from playing a sound and controlling joints on a character, to aligning an entity to a location specified by the game. Programmers can easily add new types.

Sensible use of these can let you be more hands off with the animation. E.g. no need to split animations to match sequencing to object swaps.

Game code can communicate with procedural clips through
[parameters](Mannequin%20Parameters%20Conditions.md)
 or procedural contexts (not to be confused with scope contexts).

[Sections](#sections)
[Types](#types)
[Creating & Editing Procedural Clips](#creating-and-editing-procedural-clips)
[Further Reading](#further-reading)

##
Types

For a list of supported Procedural Clips and short descriptions, see
[Procedural Clip Directory](Mannequin%20Procedural%20Clips/Procedural%20Clip%20Directory.md)
.

(p
rocedural clips that appear in the editor and their default parameter values are listed in the
file
`
Scripts/Mannequin/ProcDefs.xml
`
)

##
Creating & Editing Procedural Clips

Procedural clips are placed on procedural layers within fragments in the
[Mannequin Fragment Editor](../../Mannequin%20Editor.md#MannequinEditor-FragmentEditor)
.

##
Further Reading

-
[Procedural Clip Directory](Mannequin%20Procedural%20Clips/Procedural%20Clip%20Directory.md)
