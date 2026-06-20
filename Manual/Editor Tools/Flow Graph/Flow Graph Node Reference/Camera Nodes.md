# Camera Nodes

- Breadcrumb: Editor Tools > Flow Graph > Flow Graph Node Reference > Camera Nodes
- Parent: Flow Graph Node Reference

> **Note:** Flow Graph is a legacy visual scripting system. These nodes are still registered in the engine source but Flow Graph itself is deprecated. For new projects, use Schematyc or C++ instead.

## GetTransform

`Camera:GetTransform` — Returns the transform for the player camera — `source:Code/CryEngine/CryFlowGraph/FlowSystem/Nodes/FlowCameraNodes.cpp:459` (`CFlowNode_CameraTransform`), registered at `FlowCameraNodes.cpp:526`.

![Image](https://www.cryengine.com/docs/static/attachments/28901206)

### Output Ports

| Output Port | Description | Source |
|-------------|-------------|--------|
| **Pos** | Position of the camera (`Vec3`) | `FlowCameraNodes.cpp:490` |
| **Dir** | View direction of the camera (`Vec3`) | `FlowCameraNodes.cpp:491` |
| **Rot** | Rotation of the camera in degrees (`Vec3`) | `FlowCameraNodes.cpp:492` |

### Input Ports

| Input Port | Description | Source |
|------------|-------------|--------|
| **Get** | Trigger to retrieve the current camera position, direction, and rotation | `FlowCameraNodes.cpp:486` |

The node reads from `GetISystem()->GetViewCamera()` and outputs `GetPosition()`, `GetViewdir()`, and `RAD2DEG(GetAngles())` — `source:Code/CryEngine/CryFlowGraph/FlowSystem/Nodes/FlowCameraNodes.cpp:510-515`.

## View

`Camera:View` — Creates a custom view linked to an entity — `source:Code/CryEngine/CryFlowGraph/FlowSystem/Nodes/FlowCameraNodes.cpp:309` (`CFlowNode_CameraView`), registered at `FlowCameraNodes.cpp:525`.

![Image](https://www.cryengine.com/docs/static/attachments/28901209)

### Input Ports

| Input Port | Description | Default | Source |
|------------|-------------|---------|--------|
| **Enable** | Enable custom view. | — | `FlowCameraNodes.cpp:359` |
| **Disable** | Disable custom view. | — | `FlowCameraNodes.cpp:360` |
| **FOV** | Field of View used by the custom view (degrees). | `60.0` | `FlowCameraNodes.cpp:361` |
| **Blend** | Enables FOV, Position and Rotation blending. | `false` | `FlowCameraNodes.cpp:362` |
| **BlendFOVSpeed** | How fast to blend in the FOV offset. | `5.0` | `FlowCameraNodes.cpp:363` |
| **BlendFOVOffset** | FOV offset. | `0.0` | `FlowCameraNodes.cpp:364` |
| **BlendPosSpeed** | How fast to blend in the position offset. | `5.0` | `FlowCameraNodes.cpp:365` |
| **BlendPosOffset** | Position offset (`Vec3`). | `Vec3(0,0,0)` | `FlowCameraNodes.cpp:366` |
| **BlendRotSpeed** | How fast to blend in the rotation offset. | `10.0` | `FlowCameraNodes.cpp:367` |
| **BlendRotOffset** | Rotation offset (`Vec3`). | `Vec3(0,0,0)` | `FlowCameraNodes.cpp:368` |

This node has the `EFLN_TARGET_ENTITY` flag — the camera location will be based off the linked entity's pivot point — `source:Code/CryEngine/CryFlowGraph/FlowSystem/Nodes/FlowCameraNodes.cpp:372`. The node creates a view via `IViewSystem::CreateView()` and links it to the target entity — `source:Code/CryEngine/CryFlowGraph/FlowSystem/Nodes/FlowCameraNodes.cpp:434-455`.

## ViewShakeEx

`Camera:ViewShakeEx` — Enables a camera shake on the player's view — `source:Code/CryEngine/CryFlowGraph/FlowSystem/Nodes/FlowCameraNodes.cpp:10` (`CFlowNode_CameraViewShakeEx`), registered at `FlowCameraNodes.cpp:524`.

![Image](https://www.cryengine.com/docs/static/attachments/28901210)

### Input Ports

| Input Port | Description | Default | Source |
|------------|-------------|---------|--------|
| **Trigger** | Trigger input to start the effect. | — | `FlowCameraNodes.cpp:114` |
| **Restrict** | Restriction. Choices: `None=0`, `NoVehicle=1`, `InVehicle=2`. | `None` | `FlowCameraNodes.cpp:115` |
| **View** | Which view to use. Choices: `FirstPerson=0`, `Current=1` (might be Trackview). | `FirstPerson` | `FlowCameraNodes.cpp:116` |
| **GroundOnly** | If set, will only trigger if the player is on the ground. | `false` | `FlowCameraNodes.cpp:117` |
| **Smooth** | If true, the camera movement will be curved (suitable for breathing). If false, the camera will move linearly (violent shake). | `false` | `FlowCameraNodes.cpp:118` |
| **Angle** | `Vec3` — make the camera rotate back & forth within specified angles (degrees). | `Vec3(0.7, 0.7, 0.7)` | `FlowCameraNodes.cpp:119` |
| **Shift** | `Vec3` — move the camera's view position. | `Vec3(0.01, 0.01, 0.01)` | `FlowCameraNodes.cpp:120` |
| **Frequency** | How quickly the camera will move/rotate between the specified ranges. | `12.0` | `FlowCameraNodes.cpp:121` |
| **Randomness** | Add some random values over the top of the specified Shift & Angle. | `1.0` | `FlowCameraNodes.cpp:122` |
| **Distance** | Distance between the camera and the shake source. If an entity is associated, distance from that entity to the camera is used instead. | `0.0` | `FlowCameraNodes.cpp:123` |
| **RangeMin** | Distance where the camera shake is strongest. | `0.0` | `FlowCameraNodes.cpp:124` |
| **RangeMax** | Distance where the camera shake is null. | `30.0` | `FlowCameraNodes.cpp:125` |
| **SustainDuration** | Duration of the non-fading part (total = FadeIn + Sustain + FadeOut). `-1` = permanent. | `0.0` | `FlowCameraNodes.cpp:126` |
| **FadeInDuration** | How long to ramp effect up to maximum (seconds). | `0.0` | `FlowCameraNodes.cpp:127` |
| **FadeOutDuration** | How long to fade out the effect (seconds). | `3.0` | `FlowCameraNodes.cpp:128` |
| **Stop** | Trigger input to stop the effect (will fade out). | — | `FlowCameraNodes.cpp:129` |
| **Preset** | Choose from pre-made effects. When used, all parameter inputs are ignored. | `NoPreset` | `FlowCameraNodes.cpp:131-134` |

### Presets

Four presets are available — `source:Code/CryEngine/CryFlowGraph/FlowSystem/Nodes/FlowCameraNodes.cpp:299`:

| Preset | Description |
|--------|-------------|
| `NoPreset` (0) | No preset; use input parameters directly. |
| `DistantExplosion` (1) | Distant explosion shake. |
| `CloseExplosion` (2) | Close explosion shake. |
| `SmallTremor` (3) | Small tremor shake. |
| `SmallTremor2` (4) | Alternate small tremor shake. |

> **Note:** The shake amount is scaled by distance: `amount = clamp((rangeMax - distance) / (rangeMax - rangeMin), 0, 1)`. Both `shakeAngle` and `shakeShift` are multiplied by this amount — `source:Code/CryEngine/CryFlowGraph/FlowSystem/Nodes/FlowCameraNodes.cpp:219-222`.

> **Note:** This node has the `EFLN_TARGET_ENTITY` flag — if an entity is provided, its position is used for distance calculations instead of the raw `Distance` input — `source:Code/CryEngine/CryFlowGraph/FlowSystem/Nodes/FlowCameraNodes.cpp:137,211-215`.

## Deprecated Nodes

The following Camera nodes are deprecated and no longer registered in the engine core. `OverrideFOV` and `ScreenToWorld` still exist in the GameSDK codebase but are not part of the engine — `source:Code/GameSDK/GameDll/Nodes/FlowActorSensor.cpp:1765,1770`:

- `Camera:AutoFocusDoF` — removed
- `Camera:Camera` — removed
- `Camera:YPR` — removed
- `Camera:ViewShake` — removed (replaced by `ViewShakeEx`)
- `Camera:OverrideFOV` — `source:Code/GameSDK/GameDll/Nodes/FlowActorSensor.cpp:855` (`CFlowNode_OverrideFOV`), registered at line 1765 (GameSDK only)
- `Camera:ScreenToWorld` — `source:Code/GameSDK/GameDll/Nodes/FlowActorSensor.cpp:1770` (`CFlowNode_ScreenPosToWorldPos`, GameSDK only)

## See Also

- [API Reference > Entity > Cameras](../../../../../API%20Reference/Entity/Cameras.md) — `CCamera` API
- [Camera Object](../../../Level%20Editor%20Tab/Create%20Object/Misc%20Objects/Camera%20Object.md) — legacy Camera Object
- [Camera Shaking](../../../../Film%20and%20Cutscenes/Cinematics%20Overview/Track%20Cameras/Camera%20Shaking.md) — Track View camera shake