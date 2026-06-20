# Audio Controls Editor

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/51347481
- Page ID: 51347481
- Breadcrumb: Editor Tools > Audio Controls Editor
- Parent: Editor Tools

## Content

##
Overview

All actions, events and parameters from within a project are communicated

to the selected audio middleware
 using Audio System Controls, which are mapped to one (or several) contro
ls inside
your middleware.

The connection between the Audio System Controls and the audio middleware, as well as the creation of the Audio System Controls themselves, are achieved with the Audio Controls Editor (ACE).

Since the release of CRYENGINE 5.5, ACE files are stored in middleware specific folder, so that each middleware implementation is completely separated from each other. Moreover in release 5.6, Scopes in the ACE have been replaced by Contexts.

A migration guide has hence been included at the bottom of this page, for users interested in updating their projects to Engine version 5.5 or after.

The Audio Controls Editor can be accessed via the
**
Tools ->  Audio Controls Editor
**
option of the Sandbox's Main Menu bar, and its appearance might vary depending on the audio middleware in use (ADX2, FMOD, Wwise or SDL Mixer).

Yet it always comprises of three primary panels - Audio System Controls, Properties and Audio Middleware.

These panels can be docked and undocked at any time, allowing users to alter the ACE's layout as per their preferences.

[Image: /docs/static/attachments/51347493]

The Audio Controls Editor uses icons such as
[Image: /docs/static/attachments/51347489]
 and
[Image: /docs/static/attachments/51347488]
 in its interface; these function as tooltips, indicating files that might be missing, localized, or that are not connected to any middleware controls. Hover over these icons within the tool for more information.

##
1. Menu Bar

Opened by the
[Image: /docs/static/attachments/51347501]
 icon at the top-right corner of the ACE Tool window, the Menu Bar contains the following options:

##
File

Option
 |
Description
 |

**
Save
**
 |
Saves any and all changes made within the ACE.
 |

##
Edit

Option

 |
Description

 |

**
Reload
**
 |
Reloads the ACE and middleware files, undoing all unsaved changes made to the Audio System Controls.
 |

**
Refresh Audio System
**
 |
Reloads SoundBanks, audio files and related audio
system data.

 |

**
Preferences...
**

 |
If the selected audio middleware supports projects, the project path can be edited here.

The default paths for ADX2, Wwise and FMOD Studio are
*
audio/adx2_project, audio/wwise_project
*
and
*
audio/fmod_project
*
respectively.

Since SDL Mixer doesn't work with projects, this field cannot be edited when the SDL Mixer middleware implementation is in use.

 |

##
Toolbars

**
Option
**
 |
Description
 |

**
Customize
**
 |
Opens the toolbar customization window allowing users to customize existing toolbars, and/or create new toolbars within the ACE.
 |

**
Lock Toolbars
**
 |
When disabled, the positions of toolbars and spacers within the ACE can be changed by drag and drop.
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
Lists all default and custom toolbars created for the ACE, allowing users to select which toolbar they'd like hide or display. By default, only the following toolbar is available:

**
General
**
 |
Refer to the
[/docs/static/engines/cryengine-5/categories/23756816/pages/51347481#AudioControlsEditor-SRR](
Save, Reload and Refresh Buttons
)
 section below.
 |

 |

When a tool has a toolbar, whether this is a default one or a custom one, the options above are also available when right-clicking in the toolbar area (only when a toolbar is already displayed).

##
Window

Option

 |
Description

 |

**
Panels
**

 |
Contains the
[/docs](
Audio System Controls
)
,
[/docs/static/engines/cryengine-5/categories/23756816/pages/51347481#AudioControlsEditor-contextpanel](
Contexts
)
,
[/docs/static/engines/cryengine-5/categories/23756816/pages/51347481#AudioControlsEditor-WwiseControlsPanel](
Middleware Data
)
 and
[/docs/static/engines/cryengine-5/categories/23756816/pages/51347481#AudioControlsEditor-Propertiespanel](
Properties
)
 options, allowing users to add these panels to the ACE in case these were not already included.

 |

**
Reset layout
**

 |
Restores the default layout of the ACE.

 |

##
Help

**
Option
**
 |
Description
 |

**
Go to documentation...
**
 |
Opens the documentation page for this tool.
 |

##
2. Save, Reload and Refresh Buttons

Button

 |
Name

 |
Description

 |

[Image: /docs/static/attachments/51347509]
 |
**
Save All Changes
**

 |
Saves any and all changes made within the ACE.

 |

[Image: /docs/static/attachments/51347508]
 |
**
Reload all ACE and middleware
**
**
files
**

 |
Reloads the ACE and middleware files, undoing all unsaved changes made to the Audio System Controls.

 |

[Image: /docs/static/attachments/51347507]
 |
**
Refresh Audio System
**

 |
Reloads SoundBanks, audio files and related audio
system data.

 |

##
3. Audio System Controls

The Audio System Controls panel lists all controls included within the current CRYENGINE project.

It also allows users to create, move and delete each of the different types of controls available . Controls can also be grouped into folders, which can be useful when organizing larger projects.

[Image: /docs/static/attachments/51347506]

*
Audio System Controls panel
*

##
Control Types

Control Type
 |
Icon
 |
Description
 |

**
Triggers
**
 |
[Image: /docs/static/attachments/51347486]

 |
Triggers are containers that execute the audio middleware events connected to them. A Trigger might have any number of Events connected to it.
 |

**
Parameters
**
 |
[Image: /docs/static/attachments/51347485]
 |
