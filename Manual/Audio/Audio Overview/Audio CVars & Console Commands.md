# Audio CVars & Console Commands

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/36867762
- Page ID: 36867762
- Breadcrumb: Audio > Audio Overview > Audio CVars & Console Commands
- Parent: Audio Overview

## Content

## Overview

The following is a list of Console commands that apply to the Audio system in general.

For console commands related to Wwise and FMOD Studio, see [Wwise Console Commands](../Audio%20Middleware/Wwise%20Workflow/Wwise%20Console%20Commands.md) and [FMOD Console Commands](../Audio%20Middleware/FMOD%20Studio%20Workflow/FMOD%20Console%20Commands.md).

### CVars

#### s_ActivateContext

Activates a Context.

This CVar also loads the meta data and auto-loaded preload requests of that Context. The argument accepted by it is the name of the Context to activate.

Usage: *s_ActivateContext intro*

#### s_AudioObjectsDebugFilter

Allows for filtered display of Audio Objects by a search string.

- Usage: *s_AudioObjectsDebugFilter spaceship*
- Default: "" (all)

This CVar was removed in release version 5.5.

#### s_AudioTriggersDebugFilter

Allows for filtered display of audio triggers by a search string.

- Usage: *s_AudioTriggersDebugFilter laser*("laser" being an example here)
- Default: "" (all)
This CVar was removed in release version 5.5.

#### s_DeactivateContext

Deactivates a Context.

This CVar also unloads the meta data and auto-loaded preload requests of that Context. The argument accepted by it is the name of the Context to deactivate.

Usage: *s_DeactivateContext intro*

#### s_DebugDistance

Limits drawing of audio object debug information to the specified distance around the active listeners. Setting this Cvar to 0 disables the limiting.

- Usage: *s_DebugDistance [0/...]*
- Default: 0 m (infinite)

This CVar was added in release version 5.5.

#### s_DebugFilter

Allows for filtered display of audio debug info by a search string.

- Usage:*s_DebugFilter spaceship*
- Default: " " (all)

This CVar was added in release version 5.5.

#### s_DrawDebug

Draws audio system related debug data on the screen.

- Usage: *s_DrawDebug [0ab...]*(flags can be combined)
0: No audio debug info on the screen.
a: Draw spheres around active audio objects.
b: Draw text labels for active audio objects.
c: Draw trigger names for active audio objects.
d: Draw current states for active audio objects.
e: Draw Parameter values for active audio objects.
f: Draw Environment amounts for active audio objects.
g: Draw distance to listener for active audio objects.
h: Draw occlusion ray labels.
i: Draw occlusion rays.
j: Draw spheres with occlusion ray offset radius around active audio objects.
k: Draw listener occlusion plane.
l: Draw occlusion collision spheres.
m: Draw global object info.
n: Draw middleware specific info for active audio objects.
q: Hide audio system memory info.
r: Apply filter also to inactive object debug info.
s: Draw detailed memory pool debug info.
u: List Contexts.
v: List active Events.
w: List active Audio Objects.
x: Draw FileCache Manager debug info.
y: Draw Request debug info.

FileCache Manager debug Color Coding

Color | Description
--- | ---
Cyan | File is removable.
Grey | File is not cached.
Lime green | Global scope.
Orange red | File is loading.
Red | File not found.
Violet red | File memory allocation failed.
Yellow | Level specific scope.

Release 5.5 and Earlier
The list of *s_DrawDebug*'s flags prior to CRYENGINE 5.5 were as follows:

0: No audio debug info on the screen.

a: Draw spheres around active Audio Objects.

b: Show text labels for active Audio Objects.

c: Show trigger names for active Audio Objects.

d: Show current states for active Audio Objects.

e: Show RTPC values for active Audio Objects.

f: Show Environment amounts for active Audio Objects.

g: Draw occlusion rays.

h: Show occlusion ray labels.

v: List active events.

w: List active Audio Objects.

x: Show FileCache Manager debug info.

These flags were subsequently changed on release 5.5 to:

0: No audio debug info on the screen.

a: Draw spheres around active audio objects.

b: Show text labels for active audio objects.

c: Show trigger names for active audio objects.

d: Show current states for active audio objects.

e: Show Parameter values for active audio objects.

f: Show Environment amounts for active audio objects.

g: Shows the object distance.

i: Draw occlusion rays.

j: Show object standalone files.

m: Hide audio system memory info.

n: Apply filter also to inactive object debug info.

u: List standalone files.

v: List active Events.

w: List active Audio Objects.

x: Show FileCache Manager debug info.

#### s_ExecuteTrigger

Executes an Audio Trigger.

The argument is the name of the trigger to be executed on the Global Object.

- Usage: *s_ExecuteTrigger <Audio Trigger Name>*

#### s_FileCacheManagerDebugFilter

Allows for filtered display of the different AFCM entries such as Globals, Level Specifics, Game Hints and so on.

