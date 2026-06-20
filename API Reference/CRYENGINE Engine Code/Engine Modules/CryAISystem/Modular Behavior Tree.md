# Modular Behavior Tree

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/23306488
- Page ID: 23306488
- Breadcrumb: CRYENGINE Engine Code > Engine Modules > CryAISystem > Modular Behavior Tree
- Parent: CryAISystem

## Child Pages

- [Modular Behavior Tree Nodes](Modular%20Behavior%20Tree/Modular%20Behavior%20Tree%20Nodes.md)
- [Modular Behavior Tree Debugging](Modular%20Behavior%20Tree/Modular%20Behavior%20Tree%20Debugging.md)

## Content

### Overview

The Modular Behavior Tree (MBT) is a decision making system for individual AI characters. It allows the AI to perform actions and react to its environment. The structure of the tree is specified by certain nodes and gets defined in XML.

Basically, an MBT consists of:

- Variables
- SignalVariables
- Timestamps
- The Root node (which is where the actual tree starts)

Regarding the Root node, the most commonly used nodes in here are:

- Sequences
- Selectors
- Priorities
- Actions

#### Example Tree Structure

```
<BehaviorTree>
<Variables>
<Variable name="HasTarget"/>
</Variables>
<SignalVariables>
</SignalVariables>
<Timestamps>
</Timestamps>
<Root>
<Sequence>
<Log message="Test" />
<WaitForEvent name="OnEnemySeen" />
<Move to="Target" speed="Walk" stance="Stand" fireMode="BurstWhileMoving" />
<Halt />
</Sequence>
</Root>
</BehaviorTree>
```

Additional documentation:

- [Modular Behavior Tree Nodes](Modular%20Behavior%20Tree/Modular%20Behavior%20Tree%20Nodes.md)
- [Modular Behavior Tree Debugging](Modular%20Behavior%20Tree/Modular%20Behavior%20Tree%20Debugging.md)

#### Tree Files

The XML files need to reside in `Scripts/AI/BehaviorTrees`. Some sample trees that ship with SDK can be found in there already.

Every XML file that is located in that folder will automatically appear in the drop-down list of the entity's `ModularBehaviorTree` property in Sandbox (you may need to restart Sandbox to make new files appear).

Make sure the `SelectionTree` property is empty (only one type of tree can run)

#### Specification (draft)

Download: [Modular Behavior Tree Documentation.pdf](/docs/static/attachments/23461256)

[Modular Behavior Tree Documentation.pdf](/docs/static/attachments/23461256)
