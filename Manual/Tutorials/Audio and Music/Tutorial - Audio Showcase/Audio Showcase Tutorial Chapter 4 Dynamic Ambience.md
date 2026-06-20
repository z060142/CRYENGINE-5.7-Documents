# Audio Showcase Tutorial Chapter 4: Dynamic Ambience

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/56000755
- Page ID: 56000755
- Breadcrumb: Tutorials > Audio and Music > Tutorial - Audio Showcase > Audio Showcase Tutorial Chapter 4: Dynamic Ambience
- Parent: Tutorial - Audio Showcase

## Content

##
Overview

Since our Chinese Garden is a relatively small level, it doesn't make sense to create multiple global ambiences between which the level would switch as the player moves through it. Rather, it seems best to create a single global ambience containing different layers corresponding to:

-
Water sounds within the level,

-
Forest sounds that surround the level,

-
Sounds for the marketplace area situated on one end of the level.
These layers would grow louder as the player drew close, and fade as they moved farther away. The sounds for each of these are included in the
*
chapter_04 → loop
*

folder of your chosen middleware implementation, located within the Audio Showcase assets' installation directory, as:

**
FMOD
**
 |
Wwise
 |
SDLMixer
 |
**
Purpose
**
 |

*
l_cg_amb_water_a_01 - 03.wav
*
 |
*
l_cg_amb_water_a_01 - 03.wav
*
 |
*
Play_l_cg_amb_water_a.ogg
*
 |
First water body.
 |

*
l_cg_amb_water_b_01 - 03.wav
*
 |
*
l_cg_amb_water_b_01 - 03.wav
*
 |
*
Play_l_cg_amb_water_b.ogg
*
 |
Second water body.
 |

*
l_cg_amb_forest_01 -
*

*
03.wav
*

 |
*
l_cg_amb_forest_01 -
*

*
03.wav
*

 |
*
Play_l_cg_amb_forest.ogg
*
 |
Forest area.
 |

*
l_cg_amb_marketplace_01 - 03.wav
*
 |
*
l_cg_amb_marketplace_01 - 03.wav
*
 |
*
Play_l_cg_amb_marketplace.ogg
*
 |
Marketplace.
 |

*
l_cg_amb_global_base_
01 - 03.wav
*
 |
*
l_cg_amb_global_base_
01 - 03.wav
*
 |
*
Play_l_cg_amb_global_base.ogg
*
 |
Global ambience.
 |

*
l_cg_amb_global_day_01 - 03.wav
*

 |
*
l_cg_amb_global_day_01 - 03.wav
*

 |
*
Play_l_cg_amb_loop_day.ogg
*
 |
Day sounds for global ambience.
 |

*
l_cg_amb_global_night_01 - 03.wav
*

 |
*
l_cg_amb_global_night_01 - 03.wav
*

 |
*
Play_l_cg_amb_loop_night.ogg
*
 |
Night sounds for global ambience.
 |

We begin by defining a global area box, before creating area shapes for each of the required layers.

