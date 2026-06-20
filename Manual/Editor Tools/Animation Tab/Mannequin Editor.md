# Mannequin Editor

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/27594502
- Page ID: 27594502
- Breadcrumb: Editor Tools > Animation Tab > Mannequin Editor
- Parent: Animation Tab

## Child Pages

- [Mannequin Concepts](Mannequin Editor/Mannequin Concepts.md)
- [Mannequin Technical Topics](Mannequin Editor/Mannequin Technical Topics.md)
- [Mannequin Files](Mannequin Editor/Mannequin Files.md)
- [Mannequin Introduction](Mannequin Editor/Mannequin Introduction.md)
- [Mannequin Additive Animations](Mannequin Editor/Mannequin Additive Animations.md)
- [Mannequin AI Sequence](Mannequin Editor/Mannequin AI Sequence.md)
- [Mannequin Animation Clip Properties](Mannequin Editor/Mannequin Animation Clip Properties.md)
- [Mannequin Animation DB Editor](Mannequin Editor/Mannequin Animation DB Editor.md)
- [Mannequin Animation Layers](Mannequin Editor/Mannequin Animation Layers.md)
- [Mannequin Audio](Mannequin Editor/Mannequin Audio.md)
- [Mannequin Context Editor](Mannequin Editor/Mannequin Context Editor.md)
- [Mannequin File Manager](Mannequin Editor/Mannequin File Manager.md)
- [Mannequin Flowgraph](Mannequin Editor/Mannequin Flowgraph.md)
- [Mannequin FragmentID Editor](Mannequin Editor/Mannequin FragmentID Editor.md)
- [Mannequin List Used Animations](Mannequin Editor/Mannequin List Used Animations.md)
- [Mannequin Debugging](Mannequin Editor/Mannequin Debugging.md)
- [Mannequin Tag Definition Editor](Mannequin Editor/Mannequin Tag Definition Editor.md)
- [Mannequin Track Properties](Mannequin Editor/Mannequin Track Properties.md)

## Content

##
Overview

The Mannequin Editor is set of high level tools to help you manage the complexities of interactive animation.

[Image: /docs/static/attachments/44970373]

For a detailed introduction of the Mannequin Editor, please see
[/docs/static/engines/cryengine-5/categories/23756816/pages/23308427](
this page
)
.

##
1. Menu Bar

##
File

Option
 |
Description
 |

**
Load Preview Setup
**
 |
Load an existing preview setup.
 |

**
Preview Editor
**
 |
The Preview Editor can be used bind characters and animation databases to
[/docs/static/engines/cryengine-5/categories/23756816/pages/29450870](
Scope Contexts
)
 for visualization purposes within the Mannequin Editor. Multiple context configurations can be defined and later  switched between through the Context dropdown available in the Fragments and Transitions panes.
 |

**
Animation DB Editor
**
 |
The Animation Database Editor is used to edit the rules which determine in which
ADB file
 fragments end up. It can also be used to create new ADB files.

 |

**
Tag Definition Editor
**
 |
The Tag Definition Editor is used to create & edit
Tag Definition Files
.

More information can be found in the (technical) tutorial
[/docs/static/engines/cryengine-5/categories/23756816/pages/23308465](
Entity Setup From Scratch
)
.

 |

**
Save Changes
**
 |
Opens up a window with a list of modified files and provides a way to save or revert the changes on a file-by-file basis.
 |

**
Re-export All
**
 |
Commit all changes, so that they're visible in the level editor.
 |

##
Previewer

Option
 |
Description
 |

**
New Sequence
**
 |
Create a new sequence.
 |

**
Load Sequence
**
 |
Load an existing sequence.
 |

**
Save Sequence
**
 |
Save the current sequence.
 |

##
Tools

Option
 |
Description
 |

**
List Used Animations
**
 |
Exports a list of all animation (CAF) files used by all existing preview setups, in a CSV format.
 |

**
List Used Animations (Current Preview)
**
 |
Exports a list of all animation (CAF) files used by the currently loaded preview setup, in a CSV format.
 |

##
2. Fragments/Sequences/Transitions Pane

