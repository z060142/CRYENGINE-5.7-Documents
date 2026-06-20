# ScriptBind_AI

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/23306598
- Page ID: 23306598
- Breadcrumb: CRYENGINE API Reference > ScriptBind Reference > CRYENGINE Functions > ScriptBind_AI
- Parent: CRYENGINE Functions

## Content

### LogProgress

Used to indicate "progress markers"">e.g. during loading.</description> <param name="szMessage">message line to be displayed in log

```
AI.LogProgress( szMessage )
```

### LogEvent

Used to indicate event-driven info that would be useful for debugging (may occur on a per-frame or even per-AI-update basis).

```
AI.LogEvent( szMessage )
```

Parameter | Description
--- | ---
szMessage | message line to be displayed in log

### LogComment

Used to indicate info that would be useful for debugging, but there's too much of it for it to be enabled all the time.

```
AI.LogComment( szMessage )
```

Parameter | Description
--- | ---
szMessage | message line to be displayed in log

### Warning

Used for warnings about data/script errors.

```
AI.Warning( szMessage )
```

Parameter | Description
--- | ---
szMessage | message line to be displayed in log

### Error

Used when we really can't handle some data/situation. The code following this should struggle on so that the original cause (e.g. data) of the problem can be fixed in the editor, but in game this would halt execution.

```
AI.Error( szMessage )
```

Parameter | Description
--- | ---
szMessage | message line to be displayed in log

### RecComment

Record comment with AIRecorder.

```
AI.RecComment( szMessage )
```

Parameter | Description
--- | ---
szMessage | message line to be displayed in recorder view

### ResetParameters

Resets all the AI parameters.

```
AI.ResetParameters( entityId, bProcessMovement, PropertiesTable, PropertiesInstanceTable )
```

Parameter | Description
--- | ---
entityId | entity id
bProcessMovement | reset movement data as well
PropertiesTable | Lua table containing the entity properties like groupid, sightrange, sound range etc (editable in editor, usually defined as "Properties")
PropertiesInstanceTable | another properties table, same as PropertiesTable (editable in editor, usually defined as "PropertiesInstance")

### ChangeParameter

```
AI.ChangeParameter( entityId, paramEnum, paramValue )
```

Parameter | Description
--- | ---
paramValue | new parameter value, see above for type and meaning.

### IsEnabled

Returns true if entity's AI is enabled.

```
AI.IsEnabled( entityId )
```

Parameter | Description
--- | ---
entityId | entity id

### GetTypeOf

returns the given entity's type.

```
AI.GetTypeOf( entityId )
```

**Returns:** type of given entity (as defined in IAgent.h)
Parameter | Description
--- | ---
entityId | AI's entity id

### GetSubTypeOf

returns the given entity's sub type.

```
AI.GetSubTypeOf( entityId )
```

**Returns:** sub type of given entity (as defined in IAgent.h).
Parameter | Description
--- | ---
entityId | AI's entity id

### GetParameter

Changes an enumerated AI parameter.

```
AI.GetParameter( entityId, paramEnum )
```

**Returns:** parameter value
Parameter | Description
--- | ---
entityId | entity id
paramEnum | index of the parameter to get, see AI.ChangeParameter() for complete list

### ChangeMovementAbility

Changes an enumerated AI movement ability parameter.

```
AI.ChangeMovementAbility( entityId, paramEnum, paramValue )
```

Parameter | Description
--- | ---
entityId | entity id
paramEnum | the parameter to change, should be one of the following: AIMOVEABILITY_OPTIMALFLIGHTHEIGHT - optimal flight height while finding path (meters). AIMOVEABILITY_MINFLIGHTHEIGHT - minimum flight height while finding path (meters). AIMOVEABILITY_MAXFLIGHTHEIGHT - maximum flight height while finding path (meters).
paramValue | new parameter value, see above for type and meaning.

### ExecuteAction

Executes an Action on a set of Participants.

```
AI.ExecuteAction( action, participant1 [, participant2 [, ... , participantN ] ] )
```

Parameter | Description
--- | ---
action | Smart Object Action name or id
participant1 | entity id of the first Participant in the Action
(optional) participant2..N | entity ids of other participants

### AbortAction

Aborts execution of an action if actionId is specified, or aborts execution of all actions if actionId is nil or 0

```
AI.AbortAction( userId [, actionId ] )
```

Parameter | Description
--- | ---
userId | entity id of the user which AI action is aborted
actionId (optional) | id of action to be aborted or 0 (or nil) to abort all actions on specified entity

### SetSmartObjectState

Sets only one single smart object state replacing all other states.

```
AI.SetSmartObjectState( entityId, stateName )
```

Parameter | Description
--- | ---
entityId | entity id
stateName | name of the new state (i.e. "Idle")

### ModifySmartObjectStates

Adds/Removes smart object states of a given entity.

```
AI.ModifySmartObjectStates( entityId, listStates )
```

