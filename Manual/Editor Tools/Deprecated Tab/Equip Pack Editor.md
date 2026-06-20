# Equip Pack Editor

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/27594517
- Page ID: 27594517
- Breadcrumb: Editor Tools > Deprecated Tab > Equip Pack Editor
- Parent: Deprecated Tab

## Content

![Image](https://www.cryengine.com/docs/static/attachments/27570814)

[![Image](https://www.cryengine.com/docs/static/attachments/44971622)](https://www.cryengine.com/support)

## Overview

After completing this tutorial, you will be able to give weapons and equipment items to AI entities and to the player.

You will also be able to carry the inventory of the player from one mission to another, as well as give the player specific items at the start of a level.

## Chapters:

[Chapters:](#chapters)[Editing Equipment Packs](#editing-equipment-packs)[Accessories Setup](#accessories-setup)[Saving Players Equipment Over Multiple Levels](#saving-players-equipment-over-multiple-levels)[Giving the Player Individual Weapons and Items](#giving-the-player-individual-weapons-and-items)

### Editing Equipment Packs

##### Step 1

In the Game menu, click Edit Equipment-Packs:

![Image](https://www.cryengine.com/docs/static/attachments/51871750) **Pic1: Edit Equipment-packs**

##### Step 2

Using the drop-down list, select one of the Equipment-Packs:

![Image](https://www.cryengine.com/docs/static/attachments/51871751) **Pic2: Configuring the Equipment**

##### Step 3

You can then add equipment from the **Available Equipment** list into the ** Used Equipment** list, or remove equipment by using the Add![Image](https://www.cryengine.com/docs/static/attachments/51871752) and Remove![Image](https://www.cryengine.com/docs/static/attachments/51871753) buttons.

As ammo/weapons/accessories are added/removed from the build, the EquipmentPack Editor will automatically notify of changes and update available equipment accordingly.

Player_Default is loaded by default unless specified otherwise through Flow Graph (**[Inventory:EquipPackAdd](../Flow%20Graph/Flow%20Graph%20Node%20Reference/Inventory%20Nodes.md)**).

Or, create a new pack by clicking Add:

![Image](https://www.cryengine.com/docs/static/attachments/51871754)

**Pic3: Adding a new pack using the Equipment pack window**

### Accessories Setup

Since CRYENGINE 3.5, the Equipment Pack tool also has the ability to sort Accessories/Attachments for Weapons.

![Image](https://www.cryengine.com/docs/static/attachments/51871755) *Pic4: Sorting the Equipment packs*

In the above example you can see several accessories are ticked. This means they are equipped on the weapon by default when loading this Equipment Pack. Only one accessory can be selected to be the default per-category (as defined in the Weapon script).

This means the Pistol will start with PistolBulletAmmo, the Rifle will start with no accessories and the Shotgun will start with ShotgunSolidAmmo. If we wanted the Flashlight on the pistol by default, we'd check the box next to it in the 'bottom' category.

#### Ammunition

There is a fairly large overlap between Weapon scripts and Equipment packs which should be kept in mind. Ammunition amounts can be defined in the Accessory XML, in the Weapon XML or in the Equipment Pack.

Typically the 'greater' value will be accepted but kept within the limitations. If your maximum ammo capacity for PistolBullet is 54 and you put 200 in the Equipment pack you'd still only get 54. If you put 10 in the Equipment pack and 12 in the Weapon script, you'd have 22 ammo.

#### AI Equipment Packs

To assign a specific Equipment pack to an AI, simply reference the Equipment Pack name in the **EquipmentPack** field of the AI Properties.

Remember, if you're dealing with many AI/Equipment Packs, AI **[Entity Archetypes](../Level%20Editor%20Tab/Create%20Object/Archetype%20Entity%20(Game%20SDK).md)** can be used.

You can also access the Equipment Pack editor by clicking the EquipmentPack "**...**" button in the properties of a character with a weapon.

*![Image](https://www.cryengine.com/docs/static/attachments/51871756) Pic5: Assigning the Equipment pack for an AI*

Note that AI have an unlimited amount of ammunition so you don't need to specify the number of bullets for their Equipment packs.

### Saving Players Equipment Over Multiple Levels

During some point in the game you may want to load a new level, but also carry over the players weapons and items over to the next level.

In the following picture we have a setup where on the completion or failure of **MissionObjective** we will save the player's inventory, fade out the screen and then trigger the next level.

*![Image](https://www.cryengine.com/docs/static/attachments/51871757) Pic6: Example for saving the player's inventory*

Then once the next level has been loaded, we will restore the saved inventory, fade in and then activate the mission **MissionObjective2**.

*![Image](https://www.cryengine.com/docs/static/attachments/51871758) Pic7: Resorting the saved player's inventory*

### Giving the Player Individual Weapons and Items

To give the player individual weapons and items, the **[Inventory and Weapon Nodes](/docs/static/engines/cryengine-5/categories/23756816/pages/23309636)** should be used.

In the example below, the player would receive a Pistol at the beginning of the level, as well as Pistol ammo:

![Image](https://www.cryengine.com/docs/static/attachments/51871759)

*Pic8: Providing a player with individual weapons and items through **[Inventory and Weapon Nodes](../Flow%20Graph/Flow%20Graph%20Node%20Reference/Inventory%20Nodes.md)**.*
