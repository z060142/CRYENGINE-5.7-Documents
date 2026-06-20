# Particle Effect Features

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/36868779
- Page ID: 36868779
- Breadcrumb: Editor Tools > Particle Editor > Particle Effect Features
- Parent: Particle Editor

## Child Pages

- [Modifiers](Particle Effect Features/Modifiers.md)
- [Angles](Particle Effect Features/Angles.md)
- [Appearance](Particle Effect Features/Appearance.md)
- [Audio Feature](Particle Effect Features/Audio Feature.md)
- [Child](Particle Effect Features/Child.md)
- [Component](Particle Effect Features/Component.md)
- [Field](Particle Effect Features/Field.md)
- [General](Particle Effect Features/General.md)
- [GPU Particles](Particle Effect Features/GPU Particles.md)
- [Life](Particle Effect Features/Life.md)
- [Light](Particle Effect Features/Light.md)
- [Location](Particle Effect Features/Location.md)
- [Motion](Particle Effect Features/Motion.md)
- [Project](Particle Effect Features/Project.md)
- [Render](Particle Effect Features/Render.md)
- [SecondGen](Particle Effect Features/SecondGen.md)
- [Spawn](Particle Effect Features/Spawn.md)
- [Velocity](Particle Effect Features/Velocity.md)

## Content

##
Overview

CRYENGINE
 offers a
unique
 particle system
designed
 to
provide
 more flexibility to the user and to make optimal use of modern CPU and memory architectures. To achieve this goal, the particle simulation backend implements a data-oriented design, where memory layouts have been optimized for vectorized processing.

On the frontend side, the particle system presents a modular setup approach that allows a more flexible design of particle effects that can be set up to interact with the rest of the engine through attribute passing.

The particle system introduces seamless switching between a GPU and CPU based particle pipeline. The GPU based particle pipeline implements a subset of the CPU particle functionality while offering much higher speed for massive particle effects such as fluid like effects and fractal movement.

CRYENGINE Particle System offers a vast variety of features. Combining these features ensures that users can create unique particle effects.

These features are strictly related to the
**
Particle Editor
**
 and they are not to be confused with the
[/docs/static/engines/cryengine-5/categories/23756816/pages/36868751](
Particles Tab (Legacy Particle Editor)
)
 features.

##
In This Section
