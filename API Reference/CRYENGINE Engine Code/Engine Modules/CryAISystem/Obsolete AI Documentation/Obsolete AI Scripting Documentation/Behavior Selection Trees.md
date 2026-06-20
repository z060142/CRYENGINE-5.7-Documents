# Behavior Selection Trees

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/23306477
- Page ID: 23306477
- Breadcrumb: CRYENGINE Engine Code > Engine Modules > CryAISystem > Obsolete AI Documentation > Obsolete AI Scripting Documentation > Behavior Selection Trees
- Parent: Obsolete AI Scripting Documentation

## Child Pages

- [Create A Simple AI Behavior](Behavior Selection Trees/Create A Simple AI Behavior.md)

## Content

Obsolete documentation - This article applies to CRYENGINE 3.4.x or earlier. Selection Trees have been replaced by Modular Behavior Trees in CRYENGINE 3.5 and above.

##
Overview

While behavior scripts represent the individual logic handling states AI can exist in, there still needs to be a way to select between them and the choose the right one at any moment of game time. Behavior Selection Trees (BHS) define a set of rules that allow the AI system to keep an AI in a valid behavior at all times. Each AI type should be associated with a BHS, and more than one AI type can refer to the same BHS.

Lets define an example which will be referred to over the course of this document. Say an AI called "Grunt" has 3 behaviors: idle, alert, and attack. The AI should default to idle when it has no stimulus, be in alert if it hears something unknown, and go to attack when it can visually see the player. It can fall back to idle after a period of time if it receives no updated auditory/visual stimulus. To support this, the AI must have a Behavior Selection Tree that would define which conditions are associated with which behaviors. The global AI System would take care of updating the AI's perception and sending event signals when the AI's perception state changes.

This type of design layout is key to getting a functioning AI in game as it defines all behavior that the AI must support. This should then naturally translate into a BHS with a set of matching implemented behaviors. The reset is all implementation details.

All Behavior Selection Trees must be defined inside the game folder under
`
\Scripts\AI\SelectionTrees
`
. A new tree added to this folder will be automatically picked up in the game on an 'ai_reload' or game restart. To associate a BHS with a particular AI archetype, load the archetype in the editor, and use the drop down box for the "BehaviorSelectionTree" parameter under the "Class Properties" tab.

##
The Behavior Selection Tree concept and anatomy

The Selection Tree concept assumes that at any moment in time, an AI will have one behavior matching its current state. So when the AI notices a sound it will investigate it, and when it sees an enemy it will attack it. Notice that the BHS does not contain any information on how an AI transitions between states, just how to choose the right one for the moment.

A BHS is defined through a XML script file, and must be available for an AI to enter any behaviors. If no BHS is available, the AI can only turn to face their attention target, and
**
ai_debugdraw 1
**
 will show "No Behavior" in the debug information.

The BHS XML files do not contain any script logic, and are purely data files which the AI System parses when deciding what behavior the AI should be in at any given time. BHS's can also include shared interchangeable blocks, allowing the designer to share base behavior between multiple AI.

##
A Behavior Selection Tree has 4 components

-
**
Selection Variables
**
 - Variables are used to define the conditions that select between states in the tree.

-
**
Signal Variables
**
 - Signal's as sent by the AI system that directly change the state of selection variables from (1).

-
**
Leaf Translations
**
 - List of mappings from generic names to archetype specific behavior names.

-
**
The Selection Tree
**
 - The tree structure which defines how behaviors are prioritized and which conditions must be met.

##
Selection Variables

Selection variables are declared in their own section labeled "Variables". Each variable is just a name declaration that represents a boolean value of either true or false. They can be turned on/off externally by both the AI system and the behaviors themselves. They are conceptual switches that are used to select the current behavior state of an AI using a given BHS. It is also possible to pass a default value (though by default the values are all set to false).

For the above example, the selection variable section might look like:

```

`
<Variables>
  <Variable name="AwareOfSound" default="false"/>
  <Variable name="AwareOfEnemy"/>
</Variables>

`

```

##
Signal Variables

