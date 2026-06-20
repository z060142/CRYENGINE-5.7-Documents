# FragmentID-specific Tags (fragtags)

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/23308434
- Page ID: 23308434
- Breadcrumb: Editor Tools > Animation Tab > Mannequin Editor > Mannequin Concepts > FragmentID-specific Tags (fragtags)
- Parent: Mannequin Concepts

## Content

### Description

*FragmentID-specific tags* (also known as * fragtags*) are [tags](Mannequin%20Tags%20%26%20Tag%20Definitions.md) that you can only assign to [fragments](Mannequin%20Fragments.md) with a specific [fragmentID](../Mannequin%20Files/FragmentID%20Definition%20File%20(xxxActions.xml).md).

They exist because many tags don't have to be available to all fragments. For example you might have a FragmentID "hit" grouping together all fragments containing hit reaction animations. The actual *type* of hit (e.g. "headshot", "explosion",...) would then be encoded in tags. But those tags are only useful in the context of this "hit" fragmentID. In this case we would make those tags FragmentID-specific. As a matter of fact, most of your tags might be like this.

Another reason to keep your list of global tags small is performance. Even though the system has optimized tag storage and fast tag look-ups, the more global tags you have, the more memory they will take and the longer it will take for those look-ups.

### Creating & Editing Fragtags

You create a list of fragtags by creating a new [tag definition](Mannequin%20Tags%20%26%20Tag%20Definitions.md) in the [Mannequin Tag Definition Editor](../Mannequin%20Tag%20Definition%20Editor.md).

Then you assign this new tag definition to a FragmentID (or FragmentIDs) in the [Mannequin FragmentID Editor](../Mannequin%20FragmentID%20Editor.md).

Each fragmentID can have only *one* tag definition containing its fragtags, but for more complicated cases you can include (import) other tag definition files hierarchically from this one main tag definition. See the file format section of the [Tag Definition File (xxxTags.xml)](../Mannequin%20Files/Tag%20Definition%20File%20(xxxTags.xml).md) article.

### Storage

Fragtags are stored in separate [tag definition files](../Mannequin%20Files/Tag%20Definition%20File%20(xxxTags.xml).md). They are linked to from the [fragmentID definition file](../Mannequin%20Files/FragmentID%20Definition%20File%20(xxxActions.xml).md) as sub-tag-definitions.
