# Mannequin Files

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/23308470
- Page ID: 23308470
- Breadcrumb: Editor Tools > Animation Tab > Mannequin Editor > Mannequin Files
- Parent: Mannequin Editor

## Child Pages

- [Animation Database (ADB)](Mannequin Files/Animation Database (ADB).md)
- [Controller Definition File (xxxControllerDefs.xml)](Mannequin Files/Controller Definition File (xxxControllerDefs.xml).md)
- [FragmentID Definition File (xxxActions.xml)](Mannequin Files/FragmentID Definition File (xxxActions.xml).md)
- [Preview Setup File (xxxPreview.xml)](Mannequin Files/Preview Setup File (xxxPreview.xml).md)
- [Sequence File (xml)](Mannequin Files/Sequence File (xml).md)
- [Tag Definition File (xxxTags.xml)](Mannequin Files/Tag Definition File (xxxTags.xml).md)

## Content

##
Files used by the Game

Schematically, this is how the game refers to the mannequin files and how they refer to each other:

[Image: /docs/static/attachments/23998398]

It is simplified a bit as ADB files, FragmentID Definition and Tag Definitions can hierarchically refer to other files of their own type. And FragmentID definitions can refer to Tag Definitions to define FragmentID-specific Tag Definitions.

-
[/docs/static/engines/cryengine-5/categories/23756816/pages/23308471](
Controller Definition File (xxxControllerDefs.xml)
)
 – Used to define a mannequin setup (this is the file you will typically refer to from your entity's lua file).

-
[/docs/static/engines/cryengine-5/categories/23756816/pages/29798743](
Animation Database File (ADB)
)
 – Stores fragments and transitions (see also
[/docs/static/engines/cryengine-5/categories/23756816/pages/29450856](
Fragments
)
 and
[/docs/static/engines/cryengine-5/categories/23756816/pages/29450872](
Mannequin Transitions
)
). It is also referred to from your entity's lua file, and other systems like the hit death reaction system might refer to them independently.

-
[/docs/static/engines/cryengine-5/categories/23756816/pages/23308473](
Tag Definition File (xxxTags.xml)
)
 – Stores tag definitions (see also
[/docs/static/engines/cryengine-5/categories/23756816/pages/29450874](
Mannequin Tags & Tag Definitions
)
). It is referred to from both the Controller Definition and Animation Database files.

-
[/docs/static/engines/cryengine-5/categories/23756816/pages/23308474](
FragmentID Definition File (xxxActions.xml)
)
 – Stores fragmentID definitions.
 It is referred to from both the Controller Definition and Animation Database files.

##
Files only used by the Editor

The editor runs independent of the game, so has to use its own setup file. Compare this picture with the picture above, the setup file effectively replaces whatever setup the Game Entity uses. The Sequence file is independent of all this.

[Image: /docs/static/attachments/23998399]

-
[/docs/static/engines/cryengine-5/categories/23756816/pages/23308475](
Preview Setup File (xxxPreview.xml)
)
 – Used to configure the editor.

-
[/docs/static/engines/cryengine-5/categories/23756816/pages/23308476](
Sequence File (xml)
)
 – Used to store test sequences.
