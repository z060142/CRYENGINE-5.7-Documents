# GPU Particles

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/36868272
- Page ID: 36868272
- Breadcrumb: Editor Tools > Particle Editor > Particle Effect Features > GPU Particles
- Parent: Particle Effect Features

## Content

##
Overview

This category contains features which are exclusively used with GPU Particles.

The GPU based particle pipeline implements a subset of the CPU particle functionality while offering much higher speed for massive particle effects such as fluid like effects and fractal movement.

The following options are available under the GPU Particles category:

CRYENGINE Particle System has been optimized to fully use CPU capacity for both PCs and
Console
s and will execute efficiently in most cases. Particle effect GPU implementation has been specifically optimized to only handle very large amounts of particles and adds a significant amount of overhead if used too often with low amount of particles per runtime. Therefore, it is recommended to only use the GPU Particle feature when necessary.

##
Collision

This feature adds the ability for GPU particles to collide against the render geometry in the depth buffer of the scene. Note that the particles will only collide with the visible geometry.

Property

 |
Description

 |

**
Offset
**

 |
Offsets the depth of visible surface. Makes particles collide either earlier or later relative to the surface on the screen.

 |

**
Radius
**

 |
Approximates the radius of a particle relative to the screen.

 |

**
Restitution
**

 |
Affects the bounciness of a particle - also known as collision elasticity.

A value of 0 means that the particles will stop moving on any collision. A value of 1, on the other hand, will make particles perfectly bounce off the colliding surface.

 |

##
GPU Fluid Dynamics

This is an experimental feature and is only accessible for preview. This feature provides an example for potential future uses of CRYENGINE GPU particle pipeline and the final version might be incompatible with the current implementation.

[Image: /docs/static/attachments/44107820]

*
A sample of GPU Fluid Dynamics effect
*

This feature allows users to add a Smooth Particle Hydrodynamics (SPH) simulation to a component. The simulation will be conducted using fluid particles that are not handled by the Particle System itself. The fluid particles are used to generate and evolve a velocity field, which can be sampled to provide velocities for particles.

When the Engine is started and a GPU Fluid Dynamics feature is available, debug drawing will be activated and the bounds of the acceleration structure, as well as the positions of the SPH simulation particles, will be visualized. Be aware that this will degrade the performance of the simulation.

To deactivate debug drawing and enable maximum performance, use the CVar
**
r_GpuPhysicsFluidDynamicsDebug=0
*
.
*
**

##
Assigning GPU Fluid Dynamics values to an effect

[Image: /docs/static/attachments/44107821]

Properties

 |
Description

 |

**
Initial Velocity
**

 |
Specifies an initial velocity value for the fluid particles when they are spawned.

 |

**
Stiffness
**

 |
Specifies the stiffness when solving the pressure constraint.

 |

**
Gravity Constant
**

 |
Specifies the strength of the gravity force. When set to negative values, it simulates buoyancy.

 |

**
h
**

 |
Specifies the Fluid Particle Influence radius. The SPH particles carry a mass distribution based on a smoothing kernel and this parameter defines the radius of the smoothing kernel.

 |

**
Rest Density
**

 |
Specifies the density value which is used by the pressure solver to satisfy for any given SPH particle.

 |

**
Particle Mass
**

 |
Specifies the total mass that is carried by one SPH particle.

 |

**
Maximum Velocity
**

 |
Specifies the velocity for each SPH particle. The particles are clamped at this value to make the simulation more stable.

 |

**
Maximum Force
**

 |
Specifies the force applied on each SPH particle. The particles are clamped at this value to make the simulation more stable.

 |

**
Atmospheric Drag
**

 |
Specifies the amount of atmospheric drag to be applied to SPH particles which do not have neighbors at the boundaries of the simulation domain, to simulate the effect of a larger domain filled with a gas.

 |

**
Cohesion
**

 |
Controls the surface tension.

 |

**
Baroclinity
**

 |
Creates turbulence when a column of particles is rising upwards.

 |

**
Spread
**

 |
Specifies the radius in which SPH particles are spawned around the position of the emitter.

 |

**
Particle Influence
**

 |
Controls the drag with which particles are carried along the fluid field.

 |

**
Number of Iterations
**

 |
Specifies the number of solver iterations required per frame.

 |

**
Grid Size X, Grid Size Y, Grid Size Z
**

 |
