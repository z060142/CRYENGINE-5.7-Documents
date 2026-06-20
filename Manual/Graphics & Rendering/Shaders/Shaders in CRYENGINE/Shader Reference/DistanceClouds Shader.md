# DistanceClouds Shader

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/29448860
- Page ID: 29448860
- Breadcrumb: Graphics & Rendering > Shaders > Shaders in CRYENGINE > Shader Reference > DistanceClouds Shader
- Parent: Shader Reference

## Content

##
Shader Parameters

Distance clouds expose the following shader parameters via the
*
Shader Params
*
 section inside the Material editor to adjust their appearance.

Parameter

 |
Description

 |

**
Alpha Saturation
**

 |
Controls the alpha saturation of clouds when blending them with the sky. High values will make less opaque parts of the cloud texture fade out more.

Allows reusing the same texture for slightly different looking clouds by defining several materials with custom Alpha Saturation values.

 |

**
Attenuation
**

 |
Controls how strongly sun light is attenuated when traveling through the distance cloud. Light attenuation is computed per pixel.

It is used to blend between current sun color and sky color. Use higher attenuation values to accentuate cloud self-shadowing (e.g. strong cloud layers).

 |

**
Sky Color Multiplier
**

 |
A value multiplied to the sky color defined for the current by time of day. The result will be used in the pixel shader to blend between sun and sky color using the computed light attenuation value.

 |

**
Step Size
**

 |
Controls how fast to step through the cloud texture (density) to compute per pixel light attenuation.

This effectively controls the appearance of the gradient. The higher the value the smoother and less abrupt the gradient will be.

Higher values can easily produce aliasing artifactsastime of day changes (i.e. tangent space direction vectortosun). This will result in sudden, unnaturally looking gradient changes over time.

 |

**
Sun Color Multiplier
**

 |
A value multiplied to the sun color defined for the currentbytimeofday. The result will be used in the pixel shader to blend between sun and sky color using the computed light attenuation value.

 |

##
Simple Distance Clouds

Simple Distance Clouds allows you to use distance clouds with no volumetric shading computations.

Shader Param

 |
Description

 |

**
Exposure
**

 |
Exposure amount to enable HDR on LDR cloud texture.

 |

**
Opacity
**

 |
Opacity modifier for the cloud.

 |

##
Advanced Distance Clouds

Advanced Distance Clouds allows you to use distance clouds with more accurate shading computations.

Shader Param

 |
Description

 |

**
Alpha Multiplier
**

 |
Alpha multiplier for cloud texture.

 |

**
Alpha Saturation
**

 |
Alpha saturation of cloud texture.

 |

**
Cloud Height
**

 |
Height of the cloud layer.

 |

**
Density Sky
**

 |
Cloud density used for sky light scattering.

 |

**
Density Sun
**

 |
Cloud density used for sun light scattering.

 |

##
Shader Generation Parameters

The following options are available in the Shader Generation Parameters:

Parameter
 |
Description
 |

**
Simple distance clouds
**
 |
Enables the use of distance clouds with no volumetric shading computations.
 |

**
Advanced distance clouds
**
 |
Enables the use of distance clouds with more accurate shading computations.
 |

##
Examples

[Image: /docs/static/attachments/35397782]

 |
[Image: /docs/static/attachments/35397783]

 |
[Image: /docs/static/attachments/35397784]

 |

Alpha saturation 1.5

 |
Alpha saturation 2

 |
Alpha saturation 4

 |

[Image: /docs/static/attachments/35397785]

 |
[Image: /docs/static/attachments/35397786]

 |
[Image: /docs/static/attachments/35397787]

 |

Attenuation 0.2

 |
Attenuation 0.4

 |
Attenuation 0.6

 |

[Image: /docs/static/attachments/35397788]

 |
[Image: /docs/static/attachments/35397789]

 |
[Image: /docs/static/attachments/35397790]

 |

StepSize 0.005

 |
StepSize 0.0075

 |
StepSize 0.01

 |

[#shader-parameters](
Shader Parameters
)
[#simple-distance-clouds](
Simple Distance Clouds
)
[#advanced-distance-clouds](
Advanced Distance Clouds
)
[#shader-generation-parameters](
Shader Generation Parameters
)
[#examples](
Examples
)
