# Particles Shader

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/29449087
- Page ID: 29449087
- Breadcrumb: Graphics & Rendering > Shaders > Shaders in CRYENGINE > Shader Reference > Particles Shader
- Parent: Shader Reference

## Content

##
Overview

The Particles Shader is used by FX artists to create particle materials.

##
Shader Params

It consists of the following parameters:

Parameter
 |
Description
 |

**
Color Lookup Amplitude
**
 |
Sets the color lookup brightness and multiplier. This parameter requires that
**
Color Lookup
**
 is enabled in the

**
Shader Generation Parameter
**
 is enabled.
 |

**
Color Lookup Color Phase
**
 |
Sets the per-color phase to be used.
This parameter requires that
**
Color Lookup
**
 is enabled in the

**
Shader Generation Parameters
**
 is enabled.
 |

**
Deform Amount
**
 |
Controls deformation multiplier.
This parameter requires that
**
Deformation
**
is enabled in the

**
Shader Generation Parameters
**
.
 |

**
Deform Anim Speed
**
 |
Controls deformation animation translation speed and frequency.
This parameter requires that
**
Deformation
**
 is enabled in the

**
Shader Generation Parameters
**
.
 |

**
Deform Tiling
**
 |
Controls deformation tiling.
This parameter requires that
**
Deformation
**
 is enabled in the

**
Shader Generation Parameters
**
.
 |

**
Global Illumination Amount
**
 |
Sets the amount of global illumination.
 |

**
Perturbation Amount
**
 |
Controls the amount of deformation that is used.
This parameter requires that
**
Screen Space
**
 is enabled in the

**
Shader Generation Parameters
**
.
 |

**
Perturbation Anim Speed
**
 |
Controls animation translation speed and frequency that is applied to the deformation map.
This parameter requires that
**
Screen Space
**
 is enabled in the

**
Shader Generation Parameters
**
.
 |

**
Perturbation Tiling
**
 |
Controls the tiling amount of deformation.
This parameter requires that
**
Screen Space
**
 is enabled in the

**
Shader Generation Parameters
**
.
 |

**
Refraction Bump Scale
**
 |
Sets the refraction bump scale.
This parameter requires that
**
Refraction
**
 is enabled in the

**
Shader Generation Parameters
**
.
 |

**
Threshold for Writing Depth
**
 |
Sets the threshold for writing depth.
This parameter requires that
**
Depth Fixup
**
 is enabled in the

**
Shader Generation Parameters
**
.
 |

##
Shader Generation Params

The Particle Shader comprises of the following Shader Generation Parameters:

##
Refraction

Refraction enables particle refraction, which is useful to simulate heat haze coming from fire or any heat source or for some specific visual effect look. This increases the rendering cost slightly, so it should be used sparingly. When the refraction option is used, users should ensure that they are using a normal map also for deformation.

Shader Param
 |
Description
 |

**
Refraction Bump Scale
**
 |
When the
**
Refraction
**
option is enabled, users can use this scale for controlling the amount of deformation on refractions.
 |

##
Screen Space Deformation

**
Screen Space Deformation (SSD)
**
 deforms particles in screen space (screen aligned deformation). When
**
Screen Space Deformation
**
 is used, set the normal map to be used as deformation map in the
**
Custom
**
 slot.

Shader Param
 |
Description
 |

**
Perturbation Anim Speed
**
 |
This parameter is used for SSD, it controls animation translation speed/frequency applied to the deformation map.
 |

**
Perturbation Tilling
**
 |
Another parameter used for SSD, for controlling the tilling amount of deformation.
 |

**
Perturbation Amount
**
 |
Used for SSD, this multiplier controls the amount of deformation used.
 |

##
Deformation

**
Deformation,
**
 unlike SSD, where deformation is done screen aligned, this type of deformation is done in the particle UV space. When deformation option is used, set normal map to be used as deformation map in the
**
Custom
**
 slot.

Shader Param
 |
Description
 |

**
Deform Tilling
**
 |
Controls deformation tilling.
 |

**
Deform Amount
**
 |
Controls deformation multiplier.
 |

**
Deform Anim Speed
**
 |
Controls deformation animation translation speed/frequency.
 |

##
Color Lookup

**
Color Lookup
**
 allows users to use a color lookup texture to have color gradient variation for the same particle effect. This is useful in particular to save video memory as users can, for example, have a grayscale diffuse map and use color lookup texture to get colors. When a color lookup is used, set the lookup gradient texture in the
**
Custom Slot 1
**
.

Shader Param
 |
Description
 |

**
Color Lookup Amplitude
**
 |
Sets color look up amplitude/multiplier (how bright it will look).
 |

**
Color Lookup Color Phase
**
 |
sets the per-pixel (therefore per-color) phase to be used. Users can use this parameter to set a different range of colors coming from the gradient texture lookup.
 |

##
Specular Lighting

Enables the calculation of specular lighting in addition to diffuse lighting.

##
Depth Fixup

Enables writing depth for depth of field and post processing.

##
Refraction Lightning

Enables the use of a color texture to tint refraction.

[Shader Params](#shader-params)
[Shader Generation Params](#shader-generation-params)
[Refraction](#refraction)
[Screen Space Deformation](#screen-space-deformation)
[Deformation](#deformation)
[Color Lookup](#color-lookup)
[Specular Lighting](#specular-lighting)
[Depth Fixup](#depth-fixup)
[Refraction Lightning](#refraction-lightning)
