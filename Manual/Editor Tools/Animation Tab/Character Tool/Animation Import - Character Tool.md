# Animation Import - Character Tool

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/29450427
- Page ID: 29450427
- Breadcrumb: Editor Tools > Animation Tab > Character Tool > Animation Import - Character Tool
- Parent: Character Tool

## Content

##
Overview

The animation import process consists of the following steps:

Load an existing character in the Explorer by double clicking on it:

[Image: /docs/static/attachments/28900258]

Locate your newly created animation in the "Animations" group in Explorer and select it. All un-imported animations have an icon of a running man with an hole in his head. Note the differences in the icons below showing a compiled vs un-compiled animation  below:

-
FlagGrab_3p_01 - Running man with solid head.

-
FlagGrab_3p_02 - Running man with hole in the head.
[Image: /docs/static/attachments/28900255]

If you struggle to locate the new animation you can use advanced filtering options to do this. Press the
**
Filter
**
 icon in the top-right corner of the Assets panel, and then set "Only New" checkbox:

[Image: /docs/static/attachments/28900254]

If you still don't see your animations:

-
Make sure the folder they are in is in the animation list for this character (see the "Define animation list" section in
[/docs/static/engines/cryengine-5/categories/23756816/pages/44959476](
Creating Character Definition - Character Tool
)
.

-
The animations might have failed to compile. Look for RC errors in the log.
You may need to choose the Skeleton Alias in case the Character Tool wasn't able to match the loaded character to the skeleton alias.

To do this, click on the box next to
**
Skeleton Alias
**
 in the Properties and choose the skeleton you want from the context menu:

[Image: /docs/static/attachments/28900257]

If your skeleton is missing in the list, you can add it there through Compression / Skeleton List. See
[/docs/static/engines/cryengine-5/categories/23756816/pages/44959476](
Creating Character Definition
)
 for details.