This pane has three tabs at the bottom, with which you can switch between three panes, the Fragments pane, the Sequences pane and the Transitions pane.

##
Fragments

The Fragments pane consists of two parts: the Fragment List  and the TagState list.

This pane lists all fragments in an
[/docs/static/engines/cryengine-5/categories/23756816/pages/29798743](
animation database
)
 (and its sub-databases). It is used to find & create
[/docs/static/engines/cryengine-5/categories/23756816/pages/29450856](
fragments
)
, change fragment
[/docs/static/engines/cryengine-5/categories/23756816/pages/29450874](
tags
)
, as well as creating and editing
[/docs/static/engines/cryengine-5/categories/23756816/pages/23308432](
fragmentIDs
)
.

It is typically used in combination with either the
[/docs/static/engines/cryengine-5/categories/23756816/pages/27594502#MannequinEditor-FragmentEditor](
Fragment Editor
)
 (to edit fragments) or the
[/docs/static/engines/cryengine-5/categories/23756816/pages/27594502#MannequinEditor-previewer](
previewer
)
 (to preview sequences).

It can be accessed by clicking on the "Fragments" tab at the left side of the editor.

For tutorials that go through some of this functionality, check out
[/docs/static/engines/cryengine-5/categories/23756816/pages/23308483](
Mannequin Editor Tutorial 1 - Preview Setup, Fragments and Saving
)
 and
[/docs/static/engines/cryengine-5/categories/23756816/pages/23308484](
Mannequin Editor Tutorial 2 - Tags & Previewing
)
.

The next sections will go through the parts of this panel from top to bottom:

##
Fragment List

Option
 |
Description
 |

**
Context
**
 |
Use the context dropdown to select which context configuration you would like to use. This list is based on the current Preview Setup, which can be edited in the Preview Editor.

Fragments displayed in the browser below belong to the database of the currently active context configuration.

 |

**
Current ADB
**
 |
Shows the ADB in which fragments for the currently selected fragmentID end up in.

This ADB is not necessarily the same as the ADB the currently selected
*
fragment
*
 ends up in. This function only checks the fragmentID, not the tags.
 |

 |

**
FragmentID Filter
**
 |
Show only fragments for fragmentIDs containing this word.

 |

**
Tag Filter
**
 |
Show only fragments with tags containing this word. The word "<default>" counts too, so if you look for "default" it includes all fragments without tags.

 |

**
Anim Filter
**
 |
Show only fragments with animations containing this word.

 |

**
Sub Folders
**
 |
When checked: The fragment list will create folders for all tags. Higher priority tags will be higher up the tree than lower priority ones.

For example in the following screenshot the tags are "rifle", "pistol", "shoulder" and "iron":

When not checked: The fragment list will create folders only when there are multiple fragments for the same combination of tags (aka multiple fragment options). In this view the fragments are sorted by selection order (See
[/docs/static/engines/cryengine-5/categories/23756816/pages/23308439](
Fragment Selection Process
)
).

For example in the following screenshot there are 2 options for "pistol+iron", but the other combinations of tags have only one option each.

 |

**
Show Empty
**
 |
Show also FragmentIDs that have no fragments in it. (useful for example when creating the first fragment with a certain fragmentID)

 |

**
*
Fragment Tree
*
**

Shows the list of fragments, sorted by fragmentID.

Some things to note about this tree view:

-
The fragmentIDs are the root folders.

-
The fragments are the entries with a movie film icon.

-
Tags sometimes also appear as folders, this depends on the Sub Folders option.

-
Fragments without tags show up as options for "<Default>".
The currently 'edited' fragment is shown in
**
bold
**
. This is the fragment whose
[/docs/static/engines/cryengine-5/categories/23756816/pages/27594502#MannequinEditor-TagState](
tagstate
)
 is displayed below, and it is the same fragment which is the main fragment currently displayed in the Mannequin Fragment Editor.

Note that this is a different fragment than the currently selected one! (see screenshot above).

-
*
Left click
*
 a fragment to select it.

-
*
Double click
*
 a fragment to 'edit' it: open it in the Mannequin Fragment Editor and show its
[/docs/static/engines/cryengine-5/categories/23756816/pages/27594502#MannequinEditor-TagState](
tagstate
)
 below.

