# Dialog Editor*

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/44959678
- Page ID: 44959678
- Breadcrumb: Editor Tools > Deprecated Tab > Dialog Editor*
- Parent: Deprecated Tab

## Content

As of release 5.6, the Dialog Editor is no longer supported in Sandbox and some functionalities may not work as expected.
**
The Dynamic Response System (DRS)
**
 can be used when working on dialogues instead.

For more information about that tool, please refer to the
[/docs/static/engines/cryengine-5/categories/23756816/pages/36870836](
Dynamic Response System
)
 page.

##
Overview

The Dialog Editor is used to play spoken words in CRYENGINE during normal game sequences and in cutscenes. The Dialog Editor references specific lines of dialog, and is fully compatible with regional language localization and subtitling.

The functions of the Dialog Editor can be referenced using the Flow Graph.

[Image: /docs/static/attachments/44959679]

##
The Dialog Editor

Instead of a menu system, there are two buttons at the top of the editor.

[Image: /docs/static/attachments/44959680]

-
**
Add ScriptLine:
**
 Adds a line to the current dialogscript.

-
**
Delete ScriptLine:
**
 Deletes a line from the current dialogscript.
The
**
Dialogs
**
 panel contains a browser for all dialog scripts organized within folder
`
Libs\Dialogs
`
. By default editing dialogs is locked to remind that editing happens locally.

Right-clicking on the script and selecting
**
Local Edit
**
 will enable editing.

[Image: /docs/static/attachments/44959681]

The task menu allows access to management options for the dialog menu.

[Image: /docs/static/attachments/44959682]

-
**
New:
**
 Allows the creation of new DialogScripts and dialog script groups.

-
**
Delete:
**
 Deletes the currently selected !DialogScript, if it is not write protected. Deleting the last remaining DialogScript will cause its parent group to also be deleted.

-
**
Rename:
**
 Brings up a rename dialog for the !DialogScript. Renaming its parent group will create or move the DialogScript to the defined group.
The description box shows details and properties of the lines used within the !DialogScript.

[Image: /docs/static/attachments/44959683]

Underneath the description is the main panel for editing dialog lines.

[Image: /docs/static/attachments/44959684]

Setting

 |
Description

 |

**
Line
**

 |
Current line. Click this column to select the whole line. You can then drag the line around. To add a new line, double click in free area or use
**
Add ScriptLine
**
 from the toolbar.

To delete a line press
**
Delete
**
 or use
**
Delete
**

**
ScriptLine
**
 from the toolbar. Double-click to play or stop the Sound of the Line.

 |

**
Actor
**

 |
The Actor for this line. Select this from from the combo-box. Any Entity can be an Actor. An Entity can be assigned as Actor using the Dialog:PlayDialog flownode.

 |

**
AudioID
**

 |
The AudioControlID to be triggered.

If a sound is specified the time of 'Delay' is relative to the end of the sound.

**
Note:
**
 The sound name will show no *.wav extension. If a sound is specified the time of 'Delay' is relative to the end of the sound.

 |

**
Animation
**

 |
Name of Animation Signal or Action. You should select an entity in the main view first and then browse its signals/actions.

 |

**
Type
**

 |
Signal = OneShot animation. Action = Looping animation. Animation can automatically be stopped, when Sync is enabled.

 |

**
EP
**

 |
When checked, Exact Positioning (EP) will be used to play the animation. The target for the EP is the LookAt target. If you want to make sure that an animation is exactly oriented, use this option.

 |

**
Sync
**

 |
When checked, the animation or Action will automatically stop when the sound ends.

 |

**
FacialExpr.
**

 |
Facial expression. Normally, every sound is already lip-synced and may already contain facial expressions. Use with care.

This feature can be useful when you don't play a sound, but simply want the Actor make look with a specific mood or expression. Use #RESET# to reset expression to default state.

 |

**
Weight
**

 |
Weight of the facial expression [0-1]. How strong the facial expression should be applied. When sound already contains a facial expression, use only small values < 0.5.

 |

**
Fade
**

 |
Fade-time of the facial expression in seconds. How fast the facial expression should be applied.

 |

**
LookAt
**

 |
Lookat target of the Actor. Actor will try to look at his target before he starts to talk/animate. Sometimes this cannot be guaranteed.

