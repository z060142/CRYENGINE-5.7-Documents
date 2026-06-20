# AI Sequences

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/25535408
- Page ID: 25535408
- Breadcrumb: AI and Navigation > AI Overview > AI (NPC) > AI Sequences
- Parent: AI (NPC)

## Content

[Image: /docs/static/attachments/29933201]

##
Overview

AI Sequencer is a system to simplify and reduce the level logic needed to manually control AI characters by level designers, and it works on top of the current Flow Graph system interface.

##
Sections

[#sections](
Sections
)
[#goals](
Goals
)
[#concept](
Concept
)
[#interrupting-resuming](
Interrupting / Resuming
)
[#valid-flownodes](
Valid Flownodes
)

##
Goals

-
Reduce the amount of flownodes necessary to script the idle actions by automating much of the micromanagement logic needed to manually control the character and handle all the different scenarios that can occur during gameplay (for example, canceling the actions when the agent gets alerted or resuming the actions when he goes back to idle).

-
Provide a context to the individual actions that an agent performs when they are manually controlled by level design. This simplifies the AI code and makes it more stable.

-
Add a validation step to the level setup, minimizing the occurrence of bugs and providing better debug information when they happen.

##
Concept

An AI Sequence is a chain of actions to be performed by the AI entities. The
**

**
and
**
AISequence:End
**
 define the beginning and the end of the sequence, while the AI sequence action nodes, like
**
AISequence:Move
**
 or
**
AISequence:Animation
**
 define the order of the actions to be executed. Only one sequence can be active for an individual agent and it can only perform one action at a time.

Below is a simple example which will make the agent walk to "tag point 10", then go to "tag point 4" and play the animation AI_idleBreakBored and finally run to "tag point 3":

They can be looped as well, like in this example which will make the agent continuously move between tag points 10 and 3:

Sequences can also have conjoined sync points. In this example, both agents will start by doing a move action and will only continue to the next action when both have arrived at their first destinations:

##
Interrupting / Resuming

With the interruptible flag set to true, the AI sequence will automatically stop executing as soon as any AI entity leaves the idle state, taking care of stopping any action that could be active or triggered after that.

If it is also set to resume after interruption, the sequence will also be resumed when the AI goes back to the idle state. It will resume from the start or from the latest bookmark. Bookmarks are defined with the
**
AISequence:Bookmark
**
 flownode and can be placed in the middle of a sequence and will basically work as checkpoints from where the sequence should resume from.

In this example, if the agent is interrupted while moving to the second tag point and then goes back to idle, instead of starting from the beginning, it will resume the sequence by going directly again to the second tag point.

##
Valid Flownodes

To minimize possible bugs and unexpected behavior, only flownodes supported by the AI Sequence system can be used to define an AI sequence chain and there will be an error message when the AI sequence is triggered if an unsupported node is used.

The currently supported nodes are:

-
All AISequence flownodes.

-
All Logic flownodes.

-
All GameToken flownodes.

-
Sound:PlayDialog.

-
Sound:Dialog flownodes.

-
Sound:PlaySoundEvent.

-
Actor:AliveCheck.

-
Debug:DisplayMessage.

-
Debug:DisplayTag.

-
Debug:DisplayTagAdv.

-
Entity:BeamEntity.

-
Entity:CheckDistance.

-
Entity:EntitiesInRange.

-
Entity:GetPos.

-
Entity:Pos.

-
Movement:MoveEntityTo.

-
Movement:RotateEntity.

-
Movement:RotateEntityEx.

-
Physics:ActionImpulse.
If necessary, other flownodes can be added to this list as long as they are compatible or changed to be compatible with the AI Sequence system.
