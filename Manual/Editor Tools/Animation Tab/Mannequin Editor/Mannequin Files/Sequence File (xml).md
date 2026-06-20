# Sequence File (xml)

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/23308476
- Page ID: 23308476
- Breadcrumb: Editor Tools > Animation Tab > Mannequin Editor > Mannequin Files > Sequence File (xml)
- Parent: Mannequin Files

## Content

##
Description

A Sequence File contains a sequence of requests for animation, mimicking how the game requests animation from the system. For example it can contain a sequence of weapon fragmentIDs (select/reloading/fire/deselect) to test a weapon setup. They are created either in the mannequin editor or by recording actual gameplay.

Sequence files are stored in the folder pointed to by the
*
mn_sequence_path
*
 cvar. By default this is
*
Animations/Mannequin/FragmentSequences/
*
.

Their filename ends in .xml.

##
Creating Sequence Files

Sequence files are created either:

-
by saving a sequence using the
[Mannequin Previewer](../../Mannequin%20Editor.md#MannequinEditor-previewer)
.

-
by recording gameplay using the
*
mn_dump
*
 console command. See
[Mannequin Debugging](../Mannequin%20Debugging.md)
.

##
Editing Sequence Files

Sequence files are edited in the
[Mannequin Previewer](../../Mannequin%20Editor.md#MannequinEditor-previewer)
.

##
File Format

This is an example sequence file:

```

`
<History StartTime="0" EndTime="102.72806">
 <Item Time="32.951611" ScopeMask="Torso1P" FragmentID="idle" OptionIdx="1296707006" TagState="ammo_clipRemaining"/>
 <Item Time="33.082249" ScopeMask="" FragmentID="MotionIdle" OptionIdx="3032444839" Trump="1"/>
 <Item Time="33.209457" TagState="SDKRifle+rifle+rapid+SP+FP+iron+backward+aiming+localClient"/>
 <Item Time="33.872021" TagState="SDKRifle+rifle+rapid+SP+FP+iron+left+aiming+localClient"/>
 <Item Time="34.42939" ParamName="Curving" Type="Location">
  <Value x="0" y="0" z="0" qx="5" qy="5" qz="0" qw="1"/>
 </Item>
</History>
`

```

The
*
History
*
 element is the root element, and contains the range of time this sequence represents as
*
StartTime
*
 and
*
EndTime
*
.

It contains a list of
*
Item
*
 elements that record mannequin changes at certain
*
Time
*
s:

-
Pushing a Fragment:

-
*
FragmentID
*
 attribute: The FragmentID requested from mannequin.

-
*
ScopeMask
*
attribute: The scopemask requested from mannequin. This typically can be left empty. Scopes are assigned to the fragmentID by the definitions in the
[Controller Definition File (xxxControllerDefs.xml)](Controller%20Definition%20File%20(xxxControllerDefs.xml).md)
.

-
*
OptionIdx
*
 attribute: The option index requested from mannequin. Typically a random number during gameplay, but you can pick a specific option index if you wish.

-
*
TagState
*
 attribute: (optional) The
[FragmentID-specific Tags (fragtags)](../Mannequin%20Concepts/FragmentID-specific%20Tags%20(fragtags).md)
 used during the request.

-
*
Trump
*
 attribute: (optional) Set to 1 to enable
[Mannequin Trumping](../Mannequin%20Concepts/Mannequin%20Trumping.md)
.

-
[Global TagState](../Mannequin%20Concepts/Mannequin%20TagState.md)
 changes:

-
*
TagState
*
 attribute: The new global tagstate.

-
Parameter changes:

-
*
ParamName
*
 attribute: Contains the name of the
[Mannequin Parameter](../Mannequin%20Concepts/Mannequin%20Parameters%20Conditions.md)
.

-
*
Type
*
 attribute: Deprecated, not used.

-
*
Value
*
 element: The 'x', 'y', 'z', 'qx', 'qy', 'qz', 'qw' attributes store the value of the Mannequin Parameter. There are enough attributes to encode an offset and a quaternion, so it can be used to describe a location (eg. typical usage of the "TargetPos" parameter). Not all values are necessarily used (eg. Motion parameters only use the 'x' attribute).

##
Code

In code these sequences are represented by a list of
*
SMannHistoryItem
*
 structures in the game and a list of
*
CFragmentHistory::SHistoryItem
*
 structures in the editor.
