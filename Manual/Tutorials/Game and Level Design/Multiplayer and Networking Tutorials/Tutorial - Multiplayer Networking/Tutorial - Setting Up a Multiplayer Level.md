# Tutorial - Setting Up a Multiplayer Level

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/25535225
- Page ID: 25535225
- Breadcrumb: Tutorials > Game and Level Design > Multiplayer and Networking Tutorials > Tutorial - Multiplayer Networking > Tutorial - Setting Up a Multiplayer Level
- Parent: Tutorial - Multiplayer Networking

## Content

## Overview

This tutorial shows you how to create and set up multiplayer levels from with the CRYENGINE SDK.

### Spawn Points

Drag several **[SpawnPoint](../../../../Editor%20Tools/Level%20Editor%20Tab/Create%20Object/Legacy%20Entities/Others.md)** entities into your level and rotate them so that when players spawn they will have a clear view of their surroundings.

Spawnpoints are found in the creation panel: **Entity\Others\SpawnPoint**

*Pic1: SpawnPoint placed*![Image](https://www.cryengine.com/docs/static/attachments/44970998)

### Pickups

In the SDK by default, players will spawn with a few weapons and lots of ammo. To ensure players always have a weapon and ammo, drag several weapons into the level, preferably close to the spawn points.

Typically you would want to set up various types of weapons, as well as various ammo pickups. Weapons can be added from the **Create Object** tool **-> Entity -> Items** list into your level:

*Pic2: Weapon added*![Image](https://www.cryengine.com/docs/static/attachments/44970999)

For Weapons and AmmoPickups entities, in the **Entity Properties** (which you can find by selecting the Weapon or AmmoPickup item and opening the ** Properties** tool) you need to set:

- **Pickable**
- **Usable**
- **Respawn**
- **Timer** (in seconds)

You can add or remove weapons, items and ammo from players starting equipment by going to **Game -> Edit Equipment-Packs**. Refer to the tutorial for more information.

If you place SpawnGroups you will be able to specify different equipment packs for each SpawnGroup.

### Placing SpawnGroups

A SpawnGroup allows you to group SpawnPoints together. This can be used to create team-oriented Multiplayer levels, as well as assign various capabilities or equipment packs to players.

Place a SpawnGroup from the **Create Object** tool **-> Entity -> Multiplayer -> SpawnGroup**.

After dragging the entity into the Perspective view, link the SpawnGroup to as many SpawnPoints as you wish by selecting Pick Target under a SpawnGroup's properties.

*Pic3: Linking the SpawnGroup to SpawnPoints*![Image](https://www.cryengine.com/docs/static/attachments/44971000)

Next, it is important to rename the link as "Spawn" or "SpawnGroup".

*Pic4: Providing a link name*![Image](https://www.cryengine.com/docs/static/attachments/44971001)

Now set up a second SpawnGroup for the other group of SpawnPoints.

### Placing SpectatorPoints

Drag and drop the spectator point entity from the multiplayer entities to important areas of your level so that users can see the action while they are re-spawning.

*Pic5: Placing a Spectator points.*![Image](https://www.cryengine.com/docs/static/attachments/44971002)

When players connect to a server their cameras will travel to the spectator point. Spectator Points can be found in the Entity section in the Multiplayer directory.

If you have no spectator points the spectators will start viewing from 0,0,0 position.

Rotate it so the Y+ (green arrow) of the helper looks at key gameplay locations. It is a good idea to place the SpectatorPoint somewhere in the air to give an overview of the area.

### Blocking Players from Leaving the Game Area

You can use the Designer Tool to build a wall of simple geometry around your gameplay area to block players from leaving. Make sure you assign the `materials/special/collision_proxy_entitiesonly` material to the designer objects so it's only rendered in the editor and not in game mode.

### MiniMap

Please see the [Terrain Minimaps](../../../../Editor%20Tools/Terrain%20Editor/Terrain%20Minimaps.md) section for help creating a Mini Map. Setting up a multiplayer specific UI, however, is beyond the scope of this tutorial.

### Multiplayer Map Game Setup

Export the level to the game engine, so you can to see your level in its most up to date version in real game mode. For help exporting a level, please see the [Exporting a Level for Playing](../../../../Packaging%20and%20Deployment/Exporting%20a%20Level%20for%20Playing.md) tutorial.

Please see [Level XML setup](/docs/static/engines/cryengine-3/categories/1638401/pages/8323113) for more information on setting up the level.XML file.

[Spawn Points](#spawn-points)[Pickups](#pickups)[Placing SpawnGroups](#placing-spawngroups)[Placing SpectatorPoints](#placing-spectatorpoints)[Blocking Players from Leaving the Game Area](#blocking-players-from-leaving-the-game-area)[MiniMap](#minimap)[Multiplayer Map Game Setup](#multiplayer-map-game-setup)
