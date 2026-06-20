# EntityUtils Lua

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/23306627
- Page ID: 23306627
- Breadcrumb: CRYENGINE Engine Code > Engine Modules > CryScriptSystem > Lua Scripting > Common Lua Functions > EntityUtils Lua
- Parent: Common Lua Functions

## Content

### Entity utility functions

Commonly used Entity utility functions.

- File location: `Game/Scripts/Utils/EntityUtils.lua`
- Loaded from: `Game/Scripts/common.lua`

### Functions

- [#DumpEntities](EntityUtils%20Lua.md#EntityUtilsLua-DumpEntities)
- [#CompareEntitiesByName](EntityUtils%20Lua.md#EntityUtilsLua-CompareEntitiesByName)
- [#CompareEntitiesByDistanceFromPoint](EntityUtils%20Lua.md#EntityUtilsLua-CompareEntitiesByDistanceFromPoint)
- [#BroadcastEvent](EntityUtils%20Lua.md#EntityUtilsLua-BroadcastEvent)
- [#MakeDerivedEntity](EntityUtils%20Lua.md#EntityUtilsLua-MakeDerivedEntity)
- [#MakeDerivedEntityOverride](EntityUtils%20Lua.md#EntityUtilsLua-MakeDerivedEntityOverride)
- [#MakeUsable](EntityUtils%20Lua.md#EntityUtilsLua-MakeUsable)
- [#MakePickable](EntityUtils%20Lua.md#EntityUtilsLua-MakePickable)
- [#MakeSpawnable](EntityUtils%20Lua.md#EntityUtilsLua-MakeSpawnable)
- [#EntityCommon.PhysicalizeRigid](EntityUtils%20Lua.md#EntityUtilsLua-EntityCommon.PhysicalizeRigid)

#### DumpEntities()

Dumps all entity identifiers (**EntityId**), names, classes, positions and angles, which are currently used in the map, to console. e.g:

```
[userdata: 00000002]..name=Grunt1 clsid=Grunt pos=1016.755,1042.764,100.000 ang=0.000,0.000,1.500
[userdata: 00000003]..name=Grunt2 clsid=Grunt pos=1020.755,1072.784,100.000 ang=0.000,0.000,0.500
...
```

#### CompareEntitiesByName(ent1, ent2)

Compares two entities by name, which is commonly used while sorting tables.

**Parameters** | **Description**
--- | ---
ent1 | first entity table
ent2 | second entity table

##### Example:

```
local entities = System.GetEntitiesByClass("SomeEntityClass");
table.sort(entities, CompareEntitiesByName);
```

#### CompareEntitiesByDistanceFromPoint(ent1, ent2, point)

Compares two entities by their squared distance. If the distance to the point from entity one is greater than the distance to the point from entity two it returns **true**, otherwise it returns ** false**.

**Parameters** | **Description**
--- | ---
ent1 | first entity table
ent2 | second entity table
point | 3D position vector

##### Example:

```
local ent1 = System.GetEntityByName("NameEntityOne");
local ent2 = System.GetEntityByName("NameEntityTwo");

if(CompareEntitiesByDistanceFromPoint( ent1, ent2, g_localActor:GetPos()))then
Log("Entity One is further away from the Player than Entity two...");
end
```

#### BroadcastEvent(sender, event)

Processes an entity event broadcast.

**Parameters** | **Description**
--- | ---
sender | the entity which originally sent the event
event | string based entity event to process

##### Example:

```
BroadcastEvent(self, "Used");
```

#### MakeDerivedEntity(_DerivedClass, _Parent)

Creates a new table that is a derived version of a parent entity table. Commonly used to simplify the creation of a new entity script based on another entity.

**Parameters** | **Description**
--- | ---
_DerivedClass | derived class table
_Parent | parent or base class table

#### MakeDerivedEntityOverride(_DerivedClass, _Parent)

Creates a new table that is derived class of parent entity. The Child's Properties will override the ones from the parent.

**Parameters** | **Description**
--- | ---
_DerivedClass | derived class table
_Parent | parent or base class table

#### MakeUsable(entity)

Adds usable functionality, like **OnUsed** event, to a given entity table.

**Parameters** | **Description**
--- | ---
entity | entity table

##### Example:

```
MyEntity = { ... whatever you usually put here ... }

MakeUsable(MyEntity)

function MyEntity:OnSpawn() ...

function MyEntity:OnReset()
self:ResetOnUsed()
...
end
```

#### MakePickable(entity)

Adds a **bPickable** property to the entity properties table to add a basic pickable functionality to a given entity.

**Parameters** | **Description**
--- | ---
entity | entity table

#### MakeSpawnable(entity)

Adds spawn functionality to a given entity. Commonly used for **AI** actors during the creation.

**Parameters** | **Description**
--- | ---
entity | entity table

#### EntityCommon.PhysicalizeRigid(entity, nSlot, Properties, bActive)

Physicalizes an entity based on the given entity slot and physics properties.

**Parameters** | **Description**
--- | ---
entity | entity table
nSlot | entity slot you want to physicalize
Properties | physics properties table
bActive | not used
