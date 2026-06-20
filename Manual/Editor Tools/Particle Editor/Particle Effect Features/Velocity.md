# Velocity

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/36868166
- Page ID: 36868166
- Breadcrumb: Editor Tools > Particle Editor > Particle Effect Features > Velocity
- Parent: Particle Effect Features

## Content

##
Overview

Velocity features are used to specify the speed and direction at which the particles should move after they are spawned. By default, new born particles have no motion features attached to them.

A very important aspect to take into account is that these features can be combined with each other. So, using the right type of combinations allow users to create striking and advanced effects.

Particles will only move if at least one type of Motion feature is present, For more information, please refer to
[Motion](Motion.md)
.

The following options are available under the Velocity category:

##
Compass

Spawns particles in a direction specified by the degrees on a compass. The horizon is the plane defined by the parent's X and Y axes, while up is defined by the parent's Z axis.

Property

 |
Description

 |

**
Azimuth
**

 |
Used to specify the horizontal angle, in degrees and relative to South.

 |

**
Angle
**

 |
Used to specify the vertical angle, in degrees. A value of 0 corresponds straight up, 90 is towards the horizon, and 180 straight down.

 |

**
Velocity
**

 |
Used to specify initial scalar velocity in meters per second.

 |

##
Cone

This feature enables particles to shoot upwards in a cone shape.

Properties

 |
Description

 |

**
Axis
**

 |
Specifies the direction relative to the parent particle or emitter along which the particles should be moved.

 |

**
Angle
**

 |
Allows users to specify the aperture angle of the cone. Without modifiers, particles are only shot through the skin of the cone. Use the Random option under the
[Modifiers](Modifiers.md)
 section
**

**
to ensure that the particles are shot uniformly within the cone.

 |

**
Inner Fraction
**

 |
Sets the inner radius of distribution on circles. This is an easier and more precise way to distribute particles within the radius than adding a Random modifier to the radius parameter.

 |

**
Velocity
**

 |
Specifies the base velocity at which the particles will be moved.

 |

**
Distribution
**

 |
Particles are distributed to different dimensions based on the selected parameter:

-
**
Random -
**
Particles are distributed to randomly selected dimensions.

-
**
Ordered -
**
 When selected, one Modulus field appears for each dimension available for distribution. To distribute particles along these dimensions, each of these fields must be set to a value greater than 1.
 |

##
Directional

This feature allows the particles to move on a given direction in space. While seemingly not a very interesting feature in itself, combining it with multiple features and using Modifiers on the scale parameter probably make this probably one of the most powerful parameters in the Velocity feature. In fact, most of the Velocity features on this page could in theory be recreated by using this feature, albeit not in a very practical way.

Property

 |
Description

 |

**
Velocity
**

 |
Specifies the velocity and direction in meters per second.

 |

**
Scale
**

 |
Scales the velocity vector. Can be used with
[Modifiers](Modifiers.md)
 to dynamically change the particle's velocity.

 |

##
Inherit

This feature adds parent particles or an emitter's velocity to a new particle, For more information on parent-child relationships, see
[SecondGen](SecondGen.md)
.

Properties

 |
Description

 |

**
Scale
**

 |
Specifies the value of parent's velocity and which values should be inherited by the new particle. A value of 1 will add the entire parent's velocity, while a value of 0 will effectively disable this feature.

This value is not limited. It can be above one, meaning it will inherit more velocity than the velocity of the actual parent. It can also be negative and thus will invert the parent's velocity. This can be useful to simulate effects such as rocket trails.

 |

##
OmniDirectional

This feature moves the new particles randomly, but uniformly in every direction.

Properties

 |
Description

 |

**
Velocity
**

 |
Specifies the speed of new particles.

 |

**
Distribution
**

 |
Particles are distributed to different dimensions based on the selected parameter:

-
**
Random -
**
Particles are distributed to randomly selected dimensions.

-
**
Ordered -
**
 When selected, one Modulus field appears for each dimension available for distribution. To distribute particles along these dimensions, each of these fields must be set to a value greater than 1.
 |

##
GPU Support

All velocity features, except
**
MoveRelativeToEmitter
**
, are supported on the GPU and initialization is fully achieved on the GPU side. Properties do not support modifiers on the GPU.

[Compass](#compass)
[Cone](#cone)
[Directional](#directional)
[Inherit](#inherit)
[OmniDirectional](#omnidirectional)
[GPU Support](#gpu-support)
