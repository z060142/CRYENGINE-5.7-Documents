# FMOD Console Commands

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/44964955
- Page ID: 44964955
- Breadcrumb: Audio > Audio Middleware > FMOD Studio Workflow > FMOD Console Commands
- Parent: FMOD Studio Workflow

## Content

### Overview

Overview of the CVar's available through the FMOD Studio specific implementation.

### CVars

The CVars that are utilized in Fmod studio are outlined below:

#### s_FmodDebugListFilter

Defines which lists to show when list filtering is enabled in the debug draw of the audio system.

- Usage: *s_FmodDebugListFilter[0ab...]*(flags can be combined)
0: Draw nothing.
a: Draw event instances.
b: Draw active snapshots.
c: Draw VCA values.

- Default: abc

#### s_FmodDistanceFactor

Sets the relative distance factor to Fmod's units.

The distance factor is the Fmod 3D engine's relative distance factor, measured in meter (Exactly 1.0 meter). It equates to the number of units per meter in your engine. For example, if you are using feet then *scale* is set to 3.28.

- Usage: *s_FmodDistanceFactor <0/...>*
- Default values:
PC: 1 | XboxOne: 1 | PS4: 1 | Mac: 1 | Linux: 1 | iOS: 1 | Android: 1

#### s_FmodDopplerScale

Sets the scaling factor for Doppler shift.

The Doppler scale is a general scaling factor for the variations in the pitch due to Doppler shifting in 3D sound.

Doppler is a pitch bending effect when a sound travels towards or away the listener or moves away from it. For example, the effect is similar when you hear a train going past you with its horn turned on. With *dopplerscale* you can increase or decrease the effect.

Fmod's effective speed of sound at a Doppler factor set at 1.0 is 340 meter per second.

- Usage: *s_FmodDopplerScale [0/...]*
- Default values:
PC: 1 | XboxOne: 1 | PS4: 1 | Mac: 1 | Linux: 1 | iOS: 1 | Android: 1

#### s_FmodEnableLiveUpdate

Lets the Fmod Studio to run with *LiveUpdate* option enabled. This function requires a restart of the Fmod implementation by restarting the editor/game project.

- Usage: *s_FmodEnableLiveUpdate [0/1]*
- Default values:
PC: 0 | XboxOne: 0 | PS4: 0 | Mac: 0 | Linux: 0 | iOS: 0 | Android: 0

#### s_FmodEnableSynchronousUpdate

Enables synchronous processing and performs all the required processing on the thread which has been called instead.

Usage: *s_FmodEnableSynchronousUpdate [0/1]*

- Default values:
PC: 1 | XboxOne: 1 | PS4: 1 | Mac: 1 | Linux: 1 | iOS: 1 | Android: 1

#### s_FmodEventPoolSize

Sets the number of preallocated events.

Usage: *s_FmodEventPoolSize [0/...]*

- Default values:
PC: 256 | XboxOne: 256 | PS4: 256 | Mac: 256 | Linux: 256 | iOS: 256 | Android: 256

#### s_FmodLowpassMinCutoffFrequency

Sets the minimum LPF cutoff frequency during full audio object occlusion.

Usage:*s_FmodLowpassMinCutoffFrequency [10/...]*

- Default values:
PC: 10 | XboxOne: 10 | PS4: 10 | Mac: 10 | Linux: 10 | iOS: 10 | Android: 10

#### s_FmodMaxChannels

Sets the maximum number of channels.

Usage: *s_FmodMaxChannels [0/...]*

- Default values:
PC: 512 | XboxOne: 512 | PS4: 512 | Mac: 512 | Linux: 512 | iOS: 512 | Android: 512

#### s_FmodPositionUpdateThresholdMultiplier

An object's distance to the listener is multiplied by this value to determine the position update threshold.

- Usage: s_FmodPositionUpdateThreshold [0/...]
- Default: 0.02

#### s_FmodRolloffScale

Sets the scaling factor for 3D sound roll off or attenuation only for *FMOD_3D_INVERSEROLLOFF* based sounds (Default type).

Volume for a sound set to *FMOD_3D_INVERSEROLLOFF* will scale at min-distance/distance. This gives an inverse attenuation of volume as the source gets further away (or closer).

Setting this value makes the sound drop off faster or slower. The higher the value, the faster volume will attenuate, and similarly, the lower the value, the slower it will attenuate. For example, a roll off factor of 1 will simulate the real world; where as a value of 2 will make sounds attenuate 2 times faster.

- Usage: *s_FmodRolloffScale [0/...]*
- Default values:
PC: 1 | XboxOne: 1 | PS4: 1 | Mac: 1 | Linux: 1 | iOS: 1 | Android: 1

#### s_FmodVelocityTrackingThreshold

An object has to change its velocity by at least this amount to issue an **absolute_velocity** parameter update request to the audio system.

**Usage:***s_FmodVelocityTrackingThreshold [0/...]*

- Default: 0.1 (10 cm/s)

[CVars](#cvars)[s_FmodDebugListFilter](#sfmoddebuglistfilter)[s_FmodDistanceFactor](#sfmoddistancefactor)[s_FmodDopplerScale](#sfmoddopplerscale)[s_FmodEnableLiveUpdate](#sfmodenableliveupdate)[s_FmodEnableSynchronousUpdate](#sfmodenablesynchronousupdate)[s_FmodEventPoolSize](#sfmodeventpoolsize)[s_FmodLowpassMinCutoffFrequency](#sfmodlowpassmincutofffrequency)[s_FmodMaxChannels](#sfmodmaxchannels)[s_FmodPositionUpdateThresholdMultiplier](#sfmodpositionupdatethresholdmultiplier)[s_FmodRolloffScale](#sfmodrolloffscale)[s_FmodVelocityTrackingThreshold](#sfmodvelocitytrackingthreshold)
