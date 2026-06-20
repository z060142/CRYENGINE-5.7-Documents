# ScriptBind_UIAction

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/23306614
- Page ID: 23306614
- Breadcrumb: CRYENGINE API Reference > ScriptBind Reference > CryAction Functions > ScriptBind_UIAction
- Parent: CryAction Functions

## Content

### ReloadElement

Reloads the UI flash asset.

```
UIAction.ReloadElement( elementName, instanceID )
```

Parameter | Description
--- | ---
elementName | UI Element name as defined in the xml.
instanceID | ID of the instance (if instance with id does not exist, it will be created). '-1' for all instances.

### UnloadElement

Unloads the UI flash asset.

```
UIAction.UnloadElement( elementName, instanceID )
```

Parameter | Description
--- | ---
elementName | UI Element name as defined in the xml.
instanceID | ID of the instance (if instance with id does not exist, it will be created). '-1' for all instances.

### ShowElement

Displays the UI flash asset.

```
UIAction.ShowElement( elementName, instanceID )
```

Parameter | Description
--- | ---
elementName | UI Element name as defined in the xml.
instanceID | ID of the instance (if instance with id does not exist, it will be created). '-1' for all instances.

### HideElement

Hide the UI flash asset.

```
UIAction.HideElement( elementName, instanceID )
```

Parameter | Description
--- | ---
elementName | UI Element name as defined in the xml.
instanceID | ID of the instance (if instance with id does not exist, it will be created). '-1' for all instances.

### RequestHide

Send the fade out signal to the UI flash asset.

```
UIAction.RequestHide( elementName, instanceID )
```

Parameter | Description
--- | ---
elementName | UI Element name as defined in the xml.
instanceID | ID of the instance (if instance with id does not exist, it will be created). '-1' for all instances.

### CallFunction

Calls a function of the UI flash asset or the UIEventSystem.

```
UIAction.CallFunction( elementName, instanceID, functionName, [arg1], [arg2], [...] )
```

Parameter | Description
--- | ---
elementName | UI Element name as defined in the xml or UIEventSystem name as defined via cpp.
instanceID | ID of the instance (if instance with id does not exist, it will be created). '-1' for all instances. If used on UIEventSystem no instance id is ignored.
functionName | Function or event name.
args | List of arguments (optional).

### SetVariable

Sets a variable of the UI flash asset.

```
UIAction.SetVariable( elementName, instanceID, varName, value )
```

Parameter | Description
--- | ---
elementName | UI Element name as defined in the xml.
instanceID | ID of the instance (if instance with id does not exist, it will be created). '-1' for all instances.
varName | Variable name as defined in the xml.
value | Value to set.

### GetVariable

Gets a variable of the UI flash asset.

```
UIAction.GetVariable( elementName, instanceID, varName )
```

Parameter | Description
--- | ---
elementName | UI Element name as defined in the xml.
instanceID | ID of the instance (if instance with id does not exist, it will be created). '-1' for all instances.
varName | Variable name as defined in the xml.

### SetArray

Sets an array of the UI flash asset.

```
UIAction.SetArray( elementName, instanceID, arrayName, values )
```

Parameter | Description
--- | ---
elementName | UI Element name as defined in the xml.
instanceID | ID of the instance (if instance with id does not exist, it will be created). '-1' for all instances.
arrayName | Array name as defined in the xml.
values | Table of values for the array.

### GetArray

Returns a table with values of the array.

```
UIAction.GetArray( elementName, instanceID, arrayName )
```

Parameter | Description
--- | ---
elementName | UI Element name as defined in the xml.
instanceID | ID of the instance (if instance with id does not exist, it will be created). '-1' for all instances.
arrayName | Array name as defined in the xml.

### GotoAndPlay

Call GotoAndPlay on a MovieClip.

```
UIAction.GotoAndPlay( elementName, instanceID, mcName, frameNum )
```

Parameter | Description
--- | ---
elementName | UI Element name as defined in the xml.
instanceID | ID of the instance (if instance with id does not exist, it will be created). '-1' for all instances.
mcName | MovieClip name as defined in the xml.
frameNum | frame number.

### GotoAndStop

Call GotoAndStop on a MovieClip.

