# Getting Started

> **Audience:** You can write C++, you have opened the Sandbox Editor once or
> twice, but you have no idea *where to put your code* in a CRYENGINE project.
> This article walks you from zero to a buildable game plugin.

> **Conventions:**
> - `source:<path relative to the engine root>:<line>` citations point at the
>   exact line in the CRYENGINE source tree. Unverified claims are tagged `[unverified]`.
> - "GameTemplate" refers to the C++ project templates shipped in
>   `Code/GameTemplates/cpp/` of the engine source.

---

## 1. Mental Model — How CRYENGINE Loads Your Game

CRYENGINE itself is a set of DLLs (`CrySystem.dll`, `CryAction.dll`,
`CryEntitySystem.dll`, ...). Your game is **just another DLL** loaded by the
engine at startup. The engine finds your DLL through the project file
(`*.cryproject`) and treats it as a **plugin**.

The modern (5.3+) entry point for a game plugin is `Cry::IEnginePlugin`:

> Plug-ins are loaded from JSON in your `.cryproject` file on engine startup.
> For a fully functional example, see `Code\GameTemplates\cpp\Plugin`.
> source:Code/CryEngine/CryCommon/CrySystem/ICryPlugin.h:14-16

The legacy `IGameStartup` / `IGame` entry point is **deprecated** since v5.3:

> `IGame`, `IEditorGame` and `IGameStartup` have been replaced by `ICryPlugin`
> and will be removed in a future update.
> source:Code/CryEngine/CryCommon/CryGame/IGame.h:28

### 1.1 The Three-Step Loading Flow

```
1. Launcher reads Game.cryproject
     → sees "plugins": [ { "type": "EPluginType::Native", "path": "bin/win_x64/Game.dll" } ]
     → loads your DLL

2. Your DLL runs its CRYREGISTER_SINGLETON_CLASS macro
     → registers your plugin class with the engine factory
     → engine creates the singleton instance

3. Engine calls plugin->Initialize(env, initParams)
     → you register for system events (ESYSTEM_EVENT_REGISTER_SCHEMATYC_ENV, ESYSTEM_EVENT_GAME_POST_INIT, ...)
     → later, engine fires those events → you register Schematyc components, spawn player, etc.
```

Every step above is demonstrated in the templates. The smallest possible plugin
is `Code/GameTemplates/cpp/Plugin/Code/Plugin.cpp` (~59 lines).

---

## 2. Starting a New Project — Use a GameTemplate

Do **not** hand-write a project from scratch. Copy a GameTemplate. The engine
ships these C++ templates in `Code/GameTemplates/cpp/`:

| Template | What it shows | Good for |
|----------|---------------|----------|
| `Blank` | Bare-minimum game plugin + a player that flies around with WASD | First custom project |
| `Plugin` | A reusable library plugin (no game logic, just registers components) | Building shared features |
| `TopDownShooter` | Player, SpawnPoint, Bullet, CharacterController, shooting | Top-down / twin-stick games |
| `FirstPersonShooter` | FPS-style player with camera + animation | FPS prototypes |
| `ThirdPersonShooter` | Third-person camera + mannequin animation | TPS prototypes |
| `Sidescroller` | 2.5D side-scroller player | Sidescrollers |
| `RollingBall` | Physics-driven rolling ball | Physics toy projects |
| `IsometricPathfinding` | Isometric camera + navigation/AI | RPG / strategy prototypes |
> source:Code/GameTemplates/cpp/ (directory listing)

### 2.1 Copying a Template

1. Close the Sandbox Editor and the engine.
2. Duplicate, say, `Code/GameTemplates/cpp/Blank/` to `<YourProject>/`.
3. Rename `Game.cryproject` → `MyGame.cryproject` (optional but clearer).
4. Open the `.cryproject` in a text editor and change:
   - `info.name` → `"MyGame"`
   - `info.guid` → a freshly generated GUID (use **Tools → Create GUID** in
     Visual Studio, Registry Format)
