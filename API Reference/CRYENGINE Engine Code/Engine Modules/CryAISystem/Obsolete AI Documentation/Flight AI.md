# Flight AI

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/23306456
- Page ID: 23306456
- Breadcrumb: CRYENGINE Engine Code > Engine Modules > CryAISystem > Obsolete AI Documentation > Flight AI
- Parent: Obsolete AI Documentation

## Content

##
Changes to Flight AI for Crysis 3

We now have some new archetypes and flownodes to be used in conjunction with these entities to control flying vehicles.

In the characters archetype library you can find:

-
**
CELL/Helicopter.Regular
**

-
**
Ceph/Dropship.Regular
**

-
**
Ceph/Gunship.Regular
**
They should be used as a replacement to the old archetypes from the c3_vehicles archetype library in order to get the navigation and behavior changes.

The new flownodes that should be used with these entities can be found under the Helicopter category:

![Image](https://www.cryengine.com/docs/static/attachments/23461210)

##
FollowPath:

-
Sets the current path that the flight AI uses.

-
When AI is not in combat mode.

-
If we don't allow it to loop through the path in the flownode, the AI will try to go from its current location to the beginning of the path and follow it until it reaches the end of the path.

-
If we allow it to loop through the path in the flownode, the AI will try to go from its current location to the closest point of the path and keep following it. The node outputs indicating that it has arrived to the end of the path is only sent once.

-
When AI is in combat mode.

-
When the target is visible.

-
The path is used to position the AI to the best location to attack the target. It is also used to navigate between positions it can go to within the path.

-
When the target is not visible the path is used as a patrol path. Therefore it simplifies the setup to have paths in combat mode be looping if possible.

##
EnableCombatMode:

-
Enables or disables the ability of the AI to position itself within the combat path to engage and shoot at its current target. By default an AI is
*
not
*
 in combat mode until explicitly allowed to go into combat mode.

-
When AI is in combat mode and has an idea of where the target is (if it ever saw one), it will try to reposition itself within the current path to somewhere from where it can shoot at it.

-
Any character of an opposing faction is a good candidate for a target.

##
EnableFiring:

-
Enables or disables the ability of the AI to shoot at its current target when in combat mode. By default an AI is allowed to fire when in combat mode, unless explicitly set to disabled with this node.
The new AI behavior is implemented using the new modular behavior tree system and all of them are sharing the same one (HelicopterTree.xml)

The changes to flight navigation were done because of the unreliability or lack of functional behavior and complex setup needed. A test map for a bunch of cases that didn't work can be found in a test map called Suit_Disrupter.
