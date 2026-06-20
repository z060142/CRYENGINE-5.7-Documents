# GPU Support

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/25526352
- Page ID: 25526352
- Breadcrumb: Graphics & Rendering > Particles > GPU Support
- Parent: Particles

## Content

##
Overview

A component with a large amount of particles can benefit from being processed by our new GPU particle pipeline. This switch can be performed by adding a
*
Render: GPU Sprites
*
 feature to a component. If the
*
Render: GPU Sprites
*
 is the only active render feature, the particle component will switch into GPU mode.

In this mode, all particle data is allocated directly on the GPU and transformed by compute shaders, and the particles will be drawn directly off the GPU memory. This achieves significantly a higher particle throughput for computation-intensive effects.

When a component is in GPU mode, it can use a subset of the features that are available in CPU mode, but also has access to other functionality that is not available on the CPU, for example,
*
Screen Space Collisions
*
.

##
More Information

-
[Key Concepts](Key%20Concepts.md)

-
[Particle Effect Features](../../Editor%20Tools/Particle%20Editor/Particle%20Effect%20Features.md)

-
[Particle Editor](../../Editor%20Tools/Particle%20Editor.md)

##
Spawning particles and Lifetime management

GPU particles can be spawned in isolation or by parent CPU particles. The CPU logic decides the number of particles to be spawned, but the actual initialization of newborn particles will be done entirely on the GPU. Only information about the parent of a particle group will be extracted on the CPU and sent to the GPU.

This makes particle spawning quite efficient and allows large numbers of particles to be spawned without degrading the performance of the particle component too much.

After spawning, GPU Particles will be handled entirely on the GPU and nothing will be written back to the main memory. This allows for effects that depend solely on data that is available on the GPU, such as
*
Screen Space Collisions
*
. It is impossible for GPU particles to interact with the actual physics geometry in the game world though, since this data is only available on the CPU.

If a particle dies, the GPU masks this particle and removes it from the array of particles by swapping particles from the back of the array into the empty spots in parallel.

##
Performance characteristics

The total cost of a particle component on the GPU can be roughly split into the time that is spent on the various compute shaders (i.e. particle initialization, particle update, bookkeeping and sorting) and on rendering. For large enough particles, the total GPU time is dominated by the rendering, especially for transparent particles, since a lot of fill rate is required for rendering. For smaller particles, especially with complex behaviors such as procedural fluid motion induced by Curl Noise effectors, the update compute shader can become the primary contributor to total GPU cost of the particle component.

Generally, the GPU cost of a GPU particle component is determined by the number of particles simulated. Since initialization of a GPU particle component involves allocating resources on the GPU and
maintaining record
of active GPU particles, there is an upfront cost to be paid for each GPU particle effect.

The spawning process itself is quite fast, since the spawned particles are initialized on the GPU itself, but if a lot of particles are spawned each frame, it can become a factor to be considered in the performance evaluation.

GPU particles can be sorted, although this introduces further overhead to the computation. Also, when GPU particles are sorted, there is a second particle buffer allocated because the particles then will be double buffered, effectively nearly doubling the memory footprint of the effect. This means that sorting should only be enabled when it is really necessary and improving the quality of the effect substantially.

For more information on Particles reference, please refer
**
[here](../../Editor%20Tools/Particle%20Editor/Particle%20Effect%20Features.md)
**
.
