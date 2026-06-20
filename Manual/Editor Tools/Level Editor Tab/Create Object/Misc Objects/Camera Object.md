# Camera Object

- Breadcrumb: Editor Tools > Level Editor Tab > Create Object > Misc Objects > Camera Object
- Parent: Misc Objects

## Camera

A Camera Object is used to define custom views of your level. They can be triggered via Flow Graph and Track View, and are heavily used within animated sequences — `source:Code/Sandbox/EditorQt/Objects/CameraObject.h:27` (`CCameraObject : CEntityObject`).

![Image](https://www.cryengine.com/docs/static/attachments/36849618)

The Camera Object is a legacy editor object (distinct from the modern Camera Component). It is created from the **Create Object > Misc > Camera** panel — `source:Code/Sandbox/EditorQt/Objects/CameraObject.h:166` (`CCameraObjectClassDesc::Category() = "Misc"`, `ClassName() = "Camera"`).

### Parameters

| Parameter | Description | Default | Source |
|-----------|-------------|---------|--------|
| **FOV** | The field of view of the camera (angle in degrees). | `60°` | `CameraObject.cpp:41` |
| **NearZ** | The cut-off point closest to the camera (near clipping plane distance). | `0.1` (`DEFAULT_NEAR`) | `CameraObject.cpp:42` |
| **FarZ** | The max cut-off point of the camera (far clipping plane distance). | `1024` (`DEFAULT_FAR`) | `CameraObject.cpp:43` |
| **OmniCamera** | When enabled, renders the full 360° view to screen (omnidirectional camera). | `false` | `CameraObject.cpp:60`, `CameraObject.h:150` |

### Camera Shake Parameters

The Camera Object has two independent shake layers (A and B), each with the same set of parameters — `source:Code/Sandbox/EditorQt/Objects/CameraObject.h:134` (`mv_shakeParamsArray`).

| Parameter | Description | Default (A/B) | Source |
|-----------|-------------|----------------|--------|
| **Amplitude A/B** | `Vec3` — the strength of the shake effect on each axis. | `Vec3(1, 1, 1)` | `CameraObject.cpp:44` (A), `CameraObject.cpp:51` (B) |
| **Amplitude A/B Mult.** | Multiplier for the amplitude. | `0.0` | `CameraObject.cpp:45` (A), `CameraObject.cpp:52` (B) |
| **Frequency A/B** | `Vec3` — how often the effect plays on each axis. | `Vec3(1, 1, 1)` | `CameraObject.cpp:46` (A), `CameraObject.cpp:53` (B) |
| **Frequency A/B Mult.** | Multiplier for the frequency. | `0.0` | `CameraObject.cpp:47` (A), `CameraObject.cpp:54` (B) |
| **Noise A/B Amp. Mult.** | Adds noise to the amplitude value. | `0.0` | `CameraObject.cpp:48` (A), `CameraObject.cpp:55` (B) |
| **Noise A/B Freq. Mult.** | Adds noise to the frequency value. | `0.0` | `CameraObject.cpp:49` (A), `CameraObject.cpp:56` (B) |
| **Time Offset A/B** | Time offset for the shake effect. | `0.0` | `CameraObject.cpp:50` (A), `CameraObject.cpp:57` (B) |
| **Random Seed** | Applies random variation to the noise. | `0` | `CameraObject.cpp:59`, `CameraObject.h:149` |

> **Note:** Shake only affects rotation; it does not modify the camera position. The amplitude multipliers in Track View multiply the amplitude parameters defined here — see [Camera Shaking](../../../../Film%20and%20Cutscenes/Cinematics%20Overview/Track%20Cameras/Camera%20Shaking.md) for details.

## See Also

- [Camera Shaking](../../../../Film%20and%20Cutscenes/Cinematics%20Overview/Track%20Cameras/Camera%20Shaking.md) — Track View shake track details
- [Aiming a Camera](../../../../Film%20and%20Cutscenes/Cinematics%20Overview/Track%20Cameras/Aiming%20a%20Camera.md) — CameraTarget entity
- [Cameras Components](../../../../Entities%20and%20Tools/Entity%20Components/Entity%20Components%20(From%20Engine%20Version%205.6)/Cameras%20Components.md) — modern Camera Component (Entity Component system)
- [API Reference > Entity > Cameras](../../../../../API%20Reference/Entity/Cameras.md) — `CCamera` API