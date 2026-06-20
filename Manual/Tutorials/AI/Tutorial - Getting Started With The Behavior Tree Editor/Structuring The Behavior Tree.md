# Structuring The Behavior Tree

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/36870015
- Page ID: 36870015
- Breadcrumb: Tutorials > AI > Tutorial - Getting Started With The Behavior Tree Editor > Structuring The Behavior Tree
- Parent: Tutorial - Getting Started With The Behavior Tree Editor

## Content

## Overview

It's always best to plan the structure of a behavior tree before actually implementing it using the Behavior Tree Editor. This not only helps in determining the different nodes required and their position within the tree, but also helps in preventing errors in the tree's design ahead of their occurrence.

This section then is intended to walk users through the design of a very basic behavior tree, that causes an AI character to *follow* the player when sighted. If and when the AI is unable to follow the player through an area, the character * salutes* the player.

At the end of each step, an XML representation of the behavior tree is depicted for ease of understanding.

Only interested in knowing how to use the Behavior Tree Editor tool?

Skip this section and move on to the second part of this tutorial, [Implementing the Behavior Tree in The Behavior Tree Editor](Implementing%20The%20Behavior%20Tree%20in%20The%20Behavior%20Tree%20Editor.md) instead.

### Root Node

Every behavior tree must begin with a root node that:

- Is the first node to be executed,
- Is always running. A root node can neither succeed nor fail and,
- Has only a single child node, which it calls to execute the logic of its tree.

Since the goal of behavior tree here is to have its AI character perform a sequence of actions namely:

- Keep checking if the player is in sight,
- Move towards the player position and,
- Perform an animation when unable to move to the player.

The **Sequence** node is the most appropriate choice of node to be called by the root. Located within the ** Flow** category of nodes in the Behavior Tree Editor, the ** Sequence** node executes each of its children nodes in the order they're defined, one at a time.

**Parameters** | None.
--- | ---
**Results** | Outcome | Criteria --- | --- **Success** | When each of its children nodes returns a successful result. ** Failure** | If at least one of its children nodes returns a failure.
Outcome | Criteria
**Success** | When each of its children nodes returns a successful result.
**Failure** | If at least one of its children nodes returns a failure.

*Sequence node configuration*

```
<?xml version="1.0"?>
-<BehaviorTree>
<MetaExtensions/>
-<Root>
-<Sequence>
```

### Defining Events

Events in a behavior tree are used to inform AI agents of the occurrence of specific scenarios within the game, causing them to react accordingly.

In the case of the behavior tree here, the AI character must be notified of when the player is in sight. CRYENGINE comes with a built-in event called **OnNewAttentionTarget**, which is automatically triggered when the AI detects a target which in this case, is the player.

Since the AI agent/behavior tree must remain idle till the player is sighted, it seems appropriate to use the **Time** →** Wait for Event**node; this node works by pausing execution of the tree until a specified event is received.

**Parameters** | Parameter Name | Description | Value --- | --- | --- **Event** | Specifies the Event the node must wait for. | ** OnNewAttentionTarget** |
--- | --- | ---
Parameter Name | Description | Value
**Event** | Specifies the Event the node must wait for. | **OnNewAttentionTarget**
**Results** | Outcome | Criteria --- | --- **Success** | When the ** OnNewAttentionTarget** Event is received. ** Failure** | Never. |
Outcome | Criteria |
**Success** | When the **OnNewAttentionTarget** Event is received. |
**Failure** | Never. |

*Wait for Event node configuration*

Assuming that the **Wait for Event** node ceases execution of the behavior tree until the ** OneNewAttentionTarget** event is received, the structure of the tree so far is as follows:

```
<?xml version="1.0"?>
- <BehaviorTree>
<MetaExtensions/>
- <Root>
- <Sequence>
<WaitForEvent name="OnNewAttentionTarget"/>
```

### Node Sequence

#### Move

The next step is to have the AI agent move towards the target/player when the **OnNewAttentionTarget** event is received. To do so the ** GameSDK →****Move** node is selected, which moves the agent from its current position to a specified destination; this destination is updated if the target is moving.

**Parameters** | **Parameter Name** | Description | Value --- | --- | --- ** Stop Within Distance** | The minimum distance from the destination after which the AI agent stops moving. | ** 2** ** To** | The destination of the AI agent. | ** Target** |
--- | --- | ---
**Parameter Name** | Description | Value
**Stop Within Distance** | The minimum distance from the destination after which the AI agent stops moving. | **2**
**To** | The destination of the AI agent. | **Target**
**Results** | Outcome | Criteria --- | --- **Success** | When the agent is within the ** Stop Within Distance**. ** Failure** | If the specified destination is unreachable by the agent. |
Outcome | Criteria |
**Success** | When the agent is within the **Stop Within Distance**. |
**Failure** | If the specified destination is unreachable by the agent. |

