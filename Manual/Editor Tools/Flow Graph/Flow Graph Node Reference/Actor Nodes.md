# Actor Nodes

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/29450557
- Page ID: 29450557
- Breadcrumb: Editor Tools > Flow Graph > Flow Graph Node Reference > Actor Nodes
- Parent: Flow Graph Node Reference

## Content

##
Damage

Damages attached entity by [Damage] when [Trigger] is activated.

![Image](https://www.cryengine.com/docs/static/attachments/28901102)

The Damage node (formerly Game:DamageActor) is used to damage the AI characters or the player.

The target of the node has to be an actor, it does not work with entities that are not based on an actor class.The amount of damage as well of the position where the damage will be applied can be defined.

![Image](https://www.cryengine.com/docs/static/attachments/28901095)

In the above example, when the player is inside the trigger box it will apply 1 damage to the player every second at the start. As the Interpol:Float counts down to 0.05, this will reduce the time between each damage strike being applied.

##
EnslaveCharacter

Enslave one character to another.

![Image](https://www.cryengine.com/docs/static/attachments/28901103)

##
GrabObject

Target entity will try to grab the input object, respectively drop/throw its currently grabbed object.

![Image](https://www.cryengine.com/docs/static/attachments/28901108)

##
HealthCheck

The HealthCheck (formerly Game:ActorCheckHealth) node checks the health of an actor and outputs the result on a Boolean output port.

![Image](https://www.cryengine.com/docs/static/attachments/28901109)

A health range can be defined using the MinHealth and MaxHealth input ports.The target entity of this class needs to be an actor in order to work.

When the node is triggered the health of the target entity is checked and if it is within the defined values true will be output on the output port.

![Image](https://www.cryengine.com/docs/static/attachments/28901101)

In the above example, we have set up a flow graph to test the player's health value when he enters a trigger box, then if it is above 50, spawn all three of the enemies. If the player's health is below 50, only spawn two of the enemies. The health of an actor is checked by using the
*
Game:ActorCheckHealth
*
 node and checking the Boolean output port using a
*
Math:FromBoolean
*
 node. The input to the
*
Math:FromBoolean
*
 node will be true if the health of the target entity is between 0 and 50. The
*
Math:FromBoolean
*
 node then splits the output to be passed on to either 2 or 3 enemies.

##
HealthGet

Formerly "Game:ActorGetHealth". Get health of an entity (actor).

![Image](https://www.cryengine.com/docs/static/attachments/28901110)

This node outputs the health of the target entity as an integer.

![Image](https://www.cryengine.com/docs/static/attachments/28901106)

In this example, the health of the target entity is compared using a Math:Less node to check if the value is below 50.

If it is true, it will pass through the true port & into the HealthSet node then carry on with the flowgraph. If the health is above 50, do nothing and pass on to the next step of the flowgraph.

##
HealthSet

Formerly "Game:ActorSetHealth". Set health of an entity (actor).

![Image](https://www.cryengine.com/docs/static/attachments/28901111)

This node can be used to set the health amount on a specified entity.

![Image](https://www.cryengine.com/docs/static/attachments/28901106)

In the above example, we are testing the player's health level with the Game:ActorSetHealth node and if it is below a certain level we use the Game:ActorSetHealth node to set it to 75.

##
LocalPlayer

Outputs the local player's entity id - NOT USABLE FOR MULTIPLAYER WITHOUT UPDATING BY HAND AFTER GAMESTART.

![Image](https://www.cryengine.com/docs/static/attachments/28901114)

In this example, the ID of an entity entering a proximity trigger is compared to the local player ID using the
*
Math:Equal
*
 node.

![Image](https://www.cryengine.com/docs/static/attachments/28901096)

##
PlayMannequinFragment

Play a Mannequin Fragment on a given entity with given Tags.

![Image](https://www.cryengine.com/docs/static/attachments/28901089)

##
ProcClipEventListener

Listens for Mannequin procedural clip events.

[Damage](#damage)
[EnslaveCharacter](#enslavecharacter)
[GrabObject](#grabobject)
[HealthCheck](#healthcheck)
[HealthGet](#healthget)
[HealthSet](#healthset)
[LocalPlayer](#localplayer)
[PlayMannequinFragment](#playmannequinfragment)
[ProcClipEventListener](#procclipeventlistener)