- Usage:s_FileCacheManagerDebugFilter [0ab...] (flags can be combined)
- Default value: 0 (all)
a: Globals
b: Level Specifics
c: Game Hints

#### s_FileCacheManagerSize

Sets the size in KiB the AFCM will allocate on the heap.

- Usage: s_FileCacheManagerSize [0/...]
- Default value for Xbox One: 393216 (384 MiB)

The *s_FileCacheManagerSize* Cvar is exclusive to Xbox One.

#### s_HideInactiveObjects

When drawing Audio Object names on the screen this CVar can be used to choose between all registered Audio Objects or only those that reference active audio triggers.

- Usage: *s_HideInactiveObjects [0/1]*
- Default: 1 (active only)

In Engine release 5.5, the name of this CVar was changed from **s_ShowActiveAudioObjectsOnly** to ** s_HideInactiveAudioObjects**.

#### s_ImplName

Defines which audio middleware implementation (SDLMixer, FMOD Studio or Wwise) is loaded by CRYENGINE's audio system.

- Usage: *s_ImplName* <name of the library without extension>
- Default: CryAudioImplSDLMixer

#### s_IgnoreWindowFocus

If set to 1, the audio system will not execute the **lose_focus** and ** get_focus** default triggers when the application window focus changes.

- Usage: s_IgnoreWindowFocus [0/1]
- Default: 0 (off)

#### s_LoadRequest

Loads a preload request. The preload request has to be non-autoloaded. The argument is the name of the preload request to load.

- Usage: *s_LoadRequest VehiclePreload.*

#### s_LoadSetting

Loads a setting. The argument is the name of the setting to load.

- Usage: *s_LoadSetting main_menu.*

#### s_LoggingOptions

Toggles the logging of audio related messages.

- Usage: *s_AudioLoggingOptions [0ab...]* (flags can be combined)
- Default: 0 (logging disabled)
a: Errors
b: Warnings
c: Comments

#### s_ObjectPoolSize

Sets the number of pre-allocated audio objects and corresponding audio proxies.

- Usage:*s_ObjectPoolSize [0/...]*
- Default value: 256

In Engine release 5.6, the name of this CVar was changed from **s_AudioObjectPoolSize** to ** s_ObjectPoolSize.**

#### s_OcclusionAccumulate

Sets whether occlusion values encountered by a ray cast will be accumulated or only the highest value will be used.

- Usage: *s_OcclusionAccumulate [0/1]*
0: Off
1: On
- Default values
PC: 1 | XboxOne: 1 | PS4: 1 | Mac: 1 | Linux: 1 | iOS: 1 | Android: 1

#### s_OcclusionGlobalType

Can override audio objects' obstruction/occlusion ray type on a global scale. If set it determines whether audio objects use no, adaptive, low, medium or high granularity for rays.

This is a performance type CVar and can be used to turn off audio ray casting globally or force different modes of audio raycasting on all audio objects.

- Usage:*s_OcclusionGlobalType [0/1/2/3/4/5]*0: Audio object specific ray casting.
1: All audio objects ignore ray casting.
2: All audio objects use adaptive ray casting.
3: All audio objects use low ray casting.
4: All audio objects use medium ray casting.
5: All audio objects use high ray casting.

- Default values
PC: 0 | XboxOne: 0 | PS4: 0 | Mac: 0 | Linux: 0 | iOS: 0 | Android: 0

#### s_OcclusionHighDistance

Within this distance occlusion calculation uses the most sample points for highest granularity.

- Usage: *s_OcclusionHighDistance [0/...]*
- Default: 10 m

#### s_OcclusionInitialRayCastMode

Sets the ray cast mode of the initial occlusion check when a trigger gets executed.

- Usage: *s_OcclusionInitialRayCastMode [0/1/2]*
0: No initial occlusion check.
1: Initial occlusion check uses 1 ray from the center of the listener occlusion plane.
2: Initial occlusion check uses 5 rays. The center ray and one at each corner of the listener occlusion plane.
- Default: 1

#### s_OcclusionListenerPlaneSize

Sets the size of the plane at listener position against which occlusion is calculated.

- Usage: s_OcclusionListenerPlaneSize [0/...]
- Default: 1.0 (100 cm)

#### s_OcclusionMaxDistance

Occlusion is not calculated for the sounds, whose distance to the listener is greater than this value. Setting this value to 0 disables obstruction/occlusion calculations.

- Usage: *s_OcclusionMaxDistance [0..]*
- Default: 500 m

#### s_OcclusionMaxSyncDistance

Physics rays are processed synchronously for the sounds that are closer to the listener than this value, and asynchronously for the rest (possible performance optimization).

- Usage: *s_OcclusionMaxSyncDistance [0..]*
- Default: 10 m

#### s_OcclusionMediumDistance

Sets the occlusion medium distance. Medium occlusion calculation is done between the occlusion medium distance and high distance, using a medium amount of sample points for medium granularity.