Parameters in the Audio System Controls are floating point values that directly influence the values of connected parameters in middleware.

 |

**
Switches
**
 |
[Image: /docs/static/attachments/51347484]
 |
A Switch is a collection of States, each of which manipulates the connected parameters of a middleware in a certain way.

An example of a commonly used Switch would be that for character footsteps, that plays different footstep sounds depending on the surface (concrete, grass, etc.).

 |

**
Environments
**
 |
[Image: /docs/static/attachments/51347483]
 |
Environments are used to drive effects like reverbs and weapon reflections, in areas such as AreaBox, AreaShape, AreaSphere or AreaSolid that are found under the
**
Area
**
 option of the
[/docs/static/engines/cryengine-5/categories/23756816/pages/36869846](
Create Object
)
 tool.
 |

**
Preloads
**
 |
[Image: /docs/static/attachments/51347482]
 |
Preloads are requests to load audio specific files (such as SoundBanks in the FMOD Studio implementation) into memory. Any number of files can be grouped into a single Preload request.
 |

**
Settings
**
 |
[Image: /docs/static/attachments/51347490]

 |
Settings are used to load or unload middleware specific settings (such as DSP Bus Settings in the ADX2 implementation).

In the ADX2 implementation, loading a Setting in the ACE applies the connected DSP Bus Setting in ADX2, while unloading it in the ACE removes the DSP Bus Setting. Only one DSP Bus Setting can be active at a time.

 |

**
Folders
**
 |
[Image: /docs/static/attachments/51347491]
 |
Folders are only used for structuring the Audio System Controls in the ACE, and have no functionality associated with them.
 |

An asterisk against a Trigger, Parameter or Switch within the Audio System Controls panel indicates unsaved changes made to that item. Folders and Libraries higher up in the hierarchy to which the unsaved Trigger/Parameter/Switch belongs will also be marked with an asterisk.

##
Adding Controls/Folders/Libraries/States

Clicking the
**
Add
**
 button at the top of the Audio System Controls panel allows users to add new Libraries, Folders, Triggers, Parameters, Switches, States, Environments or Preload Requests as children of the item currently selected within the Audio System Controls panel.

When no item is selected within the Audio Controls panel, the
**
Add
**
button creates the desired Library/Folder/Trigger/Parameter/Switch/Environment/Preload Request at the root of the hierarchy of Folders.

The
**
Add
**
 menu provides options for only those items that can be added as a children of the currently selected Library, Folder, Trigger, Parameter or Switch within the Audio System Controls panel.

For example, States can only be added to Switches. This can be done by clicking the
**
Add
**
 button, right-clicking a Switch, or by dropping a middleware parameter or VCA onto a Switch.

Alternatively, right-clicking an item within the Audio System Controls panel opens a context menu with the same options as those provided by the
**
Add
**
 button.

##
Search Bar

Allows searching within the Audio System Controls panel on the basis of a string of characters, listing only those controls whose names contain the string entered within the Search Bar.

##
Filters

The
[Image: /docs/static/attachments/51347500]
 button allows users to describe specific criteria by which the Audio System Controls panel must list created/available controls and folders. Clicking this Filter button yields options to
**
Add/Clear Criteria
**
 and
**
Save/Load
**
 custom filters as required.

Clicking the
**
Add Criterion
**
 button presents a drop down menu containing the available criteria by which controls or folders may be listed within the Audio System Controls Panel panel; depending on the criteria selected, its value can be picked from a separate drop-down, set via a True/False checkbox or an empty value field.

[Image: /docs/static/attachments/51347494]

*
Add Criterion
*

Clicking the
[Image: /docs/static/attachments/36836741]
 icon inverts the specified search criteria, while
**
Clear Criteria
**
 eliminates all specified criteria and their respective values. The
**
Save/Load
**
 Filter option meanwhile generates a pop-up window which lists all previously created filters along with options to
**
Save
**
,
**
Load
**
 or
**
Delete
**
 these; a search bar at the top of this pop-up allows filtering through the listed filters.

[Image: /docs/static/attachments/36836753]

Right-clicking the filter button also makes it possible to quickly choose a saved filter instead of having to use the
**
Save/Load Filter
**
 dialog.

Audio controls can be filtered by the values of their
**
Type
**
,
**
Valid Connection
**
,
**
In pak
**
,
**
On disk
**
,
**
Context
**
 and
**
Name
**
properties.

Property

 |
Description

 |

**
Type
**

 |
An audio control can be of the following
**
Types:
**
Trigger, Parameter, Switch, State, Setting, Environment or Preload.

This property indicates the Type of an audio control listed within the Audio System Controls panel.

 |

**
Valid Connection
**

 |
Specifies if an Audio System Control in the ACE has a connection to a control in the loaded middleware project or not. Note that only the FMOD Studio and Wwise middleware support projects.

 |

**
In pak
**

 |
Indicates if an audio control belongs to a library that exists as a
**
.pak
**
 file within the project's asset directory, or not.

 |

**
On disk
**

 |
Indicates if an audio control belongs to a library that exists on disk, or not.

 |

**
Context
**

 |
Indicates if an audio control belongs to a
**
global
**
 or user-defined Context; in the case of a user-defined Context, the name of the Context will be displayed by this property field.

 |

**
Name
**

 |
Specifies the name given to an audio control.

 |

##
Context Menu

Right clicking the column header or a specific item within the Audio System Controls opens a context menu; the options of this context menu might vary depending on the item clicked.

Option

 |
Description

 |

**
Load Global Preload Request
**

 |
