# Motion

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/36867966
- Page ID: 36867966
- Breadcrumb: Editor Tools > Particle Editor > Particle Effect Features > Motion
- Parent: Particle Effect Features

## Content

## Overview

Motion features provide movement to a component. Without a motion feature, particles can't move even when a velocity value is assigned on them, See [Velocity](Velocity.md) and [Location](Location.md) for more details on how to add velocity to particles.

Motion features can also use [Effectors](Modifiers/Effectors.md) to apply non-uniform forces to the particles. Effectors are extremely important in adding flair to otherwise standard physics.

The following options are available under the Motion category:

### Collisions

This feature allows particles to collide and interact with the physical environment around them.

This feature is for CPU particles only. For GPU particles, please refer to the [GPU Particles: Collision](GPU%20Particles.md) feature. The CryPhysics motion feature already supports collisions and does not require this feature.

Properties | Description
--- | ---
**Terrain** | Allows particles to collide against the terrain.
**Static Objects** | Allows particles to collide against physical objects which cannot move; for example floors, walls etc.
**Dynamic Objects** | Allows particles to collide against physical objects that can move; for example characters, vehicles etc. This method requires significantly more performance than static Objects or Terrain. This option should be used only when it is absolutely necessary.
**Water** | Allows particles to collide against water surfaces.
**Elasticity** | Specifies elasticity for collisions and it affects bounciness. An **Elasticity** value of ** 0** means that particles will stop instantly on collision. A value of ** 1** will make particles bounce off the surface with which they collide.
**Friction** | Specifies the friction. It is especially efficient when particles are sliding over surfaces. **A value of 0** means particles are frictionless; meaning it takes a long time for the particle to stop. ** A higher value**, on the other hand, means more friction; meaning it takes less time for the particle to stop.
**Collision Limit** | Specifies if there is a limit to the number of collisions allowed: - **Unlimited -** Particles will collide against the physical environment as many times as possible. - ** Ignore -** After reaching a certain number of collisions, particles will ignore any further collision(s). - ** Stop -** After reaching a certain number of collisions, particles will stop. Even gravity can't make particles move. - ** Kill -** After reaching a certain number of collisions, particles are forcefully killed.
**Max Collisions** | This option is active only when the Collision value is not set to Unlimited. It specifies the maximum number of collisions allowed per particle.
**Rotate to Normal** | Every time a particle collides, it realigns its orientation to the surface it collided with.

The features [Location: Omni](Location.md) and Motion: Collisions can be used together to create an omnipresent colliding effect. By setting the respective feature parameters appropriately, an omnipresent environmental effect like rain or snow can be authored. With the addition of Motion: Collisions feature, these effects can react to collisions and stay out of indoors or other specific areas. For more information, see [Tutorial - Creating an Omnipresent Colliding Effect](../../../Tutorials/Graphics/Particle%20Tutorials/Tutorial%20-%20Creating%20an%20Omnipresent%20Colliding%20Effect.md).

### CryPhysics

CryPhysics is a more advanced type of Motion: Physics. It uses CRYENGINE CryPhysics to move a particle and It sacrifices the high levels of performance that Physics can provide. On the other hand, it is far more precise and better integrated with the physics scene. One of the most important aspects of this feature is that it allows the addition of mass to a particle and prevents the particle from being points in space without any physical properties. This also implies that particles can carry momentum. Therefore, not only the particles are affected by a level's physical objects, but these physical objects can also be affected by the particles. This feature also enables particle collisions. Please note that Only Point Particle collision detection is supported at the moment. Other types of collisions will be added later.

This feature supports many of the systems provided by CRYENGINE, but it comes with a significant cost in performance and is therefore not recommended to be used for more than a thousand particles. Ideally, it is recommended to use less than a thousand particles at a time. Note that while Motion: Physics can handle dozens of thousands of particles in comparison, GPU particles can handle hundreds of thousands of particles. Therefore, it is highly recommended to mix up components with regular Physics and with CryPhysics using [SecondGen](SecondGen.md) particles. By doing so, the optimal result can be achieved as this technique uses the best outcomes of both scenarios.

