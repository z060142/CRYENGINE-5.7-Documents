# Programming

## Child Pages

- [Getting Started](Programming/Getting%20Started.md)
- [Entities and Components](Programming/Entities%20and%20Components.md)
- [Schematyc Guide](Programming/Schematyc%20Guide.md)
- [Lua Scripting](Programming/Lua%20Scripting.md)
- [Examples](Programming/Examples.md)
- [GameSDK Showcase Examples](Programming/GameSDK%20Showcase%20Examples.md)
- [Plugin Update Loop](Programming/Plugin%20Update%20Loop.md)
- [Troubleshooting](Programming/Troubleshooting.md)

## Content

This chapter is a friendly, shallow-to-deep introduction to **programming a
game on CRYENGINE 5.7**. It is aimed at developers who have never touched the
engine codebase before and want a guided path from "open the project" to "my
own code is running in the Sandbox Editor".

The primary language used throughout is **C++**, with the Schematyc reflection
system used to expose components to the editor. **Lua** scripting is also
covered as a lighter-weight option — it is a fully supported scripting layer
that is gradually being de-emphasized in favor of C++ components, but remains
usable for many scenarios.

Read the articles in order for a structured on-ramp:

1. **[Getting Started](Programming/Getting%20Started.md)** — How CRYENGINE
   loads a game, the `.cryproject` file, starting from a GameTemplate, the
   plugin entry point `Cry::IEnginePlugin`, and the `StdAfx.h` module
   definition.
2. **[Entities and Components](Programming/Entities%20and%20Components.md)** —
   What entities and components are, the `IEntityComponent` interface, entity
   events, accessing/spawning entities.
3. **[Schematyc Guide](Programming/Schematyc%20Guide.md)** — Making C++
   components visible in the Sandbox Editor: `ReflectType`, `AddMember`
   properties, `CRY_STATIC_AUTO_REGISTER_FUNCTION`, and the full registration
   flow.
4. **[Lua Scripting](Programming/Lua%20Scripting.md)** — The Lua scripting
   layer: script entities, the Properties table, state machine, ScriptBind
   functions, and when to choose Lua vs C++.
5. **[Examples](Programming/Examples.md)** — Five worked examples from minimal
   to complete: a minimal plugin, a hello-world component, a property-exposing
   rotator, a full player component, and a physics bullet.
6. **[GameSDK Showcase Examples](Programming/GameSDK%20Showcase%20Examples.md)**
   — Real-world C++ patterns from the GameSDK sample: Boids flocking AI,
   deflector shield physics, moving platform manager, custom Flow Graph node,
   and global framework listener. Shows how Crytek engineers structure
   non-trivial gameplay code.
7. **[Plugin Update Loop](Programming/Plugin%20Update%20Loop.md)** — Per-frame
   plugin-level logic and querying other plugins.
8. **[Troubleshooting](Programming/Troubleshooting.md)** — The "my component
   isn't showing up" checklist and common pitfalls.

Related chapters that go deeper into specific subsystems:

- [Entity Component Programming](../Entities%20and%20Tools/Entity%20Component%20Programming.md)
- [Gameplay Framework Programming](../Gameplay/Gameplay%20Framework%20Programming.md)
- [Plugin System](../Beta%20Features/Plugin%20System.md)
- [Engine Architecture Overview](../CRYENGINE%20-%20Getting%20Started/Engine%20Architecture%20Overview.md)