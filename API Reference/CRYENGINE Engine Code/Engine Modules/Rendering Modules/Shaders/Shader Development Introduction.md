# Shader Development Introduction

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/23306638
- Page ID: 23306638
- Breadcrumb: CRYENGINE Engine Code > Engine Modules > Rendering Modules > Shaders > Shader Development Introduction
- Parent: Shaders

## Content

##
Overview

Most of the visual effect in CRYENGINE are driven by shaders. Shader development is a special programming discipline and requires a lot of expert knowledge, especially as shader code can be very performance-critical and platform-dependent.

This guide will help to get started with shader development in CRYENGINE, however, it is beyond the scope of this article to give a general introduction to shader programming.

Chapters:

[#getting-started](
Getting Started
)
[#writing-shader-code](
Writing Shader Code
)
[#remote-shader-compiler](
Remote Shader Compiler
)
[#using-shader-debugging-and-profiling-tools](
Using Shader Debugging and Profiling Tools
)
[#basic-shader-format](
Basic Shader Format
)
[#shader-flags](
Shader Flags
)
Related Pages:

##
Getting Started

##
Writing Shader Code

The easiest way to write shaders is by using a text editor and Sandbox. Sandbox supports hot reloading of shaders, so whenever you modify and save a shader file in a text editor, it will get reloaded automatically and the results can be viewed directly in a test level.

Hot reloading is supported on consoles as well by typing
**
r_reloadshaders 1
**
in the in-game console. Before reloading, the shaders have to be copied to the console.

For the X360, they need to be copied directly to the
`
Engine/Shaders
`
 directory on the devkit HDD while for the PS3, the local files in the
`
app_home
`
 directory need to be updated. It is easy to write a batch file which copies the updated shaders automatically to the required folders.

In order for shader hot-reloading to work properly, the following options have to be added to the system.cfg:

sys_PakPriority = 0

r_ShadersEditing = 1

**
sys_PakPriority 0
**
 makes sure that the shader files get loaded directly from the file system in the first place instead of just from pak files.
**
r_ShadersEditing 1
**
 ensures that shader code can be recompiled at run-time.

##
Remote Shader Compiler

It is highly recommended to use a locally running Remote Shader Compiler, so that shader debug symbols will be generated. See
[/docs/static/engines/cryengine-5/categories/23756813/pages/23306645](
Remote Shader Compiler
)
 for detailed instructions.

##
Using Shader Debugging and Profiling Tools

On Xbox 360, PIX can be used to debug and profile shader code. To make this work properly
[/docs/static/engines/cryengine-5/categories/23756813/pages/23306673](
Using PIX for GPU and CPU Profiling
)
 are required. For PS3, GPAD provides similar functionality.

To use it, the automatic 10Hz backbuffer flip has to be disabled and the usage of RSX memory as virtual memory should be disabled:

sys_flip10Hz = 0

ps3_virt_mem_rsx_size_kb = 0

##
Basic Shader Format

CRYENGINE uses a custom shader effect format that is very similar to HLSL and CgFX. An effect file contains the basic hardware shader code. Besides that, it can define techniques and declare samplers and constants.

To enable reuse of common code, effect files can include other shader files.

Shaders that can be used directly for rendering (e.g. in a material) have the extension
**
.cfx
**
 while shader include files have the extension
**
.cfi
**
.

##
Shader Flags

CRYENGINE uses an ubershader system with compile-time defines to handle the plenty of different
[/docs/static/engines/cryengine-5/categories/23756813](
Shader Permutations
)
 that are required for combining the numerous shader features.

By using ifdefs with shader flags, it is possible to define several code branches that are compiled and used depending on the flag bitmask. The shader compiler generates different hardware shader programs for each branch and stores them in the shader cache. A huger number of flags can lead to a plenty of permutations, so it is essential to keep the number of flags as small as possible. There are three different types of flags:

-
**
Engine flags
**
 - This type of flag is directly exposed by the engine. Engine flags contain general information like the supported shader model or the platform on which the engine is currently running.

-
**
Material flags
**
 - Material flags define local options for a single shader. These flags are evaluated at compile-time, so they cannot be modified at runtime. Material flags are used to parametrize shaders and are usually exposed to designers via the material editor.

-
**
Runtime flags
**
 - Runtime flags are dynamically set and unset by the engine during rendering. They make it possible to disable a special feature if it is not required for the current object in the current stage of the rendering pipeline.
Material flags are defined in extension files (
**
.ext
**
). Each effect file that exposes new flags must have a corresponding extension file with the same name. The ext file contains a list of
**
Property
**
 blocks where each of these blocks defines a single flag. Each Property must contain a
**
Name
**
 attribute (to be used in the shader to access the flag) and a bit mask. The bit mask must be unique inside the ext file and is used by the shader compiler to determine which branches need to be recompiled in case of shader code updates. The name of the flag is exposed globally, so care must be taken to not introduce any name clashes.

All available runtime flags are defined in the exentsion file
**
RunTime.ext
**
.

Example for using runtime flags in shader code:

```

`
#if %_RT_HDR_MODE && %_RT_HDR_FAKE
    OUT.Color1 = sceneColor1;
#else
    OUT.Color1 = sceneColor2;
#endif
`

```
