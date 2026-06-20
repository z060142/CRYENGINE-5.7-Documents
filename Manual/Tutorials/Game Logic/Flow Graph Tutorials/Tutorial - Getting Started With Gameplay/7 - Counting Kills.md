# 7 - Counting Kills

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/29450272
- Page ID: 29450272
- Breadcrumb: Tutorials > Game Logic > Flow Graph Tutorials > Tutorial - Getting Started With Gameplay > 7 - Counting Kills
- Parent: Tutorial - Getting Started With Gameplay

## Content

[/docs/static/engines/cryengine-5/categories/23756816/pages/29793816](
[Image: /docs/static/attachments/44971037]
6 - Spawning AI Waves
)

[/docs/static/engines/cryengine-5/categories/23756816/pages/29450274](
[Image: /docs/static/attachments/44971038]
8 - Writing to XML
)

##
When and what do I track?

In this section we will be using the base AI that ships with the GameSDK package and the death of this AI in the scene to create a kill counter in which we will increment a value and then print it to the screen. The logic is quite simple to understand: we need to be able to keep track of the Shooter and then pass this information on to a counter. This counter will check for the death of the AI entity and then print out the information on the screen once the value becomes 1.

This lesson will also take into account the Class of the Entity and show how you can differentiate between death to drive or separate the logic of factions and the way you reward the player. You can keep track of this through the Weapon info and passing the information of the target to the to a check that looks to see if the human class is being affected. If it does than you increment the GameToken variable only when it sees the Human and in this case not the Boid.

##
How To Count Kills

You need to follow these below mentioned steps to keep track of enemy kills:

-
This lesson requires the previous chapter of
[/docs/static/engines/cryengine-5/categories/23756816/pages/29793816](
6 - Spawning AI Waves
)
 to have been completed to carry on.

-
Add a
**
Graph Token
**
 to keep track of the kill count and print it to the screen. To start off we need to head up to the top of the Flow Graph tool and then click
**
Tools -> Edit Graph Tokens
**
... to assign it the name of
**
killCount
**
 and the type of
**
Int
**
.

-
Initialize your token by creating a
**
Mission:GameTokenSet
**
 node and add the
**
killCount
**
 token to the slot and assign the initial
**
Value
**
 to be
**
Zero
**
.

-
Add a
**
Weapon:HitInfo
**
 node to the graph to begin tracking the amount of kills that are happening from the player side. We will need to connect the
**
Game:Start Output
**
 to the Enable input port of the
**
Weapon
**
 node. Along with this we will need to connect an
**
Actor:LocalPlayer
**
 node to the
**
Shooter Id
**
 port.

-
Now the shooter logic has been defined, output the target logic from the
**
Weapon:HitInfo
**
 node (1). To stem this off, create an
**
Entity:EntityInfo
**
 node to check the
**
Class
**
 (2) to split scoring logic and then run a
**
String:Compare
**
 node to see if the string "
**
human
**
" is the class of the Entity (3).

-
Now we simply need to check the
**
Alive
**
 state of the Entity and if it outputs from
**
Dead
**
(2), we will run a
**
Mission:GameTokenModify
**
 node that has the
**
killCount
**
 token attached with an
**
Addition
**
operation set to
**
Integer
**
(3).

-
Finally, in this step we can hook up a
**
Mission:GameToken
**
 node with
**
killcount
**
 as the Token and
**
Output
**
 to a
**
Debug
**

**
DisplayMessage
**
 node in the
**
Show
**
 and
**
Message
**
 slots.

##
Step 2

[Image: /docs/static/attachments/29929359]

##
Step 3

[Image: /docs/static/attachments/29929360]

##
Step 4

[Image: /docs/static/attachments/29929361]

##
Step 5

[Image: /docs/static/attachments/29929362]

##
Step 6

[Image: /docs/static/attachments/29929363]

##
Step 7

[Image: /docs/static/attachments/29929364]

##
Full Graph

[Image: /docs/static/attachments/29929365]

##
Final Result

[Image: /docs/static/attachments/29929358]

[/docs/static/engines/cryengine-5/categories/23756816/pages/29793816](
[Image: /docs/static/attachments/44971037]
6 - Spawning AI Waves
)

[/docs/static/engines/cryengine-5/categories/23756816/pages/29450274](
[Image: /docs/static/attachments/44971038]
8 - Writing to XML
)