This option appears only when the selected audio control is a Preload Request in a currently active Context, and
the
**
Auto Load
**
 box in the Properties panel is unticked.

It manually loads all SoundBanks connected to the Preload Request.

 |

**
Unload Global Preload Request
**

 |
This option appears only when the selected audio control is a Preload Request in a currently active Context, and
 the
**
Auto Load
**
 box in the Properties panel is unticked.

It manually unloads all SoundBanks connected to the Preload Request.

 |

**
Load Setting
**
 |
Applies the middleware specific setting that is connected to the selected audio system Setting.

In the ADX2 implementation of the audio system, users can switch between DSP Bus Settings by simply loading the desired audio system Setting using the
**
Load Setting
**
 option; the old audio system Setting is automatically unloaded.

 |

**
Unload Setting
**
 |
Removes the middleware specific setting that is connected to the selected audio system Setting.
 |

**
Execute Trigger
**

 |
Appears only when the selected audio control is a Trigger.

This option executes the right-clicked Trigger to play the middleware control connected to it. The middleware controls associated with the selected Audio System Control can be found under the
**
Connections
**
 section of the
[/docs/static/engines/cryengine-5/categories/23756816/pages/51347481#AudioControlsEditor-Propertiespanel](
Properties
)
 panel.

A Trigger may also be executed by double clicking it or by pressing the space bar when highlighted.

 |

**
Add
**

 |
Allows users to add new Libraries, Folders, Triggers, Parameters, Switches, States or Preload Requests as children of the item currently selected within the Audio System Controls panel.

When no item is selected within the Audio Controls panel, the
**
Add
**
button creates the desired Library/Folder/Trigger/Parameter/Switch at the root of the hierarchy of Folders.

The
**
Add
**
 menu provides options for only those items that can be added as a children of the currently selected Library, Folder, Trigger, Parameter or Switch within the Audio System Controls panel.

Alternatively, items can also be added to the Audio System Controls panel by clicking the
**
Add
**
 button at its top.

 |

**
Show in File Explorer
**

 |
Opens the file explorer to locate a Library on disk.

This option is only visible when right-clicking Libraries that exist on disk.

It is not available to those that are saved in
**
.pak
**
 files within the project's asset directory, or to newly created Libraries that haven't been saved by clicking the
[Image: /docs/static/attachments/51347509]
 icon at the top of the Audio System Controls panel.

 |

**
Rename
**

 |
Allows users to change the name of the currently selected control.

Note that audio controls within the
*
default_controls
*
 folder cannot be renamed.

Alternatively, a selected control/folder within the Audio System Controls panel can be renamed by pressing the
**
F2
**
 key.

 |

**
Delete
**

 |
Removes the selected control from the Audio System Controls panel.

Audio controls within the
*
default_controls
*
 folder however cannot be renamed.

Alternatively, a selected control/folder within the Audio System Controls panel can be deleted by pressing the
**
Delete
**
 key.

 |

**
Expand Selection
**

 |
Expands the folder selected within the Audio System Controls panel to list all sub-folders and Audio System Controls contained by it.

 |

**
Collapse Selection
**

 |
Collapses the folder selected within the Audio System Controls panel to hide all sub-folders and Audio System Controls contained by it.

 |

**
Expand All
**

 |
Expands all folders listed within the Audio System Controls panel to list all sub-folders and Audio System Controls contained by them.

 |

**
Collapse All
**

 |
Collapse all folders listed within the Audio System Controls panel to hide all sub-folders and Audio System Controls contained by it.

 |

##
Moving, Editing and Previewing Controls

Controls and
 folders can be moved to other folders listed within the Audio System Controls panel by simply dragging and dropping.

Folders and controls cannot be moved to the root level. Additionally, items cannot be moved into or out of of the
*
default_controls
*
 library.

The Name, Descriptions and Context of audio controls listed within the Audio System Controls panel, as well as the properties of the middleware controls connected to these Audio System Controls, can be altered via the
[/docs/static/engines/cryengine-5/categories/23756816/pages/51347481#AudioControlsEditor-Propertiespanel](
Properties
)
 panel.

NOTE:
The name of an Audio System Control can only exist once per control type. Similarly, the name of a State name can only exist once per Switch.

For example, an Audio Trigger named
*
my_trigger
*
 cannot be created if there already exists a Trigger of the same name within the project. The ACE will ensure this by renaming any subsequently created Triggers with coinciding names as
*
my_trigger2
*
,
*
my_trigger3
*
 and so forth.

When a middleware control has been connected to a Trigger in the Audio system Controls pane, the Audio Trigger can be previewed in the Audio System Controls panel by right-clicking it and selecting the
**
Execute Trigger
**
 option, double-clicking, or pressing the
**
spacebar
**
 on the selected Trigger.

Similarly, the middleware controls that have been connected to an audio Trigger may also be previewed via the Properties panel by right-clicking the connected middleware control in the Connections section, and selecting the
**
Execute Connection
**
 option, double-clicking, or pressing the
**
spacebar
**
on it when selected.

Executed triggers will stop once deselected.

##
Default Controls

CRYENGINE's Audio System contains a few default Audio Controls of the
**
Type
**
 Trigger which are auto-created when missing.

These controls are generic, hardcoded, and apply to any and every project regardless of its nature. Please ensure to connect these controls to the corresponding audio middleware representation, so as to establish a functioning production environment.

All default controls are stored in the
*
default_controls
*
 library, and cannot be deleted, renamed or moved. Neither can other audio controls be added to this library.

##
Triggers

Trigger

 |
Description

 |

**
get_focus
**

 |
