# Facial Sequence Tracks

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/26874142
- Page ID: 26874142
- Breadcrumb: Film and Cutscenes > Cinematics Overview > Facial Sequence Tracks
- Parent: Cinematics Overview

## Content

##
Overview

Facial Animations can be added to a Track View Sequence in multiple ways depending how the facial animations are originally created in your project.

The different ways you setup your character defines the facial animation's format:

-
You can have facial animations composed of morphs (blendshapes). These are setup in the Facial Editor and the Facial Animations are saved as
[.fsq files](/docs/static/engines/cryengine-3/categories/1114113/pages/1310899#FacialAnimationAssetFiles-fsq)
. This was the method used for all Characters in Crysis.

-
If your character has a facial rig made of bones:

-
You can create animations in your DCC and export them as
[.caf files](/docs/static/engines/cryengine-3/categories/1114113/pages/1310796#ExportingAnimations-ExportingaCAFFile)
. These are then treated the same way as the body animations. This was the method used for A-Level Characters in Crysis 2.

-
You can setup the expressions in Facial Editor using Bone Expressions. These are then saved as .fsq files. This was the method used for C-Level Characters in Crysis 2.

##
Morph Based Setup

If your character is setup with morph targets, please refer to
[Facial Setup](/docs/static/engines/cryengine-3/categories/1114113/pages/1310723)
 document.

There is more information on
[Facial Animation](/docs/static/engines/cryengine-3/categories/1114113/pages/1310771)
.

To setup a character in Facial Editor, please refer to
[Facial Editor Tutorial](/docs/static/engines/cryengine-3/categories/1114113/pages/1048829)
.

To play Facial Animation on a Character setup with Morphs in Track View, you need to add a
[Facial Sequence](Facial%20Sequence%20Tracks.md#FacialSequenceTracks-FacialSequenceTrack)
 Track on the Character.

##
Bone Driven Facial Rig

##
Animations created in DCC

A-level characters use separate .caf files for their facial animations. Usually the naming of facial animation files matches the naming of the character's dialogue lines.

Facial animations have to be placed in a separate Animation track in Track View. The first Animation track of a character should contain the body animations, the second Animation track the facial animations. It is important to keep this order because the animations depend on it.

In most cases the facial animation will be matched to the dialogue line of the same name, so both have to start at the same time.

*
The first Animation track contains the body animations, the second one the facial animations. The Sound track at the bottom contains the dialogue lines that play together with the facials.
*

##
Adding Facial Animations

Facial animations are added the same way as other animations:

-
Add a new key in the Animation track you use for facial animations.

-
Click the folder icon in the key's Animation property field to open the Animation Browser.

-
Select the desired animation in the Animation Browser (it will be listed under "facial").

Blend Gap shouldn't be used on facial animations.

##
Adding Dialogue Sound Files to Play with Facials

-
Add a new key in the Sound track you use for the character's dialogue.

-
Click the folder icon in the key's Sound File property field to open the Sound Browser.

-
Click on the
*
Browse File...
*
 button.

-
The dialogue files you need will be in the
`
languages/dialog/[CRYENGINE:LevelName]
`
 folder.
For A-Level characters, enable the flags
*
Voice
*
 and
*
3D Sound
*
 in the Sound key's properties.

*
Sound key flags needed for A-level characters. Setting the LipSync flag is not required.
*

##
Eye Flickering & Blinking

Extra eye movement can be added to a character by using special eye movement animations. These animations should be put in a separate Animation track and should be added after the two tracks used for body and regular facial animations.

Eye flickering and blinking should be used especially when a character's face is shown in a close-up. It doesn't need to be used on characters the player can only see from far away (mind the player's zoom function though).

The eye movement animations are also listed under "facial" in the Animation Browser:

-
facial_eyes_blink

-
facial_eyes_flicker –
*
subtle eye movement to make the character look more alive
*

-
facial_eyes_flicker_01 –
*
slightly stronger version
*

*
Example of an Animation track used for eye movement.
*

##
Animations created in Facial Editor

C-level characters don't use separate .caf files for facial animations. Their face will be animated automatically when playing a line of dialogue. Additionally a fixed facial expression can be played.

##
Dialogue Sound File Setup

The setup is mostly the same as for A-level characters. The differences are:

-
There's no separate Animation track needed to play facial animations.

-
You also need to enable the
*
LipSync
*
 flag together with
*
Voice
*
 and
*
3D Sound
*
 in the Sound key's properties.

*
Sound key flags needed for C-level characters.
*

##
Facial Sequence Track

The Facial Sequence track allows to set fixed facial expressions on characters.

*
A Facial Sequence track being used on a C-level character.
*

[Morph Based Setup](#morph-based-setup)
[Bone Driven Facial Rig](#bone-driven-facial-rig)
[Animations created in DCC](#animations-created-in-dcc)
[Animations created in Facial Editor](#animations-created-in-facial-editor)