Properties | Description
--- | ---
**Physics Type** | Specifies the following Physics type for a particle: - **Particle** - ** Mesh**
**Surface Type** | Specifies the physical material being used by the particle. For more information on Surface Types and Material Effects, see [Material Effects](/docs/static/engines/cryengine-5/categories/23756816/pages/26215203).
**Gravity Scale** | Scales the rate of acceleration due to the gravity level applied to particles. **A value of 0** will disable gravity completely, while ** a value of 1** means full gravity acceleration.
**Drag** | Also known as air resistance, specifies how much the particle's velocity should slow down in accordance to the air around them. This feature models linear air drag which means that the force applied to the particle is inversely proportional to its own velocity. This unit is measured in seconds. The higher the value, the faster the particles will reach to wind speed.
**Density** | Specifies the density of a particle. This is in grams per milliliter (g/ml). The actual particle mass depends on its size and density. Larger particles will be heavier than smaller particles for the same density.
**Thickness** | Specifies how much of the fraction of the particle's size is to be used as a collision radius. With a value of 0, only the center of the particle collides against the scene; a value of 1, on the other hand, results in particles being simulated as spheres with a radius equal to particle size.
**Uniform Acceleration** | Applies a uniform acceleration in meters per second squared (m/s2) that will be applied to all particles. This vector is added to the CryPhysics gravity acceleration, but is not scaled by the Gravity Scale property. A value of -9.8 in the Z axis will replicate the Earth's gravity.

### MoveRelativeToEmitter

This feature moves the component's particles relative to its parent particle or emitter. Child particles will move whenever a parent has moved. This effectively stimulates local space particles and makes it much more search friendly.

Properties | Description
--- | ---
**Position Inherit** | While the parent particle is alive, this option specifies how much of the parent's position needs to be inherited.
**Velocity Inherit** | While the parent particle is alive, this option specifies how much of the parent's velocity needs to be inherited.
**Angular Inherit** | While the parent particle is alive, this option specifies how much of the parent's orientation needs to be inherited.
**Velocity Inherit After Death** | After parent dies, this option allows child particles to inherit the last known velocity of the parent.

### Physics

Physics is the standard Motion type feature to move particles around. This feature has been constructed for high levels of performance, however it sacrifices precision and interactivity between the particle and the scene.

Properties | Description
--- | ---
**Gravity Scale** | Scales the rate of acceleration due to the gravity level applied to the particles. The actual gravity acceleration and direction is specified in CRYENGINE CryPhysics. **A value of 0** will disable gravity completely, while ** a value of 1** means full gravity acceleration.
**Drag** | Also known as air resistance. It specifies how much the particle's velocity should slow down in accordance to the air around them. This feature models linear air drag which means that the force applied to the particle is inversely proportional to its own velocity. This unit is measured in 1/seconds. The higher the value, the faster the particles will reach to wind speed.
**Level Wind Scale** | Specifies how much the global wind affects the particles. Refer to [Level Settings](../../Level%20Editor%20Tab/Level%20Settings.md)for more details on how to setup global scene wind. With a value of 0, particles will not be affected by the global wind, but they will still be affected by other wind sources.
**Angular Drag Multiplier** | Additional scale multiplier on Drag to affect drag on spinning particles. When set to **1**, the Drag option will affect spinning particles in the same way it affects moving particles. If set to ** 0**, it will affect moving particles, but not their spin. Works for both 2D and 3D Spin.
**Per-Particle Force Computation** | When local force areas like wind are present, this option computes the exact force on each particle and creates a more realistic motion. If it's set to false, a single average force is computed for the entire component and it is applied to all particles.
**Uniform Acceleration** | Applies a uniform acceleration in meters per second squared (m/s2) that will be applied to all particles. This vector is added to the CryPhysics gravity acceleration, but is not scaled by the Gravity Scale property. A value of -9.8 in the Z axis will replicate the Earths gravity.
**Uniform Wind** | Specifies a global wind velocity to be applied to all particles. This is added to the scene's wind velocity, but is not scaled by the Wind Scale property of the level. See [Level Settings](../../Level%20Editor%20Tab/Level%20Settings.md)for more details on how to setup global scene wind.
**Local Effectors** | Enables the usage of the Effectors that can be applied to the particles. While Uniform Acceleration and Uniform Wind affect all particles equally, Effectors can specify different accelerations and wind velocities to each particle individually. This can enable quite sophisticated particle dynamics. For more information, see [Effectors](Modifiers/Effectors.md).

### GPU Support

This feature is supported on the GPU, but no modifiers are available for the properties.

[Collisions](#collisions)[CryPhysics](#cryphysics)[MoveRelativeToEmitter](#moverelativetoemitter)[Physics](#physics)[GPU Support](#gpu-support)
