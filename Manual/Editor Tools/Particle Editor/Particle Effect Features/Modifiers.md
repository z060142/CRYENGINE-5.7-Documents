# Modifiers

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/36868151
- Page ID: 36868151
- Breadcrumb: Editor Tools > Particle Editor > Particle Effect Features > Modifiers
- Parent: Particle Effect Features

## Child Pages

- [Color Modifiers](Modifiers/Color%20Modifiers.md)
- [Effectors](Modifiers/Effectors.md)

## Content

##
Overview

Although particle effects provide a wide range of Feature implementations that can be used to make all kinds of effects, their true power is only achieved when Modifiers are used to dynamically alter the effect behavior.

Many properties implemented by particle effect Features can contain a stack of Modifiers.

Each Modifier takes that property value and then manipulates it in a specific way and sends the modified value to the next element in the stack. Some of these combine the output value of the previous Modifier with their own input by multiplying them.
*
![Image](https://www.cryengine.com/docs/static/attachments/44107843)

*
Modifiers menu options
*
*

On this page, some of the Modifiers are marked as
**
function-based
**
. These Modifiers have an additional set of properties called
**
Domains
**
. When enabled, these domains can display additional fields, depending on the Modifier itself and the domain type. For more information about the Function-based Modifiers and domains, please refer to the
[Function-based Modifiers Common Settings](Modifiers.md#Modifiers-FBMCS)
 section below.

##
Modifiers

Modifiers can be assigned to many properties in the Inspector panel. To access the Modifiers list, click the
![Image](https://www.cryengine.com/docs/static/attachments/65438081)
 dropdown button found next to a property that supports Modifiers. When assigned, each Modifier manipulates the corresponding value in a specific way.

Depending on the property in question and the settings of the Modifier, its logic can be applied on each Component. For example,
each Modifier logic can be used on a newly spawned particle or each particle in every frame.

##
Attribute

With this option, users can modify the original property based on an effect's Attribute.

This Modifier is an alternative way of using Attributes. Another way would be to use
[Linear (Function-based Modifier)](Modifiers.md#Modifiers-linear)
 with source option set to Attribute.

Property

 |
Description

 |

**
Attribute Name
**

 |
Defines the name of the Attribute to read from. If the attribute does not exist in this emitter, the
[Domain](Modifiers.md#Modifiers-domain)
input will get a value of
**
1
**
 instead.

 |

**
Scale and Bias
**

 |
Allows the Attribute to be scaled and biased. Usually useful when the input is not in the 0 to 1 range.

 |

**
Spawn Only
**

 |
Specifies if the attribute is to be applied only when a particle is first born or if it should always affect all living particles.

 |

##
Config Spec

This option allows users to modify the original property based on the platform type or the particle quality settings. The best outcome can be achieved when it is used to scale other feature properties higher or lower for performance scalability.

Property

 |
Description

 |

**
Low
**

 |
Scale value used when on Low Spec PC.

 |

**
Medium
**

 |
Scale value used when on Medium Spec PC.

 |

**
High
**

 |
Scale value used when on High Spec PC.

 |

**
Very High
**

 |
Scale value used when on Very High Spec PC.

 |

**
XBox One
**

 |
Scale value used when on XBox One.

 |

**
XBox One X
**

 |
Scale value used when on XBox One X.

 |

**
PlayStation 4
**

 |
Scale value used when on PlayStation 4.

 |

**
PlayStation 4 Pro
**
 |
Scale value used when on PlayStation 4 Pro.
 |

##
Linear (Function-based Modifier)

This option allows users to combine properties that are modified with a Domain; however, it doesn't apply any additional modification. In this Modifier, only the function-based properties are used. Please refer to
[Function-based Modifiers Common Settings](Modifiers.md#Modifiers-FBMCS)
 for more information.

Property
 |
Description
 |

**
Owner
**
 |
See
[below](Modifiers.md#Modifiers-owner)
.
 |

**
Domain Scale
**
 |
See
[below](Modifiers.md#Modifiers-dsdb)
.
 |

**
Domain Bias
**
 |
See
[below](Modifiers.md#Modifiers-dsdb)
.
 |

##
Noise (Function-based Modifier)

Uses a potential field based on Perlin noise to randomize the input property.

Unlike the
**
Random
**
 Modifier, which tends to get fuzzy or diffuse, the
**
Noise
**
 Modifier adds smooth variations to the particles.
Property

 |
Description

 |

**
Owner
**

 |
See
[below](Modifiers.md#Modifiers-owner)
.

 |

**
Domain Scale
**
 |
See
[below](Modifiers.md#Modifiers-dsdb)
.
 |

**
Domain Bias
**
 |
See
[below](Modifiers.md#Modifiers-dsdb)
.
 |

**
Mode
**

 |
Defines the noise mode:

Option
 |
Description
 |

**
Smooth
**
 |
Simple Perlin Noise field.
 |

**
Fractal
**
 |
Adds additional roughness to the Perlin noise field.
 |

**
Pulse
**
 |
Uses the noise field to pulse between 0 and 1. Useful to add flickering effects.
 |

 |

**
Amount
**

 |
Indicates the amount of variation that will be added to the particle. If the amount is greater than
**
1
**
, then it can provide a positive and a negative variation at the same time.

 |

**
Pulse Width
**

 |
Given value specifies the balance between the frequency of pulse being turned on or off. For example, a value of
**
0.5
**
 allows the pulse to be turned on and off in an even frequency; values greater than
**
 0.5
**
 result in the pulse being turned off more often than it's turned on.

Only available when
**
Mode
**
 is set to
**
Pulse
**
.
 |

Use
**
Domain Scale
**
 and
**
Domain Bias
**
 to change the frequency and phase of noise. However, if the
**
Domain Scale
**
 value is too high, Noise starts to behave closer to pure randomness and fuzziness; as a result, diffuse might start to arise.

![Image](https://www.cryengine.com/docs/static/attachments/44107844)

 |
![Image](https://www.cryengine.com/docs/static/attachments/44107845)

 |
![Image](https://www.cryengine.com/docs/static/attachments/44107846)

 |

Smooth

 |
Fractal

 |
Pulse

 |

*
Sample of Noise modes for a particle
*

##
Wave (Function-based Modifier)

This Modifier is used to provide different types of periodic values. Its options are based on trigonometric mathematics and are useful to add regular behaviors as opposed to variance.

Properties

 |
Description

 |

**
Owner
**
 |
See
[below](Modifiers.md#Modifiers-owner)
.
 |

**
Domain Scale
**
 |
See
[below](Modifiers.md#Modifiers-dsdb)
.
 |

**
Domain Bias
**
 |
See
[below](Modifiers.md#Modifiers-dsdb)
.
 |

**
Wave
**

 |
Defines the noise modes (see below for examples):

-
**
Sin
**
**

**

-
**
Saw
**
**

**

-
**
Pulse
**
 |

**
Amplitude, Bias
**

 |
Lets users add the waveform settings.

 |

**
Inverse
**

 |
When enabled, this option inverts the waveform.

 |

Use
**
Domain Scale
**
 and
**
Domain
**

**
Bias
**
 to change the frequency and phase of a wave.

Cosine is the same as Sine with a 0.25 phase.

![Image](https://www.cryengine.com/docs/static/attachments/44107847)

 |
![Image](https://www.cryengine.com/docs/static/attachments/44107848)

 |
![Image](https://www.cryengine.com/docs/static/attachments/44107849)

 |

Sin

 |
Saw

 |
Pulse

 |

*
Wave equations samples
*

![Image](https://www.cryengine.com/docs/static/attachments/44107850)

*
A waveform setting sample
*

##
Random

Provides a fast way to add simple variations to the particle behavior.

This Modifier can only affect newly spawned particles.
Properties

 |
Description

 |

**
Amount
**

 |
Specifies the amount of variation that will be added to the particle. If the amount is greater than 1, it can provide positive and negative variations at the same time.

 |

##
Double Curve (Function-based Modifier)

Unlike Curve, the Double Curve Modifier uses two Bezier curves, in this Modifier, the
[Domain](Modifiers.md#Modifiers-domain)
is used to sample both curves at the same time, while the
**
Random
**
 field of the particle is used to interpolate between the lower and the upper Bezier curves.

This is useful in providing additional variance to the particle behavior.

Properties

 |
Description

 |

**
Owner
**
 |
See
[below](Modifiers.md#Modifiers-owner)
.
 |

**
Domain Scale
**
 |
See
[below](Modifiers.md#Modifiers-dsdb)
.
 |

**
Domain Bias
**
 |
See
[below](Modifiers.md#Modifiers-dsdb)
.
 |

**
Double Curve
**

 |
Uses a double Bezier curve to provide additional variance. See
[Particle Editor](../../Particle%20Editor.md)
 for more information about Curve Editor.

 |

##
Curve (Function-based Modifier)

Uses the domain input to sample a Bezier curve. In particles, Bezier curves have an unlimited number of points; however, each point has to be in the range from
**
0
**
 to
**
1
**
 on the X axis and there are no enforced limits on the Y axis. For performance reasons, Bezier points support slopes, but not the slope weight.

Properties

 |
Description

 |

**
Owner
**
 |
See
[below](Modifiers.md#Modifiers-owner)
.
 |

**
Domain Scale
**
 |
See
[below](Modifiers.md#Modifiers-dsdb)
.
 |

**
Domain Bias
**
 |
See
[below](Modifiers.md#Modifiers-dsdb)
.
 |

**
Curve
**

 |
Uses a single curve to modify the values. See
[Particle Editor](../../Particle%20Editor.md)
 for more information about Curve Editor.

 |

##
Inherit

This option allows child particles to inherit their parent's
**
Field
**
 output.

Property
 |
Description
 |

**
Spawn Only
**

 |
When a particle is born, it inherits the parent component's
**
Field
**
 output.

 |

##
Function-based Modifiers Common Settings

![Image](https://www.cryengine.com/docs/static/attachments/44107852)

Many of the Particle Effect Modifiers are function-based. This allows the Modifier to accept not only the input from the property value modified by previous Modifiers, but also other aspects of the particle. All of these Modifiers have a common set of properties.

The easiest way to differentiate a regular Modifier from a function-based Modifier is that in the case of a function-based Modifier, a new dropdown box appears in the user interface allowing users to select the Domain.

Properties

 |
Description

 |

**
Domain
**

 |
Following options are available on the Function-based Modifiers dropdown menu:

-
**
Age -
**
This is the normalized time of the current particle; meaning this value will always be between 0 and 1. When a particle is initially created, Self time starts at 0 and as the particle ages, this value will progressively move toward 1 until the particle dies.

-
**
Spawn Fraction -
**
When particles are spawned using the
[Spawn](Spawn.md)
 feature, a Spawn Fraction field is added to each particle property. The first particle spawned gets order value 0 and the last spawned particle gets order value 1.

-
**
Spawn Id -
**
When this Domain is selected, a new field called Id Modulus appears. Spawn Id specifies how many times a particle is distributed along the domain before wrapping. Just like Spawn Fraction, it generates domain values between 0 and 1, increasing with particle count. The only difference is that Spawn Fraction works
*
only
*
with emitters with a finite particle count and goes from 0 to 1
*
only once
*
, whereas Spawn Id works with finite
*
or
*
infinite particle counts and goes from 0 to 1
*
multiple times
*
, wrapping after Modulus entries.

-
**
Speed -
**
Specifies the speed of the particle in meters per second.

-
**
Field -
**
Particles can have other fields besides Size or Opacity. This mode allows users to select/choose any of the fields for a given particle. For more information about fields, please see Field in the
[Particle Effect Features](../Particle%20Effect%20Features.md)
 section.

-
**
Attribute -
**
Reads the value from any Attributes of the emitter. This is one of the most important Domain options since it allows attributes to actually control different aspects of the effect.

-
**
Level Time -
**
Specifies the time of the current level in seconds.

-
**
View Angle -
**
 This option corresponds to the relative angle to the camera for particles which have 3D angles. For more information about angles, please see the Angles in the
[Particle Effect Features](../Particle%20Effect%20Features.md)
section.

When a particle faces the camera, it emits an output value of 1. When the particle is perfectly flat relative to the camera, then it emits an output value of 0. This option is best used in conjunction with the
**
Field:
**

**
Opacity
**
 feature option to avoid certain types of visual artifacts with free facing particles. For more information about opacity, please see the Field section
**

**
on the
[Particle Effect Features](../Particle%20Effect%20Features.md)
 page.

-
**
Camera Distance -
**
 Specifies the distance of the particle relative to the camera.

-
**
Random -
**
 Will always output a random value between 0 and 1. Can be used to create more sophisticated random variation effects than the Random Modifier.
For immortal particles or properties that are not applied to particles during runtime, those values will always be 0.

 |

**
Attribute Name
**

 |
The name of the attribute to read from. If the attribute does not exist in this emitter, the Domain value will be 1.

Available when
**
Domain
**
is set to
**
Attribute
**
.
 |

**
Field
**

 |
Allows users to select/choose which field to read from. This property is available when
**
Domain
**
is set to
**
Field.
**

-
**
Angle2D -
**
Current particle's rotation angle (see
[Angles](Angles.md)
 for more detail).

-
**
Spin2D -
**
Current particle's spin rate (see
[Angles](Angles.md)
 for more detail).

-
**
Alpha -
**
Specifies particle's
**

**
opacity (see
[Field](Field.md)
 for more detail).

-
**
Collide Speed -
**
Particle's collision data (see
[Motion](Motion.md)
for more detail).

-
**
Size -
**
Specifies particle's
**

**
size in meters (see
[Field](Field.md)
 for more detail).

-
**
Gravity -
**
Specifies particle's
**

**
gravity multiplier (see
[Motion](Motion.md)
 for more detail).

-
**
Drag -
**
Specifies particle's
**

**
drag (see
[Motion](Motion.md)
 for more detail).

-
**
Life Time -
**
Specifies the lifetime of a particle in seconds; set it to 0 for immortal particles (see
[Life](Life.md)
 for more detail).

-
**
Random -
**
Each particle can get a random number from 0 to 1. Use this to add variance to the behavior of each particle.
There is a difference between the
**
Random
**
Domain, and the
**
Random
**
property which is available if the
**
Field
**
Domain is selected. The Random Domain will always output a different number and is fully stochastic. Field Random, on other hand, corresponds to a particle's own random number and can be used to have consistent behavior between Modifiers. This can be used for example to have varying but consistent size and opacity or to have all children particles share the same randomness as their parent.

![Image](https://www.cryengine.com/docs/static/attachments/65438083)

*
Domain Field menu options
*

 |

**
Owner
**

 |
Specifies from where the Domain or the Field option should be taken from:

-
**
Self -
**
 Takes the necessary information from the particle itself.

-
**
Parent -
**
 Takes the necessary information from the parent particle.
When the owner is a parent, but the particle's parent is already dead, the Domain value will always be
**
1
**
. The exception to this rule is the
**
Speed
**
 feature, which will be set to
**
0
**
 instead.

 |

**
Domain Scale and Domain Bias
**

 |
Allows the Domain input to be scaled and biased. Usually useful when the input might not be in the 0 to 1 range, such as Speed or Attribute.

 |

**
Spawn Only
**

 |
In some cases it is desirable to choose if the Modifier is to be applied for every particle every frame or if the Modifier should only be applied once when the particle is born.

 |

##
GPU Support

Currently, Modifiers have a very limited support in the current GPU pipeline. At the moment, the only Modifier that can be used is the
**
Curve
**
 Modifier, and it can only be used when
[Owner](Modifiers.md#Modifiers-owner)
is set to
**
 Self
**
.

[Modifiers](#modifiers)
[Function-based Modifiers Common Settings](#function-based-modifiers-common-settings)
[GPU Support](#gpu-support)
