# CryPhysics

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/23306410
- Page ID: 23306410
- Breadcrumb: CRYENGINE Engine Code > Engine Modules > CryPhysics
- Parent: Engine Modules

## Child Pages

- [In Depth Simulation Description](CryPhysics/In%20Depth%20Simulation%20Description.md)
- [GetEntitiesInBox](CryPhysics/GetEntitiesInBox.md)
- [Collision Classes](CryPhysics/Collision%20Classes.md)
- [Registering geometries in the physics](CryPhysics/Registering%20geometries%20in%20the%20physics.md)
- [Physical entity types](CryPhysics/Physical%20entity%20types.md)
- [Physical entity interface](CryPhysics/Physical%20entity%20interface.md)
- [Physical Areas](CryPhysics/Physical%20Areas.md)
- [Ray and Primitive Tracing](CryPhysics/Ray%20and%20Primitive%20Tracing.md)
- [Physical Explosions](CryPhysics/Physical%20Explosions.md)
- [Physical Breakage Systems](CryPhysics/Physical%20Breakage%20Systems.md)
- [Using NVIDIA PhysX in CRYENGINE](CryPhysics/Using%20NVIDIA%20PhysX%20in%20CRYENGINE.md)
- [Local Simulation Grids](CryPhysics/Local%20Simulation%20Grids.md)

## Content

### Overview

The physics subsystem is used to physically simulate objects registered in it. It has its own set of entities and geometries, which have counterparts in other parts of the engine. For instance, a simulated rigid body object can be associated with either an Entity System's entity, or a 3dengine's particle. Typically, an outside system requests creation of a physical entity of a certain type and stores a pointer to itself in it in so called 'foreign data'. One exception is breakable objects, where the physics creates new physical entities internally and notifies the rest of the engine, which in turn creates the accompanying engine objects and associated them with those new physical entities.

By default the physics runs in its own separate thread, and can have a customizable amount of additional worker threads. Each frame, CrySystem requests the physics to make a step with the current frame time, and the physics posts notifications when the results are ready. Note that if the physics cannot keep up with the main thread, it can take more than one main thread frame for the results to come back. Such situations, of course, should be avoided. When the physical world is doing a step, all incoming change requests to the physical entities are internally queued and executed only at the beginning of the next step (lest they interfere with an ongoing simulation). This can make debugging where certain changes come from difficult, so it's possible to switch the physics to do its calculation in the main thread via a console variable (**sys_physics_enable_MT**).

Physical notifications come in the form of events (the corresponding structures have names prefixed with "EventPhys"). In order to listen to them, other systems must register listeners via an AddEventClient call. All listeners are "global" and must internally redirect the event to specific engine objects (if necessary) using physical foreign data information. There are two types of events - immediate and logged. Immediate event clients are called directly from the physics thread, so the functions must be thread-safe regarding their systems' main threads. Logged events are accumulated in an internal queue and are sent from the main thread, close to the end of the main step. Generally, immediate events are useful for doing some additional simulation in the listener, since in this case precise synchronization with the physics is necessary.

Typically physical entities have one or more physicalized geometries. Geometry physicalization is described here: [Registering geometries in the physics](CryPhysics/Registering%20geometries%20in%20the%20physics.md)

There are several [Physical entity types](CryPhysics/Physical%20entity%20types.md). More information about setting up physical entities can be found here: [Physical entity interface](CryPhysics/Physical%20entity%20interface.md). More information about how the simulation works internally can be found [here](CryPhysics/In%20Depth%20Simulation%20Description.md).

In order to speed up broad-phase collision detection (i.e. quickly find entities that are potentially colliding with each other) the physics uses a 2-dimensional grid. Each entity is registered in each cell that's touched by its axis-aligned bounding box, so it's possible to get a list of entities that touch a specific cell. Entity-in-cell bookkeeping is facilitated by so-called "grid thunk" structures. Note that there is a global limit on their amount, and once it's reached no further grid changes will be registered, resulting in entities "losing collisions" (there will be a warning in the log about it). Cell size should be chosen based on the total map size and "interaction density", i.e. smaller cells can give more precise potential collision candidates list, but if an entity occupies many cells, the costs of gathering lists from all of them will outweigh this advantage. Grid queries are exposed to other systems via [GetEntitiesInBox](CryPhysics/GetEntitiesInBox.md)function.

Since version 5.2, [multiple simulation grids](CryPhysics/Local%20Simulation%20Grids.md) are supported.

Other commonly used world queries are [Ray and Primitive Tracing](CryPhysics/Ray%20and%20Primitive%20Tracing.md).

Various environmental effects can be simulated by using [Physical Areas](CryPhysics/Physical%20Areas.md).

There are several breakage systems in the engine, described [here](CryPhysics/Physical%20Breakage%20Systems.md).

[Explosions](CryPhysics/Physical%20Explosions.md) are one way to trigger said breakage.

It's possible to see physical entities by using **p_draw_helpers** console variable. In the simplest case it can just be set to 1 to show the most common set of helpers, but it can also be customized to include different types of entities and helpers, use "p_draw_helpers?" for details.

In addition to the engine's profiler, the physics has a more high-level one, enabled with **p_profile**. Further profiling options are ** p_profile_entities** to show the list of physical entities that take most of the simulation time, and ** p_profile_functions** to monitor the costs of RayWorldIntersection, PrimitiveWorldIntersection, and GetEntitiesInBox calls coming from various systems.

- [In Depth Simulation Description](CryPhysics/In%20Depth%20Simulation%20Description.md)
- [GetEntitiesInBox](CryPhysics/GetEntitiesInBox.md)
- [Collision Classes](CryPhysics/Collision%20Classes.md)
- [Registering geometries in the physics](CryPhysics/Registering%20geometries%20in%20the%20physics.md)
- [Physical entity types](CryPhysics/Physical%20entity%20types.md)
- [Physical entity interface](CryPhysics/Physical%20entity%20interface.md)
- [Physical Areas](CryPhysics/Physical%20Areas.md)
- [Ray and Primitive Tracing](CryPhysics/Ray%20and%20Primitive%20Tracing.md)
- [Physical Explosions](CryPhysics/Physical%20Explosions.md)
- [Physical Breakage Systems](CryPhysics/Physical%20Breakage%20Systems.md)
- [Using NVIDIA PhysX in CRYENGINE](CryPhysics/Using%20NVIDIA%20PhysX%20in%20CRYENGINE.md)
- [Local Simulation Grids](CryPhysics/Local%20Simulation%20Grids.md)
