# Game Nodes

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/29450591
- Page ID: 29450591
- Breadcrumb: Editor Tools > Flow Graph > Flow Graph Node Reference > Game Nodes
- Parent: Flow Graph Node Reference

## Content

### CheckPlatform

Use this node to change game events depending on what platform you are running the game on.

![Image](https://www.cryengine.com/docs/static/attachments/28901287)

**Inputs**

Port | Type | Description
--- | --- | ---
**Check** | Any | Triggers a check of the current platform

**Outputs**

Port | Type | Description
--- | --- | ---
**PC** | Any | Triggers if the platform is PC
**PS4** | Any | Triggers if the platform is PS4
**XboxOne** | Any | Triggers if the platform is XboxOne

![Image](https://www.cryengine.com/docs/static/attachments/28901286)

In the above example, we have setup a script that checks which platform the game is running on, then it will enable the appropriate entities.

So PC will enable all four entities, the Xbox360 will enable the first three and then the PS3 will enable the first two entities.

### ForceFeedback

FlowNode to play/stop force feedback effects.

### ForceFeedbackTweaker

FlowNode to control individual high and low frequency force feedback effect.

### GetEntityState

Get current state of an entity.

### GetGameRulesEntityId

Calls a script function on the entity.

### GetSupportedGameRulesForMap

Get supported gamerules for a map.

### IsLevelOfType

Check if a level is of given type.

### ObjectEvent

Broadcast a game object event or send to a specific entity. EventParam is an event-specific string.

### PauseGameUpdate

This node allows pausing/unpausing the game update and querying its state.

![Image](https://www.cryengine.com/docs/static/attachments/28901288)

USE THIS NODE IN UI FLOWGRAPH (e.g. UI_ACTIONS) NOT IN GAME FLOWGRAPH.

### Start

Fires on the start of the game, used to trigger flowgraphs on level start.

### Deprecated Nodes

- Game:ActorCheckHealth (now Actor:HealthCheck)
- Game:ActorGetHealth (now Actor:HealthGet)
- Game:ActorSensor (now Actor:Sensor)
- Game:ActorSetHealth (now Actor:HealthSet)
- Game:DamageActor (now Actor:Damage)
- Game:DisplayTag (now Debug:DisplayTag)
- Game:DisplayTagAdv (now Debug:DisplayTagAdv)
- Game:LocalPlayer (now Actor:LocalPlayer)
- Game:PlayerLink (now Actor:PlayerLink)
- Game:SetVehicleAltitudeLimit (deprecated, use v_altitudeLimit CVar)
- Game:DifficultyLevel
- Game:EventListener
- Game:FireSystemEvent
- Game:ForceFeedbackTriggerTweaker
- Game:GiveAchievement
- Game:IsDemo
- Game:IsZoomToggling
- Game:MP:SetEquipmentLoadout
- Game:RoundTrigger
- Game:SaveGame
- Game:SetPostEffectParam
- Game:TutorialPlayerSP
- Game:WeaponSensor

[CheckPlatform](#checkplatform)[ForceFeedback](#forcefeedback)[ForceFeedbackTweaker](#forcefeedbacktweaker)[GetEntityState](#getentitystate)[GetGameRulesEntityId](#getgamerulesentityid)[GetSupportedGameRulesForMap](#getsupportedgamerulesformap)[IsLevelOfType](#isleveloftype)[ObjectEvent](#objectevent)[PauseGameUpdate](#pausegameupdate)[Start](#start)[Deprecated Nodes](#deprecated-nodes)
