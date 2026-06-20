# Tutorial - Point Light Component

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/44965986
- Page ID: 44965986
- Breadcrumb: Tutorials > Game and Level Design > Entity Component Tutorials > Tutorial - Point Light Component
- Parent: Entity Component Tutorials

## Content

##
Introduction

This tutorial concentrates on the Point Light Component and serves as an introduction to its use and to some of its features. The Point Light Component emits light in all directions from the Entity and in the real world, it can be compared to a light bulb.

Before attempting this tutorial we recommend that you read the
[/docs/static/engines/cryengine-5/categories/23756816/pages/44966029](
Entity Components (From Engine Version 5.6)
)
 documentation. Doing so will give you a much better understanding of the concepts behind CRYENGINE's Entity Components, furthermore, the documentation can be used as a reference guide in regard to the various attributes/parameters that relate to each of the available Components.

Different methods can be used to create a new Entity. For more information see the
[/docs/static/engines/cryengine-5/categories/23756816/pages/44966282](
Creating an Entity
)
 documentation.

##
Creating the Point Light

Before you begin creating a light, use the Environment Editor to change the time of day to night so the sun doesn't overpower your lights. While you can

add a light component to an

*
existing

*
entity (such as a visible mesh representing a light bulb or fixture), it can also be added as a component independent of any entity. In this case, the light component itself is invisible to the player; only its effect is seen:

-
Open the

**
Create Object
**

tool

-
Click on

**
Components
**

and open the
**
Lights

**
folder to reveal
**
Point Light
**
.

-
You can either

**
drag
**

the component into the level, or
**
double-click
**

the component to put the mouse into

**
Create Object
**

mode.

The pivot of the light component will

*
snap

*
to the terrain or any mesh surface you click on, trapping most of the light under the terrain. Use the

**
Move
**

gizmo to move it

*
up
*

into the air.

[Image: /docs/static/attachments/44967782]

*
Adding a point light component to the level
*

##
Setting Core Light Properties

The next thing you're usually going to want to change is the

*
brightness

*
of the light. Under typical use cases, this is best accomplished by using the

**
Color ->
**

**
Diffuse Multiplier
**
property. The default is

**
1
**
; the desired value will depend on the distance between your light component and the objects and/or terrain you wish to illuminate.

You can also control the brightness of specular highlights independently using
**
Color -> Specular Multiplier
**
. For example, project a light onto a sphere so you can see the specular reflection of the light source on the ball. Set

**
Specular Multiplier
**

to

**
0
**

and the highlight

**
disappears
**

completely. Increase it and the highlight brightens and enlarges. However, we recommend leaving this parameter at the

*
default

*
value of

**
1
**

to produce

*
physically accurate
*

specular reflections, and using Diffuse Multiplier to control brightness.

The

**
Active
**

property simply turns your light component on and off; this is especially useful to control through visual scripting or code during game play in response to game states, light switches, triggers, etc.

**
Color
**

**
-> Color
**

is simply the color of the light.

##
Enabling Shadows

By default, light components do

*
not

*
cast shadows; you can enable them by setting the

**
Shadows -> Minimum Shadow Graphics
**

setting to something

*
other than
*

**
None
**
. Remember that this it not a quality setting, but determines within which

*
system shadow spec
*

an occluding entity will cast a shadow. Individual objects must have shadows enabled and an equal or lower Minimum Shadow Graphics setting to a light in order to cast a shadow from that light. Casting shadows is computationally expensive, so it will always be necessary to use shadow-casting lights selectively.

It's important to understand that it's much more expensive to ask a point light to cast shadows than a projector light - six times as expensive because it radiates in all directions. Even if a projector light's angle is set to the maximum of 180°, it will still be one sixth as computationally expensive as a point light. While you might think that you could simply place a point light against a surface so it can only radiate over a 180° angle, the point light doesn't know about the existence of that surface, and continues to project over a 360° angle of dispersion and assumes that any entities in its path will need to calculate shadows from its beam (at least for entities for which shadows have been enabled).

