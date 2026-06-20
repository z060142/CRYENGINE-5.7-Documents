# Slots, Geometry and Effects

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/26216230
- Page ID: 26216230
- Breadcrumb: Entity > Slots, Geometry and Effects
- Parent: Entity

## Content

## Overview

## Table of Contents

[Slot Transformation](#slot-transformation)[Slot Material](#slot-material)[Slot Flags](#slot-flags)[Slot Types](#slot-types)[Conclusion](#conclusion)

## Slot Transformation

Each slot is assigned a local transformation, in relation to its parent. This allows for offsetting the slot geometry from the entity it is attached to, and is especially useful when dealing with multiple slots in one entity.

Function name | Description
--- | ---
[IEntity::GetSlotWorldTM](/docs/static/engines/cryengine-5/categories/28704770/pages/29797019) | Gets the transformation of the slot in world coordinates.
[IEntity::GetSlotLocalTM](http://docs.cryengine.com/docs.cryengine.com/display/CPP/IEntity#a74dd2bc8ff7354f070bc3dcf8249b1c4) | Gets the transformation of the slot in relation to its parent.
[IEntity::SetSlotLocalTM](http://docs.cryengine.com/docs.cryengine.com/display/CPP/IEntity#a74dd2bc8ff7354f070bc3dcf8249b1c4) | Sets the relative transformation of the slot.

### Camera-Space Rendering

Camera space rendering allows for drawing an entity slot in the Camera's local space - always making it relative to the camera, and avoiding that other objects are on top. This is most commonly used for first person shooter weaponry and hands.

This is achieved by setting the ENTITY_SLOT_RENDER_NEAREST flag instead of ENTITY_SLOT_RENDER, and then setting the camera-space relative position of the object:

Function name | Description
--- | ---
[IEntity::SetSlotCameraSpacePos](/docs/static/engines/cryengine-5/categories/28704770/pages/29797019) | Sets the camera space position of the slot, used when the ENTITY_SLOT_RENDER_NEAREST is applied to the slot.
[IEntity::GetSlotCameraSpacePos](/docs/static/engines/cryengine-5/categories/28704770/pages/29797019) | Gets the camera space position of the slot, used when the ENTITY_SLOT_RENDER_NEAREST is applied to the slot.

## Slot Material

By default, a slot contains a null material - resulting in the rendered form of a slot using the default material for the object assigned to it. However, it is often useful to override the material of the slot, allowing custom effects on individual entity geometry.

This can be achieved with the [IEntity::GetSlotMaterial](/docs/static/engines/cryengine-5/categories/28704770/pages/29797019)and [IEntity::SetSlotMaterial](/docs/static/engines/cryengine-5/categories/28704770/pages/29797019) functions.

## Slot Flags

The EEntitySlotFlags enum can be used to change the behavior of individual slots, for example to disable rendering entirely - something that can be useful when a slot is only meant for physical interaction.

Function name | Description
--- | ---
[IEntity:;SetSlotFlags](/docs/static/engines/cryengine-5/categories/28704770/pages/29797019) | Used to set the flags for this slot, note that this completely overrides the flags.
[IEntity::GetSlotFlags](/docs/static/engines/cryengine-5/categories/28704770/pages/29797019) | Retrieves the specified slot's flags.

The currently available slot flags are:

Flag name | Description
--- | ---
ENTITY_SLOT_RENDER | Set by default. If cleared, the entity will no longer be rendered to the screen.
ENTITY_SLOT_RENDER_NEAREST | If set, the entity will be rendered in camera space. See [IEntity::SetSlotCameraSpacePos](http://docs.cryengine.com/docs.cryengine.com/display/CPP/IEntity#a1d7674dea67ef282c6d991e0d7f313ed) and [IEntity::GetSlotCameraSpacePos](http://docs.cryengine.com/docs.cryengine.com/display/CPP/IEntity#ac8f480ecdb92b1030c48d110227f04a2).
ENTITY_SLOT_CAST_SHADOW | If set, the entity slot will cast a shadow.

## Slot Types

There are several types of objects that can be applied to an entity slot:

### Characters

Interaction with characters on an entity is limited to:

Function name | Description
--- | ---
[IEntity::GetCharacter](/docs/static/engines/cryengine-5/categories/28704770/pages/29797019) | Retrieves the character instance at the specified slot, if any.
[IEntity::SetCharacter](/docs/static/engines/cryengine-5/categories/28704770/pages/29797019) | Applies an existing character instance (.CDF,.CHR,.CGA) to the specified slot.
[IEntity::LoadCharacter](/docs/static/engines/cryengine-5/categories/28704770/pages/29797019) | Loads specified character from disk and applies it to the specified slot.

For more information on characters, and how to approach animating them, see [Characters and Animations](Characters%20and%20Animations.md).

[Example](/docs/static/engines/cryengine-5/categories/28704770/pages/29797019)

### Static Geometry

Static geometry is represented by the CGF format, and is known in code as [IStatObj](/docs/static/engines/cryengine-5/categories/28704770/pages/29797103).

Interaction with static geometry on an entity is limited to:

Function name | Description
--- | ---
[IEntity::GetStatObj](/docs/static/engines/cryengine-5/categories/28704770/pages/29797019) | Retrieves the static geometry at the specified slot, if any.
[IEntity::SetStatObj](/docs/static/engines/cryengine-5/categories/28704770/pages/29797019) | Applies the specified static geometry (.CGF) to the specified slot.
[IEntity::LoadGeometry](/docs/static/engines/cryengine-5/categories/28704770/pages/29797019) | Loads specified static geometry (.CGF) from disk and applies it to the specified slot.

[Example](/docs/static/engines/cryengine-5/categories/28704770/pages/29797019)

### Particle Emitters

Particles can be loaded into **emitters**, a construct that will continuously emit effects from a point. When assigned to an entity, a particle emitter will follow an entity and thus allow creating very complex effects with ease. Emitters are represented in code by the [IParticleEmitter](/docs/static/engines/cryengine-5/categories/28704770/pages/29797113) interface, while the underlying particle effect (.pfx,.pfx2) is known in code as [IParticleEffect](/docs/static/engines/cryengine-5/categories/28704770/pages/29797112).

Interaction with particle emitters on an entity is limited to:

Function name | Description
--- | ---
[IEntity::GetParticleEmitter](/docs/static/engines/cryengine-5/categories/28704770/pages/29797019) | Retrieves the particle emitter at the specified slot, if any.
[IEntity::SetParticleEmitter](/docs/static/engines/cryengine-5/categories/28704770/pages/29797019) | Applies the specified particle emitter to the specified slot.
[IEntity::LoadParticleEmitter](/docs/static/engines/cryengine-5/categories/28704770/pages/29797019) | Creates an emitter in the specified slot out of the specified effect.

[Example](/docs/static/engines/cryengine-5/categories/28704770/pages/29797019)

### Lights

Very often useful, lights can be loaded into entities to create dynamic light sources that can move around the level at run-time. This is useful to create entities that provide point lights, projected lights or even environment probes.

Lights are loaded into entity slots using the [IEntity::LoadLight](/docs/static/engines/cryengine-5/categories/28704770/pages/29797019) function, with the accompanying CDLight structure defining the behavior of the light. This allows for creating point lights, projector lights and environment probes. An example is available [here](/docs/static/engines/cryengine-5/categories/28704770/pages/29797019).

[Example](/docs/static/engines/cryengine-5/categories/28704770/pages/29797019)

### Fog Volume

Entities can also load fog volumes into slots, allowing the use of dynamic fog effects around logical entities.

Fog volumes can be loaded into entity slots using the [IEntity::LoadFogVolume](/docs/static/engines/cryengine-5/categories/28704770/pages/29797019) function, with the accompanying SFogVolumeProperties structure defining the behavior of the volume.

[Example](/docs/static/engines/cryengine-5/categories/28704770/pages/29797019)

### Geom Cache / Alembic

Geom Caches can be loaded into entities, allowing the playback of arbitrarily animated geometry. This can allow for complex destruction, complicated cloth motion and other special effects that would otherwise be too expensive to calculate in real-time.

Geom Cache can be loaded into entity slots using the [IEntity::LoadGeomCache](/docs/static/engines/cryengine-5/categories/28704770/pages/29797019) function, and can subsequently be manipulated by calling [IEntity::GetGeomCacheRenderNode](/docs/static/engines/cryengine-5/categories/28704770/pages/29797019).

[Example](/docs/static/engines/cryengine-5/categories/28704770/pages/29797019)

### Render Nodes

Low-level Render nodes can be added directly to entities, allowing the dynamic rendering of effects on entities. Keep in mind that all the constructs above are also render nodes, but direct helpers for creating the render node are available to simplify ease of use.

Examples of render nodes that could be attached to entities are: [IRoadRenderNode,](/docs/static/engines/cryengine-5/categories/28704770/pages/29797410) [IDecalRenderNode](/docs/static/engines/cryengine-5/categories/28704770/pages/29797245) and [IWaterVolumeRenderNode](/docs/static/engines/cryengine-5/categories/28704770/pages/29797413), [IRopeRenderNode](/docs). It is also possible to directly query the render node attached to a slot, even in the case of using the helpers above, using [IEntity::GetSlotRenderNode](http://docs.cryengine.com/docs.cryengine.com/display/CPP/IEntity#ac8813fe9d648d258ab5652717a0aa6e2).

Otherwise, render nodes can be applied directly to a specific slot using the [IEntity::SetSlotRenderNode](/docs/static/engines/cryengine-5/categories/28704770/pages/29797019) function.

## Conclusion

That concludes this article on Entity Slots. You may be interested in:

- [Characters and Animations](Characters%20and%20Animations.md)
- [Physics and Movement](Physics%20and%20Movement.md)
