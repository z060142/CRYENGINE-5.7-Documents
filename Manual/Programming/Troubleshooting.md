# Troubleshooting

> The "my component isn't showing up" checklist and other common pitfalls.

---

## 1. "My Component Isn't Showing Up in the Editor"

Run through this list in order. 99% of new-user issues are caught by step 3 or
step 5.

1. **Compiled?** Build the project. Did the DLL actually update in
   `bin/win_x64/`?
2. **In the `.cryproject`?** Your own DLL is in `require.plugins` and
   `CryDefaultEntities` is also listed.
3. **`CRYREGISTER_SINGLETON_CLASS`** at the bottom of your `GamePlugin.cpp`?
4. **`ESYSTEM_EVENT_REGISTER_SCHEMATYC_ENV`** handled in the plugin's
   `OnSystemEvent`, calling `RegisterPackage(...)` with a lambda that calls
   `Detail::CStaticAutoRegistrar<...>::InvokeStaticCallbacks(registrar)`?
5. **`CRY_STATIC_AUTO_REGISTER_FUNCTION(&RegisterXxxComponent)`** in the
   component's `.cpp`?
6. **`ReflectType`** present and `SetGUID` called with a unique GUID?
7. **`Scope(IEntity::GetEntityScopeGUID())`** used as the registration scope?
8. Editor restarted after rebuild? (Hot-reload exists but is not always
   reliable for new components.)

If all of these pass and the component still doesn't show: check the editor
console (`~`) for `CryLog`/`CryWarning` lines from Schematyc — they usually say
exactly what went wrong.

---

## 2. "My Component Shows Up But Properties Don't Appear"

- **`AddMember` missing?** Each property you want in the editor needs an
  `AddMember` call in `ReflectType`.
- **Member is private?** `AddMember` takes a pointer-to-member. The member must
  be accessible (public, or the `ReflectType` is a `friend`).
- **Type not reflected?** `AddMember` only works for types that have their own
  `ReflectType` (primitives, `Vec3`, `Quat`, `ColorF`, `string`, and nested
  structs with `ReflectType`). Custom types need their own `ReflectType`.
- **GUID not set on the component?** `SetGUID` must be called before
  `AddMember`.

---

## 3. "My Component Runs But Doesn't Receive Update Events"

- **`GetEventMask()` not returning `EEvent::Update`?** You must explicitly
  subscribe to each event you want.
- **`ProcessEvent` not handling the right event?** Check your `switch` cases
  match the `Cry::Entity::EEvent` enum values.
- **Entity not updating?** Entities only update if they are in the update list.
  This is usually automatic, but entities that are hidden or very far away may
  not update. Check `ENTITY_FLAG_SEND_RENDER_EVENT` if you need render-related
  events.

---

## 4. "Input Doesn't Work"

- **`CInputComponent` created?** Call `m_pEntity->GetOrCreateComponent<Cry::DefaultComponents::CInputComponent>()`.
- **Actions registered?** Each action needs both `RegisterAction(group, name, callback)` and `BindAction(group, name, device, key)`.
- **Action map enabled?** The action map group must be enabled. The
  `CInputComponent` handles this automatically when you register actions, but
  if you're using `IActionMapManager` directly, you must enable the action map
  yourself.
- **Wrong device?** `eAID_KeyboardMouse` is for keyboard/mouse. Use
  `eAID_Xbox` or `eAID_PS4` for gamepads.
  source:Code/CryEngine/CryCommon/CryAction/IActionMapManager.h:95

---

## 5. "Physics Doesn't Work"

- **Entity not physicalized?** Call `m_pEntity->Physicalize(params)` with a
  valid `SEntityPhysicalizeParams`. The `type` must be set (`PE_RIGID`,
  `PE_STATIC`, `PE_PLAYER`, ...).
- **Both mass and density set?** Only one of `mass` or `density` should be set
  (the other must be `-1`, the default).
  source:Code/CryEngine/CryCommon/CryEntitySystem/IEntity.h:286-288
