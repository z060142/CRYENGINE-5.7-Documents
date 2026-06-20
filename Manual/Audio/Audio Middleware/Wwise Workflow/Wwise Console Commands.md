# Wwise Console Commands

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/44965003
- Page ID: 44965003
- Breadcrumb: Audio > Audio Middleware > Wwise Workflow > Wwise Console Commands
- Parent: Wwise Workflow

## Content

##
Overview

Overview of the CVar's available through the Wwise specific implementation.

##
CVars

##
s_WwiseChannelConfig

Specifies the channel configuration.

-
Usage:
*
s_WwiseCommandQueueMemoryPoolSize [51/...]
*

0: Default speaker setup.

10: 1.0 speaker setup.

11: 1.1 speaker setup.

20: 2.0 speaker setup.

21: 2.1 speaker setup.

30: 3.0 speaker setup.

31: 3.1 speaker setup.

40: 4.0 speaker setup.

41: 4.1 speaker setup.

50: 5.0 speaker setup.

51: 5.1 speaker setup.

60: 6.0 speaker setup.

61: 6.1 speaker setup.

70: 7.0 speaker setup.

71: 7.1 speaker setup.

-
Default: 0

##
s_WwiseCommandQueueMemoryPoolSize

Specifies the size (in KiB) of the Wwise command queue memory pool.

-
Usage:
*
s_WwiseCommandQueueMemoryPoolSize [0/...]
*

-
Default values:

PC: 256 | XboxOne: 256 | PS4: 256 | Mac: 256 | Linux: 256 | iOS: 256 | Android: 256

##
s_WwiseDebugListFilter

Defines which lists to show when list filtering is enabled in the debug draw of the audio system.

-
Usage:
*
s_WwiseDebugListFilter [0ab...]
*
 (flags can be combined)

0: Draw nothing.

a: Draw event instances.

b: Draw states values.

-
Default: ab

##
s_WwiseEnableCommSystem

Specifies whether Wwise should initialize using its Comm system or not.

-
Usage:
*
s_WwiseEnableCommSystem [0/1]
*

-
Default: 0 (off)

Only available for non-release builds.

##
s_WwiseEnableEventManagerThread

Specifies whether Wwise should initialize using its EventManager thread or not.

-
Usage:
*
s_WwiseEnableEventManagerThread [0/1]
*

-
Default: 1 (on)

##
s_WwiseEnableOutputCapture

Allows for capturing the output audio to a wav file.

-
Usage:
*
s_WwiseEnableOutputCapture [0/1]
*

-
Default: 0 (off)
Only available in non-release builds.

##
s_WwiseEnableSoundBankManagerThread

Specifies whether Wwise should initialize using its SoundBankManager thread or not.

-
Usage:
*
s_WwiseEnableSoundBankManagerThread [0/1]
*

-
Default: 1 (on)

##
s_WwiseEventPoolSize

Sets the number of preallocated events.

-
Usage:
*
s_WwiseEventPoolSize [0/...]
*

-
Default values:

PC: 256 | Xbox One: 256 | PS4: 256 | Mac: 256 | Linux: 256 | iOS: 256 | Android: 256

##
s_WwiseLowerEngineDefaultPoolSize

Specifies the size (in KiB) of the Wwise lower engine memory pool.

-
Usage:
*
s_WwiseLowerEngineDefaultPoolSize [0/...]
*

-
Default values:

PC: 16384 (16 MiB) | Xbox One: 16384 (16 MiB) | PS4: 16384 (16 MiB) | Mac: 16384 (16 MiB) | Linux: 16384 (16 MiB) | iOS: 16384 (16 MiB) | Android: 16384 (16 MiB)

##
s_WwiseMonitorMemoryPoolSize

Specifies the size (in KiB) of the Wwise monitor memory pool.

-
Usage:
*
s_WwiseMonitorMemoryPoolSize [0/...]
*

-
Default values:

PC: 256 | XboxOne: 256 | PS4: 256 | Mac: 256 | Linux: 256 | iOS: 256 | Android: 256
Only available in non-release builds.

##
s_WwiseMonitorQueueMemoryPoolSize

Specifies the size (in KiB) of the Wwise monitor queue memory pool.

-
Usage:
*
s_WwiseMonitorQueueMemoryPoolSize [0/...]
*

-
Default values:

PC: 64 | Xbox One: 64 | PS4: 64 | Mac: 64 | Linux: 64 | iOS: 64 | Android: 64
Only available in non-release builds.

##
s_WwisePanningRule

Specifies the Wwise panning rule.

-
Usage:
*
s_WwisePanningRule [0/1]

*
0: Speakers

1: Headphones

-
Default values:

PC: 0 | Xbox One: 0 | PS4: 0 | Mac: 0 | Linux: 0 | iOS: 1 | Android: 1

