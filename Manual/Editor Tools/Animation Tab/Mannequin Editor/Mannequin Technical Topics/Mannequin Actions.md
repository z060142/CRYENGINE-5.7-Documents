# Mannequin Actions

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/23308467
- Page ID: 23308467
- Breadcrumb: Editor Tools > Animation Tab > Mannequin Editor > Mannequin Technical Topics > Mannequin Actions
- Parent: Mannequin Technical Topics

## Content

##
Overview

Actions are a concept for programmers that use mannequin.

The basic action class is used to control animation and synchronize with the game. It can combine game code with simple high level animation control.

When an action is installed it
*
owns
*
 one or more
[/docs/static/engines/cryengine-5/categories/23756816/pages/29450859](
scopes
)
 and can then request
[/docs/static/engines/cryengine-5/categories/23756816/pages/23308432](
FragmentIds
)
 to play onto those scopes. At a single time each scope can only be controlled by a single action. And many actions can be running in parallel, as long as they all control different scopes.

Each action can only request one FragmentID installation at a time, but it can sequence multiple of these requests in a row if it wants to. So if you want to implement an animation state machine, either you queue multiple actions that each push one single FragmentID and you handle the state machine outside, or you queue one single action that has a state machine inside that requests the appropriate FragmentIDs. The latter is typically how you handle basic locomotion state machines.

##
Creation

You create an instance of an action class:

-
You may create a new class or simply use a generic one for simple cases (the single-fragmentID-playing-once case is the default behavior).

-
They have to inherit from the
`
IAction
`
 interface or the TAction<> helper template.
With the constructor you can then:

-
Set the relevant FragmentID (which will be the first FragmentID that will be requested)

-
Set any
[/docs/static/engines/cryengine-5/categories/23756816/pages/23308434](
FragmentID-specific Tags
)

-
Set the action’s Priority, which is used to manage overlapping actions (actions that want to own the same scope). Higher number is higher priority.
Here is a sample snippet that creates an action that plays the Idle fragmentId:

```

`
const FragmentID idleFragmentId = m_pAnimationContext->controllerDef.m_fragmentIDs.Find( "Idle" );
const int actionPriority = 0;

IActionPtr pAction = new TAction< SAnimationContext >( actionPriority, idleFragmentId );
`

```

Actions are intrusively reference counted and when keeping/releasing references you have to call
`
AddRef(
`
)/
`
Release()
`
. To simplify this we recommend you use the
`
IActionPtr
`
 typedef, which is a _
`
smart_ptr<IAction>
`
 that calls
`
AddRef
`
/
`
Release
`
 for you. In simple cases where your actions are 'fire and forget' you don't need to store the reference so you don't need to call
`
AddRef()
`
 or use
`
IActionPtr
`
.

##
Queuing

Next you queue the action onto the target’s
[/docs/static/engines/cryengine-5/categories/23756816/pages/23308466](
Mannequin ActionController
)
.

For actors this Action Controller is accessible via the AnimatedCharacter extension (IAnimatedCharacter::GetActionController()). If you want more information about managing your own action controller, see the article
[/docs/static/engines/cryengine-5/categories/23756816/pages/23308465](
Entity Setup From Scratch
)
.

The queueing looks simply like this:

```

`
pActionController->Queue( pAction );
`

```

The action goes onto the
**
pending action queue
**
 which is a priority queue. Higher priority actions are selected first. Higher numbers are higher priorities.

Each frame the system will check whether actions that are in the queue can be installed on the scopes they want to own.
To know which scopes those are, the system retrieves the requested fragmentID and looks up the associated scopemask. For more details on this, please have a look at the
[/docs/static/engines/cryengine-5/categories/23756816/pages/23308439](
Fragment Selection Process
)
.

If the candidate action has higher priority than all the actions currently owning those scopes it will be installed immediately and skip any waiting times in transitions (see
[/docs/static/engines/cryengine-5/categories/23756816/pages/29450863](
trumping
)
). Otherwise the candidate action will wait for those actions to finish, or for a suitable transition to gracefully stop the current action. See
[/docs/static/engines/cryengine-5/categories/23756816/pages/23308485#MannequinEditorTutorial3-Transitions-EarliestStartTime](
Mannequin Editor Tutorial 3 - Transitions
)
 for more details on how to work with transition start times.

If the action gets selected from the queue, it gets installed on its scopes, and its fragmentID will be pushed on and updated before the next batch of animations are sent off for processing.

Note that an action should not be queued twice!

##
Interruptible and NoAutoBlendOut

There are two flags you can pass into the IAction constructor that control more in detail how the action behaves:

-
**
`
IAction::Interruptible
`
**
: Actions that get pushed away will be stopped unless they have the
`
IAction::Interruptible
`
 set. They will get pushed back onto the pending action queue and will return when they can. This "interruptible" flag is typically used for actions controlling Movement or Idling actions. They are low priority actions that run 'by default' on certain scopes, but get pushed away by any more specific action. They come back when those specific actions end. See also the example below.

