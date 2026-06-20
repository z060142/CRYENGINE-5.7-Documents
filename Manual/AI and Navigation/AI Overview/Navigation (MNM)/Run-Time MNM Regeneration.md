# Run-Time MNM Regeneration

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/25535422
- Page ID: 25535422
- Breadcrumb: AI and Navigation > AI Overview > Navigation (MNM) > Run-Time MNM Regeneration
- Parent: Navigation (MNM)

## Content

![Image](https://www.cryengine.com/docs/static/attachments/29933212)

## Overview

## Sections

In CRYENGINE Flow Graph nodes exist which make it possible to regenerate the MNM (Multi-Layer Navigation) mesh at run-time in the Launcher.

This feature was used in [Ryse](http://www.rysegame.com/), in situations for example, where an object would be destroyed and create or block an area where AI could/couldn't navigate. This meant the navmesh needed to be updated for the AI to understand their new surroundings.

[Sections](#sections)[Entity GetBounds Node](#entity-getbounds-node)[AI RegenerateMNM Node](#ai-regeneratemnm-node)[Example Setup](#example-setup)

### Entity GetBounds Node

The **Entity:GetBounds** node can be used to obtain the bounding box size (in local or world-space coords) of an entity.

This gives us the information about the location inside the MNM area which requires updating. We'll know where the object moved to and how big it is.

### AI RegenerateMNM Node

With the **AI:RegenerateMNM** node, we can specify a min/max Vec3 world-space coordinate of where we want the navigation mesh to be regenerated.

Technically there's no reason why we couldn't regenerate the entire level, but we want to keep the performance high so it's better to regenerate only what you need.

### Example Setup

In the example below, you can see this setup being used to regenerate a small area where we're moving a GeomEntity back and forth.

The results can be seen below, taken from the Launcher. On the left we have the old results (no regeneration) and on the right using the new regeneration setup.

|
--- | ---
Beam Without Regenerate MNM | Beam With Regenerate MNM

#### Usage Notes

It is important to note that dynamically updating the AI navigation like this isn't without potential implications.

Level Designers need to be aware of potential issues such as AI being suddenly outside of a nav mesh area, time required for an AI navigation path to be updated with new information about the area, and so on.

Caution should be used to ensure that the AI always have a clear understanding of their surroundings, otherwise they can become stuck and behave incorrectly.
