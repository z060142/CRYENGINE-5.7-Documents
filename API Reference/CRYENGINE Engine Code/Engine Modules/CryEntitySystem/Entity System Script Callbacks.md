# Entity System Script Callbacks

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/23306636
- Page ID: 23306636
- Breadcrumb: CRYENGINE Engine Code > Engine Modules > CryEntitySystem > Entity System Script Callbacks
- Parent: CryEntitySystem

## Content

### Overview

The Entity System Callbacks are called as needed by the Entity System. The implementation of these callbacks functions is not obligatory, but in some cases it's required to have entities that behave properly within Sandbox. i.e; the Reset callback should be used to clean the state when the user enter/leave the game mode within Sandbox.

### Default State Functions

**State function** | **Description**
--- | ---
**OnSpawn** | Called after the entity was created by the entity system.
**OnDestroy** | Called when the entity is destroyed. (just like OnShutDown() gets called)
**OnInit** | Called when the entity gets initialized via ENTITY_EVENT_INIT as well as when its ScriptProxy gets initialized.
**OnShutDown** | Called when the entity is destroyed. (just like OnDestroy() gets called)
**OnReset** | Mostly called when Editor wants to Reset the state.
**OnPropertyChange** | Sandbox will call this function when the user is changing one of the properties.

### Script State Functions

**State function** | **Description**
--- | ---
**OnBeginState** | Called during Entity.GotoState() after the state has just been changed (i. e. after OnEndState() got called on the old state).
**OnEndState** | Called during Entity.GotoState() while the old state is still active and before OnBeginState() gets called on the new state.
**OnUpdate** | Called periodically by the engine on the entity's current state (presuming the "es_UpdateScript cvar is set to 1)
**OnTimer** | Called whenever a timer has expired. 2 Integer parameters will be passed in: 1. the timerId provided by Entity.SetTimer(), 2. the period in milliseconds at which the timer runs.
**OnEvent** | Not used anymore.
**OnDamage** | Not used anymore.
**OnEnterArea** | Called when the entity has fully entered an area or trigger. Parameters passed in: 1. areaId (int), 2. fade fraction (float) (this is always 1.0f since we've fully entered the area, and 0.0f in case of trigger boxes)
**OnLeaveArea** | Called when the entity has fully left an area or trigger. Parameters passed in: 1. areaId (int), 2. fade fraction (float) (this is always 0.0f)
**OnEnterNearArea** | Called when the entity comes inside the range of an area. Works with Box-, Sphere- and Shape-Areas if a sound volume entity is connected. Takes OuterRadius of sound entity into account to determine when an entity is near the area.
**OnMoveNearArea** | Called when the entity moves. Works with Box-, Sphere- and Shape-Areas if a sound volume entity is connected. Takes OuterRadius of sound entity into account to determine when an entity is near the area.
**OnLeaveNearArea** | Called when the entity leaves the range of an area. Works with Box-, Sphere- and Shape-Areas if a sound volume entity is connected. Takes OuterRadius of sound entity into account to determine when an entity is near the area.
**OnProceedFadeArea** | Called while the entity has recently entered an area and fading is still in progress. Parameters passed in: 1. areaId (int), 2. fade fraction (float)
**OnBind** | Called when a child entity got attached to the entity. Parameters: script table of that child entity
**OnUnBind** | Called when a child entity is about to get detached from the entity. Parameters: script table of that child entity
**OnMove** | Called whenever the entity gets moved through the world. Parameters: none
**OnCollision** | Called when a collision between the entity and something else occurred. Parameters: script table that holds various information of the collision.
**OnAnimationEvent** | No longer used.
**OnPhysicsBreak** |
**OnSoundDone** | Called when a sound has stopped. Parameters: soundId (int) (this is an ID that the caller provided when he requested to play a sound)
**OnStartLevel** | Called when a new level has been started.
**OnStartGame** | Called when the game has been started.
