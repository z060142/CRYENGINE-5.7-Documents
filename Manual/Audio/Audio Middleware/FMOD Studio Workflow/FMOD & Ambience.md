# FMOD & Ambience

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/44964948
- Page ID: 44964948
- Breadcrumb: Audio > Audio Middleware > FMOD Studio Workflow > FMOD & Ambience
- Parent: FMOD Studio Workflow

## Content

## Overview

This tutorial explains how to setup Ambient sounds in your FMOD Studio Project and CRYENGINE.

### Setting up Ambiences in FMOD Studio and CRYENGINE

#### Setting up Ambient Sounds in FMOD Studio

CRYENGINE offers two audio entities which can be used to setup ambient sounds in your Level. They are called *Audio Area Ambience* and* Audio Area entity,* and both are attached to a shape in the level to define the area in which the sound is being played.

These entities are different from the *Audio Trigger Spot,* as *Audio Area Ambience* and * Audio Area Entity* do not use the standard FMOD Studio Attenuation. Therefore, their setup in FMOD Studio has to be different in order to create a working implementation of your audio content.

##### Setting up a Basic Ambient Sound Object

You need to import a ***.wav*** file in FMOD Studio that contains your ambient sounds and make sure that it's looped by adding a New Loop Region in its Timeline.

![Image](https://www.cryengine.com/docs/static/attachments/44968253)

Now, select Add Parameter option which lets you to add a parameter for your sound event called *area_fade_distance* with a range from 0 to 1 (Initial value should be 1).

![Image](https://www.cryengine.com/docs/static/attachments/44968254)

You can enter a desired name for the parameter, and you can set the connected audio system Control with Real-Time-Parameter-Controls (RTPC) to be used on each entity. In the example below, we have used the name *area_fade_distance*.

This parameter will be used later on in CRYENGINE to attenuate or increase the sound when the object is moved closer or further away from an area connected to the audio entity. Therefore, make sure to connect the newly created *area_fade_distance* parameter to a global audio system RTPC within the [Audio Controls Editor](../../../Editor%20Tools/Audio%20Controls%20Editor.md).

When you set the parameter *area_fade_distance* to the default value =1, you can preview your ambience in the Audio Controls Editor using the Execute Trigger functionality.

In the *area_fade_distance* parameter tab, add volume automation to the sound on its Master Track. When the parameter value is set to 0, the sound should be inaudible and at 1 it should have its desired volume.

You can turn-off the Distance Attenuation in the Deck area. Additionally the 3D Panner can also be automated to hear the sound in 3D when you approach the shape. When you get closer to the shape, the sound surrounds you more.

After this your setup should look like the one displayed in the screenshot below:

![Image](https://www.cryengine.com/docs/static/attachments/44968255)

It is recommended to do the automation on the Master Track and attenuate it up to 0 db. Then adjust the volume within the audio track of the sound.

Now assign the sound to a bank, regenerate your Soundbanks, and then connect the FMOD Studio Event and the RTPC in the Audio Controls Editor as explained [here](../../../Editor%20Tools/Audio%20Controls%20Editor.md).

For more information on how to setup your created FMOD Studio Event inside CRYENGINE, please refer the following tutorial:[/docs/static/engines/cryengine-5/categories/23756816](/docs/static/engines/cryengine-5/categories/23756816)[Audio & Ambience](../../Audio%20Overview/Audio%20%26%20Ambience.md).
