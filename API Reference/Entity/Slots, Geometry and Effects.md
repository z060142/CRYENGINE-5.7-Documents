# Slots, Geometry and Effects

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/26216230
- Page ID: 26216230
- Breadcrumb: Entity > Slots, Geometry and Effects
- Parent: Entity

## Content

##
Overview

##
Table of Contents

[#slot-transformation](
Slot Transformation
)
[#slot-material](
Slot Material
)
[#slot-flags](
Slot Flags
)
[#slot-types](
Slot Types
)
[#conclusion](
Conclusion
)

##
Slot Transformation

Each slot is assigned a local transformation, in relation to its parent. This allows for offsetting the slot geometry from the entity it is attached to, and is especially useful when dealing with multiple slots in one entity.

Function name
 |
Description
 |

[/docs/static/engines/cryengine-5/categories/28704770/pages/29797019](
IEntity::GetSlotWorldTM
)
 |
Gets the transformation of the slot in world coordinates.
 |

[http://docs.cryengine.com/docs.cryengine.com/display/CPP/IEntity#a74dd2bc8ff7354f070bc3dcf8249b1c4](
IEntity::GetSlotLocalTM
)
 |
Gets the transformation of the slot in relation to its parent.
 |

[http://docs.cryengine.com/docs.cryengine.com/display/CPP/IEntity#a74dd2bc8ff7354f070bc3dcf8249b1c4](
IEntity::SetSlotLocalTM
)
 |
Sets the relative transformation of the slot.
 |

##
Camera-Space Rendering

Camera space rendering allows for drawing an entity slot in the Camera's local space - always making it relative to the camera, and avoiding that other objects are on top. This is most commonly used for first person shooter weaponry and hands.

This is achieved by setting the
ENTITY_SLOT_RENDER_NEAREST flag instead of
ENTITY_SLOT_RENDER, and then setting the camera-space relative position of the object:

Function name
 |
Description
 |

[/docs/static/engines/cryengine-5/categories/28704770/pages/29797019](
IEntity::SetSlotCameraSpacePos
)
 |
Sets the camera space position of the slot, used when the ENTITY_SLOT_RENDER_NEAREST is applied to the slot.
 |

[/docs/static/engines/cryengine-5/categories/28704770/pages/29797019](
IEntity::GetSlotCameraSpacePos
)
 |
Gets the camera space position of the slot, used when the ENTITY_SLOT_RENDER_NEAREST is applied to the slot.
 |

##
Slot Material

By default, a slot contains a null material - resulting in the rendered form of a slot using the default material for the object assigned to it. However, it is often useful to override the material of the slot, allowing custom effects on individual entity geometry.

This can be achieved with the
[/docs/static/engines/cryengine-5/categories/28704770/pages/29797019](
IEntity::GetSlotMaterial
)
and
[/docs/static/engines/cryengine-5/categories/28704770/pages/29797019](
IEntity::SetSlotMaterial
)
 functions.

##
Slot Flags

The
EEntitySlotFlags
 enum can be used to change the behavior of individual slots, for example to disable rendering entirely - something that can be useful when a slot is only meant for physical interaction.

Function name
 |
Description
 |

[/docs/static/engines/cryengine-5/categories/28704770/pages/29797019](
IEntity:;SetSlotFlags
)
 |
Used to set the flags for this slot, note that this completely overrides the flags.
 |

[/docs/static/engines/cryengine-5/categories/28704770/pages/29797019](
IEntity::GetSlotFlags
)
 |
Retrieves the specified slot's flags.
 |

The currently available slot flags are:

Flag name
 |
Description
 |

ENTITY_SLOT_RENDER
 |
Set by default. If cleared, the entity will no longer be rendered to the screen.
 |

ENTITY_SLOT_RENDER_NEAREST
 |
If set, the entity will be rendered in camera space. See
[http://docs.cryengine.com/docs.cryengine.com/display/CPP/IEntity#a1d7674dea67ef282c6d991e0d7f313ed](
IEntity::SetSlotCameraSpacePos
)
 and
[http://docs.cryengine.com/docs.cryengine.com/display/CPP/IEntity#ac8f480ecdb92b1030c48d110227f04a2](
IEntity::GetSlotCameraSpacePos
)
.
 |

ENTITY_SLOT_CAST_SHADOW
 |
If set, the entity slot will cast a shadow.
 |

##
Slot Types

There are several types of objects that can be applied to an entity slot:

##
Characters

Interaction with characters on an entity is limited to:

Function name
 |
Description
 |

[/docs/static/engines/cryengine-5/categories/28704770/pages/29797019](
IEntity::GetCharacter
)
 |
Retrieves the character instance at the specified slot, if any.
 |

[/docs/static/engines/cryengine-5/categories/28704770/pages/29797019](
IEntity::SetCharacter
)
 |
Applies an existing character instance (.CDF, .CHR, .CGA) to the specified slot.
 |

[/docs/static/engines/cryengine-5/categories/28704770/pages/29797019](
IEntity::LoadCharacter
)
 |
Loads specified character from disk and applies it to the specified slot.
 |

For more information on characters, and how to approach animating them, see
[/docs/static/engines/cryengine-5/categories/23756813/pages/26216226](
Characters and Animations
)
.

[/docs/static/engines/cryengine-5/categories/28704770/pages/29797019](
Example
)

##
Static Geometry

