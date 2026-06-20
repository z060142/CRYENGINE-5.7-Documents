# Goal Pipes

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/23306483
- Page ID: 23306483
- Breadcrumb: CRYENGINE Engine Code > Engine Modules > CryAISystem > Obsolete AI Documentation > Obsolete AI Scripting Documentation > Goal Pipes
- Parent: Obsolete AI Scripting Documentation

## Child Pages

- [Goalop Reference](Goal Pipes/Goalop Reference.md)
- [Goalpipes - From Lua to XML](Goal Pipes/Goalpipes - From Lua to XML.md)

## Content

##
Overview

AI actors in the CryAISystem are capable of executing certain actions in order to achieve some goals. The goals can be very simple – for example approach 2 meters to a certain object, or fairly complicated – for example hide in the leftmost obstacle from your current target.

The low-level AI system is responsible for the execution and management of these goals, and it also controls what happens if the goals successfully finish or if they fail. Other responsibilities include brokering which goals execute in parallel and which goals execute serially.

Goals can be atomic and derived. An
**
atomic
**
 goal is a simple goal that cannot be further split into sub-goals, and is one logical unit. A
**
derived
**
 goal is a goal that is a combination of a few atomic or derived goals that can execute in parallel or in a sequence. While atomic goals are defined by the system and introduction of new atomic goals would require working on the low-level AI system, the users can define derived goals themselves. The definition of new derived goals can be made on the C++ side or in Lua (both contain a set of functions that work with goals). Usually, goals are exclusively defined in Lua script.

Since derived goals are created by combining atomic and other derived goals, there must be a way to organize a few goals into a logical sequence – a program – that has a start point, a body to execute and conditions to end. This logical union exists in the CryAISystem and is called a
**
Goal Pipe
**
.

##
Goal Pipes

The logical sequence of atomic and derived goals for the purpose of creating another derived goal is called a goal pipe. It is called that because conceptually it resembles a pipe in which goals are pushed from one end, and as they execute they come out on the other end, and are re-pushed from the bottom again. This implies that the goals are executed in sequence – which is generally true – but there is a way to make goals execute in parallel.

Even a goal pipe can be pushed as a goal to another pipe. This enables such exotic concepts as nesting goal pipe, and recursive goal pipes. There is no limit of the amount of nesting with the goal pipes so that is left to the discretion of the user. Using recursion in pipes is not recommended but the system generally supports it.

By combining atomic goals into bigger goals, you can develop any level of abstraction for the characters in the game. For example, exiting a room might involve finding a door and using it. So you have fragmented the higher level goal into two smaller goals. Finding a door decomposes into locating a door object and approaching to it – both of which are pretty atomic. Using the door involves approaching at 1 meter, and pressing USE. So while you can create one big goal pipe that locates a door object, approaches it, stands at 1 meter to it, presses use; you can also fragment the action into two higher level sub-goals and optionally reuse them sometime later. In the same sense, maybe you can use the
**
exit_room
**
 goal pipe inside a bigger
**
exit_building
**
 goal pipe, etc. It is exactly for this purpose why the nesting of goal pipes is handy.

All goal pipes are created on startup. Goal pipes are not owned by any AI actor, they are owned by the AI system itself, so you do not need to worry that you need to release them or otherwise maintain them. Every AI actor that requests a goal pipe gets a clone of the original – that means that he has his own copy of the goal pipe and cannot possibly influence the operation of other AI actors that may use the same goal pipe. AI actors are the owners of these cloned goal pipes and they automatically perform maintenance on them, so it is another thing that doesn't need to concern the user.

To create a goal pipe, you have to call the following function (in Lua – there is an equivalent function in C++, but we will focus on Lua functions):

```

`
AI.CreateGoalPipe("crouchfire");

`

```

The AI global Lua script object offers this functionality (as well as other, which will be discussed later). The function is simple with its only argument being the name under which this goal pipe will be identified in the future.

Special care should be taken about naming the goal pipe. For one, it should not be a name of an existing atomic goal – a comprehensive list is included in the appendices. Ideally, it should be a unique name that can be easily remembered and it should pretty much explain what the goal pipe will do. Looking at the name of the example goal pipe, it is easy to surmise that this goal pipe will make the entity that is using it to fire while crouching.

If an attempt is made to create a goal pipe with a name that already exists, the old version of the goal pipe will be orderly removed and cleaned up, and will be totally replaced with the new version. This doesn't mean that if someone was already using the old version he would not know what to do, or even use the new version. Goal pipes are CLONED to be used, so whoever is using an older version of the goal pipe will keep the cloned version of the old goal pipe and finish executing it, while whoever wants to get a new version of the goal pipe will have only the new version to clone FROM. In this sense, name conflicts for goal pipes are not necessarily a terrible thing.

Goal pipes do not need to be created ONLY on startup. The user is free to create a goal pipe at any point in the game's execution. The advantage to this is that you can create a goal pipe that depends on certain condition, or a goal pipe that is geared for a very specific use – one that may not be readily available at the startup of the game. Creation of goal pipes DOES mean memory allocation and access, but the overhead is not significant if used in moderation. A good rule of thumb is that goal pipes can be created in response to an event in a behavior because those events are generally not frequent.
**
Creating new goalpipes every update frame is a bad idea.
**

