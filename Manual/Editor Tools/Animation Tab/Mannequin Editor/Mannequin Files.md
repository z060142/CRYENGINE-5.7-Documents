# Mannequin Files

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/23308470
- Page ID: 23308470
- Breadcrumb: Editor Tools > Animation Tab > Mannequin Editor > Mannequin Files
- Parent: Mannequin Editor

## Child Pages

- [Animation Database (ADB)](Mannequin%20Files/Animation%20Database%20(ADB).md)
- [Controller Definition File (xxxControllerDefs.xml)](Mannequin%20Files/Controller%20Definition%20File%20(xxxControllerDefs.xml).md)
- [FragmentID Definition File (xxxActions.xml)](Mannequin%20Files/FragmentID%20Definition%20File%20(xxxActions.xml).md)
- [Preview Setup File (xxxPreview.xml)](Mannequin%20Files/Preview%20Setup%20File%20(xxxPreview.xml).md)
- [Sequence File (xml)](Mannequin%20Files/Sequence%20File%20(xml).md)
- [Tag Definition File (xxxTags.xml)](Mannequin%20Files/Tag%20Definition%20File%20(xxxTags.xml).md)

## Content

##
Files used by the Game

Schematically, this is how the game refers to the mannequin files and how they refer to each other:

![Image](https://www.cryengine.com/docs/static/attachments/23998398)

It is simplified a bit as ADB files, FragmentID Definition and Tag Definitions can hierarchically refer to other files of their own type. And FragmentID definitions can refer to Tag Definitions to define FragmentID-specific Tag Definitions.

-
[Controller Definition File (xxxControllerDefs.xml)](Mannequin%20Files/Controller%20Definition%20File%20(xxxControllerDefs.xml).md)
 – Used to define a mannequin setup (this is the file you will typically refer to from your entity's lua file).

-
[Animation Database File (ADB)](Mannequin%20Files/Animation%20Database%20(ADB).md)
 – Stores fragments and transitions (see also
[Fragments](Mannequin%20Concepts/Mannequin%20Fragments.md)
 and
[Mannequin Transitions](Mannequin%20Concepts/Mannequin%20Transitions.md)
). It is also referred to from your entity's lua file, and other systems like the hit death reaction system might refer to them independently.

-
[Tag Definition File (xxxTags.xml)](Mannequin%20Files/Tag%20Definition%20File%20(xxxTags.xml).md)
 – Stores tag definitions (see also
[Mannequin Tags & Tag Definitions](Mannequin%20Concepts/Mannequin%20Tags%20%26%20Tag%20Definitions.md)
). It is referred to from both the Controller Definition and Animation Database files.

-
[FragmentID Definition File (xxxActions.xml)](Mannequin%20Files/FragmentID%20Definition%20File%20(xxxActions.xml).md)
 – Stores fragmentID definitions.
 It is referred to from both the Controller Definition and Animation Database files.

##
Files only used by the Editor

The editor runs independent of the game, so has to use its own setup file. Compare this picture with the picture above, the setup file effectively replaces whatever setup the Game Entity uses. The Sequence file is independent of all this.

![Image](https://www.cryengine.com/docs/static/attachments/23998399)

-
[Preview Setup File (xxxPreview.xml)](Mannequin%20Files/Preview%20Setup%20File%20(xxxPreview.xml).md)
 – Used to configure the editor.

-
[Sequence File (xml)](Mannequin%20Files/Sequence%20File%20(xml).md)
 – Used to store test sequences.