Sent when the application window is in focus. Automatically unmutes all sounds in ADX2, FMOD Studio and SDL Mixer. In Wwise it needs to be connected to an
*
unmute all
*
 event.

 |

**
lose_focus
**

 |
Sent when the application window is not in focus. Automatically mutes all sounds in ADX2, FMOD Studio and SDL Mixer. In Wwise it needs to be connected to a
*
mute all
*
 event.

 |

**
mute_all
**

 |
Sent by the Sandbox's
**
Mute Audio
**
 button if not already muted. Automatically mutes all sounds in ADX2, FMOD Studio and SDL Mixer. In Wwise it needs to be connected to a
*
mute all
*
 event.

 |

**
unmute_all
**

 |
Sent by the Sandbox's
**
Mute Audio
**
 button if
**
mute_all
**
 was sent beforehand. Automatically unmutes all sounds in ADX2, FMOD Studio and SDL Mixer. In Wwise it needs to be connected to an
*
unmute all
*
 event.

 |

**
pause_all
**

 |
Automatically pauses all sounds in ADX2, FMOD Studio and SDL Mixer. In Wwise it needs to be connected to a
*
pause all
*
 event.

 |

**
resume_all
**

 |
Automatically resumes all paused sounds in ADX2, FMOD Studio and SDL Mixer. In Wwise it needs to be connected to a
*
resume all
*
 event.

 |

**
do_nothing
**

 |
Overrides the automatic stopping of StartTrigger instances by being applied to the StopTrigger property. Not displayed in the ACE, only in the
[/docs/static/engines/cryengine-5/categories/23756816/pages/51347481#AudioControlsEditor-Resource](
Resource Selector
)
, because it should not be edited.

Note that connecting any of the above Triggers in the ACE will override their default behavior.

 |

##
4. Properties Panel

The properties of controls selected within the Audio System Controls panel can be edited within the Properties panel.

The Properties panel is also where connections between audio middleware controls and controls listed in the Audio System Controls panel can be made.

##
Properties

The top half of the Properties panel contains options to edit the
**
Name
**
,
**
Description
**
 and
**
Context
**
 of controls selected within the Audio System Controls panel.

Property

 |
Description

 |

**
Name
**

 |
The name of the control. This can also be edited in the Audio System Controls panel.

 |

**
Description
**

 |
Here you can type a short description of the Audio System Control. This will also appear on mouse-over in the
[/docs/static/engines/cryengine-5/categories/23756816/pages/51347481#AudioControlsEditor-Resource](
Resource Selector.
)

 |

**
Context
**

 |
A dropdown menu containing all user-defined Contexts, allowing users to set the value of control to a
**
global
**
 or user-defined value. Please refer to the
[/docs/static/engines/cryengine-5/categories/23756816/pages/51347481#AudioControlsEditor-contextpanel](
Contexts Panel
)
 section for more information on managing Contexts.

Since the Context of Default Controls are
**
global
**
by default, the
**
Context
**
 property is hidden when a Default control is selected.

Also, the States of a Switch do not have a Context; they inherit the Contexts of their parent Switch.

 |

**
Auto Load
**

 |
Only available for Preload Requests.

Automatically loads all connected SoundBanks when enabled. If the Context of the Preload Request is
**
Global
**
, the SoundBanks are loaded on game start. If the Context shares its name with a created level however, the SoundBanks are loaded on level start, whereas a Context with a user-defined name is loaded when activated.

 |

##
Connections

To create new connections between audio system controls and audio middleware controls, simply drag the middleware control from the Audio Middleware Data panel into the Connections section of the Properties panel.

An audio middleware control can also be dragged directly into the Audio System Controls panel. This will create a compatible audio system control with the name of the audio middleware control, automatically establishing a connection between both.

The Connections section of the Properties panel lists all middleware controls that are currently connected to an Audio System Control listed within the Audio System Controls
**

**
panel.
Selecting a connected middleware control listed under the
Connections
 section of the
Properties
 panel, provides additional properties that can be edited within the Properties panel.

T
hese properties differ depending on the audio middleware used, the type of middleware control selected, and the type of the audio system control it is connected to.

##
ADX2

When connecting an ADX2 Cue to an audio Trigger, the following options are available.

Option

 |
Description

 |

**
Action
**

 |

-
**
Start
**
 - Indicates that the Cue will start playing when the Trigger is executed.

-
**
Stop
**
 - Indicates that the Cue will be stopped when the Trigger is executed.

-
**
Pause
**
 - Indicates that the Cue will be paused when the Trigger is executed.

-
**
Resume
**
 - Indicates that the Cue will be resumed when the Trigger is executed.
 |

When connecting an ADX2 Snapshot to an audio Trigger, the following options are available.

Option

 |
Description

 |

**
Action
**

 |

-
**
Start
**
 - Indicates that the Snapshot will be activated when the Trigger is executed.

-
**
Stop
**
 - Indicates that the Snapshot will be deactivated when the Trigger is executed.
 |

**
Changeover Time
**
 |
The duration of time, in milliseconds, it takes to change the value of the Snapshot.

 |

When connecting an ADX2 AISAC - Control, Category or Game Variable to an audio system Parameter, the following options are available.

Option
 |
Description
 |

**
Advanced
**
 |
When this checkbox is ticked, the following options become available.

Option

 |
Description

 |

**
Multiply
**

 |
The audio Parameter value will be multiplied by this before being used to control the volume of the connected ADX2 control. Its value cannot be lower than
**
0
**
.

 |

**
Shift
**

 |