5. In `Code/GamePlugin.h`, update the class name and the GUID in
   `CRYGENERATE_SINGLETONCLASS_GUID` to match a **new** unique GUID.
6. Generate the solution with the engine's CMake pipeline (see the
   `README.md` in the engine root, source:CMakeLists.txt) and build.

That's it — you now have a buildable game plugin. Launch it with the engine
Launcher pointed at your `.cryproject`.

> **Tip:** The engine's CMake-based project generator reads your `.cryproject`
> and produces a Visual Studio solution. The GameTemplate's `Code/` folder is
> the source root; the output DLL lands in `bin/win_x64/` next to the project.

---

## 3. The `.cryproject` File

The `.cryproject` is a JSON manifest. The most important fields, with a real
example taken from the Blank template:

```json
{
    "version": 3,
    "info": { "name": "Blank", "guid": "cf957e42-2f59-03e6-d8cf-b05b3f1ee178" },
    "content": {
        "assets": [ "Assets" ],
        "code":   [ "Code" ],
        "libs":   [ { "name": "Blank", "shared": { "any": "", "win_x64": "", "win_x86": "" } } ]
    },
    "require": {
        "engine": "engine-5.7",
        "plugins": [
            { "type": "EPluginType::Native", "path": "CryDefaultEntities" },
            { "type": "EType::Native",        "path": "CryScaleformSchematyc" },
            { "type": "EPluginType::Native", "path": "CrySensorSystem" },
            { "type": "EPluginType::Native", "path": "CryPerceptionSystem" },
            { "type": "EPluginType::Native", "path": "bin/win_x64/Game.dll" },
            { "type": "EPluginType::Native", "path": "CryGamePlatform", "platforms": [ "PS4" ] }
        ]
    },
    "console_variables": { "sys_target_platforms": "pc,ps4,xboxone,linux" },
    "console_commands": {}
}
```
> source:Code/GameTemplates/cpp/Blank/Game.cryproject:1-62

Field-by-field:

