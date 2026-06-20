# CrySystem

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/23306425
- Page ID: 23306425
- Breadcrumb: CRYENGINE Engine Code > Engine Modules > CrySystem
- Parent: Engine Modules

## Child Pages

- [Threading](CrySystem/Threading.md)
- [Console](CrySystem/Console.md)
- [File System](CrySystem/File%20System.md)
- [User Interface (Programming)](CrySystem/User%20Interface%20(Programming).md)
- [Memory Manager](CrySystem/Memory%20Manager.md)
- [Streaming System](CrySystem/Streaming%20System.md)
- [Text Localization & Unicode Support](CrySystem/Text%20Localization%20%26%20Unicode%20Support.md)
- [Logging System](CrySystem/Logging%20System.md)

## Content

### Purpose of CrySystem

Regarding engine architecture CrySystem is the main controller of the engine. It takes care of the lifetime of most other engine modules and invokes their update functions. Please refer to the highlights table below to get an overview, what system features are implemented in this module.

It is not required to initialize each engine module one by one from your game project or from Sandbox Editor. It is sufficient to initialize CrySystem, which takes care of all other underlying engine modules. To allow cross-accessibility between these modules, CrySystem stores a global collection of pointers in a struct called **gEnv** (* SSystemGlobalEnvironment*).

*Role of CrySystem during initialization of engine modules.*

### Highlights of CrySystem

[Console](CrySystem/Console.md) Extension system [File System](CrySystem/File%20System.md) [Frame Profiler](/docs/static/engines/cryengine-5/categories/23756813) Global Environment | Job System [Text Localization](CrySystem/Text%20Localization%20%26%20Unicode%20Support.md) [Logging System](CrySystem/Logging%20System.md) [Memory Manager](CrySystem/Memory%20Manager.md) Remote Console | [User Interface (Programming)](CrySystem/User%20Interface%20(Programming).md) [Streaming System](CrySystem/Streaming%20System.md) Thread Manager XML Utilities
--- | --- | ---

- [Threading](CrySystem/Threading.md)
- [Streaming System](CrySystem/Streaming%20System.md)
- [Text Localization & Unicode Support](CrySystem/Text%20Localization%20%26%20Unicode%20Support.md)
- [Logging System](CrySystem/Logging%20System.md)
- [Console](CrySystem/Console.md)
- [File System](CrySystem/File%20System.md)
- [User Interface (Programming)](CrySystem/User%20Interface%20(Programming).md)
- [Memory Manager](CrySystem/Memory%20Manager.md)
