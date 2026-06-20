# Wwise & Reverb

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/44965000
- Page ID: 44965000
- Breadcrumb: Audio > Audio Middleware > Wwise Workflow > Wwise & Reverb
- Parent: Wwise Workflow

## Content

##
Overview

This section describes how to setup Reverbs in levels. In CRYENGINE reverbs are called Environments. To learn more about audio system Environments in CRYENGINE, please have a look in the chapter
[/docs/static/engines/cryengine-5/categories/23756816/pages/44964924](
Audio & Reverbs*
)
.

##
Setting up Reverbs in Wwise

You can create an Auxiliary Bus in Wwise and assign an effect to that bus, which in our case will be a Reverb.

[Image: /docs/static/attachments/52592659]

After the project has been saved, use the
[/docs/static/engines/cryengine-5/categories/23756816/pages/51347481](
Audio Controls Editor
)

to connect the Wwise Auxiliary Bus to an audio system Environment. You can use an
*
 Area Shape
*
 and
*
Audio Area Entity
*
 or
*
Audio Area Ambience
*
entities as described in the chapter
[/docs/static/engines/cryengine-5/categories/23756816/pages/44964884](
Audio & Ambience
)
.

*
[Image: /docs/static/attachments/52592660]
*

In the
*
Audio Area Entity
*
 or
*
Audio Area Ambience
*
 properties, select the
*
Audio Environment Name
*
 in the audio system Environment that is connected to the Auxiliary Bus, and set the
*
EnvironmentDistance
*
. This is the distance in meters from the edge of the assigned shape where the fading of the Environment (Reverb) begins.

It is possible to have Environments (Reverbs) without ambient sounds and vice versa. However, in most cases it makes sense to use both in the same entity.
EnvironmentDistance and Rtpc/FadeDistance
The
*
FadeDistance
*
 (on the
*
Audio Area Entity
*
) or
*
RtpcDistance
*
 (on
*
the Audio Area Ambience
*
) parameters define the maximum distance over which both the fade or RTPC value and the Environment (Reverb) level will be updated.
In order for the Environment (Reverb) values to be updated correctly for the entities approaching and leaving an area, then the
*
EnvironmentDistance
*
 parameter should not exceed the
*
FadeDistance
*
 or
*
RtpcDistance.
*
For Example, if your
*
EnvironmentDistance
*
 is 10 and the
*
RtpcDistance
*
 is 5, the
*
EnvironmentDistance
*
 will return to zero when the
*
RtpcDistance
*
 reaches the value of
5
.
In most implementation cases, the
*
EnvironmentDistance
*
is set lower or equal to the
*
RtpcDistance
*
 to create realistic Ambiences and Environments (Reverbs).
If it is necessary to create a higher
*
EnvironmentDistance
*
than
*
RtpcDistance,
*
 this can be achieved by using two separate audio entities to control the Environment (Reverb) and play the sound in the connected shape.

After setting the Environment (Reverb) in the
*
Audio Area Entitiy
*
 or
*
Audio Area Ambience
*
properties, the audio is sent to the auxiliary in Wwise when approaching the attached
*
Area Shape
*
.

However, for this functionality to work, the
*
 game-defined auxiliary sends

*
in Wwise have to be enabled (they are disabled by default). By enabling this functionality, it allows you to select which sounds should be affected by the audio system Environments (Reverbs) and to also adjust (separately) the
*
send volume
*
 for each sound in Wwise.

[Image: /docs/static/attachments/52592661]

The game-defined auxiliaries can be found in the general settings of the
Sound Property Editor
 in Wwise.

You can define different volumes for the
*
game-defined auxiliary sends
*
per sound object in Wwise. These values also can be assigned to a
*
GameParameter
*
 which can be controlled via an RTPC Flownode.
Remember that you can also map Game Parameters to an audio system
*
 Environment
*
 in the Audio Controls Editor.