| Field | Meaning |
|-------|---------|
| `info.name` | Project display name |
| `info.guid` | Project GUID — unique per project, never reuse |
| `content.assets` | Folders searched for game assets (.cgf, .cdf, textures, ...) |
| `content.code` | Folders containing C++ source (used by the CMake generator) |
| `content.libs[].name` | Output library/DLL name (must match what `CMakeLists.txt` builds) |
| `content.libs[].shared` | Per-platform output paths (empty = default `bin/<platform>/`) |
| `require.engine` | Engine version this project targets |
| `require.plugins[]` | Other plugins to load before yours |
| `require.plugins[].type` | `EPluginType::Native` (C++) or `Managed` (C#). Note `EType::Native` is an older alias still accepted. source:Code/CryEngine/CryCommon/CrySystem/ICryPluginManager.h:17-33 |
| `require.plugins[].path` | Either a known engine plugin name (`CryDefaultEntities`) or a relative DLL path (`bin/win_x64/Game.dll`, `bin/win_x64/MyPlugin.dll`, ...) |
| `require.plugins[].platforms` | Optional platform filter (`"PS4"`, `"PC"`, ...) |
| `console_variables` | Console vars to set at startup |
| `console_commands` | Console commands to run at startup |

The single most important entry for a Blank C++ template project is usually the
**last** plugin in the list -- the template's own game DLL
(`bin/win_x64/Game.dll`). `Game.dll` is only the default template name, not a
special engine requirement. A project can list additional native plugin DLLs in
`require.plugins` as long as each DLL exports a valid `Cry::IEnginePlugin`
implementation. The engine loads every listed plugin, in order, and each
plugin's `Initialize` runs after the engine plugins it depends on.

> **Common pitfall:** If your component does not appear in the editor's
> "Add Component" menu, check the whole registration chain: the game DLL path
> in `.cryproject`, required engine plugins such as `CryDefaultEntities`, the
> plugin's `ESYSTEM_EVENT_REGISTER_SCHEMATYC_ENV` / `RegisterPackage` path, and
> the component's `CRY_STATIC_AUTO_REGISTER_FUNCTION` registration.

### Startup Checklist

Required:

- The `.cryproject` must point at each DLL that actually exists on disk, e.g.
  `bin/win_x64/Game.dll` for the Blank template or
  `bin/win_x64/MyPlugin.dll` for an additional native plugin.
- Engine plugins used by your project must be listed in `require.plugins`;
  `CryDefaultEntities` is required for the stock component set used by the
  Blank template.
- Your plugin must listen for `ESYSTEM_EVENT_REGISTER_SCHEMATYC_ENV` and call
  `gEnv->pSchematyc->GetEnvRegistry().RegisterPackage(...)`.
- Each component that should appear in Sandbox must have both `ReflectType` and
  a `CRY_STATIC_AUTO_REGISTER_FUNCTION` registration callback.

Avoid:

- Do not treat "DLL loaded" as proof that components are registered. Plugin
  loading, Schematyc package registration, and Add Component menu population are
  separate steps.
- Do not assume Blank projects automatically expose every legacy GameSDK or Lua
  entity type. Register project-specific entity classes explicitly.

---

## 4. The Source Layout of a Plugin

Every C++ GameTemplate uses the same tiny, predictable layout. Take
`TopDownShooter` as the reference:

```
MyProject/
├── Game.cryproject
├── Assets/                 ← level files, textures, materials, ...
└── Code/
    ├── StdAfx.h            ← module definition (see §5)
    ├── StdAfx.cpp          ← precompiled header source
    ├── GamePlugin.h        ← your Cry::IEnginePlugin subclass
    ├── GamePlugin.cpp      ← plugin Initialize + system-event handling
    └── Components/
        ├── Player.h        ← player component header
        ├── Player.cpp      ← player component impl + Schematyc registration
        ├── SpawnPoint.h
        ├── SpawnPoint.cpp
        └── Bullet.h        ← header-only inline component
```
> source:Code/GameTemplates/cpp/TopDownShooter/Code/ (directory listing)

The two files you will edit most often are `GamePlugin.cpp` (one-time setup,
system events) and `Components/<YourComponent>.cpp` (per-component logic +
Schematyc registration). The rest of this chapter walks through both.

---

## 5. `StdAfx.h` — The Module Definition Every Source File Needs

Every `.cpp` in a CRYENGINE plugin starts with `#include "StdAfx.h"`. This is
not just a precompiled header — it tells the engine which *module* the code
belongs to, which in turn controls which deprecated APIs are visible and how
the DLL exports its entry symbol.

Here is the entire `StdAfx.h` from `TopDownShooter`:

```cpp
#pragma once

#include <CryCore/Project/CryModuleDefs.h>
#define eCryModule eCryM_EnginePlugin
#define GAME_API   DLL_EXPORT

#include <CryCore/Platform/platform.h>
#include <CrySystem/ISystem.h>
#include <Cry3DEngine/I3DEngine.h>
#include <CryNetwork/ISerialize.h>
```
> source:Code/GameTemplates/cpp/TopDownShooter/Code/StdAfx.h:1-12

The two magic lines:

- `#define eCryModule eCryM_EnginePlugin` — tells the engine this code is an
  engine plugin, not the legacy GameDLL. The enum value lives in
  source:Code/CryEngine/CryCommon/CryCore/Project/CryModuleDefs.h:34.
- `#define GAME_API DLL_EXPORT` — marks the DLL entry symbol for export.

> **Rule of thumb:** Copy this `StdAfx.h` verbatim into every new C++ project.
> Do not invent your own module id.

---

## 6. Writing a Plugin — `Cry::IEnginePlugin`

### 6.1 The Interface

`Cry::IEnginePlugin` is a pure-virtual interface. The only *required* method is
`Initialize`; the rest are optional update hooks you opt into with
`EnableUpdate`:

```cpp
struct IEnginePlugin : public ICryUnknown
{
    CRYINTERFACE_DECLARE_GUID(IEnginePlugin, "f491a0db-..."_cry_guid);

    virtual const char* GetName() const;
    virtual const char* GetCategory() const;            // default "Default"
    virtual bool Initialize(SSystemGlobalEnvironment& env,
                            const SSystemInitParams& initParams) = 0;   // REQUIRED

    // Optional per-frame hooks (opt-in via EnableUpdate):
    virtual void UpdateBeforeSystem()        {}
    virtual void UpdateBeforePhysics()       {}
    virtual void MainUpdate(float frameTime) {}
    virtual void UpdateBeforeFinalizeCamera(){}
    virtual void UpdateBeforeRender()        {}
    virtual void UpdateAfterRender()         {}
    virtual void UpdateAfterRenderSubmit()   {}

    // Optional flow-node registration hooks:
    virtual bool RegisterFlowNodes()   { return false; }
    virtual bool UnregisterFlowNodes() { return false; }
};
```
> source:Code/CryEngine/CryCommon/CrySystem/ICryPlugin.h:19-110

`EUpdateStep` is a bitmask of the seven update points above, in the order the
engine calls them each frame
source:Code/CryEngine/CryCommon/CrySystem/ICryPlugin.h:25-36.
Call `EnableUpdate(EUpdateStep::MainUpdate, true)` from inside `Initialize` if
you want per-frame plugin-level logic — see
[Plugin Update Loop](Plugin%20Update%20Loop.md).

### 6.2 The Smallest Possible Plugin

The Plugin GameTemplate is the canonical minimal example. The header:

```cpp
// Plugin.h
#pragma once
#include <CrySystem/ICryPlugin.h>
#include <CryGame/IGameFramework.h>
#include <CryEntitySystem/IEntityClass.h>

class CPlugin
    : public Cry::IEnginePlugin
    , public ISystemEventListener
{
public:
    CRYINTERFACE_SIMPLE(Cry::IEnginePlugin)
    CRYGENERATE_SINGLETONCLASS_GUID(CPlugin, "MyPlugin",
        "2711a23d-3848-4cdd-a95b-e9d88ffa23b0"_cry_guid)

    virtual ~CPlugin();
    virtual bool Initialize(SSystemGlobalEnvironment& env,
                            const SSystemInitParams& initParams) override;
    virtual void OnSystemEvent(ESystemEvent event,
                               UINT_PTR wparam, UINT_PTR lparam) override;
};
```
> source:Code/GameTemplates/cpp/Plugin/Code/Plugin.h:1-27

And the body:

```cpp
// Plugin.cpp
#include "StdAfx.h"
#include "Plugin.h"
#include <CrySchematyc/Env/IEnvRegistry.h>
#include <CrySchematyc/Env/EnvPackage.h>
#include <CrySchematyc/Utils/SharedString.h>
#include <CryCore/Platform/platform_impl.inl>   // once per DLL module

CPlugin::~CPlugin()
{
    gEnv->pSystem->GetISystemEventDispatcher()->RemoveListener(this);
    if (gEnv->pSchematyc)
        gEnv->pSchematyc->GetEnvRegistry().DeregisterPackage(CPlugin::GetCID());
}

bool CPlugin::Initialize(SSystemGlobalEnvironment& env,
                         const SSystemInitParams& initParams)
{
    gEnv->pSystem->GetISystemEventDispatcher()->RegisterListener(this, "CPlugin");
    return true;
}

void CPlugin::OnSystemEvent(ESystemEvent event, UINT_PTR wparam, UINT_PTR lparam)
{
    switch (event)
    {
    case ESYSTEM_EVENT_REGISTER_SCHEMATYC_ENV:
    {
        auto staticAutoRegisterLambda = [](Schematyc::IEnvRegistrar& registrar)
        {
            Detail::CStaticAutoRegistrar<Schematyc::IEnvRegistrar&>::
                InvokeStaticCallbacks(registrar);
        };
        if (gEnv->pSchematyc)
        {
            gEnv->pSchematyc->GetEnvRegistry().RegisterPackage(
                stl::make_unique<Schematyc::CEnvPackage>(
                    CPlugin::GetCID(), "EntityComponents",
                    "Crytek GmbH", "Components",
                    staticAutoRegisterLambda));
        }
        break;
    }
    }
}

CRYREGISTER_SINGLETON_CLASS(CPlugin)
```
> source:Code/GameTemplates/cpp/Plugin/Code/Plugin.cpp:1-59

#### Anatomy of this file

1. **`CRYINTERFACE_SIMPLE(Cry::IEnginePlugin)`** — declares the CryExtension
   interface for the plugin. source:Code/CryEngine/CryCommon/CryExtension/ClassWeaver.h:216
2. **`CRYGENERATE_SINGLETONCLASS_GUID(...)`** — weaves in the factory and the
   `ICryUnknown` boilerplate. The GUID here is the **plugin class GUID** —
   unique, never reused across projects.
   source:Code/CryEngine/CryCommon/CryExtension/ClassWeaver.h:419-424
3. **`CRYREGISTER_SINGLETON_CLASS(CPlugin)`** (last line of the .cpp) —
   instantiates the singleton factory so the engine can create your plugin.
   source:Code/CryEngine/CryCommon/CryExtension/ClassWeaver.h:429-430
4. **`platform_impl.inl`** — must be included exactly once per DLL. It provides
   the platform-level DLL entry point.
   source:Code/GameTemplates/cpp/Plugin/Code/Plugin.cpp:10
5. **`ESYSTEM_EVENT_REGISTER_SCHEMATYC_ENV`** — this is the engine's signal
   "Schematyc is ready, please register your types now". It is an alias for
   `ESYSTEM_EVENT_GAME_POST_INIT_DONE`.
   source:Code/CryEngine/CryCommon/CrySchematyc/FundamentalTypes.h:161
6. **`RegisterPackage`** — packages your Schematyc registrations under a named
   group owned by this plugin. When the plugin unloads, `DeregisterPackage`
   (in the destructor) cleans everything up.

> **Take-away:** The plugin file is **boilerplate you copy unchanged**. Your
> actual work goes in the components, which register themselves into the
> plugin's package via `CRY_STATIC_AUTO_REGISTER_FUNCTION` (see
> [Schematyc Guide](Schematyc%20Guide.md)).

