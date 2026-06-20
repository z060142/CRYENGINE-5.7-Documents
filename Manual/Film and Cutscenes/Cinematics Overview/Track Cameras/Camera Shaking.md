# Camera Shaking

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/26874155
- Page ID: 26874155
- Breadcrumb: Film and Cutscenes > Cinematics Overview > Track Cameras > Camera Shaking
- Parent: Track Cameras

## Content

## Overview

One of the problems that many animations have is that they are too clean. Too smooth. Too perfect. In real life, things are very rarely, if ever, perfect. There's always 'noise'. Noise is that 'thing' that breaks up what should be perfect. Whether it's the dust on a counter top, skips on a CD, the slight shake of a camera, the variation in the gate of someone's walk, basically just the slight bit of randomness that is in everything around us.

If your scene has a moving camera, it's very rarely as steady as a stationary camera. There's always some degree of shake. Sometimes a lot, sometimes just a very small amount, but it's almost always there. CRYENGINE provides a solution for adding noise to your camera to give your dynamic cinematic scenes a more realistic effect. You can add a Camera Shake track to your Camera entity in Track View.

However, to get the desired effect, you cannot just ***turn on*** and ***turn off*** the shake in Track View. You need to tweak the exposed values below to get a realistic result:

Shake > **AmplitudeA**, ** AmplitudeB**, ** FrequencyA**, ** FrequencyB**

Shake only effects rotation, it does nothing with the position of the camera.

### Amplitude Explained

**AmplitudeA** (ampA), and ** AmplitudeB** (ampB) are just multipliers that ** multiply**the camera's** AmpA**and** AmpB parameters!**

A common mistake is to assume that the amplitude values are Yaw, Pitch or Roll. The Shake track is different than the ViewShakeEx flowgraph node.
They are separate overlapping and accumulating multipliers of the amplitude camera parameters that generate the final camera orientation!

The following non-animatable parameters exist on the camera entity:

So here above is the Yaw, Pitch, Roll or in CRYENGINE: **Z,X,Y**. These are in the parameters of the Camera Entity and are not exposed in trackview. In Track View ** AmpA track** is a multiplier that multiplies the ** Amplitude A camera parameter**.

Above the AmpA is 0,0,0, so no matter how much one cranks the Amplitude A in Trackview, it will still be multiplying 0,0,0 and the camera will not shake.

Here is a video that better explains the relation between the amplitude camera parameters and the track multiplier in trackview. This camera motion is playing directly from trackview, the track AmpA multiplier is always 100, but the x,y,z camera parameters are changing:

[Embed: https://www.youtube.com/watch?v=bnIOFvbwIjc]

**Limitation:** You cannot change camera parameters on the fly to significantly alter camera shake/movement.
### Frequency Explained

Frequency is sort of what it means, how frequently the camera changes orientations. Here's a video cycling through frequency multipliers of 1,5,10:

[Embed: https://www.youtube.com/watch?v=5gN8S8c72mc]

### Tweaking the values

First let's take a look at something that looks good:

[Embed: https://www.youtube.com/watch?v=_FDB9ivIoIU]

Why does this look different than most other times you see something heavy fall in the game? Because the curves were tweaked to achieve the result.

##### Curve Editing

To achieve really good camera shake, it is important to edit the fCurves. When you add a shake keyframe in Track View, the default fcurves have wide tangents which causes extreme easing in and out.

Notice that the value takes a really long time to get to the desired peak. Most of the time the intention is to have a quick impacting shake (like a punch in the face); with many explosions, shakes or jolts, we want the effect to be *immediate!*

So how do we get this more immediate jolt? Compare the two curves below:

So now we have a 'punchy' hit. In order to get a visually linear falloff of shake, the curves are tweaked until they looked like this:

##### Useful Tips

- Don't just turn on shake and leave it for a few seconds and turn it off. Spice things up! Shake is only interesting when it stands out. A whole cutscene of shake has no contrast of the effect to give any actual impact on a scene.
- In most scenes things are *happening*, something heavy falls over, something explodes.. Edit your curves and keys to reflect this!
- For rumbling, maybe a small earthquake or so, key the frequency in and out.
- Don't go shake crazy! Try to keep your amplitudes & frequencies between 1 and 8 (if your params are 1.0 of course).
- Keep in mind that some people are playing in Stereo 3D.

[Amplitude Explained](#amplitude-explained)[Frequency Explained](#frequency-explained)[Tweaking the values](#tweaking-the-values)
