# Lua Scripting

> A lighter-weight scripting option for entity logic, designer-facing
> behavior, and rapid prototyping.

CRYENGINE embeds a **Lua 5** virtual machine exposed through `IScriptSystem`.
Lua is a fully supported scripting layer — you can write entire entity behaviors
in `.lua` files without touching C++. It is gradually being de-emphasized in
favor of C++ components and Schematyc, but remains usable for many scenarios:
designer-facing tweaks, quick prototypes, mission logic, and legacy entity
classes.

This article covers the Lua scripting workflow from the ground up.

---

## 1. When to Use Lua vs C++

| | Lua Script Entity | C++ Component |
|---|---|---|
| **Iteration speed** | Edit `.lua`, reload in editor — no compile | Edit, compile, restart |
| **Performance** | Interpreted, slower for per-frame logic | Native, fast |
| **Editor properties** | `Properties` table in Lua | `AddMember` in `ReflectType` |
| **Network replication** | Limited (via `ServerProperties` table) | Full `NetSerialize` + RMI |
| **Access to engine APIs** | Via ScriptBind functions | Direct C++ API |
| **Best for** | Doors, triggers, mission logic, designer tweaks | Players, weapons, vehicles, performance-critical code |

Many projects use **both**: C++ for performance-critical systems, Lua for
designer-authored entity behaviors. The GameSDK sample is a good reference for
this hybrid approach.

---

## 2. The Script Entity Workflow

A Lua script entity needs:

1. An **`entities.xml` registry** — tells the entity system which Lua entity
   classes exist and which script file each class uses.
2. A **`.lua` file** — implements the entity behavior.

In a Blank-style CRYENGINE 5.7.1 project, put the registry in the asset root:
`Assets/entities.xml`. The entity class registry loads the virtual path
`entities.xml` during startup and reads `<Entity>` children from an `<Entities>`
root.

> source:Code/CryEngine/CryEntitySystem/EntityClassRegistry.cpp:225
> source:Code/CryEngine/CryEntitySystem/EntityClassRegistry.cpp:245-259
> source:Code/CryEngine/CryEntitySystem/EntityClassRegistry.cpp:350-368

### 2.1 The `entities.xml` Registry

Stored as `Assets/entities.xml` in a project whose asset folder is `Assets`:

```xml
<Entities>
  <Entity
    Name="RadarBase"
    Script="Scripts/Entities/Others/RadarBase.lua"
  />
</Entities>
```

| Attribute | Description |
|-----------|-------------|
| `Name` | Name of the Entity class |
| `Script` | Path of the Lua script, relative to the asset search path |
| `Invisible` | Prevents it from being visible in the Sandbox entity list |

You can register multiple Lua entity classes in the same `entities.xml` file.
After editing the registry or Lua scripts, reload scripts or restart Sandbox so
the class registry and script system see the changes.

### 2.2 The `.lua` File

The Lua script consists of one main table which should have the same name as
the entity class. Here is a minimal script entity:

```lua
-- Scripts/Entities/Others/MyDoor.lua

MyDoor = {
    Properties = {
        bOpen = false,
        fOpenSpeed = 2.0,
        sSound = "Sounds/door_open",
        object_Model = "objects/props/door/door.cgf",
    },
    Editor = {
        Model = "%ENGINE%/EngineAssets/Objects/primitive_cube.cgf",
        Icon = "door.bmp",
        IconOnTop = true,
    },
    States = { "Closed", "Opened" },
}
```

The engine parses this table at load time:

- **`Properties`** — exposed in the Sandbox property panel. Each field's type is
  inferred from its name prefix (see §3).
- **`Editor`** — hints for the Sandbox Editor (preview model, icon, ...).
- **`States`** — declares the entity's state machine (see §5).

> source:docs(API Reference/CRYENGINE Game Code/Miscellaneous Game Code/Script Entity/Structure of a Script Entity.md:37-98)

---

## 3. The Properties Table

The `Properties` table is parsed by the Sandbox Editor and provides a UI for
changing entity class parameters. The values are defaults; each instance placed
in a level saves its own values.

```lua
Properties = {
    bRigidBody = 1,
    fHealth = 100,
    iMaxTargets = 5,
    sName = "Default",
    clrTint = { 1, 1, 1 },
    object_Character = "objects/characters/sample/sample.cdf",
    Physics = {
        bRigidBody = 1,
        Mass = 500,
        Density = -1,
    },
},
```

The property name prefix tells the editor what type to use:

