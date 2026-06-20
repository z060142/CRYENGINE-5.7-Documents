# Character Scripts

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/23306482
- Page ID: 23306482
- Breadcrumb: CRYENGINE Engine Code > Engine Modules > CryAISystem > Obsolete AI Documentation > Obsolete AI Scripting Documentation > Character Scripts
- Parent: Obsolete AI Scripting Documentation

## Content

This article is for CRYENGINE 3.4 or earlier. The Behavior Selection Tree, old-style behavior and character scripts were deprecated in favor of the Modular Behavior Tree in CRYENGINE 3.5 and beyond.

### IMPORTANT!

You are encouraged to use, rather than Character Scripts, which are discussed here.

But if you are still using Character Scripts, please **DON'T FORGET TO ADD THE FOLLOWING LINE AT THE VERY BEGINNING OF EVERY CHARACHER LUA FILE:**

– AICharacter: CharacterName [INTERNAL]

("INTERNAL" means this character will *not* be shown in the list of characters to select in the Editor.)

For example, *Boat.lua:*

```
-- AICharacter: Boat
```

*Player.lua*

```
-- AICharacter: Player INTERNAL
```

### Overview

When making a separate behavior script for every state that the enemy can be in (idle, alert, attack) there must be a way to determine the following important properties:

- Which behavior is the CURRENT behavior? All incoming game events have to be handled in the current behavior by default. Thus, the current behavior has to be defined at all times.
- What needs to happen in order for the current behavior to change? There must be a set of well defined rules that indicate how the behaviors change. For example, if the enemy was in the idle behavior, and he saw the player, then he needs to move in the attack behavior. In this case, the current behavior is the idle, the event that triggers the change is the seeing of the player, and the new behavior that needs to become the current one is the attack behavior.

This is exactly the purpose of the Character scripts. They define the actual rules for changing behaviors (states) and can be found in the Scripts/AI/Characters folder in your installation directory.

### The Character Script Concept

The character script is a completely separate script file from the behavior script. While it is possible to create enemies that have a single behavior script, when using multiple behaviors a valid Character script must be selected.

Selecting the character for an enemy entity to use is similar to selecting the behavior. The only difference is that the character property is not a **per instance** property for the enemies, but a ** per archetype** property. If you are not using archetypes, then it doesn't matter for you, but if you are then you have to access the archetype properties before you can change the character property.

The character property is called **AI character** (as can be seen in the picture). It also has an automatic selection dialog – just like the behavior. The entries listed in this dialog are all available characters that can be selected and that are properly registered within the system. Alternatively, the character name can by typed as a string, or the property can be an empty string in which case it means that the character is not necessary. This can be the case when a single behavior enemy is used.

The character scripts DO NOT contain any script logic. They are strictly data scripts and represent tables that are looked up periodically to determine whether the enemy should change behavior, and if so to determine to which behavior the enemy should change to.