- Usage: s_OcclusionMediumDistance [0/...]
- Default: 80 m

#### s_OcclusionSetFullOnMaxHits

If set to 1, the occlusion value will be set to 1 (max) when a ray cast reaches its max hit limit.

- Usage: *s_OcclusionSetFullOnMaxHits [0/1]*
0: Off
1: On
- Default: 0 (off)

#### s_PoolAllocationMode

Defines how pool sizes for audio controls are accumulated.

Pool sizes are determined by the amount of controls that exist in a Context.

- Usage: *s_PoolAllocationMode [0/...] 0: Accumulate pool sizes of all Contexts.* 1: Accumulate pool sizes of the global Context, and the largest pool size for each control in any other Context.
The value **1** may be used if at most one other Context besides the global Context is active.
- Default: 0

#### s_Refresh

Refreshes the audio system.

- Usage: *s_Refresh*

#### s_SetParameter

Sets an Audio Parameter value.

The first argument is the name of the parameter to be set, and the second argument is the float value to be set. The parameter is set on the Global Object.

- Usage: *s_SetParameter volume_music 1.0*

The name of this CVar was changed in 5.5 from **s_SetRTPC** to ** s_SetParameter**.

#### s_SetParameterGlobally

Sets an Audio Parameter value.

The first argument is the name of the parameter to be set, and the second argument is the float value to be set. The parameter is set on all constructed objects.

- Usage: *s_SetParameterGlobally volume_music 1.0*

#### s_SetSwitchState

Sets an Audio Switch to a provided State.

The first argument is the name of the switch, and the second argument is the name of the state to be set. The switch state is set on the Global Object.

- Usage: *s_SetSwitchState weather rain*

#### s_SetSwitchStateGlobally

Sets an Audio Switch to a provided State.

The first argument is the name of the switch, and the second argument is the name of the state to be set. The switch state is set on all constructed objects.

- Usage: *s_SetSwitchStateGlobally weather rain*

#### s_StopTrigger

Stops an Audio Trigger.

The argument is the name of the trigger to be stopped on the Global Object. If no argument is provided, all playing triggers on the Global Object get stopped.

- Usage: *s_StopTrigger <Audio Trigger Name>* [<Optional Audio Object ID>]

#### s_TriggerInstancePoolSize

Sets the number of preallocated trigger instances.

- Usage:*s_TriggerInstancePoolSize[0/...]*

- Default: 512

#### s_UnloadRequest

Unloads a preload request. The preload request has to be non-autoloaded. The argument is the name of the preload request to load.

- Usage: *s_UnloadRequest VehiclePreload*

#### s_UnloadSetting

Unloads a setting.

- The argument is the name of the setting to unload.
- Usage: *s_UnloadSetting main_menu.*

[CVars](#cvars)[s_ActivateContext](#sactivatecontext)[s_AudioObjectsDebugFilter](#saudioobjectsdebugfilter)[s_AudioTriggersDebugFilter](#saudiotriggersdebugfilter)[s_DeactivateContext](#sdeactivatecontext)[s_DebugDistance](#sdebugdistance)[s_DebugFilter](#sdebugfilter)[s_DrawDebug](#sdrawdebug)[s_ExecuteTrigger](#sexecutetrigger)[s_FileCacheManagerDebugFilter](#sfilecachemanagerdebugfilter)[s_FileCacheManagerSize](#sfilecachemanagersize)[s_HideInactiveObjects](#shideinactiveobjects)[s_ImplName](#simplname)[s_IgnoreWindowFocus](#signorewindowfocus)[s_LoadRequest](#sloadrequest)[s_LoadSetting](#sloadsetting)[s_LoggingOptions](#sloggingoptions)[s_ObjectPoolSize](#sobjectpoolsize)[s_OcclusionAccumulate](#socclusionaccumulate)[s_OcclusionGlobalType](#socclusionglobaltype)[s_OcclusionHighDistance](#socclusionhighdistance)[s_OcclusionInitialRayCastMode](#socclusioninitialraycastmode)[s_OcclusionListenerPlaneSize](#socclusionlistenerplanesize)[s_OcclusionMaxDistance](#socclusionmaxdistance)[s_OcclusionMaxSyncDistance](#socclusionmaxsyncdistance)[s_OcclusionMediumDistance](#socclusionmediumdistance)[s_OcclusionSetFullOnMaxHits](#socclusionsetfullonmaxhits)[s_PoolAllocationMode](#spoolallocationmode)[s_Refresh](#srefresh)[s_SetParameter](#ssetparameter)[s_SetParameterGlobally](#ssetparameterglobally)[s_SetSwitchState](#ssetswitchstate)[s_SetSwitchStateGlobally](#ssetswitchstateglobally)[s_StopTrigger](#sstoptrigger)[s_TriggerInstancePoolSize](#striggerinstancepoolsize)[s_UnloadRequest](#sunloadrequest)[s_UnloadSetting](#sunloadsetting)