-
**
`
IAction::NoAutoBlendout
`
**
: By default, actions that play a non-looping fragment will end themselves as soon as that fragment ends. If you want the action to stay installed anyway even though the fragment has ended you can set the
`
IAction::NoAutoBlendout
`
 flag. This is what you typically use on actions containing a little animation state machine picking different fragments, for example a basic 'movement action' picking Idle/Move/Turn/etc.

##
Enter/Exit

When the action is 'installed', in other words when the action is removed from the pending action queue and it starts to play,
`
IAction::Enter()
`
 is called. This happens during the call to
`
ActionController::Update()
`
.

When an installed action is pushed away or stops,
`
IAction::Exit()
`
 is called. An action will not get an
`
Exit()
`
 if it wasn't installed before.

Some notes on overriding Enter and Exit:

-
Make sure you call the parent implementation when you override
`
Enter()
`
 and
`
Exit()
`
. If you fail to do so the DEBUG_BREAK inside
`
~IAction()
`
 might trigger because
`
Enter()
`
/
`
Exit()
`
 calls are supposed to be paired and this is checked using code from the parent implementation.

-
It is possible to queue new actions within
`
Enter()
`
 and
`
Exit()
`
. They might still be installed immediately if they have proper priority. (implementation detail: this works because
`
ActionController::ResolveActionInstallations()
`
 is called over and over again until action installations are properly resolved - or a maximum number of iterations is reached, currently that number is 5).
In special cases where the action is forcefully stopped by the system because the queue overflows, or because a scope context becomes invalid,
`
IAction::Fail()
`
 is called. If the action was installed it will not get an
`
Exit()
`
 in call this case. You could treat both cases as hard failures and implement
`
assert
`
/
`
FatalError
`
 calls inside your
`
IAction::Fail()
`
 implementation.

##
Update/UpdatePending

When an action is in the pending action queue at the beginning of the actioncontroller's update,
`
UpdatePending()
`
 is called. Otherwise, so if the action is installed at that moment,
`
Update()
`
 is called.

In the special case that an action is both queued and installed during the same
`
ActionController::Update()
`
 call, you will still get one call to
`
UpdatePending()
`
. This means that you should always get at least one call to
`
UpdatePending()
`
 before
`
Enter().
`

As with
`
Enter()
`
 and
`
Exit()
`
, make sure you call the parent implementation when overriding
`
Update()
`
 or
`
UpdatePending()
`
!

During the update the Action can, for example:

-
Change the current fragment by calling SetFragment(). If you do this, make sure you call it during
`
UpdatePending()
`
 as well, because the scopes an action will be installed on, or how long an action is delayed, depends on fragmentID/fragtags and the chosen fragment!

`
void SetFragment(const FragmentID fragmentID, const TagState &tagState = TAG_STATE_EMPTY, uint32 optionIdx = OPTION_IDX_RANDOM, const uint32 userToken = 0, bool trumpSelf = true)

`

-
`
fragmentID
`
: the fragmentID you want to select

-
`
tagState
`
: the
[/docs/static/engines/cryengine-5/categories/23756816/pages/23308434](
fragtags
)
 you want to set.

-
`
optionIdx
`
: If this is
`
OPTION_IDX_RANDOM
`
, a random fragment option will be chosen. Otherwise this number will be modulated by the number of options to select the option.