The audio Parameter value will be incremented by this before being used to control the volume of the connected ADX2 control. Its value is clamped between
**
-1
**
 and
**
1
**
.

If using
**
Multiply
**
 and
**
Shift, Shift
**
 is applied to the value before the multiplier.

 |

**
Min Value
**
 |
Defines the minimum value the parameter connection can have. This value is normalized to 0 in ADX2.
 |

**
Max Value
**
 |
Defines the maximum value that the parameter connection can have. This value is normalized to 1 in ADX2.
 |

**
Reset
**
 |
Resets the
**
Multiply,
**

**
Shift, Min Value
**
 and
**
Max Value
**
properties to their original values.
 |

 |

As ADX2 uses values between 0 -1 for all parameter types, the
**
Min Value
**
 and
**
Max Value
**
 properties make it easier for users to normalize parameter values.

For example, in the case of a
*
time of day
*
 parameter that has values between 0 and 24, setting the
**
Max Value
**
 field to 24 will normalize it to 1 in code before it is passed onto ADX2. Which means, a
*
time of day
*
 value of 12 will correspond to a normalized value of 0.5 in code, and so on.

When connecting an AISAC - Control to an audio system Environment in the ACE, the following options are available.

Option
 |
Description
 |

**
Advanced
**
 |
When this checkbox is ticked, the following options become available.

Option

 |
Description

 |

**
Multiply
**

 |
The audio Environment value will be multiplied by this before being used to control the volume of the AISAC Control. Its value cannot be lower than
**
0
**
.

 |

**
Shift
**

 |
The audio Environment value will be incremented by this before being used to control the volume of the AISAC Control. Its value is clamped between
**
-1
**
 and
**
1
**
.

If using
**
Multiply
**
 and
**
Shift, Shift
**
 is applied to the value before the multiplier.

 |

**
Reset
**
 |
Resets the
**
Multiply
**
 and
**
Shift
**
properties to their original values.
 |

 |

When connecting an AISAC - Control, Category or Game Variable to an audio State in the ACE, the following options are available.

Option

 |
Description

 |

**
Value
**

 |
 The value to set the connected ADX2 control to, when the State is activated; limited between
**
0
**
 and
**
1
**
.

 |

##
SDL Mixer

When connecting an a
udio Trigger
 to an
audio file
, the following options are available.

Option

 |
Description

 |

**
Action
**

 |

-
**
Start
**
**
 -
**
Indicates that the audio file will start playing when the Trigger is executed.

-
**
Stop -
**
Indicates that the audio file will be stopped when the Trigger is executed. If the audio file was not playing or had already stopped the event will be ignored.
**

**

-
**
Pause -
**
 Indicates that the
 SDL Mixer event will be paused when the Trigger is executed.

-
**
Resume -
**
Indicates that the SDL Mixer event
will be resumed when the Trigger is executed.
 |

**
Volume (dB)
**

 |
Maximum volume at which the audio will play when not attenuated.

 |

**
Fade-In Time (sec)
**

 |
Fade-in time in seconds.

 |

**
Fade-Out Time (sec)
**

 |
Fade-out time in seconds. Used when the event is stopped.

 |

**
Enable Panning
**

 |
Allows the playing of the audio file to be 3D positioned so that it will be panned between speakers depending on the direction the player is looking at.
**

**

 |

**
Enable Attenuation
**
 |
Ticking this checkbox makes the following options available:

Option

 |
Description

 |

**
Min Distance
**

 |
Distance at which the sound will start to attenuate.

 |

**
Max Distance
**

 |
Distance at which the sound will be completely attenuated and inaudible.

 |

 |

**
Infinite Loop
**
 |
Loops the sound infinitely when within the maximum distance that the sound is played.
 |

**
Loop Count
**
 |
If the Infinite box was not ticked, this option will appear. This is the number of times the sound is played when the Trigger is executed.
 |

When connecting an
Audio System Controls Parameter
 to an
audio file
, the following options are available.

Option
 |
Description
 |

**
Advanced
**
 |
When this checkbox is ticked, the following options become available.

Option

 |
Description

 |

**
Multiply
**

 |
The audio Parameter value will be multiplied by this before being used to control the event's volume. The value cannot be lower than
**
0
**
.

 |

**
Shift
**

 |
The audio Parameter value will be incremented by this before being used to control the event's volume. The values are clamped between
**
-1
**
 and
**
1
**
.

If using
**
Multiply
**
 and
**
Shift, Shift
**
 is applied to the value before the multiplier.

 |

**
Reset
**
 |
Resets the
**
Multiply
**
 and
**
Shift
**
properties to their original values.
 |

 |

When connecting a
Audio System Controls State
 to an
audio file
, the following option is available.

Option

 |
Description

 |

**
Volume (normalized)
**

 |
The connected event will get set to this volume. It's clamped between
**
0
**
 an
**
1
**
.

 |

When using the SDL Mixer implementation, Parameters and Switches/States can only control the volume of audio events. The value of Parameters and States are normalized volumes (0 - 1).

**
0
**
 = silent (-96dB)

**
1
**
 = the volume which is set in the event connection of a trigger with a start action.

Setting a Parameter higher than
**
1
**
 will not increase the volume beyond the value which is set in the Trigger connection. Parameters and Switches/States are set per object and affect all Triggers that use the same asset on that object.

When connecting an audio file to an Audio System Controls Preload Request, the connected file will be loaded into memory every time the Preload is loaded. Audio files which are not connected to a Preload are loaded on demand.

##
Wwise

