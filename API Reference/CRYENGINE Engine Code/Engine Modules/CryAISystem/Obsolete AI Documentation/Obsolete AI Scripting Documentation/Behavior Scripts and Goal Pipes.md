# Behavior Scripts and Goal Pipes

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/23306487
- Page ID: 23306487
- Breadcrumb: CRYENGINE Engine Code > Engine Modules > CryAISystem > Obsolete AI Documentation > Obsolete AI Scripting Documentation > Behavior Scripts and Goal Pipes
- Parent: Obsolete AI Scripting Documentation

## Content

### Combining Behavior Scripts and Goal Pipes

Now that we have covered the basics of how the behavior works and how events are handled in the behavior as well as how to create goals that can be used to respond to these events, it is time to combine the two and make a simple behavior that illustrates all the concepts.

This part of the manual will demonstrate how to write a simple behavior script. For real world examples, please refer to the behavior scripts – which are nothing more than more complicated instances of behaviors. For the following example, I will use goal pipes that have already been written with CryENGINE – to find where they are defined, please search the folder `\Scripts\AI\GoalPipes`.

### Setting Up a Situation

In order to make a fairly illustrative example, we need to set up a situation in which the enemy will be engaged. This is an easy task – in the CryENGINE Sandbox place a few brush objects (rocks, crates, whatever) at some close proximity to each other. Make sure that their **Hideable** flag is set, and then generate the AI triangulation. Now the enemy that we are going to place here will have somewhere to hide, which means we can use goal pipes that have the ** hide** goal pipe within them.

Create an enemy and select the already registered Prototype behavior – if this behavior is not registered for you, please revert to this section to understand how to register it. After selecting this behavior, try to engage the enemy in the editor's game mode. Since this behavior is essentially empty, the enemy just follows you with his eyes as you move around.

### Implementing Reasonable Responses

Now that the situation is set up correctly, we can start defining what the enemy's reactions will be when engaging the player. For this purpose we will start with the simplest response an enemy character can have towards a player – shoot.

Replace the OnEnemySeen function handler in the Prototype.lua with this one:

```
OnEnemySeen = function( self, entity, fDistance )
entity:SelectPipe(0,"just_shoot");
end,
```

This handler instructs the enemy to select the goal pipe **just_shoot** when he perceives a player. It's not hard to guess what that goal pipe is actually doing, but look at its implementation (can be found in the file PipeManager2.lua):

```
AI.CreateGoalPipe("just_shoot");
AI.PushGoal("just_shoot", "firecmd", 0, 1);
AI.PushGoal("just_shoot", "timeout", 1, 1);
```

This is really a simple goal pipe that allows the enemy to shoot with the first goal, and waits for 1 second with the second goal. Arguably, the timeout is not really necessary, but its there to make this pipe a little more than ONE simple goal.

When executing this pipe, the default nature of re-executing the goal when it reaches the final goal is not a problem. Generally, an effort should be made to make the goal pipes that are to be selected **loop-able**. In other words, they should continue to loop if nothing happens and the resulting behavior should not look out of place.

Experiment with spawning behind the enemy, and understanding when he starts to actually use the **just_shoot** pipe. Notice that he may turn to you before you actually make visual contact with him – this just means he heard your footsteps.

Let's now expand this simple behavior by implementing a little more **logic** in the event handler. For example, we might want the enemy to run for cover if the player is too close to him but just shoot if the player is far enough. To do something like this, we can change the event handler to something like this:

```
OnEnemySeen = function( self, entity, fDistance )
if (fDistance > 5) then
entity:SelectPipe(0, "just_shoot");
else
entity:SelectPipe(0, "minimize_exposure");
end
end,
```

You can find the **minimize_exposure** goal pipe content in PMReusable.lua.

If your enemy is not hiding, make sure the proper hidable flags are set to the brushes and that you have generated the AI triangulation. Read this.

There are a few points to notice with this change. First, if you spawn at a distance greater than 5 meters and the enemy will start just shooting at you. This is good and expected. But, if you start approaching the enemy, and even reach a position closer than 5 meters to him, he will not select the goal pipe that makes him hide. Why is this happening?

In the previous discussion of events ant the mechanism for their triggering it was mentioned that events are ONLY generated when there is a change in the environment. Since once the enemy has seen the target there is no further change (he still sees the target) even if the target moves closer to the enemy. To make the enemy re-evaluate his position through the script, the environment must change (e.g, the player hides and then comes out again – you break visual contact with the enemy). To understand this more clearly, let's reintroduce the HUD messages to see when the event handler functions are being called:

```
OnEnemySeen = function( self, entity, fDistance )
Log("*On Enemy Seen*");
if (fDistance > 5) then
entity:SelectPipe(0, "just_shoot");
else
entity:SelectPipe(0, "minimize_exposure");
end
end,

OnEnemyMemory = function( self, entity, fDistance )
Log("*On Enemy Memory*");
end,
```

Now try to run around and see when the messages are displayed. Notice that every time the enemy turns his back to you, the OnEnemyMemory event is called – since the environment changed and the enemy cannot see you any more. To reissue the OnEnemySeen, notice that there must be an OnEnemyMemory in between that will cause a re-evaluation.

There is a way to force re-evaluation of targets, but that's not recommended since re-evaluation is the most expensive thing the AI object can be doing and therefore there are a lot of automatic mechanisms that ensure that it is done as seldom as possible. To force re-evaluation at any point in a goal pipe, you can use the goal **clear**.

Let's try to expand upon this simple behavior, in that we will make the enemy first run to hide, and then shoot from there – just like he did previously. The simplest way of accomplishing this is to insert a pipe at the beginning of **just_shoot** that will make the enemy go to cover. To do that, change the OnEnemySeen event handler to look like this:

```
OnEnemySeen = function( self, entity, fDistance )
entity:SelectPipe(0, "just_shoot");
entity:InsertSubpipe(0, "minimize_exposure");
end,
```

Notice that before inserting a pipe in to the currently executing pipe – a currently executing pipe has to be selected. Switching the order of the function calls will not work.

Now try testing this, and you will observe an interesting and unexpected turn of events. If you expected the enemy to hide one time and then just shoot from there, that is obviously not what is happening. The enemy keeps running back behind cover, even after the first time, and he doesn't shoot much. Why is this happening?

The answer is the same as the previous time. The fact that the enemy TURNS HIS BACK to the target when he turns to hide, makes him receive the OnEnemyMemory event, thus causing a re-evaluation. Then when he looks back towards the target, he gets the OnEnemySeen event again which causes the **minimize_exposure** goal pipe to be inserted again. Thus the enemy keeps hiding.

How to resolve this? In order to realize what is needed to fix this **problem**, we need to understand that the response that the enemy does when he sees the player FOR THE FIRST TIME is not necessarily the same response he will do when he sees the player again. This is because the enemy was previously idle, but after seeing the player, he switches to alert mode. Essentially, the enemy has changed the state, so he needs to start responding to events differently.

But how to change state when we have only one behavior? Well, think of behaviors as STATES, and multiple states can be created by creating multiple behaviors. In the presence of multiple behaviors, there must exist a mechanism for deciding WHEN certain behavior needs to go into another behavior (when states need to change), and the rules that define to what states the enemy can switch from any given state. Just such a mechanism is the enemy character.
