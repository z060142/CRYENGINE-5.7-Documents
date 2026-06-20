# Wwise & Ambience

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/44964994
- Page ID: 44964994
- Breadcrumb: Audio > Audio Middleware > Wwise Workflow > Wwise & Ambience
- Parent: Wwise Workflow

## Content

![Image](https://www.cryengine.com/docs/static/attachments/44964995)

##
Overview

##
Sections

This article explains how to set up Ambient sounds in your Wwise project and CRYENGINE.
CRYENGINE offers two audio entities which can be used to setup ambient sounds in your level. They are called
*
Audio Area Ambience
*
 and
*
 Audio Area Entity,
*
 and both are attached to a shape in the level to define the area in which the sound is being played.

These entities are different from the
*
Audio Trigger Spot,
*
as
*
Audio Area Ambience
*
 and
*
Audio Area Entity
*
 do not use the standard
[Wwise Attenuations](Wwise%20%26%20SpotFX.md)
. Therefore, their setup in Wwise has to be different in order to create a working implementation of your audio content.

[Sections](#sections)
[Preparing the Wwise Project to Work with Area Sounds](#preparing-the-wwise-project-to-work-with-area-sounds)
[Setting up a Basic Ambient Sound Object](#setting-up-a-basic-ambient-sound-object)

##
Preparing the Wwise Project to Work with Area Sounds

As initial step to setup your Wwise Project to support Ambiences in CRYENGINE, you need to go to the
GameSyncs
 tab and create a new
*
Game Parameter
*
 and rename it as
*
area_fade_distance
*
.

![Image](https://www.cryengine.com/docs/static/attachments/44968403)

You can enter a desired name for the
*
Game Parameter
*
, and you can set the connected audio system Control with Real-Time-Parameter-Controls (RTPC) to be used on each entity.

In the example below, we have used the name
*
area_fade_distance
*
.

Select the newly created
*
Game Parameter
*
 and set its range in the Property Editor from 0 to 1 (Default value =1).

![Image](https://www.cryengine.com/docs/static/attachments/44968405)

This parameter will be used later-on in CRYENGINE to attenuate or increase the sound when the object is moved closer or further away from an area connected to the audio entity. Therefore, make sure to connect the newly created
*
area_fade_distance
*
 Game Parameter to a global audio system RTPC within the

[Audio Controls Editor](../../../Editor%20Tools/Audio%20Controls%20Editor.md)
.

When you set the parameter
*
area_fade_distance
*
 to the default value =1, you can preview your ambience in the
Audio Controls Editor
 using the
Execute Trigger
 functionality.

##
Setting up a Basic Ambient Sound Object

You need to import a
*
*.wav
*
 file in Wwise that contains your ambient sounds and make sure that the resulting
Sound Object Play Mode
 is set to
Continuous
 and
Loop Infinite
.

After you have performed the above steps, select the sound object in Wwise and then click on the RTPC tab in the Property Editor. You can now click the
![Image](https://www.cryengine.com/docs/static/attachments/44968406)
 button (Underneath the Y axis column) and select the
Voice Volume
 property from the list as in below
*
Pic3
*
.

![Image](https://www.cryengine.com/docs/static/attachments/44968408)

A new
![Image](https://www.cryengine.com/docs/static/attachments/52592780)
  button appears for the X axis after you have configured this option in Y axis. Now you can click this button and select the newly created
*
area_fade_distance
*
 Game Parameter.

After this your setup should look like the one displayed in the screenshot below:

![Image](https://www.cryengine.com/docs/static/attachments/44968411)

In the sound object's
Positioning
 tab, create an attenuation which only affects the spread, but not the volume over distance. Similarly, the ambience spreads out completely when you are entering the area and diminishes when moving away from it.

![Image](https://www.cryengine.com/docs/static/attachments/44968414)

You can create a new event for the sound object, and regenerate your SoundBanks and connect the Wwise event in the Audio Controls Editor as explained
[here](Wwise%20Initial%20Setup.md)
.

For more information on how to setup your Wwise Event inside CRYENGINE, please refer to the tutorial
[Audio & Ambience](../../Audio%20Overview/Audio%20%26%20Ambience.md)
.
