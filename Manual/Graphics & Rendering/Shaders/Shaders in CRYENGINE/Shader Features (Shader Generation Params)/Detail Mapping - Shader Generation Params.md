# Detail Mapping - Shader Generation Params

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/29449936
- Page ID: 29449936
- Breadcrumb: Graphics & Rendering > Shaders > Shaders in CRYENGINE > Shader Features (Shader Generation Params) > Detail Mapping - Shader Generation Params
- Parent: Shader Features (Shader Generation Params)

## Content

##
Overview

Detail mapping is a simple technique to add surface detail (micro and macro) at relatively low cost, memory and performance wise.

Detail Map Off
 |
Detail Map On
 |

[Image: /docs/static/attachments/28898676]
 |
[Image: /docs/static/attachments/28898675]
 |

Simple Grey Diffuse with High Gloss
 |

[Image: /docs/static/attachments/28898669]
 |
[Image: /docs/static/attachments/28898668]
 |

Full Texture Set: Diffuse, Normals, Glossmap
 |

##
Texture Creation

CRYENGINE uses a special approach with Detail maps, often referred to as "Unified" or "Merged" detail maps.

The reason for this is Detail maps in CRYENGINE include not only Normals information, but also Diffuse and Gloss information.

Channels are organized as follows:

-
**
Red
**
: Diffuse

-
**
Green
**
: Normal Red

-
**
Blue
**
: Gloss

-
**
Alpha
**
: Normal Green
If you're converting an existing Normal map into a Detail map, you can take the existing Red/Green channels and place them in the Green/Alpha channels respectively.

[Image: /docs/static/attachments/35397172]

##
Example

To showcase how to create a Merged Detail Map, we're going to take an existing RGB Normal map:

*
From Left to Right: RGB channels, Red channel, Green channel, Blue channel
*

[Image: /docs/static/attachments/35397173]

[Image: /docs/static/attachments/35397174]

[Image: /docs/static/attachments/35397175]

[Image: /docs/static/attachments/35397176]

-
Create an
**
Alpha
**
 channel and place the
**
Green
**
 Channel into it.

-
Select the
**
Red
**
 channel and paste that into the
**
Green
**
 channel.

The texture should now look something like this:

[Image: /docs/static/attachments/28898667]

Now, for the
Red
 and
Blue
 channels we're going to add a
Diffuse
 and a
Gloss
 map.

-
Pick a suitable
**
Diffuse
**
 texture and place it in the
**
Red
**
 channel

-
Pick a suitable
**
Gloss
**
 texture and place it in the
**
Blue
**
 channel.
[Image: /docs/static/attachments/35397187]

[Image: /docs/static/attachments/28898664]

*
Left: Greyscale Diffuse, Right: Greyscale Glossmap
*

The texture should now look something like this (depending on the luminosity of the R/B channels, color may vary):

*
From Left to Right: RGB channels, Red channel, Green cahnnel, Blue channel, Alpha channel

*
[Image: /docs/static/attachments/28898672]

[Image: /docs/static/attachments/28898663]

[Image: /docs/static/attachments/28898674]

[Image: /docs/static/attachments/28898664]

*
[Image: /docs/static/attachments/28898673]
*

##
CryTif Export

Two options are available for Merged Detail Maps:
**
Detail_MergedAlbedoNormalsSmoothness
**
 (Using BC7 compression) or an additional
**
_Lossless
**
 format.

Note that the Lossless format should be used with care as file size will be 4x larger.

Detail Maps are most often tiled fairly heavily, this means you can use smaller resolutions with no noticeable loss in quality as texel density will be high due to the tiling.

[Image: /docs/static/attachments/35397185]

##
Material Setup

To use a Detail map, your Material should be using the
[/docs/static/engines/cryengine-5/categories/23756816/pages/29449070](
Illum Shader
)
.
[/docs/static/engines/cryengine-5/categories/23756816/pages/29449035](
HumanSkin
)
 and
[/docs/static/engines/cryengine-5/categories/23756816/pages/29449280](
Terrain.Layer
)
 shaders also use Detail maps but not Merged Detail maps, rather, the older Normal map style Detail maps.

-
To activate the Detail map, place the path to your Merged Detail map texture in the
**
Detail
**
 texture slot.

[Image: /docs/static/attachments/35397186]

As you can see from the above screenshot, the Detail map
tiling
 is controlled directly in the texture slot.

-
activate
**
D
**
**
etail mapping
**
 in
 Shader Generation Parameters.

Note that you will be unable to enable this checkbox if the Detail texture slot is empty.
Once enabled, this will activate three new sliders:

-
**
Detail bump scale
**
: Controls the intensity of the Green / Alpha channels (former Red/Green normal channels)

-
**
Detail diffuse scale
**
: Controls the intensity of the Red channel (greyscale diffuse texture)

-
**
Detail gloss scale
**
: Controls the intensity of the Blue channel (greyscale gloss texture)
The Detail bump scale is independent of other Material settings, a standard Normal map is not required for this to be used.

However, the Diffuse and Gloss scales are blended with the
**
Diffuse Color
**
 and
**
Glossiness
**
 Material settings respectively.

If you have a 0,0,0 Diffuse Color then you will not be able to see the Detail diffuse channel of your Detail map. If you have 0 Glossiness, you will not see the Detail gloss channel.

This control over independent channel output gives a large amount of flexibility and re-usability with Detail Maps so experiment with a variety of settings to suit your assets!

[#texture-creation](
Texture Creation
)
[#example](
Example
)
[#crytif-export](
CryTif Export
)
[#material-setup](
Material Setup
)
