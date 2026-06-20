# Effectors

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/36869033
- Page ID: 36869033
- Breadcrumb: Editor Tools > Particle Editor > Particle Effect Features > Modifiers > Effectors
- Parent: Modifiers

## Content

##
Overview

Effectors are a special type of Modifiers which are used by
**
Motion: Physics
**
 feature. They apply non-uniform forces to particles and are used to add flair to an otherwise standard physical motion.

For more information about particle physics, refer to the
[Motion](../Motion.md)
 section.

Effectors can be found under
**
Local Effectors
**
 dropdown menu and it includes the following options:

Modifiers and Effectors can be combined to create highly sophisticated effects.

![Image](https://www.cryengine.com/docs/static/attachments/44107871)

##
Turbulence

Turbulence simulates the motion of particles within a participating medium like air or water. Although participating mediums might be invisible in games, simulating their turbulence allows for the creation of complex and convincing effects

This effector creates the impression that particles are floating in a medium rather than appearing to be in a vacuum. The Turbulence Effector is applied in world space and does not depend on parent location.

For more information about parent child relationships, see
[SecondGen](../SecondGen.md)
.

Properties

 |
Description

 |

**
Mode
**

 |
Specifies the type of turbulence to be simulated:

-
**
Brownian -
**
 Simulates the effect of micro-collisions between the microscopic particles of the participating medium with the macroscopic particles of the component. Useful to create particle diffusion.

-
**
Simplex and Simplex Curl -
**
 Uses Simplex Noise to generate a velocity field for the particles to follow. This simulates turbulent wind effects. Curl is a special application of Simplex, it makes the participating medium non-compressible. With regular Simplex (also called Potential Simplex Field), it can be possible to see that particles move away from cold spots and fall into sink points. With Curl (also called Curl Simplex Field or simply Curl Noise), no cold spots or sync points are visible and particles will always flow naturally through space.
Simplex and Simplex Curl only works if
**
Drag
**
 is set to
**
a value other than 0
**
. The higher the drag force, then the faster particles snap into the simplex field.

Curl has a slightly higher cost than Simplex. However, both are significantly more costly than Brownian.

 |

**
Speed
**

 |
Specifies how fast the turbulence is applied to the particles. The actual behavior will depend on the Mode.

 |

**
Size
**

 |
Only used by Simplex or Simplex Curl. Turbulence uses Simplex noise to generate a vector field, which is similar to Perlin noise, but can be more efficient in some cases. This type of noise creates a uniform grid of vertices in space and sets a random value to each vertex. The actual velocity applied to the particle is interpolated from this grid. Size therefore specifies the distance between these vertices in this grid. If size is too small, turbulence will start to get more random, fuzzy and diffuse. If size is too large, particles will start moving mostly in the same direction and no interesting shapes will arise.

 |

**
Rate
**

 |
Only used by Simplex or Simplex Curl. One of the main advantages of Simplex noise is that it is relatively efficient to not just generate a smooth noise in space, but those that can also smoothly evolve over time. Rate controls how fast this evolution occurs. A value of 0 means no evolution and particles will always travel over the same routes.

 |

**
Octaves
**

 |
Only used by Simplex or Simplex Curl. Adds additional complexity by sampling the noise field multiple times with different sizes. This option enables the creation of Fractal Noise.

Octaves correspond to the number of times the noise field gets sampled - this can be fairly expensive.

 |

**
Scale
**

 |
Allows non-uniform scaling of the turbulence.

 |

##
Gravity

Gravity applies a gravitational force to all particles relative to a point in space. While global gravity is a uniform force, this option is non-uniform.

**
Gravity
**
does not require
**
Drag
**
 and it only affects the acceleration. In fact, higher amounts of drag will reduce the gravity effect. Also, Gravity's
**
Scale
**
 does not scale this effect, it is only scaled by global gravity.

Properties
 |
Description
 |

**
Target
**

 |
Specifies the source of gravity for each particle:

-
**
Self -
**
Uses the particle as the sources of the gravity field.

-
**
Parent -
**
Uses parent's particle (or emitter) as the source of the gravity field. For more information on parent child relationships, see
[SecondGen](../SecondGen.md)
**
.
**

-
**
Target -
**
 Particle emitter's target position (usually another game entity) as a source. For more information on targeting, see
[Key Concepts](../../../../Graphics%20%26%20Rendering/Particles/Key%20Concepts.md)
 about Targets.
 |

**
Target Offset
**

 |
Offsets source of the gravity field in space.

 |

**
Type
**

 |
Shapes the gravity field:

-
**
Spherical -
**
 Provides regular gravity field shape. Target is a point in space.

-
**
Cylindrical -
**
 Provides gravity field in the shape of a cylinder. Target then specifies an axis in space.
 |

**
Acceleration
**

 |
Maximum amount of acceleration to be applied to the particles in meters per second squared (m/s
2
). If this value is negative, particles are rejected instead of being attracted to the target.

 |

**
Decay
**

 |
Acceleration is not uniformly applied to all particles, it decays with the distance to the target. Decay corresponds to the distance, in meters, at which acceleration is halved.

Decay follows the inverse squared law. This is not physically accurate, but prevents a singularity at the target position and guaranties that the Acceleration property is the maximum acceleration possible. As a consequence it is not possible to create proper orbits.

 |

**
Axis
**

 |
Valid only when Cylindrical type is selected. Specifies the direction of the axis in the parent's space.

 |

##
Vortex

Vortex simulates the effect of turbulent wind.

The Vortex Effector affects wind velocity and requires the
**
Drag
**
 option. The higher the drag value, the faster the particles snap to the vortex.

Properties

 |
Description

 |

**
Target
**

 |
Specifies where the center of the vortex should appear:

-
**
Self -
**
Uses the particle as the center of the vortex.

-
**
Parent -
**
Uses particle's parent or its emitter as the center of the vortex. For more information on parent child relationships, please refer to the
[SecondGen](../SecondGen.md)
 page.

-
**
Target -
**
 Defines the emitter's target position, which is usually another game entity, as a source. Please refer to
[Key Concepts](../../../../Graphics%20%26%20Rendering/Particles/Key%20Concepts.md)
 to learn more about
**
Targets
**
.
 |

**
Target Offset
**

 |
Offsets the center of the vortex in space.

 |

**
Speed
**

 |
Maximum speed of the wind formed by the vortex. The speed value is calculated in meters per second.

 |

**
Decay
**

 |
Wind velocity is not uniformly applied to all particles, it decays with the distance to the target. Decay corresponds to the distance, in meters, at which the acceleration is reduced by half. Decay follows the inverse squared law.

 |

**
Direction
**

 |
Direction the wind should flow;  clockwise or counterclockwise.

 |

**
Axis
**

 |
Specified direction of the vortex axis in parent's space.

 |

##
Spiral

Makes particles move in a spiral motion based on their velocity. Can be used to create certain special types of turbulence motion effects.

Property

 |
Description

 |

**
Size
**

 |
Specifies the size for the spiral.

 |

**
Speed
**

 |
Specifies the velocity for the particles around the spiral.

 |

##
GPU Support

All Effectors are supported by the GPU pipeline. There are some limitations to be taken into account though, this is due to the way the GPU system processes particles;

-
There can only be one Effector of each type active at the same time

-
The order in which the Effectors are stacked and executed is always:

-
Brownian - Turbulence

-
Simplex - Turbulence

-
Simplex Curl - Turbulence

-
Gravity

-
Vortex
[Turbulence](#turbulence)
[Gravity](#gravity)
[Vortex](#vortex)
[Spiral](#spiral)
[GPU Support](#gpu-support)
