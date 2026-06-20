# Behavior Scripts

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/23306479
- Page ID: 23306479
- Breadcrumb: CRYENGINE Engine Code > Engine Modules > CryAISystem > Obsolete AI Documentation > Obsolete AI Scripting Documentation > Behavior Scripts
- Parent: Obsolete AI Scripting Documentation

## Content

This article is for CRYENGINE 3.4 or earlier. The Behavior Selection Tree and old-style behaviors was deprecated in favor of the Modular Behavior Tree in CRYENGINE 3.5 and beyond.

##
Overview

In order for AI to respond to the player and the environment they must have assigned behaviors. How these behaviors are arranged and selected is covered in the "Behavior Selection Trees" guide; this guide will cover how to define an individual behavior and how they integrate with the AI system. The Behavior script contains the logic on how a particular AI should react to Stimuli under current circumstances; stimuli like seeing a player, hearing a sound, receiving a signal from a group member, or a grenade landing at its feet.

All these environment changes translate to signals processed as methods of the behavior table. Therefore, the AI's current behavior has full authority over its responses. Beyond just responding to Stimuli, the behavior maintains the AI's response state. So once an AI enters a behavior, it will continue to dictate all AI actions until another behavior is selected.

Behaviors are defined through LUA script tables, and can inherit functionality from parent base behaviors. This inheritance provides considerable flexibility to make multiple unique AI types while maintaining a lot of shared behavior.

If an AI is not assigned a valid Behavior Selection Tree with at least one valid default behavior, the AI will have NO behavior whatsoever. The AI's perception handler functions independently and will still send signals, but the ONLY thing the AI will be able to do is turn towards its current Attention Target.

##
Creating a Behavior

AI are assigned behaviors through a Behavior Selection Tree. The tree is added via the "BehaviorSelectionTree" property under the AI archetype's "ClassProperties" field in CryENGINE Sandbox. Though the tree associates the behaviors with an AI, the Behaviors must be defined individually.

A behavior is defined as a LUA table in the base game directory under
`
\Scripts\AI\Behaviors
`
. When adding a behavior or making a change to an existing one, reloading scripts in Sandbox will reload it without needing a restart.

As an example, lets make a new behavior called "Idle" that inherits from another behavior table named "AIBaseBehavior".

The behavior table starts off with the following declaration:

