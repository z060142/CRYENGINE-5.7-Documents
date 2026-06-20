# Tag Definition File (xxxTags.xml)

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/23308473
- Page ID: 23308473
- Breadcrumb: Editor Tools > Animation Tab > Mannequin Editor > Mannequin Files > Tag Definition File (xxxTags.xml)
- Parent: Mannequin Files

## Content

### Description

A *Tag Definition File* contains a tag definition, which is a collection of Tags. These tags are keywords used for labeling [Fragments](../Mannequin%20Concepts/Mannequin%20Fragments.md) (and [Mannequin Transitions](../Mannequin%20Concepts/Mannequin%20Transitions.md)).

See [Mannequin Tags & Tag Definitions](../Mannequin%20Concepts/Mannequin%20Tags%20%26%20Tag%20Definitions.md) for more information on this concept.

Tag definition files are referenced by the [Controller Definition File (xxxControllerDefs.xml)](Controller%20Definition%20File%20(xxxControllerDefs.xml).md), any [Animation Database File (ADB)](Animation%20Database%20(ADB).md), and (optionally) by [FragmentID Definition Files](FragmentID%20Definition%20File%20(xxxActions.xml).md). See the overview picture on the page about [Mannequin Files](../Mannequin%20Files.md).

Tag definition files can include other tag definition files hierarchically.

### Creating a Tag Definition File

Tag Definition files can be created in the [Mannequin Tag Definition Editor](../Mannequin%20Tag%20Definition%20Editor.md).

Tag Definition files are stored in the *Animations/Mannequin/ADB/* folder. This is not an absolute requirement for the engine, but the [Mannequin Tag Definition Editor](../Mannequin%20Tag%20Definition%20Editor.md) only looks for tag definition files in this folder currently.

The filename typically ends with *Tags.xml*. Again this is not an absolute requirement, but the editor will filter on this file ending.

### Editing a Tag Definition File

Tag Definition files are edited in the [Mannequin Tag Definition Editor](../Mannequin%20Tag%20Definition%20Editor.md).

However, you cannot edit the hierarchical inclusion of tag definition files in this editor. To use this advanced feature see the [FileFormat](Tag%20Definition%20File%20(xxxTags.xml).md#TagDefinitionFile%28xxxTags.xml)-FileFormat) section.

### File Format

This is an example of the current format (version 2)

```
<TagDefinition version="2">
<Imports>
<Import filename="Animations/Mannequin/ADB/itemTags.xml"/>
</Imports>
<Tags>
<Group name="Stance">
<Tag name="Relaxed" priority="2"/>
<Tag name="Alerted" priority="2"/>
<Tag name="Stand" priority="2"/>
</Group>
<Tag name="Slave"/>
<Tag name="Scope_Aiming"/>
<Tag name="Scope_Looking"/>
</Tags>
</TagDefinition>
```

The root element *TagDefinition* should contain the proper version number.

The *Imports* element contains a list of other included tag definition files. These are merged together during loading. (similar to an #include statement in C code) In this example we refer to a shared itemTags.xml tagdefinition which could contain tags related to item handling, which are shared between multiple character types.

The *Tags* element contains the list of individual tags (* Tag*) and tag groups (* Group*). Each * individual* tag can get a priority. The default priority is 0.

The Tag Definition file uses a similar format as the [FragmentID Definition File (xxxActions.xml)](FragmentID%20Definition%20File%20(xxxActions.xml).md), as it uses the same underlying code, the [Mannequin CTagDefinition](../Mannequin%20Technical%20Topics/Mannequin%20CTagDefinition.md).
