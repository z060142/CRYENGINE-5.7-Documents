# Controlled Event Blending

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/26874176
- Page ID: 26874176
- Breadcrumb: Film and Cutscenes > Cinematics Overview > Scene Interactivity > Controlled Event Blending
- Parent: Scene Interactivity

## Content

##
Overview

##
When going into a camera controlled sequence

Make sure your camera is INSIDE of the trigger, or you will have ugly snapping back when starting the sequence:

Do not use too high or too low blending values. Try to stay between 0.5 and 2:

If possible, lower or holster the players weapon using the
**
Actor:PlayerCinematicControl
**
 node before starting the sequence, to prevent it from just popping out.

To make the transition more solid you might also want to slow the player down so he cannot jump/sprint/slide into the trigger. Using a bigger trigger, that encapsulates the actual sequence trigger works best for most of the use cases:

##
Blending back to player control

Use the
**
Entity:BeamEntity
**
 node to set the player to the end of the sequence. Make sure to position the tagpoint right below or slightly behind the last camera position to make a good looking transition.

Note: Always use the "Done" or "Finished" output of the PlaySequence node
**
directly
**
.

Do not use Gametokens or other logic in between, or there might be the old player position visible for a few frames before he gets beamed to the final position.

Don't forget to unholster the weapon and reset the player movement options!

In some cases the players last movement input can be kept in the system and still be active after the sequence, causing the player to continue to walk then even though no key is pressed.

To prevent this, place an
**
Actor:ActionFilter
**
 node with the filter "cutscene_player_moving" and activate it on start of the sequence and disable it when done:

[#when-going-into-a-camera-controlled-sequence](
When going into a camera controlled sequence
)
[#blending-back-to-player-control](
Blending back to player control
)
