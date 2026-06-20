# View System

- Breadcrumb: CRYENGINE Engine Code > Engine Modules > CryAction > View System
- Parent: CryAction

## Overview

The View System in CryAction keeps track of all the different views that can be created during your game runtime. It allows you to create, remove and switch between views as well as handling cutscene camera cut requests. The system is represented by `IViewSystem` and its views by `IView` — `source:Code/CryEngine/CryAction/IViewSystem.h:236`.

## API Types

| Type | Description | Source |
|------|-------------|--------|
| `IViewSystem` | Central view system interface | `IViewSystem.h:236` |
| `IView` | Individual view instance | `IViewSystem.h:173` |
| `SViewParams` | Parameters defining a view (position, rotation, FOV, blending, etc.) | `IViewSystem.h:20` |
| `IViewSystemListener` | Callback interface for cutscene/camera-change events | `IViewSystem.h:228` |

## IViewSystem

The `IViewSystem` is retrieved from `IGameFramework::GetIViewSystem()` — `source:Code/CryEngine/CryAction/IGameFramework.h`. It manages the lifetime of views and routes cutscene/camera events.

### View Management

| Method | Description | Source |
|--------|-------------|--------|
| `CreateView()` | Creates a new `IView` instance | `IViewSystem.h:239` |
| `RemoveView(IView* pView)` | Removes a view by pointer | `IViewSystem.h:240` |
| `RemoveView(unsigned int viewId)` | Removes a view by ID | `IViewSystem.h:241` |
| `SetActiveView(IView* pView)` | Activates a specific view | `IViewSystem.h:243` |
| `SetActiveView(unsigned int viewId)` | Activates a view by ID | `IViewSystem.h:244` |
| `GetView(unsigned int viewId)` | Retrieves a view by ID | `IViewSystem.h:247` |
| `GetActiveView()` | Retrieves the currently active view | `IViewSystem.h:248` |
| `GetViewId(IView* pView)` | Returns the ID of a view | `IViewSystem.h:251` |
| `GetActiveViewId()` | Returns the active view ID | `IViewSystem.h:252` |
| `GetViewByEntityId(unsigned int id, bool forceCreate = false)` | Gets/creates a view linked to an entity | `IViewSystem.h:254` |

### Listeners

| Method | Description | Source |
|--------|-------------|--------|
| `AddListener(IViewSystemListener* pListener)` | Registers a cutscene/camera-change listener | `IViewSystem.h:256` |
| `RemoveListener(IViewSystemListener* pListener)` | Unregisters a listener | `IViewSystem.h:257` |

`IViewSystemListener` receives callbacks for cutscene begin/end and camera changes — `source:Code/CryEngine/CryAction/IViewSystem.h:228-234`.

### Other Methods

| Method | Description | Source |
|--------|-------------|--------|
| `GetDefaultZNear()` | Default near clipping plane distance | `IViewSystem.h:263` |
| `SetBlendParams(float fBlendPosSpeed, float fBlendRotSpeed, bool performBlendOut)` | Global blend speed override | `IViewSystem.h:265` |
| `SetOverrideCameraRotation(bool bOverride, Quat rotation)` | Override camera rotation (time demo playback) | `IViewSystem.h:268` |
| `IsPlayingCutScene()` | Returns whether a cutscene is active | `IViewSystem.h:270` |
| `SetDeferredViewSystemUpdate(bool)` | Defers view-system update | `IViewSystem.h:272` |
| `UseDeferredViewSystemUpdate()` | Returns deferred update state | `IViewSystem.h:273` |
| `SetControlAudioListeners(bool)` | Enables/disables audio listener control | `IViewSystem.h:274` |
| `UpdateAudioListeners()` | Manually updates audio listeners | `IViewSystem.h:275` |

## IView

`IView` represents a single camera view. It can be linked to entities/game objects and updated with `SViewParams`.

### View Methods

| Method | Description | Source |
|--------|-------------|--------|
| `Release()` | Destroys the view | `IViewSystem.h:209` |
| `Update(float frameTime, bool isActive)` | Updates the view each frame | `IViewSystem.h:210` |
| `LinkTo(IGameObject* follow)` | Links view to a game object | `IViewSystem.h:211` |
| `LinkTo(IEntity* follow, IGameObjectView* callback = nullptr)` | Links view to an entity | `IViewSystem.h:212` |
| `GetLinkedId()` | Returns the entity ID the view is linked to | `IViewSystem.h:213` |
| `SetCurrentParams(SViewParams& params)` | Sets current view parameters | `IViewSystem.h:215` |
| `GetCurrentParams()` | Returns current view parameters | `IViewSystem.h:216` |
| `SetViewShake(...)` | Legacy camera shake | `IViewSystem.h:217` |
| `SetViewShakeEx(const SShakeParams& params)` | Extended camera shake | `IViewSystem.h:218` |
| `StopShake(int shakeID)` | Stops a specific shake | `IViewSystem.h:219` |
| `ResetShaking()` | Resets all shakes | `IViewSystem.h:220` |
| `ResetBlending()` | Resets blending offsets | `IViewSystem.h:221` |
| `SetFrameAdditiveCameraAngles(const Ang3& addFrameAngles)` | Adds per-frame rotation | `IViewSystem.h:222` |
| `SetScale(float scale)` | Sets view scale | `IViewSystem.h:223` |
| `SetZoomedScale(float scale)` | Sets zoomed scale | `IViewSystem.h:224` |
| `SetActive(bool bActive)` | Activates/deactivates the view | `IViewSystem.h:225` |

