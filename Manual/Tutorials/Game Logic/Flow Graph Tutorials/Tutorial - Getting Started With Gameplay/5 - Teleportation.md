# 5 - Teleportation

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/29793753
- Page ID: 29793753
- Breadcrumb: Tutorials > Game Logic > Flow Graph Tutorials > Tutorial - Getting Started With Gameplay > 5 - Teleportation
- Parent: Tutorial - Getting Started With Gameplay

## Content

[/docs/static/engines/cryengine-5/categories/23756816/pages/29450270](
[Image: /docs/static/attachments/44971029]
4 - Opening a Locked Door
)

[/docs/static/engines/cryengine-5/categories/23756816/pages/29793816](
[Image: /docs/static/attachments/44971030]
6 - Spawning AI Waves
)

##
What logic is required for teleportation to work?

One of the most common forms of gameplay to progress multiplayer or even story is the ability to teleport from one point to another. The logic behind this is simple in that we need to be able to define the bounds of an object that we pass into and then we need to be able to direct the repositioning of the player when we intersect those bounds.

After this we will need to be able to drive the player to a point, in this regard we will be using a Tag Point from the AI section to be able to house the positional coordinates. At first we will look at exposing the basic teleporter and then we will quickly look at the logic to make it multi-positional for teleportation on both sides.

##
How To Create a Teleporter

Follow the steps below to create a teleporter:

-
Add a small box next to where you want your Proximity Trigger to be so you know where the teleport will take place when you cross into the bounds of the Proximity Trigger.

-
Add both your Spawnpoint and a Proximity Trigger to the scene. These can be found in
**
Create Object -> Legacy Entities
**
.

-
Click
**
RMB
**
 on the Proximity Trigger and choose
**
Create Flow Graph
**
. In this exercise we will keep with the naming
*
gameplayQuickStart
*
.

-
Select both entities within your scene and then go to Flow Graph and click
**
RMB
**
 and choose
**
Add Selected Entity
**
.

-
Add a
**
Cylinder
**
 and
**
Tag Point
**
 to the level. The
**
Tag Point
**
 is located in
**
Create Object -> AI -> Tag Point
**
, while the Cylinder is a standard brush asset found in
**
Create Object -> Brush -> Objects -> Default -> Cylinder.cgf
**
.

-
In our next step we will go back to the Flow Graph setup and add a
**
Beam
**
 entity node. After this, we can hook up our logic of when and where the player should travel. First, connect the
**
Enter
**
 output from the
**
Proximity Trigger
**
 into the
**
Beam
**
 input port of the Beam node. For the
**
EntityID
**
 we have added a
**
LocalPlayer
**
 node to access the player only for the beam.

-
Now with the beam connected we will make sure that the
**
 Yellow Arrow
**
 on the
**
Tag Point
**
 is facing back towards where we were. Click in the Flow Graph to
**
Add Selected Entity
**
 and connect the
**
Position
**
 and
**
Rotation
**
 output ports to the
**
Beam Entity
**
 node.

-
Finally, jump into the game. You will notice that when you walk forward to the box platform that you get flipped around and faced back towards your origin while maintaining your velocity forward.

##
Step 1

[Image: /docs/static/attachments/29929307]

##
Step 2-1

[Image: /docs/static/attachments/29929308]

##
Step 2-2

[Image: /docs/static/attachments/29929309]

##
Step 3

[Image: /docs/static/attachments/29929310]

##
Step 4

[Image: /docs/static/attachments/29929311]

##
Step 5

[Image: /docs/static/attachments/29929312]

##
Step 6

[Image: /docs/static/attachments/29929304]

##
Step 7

[Image: /docs/static/attachments/29929305]

##
Step 8

[Image: /docs/static/attachments/29929306]

[/docs/static/engines/cryengine-5/categories/23756816/pages/29450270](
[Image: /docs/static/attachments/44971029]
4 - Opening a Locked Door
)

[/docs/static/engines/cryengine-5/categories/23756816/pages/29793816](
[Image: /docs/static/attachments/44971030]
6 - Spawning AI Waves
)
