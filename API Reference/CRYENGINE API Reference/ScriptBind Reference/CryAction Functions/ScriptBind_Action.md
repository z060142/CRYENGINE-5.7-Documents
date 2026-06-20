# ScriptBind_Action

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/23306607
- Page ID: 23306607
- Breadcrumb: CRYENGINE API Reference > ScriptBind Reference > CryAction Functions > ScriptBind_Action
- Parent: CryAction Functions

## Content

### LoadXML

```
Action.LoadXML(definitionFile, dataFile)
```

Parameter | Description
--- | ---
definitionFile | .
dataFile | XML-lua data file name.

### SaveXML

```
Action.SaveXML(definitionFile, dataFile, dataTable)
```

Parameter | Description
--- | ---
definitionFile | .
dataFile | XML-lua data file name.
dataTable | .

### IsServer

```
Action.IsServer()
```

**Returns:** true if the current script runs on a server.

### IsClient

```
Action.IsClient()
```

**Returns:** true if the current script runs on a client.

### IsGameStarted

true if the game has started.

```
Action.IsGameStarted()
```

### IsRMIServer

true if the current script is running on an RMI (Remote Method Invocation) server.

```
Action.IsRMIServer()
```

### GetPlayerList

Checks the current players list.

```
Action.GetPlayerList()
```

### IsGameObjectProbablyVisible

```
Action.IsGameObjectProbablyVisible( gameObject )
```

**Returns:** true if an object is probably visible.
Parameter | Description
--- | ---
gameObject | Object that we want to check.

### ActivateEffect

Activates the specified effect.

```
Action.ActivateEffect( name )
```

Parameter | Description
--- | ---
name | Name of the effect.

### GetWaterInfo

Gets information about the water at the position pos.

```
Action.GetWaterInfo( pos )
```

Parameter | Description
--- | ---
pos | Position to be checked.

### SetViewCamera

Saves the previous valid view and override it with the current camera settings.

```
Action.SetViewCamera()
```

### ResetToNormalCamera

Resets the camera to the last valid view stored.

```
Action.ResetToNormalCamera()
```

### GetServer

Gets the server.

```
Action.GetServer( number )
```

### RefreshPings

Refreshes pings for all the servers listed.

```
Action.RefreshPings()
```

### ConnectToServer

Connects to the specified server.

```
Action.ConnectToServer( server )
```

Parameter | Description
--- | ---
server | String that specifies the server to be used for the connection.

### GetServerTime

Gets the current time on the server.

```
Action.GetServerTime()
```

### PauseGame

Puts the game into pause mode.

```
Action.PauseGame( pause )
```

Parameter | Description
--- | ---
pause | True to set the game into the pause mode, false to resume the game.

### IsImmersivenessEnabled

```
Action.IsImmersivenessEnabled()
```

**Returns:** true if immersive multiplayer is enabled.

### IsChannelSpecial

```
Action.IsChannelSpecial()
```

**Returns:** true if the channel is special.

### ForceGameObjectUpdate

Forces the game object to be updated.

```
Action.ForceGameObjectUpdate( entityId, force )
```

Parameter | Description
--- | ---
entityId | Identifier for the entity.
force | True to force the update, false otherwise.

### CreateGameObjectForEntity

Creates a game object for the specified entity.

```
Action.CreateGameObjectForEntity( entityId )
```

Parameter | Description
--- | ---
entityId | Identifier for the entity.

### BindGameObjectToNetwork

Binds game object to the network.

```
Action.BindGameObjectToNetwork( entityId )
```

Parameter | Description
--- | ---
entityId | Identifier for the entity.

### ActivateExtensionForGameObject

Activates a specified extension for a game object.

```
Action.ActivateExtensionForGameObject( entityId, extension, activate )
```

Parameter | Description
--- | ---
entityId | Identifier for the entity.
extension | Extension name.
activate | True to activate the extension, false to deactivate it.

### SetNetworkParent

Sets the network parent.

```
Action.SetNetworkParent( entityId, parentId )
```

Parameter | Description
--- | ---
entityId | Identifier for the entity.
parentID | Identifier for the parent network.

### IsChannelOnHold

```
Action.IsChannelOnHold( channelId )
```

Parameter | Description
--- | ---
channelId | Identifier for the channel. Checks if the specified channel is on hold.

### BanPlayer

Bans a specified player.

```
Action.BanPlayer( entityId, message )
```

Parameter | Description
--- | ---
entityId | Identifier for the entity.
message | Message for the ban.

### PersistantSphere

Adds a persistent sphere to the world.

```
Action.PersistantSphere( pos, radius, color, name, timeout )
```

Parameter | Description
--- | ---
pos | Position of the sphere.
radius | Radius of the sphere.
color | Color of the sphere.
name | Name assigned to the sphere.
timeout | Timeout for the sphere.

### PersistantLine

Adds a persistent line to the world.

```
Action.PersistantLine( start, end, color, name, timeout )
```

Parameter | Description
--- | ---
start | Starting position of the line.
end | Ending position of the line.
color | Color of the line.
name | Name assigned to the line.
timeout | Timeout for the line.

### PersistantArrow

Adds a persistent arrow to the world.

```
Action.PersistantArrow( pos, radius, dir, color, name, timeout )
```

Parameter | Description
--- | ---
pos | Position of the arrow.
radius | Radius of the arrow.
dir | Direction of the arrow.
color | Color of the arrow.
name | Name assigned to the arrow.
timeout | Timeout for the arrow.