When connecting an
Audio System Controls Parameter
to a
Wwise Parameter
, the following options are available:

Option
 |
Description
 |

**
Advanced
**
 |
When this checkbox is ticked, the following options become available.

Option
 |
Description
 |

**
Multiply
**

 |
The audio Parameter value will be multiplied by this before being assigned to the Wwise parameter.

 |

**
Shift
**

 |
The audio Parameter value will be incremented by this before being assigned to the Wwise parameter.

If using
**
Multiply
**
 and
**
Shift
**
,
**
Shift
**
 is applied to the value before the multiplier.

 |

**
Reset
**
 |
Resets the
**
Multiply
**
 and
**
Shift
**
properties to their original values.
 |

 |

When connecting an
**

**
Audio System Controls State
 to a
Wwise Parameter
, the following options are available.

Option

 |
Description

 |

**
Value
**

 |
 Value to set to the Wwise Parameter when the state is activated.

 |

##
FMOD Studio

When connecting a
State
**

**
to an
FMOD Parameter or FMOD VCA
, the following options are available.

Option

 |
Description

 |

**
Value
**

 |
 Value to set to the FMOD Eve
nt or FMOD VCA
when the state is activated.

 |

When connecting an Audio System Controls parameter to an FMOD Parameter or FMOD VCA
, the following options are ava
ilable:

Option
 |
Description
 |

**
Advanced
**
 |
When this checkbox is ticked, the following options become available.

Option
 |
Description
 |

**
Multiply
**

 |
The audio Parameter value will be incremented by this before being assigned to the FMOD Parameter or VCA.

 |

**
Shift
**

 |
The audio Parameter value will be incremented by this before being assigned to the FMOD Parameter or VCA.

If using
**
Multiply
**
 and
**
Shift
**
,
**
 Shift
**
 is applied to the value before the multiplier.

 |

**
Reset
**
 |
Resets the
**
Multiply
**
 and
**
Shift
**
properties to their original values.
 |

 |

When connecting an
Audio Trigger
to an
FMOD Event
, the following options are available:

Option

 |
Description

 |

**
Action
**

 |

-
**
Start
**
**
 -
**
Indicates that the FMOD event will start playing when the trigger is executed.

-
**
Stop -
**
 Indicates that the FMOD event will be stopped when the trigger is executed.

-
**
Pause -
**
Indicates that the FMOD event will be paused when the trigger is executed.

-
**
Resume -
**
Indicates that the FMOD event will be resumed when the trigger is executed.
 |

When connecting an
Audio Trigger
to an
FMOD Snapshot
, the following options are available:

Option

 |
Description

 |

**
Action
**

 |

-
**
Start -
**
 Indicates that the FMOD snapshot will be activated when the trigger is executed.

-
**
Stop -
**
 Indicates that the FMOD snapshot will be deactivated when the trigger is executed.
 |

##
Context Menu

Right clicking a connected audio middleware control listed under the Connections section of
**

**
the Properties panel provides the following options.

Option

 |
Description

 |

**
Execute Connection
**
 |
Plays the selected middleware control.
 |

**
Remove Connection
**

 |
Disconnects this middleware control from the Audio Systems Control.

 |

**
Select in Middleware Data
**

 |
Selects the middleware control in the Middleware Data panel.

 |

**
Import Files
**
 |
Opens a file explorer, allowing users to locate and import audio files from disk into the project's SDL Mixer assets directory. Please refer to the
[/docs/static/engines/cryengine-5/categories/23756816/pages/51347481#AudioControlsEditor-ImportFiles](
Import Files
)
 section of this page for more information on importing.
 |

##
5. Middleware Data Panel

The Audio Middleware Controls panel shows a list of all the available audio middleware controls that can be connected to the currently selected control in the Audio System Controls panel.

Users can switch between the SDL Mixer, FMOD Studio and Wwise middleware by using the
**
s_ImplName
**
Cvar in the Console.

-
`
s_ImplName = CryAudioImplSDLMixer
`
 for SDL Mixer (this is the default middleware)

-
`
s_ImplName = CryAudioImplFmod
`
 for FMOD Studio

-
`
s_ImplName = CryAudioImplWwise
`
 for WWise

-
`
s_ImplName = CryAudioImplAdx2
`
 for ADX2
For more information about audio middleware implementations, see
[/docs/static/engines/cryengine-5/categories/23756816/pages/44964933](
this page
)
.

In the event of a typo while switching between middleware using the
**
s_ImplName
**
 CVar, or when no valid middleware is loaded, the UI of the ACE will be disabled.

A "Warning: No middleware implementation!" warning will be displayed in the top-right corner of the ACE.

##
Import Files

The
**
Import Files
**
 button appears at the top of the Middleware Data panel only when the SDL Mixer middleware is in use.

Clicking it opens a file explorer, allowing users to locate and import audio files from disk into the project's SDL Mixer assets directory. Selecting the required audio files and clicking the
**
Open
**
 button on this file explorer opens the Audio File Importer window.

[Image: /docs/static/attachments/51347498]

*
Audio File Importer
*

The Audio File Importer lists the audio files that have been chosen for import, along with their Source and Target destinations.

By default, all imported audio files are saved within the
*
audio/sdlmixer/assets
*
folder of a project's asset directory. This target folder can be changed by clicking the
[Image: /docs/static/attachments/51347497]
 icon beside the
**
Target Folder
**
 field, which opens the Select Target Folder window.

[Image: /docs/static/attachments/51347496]

*
Select Target Folder
*

New folders can be created within
*
audio/sdlmixer/assets
*
via the
**
Add Folder
**
 button. Additionally, checking the