##
Controlling Falloff

**
Range
**

is the maximum distance (in meters) that the light can reach. To mimic light in the real world, light "falls off" (diminishes in brightness)

*
exponentially
*
 with the distance from the light source (where Brightness = 1/Distance
2
). However, there are two other factors that will affect this:

-
Falloff only begins

*
outside

*
the radius of the virtual "light bulb," which is set by the

**
Options -> Attenuation Bulb Size
**

parameter. Again, this is a distance in meters that represents the

*
radius

*
of the "bulb." Within that radius, the intensity of the light is

*
100%
*
. The default radius is 0.1m, which is suitable for most virtual "light bulbs."

-
To avoid the problem that light in the real world never actually reaches zero (and to avoid wasting resources computing infinitely small, invisible changes in brightness), CRYENGINE lights fall off according to the conventional formula -

*
until
*

they reach

**
80%
**

of their Radius. Starting at 80%, they begin to fall off

*
linearly
*
until they are forced to
*
zero
*

brightness at 100% of the Range.

##
Understanding Attenuation Bulb Size

The Options >
**
Attenuation Bulb Size
**
 property sets the radius within which its brightness will be
**
100%
**
 (as set by the Diffuse Multiplier). In other words, falloff does not begin until
*
outside
*
 this radius.

*
Changing the Attenuation Bulb Size. The brightness within the 8m Attenuation Bulb Size is completely uniform, followed by rapid falloff from 8m to the 10m limit of the light set by the radius property.
*

[Image: /docs/static/attachments/44967783]
[Image: /docs/static/attachments/44967781]

*
Changing the light color and intensity. You can also see the falloff in intensity within the 10m radius
*

##
Animating Light Color and Brightness

In addition to controlling light color, brightness and other parameters through game code and visual scripting, the brightness and color of light components can also be varied over time using the Style >
**
Animations
**
 property. Many pre-programmed animations are supplied, including various speeds of pulsing, flickering, varying color. Some of these mimic flickering firelight, for example. The "Speed" attribute will change the playback speed of the animation. For example, light styles #36 and 39 work well to simulate flickering fire; 36 varies the brightness of the light to a greater degree.

If you want to set up custom animations, you can either animate their properties using
[/docs/static/engines/cryengine-5/categories/23756816/pages/35849263](
Track View
)
, or extract and edit the
**
Shaders\
HWScripts\CryFX\Light
.cfx
**
 shader from the
**
Engine\shaders.pak
**
 file into an
**
engine\shaders.pak\Shaders\HWScripts\CryFX
**
 folder in your project folder
.

You can get more information on shaders in the technical documentation
[/docs/static/engines/cryengine-5/categories/23756813/pages/23306637](
here
)
. You can also view a video tutorial on modifying shaders on our YouTube channel
[https://www.youtube.com/watch?v=FuRhCPQar0w](
here
)
.

##
Setting Up an Area Light

As of CRYENGINE 5.6, point lights can function as
**
area lights
**
 - light emanating from a large, flat surface. These can be either rectangular or ellipsoidal. This mimics what happens when a real-world light source is either bounced off of a large white surface or projected through a large sheet of translucent white material. In either case, the
*
entire surface
*
effectively becomes the light source.

In real life, beams of light passing through or bounced from a large surface are also
*
scattered
*
 in many directions, producing shadows that are each in slightly different locations. Together, these many shadows appear as a
**
soft-edged
**
 shadow. However, area lights in the engine do
**
not
**
 produce soft shadows. In fact,
**
shadows cannot be used with area lights at all
**
. This is consistent with the common use of soft lights as fill lights that should not cast a second shadow in real-world photographic or cinematographic lighting. They supplement a main light source but still feel "invisible" or directionless. Despite this, area lights have many practical uses to supplement lighting and produce beautiful, realistic reflections as if from a large source.