-
`
userToken
`
: Sets the 32 bit integer that will be associated with every animation that gets started by this action (it is passed using
`
CryCharAnimationParams::m_nUserToken)
`
. Subsequently you can use methods like
`
ICharacterInstance::FindAnimInFIFO()
`
 to find an animation that has this token set. Or you could check the token of any animation that is currently playing to figure out which action started it.

-
`
trumpSelf
`
: pass true to
[/docs/static/engines/cryengine-5/categories/23756816/pages/29450863](
trump
)
 the previous fragment this action was playing.

-
Set
[/docs/static/engines/cryengine-5/categories/23756816/pages/29450867](
mannequin parameters
)
 for procedural clips by calling
`
SetParam()
`
. These are simple key-value pairs. Procedural clips pick these up using
`
IProceduralClip::GetParam()
`
.

-
Do custom game-side work to assist co-ordinating animation and game state. For example sending events to your game code, overriding blend space parameters, setting IK targets, controlling pose modifiers, setting information regarding character alignment, ...

-
Decide to call
`
Stop()
`
, which means 'stop gracefully'. It will allow the action to blend out, so lower priority and equal priority actions can come in now (normally they would wait until the current fragment has finished playing).

-
Decide to call
`
ForceFinish()
`
 to force itself to finish. This will allow other actions to come in immediately and trump this action.
e.g. A Reload action handles events to ensure that ammo is installed at the correct time.

e.g. A Locomotion action changes the FragmentID based on player input.

##
Example

Here is an example how the action queuing, installation and interruption works in practice. This is a little scenario in which we start out moving around, then jump, then reload while jumping and finally perform a special 'stamp' move while we are falling.

Base
 |
Torso
 |
Weapon
 |
Priority Queue
 |
Description
 |

Locomotion
 |
Idle
 |

 |

 |
Initial state. An action controlling basic locomotion holds the base scope (and typically has a locomotion state machine inside)

and an Idle action currently has control of the torso (and typically controls a little state machine picking random idle animations).
 |

Locomotion
 |
Idle
 |

 |
Jump
 |
Game updates and queues up a Jump action. It is on the same scope as the Locomotion but with higher priority so it will interrupt it.
 |

Jump
 |
Idle
 |

 |
Locomotion
 |
Locomotion is
*
interruptible
*
 and so is automatically added to the priority queue ready for reinsertion at the earliest opportunity.
 |

Jump
 |
Idle
 |

 |
Reload
 |
Locomotion
 |
Game updates and queues up a reload action. This moves straight to the head of the priority queue.
 |

Jump
 |
Reload
 |
Reload
 |
Locomotion
 |
Action Controller updates and pushes the Reload onto the Torso and Weapon Scopes.

This triggers the character and the weapon animations synchronously. The Idle action is not interruptible and so is terminated and deleted.
 |

Jump
 |
Reload
 |
Reload
 |
Stamp
 |
Locomotion
 |
Game updates and queues up a stamp action. This is a high priority action which effects all the scopes. It goes straight to the head of the priority queue.
 |

Stamp
 |
Stamp
 |
Stamp
 |
Locomotion
 |
The Stamp is pushed on across all the scopes. The existing actions are all non-interruptible and so terminated and deleted.
 |

Stamp
 |
Stamp
 |
Stamp
 |
Locomotion
 |
The Stamp action hits the ground and pushes on its final FragmentID (StampLand).
 |

Locomotion
 |

 |

 |

 |
When we reach the most appropriate blend point the Stamp action is terminated and the Locomotion reinstalled.
 |

##
Persistent FragmentIDs

With IAction::NoAutoBlendout you can prevent an action from stopping when a non-looping fragment ends. But sometimes it's more convenient to set this up in data, on the FragmentID itself. This you can do by selecting the Persistent checkbox in the
[/docs/static/engines/cryengine-5/categories/23756816/pages/23308446](
FragmentID Editor
)
. As far as the system is concerned any fragment with this fragmentID behaves as if it is looping: the action will keep running until a higher priority action comes along, or the action is explicitly stopped or force-finished.

##
Picking up Tag Changes

You might be surprised that when tags change, the action doesn't automatically use them to pick and play a more applicable fragment. This is by design. To install the new fragment you have to call SetFragment explicitly again from within the action.

However, as this is a common use case there is a flag you can apply to the FragmentID in the editor which will enable some code in IAction that will automatically pick up the most applicable fragment for the current
[/docs/static/engines/cryengine-5/categories/23756816/pages/23308435](
TagState
)
. This is the "Auto Update" checkbox in the FragmentID. See the
[/docs/static/engines/cryengine-5/categories/23756816/pages/23308446](
Mannequin FragmentID Editor
)
. The code that handles this can serve as a simple example if you want to handle the tag changes yourself: Look at the implementation of IAction::OnResolveActionInstallations.

One example where you might want to handle it yourself is if you want to skip delays (coming from transitions). The default implementation for handling the "Auto Update" mentioned above passes "false" as last parameter to SetFragment, which means the fragment will not skip delays. If you want it to, simply pass "true" instead.

Another example would be if you want to pick the final fragment from a very specific list of fragments, and select the option you want yourself. It is an advanced use case, but it is allowed to query the animation database yourself for fragments and figure out which one is most appropriate based on your own criteria. For example you can find the database that is used by the current scope from within the action with GetRootScope().GetDatabase(), and next use IAnimationDatabase's methods to query for fragment information.

##
Playing a Sequence of Actions

If you play multiple actions in sequence the priority scheme might not be doing what you want. The previous action will only be pushed away immediately if the next action has higher priority. If the next action has the same priority, but you still want it to push away the current action, you can override the
`
IAction::ComparePriority
`
 function and do something like this:

```

`
virtual EPriorityComparison ComparePriority(const IAction& actionCurrent) const
{
    return (IAction::Installed == actionCurrent.GetStatus() && IAction::Installing & ~actionCurrent.GetFlags()) ? Higher : IAction::ComparePriority(actionCurrent);
}
`

```

Basically this returns 'Higher' when the action that is compared with is currently already installed. That is the case we want to override. Otherwise we use the default implementation so we don't break the behavior of the pending action queue, which since CRYENGINE 3.7.0 also calls the ComparePriority function when inserting new actions into the queue. Always returning Higher in that case would break the FIFO behavior.

Note that in cases where you switch constantly between same-priority actions you should consider changing it into one single action that switches fragments internally instead.
