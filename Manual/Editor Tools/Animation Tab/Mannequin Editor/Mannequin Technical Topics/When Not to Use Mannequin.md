# When Not to Use Mannequin

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/23308479
- Page ID: 23308479
- Breadcrumb: Editor Tools > Animation Tab > Mannequin Editor > Mannequin Technical Topics > When Not to Use Mannequin
- Parent: Mannequin Technical Topics

## Content

### Overview

Mannequin is designed to be an optional component in CRYENGINE. If you wish you can use 'raw' CryAnimation features instead. Why would you do this? As with every higher level system there are limitations that might get in your way, or might not do what you need.

### Non-Interactive and Simple Characters

For simple cases, Mannequin can be overkill. It does introduce some setup overhead. On the plus side, the system introduces little run-time performance overhead. And using only one system for all your characters simplifies your code, your workflow, and makes it easier to add or remove complexity later.

Note that specifically for non-interactive animation there are good alternatives:

- For Cinematics, you can use the specialized tool [Track View](../../../Track%20View.md).
- For Environment/background animations, you can create AnimObject entities.
- For Simple scripting, you can use AnimObject entities and drive them with Flowgraph nodes like PlayAnimation. (but then again, you can also use [MannequinObject](../../../../Tutorials/Animation%20and%20Characters/Mannequin%20Editor/Tutorial%20-%20Mannequin%20Scripting.md) entities)

### Can you describe Game State, Sound, Particles, Music with it?

Mannequin is a general sequencing system, so *yes* you certainly can.

If you use Mannequin as a general sequencer you minimize the number of pathways driving other systems, which makes it easier to do things like network synchronization, debugging, etc.

But:

- The way Mannequin organizes the data (or states in your system) might not be optimal for some use cases. Some examples:
- For Music a graph can be more appropriate, and the Music System provides exactly that.
- For playing sound or particle effects when handling collisions, a grid of states is typically more appropriate, and that is exactly what the Material Effects system provides.
- Certain effects might be tied more to a higher level 'action' than to the underlying animation state. For example in your game every *shoot* action might trigger the same sound, and the sound might not need to be synchronized at all with the animation. In this case you could set up the sound trigger in a higher level system. But keep in mind what was mentioned above, mixing different pathways to trigger systems typically complicates other code.
- Mannequin currently only supports synchronization of clips using absolute time. That means it has no support for synchronizing clips to cycles within a looping animation (for example footsteps that need to play on every cycle). Similarly, it doesn't adjust synchronized clips when you have animations that change length dynamically like [blend spaces](../../Character%20Tool/Blend%20Spaces%20-%20Character%20Tool.md). In both cases [Animation Events](../../Character%20Tool/Animation%20Events%20-%20Character%20Tool.md) which are tied directly to the "segment time" of animation clips can be a better fit.
