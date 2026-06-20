# Body Damage and Destruction

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/23306583
- Page ID: 23306583
- Breadcrumb: CRYENGINE Game Code > Miscellaneous Game Code > Game Characters > Body Damage and Destruction
- Parent: Game Characters

## Child Pages

- [Body Damage](Body%20Damage%20and%20Destruction/Body%20Damage.md)
- [Body Destructibility](Body%20Damage%20and%20Destruction/Body%20Destructibility.md)
- [Body Parts](Body%20Damage%20and%20Destruction/Body%20Parts.md)

## Content

##
Overview

Each AI archetype entity has under its 'Damage' properties two fields to specify which bodypart/damage setup to use.

##
Body Damage

The Body Damage game system allows for setting up damage multipliers for a character's body parts.

These damage multipliers will be used when the character is being hit by bullets, collision, explosions... during the game.

The system is split into two main components:

-
[Body Parts](Body%20Damage%20and%20Destruction/Body%20Parts.md)
 - defines the body parts - should be set up by a tech artist.

-
[Body Damage](Body%20Damage%20and%20Destruction/Body%20Damage.md)
 - sets the damage multipliers - should be tweaked by a game designer.
Debug console variables and commands related to the body damage can be found further below.

##
Body Destruction

The Body Destruction system allows for bodyparts of a character to be made destructible.

The system stores the damage done to defined body parts and triggers destruction events when its health points are depleted.

Destruction Events can also be triggered when the character's health pass a certain threshold.

Destruction events can consist of the following:

-
Hiding/Unhiding of character attachments - this can be used to remove or 'swap out' body parts for a destroyed version.

-
Particle Effects - these can be used to spawn detached bodyparts, blood, smoke, etc.

-
Explosions - these can be used to explode body parts and damage surrounding characters.

-
Material Switching of the character - this can be used to turn off glowing parts, add dirt from explosions, etc.
Some special features are available for death from Explosions and Microwave Gun.

Note that the Body Destruction system will never alter the damage done to the character itself!

The system is configured through the
[Body Destructibility](Body%20Damage%20and%20Destruction/Body%20Destructibility.md)
 xml file.

##
Console Variables and Commands

CVar

 |
Description

 |

**
g_bodyDamage_log
**

 |
Enables/Disables body damage console logging.

Log includes information regarding normal hits, and explosion hits, informing about body locations affected and damage multipliers which apply.

 |

**
g_bodyDestruction_debug
**

 |
Enables/Disables body destruction on screen logging messages.

Log information includes hit location, bullet type, damage caused, if there was an destruction event triggered, etc.

 |

**
g_bodyDestruction_debugFilter
**
*
EntityName
*

 |
Enables detailed debug information on a particular entity. Display information includes:

-
List of destroyable bones/attachments and their corresponding health status.

When displayed in green it means those are visible and/or not destroyed, while in red it means the opposite

-
List of destruction events (Available ones in green, disabled or already triggered in red)

-
List of health ratio events (Green if not triggered, red if they did)
 |

**
g_bodyDamage_reload
**

*
OptionalActorName
*

 |
Reloads BodyDamage xml data for the specified actor (optional parameter), or for everyone if none is provided.

 |