*Move node configuration*

In order to have the AI agent move towards the player (target), the value of the **Move** node's ** To** parameter is set to ** Target**; additionally, the agent will stop at a distance of ** 2m** from the ** Target**. While all other parameters have been left at their default values, feel free to experiment with alternate ones.

```
<?xml version="1.0"?>
-< BehaviorTree>
<MetaExtensions/>
- <Root>
- <Sequence>
<WaitForEvent name="OnNewAttentionTarget"/>
- <Move considerActorsAsPathObstacles="0" avoidGroupMates="0" avoidDangers="1" fireMode="Off" to="Target" glanceInMovementDirection="0" strafe="0" turnTowardsMovementDirectionBeforeMoving="0" moveToCover="0" bodyOrientation="Halfway Towards Aim Or Look" stance="Stand" speed="Run" stopDistanceVariation="0" stopWithinDistance="2"/>
```

#### Loop

In the current behavior tree configuration, the AI agent executes two actions in sequence:

- It waits until the player/target is sighted.
- It moves to the player's position after the player is sighted, stopping at a distance of **2m** from the player/target.

This movement however, will only be performed once; to make the agent to follow the player/target continuously, a **Flow →** ** Loop** node is added around the ** Move** node to cause it execute infinitely.

**Parameters** | Parameter Name | Description | Value --- | --- | --- **Repeat Count** | Specifies the number of times the node must loop the execution of its child node. | ** 0** (loops infinitely) |
--- | --- | ---
Parameter Name | Description | Value
**Repeat Count** | Specifies the number of times the node must loop the execution of its child node. | **0** (loops infinitely)
**Results** | Outcome | Criteria --- | --- **Success** | If the loop of execution runs for the specified ** Repeat Count**, which in this case is infinite. ** Failure** | If the Loop node's child fails. |
Outcome | Criteria |
**Success** | If the loop of execution runs for the specified **Repeat Count**, which in this case is infinite. |
**Failure** | If the Loop node's child fails. |

*Loop node configuration*

```
<?xml version="1.0"?>
-<BehaviorTree>
<MetaExtensions/>
- <Root>
- <Sequence>
<WaitForEvent name="OnNewAttentionTarget"/>
- Loop
- <Move considerActorsAsPathObstacles="0" avoidGroupMates="0" avoidDangers="1" fireMode="Off" to="Target" glanceInMovementDirection="0" strafe="0" turnTowardsMovementDirectionBeforeMoving="0" moveToCover="0" bodyOrientation="Halfway Towards Aim Or Look" stance="Stand" speed="Run" stopDistanceVariation="0" stopWithinDistance="2"/>
```

The problem with the current structure is that if the player/target is unreachable by the AI agent, for example when the player is outside the agent's Navmesh, the **Loop** node will fail. This in turn will cause the ** Sequence** node and hence, the ** Root** node to fail, which should not happen.

#### Suppress Failure

To avoid this, a **Core →****Suppress Failure** node is added around the ** Move** node so that its execution always succeeds. This in turn ensures that the behavior tree is always running.

**Parameters Accepted** | None.
--- | ---
**Results** | Outcome | Criteria --- | --- **Success** | Throughout the execution of its child, which in this case is a ** Move** node. ** Failure** | Never.
Outcome | Criteria
**Success** | Throughout the execution of its child, which in this case is a **Move** node.
**Failure** | Never.

*Suppress Failureconfiguration*

```
<?xml version="1.0"?>
-<BehaviorTree>
<MetaExtensions/>
- <Root>
- <Sequence>
<WaitForEvent name="OnNewAttentionTarget"/>
- Loop
- <SuppressFailure>
- <Move considerActorsAsPathObstacles="0" avoidGroupMates="0" avoidDangers="1" fireMode="Off" to="Target" glanceInMovementDirection="0" strafe="0" turnTowardsMovementDirectionBeforeMoving="0" moveToCover="0" bodyOrientation="Halfway Towards Aim Or Look" stance="Stand" speed="Run" stopDistanceVariation="0" stopWithinDistance="2"/>
</SuppressFailure>
```

#### Animate

The goal of our behavior tree however, is not that of simply suppressing failure every time the AI agent is unable to reach its target/the player. It should perform an animation instead, specifically a *salute* animation, for which reason a **GameSDK → Animate** node is added to the tree with the following configuration:

