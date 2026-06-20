# Audio & Ambience

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/44964884
- Page ID: 44964884
- Breadcrumb: Audio > Audio Overview > Audio & Ambience
- Parent: Audio Overview

## Content

[Image: /docs/static/attachments/44964885]

##
Overview

This Tutorial explains how to setup ambient sounds in CRYENGINE.

##
Ambient Sounds in levels

CRYENGINE offers two Audio Entities;
*
AudioAreaAmbience
*
 and
*
 AudioAreaEntity.
*
Both can be used to setup ambient sounds in a level, but they do need to be attached to an Area Shape, Area Box, Area Sphere or Area Solid in a level to define the Area in which the Sound will play in.

These Entities are used to set multiple attributes that allow you to define a Play and StopTrigger, an Environment as well as the Radius around the Shape where your ambience will start to fade in.

To make use of the
*
 AudioAreaAmbience
*
 or the
*
AudioAreaEntity
*
 in a level, a new Shape must first be created. The Shapes that can be used with the
*
AudioAreaAmbience
*
 and
*
AudioAreaEntity
*
 can be found in the
Create Object
 tool under
Area
. Select either a
*
Box
*
,
*
Sphere
*
,
*
Shape
*
 or
*
Solid
*
.

For this tutorial we are going to place an Area Shape in a level. To do this go to the
Create Object
 tool and select
Area -> Shape
:

After
Shape
 has been selected click in the Perspective viewport to create points which will become the corners of your Shape.

When you have chosen the position of your last point of your Shape, double-click. This completes your created Shape.

[Image: /docs/static/attachments/44971387]

If you go to the properties of the Area Shape you can give it a name and a height:

*
[Image: /docs/static/attachments/44971388]

*

##
Using the AudioAreaAmbience

The
*
 AudioAreaAmbience
*
 Entity is the main Entity that permits the implementation of ambiences in a level. It is used when you are setting up ambiences without the need to access their information in Flow Graph for advanced implementation methods.

In order to connect the
*
AudioAreaAmbience
*
, select the previously created Shape, then click the
Targets
 button in the
Operators
 section, add a target, select the empty field and select the
*
AudioAreaAmbience e
*
ntity in your level.

The
*
AudioAreaAmbience
*
 entity will now be linked to the Shape.

[Image: /docs/static/attachments/44971392]

For the PlayTrigger option select the audio system Trigger for your ambient sound. For the Rtpc option setup the audio system Parameter that is controlling the volume of the ambience.

*
[Image: /docs/static/attachments/44971394]

*

For a full reference of the properties for the
*
AudioAreaAmbience
*
Entity please refer to
[/docs/static/engines/cryengine-5/categories/23756816/pages/44964896](
Audio Entities and Flownodes - AudioAreaAmbience
)
.

You can choose/use any name you like for the audio system RTPC that is set as the RTPC in the Entity properties of the
*
AudioAreaAmbience
*
 and
*
AudioAreaEntity.
*
 In CRYENGINE we use the name "area_fade_distance".

If your character is moving towards the Area in a level, then the PlayTrigger will be called as soon as the character enters into the maximum distance as defined by the RtpcDistance value in the Entity properties.

When moving closer to the shape the RtpcDistance value is increasing and moves closer to 1, this therefore increases the volume of the ambience and in accordance to the setup in your audio middleware.

As long as your character is within the Area Shape the RtpcDistance equals 1 and therefore your ambience will play without attenuation.

The distance that is output by the
*
AudioAreaAmbience and AudioAreaEntity
*
is always scaled in the range of 0 to 1 from the maximum range you are setting in RTPC Distance. Therefore, the range of the RTPC used by your middleware needs to be as well normalized from 0 to 1.

The latest CRYENGINE 5.3.1 update includes a new parameter
Inner Fade Distance
under the following entities in the Area object:

-
Solid

-
Box

-
Sphere