Also, while doing his animation or talking he may no longer face his target. For these cases use Sticky look at. To disable sticky look-at use #RESET#.

 |

**
   Sticky
**
 |
   When you tell an Actor to look at its target, it's only applied right at the beginning of the current script line. If you want to

   make him constantly facing you, activate Sticky lookat.

   You can reset Sticky lookat by #RESET# as LookAt target or a new lookat target with Sticky enabled.
 |

**
Delay
**

 |
Delay in seconds before advancing to the next line. When a sound is played, Delay is relative to the end of the sound.

So, to slightly overlap lines and to make dialog more natural, you can use negative delays. When no sound is specified, the delay is relative to the start of the line.

 |

**
Description
**

 |
Description of the line.

 |

Dynamic Help underneath the main panel displays context sensitive help for the currently selected element of the dialog editor.

[Image: /docs/static/attachments/44959685]

##
Triggering a Dialog in Flow Graph

*
A simple dialog setup.
*

[Image: /docs/static/attachments/44959686]
*

*

The Area Trigger entity Enter port links to the Play Port of the PlayDialog node. This will cause the dialog node to play when the Enter condition of the trigger is fulfilled. This may be caused by traditional methods (the player enters the trigger), or by manually triggering the condition using a trackview event track trigger on the object.

The actors defined within your by DialogScript Actor property in each line of dialog are listed in the node. These actors are defined by the entities linked to the appropriate port of the flownode.

Input Ports

 |
Description

 |

**
Play
**

 |
Starts the dialog node playing.

 |

**
Stop
**

 |
Stops the dialog node playing.

 |

**
Dialog
**

 |
The DialogScript which the node will play.

 |

**
Startline
**

 |
The line of the DialogScript which the node will play.

 |

**
AIInterrupt
**

 |
Set the level of alertness at which the AI will abort the dialog.

 |

**
AwareDistance
**

 |
Max. Distance the player is considered listening. 0 disables this check.

 |

**
AwareAngle
**

 |
Max. view angle the player is considered listening. 0 disables this check.

 |

**
AwareTimeOut
**

 |
Time after which the player will be considered not listening any more when out of range.

 |

**
Flags
**

 |
Additional flags for dialog options.

 |

**
Buffer
**

 |
The dialog buffer type. Only one dialog can be played each time in the same buffer. Other dialogs in the same buffer get queued and played back once the buffer is free again. The different buffers have no priorities and can't block each other. The buffer types can be defined here:
*
Libs/FlowNodes/DialogFlowNodeBuffers.xml
*

 |

**
BufferDelay
**

 |
The delay in seconds after a queued dialog starts to play once the buffer is emptied.

 |

**
Actor X
**

 |
Defines the objects to be used as actors for the scene. Actor numbers defined in the dialog editor.

 |

**
Output Ports
**

 |
**
Description
**

 |

**
Started
**

 |
Triggered when the dialog has started playing dialog.

 |

**
Done
**

 |
Triggered when the dialog node has stopped performing actions.

 |

**
Finished
**

 |
Triggered when the dialog node has finished playing dialog.

 |

**
Aborted
**

 |
Triggered when the dialog node action has been halted by any influence.

 |

**
PlayerAborted
**

 |
Triggered when the dialog node action has been halted by player action.

 |

**
AIAborted
**

 |
Triggered when the dialog node action has been halted by AI action.

 |

**
ActorDied
**

 |
Triggered when any actor in the scene dies.

 |

**
Lastline
**

 |
Outputs the last line spoken.

 |

**
Curline
**

 |
Outputs the current line spoken.

 |

##
The Dialog Browser

The dialog browser can be accessed on the Sound Menu as well as the
**
Line
**
 property of the Dialog Entity. Use the Dialog Browser to select a line of dialog.

[Image: /docs/static/attachments/44959687]

##
CVARS

**
g_debugDialogBuffers 1:
**
 Enables the on screen debug info for flownode dialog buffers.

**
s_DialogVolume:
**
 Sets the volume of all dialog sounds. Default is 1, which is full volume.

**
s_GameDialogVolume:
**
 Controls the dialog volume for game use. Default is 1, which is full volume.

[#the-dialog-editor](
The Dialog Editor
)
[#triggering-a-dialog-in-flow-graph](
Triggering a Dialog in Flow Graph
)
[#the-dialog-browser](
The Dialog Browser
)
[#cvars](
CVARS
)
