# Audio

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/26871538
- Page ID: 26871538
- Breadcrumb: Entity > Audio
- Parent: Entity

## Content

##
Overview

Audio in the engine is managed by
[Cry Audio::IAudioSystem](/docs/static/engines/cryengine-5/categories/28704770/pages/29797061)
, an abstraction layer allowing for the playback of audio through any audio middleware such as
**
FMOD Studio
**
 and
**
WWise
**
. This allows mapping the middleware setup to an engine setup in the Audio Tool in the Editor, resulting in types we can query to play back audio at run-time.

Although using the audio system directly for playback of audio is possible, entities provide
[IEntityAudioComponent](/docs/static/engines/cryengine-5/categories/28704770/pages/29797269)
 as a way of handling audio that is automatically set to follow the entities’ position changes and properties.

##
Table of Contents

[Namespace](#namespace)
[API Types](#api-types)
[Listeners](#listeners)
[Triggers](#triggers)
[Parameters](#parameters)
[Switches and States](#switches-and-states)
[Preloads](#preloads)
[Environments](#environments)
[Conclusion](#conclusion)

##
Namespace

-
[CryAudio](/docs/static/engines/cryengine-5/categories/28704770/pages/29797059)

##
API Types

-
[CryAudio::IAudioSystem](/docs/static/engines/cryengine-5/categories/28704770/pages/29797061)

-
[IEntityAudioComponent](/docs/static/engines/cryengine-5/categories/28704770/pages/29797269)

-
[CryAudio::IListener](/docs/static/engines/cryengine-5/categories/28704770/pages/29797062)

-
[CryAudio::Impl::IListener](/docs/static/engines/cryengine-5/categories/28704770/pages/29797069)

-
[CryAudio::Impl::ITrigger](/docs/static/engines/cryengine-5/categories/28704770/pages/29797074)

-
[CryAudio::Impl::IParameter](/docs/static/engines/cryengine-5/categories/28704770/pages/29797071)

-
[CryAudio::Impl::IEnvironment](/docs/static/engines/cryengine-5/categories/28704770/pages/29797066)

##
Listeners

Listeners are typically automated with camera placement, in order to receive audio from the rendered location. Listeners are represented by the
[CryAudio::IListener](/docs/static/engines/cryengine-5/categories/28704770/pages/29797062)
 interface, and can be created using
[CryAudio::IAudioSystem::CreateListener](/docs/static/engines/cryengine-5/categories/28704770/pages/29797061)
. Once created, each listener's world-space transformation can be updated with
[CryAudio::IListener::SetTransformation](/docs/static/engines/cryengine-5/categories/28704770/pages/29797062)
.

Note that listener handling is automated by the Listener Component in the default components plug-in, see
Cry::Audio::DefaultComponents::CListenerComponent
. In addition, the Camera Component will automatically add a listener component that will match its transformation.

##
Triggers

Represented by the
[CryAudio::Impl::ITrigger](/docs/static/engines/cryengine-5/categories/28704770/pages/29797074)
 interface internally,
**
Triggers
**
 are merely containers that execute all controls that are connected to them. Any number of connections can be grouped into a single trigger.
Triggers can be executed with the
[IEntityAudioComponent::ExecuteTrigger](/docs/static/engines/cryengine-5/categories/28704770/pages/29797269)
 function.

[Example](/docs/static/engines/cryengine-5/categories/28704770/pages/29797269)

##
Parameters

Represented by the
[CryAudio::Impl::IParameter](/docs/static/engines/cryengine-5/categories/28704770/pages/29797071)
 interface internally,
**
Parameters
**

are used to seamlessly alter a parameter's value on which the Audio Middleware can receive and drive corresponding effects.
Parameters can be set using the
[IEntityAudioComponent::SetParameter](/docs/static/engines/cryengine-5/categories/28704770/pages/29797269)
 function.

[Example](/docs/static/engines/cryengine-5/categories/28704770/pages/29797269)

##
Switches and States

**
Switches
**
 can contain any number of states which can be set via code or Flow Graph. An example of a popular switch would be the surface type for character footsteps. The state of a switch can be set with the
[IEntityAudioComponent::SetSwitchState](/docs/static/engines/cryengine-5/categories/28704770/pages/29797269)
 function.

[Example](/docs/static/engines/cryengine-5/categories/28704770/pages/29797269)

##
Preloads

**
Preloads
**
 are requests to load audio specific files into memory. Any number of files can be grouped into a single request, avoiding disk reads at run-time.

##
Environments

**
Environments
**
 define areas that drive effects such as reverb or weapon reflections.
 Represented by the
[CryAudio::Impl::IEnvironment](/docs/static/engines/cryengine-5/categories/28704770/pages/29797066)
 interface,

##
Conclusion

This concludes the article on audio, you may be interested in:

-
[Areas and Triggers](Areas%20and%20Triggers.md)

-
[Slots, Geometry and Effects](Slots%2C%20Geometry%20and%20Effects.md)

-
[Characters and Animations](Characters%20and%20Animations.md)

-
[Networking](Networking.md)
