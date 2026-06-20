# Per Object Shadows

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/26215320
- Page ID: 26215320
- Breadcrumb: Graphics & Rendering > Lighting > Lighting Overview > Per Object Shadows
- Parent: Lighting Overview

## Content

![Image](https://www.cryengine.com/docs/static/attachments/29933282)

## Overview

With the per object shadow feature, custom shadow maps can be assigned to select objects. This can result in increased shadow quality due to higher world space shadow texel density and reduced depth range.

The drawbacks are increased memory consumption of the additional shadow maps and increased shadow filtering cost. As an example, the additional cost amounted to approximately 0.25ms for the main protagonist in Ryse on XboxOne.

*Left: In-game shadows, right: Per Object shadows*

[Usage](#usage)[Object Shadows Flow Graph Node](#object-shadows-flow-graph-node)[Restrictions](#restrictions)[Related CVars](#related-cvars)

### Usage

There are currently two ways to assign a per object shadow map:

- Via the Environment:PerEntityShadows flow graph node.
- Directly from game code via I3DEngine interface functions.

### Object Shadows Flow Graph Node

Create a PerEntityShadows node and assign the target entity to the 'entity' slot. The trigger input will apply the settings to the engine.

Note that the node is stateless w.r.t. the entity, so you can add multiple PerEntityShadow nodes for the same entity. The last one to trigger will be in effect.

There are various configurable settings to tweak the shadow appearance:

- **ConstBias/SlopeBias:** Can be used to avoid self shadowing artifacts.
- **Jittering:** Filter kernel size, directly affects shadow softness.
- **BBoxScale:** Scale factor for bounding box of the selected entity. Can be useful in case the engine bounding box is too small or too large.
- **ShadowMapSize:** Size of the custom shadow map. Note: automatically rounded to the next power of two.

### Restrictions

Per object shadows are subject to a number of restrictions:

- They only affect sun shadows.
- For performance reasons, per object shadows are not sampled on forward geometry (e.g. particles, forward rendered hair and eyes).

### Related CVars

**e_ShadowsPerObject:** 0=0ff, 1=on, -1=don't draw object shadows.
