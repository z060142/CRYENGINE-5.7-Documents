# Wwise & Occlusion

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/44964998
- Page ID: 44964998
- Breadcrumb: Audio > Audio Middleware > Wwise Workflow > Wwise & Occlusion
- Parent: Wwise Workflow

## Content

[Image: /docs/static/attachments/44964999]

##
Overview

This article explains how to make use of Obstruction/Occlusion settings in Wwise.

[#setting-up-occlusion-in-wwise](
Setting up Occlusion in Wwise
)
[#setup-examples-when-using-raycast-in-cryengine](
Setup Examples When Using Raycast in CRYENGINE
)
[#optimize-performance-when-randomizing-oneshot-sounds](
Optimize Performance when Randomizing OneShot Sounds
)
[#randomization-of-positioning](
Randomization of Positioning
)

##
Setting up Occlusion in Wwise

In Wwise, you can setup two separate behaviors for
*
Volume Attenuation
*
 and
*
Low Pass Filtering
*
, which are executed on the sound source whenever the connected game object is
*
obstructed
*
 or
*
occluded
*
. In the screenshot below, the X axis with values from 0 to 100 references the
*
 Obstruction/Occlusion
*
 value in Wwise, which goes from 0 to 1.

[Image: /docs/static/attachments/44968444]

In Wwise, the
*
VolumeAttenuation
*
and
*
LowPass Filtering
*
 curves can be set differently per platform; this provides you more flexibility in being able to adjust the final sound output of your game according to any particular platform challenges that may exist.

You can access the
*
Obstruction/Occlusion
*
 settings for your project by opening the
Project->Project Settings
 and then switching t
*
o
*
 the
Obstruction/Occlusion
tab.

Testing Different Obstruction/Occlusion Settings
In Wwise, you can test different Obstruction/Occlusion settings while being connected to the Editor and without having to rebuild your SoundBanks. You need to save the project after making changes and reconnect to the running CRYENGINE.

##
Setup Examples When Using Raycast in CRYENGINE

##
Optimize Performance when Randomizing OneShot Sounds

When you add an
*
Audio Trigger Spot
*
that triggers OneShots audio in timed intervals, you can define a random container in Wwise and have it retriggered in a specified random time range.

However, when you set up OneShot sounds, the
*
Audio Trigger Spot
*
will continue
*
 Raycasting
*
, even if no audio is playing at that moment in Wwise. This is because the
*
Wwise PlayEven
*
t on the
*
GameObject
*
 does not stop during periods when no audio is being played. Therefore, it's recommended to enable Randomization directly in the properties of the
*
Audio Trigger Spot
*
and not in Wwise. This will only add the Raycast whenever the actual event is being played and stops the Raycasting during the breaks in between when no active event is playing.

[Image: /docs/static/attachments/44968445]

##
Randomization of Positioning

You can create sounds with manual user positioning in Wwise, even though these sound do not consider any
*
Obstruction/Occlusion
*
 that happens in the game environment. The
*
Audio Trigger Spot
*
allows you to randomize its position independently on the
*
X, Y and Z axes.
*

With the
*
PlayOnX, PlayOnY, PlayOnZ
*
properties of the
*
Audio Trigger Spot,
*
 you can randomize the SoundSource position in the game environment and it gets affected by the game entities according to the
*
Occlusion/Obstruction
*
 properties that you have defined.

References of this setup can be found in the CRYENGINE Sandbox Editor showcase levels.
