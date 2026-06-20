# Triggers Entities

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/29796947
- Page ID: 29796947
- Breadcrumb: Editor Tools > Level Editor Tab > Create Object > Legacy Entities > Triggers Entities
- Parent: Legacy Entities

## Content

##
Overview

Trigger entities are used to activate events in a level. The triggers entities can be found in
**
Create Object
**
→
**
 Legacy Entities → Triggers
**
.

##
Area Trigger

The
**
Area Trigger
**
 is activated when the player enters an area.

First, create an area shape. Then, select the area trigger entity with the PICK function.

**
Property
**

 |
**
Description
**

 |

**
Enabled
**

 |
Turns the entity on or off.

 |

**
FactionFilter
**

 |
See
[Common Entity Parameters](BEGIN%20--%20Common%20Entity%20Parameters.md)
.

 |

**
InVehicleOnly
**

 |
Sets up that the trigger can only be activated when player is inside vehicle.

 |

**
OnlyLocalPlayer
**

 |
Sets the trigger to be only triggerable by the local player entity.

 |

**
OnlyPlayers
**

 |
Sets the trigger to be only triggerable by players entities.

 |

**
PlaySequence
**

 |
Plays the
[Track View](../../../Track%20View.md)
 sequence with the name specified in here.

 |

**
ScriptCommand
**

 |
Executes a script command when the trigger has been activated.

 |

**
TriggerOnce
**

 |
Disables the trigger after it has been triggered once.

 |

**
Networked
**

 |
See
[Common Entity Parameters](BEGIN%20--%20Common%20Entity%20Parameters.md)
.

 |

**
PerPlayer
**

 |

 |

##
Cinematic Trigger

The
**
Cinematic Trigger
**
 is used if the player looks at a certain spot.

**
Property
**

 |
**
Description
**

 |

**
CheckTimer
**

 |
If the player looks the trigger for the amount of time specified in this field (specified in seconds) then the trigger is activated.

 |

**
Delay
**

 |

 |

**
DimX
**

 |
Specifies how big the trigger is (x-axis).

 |

**
DimY
**

 |
Specifies how big the trigger is (y-axis).

 |

**
DimZ
**

 |
Specifies how big the trigger is (z-axis).

 |

**
Enabled
**

 |

 |

**
InVehicleOnly
**

 |
Sets up that the trigger can only be activated when player is inside vehicle.

 |

**
MaxDistance
**

 |
Sets up the maximum distance the trigger can be away in order for it to get triggered when the player looks at it.

 |

**
MinDistance
**

 |
Sets up the minimum distance the trigger must be away in order for it to get triggered when the player looks at it.

 |

**
MinVisibleTime
**

 |
If the player looks the trigger for the amount of time specified in this field (specified in seconds) then the trigger is activated.

 |

**
ScriptCommand
**

 |
Executes a script command when the trigger has been activated.

 |

**
Sequence
**

 |
Plays the
[Track View](../../../Track%20View.md)
 sequence with the name specified in here.

 |

**
TriggerOnce
**

 |
Disables the trigger after it has been triggered once.

 |

**
ZoomMinimum
**

 |
Sets up the zoom level at which the player must be in order to enable the trigger.

 |

**
MinPlayers
**

 |

 |

**
Networked
**

 |
See
[Common Entity Parameters](BEGIN%20--%20Common%20Entity%20Parameters.md)
.

 |

**
PerPlayer
**

 |

 |

##
Proximity Trigger

The
**
Proximitry Trigger
**
 is used when certain entities enter a box.

**
Property
**

 |
**
Description
**

 |

**
ActivateWithUseButton
**

 |
Specifies if the trigger is activated by pressing use.

 |

**
DimX
**

 |
Specifies how big the trigger is (x-axis).

 |

**
DimY
**

 |
Specifies how big the trigger is (y-axis).

 |

**
DimZ
**

 |
Specifies how big the trigger is (z-axis).

 |

**
Enabled
**

 |
Specifies if the trigger can be activated or not.

 |

**
EnterDelay
**

 |
Sets up a delay (in seconds) before the enter node of the trigger is activated.

 |

**
ExitDelay
**

 |
Sets up a delay (in seconds) before the exit node of the trigger is activated.

 |

**
FactionFilter
**

 |
See
[Common Entity Parameters](BEGIN%20--%20Common%20Entity%20Parameters.md)
.

 |

**
InVehicleOnly
**

 |
Sets up that the trigger can only be activated when player is inside vehicle.

 |

**
OnlyAI
**

 |
Sets the trigger to be only triggerable by AI entities.

 |

**
OnlyMyPlayer
**

 |
Sets the trigger to be only triggerable by the local player.

 |

**
OnlyOneEntity
**

 |
Sets the trigger to be only triggerable by one entity.

First one who triggers it has to leave it in order to be triggerable again.

 |

**
OnlyPlayer
**

 |
Sets the trigger to be only triggerable by player entities.

 |

**
OnlySelectedEntity
**

 |
Sets the trigger to be only triggerable by the entity with the name specified in this field.

Wildcard matches can be used such as RigidbodyEx
**
*
**
, will allow all entities with that name, regardless of number suffix, etc.

 |

**
OnlySpecialAI
**

 |
Sets the trigger to be only triggerable by the special AI entities.

 |

**
PlaySequence
**

 |
Plays the
[Track View](../../../Track%20View.md)
 sequence with the name specified in here.

 |

**
RemoveOnTrigger
**

 |
Similar to the deprecated "KillOnTrigger" param, if true, any entities (except player) which trigger this will be removed.

 |

**
ScriptCommand
**

 |
Executes a script command when the trigger has been activated

 |

**
TriggerOnce
**

 |
Disables the trigger after it has been triggered once.

 |

**
UsableMessage
**

 |
See
[Common Entity Parameters](BEGIN%20--%20Common%20Entity%20Parameters.md)
.

 |

**
Networked
**

 |
See
[Common Entity Parameters](BEGIN%20--%20Common%20Entity%20Parameters.md)
.

 |

**
PerPlayer
**

 |

 |

[Area Trigger](#area-trigger)
[Cinematic Trigger](#cinematic-trigger)
[Proximity Trigger](#proximity-trigger)
