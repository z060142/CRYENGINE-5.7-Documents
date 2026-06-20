# Particles

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/44959236
- Page ID: 44959236
- Breadcrumb: Graphics & Rendering > Particles
- Parent: Graphics & Rendering

## Child Pages

- [Key Concepts](Particles/Key%20Concepts.md)
- [GPU Support](Particles/GPU%20Support.md)

## Content

## Overview

CRYENGINE V introduces a new particle system that has been designed to offer more flexibility to the designer and to make optimal use of modern CPU and memory architectures. To achieve this goal, the particle simulation backend implements a data-oriented design, where memory layouts have been optimized for vectorized processing.

On the frontend side, the particle system presents a modular setup approach, that allows for flexible design of particle effects that can be set up to interact with the rest of the engine though attribute passing.

The particle system introduces seamless switching between a CPU and GPU based particle pipeline, where the GPU based particle pipeline implements a subset of the CPU particle functionality while offering much higher speeds for massive particle effects such as fluid like effects and fractal movement.![Image](https://www.cryengine.com/docs/static/attachments/44970657) *A sample effect created using the particle system.*

For more information on Particle Effect Features reference, please refer **[here](../Editor%20Tools/Particle%20Editor/Particle%20Effect%20Features.md)**.

- [Key Concepts](Particles/Key%20Concepts.md) - [GPU Support](Particles/GPU%20Support.md)
