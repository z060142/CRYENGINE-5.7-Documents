# Mannequin Debugging

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/29798746
- Page ID: 29798746
- Breadcrumb: Editor Tools > Animation Tab > Mannequin Editor > Mannequin Debugging
- Parent: Mannequin Editor

## Content

![Image](https://www.cryengine.com/docs/static/attachments/29934012)

##
Overview

##
Sections

Mannequin provides a couple of console variables and commands to debug the system state.

[Sections](#sections)
[On-Screen Debugging](#on-screen-debugging)
[Saving a History Sequence](#saving-a-history-sequence)
[Logging Fragment Requests](#logging-fragment-requests)
[Frame-by-Frame Debugging](#frame-by-frame-debugging)

##
On-Screen Debugging

Use the
*
mn_debug
*
 console variable to turn on/off on-screen debugging information for a specific entity.

This is most useful when combined with frame by frame recording.

##
Usage

*
mn_debug <EntityName>
*

-
EntityName: The name of the entity to debug. You can use tab-completion here. If the entity is not found or "0" is specified, debugging is turned off. Tip: The player's name is typically "Dude", and to show the names of the entities on screen, you can use "es_entity 1" (use "es_entity 0" to turn this off).

##
Description of the On-Screen Information

##
Global TagState

The current
[Global TagState](/docs/static/engines/cryengine-3/categories/1114113/pages/15011534#MannequinTagState-GlobalTagState)
 is displayed in the topleft corner.

##
Scopes

All the scopes are displayed in a list on the left side. Each scope contains the following information:

-
*
Scope
*
: The name of the
[Scope](Mannequin%20Concepts/Mannequin%20Scopes.md)
.

-
*
Action
*
: The name of the
[Action](/docs/static/engines/cryengine-3/categories/1114113/pages/15011601)
 playing on the scope.

-
*
FragmentID(Tags)
*
: The
[FragmentID](Mannequin%20Concepts/FragmentIDs.md)
 of the
[Fragment](Mannequin%20Concepts/Mannequin%20Fragments.md)
 playing on this scope. The
[tags](Mannequin%20Concepts/Mannequin%20Tags%20%26%20Tag%20Definitions.md)
 for this fragment are within the parentheses.
[Fragtags](Mannequin%20Concepts/FragmentID-specific%20Tags%20(fragtags).md)
, if any, are shown surrounded by square brackets.  If no matching fragment could be found, the tags used to request the fragment are shown, see the Motion1P scope in the overview screenshot above.

-
*
Priority
*
: The priority of the action playing on the scope.

-
*
RefCount
*
: The reference count of the action playing on the scope.

-
*
Time Remaining
*
: (estimated) time remaining for this fragment. Can be 0 for looping fragments.

-
*
Playing Clips
*
: Each line represents a layer within this fragment. The first clip on each line is which clip is playing at this moment. In case of a sequence or a transition, multiple clips are displayed and the currently playing one is highlighted.
This section is grayed out if the scope is
*
inactive
*
. This happens if the
[Scope Context](Mannequin%20Concepts/Mannequin%20Scopes/Mannequin%20Scope%20Contexts.md)
 it uses has no valid
[Animation Database File (ADB)](Mannequin%20Files/Animation%20Database%20(ADB).md)
 assigned to it, or if it is invalid (for example an non-existing entity is assigned to it).

##
Pending Action Queue

The top right section shows the actions which are currently pending, sorted by priority (the higher the number, the higher the priority). Each line contains the following information:

-
*
Action
*
: The name of the
[Action](Mannequin%20Technical%20Topics/Mannequin%20Actions.md)
 that is pending.

-
*
FragmentID
*
: The
[FragmentID](Mannequin%20Concepts/FragmentIDs.md)
 that this action is currently requesting.

-
*
Priority
*
: The priority of the action.

-
*
Forced Scope Mask
*
: (after the '-', not shown in the screenshot above) The scope mask the action is forced to use, if any. By default it uses the
[ScopeMask](Mannequin%20Concepts/Mannequin%20Scopemasks.md)
 set up in the
[FragmentID Editor](Mannequin%20FragmentID%20Editor.md)
, but code
*
can
*
 extend that one by a 'forced scope mask'.

##
Saving a History Sequence

While playing all recent changes in mannequin state are recorded and can be saved to a file. Currently the 200 latest changes are recorded. Note that this code is removed in Release builds, but it is available in Debug and Profile builds.

For this you use the
*
mn_dump
*
 console command.

##
Usage

*
mn_dump [EntityName] [duration]
*

-
EntityName: The name of the entity to debug. You can use tab-completion here. The player's name is typically "Dude". If the entity is not found, the entity specified using
*
mn_debug <EntityName>,
*
if any, is used instead.

-
Duration: optional parameter specifying how many seconds back in time you want to log. If you don't specify this or specify a negative number, the whole recorder buffer is stored.

##
Result

The sequence is stored as a
[Sequence File (xml)](Mannequin%20Files/Sequence%20File%20(xml).md)
 in the folder specified in the console variable
*
mn_debug_sequence
*
, which by default this is
*
Animations/Mannequin/FragmentSequences/.
*

The files are named
*
<EntityName>_<Date>_<Time>.xml
*
. For example
*
Dude_17_Apr_2012_15_12_37.xml.
*

You can load these sequences up in the
[Mannequin Previewer](../Mannequin%20Editor.md#MannequinEditor-previewer)
.

##
Logging Fragment Requests

You can log all fragment requests using the
*
mn_debugfragments
*
 console variable.

This info only shows up in the log if you also enable
*
mn_LogToFile
*
!

##
Usage

*
mn_debugfragments <type>
*

Type:

-
0 to turn off debugging

-
1 to turn on debugging of all fragments started on the root scope of an action for the entity specified with
[mn_debug](Mannequin%20Debugging.md#MannequinDebugging-mn_debug)

-
2 to turn on debugging of all started fragments for the entity specified with
[mn_debug](Mannequin%20Debugging.md#MannequinDebugging-mn_debug)

##
Result

This is an example output:

```

`
[ 46539] Fragment MotionMovement (rifle,) queued on scope FullBody3P for action PlayerMovement
[ 46555] Fragment fire (rifle+rapid+localClient+forceFeedback,) queued on scope WeaponForceFeedback for action ItemAction
[ 46555] Fragment rapid_fire (rifle+shoulder,) queued on scope Torso1P for action RapidFireAction
[ 46556] Fragment MotionIdle (rifle,) queued on scope FullBody3P for action PlayerMovement
[ 46561] Fragment fire (rifle+rapid+localClient+forceFeedback,) queued on scope WeaponForceFeedback for action ItemAction
[ 46562] Fragment spin_down (rifle+FP,) queued on scope OneShotSound for action ItemAction
[ 46562] Fragment idle (rifle,) queued on scope Torso1P for action ItemIdle
[ 46564] Fragment idle (No Match,) queued on scope Torso1P for action ItemIdle
`

```

Information displayed on each line:

**
[
**
 <frame index>
**
]
**

**
Fragment
**
 <fragmentID name>
**
(
**
 <tags>
**
,
**
<fragment-specific tags>
**
) queued on scope
**
 <scope>
**
for action
**
 <action>

The fragmentname is "No Match" when no match was found.

##
Frame-by-Frame Debugging

##
Usage

*
*
g_manualFrameStepFrequency
*
 <Frequency>
*

-
Frequency: The frame rate that we wish to simulate when using the manual frame-by-frame debugging mode. Setting this to 0 (default value) will disable manual frame-by-frame debugging altogether.

##
Description

In the GameSDK sample project, the
*
g_manualFrameStepFrequency
*
 CVar will let you manually generate frames, one at a time. Just set the CVar to the desired simulation frame rate (e.g. 30 or 60 frames per second) and hit "Pause" on your keyboard. The engine will then completely freeze, and new frames will be generated only when you press the right arrow key. Please note that the input system is still running when using manual frame-by-frame stepping. This means that you can use this feature to very easily test extremely specific sequences of inputs. You can leave the manual frame step mode by pressing the "Pause" key again. If you hit the left arrow key, the system will open your default image viewer program and let you scrub through the history of frames that were previously generated.

Frame-by-frame stepping is also supported in multiplayer. If one player enters the manual frame step mode, a command will be broadcast and all clients will freeze and synchronously generate frames one at a time, whenever the right arrow key is pressed. When running multiple clients on the same machine, each client will have its own history, which you can access by pressing the left arrow key.

Frame-by-frame stepping used alongside the
*
mn_debug
*
 CVar can be extremely valuable when debugging animation-related issues. It can be used to test how the game operates given a very specific sequence of inputs (even on multiple clients in a multiplayer environment), measure input lag, have a very close look at virtually any character animation topic, keep track of the fragment and transition selection process, and many other things.
