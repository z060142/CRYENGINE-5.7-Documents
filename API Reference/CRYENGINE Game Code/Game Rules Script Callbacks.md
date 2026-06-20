# Game Rules Script Callbacks

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/23306635
- Page ID: 23306635
- Breadcrumb: CRYENGINE Game Code > Game Rules Script Callbacks
- Parent: CRYENGINE Game Code

## Content

##
File location:

##
Callback Functions

-
[#OnAddTaggedEntity](Game%20Rules%20Script%20Callbacks.md#GameRulesScriptCallbacks-OnAddTaggedEntity)

-
[#OnClientConnect](Game%20Rules%20Script%20Callbacks.md#GameRulesScriptCallbacks-OnClientConnect)

-
[#OnClientDisconnect](Game%20Rules%20Script%20Callbacks.md#GameRulesScriptCallbacks-OnClientDisconnect)

-
[#OnClientEnteredGame](Game%20Rules%20Script%20Callbacks.md#GameRulesScriptCallbacks-OnClientEnteredGame)

-
[#OnDisconnect](Game%20Rules%20Script%20Callbacks.md#GameRulesScriptCallbacks-OnDisconnect)

-
[#OnChangeSpectatorMode](Game%20Rules%20Script%20Callbacks.md#GameRulesScriptCallbacks-OnChangeSpectatorMode)

-
[#OnChangeTeam](Game%20Rules%20Script%20Callbacks.md#GameRulesScriptCallbacks-OnChangeTeam)

-
[#OnExplosion](Game%20Rules%20Script%20Callbacks.md#GameRulesScriptCallbacks-OnExplosion)

-
[#OnHit](Game%20Rules%20Script%20Callbacks.md#GameRulesScriptCallbacks-OnHit)

-
[#OnItemDropped](Game%20Rules%20Script%20Callbacks.md#GameRulesScriptCallbacks-OnItemDropped)

-
[#OnItemPickedUp](Game%20Rules%20Script%20Callbacks.md#GameRulesScriptCallbacks-OnItemPickedUp)

-
[#OnKill](Game%20Rules%20Script%20Callbacks.md#GameRulesScriptCallbacks-OnKill)

-
[#OnRevive](Game%20Rules%20Script%20Callbacks.md#GameRulesScriptCallbacks-OnRevive)

-
[#OnReviveInVehicle](Game%20Rules%20Script%20Callbacks.md#GameRulesScriptCallbacks-OnReviveInVehicle)

-
[#OnSetTeam](Game%20Rules%20Script%20Callbacks.md#GameRulesScriptCallbacks-OnSetTeam)

-
[#OnVehicleDestroyed](Game%20Rules%20Script%20Callbacks.md#GameRulesScriptCallbacks-OnVehicleDestroyed)

##
OnAddTaggedEntity( shooterId, targetId )

Called whenever a player gets added as a tagged player on the minimap.

**
Parameters
**

 |
**
Description
**

 |

shooterId

 |
player entity identifier who tagged the target player

 |

targetId

 |
tagged player entity identifier

 |

Hint
Is only called on the Server.

##
OnClientConnect( channelId )

Called whenever a player connects.

**
Parameters
**

 |
**
Description
**

 |

channelId

 |
channel identifier

 |

Hint
Is only called on the Server.

##
OnClientDisconnect( channelId )

Called whenever a player disconnects.

**
Parameters
**

 |
**
Description
**

 |

channelId

 |
channel identifier

 |

Hint
Is only called on the Server.

##
OnClientEnteredGame( channelId, playerScriptTable, bReset, bLoadingSaveGame )

Called whenever a player enters the game and is part of the game world.

**
Parameters
**

 |
**
Description
**

 |

channelId

 |
channel identifier of the player

 |

playerScriptTable

 |
the player scripttable

 |

bReset

 |
**
true
**
 if it was a channel from the reset list

 |

bLoadingSaveGame

 |
specifies whether it was called during savegame loading

 |

Hint
Is only called on the Server.

##
OnDisconnect( cause, description )

Called when the player disconnects and only on this client.

**
Parameters
**

 |
**
Description
**

 |

cause

 |
integer based disconnection cause (see:
**
EDisconnectionCause
**
 /
*
Code/CryEngine/CryCommon/INetwork.h
*
)

 |

description

 |
human readable disconnection cause description (e.g:
**
User left the game
**
)

 |

Hint
Is only called on the Client.

##
OnChangeSpectatorMode( entityId , mode, targetId, resetAll )

Called whenever a player changed the spector mode.

**
Parameters
**

 |
**
Description
**

 |

entityId

 |
entity identifier of the player who changed the spectator mode

 |

mode

 |
spectator mode (fixed=
**
1
**
 / free=
**
2
**
 / follow=
**
3
**
)

 |

targetId

 |
possible target entity to spectate

 |

resetAll

 |
used to reset player related things like the inventory

 |

Hint
Is only called on the Server.

##
OnChangeTeam( entityId, teamId )

Called whenever a player switched the team.

**
Parameters
**

 |
**
Description
**

 |

entityId

 |
entity identifier of the player who switched the team

 |

teamId

 |
new team identifier

 |

Hint
Is only called on the Server.

##
OnExplosion( explosionInfoTable )

Called whenever an explosion was simulated.

**
Parameters
**

 |
**
Description
**

 |

pos

 |
world position of the explosion

 |

dir

 |
explosion direction

 |

shooterId

 |
...

 |

weaponId

 |
...

 |

shooter

 |
...

 |

weapon

 |
...

 |

materialId

 |
...

 |

damage

 |
...

 |

min_radius

 |
...

 |

radius

 |
...

 |

pressure

 |
...

 |

hole_size

 |
...

 |

effect

 |
...

 |

effectScale

 |
...

 |

effectClass

 |
...

 |

typeId

 |
...

 |

type

 |
...

 |

angle

 |
...

 |

impact

 |
...

 |

impact_velocity

 |
...

 |

impact_normal

 |
...

 |

impact_targetId

 |
...

 |

shakeMinR

 |
...

 |

shakeMaxR

 |
...

 |

shakeScale

 |
...

 |

shakeRnd

 |
...

 |

impact

 |
...

 |

impact_velocity

 |
...

 |

impact_normal

 |
...

 |

impact_targetId

 |
...

 |

AffectedEntities

 |
affected entities table

 |

AffectedEntitiesObstruction

 |
affected entities obstruction table

 |

Hint
Is called on the Server and the Client.

##
OnHit( shooterId, targetId )

Called whenever an entity gets added as a tagged entity on the minimap.

**
Parameters
**

 |
**
Description
**

 |

shooterId

 |
entity which tagged the target

 |

targetId

 |
tagged entity

 |

Hint
Is only called on the Server.

##
OnItemDropped( shooterId, targetId )

Called whenever an entity gets added as a tagged entity on the minimap.

**
Parameters
**

 |
**
Description
**

 |

shooterId

 |
entity which tagged the target

 |

targetId

 |
tagged entity

 |

Hint
Is only called on the Server.

##
OnItemPickedUp( shooterId, targetId )

Called whenever an entity gets added as a tagged entity on the minimap.

**
Parameters
**

 |
**
Description
**

 |

shooterId

 |
entity which tagged the target

 |

targetId

 |
tagged entity

 |

Hint
Is only called on the Server.

##
OnKill( shooterId, targetId )

Called whenever an entity gets added as a tagged entity on the minimap.

**
Parameters
**

 |
**
Description
**

 |

shooterId

 |
entity which tagged the target

 |

targetId

 |
tagged entity

 |

Hint
Is only called on the Server.

##
OnRevive( shooterId, targetId )

Called whenever an entity gets added as a tagged entity on the minimap.

**
Parameters
**

 |
**
Description
**

 |

shooterId

 |
entity which tagged the target

 |

targetId

 |
tagged entity

 |

Hint
Is only called on the Server.

##
OnReviveInVehicle( shooterId, targetId )

Called whenever an entity gets added as a tagged entity on the minimap.

**
Parameters
**

 |
**
Description
**

 |

shooterId

 |
entity which tagged the target

 |

targetId

 |
tagged entity

 |

Hint
Is only called on the Server.

##
OnSetTeam( shooterId, targetId )

Called whenever an entity gets added as a tagged entity on the minimap.

**
Parameters
**

 |
**
Description
**

 |

shooterId

 |
entity which tagged the target

 |

targetId

 |
tagged entity

 |

Hint
Is only called on the Server.

##
OnVehicleDestroyed( shooterId, targetId )

Called whenever an entity gets added as a tagged entity on the minimap.

**
Parameters
**

 |
**
Description
**

 |

shooterId

 |
entity which tagged the target

 |

targetId

 |
tagged entity

 |

Hint
Is only called on the Server.
