# SDL Mixer Initial Setup

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/44964959
- Page ID: 44964959
- Breadcrumb: Audio > Audio Middleware > SDL Mixer Workflow > SDL Mixer Initial Setup
- Parent: SDL Mixer Workflow

## Content

##
SDL Mixer in CRYENGINE

CRYENGINE includes a simple audio implementation system using SDL Mixer. This implementation method is intended for simple projects that do not need the power of more professional solutions, and acts as a base from where development teams can create their own in-house audio solutions.

The implementation method currently supports the playing and stopping of MP3, Ogg Vorbis and WAVE files when audio system
[Triggers](../../../Editor%20Tools/Audio%20Controls%20Editor.md#AudioControlsEditor-ControlTypes)
are executed and setting up switches and states to provide extra control over the sounds playing.

##
In this topic

[SDL Mixer in CRYENGINE](#sdl-mixer-in-cryengine)
[In this topic](#in-this-topic)
[Setting up Your Project](#setting-up-your-project)
[Getting Started](#getting-started)

##
Setting up Your Project

Follow the below steps to setup your project:

-
Enable the SDL Mixer in CRYENGINE's
Console
 by setting the
*
s_ImplName
*
 CVar to
*
CryAudioImplSDLMixer
*
. This is the default setting in CRYENGINE. As an alternative you can also add following line in your system.cfg or user.cfg file (located in the root folder of the CRYENGINE):

s_ImplName = CryAudioImplSDLMixer

-
Copy all your Ogg Vorbis or WAVE files to
*
/<project folder>/assets/audio/sdlmixer
*
 In release 5.5 this location changed to
*
/<project folder>/<project assets folder>/audio/sdlmixer/assets
*
, where
*
<project assets folder>
*
 refers to the assets folder set in the project's .cryproject file.

The SDL Mixer can only play 16 bit, 48 kHz sample rate, stereo or mono files in either *.mp3, *.wav or *.ogg formats.

##
Getting Started

After you setup your project, you should be able to see all of your audio files when you open the
[Audio Controls Editor](../../../Editor%20Tools/Audio%20Controls%20Editor.md)
. The Audio Controls Editor can be accessed via the CRYENGINE's main menu
Tools -> Audio Controls Editor
.

When you select an audio system Trigger in your project, it allows you to connect the audio files that you want to play or stop when that trigger is executed. You can simply drag and drop your audio file to the
Connected Controls
 field in the Properties panel
*
.
*
 Alternatively, you can also drag the audio files directly over the Audio Controls tree and add an audio system Trigger directly to an audio file.

![Image](https://www.cryengine.com/docs/static/attachments/44968275)

After you have made the connection between an audio system Trigger and your audio file(s), you can select the audio file in the Connected Controls pane to display its properties.

Property
 |
Description
 |

Action

 |
Lets you to choose to either
Start
 or
Stop
 playback of the audio file in the object where the trigger is executed. For other objects where the same sound is used will not be affected by the
Stop
 action.

 |

Enable Panning

 |
Enables the audio to pan depending on the position of the audio object and the listener's position.

 |

Enable Distance Attenuation

 |
Enables the sound to be linearly attenuated based on the distance between the audio object and the listener's position.

 |

Min Distance

 |
Lets you specify the distance from the listener when the sound starts to attenuate, if Distance Attenuation is enabled.

 |

Max Distance

 |
Lets you specify the distance from the listener when the sound stops to be audible, if Distance Attenuation is enabled.

 |

Volume

 |
Lets you specify the volume in dB at which the sound should be played.

 |

Looping

 |
Lets you specify the
Count
 value to determine the number of times the sound gets repeated before it stops. When
Infinite
 is set the sound will loop until it is explicitly stopped (using the Stop action in another trigger) or when the object is destroyed.

 |

##
Placing an Audio System Trigger in the Game

If you have followed the above steps, you can now select your audio system Trigger in the Editor and play it back on an audio entity. You can pre-listen to your audio system Triggers in the Audio Controls Editor by either right-clicking on it and selecting
Execute Trigger
 or by pressing the
spacebar
.

In order to hear your sound in the game, you need to place an audio entity in the level which executes the audio system Trigger during game play.

For each level, it is recommended to first create a dedicated Audio-Layer which will contain all your audio data. For creating a dedicated Audio-Layer, click on the
Level Explorer
 tab, create a new Layer and name it Audio:

![Image](https://www.cryengine.com/docs/static/attachments/44968276)

As long as the Audio layer is active (double-click on it and you'll see a blue
V
 showing that the layer is active), all the entities you are placing in the level are going to be included in the layer.

![Image](https://www.cryengine.com/docs/static/attachments/52592792)

Now go to the
Create Object
 tab, select
Audio
 and then the
*
Audio Trigger Spot
*
 entity. You can place the entity in the level by dragging and dropping it into the
Perspective
 Viewport.

![Image](https://www.cryengine.com/docs/static/attachments/52592793)

Best Practice
It is always recommended to name your audio entities using abbreviations. This improves readability particularly while working on large projects. For example, we use ATS as the abbreviation for the
*
Audio Trigger Spot;
*
hence the sound of a small fire could be named ATS_small_fire on the
*
Audio Trigger Spot
*
.

Here are some common audio specific abbreviations:

-
*
AAA (Audio Area Ambience)
*

-
*
AAE (Audio Area Entity)
*

-
*
AAR (Audio Area Random)
*

-
*
ATS (Audio Trigger Spot)
*

-
*
ACE (Audio Controls Editor)
*

-
*
ASh (Area Shape)
*

-
*
AB (Area Box)
*

-
*
ASp (Area Sphere)
*

-
*
ASo (Area Solid)
*

-
*
FG (Flow Graph)
*
You can now select your audio system Trigger in the
Properties
 tab of the
*
Audio Trigger Spot
*
.

![Image](https://www.cryengine.com/docs/static/attachments/52592794)

For more information on
*
Audio Trigger Spot
*
 in combination with the SDL-Mixer, please refer
[here](SDL%20Mixer%20%26%20SpotFX.md)
.