##
Pushing Goals in Goal Pipes

Once a goal pipe has been successfully created, you can start pushing goals onto it. As mentioned previously, the goal pipe works in essence as an FIFO (first in first out) buffer. What that means is that the goals pushed into the pipe will execute
**
in the same order in which they were initially pushed
**
. There is no limit (other than common sense) to the amount of goals that you can push into a goal pipe and remember that you can also push sub-goal pipes into the pipe.

To push a goal into a pipe, you can use the following function:

```

`
AI.PushGoal("crouchfire", "firecmd", 0, 1);

`

```

Notice that the function is a part of the functionality that the AI global Lua object offers. The arguments to this function are fairly self-explanatory: first and foremost, the goal pipe in which we want to push has to be defined by name. Next, the actual goal that is going to be pushed onto this goal pipe has to be specified, also by name. In the example, that is the simple goal
**
firecmd
**
 which basically instructs the enemy that executes it whether it is allowed to fire or not, based on its later parameters.

The third parameter of this function is an integer that can only be one of two values - 0 or 1. This is the last parameter that is common to all pushed goals – all parameters after this one are goal-specific, which means that they are different based on the actual goal that needs to be pushed. This third parameter is called the blocking flag. If it is set to 1, that means that when this goal starts executing, the further execution of the goal pipe should HALT until the currently executing goal finishes. If it is set to 0, that means that even though the current goal may not be finished, the execution of the goal pipe should continue.

This provides a mechanism to determine whether the goals will be executed in sequence or in parallel. Different derived goals require different behavior, so this is why this property can be controlled on a per goal level. For example, if we are writing a goal that needs to use an elevator button, it is normal that we need to wait before pressing use until we have approached the elevator to a certain distance. In this example, we would make the approach goal blocking, and follow it with a goal that generates a key press corresponding to the USE key.

**
Sub goal pipes CANNOT be non-blocking.
**
 They are blocking by default and any goal pipes that have sub pipes have to wait until the sub pipe has finished executing before they can continue with their own execution.

The reference section at the end of this document contains a full reference of all of the atomic goals that the system recognizes in its current state. Refer there for specific discussion on the parameters for a specific goal and its behavior.

The GoalPipes directory in the AI script directory contains all the goal pipes that were used in the game, distributed over a few script files. Not all of those pipes were used. Refer to these files for an idea how finished goal pipes might look, and also for examples on the usage of the atomic goals, nesting, etc.

##
Selecting Goal Pipes to Execute

Once a goal pipe is created and goals are pushed into it, then it is ready to be selected by any entity that has an AI actor for execution. Usually goal pipes are selected for execution in response to a game event and they specify to the entity that receives the event what it should do.

The selection of the goal pipe is the simplest and the most used function in scripting behaviors for the enemies. By selecting a particular goal pipe for a particular entity, you are forcing the entity to execute the goals contained within that goal pipe. One entity can execute ONLY ONE goal pipe at a time. When a new goal pipe is selected (and this is an asynchronous operation),
**
the old pipe is removed and deleted, any remaining goals from the old pipe are also removed
**
, and the new pipe is cloned and set for execution.

To select a goal pipe to execute for a particular entity, the following function should be called on the entity script object:

```

`
entity:SelectPipe(0, "cover_look_closer");

`

```

The entity script object is passed to every event handling function, so it is easy to call functions on it and change its state. The parameters of this call are very simple: the first integer parameter is reserved and should always be 0 (for partly historical reasons). The second parameter denotes the name of the goal pipe that needs to be selected. That has to be a name of an existing goal pipe; otherwise the function call will fail.

It makes no sense to make multiple calls to the SelectPipe function in a single event. Because the limitation that only ONE goal pipe can be executed at a time, only the last call to SelectPipe will actually be valid, and the last selected pipe will be the one that ends up executing.

There is a mechanism to asynchronously nest goal pipes into whatever goal pipe is currently executing for an entity. At any point in time, it is possible to INSERT a goal pipe into the currently executing one. This operation will stop the currently executing pipe; insert the selected goal pipe as its nested sub-pipe and continue execution inside the nested goal pipe.

To insert a sub-pipe into the currently executing goal pipe, the following function should be called on the entity script object:

```

`
entity:InsertSubpipe(0, "setup_stealth");

`

```

The sub-pipe will always be inserted in the currently executing pipe, regardless of what recursion depth it may be currently at. What this means is that if the goal pipe was already executing a sub-pipe (or more) at the time of the insertion, the new goal pipe will be inserted into the sub-pipe.

Pipe insertion can be used in a wider context, for example to queue a few pipes to execute in some order. Calling InsertSubpipe multiple times in the same event does not have the same consequence as calling SelectPipe multiple times in the same event. The goal pipes that are inserted are always inserted at the top of the previous goal pipe, so when execution starts, the goals will be executed in a sequence starting from the goal in the last call to InsertSubpipe to the goal in the first call to InsertSubpipe. For example

