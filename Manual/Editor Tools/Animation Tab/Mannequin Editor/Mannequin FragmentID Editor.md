# Mannequin FragmentID Editor

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/23308446
- Page ID: 23308446
- Breadcrumb: Editor Tools > Animation Tab > Mannequin Editor > Mannequin FragmentID Editor
- Parent: Mannequin Editor

## Content

### Overview

![Image](https://www.cryengine.com/docs/static/attachments/23998311)

The [FragmentID](Mannequin%20Concepts/FragmentIDs.md)editor is used to edit a fragmentID's name as well as the fragment definition properties that are stored in the [Controller Definition File (xxxControllerDefs.xml)](Mannequin%20Files/Controller%20Definition%20File%20(xxxControllerDefs.xml).md).

For a very simple example of its use see the [Mannequin Editor Tutorial 1 - Preview Setup, Fragments and Saving](../../../Tutorials/Animation%20and%20Characters/Mannequin%20Editor/Mannequin%20Editor%20Tutorial%201%20-%20Preview%20Setup%2C%20Fragments%20and%20Saving.md).

### Functions

- *Fragment ID Name*: the name of this fragmentID.
- *Tags Definition*: The tag definition file containing the [FragmentID-specific Tags (fragtags)](Mannequin%20Concepts/FragmentID-specific%20Tags%20(fragtags).md) for this fragmentID.
- *Edit*: Edit the selected tag definition file in the [Mannequin Tag Definition Editor](Mannequin%20Tag%20Definition%20Editor.md).
- *Database File*:
- *New*: Move this fragment into a new sub-ADB file.
- *Persistent*: Forces the action to keep playing, even when the fragment that is playing is not looping and has ended.
- *Auto Update*: When this fragmentID is installed in the game, it constantly checks whether there is a fragment available that matches the current [Mannequin TagState](Mannequin%20Concepts/Mannequin%20TagState.md) better than the current one. If so, the system will push the new, better matching fragment for you. Useful for basic 'idling' actions. Typically used together with the "Persistent" flag.
- *Default Scopes*: The default [scopemask](Mannequin%20Concepts/Mannequin%20Scopemasks.md)assigned to this fragmentID. (it is called 'default' as it can be overridden by the programmer)
- *OK/Cancel*: Apply/Cancel changes.