| Prefix | Type |
|--------|------|
| `b` | boolean |
| `f` | float |
| `i` | integer |
| `s` | string |
| `clr` | color (table of r, g, b) |
| `object_` | asset reference (CGF, CGA, CHR, or CDF file) |
| `surf_` | surface type |

> source:docs(API Reference/CRYENGINE Game Code/Miscellaneous Game Code/Script Entity/Structure of a Script Entity.md:77-84)

### Special Comments (Slider Hints)

You can add comments behind a numeric variable to give the editor slider bounds:

```lua
Properties = {
    fDamage = 50, --[0, 100, 1, "Damage threshold"]
},
```

This tells the engine:

- The value is limited to 0–100
- The slider step is 1
- "Damage threshold" appears as a tooltip

> source:docs(API Reference/CRYENGINE Game Code/Miscellaneous Game Code/Script Entity/Structure of a Script Entity.md:100-116)

When a property is changed in the editor, the `OnPropertyChange()` callback is
called on the entity (if implemented).

---

## 4. Entity Callbacks

The script entity can include several callback functions called by the engine.
Implementation is optional, but some are expected for correct editor behavior.

### Default State Functions

| Function | When called |
|----------|-------------|
| `OnSpawn` | After the entity was created by the entity system |
| `OnDestroy` | When the entity is destroyed |
| `OnInit` | When the entity gets initialized |
| `OnShutDown` | When the entity is destroyed (same as OnDestroy) |
| `OnReset` | When the editor resets state (enter/leave game mode) |
| `OnPropertyChange` | When the user changes a property in Sandbox |

> source:docs(API Reference/CRYENGINE Engine Code/Engine Modules/CryEntitySystem/Entity System Script Callbacks.md:17-24)

### Script State Functions

| Function | When called |
|----------|-------------|
| `OnBeginState` | During `GotoState()` after the state has just been changed |
| `OnEndState` | During `GotoState()` while the old state is still active |
| `OnUpdate` | Called periodically on the entity's current state (requires `es_UpdateScript` cvar = 1) |
| `OnTimer` | When a timer expires. Params: timerId, period in ms |
| `OnEnterArea` / `OnLeaveArea` | Area trigger events |
| `OnCollision` | When a collision occurs |
| `OnStartGame` | When the game has been started |
| `OnStartLevel` | When a new level has been started |

> source:docs(API Reference/CRYENGINE Engine Code/Engine Modules/CryEntitySystem/Entity System Script Callbacks.md:26-49)

### A Complete Minimal Lua Entity

```lua
-- Scripts/Entities/Others/MyDoor.lua

MyDoor = {
    Properties = {
        object_Model = "objects/props/door/door.cgf",
        bStartsOpen = 0,
        fOpenSpeed = 2.0,
    },
    States = { "Closed", "Opened" },
}

function MyDoor:OnSpawn()
    -- Load the model into slot 0
    self:LoadObject(0, self.Properties.object_Model)
end

function MyDoor:OnInit()
    self:OnReset()
end

function MyDoor:OnReset()
    -- Reset state when entering/leaving game mode
    if self.Properties.bStartsOpen == 1 then
        self:GotoState("Opened")
    else
        self:GotoState("Closed")
    end
end

function MyDoor:OnPropertyChange()
    -- Reload model if it changed
    self:LoadObject(0, self.Properties.object_Model)
end

function MyDoor:OnDestroy()
    -- Cleanup (optional)
end

-- State: Closed
MyDoor.Closed = {
    OnBeginState = function(self)
        System.LogAlways("Door is now closed")
    end,

    OnUpdate = function(self, dt)
        -- Per-frame logic when in Closed state (requires es_UpdateScript=1)
    end,

    OnHit = function(self, hit)
        self:GotoState("Opened")
    end,
}

-- State: Opened
MyDoor.Opened = {
    OnBeginState = function(self)
        System.LogAlways("Door is now open")
    end,
}
```

Key things to notice:

- **`self:LoadObject(slot, filename)`** — loads a 3D model into an entity slot.
  This is a ScriptBind function (see §6).
- **`self:GotoState("Opened")`** — switches the entity to the "Opened" state.
  States must be declared in the `States` table.
- **`System.Log("...")` / `System.LogAlways("...")`** — prints from Lua through
  the engine's `System` script binding. `CryLog` is a C++ logging macro, not a
  Lua global in this 5.7.1 validation project.

---

## 5. Entity States

The entity system provides a simple state switching mechanism for script
entities. Each state consists of:

- A name (string)
- A Lua table within the entity table identified with the state name
- Optional callback functions (`OnBeginState`, `OnEndState`, `OnUpdate`, ...)

All entity states must be **declared** in the entity's main table first:

