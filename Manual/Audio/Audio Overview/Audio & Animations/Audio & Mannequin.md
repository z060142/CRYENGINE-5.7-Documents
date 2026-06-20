# Audio & Mannequin

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/44964890
- Page ID: 44964890
- Breadcrumb: Audio > Audio Overview > Audio & Animations > Audio & Mannequin
- Parent: Audio & Animations

## Child Pages

- [Audio & Mannequin Usecases*](Audio & Mannequin/Audio & Mannequin Usecases.md)

## Content

##
Overview

This section gives an overview of how to apply Audio to Mannequin. Please note however that the article
[/docs/static/engines/cryengine-5/categories/23756816/pages/23308483](
Mannequin Editor Tutorial 1
)
 is prerequisite knowledge for the following information.

##
Introduction

Audio in Mannequin is controlled by adding
[/docs/static/engines/cryengine-5/categories/23756816/pages/29450878](
Procedural Clips
)
 to
[/docs/static/engines/cryengine-5/categories/23756816/pages/29450856](
Fragments
)

and setting their
Type
 to
Audio
 in the
Procedural Clip Properties
.

*
Fragments
*
 are played on
[/docs/static/engines/cryengine-5/categories/23756816/pages/29450859](
Scopes
)
*
[/docs/static/engines/cryengine-5/categories/23756816/pages/23308437](
,
)

*
but there are no technical restrictions on which
*
Scopes
*
 the Audio
*
Procedural Clip
*
s are placed. However, it is quite common for a project to setup a Mannequin character in such a way that certain
*
Scopes
*
 only have audio system Triggers placed on them. For example, in the case of the
[/docs/static/engines/cryengine-5/categories/23756816/pages/44964891](
Audio & Mannequin Usecases*
)
 we have the
Audio1
 and
Audio2

*
Scopes
*
 on which all audio system Triggers
*

*
are placed.

Mannequin decides which
*
Fragments
*
 it will trigger via
[/docs/static/engines/cryengine-5/categories/23756816/pages/29450874](
Tag States
)
. This allows flexibility in supporting animations with sound, so you can go very granular or stay rather generic.

The
[/docs/static/engines/cryengine-5/categories/23756816/pages/27594502](
Mannequin Editor
)

describes how to add tags to a
*
Fragment
*
. These tags define what needs to be going on in the game or with the character in order for that specific
*
Fragment
*
 to be selected.

For example, say you want to support each weapon with a different sound, but you don't necessarily want to distinguish between whether the player is crouching or standing while firing. To ensure this, you need to make sure that the
[/docs/static/engines/cryengine-5/categories/23756816/pages/29450856](
FragmentID
)
 is properly flagged using the parent of the weapon item name. For example, fire
[SDKRifl
e]
 needs the SDKRifle selected to work in all stances (crouch, stand, etc).

*
FragmentID properly flagged
*

[Image: /docs/static/attachments/44971420]

The game might also trigger extra tags such as "standing" or "crouch" depending on the character's stance, but will always pick the best fitting one - this means the one that matches most of the tags provided.  If you decide to provide more detail, this can be achieved by creating different
*
Fragments
*
 with different
*
audio system Triggers
*
 and a wider range of tags.

To learn more about Tags please read the article
[/docs/static/engines/cryengine-5/categories/23756816/pages/23308456](
Mannequin Tag Definition Editor
)
.

##
Enabling Scopes for a Fragment

Depending on your setup, you might want to place audio system Triggers in specific
*
Scopes
*
. For example, in the
Sandbox Editor setup
, sounds are usually placed in the "Audio1" or the "Audio2"
*
Scopes
*
.

Furthermore, the preferred way of enabling a
*
Scope
*
 for a
*
FragmentID
*
 is to edit its default Scope Mask: When editing a
*
FragmentID
*
 you can select which
*
Scopes
*
 it should use by default.

*
Enabling a Scope for a Fragment - 1
*

[Image: /docs/static/attachments/44971422]

*
Enabling a Scope for a Fragment - 2

*
[Image: /docs/static/attachments/44971423]

For an extensive step-by-step guide on how to achieve this please refer to the
[/docs/static/engines/cryengine-5/categories/23756816/pages/23308483](
Mannequin Editor Tutorial 1
)
.

##
Adding a ProcLayer Track

Once you have decided on which
*
Scope
*
 you want to place the audio system
*
Triggers
*
 on, you need to create a
*
ProcLayer t
*
rack.

To add a
*
ProcLayer
*
track, right click on the
Scope
 and select
AddTrack -> ProcLayer
:

[Image: /docs/static/attachments/44971429]

Afterwards the layout should look like screenshot below.

[Image: /docs/static/attachments/44971430]

To learn more about these tracks and their properties, please read the article
[/docs/static/engines/cryengine-5/categories/23756816/pages/23308450](
Mannequin Track Properties
)
.

##
Creating an Audio System Trigger on an Audio Proc Layer

In the
*
ProcLayer’s
*
 timeline double-click to add a
*
Procedural Clip
*
. The clip can be moved by dragging its start point.

Under the Procedural Clip Properties menu you can set what type the clip should be.

In order to execute audio system Triggers click on the Type property and select Audio
.

[Image: /docs/static/attachments/44971431]

You can see that this selection changes the options available for the clip in the Procedural Clip Properties  (screenshot below). It is now possible to set a Start and Stop Trigger and define its behavior.

When the
*
Fragment
*
 ends the Sound stops and as described in the Start/Stop Trigger behavior see
[/docs/static/engines/cryengine-5/categories/23756816/pages/44964879](
here
)
.

To keep the Sound playing, then use
*
do_nothing
*
 as the
*
StopTrigger
*
.

[Image: /docs/static/attachments/44971432]

The Blend time does not affect the fade-in of a sound.

##
Tips

You can add any number of
*
ProcLayers
*
 to a S
*
cope
*
 which can help you to better organize your
*
Fragment
*
.

*
Procedural Clip
*
s can be added to any
*
ProcLayer
*
 on any
*
Scope
*
. Just be aware that depending on your setup the clips might then be saved to a different
[/docs/static/engines/cryengine-5/categories/23756816/pages/29798743](
Database
)
 file.

The CVar
mn_debug <entity name>
 shows you the
*
Fragments
*
 and Animations that are triggered by an Entity at any given time. This helps you to figure out which
*
Fragments
*
 are the ones without Sound. See
[/docs/static/engines/cryengine-5/categories/23756816/pages/29798746](
Mannequin Debugging
)
.
[#introduction](
Introduction
)
[#enabling-scopes-for-a-fragment](
Enabling Scopes for a Fragment
)
[#adding-a-proclayer-track](
Adding a ProcLayer Track
)
[#creating-an-audio-system-trigger-on-an-audio-proc-layer](
Creating an Audio System Trigger on an Audio Proc Layer
)
[#tips](
Tips
)