##
s_WwisePositionUpdateThresholdMultiplier

An object's distance to the listener is multiplied by this value to determine the position update threshold.

-
Usage:
*
 s_WwisePositionUpdateThreshold [0/...]
*

-
Default: 0.02

##
s_WwisePrepareEventMemoryPoolSize

Specifies the size (in KiB) of the Wwise prepare event memory pool.

-
Usage:
*
s_WwisePrepareEventMemoryPoolSize [0/...]
*

-
Default values:

PC: 2048 (2 MiB) | Xbox One: 2048 (2 MiB) | PS4: 2048 (2 MiB) | Mac: 2048 (2 MiB) | Linux: 2048 (2 MiB) | iOS: 2048 (2 MiB) | Android: 2048 (2 MiB)

##
s_WwiseSecondaryPoolSize

Specifies the size (in KiB) of the memory pool to be used by the Wwise implementation.

-
Usage:
*
s_WwiseSecondaryPoolSize [0/...]
*

-
Default values

PC: 0 | Xbox One: 32768 (32 MiB) | PS4: 0 | Mac: 0 | Linux: 0 | WiiU: 0 | iOS: 0 | Android: 0

##
s_WwiseSoundEngineDefaultMemoryPoolSize

Specifies the size (in KiB) of the Wwise sound engine default memory pool.

-
Usage:
*
s_WwiseSoundEngineDefaultMemoryPoolSize [0/...]
*

-
Default values:

PC: 8192 (8 MiB) | Xbox One: 8192 (8 MiB) | PS4: 8192 (8 MiB) | Mac: 8192 (8 MiB) | Linux: 8192 (8 MiB) | iOS: 8192 (8 MiB) | Android: 8192 (8 MiB)

##
s_WwiseStreamDeviceMemoryPoolSize

Specifies the size (in KiB) of the Wwise stream device memory pool.

-
Usage:
*
s_WwiseStreamDeviceMemoryPoolSize [0/...]
*

-
Default values:

PC: 2048 (2 MiB) | Xbox One: 2048 (2 MiB) | PS4: 2048 (2 MiB) | Mac: 2048 (2 MiB) | Linux: 2048 (2 MiB) | iOS: 2048 (2 MiB) | Android: 2048 (2 MiB)

##
s_WwiseStreamManagerMemoryPoolSize

Specifies the size (in KiB) of the Wwise stream manager memory pool.

-
Usage:
*
s_WwiseStreamManagerMemoryPoolSize [0/...]
*

-
Default values:

PC: 64 | Xbox One: 64 | PS4: 64 | Mac: 64 | Linux: 64 | iOS: 64 | Android: 64

##
s_WwiseVelocityTrackingThreshold

An object has to change its velocity by at least this amount to issue an
**
absolute_velocity
**
 parameter update request to the audio system.

-
**
Usage:
**
*
s_WwiseVelocityTrackingThreshold [0/...]
*

-
Default: 0.1 (10 cm/s)
[CVars](#cvars)
[s_WwiseChannelConfig](#swwisechannelconfig)
[s_WwiseCommandQueueMemoryPoolSize](#swwisecommandqueuememorypoolsize)
[s_WwiseDebugListFilter](#swwisedebuglistfilter)
[s_WwiseEnableCommSystem](#swwiseenablecommsystem)
[s_WwiseEnableEventManagerThread](#swwiseenableeventmanagerthread)
[s_WwiseEnableOutputCapture](#swwiseenableoutputcapture)
[s_WwiseEnableSoundBankManagerThread](#swwiseenablesoundbankmanagerthread)
[s_WwiseEventPoolSize](#swwiseeventpoolsize)
[s_WwiseLowerEngineDefaultPoolSize](#swwiselowerenginedefaultpoolsize)
[s_WwiseMonitorMemoryPoolSize](#swwisemonitormemorypoolsize)
[s_WwiseMonitorQueueMemoryPoolSize](#swwisemonitorqueuememorypoolsize)
[s_WwisePanningRule](#swwisepanningrule)
[s_WwisePositionUpdateThresholdMultiplier](#swwisepositionupdatethresholdmultiplier)
[s_WwisePrepareEventMemoryPoolSize](#swwiseprepareeventmemorypoolsize)
[s_WwiseSecondaryPoolSize](#swwisesecondarypoolsize)
[s_WwiseSoundEngineDefaultMemoryPoolSize](#swwisesoundenginedefaultmemorypoolsize)
[s_WwiseStreamDeviceMemoryPoolSize](#swwisestreamdevicememorypoolsize)
[s_WwiseStreamManagerMemoryPoolSize](#swwisestreammanagermemorypoolsize)
[s_WwiseVelocityTrackingThreshold](#swwisevelocitytrackingthreshold)
