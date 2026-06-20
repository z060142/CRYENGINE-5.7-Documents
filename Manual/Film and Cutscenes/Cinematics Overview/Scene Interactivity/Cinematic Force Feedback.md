# Cinematic Force Feedback

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/26874136
- Page ID: 26874136
- Breadcrumb: Film and Cutscenes > Cinematics Overview > Scene Interactivity > Cinematic Force Feedback
- Parent: Scene Interactivity

## Content

##
Overview

**
Force Feedback
**
 (or Rumble) is referring to activating the gyros in external controller devices. Most commonly used are of course the Xbox 360 and the PS3 controllers.

This is often used to make impacts and
**
boom
**
 moments that have more of an impact to the player itself but they can be used for anything ranging from subtle heart beating to slowly rising earthquake rumbling.

##
Setup

##
Trackview Solution

To add the rumble tracks to your Track View sequence, simply right click anywhere and click
**
Add Script Variable
**
. You will need two of these. Name the first one
**
Cinematic_RumbleA
**
, responsible for the high frequency motor, and the second one
**
Cinematic_RumbleB
**
, responsible for the low frequency motor.

For the Rumble effects to work, you must set the
**
Cut Scene
**
 flag in the sequence properties.

Now you have normal Track View tracks you can modify to your heart's content as usual.

The nodes for force feedback only range from 0 (off) to 1 (maximum) in increments of
**
.1
**
 (you can use more subtle values like
**
.15
**
 but it most likely won't be noticeable).

Note that you can use values over 1 and it will still work but internally the engine always clamps to a maximum of 1.

Remember you can modify the curves in the curve editor as with any other node setup. This can be used to have subtly rising effects all the way to abrupt halts. Keep in mind the gyros need a bit of time to get going and to fully stop. This is a hardware limitation that cannot be circumvented by this system.

##
Flowgraph Solution

There are two flowgraph nodes that can be used to setup your force feedback experience.

The node on the left functions the same as the Track View nodes. You have Low and High pass options that function the same as setting the values in the Track View. Remember that the engine clamps to 0 and 1 as maximum even though the slider suggests you can set anything up to 100.

The node on the right has the flaw that you cannot specifically tweak the high and low frequency gyros separately but has the benefit that it allows presets. Design can draft them and code implements them so designers can use them in game and the experience is the same across the board. Keep in mind that there is many places this can be used and a single person should make sure its usage doesn't get out of hand.

##
Example Setups

Heartbeat: One stronger and quicker beat followed by a slightly weaker and longer end beat, repeat as needed.

Impact: Player falling from moderate height; impact and weaker impact afterwards to simulate a little bouncing.

Quake: Slowly rising rumble ending in a grand rumble fiesta finale which will fade out slowly.

##
Comments

While very powerful and easy to setup up it should be kept in mind that force feedback rumbling can be a very subjective topic. What seems appropriate for one person can be seen as over the top for another. It is recommended that one person sets it up after general guidelines are agreed upon by higher ups. Also there can be rather drastic differences in the hardware that is targeted by this setup. There are differences in the 360 and PS3 controllers ability when it comes to response time, sustain and feeling of the force feedback. Even within the same controller types there can be noticeable differences that can be caused by anything from old/weak gyros to differences in brand and make.

Another thing to keep in mind is where to draw the line of what should have rumble and what should not. In general nothing that wouldn't produce rumble feedback in the game itself should do so in a cinematic and vice-versa to stay consistent and not throw the player out of his/her immersion. Good examples for rumble are simulating a heartbeat in a quiet life/death situation (e.g. drowning) and heavy impacts (e.g. falling off a cliff and landing on floor 3m below). Stuff like normal footsteps etc. should not produce force feedback unless the effect is explicitly desired.

[Setup](#setup)
[Comments](#comments)
[Setup](#setup)
[Comments](#comments)

##
Overview

**
Force Feedback
**
 (or Rumble) is referring to activating the gyros in external controller devices. Most commonly used are of course the Xbox 360 and the PS3 controllers.

This is often used to make impacts and
**
boom
**
 moments that have more of an impact to the player itself but they can be used for anything ranging from subtle heart beating to slowly rising earthquake rumbling.

##
Setup

##
Trackview Solution

To add the rumble tracks to your Track View sequence, simply right click anywhere and click
**
Add Script Variable
**
. You will need two of these. Name the first one
**
Cinematic_RumbleA
**
, responsible for the high frequency motor, and the second one
**
Cinematic_RumbleB
**
, responsible for the low frequency motor.

For the Rumble effects to work, you must set the
**
Cut Scene
**
 flag in the sequence properties.

Now you have normal Track View tracks you can modify to your heart's content as usual.

The nodes for force feedback only range from 0 (off) to 1 (maximum) in increments of
**
.1
**
 (you can use more subtle values like
**
.15
**
 but it most likely won't be noticeable).

Note that you can use values over 1 and it will still work but internally the engine always clamps to a maximum of 1.

Remember you can modify the curves in the curve editor as with any other node setup. This can be used to have subtly rising effects all the way to abrupt halts. Keep in mind the gyros need a bit of time to get going and to fully stop. This is a hardware limitation that cannot be circumvented by this system.

##
Flowgraph Solution

There are two flowgraph nodes that can be used to setup your force feedback experience.

The node on the left functions the same as the Track View nodes. You have Low and High pass options that function the same as setting the values in the Track View. Remember that the engine clamps to 0 and 1 as maximum even though the slider suggests you can set anything up to 100.

The node on the right has the flaw that you cannot specifically tweak the high and low frequency gyros separately but has the benefit that it allows presets. Design can draft them and code implements them so designers can use them in game and the experience is the same across the board. Keep in mind that there is many places this can be used and a single person should make sure its usage doesn't get out of hand.

##
Example Setups

Heartbeat: One stronger and quicker beat followed by a slightly weaker and longer end beat, repeat as needed.

Impact: Player falling from moderate height; impact and weaker impact afterwards to simulate a little bouncing.

Quake: Slowly rising rumble ending in a grand rumble fiesta finale which will fade out slowly.

##
Comments

While very powerful and easy to setup up it should be kept in mind that force feedback rumbling can be a very subjective topic. What seems appropriate for one person can be seen as over the top for another. It is recommended that one person sets it up after general guidelines are agreed upon by higher ups. Also there can be rather drastic differences in the hardware that is targeted by this setup. There are differences in the 360 and PS3 controllers ability when it comes to response time, sustain and feeling of the force feedback. Even within the same controller types there can be noticeable differences that can be caused by anything from old/weak gyros to differences in brand and make.

Another thing to keep in mind is where to draw the line of what should have rumble and what should not. In general nothing that wouldn't produce rumble feedback in the game itself should do so in a cinematic and vice-versa to stay consistent and not throw the player out of his/her immersion. Good examples for rumble are simulating a heartbeat in a quiet life/death situation (e.g. drowning) and heavy impacts (e.g. falling off a cliff and landing on floor 3m below). Stuff like normal footsteps etc. should not produce force feedback unless the effect is explicitly desired.
