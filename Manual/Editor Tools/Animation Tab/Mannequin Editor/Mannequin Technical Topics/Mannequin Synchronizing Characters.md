# Mannequin Synchronizing Characters

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/23308469
- Page ID: 23308469
- Breadcrumb: Editor Tools > Animation Tab > Mannequin Editor > Mannequin Technical Topics > Mannequin Synchronizing Characters
- Parent: Mannequin Technical Topics

## Content

##
Overview

Synchronizing multiple animated characters is a pretty common task that Mannequin can help you with. Some practical examples could be:

-
Animating a weapon in sync with a character's body when reloading or firing.

-
Synchronized actions across multiple characters, such as stealth kills or execution moves.
This can easily be achieved with Mannequin through the use of
[Scope Contexts](../Mannequin%20Concepts/Mannequin%20Scopes/Mannequin%20Scope%20Contexts.md)
 and the concept of enslavement. We're here going to explain here how to synchronize simple characters, as well as more complex ones, with their own
[Mannequin ActionController](Mannequin%20ActionController.md)
.

##
Setting up the scopes and scope contexts

The first step required to synchronize a secondary character with a primary one is to add an extra
[scope](../Mannequin%20Concepts/Mannequin%20Scopes.md)
 and
[scope context](../Mannequin%20Concepts/Mannequin%20Scopes/Mannequin%20Scope%20Contexts.md)
 in the host's
[Controller Definition File (xxxControllerDefs.xml)](../Mannequin%20Files/Controller%20Definition%20File%20(xxxControllerDefs.xml).md)
. We will then attach the secondary character to this newly created scope context. Here is an example from playerControllerDefs in the SDK sample game:

```

`
<ControllerDef>
 ...
 <ScopeDefs>
  <FullBody1P layer="0" numLayers="3" context="Char1P"/>
  ...
  <FullBody3P layer="0" numLayers="3" context="Char3P"/>
  ...
  <Weapon layer="0" numLayers="3" context="Weapon"/>
  ...
  <AttachmentTop layer="0" numLayers="3" context="attachment_top"/>
  <AttachmentBottom layer="0" numLayers="3" context="attachment_bottom"/>
  <SlaveChar layer="0" numLayers="3" context="SlaveChar" Tags="slave"/>
  <SlaveObject layer="0" numLayers="3" context="SlaveObject" Tags="slave"/>
 </ScopeDefs>
</ControllerDef>
`

```

This example shows 7 scopes, using 7 different scope contexts:

Scope
 |
Scope Context
 |
Scope Tags
 |
Layers
 |

FullBody1P
 |
Char1P
 |

 |
0, 1, 2
 |

FullBody3P
 |
Char3P
 |

 |
0, 1, 2
 |

Weapon
 |
Weapon
 |

 |
0, 1, 2
 |

AttachmentTop
 |
attachment_top
 |

 |
0, 1, 2
 |

AttachmentBottom
 |
attachment_bottom
 |

 |
0, 1, 2
 |

SlaveChar
 |
SlaveChar
 |
slave
 |
0, 1, 2
 |

SlaveObject
 |
SlaveObject
 |
slave
 |
0, 1, 2
 |

With this setup, we can therefore synchronize fragments for up to 7 different characters.

##
Attaching characters to scopes

The next step is for the game to fill the matching scope contexts with the appropriate Entity, Character and Animation Database. There are two different ways of doing this, depending on whether the character we want to bind to a scope context already has its own action controller or not.

##
Simple secondary characters

Simple animated objects such as weapons in a shooter game typically do not have their own action controller. Driving synchronized animations on such objects is therefore only a matter of binding the character to the relevant host's scope context. This can be done in numerous ways. Please look at
[Scope Contexts](../Mannequin%20Concepts/Mannequin%20Scopes/Mannequin%20Scope%20Contexts.md#MannequinScopeContexts-FillingScopeContexts)
 for more details on this.

##
Mannequin-driven secondary characters

In some situations, you might want to synchronize animations with another game character having its own Mannequin action controller. An example of this would be a player performing a synchronized stealth kill animation on another player in an action game. In those situations, we refer to the character driving the animation as the master, and the other one as a slave. For such scenarios, we actually want the master to temporary take control over the slave's action controller, so that no concurrent fragment requests occur. This can safely be performed in code by calling the IActionController::SetSlaveController method on the host. This method will internally take care of binding the slave character to the relevant scope context, as well as make sure that no conflicting requests occur on the slave's controller. Whenever you need to release the slave character, just call IActionController::SetSlaveController again with 'enslave' set to false on the host's action controller, and the enslavement will be terminated.

Typically you would call those methods from a dedicated
[Mannequin Action](Mannequin%20Actions.md)
, which provides a safe and consistent framework to setup the enslavement process. In the sample game provided with the SDK, this is for example performed by the CActionCoopAnim or CActionMultiCoopAnim actions, which handle cooperative (synchronized) animations. Those actions are in turn used by the Hit Death Reactions system to handle synchronized kills.

It is also possible to enslave characters using the dedicated EnslaveCharacter FlowGraph node. For more details, please refer to
[Mannequin Flowgraph](../Mannequin%20Flowgraph.md)
.

Using a different animation database when enslaving a character.
When calling IActionController::SetSlaveController or using the EnslaveCharacter FlowGraph node, you can optionally give a pointer to an
[Animation Database](../Mannequin%20Files/Animation%20Database%20(ADB).md)
. If you do so, fragments played on the slave characters will be looked for in this database. Otherwise (or if you just send a NULL pointer), they'll be queried from the master's animation database.

Also, if you use this optional animation database field, please note that the slave's action controller will be completely paused for the duration of the enslavement. Any fragment currently playing on any scope of the slave's action controller will be stopped, and it will not be possible to install any new one until the enslavement is finished. If you do not use this optional animation database, then it will still be possible to play fragments on various scopes, even while the enslavement is active. It is even possible this way to have one action controller being slave of multiple other controllers on different scopes.

##
Playing a synchronized fragment

Once the relevant characters are attached to the suitable scope contexts, playing a synchronized animation is only a matter of requesting a fragment on the host's action controller. The
[Fragment Selection Process](../Mannequin%20Concepts/Fragment%20Selection%20Process.md)
 will internally make sure that the correct fragment is played on every relevant scope, and strict synchronization will therefore be guaranteed.
