# Plugin Update Loop

> How to run per-frame logic at the plugin level (not tied to an entity).

Sometimes you want logic that runs every frame but is not tied to a specific
entity — a global game-mode manager, a rules system, a debug overlay. Use the
plugin's update hooks.

---

## 1. Opting In

By default, a plugin does **not** receive per-frame callbacks. You must opt in
during `Initialize`:

```cpp
bool CMyPlugin::Initialize(SSystemGlobalEnvironment& env, const SSystemInitParams& initParams)
{
    EnableUpdate(EUpdateStep::MainUpdate, true);   // opt in
    return true;
}

void CMyPlugin::MainUpdate(float frameTime)
{
    // Runs once per frame, after ISystem has updated.
    // Most game-logic-style plugin updates belong here.
}
```
> source:Code/CryEngine/CryCommon/CrySystem/ICryPlugin.h:47-103

---

## 2. The Seven Update Steps

The available update steps, in the order the engine calls them each frame:

| Step | Method | When | Use for |
|------|--------|------|---------|
| `BeforeSystem` | `UpdateBeforeSystem()` | Earliest, before `ISystem::Update` | Pre-frame input polling |
| `BeforePhysics` | `UpdateBeforePhysics()` | Before the physics step | Queuing physics jobs |
| `MainUpdate` | `MainUpdate(frameTime)` | After `ISystem::Update` (default) | Most game logic |
| `BeforeFinalizeCamera` | `UpdateBeforeFinalizeCamera()` | Just before the camera is finalized | Last-minute camera tweaks, VR late injection |
| `BeforeRender` | `UpdateBeforeRender()` | Before rendering starts | Submit render-world changes |
| `AfterRender` | `UpdateAfterRender()` | After the render request is submitted | Post-render hooks |
| `AfterRenderSubmit` | `UpdateAfterRenderSubmit()` | After the frame is handed to the output device | VR frame timing |

> source:Code/CryEngine/CryCommon/CrySystem/ICryPlugin.h:25-70

You can enable multiple steps:

```cpp
EnableUpdate(EUpdateStep::MainUpdate, true);
EnableUpdate(EUpdateStep::BeforeFinalizeCamera, true);
```

Each enabled step will call its corresponding virtual method on your plugin.

---

## 3. Disabling Updates

You can disable a step at any time:

```cpp
EnableUpdate(EUpdateStep::MainUpdate, false);
```

This is useful for pausing game logic when the game is paused, or for
conditional updates that only run during specific game states.

---

## 4. Querying Other Plugins

If your plugin needs to talk to another plugin (e.g. a game rules plugin
querying a statistics plugin), use the plugin manager:

```cpp
if (auto* pOther = gEnv->pSystem->GetIPluginManager()->QueryPlugin<COtherPlugin>())
{
    pOther->DoThing();
}
```
> source:Code/CryEngine/CryCommon/CrySystem/ICryPluginManager.h:57-68
> source:Code/CryEngine/CryCommon/CrySystem/ISystem.h:1189

`QueryPlugin<T>()` returns `nullptr` if the plugin is not loaded. This only
works if the plugin was listed in the `.cryproject` file's `require.plugins`
array.

---

## 5. Plugin Event Listeners

You can also register to be notified when a specific plugin is loaded or
unloaded:

```cpp
class CMyPlugin : public Cry::IEnginePlugin
                , public Cry::IPluginManager::IEventListener
{
    void OnPluginEvent(const CryClassID& pluginClassId, EEvent event) override
    {
        if (event == EEvent::Initialized)
        {
            // The plugin with pluginClassId was just initialized
        }
        else if (event == EEvent::Unloaded)
        {
            // It was unloaded
        }
    }
};

// In Initialize:
gEnv->pSystem->GetIPluginManager()->RegisterEventListener<COtherPlugin>(this);
```
> source:Code/CryEngine/CryCommon/CrySystem/ICryPluginManager.h:35-55

---

## 6. When to Use Plugin Update vs Entity Update

| | Plugin Update | Entity Component Update |
|---|---|---|
| **Scope** | Global | Per-entity |
| **Lifespan** | Entire game session | Entity lifetime |
| **Use case** | Global systems, rules, managers | Gameplay logic on a specific entity |
| **How to enable** | `EnableUpdate(step, true)` in `Initialize` | Return `EEvent::Update` from `GetEventMask()` |

Most gameplay logic belongs in entity components. Plugin updates are for
systems that need to run regardless of whether any specific entity exists.

---

## Next

- [Troubleshooting](Troubleshooting.md) — common pitfalls
- [Getting Started](Getting%20Started.md) — plugin setup recap
- [Plugin System](../Beta%20Features/Plugin%20System.md) — beta plugin manager overview