### Persistant2DText

Adds a persistent 2D text.

```
Action.Persistant2DText( text, size, color, name, timeout )
```

Parameter | Description
--- | ---
text | Text that has to be displayed.
size | Size of the 2D text.
color | Color of the 2D text.
name | Name assigned to the 2D text.
timeout | Timeout for the 2D text.

### PersistantEntityTag

Adds a persistent entity tag.

```
Action.PersistantEntityTag( entityId, text )
```

Parameter | Description
--- | ---
entityId | Identifier for the entity.
text | Text for the entity tag.

### ClearEntityTags

Clears the tag for the specified entity.

```
Action.ClearEntityTags( entityId )
```

Parameter | Description
--- | ---
entityId | Identifier for the entity.

### ClearStaticTag

Clears the specified static tag for the specified entity.

```
Action.ClearStaticTag( entityId, staticId )
```

Parameter | Description
--- | ---
entityId | Identifier for the entity.
staticId | Identifier for the static tag.

### SendGameplayEvent

Sends an event for the gameplay.

```
Action.SendGameplayEvent( entityId, event )
```

Parameter | Description
--- | ---
entityId | Identifier for the entity.
event | Integer for the event.

### CacheItemSound

Caches an item sound.

```
Action.CacheItemSound( itemName )
```

Parameter | Description
--- | ---
itemName | Item name string.

### CacheItemGeometry

Caches an item geometry.

```
Action.CacheItemGeometry( itemName )
```

Parameter | Description
--- | ---
itemName | Item name string.

### DontSyncPhysics

Doesn't sync physics for the specified entity.

```
Action.DontSyncPhysics( entityId )
```

Parameter | Description
--- | ---
entityId | Identifier for the entity.

### EnableSignalTimer

```
Action.EnableSignalTimer( entityId, sText )
```

Parameter | Description
--- | ---
entityId | Identifier for the entity.
sText | Text for the signal.

### DisableSignalTimer

Disables the signal timer.

```
Action.DisableSignalTimer( entityId, sText )
```

Parameter | Description
--- | ---
entityId | Identifier for the entity.
sText | Text for the signal.

### SetSignalTimerRate

Sets the rate for the signal timer.

```
Action.SetSignalTimerRate( entityId, sText, fRateMin, fRateMax )
```

Parameter | Description
--- | ---
entityId | Identifier for the entity.
sText | Text for the signal.
fRateMin | Minimum rate for the signal timer.
fRateMax | Maximum rate for the signal timer.

### ResetSignalTimer

Resets the rate for the signal timer.

```
Action.ResetSignalTimer( entityId, sText )
```

Parameter | Description
--- | ---
entityId | Identifier for the entity.
sText | Text for the signal.

### EnableRangeSignaling

Enable/Disable range signalling for the specified entity.

```
Action.EnableRangeSignaling( entityId, bEnable )
```

Parameter | Description
--- | ---
entityId | Identifier for the entity.
bEnable | Enable/Disable range signalling.

### DestroyRangeSignaling

```
Action.DestroyRangeSignaling( entityId )
```

Parameter | Description
--- | ---
entityId | Identifier for the entity.

### ResetRangeSignaling

```
Action.ResetRangeSignaling( entityId )
```

Parameter | Description
--- | ---
entityId | Identifier for the entity.

### AddRangeSignal

Adds a range for the signal.

```
Action.AddRangeSignal( entityId, fRadius, fFlexibleBoundary, sSignal )
```

Parameter | Description
--- | ---
entityId | Identifier for the entity.
fRadius | Radius of the range area.
fFlexibleBoundary | Flexible boundary size.
sSignal | String for signal.

### AddTargetRangeSignal

```
Action.AddTargetRangeSignal( entityId, targetId, fRadius, fFlexibleBoundary, sSignal )
```

Parameter | Description
--- | ---
entityId | Identifier for the entity.
targetId | Identifier for the target.
fRadius | Radius of the range area.
fFlexibleBoundary | Flexible boundary size.
sSignal | String for signal.

### AddAngleSignal

Adds an angle for the signal.

```
Action.AddRangeSignal( entityId, fAngle, fFlexibleBoundary, sSignal )
```

Parameter | Description
--- | ---
entityId | Identifier for the entity.
fAngle | Angle value.
fFlexibleBoundary | Flexible boundary size.
sSignal | String for signal.

### RegisterWithAI

Registers the entity to AI System, creating an AI object associated to it.

```
Action.RegisterWithAI()
```

### HasAI

```
Action.HasAI( entityId )
```

**Returns:** true if the entity has an AI object associated to it, meaning it has been registered with the AI System

### GetClassName

```
Action.GetClassName( classId )
```

**Returns:** the matching class name if available for specified classId.

### SetAimQueryMode

Set the aim query mode for the ai proxy. Normally the ai proxy asks the movement controller if the character is aiming. You can override that and set your own 'isAiming' state.

```
Action.SetAimQueryMode( entityId, mode )
```

Parameter | Description
--- | ---
entityId | Identifier for the entity.
mode | QueryAimFromMovementController or OverriddenAndAiming or OverriddenAndNotAiming

### PreLoadADB

Use this function to pre-cache ADB files.

```
Action.PreLoadADB( adbFileName )
```

Parameter | Description
--- | ---
adbFileName | The path and filename of the animation ADB file which is to be pre-loaded.
