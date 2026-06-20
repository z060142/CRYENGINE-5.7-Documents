# Animation Streaming

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/23306441
- Page ID: 23306441
- Breadcrumb: CRYENGINE Engine Code > Engine Modules > CryAnimation > Animation Streaming
- Parent: CryAnimation

## Content

##
Overview

Animation can be a very memory intensive resource. Limited memory budgets, a high number of animated joints and high animation quality requirements makes it extremely wasteful for a project to have all animations loaded
in memory
all the time.

CRYENGINE's animation system alleviates this issue by streaming in animation resources (file granularity level) when they are needed and unloading them when not used any more.
Streaming of asset files is achieved by using the
[/docs/static/engines/cryengine-5/categories/23756813/pages/23306430](
Streaming System
)
.
Streaming assets in and out allows to have in memory only the resources we need, at the expense of more complexity given that we now require certain planning on how and when the animation resources are going to be used.

##
Animation Data

Animation data usage can be divided into two main sections:
**
Header Data
**
 and
**
Controllers Data
**
.

The
**
header
**
 section contains generic information for an animation (filename, duration, flags, etc).

The
**
controller
**
 section contains the animation curves. For each joint involved, this contains information on all the position and orientation values that the joint needs to play that animation. Even when compressed, controller data can easily take up more than 95% of the total memory required for an animation.

##
Animation Header Data

Header data for animations is stored in CAF files and in the animations.img file.

CAF files contain the header information on a single animation, while animations.img contains header information for all animations in the build.
The animations.img is obtained as a result of processing all the animations with the Resource Compiler.

The engine usually loads all the animation files' headers from the animations.img file instead of loading from individual files, since reading the information from individual files can slow down loading time considerably.

Given the extreme size differences between controllers and headers, we only stream in and out the controller data. The header data for all animations is kept at all times in memory, since it is practical to have that information at hand at all times.

During development,
for example
when working with local animation files, it is necessary to disable usage of animations.img and load the header information from individual CAF files instead. To do so, set the
**
ca_UseIMG_CAF
**
 console variable to 0
**
before
**
 the engine starts.

##
Animation Controller Data

##
Location in Files

The controller data for animations is stored in CAF files or
[/docs/static/engines/cryengine-3/categories/1114113/pages/15012226](
DBA files
)
.

CAF files contain controller information for a single animation.

DBA files contain controller information for a group of animations.

When a DBA is loaded, controllers for all animations contained in that DBA will be available until the DBA is unloaded. For this reason, it is useful to group together in the same DBA animations that are used together (eg. Crysis3 had a DBA file per weapon). An extra benefit of putting similar animations together in a DBA is that equal controllers are only stored once. This can potentially reduce the memory usage of your animations a lot.

##
Loading of Controller Data

The animation system can only properly play animations when their controllers are in memory.

If we are unlucky and the controller data is not available when playback of an asset is requested, the animation system will stream it in from disk.
Streaming of controller data is performed asynchronously: The animation system doesn't wait after asset playback is requested. This prevents the system from performing unwanted stalls.

If high level systems are not notifying the animation system that they require controller data (see the preload functions below), the soonest the animation system knows an asset is required is the point when it is requested to play. This is dangerously close to when the controller data is needed.
If the controller data is not available by the time it is needed it will typically lead to visual glitches. (These cases can sometimes be identified when we observe glitches only the first time an animation is played for example)

It is therefore deemed very convenient to have controller data streamed in before playback of an animation is requested: in order to minimize undesired glitches due to waiting for animation streaming to end.

The amount of time required for streaming to complete depends on many factors like the current system load, streaming speed of the target system, size of the resource that needs to be loaded, etc.

##
Unloading of Controller Data

The animation system will not unload controller data while it is in use.

It is possible to prevent unloading of animation data completely by setting
**
ca_DisableAnimationUnloading
**
 to 1.

Controllers in CAF files are unloaded after the system figures out that no one is using them any more. To prevent controllers in CAF files from being unloaded set
**
ca_UnloadAnimationCAF
**
 to 0.

Controllers in DBA files remain in memory until a certain amount of time passes since animations in them are used, unless the DBA is locked, in which case it will not be unloaded until the lock status is set back to 0.

To tweak the time the animation system uses to unload controllers in DBA files use the following cvars:

**
ca_DBAUnloadUnregisterTime
**
: Timeout in seconds before last usage of a controller in a DBA and when all animations using that DBA will mark their controller data as unloaded.

**
ca_DBAUnloadRemoveTime
**
: Timeout in seconds since last usage of a controller in a DBA that must elapse before a DBA gets really unloaded from memory. Should be greater or equal than ca_DBAUnloadUnregisterTime.

It is possible to lock individual resources in memory to prevent the system from unloading them.

##
Preloading and Keeping Controllers in Memory

The responsibility of calling the preloading functions is left to high level systems or user code (usually game code) since that's the point where most information is available on when and how assets are accessed. For example, trackview looks a number of seconds ahead in the timeline for any animations that might appear, and calls the preload functions.

##
Preloading Controllers in DBA Files

To preload and trigger the streaming of a DBA file:

```

`
gEnv->pCharacterManager->DBA_PreLoad(dbaFilename, priority);
`

```

To trigger the streaming of a DBA file (and request a change to the locked state that specifies if it should be locked in memory):

```

`
gEnv->pCharacterManager->DBA_LockStatus(dbaFilename, lockStatus, priority);
`

```

To unload all controller data in a DBA from memory (will only unload the data if none of the controllers are currently being used).

```

`
gEnv->pCharacterManager->DBA_Unload(dbaFilename);
`

```

You can make the system automatically load and lock a DBA file while a character is loaded by using the flags="persistent" feature in the chrparams file. See

[/docs/static/engines/cryengine-3/categories/1114113/pages/15012226](
Database File (dba)
)
 or

[/docs/static/engines/cryengine-5/categories/23756813](
CHRPARAMS File
)
 for more details.

##
Preloading Controllers in CAF Files

To increase the reference count of a CAF file:

```

`
gEnv->pCharacterManager->CAF_AddRef(lowercaseAnimationPathCRC);
`

```

Controllers for a CAF file will start streaming in when it's ref count goes from 0 to 1.

To decrease the reference count of a CAF file:

```

`
gEnv->pCharacterManager->CAF_Release(lowercaseAnimationPathCRC);
`

```

Controllers for a CAF file will be unloaded by the animation system only after the reference count reaches 0 (the animation system, when playing a CAF file, also increases this reference count, so an animation will not be unloaded while in use).

To check if the controllers for a CAF file are loaded:

```

`
gEnv->pCharacterManager->CAF_IsLoaded(lowercaseAnimationPathCRC);
`

```

To synchronously load the controllers for a CAF file:

```

`
gEnv->pCharacterManager->CAF_LoadSynchronously(lowercaseAnimationPathCRC);
`

```

It is strongly discouraged to synchronously load CAF assets unless absolutely necessary since it most likely will result in stalls.