**Parameters** | Parameter Name | Description | Value --- | --- | --- **Name** | Name of the [Fragment](../../../Editor%20Tools/Animation%20Tab/Mannequin%20Editor/Mannequin%20Concepts/Mannequin%20Fragments.md) containing the animation which must be played by the agent. | ** IA_salute_01** The ** IA_salute_01** references a * salute* animation for the AI Human character included in GameSDK. To preview and experiment with other GameSDK animations, load the **sdk_humanpreview.xml** preview setup in the [Mannequin Fragment Browser](/docs/static/engines/cryengine-3/categories/1114113/pages/15011340) using the ** File → Load Preview Setup...** option of its main menu. Scroll through the Fragment List to view all available animations. ** Play Mode** | States if the animation must be played once or loop infinitely. | ** PlayOnce** |
--- | --- | ---
Parameter Name | Description | Value
**Name** | Name of the [Fragment](../../../Editor%20Tools/Animation%20Tab/Mannequin%20Editor/Mannequin%20Concepts/Mannequin%20Fragments.md) containing the animation which must be played by the agent. | **IA_salute_01** The ** IA_salute_01** references a * salute* animation for the AI Human character included in GameSDK. To preview and experiment with other GameSDK animations, load the **sdk_humanpreview.xml** preview setup in the [Mannequin Fragment Browser](/docs/static/engines/cryengine-3/categories/1114113/pages/15011340) using the ** File → Load Preview Setup...** option of its main menu. Scroll through the Fragment List to view all available animations.
**Play Mode** | States if the animation must be played once or loop infinitely. | **PlayOnce**
**Results** | Outcome | Criteria --- | --- **Success** | - When the specified animation is played once. - If the specified animation fails to play. ** Failure** | Never. |
Outcome | Criteria |
**Success** | - When the specified animation is played once. - If the specified animation fails to play. |
**Failure** | Never. |

*Animate node configuration*

#### Selector

In order to ensure that the **Move** node is executed first with priority, and that the ** Animate** node is executed only when the ** Move** node fails, a ** Flow → Selector** node is used. Since the ** Selector** node executes its children in the order of their definition, one at a time, the ** Move** and an ** Animate** nodes are made its children as follows:

**Parameters** | None.
--- | ---
**Results** | Outcome | Criteria --- | --- **Success** | When at least one of its children nodes returns a successful result. ** Failure** | If all of its children nodes return a failure.
Outcome | Criteria
**Success** | When at least one of its children nodes returns a successful result.
**Failure** | If all of its children nodes return a failure.

*Selector node configuration*

```
<?xml version="1.0"?>
-<BehaviorTree>
<MetaExtensions/>
- <Root>
- <Sequence>
<WaitForEvent name="OnNewAttentionTarget"/>
- Loop
- <Selector>
- <Move considerActorsAsPathObstacles="0" avoidGroupMates="0" avoidDangers="1" fireMode="Off" to="Target" glanceInMovementDirection="0" strafe="0" turnTowardsMovementDirectionBeforeMoving="0" moveToCover="0" bodyOrientation="Halfway Towards Aim Or Look" stance="Stand" speed="Run" stopDistanceVariation="0" stopWithinDistance="2"/>
- <Animate name="IA_Salute_01" setBodyDirectionTowardsAttentionTarget="0" urgent="1" playMode="PlayOnce"/>
</Selector>
</Loop>
</Sequence>
</Root>
</BehaviorTree>
```

### Final Configuration

At this point, the behavior tree is complete and its sequence is as follows:

- The **Root** node calls a ** Sequence** node, which in turn waits for the ** OnNewAttentionTarget** event before executing its children,
- As soon as the AI agent sees the player/target, the **OnNewAttentionTarget** event is received and the ** WaitforEvent** node succeeds.
- The **Sequence** node then executes its second child node, a ** Loop** node which repeatedly executes a ** Selector** node. This ** Selector** node has two children, a ** Move**and an ** Animate** node, which it processes as follows:

- - - The **Move** child node is executed for as long as the target/player is reachable by the agent. This causes the agent to follow the player/target within its NavMesh. As soon as the player/target leaves the NavMesh, the ** Move**node fails.
- The **Animate** child node is executed when the player/target leaves the Navmesh, causing the agent to * salute*the player/target when unreachable. As soon as the player/target returns to the NavMesh, the **Move** node is executed again and the agent follows the player/target as before.

The structural design of the behavior tree is now complete. Now to implement it in the Behavior Tree Editor, and link it to an AI character in the [next section](Implementing%20The%20Behavior%20Tree%20in%20The%20Behavior%20Tree%20Editor.md) of this tutorial.

[Root Node](#root-node)[Defining Events](#defining-events)[Node Sequence](#node-sequence)[Final Configuration](#final-configuration)

##### Related Pages

[Implementing The Behavior Tree in The Behavior Tree Editor](Implementing%20The%20Behavior%20Tree%20in%20The%20Behavior%20Tree%20Editor.md)

[Behavior Tree Editor](../../../Editor%20Tools/Behavior%20Tree%20Editor.md)
