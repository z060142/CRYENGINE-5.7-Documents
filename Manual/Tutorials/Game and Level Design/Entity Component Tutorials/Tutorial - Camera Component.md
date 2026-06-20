# Tutorial - Camera Component

- Breadcrumb: Tutorials > Game and Level Design > Entity Component Tutorials > Tutorial - Camera Component
- Parent: Entity Component Tutorials

## Using the Camera Component

This tutorial explains the Camera Component. The Camera Component adds a camera to the scene which can then be activated from either C++/C# or Schematyc — `source:Code/CryPlugins/CryDefaultEntities/Module/DefaultComponents/Cameras/CameraComponent.h:37`. See also [Entity Components](../../../Entities%20and%20Tools/Entity%20Components.md) and [Cameras Components](../../../Entities%20and%20Tools/Entity%20Components/Entity%20Components%20(From%20Engine%20Version%205.6)/Cameras%20Components.md) for the full list of attributes.

1. First create a new entity with a Camera Component. Click on the "Empty Entity" button in the "Create Object" panel and place the entity in the level. After that, select the entity and click on the "Add Component" button in the "Properties" panel and select the Camera Component.

   *Creating an empty entity and adding the Camera Component to it.*
   ![Image](https://www.cryengine.com/docs/static/attachments/28254508)

2. The Camera Component now exposes all attributes and we can start adjusting them. We can change the field of view of the camera or change the offset of the near plane, which is responsible for culling objects too close to the camera. To change any value, click in the attribute box and either drag the value or type in the wanted value.

   *Changing the field of view.*
   ![Image](https://www.cryengine.com/docs/static/attachments/28254509)

   The available attributes are — `source:Code/CryPlugins/CryDefaultEntities/Module/DefaultComponents/Cameras/CameraComponent.h:118`:

   | Attribute | Description | Default |
   |-----------|-------------|---------|
   | **Type** | `Default` (one-directional) or `Omnidirectional` (360°). | `Default` |
   | **Active** | Whether this camera should be active by default. | `true` |
   | **Near Plane** | Distance from camera to start rendering (meters). | `0.25` |
   | **Far Plane** | Distance from camera to stop rendering (meters). | `1024` |
   | **Field of View** | Vertical FOV angle, clamped to 20–360 degrees. | `70°` |

3. Above the "Field of View" attribute is the "Active" attribute which determines if the camera should be active by default. An important thing to note is that **only one camera can be active at the same time** — `source:Code/CryPlugins/CryDefaultEntities/Module/DefaultComponents/Cameras/CameraManager.h:22` (`SwitchCameraToActive` sets a single `m_pActive`). If someone creates a new camera and activates it, that one will be used by the engine. The Camera Component can also be moved or rotated by adjusting the values of the "Transformation" attribute.

   *Changing the camera transformation.*
   ![Image](https://www.cryengine.com/docs/static/attachments/28254510)

## Adding an Audio Listener

> **Note:** The original version of this tutorial stated that an Audio Listener Component would appear automatically after adding the Camera Component. This is **incorrect** — the Camera Component does **not** automatically add an Audio Listener — `source:Code/CryPlugins/CryDefaultEntities/Module/DefaultComponents/Cameras/CameraComponent.h` (no audio listener logic).

If you want audio to be played from the camera position, you need to manually add an **Audio Listener** Component (`Cry::Audio::DefaultComponents::CListenerComponent`) to the same entity — `source:Code/CryPlugins/CryDefaultEntities/Module/DefaultComponents/Audio/ListenerComponent.h:66`.

To add it: select the camera entity, click "Add Component" in the "Properties" panel, and choose "Audio Listener". The listener will automatically follow the entity's transformation.

## See Also

- [Cameras Components](../../../Entities%20and%20Tools/Entity%20Components/Entity%20Components%20(From%20Engine%20Version%205.6)/Cameras%20Components.md) — full Camera Component reference
- [API Reference > Entity > Cameras](../../../../API%20Reference/Entity/Cameras.md) — `CCamera` API
- [Entity Components](../../../Entities%20and%20Tools/Entity%20Components.md) — component system overview