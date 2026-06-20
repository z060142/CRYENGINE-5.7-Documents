# Smart Objects Editor***

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/27594510
- Page ID: 27594510
- Breadcrumb: Editor Tools > Deprecated Tab > Smart Objects Editor***
- Parent: Deprecated Tab

## Child Pages

- [Setting Up a New Smart Objects Behavior***](Smart%20Objects%20Editor/Setting%20Up%20a%20New%20Smart%20Objects%20Behavior.md)

## Content

##
Overview

The SmartObject system is used to create general and level specific behaviors. The term SmartObject describes an object that is set up to interact with one or more other objects in the game.

Specific rules can be created that define which object will interact with which other object. These rules are based on the class and state of an object and apply to all objects in the game completely independent from the object model or the level the object is placed in.

The SmartObject system can be used for:

-
Creating puzzles.

-
Creating automatic doors, traps, and other devices.

-
Creating background behaviors for a level such as moving things, machines, etc.

-
Controlling AI behavior.

-
Adding 'scripted' AI moments to the level.

-
Setting up special navigational spots in the level.

-
SmartObject rules are not stored within the
**
.cry
**
 file of the level, but in a separate
**
XML
**
 file.

##
The Smart Objects Editor

The Smart Objects Editor is integrated into Sandbox and can be opened from the "View/Open View Pane" menu. This is the tool that is used to create and edit all rules.

