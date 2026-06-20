# Animated

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/25534109
- Page ID: 25534109
- Breadcrumb: Asset Prep (External) > Asset Exporting Overview > Texture Creation Overview > Animated
- Parent: Texture Creation Overview

## Content

![Image](https://www.cryengine.com/docs/static/attachments/29933274)

## Overview

## Sections

In order to animate textures in Sandbox, you need to have a particular name in the material editor like this.

For a hands-on example please download this sample package [animate_test.rar](/docs/static/attachments/1442751).

[Sections](#sections)[Naming in the Material Editor](#naming-in-the-material-editor)[Texture names themselves](#texture-names-themselves)

### Naming in the Material Editor

.../number##ns_necount(0.5).dds

- number - Start of the texture name.
- ## - Digits of animated sequence (two characters # mean two digits of animated sequence).
- ns_ne - This is the first and last numbers of animated sequence respectively.
- count - Optional end of texture name.
- (0.5) - Optional time of single frame in seconds (default value is 0.05 seconds = 50 ms).

*Here is an example of the texture in the material editor: objects/number##00_04count(0.5).dds*

### Texture names themselves

Then the actual textures should have the following names: number00count.tif, number01count.tif,..., number05count.tif.

It's also possible to use the format: number00##. In this case the engine will try to load all textures from name number0000 until the last texture file that's available.

*Example texture files*
