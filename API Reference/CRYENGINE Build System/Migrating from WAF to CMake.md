# Migrating from WAF to CMake

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/26218339
- Page ID: 26218339
- Breadcrumb: CRYENGINE Build System > Migrating from WAF to CMake
- Parent: CRYENGINE Build System

## Content

## Overview

We have tried to make it as easy as possible to migrate from WAF to CMake. This section will explain the process of converting a project.

### Important Differences

While we have tried to keep things as similar as possible, there are a few differences that should be kept in mind when converting.

- When building static libraries, WAF will create a list of module users and then build each library multiple times if different module users specify differing compilation flags.
CMake will only build each static library once, with a single set of compilation flags.
- In WAF, static libraries were built to object files and then these object files were linked into each DLL that made use of them.
In CMake, static libraries go through an intermediate .a/.lib file. This may cause differences at link time.
- If you are using Incredibuild for building, WAF would previously provide the option to invoke Incredibuild for you.
With CMake, you must invoke Incredibuild manually.
- If you include Sandbox in your solution, only Debug and Profile builds are possible. You have to create a solution without Sandbox in order to build Release binaries.
- CMake does not provide a Performance configuration; only Debug, Profile and Release are available.

### Specifying Source Files

A key difference between the structure of our WAF and CMake scripts is that the list of source files is embedded into the same `CMakeLists.txt` file as the project extension, rather than being stored in external files.

To assist with converting over existing file lists, we provide a tool called `waf2cmake`, located in ` Tools\CMake\waf2cmake`.

If you run the batch file `run_waf2cmake.bat`, the tool will automatically traverse all WAF modules defined through ` Code\wscript` and ` Engine\wscript`. If a module directory has a ` CMakeLists.txt`, that file will be updated to match the WAF file lists. The tool can also try to check out these files to the default changelist in Perforce, using the command-line Perforce client.

If you have existing game projects not referenced from either of these files, you can use the --paths command-line option to parse additional directories. By default, the tool will parse `Code/GameMono`, ` Code/GameSDK` and ` Code/GameZero`.

The 5.3.0 release requires you to modify the batch file to add these options. 5.3.1 will add the ability to pass these extra arguments directly to the batch file.

To avoid accidentally overwriting critical parts of the file, `waf2cmake` only replaces text between specific, pre-defined tokens. If you are adding a custom module that was previously defined with WAF, and you wish to use ` waf2cmake` to populate the file list, put the following text near the top of your ` CMakeLists.txt` before running ` waf2cmake`:

```
#START-FILE-LIST
#END-FILE-LIST
```

When run, `waf2cmake` will replace the contents of this block with the file lists.

`waf2cmake` only updates the list of source files. Settings for the individual project must still be maintained manually.

### Converting projects

We will use the following module as an example. While this does not cover all possible cases, it should provide enough insight into how we have performed these conversions.

```
def build(bld):

bld.CryEngineModule(
target                  = 'MyModule',
vs_filter               = 'CryEngine/Extensions',
file_list               = 'mymodule.waf_files',
win_file_list           = 'mymodule_win.waf_files',

pch                     = 'StdAfx.cpp',
includes                = [ Path('Code/MyModule/include'), ],
module_provides         = dict(
includes = [ Path('Code/MyModule/include'), ],
defines  = [ 'MY_MODULE' ],
),
use_module              = [ 'lua' ],

win_lib                 = [ 'shell32'],
win_x86_debug_libpath   = [ Path('Code/SDKs/MySDK/x86/debug'),
win_x86_profile_libpath = [ Path('Code/SDKs/MySDK/x86/release'),
win_x86_release_libpath = [ Path('Code/SDKs/MySDK/x86/release'),
win_x64_debug_libpath   = [ Path('Code/SDKs/MySDK/x64/debug'),
win_x64_profile_libpath = [ Path('Code/SDKs/MySDK/x64/release'),
win_x64_release_libpath = [ Path('Code/SDKs/MySDK/x64/release'),
win_debug_lib           = [ 'MySDKd' ],
win_profile_lib         = [ 'MySDK' ],
win_release_lib         = [ 'MySDK' ],
)
```

We will assume you have already created an empty `CMakeLists.txt` file in this directory, added the tokens mentioned in the previous sections, and run ` waf2cmake`. This will automatically have taken care of the ` file_list` and ` win_file_list` arguments for us.

