# Cameras

- Breadcrumb: Entity > Cameras
- Parent: Entity

## Overview

Cameras in CRYENGINE are represented by the `CCamera` structure, and represent a view into the world. The main camera needs to be set by calling `ISystem::SetViewCamera` at any point before `Cry::IEnginePlugin::UpdateBeforeFinalizeCamera` is called in order to be set in time for occlusion culling and rendering — `source:Code/CryEngine/CryCommon/CrySystem/ISystem.h:1266`.

A camera is commonly initialized with `CCamera::SetFrustum`, specifying resolution, field of view, near plane and the far plane, in addition to `CCamera::SetMatrix` being used to set the world transformation of the specified camera — `source:Code/CryEngine/CryCommon/CryMath/Cry_Camera.h:127` (SetFrustum), `source:Code/CryEngine/CryCommon/CryMath/Cry_Camera.h:103` (SetMatrix).

Note that camera handling is automated by the Camera Component in the default components plug-in, see `Cry::DefaultComponents::CCameraComponent` — `source:Code/CryPlugins/CryDefaultEntities/Module/DefaultComponents/Cameras/CameraComponent.h:37`.

## Table of Contents

- [CCamera](#ccamera)
- [Coordinate System](#coordinate-system)
- [Construction and Defaults](#construction-and-defaults)
- [Frustum Setup](#frustum-setup)
- [Transformation](#transformation)
- [Projection and Screen Mapping](#projection-and-screen-mapping)
- [Frustum Culling](#frustum-culling)
- [Render Matrices](#render-matrices)
- [Asymmetric Frustum and Oblique Clip Plane](#asymmetric-frustum-and-oblique-clip-plane)
- [Stereo / Multi-Camera](#stereo--multi-camera)
- [Static Orientation Helpers](#static-orientation-helpers)
- [Audio Listeners](#audio-listeners)
- [Asynchronous Camera Injection (VR)](#asynchronous-camera-injection-vr)
- [Camera Component](#camera-component)
- [Conclusion](#conclusion)

## CCamera

`CCamera` is a value type (not an interface) declared in `Cry_Camera.h`. It implements essential operations like calculation of a view-matrix and frustum-culling with simple geometric primitives (Point, Sphere, AABB, OBB). All calculations are based on the CRYENGINE coordinate-system — `source:Code/CryEngine/CryCommon/CryMath/Cry_Camera.h:33`.

```cpp
class CCamera
// source:Code/CryEngine/CryCommon/CryMath/Cry_Camera.h:62
```

### Coordinate System

CRYENGINE uses a **right-handed** coordinate system, where the positive X-Axis points to the right, the positive Y-Axis points away from the viewer and the positive Z-Axis points up — `source:Code/CryEngine/CryCommon/CryMath/Cry_Camera.h:35`.

```
z-axis
 ^
 |
 |   y-axis
 |  /
 | /
 |/
 +---------------->   x-axis
```

This same system is also used in 3D-Studio-MAX. The 6 DOFs (degrees-of-freedom) are stored in one single 3x4 matrix (`m_Matrix`). The 3 orientation-DOFs are stored in the 3x3 part and the 3 position-DOFs are stored in the translation-vector — `source:Code/CryEngine/CryCommon/CryMath/Cry_Camera.h:53`.

### Construction and Defaults

The default constructor initializes the matrix to identity, sets a default frustum of 640x480, and sets the eye to `eEye_Left` — `source:Code/CryEngine/CryCommon/CryMath/Cry_Camera.h:75`.

Default constants — `source:Code/CryEngine/CryCommon/CryMath/Cry_Camera.h:11`:

| Constant         | Value                        | Description                          |
|------------------|------------------------------|--------------------------------------|
| `DEFAULT_NEAR`   | `0.1f`                       | Default near clipping plane distance |
| `DEFAULT_FAR`    | `1024.0f`                    | Default far clipping plane distance  |
| `DEFAULT_FOV`    | `75.0f * gf_PI / 180.0f`     | Default vertical field of view (rad) |

Frustum plane indices are defined as an anonymous enum — `source:Code/CryEngine/CryCommon/CryMath/Cry_Camera.h:15`:

| Constant          | Value | Description          |
|-------------------|-------|----------------------|
| `FR_PLANE_NEAR`   | 0     | Near clipping plane  |
| `FR_PLANE_FAR`    | 1     | Far clipping plane   |
| `FR_PLANE_RIGHT`  | 2     | Right plane          |
| `FR_PLANE_LEFT`   | 3     | Left plane           |
| `FR_PLANE_TOP`    | 4     | Top plane            |
| `FR_PLANE_BOTTOM` | 5     | Bottom plane         |
| `FRUSTUM_PLANES`  | 6     | Total plane count    |

Culling result codes — `source:Code/CryEngine/CryCommon/CryMath/Cry_Camera.h:26`:

| Enum Value        | Description                                    |
|-------------------|------------------------------------------------|
| `CULL_EXCLUSION`  | The whole object is outside of frustum         |
| `CULL_OVERLAP`    | The object & frustum overlap                   |
| `CULL_INCLUSION`  | The whole object is inside frustum             |

### Frustum Setup

```cpp
void SetFrustum(int nWidth, int nHeight, f32 FOV = DEFAULT_FOV,
                f32 nearplane = DEFAULT_NEAR, f32 farpane = DEFAULT_FAR,
                f32 fPixelAspectRatio = 1.0f);
// source:Code/CryEngine/CryCommon/CryMath/Cry_Camera.h:127
```

Sets the frustum parameters. `FOV` is the **vertical** field of view in radians `[0..1*2PI]`. `fPixelAspectRatio` accounts for non-square pixels (1.0 for square pixels). The projection ratio (width/height) is derived from `nWidth / fPixelAspectRatio / nHeight`.

Assertions validate: `nearplane > 0.001f`, `farpane > 0.1f`, `farpane > nearplane`, `FOV >= 0.0000001f && FOV < gf_PI` — `source:Code/CryEngine/CryCommon/CryMath/Cry_Camera.h:594`.

Frustum query methods:

| Method | Return | Source |
|--------|--------|--------|
| `GetViewSurfaceX()` | Surface width-resolution (`int`) | `Cry_Camera.h:130` |
| `GetViewSurfaceZ()` | Surface height-resolution (`int`) | `Cry_Camera.h:131` |
| `GetFov()` | Vertical FOV in radians (`f32`) | `Cry_Camera.h:132` |
| `GetHorizontalFov()` | Horizontal FOV in radians (`float`) | `Cry_Camera.h:133`, `Cry_Camera.h:345` |
| `GetNearPlane()` | Near plane distance (`f32`) | `Cry_Camera.h:134` |
| `GetFarPlane()` | Far plane distance (`f32`) | `Cry_Camera.h:135` |
| `GetProjRatio()` | Projection ratio (width/height) (`f32`) | `Cry_Camera.h:136` |
| `GetAngularResolution()` | `m_Height / m_fov` (`f32`) | `Cry_Camera.h:137` |
| `GetPixelAspectRatio()` | Pixel aspect ratio (`f32`) | `Cry_Camera.h:138` |

The horizontal FOV is computed as `atan(tan(m_fov * 0.5f) * GetProjRatio()) * 2` — `source:Code/CryEngine/CryCommon/CryMath/Cry_Camera.h:345`.

### Transformation

The camera's 6 DOFs (position + orientation) are stored in a single `Matrix34` (`m_Matrix`). Use the following methods to access or modify it — `source:Code/CryEngine/CryCommon/CryMath/Cry_Camera.h:103`:

| Method | Description | Source |
|--------|-------------|--------|
| `SetMatrix(const Matrix34& mat)` | Set world matrix; asserts orthonormal; calls `UpdateFrustum()` | `Cry_Camera.h:103` |
| `SetMatrixNoUpdate(const Matrix34& mat)` | Set world matrix without updating frustum | `Cry_Camera.h:104` |
| `GetMatrix()` | Get world matrix (`const Matrix34&`) | `Cry_Camera.h:105` |
| `GetViewdir()` | View direction = `m_Matrix.GetColumn1()` | `Cry_Camera.h:106` |
| `GetViewMatrix()` | Inverse of world matrix (`Matrix34`) | `Cry_Camera.h:108` |
| `GetPosition()` | Camera position (`Vec3`) | `Cry_Camera.h:109` |
| `SetPosition(const Vec3& p)` | Set position; calls `UpdateFrustum()` | `Cry_Camera.h:110` |
| `SetPositionNoUpdate(const Vec3& p)` | Set position without updating frustum | `Cry_Camera.h:111` |
| `GetUp()` | Up vector = `m_Matrix.GetColumn2()` | `Cry_Camera.h:116` |
| `GetAngles()` | YPR angles from matrix (`Ang3`) | `Cry_Camera.h:324` |
| `SetAngles(const Ang3& angles)` | Set rotation from YPR angles | `Cry_Camera.h:325` |

### Projection and Screen Mapping

```cpp
bool Project(const Vec3& p, Vec3& result,
             Vec2i topLeft = Vec2i(0, 0),
             Vec2i widthHeight = Vec2i(0, 0)) const;
// source:Code/CryEngine/CryCommon/CryMath/Cry_Camera.h:112
```

Projects a world-space point `p` to screen-space `result`. Returns `true` if the point is visible on screen. The result's `x`/`y` are pixel coordinates, `z` is the normalized depth — `source:Code/CryEngine/CryCommon/CryMath/Cry_Camera.h:439`.

```cpp
bool Unproject(const Vec3& viewportPos, Vec3& result,
               Vec2i topLeft = Vec2i(0, 0),
               Vec2i widthHeight = Vec2i(0, 0)) const;
// source:Code/CryEngine/CryCommon/CryMath/Cry_Camera.h:113
```

Unprojects a viewport-space position to world-space. Returns `true` on success — `source:Code/CryEngine/CryCommon/CryMath/Cry_Camera.h:479`.

```cpp
void CalcScreenBounds(int* vOut, const AABB* pAABB, int x, int y,
                      int nWidth, int nHeight) const;
// source:Code/CryEngine/CryCommon/CryMath/Cry_Camera.h:114
```

Calculates the screen-space bounding rectangle of an AABB. `vOut` receives 4 ints: `x0, y0, x1, y1` — `source:Code/CryEngine/CryCommon/CryMath/Cry_Camera.h:512`.

### Frustum Culling

`CCamera` provides several visibility tests against its 6-plane frustum. The suffixes indicate the variant:

- **`_F`** — Fast (single dot-product per plane, conservative)
- **`_FH`** — Fast + Hierarchical (also detects full inclusion)
- **`_E`** — Exact (additional checks, ~30% slower, rejects edge cases)
- **`_EH`** — Exact + Hierarchical
- **`_M`** — Multi-camera (checks `m_pMultiCamera` array if set)

#### Point

```cpp
bool IsPointVisible(const Vec3& p) const;
// source:Code/CryEngine/CryCommon/CryMath/Cry_Camera.h:174
```

Returns `CULL_OVERLAP` (true) if the point is inside the frustum, `CULL_EXCLUSION` (false) otherwise — `source:Code/CryEngine/CryCommon/CryMath/Cry_Camera.h:861`.

#### Sphere

| Method | Return | Source |
|--------|--------|--------|
| `IsSphereVisible_F(const Sphere& s)` | `bool` (CULL_EXCLUSION / CULL_OVERLAP) | `Cry_Camera.h:177` |
| `IsSphereVisible_FH(const Sphere& s)` | `uint8` (CULL_EXCLUSION / CULL_OVERLAP / CULL_INCLUSION) | `Cry_Camera.h:178` |

#### AABB

| Method | Return | Source |
|--------|--------|--------|
| `IsAABBVisible_F(const AABB& aabb)` | `bool` | `Cry_Camera.h:182` |
| `IsAABBVisible_FH(const AABB& aabb, bool* pAllInside)` | `uint8` | `Cry_Camera.h:183` |
| `IsAABBVisible_FH(const AABB& aabb)` | `uint8` | `Cry_Camera.h:184` |
| `IsAABBVisible_E(const AABB& aabb)` | `bool` | `Cry_Camera.h:187` |
| `IsAABBVisible_EH(const AABB& aabb, bool* pAllInside)` | `uint8` | `Cry_Camera.h:188` |
| `IsAABBVisible_EH(const AABB& aabb)` | `uint8` | `Cry_Camera.h:189` |
| `IsAABBVisible_EHM(const AABB& aabb, bool* pAllInside)` | `bool` (multi-camera) | `Cry_Camera.h:192` |
| `IsAABBVisible_EM(const AABB& aabb)` | `bool` (multi-camera) | `Cry_Camera.h:193` |
| `IsAABBVisible_FM(const AABB& aabb)` | `bool` (multi-camera) | `Cry_Camera.h:194` |

#### OBB

| Method | Return | Source |
|--------|--------|--------|
| `IsOBBVisible_F(const Vec3& wpos, const OBB& obb)` | `bool` | `Cry_Camera.h:197` |
| `IsOBBVisible_FH(const Vec3& wpos, const OBB& obb)` | `uint8` | `Cry_Camera.h:198` |
| `IsOBBVisible_E(const Vec3& wpos, const OBB& obb, f32 uscale)` | `bool` | `Cry_Camera.h:199` |
| `IsOBBVisible_EH(const Vec3& wpos, const OBB& obb, f32 uscale)` | `uint8` | `Cry_Camera.h:200` |

#### Frustum Vertices

```cpp
void GetFrustumVertices(Vec3* pVerts) const;       // 8 verts, world space
// source:Code/CryEngine/CryCommon/CryMath/Cry_Camera.h:202

void GetFrustumVerticesCam(Vec3* pVerts) const;    // 8 verts, camera space
// source:Code/CryEngine/CryCommon/CryMath/Cry_Camera.h:203
```

Near/far/projection-plane vertices can also be queried individually via `GetNPVertex(nId)`, `GetFPVertex(nId)`, `GetPPVertex(nId)` where `nId` is 0-3 — `source:Code/CryEngine/CryCommon/CryMath/Cry_Camera.h:149`.

Frustum planes are accessible via:
```cpp
const Plane* GetFrustumPlane(int numplane) const;
// source:Code/CryEngine/CryCommon/CryMath/Cry_Camera.h:153
```

### Render Matrices

The camera caches the view and projection matrices used by the renderer. These are computed in `UpdateFrustum()` via `CalculateRenderMatrices()` — `source:Code/CryEngine/CryCommon/CryMath/Cry_Camera.h:702`.

| Method | Return | Source |
|--------|--------|--------|
| `GetRenderViewMatrix()` | `const Matrix44&` (view matrix) | `Cry_Camera.h:118` |
| `GetRenderProjectionMatrix()` | `const Matrix44&` (projection matrix) | `Cry_Camera.h:119` |
| `GetRenderVectorX()` | `const Vec3` (render basis X) | `Cry_Camera.h:121` |
| `GetRenderVectorY()` | `const Vec3` (render basis Y) | `Cry_Camera.h:122` |
| `GetRenderVectorZ()` | `const Vec3` (render basis Z) | `Cry_Camera.h:123` |
| `CalculateRenderMatrices()` | `void` (recomputes matrices) | `Cry_Camera.h:214` |

### Asymmetric Frustum and Oblique Clip Plane

```cpp
void SetAsymmetry(float l, float r, float b, float t);
// source:Code/CryEngine/CryCommon/CryMath/Cry_Camera.h:128
```

Sets asymmetric frustum shift values. Used for stereo rendering and off-axis projections — `source:Code/CryEngine/CryCommon/CryMath/Cry_Camera.h:128`.

Asymmetry query methods: `GetAsymL()`, `GetAsymR()`, `GetAsymB()`, `GetAsymT()` — `source:Code/CryEngine/CryCommon/CryMath/Cry_Camera.h:144`.

```cpp
void GetAsymmetricFrustumParams(float& l, float& r, float& b, float& t) const;
void CalcAsymmetricFrustumVertices(Vec3 vout[8]) const;
// source:Code/CryEngine/CryCommon/CryMath/Cry_Camera.h:155-156
```

**Oblique clip plane** (e.g. for reflections):

| Method | Source |
|--------|--------|
| `SetObliqueClipPlane(const Plane& plane)` | `Cry_Camera.h:218` |
| `GetObliqueClipPlane()` | `Cry_Camera.h:219` |
| `SetObliqueClipPlaneEnabled(bool bEnabled)` | `Cry_Camera.h:221` |
| `IsObliqueClipPlaneEnabled()` | `Cry_Camera.h:222` |

**Z-Buffer range override**:

```cpp
void SetZRange(float zmin, float zmax);  // clamps to [0, 1]
float GetZRangeMin() const;
float GetZRangeMax() const;
// source:Code/CryEngine/CryCommon/CryMath/Cry_Camera.h:162-169
```

### Stereo / Multi-Camera

`CCamera` defines an `EEye` enum for stereo (VR) rendering — `source:Code/CryEngine/CryCommon/CryMath/Cry_Camera.h:65`:

| Enum Value    | Value | Description           |
|---------------|-------|-----------------------|
| `eEye_Left`   | 0     | Left eye              |
| `eEye_Right`  | 1     | Right eye             |
| `eEye_eCount` | 2     | Eye count             |
| `eEye_Both`   | 2     | Alias for eye count   |

```cpp
EEye GetEye() const;
void SetEye(EEye eye);
// source:Code/CryEngine/CryCommon/CryMath/Cry_Camera.h:211-212
```

Multi-camera support: a `PodArray<CCamera>* m_pMultiCamera` can be assigned. When set, the `*_M` culling variants test against all cameras in the array; an object is visible if at least one camera sees it — `source:Code/CryEngine/CryCommon/CryMath/Cry_Camera.h:334`.

Omni-camera flag: `bool m_bOmniCamera` (default `false`) marks the camera as a 360-degree omnidirectional camera — `source:Code/CryEngine/CryCommon/CryMath/Cry_Camera.h:341`.

Activation flag: `m_JustActivated` is set when the camera is activated in the current frame, used for disabling motion blur at camera cuts in cinematics — `source:Code/CryEngine/CryCommon/CryMath/Cry_Camera.h:339`.

```cpp
void SetJustActivated(const bool justActivated);
bool IsJustActivated() const;
// source:Code/CryEngine/CryCommon/CryMath/Cry_Camera.h:205-206
```

### Static Orientation Helpers

These static helper functions convert between Yaw-Pitch-Roll angles, orientation matrices, and view directions. Rotation order for orientation matrices is **Z-X-Y** (Z=YAW, X=PITCH, Y=ROLL) — `source:Code/CryEngine/CryCommon/CryMath/Cry_Camera.h:355`.

```cpp
static Matrix33 CreateOrientationYPR(const Ang3& ypr);
// source:Code/CryEngine/CryCommon/CryMath/Cry_Camera.h:97
```
Builds a 3x3 orientation matrix from YPR angles — `source:Code/CryEngine/CryCommon/CryMath/Cry_Camera.h:368`.

```cpp
static Ang3 CreateAnglesYPR(const Matrix33& m);
// source:Code/CryEngine/CryCommon/CryMath/Cry_Camera.h:98
```
Extracts YPR angles from a 3x3 matrix. Returns `Ang3(yaw, pitch, roll)` where `x=YAW`, `y=PITCH` (negative=looking down / positive=looking up), `z=ROLL` — `source:Code/CryEngine/CryCommon/CryMath/Cry_Camera.h:395`.

```cpp
static Ang3 CreateAnglesYPR(const Vec3& vdir, f32 r = 0);
// source:Code/CryEngine/CryCommon/CryMath/Cry_Camera.h:99
```
Computes YPR from a view direction vector and an optional roll. Note: roll cannot be extracted from a view vector alone — `source:Code/CryEngine/CryCommon/CryMath/Cry_Camera.h:411`.

```cpp
static Vec3 CreateViewdir(const Ang3& ypr);
// source:Code/CryEngine/CryCommon/CryMath/Cry_Camera.h:100
```
Computes a view direction vector from YPR angles — `source:Code/CryEngine/CryCommon/CryMath/Cry_Camera.h:426`.

```cpp
static Vec3 CreateViewdir(const Matrix33& m);
// source:Code/CryEngine/CryCommon/CryMath/Cry_Camera.h:101
```
Returns `m.GetColumn1()` (the forward axis of the matrix).

## Audio Listeners

Cameras can maintain an audio listener so that audio is played at the camera origin. Listeners are represented by the `CryAudio::IListener` interface and can be created via `CryAudio::IAudioSystem::CreateListener` — see [Audio](Audio.md).

> **Note:** The Camera Component (`Cry::DefaultComponents::CCameraComponent`) does **not** automatically add an Audio Listener Component. Audio listeners are a separate component (`Cry::Audio::DefaultComponents::CListenerComponent`) that users must add manually to the entity if audio should follow the camera — `source:Code/CryPlugins/CryDefaultEntities/Module/DefaultComponents/Audio/ListenerComponent.h:66`.

## Asynchronous Camera Injection (VR)

A big problem in Virtual Reality is the latency between the user moving the tracked headset, and the rendered picture on screen. Besides rendering as fast as possible, CRYENGINE uses **late-stage camera injection** to update the camera pose as late as possible in order to avoid a mismatch between the rendered frame and the new location of the headset.

This is achieved via `IHmdDevice::EnableLateCameraInjectionForCurrentFrame`, which stores an orientation to be applied late in the render thread — `source:Code/CryEngine/CryCommon/CrySystem/VR/IHMDDevice.h:326`:

```cpp
void EnableLateCameraInjectionForCurrentFrame(uint64 frameId,
    const std::pair<Quat, Vec3>& currentOrientation);
// source:Code/CryEngine/CryCommon/CrySystem/VR/IHMDDevice.h:327
```

The render thread can then retrieve the latest orientation via `GetOrientationForLateCameraInjection` — `source:Code/CryEngine/CryCommon/CrySystem/VR/IHMDDevice.h:328`. An additional `RequestAsyncCameraUpdate` can be called from any thread to get the most up-to-date camera transformation — `source:Code/CryEngine/CryCommon/CrySystem/VR/IHMDDevice.h:335`.

> **Note:** The original documentation referenced a non-existent `IHmdDevice::IAsyncCameraCallback` interface. This type does not exist in the 5.7 source; late camera injection is handled via the methods documented above.

## Camera Component

The `Cry::DefaultComponents::CCameraComponent` entity component automates camera handling. It is part of the CryDefaultEntities plug-in — `source:Code/CryPlugins/CryDefaultEntities/Module/DefaultComponents/Cameras/CameraComponent.h:37`.

**Behavior** (in `ProcessEvent`, on `ENTITY_EVENT_UPDATE` when not editing) — `source:Code/CryPlugins/CryDefaultEntities/Module/DefaultComponents/Cameras/CameraComponent.h:58`:
1. Copies the surface width/height and pixel aspect ratio from the current system camera
2. Calls `m_camera.SetFrustum(width, height, m_fieldOfView.ToRadians(), m_nearPlane, m_farPlane, pixelAspectRatio)`
3. Calls `m_camera.SetMatrix(GetWorldTransformMatrix())` to apply the entity's world transform
4. Calls `gEnv->pSystem->SetViewCamera(m_camera)` to set it as the main view camera
5. If an HMD device is present, calls `EnableLateCameraInjectionForCurrentFrame` with the entity's world transform

**Schematyc-exposed properties** — `source:Code/CryPlugins/CryDefaultEntities/Module/DefaultComponents/Cameras/CameraComponent.h:118`:

| Property        | Member            | Type                          | Default       | Source |
|-----------------|-------------------|-------------------------------|---------------|--------|
| Type            | `m_type`          | `ECameraType`                 | `Default`     | `CameraComponent.h:127` |
| Active          | `m_bActivateOnCreate` | `bool`                    | `true`        | `CameraComponent.h:128` |
| Near Plane      | `m_nearPlane`     | `Schematyc::Range<0, 32768>`  | `0.25f`       | `CameraComponent.h:129` |
| Far Plane       | `m_farPlane`      | `Schematyc::Range<0, 32768>`  | `1024.f`      | `CameraComponent.h:130` |
| Field of View   | `m_fieldOfView`   | `CClampedAngle<20, 360>`      | `70.0_degrees`| `CameraComponent.h:131` |

**Camera Type enum** — `source:Code/CryPlugins/CryDefaultEntities/Module/DefaultComponents/Cameras/CameraComponent.h:22`:

| Value             | Description                              |
|-------------------|------------------------------------------|
| `Default`         | A normal, one-directional camera         |
| `Omnidirectional` | Renders the full 360 view to screen       |

**Key methods**:

| Method | Description | Source |
|--------|-------------|--------|
| `Activate()` | Makes this camera the active one via `ICameraManager::SwitchCameraToActive` | `CameraComponent.h:134` |
| `IsActive()` | Returns whether this camera is the active one | `CameraComponent.h:140` |
| `EnableAutomaticActivation(bool)` | Sets `m_bActivateOnCreate` | `CameraComponent.h:145` |
| `SetNearPlane(float)` / `GetNearPlane()` | Accessors for near plane | `CameraComponent.h:148-149` |
| `SetFarPlane(float)` / `GetFarPlane()` | Accessors for far plane | `CameraComponent.h:151-152` |
| `SetFieldOfView(CAngle)` / `GetFieldOfView()` | Accessors for FOV | `CameraComponent.h:154-155` |
| `GetType()` | Returns `ECameraType` | `CameraComponent.h:157` |
| `GetCamera()` | Returns the internal `CCamera&` | `CameraComponent.h:159` |

**Component flags**: `Transform | Socket | Attach | ClientOnly` — `source:Code/CryPlugins/CryDefaultEntities/Module/DefaultComponents/Cameras/CameraComponent.h:125`.

**Room Scale VR Camera**: `Cry::DefaultComponents::VirtualReality::CRoomscaleCameraComponent` provides a dedicated Roomscale VR camera. It reads the HMD tracking state and applies it to the camera matrix, enabling late camera injection each frame. Its exposed properties are `Active`, `Near Plane` (default `0.25f`), `Far Plane` (default `1024.f`). It uses a fixed FOV of `75.0_degrees` — `source:Code/CryPlugins/CryDefaultEntities/Module/DefaultComponents/Cameras/VirtualReality/RoomscaleCamera.h:54`, `RoomscaleCamera.cpp:66`.

**ICameraManager**: The `ICameraManager` tracks all camera components and maintains a single active camera — `source:Code/CryPlugins/CryDefaultEntities/Module/DefaultComponents/Cameras/ICameraManager.h:13`:

| Method | Description | Source |
|--------|-------------|--------|
| `AddCamera(ICameraComponent*)` | Registers a camera | `ICameraManager.h:16` |
| `SwitchCameraToActive(ICameraComponent*)` | Sets the active camera | `ICameraManager.h:17` |
| `RemoveCamera(ICameraComponent*)` | Unregisters a camera | `ICameraManager.h:18` |
| `IsThisCameraActive(const ICameraComponent*)` | Checks if a camera is active | `ICameraManager.h:19` |

## Setting the Main Camera from Code

The main view camera is set via `ISystem`:

```cpp
virtual void SetViewCamera(CCamera& Camera) = 0;
virtual const CCamera& GetViewCamera() const = 0;
// source:Code/CryEngine/CryCommon/CrySystem/ISystem.h:1267-1270
```

`SetViewCamera` must be called before `Cry::IEnginePlugin::UpdateBeforeFinalizeCamera` in order to be set in time for occlusion culling and rendering. The camera is only considered final after `UpdateBeforeFinalizeCamera` has been executed, as user code may override it — `source:Code/CryEngine/CryCommon/CrySystem/ISystem.h:1266-1269`.

`Cry::IEnginePlugin::UpdateBeforeFinalizeCamera` is a virtual method called by the plugin manager each frame — `source:Code/CryEngine/CryCommon/CrySystem/ICryPlugin.h:61`:

```cpp
virtual void UpdateBeforeFinalizeCamera() {}
// source:Code/CryEngine/CryCommon/CrySystem/ICryPlugin.h:61
```

## Conclusion

This concludes the article on Cameras. You may be interested in:

- [Execution Order and Lifecycle](Execution%20Order%20and%20Lifecycle.md)
- [Input and Action Mapping](Input%20and%20Action%20Mapping.md)
- [Audio](Audio.md)
- [Entity Component Programming](../../Manual/Entities%20and%20Tools/Entity%20Component%20Programming.md)