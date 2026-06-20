# Flow Graph Basics

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/25535227
- Page ID: 25535227
- Breadcrumb: Scripting > Flow Graph Overview > Flow Graph Basics
- Parent: Flow Graph Overview

## Child Pages

- [Adding & Editing Nodes](Flow%20Graph%20Basics/Adding%20%26%20Editing%20Nodes.md)
- [Creating & Editing Links](Flow%20Graph%20Basics/Creating%20%26%20Editing%20Links.md)
- [Flow Graph Node Composition](Flow%20Graph%20Basics/Flow%20Graph%20Node%20Composition.md)
- [Importing & Exporting Flow Graphs](Flow%20Graph%20Basics/Importing%20%26%20Exporting%20Flow%20Graphs.md)

## Content

![Image](https://www.cryengine.com/docs/static/attachments/29933583)

##
Overview

##
Sections

After completing this tutorial, you will be able to set up a simple mission, define the starting point of the level, assign one objective, and a load next level trigger.

The more non-linear the mission objectives are, the more time you need to spend testing them. It is therefore recommended that beginners make a linear gameplay path to start with: 1st objective, complete triggers, 2nd objective, and triggers mission end.

[Sections](#sections)
[Adding a Spawn Point](#adding-a-spawn-point)
[Triggering Events](#triggering-events)
[Adding Logic to Triggers](#adding-logic-to-triggers)
[Loading a New Mission](#loading-a-new-mission)
[Result](#result)

##
Adding a Spawn Point

Under the
Create Object -> Entity -> Others
, drag the
SpawnPoint
 entity to a point in the Perspective viewport.

*
Pic1: Creating a Spawnpoint
*

![Image](https://www.cryengine.com/docs/static/attachments/35401651)

It is generally a good idea to use
Flow Graph
 to script the game to spawn the player at the spawn point. Otherwise when you run the Launcher, you can be spawned at the
0,0,0
 location coordinates within the level.

To make the Spawn Point work, select it and right-click on it. Then choose Create Flow Graph and give it a logical name, like "SpawnPoint".

Then right-click in the Flowgraph and choose
Add Node -> Game -> Start
. Next, make sure you have the Spawn Point selected, right-click on an empty space and choose
Add Selected Entity
.

Now all you need to do is click and hold the
output
 port of the
Start
 node and drag the appearing arrow to the
Spawn
 port of the
SpawnPoint
 node.

*
Pic2:  Using Flowgraph to script the game's Spawn Point

![Image](https://www.cryengine.com/docs/static/attachments/35401650)

*

The reason this is not automated is levels can have multiple spawn points, like one at every checkpoint, for example. So you need to define where you want the player to spawn and when.

##
Triggering Events

##
Proximity Triggers

You can use triggers to activate various actions in the Editor. This tutorial covers two main ones:
Proximity Triggers
 and
Area Triggers
. You can drag triggers also to the Perspective viewport.

*
Pic3: ProximityTrigger location
*

![Image](https://www.cryengine.com/docs/static/attachments/35401651)

You can double-click or drag and place this trigger in your level. It will be displayed as a
T
 icon with a yellow box around it:

*
Pic4: Proximity Trigger placed
*

![Image](https://www.cryengine.com/docs/static/attachments/35401652)

When you select the Proximity Trigger, you can change its properties in the Properties tool:

*
Pic5: Proximity Trigger properties
*

![Image](https://www.cryengine.com/docs/static/attachments/35401653)

There are numerous things you can set up here, like the size of the area in which it's triggered (
DimX
,
DimY
,
DimZ
), whether it can only triggered by AI (
OnlyAI
), the player (
OnlyMyPlayer
) etc., or if it can only be triggered once (
TriggerOnce
).

##
Placing an Area Trigger

An AreaTrigger is split into 2 parts, the
Area Shape
 and the
Area Trigger
 Entity. The Trigger is placed from the
Create Object
 tab.

First go to the
Create Object
 tool (
Entities -> Triggers -> AreaTrigger
) and place one down in the level.

Then create a
Shape
 using the
Area
 tool found in the
Create Object
 tool (
Area -> Shape)
, and draw out a shape by clicking at four different spots and double-clicking the last spot to close the shape.

You can add as many points in as you want to define the exact shape of the triggers activation area, but it doesn't have to be super detailed, simply approximate the shape.
Make sure
Snapping to Geometry
is turned on before drawing your shape, as otherwise it might be drawn vertically instead of on the terrain.

Pic6:
*
Creating a Shape using the Area tool
*

![Image](https://www.cryengine.com/docs/static/attachments/35401654)

*
Pic7: Area Shape drawn

![Image](https://www.cryengine.com/docs/static/attachments/35401655)

*

Next place down an area trigger from
Create Object -> Entity -> Triggers -> Area Trigger
 and assign the
AreaTrigger
 to the shape.

You do this by selecting the shape, clicking the button next to
EntityLinks
 in the
Properties
 and choosing
Add
:

*
Pic8: Adding an EntityLink

![Image](https://www.cryengine.com/docs/static/attachments/35401656)

*

When you've done this, a box will appear under the EntityLinks header. Click on this box and it will read "Pick an Entity...". All you have to do now is click on the AreaTrigger you have created earlier and the shape and AreaTrigger will be linked:

*
Pic9: Picking the AreaTrigger
*

![Image](https://www.cryengine.com/docs/static/attachments/35401657)

Unlike Proximity Triggers, Area Triggers have no boundary to speak of. They are simply logical triggers. To use Area Triggers, you must link a shape to them to so they can work.
Area Shapes when created are a flat plane. Technically this means that the "activation area" of that shape is infinite in the Z axis. This is OK for most situations, unless you have a multi-floor setup where you only want to activate it on the ground floor.

To restrict this infinite Z axis on an Area Shape, we can assign a height to the shape from within its properties. To do this, change the
DimZ
 property in its
Entity Properties
:

*
Pic10: Changing the height of a Proximity Trigger

![Image](https://www.cryengine.com/docs/static/attachments/35401658)

*

This will then cap the height of the shape into a defined volume. X and Y is defined by the area shape and the height defines the limit of the Z axis.

When creating Proximity or Area Triggers, it's good practice to sink them slightly into the floor. This is to ensure activation of the trigger, as the player's reference point (Gizmo) is located between his feet.

##
Adding Logic to Triggers

##
Creating a Flow Graph

To define what a trigger should do, a Flow Graph needs to be created. Select the
AreaTrigger
 we just created, and then click
Open
in the
FlowGraph
 section of the
Entity Properties
 in the
Properties
 tool, or right-click the AreaTrigger in the viewport and select
Create Flow Graph
.

*
Pic11: Creating a Flow Graph
*

![Image](https://www.cryengine.com/docs/static/attachments/35401659)

Specify a group name for the Flow Graph by clicking
New...
 or by adding it to an existing group in the list. It is good practice to organize the level in layers, and then give the Flow Graph a name that contains the layer it mainly affects.

We will create a new group called
Mission.

*
Pic12: Creating a new group
*

*
![Image](https://www.cryengine.com/docs/static/attachments/35401660)

*

For more information, please see the documentation on using the
[How to Use Flow Graph](../../Editor%20Tools/Flow%20Graph/How%20to%20Use%20Flow%20Graph.md)
.

##
Adding an Entity to the Flow Graph

First make sure that the
AreaTrigger
 is selected in the Sandbox Editor. Then, in the
FlowGraph
 window, right-click in the empty field in the middle and select
Add Selected Entity
.

*
Pic13: Adding AreaTrigger node in Flow Graph
*

![Image](https://www.cryengine.com/docs/static/attachments/35401661)

Make sure that the
AreaTrigger
 node can be seen, by zooming in with the mouse wheel or by right-clicking in an empty space in the Flow Graph and choosing
Fit Graph To View
:

*
Pic14: Fitting the Graph to view
*

*
![Image](https://www.cryengine.com/docs/static/attachments/35401662)

*

The
AreaTrigger
 node has the input events on the left side and the output events on the right side.

##
Adding a Mission Objective

Drag the
MissionObjective
 entity to a place in the level where the player should go to.

*
Pic15: MissionObjective location

![Image](https://www.cryengine.com/docs/static/attachments/35401663)

*

*
Pic16: MissionObjective dragged into the level

![Image](https://www.cryengine.com/docs/static/attachments/35401664)

*

Open the
FlowGraph
 that you previously created, and then select the
MissionObjective
 entity in the Perspective view.

Now, add the
MissionObjective
 to the
FlowGraph
 by right-clicking the
FlowGraphs
 main window and selecting
Add Selected Entity
.

##
Connecting Entities in the FlowGraph

Now, move the
MissionObjective
 object to the right of the
AreaTrigger
 by clicking and dragging the object frame.

Once it is in place, left click and hold the
Enter
 port in the
AreaTrigger
 and drag the mouse to the
Activate
 port in the
MissionObjective
:

*
Pic17: Connecting AreaTrigger node to MissionObjective node
*

![Image](https://www.cryengine.com/docs/static/attachments/35401665)

The Mission Objective has several important inputs:

Input

 |
Description

 |

Activate

 |
0 means objective is not activated and 1 mean it is activated.

 |

Completed

 |
Marks an objective in the PDA as completed.

 |

Deactivate

 |
Removes an objective from the PDA.

 |

Failed

 |
Marks an objective in the PDA as failed.

 |

##
Loading a New Mission

Once the player has finished his objective, let's load the next level (obviously you could trigger another objective after the first one, but for this test, simply load the next level. Any random level will do, for example Woodland if you have downloaded the CRYENGINE GameSDK Sample Project from the
[Asset Database](https://www.cryengine.com/marketplace/product/crytek/cryengine-gamesdk-sample-project)
).

-
Place a
ProximityTrigger
 over the
MissionObjective
 node.

-
Add the
ProximityTrigger
 node to the
Flow Graph
.

-
Connect the
Enter
*
out
*
 port of the
ProximityTrigger
 with the
Completed
*
in
*
 port of the
MissionObjective
.

-
Add a
Delay
 node, double-click on its
Delay
 property and set a delay of 3 seconds.

-
Now, add a
Mission -> LoadNextLevel
 node.

-
Connect the
Completed
*
out
*
 port of the
MissionObjective
 to the
*
In
*
 of the
Delay,
 then connect the
*
out
*
 of the
Delay
 to the
*
input
*
Trigger
 port of the
LoadNextLevel
node.

-
Select the
LoadNextLevel
node and specify the name of the level that should be loaded in the Inputs field (Woodland).
*
Pic18: Loading a new mission using FlowGraph
*

*
![Image](https://www.cryengine.com/docs/static/attachments/35401666)

*

##
Result

When the player enters the Area Trigger, this activates the mission objective (top).

Then when the player walks into the Proximity Trigger (on enter output), this completes the mission and the next mission will be loaded after 3 seconds.

If you press
L
 (default key) for the mission objective HUD, you can see the missions come into your HUD and get updated when completed.

This (level loading command) works only in true game mode - the Editor will not load the next level.
You will get a warning in the console instead:

[SANDBOX: Warning] CCryAction: Suppressing loading of next level 'levelname' in Editor
