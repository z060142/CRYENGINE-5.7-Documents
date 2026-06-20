# GamePlatform Services

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/76448647
- Page ID: 76448647
- Breadcrumb: Projects and Plug-ins > GamePlatform Plugin > GamePlatform Services
- Parent: GamePlatform Plugin

## Child Pages

- [Setting Up Plugin Definitions for Platform Services](GamePlatform Services/Setting Up Plugin Definitions for Platform Services.md)
- [Setting Up Discord Platform Services](GamePlatform Services/Setting Up Discord Platform Services.md)
- [Setting Up Steam Platform Services](GamePlatform Services/Setting Up Steam Platform Services.md)

## Content

##
Overview

Services are the underlying implementations for each supported platform. They provide all the functions and interfaces necessary to communicate with the host platform, and other supported services on that platform.

##
The Main Service

This is the first platform service registered to the GamePlatform plugin service registry.

There can only be one main Service at a time; usually this corresponds to the platform the game is deployed on such as Steam or the PSN Network. However, if there is no supported implementation for the platform the game is deployed on (for example, Epic or other eco systems) then the Main Service may not be available. You can still use optional services such as Discord, with or without a main service being registered.

Supported main services include:

-
Steam

-
Playstation Network

-
Xbox Live

##
Optional Services

Optional services are those that are not necessarily related to the platform the game is deployed upon, and can co-exist with a main platform. There can be multiple optional services registered at any time.

Supported optional services include:

-
Discord

##
Setup

-
[/docs/static/engines/cryengine-5/categories/23756813/pages/76448650](
Setting Up Plugin Definitions for Platform Services
)

-
[/docs/static/engines/cryengine-5/categories/23756813/pages/76448678](
Setting Up Discord Platform Services
)

-
[/docs/static/engines/cryengine-5/categories/23756813/pages/76448685](
Setting Up Steam Platform Services
)
[#the-main-service](
The Main Service
)
[#optional-services](
Optional Services
)
[#setup](
Setup
)
