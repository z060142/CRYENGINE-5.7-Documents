# Particle Effect Features

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/36868779
- Page ID: 36868779
- Breadcrumb: Editor Tools > Particle Editor > Particle Effect Features
- Parent: Particle Editor

## Child Pages

- [Modifiers](Particle%20Effect%20Features/Modifiers.md)
- [Angles](Particle%20Effect%20Features/Angles.md)
- [Appearance](Particle%20Effect%20Features/Appearance.md)
- [Audio Feature](Particle%20Effect%20Features/Audio%20Feature.md)
- [Child](Particle%20Effect%20Features/Child.md)
- [Component](Particle%20Effect%20Features/Component.md)
- [Field](Particle%20Effect%20Features/Field.md)
- [General](Particle%20Effect%20Features/General.md)
- [GPU Particles](Particle%20Effect%20Features/GPU%20Particles.md)
- [Life](Particle%20Effect%20Features/Life.md)
- [Light](Particle%20Effect%20Features/Light.md)
- [Location](Particle%20Effect%20Features/Location.md)
- [Motion](Particle%20Effect%20Features/Motion.md)
- [Project](Particle%20Effect%20Features/Project.md)
- [Render](Particle%20Effect%20Features/Render.md)
- [SecondGen](Particle%20Effect%20Features/SecondGen.md)
- [Spawn](Particle%20Effect%20Features/Spawn.md)
- [Velocity](Particle%20Effect%20Features/Velocity.md)

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
[Particles Tab (Legacy Particle Editor)](../DataBase%20View/Particles%20Tab%20(Legacy%20Particle%20Editor).md)
 features.

##
In This Section
