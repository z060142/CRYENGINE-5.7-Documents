# ADX2 Console Commands

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/44967893
- Page ID: 44967893
- Breadcrumb: Audio > Audio Middleware > ADX2 Workflow > ADX2 Console Commands
- Parent: ADX2 Workflow

## Content

## Overview

The CVars utilized by CRYENGINE's ADX2 implementation are outlined below.

### CVars

#### s_Adx2CuePoolSize

- Sets the number of pre-allocated cue instances.
- Usage: *s_Adx2CuePoolSize* *[0/...]*
- Default Values:
PC: 256 | XboxOne: 256 | PS4: 256 |Mac: 256 | Linux: 256 | iOS: 256 | Android: 256

#### s_Adx2MaxVirtualVoices

- Specifies the maximum number of voices for which voice control is performed simultaneously.
- Usage:*s_Adx2MaxVirtualVoices [0/...]*
- Default Values:
PC: 16

#### s_AdxMaxVoiceLimitGroups

- Specifies the maximum number of Voice Limit Groups that can be created.
- Usage: *s_AdxMaxVoiceLimitGroups* *[0/...]*
- Default Values:
PC: 16

#### s_Adx2MaxCategories

- Specifies the maximum number of categories that can be created.
- Usage: *s_Adx2MaxCategories [0/...]*
- Default Values
PC: 16

#### s_Adx2CategoriesPerPlayback

- Specifies the number of categories that can be referenced per playback.
- Usage: *s_Adx2CategoriesPerPlayback [0/...]*
- Default Values:
PC: 4

#### s_Adx2MaxTracks

- Specifies the total number of tracks in a sequence that can be played back simultaneously.
- Usage: *s_Adx2MaxTracks [0/...]*
- Default Values:
PC: 32

#### s_Adx2MaxFaders

- Specifies the maximum number of faders used in the Atom library.
- Usage: s_Adx2MaxFaders [0/...]
- Default Values:
PC: 4

#### s_Adx2NumVoices

- Specifies the number of voices.
- Usage: *s_Adx2NumVoices [0/...]*
- Default Values:
PC: 8

#### s_Adx2MaxChannels

- Specifies the maximum number of channels that can be processed by a DSP.
- Usage:*s_Adx2MaxChannels [0/...]*
- Default Values:
PC: 2

#### s_Adx2MaxSamplingRate

- Specifies the maximum sampling rate that can be processed by a DSP.\
- Usage: *s_Adx2MaxSamplingRate [0/...]\n*
- Default Values:
PC: 48000

#### s_Adx2NumBuses

- Specifies the number of buses.
- Usage: *s_Adx2NumBuses [0/...]*
- Default Values:
PC: 8

#### s_Adx2OutputChannels

- Specifies the number of output channels.
- Usage:*s_Adx2OutputChannels [0/...]*
- Default Values:
PC: 6

#### s_Adx2OutputSamplingRate

- Specifies the sampling rate.
- Usage:*s_Adx2OutputSamplingRate [0/...]*
- Default Values:
PC: 48000

#### s_Adx2MaxStreams

- Specifies the instantaneous maximum number of streamings.
- Usage: *s_Adx2MaxStreams [0/...]*
- Default Values:
PC: 8

#### s_Adx2MaxFiles

- Specifies the maximum number of files to open simultaneously.
- Usage: *s_Adx2MaxFiles [0/...]*
- Default Values:
PC: 32

#### s_Adx2VoiceAllocationMethod

- Specifies the method used when an AtomEx Player allocates voices.
- Usage: *s_Adx2VoiceAllocationMethod [0/1]*0: Voice allocation is tried once.
1: Voice allocation is tried as many times as needed.
- Default Values:
PC: 0

#### s_Adx2MaxPitch

- Specifies the upper limit of the pitch change applied in the Atom library.
- Usage: *s_Adx2MaxPitch [0/...]*
- Default Values:
PC: 2400

#### s_Adx2VelocityTrackingThreshold

- An object has to change its velocity by at least this amount to issue an *absolute_velocity* parameter update request to the audio system.
- Usage: *s_Adx2VelocityTrackingThreshold [0/...]*
- Default Values:
PC: 0.1 (10 cm/s)

#### s_Adx2PositionUpdateThresholdMultiplier

- An object's distance to the listener is multiplied by this value to determine the position update threshold.
- Usage: *s_Adx2PositionUpdateThresholdMultiplier [0/...]*
- Default Values:
PC: 0.02

#### s_Adx2MaxVelocity

- The maximum velocity that will be normalized to 1.0 of the AISCA-Control *absolute_velocity.*
- For instance if this value is set to 100, and an object has a speed of 20, the corresponding AISAC-Control value will be 0.2.
- Usage: *s_Adx2MaxVelocity* *[0/...]*
- Default Values:
PC: 100

#### s_Adx2DebugListFilter

- Defines which lists to show when list filtering is enabled in the debug draw of the audio system.

This CVar only works in profile and debug builds.

- Usage: *s_Adx2DebugListFilter [0ab...]* (flags can be combined)
0: Draw nothing.
a: Draw cue instances.
b: Draw GameVariable values.
c: Draw Category values.
- Default Values:
PC: abc

[CVars](#cvars)[s_Adx2CuePoolSize](#sadx2cuepoolsize)[s_Adx2MaxVirtualVoices](#sadx2maxvirtualvoices)[s_AdxMaxVoiceLimitGroups](#sadxmaxvoicelimitgroups)[s_Adx2MaxCategories](#sadx2maxcategories)[s_Adx2CategoriesPerPlayback](#sadx2categoriesperplayback)[s_Adx2MaxTracks](#sadx2maxtracks)[s_Adx2MaxFaders](#sadx2maxfaders)[s_Adx2NumVoices](#sadx2numvoices)[s_Adx2MaxChannels](#sadx2maxchannels)[s_Adx2MaxSamplingRate](#sadx2maxsamplingrate)[s_Adx2NumBuses](#sadx2numbuses)[s_Adx2OutputChannels](#sadx2outputchannels)[s_Adx2OutputSamplingRate](#sadx2outputsamplingrate)[s_Adx2MaxStreams](#sadx2maxstreams)[s_Adx2MaxFiles](#sadx2maxfiles)[s_Adx2VoiceAllocationMethod](#sadx2voiceallocationmethod)[s_Adx2MaxPitch](#sadx2maxpitch)[s_Adx2VelocityTrackingThreshold](#sadx2velocitytrackingthreshold)[s_Adx2PositionUpdateThresholdMultiplier](#sadx2positionupdatethresholdmultiplier)[s_Adx2MaxVelocity](#sadx2maxvelocity)[s_Adx2DebugListFilter](#sadx2debuglistfilter)