```lua
AdvancedDoor = {
    Client = {},
    Server = {},
    Properties = { ... },
    States = { "Opened", "Closed", "Destroyed" },
}
```

State logic goes in `Server.<StateName>` or `Client.<StateName>`:

```lua
AdvancedDoor.Server.Opened = {
    OnBeginState = function(self)
        if self.Properties.bUsePortal == 1 then
            System.ActivatePortal(self:GetWorldPos(), 1, self.id)
        end
        self.bUpdate = 1
        self:Play(1)
    end,

    OnUpdate = function(self, dt)
        self:OnUpdate()
    end,
}
```

Transitioning between states uses `GotoState()`:

```lua
function AdvancedDoor:OnReset()
    self:GotoState("Opened")
end
```

Querying the current state uses `GetState()`:

```lua
if self:GetState() == "Opened" then
    -- ...
end
```

> source:docs(API Reference/CRYENGINE Game Code/Miscellaneous Game Code/Script Entity/Using Entity State.md:10-83)

---

## 6. ScriptBind — Calling C++ from Lua

The engine exposes a large set of C++ functions to Lua via **ScriptBind** classes.
Each ScriptBind registers a global table (e.g. `Entity`, `System`, `Sound`,
`Physics`, ...) whose methods call into C++.

### The `Entity` ScriptBind

