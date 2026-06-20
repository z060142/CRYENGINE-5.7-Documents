# Setting Up Plugin Definitions for Platform Services

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/76448650
- Page ID: 76448650
- Breadcrumb: Projects and Plug-ins > GamePlatform Plugin > GamePlatform Services > Setting Up Plugin Definitions for Platform Services
- Parent: GamePlatform Services

## Content

##
Overview

Before you can use any of the platform services, you will need to tell the Engine to load the corresponding plugins.

By specifying the platforms you wish to load the plugins on, you only need a single project file to load the required plugins for each respective platform.

##
Example

Here is an example of plugin definitions in the
*
FirstPersonShooter.cryproject
*
 template project file

```

`
  "require": {
    "engine": "engine-5.7",
    "plugins": [
      { "guid": "", "type": "EType::Native", "path": "CryDefaultEntities" },
      { "guid": "", "type": "EType::Native", "path": "CrySensorSystem" },
      { "guid": "", "type": "EType::Native", "path": "CryScaleformSchematyc" },
      { "guid": "", "type": "EType::Native", "path": "CryPerceptionSystem" },

      { "guid": "", "type": "EType::Native", "path": "CryGamePlatform", "platforms": [ "PC", "PS4", "XboxOne" ] },
      { "guid": "", "type": "EType::Native", "path": "CryGamePlatformSteam", "platforms": [ "PC" ] },
      { "guid": "", "type": "EType::Native", "path": "CryGamePlatformDiscord", "platforms": [ "PC" ] },
      { "guid": "", "type": "EType::Native", "path": "CryGamePlatformPSN", "platforms": [ "PS4" ] },
      { "guid": "", "type": "EType::Native", "path": "CryGamePlatformXbox", "platforms": [ "XboxOne" ] },
      { "guid": "", "type": "EType::Native", "path": "CryGamePlatformNodes", "platforms": [ "PC", "PS4", "XboxOne" ] },

      { "guid": "", "type": "EType::Native", "path": "bin/win_x64/Game.dll" }
    ]
  },
`

```

[#example](
Example
)