**
Localized
**
 checkbox beside the
[Image: /docs/static/attachments/51347497]
 icon indicates to the Audio System that the imported files are localized.

Doing so automatically changes the target folder to the
*
localization
*
 folder of a project's directory. More information on importing localized audio files into CRYENGINE's SDL Mixer based audio implementation can be found on the
[/docs/static/engines/cryengine-5/categories/23756816/pages/44964973](
SDL Mixer & Localization
)
 page.

The
**
Import
**
column of the Audio File Importer meanwhile contains checkboxes for each listed audio file, letting users manually specify if a listed audio file must be imported or not. The values these checkboxes can take are as follows.

Option

 |
Description

 |

**
Import (as new)
**

 |
Indicates that the audio file doesn't already exist within the target Folder. If checked, it will be imported as a new file.

 |

**
Import (as replacement)
**

 |
Indicates that an audio file with the same name as the currently listed audio file already exists in the target Folder. If checked, the listed audio file will replace the existing file when imported.

 |

The
**
Import
**
 and
**
Ignore
**
 options of the
**
Set all to
**
 field at the top-right corner of the Audio File Importer window will check/uncheck
**
Import
**
 checkboxes of all listed audio files in bulk.

Clicking the
**
OK
**
 button at the bottom-right corner of the Audio File Importer window completes the import operation.

##
Filters

The

[Image: /docs/static/attachments/51347500]
 button allows users to describe specific criteria by which the panel must list the current audio middleware's controls . Clicking this Filter button yields options to
**
Add/Clear Criteria
**
 and
**
Save/Load
**
 custom filters as required.

Middleware controls can be filtered by the values of their
**
Connected
**
,
**
In pak
**
,
**
On disk
**
,
**
Localized
**
 and
**
Name
**
properties.

Property

 |
Description

 |

**
Connected
**

 |
Specifies if a middleware control has a connection with an audio system control (Trigger/Parameter/Switch) listed within the Audio System Controls panel.

 |

**
In pak
**

 |
Indicates if a middleware control belongs to a library that exists as a
**
.pak
**
 file within the project's asset directory, or not.

 |

**
On disk
**

 |
Indicates if a middleware control belongs to a library that exists on disk, or not.

 |

**
Localized
**

 |
Specifies if the middleware control audio file is localized or not.

Localized audio files are identified by the
[Image: /docs/static/attachments/51347487]
 icon besides their listings in the Middleware Data panel.

 |

**
Name
**

 |
Specifies the name given to a middleware control.

 |

Please refer to the
[/docs/static/engines/cryengine-5/categories/23756816/pages/51347481#AudioControlsEditor-filters](
Filters
)
 sub-section of the Audio System Controls panel above for an understanding of implementing and using filters.

##
Context Menu

Depending on the middleware set up, the options that appear when right clicking a folder or middleware control in the Middleware Data panel might differ.

Option

 |
Description

 |

**
Play Event/Cue
**

 |
Previews the audio of an Event/ADX2 Cue selected from the Middleware Data Panel. Events/Cues may alternatively be previewed by double clicking their listings or pressing space bar within the Data Panel.

-
The
**
Play Event
**
 option is called
**
Play Cue
**
 when the ADX2 middleware implementation is enabled.

-
In Wwise, FMOD and ADX2, Events can only play if their corresponding banks have been loaded. In the case of SDL Mixer, any Event should play.
 |

**
Connections
**

 |
Displays a list of Audio System Controls the selected Middleware Control is connected to; selecting an Audio System Control opens it in the
**
Properties
**
 panel

 |

**
Show in File Explorer
**

 |
Opens the file explorer to locate the selected Middleware Control on disk.

This option is only visible when right-clicking Middleware Controls that exist on disk.

 |

**
Expand Selection
**

 |
Expands the selected items.

 |

**
Collapse Selection
**

 |
Collapses the selected items.

 |

**
Expand All
**

 |
Expands all items.

 |

**
Collapse All
**

 |
Collapse all items.

 |

**
Import Files
**

 |
Opens a file explorer, allowing users to locate and import audio files from disk into the project's SDL Mixer assets directory. Please refer to the
[/docs/static/engines/cryengine-5/categories/23756816/pages/51347481#AudioControlsEditor-ImportFiles](
Import Files
)
 section of this page for more information on importing.

 |

##
6. Contexts Panel

An Audio System Control can exist either in a
*
Global
*
 or
*
user-defined
*
 Context.

A control with a
*
Global
*
 Context will exist as long as the game is running, regardless of whether the control is used or not in the current level. A control with a
*
user-defined
*
context however will exist only when that Context is activated. Contexts can be created, activated and deactivated via the Contexts panel.

[Image: /docs/static/attachments/51347492]

*
Contexts
*

##
Adding, Renaming and Deleting Contexts

The
**
global
**
Context can neither be activated, deactivated, deleted or renamed.
Clicking the
**
Add
**
 button at the top of the Contexts panel creates a new Context; all Contexts are listed within the Context panel in alphabetical order.

Created Contexts can be renamed or deleted by right-clicking them, and selecting the
**
Rename
**
 or
**
Delete
**
 options from the context menu.

If a Context has the same name as a level included within a project, the Context and its controls will be automatically loaded/unloaded with that level.

##
Activating and Deactivating Contexts

Activating/deactivating a Context loads/unloads all Audio System Controls contained by it.

Contexts can be activated/deactivated by right-clicking them, and selecting the
**
Activate
**
/
**
Deactivate
**
 option respectively. An active Context is identified by the
