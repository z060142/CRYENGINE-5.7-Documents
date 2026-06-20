# CrySystem

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/23306425
- Page ID: 23306425
- Breadcrumb: CRYENGINE Engine Code > Engine Modules > CrySystem
- Parent: Engine Modules

## Child Pages

- [Threading](CrySystem/Threading.md)
- [Console](CrySystem/Console.md)
- [File System](CrySystem/File System.md)
- [User Interface (Programming)](CrySystem/User Interface (Programming).md)
- [Memory Manager](CrySystem/Memory Manager.md)
- [Streaming System](CrySystem/Streaming System.md)
- [Text Localization & Unicode Support](CrySystem/Text Localization & Unicode Support.md)
- [Logging System](CrySystem/Logging System.md)

## Content

##
Purpose of CrySystem

Regarding engine architecture CrySystem is the main controller of the engine. It takes care of the lifetime of most other engine modules and invokes their update functions. Please refer to the highlights table below to get an overview, what system features are implemented in this module.

It is not required to initialize each engine module one by one from your game project or from Sandbox Editor. It is sufficient to initialize CrySystem, which takes care of all other underlying engine modules. To allow cross-accessibility between these modules, CrySystem stores a global collection of pointers in a struct called
**
gEnv
**
 (
*
SSystemGlobalEnvironment
*
).

*
Role of CrySystem during initialization of engine modules.
*

##
Highlights of CrySystem

[/docs/static/engines/cryengine-5/categories/23756813/pages/23306428](
Console
)

Extension system

[/docs/static/engines/cryengine-5/categories/23756813/pages/23306405](
File System
)

[/docs/static/engines/cryengine-5/categories/23756813](
Frame Profiler
)

Global Environment

 |
Job System

[/docs/static/engines/cryengine-5/categories/23756813/pages/23306431](
Text Localization
)

[/docs/static/engines/cryengine-5/categories/23756813/pages/23306426](
Logging System
)

[/docs/static/engines/cryengine-5/categories/23756813/pages/24281463](
Memory Manager
)

Remote Console

 |
[/docs/static/engines/cryengine-5/categories/23756813/pages/23309135](
User Interface (Programming)
)

[/docs/static/engines/cryengine-5/categories/23756813/pages/23306430](
Streaming System
)

Thread Manager

XML Utilities

 |

-
[/docs/static/engines/cryengine-5/categories/23756813/pages/23306432](
Threading
)

-
[/docs/static/engines/cryengine-5/categories/23756813/pages/23306430](
Streaming System
)

-
[/docs/static/engines/cryengine-5/categories/23756813/pages/23306431](
Text Localization & Unicode Support
)

-
[/docs/static/engines/cryengine-5/categories/23756813/pages/23306426](
Logging System
)

-
[/docs/static/engines/cryengine-5/categories/23756813/pages/23306428](
Console
)

-
[/docs/static/engines/cryengine-5/categories/23756813/pages/23306405](
File System
)

-
[/docs/static/engines/cryengine-5/categories/23756813/pages/23309135](
User Interface (Programming)
)

-
[/docs/static/engines/cryengine-5/categories/23756813/pages/24281463](
Memory Manager
)
