# Using the Entity Slots

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/23306595
- Page ID: 23306595
- Breadcrumb: CRYENGINE Game Code > Miscellaneous Game Code > Script Entity > Using the Entity Slots
- Parent: Script Entity

## Content

### Overview

Each entity can have slots which are used to hold different resources available in CryENGINE.

### Usage

#### Allocating a Slot

The following table list all the different resources which can be allocated in a slot along with the ScriptBind function which allocates it.

**CryENGINE Resource** | **Function**
--- | ---
**static geometry** | LoadObject() or LoadSubObject()
**animated character** | LoadCharacter()
**particle emitter** | LoadParticleEffect()
**light** | LoadLight()
**cloud** | LoadCloud()
**fog** | LoadFogVolume()
**volume** | LoadVolumeObject()

#### Modifying Slot Parameters

Each one of these resource may be moved, rotated or scaled related to the entity itself.

- SetSlotPos()
- GetSlotPos()
- SetSlotAngles()
- GetSlotAngles()
- SetSlotScale()
- GetSlotScale()

It's possible to add parenting link between the slots, making it possible to have related positions.

- SetParentSlot()
- GetParentSlot()

#### Slot Management

It is possible to determine if a specified slot is allocated by calling!IsSlotValid().

Additionally, it's possible either to free one slot by calling!FreeSlot() or to free all allocated slot within the entity by calling!FreeAllSlots().

#### Example of Loading a Slot in a Script Function

```
local pos={x=0,y=0,z=0};
self:LoadObject(0,props.fileModel);
self:SetSlotPos(0,pos);
self:SetCurrentSlot(0);
```
