# SDL Mixer & Ambience

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/44964961
- Page ID: 44964961
- Breadcrumb: Audio > Audio Middleware > SDL Mixer Workflow > SDL Mixer & Ambience
- Parent: SDL Mixer Workflow

## Content

### Overview

This tutorial explains how to set up Ambient sounds with the SDL-Mixer and CRYENGINE.

### In This Topic

[In This Topic](#in-this-topic)[Setting up Ambiences in SDL-Mixer](#setting-up-ambiences-in-sdl-mixer)

### Setting up Ambiences in SDL-Mixer

For the implementation of Ambient sounds using SDL-Mixer in CRYENGINE, the *Audio Area Ambience* entity is used.

To set up an SDL-Mixer event for the playback of an Ambience:

- Enable Panning checkbox must be disabled (Required since the SDL-Mixer does not support sound spreading).
- Enable Distance Attenuation checkbox should be enabled and will attenuate the volume of the sound (Depending on the distance values used).

![Image](https://www.cryengine.com/docs/static/attachments/44968283)

Important
The Max Distance value in the SDL-Mixer properties must be equal to or lower than the RtpcDistance property of the *Audio Area Ambience e* ntity, if not then the sound begins to play and does not fade gradually.

![Image](https://www.cryengine.com/docs/static/attachments/44970763)

In order to learn how to setup your audio system Trigger inside CRYENGINE, please refer to the tutorial [Audio & Ambience](../../Audio%20Overview/Audio%20%26%20Ambience.md).

Please note that there are certain differences in the implementation approach for Ambiences in a level. This is due to feature based limitations of the SDL-Mixer.
You do not need to specify a RTPC or an Environment in the entity properties as the SDL-Mixer does not support these advanced functionalities. If you need more control over the audio content of your project and want to make use of advanced features, it is recommended to use a professional audio middleware such as the [Wwise](../Wwise%20Workflow.md) or [FMOD Studio](../FMOD%20Studio%20Workflow.md) implementations in CRYENGINE.
Learn more about the SDL Mixer Console Commands within CRYENGINE in [SDL Mixer Console Commands](SDL%20Mixer%20Console%20Commands.md).
