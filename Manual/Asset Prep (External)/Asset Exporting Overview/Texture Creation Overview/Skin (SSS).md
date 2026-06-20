# Skin (SSS)

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/25534119
- Page ID: 25534119
- Breadcrumb: Asset Prep (External) > Asset Exporting Overview > Texture Creation Overview > Skin (SSS)
- Parent: Texture Creation Overview

## Content

[Image: /docs/static/attachments/29933579]

##
Overview

##
Sections

The HumanSkin shader is a specialized shader for rendering skin surfaces as skin shading cannot be accurately reproduced using regular lighting models.

[Image: /docs/static/attachments/28898533]

[#sections](
Sections
)
[#shader-params](
Shader Params
)
[#using-the-humanskin-shader](
Using the HumanSkin shader
)

##
Shader Params

Shader Params

 |
Description

 |
Shader gen option

 |

**
Detail bump scale
**

 |
Controls the strength of the detail normal map (default 0.5)

 |
Detail normal map

 |

**
Displacement bias
**

 |
See
[/docs/static/engines/cryengine-3/categories/1114113/pages/1048776](
Tessellation and Displacement
)
 for more information.

 |
Displacement Mapping

 |

**
Displacement height scale
**

 |
See
[/docs/static/engines/cryengine-3/categories/1114113/pages/1048776](
Tessellation and Displacement
)
 for more information.

 |
Displacement Mapping

 |

**
Indirect bounce color
**

 |
See
[/docs/static/engines/cryengine-3/categories/1114113/pages/1048911](
Illum Shader
)
 for more information.

 |
All

 |

**
Melanin
**

 |
Legacy feature. Controls the amount of pigmentation in the skin (default 0.0)

 |
All

 |

**
SSS Index
**

 |
Functionally obsolete. The skin shader is locked to the skin SSS range (1.001 to 1.999) by default

 |
All

 |

**
Tessellation face cull
**

 |
See
[/docs/static/engines/cryengine-3/categories/1114113/pages/1048776](
Tessellation and Displacement
)
 for more information.

 |
Displacement Mapping

 |

**
Tessellation factor
**

 |
See
[/docs/static/engines/cryengine-3/categories/1114113/pages/1048776](
Tessellation and Displacement
)
 for more information.

 |
Displacement Mapping

 |

**
Tessellation factor max
**

 |
See
[/docs/static/engines/cryengine-3/categories/1114113/pages/1048776](
Tessellation and Displacement
)
 for more information.

 |
Displacement Mapping

 |

**
Tessellation factor min
**

 |
See
[/docs/static/engines/cryengine-3/categories/1114113/pages/1048776](
Tessellation and Displacement
)
 for more information.

 |
Displacement Mapping

 |

**
Translucency Multiplier
**

 |
Controls strength of the SSS feature (default 0.7)

 |
All

 |

**
Wrinkles blend
**

 |
Controls strength of the wrinkle map (default 1.0)

 |
Wrinkle blending

 |

##
Using the HumanSkin shader

This new version of the HumanSkin shader is fully integrated with the Physically Based Shading model. From a user standpoint, the shader has been streamlined - most tweaking takes place directly via the individual texture maps, with individual attributes of the shader being locked to the physically correct values. This enhances usability and insures consistency between assets. HumanSkin features some unique texture slots to give artists control over the specific features of the shader.

##
Diffuse

Its generally advisable to author 'flat' diffuse maps. I.e. when basing textures off photographs or scan information, its key to remove most lighting information. When hand-painting diffuse maps, the focus should be on color and hue changes. An exception to this is high-frequency Ambient Occlusion/Cavity information, which can be added to fake detail occlusion and shading.

##
Specular Map

In order to achieve a physically correct representation of human skin in the PBR model, a flat base-value of 51 should be used for the specular map. Adding subtle pore detail on top of that (simulating high frequency occlusion) will generally give the most convincing results. Also, to compensate for precision issues with occlusion and shadow casting, it can be helpful to paint in/darken details such as nostrils, cavities of the ear, etc.

##
Bumpmap (Normalmap)

For best results, it is advisable to experiment with the strength of high-frequency details on the highpoly source asset – i.e. keeping such details on separate layer(s) in the digital sculpting app, can be helpful.

##
Gloss (Normalmap Alpha)

On the large scale, the gloss map should capture how oily/shiny certain areas of e.g. a face are. This  Adding high contrast details will help to break up specular highlights and improve the look.

[Image: /docs/static/attachments/28898535]

##
Detail

The selected map will be overlayed with the base normalmap – an easy way to add very high-frequency detail to a model and further break up specular highlights. Tiling can be controlled in the tiling subsection of the texture slot.

[Image: /docs/static/attachments/28898534]

Detail
Detail normal map must be turned on in ‘Shader Generation Params’

##
Opacity Map (SubSurfaceScattering)

The SSS map should represent thin areas of skin that can readily be penetrated by light (e.g. ears, nostrils, etc.). SSS maps can be either manually authored or baked with an appropriate tool (e.g. with version 3.18.6, xNormal introduced a feature to bake translucency maps)

[Image: /docs/static/attachments/28898536]

##
Decal

Will overlay a secondary diffuse map (requires an alpha channel). This is useful to create variation of existing textures, e.g. add tattoos, warpaint or dirt.

[Image: /docs/static/attachments/28898533]

Decal
Decal Map must be turned on in ‘Shader Generation Params’
