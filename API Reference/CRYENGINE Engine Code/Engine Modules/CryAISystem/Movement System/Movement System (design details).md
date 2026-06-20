# Movement System (design details)

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/23306464
- Page ID: 23306464
- Breadcrumb: CRYENGINE Engine Code > Engine Modules > CryAISystem > Movement System > Movement System (design details)
- Parent: Movement System

## Content

### Overview

#### Robust and predictable

During Crysis 2 we had a lot of issues with unreliable navigation. There was no guarantee that a character would carry out the requested movement and end up at the wanted destination. Level designers and programmers didn't really know why things would break and how to fix it. It appeared as a very organic problem. This lead to a lot of ugly error handling logic on all layers - C++, Lua and Flow Graph - which in turn added to the organic nature of the problem. Sometimes it worked, sometimes it didn't. The AI movement system introduced in Crysis 3 solves this by being more explicit. No longer is "something failed, therefore you fail." valid. There has to be a reason for it and that has to be correctly propagated down and communicated.

#### Central, clear ownership and easy to debug*

Prior to Crysis 3 the AI movement code lived in the logical leafs (goal ops) and meant that the lifetime of the contextual movement information, such as style, destination, requester and so on, was as long as that of the goal op itself. That's not good, because when a behavior switch occurred all the information was gone. In Crysis 3, this information is maintained in a central place, and separated from the actual request sent from the goal op. In fact, it's completely separated from the goal op concept. In practice, a movement request could be sent from anywhere and the movement system will handle it centrally. When the requester is no longer interested in the request it sent, it simply cancels the request. This doesn't mean the character will stop immediately and loose all the information, but rather the interest in that request has expired.

#### Planning

Prior to Crysis 3 it was hard to know what was being processed right now and what was coming up. There was no bigger plan and the logic was scattered all over the place with lots and lots of branching. For Crysis 3 we try to separate this spaghetti into blocks of logic. These "movement blocks" are responsible for their own isolated task, such as FollowPath, LeaveCover and UseSmartObject. Many Blocks together in a sequence comprise a Plan, and the Plan is produced by a Controller with a string-pulled path as input. We only scratched the surface of what could potentially be planned, but it will still help us get an overview of where we are in the bigger Plan.

### Disclaimer

It should be noted that this system was not designed and written for perfection, but should be considered a product of heavy refactoring of the existing code base. It's likely not suitable for all game titles.

### Using The System

- Fill out a MovementRequest object with information about the destination, style and a callback. Queue it in the MovementSystem and receive a MovementRequestID. Use this if you want to cancel the request.
- Sit back and wait for the MovementSystem to satisfy your request. Once your request is satisfied you will get notified via a callback.

### How It Works Internally

- Fill out a MovementRequest object with information about the destination, style and a callback. Queue it in the MovementSystem and receive a MovementRequestID. Use this if you want to cancel the request.
- The MovementSystem creates an internal representation of the character that is referred to as the MovementActor. This is the container for all internal states and the proxy to all external states/logic related to a character. It binds a MovementController to the actor. Right now, there's only one available - GenericController - which is the result of what was done before. This would ultimately be splitted up into specific ones for the Pinger, Scorcher, BipedCoverUsed etc. The Controller term is confusingly similar (the same) as the one seen on the game side. The reason is because these should merge. There might not be time enough for that on Crysis 3, however.
- The MovementSystem tells the Controller that there's a new Request that it should start working on. The GenericController kicks off the path finder.
- Once the path finding result is in, the GenericController produces a Plan that it starts to follow.
- When the GenericController finishes the last Block in the Plan, it tells the MovementSystem it finnished.
- The MovementSystem notifies the requester of the success.
- The MovementSystem moves on to the next request.

### Notes / Things That Could Be Improved

- Remove the request queue and only allow one request at a time. If a request is coming in while there is already one, interrupt the current one and report it.
- Validate pipe user before proceeding with the update.
- Movement Requests are being processed one at a time, in FIFO order.
- Movement Requests are immutable; it's impossible to change a request once it has been queued. Your only option is to cancel a request and queue a new one.
- When the 'UseSmartObject' movement block detects that the exact positioning system fails to position a character at the start of a smart object it reports this through the agent's bubble and in the log, and then resolves by teleporting to the end of the smart object and proceeds to the next block in the plan.
- The GenericController is only allowed to start working on a new request while it's executing a FollowPath block. It then shaves off all the subsequantial blocks so that the Actor doesn't find himself in the middle of a smart object when the planning takes place. This could be improved by allowing the Controller to produce a part of the plan, further ahead, and patch it all up with the current plan.
- The Plan isn't removed when a Request is canceled. This is because a subsequent 'Stop' Request or 'Move' Request should take it's place. Until such a Request has been received, the Controller has little knowledge about what the best thing is to do.
- The path finding request is being channeled through the pipe user and it returns the result to the pipe user too, and stores it in m_path. This path is then extracted by the AI movement controller. It would be better if the path finder could be employed directly by the movement controller and skip the pipe user as a middle layer.
- The AI movement controller code would fit better on the game side, since that's where the information about the characters should live. This shift might never happen for Crysis 3 as it's a short project and relatively closed off from other projects so it might as well live in the AI module.
- Merge with the movement transitions that are handled on the game side.
- Being able to pull out the request at any time makes the code slightly more complex since we can't rely on that fact that the controller is always working on a request that still exists. We could keep it around, flag it as abandoned and clear the callback.
- The code would maybe be nicer if we'd handle the planning and the plan execution through two different code paths instead of one.
