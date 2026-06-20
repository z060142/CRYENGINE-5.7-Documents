# Field

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/36868265
- Page ID: 36868265
- Breadcrumb: Editor Tools > Particle Editor > Particle Effect Features > Field
- Parent: Particle Effect Features

## Content

##
Overview

Field is one of the most important particle effect features. It represents different aspects of how each individual particle should look like and the type of internal data each particle should have. This can be used to create a quite sophisticated effect logic. With this feature, users can define the color of the particle material, adjust the opacity level and control the size of the particles.

Fields are specifically designed to interact with Modifiers. For more information, please refer to
[Modifiers](Modifiers.md)
.

##
Color

The color feature specifies the tone that will be assigned to the particles. The color acts as a filter on top of the diffuse texture and particle lighting. Black color will make particles look completely black, even when the emissive values are specified, while white color will effectively remove the filter.

Since color acts as a filter and not the albedo itself, using white color is still physically correct, since the settings from the feature Appearance: Lighting will still apply. However, black or very dark colors are not recommended since perfect filters do not appear in nature. Please refer to
[Appearance](Appearance.md)
 for more information.

Property

 |
Description

 |

**
Color
**

 |
Defines the base color of the particles.

 |

##
PixelSize

This feature directly manipulates both size and opacity fields. It prevents a particle from getting too large or too small. When a particle size starts to get smaller than a certain number of pixels on the screen, its size is maintained while its opacity gets reduced. This is a very useful feature when effects have multiple small particles and start to flicker as they move around as it will trade sharpness for flickering.

Property

 |
Description

 |

**
Minimum Pixel Size
**

 |
Minimum size in pixels that a particle can have on the screen. If a particle is smaller than this value, then it gets augmented.

 |

**
Maximum Pixel Size
**

 |
Maximum size in pixels that a particle can have on the screen. If a particle is larger than this value, then it gets diminished.

 |

**
Affect Opacity
**

 |
When enabled, if a particle gets smaller than the set minimum pixel size, the particle size is not just clamped to that value, but its opacity is also reduced. It is recommended to have this option always enabled, otherwise particles will break the laws of conservation of energy and the particles which are far away will be brighter than they are supposed to be.

 |

##
Size

Size specifies how large a particle should look like. If a particle is to be interpreted as a spherical object, size will correspond to its radius and not its diameter. This field can have any value as long it is positive. Zero or negative particle sizes prevents the particle to be rendered by CRYENGINE.

Property

 |
Description

 |

**
Value
**

 |
Base value of particle size before being modified.

 |

##
GPU Support

All Fields features are supported in the GPU pipeline, although there is only limited support for modifiers in properties. Currently, only the Color, Size and Opacity can be modified using the Curve modifier with Self Time as the source.

[Color](#color)
[PixelSize](#pixelsize)
[Size](#size)
[GPU Support](#gpu-support)