### 6.3 A Game Plugin (with Player Spawning)

When your plugin is *the game* (not a shared library), it typically also listens
for network-client events to spawn the local player. `Blank` is the canonical
example. Its `OnSystemEvent` handles three events:

```cpp
void CGamePlugin::OnSystemEvent(ESystemEvent event, UINT_PTR wparam, UINT_PTR lparam)
{
    switch (event)
    {
    case ESYSTEM_EVENT_GAME_POST_INIT:
        gEnv->pGameFramework->AddNetworkedClientListener(*this);
        if (!gEnv->IsEditor())
            gEnv->pConsole->ExecuteString("map example s", false, true);
        break;

    case ESYSTEM_EVENT_REGISTER_SCHEMATYC_ENV:
        /* ... same RegisterPackage call as §6.2 ... */
        break;

    case ESYSTEM_EVENT_LEVEL_UNLOAD:
        m_players.clear();
        break;
    }
}
```
> source:Code/GameTemplates/cpp/Blank/Code/GamePlugin.cpp:41-90

When a client connects, the plugin spawns a default-class entity and attaches
the player component:

```cpp
bool CGamePlugin::OnClientConnectionReceived(int channelId, bool bIsReset)
{
    SEntitySpawnParams spawnParams;
    spawnParams.pClass = gEnv->pEntitySystem->GetClassRegistry()->GetDefaultClass();
    spawnParams.sName = string().Format("Player%" PRISIZE_T, m_players.size());

    if (m_players.empty() && !gEnv->IsDedicated())
    {
        spawnParams.id = LOCAL_PLAYER_ENTITY_ID;
        spawnParams.nFlags |= ENTITY_FLAG_LOCAL_PLAYER;
    }

    if (IEntity* pPlayerEntity = gEnv->pEntitySystem->SpawnEntity(spawnParams))
    {
        pPlayerEntity->GetNetEntity()->SetChannelId(channelId);
        if (CPlayerComponent* pPlayer = pPlayerEntity->GetOrCreateComponentClass<CPlayerComponent>())
            m_players.emplace(std::make_pair(channelId, pPlayerEntity->GetId()));
    }
    return true;
}
```
> source:Code/GameTemplates/cpp/Blank/Code/GamePlugin.cpp:92-126

