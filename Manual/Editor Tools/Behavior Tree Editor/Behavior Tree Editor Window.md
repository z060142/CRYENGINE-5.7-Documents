# Behavior Tree Editor Window

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/36869459
- Page ID: 36869459
- Breadcrumb: Editor Tools > Behavior Tree Editor > Behavior Tree Editor Window
- Parent: Behavior Tree Editor

## Content

##
The Editor

![Image](https://www.cryengine.com/docs/static/attachments/36849222)

*
Editor window
*

##
1. Menu

##
File

Option

 |
Description

 |

**
New
**

 |
Opens the file explorer to create a new behavior tree in the directory of choice.

The created tree is saved as an XML file.

Previously created behavior trees can be accessed via the Behavior Tree Editor regardless of their save locations.

However, for them to be used within Sandbox and associated with AI characters correctly, behavior trees need to be saved under
*
Scripts/AI/BehaviorTrees
*
 .

Please refer to the
[Connecting Behavior Trees](../../Tutorials/AI/Tutorial%20-%20Getting%20Started%20With%20The%20Behavior%20Tree%20Editor/Implementing%20The%20Behavior%20Tree%20in%20The%20Behavior%20Tree%20Editor.md)
 section of the Getting Started With The Behavior Tree Editor tutorial for an example.

 |

**
Open
**

 |
Opens the file explorer to locate and open the XML file of a previously created behavior tree.

 |

**
Save
**

 |
Saves changes made to the currently loaded behavior tree.

Changes cannot be saved if there are unresolved errors in the tree.

 |

**
Save As...
**

 |
Opens the file explorer to change the save destination and/or name of the currently loaded behavior tree.

 |

**
Recent Files
**

 |
Shows a list of recently loaded behavior trees.

 |

##
View

Option

 |
Description

 |

**
Show XML Line Numbers
**

 |
Enables line numbers alongside each node in the Behavior Tree Editor, which correspond to their actual line numbers in the XML format of the behavior tree.

XML line numbers are especially useful in manually locating and fixing syntax errors in the XML file of a behavior tree. An XML editor is required for the same.

 |

**
Show Comments
**

 |
Enables text boxes for developer comments alongside each node in the Behavior Tree Editor.

 |

**
Built-in Events
**

 |
Enables the
**
CryEngine
**
,
**
GameSDK
**
, and/or
**
Deprecated
**
 built-in event categories for use in the construction of a behavior tree via the Behavior Tree Editor..

When a category is enabled, the
**
Events
**
 section of the Data Definitions block (number 2 in the
*
[Editor Window](Behavior%20Tree%20Editor%20Window.md#BehaviorTreeEditorWindow-ed_window)
*
 image above) is made to include a list of events from that category. These events can be used in the tree by selecting them from the dropdown menus of nodes that require events to be specified.

Disabling a
**
Built-in Event
**
 category when its events are in use in the Behavior Tree Editor will generate error messages within the current tree.

When loading an existing behavior tree that makes use of built-in events then, please make sure to enable the required
**
Built-in Event
**
 category; not doing so will cause the Editor to declare all built-in events included within the tree as user-defined events.

 |

##
Toolbars

Option
 |
Description
 |

**
Customize
**
 |
Opens the toolbar customization window allowing users to customize existing toolbars, and/or create new toolbars within the Behavior Tree Editor.
 |

**
Lock Toolbars
**
 |
When disabled, the positions of toolbars and spacers within the Behavior Tree Editor can be changed by drag and drop.
 |

**
Spacers
**
 |
The following options allow users to use spacers in positioning their toolbars.

**
Insert Expanding Spacer
**
 |
Adds an expanding spacer to the toolbar layout; an expanding spacer pushes all elements situated at its ends to the edge of the tool window.
 |

**
Insert Fixed Spacer
**
 |
Adds a fixed spacer, which has a fixed size of one icon.
 |

The
**
Spacers
**

menu options are only available when

**
Toolbars → Lock Toolbars
**

is disabled.
 |

**
Toolbars
**
 |
Lists all default and custom toolbars (if any) created for the Behavior Tree Editor, allowing users to select which toolbar they'd like to hide or display.

 |

##
Debug

The Debug menu options provide real-time, on-screen visualization of the execution status of a behavior tree in game mode (
**
Ctrl
**

**
+ G
**
). Assuming that the behavior tree to be tested is assigned to an AI agent, the agent can be selected for debugging using the
**
ai_DebugAgent
**
CVar which accepts the following values:

-
**
closest
**
: Selects the agent closest to the Viewport camera.

-
**
centerview
**
: Selects the agent currently located at the center of the Viewport camera.

-
**
name
**
: Selects an AI agent by name, where the CVar value
**
name
**
 corresponds to the name of the target agent.
Calling the CVar without a parameter stops all visualization. Alternatively, while in game mode (
**
Ctrl + G
**
), pressing the forward-slash key (
**
/
**
) picks the AI agent located at the center of the in-game camera for debugging.

Option

 |
Description

 |

**
Show Tree
**

 |
Displays information related to the behavior tree's active branch at the top-left corner of the screen, in textual format, as follows:

```

Modular Behavior Tree '<behavior_tree_name>' for agent '<agent_name>',

```

```

<XML_line_number> ` <Type_of_executed_node>,

```

where nodes with custom information such as State Machine nodes are represented by white text, Action nodes by blue text, and other intermediate nodes by gray text.

The
**
Show Tree
**
 debugging option can also be enabled via the CVar
**
ai_ModularBehaviorTreeDebugTree.
**

![Image](https://www.cryengine.com/docs/static/attachments/36849221)

*
Show Tree
*

 |

**
Show Variables
**

 |
Displays information related to the evaluation of behavior tree variables, such that variables that return the value
*
True
*
 as their results are highlighted in yellow.

Alternatively enabled via the
**
ai_ModularBehaviorTreeDebugVariables
**
**

**
CVar.

![Image](https://www.cryengine.com/docs/static/attachments/36849220)
*
Show Variables
*

 |

**
Show Timestamps
**

 |
Displays information related to the execution of behavior tree timestamps, such that active timestamps are highlighted in yellow.

Alternatively enabled via the
**
ai_ModularBehaviorTreeDebugTimestamps
**
 CVar.

![Image](https://www.cryengine.com/docs/static/attachments/36849219)

*
Show Timestamps
*

 |

**
Show Events
**

 |
Displays the stream of events generated during execution of a behavior tree, in an Event Log at the bottom-right corner of the screen, with the most recently executed event listed at the top.

Alternatively enabled via the
**
ai_ModularBehaviorTreeDebugEvents
**

CVar.

![Image](https://www.cryengine.com/docs/static/attachments/36849546)
*
Show Events
*

 |

**
Show Log
**

 |
Displays a general purpose log of the behavior tree at the center of the screen.

Alternatively enabled via the
**
ai_ModularBehaviorTreeDebugLog
**
 CVar.

For more information on writing messages to the Debug log, please refer to the
[Use Debug Log](../../../API%20Reference/AI/Behavior%20Trees/Custom%20Nodes%20in%20C%2B%2B.md)
Technical Documentation.

 |

**
Show Blackboard
**
 |
Displays the contents of the behavior tree's Blackboard during execution.

![Image](https://www.cryengine.com/docs/static/attachments/44958972)

*
Show Blackboard
*

The Blackboard is a data structure maintained by a behavior tree, containing variables and values relevant to an AI agent.

Please refer to our
[technical documentation](../../../API%20Reference/AI/Behavior%20Trees/Behavior%20Tree%20Blackboard.md)
 for more information.

 |

**
Show All
**

 |
Enables all of the above options.

 |

**
Show Statistics
**

 |
Displays the memory usage statistics of the behavior tree.

 |

**
Execution History
**

 |
Writes the execution history of the selected AI agent(s) to a log file, on a frame-by-frame basis. The options provided by this option include:

-
**
Log execution for current agent:
**
 Logs the execution history of only the currently selected agent,

-
**
Log execution for all agents:
**
 Logs the history for all agents.

The execution history of each AI agent is written to a separate text file named
*
mbt_<agent_name>_<entity_ID>
*
, stored within the
*
\user\mbt_logs
*
 directory of a project.
 |

##
2. Data Definitions

The Data Definitions block section of the Behavior Tree Editor is where user-defined data such as Variables, Events, Timestamps and Event Handles are declared.

##
Variables

Variables are boolean in nature, the values of which are read/written during the execution and decision making process of a behavior tree.

![Image](https://www.cryengine.com/docs/static/attachments/36849217)

*
List of custom variables
*

These variables are used by behavior tree nodes, and their values are updated through the use of events and timestamps.
To insert/add a variable,

-
Click the dropdown in the
**
Variables
**
 section of the Editor and select the insert/add options from the menu,

-
This creates a new
**
Name
**
 field; enter a name for the variable in the provided field.
To remove all variables, choose the
**
Remove
**
option from the dropdown. The number included within the dropdown indicates the number of created variables in the behavior tree.

##
Events

Events are used to inform AI agents of the occurrence of specific scenarios within the game, causing them to react accordingly. For example an agent receiving the
*
OnEnemySeen
*
 event when the player is sighted, can be programmed to shoot at the player in response.

As mentioned previously, the Behavior Tree Editor already includes a number of built-in events that can be used in the development of a tree.

Although these events define circumstances most common and relevant to the AI in an FPS game, users may also define custom events.

![Image](https://www.cryengine.com/docs/static/attachments/36849213)

*
Events
*

To define a custom event,

-
Click the
**
Game Events
**
 dropdown and select the insert/add option from the menu generated.

-
This creates a
**
Name
**
field in the
**
Game Events
**
 section; enter a name for the custom Event in the field provided.
To remove all created events, select the
**
Remove All
**
 option from the
**
Game Events
**
 dropdown. The number included within the
**
Game Events
**
 dropdown indicates the number of created Events.

##
Event Handles

Event handles are used to change the value of one or more previously defined Variables when a specific Event occurs.

In case of the example provided in the
**
Events
**
 section above, the value of a variable
*
EnemySeen
*
 can be set to
*
True
*
when an agent receives the
*
OnEnemySeen
*
 event.

The agent can then be programmed to shoot at the player whenever the value of
*
EnemySeen
*
 variable is set to
*
True,
*
and to perform other behavior when
*
False.
*

![Image](https://www.cryengine.com/docs/static/attachments/36849215)

*
Event handles
*

To insert/add a new Event handle,

-
Click the
**
Event Handles
**
 dropdown, and select the insert/add option from the menu generated.

-
This creates a new entry in the
**
Event Handles
**
 section with the following columns:
Field
 |
Description
 |

**
On Event
**

 |
Specifies the Event on which the value of a Variable must be switched.

The option opens a pop-up window containing a complete list of activated
**
Built-in
**
 and custom
**
Game Events
**
; users can search for and select specific events within this list via the search bar at its top.

 |

**
Switch Variable
**

 |
A dropdown menu containing a complete list of created Variables; it specifies the Variable whose value needs to be changed on the occurrence of the event selected in the
**
On Event
**
 field.

 |

**
Value(True/False)
**

 |
Specifies the value to which the Variable in the
**
Switch Variable
**
 field must be set to, on the occurrence of the Event selected in the
**
On Event
**
 field. A ticked checkbox represents the value True, while an empty checkbox represents False.

 |

-
Enter the values in the
**
On Event
**
,
**
Switch Variable
**
 and
**
Value(True/False)
**
 fields as required.

##
Timestamps

Timestamps are useful in tracking the occurrence of events, such as when a character was last shot at/injured.

Users can define one or more Timestamps to be set when a particular Event is triggered, and these Timestamps can also be designed to be exclusive to each other.

![Image](https://www.cryengine.com/docs/static/attachments/36849214)

*
Timestamps
*

To insert/add a Timestamp,

-
Click the
**
Timestamps
**
 dropdown, and select the insert/add option from the menu generated.

-
This creates an entry in the
**
Timestamp
**
 section with the following columns:
Field

 |
Description

 |

**
Name
**

 |
Allows users to specify a custom name for the created Timestamp.

 |

**
Set On Event
**

 |
Specifies the Event on which the value of the Timestamp must be set.

The option opens a pop-up window containing a complete list of activated
**
Built-in
**
 and custom
**
Game Events
**
; users can search for and select specific Events within this list via the search bar at its top.

 |

**
Exclusive To
**

 |
A dropdown menu containing a list of all created Timestamps; a Timestamp selected in this field will be 'exclusive to' the Timestamp defined in the
**
Name
**
field of the same entry, meaning only one of the two Timestamps will be active at a time.

For example, consider two Timestamps
*
TargetSpotted
*
 that marks when the player is spotted by an enemy agent, and
*
TargetLost
*
 that marks when the agent loses sight of the player.

It would make sense to have these two Timestamps exclusive to each other, since the AI agent wouldn't spot and lose sight of the player at the same time.

 |

##
3. Behavior Tree

The Behavior Tree section is used to construct the actual structure of the tree via the Behavior Tree Editor and as a result, must always begin with a root node (denoted by the
**
Tree Root
**
 field).

The behavior of the tree is then defined by combining different types of nodes.

Based on their functionality/purpose, these nodes have been categorized into six different categories namely,
[Flow](Behavior%20Tree%20Nodes/%5BNode%5D%20Flow.md)
,
[Conditions](Behavior%20Tree%20Nodes/%5BNode%5D%20Conditions.md)
,
[Time](Behavior%20Tree%20Nodes/%5BNode%5D%20Time.md)
,
[Core](Behavior%20Tree%20Nodes/%5BNode%5D%20Core.md)
,
[Debug](Behavior%20Tree%20Nodes/%5BNode%5D%20Debug.md)
 and
[GameSDK](Behavior%20Tree%20Nodes/%5BNode%5D%20GameSDK.md)
; the general characteristics of these categories and the nodes they contain are explained in their respective sections.

To begin creating a Behavior Tree, define its first node from the
**
Tree Root
**
 dropdown in the Behavior Tree block
(number 3 in the
*
[Editor Window](Behavior%20Tree%20Editor%20Window.md#BehaviorTreeEditorWindow-ed_window)
*
 image above).

Depending on the type of node selected, enter the values of required parameters or insert/add children nodes as required.

##
Context Menus

Right-clicking within the Behavior Tree Editor opens a context menu, whose options might vary with the area clicked as follows.

Option

 |
Description

 |

**
Insert
**

 |
Used to add a Variable, custom Game Event, Event Handle or Timestamp entry to the current configuration of the Behavior Tree.

This option is only available when right-clicking the
**
Variables
**
,
**
Game Events
**
,
**
Event Handles
**
 and
**
Timestamps
**
 fields of the Data Definitions block.

 |

**
Add
**

 |
Similar to
**
Insert
**
, this option is also used to add a Variable, custom Game Event, Event Handle or Timestamp entry to the current configuration of the Behavior Tree.

Available when right-clicking the
**
Variables
**
,
**
Game Events
**
,
**
Event Handles
**
 and
**
Timestamps
**
 fields of the Data Definitions block.

 |

**
Remove All
**

 |
Removes all user defined Events from under the
**
Game Events
**
 section of the Data Definitions block.

Visible when the
**
Game Events
**
 field is right-clicked.

 |

**
Remove Children
**

 |
Removes all Event handles and Timestamps defined under the
**
Event Handles
**
and
**
Timestamps
**
 sections respectively.

Visible when the
**
Event Handles
**
 and
**
Timestamps
**
 fields are right-clicked.

 |

**
Expand
**

 |
Expands a collapsed section/node of the Behavior Tree Editor (such as
**
Variables, Events, Game Events
**
 or else), to reveal all behavior tree elements defined within that section/node.

 |

**
Collapse
**

 |
Collapses a section/node of the Behavior Tree Editor to hide elements defined within it.

 |

**
Set
**

 |
Lists all categories of available nodes, letting users add their choice of node to a behavior tree.

This option appears when right-clicking a node in the Behavior Tree Editor.

 |

**
Undo
**

 |
Reverts the last entry or change made to the current configuration of the behavior tree.

 |

**
Redo
**

 |
Restores any changes or entries made to the behavior tree, that were previously undone via the
**
Undo
**
 option.

 |

**
Cut
**

 |
Deletes and copies the content of a text field onto the clipboard.

 |

**
Copy/Paste
**

 |
May be used to copy/paste a custom Game Event, Event Handle, Timestamp, Behavior Tree structure, or the contents of a text field to/from the clipboard.

 |

**
Delete
**

 |
Completely deletes the contents of a text field.

 |

**
Copy All/Paste All
**

 |
Known issue: The
**
Copy All
**
 and
**
Paste All
**
options may not function correctly.

 |

**
Filter...
**

 |
Filters the contents of the Behavior Tree Editor on the basis of an entered string.

Clicking this option creates a search bar at the top of the Editor window, such that any string entered within this bar acts a filter; the Behavior Tree Editor will display only those tree elements that match the text of the entered string.

Pressing
**
Ctrl + F
**
 within the Behavior Tree Editor also performs the same function.

 |

**
Filter by
**

 |
**
Name
**

 |
Uses the name of the right-clicked field as a filter, such that only those Behavior Tree elements whose names match that of the right-clicked field are displayed.

 |

**
Value
**

 |
Displays those Behavior Tree elements whose values match that of the right-clicked field.

 |

**
Type
**

 |
Displays Behavior Tree elements according to the type (boolean, string, etc.) of the right-clicked field's value.

 |

 |

[The Editor](#the-editor)
[1. Menu](#1-menu)
[2. Data Definitions](#2-data-definitions)
[3. Behavior Tree](#3-behavior-tree)
[Context Menus](#context-menus)