[Image: /docs/static/attachments/51347495]
 icon against its listing.

Activating and deactivating Contexts that do not share names with an existing level can also be done via
[/docs/static/engines/cryengine-5/categories/28704770/pages/29797061](
code
)
.

Multiple contexts can be activated at a time. These contexts are not tied to levels, and each level can have multiple contexts. For example, a level may use separate contexts to play specific sounds in different game modes (singleplayer, multiplayer deathmatch, capture the flag, etc.).

##
Resource Selectors

When you click a resource selector that requires an Audio System Control, like when you add a Trigger component to an entity, a window opens in which you can select the Audio System Control of your preference:

[Image: /docs/static/attachments/51347504]

##
Search Bar

This works like other Search Bars, so typing anything in here will filter the Audio System Controls and only show ones that have that specific combination of letters and symbols in their name.

##
Context Menu

Right clicking on a folder or Audio System Control will give you the following options:

Option

 |
Description

 |

**
Execute Trigger
**

 |
Executes the Trigger you right clicked on (only available when clicking on Triggers).

**
NOTE:
**
You can also execute a trigger by
 pressing
**
spacebar
**
.

 |

**
Expand Selection
**

 |
Expands the selected items.

 |

**
Collapse Selection
**

 |
Collapses the selected items.

 |

**
Expand All
**

 |
Expands all items.

 |

**
Collapse All
**

 |
Collapse all items.

 |

##
Advanced Users

##
Data Handling

Data for Audio System Controls can be found in the
**
.xml
**
 files in the folder
*
...<Project>\audio\<middleware>\ace
*
.

Each
**
.xml
**
 file represents an audio library (top level item) in the Audio System Controls panel (folders are specified inside the
**
.xml
**
 files). Files situated in the ace root are seen and treated as files that provide data for the global data Context.

However, files under
*
...<Project>\audio\<middleware>\ace\contexts\
*
 are seen and treated as files that provide data for level-specific Contexts.

In a sense these
**
.xml
**
 files can be understood as work units. You can spread your data across as many files as you wish or you can put all your audio-specific data into 1 single file, however that will most likely cause version control conflicts particularly if several people contribute audio work to that level. Therefore, we do advise to spread the data, but that depends on the size of the project.

##
Migration Guide

##
Changes in Release 5.6

With release 5.6, Scopes have been replaced with Contexts in the ACE.

Contexts function similar to Scopes in that they load Preload Requests and Audio System Controls assigned to them. Contrary to Scopes however, Contexts are not tied to levels.

When upgrading from older CRYENGINE releases to version 5.6 and later, please note:

-
That all libraries that were previously tied to a non-global Scope will be marked by an asterisk in the ACE, indicating unsaved changes. Click the
[Image: /docs/static/attachments/51347509]
 icon to save the libraries in their respective Contexts.

-
The <
*
Project>\audio\
<middleware>\
ace\levels
*
folder has been renamed to
*
Project>\audio\
<middleware>\ace\contexts.
*

##
Changes in Release 5.5

From release 5.5 onwards, ACE files will be saved in their middleware specific folder, so each middleware implementation is completely separated by each other.

1. Create a folder called "assets" inside the current
*
audio/<middleware>
*
 folder.

2. Move all SoundBanks and audio files from the middleware folder to the new "assets" subfolder. For instance:

-
*
audio/wwise to audio/wwise/assets
*

-
*
audio/fmod to audio/fmod/assets
*

-
*
audio/sdlmixer to audio/sdlmixer/assets
*
Do the same for localized SoundBanks if there are any. For instance:

*
localization/english/audio/wwise
*
 to
*
localization/english/audio/wwise/assets
*

3. Backup all
**
.xml
**
 files of the
*
audio/ace
*
 folder.

4. Remove the write protection on all xml files inside the
*
audio/ace
*
 folder.

5. Remove all
**
.xml
**
 files from
**
.pak
**
 files (usually inside the
*
audio.pak
*
).

6. Launch the Sandbox and open the Audio Controls Editor from the
**
Tools
**
 menu.

7. All audio libraries should now be marked as modified. Press the
**
Save All
**
 button inside the Audio Controls Editor.

8. If the project contains Preload Requests, a dialog will appear that asks for reloading the audio system. Press
**
Yes
**
.

This completes the migration.

For cleanup remove the old
*
audio/ace
*
 folder. If it contains
**
.cryasset
**
 files, they can be removed as well.

If ACE
**
.xml
**
 files are write-protected they will not be automatically deleted during the migration and should be removed manually afterwards, otherwise they will get parsed again every time the Sandbox starts or the Audio Controls Editor is opened, which will increase loading time.

Source controls paths and generated SoundBank paths inside the middleware might need to get updated as well, depending on the project. Audio files are loaded from the
*
audio/<middleware>/assets
*
 folder and their respective localization folders
*
localization/<language>/audio/<middleware>/assets.
*

ACE xml files are loaded from
`
audio/<middleware>/ace
`
 folder.

[#1-menu-bar](
1. Menu Bar
)
[#2-save-reload-and-refresh-buttons](
2. Save, Reload and Refresh Buttons
)
[#3-audio-system-controls](
3. Audio System Controls
)
[#4-properties-panel](
4. Properties Panel
)
[#5-middleware-data-panel](
5. Middleware Data Panel
)
[#6-contexts-panel](
6. Contexts Panel
)
[#resource-selectors](
Resource Selectors
)
[#advanced-users](
Advanced Users
)
[#migration-guide](
Migration Guide
)
