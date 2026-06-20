# User Interface

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/23306532
- Page ID: 23306532
- Breadcrumb: CRYENGINE Game Code > Miscellaneous Game Code > User Interface
- Parent: Miscellaneous Game Code

## Child Pages

- [Lua and the UI system](User Interface/Lua and the UI system.md)
- [UI Element](User Interface/UI Element.md)
- [UI Action](User Interface/UI Action.md)
- [Scaleform GFx Video Playback](User Interface/Scaleform GFx Video Playback.md)
- [UI Localization](User Interface/UI Localization.md)
- [IME](User Interface/IME.md)
- [Enabling Scaleform 4 for Projects and Custom Engine Builds](User Interface/Enabling Scaleform 4 for Projects and Custom Engine Builds.md)

## Content

##
Overview

Creating UI with CRYENGINE is easy and straightforward. We start our journey in the UI world with the basics, which everybody working on UI needs to know and should understand. After all of the underlying systems are presented and explained, the user can follow a
[/docs/static/engines/cryengine-3/categories/1638401/pages/1605725](
tutorial
)
for creating a simple button which sends events to the game code and reacts on user input.

CRYENGINE uses Scaleform for the in game User Interface. Scaleform is
an external middleware that provides functionality to render / run Flash assets. The rendered assets can be used to implement Menus, HUD etc. They can even act as materials, which can be applied to in world
geometry see
[/docs/static/engines/cryengine-3/categories/1114113/pages/1310910](
UI Elements as Dynamic Textures
)
.

##
Key Components

There are three key elements, which power the UI implementation in CRYENGINE:

-
**
[/docs/static/engines/cryengine-3/categories/1638401/pages/15011348](
UI Elements
)
 -
**
These are the actual UI Flash assets. They define what is displayed on screen and also contain all the logic exposed to
[/docs/static/engines/cryengine-3/categories/1638401/pages/1605670](
Flowgraph
)
 or accessible from C++ code.
They can be viewed as the smallest integral part, that the whole UI system is built upon.

-
**
[/docs/static/engines/cryengine-3/categories/1638401/pages/15011350](
UI Actions
)
 -
**
These are a special version of
[/docs/static/engines/cryengine-3/categories/1638401/pages/1605670](
Flowgraph
)
. They are typically used to define, encapsulate and link UI logic with the game code.

-
**
[/docs/static/engines/cryengine-3/categories/1638401/pages/15011352](
UI Event System
)
 -
**
 In order to simplify the communication between game code, UI code and
[/docs/static/engines/cryengine-3/categories/1638401/pages/1605670](
Flowgraph
)
 even more, CRYENGINE provides a custom event system, which handles sending events in both directions.

##
Useful CVars

There are different
[/docs/static/engines/cryengine-3/categories/9895942/pages/9215968](
CVars
)
 that can control the Flash environment:

-
**
sys_flash
**
 = enables/disables the Flash rendering.

-
**
sys_flash_info
**
 = enables Flash profiling, and various information is displayed.

-
**
sys_flash_log_options
**
 = enables logging of several Flash related aspects (Flash loading, Flash action script execution, etc).

##
Further Reading

-
[/docs/static/engines/cryengine-5/categories/23756813/pages/23306537](
UI Element
)

-
[/docs/static/engines/cryengine-5/categories/23756813/pages/23306538](
UI Action
)

-
[/docs/static/engines/cryengine-5/categories/23756813/pages/23306535](
Scaleform GFx Video Playback
)

-
[/docs/static/engines/cryengine-5/categories/23756813/pages/23306547](
Lua and the UI system
)

-
[/docs/static/engines/cryengine-5/categories/23756813/pages/23306533](
UI Localization
)

-
[/docs/static/engines/cryengine-5/categories/23756813/pages/23306549](
IME
)

-
[/docs/static/engines/cryengine-5/categories/23756813/pages/90833060](
Enabling Scaleform 4 for Projects and Custom Engine Builds
)

-
[/docs/static/engines/cryengine-3/categories/1114113/pages/1310910](
UI Elements as Dynamic Textures
)

-
[/docs/static/engines/cryengine-5/categories/23756813/pages/23306540](
Examples
)