-
*
Left-mouse drag and drop
*
 a fragment onto a scope in the Previewer to automatically create FragmentID & Tags Keys to select this specific fragment.

-
*
Right-mouse drag and drop
*
 a fragment to duplicate it.

-
*
Right-click on a fragment and select "Copy Selected Text"
*
 to copy its
[/docs/static/engines/cryengine-5/categories/23756816/pages/27594502#MannequinEditor-TagState](
tagstate
)
.

-
Use
*
Ctrl+C/Ctrl+V
*
 on a fragment to duplicate it.

-
Use Ctrl+C/Ctrl+V on a tag folder to duplicate all fragments within that folder. For example here is what happens when we copy everything within 'standing' onto itself:

-
Use
**
Ctrl+C/Ctrl+Shift+V
**
 on a tag folder to duplicate all fragments within that folder
*
while changing specific tags
*
. The following window will pop up, in which you can change tags:

This is what happens when we copy everything within "standing" and change the stance tag from "standing" to "kneeling":

*
**
Function Buttons
**
*

Button
 |
Description
 |

**
New
**
 |
Create new Fragment within the currently selected fragmentID.
 |

**
Delete
**
 |
Delete the currently selected fragment.
 |

**
Edit
**
 |
Edit the currently selected fragment: open it in the Mannequin Fragment Editor and show its tagstate below.
 |

**
New ID
**
 |
Create new FragmentID. First it will ask you for a name, after which it opens the
[/docs/static/engines/cryengine-5/categories/23756816/pages/23308446](
Mannequin FragmentID Editor
)
.
 |

**
Delete ID
**
 |
Delete currently selected FragmentID.
 |

**
Edit ID
**
 |
Open the Mannequin FragmentID Editor for the currently selected FragmentID.
 |

**
Tag Definition Editor
**
 |
Open the Mannequin Tag Definition Editor.
 |

##
TagState

This shows the tagstate (both global tags and fragtags) of the currently edited fragment, which is the boldface fragment in the fragment list.

Here you can edit this fragment's tagstate. An empty or unchecked tag means the tag is not set on the fragment.

##
Sequences Browser

The Sequences browser is used to select the
[/docs/static/engines/cryengine-5/categories/23756816/pages/23308476](
sequence
)
 you would like to open in the
[/docs/static/engines/cryengine-5/categories/23756816/pages/27594502#MannequinEditor-previewer](
Mannequin Previewer
)
.

It simply lists the files in the default sequence folder, described in the article on
[/docs/static/engines/cryengine-5/categories/23756816/pages/23308476](
sequence files
)
.

To access the panel, click on the tab
**
Sequences
**
 at the bottom of the mannequin editor.

Use double click or the
**
Open
**
 button to open the selected sequence.

##
Transitions Browser

The Transition Browser is used to list all the
[/docs/static/engines/cryengine-5/categories/23756816/pages/29450872](
transitions
)
 in a certain
[/docs/static/engines/cryengine-5/categories/23756816/pages/29798743](
animation database
)
 (and its sub-ADBs).

It is used in combination with the
[/docs/static/engines/cryengine-5/categories/23756816/pages/27594502#MannequinEditor-TransitionEditor](
Mannequin Transition Editor
)
.

It can be accessed by clicking the
**
Transitions
**
 tab at the bottom of the mannequin editor.

See
[/docs/static/engines/cryengine-5/categories/23756816/pages/23308485](
Mannequin Editor Tutorial 3 - Transitions
)
.

Option
 |
Description
 |

Context
 |
Use the context dropdown to select which context configuration you would like to use. This list is based on the current Preview Setup, which can be edited in the Preview Editor.

Transitions displayed in the browser below belong to the database of the currently active context configuration.
 |

**
Transition From/To
**
 |
Provides a way to filter the transition list below based on Fragment IDs and tagstate.
 |

##
Function Buttons

Button
 |
Description
 |

**
New
**
 |
Create a new transition.
 |

**
Open
**
 |
Open
the currently selected transition in the Transition Editor and shows it in the Transition Preview below.

 |

**
Edit
**
 |
