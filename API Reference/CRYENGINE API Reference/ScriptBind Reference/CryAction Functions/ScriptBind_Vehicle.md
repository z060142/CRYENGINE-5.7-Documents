# ScriptBind_Vehicle

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/23306615
- Page ID: 23306615
- Breadcrumb: CRYENGINE API Reference > ScriptBind Reference > CryAction Functions > ScriptBind_Vehicle
- Parent: CryAction Functions

## Content

### GetVehicle

Gets the vehicle identifier.

```
Vehicle.GetVehicle()
```

### Reset

Resets the vehicle.

```
Vehicle.Reset()
```

### IsInsideRadius

Checks if the vehicle is inside the specified radius.

```
Vehicle.IsInsideRadius( pos, radius )
```

### MultiplyWithWorldTM

Multiplies with the world transformation matrix.

```
Vehicle.MultiplyWithWorldTM( pos )
```

Parameter | Description
--- | ---
pos | Position vector.

### ResetSlotGeometry

```
Vehicle.ResetSlotGeometry( slot, filename, geometry )
```

### AddSeat

Adds a seat to the vehicle.

```
Vehicle.AddSeat( paramsTable )
```

Parameter | Description
--- | ---
paramsTable | Seat parameters.

### HasHelper

Checks if the vehicle has the specified helper.

```
Vehicle.HasHelper(name)
```

Parameter | Description
--- | ---
name | Helper name.

### GetHelperPos

Gets the helper position.

```
Vehicle.GetHelperPos(name, isInVehicleSpace)
```

Parameter | Description
--- | ---
name | Helper name.
isInVehicleSpace | .

### GetHelperDir

Gets the helper direction.

```
Vehicle.GetHelperDir( name, isInVehicleSpace )
```

Parameter | Description
--- | ---
name | Helper name.
isInVehicleSpace | .

### GetHelperWorldPos

Gets the helper position in the world coordinates.

```
Vehicle.GetHelperWorldPos( name )
```

Parameter | Description
--- | ---
name | Helper name.

### EnableMovement

Enables/disables the movement of the vehicle.

```
Vehicle.EnableMovement( enable )
```

Parameter | Description
--- | ---
enable | True to enable movement, false to disable.

### DisableEngine

Disables/enables the engine of the vehicle.

```
Vehicle.DisableEngine( disable )
```

Parameter | Description
--- | ---
disable | True to disable the engine, false to enable.

### OnHit

Event that occurs after the vehicle is hit.

```
Vehicle.OnHit( targetId, shooterId, damage, position, radius, pHitClass, explosion )
```

Parameter | Description
--- | ---
targetId | Target identifier.
shooterId | Shooter identifier.
damage | Damage amount.
radius | Radius of the hit.
hitTypeId | Hit type.
explosion | True if the hit cause an explosion, false otherwise.

### ProcessPassengerDamage

Processes passenger damages.

```
Vehicle.ProcessPassengerDamage( passengerId, actorHealth, damage, pDamageClass, explosion )
```

Parameter | Description
--- | ---
passengerId | Passenger identifier.
actorHealth | Actor health amount.
damage | Damage amount.
hitTypeId | Damage type.
explosion | True if there is an explosion, false otherwise.

### Destroy

Destroys the vehicle.

```
Vehicle.Destroy()
```

### IsDestroyed

Checks if the vehicle is destroyed.

```
Vehicle.IsDestroyed()
```

### IsUsable

Checks if the vehicle is usable by the user.

```
Vehicle.IsUsable( userHandle )
```

Parameter | Description
--- | ---
userHandle | User identifier.

### OnUsed

Events that occurs when the user uses the vehicle.

```
Vehicle.OnUsed( userHandle, index )
```

Parameter | Description
--- | ---
userHandle | User identifier.
index | Seat identifier.

### EnterVehicle

Makes the actor entering the vehicle.

```
Vehicle.EnterVehicle( actorHandle, seatId, isAnimationEnabled )
```

Parameter | Description
--- | ---
actorHandle | Actor identifier.
seatId | Seat identifier.

### ChangeSeat

Makes the actor changing the seat inside the vehicle.

```
Vehicle.ChangeSeat(actorHandle, seatId, isAnimationEnabled)
```

Parameter | Description
--- | ---
actorHandle | Actor identifier.
seatId | Seat identifier.

### ExitVehicle

Makes the actor going out from the vehicle.

```
Vehicle.ExitVehicle( actorHandle )
```

Parameter | Description
--- | ---
actorHandle | Actor identifier.

### GetComponentDamageRatio

Gets the damage ratio of the specified component.

```
Vehicle.GetComponentDamageRatio( componentName )
```

### GetSeatForPassenger

```
Vehicle.GetSeatForPassenger(id)
```

**Returns:** Vehicle seat id for the specified passenger.
Parameter | Description
--- | ---
id | passenger id.

### OnSpawnComplete

Callback into game code for OnSpawnComplete.

```
Vehicle.OnSpawnComplete()
```