```
UIAction.GotoAndStop( elementName, instanceID, mcName, frameNum )
```

Parameter | Description
--- | ---
elementName | UI Element name as defined in the xml.
instanceID | ID of the instance (if instance with id does not exist, it will be created). '-1' for all instances.
mcName | MovieClip name as defined in the xml.
frameNum | frame number.

### GotoAndPlayFrameName

Call GotoAndPlay on a MovieClip by frame name.

```
UIAction.GotoAndPlayFrameName( elementName, instanceID, mcName, frameName )
```

Parameter | Description
--- | ---
elementName | UI Element name as defined in the xml.
instanceID | ID of the instance (if instance with id does not exist, it will be created). '-1' for all instances.
mcName | MovieClip name as defined in the xml.
frameName | frame name.

### GotoAndStopFrameName

Call GotoAndStop on a MovieClip by frame name.

```
UIAction.GotoAndStopFrameName( elementName, instanceID, mcName, frameName )
```

Parameter | Description
--- | ---
elementName | UI Element name as defined in the xml.
instanceID | ID of the instance (if instance with id does not exist, it will be created). '-1' for all instances.
mcName | MovieClip name as defined in the xml.
frameName | frame name.

### SetAlpha

Set MovieClip alpha value.

```
UIAction.SetAlpha( elementName, instanceID, mcName, fAlpha )
```

Parameter | Description
--- | ---
elementName | UI Element name as defined in the xml.
instanceID | ID of the instance (if instance with id does not exist, it will be created). '-1' for all instances.
mcName | MovieClip name as defined in the xml.
fAlpha | alpha value (0-1).

### GetAlpha

Get MovieClip alpha value.

```
UIAction.GetAlpha( elementName, instanceID, mcName )
```

Parameter | Description
--- | ---
elementName | UI Element name as defined in the xml.
instanceID | ID of the instance (if instance with id does not exist, it will be created). '-1' for all instances.
mcName | MovieClip name as defined in the xml.

### SetVisible

Set MovieClip visible state.

```
UIAction.SetVisible( elementName, instanceID, mcName, bVisible )
```

Parameter | Description
--- | ---
elementName | UI Element name as defined in the xml.
instanceID | ID of the instance (if instance with id does not exist, it will be created). '-1' for all instances.
mcName | MovieClip name as defined in the xml.
bVisible | visible.

### IsVisible

Get MovieClip visible state.

```
UIAction.IsVisible( elementName, instanceID, mcName )
```

Parameter | Description
--- | ---
elementName | UI Element name as defined in the xml.
instanceID | ID of the instance (if instance with id does not exist, it will be created). '-1' for all instances.
mcName | MovieClip name as defined in the xml.

### SetPos

Set MovieClip position.

```
UIAction.SetPos( elementName, instanceID, mcName, vPos )
```

Parameter | Description
--- | ---
elementName | UI Element name as defined in the xml.
instanceID | ID of the instance (if instance with id does not exist, it will be created). '-1' for all instances.
mcName | MovieClip name as defined in the xml.
vPos | position.

### GetPos

Get MovieClip position.

```
UIAction.GetPos( elementName, instanceID, mcName )
```

Parameter | Description
--- | ---
elementName | UI Element name as defined in the xml.
instanceID | ID of the instance (if instance with id does not exist, it will be created). '-1' for all instances.
mcName | MovieClip name as defined in the xml.

### SetRotation

Set MovieClip rotation.

```
UIAction.SetRotation( elementName, instanceID, mcName, vRotation )
```

Parameter | Description
--- | ---
elementName | UI Element name as defined in the xml.
instanceID | ID of the instance (if instance with id does not exist, it will be created). '-1' for all instances.
mcName | MovieClip name as defined in the xml.
vRotation | rotation.

### GetRotation

Get MovieClip rotation.

```
UIAction.GetRotation( elementName, instanceID, mcName )
```

Parameter | Description
--- | ---
elementName | UI Element name as defined in the xml.
instanceID | ID of the instance (if instance with id does not exist, it will be created). '-1' for all instances
mcName | MovieClip name as defined in the xml.

### SetScale

Set MovieClip scale.

