# Detail

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/25534115
- Page ID: 25534115
- Breadcrumb: Asset Prep (External) > Asset Exporting Overview > Texture Creation Overview > Detail
- Parent: Texture Creation Overview

## Content

![Image](https://www.cryengine.com/docs/static/attachments/29934008)

## Overview

## Sections

Detail mapping is a simple technique to add surface detail (micro and macro) at relatively low cost, memory and performance wise.

[Sections](#sections)[Texture Creation](#texture-creation)[Example](#example)[CryTif Export](#crytif-export)

### Texture Creation

CRYENGINE uses a special approach with Detail maps, often referred to as "Unified" or "Merged" detail maps.

The reason for this is Detail maps in CRYENGINE include not only Normals information, but also Diffuse and Gloss information.

Channels are organized as follows:

- **Red**: Diffuse
- **Green**: Normal Red
- **Blue**: Gloss
- **Alpha**: Normal Green

If you're converting an existing Normal map into a Detail map, you can take the existing Red/Green channels and place them in the Green/Alpha channels respectively.

#### Example

To showcase how to create a Merged Detail Map, we're going to take an existing RGB Normal map:

*From Left to Right: RGB Channels, Red Channel, Green Channel, Blue Channel.*

Create an **Alpha** channel and place the ** Green** Channel into it.

Select the **Red** channel and paste that into the ** Green** channel.

The texture should now look something like this:

Now, for the **Red** and ** Blue** channels we're going to add a ** Diffuse** and a ** Gloss** map.

Pick a suitable **Diffuse** texture and place it in the ** Red** channel then pick a suitable ** Gloss** texture and place it in the ** Blue** channel.

*Left: Greyscale Diffuse, Right: Greyscale Glossmap*

The texture should now look something like this (depending on the luminosity of the R/B channels, color may vary):

*From Left to Right: RGB Channels, Red Channel, Green Channel, Blue Channel, Alpha Channel.*

#### CryTif Export

Two options are available for Merged Detail Maps: **Detail_MergedAlbedoNormalsSmoothness** (Using BC7 compression) or an additional **_Lossless** format.

Note that the Lossless format should be used with care as file size will be 4x larger.

Detail Maps are most often tiled fairly heavily, this means you can use smaller resolutions without noticeable a loss in quality as texel density will be high due to the tiling.
