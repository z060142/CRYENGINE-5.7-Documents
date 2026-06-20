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
[/docs/static/engines/cryengine-5/categories/28704770/pages/29797195](
IInput
)
 interface directly, games typically use the action mapping system, exposed via
[/docs/static/engines/cryengine-5/categories/28704770/pages/29797188](
IActionMapManager
)
.

The purpose of the action mapping is to support getting input from multiple device types instead of the developer having to hard-code devices in game logic. For example, a “jump” action could be tied to the keyboard’s space key and a gamepad’s A button – regardless of which is pressed, the “jump” action would be sent to code, meaning no extra work is needed to handle different or new devices.

Note that most of the input and action map handling is automated by the Input Component in the default components plug-in, see
Cry::DefaultComponents::CInputComponent
.

##
Table of Contents

[#api-types](
API Types
)
[#low-level-input](
Low-level input
)
[#action-maps](
Action maps
)
[#conclusion](
Conclusion
)

##
API Types

-
[/docs/static/engines/cryengine-5/categories/28704770/pages/29797195](
IInput
)

-
[/docs/static/engines/cryengine-5/categories/28704770/pages/29797188](
IActionMapManager
)

##
Low-level input

The low-level
[/docs/static/engines/cryengine-5/categories/28704770/pages/29797195](
IInput
)
 interface abstracts platform and device-specific logic for receiving input events. This is achieved by the
[/docs/static/engines/cryengine-5/categories/28704770/pages/29797349](
IInputDevice
)
 interface, traditionally implemented in the
CryInput m
odule. Each input device is responsible for communicating with the device API (for example DirectX Input), and then call
IInput::PostInputEvent
 to report input from the user.

Once an event is posted, input listeners (see
[/docs/static/engines/cryengine-5/categories/28704770/pages/29797348](
IInputEventListener
)
) are notified to handle the event. One example of this is the action map system - listening for raw input events and forwarding it to any gameplay actions that should respond.

##
Action maps

Represented by the
[/docs/static/engines/cryengine-5/categories/28704770/pages/29797189](
IActionMap
)
 interface, an action map represents a group of actions (see
[/docs/static/engines/cryengine-5/categories/28704770/pages/29797192](
IActionMapAction
)
) that are individually triggered by raw input. The concept of grouping allows us to separate gameplay logic into modular parts, for example to toggle an "in air" and "on ground" state, and only allow certain actions to be triggered in a certain gameplay state.

Game code can listen to action map events by implementing the
[/docs/static/engines/cryengine-5/categories/28704770/pages/29797186](
IActionListener
)
 interface, receiving callbacks when actions from a specific action map are triggered, see the example below.

[/docs/static/engines/cryengine-5/categories/28704770/pages/29797186](
Example
)

Also see
[/docs/static/engines/cryengine-5/categories/23756813/pages/24283649](
ActionMapManager
)
 and
[/docs/static/engines/cryengine-5/categories/23756813/pages/23306384](
Setting Up Controls and Action Maps
)
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
[/docs/static/engines/cryengine-5/categories/28704770/pages/29797189](
IActionMap::ReBindActionInput
)
function.

[/docs/static/engines/cryengine-5/categories/28704770/pages/29797189](
Example
)

##
Conclusion

This concludes the article on Input and Action Mapping. You may be interested in:

-
[/docs/static/engines/cryengine-5/categories/23756813/pages/26216224](
Physics and Movement
)

-
[/docs/static/engines/cryengine-5/categories/23756813/pages/26216226](
Characters and Animations
)

-
[/docs/static/engines/cryengine-5/categories/23756813/pages/26216232](
Networking
)

-
[/docs/static/engines/cryengine-5/categories/23756813/pages/26871538](
Audio
)

-
[/docs/static/engines/cryengine-5/categories/23756813/pages/28184910](
Execution Order and Lifecycle
)