```
UIAction.SetScale( elementName, instanceID, mcName, vScale )
```

Parameter | Description
--- | ---
elementName | UI Element name as defined in the xml.
instanceID | ID of the instance (if instance with id does not exist, it will be created). '-1' for all instances.
mcName | MovieClip name as defined in the xml.
vScale | scale.

### GetScale

Get MovieClip scale.

```
UIAction.GetScale( elementName, instanceID, mcName  )
```

Parameter | Description
--- | ---
elementName | UI Element name as defined in the xml.
instanceID | ID of the instance (if instance with id does not exist, it will be created). '-1' for all instances.
mcName | MovieClip name as defined in the xml.

### StartAction

Starts a UI Action.

```
UIAction.StartAction( actionName, arguments )
```

Parameter | Description
--- | ---
actionName | UI Action name.
arguments | arguments to pass to this action.

### EndAction

Ends a UI Action. This can be only used withing a UIAction Lua script!

```
UIAction.EndAction( table, disable, arguments )
```

Parameter | Description
--- | ---
table | must be "self".
disable | if true this action gets disabled on end.
arguments | arguments to return from this action.

### EnableAction

Enables the UI Action.

```
UIAction.EnableAction( actionName )
```

Parameter | Description
--- | ---
actionName | UI Action name.

### DisableAction

Disables the UI Action.

```
UIAction.DisableAction( actionName )
```

Parameter | Description
--- | ---
actionName | UI Action name.

### RegisterElementListener

Register a callback function for a UIElement event. Callback Function must have form: CallbackName(elementName, instanceId, eventName, argTable)

```
UIAction.RegisterElementListener( table, elementName, instanceID, eventName, callbackFunctionName )
```

Parameter | Description
--- | ---
table | the script that receives the callback (can be "self" to refer the current script).
elementName | UI Element name as defined in the xml.
instanceID | ID of the instance (if instance with id does not exist, it will be created). '-1' for all instances.
eventName | Name of the event that is fired from the UI Element - if empty string it will receive all events!
callbackFunctionName | name of the script function that will receive the callback.

### RegisterActionListener

Register a callback function for a UIAction event. Callback Function must have form: CallbackName(actionName, eventName, argTable)

```
UIAction.RegisterActionListener( table, actionName, eventName, callbackFunctionName )
```

Parameter | Description
--- | ---
table | the script that receives the callback (can be "self" to refer the current script).
actionName | UI Action name.
eventName | Name of the event that is fired from the UI Action (can be "OnStart" or "OnEnd") - if empty string it will receive all events!
callbackFunctionName | name of the script function that will receive the callback.

### RegisterEventSystemListener

Register a callback function for a UIEventSystem event. Callback Function must have form: CallbackName(actionName, eventName, argTable)

```
UIAction.RegisterEventSystemListener( table, eventSystem, eventName, callbackFunctionName )
```

Parameter | Description
--- | ---
table | the script that receives the callback (can be "self" to refer the current script).
eventSystem | UI Event System name
eventName | Name of the event that is fired from the UI EventSystem - if empty string it will receive all events!
callbackFunctionName | name of the script function that will receive the callback.

### UnregisterElementListener

Unregister callback functions for a UIElement event.

```
UIAction.UnregisterElementListener( table, callbackFunctionName )
```

Parameter | Description
--- | ---
table | the script that receives the callback (can be "self" to refer the current script).
callbackFunctionName | name of the script function that receives the callback. if "" all callbacks for this script will be removed.

### UnregisterActionListener

Unregister callback functions for a UIAction event.

```
UIAction.UnregisterActionListener( table, callbackFunctionName )
```

Parameter | Description
--- | ---
table | the script that receives the callback (can be "self" to refer the current script).
callbackFunctionName | name of the script function that receives the callback. if "" all callbacks for this script will be removed.

### UnregisterEventSystemListener

Unregister callback functions for a UIEventSystem event.

```
UIAction.UnregisterEventSystemListener( table, callbackFunctionName )
```

Parameter | Description
--- | ---
table | the script that receives the callback (can be "self" to refer the current script).
callbackFunctionName | name of the script function that receives the callback. if "" all callbacks for this script will be removed.