- **Geometry loaded before physicalizing?** The physics needs geometry to
  collide with. Call `LoadGeometry` before `Physicalize`.
- **Collision event not firing?** You must return `ENTITY_EVENT_COLLISION` (or
  `Cry::Entity::EEvent::PhysicsCollision`) from `GetEventMask()`.

---

## 6. "Network Replication Doesn't Work"

- **`BindToNetwork()` called?** Call `m_pEntity->GetNetEntity()->BindToNetwork()`
  in `Initialize`.
- **`GetNetSerializeAspectMask()` returning 0?** Return the bitmask of aspects
  you serialize.
- **`NetMarkAspectsDirty()` called after local changes?** The engine doesn't
  auto-detect changes; you must mark aspects dirty.
- **Wrong aspect?** Make sure the aspect you're serializing matches what you
  return from `GetNetSerializeAspectMask()`.

---

## 7. "Build Errors"

- **`eCryModule` not defined?** Your `StdAfx.h` must `#define eCryModule eCryM_EnginePlugin`
  before including any engine headers.
- **`platform_impl.inl` included twice?** It must be included exactly once per
  DLL module, in the main .cpp file (usually `GamePlugin.cpp`).
- **Linker errors for unresolved symbols?** Make sure your `.cryproject` lists
  all required plugins in `require.plugins`. Missing `CryDefaultEntities` is a
  common cause.
- **`CRYREGISTER_SINGLETON_CLASS` missing?** It must be at the bottom of
  exactly one .cpp file in your DLL.

---

## 8. "Editor Crashes on Startup"

- **Duplicate GUID?** Every component GUID must be unique. Two components with
  the same GUID will cause a crash or silent failure.
- **Plugin GUID matches another plugin?** The GUID in
  `CRYGENERATE_SINGLETONCLASS_GUID` must be unique across all loaded plugins.
- **Old DLL still loaded?** Close the editor before rebuilding. The editor may
  hold a lock on the DLL.

---

## 9. "Lua Script Not Loading"

- **`entities.xml` in the asset root?** The legacy script entity registry loads
  `entities.xml` from the project asset search path. In a Blank-style project,
  place it at `Assets/entities.xml`.
- **XML shape correct?** The root must be `<Entities>`, with child
  `<Entity Name="..." Script="...">` elements.
- **Script path correct?** The `Script` attribute is relative to the asset
  search path, for example `Scripts/Entities/Others/MyDoor.lua`.
- **Syntax error?** Check the console (`~`) for Lua errors. They are usually
  printed with the file and line number.
- **Script not reloaded?** Use the console command `es_reload_scripts` or
  restart the editor after editing.
- **Logging function correct?** Use `System.Log(...)` or
  `System.LogAlways(...)` from Lua. `CryLog(...)` is a C++ macro, not a Lua
  global in a Blank-style project.

---

## 10. Common Pitfalls Summary

| Pitfall | Fix |
|---------|-----|
| Component invisible in editor | Check the 8-step list in §1 |
| Properties not editable | Add `AddMember` in `ReflectType` |
| No Update events | Return `EEvent::Update` from `GetEventMask` |
| No collision events | Return `EEvent::PhysicsCollision` from `GetEventMask` |
| Input silent | Create `CInputComponent`, register + bind actions |
| Physics silent | `Physicalize` with valid params, load geometry first |
| Network not syncing | `BindToNetwork`, return aspect mask, mark dirty |
| Build fails | Check `StdAfx.h`, `platform_impl.inl`, plugin list |
| Crash on startup | Check for duplicate GUIDs |
| Lua not loading | Check `Assets/entities.xml` and script path |

---

## Next

- [Getting Started](Getting%20Started.md) — start over if something went wrong
- [Examples](Examples.md) — copy-paste working code
- [Schematyc Guide](Schematyc%20Guide.md) — registration flow in detail
