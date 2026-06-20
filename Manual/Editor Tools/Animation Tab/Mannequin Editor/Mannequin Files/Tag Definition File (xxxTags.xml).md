# Tag Definition File (xxxTags.xml)

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/23308473
- Page ID: 23308473
- Breadcrumb: Editor Tools > Animation Tab > Mannequin Editor > Mannequin Files > Tag Definition File (xxxTags.xml)
- Parent: Mannequin Files

## Content

##
Description

A
*
Tag Definition File
*
 contains a tag definition, which is a collection of Tags. These tags are keywords used for labeling
[/docs/static/engines/cryengine-5/categories/23756816/pages/29450856](
Fragments
)
 (and
[/docs/static/engines/cryengine-5/categories/23756816/pages/29450872](
Mannequin Transitions
)
).

See
[/docs/static/engines/cryengine-5/categories/23756816/pages/29450874](
Mannequin Tags & Tag Definitions
)
 for more information on this concept.

Tag definition files are referenced by the
[/docs/static/engines/cryengine-5/categories/23756816/pages/23308471](
Controller Definition File (xxxControllerDefs.xml)
)
, any
[/docs/static/engines/cryengine-5/categories/23756816/pages/29798743](
Animation Database File (ADB)
)
, and (optionally) by
[/docs/static/engines/cryengine-5/categories/23756816/pages/23308474](
FragmentID Definition Files
)
. See the overview picture on the page about
[/docs/static/engines/cryengine-5/categories/23756816/pages/23308470](
Mannequin Files
)
.

Tag definition files can include other tag definition files hierarchically.

##
Creating a Tag Definition File

Tag Definition files can be created in the
[/docs/static/engines/cryengine-5/categories/23756816/pages/23308456](
Mannequin Tag Definition Editor
)
.

Tag Definition files are stored in the
*
Animations/Mannequin/ADB/
*
 folder. This is not an absolute requirement for the engine, but the
[/docs/static/engines/cryengine-5/categories/23756816/pages/23308456](
Mannequin Tag Definition Editor
)
 only looks for tag definition files in this folder currently.

The filename typically ends with
*
Tags.xml
*
. Again this is not an absolute requirement, but the editor will filter on this file ending.

##
Editing a Tag Definition File

Tag Definition files are edited in the

[/docs/static/engines/cryengine-5/categories/23756816/pages/23308456](
Mannequin Tag Definition Editor
)
.

However, you cannot edit the hierarchical inclusion of tag definition files in this editor. To use this advanced feature see the
[/docs/static/engines/cryengine-5/categories/23756816/pages/23308473#TagDefinitionFile(xxxTags.xml)-FileFormat](
FileFormat
)
 section.

##
File Format

This is an example of the current format (version 2)

```

`
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
`

```

The root element
*
TagDefinition
*
 should contain the proper version number.

The
*
Imports
*
 element contains a list of other included tag definition files. These are merged together during loading. (similar to an #include statement in C code) In this example we refer to a shared itemTags.xml tagdefinition which could contain tags related to item handling, which are shared between multiple character types.

The
*
Tags
*
 element contains the list of individual tags (
*
Tag
*
) and tag groups (
*
Group
*
).  Each
*
individual
*
 tag can get a priority. The default priority is 0.

The Tag Definition file uses a similar format as the
[/docs/static/engines/cryengine-5/categories/23756816/pages/23308474](
FragmentID Definition File (xxxActions.xml)
)
, as it uses the same underlying code, the
[/docs/static/engines/cryengine-5/categories/23756816/pages/23308477](
Mannequin CTagDefinition
)
.