To enable a point light as an area light, scroll to the
**
Shape
**
 properties and change the Shape property to either
**
Rectangle
**
 or
**
Disk
**
. Set the desired width and height of your area light up to a maximum of 10m. If helpers are enabled, you'll see the area light represented by a white outline around your point light. Remember that you
**
must
**
  set Shadows > Minimum Shadow Graphics to
**
None
**
 in order to change the component from a point light to an area light.

However, if you move your area light close to a surface with the default Attenuation Bulb Size setting of .1 and look closely, you'll notice that the light is still emanating and falling off exponentially from the center point of the point light component. In other words, it is
**
not even across the entire width and height of the area light
**
 (a 5x5m rectangle in this case), as seen in the image below. It is not realistic if used this way.

[Image: /docs/static/attachments/44967851]

*
Incorrect
 setup for an Area Light with Attenuation Bulb Size not creating correct evenness across the entire area. Note the large reflection of the entire area light in the objects
*

In order to make an area light behave correctly and have even luminosity across its entire surface, the Attenuation Bulb Size must be equal to (or greater than) the widest dimension of the area light (width or height). The example below illustrate this - the light is completely even across the entire 5x5m area light rectangle shape because Attenuation Bulb Size has been changed to 5m.

[Image: /docs/static/attachments/44967852]

*
Correct setup for an Area Light, with Attenuation Bulb Size matching the Shape size
*

Note that like projector lights, you can also choose to project a texture with an area light to shape its look further (
**
Shape
**
 >
**
Texture
**
). In the example below, we've assigned a texture from the GameSDK assets (textures/lights/scatter.dds), which looks like this:

[Image: /docs/static/attachments/44967845]

The texture provides some organic imperfections to break up the even wash of light from a light with no texture. You'll notice that the shiny metal sphere reflects the circular texture, even though it's projected through a rectangular area light shape. You can see the result below. For information on creating your own projection textures, see the
[/docs/static/engines/cryengine-5/categories/23756816/pages/44966009](
Tutorial - Projector Light Component
)
 page.

(Note that in the image below, the specular highlights on the sphere come from the blue backlight and the moon hanging above the scene out of view.)

[Image: /docs/static/attachments/44967844]

##
Related Topics

-
[/docs/static/engines/cryengine-5/categories/23756816/pages/44966009](
Tutorial - Projector Light Component
)

-
[/docs/static/engines/cryengine-5/categories/23756816/pages/26215326](
Volumetric Fog
)

-
[/docs/static/engines/cryengine-5/categories/23756816/pages/36869891](
Clip Volumes
)

-
[/docs/static/engines/cryengine-5/categories/23756816/pages/36869910](
Vis Areas
)

-
[/docs/static/engines/cryengine-5/categories/23756816/pages/36868680](
Optical Flare System
)

-
[/docs/static/engines/cryengine-5/categories/23756816/pages/36869088](
Lens Flare Editor
)

-
[/docs/static/engines/cryengine-5/categories/23756816/pages/25535599](
Global Illumination (SVOGI)
)

-
[/docs/static/engines/cryengine-3/categories/1114113/pages/19380385](
Shadows
)

-
[/docs/static/engines/cryengine-3/categories/1114113/pages/1310742](
CryTif Plug-In
)
[#introduction](
Introduction
)
[#creating-the-point-light](
Creating the Point Light
)
[#setting-core-light-properties](
Setting Core Light Properties
)
[#enabling-shadows](
Enabling Shadows
)
[#controlling-falloff](
Controlling Falloff
)
[#understanding-attenuation-bulb-size](
Understanding Attenuation Bulb Size
)
[#animating-light-color-and-brightness](
Animating Light Color and Brightness
)
[#setting-up-an-area-light](
Setting Up an Area Light
)
[#related-topics](
Related Topics
)