![Image](https://www.cryengine.com/docs/static/attachments/27570805)

The UI of the Editor is split into four parts:

![Image](https://www.cryengine.com/docs/static/attachments/27570804)

##
1. Rules Tree

This window provides an overview about all existing SmartObject rules. The explorer-like display helps organizing your rule sets.

##
2. Rule Details

The details of a SmartObject rule can be viewed in this window. While the lower part of the window shows a description of the selected rule, the upper window part provides an overview over all rules in the currently selected folder.

Rules can be moved between the different folders by dragging and dropping them to the desired place. Greyed out rules are currently deactivated.

Rules can be sorted by clicking on the buttons on the top of each column. To hide or add columns, right-click on the buttons and select the desired column.

##
3. Rule Properties

The Properties window contains all settings that can be made for a rule. The settings made in this window determine which action will be executed and whether the rule is valid or not.

**
Property
**
 |
**
Description
**
 |

**
Name
**
 |
The name of the SmartObject rule can be entered here.
 |

Description
 |
The description of the SmartObject rule can be entered here. This description will be shown in lower part of the rule overview window. Make sure all the rules you create have a thorough description.
 |

Location
 |
The location is the name of the folder the rule is placed in. Subfolders can be created using '\'. Entering
*
'Test'
*
 for example will place the rule in a folder named 'Test', entering
*
'Test/MoreTest'
*
 will place the rule in the folder 'MoreTest' in the 'Test' folder. The location of a rule can always be changed later if reorganization should become necessary. There are two ways to move a rule from one folder to another. The first is changing the location string, and the second is to drag and drop the rule from the rule details window to the desired folder in the rule overview window.
 |

Enabled
 |
If this check box is unset, the according rule will not be applied. As a default new rules are not enabled.
 |

Template
 |
Template used on this Smart Object Rule.
 |

Navigation Rule
 |
A rule can be marked as a navigational rule by selecting this option. A navigational rule is a special type of rule which can be used to create doors and connections between navigation modifiers.
 |

Event
 |
Event on which this rule will be triggered.
 |

**
User
**
 |
The settings in this category define the user of a the rule.
 |

Class
 |
SmartObject class of the user. Only users of this class will be considered.
 |

State Pattern
 |
State pattern to match on the user class. Only users which state matches the state pattern will be considered.
 |

Helper
 |
The selected helper will be used, instead of the position and orientation of the user SmartObject class.
 |

Max. Alertness
 |
Can be 0,1 or 2. The alertness set here defines how alarmed a user is allowed to be. If the alertness is set to 0 for example the rule will not be valid if the user is in any alerted state.
 |

**
Object
**
 |
Contains all setting that define the object of a SmartObject rule.
 |

Class
 |
SmartObject class of the object. Only objects of this class will be considered.
 |

State Pattern
 |
State pattern to match on the object class. Only objects which state matches the pattern will be considered.
 |

Helper
 |
The selected helper will be used, instead of the position and orientation of the object SmartObject class.
 |

Cost Multiplier
 |
The distance between helpers multiplied with this value gives the cost of passing through.
 |

**
Navigation
**
 |
If the rule is a navigational rule, the according helpers can be defined in this category.
 |

Entrance
 |
The entrance helper of the navigational rule is selected here.
 |

Exit
 |
The exit helper of the navigational rule is selected here.
 |

**
Limits
**
 |
The options in this category determine the distance and orientation between the user and the object of the rule.
 |

Distance from
 |
The minimum distance which has to be between user and object.
 |

Distance to
 |
User and object must not be further away from each other than the distance entered here.
 |

Orientation
 |
The angle entered here describes the orientation of the user to the object. A angle of 360 means the rule will always be valid, no matter if the user looks at the object or not.
 |

User's Target
 |
Object's orientation limit towards the users attention target.
 |

**
Delay
**
 |
The settings made in this category determine how long it will take for an action to start.
 |

Minimum
 |
The minimum amount of time it will take for the action to be executed.
 |

Maximum
 |
The maximum amount of time it will take for the action to be executed.
 |

Memory
 |
This value tells the user how long to remember the connection to the object.
 |

Randomness
 |
This value sets how much randomness will be added between the minimum and the maximum delay.
 |

**
Multipliers
**
 |
The additional settings in this category are used further define rule and emphasize certain aspects.
 |

Proximity
 |
This value sets the importance of the proximity of the object to the user. This value can be used be the most far away objects the first to be used by the user.
 |

Orientation
 |
This value sets the importance of the orientation of the user towards the object.
 |

Visibility
 |
This value determines how importance the visibility between user and object is.
 |

Randomness
 |
This value determines how much randomness will be added between the values.
 |
 |

**
Action
**
 |
Not only the action itself can be selected in this category, but the pre and post action states. The pre action states are set before the action is started and prevents it to be started multiple times.

The post action states are set automatically after the action has ended. Although it is possible, it is not necessary to set the post action state manually inside the action itself.
 |

LookAt On
 |
The value entered here describes when the user will turn to look at the object in relation to the total duration before the action is being executed. The value is entered as percent, that means a value of 50% will make the user look at the object after 2 second for a duration of 4 seconds. This LookAt behavior is only applied if the user is a character. If the user is a box for example it will not turn in direction of the object.
 |

User: Pre-Action State
 |
The user will be set to the state pattern selected here before the action starts.
 |

Object: Pre-Action State
 |
The object will be set to the state pattern selected here before the action starts.
 |

Action Type
 |
The action type that has to be executed can be selected here.
 |

Action Name
 |
The action that has to be executed can be selected here. When the edit field is clicked the action selection window opens. If an action that is needed does not exist, it can be created in this window.
 |

Early Path Regeneration
 |
Decides when the path gets regenerated, at the animation start (true) or after the end (false).
 |

User: Post-Action State
 |
The state pattern selected here will be applied to the user after the action has ended.
 |

Object: Post-Action State
 |
The state pattern selected here will be applied to the object after the action has ended.
 |

**
Exact Positioning
**
 |
Makes the AI agent move to the exact start position of the Smart Object before performing the action, so the animation perfectly matches the Smart Object shape.
 |

Speed
 |
Movement speed while approaching the helper point.
 |

Stance
 |
Body stance while approaching the helper point.
 |

Animation Helper
 |
Object's helper point at which the animation will be played. Default is the entrance helper point.
 |

Approach Helper
 |
Object's helper point to approach before the animation play. If empty, the animation's helper is used.
 |

Start Radius
 |
Distance from Smart Object start point required for starting the animation.
 |

Direction Tolerance
 |
Maximum difference between AI and smart object start point orientation - if the AI is not oriented like that, it's rotated before starting.
 |

Target Radius
 |
Target radius (tolerance) for playing animation.
 |

##
4. Tasks

The Tasks window contains all controls to create, edit and delete new rules and helpers.

##
Rules

A SmartObject rule describes the relation between two SmartObject classes. Whenever the conditions of a rule is matched, a specific AIAction will be executed.

A SmartObject rule consists of:

-
A 'User' and 'Object' SmartObject class.

-
A state pattern for the 'User' and 'Object' class, which has to be matched.

-
Various additional parameters to further define the rule (Distance, Orientation, etc).

-
An AIAction to be executed if all conditions are matched.

##
Helpers

SmartObject helpers store position offsets within a SmartObject class. These helpers can be accessed from within an action graph using the 'SmartObjectHelper' node which outputs all neccessary information. Can also be accessed for example from the Exact Positioning Parameter group Animation and Approach Helper.

A helper is always attached to the SmartObject class and is in no way related to the entity model. Every AIAction can automatically access all helpers, no matter what class they are attached to.

##
Smart Objects Helper Editor UI

Smart object helpers are oriented points attached to smart objects. They are used to define some specific points or directions relative to current smart object position and orientation. Their position and orientation can be obtained using a flow graph node. In some specific cases their position and orientation will be also used internally within the Smart objects subsystem, and by now this happens only in the case when smart objects are used for navigation. Each smart object class has its own set of helpers. All helpers are uniquely named within a smart object class. All smart objects of a particular smart object class have attached their own copy of helpers.

Helpers are defined using the Smart Objects Editor window. Its Tasks bar contains the group Helpers where initially only the command Edit is available. Since helper definitions belong to smart object classes, pressing the Edit command brings up a dialog window showing a list of all known smart object classes. By choosing one of them helper editor mode gets activated. The command Edit will change its caption to Editing showing the chosen smart object class. Only the helpers belonging to chosen smart object class will be available for editing.

In helper editor mode the following operations are available:

-
The command New in group Helpers allows new helpers to be created.

-
Selecting any object belonging to the smart object class chosen for editing shows all helpers as small wire-frame boxes connected to selected object with lines.

-
Boxes shown to represent the helpers are selectable in the Editor or from the list by helper name using the command Editing.

-
Selected helpers can be moved and rotated in the Editor.

-
Selected helper can be deleted using the command Delete of commands group Helpers.

-
The command Done terminates helper editor mode.
Note: Smart object helper definitions are stored in the file:
`
Game/Libs/SmartObjects.xml
`

##
Adding_Helpers_to_a_SmartObject

![Image](https://www.cryengine.com/docs/static/attachments/27570803)

To add a new helper to a SmartObject:

-
Select the entity and assign the correct SmartObjectClass.

-
Click
**
Edit
**
 in the Smart Objects Editor window. A dialog window appears. If no SO class is selected it means that the entity is not registered as a smart object yet so start AI/Physics and exit it to refresh the system. Deselect and select the entity once again and repeat this step.

-
Choose the smart object class for which you want to edit the helpers (if some other is already chosen) and click
**
OK
**
.

-
Click the
**
New
**
 button in the Helpers section. A new dialog window appears.

-
Type the name of the helper you want to create and click
**
OK
**
. The helper will be created and (if the entity is still selected) appears in the editor's main view as a small yellow wire box. It is already selected. When the mouse is pointed over the box, its name will be shown next to it.

-
Use the Move and Rotate tools to adjust its position and orientation. Note that if it becomes deselected or another object is selected the helper will disappear. Select the entity again and the helper will appear again. Select the helper.

-
Finally, click
**
Done
**
 in the Helpers section to exit the "edit helpers" mode.

##
Accessing Smart Object Data Outside the Smart Object Editor

##
SmartObject Classes

Almost all entities in the game can have a Smart Objects class. Setting a Smart Objects class for an entity does not change anything on the entity itself, it is only an additional information for the Smart Objects system.

Whether an entity can be assigned a Smart Objects class or not can be seen in the properties window of the entity.

![Image](https://www.cryengine.com/docs/static/attachments/27570806)

*
SmartObject class property
*

The SmartObject class of an entity can be set by clicking in the edit field of the '!SmartObjectClass' property. An entity can have any number of SmartObject classes.

If an entity has more than one SmartObject class, every rule which is assigned to this class will be applied to this entity.

![Image](https://www.cryengine.com/docs/static/attachments/27570807)

*
SmartObject class selection window
*

##
AIActions

An AIAction is a special type of Flow-Graph that is beeing executed by a SmartObject rule if its condition are matched. IActions can be executed from within any Flow-Graph using the AIExcute node as well, but the normally they are called by a SmartObject rule.

The main difference between a normal Flow-Graph and an AIAction is that an AIAction is limited to use only the user and the object of a SmartObject rule as target entities within the graph.

##
ActionStart/ActionEnd

Whenever a new AIAction is created two nodes will be added to the graph automatically:

ActionStart and !ActionEnd. These nodes are used to start and end the AIAction.

![Image](https://www.cryengine.com/docs/static/attachments/27570812)

*
Default AIAction graph
*

The only entities that can be used are the user and the object entity of an SmartObject rule. Although every other entity can be added to the action graph, only user and object entity ID's are valid.

Whenever an AIAction is started, the ActionStart node outputs the ID's of the user and the object on the according ports. This pulse can be used to trigger all necessary nodes, just like in a normal graph.

##
User and Object IDs

There are two ways of selecting the target entity for a node in a action graph: Connecting the ActionStart output ports to the according ID input port, or selecting the target entity from the context menu of the entity.

![Image](https://www.cryengine.com/docs/static/attachments/27570810)

*
Using the context menu to select the target entity.
*

![Image](https://www.cryengine.com/docs/static/attachments/27570811)

*
Assigning the target entity externally.
*

##
Organizing AIActions

Like normal Flow-Graphs, AIActions can be categorized in different folders.

To place an AIAction into a folder, open the context menu on the action in the 'Flow Graphs' window and select the 'Change Folder' option. A new folder will be created when the a new folder name is entered.

##
States

For both the user and the object entity of a SmartObject rule a state pattern can be selected. If this pattern is matched the according AIAction of the rule is being executed.

A SmartObject class is not limited to have only one state. You can create as many states for a class as you want.

A state pattern consists of a set of sub patterns which each contain two sets of states, an 'Include' and 'Exclude' set. The 'Include' set determines which states have to be set.

If the 'Include' set contains three different states, all these states have to be set for the pattern match to be successful. All states that are added to the 'Exclude' set must not be be set for a positive pattern match.

![Image](https://www.cryengine.com/docs/static/attachments/27570809)

*
A state pattern consists of an 'Include' and an 'Exclude' set
*

##
Modifying States

To modify a state, a state pattern has to be set for a SmartObject class. All states in the Include set of this pattern will be added to the class and all states from the Exclude set will be removed. This pattern for example would remove the states 'Observing' and 'PrepareCombat' from the according entity and add the states 'Alerted' and 'Combat'

*
Example pattern
*

The states of an object can be changed in different ways:

##
Using the Pre- and Post-Action Settings

The pre and post action settings in the rule properties can be used to set the states. This is the fastest way of setting states.

##
Using the AIModifyStates Node

The AIModifyStates node can be used in action graphs or normal graphs to modify the states of an entity.

##
Setting the State in the Scripts

You can also modify the SmartObject states using a LUA script any time. You have to provide the entity ID and the state pattern string as parameters.

Just call:

```

`
AI.ModifySmartObjectStates( _EntityID_ , _StatePattern_ )
`

```

Example:

```

`
!AI.ModifySmartObjectStates( entity.id, "-Idle" );
`

```
