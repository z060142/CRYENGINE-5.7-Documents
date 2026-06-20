# Behavior Scripts (Obsolete Version)

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/23306486
- Page ID: 23306486
- Breadcrumb: CRYENGINE Engine Code > Engine Modules > CryAISystem > Obsolete AI Documentation > Obsolete AI Scripting Documentation > Behavior Scripts (Obsolete Version)
- Parent: Obsolete AI Scripting Documentation

## Content

##
Overview

All enemies have to have at least ONE behavior script before they can do anything in the game. The behavior script is the final authority that defines what a particular character has to do when something in his environment changes--like he sees a player, or he hears a sound or he receives a signal from a group member. All these environment changes translate to callback functions in the behavior script, and then it's the script's responsibility to define what the character's response will be.

When you place an character in the CryEngine Sandbox, it will come with some default behavior. But, if the character had NO behavior whatsoever, he will at minimum follow any targets he selects with his eyes, but he will just stand there. This means that target acquisition and processing is still working for this character, he just doesn't know what to do when he perceives a particular target.

##
Setting Up the Behavior

In the CryENGINE Sandbox, the behavior for a particular character can be configured using the properties rollout that appears when the character is selected. The behavior is selected by clicking on the
**
Ai behaviour
**
 property and selecting it from the behavior selection dialog. At this time, we are not interested in any of the predefined behaviors that can be selected in this dialog. In order to facilitate better introduction to the concept of the behavior, it's important to start with an empty behavior.

A character configured like this will never move or do anything of significance. The lowermost layer of the AI Object (sitting deep within C++ code) will still work, and that means that the character will still get visual and audible targets, but will just look at them and not do anything. If you try to move around this character in the editor's game mode, he will follow the player character by looking at him. Experiment with going closer and further from the character, as well as going to third person (F1) and crouching, proning or jumping in close proximity to the character. Observe how he will follow with his eyes, head and upper torso the position of the head of the player character.

The reason why this character is not doing anything is because when the AI system notifies him that he is seeing a player target, there is no logic selected to determine what he should do in response to that. That is EXACTLY what the behavior should do; provide the system with instructions on what to do when something in the environment changes.

To select which behavior a particular character uses, the behavior name should be typed into the appropriate property (
**
Ai behaviour
**
).

##
Creating a Simple Behavior

The behavior needs to be defined as a LUA table. There is a global LUA table called
**
AIBehaviour
**
. This table contains (as its sub tables) all the behaviors that the game can use and that can be specified in the behavior property for an character. To be able to use a behavior in the game, it has to be registered as a sub table to this table.

The file
*
Scripts/AI/Behaviors/AIBehaviour.lua
*
 lists all possible behaviors in the game. Ignoring the finer details of this file (like the existence of two sub tables
**
AVAILABLE
**
 and
**
INTERNAL
**
) we can add a new behavior to this table. For illustration, we can add the following line in the
**
AVAILABLE
**
 sub table:

```

`
Prototype = "Scripts/AI/Behaviors/Personalities/Prototype.lua";

`

```

This line can be entered anywhere in the
**
AVAILABLE
**
 sub table, but for the sake of argument, lets say we added it as the very first line after the
**
AVAILABLE
**
 = line. The script for this behavior EXISTS already (in the directory that you specified with the line you just added--look for it), but it is not selecting any response to any incoming event. It does however contain all the important events that can happen during execution of the game. So the next step is to write some logic inside them in order to make the enemy that uses this behavior do something. Don't forget to save the
**
AIBehaviour.lua
**
 after this and reload the scripts.

But first, let's look at the way events are described in the behavior in more detail. Looking at a part of the events in the Prototype.lua file, we might see something like this:

```

`
OnNoTarget = function( self, entity )
  -- called when the AI stops having an attention target
end,

OnEnemySeen = function( self, entity, fDistance )
  -- called when the AI sees a living enemy
end,

OnGrenadeSeen = function( self, entity, fDistance )
  -- called when the AI sees a grenade
end,

`

```

The first thing to notice here is the fact that all of these
**
events
**
 are nothing more than functions with arguments. The name of the function is the name of the event, and the arguments (for most of the events) are always the same:

