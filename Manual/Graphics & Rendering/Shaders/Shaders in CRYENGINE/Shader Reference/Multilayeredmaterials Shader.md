# Multilayeredmaterials Shader

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/44959873
- Page ID: 44959873
- Breadcrumb: Graphics & Rendering > Shaders > Shaders in CRYENGINE > Shader Reference > Multilayeredmaterials Shader
- Parent: Shader Reference

## Content

##
Overview

**
Multilayeredmaterials
**
 is a shader type that is used for modeling materials as a stack of thin layers, including an optional thin-film on top. Each of these layers is a micro-facet surface with its own physical properties, which when combined together, act as a single material with a unique optical response that generally can not be reproduced with the traditional single-layer models. This is especially useful for modelling synthetic materials, such as all kinds of treated surfaces (leather, wood, etc.), l
acquer
, paints, thin-translucent films applied to windows, thin-liquid films (soap, oil, etc.) and as well as metals of which the color and response arise due to an interference with a naturally occurring thin-layer of oxide.

##
Multi-layered Materials

A multi-layered material is a material consisting of a dielectric or conductive base layer, up to 2 dielectric layers and optionally an additional thin-film on top. Geometrically, all the layers are parallel to each other and each of them is a micro-facet surface with an individual roughness control:

The base layer is always active. Dielectric layers can be activated by specifying a
**
diffuse texture
**
, and a thin-film can be enabled as well by clicking the related checkbox on the
[Material Editor](../../../../Editor%20Tools/Material%20Editor.md)
's Properties panel. The layers model the thin coatings and not the additional geometry; therefore no per-layer geometric modulations (normal maps, all kinds of parallax mappings, etc.) conform to this context. The normal direction of the macroscopic surface of each layer is always the base layer's normal. The parametric controls of each layer are then the thickness, the roughness and the optical properties (diffuse color and refractive index) which can be modulated via a texture.

##
Thin-film and the Thin-film Interference

Thin-film interference is a

well-known phenomena

where the light that is reflected at the bottom of the film interferes with the light that is reflected at the top of the film. The constructive-destructive wave interference extinguishes some wavelengths while amplifying others, potentially producing color shifts as the angle of incidence changes (e.g. oxide film on a metallic surface) or rich color variations as the film's thickness varies (e.g. oil film on water).

As a light wave's phase can change upon reflection, the interference patterns of a thin-film greatly depend on the optical properties of the underlying surface. Dielectrics generally admit either phase inversion (phase shift of

π
) or no phase change on reflection, but can introduce any phase change when total reflection happens; i.e. when the thin-film has a higher refractive-index than the base layer and the incidence angle is high enough. On the other hand, reflections of conductors always result in a phase shift. To faithfully reproduce the color, the look and the feel of metals, it is crucial to take into account the interference with the naturally occurring layer of metallic oxide.

A common example is the tempering color chart used by blacksmiths to judge steel temperature. As iron or steel heats, its layer of iron oxide thickens resulting in a color change:

The same phenomena can be reproduced by adding a thin-film of high refractive-index to an iron base layer:

