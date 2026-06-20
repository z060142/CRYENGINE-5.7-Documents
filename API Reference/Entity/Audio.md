# Audio

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/26871538
- Page ID: 26871538
- Breadcrumb: Entity > Audio
- Parent: Entity

## Content

##
Overview

Audio in the engine is managed by
[/docs/static/engines/cryengine-5/categories/28704770/pages/29797061](
Cry Audio::IAudioSystem
)
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
[/docs/static/engines/cryengine-5/categories/28704770/pages/29797269](
IEntityAudioComponent
)
 as a way of handling audio that is automatically set to follow the entities’ position changes and properties.

##
Table of Contents

[#namespace](
Namespace
)
[#api-types](
API Types
)
[#listeners](
Listeners
)
[#triggers](
Triggers
)
[#parameters](
Parameters
)
[#switches-and-states](
Switches and States
)
[#preloads](
Preloads
)
[#environments](
Environments
)
[#conclusion](
Conclusion
)

##
Namespace

-
[/docs/static/engines/cryengine-5/categories/28704770/pages/29797059](
CryAudio
)

##
API Types

-
[/docs/static/engines/cryengine-5/categories/28704770/pages/29797061](
CryAudio::IAudioSystem
)

-
[/docs/static/engines/cryengine-5/categories/28704770/pages/29797269](
IEntityAudioComponent
)

-
[/docs/static/engines/cryengine-5/categories/28704770/pages/29797062](
CryAudio::IListener
)

-
[/docs/static/engines/cryengine-5/categories/28704770/pages/29797069](
CryAudio::Impl::IListener
)

-
[/docs/static/engines/cryengine-5/categories/28704770/pages/29797074](
CryAudio::Impl::ITrigger
)

-
[/docs/static/engines/cryengine-5/categories/28704770/pages/29797071](
CryAudio::Impl::IParameter
)

-
[/docs/static/engines/cryengine-5/categories/28704770/pages/29797066](
CryAudio::Impl::IEnvironment
)

##
Listeners

Listeners are typically automated with camera placement, in order to receive audio from the rendered location. Listeners are represented by the
[/docs/static/engines/cryengine-5/categories/28704770/pages/29797062](
CryAudio::IListener
)
 interface, and can be created using
[/docs/static/engines/cryengine-5/categories/28704770/pages/29797061](
CryAudio::IAudioSystem::CreateListener
)
. Once created, each listener's world-space transformation can be updated with
[/docs/static/engines/cryengine-5/categories/28704770/pages/29797062](
CryAudio::IListener::SetTransformation
)
.

Note that listener handling is automated by the Listener Component in the default components plug-in, see
Cry::Audio::DefaultComponents::CListenerComponent
. In addition, the Camera Component will automatically add a listener component that will match its transformation.

##
Triggers

Represented by the
[/docs/static/engines/cryengine-5/categories/28704770/pages/29797074](
CryAudio::Impl::ITrigger
)
 interface internally,
**
Triggers
**
 are merely containers that execute all controls that are connected to them. Any number of connections can be grouped into a single trigger.
Triggers can be executed with the
[/docs/static/engines/cryengine-5/categories/28704770/pages/29797269](
IEntityAudioComponent::ExecuteTrigger
)
 function.

[/docs/static/engines/cryengine-5/categories/28704770/pages/29797269](
Example
)

##
Parameters

Represented by the
[/docs/static/engines/cryengine-5/categories/28704770/pages/29797071](
CryAudio::Impl::IParameter
)
 interface internally,
**
Parameters
**

are used to seamlessly alter a parameter's value on which the Audio Middleware can receive and drive corresponding effects.
Parameters can be set using the
[/docs/static/engines/cryengine-5/categories/28704770/pages/29797269](
IEntityAudioComponent::SetParameter
)
 function.

[/docs/static/engines/cryengine-5/categories/28704770/pages/29797269](
Example
)

##
Switches and States

**
Switches
**
 can contain any number of states which can be set via code or Flow Graph. An example of a popular switch would be the surface type for character footsteps. The state of a switch can be set with the
[/docs/static/engines/cryengine-5/categories/28704770/pages/29797269](
IEntityAudioComponent::SetSwitchState
)
 function.

[/docs/static/engines/cryengine-5/categories/28704770/pages/29797269](
Example
)

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
[/docs/static/engines/cryengine-5/categories/28704770/pages/29797066](
CryAudio::Impl::IEnvironment
)
 interface,

##
Conclusion

This concludes the article on audio, you may be interested in:

-
[/docs/static/engines/cryengine-5/categories/23756813/pages/26871540](
Areas and Triggers
)

-
[/docs/static/engines/cryengine-5/categories/23756813/pages/26216230](
Slots, Geometry and Effects
)

-
[/docs/static/engines/cryengine-5/categories/23756813/pages/26216226](
Characters and Animations
)

-
[/docs/static/engines/cryengine-5/categories/23756813/pages/26216232](
Networking
)
