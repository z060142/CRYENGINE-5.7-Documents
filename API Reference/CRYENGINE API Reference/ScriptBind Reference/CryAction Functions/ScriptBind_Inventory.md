# ScriptBind_Inventory

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/23306610
- Page ID: 23306610
- Breadcrumb: CRYENGINE API Reference > ScriptBind Reference > CryAction Functions > ScriptBind_Inventory
- Parent: CryAction Functions

## Content

### Destroy

Destroys the inventory.

```
Inventory.Destroy()
```

### Clear

Clears the inventory.

```
Inventory.Clear()
```

### Dump

Dumps the inventory.

```
Inventory.Dump()
```

### GetItemByClass

Gets item by class name.

```
Inventory.GetItemByClass( className )
```

Parameter | Description
--- | ---
className | Class name.

### GetGrenadeWeaponByClass

Gets grenade weapon by class name.

```
Inventory.GetGrenadeWeaponByClass( className )
```

Parameter | Description
--- | ---
className | Class name.

### HasAccessory

Checks if the inventory contains the specified accessory.

```
Inventory.HasAccessory( accessoryName )
```

Parameter | Description
--- | ---
accessoryName | Accessory name.

### GetCurrentItemId

Gets the identifier of the current item.

```
Inventory.GetCurrentItemId()
```

### GetCurrentItem

Gets the current item.

```
Inventory.GetCurrentItem()
```

### GetAmmoCount

Gets the amount of the specified ammunition name.

```
Inventory.GetAmmoCount(ammoName)
```

Parameter | Description
--- | ---
ammoName | Ammunition name.

### GetAmmoCapacity

Gets the capacity for the specified ammunition.

```
Inventory.GetAmmoCapacity( ammoName )
```

Parameter | Description
--- | ---
ammoName | Ammunition name.

### SetAmmoCount

Sets the amount of the specified ammunition.

```
Inventory.SetAmmoCount( ammoName, count )
```

Parameter | Description
--- | ---
ammoName | Ammunition name.
count | Ammunition amount.
