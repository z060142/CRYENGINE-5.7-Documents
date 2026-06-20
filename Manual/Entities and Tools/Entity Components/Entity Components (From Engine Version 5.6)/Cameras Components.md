# Cameras Components

- Breadcrumb: Entities and Tools > Entity Components > Entity Components (From Engine Version 5.6) > Cameras Components
- Parent: Entity Components (From Engine Version 5.6)

## Camera

This represents a camera in the world from which the level can be rendered. Only one camera can be active at a time — `source:Code/CryPlugins/CryDefaultEntities/Module/DefaultComponents/Cameras/CameraManager.h:22` (`SwitchCameraToActive` sets a single `m_pActive`).

Entities with Camera components show up in the **Camera** menu in the **Perspective** viewport, under **Camera Entity**.

The Camera Component is `Cry::DefaultComponents::CCameraComponent` — `source:Code/CryPlugins/CryDefaultEntities/Module/DefaultComponents/Cameras/CameraComponent.h:37`.

### Settings

| Setting | Description | Default | Source |
|---------|-------------|---------|--------|
| **Type** | Method of rendering to use for the camera. | `Default` | `CameraComponent.h:127` |
| **Active** | Whether or not this camera should be activated on component creation. | `true` | `CameraComponent.h:128` |
| **Near Plane** | Distance from the camera that the engine will start rendering from (meters). Range: 0–32768. | `0.25` | `CameraComponent.h:129,165` |
| **Far Plane** | Distance from the camera that the engine will stop rendering at (meters). Range: 0–32768. | `1024` | `CameraComponent.h:130,166` |
| **Field of View** | The vertical field of view angle. Clamped to 20–360 degrees. | `70°` | `CameraComponent.h:131,167` |

#### Type

| Value | Description | Source |
|-------|-------------|--------|
| **Default** | A normal, one-directional camera. | `CameraComponent.h:23` |
| **Omnidirectional** | Renders the full 360 view to screen. Sets `CCamera::m_bOmniCamera = true`. | `CameraComponent.h:25`, `Cry_Camera.h:341` |

### Behavior

On each `ENTITY_EVENT_UPDATE` (when not in edit mode), the Camera Component — `source:Code/CryPlugins/CryDefaultEntities/Module/DefaultComponents/Cameras/CameraComponent.h:58`:

1. Copies the surface width/height and pixel aspect ratio from the current system camera.
2. Calls `SetFrustum(width, height, FOV-in-radians, nearPlane, farPlane, pixelAspectRatio)` on its internal `CCamera`.
3. Calls `SetMatrix(GetWorldTransformMatrix())` to apply the entity's world transform.
4. Calls `gEnv->pSystem->SetViewCamera(m_camera)` to set it as the main view camera.
5. If an HMD device is present, enables late camera injection for the current frame using the entity's world transform.

### Methods

| Method | Description | Source |
|--------|-------------|--------|
| `Activate()` | Makes this camera the active camera. | `CameraComponent.h:134` |
| `IsActive()` | Returns whether this camera is currently active. | `CameraComponent.h:140` |
| `EnableAutomaticActivation(bool)` | Sets whether the camera activates on creation. | `CameraComponent.h:145` |
| `SetNearPlane(float)` / `GetNearPlane()` | Near plane accessors. | `CameraComponent.h:148-149` |
| `SetFarPlane(float)` / `GetFarPlane()` | Far plane accessors. | `CameraComponent.h:151-152` |
| `SetFieldOfView(CAngle)` / `GetFieldOfView()` | FOV accessors. | `CameraComponent.h:154-155` |
| `GetType()` | Returns the `ECameraType`. | `CameraComponent.h:157` |
| `GetCamera()` | Returns the internal `CCamera&`. | `CameraComponent.h:159` |

> **Note:** The Camera Component does **not** automatically add an Audio Listener Component. To play audio from the camera position, add a Listener Component (`Cry::Audio::DefaultComponents::CListenerComponent`) to the same entity manually — `source:Code/CryPlugins/CryDefaultEntities/Module/DefaultComponents/Audio/ListenerComponent.h:66`.

## Roomscale VR Camera

Exposes an Entity Component that allows for easily creating a Roomscale VR camera — `Cry::DefaultComponents::VirtualReality::CRoomscaleCameraComponent` — `source:Code/CryPlugins/CryDefaultEntities/Module/DefaultComponents/Cameras/VirtualReality/RoomscaleCamera.h:19`.

All the user has to do is drag the component into their Schematyc entity, and it will be activated. The component automates asynchronous (late) camera injection, retrieving the headset's coordinates as late as possible to avoid unnecessary lag.

### Settings

| Setting | Description | Default | Source |
|---------|-------------|---------|--------|
| **Active** | Whether or not this camera should be activated on component creation. | `true` | `RoomscaleCamera.h:63` |
| **Near Plane** | Minimum distance that the engine will start rendering from (meters). Range: 0–32768. Example: `0.25` means rendering starts at 0.25m from the camera. | `0.25` | `RoomscaleCamera.h:64,93` |
| **Far Plane** | Maximum distance that the engine will render to (meters). Range: 0–32768. Example: `1024` means rendering stops at 1024m. | `1024` | `RoomscaleCamera.h:65,94` |

> **Note:** The Roomscale VR Camera uses a **fixed** field of view of `75°` (`75.0_degrees`). Unlike the standard Camera Component, the FOV is not exposed as a user-editable property — `source:Code/CryPlugins/CryDefaultEntities/Module/DefaultComponents/Cameras/VirtualReality/RoomscaleCamera.cpp:66`.

### Behavior

On each `ENTITY_EVENT_UPDATE` — `source:Code/CryPlugins/CryDefaultEntities/Module/DefaultComponents/Cameras/VirtualReality/RoomscaleCamera.cpp:47`:

1. If an HMD device is present, enables late camera injection using the entity's world transform, then reads the local tracking state and applies it to the camera matrix: `m_camera.SetMatrix(worldTransform * Matrix34::Create(Vec3(1), state.pose.orientation, state.pose.position))`.
2. If no HMD device is present, falls back to a fixed eye-height offset of 1.7m: `m_camera.SetMatrix(worldTM * Matrix34::Create(Vec3(1), IDENTITY, worldRot.GetInverted() * Vec3(0, 0, 1.7)))`.
3. Sets the frustum using the fixed 75° FOV.
4. Calls `gEnv->pSystem->SetViewCamera(m_camera)`.

## See Also

- [API Reference > Entity > Cameras](../../../../API%20Reference/Entity/Cameras.md) — full `CCamera` API reference
- [Audio](Audio.md) — Audio Listeners