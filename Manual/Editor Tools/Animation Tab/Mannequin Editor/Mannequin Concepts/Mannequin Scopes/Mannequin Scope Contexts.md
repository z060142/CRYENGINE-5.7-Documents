# Mannequin Scope Contexts

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/29450870
- Page ID: 29450870
- Breadcrumb: Editor Tools > Animation Tab > Mannequin Editor > Mannequin Concepts > Mannequin Scopes > Mannequin Scope Contexts
- Parent: Mannequin Scopes

## Content

![Image](https://www.cryengine.com/docs/static/attachments/29934030)

## Overview

## Sections

A *Scope Context* tells [Scopes](../Mannequin%20Scopes.md) which entity, character & [animation database](../../Mannequin%20Files/Animation%20Database%20(ADB).md) to use.

Each scope is attached to a scope context, so you always need at least one Scope Context describing your character.

We fill in the entity, character & animation database during the entity setup by referring to the scope context by name (for example "MainCharacter"). These properties of a Scope Context can change during run-time, so it is possible to swap the entity, character instance or animation database we are playing animations on at any time. This is used for example for swapping weapons, or attaching other characters to the player during a synchronized animation.

[Sections](#sections)[Scope Layout](#scope-layout)[Creating Scope Contexts](#creating-scope-contexts)[Filling Scope Contexts](#filling-scope-contexts)

### Scope Layout

This is how a scope context could look:

By making a scope context a separate object you are able to reuse the same combination of entity/character/animation database on multiple scopes.

#### Example

We want a setup in which we have a full body, an upper body and a weapon entity that we want to control separately and be able to synchronize animations on.

We could do so by having three scopes in our controller definition: one to control full body fragments, one for upper body and a final one for the weapon.

Next to the MainCharacter scope context (pictured above), we also added a Weapon scope context that contains the weapon entity:

And now we can refer to them from the scopes:

### Creating Scope Contexts

You create scope contexts by referring to them in the scope setup in the [Controller Definition File (xxxControllerDefs.xml)](../../Mannequin%20Files/Controller%20Definition%20File%20(xxxControllerDefs.xml).md).

### Filling Scope Contexts

#### In the Mannequin Editor

In the editor, the game code is not executed and we use a [preview setup file](../../Mannequin%20Files/Preview%20Setup%20File%20(xxxPreview.xml).md) to fill the scope contexts. You edit these in the [context editor](../../Mannequin%20Context%20Editor.md).

#### During the Game (or while playing the game in the editor)

##### In General

The scope contexts are filled in by game code.

For programmers: this is done by calling IActionController::SetScopeContext().

##### Main Setup (AnimatedCharacter)

In the standard GameDLL, the AI and player characters have an AnimatedCharacter component which will control mannequin. It takes care of filling in the main scope contexts, which *have to be* named "Char1P" (first person character), "Char3P" (3rd person character) and "Audio". You configure the animation databases that will be used for the scope contexts through the entity's LUA file. The properties controlling this have the following names:

Scope Context Name | Property Name
--- | ---
Char1P | AnimationDatabase1P
Char3P | AnimationDatabase3P
Audio | SoundDatabase

For example this is a part of the human_x.lua file configuring the human AI, specifying the Animation Database for these contexts. Note that the AI does not have 1st person character, so it doesn't have a Char1P scope and it doesn't need an "AnimationDatabase1P".

```
...
Human_x =
{
ActionController = "Animations/Mannequin/ADB/humanControllerDefs.xml",
AnimDatabase3P = "Animations/Mannequin/ADB/human.adb",
SoundDatabase = "Animations/Mannequin/ADB/humanSounds.adb",
...
```

Before CryEngine 3.7, the "Audio" scope was called "Sound".

##### Weapon/Item Setup

Each individual weapon or item has its own ADB. If a weapon is controlled by a player, the weapon system will take care of assigning this ADB to the proper scope context.

The scope contexts in the weapon system are named:

Weapon
---
attachment_top
attachment_bottom

You configure the animation database that will be assigned to these using the item's XML file.

eg. *GameSDK/Scripts/Entities/Items/XML/Weapons/Rifle.xml* contains:

```
<param name="adb" value="rifleWeaponAnims.adb" />
```

Hit Death Reaction System

When controlling a slave during a 'synchronized kill', the hit death reactions system fills the scope context named "SlaveChar"

The animation database to fill in, as well as which [global tag](../Mannequin%20TagState.md) to set when performing a synchronized kill with a certain entity, is configured in *Libs/HitDeathReactionsData/HitDeathReactions_XXX.xml files.*

The manqTargetTag is used to identify the fragments playing on the master and slave while executing the synchronized kill.

It is also the tag you use in the context data when making a [preview setup file](../../Mannequin%20Files/Preview%20Setup%20File%20(xxxPreview.xml).md) in the [Mannequin Context Editor](../../Mannequin%20Context%20Editor.md).

Do not confuse this tag with the tag "slave" which is the [scope tag](../Mannequin%20TagState.md) for the SlaveChar scope in the GameSDK setup. So fragments playing on the slave will have both the "slave" tag and the manqTargetTag set. And fragments playing on the master will only have the manqTargetTag set.

For example this comes from *GameSDK/Libs/HitDeathReactionsData/HitDeathReactions_SDKGrunt.xml*:

```
...
<DeathHitReactionsParams>
<HitDeathReactionsConfig
...
manqTargetTag="slaveHuman"
animDatabaseSlave="Animations/Mannequin/ADB/humanSlaveAnims3P.adb"
/>
...
```

See also: [Hit and Death Reactions System](../../../../../../API%20Reference/CRYENGINE%20Game%20Code/Miscellaneous%20Game%20Code/Game%20Characters/Hit%20and%20Death%20Reactions%20System.md)