The singleton instance is reachable from anywhere via:

```cpp
static CGamePlugin* GetInstance()
{
    return cryinterface_cast<CGamePlugin>(
        CGamePlugin::s_factory.CreateClassInstance().get());
}
```
> source:Code/GameTemplates/cpp/Blank/Code/GamePlugin.h:56-59

---

## 7. System Events Reference

Your plugin's `OnSystemEvent` is the central place for one-time setup. The most
commonly handled events:

| Event | When fired | Typical use |
|-------|------------|-------------|
| `ESYSTEM_EVENT_REGISTER_SCHEMATYC_ENV` | Schematyc is ready | Register all Schematyc components (see [Schematyc Guide](Schematyc%20Guide.md)) |
| `ESYSTEM_EVENT_GAME_POST_INIT` | Game framework initialized | Register network listeners, load first map |
| `ESYSTEM_EVENT_GAME_POST_INIT_DONE` | Same as above, no loading allowed | Alias for `ESYSTEM_EVENT_REGISTER_SCHEMATYC_ENV` |
| `ESYSTEM_EVENT_LEVEL_LOAD_END` | Level finished loading | Post-load setup |
| `ESYSTEM_EVENT_LEVEL_UNLOAD` | Level is unloading | Clear per-level state |
| `ESYSTEM_EVENT_FULL_SHUTDOWN` | Engine shutting down | Cleanup |
| `ESYSTEM_EVENT_EDITOR_GAME_MODE_CHANGED` | Editor enter/leave game mode | Toggle debug logic |