1.
**
self
**
 – This argument represents the instance of the behavior itself. This sounds more complicated than it actually is. It basically provides a way inside the function to refer to something that is contained within an instance of the behavior. For example, if I would write

```

`
self:OnEnemySeen(entity, fDistance)

`

```

inside the OnEnemySeen function, then I would call the function I am in from inside it, making in essence a recursive call. Notice that when I use the colon ( : ) form of calling a function, the first argument
**
self
**
 is implicitly passed – just like the this implicit argument in C++ classes. If I were to use the ( . ) method of calling the function, then I would have had to specify the
**
self
**
 argument explicitly, like this:

```

`
self.OnEnemySeen(self, entity, fDistance)

`

```

This is a strictly CryEngine behavior of Lua and its only mentioned here to avoid confusion about using the colon to call a function.

2.
**
entity
**
 – Since behavior tables are loaded once and not reused, that means that ALL AI enemies reuse the same table. In order to be able to determine which entity is currently being processed, it's being passed as an argument to every event function handler.

3. Different functions can have different arguments after the initial two. While most of them don't, we can even see in the OnEnemySeen function that there is a third argument – the distance to the player target. The appendices contain a complete list of all system defined events and all arguments that are passed to them.

The behavior that was registered can then be selected from the behavior selection dialog, or just typed into the appropriate property of the entity. For the sake of clarity, we can manually type the behavior
**
Prototype
**
 in the
**
behaviour
**
 property – but to make sure that the behavior table script is reloaded, don't forget to reload the scripts in the editor (consult editor documentation on how to do that).

##
Responding to an Event in the Behavior

Now that the prototype behavior is set up, we can start experimenting with responding to some events that occur in the course of playing the game. In order to respond to any particular event, all we have to do is write some logic in the appropriate function of the behavior – for example if we wanted to do something when the enemy sees the player, we would write something in the
**
OnEnemySeen
**
 function of the behavior.

As an exercise, we will output some text when the enemy sees the player. This text will be output in the HUD, so you can confirm that the HUD is visible in the game mode of the editor by typing
**
cl_display_hud 1
**
 in the console.

Next, lets replace the OnEnemySeen function with the following version (the new parts are highlighted):

```

`
OnEnemySeen = function( self, entity, fDistance )
  -- called when the enemy sees a living player
  Hud:AddMessage("I SEE YOU");
end,

`

```

Now, every time the enemy sees you, it will output this text to the console. To test this, save the new version of Prototype.lua and reload scripts in the editor. Then go into game mode and walk around the enemy until you see the text displayed in your HUD.

There are a few things to notice here – first of all notice that the event function is only called ONE time when the enemy actually perceives the player for the first time – NOT every frame afterwards. This is done to minimize the potentially very expensive script call when it's not necessary and when the script actually had a chance to act upon a change in the environment. The second thing to notice is that the enemy does NOT see you right away, but only after the stealth-o-meter rises to maximum value. This is normal operation.

The events are called ALWAYS when the appropriate event happens, even if multiple events happen at very close time intervals. To illustrate this, let's try to handle another system event that happens during the playing of the game – the OnThreateningSoundHeard event:

```

`
OnThreateningSoundHeard = function( self, entity )
  -- called when the enemy hears a scary sound
  Hud:AddMessage("I HEAR SOMETHING!!");
end,

`

```

To test this, enter game mode in a position behind the enemy that uses this behavior, and then shoot in the air. This will create the situation in which the enemy will hear the gunshot, thus receive the event that we just enhanced. After hearing the shot, he will turn to face the direction of the shot and consequently see the player. Then he will receive the usual
**
OnEnemySeen
**
 event.

There is no limit on what you can put as processing logic for a particular event. In the example we used a simple HUD message, but any kind of logic can be performed here. Having access to all global objects in the Lua state means you can affect the rendering, physical state of the world, play sounds or music or a particular animation, or send a message to another entity. This makes scripting AI response quite simple and quite powerful.

However, here we are not interested in affecting the world or indeed anything else than the entity that is executing the current behavior, since that is what is the most interesting. To affect the entity and tell him what to do when a certain event is triggered, we need to get familiar with another concept in the AI system – goal pipes.
