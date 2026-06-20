# Audio Feature

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/36868256
- Page ID: 36868256
- Breadcrumb: Editor Tools > Particle Editor > Particle Effect Features > Audio Feature
- Parent: Particle Effect Features

## Content

## Overview

The Audio category handles the triggering of audio files in particle effects. This feature can be used multiple times in a single component and it allows a sophisticated audio logic to be used in the particle effects.

The following options are available under the Audio category:

### Real-Time-Parameter-Controls (RTPC)

Contains the Real-Time-Parameter-Controls (RTPC) settings for CRYENGINE's Audio system. RTPC are audio attributes that can control certain aspects of sound such as pitch, volume, filter cutoffs, etc. For more information about RTPC's, please refer to CRYENGINE's [Audio documentation](../../../Audio.md).

Property | Description
--- | ---
**Name** | Click on the browse button or right click on the field and choose **Pick Resource...** to select an RTPC from the Audio Controls panel.
**Value** | Allows setting a value or curve in an advanced behavior. This value supports modifiers so that advance interactions can be had with the effect and the game scene. Please refer to [Modifiers](Modifiers.md) for more details on how to create advanced effects.

### Trigger

This feature allows each particle in this component to trigger an audio event.

Property | Description
--- | ---
**Play Trigger** | Allows users to select an Audio Trigger from the Audio Controls in CRYENGINE. These audio triggers can also be of a looping type which can be specified on the audio DCC tools.
**Stop Trigger** | Specifies the Audio Trigger to execute when the particle dies. This trigger is optional. If is left blank the **Stop on Death** option appears.
**Occlusion** | Allows selecting the type of Occlusion Raycast options. CRYENGINE's Audio engine supports occlusion of audio sources by the scene geometry. The following options are available under this property: - **Ignore -** The audio object does not calculate occlusion against the level geometry - ** Adaptive -** The audio object switches between the occlusion types depending on its distance to the audio listener. - ** Low -** The audio object uses a coarse grained occlusion plane for calculation. - ** Medium -** The audio object uses a medium grained occlusion plane for calculation. - ** High -** The audio object uses a fine grained occlusion plane for a calculation.
**Follow Particle** | Causes the audio object that has been assigned to **Play Trigger** to follow the particle while it moves around the scene. It is recommended to use this setting if an audio event is in a looping mode.
**Stop on Death** | When the particle is killed, stops the execution of the audio item that has been assigned to **Play Trigger**. This option is only available if a ** Stop Trigger** item has ** not** been specified.

### GPU Support

Since there is no communication between GPU particles and the host, audio events are not supported for GPU particles.

[Real-Time-Parameter-Controls (RTPC)](#real-time-parameter-controls-rtpc)[Trigger](#trigger)[GPU Support](#gpu-support)
