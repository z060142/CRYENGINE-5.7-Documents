# Weapon Nodes

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/29450650
- Page ID: 29450650
- Breadcrumb: Editor Tools > Flow Graph > Flow Graph Node Reference > Weapon Nodes
- Parent: Flow Graph Node Reference

## Content

### Accessory

Attach/Detach [Accessory] from Actor's weapon [Weapon]. Both must be in the Inventory.

![Image](https://www.cryengine.com/docs/static/attachments/29688112)

In this example, we're pressing 'P' to detach the currently equipped SniperScope from the player's Rifle and then after a short delay, attaching the AssaultScope accessory.

![Image](https://www.cryengine.com/docs/static/attachments/29688111)

### AccessoryCheck

Checks if target actor's current weapon has [Accessory] attached.

![Image](https://www.cryengine.com/docs/static/attachments/29688114)

In this example, we're checking which Scope the player's current weapon has attached. In this case, it's the SniperScope stating 'true'.

![Image](https://www.cryengine.com/docs/static/attachments/29688113)

### ActorWeaponMagazineAmmo

Get/Set ammo in the magazine of the current player's weapon.

![Image](https://www.cryengine.com/docs/static/attachments/29688116)

In this example, we're getting the current AmmoCount with the 'O' key and it outputs '9' (only checks the current magazine, not full inventory amount).

We also set the AmmoCount amount to '3' with the 'P' key which then gives us 3 shots left in the current magazine before a reload is required.

![Image](https://www.cryengine.com/docs/static/attachments/29688115)

### AmmoChange

Give or Take ammo to/from a local player. Weapon and AmmoType must match [e.g. "SOCOM and "bullet"].

### AutoSightWeapon

This node allows to connect the enenmy position vector to shoot here.

![Image](https://www.cryengine.com/docs/static/attachments/29688103)

**Inputs**

Port | Type | Description
--- | --- | ---
**Enemy** | Vec3 | Aims the weapon at the enemy's position

### ChangeFireMode

Switched the weapon fire mode.

### Explosion

Triggers an explosion.

### ExplosionInfo

Tracks Explosions. All input conditions (ShooterId, Ammo, ImpactTargetId) must be fulfilled to output. If a condition is left empty/not connected, it is regarded as fulfilled.

### FireWeapon

Fires a weapon and sets a target entity or a target position.

### HitInfo

Tracks Hits on Actors. All input conditions (ShooterId, TargetId, Weapon, Ammo) must be fulfilled to output. If a condition is left empty/not connected, it is regarded as fulfilled.

### ItemAction

Plays an action on an item.

### Listener

Listens on [WeaponId] (or players [WeaponClass], or as fallback current players weapon) and triggers OnShoot when shot.

### ZoomCheck

Checks if target actor's current weapon is zoomed.

### Deprecated Nodes

- ChangeAmmo
- CheckAccessory
- CheckZoom
- WeaponListener

[Accessory](#accessory)[AccessoryCheck](#accessorycheck)[ActorWeaponMagazineAmmo](#actorweaponmagazineammo)[AmmoChange](#ammochange)[AutoSightWeapon](#autosightweapon)[ChangeFireMode](#changefiremode)[Explosion](#explosion)[ExplosionInfo](#explosioninfo)[FireWeapon](#fireweapon)[HitInfo](#hitinfo)[ItemAction](#itemaction)[Listener](#listener)[ZoomCheck](#zoomcheck)[Deprecated Nodes](#deprecated-nodes)
