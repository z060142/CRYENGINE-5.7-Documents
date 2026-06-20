# ItemPackages Scripting

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/23306531
- Page ID: 23306531
- Breadcrumb: CRYENGINE Game Code > Miscellaneous Game Code > Weapon and ItemPackages > ItemPackages Scripting
- Parent: Weapon and ItemPackages

## Content

##
Overview

The ItemPackages.xml file allows you to create custom DisplayNames for Items (namely, weapons), depending on what accessories they have equipped.

##
Script Setup

Open the script from the following location:
`
GameSDK/Scripts/Entities/Items/ItemPackages.xml
`

The default setup will look something like this:

```

`
<ItemPackages>

  <!-- Pistol -->
  <package display_name="@mp_eFlashlightPistol" item="Pistol" setup="Flashlight" />
  <package display_name="@mp_eExplosivePistol" item="Pistol" setup="PistolIncendiaryAmmo" />
  <package display_name="@mp_eAssaultPistol" item="Pistol" setup="Flashlight;PistolIncendiaryAmmo" />

  <!-- Rifle -->
  <package display_name="@mp_eSilencedRifle" item="Rifle" setup="Silencer" />

  <!-- Shotgun -->
  <package display_name="@mp_eSlugShotgun" item="Shotgun" setup="ShotgunSolidAmmo" />

</ItemPackages>
`

```

The
**
"package"
**
 refers to the collection of both the
**
"item"
**
 (weapon) and it's
**
"setup"
**
 (accessories).

The
**
"display_name"
**
 is similar to what you can define inside the item scripts themselves and is referenced by the
[localization system](/docs/static/engines/cryengine-3/categories/1114113/pages/1310919)
.

When an item, for example, the Pistol has an accessory, for example, the Flashlight, the ItemPackages system will override any display names with whatever you define in the script.