A character script cannot be used in the game unless it has been registered inside the AICharacter.lua script file. This file is very similar to the AIBehavior.lua file in that it specifies the character script table name and the full path to the actual script that contains that table. This file can be found in the Scripts/AI/Characters directory, and this is how it might look like (this is not the entire file:

```
AICharacter = {

AVAILABLE = {
Cover    = "Scripts/AI/Characters/Personalities/Cover.lua",
Scout    = "Scripts/AI/Characters/Personalities/Scout.lua",
Swat    = "Scripts/AI/Characters/Personalities/Swat.lua",
Rear    = "Scripts/AI/Characters/Personalities/Rear.lua",
Sniper    = "Scripts/AI/Characters/Personalities/Sniper.lua",
...
```

The characters that are listed in the character selection dialog all come from this table and are enumerated every time the editor restarts or scripts are reloaded.

Conceptually, the character script can be represented graphically as a connected graph. The nodes of the graph are the behaviors and represent the states that the enemy can be in. The links of the graph are the events that need to happen in order for the enemy to move into another state (change behavior). A schematic like that has already been represented in the previous text, but here it is again for clarity:

In light of the new concepts of behavior and events that we introduced in the previous text, this picture is starting to make more sense now. All the nodes will in fact correspond 1:1 to an actual behavior Script, and all the links correspond to actual in-game events. And indeed, if you check the Scripts/AI/Behaviors/Personalities/Cover directory, you will find all of the scripts mentioned in the diagram.

From the diagram we can see that if the enemy was in the CoverIdle behaviour, and received the signal **interesting sound**, then he needs to change his current behavior into the CoverInterested behavior. All subsequent events that happen will be handled in the CoverInterested behavior until such an event happens that triggers a change out of this behavior and into another. Obviously the responses of the enemy in the ** interested** behavior would be slightly different than those in the ** idle** behavior.

A diagram like this was an essential part of planning the enemy behaviors in the game. Before doing anything else, each enemy had to have a diagram like this and that provided a mental image of how this enemy would behave under different circumstances. In other words, getting this diagram was the hard part – translating it into a character script was easy.

The character scripts contain entries in a very simple form. They contain a table for each of the behaviors that the enemy using the character can be possibly in. Each of those tables then contains a list of all events that can trigger a change into another behavior. Together with the actual events, the new behavior is also specified. So in general terms, a character script contains entries of the following form:

```
current behaviour = {
signal = next behaviour,
signal = next behaviour,
...
}
```

The current behavior represents any behavior that the enemy can be executing at some time – this corresponds to the nodes in the graph in the picture. The signal represents any incoming signals that can cause a change into another behavior – this corresponds to the links in the picture. And finally – the next behavior corresponds to the behavior that the enemy needs to switch to after receiving a given signal – this corresponds to the node that the followed link points to.

Let's illustrate this with an example taken directly from the Cover graph. Lets look at how the entry for the CoverInterested behavior would look like. We can see that if we receive the signal **No Target**, we need to switch to CoverIdle. This can be represented like this:

```
CoverInterested = {
OnNoTarget = "CoverIdle",
}
```

The **OnNoTarget** game event is the accurate name of the event that occurs when the enemy had a target previously, but now lost it. The diagram does not contain the actual names of the events, just their conceptual names.

Further, we see in the diagram that if we receive a signal that tells us that a target was seen, the behavior needs to change into CoverAttack. Similarly, if a threatening sound was heard, then the behavior needs to change into CoverThreatened. Let's add this into the entry:

```
CoverInterested = {
OnNoTarget               = "CoverIdle",
OnEnemySeen              = "CoverAttack",
OnThreateningSoundHeard  = "CoverThreatened",
}
```

The final behavior to add is the CoverAlert behavior. Here we see an interesting change, in that multiple events can cause the enemy to switch to this behavior. There is no limit on how many events can be used to change the behavior; it only depends on what the desired behavior logic is. Let's add all the remaining events to the table entry:

```
CoverInterested = {
OnNoTarget               = "CoverIdle",
OnEnemySeen              = "CoverAttack",
OnThreateningSoundHeard  = "CoverThreatened",
OnBulletRain             = "CoverAlert",
OnReceivingDamage        = "CoverAlert",
OnGrenadeSeen            = "CoverAlert",
HEADS_UP_GUYS            = "CoverAlert",
}
```

The last entry is very interesting, as it is not a signal that the system generates, but a custom signal created by the user. In this case it happens when one enemy from a group of more enemies sees any kind of disturbance, he sends the signal **HEADS_UP_GUYS** which causes the rest of his team to become alerted.

This means that ANY signal, system or user defined, can be used to trigger a change in behaviors. In this way, some really specific and powerful behaviors can be created.

There is no limit on the amount of behaviors that can be created for a particular enemy type and no limit on the amount of entries in the character table.

### The Mechanics of Changing Behavior

To be able to fully use the vast amount of customizability and power that the character scripts provide the user, a thorough understanding of how they work and where do they fit in the normal game loop is required. This small section will discuss exactly that.

Characters are loaded on startup, and each enemy that uses a particular character is given a reference to it. Character scripts, like behavior scripts are NOT copied for every enemy that wants to use them. There is one instance of a particular character that ALL enemies that use that character refer to.

Every time a game event arrives down to the logic layer (the script layer) in order to process the event handler, the system automatically checks if this particular event needs to trigger a change in the behavior. The actual order of events is as follows:

- An event arrives for processing
- The event function handler in the current behavior is called and the function is executed. This is important since regardless of whether this particular event will trigger a change in behavior or not – the contents of the handler function MUST be executed.
- The system checks whether a character script exists for this enemy
- The character script is analyzed if it contains an entry for the current behavior
- A search is performed inside the current behavior entry for the event that is processing
- If such an event is found, then the behavior is changed to the one specified with the event

Of course, how much of these steps will be actually executed depends on the result of some of the searches performed. There are some steps that are taken even after the final step indicated here, but they are discussed in detail later. The sequence of events as depicted here is the normal operation for an event that will actually trigger a change of behavior. It is perhaps useful to mention that a large majority of the events will not actually trigger a change.

It is also worth to mention that the same mechanism happens every time a user generated signal is processed. That enables behavior changing on user defined signals.

All the operations specified here are on a script level, and as such are not overly expensive. This means that generally changing the behavior around is not discouraged, but it may lead to problems in maintenance of an enemy character that has many rules of how if changes behaviors. For the sake of clarity and your own sanity, you should keep the behavior changing to the absolute minimum possible.

### Making a New Character

To make a new character, there are a few extra steps that need to be taken apart from actually typing the new script. And even in typing the script, there are some guidelines that need to be followed.

The new character script needs to create a NEW script table, and declare it as a sub table to the AICharacter script table. The AICharacter script table is always created and it is global. It should contain ALL character scripts that will be used in the game, and no character script will be loaded unless it is declared as a sub table to this table. The declaration is rather simple, and it should look something like this:

```
AICharacter.Cover = {
}
```

This declares the Cover script table under the AICharacter script table.

Doing just this will not make it possible to select the character for an enemy inside the game. In order to do that, the character has to be registered with the system and shown the location of the new script file so it can load it. This procedure is very similar to the registering of the behaviors. The file that keeps a list of all the registered characters and their corresponding script files is the AICharacter.lua file which can be found in the Scripts/AI/Characters folder.

The format of an entry in this file is very similar to the registration entry for behaviors. It basically lists the name of the script table together with the path to the script file in which this table is declared:

```
table name = path to script file relative to game root folder
```

These entries are declared in the AVAILABLE sub table of the AICharacter table. For example, if you have created a new character called InfantrySoldier and saved the file containing it in the file `Infantry.lua` in the Characters folder, then this is how its registration entry should look like:

```
AVAILABLE = {
...
InfantrySoldier = *Scripts/AI/Characters/Infantry.lua*,
...
},
```

A character registered in this way can then be specified by typing its table name into the character entity property for enemies, or it can be selected from the character selection dialog in the Sanbox.

### Relationship Between Behaviors and Characters

There is no STRONG relationship between characters and behaviors. In theory, you can freely mix and match any character with any behavior – so really there is no conceptual pairing between characters and behaviors.

In the loosest possible terms, a character only depends on the behaviors that it has specified inside it. For example, there is a big amount of shared behaviors that are then reused inside almost all of the characters. If a user would make a character that specifies that an enemy should go from CoverIdle into ScoutAttack when it spots an enemy – this is by no means an error situation – conceptually.

On the other hand, behaviors are not at all aware of the character existence. As far as the execution of the behavior goes – it is irrelevant whether a character exists at the same time or not – it has no bearing on the behavior execution. It is however possible that the behavior implements certain logic inside an event that can cause different signals to be emitted and thus **influence** implicitly to which behavior the character will switch. This is also not an error condition – in fact, a few of the game behaviors employ this trick.

One thing that is VERY important to understand in regards to characters, behaviors and behavior switching is the following: If the character specifies that the behavior needs to be switched on a particular event – There is nothing that the behavior can possibly do (overall and inside the function handler) to prevent that. In other words, it is impossible to implement any logic that uses the same event to switch to one behavior if some condition is true and another behavior when the same condition is false. Then what is the solution for this?

The solution is to create special signals for the two behaviors, and use them as the events that will trigger the behavior switch instead of using one event. As a simple example to illustrate this, consider the following:

```
OnThreateningSoundHeard = function( self, entity, fDistance )
if (fDistance < 40) then
AI.Signal(0, 1, "HOLD_POSITION", entity.id);
else
AI.Signal(0, 1, "NORMAL_THREAT_SOUND", entity.id);
end
end,
```

So now, instead of performing the behavior change on the OnThreateningSoundHeard event, we implemented some kind of logic inside it that determines which signal will be sent. The change to the different behaviors is done on the special signals.

In this way it is possible to define with logic from the current behavior what the next behavior will be. The example is a condensed real-world example from the behaviors.
