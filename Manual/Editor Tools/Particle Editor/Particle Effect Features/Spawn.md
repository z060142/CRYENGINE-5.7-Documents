# Spawn

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/36868327
- Page ID: 36868327
- Breadcrumb: Editor Tools > Particle Editor > Particle Effect Features > Spawn
- Parent: Particle Effect Features

## Content

## Overview

This category controls the number and duration of new particles that are added to the component. Spawn logic is always updated for each emitter that is created in the game. When a component is a child of a SecondGen component, spawn logic will instead update each parent particle that meets the trigger condition. When a parent particle dies, Spawn features will automatically stop adding new particles for that parent. For more information about SecondGen components, please refer to [SecondGen](SecondGen.md).

Similar to most other features, Spawn features can also be combined together to achieve more sophisticated spawning effects.

The following options are available under the Spawn category:

### Count

This feature spawns a specific number of particles in a single burst.

Properties | Description
--- | ---
**Amount** | Specifies the number of particles to be spawned. Can be used with [Modifiers](Modifiers.md) for more dynamic control of particle spawning.
**Delay** | Adds a delay in seconds to the particle effect and makes the feature start spawning particles when the specified time is reached. This feature is optional.
**Duration** | If enabled, specifies the spawn duration of the particles. If it is set to **0**, a number of particles, which is defined by the Count value, will be spawned in a single frame. If disabled, it continuously spawns new particles while trying to keep the number of particles per instance as specified by the ** Count** value.
**Restart** | When a value is assigned to **Duration**, this option appears. If it's enabled, the entire feature will be restarted every time the specified amount of time is reached.
**Mode** | Only appears when **Duration** is not Infinite. Defines the outcome of ** Amount** option. - ** Maximum Particles -** The particle emission rate is computed such that the maximum particles alive at any time is equal to ** Amount**. - ** Total Particles -** The particle emission rate is computed such that the total particles emitted over the component lifetime is equal to ** Amount**.

### Density

This feature spawns particles to achieve the given spatial density and is based on the spawn length, area or volume which is usually specified in the [Location](Location.md) feature. For each dimension, at least one particle is always spawned.

Properties | Description
--- | ---
**Amount** | Depends on the dimensions and spawns for the specified number of particles for each meter, square meter or cubic meter (m, m2 or m3). For example, if a component contains a location box with the dimensions of width 4m, length 1m and height 0.5m (volume = 2m3), and the number of particles is set to 20, the total number of particles that will be spawned will be 40 (2m3 x 20).
**Delay** | Adds a delay in seconds to the particle effect and makes the feature start spawning particles when the specified time is reached. This feature is optional.
**Duration** | Specifies the spawn duration of the particles. If no time is specified, spawns all particles at once in a single frame.
**Restart** | When a value is set for **Duration**, this option appears. If it's enabled, the entire feature will be restarted every time the specified amount of time is reached.

### Distance

This feature allows spawning new particles at a specific rate based on the emitter's or parent particle's motion distance. Commonly used on trails to distribute new particles uniformly regardless of the actual parent velocity.

In cases where a parent particle stops moving, (due to drag, for instance) and new particles should still spawn, it is recommended to pair this feature with Spawn: Rate; It will always guarantee new particles to spawn, while the Spawn: Distance feature will adapt to the motion of the parent.

Since the spawn rate of this feature depends on external conditions like the motion of the emitter which is usually driven by game play, special care must be taken to avoid creating an excessive number of particles.

Properties | Description
--- | ---
**Amount** | Specifies the amount of particles to spawn. Can be used with [Modifiers](Modifiers.md) for a more dynamic control of particle spawning.
**Delay** | Adds a delay in seconds to the particle effect and makes the feature start spawning particles when the specified time is reached. This feature is optional.
**Duration** | Specifies the spawn duration of the particles. If no time is specified, spawns all particles at once and in a single frame.
**Restart** | When a value is set for **Duration**, this option appears. If it's enabled, the entire feature will be restarted every time the specified amount of time is reached.
**Mode** | Defines the function of Amount: - **Particles per Meter -** Amount refers to the number of particles to be spawned for each meter traveled by the parent particles or emitter. - ** Meters per Particle -** Amount refers to the distance that needs to be traveled by the parent particle or emitter for a single new particle to be spawned.

### Rate

This feature spawns new particles at a specified rate based on time.

Properties | Description
--- | ---
**Amount** | Specifies the amount of particles to spawn. Can be used with [Modifiers](Modifiers.md) for a more dynamic control of particle spawning.
**Delay** | Adds a delay in seconds to the particle effect and makes the feature start spawning particles when the specified time is reached. This feature is optional.
**Duration** | If used, only spawns particles for the amount of time defined by this option. If not used, this feature is continuous and only stops when the emitter of parent particle also stops.
**Restart** | When e specific value is set for **Duration**, this option appears. If it's enabled, the entire feature will be restarted every time the specified amount of time is reached.
**Mode** | Specifies the function of Amount: - **Particles per Second -** Amount refers to the number of particles to be spawned every second. - ** Seconds per Particle -** Amount refers to the waiting time in seconds until next particle is spawned. - ** Particles per Frame -** Amount refers to the number of particles to be spawned every frame.

### GPU Support

Only the **Spawn**:** Rate** Feature is supported for spawning GPU particles.

[Count](#count)[Density](#density)[Distance](#distance)[Rate](#rate)[GPU Support](#gpu-support)
