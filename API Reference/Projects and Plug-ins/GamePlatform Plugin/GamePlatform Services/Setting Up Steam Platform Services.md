# Setting Up Steam Platform Services

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/76448685
- Page ID: 76448685
- Breadcrumb: Projects and Plug-ins > GamePlatform Plugin > GamePlatform Services > Setting Up Steam Platform Services
- Parent: GamePlatform Services

## Content

##
Requirements

-
Windows 10 x64.

-
Steam.

-
A valid Steam Developer game with a valid Steam AppId.

-
Although Windows 11 x64 might work, it is not officially supported.

-
Be sure to copy
*
steam_api64.dll
*
 from the Steamworks SDK into the binary output folder of your CRYENGINE project (by default:

*
bin/win_x64

*
for Profile builds). Since the CryGamePlatform Steam plugin links to this DLL dynamically, this DLL must be somewhere the application can find it (such as the binary folder).

-
By default, the
*
steam_api64.dll
*
 file can be found in the

*
Code/SDKs/Steamworks/redistributable_bin/win64
*
folder of your project.

##
Configuration Setup

By default, the Steam implementation will not load if you run your project via the Sandbox Editor. To enable the implementation in the Sandbox Editor:

-
Set the
`
steam_editor_support
`
CVar to
**
1.
**

-
Declare
`
steam_appid
`
 , the Application Identifier of your game application created via the Steam Developer portal.
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
        "steam_appid": "480",
        "steam_editor_support": "1"
  }
`

```

For more information on setting up your own Steamworks Application, please see the

[https://partner.steamgames.com/doc/home](
Steamworks Developer Documentation
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