Signal Variables provide a way to directly modify the variable state of an AI instance's BHS. They are received from the AI system and turn on/off variables declared in the Variables section. Three parameters must be defined for each signal variable. They must be given a name that matches the expected signal name from the AI system, the name of the selection variable to be altered, and the value to set the selection variable to.

For the above example, the signal variable section might look like:

```

`
<SignalVariables>
  <Signal name="OnHearSound" variable="AwareOfSound" value="true"/>
  <Signal name="OnEnemySeen" variable="AwareOfEnemy" value="true"/>
  <Signal name="OnNoTarget" variable="AwareOfSound" value="false"/>
  <Signal name="OnNoTarget" variable="AwareOfEnemy" value="false"/>
</SignalVariables>

`

```

##
Leaf Translations

Leaf translations allow for a cleaner and more robust tree definition. They provide a mapping of generic behavior names (that are potentially shared), to archetype specific behaviors. These are not necessary unless using a shared selection tree block, which will be discussed later in this document. However, they can be used to keep your tree definition more human readable as well.

For the above example, the leaf translations section might look like:

```

`
<LeafTranslations>
  <Map node="Idle" target="GruntIdle"/>
  <Map node="Investigate" target="GruntInvestigate"/>
  <Map node="Attack" target="GruntAttack"/>
</LeafTranslations>

`

```

As noted this section is not necessary, but for the purposes of this example it will be assumed. This does change how the selection tree section will look.

##
The Selection Tree

This section uses the above 3 components to define the available behaviors for an AI and how the correct one is chosen each time the tree is evaluated. As suggested by the name, the behaviors are organized into a tree structure. Each tree node represents a grouping of behaviors and the conditions needed to allow evaluation of child nodes. Each leaf node represents a reference to a specific behavior and the conditions needed to pass for it to be selectable.

Priority of the nodes is determined by order in the file. So if two or more nodes would match the current selection variable state, the the first one encountered as laid out in the tree will be chosen.

For the above example, the selection tree section might look like:

```

`
<Priority name="Root">
  <Priority name="Combat" condition="AwareOfEnemy">
    <Leaf name="Attack"/>
  </Priority>
  <Leaf name="Investigate" condition="AwareOfSound"/>
  <Leaf name="Idle"/>
</Priority>

`

```

There are a few noteworthy things to point out from the above sample. The leaf names must match the behavior names. Either the raw behavior name (GruntAttack), or the mapped name (Attack). In the sample, notice that "Attack" is a leaf for a behavior grouping called "Combat". It only has one leaf, but more could be added later. For any of those leaves to be evaluated, the selection variable "AwareOfEnemy" must be true. Since "Attack" is higher in the file, if it passes the conditions it will be selected even if "Investigate" is selectable as well. The last point to make is that the "Idle" behavior has no conditions attached to it. This makes it the default behavior. If nothing else is evaluated to be valid first, then "Idle" will be chosen.

There is no limit on the number of variables, mappings, or behavior entries that can be defined in the BHS.

##
Behavior Selection Tree Evaluation

A solid understanding of how the BHS is evaluated will help in understanding how to best design both the behaviors and the selection tree itself.

Like Behaviors, a BHS is not copied for each AI instance that uses it. Instead each AI instance gets a copy of the selection variables, which fully represents the selection state of an AI.

The tree is then evaluated with a set of selection variables to determine what state the corresponding AI should be in.

On each AI system update of an AI (many frames per second):

-
The AI's Selection Tree re-evaluates the AI's associated Selection Variables.

-
If the selected Behavior is the same as the current one, then nothing happens.

-
If the selected Behavior is different, then the AI calls the destructor of the current behavior.

-
The AI changes to the new behavior and...

-
The new behavior's constructor is called on the AI.
The selection variables associated with the AI are modified in a few ways.

-
The AI System creates new signals that are sent to the behavior system (e.g. The Perception system determines the AI can now see the player).

 ... The signals are received by the AI's BHS and processed as defined in the signal variable section.

 ... The AI's current behavior receives the signal and directly modifies a selection variable.

-
The AI System itself directly modifies an AI's selection variable. (This is not commonly desired/needed)
As an example, a behavior can contain conditional logic to change behaviors, depending on the current environment.

