# Key Concepts

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/26217391
- Page ID: 26217391
- Breadcrumb: Graphics & Rendering > Particles > Key Concepts
- Parent: Particles

## Content

##
Overview

The main key concepts that are used in CRYENGINE's particle system are listed below:

For more information on Particles reference, please refer
**
[here](../../Editor%20Tools/Particle%20Editor/Particle%20Effect%20Features.md)
**
.

##
More Information

-
[GPU Support](GPU%20Support.md)

-
[Particle Effect Features](../../Editor%20Tools/Particle%20Editor/Particle%20Effect%20Features.md)

-
[Particle Editor](../../Editor%20Tools/Particle%20Editor.md)

[More Information](#more-information)
[Particle Editor](#particle-editor)
[Particle Effect](#particle-effect)
[Component](#component)
[Feature](#feature)
[Modifiers and Effectors](#modifiers-and-effectors)
[SecondGen (Second Generation)](#secondgen-second-generation)
[Attributes](#attributes)
[Particle Emitter](#particle-emitter)
[Runtime](#runtime)
[Emitter Targets](#emitter-targets)

##
Particle Editor

It is a particle editing tool in CRYENGINE which gives you access to an advanced particle system. It is used to create realistic effects such as explosions, fire, smoke effects and much more. For more information on particle system, refer
**
[here](../../Editor%20Tools/Particle%20Editor.md)
**
.

##
Particle Effect

It is a combination of components merged as an individual asset usually created by an artist that represents a placeable object. For example, fireworks, lightning, magic spells and many more.

##
Component

Effects are composed of multiple components. Each component represents a particular aspect of the effect. For example, a firework effect might be composed out of rockets, glitter, flash bangs, colorful willows, and etc. For more information on adding an effect to a component, please refer
**
[here](../../Editor%20Tools/Particle%20Editor/Particle%20Effect%20Features/Component.md)
**
.

##
Feature

Features are used to implement a particular behavior in a component. They are the building blocks in each component which is used to specify various aspects such as velocity, size and appearance of a particle.

##
Modifiers and Effectors

It allows some features behaviors to be further manipulated over each particle life time or other aspects. By combining different features along with modifiers and effectors together, you can create stunningly complex behaviors. Multiple modifiers can be added to a feature. For more information on adding a Modifier to a feature, please refer
**
[here](../../Editor%20Tools/Particle%20Editor/Particle%20Effect%20Features/Modifiers.md)
**
.

##
SecondGen (Second Generation)

One of the key highlights of CRYENGINE's particle system is SecondGen feature. This allows to connect multiple components together as parent-children relationships. This enables parent particles to spawn multiple child particles, and the child particles will inherit data/fields from its parent particle. For more information on SecondGen feature, please refer
**
[here](../../Editor%20Tools/Particle%20Editor/Particle%20Effect%20Features/SecondGen.md)
**
.

##
Attributes

Attributes allows manipulating a particle effect using external factors usually from FlowGraph or TrackView and also from game code. Attributes acts as a layer of communication between the effect and the game which provides the artist full visual control over how an effect should behave in different conditions.

##
Particle Emitter

When the particle effects get spawned into a level either as an entity, game code or any other means, They are spawned as Particle Emitters which contains the full working logic of a particle effect.

##
Runtime

A Runtime contains the full running logic of a component. It is the one that actually does the simulation and rendering of particles.

##
Emitter Targets

A target is a single point in space, often attached to another game entity. Many features support targets as a property. In the particle system, targets are setup by using entity links named as
*
Target
*
. Targets can also be setup by the game code for gameplay purposes.
