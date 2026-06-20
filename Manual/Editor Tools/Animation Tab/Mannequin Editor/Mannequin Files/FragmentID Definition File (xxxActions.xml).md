# FragmentID Definition File (xxxActions.xml)

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/23308474
- Page ID: 23308474
- Breadcrumb: Editor Tools > Animation Tab > Mannequin Editor > Mannequin Files > FragmentID Definition File (xxxActions.xml)
- Parent: Mannequin Files

## Content

### Description

A *FragmentID Definition File* contains a FragmentID definition, which is basically a collection of names for [FragmentIDs](../Mannequin%20Concepts/FragmentIDs.md). They are used to define which FragmentIDs a mannequin character can use.

FragmentID definition files are referenced by the [Controller Definition File](Controller%20Definition%20File%20(xxxControllerDefs.xml).md) and any [Animation Database File](Animation%20Database%20(ADB).md). Or they can be included hierarchically in other FragmentID definition files. See the overview picture on the page about [Mannequin Files](../Mannequin%20Files.md).

FragmentID definition files can refer to [Tag Definition Files](Tag%20Definition%20File%20(xxxTags.xml).md) to define [FragmentID-specific Tags (fragtags)](../Mannequin%20Concepts/FragmentID-specific%20Tags%20(fragtags).md).

### Creating a FragmentID Definition File

FragmentID Definition files have to be created manually. See the [FileFormat](FragmentID%20Definition%20File%20(xxxActions.xml).md#FragmentIDDefinitionFile%28xxxActions.xml)-FileFormat) section.

FragmentID Definition files are stored in the *Animations/Mannequin/ADB/* folder. This is not an absolute requirement for the engine though.

The filename typically ends with *Actions.xml*, at least in the provided examples. But this is not a requirement at all. To prevent confusion it's better to use something like "FragmentID" in the name.

### Editing a FragmentID Definition File

FragmentID Definition files are edited indirectly by adding/removing/renaming FragmentIDs using the [Mannequin Fragment Browser](../../Mannequin%20Editor.md#MannequinEditor-Fragments) and editing their settings using the [Mannequin FragmentID Editor](../Mannequin%20FragmentID%20Editor.md).

### File Format

This is an example of the current format (version 2)

```
<TagDefinition version="2">
<Imports>
<Import filename="Animations/Mannequin/ADB/itemActions.xml"/>
</Imports>
<Tags>
<Tag name="MotionIdle"/>
<Tag name="MotionMovement"/>
<Tag name="LedgeGrab" subTagDef="Animations/Mannequin/ADB/LedgeGrabTags.xml"/>
<Tag name="Interact" subTagDef="Animations/Mannequin/ADB/InteractiveActionTags.xml"/>
</Tags>
</TagDefinition>
```

The root element is *TagDefinition* (* NOT* FragmentIDDefinition which you might expect) and should contain the proper version number. The current version is 2.

The *Imports* element contains a list of other included fragmentID definition files. These are merged together during loading. (similar to an #include statement in C code) In this example we refer to a shared itemActions.xml fragmentID definition which could contain fragmentIDs related to item handling, which are shared between multiple character types.

The *Tags* element contains the list of individual FragmentIDs in * Tag*elements. Each individual FragmentID can have a Tag Definition assigned to it containing [FragmentID-specific Tags (fragtags)](../Mannequin%20Concepts/FragmentID-specific%20Tags%20(fragtags).md). This is done by specifying a [Tag Definition File (xxxTags.xml)](Tag%20Definition%20File%20(xxxTags.xml).md) in the * subTagDef* attribute.

The FragmentID Definition file uses a similar format as the [Tag Definition File (xxxTags.xml)](Tag%20Definition%20File%20(xxxTags.xml).md), as it uses the same underlying code, the [Mannequin CTagDefinition](../Mannequin%20Technical%20Topics/Mannequin%20CTagDefinition.md).
