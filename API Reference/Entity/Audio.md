# Audio

- Breadcrumb: Entity > Audio
- Parent: Entity

## Content

## Overview

Audio in the engine is managed by `CryAudio::IAudioSystem`, an abstraction layer allowing for the playback of audio through any audio middleware such as **FMOD Studio** and **Wwise** — `source:Code/CryEngine/CryCommon/CryAudio/IAudioSystem.h:19` (`struct IAudioSystem`). This allows mapping the middleware setup to an engine setup in the Audio Tool in the Editor, resulting in types we can query to play back audio at run-time.

Although using the audio system directly for playback of audio is possible, entities provide `IEntityAudioComponent` as a way of handling audio that is automatically set to follow the entities' position changes and properties.

## Table of Contents

- [Namespace](#namespace)
- [API Types](#api-types)
- [Listeners](#listeners)
- [Triggers](#triggers)
- [Parameters](#parameters)
- [Switches and States](#switches-and-states)
- [Preloads](#preloads)
- [Environments](#environments)
- [Conclusion](#conclusion)

## Namespace

- `CryAudio` — `source:Code/CryEngine/CryCommon/CryAudio/IAudioInterfacesCommonData.h`

## API Types

| Type | Description | Source |
|------|-------------|--------|
| `CryAudio::IAudioSystem` | Central audio system interface | `IAudioSystem.h:19` |
| `IEntityAudioComponent` | Entity component for audio playback | `Code/CryEngine/CryCommon/CryEntitySystem/IEntityAudioComponent.h` |
| `CryAudio::IListener` | Audio listener interface | `IListener.h:19` |
| `CryAudio::Impl::IListener` | Middleware-side listener interface | `Code/CryEngine/CryCommon/CryAudio/Impl/IListener.h` |
| `CryAudio::Impl::ITrigger` | Middleware-side trigger | `Code/CryEngine/CryCommon/CryAudio/Impl/ITrigger.h` |
| `CryAudio::Impl::IParameter` | Middleware-side parameter | `Code/CryEngine/CryCommon/CryAudio/Impl/IParameter.h` |
| `CryAudio::Impl::IEnvironment` | Middleware-side environment | `Code/CryEngine/CryCommon/CryAudio/Impl/IEnvironment.h` |

## Listeners

Listeners are typically placed at the camera location, in order to receive audio from the rendered location. Listeners are represented by the `CryAudio::IListener` interface — `source:Code/CryEngine/CryCommon/CryAudio/IListener.h:19`, and can be created using `CryAudio::IAudioSystem::CreateListener` — `source:Code/CryEngine/CryCommon/CryAudio/IAudioSystem.h:481`. Once created, each listener's world-space transformation can be updated with `CryAudio::IListener::SetTransformation` — `source:Code/CryEngine/CryCommon/CryAudio/IListener.h:38`.

> **Note:** Listener handling is automated by the **Listener Component** in the default components plug-in, see `Cry::Audio::DefaultComponents::CListenerComponent` — `source:Code/CryPlugins/CryDefaultEntities/Module/DefaultComponents/Audio/ListenerComponent.h:66`. The **Camera Component** (`Cry::DefaultComponents::CCameraComponent`) does **not** automatically add a listener component. If you want audio to follow a camera, add a Listener Component to the same entity manually — see [Cameras](Cameras.md).

## Triggers

Represented by the [CryAudio::Impl::ITrigger](/docs/static/engines/cryengine-5/categories/28704770/pages/29797074) interface internally, **Triggers** are merely containers that execute all controls that are connected to them. Any number of connections can be grouped into a single trigger. Triggers can be executed with the [IEntityAudioComponent::ExecuteTrigger](/docs/static/engines/cryengine-5/categories/28704770/pages/29797269) function.

[Example](/docs/static/engines/cryengine-5/categories/28704770/pages/29797269)

## Parameters

Represented by the [CryAudio::Impl::IParameter](/docs/static/engines/cryengine-5/categories/28704770/pages/29797071) interface internally, **Parameters** are used to seamlessly alter a parameter's value on which the Audio Middleware can receive and drive corresponding effects. Parameters can be set using the [IEntityAudioComponent::SetParameter](/docs/static/engines/cryengine-5/categories/28704770/pages/29797269) function.

[Example](/docs/static/engines/cryengine-5/categories/28704770/pages/29797269)

## Switches and States

**Switches** can contain any number of states which can be set via code or Flow Graph. An example of a popular switch would be the surface type for character footsteps. The state of a switch can be set with the [IEntityAudioComponent::SetSwitchState](/docs/static/engines/cryengine-5/categories/28704770/pages/29797269) function.

[Example](/docs/static/engines/cryengine-5/categories/28704770/pages/29797269)

## Preloads

**Preloads** are requests to load audio specific files into memory. Any number of files can be grouped into a single request, avoiding disk reads at run-time.

## Environments

**Environments** define areas that drive effects such as reverb or weapon reflections. Represented by the [CryAudio::Impl::IEnvironment](/docs/static/engines/cryengine-5/categories/28704770/pages/29797066) interface,

## Conclusion

This concludes the article on audio, you may be interested in:

- [Areas and Triggers](Areas%20and%20Triggers.md)
- [Slots, Geometry and Effects](Slots%2C%20Geometry%20and%20Effects.md)
- [Characters and Animations](Characters%20and%20Animations.md)
- [Networking](Networking.md)
