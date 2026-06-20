# EaaS 3.6.15

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/47316993/pages/44963021
- Page ID: 44963021
- Breadcrumb: Engine Release Notes (Current) > CRYENGINE 3.x > EaaS 3.6 > EaaS 3.6.15
- Parent: EaaS 3.6

## Content

Released 16th January, 2015

Make sure you check out the [Guide to releasing EaaS-based projects (3.6) - DEPRECATED](/docs/static/engines/cryengine-3/categories/1638401) article, which covers information on how to setup your EaaS game to be compiled in "Release" mode.

### Editor

- **Fixed**: Unlikely null-pointer de-reference when switching to game mode (CE-5258).

### Engine

- **New**: (Build) Added release build config for EaaS (which is not identical to "normal" release in terms of linking).
- **New**: (CrySystem) Allows game code to specify a list of pak-files to load (instead of hard-coding in CrySystem), for use by EaaS.
- **Fixed**: (RC, CryCommonTools) RC ignores files that are inside a subfolder of which the name starts with a. (dot).

### Renderer

- **Fixed**: Don't skip deferred shadow gen when there are still custom or cloud shadows to be rendered (CE-5168).
- **Fixed**: Overlapping stencil values with cascade blending and custom shadow maps.
- **Fixed**: Use area light for sun just when area light support is enabled. Fixed area lights with tiled shading.
- **Fixed**: gbuffer velocity generation when tessellation is enabled (fixes Character motion blur issues) (CE-3335).
- **Fixed**: Sun specular multiplier in standard shading path (fixes sun specular not being configurable in tiledshading '2' mode).

### Audio

- **New**: Updated to Wwise version 2014.1.2 build 5195.
- **New**: Introduced console functions to Execute/Stop Audio Triggers and Set Audio Rtpcs and Switches.
- **New**: Added error logging for failed AFCM cache requests if a file not found at the target location.
- **Fixed**: (ACB) The very first Wwise control was hidden from the user.
- **Fixed**: (ACB) ACB would crash on a NULL control pointer during undo/redo (CE-4823).
- **Fixed**: Environments were still updated on the AAA and AAE even thought they were disabled (CE-4570/CE-4719).
- **Fixed**: Audio object ID invalidation on audio proxies during Save/Load.
