# User Interface

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/23306532
- Page ID: 23306532
- Breadcrumb: CRYENGINE Game Code > Miscellaneous Game Code > User Interface
- Parent: Miscellaneous Game Code

## Child Pages

- [Lua and the UI system](User%20Interface/Lua%20and%20the%20UI%20system.md)
- [UI Element](User%20Interface/UI%20Element.md)
- [UI Action](User%20Interface/UI%20Action.md)
- [Scaleform GFx Video Playback](User%20Interface/Scaleform%20GFx%20Video%20Playback.md)
- [UI Localization](User%20Interface/UI%20Localization.md)
- [IME](User%20Interface/IME.md)
- [Enabling Scaleform 4 for Projects and Custom Engine Builds](User%20Interface/Enabling%20Scaleform%204%20for%20Projects%20and%20Custom%20Engine%20Builds.md)

## Content

### Overview

Creating UI with CRYENGINE is easy and straightforward. We start our journey in the UI world with the basics, which everybody working on UI needs to know and should understand. After all of the underlying systems are presented and explained, the user can follow a [tutorial](/docs/static/engines/cryengine-3/categories/1638401/pages/1605725)for creating a simple button which sends events to the game code and reacts on user input.

CRYENGINE uses Scaleform for the in game User Interface. Scaleform is an external middleware that provides functionality to render / run Flash assets. The rendered assets can be used to implement Menus, HUD etc. They can even act as materials, which can be applied to in world geometry see [UI Elements as Dynamic Textures](/docs/static/engines/cryengine-3/categories/1114113/pages/1310910).

### Key Components

There are three key elements, which power the UI implementation in CRYENGINE:

- **[UI Elements](/docs/static/engines/cryengine-3/categories/1638401/pages/15011348) -** These are the actual UI Flash assets. They define what is displayed on screen and also contain all the logic exposed to [Flowgraph](/docs/static/engines/cryengine-3/categories/1638401/pages/1605670) or accessible from C++ code. They can be viewed as the smallest integral part, that the whole UI system is built upon.
- **[UI Actions](/docs/static/engines/cryengine-3/categories/1638401/pages/15011350) -** These are a special version of [Flowgraph](/docs/static/engines/cryengine-3/categories/1638401/pages/1605670). They are typically used to define, encapsulate and link UI logic with the game code.
- **[UI Event System](/docs/static/engines/cryengine-3/categories/1638401/pages/15011352) -** In order to simplify the communication between game code, UI code and [Flowgraph](/docs/static/engines/cryengine-3/categories/1638401/pages/1605670) even more, CRYENGINE provides a custom event system, which handles sending events in both directions.

### Useful CVars

There are different [CVars](/docs/static/engines/cryengine-3/categories/9895942/pages/9215968) that can control the Flash environment:

- **sys_flash** = enables/disables the Flash rendering.
- **sys_flash_info** = enables Flash profiling, and various information is displayed.
- **sys_flash_log_options** = enables logging of several Flash related aspects (Flash loading, Flash action script execution, etc).

### Further Reading

- [UI Element](User%20Interface/UI%20Element.md)
- [UI Action](User%20Interface/UI%20Action.md)
- [Scaleform GFx Video Playback](User%20Interface/Scaleform%20GFx%20Video%20Playback.md)
- [Lua and the UI system](User%20Interface/Lua%20and%20the%20UI%20system.md)
- [UI Localization](User%20Interface/UI%20Localization.md)
- [IME](User%20Interface/IME.md)
- [Enabling Scaleform 4 for Projects and Custom Engine Builds](User%20Interface/Enabling%20Scaleform%204%20for%20Projects%20and%20Custom%20Engine%20Builds.md)

- [UI Elements as Dynamic Textures](/docs/static/engines/cryengine-3/categories/1114113/pages/1310910)
- [Examples](../../CRYENGINE%20Code%20Tutorials/Miscellaneous%20Tutorials/UI%20Examples.md)
