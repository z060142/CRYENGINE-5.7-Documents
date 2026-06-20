# C++ API GamePlatform Usage Tips

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/76448706
- Page ID: 76448706
- Breadcrumb: Projects and Plug-ins > GamePlatform Plugin > GamePlatform Usage Tips > C++ API GamePlatform Usage Tips
- Parent: GamePlatform Usage Tips

## Content

##
Overview

The C++ API tries to abstract the interfaces of various platform implementations. This necessitates several custom types that allow identification of the service the data originates from, as well as custom events and classes that allow interaction with the various systems of the platform service.

For an overview of capabilities and support, please refer to
[GamePlatform Features (Discord/Steam)](../GamePlatform%20Features%20(Discord%20Steam).md)

##
GamePlatform Plugin Interop

-
The GamePlatform plugin is a standard CRYENGINE plugin and can therefore be accessed using the CrySystem PluginManager system.

-
To help manage a pointer to the GamePlatform plugin, such that it returns a

*
nullptr
*

when the plugin is unloaded without querying the plugin interface every time, use the
*
Cry::GamePlatform::CPluginHelper
*
 template class provided by the GamePlatformNodes interfaces (
*
CryPlugins/CryGamePlatformNodes/Interface/Utils/PluginUtils.h
*
).

##
Customizing Project CMakelists

If you are using a custom CRYENGINE project, you can include the interface directory by adding a line to your project's
*
CMakelists.txt
*
 file. Since the
*
CMakelists.txt
*
 file is regenerated when a solution for your project is generated, the file has a special section that is copied with each regeneration of the file.

Look for the following block:

```

`
#BEGIN-CUSTOM
# Make any custom changes here, modifications outside of the block will be discarded on regeneration.
#END-CUSTOM
`

```

And change it to the following:

```

`
#BEGIN-CUSTOM
# Make any custom changes here, modifications outside of the block will be discarded on regeneration.
target_include_directories(${THIS_PROJECT}
PRIVATE
    "${CRYENGINE_DIR}/Code/CryPlugins/CryGamePlatform/Interface"
    "${CRYENGINE_DIR}/Code/CryPlugins/CryGamePlatformNodes/Interface"
)
#END-CUSTOM
`

```

##
Using the Plugin Helper

The following example demonstrates how to make use of the GamePlatformPlugin and, in fact, any other CryPlugin Modules.

```

`
// Include CryGamePlatform core module
#include <IGamePlatform.h>

// Include CryGamePlatformNodes module
#include <IPlugin.h>

// Include Plugin Helper
#include <Utils/PluginUtils.h>

void UseGamePlatformCore()
{
  if (auto pGamePlatform = Cry::GamePlatform::CPluginHelper<Cry::GamePlatform::IPlugin>::Get())
  {
    ...
  }
}
void UseGamePlatformNodes()
{
  if (auto pGamePlatformNodes = Cry::GamePlatform::CPluginHelper<Cry::GamePlatform::IPlugin_GamePlatformNodes>::Get())
  {
    ...
  }
}
`

```

##
Service Identifiers

Each platform service has a unique 128 bit identifier.

-
This identifier is created using the ISO Standard GUID (UUID) strings that can be generated either via Visual Studio or other ISO compliant GUID generators.

-
This is then used to identify a service by this 128 bit value, and is attached to every Service Specific Identifier that is created.
Identifiers also allow the usage of integer based, or string based data, depending on the requirements of the platform the identifier is used for.

##
Service Specific Identifiers:

-
AccountIdentifier -
*

*
Used to identify a unique account on a specific platform.

-
LobbyIdentifier
*
 -
*
 Used to identify a unique lobby instance.

-
InventoryItemIdentifier
*
 -
*
Used to identify an item in an account inventory.

-
TransactionIdentifier
*
 -
*
Used to identify a specific microtransaction made on the platform.

-
LeaderboardIdentifier - Used to identify a specific leaderboard.
*

*

Identifier Contents

-
The data held by each identifier is platform specific. For example, an AccountIdentifier from the Steam platform will hold the 64 bit Steam ID of the account.

-
Each identifier instance also holds the service GUID that it belongs to.
[GamePlatform Plugin Interop](#gameplatform-plugin-interop)
[Customizing Project CMakelists](#customizing-project-cmakelists)
[Using the Plugin Helper](#using-the-plugin-helper)
[Service Identifiers](#service-identifiers)
[Service Specific Identifiers:](#service-specific-identifiers)
