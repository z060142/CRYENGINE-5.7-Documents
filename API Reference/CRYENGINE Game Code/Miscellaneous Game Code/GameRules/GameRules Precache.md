# GameRules Precache

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/23306578
- Page ID: 23306578
- Breadcrumb: CRYENGINE Game Code > Miscellaneous Game Code > GameRules > GameRules Precache
- Parent: GameRules

## Content

##
Overview

The Game Rules Precache is a game subsystem designed to centralize the preloading and caching of assets.

During LevelSystem's LoadLevel, the PrecacheLevel function for the GameRules system is called. During this phase, the resources listed in the XML file
`
Scripts/GameRules/PrecacheLists.xml
`
 file are precached.

The assets listed in the XML file are organized by asset type, game mode, and level name. If an asset is only needed for Singleplayer, or if it's only needed for a specific multiplayer mode or level, it can be marked to only be preloaded for that mode or level.

##
Supported Asset Types

Name

 |
Type

 |

**
DBAs
**

 |
Animation Database Files.

 |

**
ADBs
**

 |
Mannequin Database Files.

 |

**
AGs
**

 |
Animation Graph Files.

 |

**
CDFs
**

 |
Character Definition Files.

 |

**
CGFs
**

 |
Geometry Files.

 |

**
CGAs
**

 |
Animated Geometry Files.

 |

**
CHRs
**

 |
Character Files.

 |

**
Particles
**

 |
Particle Effect Names.

 |

**
Sounds
**

 |
Sound Names.

 |

**
AudioHints
**

 |
Game Audio Hint Names.

 |

**
VehicleXMLs
**

 |
Vehicle XML Files.

 |

**
FlashTexs
**

 |
Texture Files.

 |

**
Ammos
**

 |
Ammo XML Files.

 |

**
Weapons
**

 |
Weapon XML files.

 |

**
BodyDamages
**

 |
BodyDamage or BodyDestruction XML files .

 |

**
GFXs
**

 |
Flash Files.

 |

**
MTLs
**

 |
Material Files.

 |

**
ControllerDefs
**

 |
Mannequin Controller Definition Files.

 |

The name listed on the table corresponds to the XML tag in the
PrecacheLists.xml file. See example below.

##
Code Location

The code handling the processing of the XML and the preloading of its resources can be found in GameRulesPrecache.cpp.

##
Lifetime and Ownership

The GameRulesPrecache module is owned by the GameRules. Its lifetime is tied to the lifetime of the GameRules, which means that the GameRulesPrecache is created when starting to load a level, and destroyed when a level is unloaded.

##
Unloading of assets

The handling of unloading of assets depends on their specific type, and in most cases it's not handled by the GameRulesPrecache class directly.

For example:

-
CGFs and CGAs are managed by the Item Geometry Cache, which will also take care of their unloading when a level unloads.

-
DBAs are managed by the CharacterManager, which by default releases all resources and gets destroyed during level unload, and recreated during level load.

-
For some other asset types the GameRulesPrecache may keeps a list of smart pointers to each of the preloaded assets to increment their refcount and making sure assets are not unloaded while the level is running, and when the GameRules gets destroyed during level unload, the vectors will get destructed.

##
Example File