Static geometry is represented by the CGF format, and is known in code as
[/docs/static/engines/cryengine-5/categories/28704770/pages/29797103](
IStatObj
)
.

Interaction with static geometry on an entity is limited to:

Function name
 |
Description
 |

[/docs/static/engines/cryengine-5/categories/28704770/pages/29797019](
IEntity::GetStatObj
)
 |
Retrieves the static geometry at the specified slot, if any.
 |

[/docs/static/engines/cryengine-5/categories/28704770/pages/29797019](
IEntity::SetStatObj
)
 |
Applies the specified static geometry (.CGF) to the specified slot.
 |

[/docs/static/engines/cryengine-5/categories/28704770/pages/29797019](
IEntity::LoadGeometry
)
 |
Loads specified static geometry (.CGF) from disk and applies it to the specified slot.
 |

[/docs/static/engines/cryengine-5/categories/28704770/pages/29797019](
Example
)

##
Particle Emitters

Particles can be loaded into
**
emitters
**
, a construct that will continuously emit effects from a point. When assigned to an entity, a particle emitter will follow an entity and thus allow creating very complex effects with ease. Emitters are represented in code by the
[/docs/static/engines/cryengine-5/categories/28704770/pages/29797113](
IParticleEmitter
)
 interface, while the underlying particle effect (.pfx, .pfx2) is known in code as
[/docs/static/engines/cryengine-5/categories/28704770/pages/29797112](
IParticleEffect
)
.

Interaction with particle emitters on an entity is limited to:

Function name
 |
Description
 |

[/docs/static/engines/cryengine-5/categories/28704770/pages/29797019](
IEntity::GetParticleEmitter
)
 |
Retrieves the particle emitter at the specified slot, if any.
 |

[/docs/static/engines/cryengine-5/categories/28704770/pages/29797019](
IEntity::SetParticleEmitter
)
 |
Applies the specified particle emitter to the specified slot.
 |

[/docs/static/engines/cryengine-5/categories/28704770/pages/29797019](
IEntity::LoadParticleEmitter
)
 |
Creates an emitter in the specified slot out of the specified effect.
 |

[/docs/static/engines/cryengine-5/categories/28704770/pages/29797019](
Example
)

##
Lights

Very often useful, lights can be loaded into entities to create dynamic light sources that can move around the level at run-time. This is useful to create entities that provide point lights, projected lights or even environment probes.

Lights are loaded into entity slots using the
[/docs/static/engines/cryengine-5/categories/28704770/pages/29797019](
IEntity::LoadLight
)
 function, with the accompanying
CDLight
 structure defining the behavior of the light. This allows for creating point lights, projector lights and environment probes. An example is available
[/docs/static/engines/cryengine-5/categories/28704770/pages/29797019](
here
)
.

[/docs/static/engines/cryengine-5/categories/28704770/pages/29797019](
Example
)

##
Fog Volume

Entities can also load fog volumes into slots, allowing the use of dynamic fog effects around logical entities.

Fog volumes can be loaded into entity slots using the
[/docs/static/engines/cryengine-5/categories/28704770/pages/29797019](
IEntity::LoadFogVolume
)
 function, with the accompanying
SFogVolumeProperties
 structure defining the behavior of the volume.

[/docs/static/engines/cryengine-5/categories/28704770/pages/29797019](
Example
)

##
Geom Cache / Alembic

Geom Caches can be loaded into entities, allowing the playback of arbitrarily animated geometry. This can allow for complex destruction, complicated cloth motion and other special effects that would otherwise be too expensive to calculate in real-time.

Geom Cache can be loaded into entity slots using the
[/docs/static/engines/cryengine-5/categories/28704770/pages/29797019](
IEntity::LoadGeomCache
)
 function, and can subsequently be manipulated by calling
[/docs/static/engines/cryengine-5/categories/28704770/pages/29797019](
IEntity::GetGeomCacheRenderNode
)
.

[/docs/static/engines/cryengine-5/categories/28704770/pages/29797019](
Example
)

##
Render Nodes

Low-level Render nodes can be added directly to entities, allowing the dynamic rendering of effects on entities. Keep in mind that all the constructs above are also render nodes, but direct helpers for creating the render node are available to simplify ease of use.

Examples of render nodes that could be attached to entities are:
[/docs/static/engines/cryengine-5/categories/28704770/pages/29797410](
IRoadRenderNode,
)

[/docs/static/engines/cryengine-5/categories/28704770/pages/29797245](
IDecalRenderNode
)
 and
[/docs/static/engines/cryengine-5/categories/28704770/pages/29797413](
IWaterVolumeRenderNode
)
,
[/docs](
IRopeRenderNode
)
. It is also possible to directly query the render node attached to a slot, even in the case of using the helpers above, using
[http://docs.cryengine.com/docs.cryengine.com/display/CPP/IEntity#ac8813fe9d648d258ab5652717a0aa6e2](
IEntity::GetSlotRenderNode
)
.

Otherwise, render nodes can be applied directly to a specific slot using the
[/docs/static/engines/cryengine-5/categories/28704770/pages/29797019](
IEntity::SetSlotRenderNode
)
 function.

##
Conclusion

That concludes this article on Entity Slots. You may be interested in:

-
[/docs/static/engines/cryengine-5/categories/23756813/pages/26216226](
Characters and Animations
)

-
[/docs/static/engines/cryengine-5/categories/23756813/pages/26216224](
Physics and Movement
)