```

`
local Behavior = CreateAIBehavior("Idle", "AIBaseBehavior",
{
  TABLE METHODS...
}

`

```

The second argument to CreateAIBehavior is only necessary if the behavior is meant to inherit from a parent behavior. This inheritance is not necessary, but it does insure that the new behavior has some base set of supported functionality.

##
Constructors

All behaviors
**
MUST
**
 have a Constructor method, and optionally should have a Destructor method. The constructor method is critical, as it is called
**
EACH
**
 and
**
EVERY
**
 time the AI switches to the behavior. It should take care of initializing any state on the entity, and start the AI's actions which will be performed while running the behavior.

For instance our Idle behavior constructor might look like:

```

`
Constructor = function (behavior, entity)
  if ( entity:IsActive() ) then
    entity:SelectPrimaryWeapon()
  end
end,

`

```

##
Destructors

The destructor on the other hand is called whenever leaving the behavior and switching to a new one. It might clear entity state, or save some new state for a future call back into this behavior. Say for example we want to track the last position that the AI was idle:

```

`
Destructor = function(behavior, entity)
  entity.lastIdlePosition = entity:GetPos()
end,

`

```

##
Signal support

Beyond that its also possible to integrate the behavior with AI System signals (otherwise known as events). Some examples might be:

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

AI System
**
events
**
/
**
signals
**
 functions with arguments. The name of the function is the name of the event, and the argument list is as follows:

1.
**
self
**
 – This argument is a reference back to the behavior table itself. This allows a method of a behavior table, to call another method of the behavior as it constantly holds a reference to itself.

For example:

```

`
ProcessVisual = function( self, entity, fDistance )
end,

OnEnemySeen = function( self, entity, fDistance )
  -- called when the AI sees a living enemy
  self:ProcessVisual(entity, fDistance)
end,

`

```

The OnEnemySeen function calls the ProcessVisual method of the same behavior. Notice that when using the colon ( : ) form of calling a method, the first argument
**
self
**
 is implicitly passed – just like the this implicit argument in C++ classes. If the ( . ) method is used to call a method, then the
**
self
**
 argument must be explicitly passed, like this:

```

`
self.OnEnemySeen(self, entity, fDistance)

`

```

This is a strictly CryENGINE behavior of Lua and is only mentioned here for clarity's sake.

2.
**
entity
**
 – Behavior tables are not instanced, that means that ALL AI enemies reuse the same table. Therefore the Behavior tables are not meant to share AI state, and any necessary state should be stored on the entity table itself. In order to be able to determine which entity is currently being processed, the entity table is passed as well. On a related note, if there is any behavior related state that needs to be serialized into and out of a save game, then it should be stored in the entity's AI sub-table. That way the data will automatically be included with the save game.

For instance:

```

`
ProcessVisual = function( self, entity, fDistance )
 entity.AI.lastVisualDistance = fDistance
end,

`

```

3.
**
Additional
**
 arguments are passed as data values needed to process the passed signal. As exhibited, the OnEnemySeen function has a third argument – the distance to the player target. The appendices contain a complete list of all system defined events and all arguments that are passed to them.

##
Additional methods

Beyond the above components, its up to the designer to add what they want to a behavior. The other way in which behaviors control AI state is by goal pipes which can call back into the current behavior. This is discussed in another guide "Behaviors and Goal Pipes".

##
Example of Signal Handling

Lets setup a real prototype "Idle" behavior. Remember, this will need to be added to a valid "Behavior Selection Tree" which will need to be assigned to the AI that is used for testing.

The "Idle" behavior can be quite simple for demonstration purposes:

```

`
local Behavior = CreateAIBehavior("Idle",
{
  Constructor = function (behavior, entity)
    if ( entity:IsActive() ) then
      entity:SelectPrimaryWeapon()
    end
  end,
}

`

```

This behavior will not do anything other than select their weapon and stand there, but it allows us to experiment with responding to some AI system signals. In order to respond to any particular event, all we have to do is create logic to handle the event inside the behavior as described earlier in the guide – for example if we wanted to do something when the enemy sees the player, we would write something in the
**
OnEnemySeen
**
 function of the behavior.

As an exercise, we will output some text when the enemy sees the player. This text will be output in the HUD, so you should confirm that the HUD is visible in the game mode of the editor by typing
**
g_showhud 1
**
 (or
**
cl_hud 1
**
) in the console.

Next, lets add the OnEnemySeen function:

```

`
OnEnemySeen = function( self, entity, fDistance )
  -- called when the enemy sees a living player
  Hud:AddMessage("I SEE YOU");
end,

`

```

Now, every time the enemy sees you, it will output this text to the console. To test this, reload scripts and go into game mode. Walk around the enemy until you see the text displayed in your HUD.

Notice that the event function is only called ONE time when the enemy first perceives the player – NOT every frame afterwards. This is done to minimize unnecessary script calls (which can be expensive) by assuming only state changes need to be registered by the behaviors. Once the AI starts seeing the player, it assumes it keeps seeing it until told otherwise. The other thing to notice is that the enemy does NOT see you immediately, but only after the stealth-o-meter rises to maximum value. This is normal operation and can be edited through the C++ in the game dll.

The events are called without any knowledge of state in the behavior. To illustrate this, let's handle another system event that happens during gameplay – the OnThreateningSoundHeard event:

```

`
OnThreateningSoundHeard = function( self, entity )
  -- called when the enemy hears a scary sound
  Hud:AddMessage("I HEAR SOMETHING!!");
end,

`

```

To test this, enter game mode in a position behind the AI that is idle, and then shoot in the air. The AI will hear the gunshot, and react using the functionality in OnThreateningSoundHeard. After hearing the shot, the AI will turn to face the direction of the shot and consequently see the player. This will trigger the
**
OnEnemySeen
**
 event.

Almost any kind of logic can be performed through LUA behavior hooks. Having access to all global objects in the Lua state means you can affect the rendering, physical state of the world, play sounds or music, or particular animations. This makes scripting AI responses simple and at the same time quite powerful.

After playing around with these basic concepts, its recommended to read the guides on Goal Pipes and how to integrate them into behaviors.