## SViewParams

`SViewParams` holds the configuration of a view. Key fields — `source:Code/CryEngine/CryAction/IViewSystem.h:20`:

| Field | Description | Default |
|-------|-------------|---------|
| `position` | View position | `ZERO` |
| `rotation` | View orientation | `IDENTITY` |
| `nearplane` | Custom near plane (0 = use engine default) | `0.0f` |
| `fov` | Field of view | `0.0f` |
| `viewID` | View ID for blending | `0` |
| `blend` | Enable position/rotation/FOV blending | `true` |
| `blendPosSpeed` | Position blend speed | `5.0f` |
| `blendRotSpeed` | Rotation blend speed | `10.0f` |
| `blendFOVSpeed` | FOV blend speed | `5.0f` |
| `blendPosOffset` | Position blend offset | `ZERO` |
| `blendRotOffset` | Rotation blend offset | `IDENTITY` |
| `blendFOVOffset` | FOV blend offset | `0` |
| `justActivated` | True when the view was just activated | `false` |

### SViewParams Helper Methods

| Method | Description | Source |
|--------|-------------|--------|
| `SetViewID(uint8 id, bool blend = true)` | Sets view ID for blending | `IViewSystem.h:54` |
| `UpdateBlending(float frameTime)` | Blends position/rotation/FOV over time | `IViewSystem.h:61` |
| `BlendFrom(const SViewParams& params)` | Starts blending from another set of params | `IViewSystem.h:93` |
| `SaveLast()` | Saves last position/rotation/FOV | `IViewSystem.h:103` |
| `ResetBlending()` | Resets blend offsets | `IViewSystem.h:117` |

## View IDs

Predefined view identifiers — `source:Code/CryEngine/CryAction/IViewSystem.h:8-11`:

| ID | Value | Description |
|---|------|-------------|
| `VIEWID_NORMAL` | 0 | Normal player view |
| `VIEWID_FOLLOWHEAD` | 1 | Follow head/bone view |
| `VIEWID_VEHICLE` | 2 | Vehicle view |
| `VIEWID_RAGDOLL` | 3 | Ragdoll/death view |

## Camera Shake

`IView::SShakeParams` defines an extended camera shake — `source:Code/CryEngine/CryAction/IViewSystem.h:176`:

| Field | Description | Default |
|-------|-------------|---------|
| `shakeAngle` | Angular shake amplitude | `Ang3(0,0,0)` |
| `shakeShift` | Translational shake amplitude | `Vec3(0,0,0)` |
| `sustainDuration` | Duration of full shake after fade-in | `0` |
| `fadeInDuration` | Fade-in time | `0` |
| `fadeOutDuration` | Fade-out time | `2.0f` |
| `frequency` | Shake frequency | `0` |
| `randomness` | Randomness amount | `0` |
| `shakeID` | Shake identifier for stopping | `0` |
| `bFlipVec` | Flip shake vector | `true` |
| `bUpdateOnly` | Update-only mode | `false` |
| `bGroundOnly` | Only shake when on ground | `false` |
| `bPermanent` | Permanent shake (ignores sustainDuration) | `false` |
| `isSmooth` | Smooth (curved) vs linear shake | `false` |

## CVars

The View System implements the following CVars:

| Name | Purpose |
|------|---------|
| `cl_camera_noise` | Adds hand-held-like camera noise to the camera view. The higher the value, the higher the noise. A value <= 0 disables it. |
| `cl_camera_noise_freq` | Defines camera noise frequency for the camera view. The higher the value, the higher the noise. |
| `cl_ViewSystemDebug` | Sets debug information of the ViewSystem. |
| `cl_DefaultNearPlane` | Sets the default camera near plane. Default is `0.25`. |

## See Also

- [Cameras](../../../Entity/Cameras.md) — `CCamera`, `ISystem::SetViewCamera`, `CCameraComponent`
- [Camera Nodes](../../../../Manual/Editor%20Tools/Flow%20Graph/Flow%20Graph%20Node%20Reference/Camera%20Nodes.md) — Flow Graph camera nodes (`Camera:View`, `Camera:ViewShakeEx`)
- [Camera Shaking](../../../../Manual/Film%20and%20Cutscenes/Cinematics%20Overview/Track%20Cameras/Camera%20Shaking.md) — Track View camera shake