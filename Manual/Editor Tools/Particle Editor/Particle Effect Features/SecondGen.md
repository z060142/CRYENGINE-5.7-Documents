# SecondGen

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/36868322
- Page ID: 36868322
- Breadcrumb: Editor Tools > Particle Editor > Particle Effect Features > SecondGen
- Parent: Particle Effect Features

## Content

## Overview

Second Generation particles (SecondGen) permit the individual particles to act as sub-emitters of other components. Many different types of effects can be achieved with this feature, but the most common ones would be effects with trails.

Although the feature is called SecondGen, which implies a parent-child relationship, in practice, there is no limit to the number of generations that can be achieved. There is also no limit to the number of SecondGen features that can be added to a single component or the number of child components attached to those features.

The following options are available under the SecondGen category:

### OnCollide

This feature will be triggered every time a parent particle collides with anything. Can be triggered several times per parent and it will be valid until the parent dies.

For more information regarding the options available in this feature, see the Common Settings section below.

### OnDeath

This feature will be triggered every time a parent particle dies. This is a single frame event; meaning that it will only allow child particles to spawn in a single update loop.

For more information on the options available in this feature, see the Common Settingssection below.

### OnSpawn

This feature will start spawning child effects every time a new particle is spawned. This is a continuous event; it will trigger the spawning of child particles when a new parent particle is born and will automatically stop when the parent particle finally dies. The actual child spawning logic is executed within the child component. See [Spawn](Spawn.md) features for more details. Use this feature to create effects such as trails.

For more information regarding the options available in this feature, see the Common Settings section below.

### Common Settings

All SecondGen features share a common behavior, which can be later specialized but is still based on each individual feature.

Properties | Description
--- | ---
**Mode** | When more than one child component is attached to this SecondGen feature, it specifies which behavior is to be expected when the feature gets triggered for each parent particle. It includes the following options: - **All -** When the trigger conditions are met, starts spawning particles on all the children attached to the feature. It is usually used when each child acts as a visual layer and follow their parents. - ** Random -** When the trigger conditions are met, one of the attached children is randomly chosen to start spawning child particles. Usually used when child components are variations of each other; only one child is supposed to be active for each parent particle.
**Probability** | Sets the probability that a child particle will start spawning for a parent particle when the trigger condition is met. A value of 1 means that it will trigger every time; a value of **0** effectively disables the feature; a value of ** 0.5** means that only half of the trigger conditions will actually spawn new child particles.
**Components** | Lists the number of child components attached to this feature. This property is read only. To attach a child to a parent component, use the graphical user interface links.

### GPU Support

GPU particles can be spawned by CPU particles but not the other way round. Information about the parent particles is sent to the GPU and saved in the GPU memory.

[OnCollide](#oncollide)[OnDeath](#ondeath)[OnSpawn](#onspawn)[Common Settings](#common-settings)[GPU Support](#gpu-support)