```

`
entity:InsertSubpipe(0, "setup_stealth");
entity:InsertSubpipe(0, "DRAW_GUN");

`

```

will execute the goal pipe
**
DRAW_GUN
**
 first and when its finished, it will execute the
**
setup_stealth
**
 goal pipe. Once an inserted sub pipe is finished executing, it will return to the previous goal pipe in which it was initially inserted.

##
Goal Pipe Arguments and Execution Details

As discussed before, the goal pipes execute the goals pushed in them in sequence. But what happens when the final goal of the pipe is executed? The answer to this question depends on whether the goal pipe was selected or inserted.

Selected goal pipes will resume execution from the beginning if they execute to the end, meaning they wrap around. If a selected goal pipe is not in any way interrupted (by the selection of another goal pipe or by the insertion of a goal pipe) it will loop forever, together with any nested goal pipes that it has.

If however the pipe was inserted, after it executes the last goal, it will be removed, deleted and will not be executed again unless it is inserted again. This is valid ONLY for pipes that are inserted asynchronously – if a goal pipe is NESTED in some other goal pipe by pushing it in the normal procedure, it will be re-executed every time the parent pipe reaches it.

Goal pipe execution is pretty robust. It is natural that some goals require some prerequisites to run properly, and most of the time these prerequisites will be met – for example, the approach goal cannot execute without an attention target, because it will not know to what it should approach to. If situations like this occur during the execution of the goals, the goal is suspended (finished) and execution in the goal pipe continues uninterrupted. The consequences of this are sometimes positive and sometimes negative, depending on the context of the pipe execution and the desired behavior. Knowing the default operating procedure of goals that cannot execute properly should help the behavior designer in diagnosing problems and coming up with solutions.

Goal pipes can also
**
receive an argument
**
 Only one type of argument is allowed for the goal pipes, and that is a valid AI object – it can be an entity, a tag point, and anchor, etc. The argument is passed to the pipe at selection (or insertion) time, and it is placed in the last operation target operand. In there it can be easily accessed by any goal executing in the pipe since a lot of goals can be configured to operate on the last operation target instead of the attention target. A discussion on attention targets and last operation targets can be found here.

Goal pipes remember their argument, which means that it is possible to nest different goal pipes with different arguments. The system will make sure that always the correct argument is placed into the last operation target before an inserted or selected pipe starts to execute.

To specify an argument to a goal pipe, you have to supply it during the call to SelectPipe or InsertSubpipe. The argument can only be a valid AI Object, but the way it is specified can be done in multiple ways. For example, you can specify a target entity as an argument by passing its ENTITY ID to the selection function, or generally any AI object by specifying the NAME of the desired AI object. The AI system guarantees that names of AI objects will be unique – but not necessarily exactly what the user named them. In that sense, it is not recommended to
**
hardcode
**
 names into the arguments – instead they should be retrieved and just passed around.

The argument passing mechanism is robust enough and it will handle any strange situations, like for example when a name of an argument is passed that it cannot find. The execution of the goal pipe will continue normally.

Here is an example on how to specify an argument to a goal pipes:

```

`
OnGroupMemberDiedNearest = function (self, entity, sender)
    -- someone from your group died
  entity:SelectPipe(0, "RecogCorpse", sender.id);
end,

`

```

In this example, the pipe
**
RecogCorpse
**
 is selected and the sender of the
**
OnGroupMemberDiedNearest
**
 signal is passed as an argument to it using its entity id. This signal is sent by a dying enemy, and is received by the team member closest to his position. The receiver of this signal probably will try to move towards the sender in order to check if he is still alive.

 Another example, that illustrates passing the argument to the pipe via its name:

```

`
local gunrack = AI.FindObjectOfType(self:GetPos(), 30, AIAnchor.GUN_RACK);
if (gunrack) then
  self:InsertSubpipe(0, "get_gun", gunrack);
end

`

```

The function FindObjectOfType will return the name of the closest object in the 30 meter radius of type AIAnchor.GUN_RACK. Notice that we never handle the name explicitly, it is just passed to the pipe insertion function
**
as is
**
 returned from the Find function. Also notice that now the entity is referred as self, instead of entity. This means it is probably called from within its own script, and not the script of the behavior.

##
Passing Additional Parameters to a GoalPipe as GoalParams

It's possible to pass a dynamic number of parameter to a specific GoalPipe as GoalParams.

A basic example of how to use the GoalParams into LUA code is:

```

`
YOUR_FUNCTION = function( self, entity, sender, data )
 local tbl = {
                  {},
                  {},
                  {},
              }

 tbl[1].name = "firstParamName"
 tbl[1].value = data.fValue

 tbl[2].name = "secondParamName"
 tbl[2].value = data.point.x

 entity:SelectPipe(0, "YourGoalPipeName", 0, 0, 1, tbl)

end

`

```

The parameter 6 of the function
**
SelectPipe
**
 is the one relative to the dynamic parameters. The engine will create an internal structure to store a list of
**
[parameter_name, parameter_value]
**
 that a specific Goalpipe can interpret later if it's needed.
