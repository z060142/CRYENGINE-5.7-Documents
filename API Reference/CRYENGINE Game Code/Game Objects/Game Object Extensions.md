# Game Object Extensions

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/23306554
- Page ID: 23306554
- Breadcrumb: CRYENGINE Game Code > Game Objects > Game Object Extensions
- Parent: Game Objects

## Content

##
Implementing a New Game Object Extension in C++

##
Using the Helper Template

The CGameObjectExtensionHelper template can be used to simplify the implementation of a GameObjectExtension. This helper template will handle the RMI functionality of the extension interface.

This template is included inside of the header file IGameObject.h. To use the helper class, the declaration needs to follow this example:

```

`
class CNewGameObjectExt
 : public CGameObjectExtensionHelper <CNewGameObjectExt, IGameObjectExtension>
{
  //...
}

`

```

A third CGameObjectExtensionHelper parameter is available, and denotes the maximum number of
**

[RMIs](../../CRYENGINE%20Engine%20Code/Engine%20Modules/CryNetwork/RMI%20Functions.md)
**
supported by this game object.

The important functions to implement the most basic Game Objectextension are the following:

**
Function
**

 |
**
Description
**

 |

IGameObjectExtension::Init()

 |
The Init function should set the member values and validate with the return value if the initialization is successful. If needed, resources should be allocated during the execution of the Init.

 |

IGameObjectExtension::PostInit()

 |
The ideal location to set the initial update slot state (more information can be found in IGameObject::EnableUpdateSlot()).

 |

IGameObjectExtension::Release()

 |
This function should release any resource previously allocated by the extension. Additionally, the Release function need to free the object instance.

 |

IGameObjectExtension::Serialize()

 |
Any critical state variables needs to be serialized, both for disc serialization (i.e.: save games) or network serialization.

 |

IGameObjectExtension::Update()

 |
Any frame rate dependent updates should be implemented as part of this function.

 |

##
Registering the New Extension

A new GameObjectExtension should register itself in IGameFramework before it's possible to spawn new instances of its class.

The REGISTER_FACTORY macro defined inside IGameFramework.h is used to simplify the registration.

```

`
IGameFramework *pFramework = gEnv->pGame->GetIGameFramework();
REGISTER_FACTORY(pFramework, "NewGameObject", CNewGameObjectExt, false);

`

```

The GameDLL initialization is the perfect location for the GameObjectExtension registrations.

##
GameObject Update Policies

CGameObject is the responsible class for enabling or disabling an entity that is executing game code. Since there are many disparate systems that may need to be updated at different times, the class employs a voting mechanism to arbitrate between things. Effectively if anything says it needs an update, the entity is activated, and those parts of the system that need it receive a tick.

For the game code, there are four update slots for each Game Object extension, and each can be governed by a built in rule. This rule allows the Game Object itself to decide activation state without having to call into external code (in an effort to avoid memory thrashing). The rules are detailed in EUpdateEnableCondition. Part of these rules is whether the update condition depends on the AI state or not – usually it does, but for some update slots we want that it gets updated separately (for example the GameRules).

Conditions in EUpdateEnableCondition

 |

eUEC_Never

 |

eUEC_Always

 |

eUEC_Visible

 |

eUEC_InRange

 |

eUEC_VisibleAndInRange

 |

eUEC_VisibleOrInRange

 |

eUEC_VisibleOrInRangeIgnoreAI

 |

eUEC_VisibleIgnoreAI

 |

eUEC_WithoutAI

 |

To enable or disable AI, we have a separate rule that gets configured on the CGameObject. The EGameObjectAIActivationMode is available and set from the AIProxy. It has three values (Never, Always, and VisibleOrInRange – the default). Game Object uses this value to decide whether the AI should be activated or not. It is important to note that whenever the entity is activated the AI is informed however, so that it can maintain state synchronization with the entity.

Finally, there's a third configurable rule for when the pre-physics update event should be sent to an entity, EPrePhysicsUpdate. We use this pre-physics call to perform some work in AnimatedCharacter.

To see how this system is working, you can always use g_showUpdateState 2. It's showing all of the details about why a particular entity has been enabled.

 In order to do the visibility and range checks to evaluate the update rules, the following is done:

-
For Visibility: when an entity is invisible, it registers for an event from the Renderer that it has become visible again, at which point it 'becomes visible' and update rules are re-evaluated. When it is visible, in order to avoid too much entity system event spam, the entity only periodically registers for this event, so an entity may take 5 or 10 seconds to become invisible once you look away.

-
For Distance checking: there is a moderately large proximity trigger located around the player. This trigger is snapped to two meter grid coordinates and we try to move it around only rarely (once every second currently) in order to prevent too much thrashing in the proximity trigger system. As entities move in and out of this region they are updated as being 'faraway' or 'close.' The proximity trigger is needed in order to activate entities immediately when they come into range.
There is a small table-driven state machine driving this process in
*
CGameObject::UpdateTransitions
*
.
