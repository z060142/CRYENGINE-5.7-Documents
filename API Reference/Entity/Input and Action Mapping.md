# Input and Action Mapping

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/29428286
- Page ID: 29428286
- Breadcrumb: Entity > Input and Action Mapping
- Parent: Entity

## Content

##
Overview

Input in the engine is managed by
**
CryInput
**
, a system that collects and abstracts away platform-specific input data. Although it is possible to get device-specific data from the
[IInput](/docs/static/engines/cryengine-5/categories/28704770/pages/29797195)
 interface directly, games typically use the action mapping system, exposed via
[IActionMapManager](/docs/static/engines/cryengine-5/categories/28704770/pages/29797188)
.

The purpose of the action mapping is to support getting input from multiple device types instead of the developer having to hard-code devices in game logic. For example, a “jump” action could be tied to the keyboard’s space key and a gamepad’s A button – regardless of which is pressed, the “jump” action would be sent to code, meaning no extra work is needed to handle different or new devices.

Note that most of the input and action map handling is automated by the Input Component in the default components plug-in, see
Cry::DefaultComponents::CInputComponent
.

##
Table of Contents

[API Types](#api-types)
[Low-level input](#low-level-input)
[Action maps](#action-maps)
[Conclusion](#conclusion)

##
API Types

-
[IInput](/docs/static/engines/cryengine-5/categories/28704770/pages/29797195)

-
[IActionMapManager](/docs/static/engines/cryengine-5/categories/28704770/pages/29797188)

##
Low-level input

The low-level
[IInput](/docs/static/engines/cryengine-5/categories/28704770/pages/29797195)
 interface abstracts platform and device-specific logic for receiving input events. This is achieved by the
[IInputDevice](/docs/static/engines/cryengine-5/categories/28704770/pages/29797349)
 interface, traditionally implemented in the
CryInput m
odule. Each input device is responsible for communicating with the device API (for example DirectX Input), and then call
IInput::PostInputEvent
 to report input from the user.

Once an event is posted, input listeners (see
[IInputEventListener](/docs/static/engines/cryengine-5/categories/28704770/pages/29797348)
) are notified to handle the event. One example of this is the action map system - listening for raw input events and forwarding it to any gameplay actions that should respond.

##
Action maps

Represented by the
[IActionMap](/docs/static/engines/cryengine-5/categories/28704770/pages/29797189)
 interface, an action map represents a group of actions (see
[IActionMapAction](/docs/static/engines/cryengine-5/categories/28704770/pages/29797192)
) that are individually triggered by raw input. The concept of grouping allows us to separate gameplay logic into modular parts, for example to toggle an "in air" and "on ground" state, and only allow certain actions to be triggered in a certain gameplay state.

Game code can listen to action map events by implementing the
[IActionListener](/docs/static/engines/cryengine-5/categories/28704770/pages/29797186)
 interface, receiving callbacks when actions from a specific action map are triggered, see the example below.

[Example](/docs/static/engines/cryengine-5/categories/28704770/pages/29797186)

Also see
[ActionMapManager](../CRYENGINE%20Engine%20Code/Engine%20Modules/CryAction/ActionMapManager.md)
 and
[Setting Up Controls and Action Maps](../CRYENGINE%20Game%20Code/Miscellaneous%20Game%20Code/Setting%20Up%20Controls%20and%20Action%20Maps.md)
.

Using the Input Component causes it to register its own action maps, and reset the Action Map manager; the Input Component and Action manager cannot be used at the same time.

So you should either:

-
Use a single Input Component to handle input logic (for simple inputs per-level/entity)

-
Use the Action Map manager manually in code, and not use any Input Components (either in code or in the Sandbox Editor).

##
Action rebinding

It is common for games to implement a user interface for remapping inputs based on their preference. The action map system facilitates this by allowing the rebinding of actions, using the
[IActionMap::ReBindActionInput](/docs/static/engines/cryengine-5/categories/28704770/pages/29797189)
function.

[Example](/docs/static/engines/cryengine-5/categories/28704770/pages/29797189)

##
Conclusion

This concludes the article on Input and Action Mapping. You may be interested in:

-
[Physics and Movement](Physics%20and%20Movement.md)

-
[Characters and Animations](Characters%20and%20Animations.md)

-
[Networking](Networking.md)

-
[Audio](Audio.md)

-
[Execution Order and Lifecycle](Execution%20Order%20and%20Lifecycle.md)