> source:Code/CryEngine/CryCommon/CrySystem/ISystem.h:290-399

---

## 8. Where to Look in the Engine Source

When in doubt, grep the engine source. The most useful starting points:

| You want to know about... | Open this header |
|---------------------------|-------------------|
| Plugin lifecycle, update steps | `Code/CryEngine/CryCommon/CrySystem/ICryPlugin.h` |
| Plugin manager, QueryPlugin | `Code/CryEngine/CryCommon/CrySystem/ICryPluginManager.h` |
| System events (`ESYSTEM_EVENT_*`) | `Code/CryEngine/CryCommon/CrySystem/ISystem.h` |
| Class factory macros (`CRYGENERATE_*`, `CRYREGISTER_*`) | `Code/CryEngine/CryCommon/CryExtension/ClassWeaver.h` |
| Module id (`eCryModule`) | `Code/CryEngine/CryCommon/CryCore/Project/CryModuleDefs.h` |
| Complete reference C++ game plugin | `Code/GameTemplates/cpp/Blank/` |
| Complete reference library plugin | `Code/GameTemplates/cpp/Plugin/` |

---

## Next

- [Entities and Components](Entities%20and%20Components.md) — what entities and
  components are, how to write one
- [Schematyc Guide](Schematyc%20Guide.md) — making components appear in the
  Sandbox Editor
- [Examples](Examples.md) — ready-to-paste worked examples