We start by declaring the module. This is done using the **`CryEngineModule`** function, which also lets us specify the precompiled header and solution folder. Place this at the end of the file, after the **`#END-FILE-LIST`** marker.

```
CryEngineModule(MyModule PCH "StdAfx.cpp" SOLUTION_FOLDER "CryEngine/Extensions")
```

This will automatically pick up the appropriate list of source files for your module based on the source files listed earlier in the file, as inserted by `waf2cmake`. Source files which are not relevant for your current build target will show up in the solution if they are available, but they will not be compiled.

Next, we will convert includes and module_provides:

```
target_include_directories(${THIS_PROJECT} PUBLIC ${CRYENGINE_DIR}/Code/MyModule/include)
target_compile_definitions(${THIS_PROJECT} INTERFACE -DMY_MODULE)
```

**`${THIS_PROJECT}`** is a variable that gets set by **`CryEngineModule`**, providing an easy way of referring to the module most recently defined this way. **` PUBLIC`**and **` INTERFACE`**specify where this information gets applied: **` PUBLIC`**is used for the module itself and anything that links to it, while **` INTERFACE`**only applies to other modules that link to your module. Since our module exposes the same include directory as it uses, we can take advantage of this and combing these using **` PUBLIC`**.

For use_module, we just need to link to the corresponding library.

```
target_link_libraries(${THIS_PROJECT} PRIVATE lua)
```

In line with **`PUBLIC`** and **`INTERFACE`** from the previous part, **`PRIVATE`** signifies that this only applies to the module itself, not to anything that links to the module.

Next, we have a Windows-specific section, so we need to surround further directives with this block:

```
if(WIN32 OR WIN64)
# Further directives go here
endif()
```

WIN32 is also set on 64-bit Windows builds, but being explicit can help serve as a reminder that this part applies to both.

Here, we can link to shell32 in the same way we linked to lua previously:

```
target_link_libraries(${THIS_PROJECT} PRIVATE shell32)
```

For **`libpath`**, CMake has no direct equivalent - instead, you are supposed to provide the full path to the module in question. In some cases, however, this may not be straightforward or desirable, so you can still emulate this directive. We need different folders for each platform, so we will separate the common parts out and add the platform-specific part separately:

```
set(MySDK_basedir ${SDK_DIR}/MySDK)
if (WIN64)
set(MySDK_dir ${MySDK_basedir}/x64)
elseif(WIN32)
set(MySDK_dir ${MySDK_basedir}/x86)
endif()
set_libpath_flag()
set_property(TARGET ${THIS_PROJECT} APPEND_STRING PROPERTY LINK_FLAGS_DEBUG " ${LIBPATH_FLAG}${MySDK_dir}/debug")
set_property(TARGET ${THIS_PROJECT} APPEND_STRING PROPERTY LINK_FLAGS_PROFILE " ${LIBPATH_FLAG}${MySDK_dir}/release")
set_property(TARGET ${THIS_PROJECT} APPEND_STRING PROPERTY LINK_FLAGS_RELEASE " ${LIBPATH_FLAG}${MySDK_dir}/release")
```

The space after the opening quotation mark is required to ensure correct operation.

Finally, we need to specify linking to MySDK. For this, we use CMake's generator expressions. In this case, we will use one expression to match our debug-only library, and another to match the other configurations:

```
target_link_libraries(${THIS_PROJECT} PRIVATE $<$<CONFIG:Debug>:MySDKd> $<$<NOT:$<CONFIG:Debug>>:MySDK>)
```

When linking multiple libraries to a specific configuration, each library must have its own generator expression. Spaces in generator expressions may not work reliably.

With that, the module conversion is complete. The last step is to make CMake include the module. For this, we go to **`Tools\CMake`** and add a matching **` add_subdirectory`** directive to the appropriate **` Build*.cmake`** file. Since this is an engine module, open **` BuildEngine.cmake`** and add the following line in an appropriate place:

```
add_subdirectory ("${CRYENGINE_DIR}/Code/MyModule" "${CMAKE_BINARY_DIR}/MyModule")
```

```

```

[Important Differences](#important-differences)[Specifying Source Files](#specifying-source-files)[Converting projects](#converting-projects)
