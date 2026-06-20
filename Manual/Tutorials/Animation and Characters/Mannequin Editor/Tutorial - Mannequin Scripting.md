# Tutorial - Mannequin Scripting

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/23308486
- Page ID: 23308486
- Breadcrumb: Tutorials > Animation and Characters > Mannequin Editor* > Tutorial - Mannequin Scripting
- Parent: Mannequin Editor*

## Content

### Overview

In this tutorial, we will look at how we can setup a mannequin object in a level and use flow graph nodes to script its behavior. We will specifically look at:

- [Creating a Mannequin object.](Tutorial%20-%20Mannequin%20Scripting.md#Tutorial-MannequinScripting-CreatingaMannequinobject)
- [Playing some fragments through Flowgraph.](Tutorial%20-%20Mannequin%20Scripting.md#Tutorial-MannequinScripting-PlayingFragmentsThroughFlowGraph)
- [Setup a sequence of fragments smoothly transitioning from one to the other.](Tutorial%20-%20Mannequin%20Scripting.md#Tutorial-MannequinScripting-SettingUpaTransition)
- [Setting up synchronized animations.](Tutorial%20-%20Mannequin%20Scripting.md#Tutorial-MannequinScripting-SettingUpaSynchronizedAnimation)

As a starting point for this tutorial, we will only be using an empty Mannequin setup, located in the folder: `<GameFolder>/Animations/Mannequin/ADB/mannequin_workshop/mannequin_workshop_start/`

This setup includes all the required Mannequin files, though they are mostly empty for now. We will be adding some new fragments through the tutorial. For reference, the completed tutorial files can also be found under the mannequin_workshop_finished folder.

Requirements
It is recommended to be a bit familiar with the Mannequin editor before performing this tutorial. If you are completely new to Mannequin, please look at the [Mannequin Editor Tutorial](Mannequin%20Editor%20Tutorial%201%20-%20Preview%20Setup%2C%20Fragments%20and%20Saving.md) first.

### Creating a Mannequin Object

Mannequin will typically be used to drive complex characters, and it is likely that the creation of those characters is mostly going to be code-driven.

It is still possible though to use the "Mannequin Object" entity type to create a character which can host a Mannequin setup, and therefore support any feature you would be able to use on any Mannequin-driven character.

To do so, just create a new Entity of type **Anim/MannequinObject** in your level.

![Image](https://www.cryengine.com/docs/static/attachments/23998516)

In the entity properties, you will need to assign your character a Mannequin controller definition file, an animation database, and a model. We will use the following assets:

- `Animations/Mannequin/ADB/mannequin_workshop/workshop_setup_start/workshop_controller_def.xml`
- `Animations/Mannequin/ADB/mannequin_workshop/workshop_setup_start/workshop_adb.adb`
- `Objects/characters/human/sdk_player/sdk_player.cdf`

The object properties should look like this at this point:

![Image](https://www.cryengine.com/docs/static/attachments/23998518)

In the level editor viewport, you should now see the character staying in T pose. Please note that even though no animation is playing, the character at this point does have a proper Mannequin setup.

This means, that we can for instance use the mn_debug CVar to see the Mannequin state of our entity.

Typing **mn_debug MannequinObject1** in the console, we should now see the basic Mannequin debug info showing up on screen:

![Image](https://www.cryengine.com/docs/static/attachments/23998517)

You can see that even though no fragment is playing, the "Fullbody" and "Upperbody" scope are properly bound to a character, and that the "Slave" scope is currently inactive.

### Playing Fragments Through FlowGraph

Now that we have our Mannequin character properly setup in a level, we will start creating and playing some fragments on him.

Let's open the Mannequin editor and load the relevant preview setup: `<GameFolder>/Animations/Mannequin/ADB/mannequin_workshop/workshop_setup_start/workshop_preview.xml`

Note that currently, this setup is completely empty:

![Image](https://www.cryengine.com/docs/static/attachments/23998513)

### Creating a Fullbody Fragment

The first thing we will do now is create a simple "Idle" FragmentID. We will assign it only the "Fullbody" scope, so make sure to uncheck the "Upperbody" and "Slave" ones.

![Image](https://www.cryengine.com/docs/static/attachments/23998510)

![Image](https://www.cryengine.com/docs/static/attachments/23998511)

We will now add a simple fragment to this new FragmentID. We will only create one animation layer with one single clip, and play the "relaxed_tac_idle_nw_3p_01" animation. The fragment should look like this:

![Image](https://www.cryengine.com/docs/static/attachments/23998509)

We are now done with the Mannequin setup for this first step. We will now take care of setting up a simple FlowGraph which will take care of playing the fragment we just created.

To do so, go back to the level editor, right click on our character, and select "Create Flow Graph". The name of the graph is not important for this tutorial.

![Image](https://www.cryengine.com/docs/static/attachments/23998508)

In our graph, we will then use the Actor:PlayMannequinFragment node to request the "Idle" fragment we just created.

We will connect it to a "Game:Start" node so that it automatically gets triggered when we start the game. The graph should look like this:

![Image](https://www.cryengine.com/docs/static/attachments/23998514)

To see the graph in action, we can now either jump in game, or just toggle the "AI/Physics" button. Doing so, you will now see our character playing the proper fragment.

![Image](https://www.cryengine.com/docs/static/attachments/23998505)

![Image](https://www.cryengine.com/docs/static/attachments/23998512)

We can now see that our Idle fragment is correctly playing on the Fullbody scope.

### Creating an Upperbody Fragment

Similarly to how we create a fullbody fragment, we will now create an upperbody one. To do so, let's go back to the mannequin editor, and create a new FragmentID which we're going to call "Upperbody_Detail".

Let's make sure that it only uses the "Upperbody" scope in the FragmentID creating dialog:

![Image](https://www.cryengine.com/docs/static/attachments/23998532)

Again, we will now create a simple fragment with only one animation clip. Let's use "relaxed_tac_lookaround_rifle_add_3p_01".

![Image](https://www.cryengine.com/docs/static/attachments/23998531)

Going back to our Flowgraph, we will now also request this new FragmentID with an **Actor:PlayMannequinFragment** node.

Just for the sake of testing, we will also add some delays to start and stop this upperbody fragment while the fullbody one is still running. The flowgraph should then look something like this:

![Image](https://www.cryengine.com/docs/static/attachments/23998530)

Looking in game, we now see that after a couple of seconds, both the fullbody and upperbody fragments will be playing simultaneously.

After five seconds, the upperbody animation will stop, but the fullbody one will continue.

![Image](https://www.cryengine.com/docs/static/attachments/23998533)

### Setting Up a Transition

Now that we've seen how to independently play some fragments on different scopes (i.e. FullBody and Upperbody), we're going to have a look at how to play a sequence of fragments, and how to setup a transition between them. To do so, we will create a new FragmentID, named "OfficerListen", playing only on the Fullbody scope. Once again, we will there put one single animation clip pointing to the "relaxed_tac_officerlistening_nw_3p_01" clip. Let's now update our FlowGraph so that we play this fragment after the Idle one we've already setup. At this point, we don't need the UpperBody fragment anymore, so we'll just remove it from the graph.

In FlowGraph, you will notice that if you request the newly created "OfficerListen" FragmentID after the Idle one, nothing will happen by default, and the character will keep playing the "Idle". This is because by default, both requests will have the same priority (0), and "Idle" is looping, meaning that it will not automatically stop unless we request something with a higher priority. To cope with this, we are simply going to assign "OfficerListen" a priority of 1, to make sure that the "Idle" gets interrupted. The FlowGraph should then look like this:

![Image](https://www.cryengine.com/docs/static/attachments/23998519)

Jumping in game, you will now see that both fragments get played in a sequence, as one would expect. At this point though, we might want to tweak the transition between those two fragments. Let's say that when going from "Idle" to "OfficerListen", we always want to play a salute animation. This can easily be achieved by setting up a transition in the Mannequin editor.

For more detailed instructions on how to use the transition editor, please refer to [Mannequin Editor Tutorial 3 - Transitions](Mannequin%20Editor%20Tutorial%203%20-%20Transitions.md).

Let's now switch to the Mannequin transition editor. There, let's create a new transition, going from Idle to OfficerListen.

![Image](https://www.cryengine.com/docs/static/attachments/23998528)

In this transition, we will simply add an intermediate salute animation between the "idle" and "listen" animation clips. Let's use "relaxed_tac_idle_saluteofficer_rifle_3p_01". The transition should then look like this:

![Image](https://www.cryengine.com/docs/static/attachments/23998527)

Jumping back in game, you should now see that when the "OfficerListen" FragmentID is request, the transition we've just setup is correctly played. In the in-game Mannequin debug rendering, you can see that the transition animation is indeed queued:

![Image](https://www.cryengine.com/docs/static/attachments/23998529)

### Setting Up a Synchronized Animation

So far, we've seen how to play fragments on different layers through FlowGraph. We will now look at how we can setup some synchronized animations in Mannequin.

The first thing to do is to setup the synchronized fragments in Mannequin. Let's jump to the editor, and create a new FragmentId called "Synced_Animation", running on the "FullBody" and "Slave" scopes:

![Image](https://www.cryengine.com/docs/static/attachments/23998524)

We now need to create one fragment for each scope. To differentiate them, we need to set the "scope_slave" tag on the slave one.

We also need to setup the "context_slave" tag on both. This tag will be used to let the game and editor know which character we want to use for the slave. In the end, the fragments should look like this in the Fragment Browser:

![Image](https://www.cryengine.com/docs/static/attachments/23998523)

When selecting one of those fragments, you should now see two characters in the Mannequin editor viewport.

However, they will both be at the exact same location by default, making it very inconvenient to visualize our work. Let's change this by editing the preview context:

![Image](https://www.cryengine.com/docs/static/attachments/23998506)

In there, you will see the different contexts we have. The one we're looking at is the slave one.

Let's double-click on it, and give it an offset in both position and rotation so that it stands in front of the master:

![Image](https://www.cryengine.com/docs/static/attachments/23998507)

The position and rotation values that we are setting in this window only impact the editor preview. If you want your characters to strictly align in the game when you play your fragment, you would need to for instance use a procedural clip to move your chararacters in position when starting the animation.

Once this is done, we should now see both characters facing each other in the editor whenever editing a fragment with the "context_slave" tag set:

![Image](https://www.cryengine.com/docs/static/attachments/23998520)

We can now easily edit the actual content of the fragments. Let's setup a quick scene where one character is saluting the other and then looking around.

Meanwhile, the second character will stand idle, and have a drink as soon as the first one turns around.

We'll use the following animations: "stand_tac_idle_salute_rifle_3p_02", "relaxed_tac_idle_look180_rifle_3p_01", and "relaxed_tac_idle_drink_rifle_3p_01".

The fragment setup should look like this in the end:

![Image](https://www.cryengine.com/docs/static/attachments/23998522)

We're basically done with the Mannequin setup. Now, we need to update our level and FlowGraph to play this scene. Let's switch back to the level editor and create a new MannequinObject refering to the same action controller, animation database and model files.

The only thing we have left to do is enslave this character to the first one in our script, and then request the "Synced_Animation" FragmentID.

When requesting the FragmentID, it is also important not to forget to set the "context_slave" tag. This can easily be done using the EnslaveCharacter and PlayMannequinFragment nodes.

In the end, the graph for the "master" character should look like this:

![Image](https://www.cryengine.com/docs/static/attachments/23998521)

When starting the game, we should now see both characters performing the synchronized fragments we've just setup:

![Image](https://www.cryengine.com/docs/static/attachments/23998525)

[Creating a Mannequin Object](#creating-a-mannequin-object)[Playing Fragments Through FlowGraph](#playing-fragments-through-flowgraph)[Creating a Fullbody Fragment](#creating-a-fullbody-fragment)[Creating an Upperbody Fragment](#creating-an-upperbody-fragment)[Setting Up a Transition](#setting-up-a-transition)[Setting Up a Synchronized Animation](#setting-up-a-synchronized-animation)