![Image](https://www.cryengine.com/docs/static/attachments/44105760)

*
Dynamic ambience overview
*

##
FMOD Video Tutorial

The FMOD workflow of this chapter is also covered in the following video:

[Embed: https://www.youtube.com/watch?v=5wgAJTuHtNw]

##
Defining a Global Area Box

With our Chinese Garden level loaded on CRYENGINE's Sandbox, create a new folder called
*
audio
*
 within the Level Explorer (located at the bottom left-corner of the Editor, by default) by right-clicking a blank space, and selecting the
**
New Folder
**
 option from the context menu. Within it, create a new layer called
*
area shape
*
and double click it to make it the active layer.

This means that all entities created henceforth will be added to this layer by default.

Located above the Level Explorer is the Create Object tool, which is used to create/add entities and objects to a scene. Select the
**
Area → Box
**
 option within it to begin creating our Area Box. At this point, you should be able to see the Area Box's properties listed within the Properties panel situated on the right of your Editor window.

![Image](https://www.cryengine.com/docs/static/attachments/44105768)

*
Area box properties
*

You may set the width, length and height of the Area Box to the values used in the image above, or your own values, provided the Area Box is big enough to fully surround the entire level. Once its size has been set, click within the Viewport to place the Area Box in the level. Also:

-
Give the Area Box a custom name using the
**
Name
**
 field, located under the
**
General
**
 tab of the Properties panel. We've named our Area Box
*
AB_Global_Exterior
*
 for the sake of this tutorial.

-
Set the Area Box's
**
Group Id
**
 and
**
Priority
**
 to 1 and 5 respectively, under the
**
Area box
**
 tab of the Properties panel. The significance of these values will be made clear further on.

##
Creating the Global Ambience

The idea behind creating the global ambience in this section is to have a static background layer that isn't triggered from a specific position, and a set of one shots that are positioned around the player as part of the 3D environment. Both are combined to create a rich ambience with a relatively simple setup.

FMOD Global Ambience Setup.

##
FMOD

Switch back to your FMOD project, and create a new sub-folder called
*
loop
*
 within the
*
Ambience
*
 folder of your FMOD
**
Events
**
 tab and Audio Bin.

-
Drag
*
 l_cg_amb_global_base_01.wav, l_cg_amb_global_base_02.wav
*
 and
*
l_cg_amb_global_base_03.wav
*
from the
*
_Audio_Assets/FMod Studio/chapter_04/loop
*
folder of your project into the
*
loop
*
 folder of the Audio Bin.

-
Next, drag and drop the three files from the Audio Bin into the
**
Events
**
tab of your project to create a new Event; the Event should be 2D, with one multi-instrument. Name it
*
Play_l_cg_amb_global
*
.
This Event requires two more audio tracks, for day and night variations of the global ambience.

![Image](https://www.cryengine.com/docs/static/attachments/56000778)

*
FMOD global ambience
*

-
In the
**
Timeline
**
 view of the
*
l_cg_amb_global
*
 Event, right-click the Base track and select the
**
Add Audio Track
**
 option from the menu; then, drag and drop the
*
l_cg_amb_global_day_01.wav, l_cg_amb_global_day_02.wav
*
and
*
l_cg_amb_global_day_03.wav
*
 files from the Audio Bin onto the audio track to create a multi-instrument for the global ambience's daytime sounds.

-
Repeat the above step for the
*
*
l_cg_amb_global_night_01.wav, l_cg_amb_global_night_02.wav
*
*
 and
*
*
l_cg_amb_global_night_03.wav
*
*
 files as well, creating a multi-instrument for nighttime sounds, as shown in the GIF above.
Once the three multi-instruments have been created, add a loop region for the entire
*
Play_l_cg_amb_global
*
Event, as described in the
[previous chapter](/docs)
. Also,

-
Activate the
**
Async
**
 and Loop Playlist
![Image](https://www.cryengine.com/docs/static/attachments/56000777)
 options for each multi-instrument,

-
Add a loop region for the Event.
Finally, add the
*
Play_l_cg_amb_global
*
Event to your
*
Ambience
*
 Soundbank. Rebuild all Soundbanks and save the FMOD project.

Wwise Global Ambience Setup.

##
Wwise

Rather than import every audio file from the
*
*
_Audio_Assets/Wwise/chapter_04/loop
*
*
 folder into the
*
Ambience
*
 Actor-Mixer we created in Chapter 01, it's better to use Wwise's Import Folder function.

-
Right-click the
*
Ambience
*
 Actor-Mixer and select the
**
Import Audio Files
**
 option from the menu.

-
Click the
**
Add Folders...
**
 button in Audio File Importer window, navigate to the

*
*
_Audio_Assets/Wwise/chapter_04/
*
*
 directory and select the
*
Loop
*
 folder. The
**
Audio/File Folder
**
 column shows the structure of the
*
Loop
*
 folder as it appears on disk, while the
**
Object
**
column shows the folder structure that will be created in Wwise. The folder
*
Loop
*
 at the top of this structure will serve as our Actor-Mixer.

-
In the
**
Object Type/Action
**
 column, select the dropdown corresponding to this
*
Loop
*
 folder, and change its values from
**
Virtual Folder
**
 to
**
Actor-Mixer
**
.

-
Similarly, set the
**
Object Type/Action
**
 values of the
*
l_cg_amb_global
*
 and the
*
l_cg_amb_global_timeofday
*
folders to
**
Blend Container
**
, and the remaining folders to
**
Random Container
**
 as shown.
![Image](https://www.cryengine.com/docs/static/attachments/56000768)

*
Import audio files
*

A Blend Container has two purposes:

-
To blend (fade) two or more sub-containers based on the value of a Real-Time Parameter Control (RTPC).

-
To group all sub-containers and play them at the same exact moment. This works only if the Blend Container has no Blend Track assigned to it.
Recall that the global ambience that we're creating must contain three different layers that play simultaneously; the Base layer which contains background cricket noise, the Day layer with bird calls, and a Night layer with more cricket and frog sounds.

Our
*
l_cg_amb_global
*
Blend Container contains two sub-containers: the
*
l_cg_amb_global_base
*
 Random Container which corresponds to the base layer, and the
*
l_cg_amb_global_timeofday
*
 Blend Container which contains the day/night layers as Random Containers.

Set the
*
l_cg_amb_global_base, l_cg_amb_global_day
*
 and
*
l_cg_amb_global_night
*
 Random Containers to loop, as we did to the fire particle in the
[previous chapter](/docs)
, and set their Transition
**
Type
**
 values to
**
Xfade (power).
**
Use the GIF below for reference.

![Image](https://www.cryengine.com/docs/static/attachments/56000767)

*
Transition Type
*

Finally, create a new Play Event for the
*
l_cg_amb_global
*
 Blend Container, create a new folder called
*
Loop
*
within the
*
Ambience
*
 folder in the
**
Events
**
 tab, and add the
*
Play_l_cg_amb_global
*
event to it. Also remember to Generate All SoundBanks and save your project.

SDL Mixer Global Ambience Setup.

##
SDL Mixer

Copy
the
*
Play_l_cg_amb_loop_base.ogg
*
 file from

*
_Audio_Assets/SDL Mixer/chapter_04/

*
folder of your Audio Showcase Level installation into the
*
Assets/Audio/SDL_Mixer/assets

*
directory of your project.

##
Connecting The Global Ambience To The Area Box

Switch back to the ACE on CRYENGINE and create the folder
*
loop
*
 within the library
*
Ambience
*
 that we created in Chapter 01.

-
Drag and drop
*
Play_l_cg_amb_global
*
 from the Middleware Data panel into the
*
loop
*
 folder in the Audio System Controls panel, creating a trigger of the same name.

If using SDL Mixer, activate
**
 Infinite Loop
**
 and deactivate the
**
Enable Attenuation
**
and
**
Enable Panning
**
 properties of the
*
Play_l_cg_amb_global
*
audio trigger in the Properties panel.
Also, create a parameter for the
*
Play_l_cg_amb_global
*
audio Trigger in the
*
Ambience
*
 folder of the Audio System Controls panel:

-
Right-click within the
*
Ambience
*
folder and select the
**
Add → Parameter
**
option. Name it
*
Param_Play_l_cg_amb_global.
*

-
Connect the corresponding sound file to the parameter, by selecting the Parameter, dragging and dropping the
*
Play_l_cg_amb_loop_base.ogg
*
 file from the Middleware Data panel into the
**
Connections
**
 section of the ACE's Properties panel.
The created parameter is used in a custom FlowGraph script included within the Audio Showcase Level that changes the volume of ambience sounds based on the time of day.

-
Save the library and reload the audio engine.
On CRYENGINE, Audio Area Ambience is an Entity that permits the implementation of a simple ambience within a level, without having to define its functionality in Flow Graph. It needs to be linked to an Area Shape, Area Box, Area Sphere or Area Solid to function.

In the Level Explorer, create a new layer called
*
audio_area_ambience
*
 within the
*
audio
*
folder we created at the beginning of this chapter; double-click the
*
audio_area_ambience
*
layer to make it the active layer. Since we need to create an
*
Audio Area Ambience
*
 Entity to implement our
*
Play_l_cg_amb_global
*
 ambience:

-
In the Create Object tool, select the
**
Audio → Audio Area Ambience
**
option.

-
Click anywhere within the Viewport to place the
*
Audio Area Ambience
*
Entity. We'll call it
*
AAA_Global_Exterior
*
for the rest of this tutorial.

-
Attach the
*
Play_l_cg_amb_global
*
trigger to the
*
AAA_Global_Exterior
*
 Entity via its
**
PlayTrigger
**
 property field in the Properties panel.
Recall that the
*
Audio Area Ambience
*
 Entity now needs to be connected to the
*
AB_Global_Exterior
*
 Area Box we created at the beginning of this section.

-
Select the
*
AB_Global_Exterior
*
 Area Box to display its properties in the Properties panel.

-
Under the
**
Area
**
tab of the Properties panel, click the
**
Pick
**
 button, then select the
*
AAA_Global_Exterior
*
 Entit
*
y
*
from the Viewport.
You should now be able to hear the global ambience, however only when the default camera of the Perspective Viewport is situated inside the Area Box. On FMOD and Wwise, the global ambience can be made to fade as the Viewport camera draws farther away, by creating a Parameter.

If you're unable to hear the global ambience within the Area Box, move the Viewport camera outside the Area Box and reenter it again to trigger the sound.

##
Fading The Global Ambience

SDL Mixer users can skip this section of the tutorial.

Fading The Global Ambience With FMOD.

##
FMOD

Open the Preset Browser in FMOD Studio and create a
**
User: Continuous
**
parameter with the name
*
area_fade_distance
*
.  Let its range be between
**
0
**
 and
**
1
**
.

-
In the Events tab of your project, select the
*
Play_l_cg_amb_global
*
Event.

-
Click the
**
+
**
symbol besides the Event's Timeline tab, above its timeline, and add the
*
area_fade_distance
*
tab.
![Image](https://www.cryengine.com/docs/static/attachments/56000776)

*
Area fade distance
*

To now add an automation to the Event, as shown in the GIF above, such that the
*
Play_l_cg_amb_global
*
 ambience is fully audible when the
*
area_fade_distance
*
 Parameter reaches 1, and inaudible when 0:

-
Right-click on the Master track's volume dial and select the
**
Add Automation
**
 option from the menu.

-
Adjust the curve as shown in the GIF above. The small dot that is on the center of the line between the two points can also be moved to change the sound's fade.
Save the FMOD project and remember to rebuild all Soundbanks. Back in the ACE, the
*
area_fade_distance
*
parameter should be listed under the
*
Parameters
*
folder of the Middleware Data panel. Drag and drop it into the
*
Ambience
*
folder in the Audio System Controls panel to create a parameter in the Audio System of the same name.

-
In the Viewport, select the
*
AAA_Global_Exterior
*
Entity to display its properties in the Properties panel.

-
Add the
*
area_fade_distance
*
 parameter to the
**
Rtpc
**
 property field by clicking the
![Image](https://www.cryengine.com/docs/static/attachments/56000756)
 icon against it.

-
Under the
**
AudioAreaAmbience Properties
**
 tab is a property called
**
RtpcDistance
**
. Let's set its value to 20.
The distance output of the

*
Audio Area Ambience
*
 Entity
is always scaled in the range of 0 to 1 with respect to the maximum range specified by its
**
RtpcDistance
**
property, such that the
**
RtpcDistance
**
 parameter increases and moves to 1 as the listener draws closer to the Area shape the Entity is linked to.

It is for this reason that the range of the
*
area_fade_distance
*
 parameter created in our FMOD project was also normalized to 0 to 1.

Fading The Global Ambience With Wwise.

##
Wwise

Navigate to the
**
Game Syncs
**
 tab in the Project Explorer and create a parameter with the name
*
area_fade_distance
*
 as follows:

-
Select the
*
Default Work Unit
*
 under
*
Game Parameters
*
, and then click the
![Image](https://www.cryengine.com/docs/static/attachments/56000766)
 symbol at the top of the panel.

-
In the Property Editor panel, set the
**
Min
**
,
**
Max
**
and
**
Default
**
 values of the
**
Range
**
 to
**
0
**
,
**
1
**
and
**
1
**
 respectively;
**
Default
**
 corresponds to the value assigned to the parameter when no value is sent by the game Engine, for example, while previewing an audio trigger in the ACE.
![Image](https://www.cryengine.com/docs/static/attachments/56000765)

*
area_fade_distance
*

We now need to link this parameter to the
*
l_cg_amb_global
*
Blend Container.

-
Select the
*
l_cg_amb_global
*
Container from the
**
Audio
**
tab of the Project Explorer.

-
In the Property Editor, open the
**
RTPC
**
 tab, click on the
![Image](https://www.cryengine.com/docs/static/attachments/56000764)
 symbol, and select the
**
Voice Volume
**
 option; this adds the voice volume of the
*
l_cg_amb_global
*
Blend Container to the y-axis.

-
Now, click the
![Image](https://www.cryengine.com/docs/static/attachments/56000764)
 symbol under the
**
X axis
**
 field and select the
**
Game Parameters → Default Work Unit → area_fade_distance
**
*

*
option which adds the value of the
*
area_fade_distance
*
 to the x-axis.
![Image](https://www.cryengine.com/docs/static/attachments/56000763)

*
l_cg_amb_global Property Editor
*

The default curve that is now displayed in the Property Editor indicates that the
*
Play_l_cg_amb_global's
*
 Event will be muted when the
*
area_fade_distance
*
 p
*
arameter
*
 reaches to 0, and will be fully audible when the game Engine sets the parameter to 1.

Save your Wwise project after generating all SoundBanks. Back in the ACE, the
*
area_fade_distance
*
parameter should be listed under the
*
Game
*

*
Parameters
*
folder of the Middleware Data panel. Drag and drop this parameter
*

*
into a new library called
*
Parameter
*
 in the Audio System Controls panel, to create a parameter in the Audio System of the same name.

-
Back in the Viewport, select the
*
AAA_Global_Exterior
*
Entity to display its properties in the Properties panel.

-
Add the
*
area_fade_distance
*
 parameter to the
**
Rtpc
**
 property field by clicking the
![Image](https://www.cryengine.com/docs/static/attachments/56000756)
 icon against it.

-
Under the
**
AudioAreaAmbience Properties
**
 tab is a property called
**
RtpcDistance
**
. Let's set its value to 20.
If set up correctly, you'll find that the global ambience sound now fades out as the Viewport camera moves away from the global ambience box.

##
Setting Up The Remaining Ambience Layers

Now that we have our global ambience working, it's time to add the remaining layers of ambience for the forest, marketplace area and water bodies as shown in the following image.

![Image](https://www.cryengine.com/docs/static/attachments/56000757)

*
Showcase Audio Ambience
*

FMOD Ambience Layers Setup.

##
FMOD

Create 2D events for all remaining sounds contained in the
*
_Audio_Assets/FMod Studio/chapter_04/loop
*
folder of your project as follows:

 |
Event

 |
Files
 |
Type
 |

1
 |
*
Play_l_cg_amb_forest
*

 |
*
l_cg_amb_forest_01.wav, l_cg_amb_forest_02.wav
*
and
*
 l_cg_amb_forest_03.wav.
*

 |
2D Event with one multi-instrument
 |

2
 |
*
*
Play_l_cg_amb_marketplace
*
*
 |
*
l_cg_amb_marketplace_01.wav, l_cg_amb_marketplace_02.wav
*
 and
*
l_cg_amb_marketplace_03.wav.
*
 |
2D Event with one multi-instrument
 |

3
 |
*
*
Play_l_cg_amb_water_a
*
*
 |
*
l_cg_amb_water_a_01.wav
*
,
*
l_cg_amb_water_a_02.wav
*
and
*
l_cg_amb_water_a_03.wav,
*

 |
2D Event with one multi-instrument
 |

4
 |
*
*
Play_l_cg_amb_water_b
*
*
 |
*
l_cg_amb_water_b_01.wav
*
,
*
l_cg_amb_water_b_02.wav
*
and
*
l_cg_amb_water_b_03.wav.
*

 |
2D Event with one multi-instrument
 |

Make sure to activate the
**
Async
**
 and Loop Playlist
![Image](https://www.cryengine.com/docs/static/attachments/56000777)
 options for each of the above multi-instruments that you create. Also create a loop region for each of them, and add  the
*
area_fade_distance
*
 parameter to their timelines; the shape of the
*
area_fade_distance
*
curves for each must be the same as that of the
*
Play_l_cg_amb_global
*
Event
.

Save the project, rebuild Soundbanks, and create triggers for each of the Events in the ACE.

Wwise Ambience Layers Setup.

##
Wwise

Since we've already imported the audio files corresponding to the remaining ambience layers in the Creating The Global Ambience section of this chapter, all we need to do is make the
*
l_cg_amb_forest
*
,
*
l_cg_amb_marketplace
*
,
*
l_cg_amb_water_a
*
 and
*
l_cg_amb_water_b
*
 Random Containers loop.

-
Select these Random Containers, right-click and select the
**
Show in Multi-Editor
**
 option from the menu. The options we need are located under
**
Audio → General Settings → Random Sequence Container → Play Mode
**
in the Multi-Editor.

-
Under
**
Play Mode
**
, set the value of the
**
Step or Continuous
**
 field to
**
Continuous
**
. Also activate the
**
Loop
**
 and
**
Transition
**
 checkboxes, and set the
**
Transition Type
**
 to
**
Xfade (power)
**
; these changes will automatically apply to all selected Containers.
![Image](https://www.cryengine.com/docs/static/attachments/56000762)

*
Multi-editor
*

Finally, we need to add the
*
area_fade_distance
*
parameter curve to each of the Random Containers.

-
Select the
*
l_cg_amb_global
*
 Blend Container, navigate to its RTPC tab in the Property Editor, right-click the entry on the bottom panel of the Property Editor, and select the
**
Copy
**
 option from the menu.

-
Paste this entry onto the RTPC tabs of the
*
l_cg_amb_forest
*
,
*
l_cg_amb_marketplace
*
,
*
l_cg_amb_water_a
*
 and
*
l_cg_amb_water_b
*
 Random Containers.
![Image](https://www.cryengine.com/docs/static/attachments/56000761)
*
Copying area_fade_distance
*

Now create a new Event for each of the Random Containers, and add them to the
*
Ambience → Loop
*
Event folder. Save your project, generate all SoundBanks, and create Triggers for each of the Events in the ACE.

SDL Mixer Ambience Layers Setup.

##
SDL Mixer

Copy the following files from the
*
_Audio_Assets/SDL Mixer/chapter_04/

*
folder of your Audio Showcase Level installation, into the
*
Assets/Audio/SDL_Mixer/assets

*
directory of your project.

-
*
Play_l_cg_amb_forest.ogg
*

-
*
Play_l_cg_amb_marketplace.ogg
*

-
*
Play_l_cg_amb_water_01.ogg
*

-
*
Play_l_cg_amb_water_02.ogg
*
Create audio Triggers for each of the files in the ACE; also activate their
**
Infinite Loop
**
 properties, and deactivate the
**
Enable Panning
**
 and
**
Enable Attenuation
**
 properties for each.

Create parameters for each of the imported audio files, similar to how we did for the
*
Play_l_cg_amb_global.ogg
*
 audio file previously, for the custom Flow Graph script that changes the volume of sounds according to the time of day. Name each parameter as
*
Param_<filename>.
*

##
Adding Area Shapes To The Level

Recall that the Audio Area Ambience Entity is used to implement simple ambiences within a level, which in turn must be linked to an
*
Area Shape
*
 to function.  We begin then by creating
*
Area Shapes
*
 for each of the Events created in the previous section.

-
Create a new layer
*
area_shape
*
 in the Level Explorer.

-
In the Create Object tool, select the
**
Area → Shape
**
 option to create an
*
Area Shape
*
.
Although we'd previously used the
*
Area Box
*
 in creating the global ambience, the area shapes of the forest, marketplace and water bodies need to be more precise, for which reason we're creating
*
Area Shapes
*
 for each.

-
Click on the edges of one of the two water surfaces, being as accurate as possible, to start creating its
*
Area Shape
*
. Whenever you choose to stop/finish creating the
*
Shape,
*
double-click while placing a point; finally, name the created Shape according to the
*
[Showcase_Audio ambience](Audio%20Showcase%20Tutorial%20Chapter%204%20Dynamic%20Ambience.md#AudioShowcaseTutorialChapter4%3ADynamicAmbience-a)

*
image above
*
(AS_Water_a
*
 or
*
AS_Water_b
*
, for example).

Make sure the
**
Close
**
**
d
**
 property is activated in the Properties panel when creating the
*
Area Shape,
*
to ensure that a closed Shape is created.

-
Set the value of the
**
Height
**
 property of the created Shape to any easy-to-read value between
**
10
**
 and
**
50
**
 in the Properties panel.

-
Similarly, create
*
Area Shapes
*
 for the remaining water bodies, the marketplace, forest, and the two pagodas
*
(House_a
*
 and
*
House_b
*
), respectively.

-
To improve the visibility of your
*
Area Shapes
*
 in the Viewport, activate the
**
Display Filled
**
 property from the Properties panel; this fills the created areas with color in the Viewport.

-
To move a created
*
Area Shape
*
, use the
![Image](https://www.cryengine.com/docs/static/attachments/56000774)
 button from the upper left corner of the Editor.

-
To move only a specific point of a created
*
Area Shape,
*
click the
**
Edit Shape
**
 button under the
**
Operators
**
 tab of the Properties panel.
We now need to set the Group ID and Priority values for each of the
*
Area Shapes,
*
as we did for the Global Area Box earlier on in this section. Group ID's along with Priority help define how the ambient sounds of
*
Area Shapes
*
 are processed, such that when two or more Shapes share the same Group ID, the Shape with the highest Priority is processed first.

This is useful when
*
Area Shapes
*
 are nested within each other; an Audio Area Ambience that is attached to an
*
Area Shape
*
 will stop playing when the listener enters an inner
*
Area Shape,
*
 if the priority of the inner Shape is higher than the outer. If the Group ID and the Priority values of two or more Shapes are equal, the Shapes have no influence over each other.

Use the following Group ID and Priority setup for the
*
Area Shapes
*
 created.

AS / AB Properties
 |
Global
 |
AS_Water_a
 |
AS_Water_b
 |
Forest
 |
Marketplace
 |
House_a
 |
House_b
 |

**
Group ID
**
 |
1
 |
2
 |
2
 |
2
 |
2
 |
1
 |
1
 |

**
Priority
**
 |
2
 |
5
 |
5
 |
5
 |
5
 |
10
 |
10
 |

**
Inner Fade Distance
**
 |
0
 |
0
 |
0
 |
0
 |
0
 |
7.5
 |
4
 |

The
**
Inner Fade Distance
**
 property determines how far the ambience of an
*
Area Shape
*
 blends into another
*
Shape
*
 of higher priority. You'll  notice that both pagodas have a higher priority in comparison to the other shapes; the goal is to have the global ambience fade out as the listener enters into one of the pagodas.

It is for this reason that the
**
Inner Fade Distance
**
 property values for
*
House_01
*
 and
*
House_02
*
have been set to 7.5 and 4 respectively

Activating the
**
Display Sound Info
**
checkbox in the Property panels of the
*
House_01
*
 and
*
House_02
*

*
Area Shapes
*
 reveals Sound Obstruction options for the Shapes' sides. Ticking a checkbox flags that side for obstruction; the distance of the player from an Area Shape is not calculated from the obstructed sides.

Since we don't require the ambience to fade with respect to player distance at the floor/roof of the pagodas, the sides corresponding to the floors/roofs can be deactivated. The obstructed sides of an
*
Area Shape
*
are marked in red.

##
Creating AAA Entities for all Area Shapes

With the
*
Area Shapes
*
 created for the forest, marketplace, two water bodies and two pagodas in the previous section, we now need to create Audio Area Ambience Entities for each of the
*
Area Shapes
*
, except for those of the pagodas (
*
House_a
*
 and
*
House_b).
*
When doing so, make sure to set the
*
audio_area_ambience
*
layer as the active layer.

After creating the Audio Ambience Entities, set the values of their
**
Play Trigger
**
,
**
Rtpc
**
and
**
Rtpc Distance
**
 fields to the following values.

AAA Properties
 |
Global
 |
AS_Water_a
 |
AS_Water_b
 |
Forest
 |
Marketplace
 |

**
Play Trigger
**
 |
Play_l_cg_amb_global
 |
Play_l_cg_amb_water_a
 |
Play_l_cg_amb_water_b
 |
Play_l_cg_amb_forest
 |
Play_l_cg_amb_marketplace
 |

**
Rtpc
**
 |
**
FMOD
**
 |
area_fade_distance
 |

**
Wwise
**
 |
area_fade_distance
 |

**
SDL Mixer
**
 |
Param_l_cg_amb_global
 |

 |
**
FMOD
**
 |
area_fade_distance
 |

**
Wwise
**
 |
area_fade_distance
 |

**
SDL Mixer
**
 |
Param_l_cg_amb_global
 |

 |
**
FMOD
**
 |
area_fade_distance
 |

**
Wwise
**
 |
area_fade_distance
 |

**
SDL Mixer
**
 |
Param_l_cg_amb_global
 |

 |
**
FMOD
**
 |
area_fade_distance
 |

**
Wwise
**
 |
area_fade_distance
 |

**
SDL Mixer
**
 |
Param_l_cg_amb_global
 |

 |
**
FMOD
**
 |
area_fade_distance
 |

**
Wwise
**
 |
area_fade_distance
 |

**
SDL Mixer
**
 |
Param_l_cg_amb_global
 |

 |

**
Rtpc Distance
**
 |
20
 |
5
 |
5
 |
30
 |
7
 |

Feel free to experiment with your own
**
Rtpc Distance
**
 values; recall that the
**
Rtpc Distance
**
 property defines the distance over which parameter fades from 1 to 0.

Finally, remember to attach the Audio Area Ambience Entities to their corresponding
*
Area Shapes
*
 using the
**
Pick
**
 button, located under the
**
Operators
**
 tab of the
*
Area Shapes'
*
Properties panel. You can then go ahead and listen to the outcome in Game Mode. If you'd like, you could even design custom ambiences for each of the pagodas, although the absence of sound often has a greater impact on the listener.

##
One Shots For Bird Calls

What we've created at this stage, is a dynamic ambience with five different layers. To further improve its realism, let's add in a few random one shots to the global ambience using Audio Trigger Spot (ATS) Entities.

FMOD Bird Call Setup.

##
FMOD

Located in the
*
_Audio_Assets/FMod Studio/chapter_04/Oneshot
*
folder of your project directory are 11 different bird calls,  named
*
Play_l_cg_amb_one_shot_bird_a/b/c/d/e_0X.wav.
*
Drag these into your Audio Bin to create five Events as follows:

 |
Event

 |
Files
 |
Type
 |

1
 |
*
Play_l_cg_amb_one_shot_bird_a
*
 |
*
l_cg_amb_one_shot_bird_a_01.wav,
*

*
l_cg_amb_one_shot_bird_a_02.wav,
*

and
*
l_cg_amb_one_shot_bird_a_03.wav
*

 |
3D Event with one multi-instrument
 |

2
 |
*
Play_l_cg_amb_one_shot_bird_b
*
 |
*
l_cg_amb_one_shot_bird_b_01.wav
*
and
*
l_cg_amb_one_shot_bird_b_02.wav
*
 |
3D Event with one multi-instrument
 |

3
 |
*
*
Play_l_cg_amb_one_shot_bird_c
*
*
 |
*
*
l_cg_amb_one_shot_bird_c_01.wav
*
*
 and
*
*
l_cg_amb_one_shot_bird_c_02.wav
*
*

 |
3D Event with one multi-instrument
 |

4
 |
*
*
Play_l_cg_amb_one_shot_bird_d
*
*
 |
*
*
l_cg_amb_one_shot_bird_d_01.wav
*
*
and
*
*
l_cg_amb_one_shot_bird_d_02.wav
*
*
 |
3D Event with one multi-instrument

 |

5
 |
*
*
Play_l_cg_amb_one_shot_bird_e
*
*
 |
*
*
l_cg_amb_one_shot_bird_e_01.wav
*
*
and
*
*
l_cg_amb_one_shot_bird_e_02.wav
*
*
 |
3D Event with one multi-instrument
 |

Since we'd like to hear the bird calls across the entire level, we'll set the
**
Max
**
 attenuation distance of each event to
**
100
**
 meters within the Spatializer plugin. Add the Events to the Ambience Soundbank, rebuild all Soundbanks, and switch back to the ACE to create audio triggers for each of them.

Wwise Bird Call Setup.

##
Wwise

Using the Import Folder function like we did while creating the Global Ambience, add the
*
Oneshots
*
folder included in the
*
*
_Audio_Assets/Wwise/chapter_04/
*
*
directory of your project, to the
*
Ambience
*
 Actor Mixer. Remember to s
et the
**
Object Type/Action
**
 of the
*
Oneshots
*
 folder
to
**
Actor-Mixer.
**

Included in the
*
Oneshots
*
 folder are 11 different bird calls, named
*
l_cg_amb_one_shot_bird_a/b/c/d/e_0X.wav.
*
Create five Random Containers for these bird calls as follows:

 |
Random Container

 |
Audio Files
 |

1
 |
*
l_cg_amb_one_shot_bird_a
*
 |
*
l_cg_amb_one_shot_bird_a_01.wav,
*

*
l_cg_amb_one_shot_bird_a_02.wav,
*

and
*
l_cg_amb_one_shot_bird_a_03.wav
*

 |

2
 |
*
l_cg_amb_one_shot_bird_b
*
 |
*
l_cg_amb_one_shot_bird_b_01.wav
*
and
*
l_cg_amb_one_shot_bird_b_02.wav
*
 |

3
 |
*
*
l_cg_amb_one_shot_bird_c
*
*
 |
*
*
l_cg_amb_one_shot_bird_c_01.wav
*
*
 and
*
*
l_cg_amb_one_shot_bird_c_02.wav
*
*

 |

4
 |
*
*
l_cg_amb_one_shot_bird_d
*
*
 |
*
*
l_cg_amb_one_shot_bird_d_01.wav
*
*
and
*
*
l_cg_amb_one_shot_bird_d_02.wav
*
*
 |

5
 |
*
*
l_cg_amb_one_shot_bird_e
*
*
 |
*
*
l_cg_amb_one_shot_bird_e_01.wav
*
*
and
*
*
l_cg_amb_one_shot_bird_e_02.wav
*
*
 |

Create a new Attenuation Share-Set on the
*
Oneshots
*
Actor-Mixer similar to the one used on the
[campfire particle audio](/docs)
. However since we'd like to hear the bird calls across the entire level, set the
**
Max distance
**
 of the Attenuation Share-Set to 100m. Name it
*
Attenuation_100m.
*

Attenuation Share Sets are hereditary, meaning all of the
*
Oneshots
*
 Actor-Mixer's children will use the same attenuation settings.

Finally, create Events for each of the bird-call Random Containers, add them to a new
*
Oneshots
*
Events folder, and generate all SoundBanks. Save your project, before switching back to the ACE to create audio triggers for each of them.

SDL Mixer Bird Call Setup.

##
SDL Mixer

The bird call one shots are included within the
*
_Audio_Assets/SDL Mixer/chapter_04/

*
folder of your Audio Showcase Level as
*
Play_l_cg_amb_one_shot_bird_a.ogg, Play_l_cg_amb_one_shot_bird_b.ogg, Play_l_cg_amb_one_shot_bird_c.ogg
*
and
*
Play_l_cg_amb_one_shot_bird_d.ogg.
*
Copy
these
into the
*
Assets/Audio/sdlmixer/assets

*
directory of your project and create audio Triggers for each.

Also create parameters with the name
*
Param_<filename>
*
 for each created audio Trigger.

Activate the
**
Enable Panning
**
 and
**
Enable Attenuation
**
 properties for each of the bird call one shot Triggers.

After the bird call Events have been created using your choice of middleware, create a new layer called
*
one_shots
*
 within the Level Explorer, and double-click it to make it the active layer.

-
Create five Audio Trigger Spots, corresponding to each of the bird call events
*
Play_l_cg_amb_one_shot_bird a/b/c.d
*
.

-
Place these in four different positions above the Garden wall.

-
Shift-click the first and last of the five Audio Trigger Spots to activate the multi-update option; activate the
**
DrawRandomizationArea
**
 Debug property from the Properties panel, which displays a box around the area where randomization of the ATS Entity is applied.

-
Now tweak the values of the
**
RandomizationArea
**
 property, which determines the dimensions of the area boxes made visible in the previous step. The sound of the trigger linked to an Audio Trigger Spot is randomly positioned within its area box.

Even though SDL Mixer doesn't provide any form of audio randomization, its sound attenuation feature can be used as a means to randomize sound volume. This can be done by giving the
**
RandomizationArea
**
 of an area box a high depth value, such that sounds will appear high in volume when they're triggered close to the player, and lower in volume when triggered farther away.

![Image](https://www.cryengine.com/docs/static/attachments/56000773)

*
Bird call area boxes
*

Finally, connect the bird call audio triggers created at the beginning of this section to the Audio Trigger Spots, using the
**
Play Trigger
**
 property from the ATS Entities' Properties panel. We'll also set the
**
Behavior
**
 property of each ATS to
**
Trigger Rate
**
and its
**
Max Delay
**
 value to
**
100,000;
**
this causes the audio triggers to execute every 'x' seconds after the previous trigger instance is done, where 'x' is a random value between their
**
Min Delay
**
 and
**
Max Delay
**
 values.

##
Forest One Shots

To wrap up, we'll add a few one shots to the forest ambience through FMOD/Wwise.

The implementation of forest one shots requires the use of a Scatterer Instrument (FMOD) or Random Container (Wwise); since SDL Mixer lacks a system to achieve similar effects, the implementation of forest one shots via SDL Mixer has been omitted in this tutorial. Users can still create a setup similar to the bird one shots for the forest one shots; however, this would be tedious to implement.

FMOD Forest One Shots Setup.

##
FMOD

Go back to your FMOD project, and open the
*
Play_l_cg_amb_forest
*
ambience we created earlier in this section.

-
Add a new Audio track in the
**
Timeline
**
 tab of the
*
Play_l_cg_amb_forest
*
 Event.

-
To this Audio Track, add a Scatterer Instrument by right-clicking its timeline and selecting the
**
Add Scatterer Instrument
**
 option from the menu.

-
Click on the Scatterer Instrument and open the Audio Bin; drag the
*
l_cg_amb_forest_oneshot_crack_01 - 06
*

**
.wav
**
files from the
*
_Audio_Assets/FMod Studio/chapter_04/Oneshot
*
folder of your project directory, and drop them into the
*
Ambience → Oneshot
*
folder of your Audio Bin.

-
Then, drag and drop
*
l_cg_amb_forest_oneshot_crack_01 - 05.wav
*
 into the Scatterer Instrument's playlist as shown in the GIF below.
A Scatterer Instrument allows the trigger rate and positioning of a sound to be randomized, which is ideal for the forest one shots we'd like to add.

![Image](https://www.cryengine.com/docs/static/attachments/56000772)

*
Scatterer Instrument playlist
*

The playlist of a Scatterer Instrument displays all audio assets that can be triggered by it; make sure to enlarge the Scatterer Instrument to the exact length of the defined loop region.

With the Scatterer Instrument selected, you can change the trigger rate of the files in the Scatterer Instrument's playlist using the panel at the bottom of your FMOD window. For the forest crack one shots, we've set the Spawn interval to
**
2.50s - 6.50s
**
and the Min/Max Scatter Distance to
**
0.10 - 1.00
**
. Since the original assets already sound subtle and distant, we don't need too big of a distance value.

Repeat the above steps to create another audio track using the
*
l_cg_amb_forest_oneshot_creak_01 - 05
*
**
.wav
**
files from your project's
*
_Audio_Assets/FMod Studio/chapter_04/Oneshot
*
folder.

-
Set its Spawn interval to a bigger range of
**
8.00s - 22.00s
**
, and its Min and Max Scatter Distance to
**
2.00
**
 and
**
 30.0
**
respectively.

-
Name both audio tracks so that they can be distinguished later on.

Wwise Forest One Shot Setup.

##
Wwise

In the
**
Audio
**
tab of Wwise's Project Explorer, create a parent Blend Container for the
*
l_cg_amb_forest
*
 Random Container; name the Blend Container
*
l_cg_amb_forest
*
 as well.

-
Add a new Random Container to the
*
l_cg_amb_forest
*
 Blend Container and name it
*
l_cg_amb_forest_oneshot_crack.
*
Drag and drop files
*
l_cg_amb_forest_oneshot_crack_01 - 06
*
from the
*
Oneshot
*
 Actor-Mixer into the
*
l_cg_amb_forest_oneshot_crack
*
 Random Container.

-
In the Property Editor, set
**
Play Mode
**
 to
**
Loop
**
, activate the
**
Transitions
**
 toggle, and set the Transition
**
Type
**
 to
**
Trigger Rate.
**

-
Set the
**
Duration
**
 value to 4.5 seconds and double-click the
![Image](https://www.cryengine.com/docs/static/attachments/56000760)
 icon to open the Randomizer window; tick the
**
Enabled
**
checkbox to activate the Randomizer, and set the
**
Min Offset/Max Offset
**
to -2 and 2 respectively.

The Trigger Rate duration specifies how often the
*
l_cg_amb_forest_oneshot_crack
*
Random Container is triggered and a new sound selected to play; the Randomizer helps apply an additional randomization to the trigger rate, allowing for a bit of variation in timing between each sound.

It'd also be appropriate for the one shot to play at random positions, rather than in a 2D space around the player.

-
Switch to the
**
Positioning
**
tab in the Property Editor, tick the
**
Override Parent
**
 checkbox, and set the value of the
**
3D Spatialziation dropdown
**
to
**
Position + Orientation
**
.

-
Assign the
*
Attenuation_100m
*
 Share Set created in the previous section to the
**
Attenuation
**
 field.

-
Change the value of the
**
3D Position
**
 field to
**
Emitter with Automation
**
 from the dropdown to set a user-defined position automation of the sound around the listener.
Click the
**
Automation...
**
 button to open the 3D Automation window. Create a new automation path and set the Random Range to the values used in the image below; also activate the
**
Pick new Path when sound starts
**
 toggle to force a new automation path to be used every time the sound is triggered.

![Image](https://www.cryengine.com/docs/static/attachments/56000759)

*
l_cg_amb_forest_oneshot_crack automation
*

Repeat the above setup for the
*
l_cg_amb_forest_oneshot_creak_01 - 05
*
 audio files, to create a
*
l_cg_amb_forest_oneshot_creak
*
 Random Container within the
*
l_cg_amb_forest
*
 Blend Container.

-
Set the Trigger Rate
**
Duration
**
to 3 seconds.

-
Set the
**
Min Offset/Max Offset
**
to -1 and 1 respectively in the Randomizer.

The above
**
Duration
**
 and
**
Min Offset/Max Offset
**
 values have been set for a more natural sounding ambience.

Before generating all SoundBanks, make sure to update the
*
Play_l_cg_amb_forest
*
Event.

-
Select the
*
Play_l_cg_amb_forest
*
 Event in the
**
Events
**
 tab of the Property Editor to open the Event Editor on the right panel.

-
Switch to the
**
Audio
**
 tab in the Property Editor, drag and drop the
*
l_cg_amb_forest
*
Blend Container Blend Container into the Event Editor.
Save the project, generate all SoundBanks and try all your changes in Sandbox.

##
Changing the Global Ambience With Time of Day

Now that we have finished setting up our ambience, we'd like to have it change based on the level's time of day. This is relatively easy to do, as most of the information is automatically given to the ACE by default..

SDL Mixer
SDL Mixer handles parameters in a way that is unsuitable for a time of day based implementation of the ambience. A time of day setup similar to FMOD and Wwise can be achieved in combination with Flow Graph scripts, which is beyond the scope of this tutorial; it has hence been omitted for the SDL Mixer implementation of this tutorial.

FMOD Time of Day Setup.

##
FMOD

-
Create a new Parameter called
*
time-of-day
*
 with a range of 0-24 within your FMOD project, and add it to the ACE.

-
In your FMOD project, select the
*
Play_l_cg_amb_global
*
 Event, and add the
*
time_of_day
*
 Parameter to it using the
**
+
**
 icon besides its
**
Timeline
**
and
**
area_fade_distance
**
parameters in the center panel.

-
Next, add a Volume Automation for your Night and Day Audio tracks by right-clicking the volume dial on each of the tracks, and selecting the
**
Add Automation
**
 option from the menu.

-
Add points of automation to the Volume curves of both tracks by clicking on the dotted line; the day ambience should be audible between 10 a.m - 6 p.m, fading in/out over 4 hours. The night ambience meanwhile should be audible during the remaining hours. The curves should resemble those in the image below.
![Image](https://www.cryengine.com/docs/static/attachments/56000771)

*
Volume automation
*

You can now save your project, rebuild Soundbanks and switch back to CRYENGINE.

Wwise Time of Day Setup.

##
Wwise

In the
**
Game Syncs
**
 tab of Wwise, create a new parameter called
*
time_of_day
*
 with a range of 0 - 24, and set its default value to 12 via the Property Editor.

We now have to add a blend track to the
*
l_cg_amb_global_timeofday
*
Blend Container.

-
Select the Blend Container and click the
**
Edit...
**
 button in the
**
Blend Tracks
**
section of the Property Editor.

-
In the Blend Track Editor that opens, activate the
**
Crossfade
**
 toggle and click the
![Image](https://www.cryengine.com/docs/static/attachments/56000764)
 icon to add the
*
time_of_day
*
 parameter to the Blend Track. You can also rename the Track as per your preference.
The created Blend Track is displayed under the
**
Blend Tracks
**
 section of the Content Editor.

-
Drag the
*
l_cg_amb_global_night
*
 Random Container from the left panel of the Content Editor, and drop it into the
**
Blend Tracks
**
 section. Repeat the same for the
*
l_cg_amb_global_day
*
 Container, and for
*
l_cg_amb_global_night
*
. This determines the behavior of the Containers in the Blend Track Editor, such that the
*
day
*
 Container is in between two
*
night
*
 Containers.

-
Click on any other Random Container and then back on
*
l_cg_amb_global_timeofday
*
; if you open the Blend Track Editor again, you should now be able to see three distinct areas corresponding to the
*
night
*
,
*
day
*
 and
*
night
*
 Containers respectively.

-
The edges of each track can be moved; set the first
*
l_cg_amb_global_night
*
 track to a
*
time_of_day
*
parameter range of 0-10, the middle
*
l_cg_amb_global_day
*
 track to a range of 6-22, and the second
*
l_cg_amb_global_night
*
 track to a range of 18-24. This results in a fade of 6-10 and 18-22 between the
*
day
*
and
*
night
*
 tracks.
Compare the outcome to the GIF below; changes can be previewed by pressing the
**
spacebar
**
, and moving the
*
time_of_day
*
cursor over the Blend Track in the Blend Track Editor.

![Image](https://www.cryengine.com/docs/static/attachments/56000758)

*
time_of_day Blend Track
*

If you can't preview sounds, perhaps your
*
area_fade_distance
*
 parameter is set to 0. This can be changed by clicking on the
**
RTPCs
**
 button in the
**
Transport Control
**
 panel at the bottom of your project's Designer Layout.

Save your project, generate all SoundBanks and switch back to CRYENGINE.
Reload the audio engine, drag and drop the
*
time_of_day
*
 parameter from the Middleware Data panel into the
*
Parameter
*
 Library in the Audio Systems Control panel.

Reload the audio engine, and open the Environment Editor tool using the
**
Tools → Environment Editor
**
 option from the Sandbox's Main Menu.

-
First, create a new Environment preset by selecting the
**
New
**
 option from the Environment Editor's
![Image](https://www.cryengine.com/docs/static/attachments/56000770)
 menu.

-
From this window, you can now customize different properties of the level's day-night cycle. Set the speed of the day-night cycle to 1, using the
**
Speed
**
 field at the bottom of the window.

-
Jump into Game Mode to try out your changes.
![Image](https://www.cryengine.com/docs/static/attachments/56000769)

*
Environment Editor
*

If the global ambience fails to play, exit Game Mode and move the Viewport camera far outside the global ambience area box before bringing it back in again to re-trigger the ambience.

Feel free to tweak all the Parameters we've created up to this point to achieve different results. You could, for example, deactivate bird calls at night time with the help of the
*
time_of_day
*
parameter, or possibly increase the volume of the forest ambience at night time to emphasize darkness outside the Garden.

##
Conclusion

Congratulations, you've made it to the end of the Audio Showcase Tutorial using CRYENGINE V. We've put together a few suggestions at the bottom of this section, to ensure you're getting the most out of your middleware implementation on CRYENGINE.

-
Make sure to always save your FMOD/Wwise Project to see newly created Events, Parameters or Soundbanks within the ACE.

-
After rebuilding Soundbanks, CRYENGINE's audio engine must always be refreshed so that cached Soundbanks are refreshed.

-
Pay attention to the naming of Tracks, Parameters, Events, Banks, Folders etc. As projects grow in size, it can quickly become difficult to keep track of all variables.

-
If for some reason you can't hear an Event in FMOD/Wwise, make sure that no Parameter is set to a value that makes the Event inaudible.
[FMOD Video Tutorial](#fmod-video-tutorial)
[Defining a Global Area Box](#defining-a-global-area-box)
[Creating the Global Ambience](#creating-the-global-ambience)
[Connecting The Global Ambience To The Area Box](#connecting-the-global-ambience-to-the-area-box)
[Fading The Global Ambience](#fading-the-global-ambience)
[Setting Up The Remaining Ambience Layers](#setting-up-the-remaining-ambience-layers)
[Adding Area Shapes To The Level](#adding-area-shapes-to-the-level)
[Creating AAA Entities for all Area Shapes](#creating-aaa-entities-for-all-area-shapes)
[One Shots For Bird Calls](#one-shots-for-bird-calls)
[Forest One Shots](#forest-one-shots)
[Changing the Global Ambience With Time of Day](#changing-the-global-ambience-with-time-of-day)
[Conclusion](#conclusion)
