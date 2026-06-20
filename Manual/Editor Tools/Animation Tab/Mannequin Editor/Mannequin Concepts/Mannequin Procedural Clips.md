# Mannequin Procedural Clips

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/29450878
- Page ID: 29450878
- Breadcrumb: Editor Tools > Animation Tab > Mannequin Editor > Mannequin Concepts > Mannequin Procedural Clips
- Parent: Mannequin Concepts

## Child Pages

- [Procedural Clip Directory](Mannequin Procedural Clips/Procedural Clip Directory.md)

## Content

[Image: /docs/static/attachments/29934027]

##
Overview

##
Sections

Procedural Clips are clips that can be placed in
[/docs/static/engines/cryengine-5/categories/23756816/pages/29450856](
fragments
)
 and allow to execute custom code in sync with the rest of the fragment. They are sequenced like other clips so are started (entered) and stopped (exited) for you, and can have custom parameters, trigger and blend duration timing.

We have Procedural Clips that range all the way from playing a sound and controlling joints on a character, to aligning an entity to a location specified by the game. Programmers can easily add new types.

Sensible use of these can let you be more hands off with the animation. E.g. no need to split animations to match sequencing to object swaps.

Game code can communicate with procedural clips through
[/docs/static/engines/cryengine-5/categories/23756816/pages/29450867](
parameters
)
 or procedural contexts (not to be confused with scope contexts).

[#sections](
Sections
)
[#types](
Types
)
[#creating-and-editing-procedural-clips](
Creating & Editing Procedural Clips
)
[#further-reading](
Further Reading
)

##
Types

For a list of supported Procedural Clips and short descriptions, see
[/docs/static/engines/cryengine-5/categories/23756816/pages/29798726](
Procedural Clip Directory
)
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
[/docs/static/engines/cryengine-5/categories/23756816/pages/27594502#MannequinEditor-FragmentEditor](
Mannequin Fragment Editor
)
.

##
Further Reading

-
[/docs/static/engines/cryengine-5/categories/23756816/pages/29798726](
Procedural Clip Directory
)