Specifies the number of cells for the acceleration grid in each dimension.

 |

**
Particles Per Frame
**

 |
Specifies the amount of fluid simulation particles to be spawned per frame.

 |

CVar/Command
 |
Description
 |
Comment and examples
 |

**
r_GpuPhysicsFluidDynamicsDebug
**

 |
Draws GPU Fluid Particles for debugging purposes. This drastically decreases simulation performance. The
**
default value
**
 of this feature is
**
1
**
.

 |
0 - Prevents fetching of any debug information.

1 - Fetches the acceleration structure bounds and fluid particle positions.

 |

##
Sprites

This feature forces the entire component to be evaluated on the GPU rather than the CPU. The GPU is far more suitable for the processing of a large amount of particles than the CPU. Using a
[/docs/static/engines/cryengine-5/categories/23756816/pages/36867966](
Motion:
 Physics
)
 feature, the CPU can handle dozens of thousands of particles and in some cases up to hundreds of thousands of particles. Since the computational effort is roughly linear in regard to the particle amount, then the processing of these particles can eventually become a bottleneck. However, the same feature in GPU mode can easily handle hundreds of thousands of particles.

Depending on the game type and the performance of the GPU, it can even be possible to have more than a million particles introduced to the game. Currently, the user interface limits the maximum number of GPU Particles to two million. After paying the upfront cost that comes with initializing and running the GPU pipeline, the investment quickly pays off when processing a large number of particles. This is especially true for heavy features such as the Motion: Physics component; also Simplex or Simplex Curl Noise benefit a lot from the raw processing power that is available on a modern GPU. On the other hand, the GPU pipeline is more limited in functionality.

For more details on how GPU particles work see
[/docs/static/engines/cryengine-5/categories/23756816/pages/25526352](
GPU Support
)
.

For more information about the difference between a Component and a Runtime, please see
[/docs/static/engines/cryengine-5/categories/23756816/pages/26217391](
Key Concepts
)
.

*
[Image: /docs/static/attachments/44107823]

*

Properties

 |
Description

 |

**
Sort Mode
**

 |
Determines the type of sorting to be used for particles.

Sorting is always applied in every frame. It is important for semi-transparent particles, since the order in which they are rendered influences the final visual quality. If no sorting is applied, particles might start to randomly appear on top of each other; this is due to how the particles are stored in memory.

-
**
None -
**
 No sorting is applied to the particles and they will be rendered randomly. Use this method for fast rendering; be aware that in some cases it can result in visual glitches.

-
**
Back to Front -
**
First, renders the particles that are on the farthest point from the camera. Then, particles closest to the camera are rendered. This is the standard method to sort particles.

-
**
Front to Back -
**
Renders the particles which are closest to the camera first. This causes particles to appear hollow.

-
**
Old to New -
**
Renders the oldest particles first; the recently created particles are created afterwards.

-
**
New to Old -
**
Renders the newest particles first, then the older particles.

If
**
Appearance: Blending
**
 is to be used with mode
**
Additive
**
, please set this property to
**
None
**
. Additive particles do not need sorting. For more details about the Appearance: Blending feature, please refer to
[/docs/static/engines/cryengine-5/categories/23756816/pages/36868247](
Appearance
)
.
 |

**
Facing Mode
**

 |
Specifies which way particles face.

-
**
Screen -
**
 Aligns the sprites to face towards the screen.

-
**
Velocity -
**
 Aligns the sprite along its velocity line while maintaining its face towards the camera. This method is fundamental for fast moving particles.
 |

**
Axis Scale
**

 |
Only valid when
**
 Facing Mode
**
 is set to
**
Velocity.
**
Specifies the size of the particle for its velocity vector, while the height of the particle is always constrained by its size. Recommended value for this property is 0.016 (which is 1/60); this makes a sprite behave like motion blur.

 |

**
Sort Bias
**

 |
Specifies the sorting order of components that are always based on the distance to the camera of the emitter to which they belong. While Sort Mode specifies sorting of sprites within a component, sprites do not sort themselves with other components. This bias is added to that distance to reorder the component relative to other components. It can for example, force fire particles to always render on top of smoke.

 |

[#collision](
Collision
)
[#gpu-fluid-dynamics](
GPU Fluid Dynamics
)
[#sprites](
Sprites
)
