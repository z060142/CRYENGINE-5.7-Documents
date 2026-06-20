# CRYENGINE 5.6.3

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/47316993/pages/52593456
- Page ID: 52593456
- Breadcrumb: Engine Release Notes (Current) > CRYENGINE 5 > CRYENGINE 5.6 > CRYENGINE 5.6.3
- Parent: CRYENGINE 5.6

## Content

Known Issues

- Oculus VR Plugin cannot be compiled with Visual Studio 2019 v16.3.0.
- Starting a C++ Plugin only project in Editor/Game Launcher causes a crash.
- Drag and dropping brushes or entities with children into another layer crashes the Editor.
- Turning on the "Ambient" light option for the Point Light entity component triggers asserts and sometimes causes crashes.

## Animation

- **Optimized:** The attached characters cache to only update when attachments change.
- **Fixed:** An issue with the max view distance render node property (not being propagated through attachment hierarchies).

## AI

- **Fixed:** Saving the level and generating an environment probe, triggers an assertion failure (NavigationSystem.cpp L 1172) and a warning which will pop up endlessly (Editor background thread is still running) making the Editor unusable.

## Audio

- **Tweaked:** Updated to Wwise SDK v2019.1.4.

## Core/System

- **Fixed:** Work around for compiler error with rsqrt_fast in VS 2019 16.3.
- **Fixed:** Compiler error with if_else_zero. if_else and if_else_zero are now overloaded to optimally use int or float version of SSE "and" intrinsic.

## Default Entities

- **Fixed:** Added missing include for RoomscaleCamera.

## CMake

- **Fixed:** Disabled Oculus VR plugin when using VS2019 16.3.0 (due to compilation issue)
- **Tweaked:** Fix Oculus VR plugin version check and comments.

## Core Systems

- **Tweaked:** Build error when using MSVCs Edit And Continue feature.

## Graphics and Rendering

- **Optimized:** (Particles) Removed ILINE on huge SNoise and other functions.

## Sandbox

- **Fixed:** (EE) Unable to switch between presets open in two docked EE instances.

## Plugins and Projects

- **Fixed:** The player entity is not correctly spawned when loading subsequent levels in the Sandbox.