![Image](https://www.cryengine.com/docs/static/attachments/44964032)

 |
![Image](https://www.cryengine.com/docs/static/attachments/44964033)

 |
![Image](https://www.cryengine.com/docs/static/attachments/44964034)

 |
![Image](https://www.cryengine.com/docs/static/attachments/44964035)

 |
![Image](https://www.cryengine.com/docs/static/attachments/44964036)

 |

![Image](https://www.cryengine.com/docs/static/attachments/44964037)

 |
![Image](https://www.cryengine.com/docs/static/attachments/44964038)

 |
![Image](https://www.cryengine.com/docs/static/attachments/44964040)

 |
![Image](https://www.cryengine.com/docs/static/attachments/44964039)

 |
![Image](https://www.cryengine.com/docs/static/attachments/44964041)

 |

Some metals, like copper, exhibit strong non-uniform color shifts due to the natural oxide layer that forms on the surface. The Cu2O layer is very thin (up to 10 nanometers) but will slowly grow in time; a process that can be vastly accelerated and amplified when copper is

heated,

resulting in oxygen diffusion into the surface for, potentially, up to hundreds of nanometers.

From right to left, copper spheres rendered with;

no oxide layer
 |
thin layer (10nm)
 |
moderate layer (25nm)
 |
thick layer (50nm)
 |
very thick layer (75nm)
 |

![Image](https://www.cryengine.com/docs/static/attachments/44964043)

 |
![Image](https://www.cryengine.com/docs/static/attachments/44964044)

 |
![Image](https://www.cryengine.com/docs/static/attachments/44964045)

 |
![Image](https://www.cryengine.com/docs/static/attachments/44964046)

 |
![Image](https://www.cryengine.com/docs/static/attachments/44964047)

 |

##
Setting Up Layers

Layers are not isolated components; similar layers will produce a different response when combined with different layers, e.g. a rough layer on top of a smooth base will flatten the specular response of the base layer, while a smooth layer on top of a rough base will add a sharp specular highlight.

There are currently four different layers that can be assigned to a material via the
**
Multilayeredmaterials
**
 shader option in the
**
Material Editor
**
.

For more information about the shader parameters, please refer to the
[Material Editor](../../../../Editor%20Tools/Material%20Editor.md#MaterialEditor-shaderparams)
 reference page.

For more information about the dielectric and conductive layers, please see the
[Physically Based Shading (PBS)](../../Physically%20Based%20Shading%20(PBS).md)
 page.

##
Dielectric Base Layer

Use the following options to set up a dielectric base layer for the object:

-
**
Texture Maps → Base Layer Diffuse -
**
Assign a texture as the base layer. This texture will define the color of the light that is penetrating the base layer and scattering.

-
**
Shader Params → Base Layer Reflectivity -
**
 Choose a texture which will define the reflectivity, at a normal incidence, of the dielectric base layer.

-
**
Shader params
**
 →
**
Base layer Reflectivity Scale -
**
Specify what
*
Index of Refraction
*
(
[see below](Multilayeredmaterials%20Shader.md#MultilayeredmaterialsShader-ior)
) a fully white value in the reflectivity map maps to by adjusting the slider.

##
Conductive Base Layer

Use the following options to set up a conductive base layer for the object:

-
**
Texture Maps →
**

**
Base Layer Reflectivity -
**
Assign a texture to define the reflectivity at a normal incidence.

-
**
Shader Generation Params → Base layer is a conductor -
**
Set this
**

**
option to
**
true
**
 to display the
**
Base Layer Edge-tint
**
 field which will replace the
**
Base Layer Diffuse
**
field.

-
**
Texture Maps →
**

**
Base Layer Edge-tint -
**
Assign a texture to define the edge-tint of the conductor.

##
Additional Layers

Use the options below to set up additional layer(s) for the object:

-
**
Texture Maps → Layer 1 Diffuse/Layer 2 Diffuse -
**
 Assign a texture to one or both of these fields. The assigned texture(s) will define the color of the light scattered by the layer(s). The optional alpha channel modulates the optical thickness of the layer.

-
**
Texture Maps → Layer Smoothness Map -
**
Assign a texture to
**

**
modulate the smoothness of each layer (Red channel for Layer 1 and green channel for Layer 2).

-
**
Texture Maps → Layer 1 Reflectivity Map/Layer 2 Reflectivity Map -
**
Only available if a texture is assigned to Layer 1 Diffuse and Layer 2 Diffuse options. Choose a texture which will define the reflectivity, at a normal incidence, of the respective layer(s).

-
**
Shader Params
**
 →
**
Layer 1 Reflectivity Scale/Layer 2 Reflectivity Scale -
**
Adjust the slider(s) based on what
*
Index of Refraction
*
 a full white value in the reflectivity map is supposed to map to.

-
**
Shader Params → Layer 1 Optical Depth (mm)/Layer 2 Optical Depth (mm) -
**
Use the slider(s) to adjust the effective thickness of the layer(s), that is the thickness (in millimeter) multiplied by the attenuation coefficient. The optical depth is modulated by the alpha channel of the layer's diffuse texture.

-
**
Shader Params → Layer 1 Smoothness/Layer 2 Smoothness -
**
Use the slider(s) to adjust the smoothness value of a layer that is modulated by the smoothness map.

##
Thin-film Layer

Use the following options to set up a thin-film layer for the object:

-
**
Shader Generation Params → Thin-film -
**
Click the checkbox to display the thin-film related options.

-
**
Texture Maps → Thin-film Reflectivity Map -
**
Assign a texture that will control the
*
Index of Refraction
*
of the thin-film. Optional alpha channel modulates the thickness of the thin-film.

-
**
Texture Maps → Thin-film Reflectivity Scale -
**
Adjust the slider to specify what
*
Index of Refraction
*
a fully white value in the reflectivity map maps to.

-
**
Shader Params → Thin-film Thickness(nanometre) -
**
Set this option  to a value based on which the thickness of the thin-film in nanometers will be defined.

##
Meaning of Reflectivity

The reflectivity of a medium is directly tied to its

*
I
*
*
ndex of Refraction (IOR)
*
. The IOR is an optical property of a medium that relates to the phase velocity of light in that medium. Higher IOR values indicate a slower medium with a higher impedance, which results in less light penetrating the surface and more light reflecting off of it. Air has an IOR of just over 1. Water is about 1.33, and most dielectrics will have an IOR of around 1.2-1.6. Thin-films of oil, paint, etc. exhibit similar ranges of values; however, the films of metallic oxide generally have a higher IOR of >2.2.

We remap the IOR,

![Image](https://www.cryengine.com/docs/static/attachments/44960944)
, to a more intuitive reflectivity control via the invertible function:

![Image](https://www.cryengine.com/docs/static/attachments/44960942)

##
Artist Control of a Conductor

For an artist-friendly control of the complex
*
Index of Refraction
*
, we use the remapping to reflectivity and edge-tint controls. Given a complex IOR:
![Image](https://www.cryengine.com/docs/static/attachments/44960946)
, our new control parameters, the reflectivity (r) at normal incidence and the edge-tint (g) can be extracted via the following equations:

![Image](https://www.cryengine.com/docs/static/attachments/44960943)

Those two functions define a bijection between the IOR,

![Image](https://www.cryengine.com/docs/static/attachments/44960944)
, and the artist controls, r and g, therefore the complex IOR can be uniquely recovered from

![Image](https://www.cryengine.com/docs/static/attachments/44960945)
.

As the IOR can vary strongly with wavelength we use an IOR per-channel for conductors (that is, a reflectivity and edge-tint value pair for each RGB channel). Therefore, to control the visual response of a conductor in an artist friendly fashion, we use RGB reflectivity and edge-tint textures.

When attempting to reproduce the appearance of real materials,

online IOR databases

can be consulted and the equations above can be used to convert the IOR to the corresponding reflectivity and edge-tint values. It is also highly advisable to use higher precision textures for conductor's reflectivity and edge-tint.

##
Examples of Conductor Values (RGB Triplets for Each Value)

![Image](https://www.cryengine.com/docs/static/attachments/44961594)

![Image](https://www.cryengine.com/docs/static/attachments/44961595)

![Image](https://www.cryengine.com/docs/static/attachments/44961596)

[Multi-layered Materials](#multi-layered-materials)
[Thin-film and the Thin-film Interference](#thin-film-and-the-thin-film-interference)
[Setting Up Layers](#setting-up-layers)
[Meaning of Reflectivity](#meaning-of-reflectivity)
