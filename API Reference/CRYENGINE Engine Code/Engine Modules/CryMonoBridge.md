# CryMonoBridge

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/26874559
- Page ID: 26874559
- Breadcrumb: CRYENGINE Engine Code > Engine Modules > CryMonoBridge
- Parent: Engine Modules

## Content

##
Overview

The purpose of CryMonoBridge is to load and handle the Mono runtime for the execution of .NET based modules. As such, it is an integral part of the
C# Framework
 which allows for the development of C# based CRYENGINE games. Removing CryMonoBridge will entirely remove execution of any .NET content from the engine.

When CryMonoBridge is executed by the engine, it loads all specified .NET plugins as a
**
`
ManagedPlugin
`
**
 from the cryproject-file which is located in the root folder of your project. When the plugin initializes it will call
**
`
ScanAssembly()
`
**
 on the
`
Engine
`
 class of the core-assembly. This will register every
**
`
EntityComponent
`
**
 and
**
`
BehaviorTreeNode
`
**
. Once everything is registered it will call the
**
`
Initialize()
`
**
 method on the first class that inherits from
**
`
ICryEnginePlugin
`
**
. Messages such as
**
`
Shutdown
`
**
, and
**
`
OnGameStart
`
**
 are all send to this plugin later on.

Related Content:

-
[/docs/static/engines/cryengine-5/categories/23756813/pages/26875052](
C# API Reference
)

-
[/docs/static/engines/cryengine-5/categories/23756813/pages/29791112](
C# Programming
)