Parameter | Description
--- | ---
entityId | entity id
listStates | names of the states to be added and removed (i.e. "Closed, Locked">Open, Unlocked, Busy")

### SmartObjectEvent

Executes a smart action.

```
AI.SmartObjectEvent( actionName, userEntityId, objectEntityId [, vRefPoint] )
```

**Returns:** 0 if smart object rule wasn't found or a non-zero unique id of the goal pipe inserted to execute the action.
Parameter | Description
--- | ---
actionName | smart action name
usedEntityId | entity id of the user who needs to execute the smart action or a nil if user is unknown
objectEntityId | entity id of the object on which the smart action needs to be executed or a nil if objects is unknown
vRefPoint | (optional) point to be used instead of user's attention target position

### GetLastUsedSmartObject

Returns the last used smart object.

```
AI.GetLastUsedSmartObject( userEntityId )
```

**Returns:** nil if there's no last used smart object (or if an error has occurred) or the script table of the entity which is the last used smart object
Parameter | Description
--- | ---
usedEntityId | entity id of the user for which its last used smart object is needed

### CreateGoalPipe

Used for warnings about data/script errors.

```
AI.CreateGoalPipe( szPipeName )
```

Parameter | Description
--- | ---
szPipeName | goal pipe name

### BeginGoalPipe

Creates a goal pipe and allows to start filling it.

```
AI.BeginGoalPipe( szPipeName )
```

Parameter | Description
--- | ---
szPipeName | goal pipe name

### EndGoalPipe

Ends creating a goal pipe.

```
AI.EndGoalPipe()
```

### BeginGroup

to define group of goals.

```
AI.BeginGroup()
```

### EndGroup

Defines the end of a group of goals.

```
AI.EndGroup()
```

### PushGoal

Used for warnings about data/script errors. <param name="until the goal has finished) 0: not blocking, 1: blocking</param> <param name="(optional) params">set of parameters depending on the goal selected; see the AI Manual for a complete list of the parameters for each goal

```
AI.PushGoal( szPipeName, goalName, blocking [,{params}] )
```

Parameter | Description
--- | ---
szPipeName | goal pipe name
szGoalName | goal name - see AI Manual for a complete list of goals
blocking | used to mark the goal as blocking (goal pipe execution will stop here

### PushLabel

Used in combination with "branch" goal operation to identify jump destination.

```
AI.PushLabel( szPipeName, szLabelName )
```

Parameter | Description
--- | ---
szPipeName | goalpipe name
szLabelName | label name

### IsGoalPipe

Checks is a goalpipe of certain name exists already, returns true if pipe exists.

```
AI.IsGoalPipe( szPipeName )
```

Parameter | Description
--- | ---
szPipeName | goalpipe name

### ClearForReload

Clears all goalpipes from the system.

```
AI.ClearForReload( szPipeName )
```

### Signal

10: signal is added in the sender's signal queue even if another signal with same text is present (normally it's not) <param name="signalText: signal text which will be processed by the receivers (in a Lua callback with the same name as the text, or directly by the CAIObject)</param> <param name="(optional) signalExtraData: lua table which can be used to send extra data. It can contains the following values: point: a vector in format {x,y,z} point2: a vector in format {x,y,z} ObjectName: a string id: an entity id fValue: a float value iValue: an integer value iValue2: a second integer value

```
AI.Signal(signalFilter, signalType, SignalText, senderId [, signalExtraData] )
```

### FreeSignal

Sends a signal to anyone in a given radius around a position.

```
AI.FreeSignal( signalType, SignalText, position, radius [, entityID [,signalExtraData]] )
```

Parameter | Description
--- | ---
signalType | see AI.Signal
signalText | See AI.Signal
position | center position {x,y,z}around which the signal is sent
radius | radius inside which the signal is sent
(optional) entityID | signal is NOT sent to entities which groupID is same as the entity's one
(optional) signalExtraData | See AI.Signal

### SetIgnorant

makes an AI ignore system signals, visual stimuli and sound stimuli.

```
AI.SetIgnorant( entityId, ignorant )
```

Parameter | Description
--- | ---
entityId | AI's entity id
ignorant | 0: not ignorant, 1: ignorant

### GetGroupCount

returns the given entity's group members count.

```
AI.GetGroupCount( entityId, flags, type )
```

**Returns:** group members count
Parameter | Description
--- | ---
entityId | AI's entity id or groupId - AI's group id
flags | combination of following flags: GROUP_ALL - Returns all agents in the group (default). GROUP_ENABLED - Returns only the count of enabled agents (exclusive with all). GROUP_MAX - Returns the maximum number of agents during the game (can be combined with all or enabled).
type | allows to filter to return only specific AI objects by type (cannot be used in together with GROUP_MAX flag).

### GetGroupMember

returns the idx-th entity in the given group.

```
AI.GetGroupMember( entityId|groupId, idx, flags, type)
```

**Returns:** script handler of idx-th entity (null if idx is out of range)
Parameter | Description
--- | ---
entityId|groupId | AI's entity id \ group id
idx | index (1..N)
flags | combination of following flags: GROUP_ALL - Returns all agents in the group (default). GROUP_ENABLED - Returns only the count of enabled agents (exclusive with all).
type | allows to filter to return only specific AI objects by type (cannot be used in together with GROUP_MAX flag).

### GetGroupOf

returns the given entity's group id.

```
AI.GetGroupOf( entityId )
```

**Returns:** group id of given entity
Parameter | Description
--- | ---
entityId | AI's entity id

### GetFactionOf

```
AI.GetFactionOf( entityID )
```

**Returns:** The faction of the specified entity.

### SetFactionOf

Make the specified entity a member of the named faction.

```
AI.SetFactionOf( entityID, factionName )
```

### GetUnitInRank

Returns the entity in the group id in the given rank position, or the highest if rank == nil or rank <=0 the rank is specified in entity.Properties.nRank

```
AI.GetUnitInRank( groupID [,rank] )
```

**Returns:** entity script table of the ranked unit
Parameter | Description
--- | ---
rank | rank position (the highest (1) if rank == nil or rank <=0)

### SetUnitProperties

Sets the leader knowledge about the units combat capabilities. The leader will be found based on the group id of the entity.

```
AI.SetUnitProperties( entityId, unitProperties )
```

Parameter | Description
--- | ---
entityId | AI's entity id
unitProperties | binary mask of unit properties type for which the attack is requested (in the form of UPR_* + UPR* i.e. UPR_COMBAT_GROUND + UPR_COMBAT_FLIGHT) see IAgent.h for definition of unit properties UPR_*

### GetUnitCount

Gets the number of units the leader knows about. The leader will be found based on the group id of the entity.

```
AI.GetUnitCount( entityId, unitProperties )
```

Parameter | Description
--- | ---
entityId | AI's entity id
unitProperties | binary mask of the returned unit properties type (in the form of UPR_* + UPR* i.e. UPR_COMBAT_GROUND + UPR_COMBAT_FLIGHT) see IAgent.h for definition of unit properties UPR_*

### Hostile

returns true if the two entities are hostile.

```
AI.Hostile( entityId, entity2Id|AIObjectName )
```

**Returns:** true if the entities are hostile
Parameter | Description
--- | ---
entityId | 1st AI's entity id
entity2Id | AIObjectName | 2nd AI's entity id | 2nd AIobject's name

### GetLeader

```
AI.GetLeader( groupID | entityID )
```

**Returns:** the leader's name of the given groupID / entity
Parameter | Description
--- | ---
groupID | group id
entityID | entity (id) of which we want to find the leader

### SetLeader

Set the given entity as Leader (associating a CLeader object to it and creating it if it doesn't exist) Only one leader can be set per group.

```
AI.SetLeader( entityID )
```

**Returns:** true if the leader creation/association has been successful
Parameter | Description
--- | ---
entityID | entity (id) of which to which we want to associate a leader class

### GetBeaconPosition

get the beacon's position for the given entity/object's group.

```
AI.GetBeaconPosition( entityId | AIObjectName, returnPos )
```

**Returns:** true if the beacon has been found and the position set
Parameter | Description
--- | ---
entityId | AIObjectName | AI's entity id | AI object name
returnPos | vector {x,y,z} where the beacon position will be set

### SetBeaconPosition

Set the beacon's position for the given entity/object's group.

```
AI.SetBeaconPosition( entityId | AIObjectName, pos )
```

Parameter | Description
--- | ---
entityId | AIObjectName | AI's entity id | AI object name
pos | beacon position vector {x,y,z}

### RequestAttack

in a group with leader, the entity requests for a group attack behavior against the enemy The Cleader later will possibly create an attack leader action (CLeaderAction_Attack_*)

```
AI.RequestAttack( entityId, unitProperties, attackTypeList [,duration] )
```

Parameter | Description
--- | ---
entityId | AI's entity id which group/leader is determined
unitProperties | binary mask of unit properties type for which the attack is requested (in the form of UPR_* + UPR* i.e. UPR_COMBAT_GROUND + UPR_COMBAT_FLIGHT) see IAgent.h for definition of unit properties UPR_*
attackTypeList | a lua table which contains the list of preferred attack strategies (Leader action subtypes), sorted by priority (most preferred first) the list must be in the format {LAS_*, LAS_*,..} i.e. (LAS_ATTACK_ROW,LAS_ATTACK_FLANK} means that first an Attack_row action will be tried, then an attack_flank if the first ends/fails. see IAgent.h for definition of LeaderActionSubtype (LAS_*) action types
duration | (optional) max duration in sec (default = 0)

### GetGroupTarget

Returns the most threatening attention target amongst the agents in the given entity's group. (see IAgent.h for definition of alert status)

```
AI.GetGroupTarget( entityId [,bHostileOnly [,bLiveOnly]] )
```

Parameter | Description
--- | ---
entityId | AI's entity id which group is determined
bHostileOnly (optional) | filter only hostile targets in group
bLiveOnly (optional) | filter only live targets in group (entities)

### GetGroupTargetType

```
AI.GetGroupTargetType( groupID )
```

### GetGroupTargetThreat

```
AI.GetGroupTargetThreat( groupID )
```

### GetGroupTargetEntity

```
AI.GetGroupTargetEntity( groupID )
```

### GetGroupScriptTable

```
AI.GetGroupScriptTable( groupID )
```

### GetGroupTargetCount

Returns the number of attention targets amongst the agents in the given entity's group.

```
AI.GetGroupTargetCount( entityId [,bHostileOnly [,bLiveOnly]] )
```

Parameter | Description
--- | ---
entityId | AI's entity id which group is determined
bHostileOnly (optional) | filter only hostile targets in group
bLiveOnly (optional) | filter only live targets in group (entities)

### GetGroupAveragePosition

gets the average position of the (leader's) group members

```
AI.GetGroupAveragePosition( entityId, properties, returnPos )
```

**Returns:** Pos returned average position
Parameter | Description
--- | ---
entityId | AI's entity id which group/leader is determined
unitProperties | binary mask of unit properties type for which the attack is requested (in the form of UPR_* + UPR* i.e. UPR_COMBAT_GROUND + UPR_COMBAT_FLIGHT) see IAgent.h for definition of unit properties UPR_*

### FindObjectOfType

returns the closest AIObject of a given type around a given entity/position; once an AIObject is found, it's devalued and can't be found again for some seconds (unless specified in flags).

```
AI.FindObjectOfType( entityId, radius, AIObjectType, flags [,returnPosition [,returnDirection]] ) AI.FindObjectOfType( position, radius, AIObjectType, [,returnPosition [,returnDirection]] )
```

**Returns:** the found AIObject's name (nil if not found)
Parameter | Description
--- | ---
entityId | AI's entity id as a center position of the search (if 1st parameter is not a vector)
position | center position of the search (if 1st parameter is not an entity id)
radius | radius inside which the object must be found
AIObjectType | AIObject type; see ScriptBindAI.cpp and Scripts/AIAnchor.lua for a complete list of AIObject types available
flags | filter for AI Objects to search, which can be the sum of one or more of the following values: AIFAF_VISIBLE_FROM_REQUESTER: Requires whoever is requesting the anchor to also have a line of sight to it AIFAF_VISIBLE_TARGET: Requires that there is a line of sight between target and anchor AIFAF_INCLUDE_DEVALUED: don't care if the object is devalued AIFAF_INCLUDE_DISABLED: don't care if the object is disabled
(optional) returnPosition | position of the found object
(optional) returnDirection | direction of the found object

### GetAnchor

returns the closest Anchor of a given type around a given entity; once an Anchor is found, it's devalued and can't be found again for some seconds (unless specified in flags).

```
AI.GetAnchor( entityId, radius, AIAnchorType, searchType [,returnPosition [,returnDirection]] )
```

**Returns:** the found Anchor's name (nil if not found)
Parameter | Description
--- | ---
entityId | AI's entity id as a center position of the search
radius | radius inside which the object must be found. Alternatively a search range can be specified {min=minRad,max=maxRad}.
AIAnchorType | Anchor type; see Scripts/AIAnchor.lua for a complete list of Anchor types available
searchType | search type filter, which can be one of the following values: AIANCHOR_NEAREST: (default) the nearest anchor of the given type AIANCHOR_NEAREST_IN_FRONT: the nearest anchor inside the front cone of entity AIANCHOR_NEAREST_FACING_AT: the nearest anchor of given type which is oriented towards entity's attention target (...Dejan?) AIANCHOR_RANDOM_IN_RANGE: a random anchor of the given type AIANCHOR_NEAREST_TO_REFPOINT: the nearest anchor of given type to the entity's reference point
(optional) returnPosition | position of the found object
(optional) returnDirection | direction of the found object

### GetNearestEntitiesOfType

```
AI.GetNearestEntitiesOfType( entityId|objectname|position, AIObjectType, maxObjects, returnList [,objectFilter [,radius]] )
```

**Returns:** the number of found entities
Parameter | Description
--- | ---
entityId | objectname |position | AI's entity id | name| position as a center position of the search
radius | radius inside which the entities must be found
AIObjectType | AIObject type; see ScriptBindAI.cpp and Scripts/AIAnchor.lua for a complete list of AIObject types available
maxObjects | maximum number of objects to find
return list | Lua table which will be filled up with the list of the found entities (Lua handlers)
(optional) objectFilter | search type filter, which can be the sum of one or more of the following values: AIOBJECTFILTER_SAMEFACTION: AI objects of the same species of the querying object AIOBJECTFILTER_SAMEGROUP: AI objects of the same group of the querying object or with no group AIOBJECTFILTER_NOGROUP:AI objects with Group ID ==AI_NOGROUP AIOBJECTFILTER_INCLUDEINACTIVE:Includes objects which are inactivated.

### GetAIObjectPosition

get the given AIObject's position.

```
AI.GetAIObjectPosition( entityId | AIObjectName )
```

**Returns:** AI Object position vector {x,y,z}
Parameter | Description
--- | ---
entityId | AIObjectName | AI's entity id | AI object name

### IgnoreCurrentHideObject

Marks the current hideobject unreachable (will be omitted from future hidespot selections).

```
AI.IgnoreCurrentHideObject( entityId )
```

Parameter | Description
--- | ---
entityId | AI's entity id

### GetCurrentHideAnchor

Returns the name of the current anchor the entity is using for cover.

```
AI.GetCurrentHideAnchor( entityId )
```

Parameter | Description
--- | ---
entityId | AI's entity id

### GetAttentionTargetOf

returns the given entity's attention target.

```
AI.GetAttentionTargetOf( entityId )
```

**Returns:** attention target's name (nil if no target)
Parameter | Description
--- | ---
entityId | AI's entity id

### GetAttentionTargetAIType

returns the given entity's attention target AI type (AIOBJECT_*).

```
AI.GetAttentionTargetAIType( entityId )
```

**Returns:** attention target's type (AIOBJECT_NONE if no target)
Parameter | Description
--- | ---
entityId | AI's entity id

### GetAttentionTargetType

returns the given entity's attention target type (AITARGET_*).

```
AI.GetAttentionTargetType( entityId )
```

**Returns:** attention target's type (AITARGET_NONE if no target)
Parameter | Description
--- | ---
entityId | AI's entity id

### GetAttentionTargetEntity

returns the given entity's attention target entity (if it is an entity) or the owner entity of the attention target if it is a dummy object (if there is an owner entity).

```
AI.GetAttentionTargetEntity( entityId )
```

**Returns:** attention target's entity
Parameter | Description
--- | ---
entityId | AI's entity id

### GetAttentionTargetPosition

returns the given entity's attention target's position.

```
AI.GetAttentionTargetPosition( entityId, returnPos )
```

**Returns:** Pos - vector {x,y,z} passed as a return value (attention target 's position)
Parameter | Description
--- | ---
entityId | AI's entity id

### GetAttentionTargetDirection

returns the given entity's attention target's direction.

```
AI.GetAttentionTargetDirection( entityId, returnDir )
```

**Returns:** Dir - vector {x,y,z} passed as a return value (attention target 's direction)
Parameter | Description
--- | ---
entityId | AI's entity id

### GetAttentionTargetViewDirection

returns the given entity's attention target's view direction.

```
AI.GetAttentionTargetViewDirection( entityId, returnDir )
```

**Returns:** Dir - vector {x,y,z} passed as a return value (attention target 's direction)
Parameter | Description
--- | ---
entityId | AI's entity id

### GetAttentionTargetDistance

returns the given entity's attention target's distance to the entity.

```
AI.GetAttentionTargetDistance( entityId )
```

**Returns:** distance to the attention target (nil if no target)
Parameter | Description
--- | ---
entityId | AI's entity id

### GetAttentionTargetThreat

```
AI.GetAttentionTargetThreat( entityID )
```

### UpTargetPriority

modifies the current entity's target priority for the given target if the given target is among the entity's target list.

```
AI.UpTargetPriority( entityId, targetId, increment )
```

Parameter | Description
--- | ---
entityId | AI's entity id
targetId | target's entity id
increment | value to modify the target's priority

### DropTarget

Clears the target from the AI's perception handler.

```
AI.DropTarget( entityId, targetId )
```

Parameter | Description
--- | ---
entityId | AI's entity id
targetId | target's entity id

### ClearPotentialTargets

Clears all the potential targets from the AI's perception handler.

```
AI.ClearPotentialTargets( entityId )
```

Parameter | Description
--- | ---
entityId | AI's entity id

### SetTempTargetPriority

Set the selection priority of the temp target over other potential targets.

```
AI.SetTempTargetPriority( entityId, priority )
```

**Returns:** true if updated
Parameter | Description
--- | ---
entityId | AI's entity id
priority | New priority value

### AddAggressiveTarget

Add the target Id as an aggressive potential target to the entity's list.

```
AI.AddAggressiveTarget( entityId, targetId )
```

**Returns:** true if updated
Parameter | Description
--- | ---
entityId | AI's entity id
targetId | Target to add to the list

### UpdateTempTarget

Updates the entity's temporary potential target to the given position.

```
AI.UpdateTempTarget( entityId, vPos )
```

**Returns:** true if updated
Parameter | Description
--- | ---
entityId | AI's entity id
vPos | New position of the temporary target

### ClearTempTarget

Removes the entity's temporary potential target, so it is no longer considered for target selection.

```
AI.ClearTempTarget( entityId )
```

**Returns:** true if cleared
Parameter | Description
--- | ---
entityId | AI's entity id

### SetExtraPriority

Set a extra priority value to the entity which is given by enemyEntityId.

```
AI.SetExtraPriority( enemyEntityId, increment )
```

Parameter | Description
--- | ---
enemyEntityId | AI's entity id
float increment | value to add to the target's priority

### GetExtraPriority

get an extra priority value to the entity which is given by enemyEntityId.

```
AI.GetExtraPriority( enemyEntityId )
```

Parameter | Description
--- | ---
enemyEntityId | AI's entity id

### GetTargetType

Returns the type of current entity's attention target (memory, human, none etc).

```
AI.GetTargetType(entityId)
```

**Returns:** Target type value (AITARGET_NONE,AITARGET_MEMORY,AITARGET_BEACON,AITARGET_ENEMY etc) - see IAgent.h for all definitions of target types.
Parameter | Description
--- | ---
entityId | AI's entity id

### GetTargetSubType

Returns the subtype of current entity's attention target.

```
AI.GetTargetSubType(entityId)
```

**Returns:** Target subtype value - see IAgent.h for all definitions of target types
Parameter | Description
--- | ---
entityId | AI's entity id

### RegisterTargetTrack

Registers the AI object to use the given target track configuration for target selection.

```
AI.RegisterTargetTrack(entityId, configuration, targetLimit, classThreat)
```

**Returns:** True if registration was successful. Note that this does nothing if 'ai_TargetTracking' is not set to '2'
Parameter | Description
--- | ---
entityId | AI's entity id
configuration | Target stimulus configuration to use
targetLimit | Number of agents who can target the AI at any given time (0 for infinite)
classThreat | (Optional) Initial class threat value for the user

### UnregisterTargetTrack

Unregisters the AI object with the target track manager.

```
AI.UnregisterTargetTrack(entityId)
```

**Returns:** True if unregistration was successful. Note that this does nothing if 'ai_TargetTracking' is not set to '2'.
Parameter | Description
--- | ---
entityId | AI's entity id

### SetTargetTrackClassThreat

Sets the class threat for the entity for target track usage.

```
AI.SetTargetTrackClassThreat(entityId, classThreat)
```

Parameter | Description
--- | ---
entityId | AI's entity id
classThreat | Class threat value for the user

### CreateStimulusEvent

Creates a target track stimulus event for the entity using the specified data.

```
AI.CreateStimulusEvent(entityId, targetId, stimulusName, pData)
```

Parameter | Description
--- | ---
ownerId | Owner's entity id (who owns and is receiving the event)
targetId | Target's entity id (who sent the event, and becomes owner's perceived target)
stimulusName | Name of the stimulus event
pData | Data about the event (see TargetTrackHelpers::SStimulusEvent)

### SoundEvent

Generates a sound event in the AI system with the given parameters.

```
AI.SoundEvent(position, radius, threat, interest, entityId)
```

Parameter | Description
--- | ---
position | of the origin of the sound event
radius | in which this sound event should be heard
threat | value of the sound event
interest | value of the sound event
entityId | of the entity who generated this sound event

### VisualEvent

Generates a visual event in the AI system with the given parameters.

```
AI.VisualEvent(entityId, targetId)
```

Parameter | Description
--- | ---
entityId | who receives the visual event
targetId | who the receiver is seeing

### GetSoundPerceptionDescriptor

Fills descriptorTable with info about how perception works for the entity dealing with soundType.

```
AI.GetSoundPerceptionDescriptor(entityId, soundType, descriptorTable)
```

**Returns:** True if info was returned
Parameter | Description
--- | ---
entityId | who to get the info from
soundType | what type of sound stimulus to get the info for
descriptorTable | where to store the info once retrieved

### SetSoundPerceptionDescriptor

Sets data on how perception works for the entity dealing with soundType.

```
AI.SetSoundPerceptionDescriptor(entityId, soundType, descriptorTable)
```

**Returns:** True if info was saved
Parameter | Description
--- | ---
entityId | who to set the info for
soundType | what type of sound stimulus to set the info for
descriptorTable | info to be set

### SetAssesmentMultiplier

set the assesment multiplier factor for the given AIObject type.

```
AI.SetAssesmentMultiplier(AIObjectType, multiplier)
```

Parameter | Description
--- | ---
AIObjectType | AIObject type; see ScriptBindAI.cpp for a complete list of AIObject types available
multiplier | assesment multiplication factor

### SetFactionThreatMultiplier

set the threat multiplier factor for the given species (if 0, species is not hostile to any other). <param name="factionID: factionID</param> <param name="multiplier">Threat multiplication factor

```
AI.SetFactionThreatMultiplier(nSpecies, multiplier)
```

### GetRefPointPosition

Get the entity's reference point World position.

```
AI.GetRefPointPosition(entityId)
```

**Returns:** (script)vector (x,y,z) reference point position
Parameter | Description
--- | ---
entityId | AI's entity id

### GetRefPointDirection

Get the entity's reference point direction.

```
AI.GetRefPointDirection(entityId)
```

**Returns:** (script)vector (x,y,z) reference point direction
Parameter | Description
--- | ---
entityId | AI's entity id

### SetRefPointPosition

Sets the reference point's World position of an entity

```
AI.SetRefPointPosition(entityId, vRefPointPos)
```

Parameter | Description
--- | ---
entityId | AI's entity id
vRefPointPos | (script)vector (x,y,z) value

### SetRefPointDirection

Sets the reference point's World position of an entity

```
AI.SetRefPointDirection( vRefPointDir )
```

Parameter | Description
--- | ---
vRefPointDir | (script)vector (x,y,z) value

### SetRefPointRadius

Sets the reference point's radius.

```
AI.SetRefPointRadius(entityId, radius)
```

Parameter | Description
--- | ---
entityId | AI's entity id
radius | the radius to set.

### SetRefShapeName

Sets the reference shape name.

```
AI.SetRefShapeName(entityId, name)
```

Parameter | Description
--- | ---
entityId | AI's entity id
name | the name of the reference shape.

### GetRefShapeName

```
AI.GetRefShapeName(entityId)
```

**Returns:** reference shape name.
Parameter | Description
--- | ---
entityId | AI's entity id

### SetTerritoryShapeName

Sets the territory of the AI Actor.

```
AI.SetTerritoryShapeName(entityId, shapeName)
```

Parameter | Description
--- | ---
entityId | AI's entity id
shapeName | name of the shape to set

### SetRefPointAtDefensePos

Set the entity refpoint position in an intermediate distance between the entity's att target and the given point.

```
AI.SetRefPointAtDefensePos(entityId, point2defend, distance)
```

Parameter | Description
--- | ---
entityId | AI's entity id
point2defend | point to defend
distance | max distance to keep from the point

### SetPathToFollow

Set the name of the path to be used in 'followpath' goal operation.

```
AI.SetPathToFollow(entityId, pathName)
```

Parameter | Description
--- | ---
entityId | AI's entity id
pathName | (string) name of the path to set to be followed.

### SetPathAttributeToFollow

Set the attribute of the path to be used in 'followpath' goal operation.

```
AI.SetPathAttributeToFollow(entityId, flag)
```

Parameter | Description
--- | ---
entityId | AI's entity id
flag | .

### GetNearestPathOfTypeInRange

Queries a nearest path of specified type. The type uses same types as anchors and is specified in the path properties. The function will only return paths that match the requesters (entityId) navigation caps. The nav type is also specified in the path properties.

```
AI.GetNearestPathOfTypeInRange(entityId, pos, range, type [, devalue, useStartNode])
```

Parameter | Description
--- | ---
entityId | AI's entity id
pos | a vector specifying to the point of interest. Path nearest to this position is returned.
range | search range. If useStartNode=1, paths whose start point are within this range are returned or if useStartNode=0 nearest distance to the path is calculated and compared against the range.
type | type of path to return.
devalue | (optional) specifies the time the returned path is marked as occupied.
useStartNode | (optional) if set to 1 the range check will use distance to the start node on the path, else nearest distance to the path is used.

### GetTotalLengthOfPath

```
AI.GetTotalLengthOfPath( entityId, pathname )
```

**Returns:** a total length of the path
Parameter | Description
--- | ---
entityId | AI's entity id
pathname | designers path name

### GetNearestPointOnPath

```
AI.GetNearestPointOnPath( entityId, pathname, vPos )
```

**Returns:** a nearest point on the path from vPos
Parameter | Description
--- | ---
entityId | AI's entity id
pathname | designers path name
vPos | .

### GetPathSegNoOnPath

```
AI.GetPathSegNoOnPath( entityId, pathname, vPos )
```

**Returns:** segment ratio ( 0.0 start point 100.0 end point )
Parameter | Description
--- | ---
entityId | AI's entity id
pathname | designer's path name
vPos | .

### GetPointOnPathBySegNo

```
AI.GetPathSegNoOnPath( entityId, pathname, segNo )
```

**Returns:** returns point by segment ratio ( 0.0 start point 100.0 end point )
Parameter | Description
--- | ---
entityId | AI's entity id
pathname | designer's path name
segNo | segment ratio

### GetPathLoop

```
AI.GetPathSegNoOnPath( entityId, pathname )
```

**Returns:** returns true if the path is looped
Parameter | Description
--- | ---
entityId | AI's entity id
pathname | designer's path name

### GetPredictedPosAlongPath

Gets the agent predicted position along his path at a given time

```
AI.GetPredictedPosAlongPath( entityId, time, retPos )
```

**Returns:** true if successful
Parameter | Description
--- | ---
entityId | AI's entity id
time | prediction time (sec)
retPos | return point value

### SetPointListToFollow

Set a point list for followpath goal op

```
AI.SetPointListToFollow(entityId, pointlist, howmanypoints, bspline [, navtype])
```

Parameter | Description
--- | ---
entityId | AI's entity id
pointList | should be like below local vectors = { { x = 0.0, y = 0.0, z = 0.0 },
howmanypoints | .
bspline | if true, the line is recalcurated by spline interpolation.
navtype | (optional) specify a navigation type (default = IAISystem::NAV_FLIGHT)

### CanMoveStraightToPoint

```
AI.CanMoveStraightToPoint(entityId, position)
```

**Returns:** true if the entity can move to the specified position in a straight line (no multiple segment path necessary)
Parameter | Description
--- | ---
entityId | AI's entity id
position | the position to check

### GetNearestHidespot

```
AI.GetNearestHidespot(entityId, rangeMin, rangeMax [, center])
```

**Returns:** position of a nearest hidepoint within specified range, returns nil if no hidepoint is found.
Parameter | Description
--- | ---
entityId | AI's entity id
rangeMin | specifies the min range where the hidepoints are looked for.
rangeMax | specifies the max range where the hidepoints are looked for.
centre | (optional) specifies the centre of search. If not specified, the entity position is used.

### GetEnclosingGenericShapeOfType

```
AI.GetEnclosingGenericShapeOfType(position, type[, checkHeight])
```

**Returns:** the name of the first shape that is enclosing the specified point and is of specified type
Parameter | Description
--- | ---
position | the position to check
type | the type of the shapes to check against (uses anchor types).
checkHeight | (optional) Default=false, if the flag is set the height of the shape is tested too. The test will check space between the shape.aabb.min.z and shape.aabb.min.z+shape.height.

### IsPointInsideGenericShape

```
AI.IsPointInsideGenericShape(position, shapeName[, checkHeight])
```

**Returns:** true if the point is inside the specified shape.
Parameter | Description
--- | ---
position | the position to check
shapeName | the name of the shape to test (returned by AI.GetEnclosingGenericShapeOfType)
checkHeight | (optional) Default=false, if the flag is set the height of the shape is tested too. The test will check space between the shape.aabb.min.z and shape.aabb.min.z+shape.height.

### ConstrainPointInsideGenericShape

```
AI.ConstrainPointInsideGenericShape(position, shapeName[, checkHeight])
```

**Returns:** the nearest point inside specified shape.
Parameter | Description
--- | ---
position | the position to check
shapeName | the name of the shape to use as constraint.
checkHeight | (optional) Default=false, if the flag is set the height should be constrained too.

### DistanceToGenericShape

```
AI.DistanceToGenericShape(position, shapeName[, checkHeight])
```

**Returns:** true if the point is inside the specified shape.
Parameter | Description
--- | ---
position | the position to check
shapeName | the name of the shape to test (returned by AI.GetEnclosingGenericShapeOfType)
checkHeight | (optional) if the flag is set the height of the shape is tested too. The test will check space between the shape.aabb.min.z and shape.aabb.min.z+shape.height.

### CreateTempGenericShapeBox

Creates a temporary box shaped generic shape (will be destroyed upon AIsystem reset).

```
AI.CreateTempGenericShapeBox(center, radius, height, type)
```

**Returns:** the name of the shape.
Parameter | Description
--- | ---
center | the center of the box
radius | the extend of the box in x and y directions.
height | the height of the box.
type | the AIanchor type of the shape.

### GetObjectRadius

```
AI.GetObjectRadius(entityId)
```

**Returns:** the radius of specified AI object.
Parameter | Description
--- | ---
entityId | AI's entity id

### GetProbableTargetPosition

```
AI.GetProbableTargetPosition(entityId)
```

**Returns:** the probable target position of the AI.
Parameter | Description
--- | ---
entityId | AI's entity id

### EvalPeek

Evaluates if an AI object can peek from his current position.

```
AI.EvalPeek(entityId [, bGetOptimalSide])
```

**Returns:** -1 - don't need to peek 0 - cannot peek 1 - can peek from left 2 - can peek from right 3 - can peek from left & right
Parameter | Description
--- | ---
entityId | AI's entity id
bGetOptimalSide (optional) | If TRUE, and AI object can peek from both sides, will return the side that best fits where the attention target currently is

### AddPersonallyHostile

```
AI.AddPersonallyHostile(entityID, hostileID)
```

### RemovePersonallyHostile

```
AI.RemovePersonallyHostile(entityID, hostileID)
```

### ResetPersonallyHostiles

```
AI.ResetPersonallyHostiles(entityID, hostileID)
```

### IsPersonallyHostile

```
AI.IsPersonallyHostile(entityID, hostileID)
```

### GetDirectAnchorPos

```
AI.GetDirectAttackPos(entityId, searchRange, minAttackRange)
```

**Returns:** a cover point which can be used to directly attack the attention target, nil if no attack point is available.
Parameter | Description
--- | ---
entityId | AI's entity id
AIAnchorType | Anchor type; see Scripts/AIAnchor.lua for a complete list of Anchor types available
maxDist | search range

### GetPotentialTargetCountFromFaction

Retrieves the number of potential targets for an entity from a specified factions.

```
AI.GetPotentialTargetCountFromFaction( entityID, name )
```

Parameter | Description
--- | ---
entityId | id handle of entity to match against.
name | name of specified faction.

### GetPotentialTargetCount

Retrieves the number of potential targets for an entity from a specified factions.

```
AI.GetPotentialTargetCount( entityID )
```

Parameter | Description
--- | ---
entityId | id handle of entity to match against.

### CreateFormation

Creates a formation descriptor and adds a fixed node at 0,0,0 (owner's node).

```
AI.CreateFormation( name )
```

Parameter | Description
--- | ---
name | name of the new formation descriptor.

### AddFormationPointFixed

Adds a node with a fixed offset to a formation descriptor.

```
AI.AddFormationPointFixed(name, sightangle, x, y, z [,unit_class])
```

Parameter | Description
--- | ---
name | name of the formation descriptor
sightangle | angle of sight of the node (-180,180; 0 = the guy looks forward)
x, y, z | offset from formation owner
unit_class | class of soldier (see eSoldierClass definition in IAgent.h)

### AddFormationPoint

Adds a follow-type node to a formation descriptor. <param name="distanceAlt (optional)- alternative distance from the formation owner (if 0, distanceAlt and offsetAlt will be set respectively to distance and offset)</param> <param name="offsetAlt (optional)">alternative X offset

```
AI.AddFormationPoint(name, sightangle, distance, offset, [unit_class [,distanceAlt, offsetAlt]] )
```

Parameter | Description
--- | ---
name | name of the formation descriptor
sightangle | angle of sight of the node (-180,180; 0 = the guy looks forward)
distance | distance from the formation's owner
offset | X offset along the following line (negative = left, positive = right)
unit_class | class of soldier (see eSoldierClass definition in IAgent.h)

### GetFormationPointClass

Adds a follow-type node to a formation descriptor.

```
AI.AddFormationPoint(name, position )
```

**Returns:** class of specified formation point (-1 if not found)
Parameter | Description
--- | ---
name | name of the formation descriptor
position | point index in the formation (1..N)

### GetFormationPointPosition

Gets the AI's formation point position.

```
AI.GetFormationPointPosition(entityId, pos)
```

**Returns:** true if the formation point has been found
Parameter | Description
--- | ---
entityId | AI's entity id
pos | return value- position of entity AI's current formation point if there is

### BeginTrackPattern

Begins definition of a new track pattern descriptor. The pattern is created bu calling the AI.AddPatternPoint() and AI.AddPatternBranch() functions, and finalised by calling the AI.EndTrackPattern().

```
AI.BeginTrackPattern( patternName, flags, validationRadius, [stateTresholdMin],
```

Parameter | Description
--- | ---
patternName | name of the new track pattern descriptor
flags | The functionality flags of the track pattern. Validation: The validation method describes how the pattern is validated to fit the physical world. Should be one of: AITRACKPAT_VALIDATE_NONE - no validation at all. AITRACKPAT_VALIDATE_SWEPTSPHERE - validate using swept sphere tests, the spehre radius is validation radius plus the entity pass radius. AITRACKPAT_VALIDATE_RAYCAST - validate using raycasting, the hit position is pulled back by the amount of validation radius plus the entity pass radius. Aligning: When the pattern is selected to be used the alignment of the patter ncan be changed. The alignment can be combination of the following. The descriptions are in order they are evaluated. AITRACKPAT_ALIGN_TO_TARGET - Align the pattern so that the y-axis will point towards the target each time it is set. If the agent does not have valid attention target at the time the pattern is set the pattern will be aligned to the world. AITRACKPAT_ALIGN_RANDOM - Align the pattern randonly each time it is set. The rotation ranges are set using SetRandomRotation().
validationRadius | the validation radius is added to the entity pass radius when validating the pattern along the offsets.
stateTresholdMin (optional) | If the state of the pattern is 'enclosed' (high deformation) and the global deformation < stateTresholdMin, the state becomes exposed. Default 0.35.
stateTresholdMax (optional) | If the state of the pattern is 'exposed' (low deformation) and the global deformation > stateTresholdMax, the state becomes enclosed. Default 0.4.
globalDeformTreshold (optional) | the deformation of the whole pattern is tracked in range [0..1]. This treshold value can be used to clamp the bottom range, so that values in range [trhd..1] becomes [0..1], default 0.0.
localDeformTreshold (optional) | the deformation of the each node is tracked in range [0..1]. This treshold value can be used to clamp the bottom range, so that values in range [trhd..1] becomes [0..1], default 0.0.
exposureMod (optional) | the exposure modifier allows to take the node exposure (how much it is seen by the tracked target) into account when branching. The modifier should be in range [-1..1], -1 means to favor unseen nodes, and 1 means to favor seen, exposed node. Default 0 (no effect).
randomRotAng (optional) | each time the pattern is set, it can be optionally rotated randomly. This parameter allows to define angles (in degrees) around each axis. The rotation is performed in XYZ order.

### AddPatternNode

Adds point to the track pattern. When validating the points test is made from the start position to the end position. Start position is either the pattern origin or in case the parent is provided, the parent position. The end position is either relative offset from the start position or offset from the pattern origin, this is chosen based on the node flag. The offset is clamped to the physical world based on the test method. The points will be evaluated in the same oder they are added to the descriptor, and hte system does not try to correct the evaluation order. In case hierarchies are used (parent name is defined) it is up to the pattern creator to make sure the nodes are created in such order that the parent is added before it is referenced.

```
AI.AddPatternNode( nodeName, offsetx, offsety, offsetz, flags, [parent], [signalValue] )
```

Parameter | Description
--- | ---
nodeName | name of the new point, the point names are local to the pattern that is currently being specified.
offsetx, offsety, offsetz | The offset from the start position or from the pattern center, see AITRACKPAT_NODE_ABSOLUTE.
flags | Defines the node evaluation flags, the flags are as follows and can be combined: AITRACKPAT_NODE_START - If this flag is set, this node can be used as the first node in the pattern. There can be multiple start nodes. In that case the closest one is chosen. AITRACKPAT_NODE_ABSOLUTE - If this flag is set, the offset is interpret as an offset from the pattern center, otherwise the offset is offset from the start position. AITRACKPAT_NODE_SIGNAL - If this flag is set, a signal "OnReachedTrackPatternNode" will be send when the node is reached. AITRACKPAT_NODE_STOP - If this flag is set, the advancing will be stopped, it can be continue by calling entity:ChangeAIParameter(AIPARAM_TRACKPATTERN_ADVANCE, 1). AITRACKPAT_NODE_DIRBRANCH - The default direction at each pattern node is direction from the node position to the center of the pattern If this flag is set, the direction will be average direction to the branch nodes.
parent (optional) | If this parameter is set, the start position is considered to be the parent node position instead of the pattern center.
signalValue (optional) | If the signal flag is set, this value will be passed as signal parameter, it is accessible from the signal handler in data.iValue.

### AddPatternBranch

Creates a branch pattern at the specified node. When the entity has approached the specified node (nodeName), and it is time to choose a new point, the rules defined by this function will be used to select the new point. This function allows to associate multiple target points and an evaluation rule.

```
AI.AddPatternBranch( nodeName, method, branchNode1, branchNode2, ..., branchNodeN )
```

Parameter | Description
--- | ---
nodeName | name of the node to add the branches.
method | The method to choose the next node when the node is reached. Should be one of the following: AITRACKPAT_CHOOSE_ALWAYS - Chooses on node from the list in linear sequence. AITRACKPAT_CHOOSE_LESS_DEFORMED - Chooses the least deformed point in the list. Each node is associated with a deformation value (percentage) which describes how much it was required to move in order to stay within the physical world. These deformation values are summed down to the parent nodes so that deformation at the end of the hierarchy will be caught down the hierarchy. AITRACKPAT_CHOOSE_RANDOM - Chooses one point in the list randomly.

### EndTrackPattern

Finalizes the track pattern definition. This function should always called to finalize the pattern. Failing to do so will cause erratic behavior.

```
AI.EndTrackPattern()
```

### ChangeFormation

Changes the formation descriptor for the current formation of given entity's group (if there is a formation).

```
AI.ChangeFormation(entityId, name [,scale] )
```

**Returns:** true if the formation change was successful
Parameter | Description
--- | ---
entityId | entity id of which group the formation is changed
name | name of the formation descriptor
scale (optional) | scale factor (1 = default)

### ScaleFormation

changes the scale factor of the given entity's formation (if there is).

```
AI.ScaleFormation(entityId, scale)
```

**Returns:** true if the formation scaling was successful
Parameter | Description
--- | ---
entityId | entity id of which group the formation is scaled
scale | scale factor

### SetFormationUpdate

Changes the update flag of the given entity's formation (if there is) - the formation is no more updated if the flag is false.

```
AI.SetFormationUpdate(entityId, update)
```

**Returns:** true if the formation update setting was successful
Parameter | Description
--- | ---
entityId | entity id of which group the formation is scaled
update | update flag (true/false)

### SetFormationUpdateSight

Sets a random angle rotation for the given entity's formation sight directions.

```
AI.SetFormationUpdateSight(entityId, range, minTime, maxTime )
```

Parameter | Description
--- | ---
entityId | entity id owner of the formation
range | angle (0,360) of rotation around the default sight direction
minTime (optional) | minimum timespan for changing the direction (default = 2)
maxTime (optional) | minimum timespan for changing the direction (default = minTime)

### GetNavigationType

returns the navigation type value at the specified entity's position, given the entity navigation properties.

```
AI.GetNavigationType(entityId)
```

**Returns:** navigation type at the entity's position (NAV_TRIANGULAR,NAV_WAYPOINT_HUMAN,NAV_ROAD,NAV_VOLUME,NAV_WAYPOINT_3DSURFACE, NAV_FLIGHT,NAV_SMARTOBJECT) see IAISystem::ENavigationType definition
Parameter | Description
--- | ---
entityId | AI's entity id

### GetDistanceAlongPath

returns the distance between entity1 and entity2, along entity1's path.

```
AI.GetDistanceAlongPath(entityId1, entityid2)
```

**Returns:** distance along entity1 path; distance value would be negative if the entity2 is ahead along the path
Parameter | Description
--- | ---
entityId1 | AI's entity1 id
entityId2 | AI's entity2 id

### IntersectsForbidden

check if the line is in a Forbidden Region.

```
AI.IsPointInFlightRegion(start, end)
```

**Returns:** intersected position or end (if there is no intersection)
Parameter | Description
--- | ---
start | a vector in format {x,y,z}
end | a vector in format {x,y,z}

### IsPointInFlightRegion

Check if the point is in the Flight Region. <param name="point: a vector in format {x,y,z}

```
AI.IsPointInFlightRegion(point)
```

**Returns:** true if the point is in the Flight Region

### IsPointInWaterRegion

Check if the point is in the Flight Region. <param name="point: a vector in format {x,y,z}

```
AI.IsPointInFlightRegion(point)
```

**Returns:** water level - ground level, values greater than 0 mean there is water.

### SetFireMode

Immediately sets firemode.

```
AI.SetFireMode(entityId, mode)
```

Parameter | Description
--- | ---
entityId | AI's entity id
firemode | new firemode

### SetMemoryFireType

Sets how the puppet handles firing at its memory target.

```
AI.SetMemoryFireType(entityId, type)
```

Parameter | Description
--- | ---
entityId | AI's entity id
type | Memory fire type (see EMemoryFireType)

### GetMemoryFireType

```
AI.GetMemoryFireType(entityId)
```

**Returns:** How the puppet handles firing at its memory target.
Parameter | Description
--- | ---
entityId | AI's entity id

### ThrowGrenade

Throws a specified grenade at target type without interrupting fire mode.

```
AI.ThrowGrenade(entityId, grenadeType, regTargetType)
```

Parameter | Description
--- | ---
entityId | AI's entity id
grenadeType | Requested grenade type (see ERequestedGrenadeType)
regTargetType | Who to throw at (see AI_REG_*)

### EnableCoverFire

Enables/disables fire when the FIREMODE_COVER is selected.

```
AI.EnableCoverFire(entityId, enable)
```

Parameter | Description
--- | ---
entityId | AI's entity id
enable | boolean

### EnableFire

Enables/disables fire.

```
AI.EnableFire(entityId, enable)
```

Parameter | Description
--- | ---
entityId | AI's entity id
enable | boolean

### IsFireEnabled

Checks if AI is allowed to fire or not.

```
AI.IsFireEnabled(entityId)
```

**Returns:** True if AI is enabled to fire
Parameter | Description
--- | ---
entityId | AI's entity id

### CanFireInStance

```
AI.CanFireInStance(entityId, stance)
```

**Returns:** true if AI can fire at his target in the given stance at his current position
Parameter | Description
--- | ---
entityId | AI's entity id
stance | Stance Id (STANCE_*)

### SetUseSecondaryVehicleWeapon

Sets if the AI should use the secondary weapon when firing from a vehicle gunner seat if possible.

```
AI.SetUseSecondaryVehicleWeapon(entityId, bUseSecondary)
```

Parameter | Description
--- | ---
entityId | AI's entity id
bUseSecondary | TRUE to use the secondary weapon

### SetPFBlockerRadius

```
AI.SetPFBlockerRadius(entityId, blocker, radius)
```

Parameter | Description
--- | ---
entityId | AI's entity id

### IsAgentInTargetFOV

Checks if the entity is in the FOV of the attention target.

```
AI.IsAgentInTargetFOV(entityId, fov)
```

**Returns:** true if in the FOV of the attention target else false.
Parameter | Description
--- | ---
entityId | AI's entity id.
fov | FOV of the enemy in degrees.

### AgentLookAtPos

Makes the entityId look at certain position.

```
AI.AgentLookAtPos(entityId, pos)
```

Parameter | Description
--- | ---
entityId | AI's entity id.
fov | vec3 to look at

### ResetAgentLookAtPos

Makes the entityId resets a previous call to AgentLookAtPos().

```
AI.ResetAgentLookAtPos(entityId)
```

Parameter | Description
--- | ---
entityId | AI's entity id.

### IsAgentInAgentFOV

Check if the entity2 is within the entity FOV.

```
AI.IsAgentInAgentFOV(entityId, entityId2)
```

**Returns:** 1st value - TRUE if the agent is within the entity FOV 2nd value - TRUE if the agent is within the entity's primary FOV or FALSE if within secondary FOV
Parameter | Description
--- | ---
entityId | AI's entity who's FOV is checked
entityId2 | that's entity is looking for;)

### CreateGroupFormation

Creates a group formation with leader (or updates leader).

```
AI.CreateGroupFormation(entityId, leaderId)
```

Parameter | Description
--- | ---
entityId | AI's entity
leaderId | New leader

### SetFormationPosition

Sets the Relative position inside the formation.

```
AI.SetFormationPosition(entityId, v2RelativePosition )
```

Parameter | Description
--- | ---
entityId | AI's entity
v2RelativePosition | Table with format {x,y} storing the new relative position

### SetFormationLookingPoint

Sets the Relative looking point position inside the formation.

```
AI.SetFormationLookingPoint(entityId, v3RelativePosition )
```

Parameter | Description
--- | ---
entityId | AI's entity
v3RelativePosition | Table with format {x,y,z} storing the new relative looking point

### SetFormationAngleThreshold

Sets the Relative position inside the formation.

```
AI.SetFormationAngleThreshold(entityId, fAngleThreshold )
```

Parameter | Description
--- | ---
entityId | AI's entity
fAngleThreshold | New Leader orientation angle threshold in degrees to recal position

### GetFormationPosition

Gets the Relative position inside the formation.

```
AI.GetFormationPosition(entityId)
```

**Returns:** v3 - Table with format {x,y,z} storing the relative position
Parameter | Description
--- | ---
entityId | AI's entity

### GetFormationLookingPoint

Gets the looking point position inside the formation.

```
AI.GetFormationLookingPoint(entityId)
```

**Returns:** v3 - Table with format {x,y,z} storing the looking point position
Parameter | Description
--- | ---
entityId | AI's entity

### SetAnimationTag

```
AI.SetAnimationTag(entityId, tagName)
```

Parameter | Description
--- | ---
entityId | AI's entity
tagName | .

### ClearAnimationTag

```
AI.ClearAnimationTag(entityId, tagName)
```

Parameter | Description
--- | ---
entityId | AI's entity
tagName | .

### GetStance

Get the given entity's stance.

```
AI.GetStance(entityId)
```

**Returns:** entity stance (STANCE_*)
Parameter | Description
--- | ---
entityId | AI's entity id

### SetStance

Set the given entity's stance.

```
AI.SetStance(entityId, stance)
```

Parameter | Description
--- | ---
entityId | AI's entity id
stance | stance value (STANCE_*)

### SetMovementContext

Set the given entity's movement context.

```
AI.SetMovementContext(entityId, context)
```

Parameter | Description
--- | ---
entityId | AI's entity id
context | context value

### ClearMovementContext

Reset the given entity's movement context.

```
AI.ResetMovementContext(entityId)
```

Parameter | Description
--- | ---
entityId | AI's entity id
context | context value

### SetPostures

Set the given entity's postures.

```
AI.SetPostures(entityId, postures)
```

Parameter | Description
--- | ---
entityId | AI's entity id
postures | .

### SetPosturePriority

Set the given entity's posture priority.

```
AI.SetPosturePriority(entityId, postureName, priority)
```

### GetPosturePriority

Set the given entity's posture priority.

```
AI.GetPosturePriority(entityId, postureName)
```

### IsMoving

Returns true if the agent desires to move.

```
AI.IsMoving(entityId)
```

Parameter | Description
--- | ---
entityId | AI's entity id

### RegisterDamageRegion

Register a spherical region that causes damage (so should be avoided in pathfinding). Owner entity position is used as region center. Can be called multiple times, will just move update region position

```
AI.RegisterDamageRegion(entityId, radius)
```

Parameter | Description
--- | ---
entityId | owner entity id.
radius | If radius <= 0 then the region is disabled

### GetBiasedDirection

Get biased direction of certain point.

```
AI.GetBiasedDirection(entityId)
```

Parameter | Description
--- | ---
entityId | AI's entity

### SetAttentiontarget

Set a new attention target.

```
AI.SetAttentiontarget(entityId, targetId)
```

Parameter | Description
--- | ---
entityId | AI's entity
targetId | target's id

### FindStandbySpotInShape

```
AI.FindStandbySpotInShape(centerPos, targetPos, anchorType)
```

### FindStandbySpotInSphere

```
AI.FindStandbySpotInSphere(centerPos, targetPos, anchorType)
```

### CanMelee

returns 1 if the AI is able to do melee attack.

```
AI.CanMelee(entityId)
```

Parameter | Description
--- | ---
entityId | AI's entity id

### CheckMeleeDamage

returns 1 if the AI performing melee is actually hitting target.

```
AI.CheckMeleeDamage(entityId, targetId, radius, minheight, maxheight, angle)
```

**Returns:** (distance,angle) pair between entity and target (degrees) if melee is possible, nil otherwise
Parameter | Description
--- | ---
entityId | AI's entity id
targetId | AI's target entity id
radius | max distance in 2d to target
minheight | min distance in height
maxheight | max distance in height
angle | FOV to include target

### GetDirLabelToPoint

Returns a direction label (front=0, back=1, left=2, right_3, above=4, -1=invalid) to the specified point.

```
AI.GetDirLabelToPoint(entityId, point)
```

Parameter | Description
--- | ---
entityId | AI's entity id
point | point to evaluate.

### DebugReportHitDamage

Creates a debug report for the hit damage.

```
AI.DebugReportHitDamage(pVictimEntity, pShooterEntity)
```

Parameter | Description
--- | ---
pVictimEntity | Victim ID.
pShooterEntity | Shooter ID.

### ProcessBalancedDamage

Processes balanced damage.

```
AI.ProcessBalancedDamage(pShooterEntity, pTargetEntity, damage, damageType)
```

Parameter | Description
--- | ---
pShooterEntity | Shooter ID.
pTargetEntity | Target ID.
damage | Hit damage.
damageType | Hit damage type.

### SetRefpointToAnchor

Sets a reference point to an anchor.

```
AI.SetRefpointToAnchor(entityId, rangeMin, rangeMax, findType, findMethod)
```

Parameter | Description
--- | ---
entityId | AI's entity ID.
rangeMin | Minimum range.
rangeMax | Maximum range.
findType | Finding type.
findMethod | Finding method.

### SetRefpointToPunchableObject

Sets the reference point to the punchable object.

```
AI.SetRefpointToPunchableObject(entityId, range)
```

Parameter | Description
--- | ---
entityId | AI's entity ID.
range | Range for the punchable object.

### MeleePunchableObject

```
AI.MeleePunchableObject(entityId, objectId, origPos)
```

Parameter | Description
--- | ---
entityId | AI's entity ID.
objectId | Object ID.
origPos | Position of the melee punchable object

### IsPunchableObjectValid

Checks if a punchable object is valid.

```
AI.IsPunchableObjectValid(userId, objectId, origPos)
```

Parameter | Description
--- | ---
userId | User ID.
objectId | Object ID.
origPos | Object position in the world.

### PlayReadabilitySound

Plays readability sound on the AI agent. This call does not do any filtering like playing readability using signals.

```
AI.PlayReadabilitySound(entityId, soundName)
```

Parameter | Description
--- | ---
entityId | AI's entity id
soundName | the name of the readability sound signal to play
stopPreviousSounds (Optional) | TRUE if any currently playing readability should be stopped in favor of this one
responseDelayMin (Optional) | Minimum (or exact, if no maximum) delay for the Response readability to play
repsonseDelayMax (Optional) | Maximum delay for the Response readability to play

### PlayCommunication

Plays communication on the AI agent.

```
AI.PlayCommunication(entityId, commName, channelName[, targetId] [, targetPos])
```

Parameter | Description
--- | ---
entityId | AI's entity id
commName | The name of the communication to play
channelName | The name of the channel where the communication will play

### StopCommunication

Stops given communication.

```
AI.StopCommunication(playID)
```

Parameter | Description
--- | ---
playID | The id of the communication to stop.

### EnableWeaponAccessory

Enables or disables certain weapon accessory usage.

```
AI.EnableWeaponAccessory(entityId, accessory, state)
```

Parameter | Description
--- | ---
entityId | AI's entity id
accessory | enum of the accessory to enable (see EAIWeaponAccessories)
state | true/false to enable/disable

### RegisterInterestingEntity

Registers the entity with the interest system. Any errors go to the error log.

```
AI.RegisterInterestingEntity(entityId, baseInterest, category, aiAction)
```

**Returns:** true - if a valid update was performed nil - if not (Interest system is disabled, parameters not valid, etc)
Parameter | Description
--- | ---
entityId | AI's entity id

### UnregisterInterestingEntity

Unregisters the entity with the interest system. Any errors go to the error log.

```
AI.UnregisterInterestingEntity(entityId)
```

Parameter | Description
--- | ---
entityId | AI's entity

### RegisterInterestedActor

Registers the interested actor with the interest system. Any errors go to the error log.

```
AI.RegisterInterestedActor(entityId, fInterestFilter, fAngleInDegrees)
```

**Returns:** true - if a valid update was performed nil - if not (Interest system is disabled, parameters not valid, etc)
Parameter | Description
--- | ---
entityId | AI's entity

### UnregisterInterestedActor

Unregisters the entity with the interest system. Any errors go to the error log.

```
AI.UnregisterInterestedActor(entityId)
```

Parameter | Description
--- | ---
entityId | AI's entity id

### IsCoverCompromised

```
AI.IsCoverCompromised(entityId)
```

**Returns:** true - Cover is not good anymore nil - if not
Parameter | Description
--- | ---
entityId | AI's entity

### SetCoverCompromised

```
AI.SetCoverCompromised(entityId)
```

Parameter | Description
--- | ---
entityId | AI's entity

### IsTakingCover

```
AI.IsTakingCover(entityId, [distanceThreshold])
```

**Returns:** true - Agent is either in cover or running to cover nil - if not
Parameter | Description
--- | ---
entityId | AI's entity
distanceThreshold | (optional) distance over which if the agent is running to cover, he won't be considered as taking cover

### IsMovingInCover

```
AI.IsMovingInCover(entityId)
```

**Returns:** true - Agent is moving in cover nil - if not
Parameter | Description
--- | ---
entityId | AI's entity

### IsMovingToCover

true - Agent is running to cover nil - if not

```
AI.IsMovingToCover(entityId)
```

Parameter | Description
--- | ---
entityId | AI's entity

### IsInCover

true - if AI is using cover nil - if not

```
AI.IsInCover(entityId)
```

### SetInCover

```
AI.SetInCover(entityId, inCover)
```

Parameter | Description
--- | ---
entityId | AI's entity
inCover | if the AI should be set to be in cover or not

### IsOutOfAmmo

```
AI.IsOutOfAmmo(entityId)
```

**Returns:** true - Entity is out of ammo nil - if not
Parameter | Description
--- | ---
entityId | AI's entity

### IsLowOnAmmo

```
AI.IsLowOnAmmo(entityId)
```

Parameter | Description
--- | ---
entityId | AI's entity
threshold | the ammo percentage threshold

### ResetAgentState

Resets a particular aspect of the agent's state, such as "lean". Intended to keep these hacky concepts together.

```
AI.ResetAgentState(entityId,stateLabel)
```

**Returns:** nil
Parameter | Description
--- | ---
entityId | AI's entity
stateLabel | string describing the state that must be reset to default

### RegisterTacticalPointQuery

Get a query ID for the given tactical point query.

```
AI.RegisterTacticalPointQuery( querySpecTable )
```

**Returns:** > 0 - If the query was parsed successfully 0 - Otherwise
Parameter | Description
--- | ---
querySpecTable | table specifying the query (a mini-language - see Tactical Point System docs elsewhere)

### GetTacticalPoints

Get a point matching a description, related to an entity. Format of a point is: { x,y,z }.

```
AI.GetTacticalPoints( entityId, tacPointSpec, point )
```

**Returns:** true - If a valid point was found false - Otherwise
Parameter | Description
--- | ---
entityId | AI's entity
tacPointSpec | table specifying the points required
point | a table put coordinates of point found

### DestroyAllTPSQueries

Destroys all the tactical point system queries.

```
AI2.DestroyAllTPSQueries()
```

### GetObjectBlackBoard

retrieves given object's black board (a Lua table).

```
AI.GetObjectBlackBoard( entity )
```

**Returns:** black board - if there was one nil - Otherwise
Parameter | Description
--- | ---
entityId or entityName | some kind of AI entity's identifier

### GetBehaviorBlackBoard

retrieves given AIActor current behaviour's black board (a Lua table).

```
AI.GetBehaviorBlackBoard( entity )
```

**Returns:** black board - if there was one nil - Otherwise
Parameter | Description
--- | ---
entityId or entityName | some kind of AIActors's identifier

### SetBehaviorVariable

Sets a behaviour variable for the specified actor.

```
AI.SetBehaviorVariable( entity, variableName, value )
```

### GetBehaviorVariable

Returns a behavior variable for the specified actor.

```
AI.GetBehaviorVariable( entity, variableName, value )
```

### ParseTables

```
AI.ParseTables( firstTable,parseMovementAbility,pH,aiParams,updateAlways )
```

Parameter | Description
--- | ---
firstTable | Properties table.
parseMovementAbility | True to parse movement ability, false otherwise.
aiParams | AI parameters.
updateAlways | .

### GoTo

This function is intended to allow AI Actor (the entity) go to the specified destination.

```
AI.GoTo(entityId, vDestination)
```

Parameter | Description
--- | ---
entityId | AI's entity
vDestination | .

### SetSpeed

This function allows the user to override the entity's current speed (urgency).

```
AI.SetSpeed(entityId, urgency)
```

Parameter | Description
--- | ---
entityId | AI's entity
urgency | float value specifying the movement urgency (see AgentMovementSpeeds::EAgentMovementUrgency)

### SetEntitySpeedRange

```
AI.SetEntitySpeedRange( userEntityId, urgency, defaultSpeed, minSpeed, maxSpeed, stance = all)
```

**Returns:** true if the operation was successful and false otherwise
Parameter | Description
--- | ---
usedEntityId | entity id of the user for which its last used smart object is needed
urgency | integer value specifying the movement urgency (see AgentMovementSpeeds::EAgentMovementUrgency)
defaultSpeed | floating point value specifying the default speed
minSpeed | floating point value specifying the min speed

### SetAlarmed

This function sets the entity to be "perception alarmed".

```
AI.SetAlarmed( entityId )
```

### LoadBehaviors

```
AI.LoadBehaviors( folderName, extension, globalEnv)
```

### IsLowHealthPauseActive

```
AI.IsLowHealthPauseActive( entityID )
```

### GetPreviousBehaviorName

```
AI.GetPreviousBehaviorName( entityID )
```

### SetContinuousMotion

```
AI.SetContinuousMotion( entityID, continuousMotion )
```

### GetPeakThreatLevel

```
AI.GetPeakThreatLevel( entityID )
```

### GetPeakThreatType

```
AI.GetPeakThreatType( entityID )
```

### GetPreviousPeakThreatLevel

```
AI.GetPreviousPeakThreatLevel( entityID )
```

### GetPreviousPeakThreatType

```
AI.GetPreviousPeakThreatType( entityID )
```

### CheckForFriendlyAgentsAroundPoint

```
AI.CheckForFriendlyAgentsAroundPoint( entityID, point, radius)
```

### EnableUpdateLookTarget

```
AI.EnableUpdateLookTarget(entityID, bEnable)
```

### SetBehaviorTreeEvaluationEnabled

```
AI.SetBehaviorTreeEvaluationEnabled(entityID, enable)
```

### UpdateGlobalPerceptionScale

```
AI.UpdateGlobalPerceptionScale(visualScale, audioScale, [filterType], [faction])
```

### QueueBubbleMessage

```
AI.QueueBubbleMessage(entityID, message, flags)
```

### SequenceBehaviorReady

```
AI.SequenceBehaviorReady(entityId)
```

### SequenceInterruptibleBehaviorLeft

```
AI.SequenceInterruptibleBehaviorLeft(entityId)
```

### SequenceNonInterruptibleBehaviorLeft

```
AI.SequenceNonInterruptibleBehaviorLeft(entityId)
```

### SetCollisionAvoidanceRadiusIncrement

```
AI.SetCollisionAvoidanceRadiusIncrement(entityId, radius)
```

### RequestToStopMovement

```
AI.RequestToStopMovement(entityId)
```

### GetDistanceToClosestGroupMember

```
AI.GetDistanceToClosestGroupMember(entityId)
```

### IsAimReady

```
AI.IsAimReady(entityIdHandle)
```

### AllowLowerBodyToTurn

```
AI.LockBodyTurn(entityID, bAllowLowerBodyToTurn)
```

Parameter | Description
--- | ---
entityId | entity id of the agent you want to set the look style to
bAllowLowerBodyToTurn | true if you want to allow the turning movement of the body, false otherwise

### GetGroupScopeUserCount

```
AI.GetGroupScopeUserCount(entityID, bAllowLowerBodyToTurn)
```

**Returns:** The amount of actors inside the group scope (>= 0) or nil if an error occurred.
Parameter | Description
--- | ---
entityId | entity id of the agent you want to access the group scope for.
groupScopeName | the group scope name.