The most commonly used ScriptBind. Accessible via `self:` inside an entity
script (since the entity's script table *is* the `Entity` table). Examples:

```lua
-- Geometry
self:LoadObject(0, "objects/props/door/door.cgf")
self:LoadCharacter(0, "objects/characters/sample/sample.cdf")

-- Transform
self:SetPos(Vec3(0, 0, 10))
local pos = self:GetPos()
self:SetAngles(Ang3(0, 0, 90))
local ang = self:GetAngles()

-- Physics
self:Physicalize(0, PE_RIGID, physicsParams)
self:AwakePhysics(1)
self:DestroyPhysics()

-- Slots
self:DrawSlot(0, 1)   -- enable rendering of slot 0
self:FreeSlot(0)      -- free slot 0

-- Name / flags
self:SetName("MyDoor")
local name = self:GetName()
```

> source:Code/CryEngine/CryEntitySystem/ScriptBind_Entity.cpp:76-213 (registration calls)
> source:docs(API Reference/CRYENGINE API Reference/ScriptBind Reference/CRYENGINE Functions/ScriptBind_Entity.md)

### The `System` ScriptBind

Global engine functions:

```lua
System.GetEntityByName("Player1")
System.GetEntity(entityId)
System.GetEntitiesByClass("MyDoor")
System.Log("Hello from Lua!")
System.LogAlways("Always visible Lua message")
System.ExecuteCommand("map example s")
System.GetFrameTime()
System.GetCurrTime()
```

Use `System.Log(...)` or `System.LogAlways(...)` for Lua logging. `CryLog(...)`
is a C++ logging macro; it is not a Lua global in a Blank-style project.

> source:Code/CryEngine/CryScriptSystem/ScriptBindings/ScriptBind_System.cpp:162-165
> source:Code/CryEngine/CryScriptSystem/ScriptBindings/ScriptBind_System.cpp:393-404
> source:Code/CryEngine/CryScriptSystem/ScriptBindings/ScriptBind_System.cpp:460-466

### Other ScriptBinds

| ScriptBind | Global table | Purpose |
|------------|-------------|---------|
| `ScriptBind_AI` | `AI` | AI queries, goal pipes, smart objects |
| `ScriptBind_Sound` | `Sound` | Play/stop sounds |
| `ScriptBind_Physics` | `Physics` | Ray casting, world queries |
| `ScriptBind_Particle` | `Particle` | Spawn particle effects |
| `ScriptBind_Movie` | `Movie` | Trackview control |
| `ScriptBind_GameToken` | `GameToken` | Read/write game tokens |

Full reference: [ScriptBind Reference](../../API%20Reference/CRYENGINE%20API%20Reference/ScriptBind%20Reference/CRYENGINE%20Functions.md)

---

## 7. Calling Lua from C++

If your C++ code needs to call a Lua function, use `IScriptSystem`:

```cpp
IScriptSystem* pSS = gEnv->pScriptSystem;

// Call a global function: MyGlobalFunc(42, "hello")
pSS->BeginCall("MyGlobalFunc");
pSS->PushParam(42);
pSS->PushParam("hello");
bool ok = pSS->EndCall();

// Call a method on a table: MyTable:MyMethod(42)
pSS->BeginCall("MyTable", "MyMethod");
pSS->PushParam(42);
bool ok2 = pSS->EndCall();
```
> source:Code/CryEngine/CryCommon/CryScriptSystem/IScriptSystem.h:407-431

To get a script table (e.g. the entity's script table from C++):

```cpp
IScriptTable* pScriptTable = pEntity->GetScriptTable();
// Read a value
ScriptAnyValue val;
pScriptTable->GetValueAny("fHealth", val);
```
> source:Code/CryEngine/CryCommon/CryEntitySystem/IEntityComponent.h:613

---

## 8. Exposing C++ Functions to Lua (ScriptBind)

To expose your own C++ functions to Lua, derive from `CScriptableBase`:

```cpp
class CScriptBind_Game : public CScriptableBase
{
public:
    CScriptBind_Game(ISystem* pSystem)
    {
        Init(pSystem->GetIScriptSystem(), pSystem);
        SetGlobalName("Game");

        #undef SCRIPT_REG_CLASSNAME
        #define SCRIPT_REG_CLASSNAME &CScriptBind_Game::
        SCRIPT_REG_TEMPLFUNC(GameLog, "text");
    }

    int GameLog(IFunctionHandler* pH, char* pText)
    {
        CryLog("[Game] %s", pText);
        return pH->EndFunction();
    }
};
```

From Lua, this is accessible as:

```lua
Game.GameLog("a message")
```
> source:Code/CryEngine/CryCommon/CryScriptSystem/IScriptSystem.h:1190-1259
> source:docs(API Reference/CRYENGINE Engine Code/Engine Modules/CryScriptSystem/Lua Scripting/Integrations Between Lua and C++.md:26-72)

Key registration macros:

| Macro | Purpose |
|-------|---------|
| `SCRIPT_REG_FUNC(Name)` | Register a no-argument function |
| `SCRIPT_REG_TEMPLFUNC(Name, "params")` | Register a templated function with param hint string |

The param hint string (e.g. `"nSlot,sFilename"`) documents the parameter names
and is shown in the editor's autocomplete.

---

## 9. Enabling Script Update

By default, script entities do **not** receive `OnUpdate` calls. You must either:

1. Set the console variable `es_UpdateScript` to `1`, OR
2. Call `EnableScriptUpdate(true)` on the entity's `IEntityScriptComponent` from C++:

```cpp
if (auto* pScriptComponent = pEntity->GetComponent<IEntityScriptComponent>())
{
    pScriptComponent->EnableScriptUpdate(true);
    pScriptComponent->SetScriptUpdateRate(0.0f);  // every frame
}
```
> source:Code/CryEngine/CryCommon/CryEntitySystem/IEntityComponent.h:661
> source:Code/CryEngine/CryCommon/CryEntitySystem/IEntityComponent.h:612

`SetScriptUpdateRate(0.0f)` means "update every frame". A non-zero value means
"update every N seconds" (e.g. `0.5f` = twice per second).

---

## 10. Common Utility Functions

The engine ships a set of Lua utility functions in `Scripts/Utils/EntityUtils.lua`.
The most useful:

| Function | Purpose |
|----------|---------|
| `MakeDerivedEntity(child, parent)` | Inherit from another entity script |
| `MakeUsable(entity)` | Add `OnUsed` event support |
| `MakePickable(entity)` | Add pickable behavior |
| `MakeSpawnable(entity)` | Add spawn-from-archetype support |
| `BroadcastEvent(sender, "EventName")` | Broadcast a string event to linked entities |
| `EntityCommon.PhysicalizeRigid(entity, slot, params)` | Standard rigid body physicalization |

> source:docs(API Reference/CRYENGINE Engine Code/Engine Modules/CryScriptSystem/Lua Scripting/Common Lua Functions/EntityUtils Lua.md)

---

## 11. A Lua-Driven Spawner Example

This entity listens for a timer and spawns another entity periodically:

```lua
-- Scripts/Entities/Others/Spawner.lua

Spawner = {
    Properties = {
        sEntityClass = "MyBullet",
        fInterval = 2.0, --[0.1, 60, 0.1, "Spawn interval in seconds"]
        iMaxSpawns = 10,
    },
}

function Spawner:OnSpawn()
    self.spawnedCount = 0
end

function Spawner:OnInit()
    self:OnReset()
end

function Spawner:OnReset()
    self.spawnedCount = 0
    -- Start a repeating timer (id=1, period in ms)
    self:SetTimer(1, self.Properties.fInterval * 1000)
end

function Spawner:OnTimer(timerId, ms)
    if timerId == 1 and self.spawnedCount < self.Properties.iMaxSpawns then
        -- Spawn at this entity's position
        local pos = self:GetWorldPos()
        local spawned = System.SpawnEntity({
            class = self.Properties.sEntityClass,
            pos = pos,
            name = "Spawned_" .. self.spawnedCount,
        })
        self.spawnedCount = self.spawnedCount + 1
        System.LogAlways("Spawned entity #" .. self.spawnedCount)

        -- Repeat
        self:SetTimer(1, self.Properties.fInterval * 1000)
    end
end

function Spawner:OnDestroy()
    self:KillTimer(1)
end
```

Corresponding `Assets/entities.xml` entry:

```xml
<Entities>
  <Entity
    Name="Spawner"
    Script="Scripts/Entities/Others/Spawner.lua"
  />
</Entities>
```

---

## 12. IScriptSystem API Reference

The core script system interface:

| Method | Purpose |
|--------|---------|
| `ExecuteFile(path)` | Load and run a `.lua` file source:Code/CryEngine/CryCommon/CryScriptSystem/IScriptSystem.h:370 |
| `ExecuteBuffer(buf, size)` | Execute a Lua string source:Code/CryEngine/CryCommon/CryScriptSystem/IScriptSystem.h:378 |
| `ReloadScript(path)` | Reload a script at runtime source:Code/CryEngine/CryCommon/CryScriptSystem/IScriptSystem.h:394 |
| `ReloadScripts()` | Reload all loaded scripts source:Code/CryEngine/CryCommon/CryScriptSystem/IScriptSystem.h:398 |
| `UnloadScript(path)` | Unload a script source:Code/CryEngine/CryCommon/CryScriptSystem/IScriptSystem.h:384 |
| `CreateTable()` | Create a new Lua table source:Code/CryEngine/CryCommon/CryScriptSystem/IScriptSystem.h:405 |
| `BeginCall(table, func)` | Start calling a Lua function source:Code/CryEngine/CryCommon/CryScriptSystem/IScriptSystem.h:417-424 |
| `EndCall()` | Finish the call source:Code/CryEngine/CryCommon/CryScriptSystem/IScriptSystem.h:427 |
| `SetGlobalValue(name, value)` | Set a global Lua variable |
| `GetGlobalValue(name)` | Get a global Lua variable |

---

## 13. Migrating from Lua to C++

If you are porting a Lua script entity to a C++ component:

| Lua concept | C++ equivalent |
|-------------|----------------|
| `entities.xml` + `.lua` file | `IEntityComponent` subclass with `ReflectType` |
| `Properties` table | `AddMember` in `ReflectType` |
| `OnSpawn` / `OnInit` | `Initialize()` |
| `OnUpdate` | `ProcessEvent` with `EEvent::Update` |
| `OnReset` | `ProcessEvent` with `EEvent::Reset` |
| `OnPropertyChange` | `ProcessEvent` with `EEvent::EditorPropertyChanged` |
| `OnCollision` | `ProcessEvent` with `EEvent::PhysicsCollision` |
| `GotoState("Name")` | Custom state machine in your component (no built-in equivalent) |
| `self:LoadObject(slot, path)` | `m_pEntity->LoadGeometry(slot, path)` |
| `self:SetPos(v)` | `m_pEntity->SetPos(v)` |
| `self:Physicalize(...)` | `m_pEntity->Physicalize(params)` |
| ScriptBind functions | Direct C++ API calls |

The C++ component version will be faster (no interpreter overhead), support
full network replication, and appear in the Sandbox "Add Component" menu with
Schematyc. Lua remains useful for the designer-facing, hot-reloadable layer.

---

## Next

- [Examples](Examples.md) — C++ component examples for comparison
- [Schematyc Guide](Schematyc%20Guide.md) — the C++ property system that
  replaces the Lua Properties table
- [ScriptBind Reference](../../API%20Reference/CRYENGINE%20API%20Reference/ScriptBind%20Reference/CRYENGINE%20Functions.md)
- [Structure of a Script Entity](../../API%20Reference/CRYENGINE%20Game%20Code/Miscellaneous%20Game%20Code/Script%20Entity/Structure%20of%20a%20Script%20Entity.md)
- [Entity System Script Callbacks](../../API%20Reference/CRYENGINE%20Engine%20Code/Engine%20Modules/CryEntitySystem/Entity%20System%20Script%20Callbacks.md)
- [Integrations Between Lua and C++](../../API%20Reference/CRYENGINE%20Engine%20Code/Engine%20Modules/CryScriptSystem/Lua%20Scripting/Integrations%20Between%20Lua%20and%20C%2B%2B.md)