-
Shape
This value (specified in meters) determines how far an ambience sound can blend into the shape with higher priority.

[Image: /docs/static/attachments/44971396]

Previously, this value was determined based on the largest
RTPC Distance
 value specified in the Audio entities such as
[/docs/static/engines/cryengine-5/categories/23756816/pages/44964896](
*
Audio Area Ambience
*
)
,
[/docs/static/engines/cryengine-5/categories/23756816/pages/44964896](
*
Audio Area Entity
*
)
*

*
and
[/docs/static/engines/cryengine-5/categories/23756816/pages/44964896](
A
*
udio Area Random
*
)
*

*
which are attached to the inner area where the listener enters. This prevented the option of determining individual roll offs for a shape with multiple entities such as Audio Area Ambience and Audio Area Random, attached to it.

In addition, it can cause also confusion since the same parameter serves different purposes based on whether the attached shape has a higher or lower priority value.

Now, the
RTPC distance
 in the Audio entity specifies the roll off to the outside, while the
Inner Fade Distance
 on the Area Solid, Area Box, Area Sphere, or Area Shape specifies the roll off to the inside.

[Image: /docs/static/attachments/44971398]

##
Using the AudioAreaEntity

The
*
AudioAreaEntity
*
 works in a similar way to the
*
AudioAreaAmbience,
*
but needs manual setup via Flow Graph to trigger the audio system Controls.

This extra step gives you access to multiple parameters and more advanced setup possibilities than with the
*
AudioAreaAmbience
*
.

When looking at the properties of the
*
AudioAreaEntity
*
 you will notice that it does not contain an RtpcDistance, but includes a FadeDistance parameter. This value behaves the same as in the
*
AudioAreaAmbience,
*
but is named differently as it can be connected to any Object via Flow Graph and not only an audio system control RTPC.

You will also notice that there are no Play and Stop Triggers in the Entity properties, this is because they are setup manually in Flow Graph - this is explained in the next step.

[Image: /docs/static/attachments/44971399]

For a full reference of the properties for the
*
AudioAreaEntity
*
 please
*

*
refer to
[/docs/static/engines/cryengine-5/categories/23756816](
Audio Entities and Flownodes
)
.

In order to setup an
*
AudioAreaEntity
*
 in a level first follow the same steps as with the
*
AudioAreaAmbience
*
 i.e. by placing the Entity in your level and connecting it to an Area Shape.

*
Adding a Flownode for the selected entity
*

[Image: /docs/static/attachments/44971400]

Best Practice
It is useful to contain all audio functionality inside one Flow Graph. It's also good practice to place a Flow Graph Entity in your Audio Layer and create all Flow Graph specific audio inside of it.

For this add the Flow Graph Entity which can be found in the
Create Object tool
under
Entity -> Default -> FlowgraphEntity
 and create a Flow Graph on the Entity which all your Audio Objects will use.

Now, we have to add an AudioAreaEntity to the level by opening the
Create Object
 tool, going to
Audio -> Audio Area Entity
. and drag it into the scene. Next, inside
Flow Graph
, we right-click and choose
Add Selected Entity
 to add the Audio Area Entity to the graph.

The
*
AudioAreaEntity
*
 Flow Graph node does not have any Playback functionality itself. It outputs triggers when the character is entering or leaving the connected Area or by its outer values as defined by the EventDistance. It also sends out a value that can be used to control any audio system RTPC via the
*
Audio:Rtpc
*
 node.

Therefore, in order to enable the playback of an ambience for your Area with the
*
AudioAreaEntity
*
 you have to add an Audio:Trigger and an Audio:RTPC node to the Flow Graph.

After adding an
*
Audio:Trigger
*
 and an
*
Audio:RTPC
*
 node to the Flow Graph, right-click on them and select
Assign Selected Entity
 from the menu (in this example AudioAreaEntity1). Now both the
*
Audio:Trigger
*
 and the
