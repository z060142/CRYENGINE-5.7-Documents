# Setting Up Discord Platform Services

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/76448678
- Page ID: 76448678
- Breadcrumb: Projects and Plug-ins > GamePlatform Plugin > GamePlatform Services > Setting Up Discord Platform Services
- Parent: GamePlatform Services

## Content

##
Requirements

-
Windows 10 x64.

-
Discord.

-
A valid game application (with a valid Application Identified) developed via the Discord Developer portal.

-
Although Windows 11 x64 might work, it is not officially supported.

-
Be sure to copy
*
discord_game_sdk.dll
*
 from the Discord Game SDK into the binary output folder of your CRYENGINE project (by default:

*
bin/win_x64

*
for Profile builds). Since the CryGamePlatform Discord plugin links to this DLL dynamically, this DLL must be somewhere the application can find it (such as the binary folder).

-
By default, the

*
discord_game_sdk
*
*
.dll
*

file can be found in the

*
Code/SDKs/discord-game-sdk/lib/x86_64/
*
 folder of your CRYENGINE project.

##
Configuration Setup

By default, the Discord implementation will not load if you run your project via the Sandbox Editor. To enable the implementation in the Sandbox Editor:

-
Set the
`
discord_editor_support
`
CVar to
**
1
**
.

-
Declare
`
discord_appid
`
, the Application Identifier of your game application created via the Discord Developer portal.
These can be placed in one of the default .cfg files (
*
system.cfg, game.cfg
*
 or
*
user.cfg
*
), or embedded into your
*
.cryproject
*
 file.

##
Example

Here is an example of the CVar and Application Identifier declared in a First Shooter Template project:

```

`
  "console_commands": { },
  "console_variables": {
    "cl_DefaultNearPlane": "0.05",
    "sys_target_platforms": "pc,ps4,xboxone,linux",
        "discord_appid": "931611096516476130",
        "discord_editor_support": "1"
  }
`

```

For more information on setting up your own Discord Application for use with your game, please see the

[https://discord.com/developers/docs/game-sdk/sdk-starter-guide#get-set-up](
Discord Developer Portal Documentation
)
.

[#requirements](
Requirements
)
[#configuration-setup](
Configuration Setup
)
[#example](
Example
)
