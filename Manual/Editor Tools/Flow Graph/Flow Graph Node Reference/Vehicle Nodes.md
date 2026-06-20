# Vehicle Nodes

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/29450644
- Page ID: 29450644
- Breadcrumb: Editor Tools > Flow Graph > Flow Graph Node Reference > Vehicle Nodes
- Parent: Flow Graph Node Reference

## Child Pages

- [Vehicle Nodes Use Cases](Vehicle%20Nodes/Vehicle%20Nodes%20Use%20Cases.md)

## Content

### Attachment

Handle vehicle entity attachments.

### ChangeSeat

Moves an actor from a seat to another one. Only works if the actor is already inside a vehicle.

### ChangeView

Used to set vehicle view per seat.

![Image](https://www.cryengine.com/docs/static/attachments/29688079)

### ChaseTarget

Follows/navigates on the specified path, trying to establish line of sight/fire with the specified target.

### Damage

Handle vehicle damage.

### Destroy

Node to destroy vehicle.

### Enter

Makes AI enter specified seat of specified vehicle.

### FollowPath

Follow path speed stance action.

### GetSeatHelper

Gets the helper pos of a seat(e.g for entering).

### Handbrake

Toggle vehicle handbrake. Currently only supported for ArcadeWheeled movement type.

### Honk

Use a vehicle's horn.

### Helicopter

#### EnableCombatMode

Used to alter the path the flight AI should follow so as to find the best position from which to engage the target.

![Image](https://www.cryengine.com/docs/static/attachments/29688077)

**Inputs**

Port | Type | Description
--- | --- | ---
**Enable** | Any | Enables combat mode
**Disable** | Any | Disables combat mode

#### EnableFiring

Used to enable the flight AI to fire at a target when used in combination with the**EnableCombatMode** node. If disabled, it just tactically positions itself to places from where it can see/hit the target. The default state is enabled.

![Image](https://www.cryengine.com/docs/static/attachments/29688076)

**Inputs**

Port | Type | Description
--- | --- | ---
**Enable** | Any | Enables firing mode
**Disable** | Any | Disables firing mode

#### FollowPath

Used to set the path that the flight AI should follow. When not in combat mode it will follow as accurately as possible from start to end. When in combat mode it represents the path along where the AI is allowed to position itself/patrol.

![Image](https://www.cryengine.com/docs/static/attachments/29688075)

**Inputs**

Port | Type | Description
--- | --- | ---
**Start** | Any | Start following the path
**Stop** | Any | Stop following the path
**PathName** | String | Name of the path to follow
**LoopPath** | Boolean | How many times to loop around the path
**Speed** | Float | Speed of the flight AI

**Outputs**

Port | Type | Description
--- | --- | ---
**ArrivedAtEnd** | Any | Triggers when flight AI is at the end of the path
**ArrivedNearToEnd** | Any | Triggers when flight AI is near the end of the path
**Stopped** | Any | Triggers when flight AI has stopped

#### ForceFire

Used to force the attention target of the flight AI to a specific entity.

![Image](https://www.cryengine.com/docs/static/attachments/29688074)

**Inputs**

Port | Type | Description
--- | --- | ---
**Enable** | Any | Enables force firing
**Disable** | Any | Disables force firing
**Target** | Any | Attention target

**Outputs**

Port | Type | Description
--- | --- | ---
**Finished** | Any | Triggers when finished

### Lights

Toggle vehicle lights.

### Lock

Locks/Unlocks all seats of vehicle.

### MoveActionMult

Add multipliers to vehicle movement actions.

### Movement

Handle vehicle movement.

### MovementParams

Modifies vehicle movement params.

### Passenger

Handle vehicle passengers.

### Seat

Handle vehicle seats.

### StickPath

Follows the specified path to the end, sticking to the optional target, either continuously or as a one-off event. Use the vehicle with the node's Entity input.

### Turret

Handle vehicle turret.

### Unload

Unloads vehicle, ejecting specified passengers.

### View

Used to Enable/Disable Views per Seat.

![Image](https://www.cryengine.com/docs/static/attachments/29688073)

[Attachment](#attachment)[ChangeSeat](#changeseat)[ChangeView](#changeview)[ChaseTarget](#chasetarget)[Damage](#damage)[Destroy](#destroy)[Enter](#enter)[FollowPath](#followpath)[GetSeatHelper](#getseathelper)[Handbrake](#handbrake)[Honk](#honk)[Helicopter](#helicopter)[Lights](#lights)[Lock](#lock)[MoveActionMult](#moveactionmult)[Movement](#movement)[MovementParams](#movementparams)[Passenger](#passenger)[Seat](#seat)[StickPath](#stickpath)[Turret](#turret)[Unload](#unload)[View](#view)
