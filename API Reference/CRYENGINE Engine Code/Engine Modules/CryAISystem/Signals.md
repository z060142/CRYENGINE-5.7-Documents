# Signals

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/23306492
- Page ID: 23306492
- Breadcrumb: CRYENGINE Engine Code > Engine Modules > CryAISystem > Signals
- Parent: CryAISystem

## Child Pages

- [Signal Reference](Signals/Signal Reference.md)

## Content

##
Overview

CryAISystem provides a powerful, fully customizable tool to make AI entities communicate with each other, which is the Signal system. A signal is an event that can be sent by an agent to another single agent (including itself) or to a sub-set of all the agents currently active in the game. We have already met the concept of signal in the Goalpipe section (see the
**
signal
**
 goal description for details). In this section, we'll describe:

-
How to send signals from an agent's behavior to other agents.

-
How to define the sub-set of the agents which will receive the sent signal.

-
How the recipient agent can react to the sent signal.

##
Sending Signals

The method to send a signal is the following:

```

`
AI:Signal(Signal_filter, signal_type, *MySignalName*, sender_entity_id);

`

```

*
Where...
*

-
**
Signal_filter
**
 defines the subset of agents in the game which will receive the signal. It can be chosen among a fixed set of symbols which have the prefix SIGNALFILTER_. The complete list of available signal filters is showed below.

signal_types

 |
Description

 |

**
1
**

 |
The entity receiving the signal will process it only if it's enabled and it's not set to ignorant (see AI:MakePuppetIgnorant for details).

 |

**
0
**

 |
The entity receiving the signal will process it if it's not set to ignorant.

 |

**
-1
**

 |
The entity receiving the signal will process it unconditionally.

 |

-
**
MySignalName:
**
 the actual identifier of the signal. It can be any non-empty string; for the signal recipient, it must exist a function with the same name either in its current behavior, its default behavior or in the DEFAULT.lua script file in order to react to the received signal.

-
**
entity_id:
**
 the entity id of the signal's recipient. Usually you may want to put entity.id (or self.id if it's called from the entity and not from its behavior), to send the signal to the sender itself, but you can also put any other id there to send the signal to another entity.

##
Defining Who Will Receive the Signal

With the signal filter, we can define the subset of agents which will receive the signal.

The signal filter parameter in the AI:Signal (...) function call can be one of the following:

Signal filter

 |
The signal is sent to...

 |

**
0
**

 |
To the entity specified with the entity_id parameter (usually the sender itself but not necessarily).

 |

**
SIGNALFILTER_LASTOP
**

 |
The entity's last operation target (if it has one).

 |

**
SIGNALFILTER_TARGET
**

 |
The current entity's attention target.

 |

**
SIGNALFILTER_GROUPONLY
**

 |
All the entities in the sender's group, i.e. the entities with its same group id, in the sender's communication range.

 |

**
SIGNALFILTER_SUPERGROUP
**

 |
All the entities in the sender's group, i.e. the entities with its same group id, in the whole level.

 |

**
SIGNALFILTER_SPECIESONLY
**

 |
All the entities of the same sender's species, in the sender's communication range.

 |

**
SIGNALFILTER_SUPERSPECIES
**

 |
All the entities of the same sender's species, in the whole level.

 |

**
SIGNALFILTER_HALFOFGROUP
**

 |
Half the entities of the sender's group (there's no way to specify which entities).

 |

**
SIGNALFILTER_NEARESTGROUP
**

 |
The nearest entity to the sender in its group.

 |

**
SIGNALFILTER_NEARESTINCOMM
**

 |
The nearest entity to the sender in its group, if it's in its communication range.

 |

**
SIGNALFILTER_ANYONEINCOMM
**

 |
All the entities in the sender's communication range.

 |

**
SIGNALID_READIBILITY
**

 |
This is a special kind of signal which is used to make the entity recipient perform a readability event (sound/animation).

 |

##
Receiving the Signal

The action to be performed once a signal is received is defined in a function like this:

```

`
MySignalName = function(self, entity, sender)
...
end

where
self: the entity's behavior
entity: the entity itself
sender: the signal's sender

`

```

This function is actually a callback which, exactly like the system events, can be defined in the recipient entity's current behavior, the default idle behavior (if it's not present in current behavior) or in the
`
Scripts/AI/Behaviors/Default.lua
`
 script file (if not present in the default idle behavior).

As for system events, a signal can be used also to make a character change its behavior; if we add a line like the following in a character file:

```

`
Behaviour1 = {
  OnEnemySeen   = *Behaviour1*,
  OnEnemyMemory = *Behaviour2*,
  …
  MySignalName  = *MyNewBehaviour*,
}

`

```

This means that if the character is currently in Behaviour1, and receives the signal MySignalName, after having executed the callback function above it will then switch its behavior to MyNewBehaviour.

##
Example

A typical example is when a player's enemy spots the player: its OnEnemySeen system event is called, and let's suppose he wants to inform his mates (The guys with his same group id). In his default idle behavior (i.e. CoverAttack.lua if the character is Cover), we modify its OnEnemySeen event like this:

```

`
OnEnemySeen = function( self, entity, fDistance )
  -- called when the enemy sees a living enemy

  AI:Signal(SIGNALFILTER_GROUPONLY, 1, "ENEMY_SPOTTED",entity.id);
end,

`

```

Here we have defined a new signal called ENEMY_SPOTTED.

The next step is to define the callback function. Let's assume the other members in the group have the same character, we then add the callback function to the same idle behavior in which we have just modified OnEnemySeen.

```

`
ENEMY_SPOTTED = function (self, entity, sender)
  entity:Readibility("FIRST_HOSTILE_CONTACT");
  entity:InsertSubpipe(0, "DRAW_GUN");
End,

`

```

This will make the guys (including the signal sender itself, who has the same behavior) change their animation and producing some kind of
**
alert
**
 sound (readability), and then draw their gun. Notice that by modifying its idle behavior, we create a default callback which will be executed for any behavior the character is in. Later on, we may want to override this callback in other behaviors. For example, if we wanted the character to react differently whether it's in idle or attack behavior, we'll add the following callback function in the CoverAttack.lua file:

```

`
ENEMY_SPOTTED = function (self, entity, sender)
  entity:SelectPipe(0, "cover_pindown");
End,

`

```

Where "cover_pindown" is a goalpipe that makes the guy hide behind the nearest cover place to the target.

We can extend this to other characters: if there are group members with different characters (i.e. Scout, Rear etc) and we want them to react as well, we must add the ENEMY_SPOTTED callback also to their idle/attack behavior.

Finally, we want the guys to switch their behavior from idle to attack if they see an enemy. We'll then add the following line to the character (
`
Scripts/AI/Characters/Personalities/Cover.lua
`
 in the example):

```

`
CoverIdle = {
  …
  ENEMY_SPOTTED = *CoverAttack*,
},

`

```

##
Behavior Inheritance

If specific signals are to be used in more than one behavior, there is an inheritance mechanism. Behavior classes can either directly inherit a more general implementation by keyword
*
Base = [CRYENGINE:ParentBehaviorName]
*
 or indirectly, as a character's Idle behavior as well as the default behavior (defined in file DEFAULT.lua) are considered as fallback behaviors if a signal is not implemented in the current behavior.
