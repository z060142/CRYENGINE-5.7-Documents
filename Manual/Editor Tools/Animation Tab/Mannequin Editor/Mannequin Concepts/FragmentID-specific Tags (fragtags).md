# FragmentID-specific Tags (fragtags)

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/23308434
- Page ID: 23308434
- Breadcrumb: Editor Tools > Animation Tab > Mannequin Editor > Mannequin Concepts > FragmentID-specific Tags (fragtags)
- Parent: Mannequin Concepts

## Content

##
Description

*
FragmentID-specific tags
*
 (also known as
*
fragtags
*
) are
[/docs/static/engines/cryengine-5/categories/23756816/pages/29450874](
tags
)
 that you can only assign to
[/docs/static/engines/cryengine-5/categories/23756816/pages/29450856](
fragments
)
 with a specific
[/docs/static/engines/cryengine-5/categories/23756816/pages/23308474](
fragmentID
)
.

They exist because many tags don't have to be available to all fragments. For example you might have a FragmentID "hit" grouping together all fragments containing hit reaction animations. The actual
*
type
*
 of hit (e.g. "headshot", "explosion", ...) would then be encoded in tags. But those tags are only useful in the context of this "hit" fragmentID. In this case we would make those tags FragmentID-specific.
As a matter of fact, most of your tags might be like this.

Another reason to keep your list of global tags small is performance. Even though the system has optimized tag storage and fast tag look-ups, the more global tags you have, the more memory they will take and the longer it will take for those look-ups.

##
Creating & Editing Fragtags

You create a list of fragtags by creating a new
[/docs/static/engines/cryengine-5/categories/23756816/pages/29450874](
tag definition
)
 in the
[/docs/static/engines/cryengine-5/categories/23756816/pages/23308456](
Mannequin Tag Definition Editor
)
.

Then you assign this new tag definition to a FragmentID (or FragmentIDs) in the
[/docs/static/engines/cryengine-5/categories/23756816/pages/23308446](
Mannequin FragmentID Editor
)
.

Each fragmentID can have only
*
one
*
 tag definition containing its fragtags, but for more complicated cases you can include (import) other tag definition files hierarchically from this one main tag definition. See the file format section of the
[/docs/static/engines/cryengine-5/categories/23756816/pages/23308473](
Tag Definition File (xxxTags.xml)
)
 article.

##
Storage

Fragtags are stored in separate
[/docs/static/engines/cryengine-5/categories/23756816/pages/23308473](
tag definition files
)
. They are linked to from the
[/docs/static/engines/cryengine-5/categories/23756816/pages/23308474](
fragmentID definition file
)
 as sub-tag-definitions.
