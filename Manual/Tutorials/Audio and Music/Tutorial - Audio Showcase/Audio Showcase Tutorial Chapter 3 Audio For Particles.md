# Audio Showcase Tutorial Chapter 3: Audio For Particles

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/56000727
- Page ID: 56000727
- Breadcrumb: Tutorials > Audio and Music > Tutorial - Audio Showcase > Audio Showcase Tutorial Chapter 3: Audio For Particles
- Parent: Tutorial - Audio Showcase

## Content

##
Overview

By the end of Chapter 01, we'd succeeded in creating a very basic ambience for our Chinese Garden, before moving on to add sound effects/foley to the gunfire and footsteps of the first-person character.

This chapter sees us visiting the campfire situated at the center of the map, to add looping audio to the fire particle along with a realistic attenuation. The audio files we'll be using are included in the
*
chapter_03
*
 folder of your chosen middleware implementation, located within the Audio Showcase assets' installation directory.

Go ahead and listen to them!

![Image](https://www.cryengine.com/docs/static/attachments/56000745)

*
Fireplace
*

##
FMOD Video Tutorial

The FMOD workflow of this chapter is also covered in the following video:

[Embed: https://www.youtube.com/watch?v=9qUtvEwRk0A&feature=youtu.be]

##
Adding a Loop to The Fire Particle

FMOD Looping Audio Setup.

##
FMOD Studio

The audio files that we'll be using to create a looping audio effect for the campfire, are stored in the
*
_Audio_Assets/FMod Studio/chapter_03/
*
folder of your Audio Showcase assets' installation directory as
*
l_global_particle_fire_01.wav, l_global_particle_fire_02.wav, l_global_particle_fire_03.wav, l_global_particle_fire_04.wav and l_global_particle_fire_05.wav.
*

Create a new folder in the Audio Bin and
**
Event
**
 tab of your FMOD project called
*
Particle,
*
and drag/drop the five audio files into them to create a new 3D multi-instrument Event. Name it
*
l_global_particle_fire.
*

Select the
*
l_global_particle_fire
*
 Event and click on the
**
Multi-instrument
**
 timeline at the center of the screen; y
ou should see the following playlist of audio assets that make up the Event in the bottom panel.

![Image](https://www.cryengine.com/docs/static/attachments/56000748)

*
Playlist
*

Click the
![Image](https://www.cryengine.com/docs/static/attachments/56000733)
 button to have the audio files play in a loop when the Event is triggered. To make sure the Event loops properly, activate the
**
Async
**
 option; this ensures that the audio assets play in their entirety once triggered, especially if they aren't of the same length. You'll notice the waveforms of all five audio assets are stretched to fit the time scale on the multi-instrument; this is just a visual change as the assets sound exactly the same as before.

If you now play the Event, you'll notice two locators moving across the multi-instrument display. The smaller one inside of each track displays the playback time of that file, while the bigger locator is used for automation data. The subject of automation is addressed in Chapter 04.

We then need to create a Loop Region to specify the area of the Multi-instrument that needs to be looped. Since we'd like for the entire Multi-Instrument's timeline to loop:

-
Right-click the
**
Multi-instrument
**
 timeline and select the
**
New Loop Region
**
 option from the context menu.

-
This creates a new blue marker above the
**
Multi-instrument
**
 timeline. Play the Event and listen to the result.
Finally, add this
*
l_global_particle_fire
*
 Event to a new Bank called
*
Particle
*
, before rebuilding all SoundBanks by pressing the
**
F7
**
 key. Switch back to the ACE and create a new Library called
*
Particle
*
 in the
**
Audio System Controls
**
 panel.

-
Drag and drop the
*
l_global_particle_fire
*
 Event we just created into the
*
Particle
*
Library to create an audio trigger of the same name.

-
Also add the
*
Particle
*
 Soundbank from the
**
Middleware Data
**
 panel to the
*
Preloads
*
 library before reloading the audio engine.

Wwise Looping Audio Setup.

##
Wwise

The audio files that we'll be using to create a looping audio effect for the campfire are stored in the
*
_Audio_Assets/Wwise/chapter_03/
*
folder of your Audio Showcase assets' installation directory as
*
l_global_particle_fire_01.wav, l_global_particle_fire_02.wav, l_global_particle_fire_03.wav, l_global_particle_fire_04.wav and l_global_particle_fire_05.wav.
*

Begin by creating a new Actor-Mixer called
*
Particle
*
in the Default Work Unit of the
*
Actor-Mixer Hierarchy,
*
a new
*
Particle
*
 folder in the
**
Events
**
 tab, and a new
*
Particle
*
 SoundBank in Wwise. Then drag and drop all assets from the
*
_Audio_Assets/Wwise/chapter_03/
*
folder into a new Random Container within the
*
Particle
*
Actor-Mixer, and name the Container
*
l_global_particle_fire.

*

The goal is to create a looping fire particle that plays random audio files on each loop for maximum variety. To do this, a parent Random Container needs to created for our current
*
l_global_particle_fire
*
Container:

-
Right-click the
*
l_global_particle_fire
*
 Random Container and select the
**
New Parent → Random Container
**
option. Name the parent Random container
*
l_global_particle_fire.
*

-
Select the parent
*
l_global_particle_fire
*
Container and then in the
**
General Settings
**
 tab of the Property Editor, set the
**
Play Mode
**
 to Continuous. Select the
**
Loop
**
 option, activate
**
Transitions
**
, and set the transition
**
Type
**
 to
**
Xfade(power)
**
 from the dropdown.
The Xfade (power) crossfade on Wwise allows for a smooth crossfade between the audio files of a Container, while keeping the volume constant.

![Image](https://www.cryengine.com/docs/static/attachments/56000744)

*
Transitions
*

A Transition
**
Duration
**
of 1 second is appropriate; now, when the parent
*
l_global_particle_fire
*
 Container is looped, it triggers the child
*
l_global_particle_fire
*
 Container which then randomly selects one of the
*
l_global_particle_fire_0X
*
files. In this way, multiple different audio systems can be created simply by combining different container types in Wwise.

-
Next, create a new Event for the parent
*
l_global_particle_fire
*
Container by right-clicking it and selecting the
**
New Event → Play
**
option.

-
In the
**
Events
**
 tab, create a new folder called
*
Particle,
*
 and move the
*
Play_l_global_particle_fire
*
 Event you just created into it.

-
Finally, add the
*
Particle
*
 Event folder to the
*
Particle
*
 SoundBank. Save the project and Generate All Soundbanks.
Switch back to the ACE and create a new Library called
*
Particle
*
 in the Audio System Controls panel.

-
Drag and drop the
*
Play_l_global_particle_fire
*
 Event we've just created into the
*
Particle
*
Library to create an audio trigger of the same name.

-
Also, add the
*
Particle
*
 Soundbank from the Middleware Data panel to the
*
g_preloads
*
 library before reloading the audio engine.
SDL Mixer Looping Audio Setup.

##
SDL Mixer

Audio for the campfire has been included as
*
Play_l_global_particle_fire.ogg,
*
 under the

*
_Audio_Assets/SDL_Mixer/
chapter_03/
*
folder of the Audio Showcase Level assets' installation directory.

-
Create a new Library called
*
Particle
*
 under the

*
/Assets/Audio/sdlmixer/assets
*
directory of your project, and copy the file into it.

-
Set the value of the
**
Max Distance
**
 property to
**
10
**
 in the Properties panel.

-
Also activate the
**
Infinite Loop
**
 property.
When
**
Enable Attenuation
**
 is activated, the
**
Max Distance
**
 field's value specifies the distance at which the trigger's sound will be completely inaudible. The
**
Infinite Loop
**
property meanwhile, c
auses the audio Trigger to loop indefinitely.

Save the created Library and reload the audio engine before proceeding to link the Trigger to the fire particle.

##
Adding the Trigger to the Fire Particle

Particles refer to the elements that are used to create visual effects or small physical objects that can move, emit light, react to collisions and so forth. The Particle Editor provides a node based visualization of a particle's components, and will be used to add audio to the campfire's fire particle. Go ahead and open it using the
**
Tools → Particle Editor
**
 option from the Sandbox's Main Menu.

The fire particle is located in the
*
/Assets/Particles/Fire.pfx
*
 folder of our project's asset directory; open it by clicking the
![Image](https://www.cryengine.com/docs/static/attachments/56000732)
 button at the top-right corner of the Particle Editor tool window, and selecting the
*
Open
*
 option.

![Image](https://www.cryengine.com/docs/static/attachments/56000737)

*
Particle setup
*

You should now be able to see the different components that make up the fire particle. To add the
*
Play_l_global_particle_fire
*
audio trigger created in the previous step to the particle:

-
Right-click on empty space within the
**
Effect
**
 window.

-
Search for the
**
default → audio
**
 component in the search box that appears, and select it.
Now the goal is to have the audio trigger stop when the fire particle is killed, It should also not re-trigger, since the
*
Play_l_global_particle_fire
*
 Event from which the audio trigger is derived has already been designed to loop in our middleware setup.

-
In the
**
audio
**
 component, select the purple
**
Audio: Trigger
**
 feature. This displays a list of the feature's properties in the Inspector panel of the Particle Editor window.

-
Add the
*
Play_l_global_particle_fire
*
 trigger to the
**
Play Trigger
**
 field by clicking the icon and selecting the trigger from the list that appears.

-
Refresh the
**
audio
**
 component by left-clicking on empty space within the
**
Effect
**
window, and then back on the
**
Audio: Trigger
**
 feature. Activate the
**
Follow Particle
**
and
**
Stop on Death
**
 properties of the component in the Inspector panel.
As the name implies, the
**
Stop on Death
**
 property causes an audio trigger to stop playing when the particle is disabled. The
**
Follow Particle
**
 property meanwhile, causes the sound of an audio trigger to follow the particle as it is moved around a scene; it is hence recommended that this setting be used when the audio trigger is designed to loop.

Lastly, click the brown
**
Life: Time
**
feature and deactivate the
**
Life Time
**
 property from the Inspector window. This sets the value of the particle's lifetime to infinity. Remember to save all progress by selecting the
**
Save
**
 option from the
![Image](https://www.cryengine.com/docs/static/attachments/56000732)
 menu of the Particle Editor, before jumping into the game to test your fire particle sound.

##
Attenuation

FMOD Attenuation Implementation.

##
FMOD

If using an FMOD middleware implementation, you'll have noticed that the sound of the campfire trigger reduces as the player moves farther away. This is because FMOD Studio sets a default attenuation for each 3D Event.

To view the
*
Play_l_global_particle_fire
*
Event's attenuation settings within your FMOD project:

-
Select the
*
Play_l_global_particle_fire
*
Event from the
**
Events
**
 tab of your FMOD project.

-
Click the Event's Master Track
![Image](https://www.cryengine.com/docs/static/attachments/56000731)
 to see the
**
Spatializer Effect
**
 panel at the bottom of the window; this is a standard effect applied by FMOD Studio to all 3D Events.
Within the
**
Spatializer Effect
**
 panel is a red curve that describes how the volume of the Event changes with distance; specific
**
Min
**
 and
**
Max
**
 values can be set from below the curve.

By default, a distance of 1 unit in FMOD translates to 1 meter on CRYENGINE. This distance factor can be changed by using the
[s_FmodDistanceFactor](../../../Audio/Audio%20Middleware/FMOD%20Studio%20Workflow/FMOD%20Console%20Commands.md)
**

**
CVar within the console.

Any changes made to the
**
Min
**
 and
**
Max
**
 values of
*
Play_l_global_particle_fire
*
*
's
*
 attenuation can be tested within FMOD's Sandbox as follows.

-
Select
**
Window → Sandbox
**
 from FMOD Studio's main menu. This opens a window with a small arrow at the center of a grid, as shown in the image below, representing the listener's position and orientation.

-
Drag and drop the
*
Play_l_global_particle_fire
*
Event from the panel on the left onto the grid. This creates a new circle on the grid that represents the position of the Event sound with respect to the listener; click the Event circle and move it using the LMB to change its distance from the listener.

-
With the position of the Event and its distance from the Listener set, the effect of different Attenuation curves and Min/Max values can be heard by double-clicking the Event circle to trigger it.
![Image](https://www.cryengine.com/docs/static/attachments/56000747)

*
FMOD Sandbox
*

In the real world, there is not just a reduction in volume but also a loss of high frequencies as distance increases. To implement this frequency modulation in a game environment, we need to create a parameter that changes over distance.

Open the Preset Browser using the
**
Window → Preset Browser
**
 option from your FMOD Studio project window.

-
Right-click within the light-grey pane of the Preset Browser and select the
**
New Parameter
**
 option from the menu.

-
Since we need to use a Built-In Parameter, select the
**
Built-in: Distance
**
 option in the Add Parameter window that opens; its
**
Range
**
 can be set from 0 to 100, meaning that when the Event is 105 meters away from the listener, the value of the
**
Distance
**
 parameter will be 100, its highest value.

-
Click OK on the Add Parameter window to create the Parameter and close the Preset Browser.
We now need this Distance parameter to drive the cut-off frequency of a Low Pass filter.

-
First, go back to the
*
Play_l_global_particle_fire
*
Event
 in the Event Editor tab of your FMOD project, select its Master Track, and add a new Effect to it by clicking next to its
**
Spatializer
**
**
Effect
**
 panel in the bar down below. Select the
**
Add Effect →Multiband-EQ
**
option from the menu.

A multiband-EQ is used to reduce high frequencies over distance using a low-pass filter.

-
Right-click the yellow Freq. (A) value on the Multiband EQ panel and select
**
Add Automation
**
; this adds a new track called
*
Multiband EQ
*
 below the Master track.

-
Now, above the Audio 1 track of the Event is a tab called
*
Timeline
*
. Click the
**
+
**
icon beside it, and select the
**
Distance
**
 parameter from the Select Parameter window that appears, as shown.
![Image](https://www.cryengine.com/docs/static/attachments/56000746)

*
Select Parameter
*

You should now see the scale above the Audio 1 track change to the range of
**
0
**
 -
**
100
**
, which corresponds to the range of the Distance Parameter we created. By adding different points to the curve of the Multiband EQ track, you may now change the cut-off frequency of the low-pass filter at different values of the Distance Parameter as shown in the GIF above.

Add points to the Multiband EQ by left-clicking upon its red curve; points can be deleted by selecting them, and pressing the
**
Delete
**
 key. The value of the Distance Parameter can be set either by adjusting the
**
Distance
**
 dial above the scale, or by moving the slider in the
**
Distance
**
 tab,

Test various cut-off frequency values in combination with different attenuation settings using the FMOD Studio Sandbox and, when satisfied, rebuild all Soundbanks, reload the audio engine in the ACE, and jump into Game Mode to hear your changes.

If you'd like to tweak the attenuation/Distance parameter values when in-game, set the
**
s_FmodEnableLiveUpdate
**
 CVar to 1 in your project's
*
user.cfg
*
 file, and restart CRYENGINE. Once the level is loaded again, turn on live updates by clicking the
![Image](https://www.cryengine.com/docs/static/attachments/56000728)
 at the bottom of your FMOD Studio project window; set your IP address to
*
localhost
*
 and then click
**
Connect
**
.

Also in CRYENGINE, setting the
**
s_DrawDebug
**
 CVar to
*
acg
*
 will activate audio debugging such that active audio triggers are marked by spheres, while their names and their distance from the listener are displayed. The
**
s_DrawDebug
**
 CVar is capable of displaying a host of debugging information on screen; type
**
s_DrawDebug ?
**
 in the Engine Console to view all possible display options.

Wwise Attenuation Implementation.

##
Wwise

You'll notice that the sound of the campfire remains constant regardless of the player's position, because it isn't 3D spatialized. To change this:

-
Select the
*
Particle
*
 Actor-Mixer on Wwise and open the
**
Positioning
**
 tab in the Property Editor.

-
Tick the
**
Override Parent
**
 box and set the
**
3D Spatialization
**
 field to
**
Position + Orientation
**
; this positions the sound in 3D space relative to the listener's orientation.
We now need to add attenuation to the sound, which defines how the sound changes over distance; Wwise gives us the option to not only change the volume of the sound, but also set low/high-pass filters and change the spread of the sound.

Aspects such as the frequency and spread of a sound are stored within an Attenuation Share Set, which can also be used by multiple other sounds.

-
Click on the icon within the
**
Attenuation
**
 section in the
**
Properties
**
 tab of the Property Editor.

-
Select the
**
New
**
 option from the menu to create a new Share Set, and name it
*
Attenuation_30m
*
. As this Share Set is now assigned to the
*
Particle
*
 Actor-Mixer, clicking the
**
Edit
**
 button opens the Attenuation Editor as shown.
![Image](https://www.cryengine.com/docs/static/attachments/56000743)

*
Attenuation
*

The red line that you see on the Attenuation Settings graph represents the volume of the sound, which is active by default. Try setting the
**
Max
**

**
distance
**
 to
**
30
**
.

Under the
**
Curves
**
 section is a list of other parameters that can be activated; since we'd like to add a low pass filter for attenuation, change the value of the
**
Low-pass filter
**
to
**
Custom
**
in the
**
Curves
**
 section; you should now see a blue line in the Attenuation Settings grid.

-
Double-click on a curve to add a new point on it.

-
Right-click to apply a specific smoothing. It must be noted that curves are usually worse for performance than linear lines, because of the increased number of calculations that have to be made.
Feel free to use the GIF above for reference.

Multiple curves can be visualized on the Attenuation Settings grid by clicking the pin next to a curve's color code in the
**
Curves
**
 section. Note however, that only the selected curve can be edited when viewing multiple curves at a time on the grid.

Attenuation settings can be previewed by pressing the
**
spacebar
**
 in the Attenuation Editor and moving the
![Image](https://www.cryengine.com/docs/static/attachments/56000730)
box to simulate specific distances.

Test various attenuation settings and, when satisfied, generate all SoundBanks, reload the audio engine in the ACE, and jump into Game Mode to hear your changes.

If you'd like to tweak the attenuation settings when in-game, set the
**
[s_WwiseEnableCommSystem](../../../Audio/Audio%20Middleware/Wwise%20Workflow/Wwise%20Console%20Commands.md)
**
 CVar to 1 in your project's
*
user.cfg
*
 file, and restart CRYENGINE. Once the level is loaded again, click on the
**
Connect to Remote Platform
**

![Image](https://www.cryengine.com/docs/static/attachments/56000729)
 icon at the top of your Wwise window, select your system from the Remote Connections window, and press
**
Connect
**
.

Wwise should automatically identify CRYENGINE and your machine as a possible connection; for more information, press the
**
F1
**
 key in the Remote Connections window to be directed to Audiokinetic's documentation.

Also in CRYENGINE, setting the
**
s_DrawDebug
**
 CVar to
*
acg
*
 will activate audio debugging such that active audio triggers are marked by spheres, while their names and their distance from the listener are displayed. The
**
s_DrawDebug
**
 CVar is capable of displaying a host of debugging information on screen; type
**
s_DrawDebug ?
**
 in the Engine Console to view all possible display options.

##
Conclusion

Our level now contains a natural campfire sound, besides the tree movement ambient sounds we added in Chapter 01. In the next and final chapter, we'll work to create a dynamic ambience for the level by using a combination of sound layering, nested ambiences, and one shots.

[FMOD Video Tutorial](#fmod-video-tutorial)
[Adding a Loop to The Fire Particle](#adding-a-loop-to-the-fire-particle)
[Adding the Trigger to the Fire Particle](#adding-the-trigger-to-the-fire-particle)
[Attenuation](#attenuation)
[Conclusion](#conclusion)