```

`
<PrecacheLists>
  <Always>
    <FlashTexs>
      <FlashTex name='textures/sprites/hud/dirt1_bullet.tif' />
      <FlashTex name='textures/sprites/hud/dirt2_bullet.tif' />
      <FlashTex name='textures/sprites/hud/dirt3_bullet.tif' />
      <FlashTex name='textures/weapons/damage_blurmask.tif' />
      <FlashTex name='textures/weapons/ironzoom_blurmask.tif' />
    </FlashTexs>
    <GFXs>
      <GFX name='/libs/ui/Menus_Background.gfx' />
      <GFX name='/libs/ui/Menus_Confirmation.gfx' />
      <GFX name='/libs/ui/Menus_Dialogs.gfx' />
      <GFX name='/libs/ui/Menus_Startmenu.gfx' />
    </GFXs>
    <ADBTagDefs>
      <ADBTagDef name='Animations/Mannequin/ADB/blendRagdollTags.xml'/>
    </ADBTagDefs>
  </Always>
  <GameMode name='Multiplayer'>
    <CDFs>
      <CDF name='Objects/characters/human/sdk_player/sdk_player.cdf' />
    </CDFs>
    <DBAs>
      <DBA name='animations/human/male/locomotion.dba' />
      <DBA name='animations/human/male/locomotion/vault.dba' />
      <DBA name='animations/human/male/locomotion/rifle.dba' />
      <DBA name='animations/human/male/locomotion/pistol.dba' />
      <DBA name='animations/human/male/locomotion/slide.dba' />
      <DBA name='animations/human/male/locomotion/jump.dba' />
      <DBA name='animations/human/male/smartObjects/coophuman.dba' />
      <DBA name='animations/human/male/weapons/generic_1p.dba' />
      <DBA name='animations/human/male/weapons/generic.dba' />
      <DBA name='animations/human/male/weapons/pickable/pickable_1p.dba' />
      <DBA name='animations/human/male/weapons/pickable/pickable_3p.dba' />
    </DBAs>
    <CGFs>
      <CGF name='objects/weapons/attachments/silencer/silencer_scar_tp.cgf' />
      <CGF name='objects/weapons/attachments/rifle_magazine/rifle_magazine.cgf' />
    </CGFs>
    <Particles>
      <Particle name='Explosions.grenade_air.explosion' />
    </Particles>
    <VehicleXMLs>
      <VehicleXML name='Scripts/Entities/Vehicles/Implementations/Xml/HMMWV.xml'/>
      <VehicleXML name='Scripts/Entities/Vehicles/Implementations/Xml/MH60_Blackhawk.xml'/>
      <VehicleXML name='Scripts/Entities/Vehicles/Implementations/Xml/SpeedBoat.xml'/>
      <VehicleXML name='Scripts/Entities/Vehicles/Implementations/Xml/Abrams.xml'/>
    </VehicleXMLs>
    <FlashTexs>
      <FlashTex name='libs/ui/textures/menus_startmenu_noise.tif' />
      <FlashTex name='textures/sprites/glow/glow_linear_uncompressed.dds' />
    </FlashTexs>
    <Ammos>
      <Ammo name="PistolBullet" />
      <Ammo name="RifleBullet" />
      <Ammo name="Tank125" />
      <Ammo name="MGbullet" />
    </Ammos>
    <BodyDamages>
      <BodyDamage body="Libs/BodyDamage/BodyDamage_MP.xml" parts="Libs/BodyDamage/BodyParts_HumanMaleShared.xml" />
      <BodyDestruction name="Libs/BodyDamage/BodyDestructibility_Default.xml" />
    </BodyDamages>
    <GFXs>
      <GFX name='/libs/ui/Menus_Background.gfx' />
      <GFX name='/libs/ui/Menus_Confirmation.gfx' />
      <GFX name='/libs/ui/Menus_Dialogs.gfx' />
      <GFX name='/libs/ui/Menus_Startmenu.gfx' />
    </GFXs>
    <ADBs>
      <ADB name='Animations/Mannequin/ADB/humanSlaveAnims3P.adb'/>
    </ADBs>
  </GameMode>
  <GameMode name='SinglePlayer'>
    <CGFs>
      <CGF name='objects/weapons/rifle/rifle_fp.cgf' />
      <CGF name='objects/weapons/attachments/silencer/silencer_scar_tp.cgf' />
      <CGF name='objects/weapons/attachments/rifle_magazine/rifle_magazine.cgf' />
    </CGFs>
    <FlashTexs>
      <FlashTex name='libs/ui/textures/menus_startmenu_noise.tif' />
    </FlashTexs>
    <GFXs>
      <GFX name='/libs/ui/Menus_Background.gfx' />
      <GFX name='/libs/ui/Menus_Confirmation.gfx' />
      <GFX name='/libs/ui/Menus_Dialogs.gfx' />
      <GFX name='/libs/ui/Menus_Startmenu.gfx' />
    </GFXs>
  </GameMode>
  <Level name='Forest'>
    <CGFs>
      <CGF name='Objects/weapons/equipment/binoculars/binoculars_tp.cgf' />
    </CGFs>
  </Level>
</PrecacheLists>
`

```