Edit
the currently selected transition: opens it in the Transition Editor and shows it in the Transition Preview below.
 |

**
Copy
**
 |
Copy the selected transition.
 |

**
Delete
**
 |
Deletes the selected transition.
 |

##
3. Fragment Editor/Transition Editor/Previewer/Mannequin Error Report

In the pane on the right you can open four different tools within the Mannequin Editor: the Fragment Editor, the Transition Editor, the Previewer and the Mannequin Error Report.

##
Fragment Editor

The Fragment Editor is used to edit fragments (multiple at a time).

It can be brought up by:

-
clicking on the
**
Fragment Editor
**
 tab at the bottom of the mannequin editor.

-
double clicking a fragment or selecting
**
edit
**
 in the Mannequin Fragment Browser.

-
selecting
**
Edit Fragment
**
 from the right-click menu of a fragmentID key (in the Mannequin Previewer or other editors)
For details on the tracks, see
[/docs/static/engines/cryengine-5/categories/23756816/pages/23308450](
Mannequin Track Properties
)
.

For specific details on editing clips, see
[/docs/static/engines/cryengine-5/categories/23756816/pages/23308449](
Mannequin Animation Clip Properties
)
.

For more, see
[/docs/static/engines/cryengine-5/categories/23756816/pages/23308483](
Mannequin Editor Tutorial 1 - Preview Setup, Fragments and Saving
)
.

##
Transition Editor

The Transition Editor is where you edit specific
[/docs/static/engines/cryengine-5/categories/23756816/pages/29450872](
mannequin transitions
)
.

It is typically used together with the
[/docs/static/engines/cryengine-5/categories/23756816/pages/27594502#MannequinEditor-TransitionBrowser](
Transition Browser
)
.

Is is accessed by clicking the
**
Transitions
**
 tab at the bottom of the mannequin editor.

See
[/docs/static/engines/cryengine-5/categories/23756816/pages/23308485](
Mannequin Editor Tutorial 3 - Transitions
)
.

##
Previewer

The Previewer is used to edit and view
[/docs/static/engines/cryengine-5/categories/23756816/pages/23308476](
Sequence Files
)
, or simply to test a sequence of fragments without even saving it to a file.

It can be accessed by clicking the "Previewer" tab at the bottom of the mannequin editor.

See
[/docs/static/engines/cryengine-5/categories/23756816/pages/23308484](
Mannequin Editor Tutorial 2: Tags & Previewing
)
.

##
Mannequin Error Report

This panel displays the result of validation on the currently opened
[/docs/static/engines/cryengine-5/categories/23756816/pages/23308475](
setup
)
.

It is one of the panels at the right of the mannequin editor. To access it simply press the "Error Report" tab at the bottom.

Every time you open a
[/docs/static/engines/cryengine-5/categories/23756816/pages/23308475](
preview setup
)
 validation is done on that setup. If any errors are found, the error report will pop up to the front automatically.

##
Error/Warning List

This area shows the list of errors/warnings the validation found.

Double click a line to select that
[/docs/static/engines/cryengine-5/categories/23756816/pages/29450856](
fragment
)
 in the Fragment Browser/Editor.

Select one or more lines to operate on those fragments using the menu or right click menu.

##
Error Report Menu

Button
 |
Description
 |

**
Select All
**
 |
Check all listed errors/warnings.
 |

**
Clear Selection
**
 |
Uncheck all.
 |

**
Check
**
 |
Run the validation again.
 |

**
Delete Fragments
**
 |
Delete the fragments corresponding to the
*
checked
*
 errors/warnings.
 |

##
Right Click Menu

Option
 |
Description
 |

**
Copy Warning(s) To Clipboard
**
 |
Copy
*
all
*
 lines to the clipboard.
 |

**
E-mail Error Report
**
 |
Create a mail with all lines.
 |

**
Open in Excel
**
 |
Open the lines in Excel.
 |

[#1-menu-bar](
1. Menu Bar
)
[#2-fragmentssequencestransitions-pane](
2. Fragments/Sequences/Transitions Pane
)
[#3-fragment-editortransition-editorpreviewermannequin-error-report](
3. Fragment Editor/Transition Editor/Previewer/Mannequin Error Report
)