*
Audio:RTPC
*
 nodes will  be set to their assigned Entity which in this case is
*
AudioAreaEntity1
*
.

Double-click on the
Name
 input on the Rtpc node and select the area_fade_distance Rtpc:

*
[Image: /docs/static/attachments/44971402]

*

The value for the Rtpc node comes from the Entities properties 5 (meters) and this is passed through to the Audio:Rtpc node from the AudioAreaEntity
*
FadeValue
*
 output. The volume of the sound will then increase until the edge of the shape is reached.

The Audio:Trigger node will also need a sound assigned to the PlayTrigger. This is done in the same way as we assigned the the area_fade_distance to the Rtpc above: by double-clicking on PlayTrigger and choosing a sound, for example
Play_l_global_sfx_waterfall_large_loop
.

After doing this, we'll just have to connect the nodes in the way shown below and the Flow Graph should work:

*
[Image: /docs/static/attachments/44971404]

*

Jump in the game and check it out!

You don't need to specify a StopTrigger as CRYENGINE automatically stops the playing of the audio system Trigger if no Stop Event is assigned.

In the case of the ambience setup, the StopTrigger is called when leaving the maximum RtpcDistance/FadeDistance.

When in the Editor, ambiences that are setup with the
*
AudioAreaEntity
*
 will not play by default as they are triggering the audio system Controls in Flow Graph.

In order to preview the
*
AudioAreaEntity
*
 when not in-game you have to enable the AI/Physics button so that the Flow Graph is calculated.

[Image: /docs/static/attachments/44971406]

##
Working with Shape Priorities and Shape Nesting

When you are using multiple Shapes in a level you can setup GroupIds and Shape Priorities in order to define how the Audio behaves when transitioning from one Shape to another.

You can set the GroupId and Priority per Shape in the properties:

[Image: /docs/static/attachments/44971408]

If the shapes share the same GroupId, the Shape with the higher priority will override the
*
RtpcDistance/FadeDistance
*
 that is set on the
*
AudioAreaAmbience/AudioAreaEntity
*
 of the Shape with the lower priority.

##
Example

Shape A has
*
GroupId
*
 of 1,
*
Priority
*
 of 20 and a
*
FadeDistance
*
 of 10, whereas Shape B has a
*
GroupId
*
of 1
*
, Priority
*
 of 40 and a
*
FadeDistance
*
 of 5. Shape B is nested in Shape A.

*
Example of shapes with same GroupId and different Priority and FadeDistance
*

[Image: /docs/static/attachments/44971409]

-
When the player approaches Shape A, then 10 m before the edge of the Shape the sound starts to fade in.

-
When the player approaches Shape B, then 5 m before the edge of the Shape the sound starts to fade in.

-
When the player enters Shape B the sound of Shape A fades out within 5 m.
Easier Shape Selection
With
Helpers
 enabled and pressing the
Spacebar
 on your keyboard will show the Pivots of all Entities in your level. This feature also allows you to select Areas more easily when they are nested together.

##
Using Sound Obstruction on Area Shapes

The sides of an Area Shape and an Area Box can be flagged for obstruction by enabling the DisplaySoundInfo checkbox.

Obstructed sides are displayed in red and do
*
not
*
 calculate the ambience updates for that segment.

Non-obstructed sides are displayed green and
*
do
*
 calculate ambience updates for that segment.

[Image: /docs/static/attachments/44971410]

This feature can be used to define doorways and windows as well as offering greater flexibility in complex shape in shape setups.

[#ambient-sounds-in-levels](
Ambient Sounds in levels
)
[#using-the-audioareaambience](
Using the AudioAreaAmbience
)
[#using-the-audioareaentity](
Using the AudioAreaEntity
)
[#working-with-shape-priorities-and-shape-nesting](
Working with Shape Priorities and Shape Nesting
)
[#using-sound-obstruction-on-area-shapes](
Using Sound Obstruction on Area Shapes
)