Say for example our behavior called "Investigate" had a signal method "OnSoundHeard" that would be received from the AI System when a new sound was registered by the AI's perception.

```

`
OnSoundHeard = function( self, entity, fDistance )
  if (fDistance < 5) then
   AI.SetBehaviorVariable(entity.id, "AwareOfEnemy", true);
  end
end,

`

```

So if a new sound is generated that's extremely close to the AI, it will update the behavior state to go to "Attack" even though it hasn't visually confirmed the target yet.

Of note, changing behaviors is not particularly expensive, but if the AI is constantly swapping behaviors it may make it harder to debug and follow. When designing appropriate behaviors, try not to think about behaviors being individual actions. Think of them more as states providing related actions. For instance a FireFromCover behavior might contain actions to duck behind cover for some time, to peek over the cover and check for targets, to blind fire, and to stand up and fire directly.

##
Sharing Behavior Blocks between Behavior Selection Trees

There is no STRONG relationship between a BHS and the behaviors it uses. Behaviors can be freely reused between Selection Trees, as long as the behavior sensibly works with a particular AI type.

See the documentation on Behaviors and GoalPipes for more information on proper Behavior setup.

To aid in sharing base behaviors, there is also the possibility to declare Behavior "Blocks". These go in their own XML file(s) in the same directory (or subdirectories) as the BHS files.

To demonstrate with the same example, there might be a file called
**
Common.xml
**
 sitting in the base Selection Tree folder.

It might look like this:

```

`
<Blocks>
  <Block name="CommonVars">
    <Variable name="AwareOfSound"/>
    <Variable name="AwareOfEnemy"/>
  </Block>

  <Block name="CommonSignalVars">
    <Signal name="OnHearSound" variable="AwareOfSound" value="true"/>
    <Signal name="OnEnemySeen" variable="AwareOfEnemy" value="true"/>
    <Signal name="OnNoTarget" variable="AwareOfSound" value="false"/>
    <Signal name="OnNoTarget" variable="AwareOfEnemy" value="false"/>
  </Block>
</Blocks>

`

```

The files can contain any number of "Blocks", and each "Block" is completely separate from all other "Blocks". They are meant to be modular and loaded in BHS files as needed. To include a "Block" within a BHS you add a reference in the appropriate section.

For instance, our selection variable section could be replaced with the much more terse:

```

`
<Variables>
  <ref name="CommonVars"/>
</Variables>

`

```

and the signal variable section with:

```

`
<SignalVariables>
  <ref name="CommonSignalVars"/>
</SignalVariables>

`

```

In this way you could mandate a certain set of Selection Variables and Signal Variables across all of your AI types. Using this formalism should keep your behavior files cleaner and more manageable.

Lets revisit the Leaf Translations concept from earlier in this guide. Say we define another logic block as such:

```

`
<Block name="CommonBehaviorTree">
  <Priority name="CommonRoot">
    <Priority name="Combat" condition="AwareOfEnemy">
      <Leaf name="Attack"/>
    </Priority>
    <Leaf name="Investigate" condition="AwareOfSound"/>
    <Leaf name="Idle"/>
  </Priority>
</Block>

`

```

We could then replace the Selection Tree portion of our Grunt BHS with:

```

`
<Priority name="Root">
  <Ref name="CommonBehaviorTree"/>
</Priority>

`

```

Now because we have the leaf translations section which maps generic names to archetype AI specific behavior names, everything will still work. So you could share a behavior tree among a bunch of different AI types, but still have unique behaviors assigned to each leaf in the tree. To demonstrate, we might have another AI type called "Alien". Say we expect the "Alien" to share the same basic behavior types. We could duplicate the BHS from the "Grunt" and replace the Leaf Translation section with:

```

`
<LeafTranslations>
  <Map node="Idle" target="AlienIdle"/>
  <Map node="Investigate" target="AlienInvestigate"/>
  <Map node="Attack" target="AlienAttack"/>
</LeafTranslations>

`

```

Assuming those behaviors exist, the "Alien" AI type would be ready to go, and still have unique AI behavior handling.
