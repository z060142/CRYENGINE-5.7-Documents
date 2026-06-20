# Tutorial - Environment Editor Part 1

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/56658335
- Page ID: 56658335
- Breadcrumb: Tutorials > Graphics > Environment Tutorials > Environment Editor Tutorials > Tutorial - Environment Editor Part 1
- Parent: Environment Editor Tutorials

## Content

##
Overview

In this tutorial, we'll learn how the major elements of sunlight-based lighting and the Environment Editor work by creating a variety of naturalistic and other-worldly looks. We'll be using the
[Environment Editor](../../../../Editor%20Tools/Environment%20Editor.md)
 (
**
Tools → Environment Editor
**
) and natural light (sunlight) throughout this tutorial. The Environment Editor and environment lighting is a big topic, so this tutorial series is lengthy in order to be thorough.

We suggest that you consult the table of contents to find specific topics, although if you are new to CRYENGINE, it would be beneficial to work through this information in the order presented, as it teaches individual concepts before examining use cases that involve every setting. The best way to learn these concepts is to read and test the settings in your own levels rather than trying to digest all of this material in one sitting. We also recommend viewing the accompanying video tutorials.

##
Environment Editor Design

On first viewing, it may seem that the Environment Editor presents an overwhelming number of parameters to model what might look simple to the eye: the color of the sky, the position and intensity of the sun and moon, the shape of the clouds, etc. In fact, the Environment Editor is built on a mathematical model for simulating what you see on planet Earth; as such, it is modeled on real-world physics, but simplified to the point where a believable simulation can be achieved in real time. In other words, while the controls are more complex than picking swatches for "sky color", "sun color", etc., there are actually a minimum number of parameters to allow you to accurately simulate Earth-style lighting without unnecessary complexity while also providing tools flexible enough to empower you to create looks unlike anything seen on planet Earth.

When designing your environment and lighting, start from the large-scale, general settings, and work your way toward the smaller, more specific areas.

##
Dynamic vs. Static Time of Day and Curve Editor

Before creating an environment preset, it's essential to understand the role of the Curve Editor. The Curve Editor is used for
**
keyframing
**
 changes in Environment Editor
**
Variables
**
when
*
dynamic
*
 time of day is desired. However, even if you wish to create a
**
static
**
 time of day, you will still be setting keyframes, because any change to a variable will set a keyframe for it
**
at the current time
**
. In other words, all variable values are associated with a time of day.

Since
**
specular reflections
**
 rely on pre-generated, static cube maps, achieving dynamic time of day involves greater complexity and scripting to blend between cube maps. For that reason, you may choose not to use dynamic time of day in your level. In that case, you can drag the time ruler in the Curve Editor to any position that gives you a look similar to what you plan to create, or simply leave it at the default 12:00 noon, and its panel closed and ignored thereafter. (For example, Hunt Showdown uses 12:00 noon as the time of day for all of its environment presets, which cover a wide range of day and night settings. This also has the added convenience of never having to worry about searching for the time of day where you set all your keyframes, as 12:00 is the default time for new presets.)

To learn how to use dynamic time of day, see
[Creating a 24 Hour Cycle](../../Lighting%20Tutorials/Tutorial%20-%20Lighting%20-%20Creating%20a%2024%20hour%20cycle.md)
.

However, when you are just starting to learn to use the Environment Editor, it can be quite useful to scroll along the time ruler in
**
Curve Editor
**
 and click on
**
Variable
**
 names to observe how the values at each keyframe create various looks: day, dawn, sunrise, midday, dusk, night, etc. (You'll need to zoom in and out to find the spline path between keyframes in the Curve Editor.)

Keep in mind that it’s not changing time of day that alters the look of the lighting and environment; it’s the fact that Variable values have been set at various points on the timeline, creating keyframes on the Curve Editor's. In other words, you can create a dark clear night with bright stars even at noon, or a bright sunny day at midnight. It's simply a matter of setting the parameters to the desired values.

So while you can certainly scroll the Curve Editor to a particular time of day and use the values at the time as the basis to create a similar look, you can also simply ignore the Curve Editor and create your look at
**
any
**
 time of day. Closing the curve editor as a first step is a good way to avoid the mistake of changing the time of day once you've begun setting up your values, since you'll end up with Variables keyframed at different times of day instead of at the same time.

We recommend
**
typing
**
 a time value in the Current Time box (try
**
Ctrl A
**
 to select all four digits) on which your team wishes to standardize before you close the Curve Editor and start setting keyframes by changing Variable values. Dragging on the time ruler sets time of day using a much higher degree of precision than hours and minutes (five decimal places), requiring you to zoom all the way in to see the exact position of a keyframe.

![Image](https://www.cryengine.com/docs/static/attachments/56660080)

Typing a current time of day simplifies this: for example, typing "13:00" will set time of day to exactly 13:00, even though the additional precision isn't shown in the Start, Current, and End time of day fields.

The rest of this tutorial will focus on creating static presets
**
without
**
 dynamic time of day.

##
Creating and Assigning a New Environment Preset

The first step after creating a new level is to assign an environment preset to it.

Let's create and assign our first example: a sunny afternoon:

-
In the
**
Environment Editor's Asset Browser
**
 panel, navigate to
*
libs\EnvironmentPresets
*
, right- click in an empty area and choose
**
New Asset → Environment
**
. Call it "sunny_afternoon" or whatever you'd like to create. Click
**
OK
**
. The preset has been created.

-
Open
**
Tools
**
 →
**
Level Editor
**
 →
**
Level Settings
**
 →
**
Environment Presets
**
. You'll see that an environment preset called default.env is assigned to every new level by default. This is bundled in the engine assets and cannot be viewed or changed. Let's unassign it: click on the
**
1
**
 button next to
**
Presets
**
 and choose
**
Remove All
**
.

-
To assign your environment preset to the level, simply drag it from the asset browser into the perspective viewport. You can confirm that the environment preset has been assigned by inspecting
**
Tools → Level Editor → Level Settings
**
.

-
**
Save
**
 your level.

-
Click your environment preset in the Environment Editor's Asset Browser to
*
activate
*
your new "sunny_afternoon" preset and load its settings to be further modified.
We'll customize this preset, and its current values will be reflected live in your level. Keep in mind that like many other CRYENGINE tools, you need to press
**
Ctrl + S
**
 while the Environment Editor is the
**
active window
**
 to save changes to the active environment preset. This does
**
not
**
 save the level; that must be done by using
**
Ctrl + S
**
 or
**
File → Save
**
 with a
*
viewport
*
 as the active window.

If your level is empty, populate it with some quick geometry or vegetation or use the Designer Tool to quickly whitebox something approximating your intended design. This is also a good time to customize (sculpt or import, then paint) your heightmap using the Terrain Editor. Until you have some sense of what your level looks like, what kind of materials you're using, and have some objects to cast shadows, it will be difficult to create the appropriate lighting.

**
TIP
**
: Before you do anything else, here are two recommended settings to start customizing any environment preset:

-
**
Variables → HDR → Color balance
**
 is set to a yellow tint by default. Desaturating the color completely is advisable, as it is the last step in the imaging process that will affect every other environment setting. You can fine-tune the color palette of a scene much more precisely using
[color grading](../../../../Post-processing/Tutorial%20-%20Color%20Grading.md)
.

-
The
**
HDR eye adaptation
**
 by default is set to be compatible with versions of the engine before CRYENGINE 5. If you're using CRYENGINE 5 or later, switch to the new and improved mode by typing
**
r_HDREyeAdaptationMode 1
**
 in the Console (and setting it permanently in your autoexec.cfg or other
[config file](../../../../System%20Utilities/System%20Utilities%20Overview/Console%20Variables%20%26%20Config%20Files.md)
).

##
Key Lighting Parameters: Sun, Sky, Fog

There are three key factors that have a profound effect on lighting (in particular, lighting using the sun):

-
Sun

-
Sky/ambient light

-
Fog
Note that while we highly recommend that you use volumetric fog over the old, simple fog effect for reasons that will be detailed here, we will begin by only using the old fog effect for purposes of demonstration. It's useful to understand both systems and see how they compare. It's also possible that you may decide to use the old fog effect in more simple game designs, or for
performance reasons.

##
Environmental Lighting: A Quick Tour

Before we take apart what constitutes the environment piece by piece, let's take a quick look at what controls daylight in the Environment Editor. We'll just look at the three most significant factors: sun, sky, and fog:

Make sure volumetric fog is disabled (e_VolumetricFog 0 in console)

Move the camera away from the terrain horizontally and above it.

If your terrain is flat, generate some terrain height variation using the Terrain Editor:
**
File → Generate Terrain
**
: accept the defaults to generate some mountains. Your camera may end up under the newly elevated terrain; in that case, simply move it up.

Let's enable shadows from the terrain:
**
Level Settings → Env State → Sun Shadows From Terrain
**

Now let's move the sun lower in the sky so you can see the terrain texture better. In Environment Editor under
**
Constants
**
 →
**
Sun
**
,
disable

**
Sun Linked to TOD
**
 and change the
**
longitude
**
 to
**
25
**
 or less, as you like. Now the level looks something like this:

![Image](https://www.cryengine.com/docs/static/attachments/56659268)

Now let's switch off pieces one by one to see how they contribute. First, let's turn off the sun: Set
**
Variables
**
 →
**
Sun
**
 →
**
Sun intensity (lux)
**
 to
**
0
**
. Your level should look like this:

![Image](https://www.cryengine.com/docs/static/attachments/56659279)

You may be surprised that the difference is such a subtle change in the light on the terrain. The world hasn't gone dark, you can still see the sun's orb in the sky, and the sky (which is just the Earth's atmosphere scattering sunlight) is still just as bright. Unlike in nature, you have separate control over each of these elements in CRYENGINE.

Let's turn the skylight almost off: s
et
**
Variables
**
 →
**
Sky Light
**
→
**
Sun intensity multiplier
**
 to
**
.1
**
. The sky will go very dark, but you'll still see a small sun orb in the sky. Your level should look like this:

![Image](https://www.cryengine.com/docs/static/attachments/56659281)

Change the
**
Sun intensity multiplier
**
 to
**
0
**
, and both the sky and
the sun orb
will go completely black.
You've effectively prevented Earth's atmosphere from trapping any sunlight, so the sky looks black, yet the terrain and ocean are not. Now we need to clarify the key role that fog plays:

Move your camera down to the terrain. As you look around, you'll verify that the terrain is completely black, but if you look up, you may be surprised to see that the world appears to have a blue sky above you, albeit a bit on the dark side. Change the
**
Variables
**
 →
**
Fog
**
→
**
Color (top) multiplier
**
 to 4, and that blue "sky" will look almost normal.

While this is not a recommended way to create the illusion of sky, it's essential to understand that the player views what's above through the fog layer that is normally set to be most dense at the terrain height, and that the color of the fog in this case hides the fact that the sky above it is actually pitch black. Even if you are using a more typical value for
**
Variables
**
 →
**
Sky Light
**
→
**
Sun intensity multiplier
**
, the
**
Variables
**
 →
**
Fog
**
→
**
Color (top) multiplier
**
variable will have a profound effect on what the player perceives to be the sky.

Move the camera back above the terrain so you can see the black sky as well as the terrain with the fog floating on it.
The fog seems to be trapping or emitting light, some of it blue, some of it golden, but where are those lights coming from?

There are actually
**
six
**
 sources of light in this fog effect!

-
**
Fog
**
 →
**
Color (radial)
**
: t
he golden light is coming from this color, which mimics light scattered
*
around
*
 the sun. This
color swatch determines the color and brightness of the light scattered from the sun through the fog.

-
**
Fog → Color (radial) multiplier
**
 determines how intensely it's applied. (1 = 100%, although you can multiply it all the way up to 16, which is 1600% of its swatch color).

-
Similar to this, the bluish light is set over a vertical range by four settings:
**
Fog
**
 →
**
Color (bottom)
**
 and
**
Fog
**
 →
**
Color (bottom) multiplier
**
 determine the color and intensity at the bottom of the range, creating a fog gradient to the
**
Fog
**
 →
**
Color (top)
**
 and
**
Fog
**
 →
**
Color (top) multiplier
**
 values at the top of the fog's vertical range.
Let's remove the golden glow: set
**
Fog → Color (radial) multiplier
**
 to
**
0
**
. (Alternatively, you could also set  →
**
Color (radial)
**
 to pure black to accomplish the same thing.)

If you look at the Fog settings labeled bottom and top, you'll see that by default, the fog effect extends from 0 to 400m high, fading from 100% to .0001% density from bottom to top.
Another interesting note: the latitude and longitude of Constants → Sun will still control the
**
direction
**
 of the light inside the fog - even if sunlight intensity has been reduced to zero!

In the image below, the fog has been placed
**
above
**
 the terrain, and the density gradient has been flipped from its usual values, fading from 100% at the
*
top
*
 to .0001 at the
*
bottom
*
. The sun intensity (lux) is 0. As you can see, while the fog glows brightly, it doesn't actually illuminate the terrain as a light source would. But when you view entities or terrain
*
through
*
 translucent fog, its luminance affects the appearance of the entities and terrain within it without actually
*
illuminating
*
 their details. More specifically, the fog makes everything look increasingly fog-colored as you view it from farther away. If the fog was purple, everything would eventually look purple if there was enough fog between the camera and the entities or terrain.

![Image](https://www.cryengine.com/docs/static/attachments/56659291)

Let's turn off the fog at the top of its range: set
**
Fog
**
 →
**
Density (bottom)
**
 to
**
Density (top)
**
. The tops of your mountains will be a bit darker:

![Image](https://www.cryengine.com/docs/static/attachments/56659284)

Finally, if you eliminate the fog at the top of the range by setting
**
Fog → Color (bottom)
**
to
**
black
**
, you'll finally see an entirely dark world. While you're unlikely to use such settings, now you know the main settings and can restore some sun intensity and fog to achieve a night look for example. In the next part of this tutorial, we'll go into greater depth about settings, and learn how to create some realistic night and day looks.

Now that you've had a quick tour of the basic components that comprise the light on a level, let's look at how they work in detail, how best to use them and how to build on them. You can either undo or discard all of the changes to your environment preset (right-click on it in the
**
Environment Editor's Asset Browser
**
 and choose
**
Discard Changes
**
) or make a new one and assign to your level.

##
Sun in Depth

The first concept you need to understand about the sun is that the light
*
produced
*
 by the sun (seen illuminating your level and scattered in the atmosphere) is controlled separately from the visible appearance of the sun
*
orb
*
 itself. While these are always synchronous in the real world, they are separately controlled in the engine. This allows you the flexibility to do practical things, like hiding the sun orb when using a cloudy, overcast sky box texture, as well as to create fantastical game worlds with suns and skies unlike anything familiar to Earthlings. But it also means that in order to create realistic Earth-like conditions, there are numerous parameters you'll need to set.

##
Sun Position

When you create a new environment preset, the sun is positioned by default directly overhead (90° longitude), effectively as if you were standing at the Earth's equator at 12:00 noon. You'll notice that shadows are directly beneath objects, making it difficult to gauge their forms. One thing you might want to do to make it easier to see as you're working on your level (even if you're not ready to finalize your lighting) is simply go to
**
Constants → Sun
**
 , disable
**
Sun Linked to TOD
**
 (since we want to manually control sun position and not depend on time of day), and set
**
Longitude
**
 to a value smaller than 90 to move the sun lower in the sky. This will lengthen your shadows and make it easier to see your meshes and terrain.

##
Sun Color and Intensity

These parameters, found under
**
Variables
**
 →
**
Sun
**
, control the color and intensity of the
**
light
**
 produced by the sun (that which you see illuminating your terrain), not the appearance of the
**
sun orb
**
 itself. Brightness is expressed using the
[lux](https://en.wikipedia.org/wiki/Lux)
 scale of illuminance. The default brightness is much brighter than actual sunlight on planet Earth, and won't give you physically accurate luminance within our recommended PBS/PBR (Physically Based Shading/Rendering) workflow. See
[this tutorial](../../../../Graphics%20%26%20Rendering/Lighting/Lighting%20Overview/Lighting%20Levels%20Using%20PBS.md)
 for detailed information about calculating realistic light levels.

Also, while you are free to set the color of the sunlight as you like, keep in mind that if realism is your goal, its color should be affected relative to the position of the sun in the sky with respect to the camera. Why? Because light rays pass in a path between sun and camera (or your eyes), and the closer that path is to Earth's surface, the more dense the
**
atmosphere
**
 and the more strongly reddish light is scattered (producing the reddening you see at sunrise and sunset). This is quite different from the blue scattering you see in midday. So it's advisable to finalize the sun's position
**
before
**
 you set its color.

To get started, decide whether you want to create a day or a night look and adjust the
**
position
**
 and
**
intensity
**
 of the sun accordingly. Sun intensity is just one aspect, so for now, just dial in an approximate value, and later you'll fine tune the look using light components, environment probes, and possibly SVOGI. You'll also need to tweak the brightness of the sky and, for night looks, the visibility of the moon and stars.

We'll come back to set the appearance of the sun
*
orb
*
 after we've set the appearance of the sky, as the engine provides control over its appearance independent of the light it produces.

##
Sky in Depth

Although a simplified interface for environmental lighting could theoretically have been provided, for example a single color picker for "sky color," the controls presented to you are based on the actual science behind the sky you ultimately see. While this means you have to deal with some of the complexities behind the science, it has the advantage of allowing you to create very realistic (as well as pure fantasy) skies.

##
Earth's Sky, Defined

When it comes to what you perceive as the sky, it helps to keep a few things in mind:

-
The "sky" that you can see is essentially a
**
hemisphere
**
 (presupposing that you have an unobstructed view) which is not a physical entity or a solid surface; it's the light that is trapped and scattered by the Earth's atmosphere. (about 23% of the sunlight that reaches the Earth) The particles in the atmosphere become illuminated, producing a vast range of colors, depending on the composition of the atmosphere and the position of the sun relative to your vantage point.

-
During the middle of the day, the sky looks
**
blue
**
 because Earth's atmosphere scatters shorter blue wavelengths more than longer wavelengths. This is primarily caused by what's known as
**
Rayleigh scattering
**
, caused mostly by smaller particles in the atmosphere. This is also why the sun appears slightly yellow from Earth, as it's the opposite of the blue that's been subtracted from the white light emitted by the sun. (It's interesting to note that if you had a chance to take a trip into outer space beyond Earth's atmosphere, you'd see that the sun appears white, not yellow.)

-
Around sunrise and sunset, the sun's rays pass through the dense atmosphere closest to the Earth's surface to reach the viewer. This results in even greater scattering, but as most of the blue and green light is scattered away before it reaches the viewer, what you end up seeing are the characteristic warm colors of sunrise and sunset.

-
**
Mie scattering
**
is triggered by larger particles in the air, aerosols like dust, and pollution. Unlike Rayleigh scattering, it tends to scatter all wavelengths of light equally. So instead of producing a color shift, Mie scattering produces a slightly grey sky on a hazy day as well as producing a large white halo around the sun.

-
On the other side of Earth's atmosphere is always the
**
blackness
**
 of outer space and the planets, stars, and at night, physical entities visible from Earth.

-
The higher your altitude above Earth's surface, the
**
thinner
**
 the atmosphere you're seeing through when you look up, thus the closer you're getting to seeing the blackness of space and the true, unchanging color of the sun. In other words, the vantage point of the player will affect how the sky (and sun) look.

-
The sky is not a uniform color or tone as you look around the visible hemisphere, because light trapped by scattering varies as you look towards or away from the sun or moon.

-
As you look down towards the horizon line, the sky color changes because the atmosphere is
**
thickest
**
 closest to the Earth's surface, as well as containing a different composition (most of the water vapor, clouds, and dust, for example). This change in atmospheric composition and density forms a gradient from the horizon line to the point directly overhead. It also changes colors as you look around towards and away from the sun or moon.

-
Earth's atmosphere actually extends as high as 10,000 km from the surface, but 99% of it is within 16 km (10 miles) of the surface in the first two layers (the troposphere and stratosphere). This sunlight trapped here comprises what we see as skylight, and in addition to reflected sunlight comprises ambient light on Earth.
Hopefully this helps explain why there isn't simply a "sky color" button in the Environment Editor. The sky is much more complex than a single color!

##
Elements of the CRYENGINE Sky

The Environment Editor uses terms consistent with the science behind the way Earth's sky looks, while hiding additional complexities that wouldn't be worth setting (like the composition of the five different layers that make up the atmosphere, for example). When you master these concepts, then you'll be able to get any look that you're seeking, whether naturalistic or complete fantasy.

It may be useful to think of what you perceive as the "sky" in CRYENGINE as
**
layers
**
. From
**
back to front
**
, these are:

-
**
Outer space
**
 - the darkness of empty space, the stars, and the moon texture. Everything here is controlled through the
**
Variables
**
 →
**
Night Sky
**
 values.

-
Skylight - the light trapped in Earth's atmosphere. This is controlled by Variables → Sky Light. Unlike Earth, however, this is infinite rather than giving way to the blackness of space. Whatever value you set here is what you'll see no matter how high the camera moves up, although the density of global fog will taper off as you move up and affect your perception of what appears to be "sky.

-
A
**
SkyBox
**
 texture, if used. At an opacity of 1 (100%), this completely covers the sky color, or it can remain translucent.

-
**
Sun rays
**
. Even if a full opacity sky box covers your sun orb, its scattered rays are still visible in front of it. (Variables → Sun Rays Effect)

-
**
Volumetric clouds
**
, if enabled (r_VolumetricClouds 1). The altitude of volumetric clouds is completely up to you, so they could be floating above or in the midst of your vertical fog range.

-
**
Fog
**
 (global): set by Variables → Fog or Variables → Volumetric Fog.

-
**
Fog volumes
**
 (local volumetric fog components), if enabled (e_VolumetricFog 1). While it's probably not that useful to think of local fog volumes, like mist on a lake, as part of the sky, a player on the terrain is always viewing the sky through any fog volumes (since they are all placed above the terrain), so it could be argued that those (at least those on the taller side) affect the player's perception of the "sky."
Of these, fog typically plays the biggest part in creating the player's perception of sky, as we'll see.

##
Key Sky Settings

The sky is effectively generated by these parameters. Keep in mind that the height of the sun above the horizon has a strong effect as well.

-
**
Variables
**
 →
**
Sky Light → Sun intensity
**
: despite its name, this controls not only the sun orb, but also the
**
brightness
**
 and
**
color
**
 of the
**
sky
**
. That is
**
independent
**
of the color and brightness set by the Variables → Sun settings, so there's nothing to stop you from creating unnatural but possibly interesting worlds (see examples below). A key concept to understand is that, as you saw in our quick tour, even if you turn this to 0 to blacken the sky, players looking up through any fog will see the fog, not the sky. The fog blocks the player's view of the actual sky, effectively becoming what the players
*
see
*
 as sky.

-
**
Variables → Sky Light → Sun intensity multiplier
**
: not how strong the sunlight is, but effectively how strongly
**
Sky Light
**
 →
**
Sun intensity
**
 sets the sky color and brightness. Setting this to 0 makes the sky
**
black
**
, no matter what
**
Sky Light → Sun intensity
**
 is set to. But it also contributes to the visibility of the sun orb itself. 0 = invisible sun. .0001 = a very small but visible sun (provided Sky Light → Sun intensity is not black) and near-black sky.

-
**
Variables
**
 →
**
Rayleigh scattering
**
: By setting atmospheric density, this effectively determines the
**
color
**
 of the sky by controlling which wavelengths of light are scattered in the atmosphere. (Keep in mind that moonlight is just reflected sunlight.)
At a default value of
**
2
**
, you'll see realistic Earth colors: blue skies far from the horizon, warm red-orange-yellow close to the horizon.
**
Higher
**
 values make the atmosphere more
**
dense
**
, shifting the sky toward
**
red and yellow
**
. A higher density also means you'll need to raise the Sky Light → Sun intensity multiplier to allow more light to penetrate and illuminate the sky.
**
Smaller
**
 values make the atmosphere
**
less dense
**
, allowing more light to pass and shifting the sky towards
**
blue
**
. Small changes will make a big difference here, and values above around 40-50 will produce an atmosphere so dense that little light will pass through it. In most environments, you can simply leave this at the default value of 2. However, if you're trying to recreate the atmosphere of a non-Earth world, changing these values to affect atmospheric density (and thus the colors that are scattered) while compensating for that density by tweaking the Sun intensity multiplier will produce a wide variety of colors, including bands of color.

-
**
Variables
**
 →
**
Mie scattering
**
: this controls the effects of scattering with larger particles, closer to the size of the wavelength of visible light. Visually, this won't make nearly as much difference as adjusting Rayleigh scattering,
so we suggest leaving it at the default value.
The most simple way to set your sky color is to keep the default values in this section and just vary the sun's position in the sky to get realistic changes in sky color. However, you can create many looks by playing with these values.

##
Sky Light Examples

This example demonstrates how you can independently set the sky and the sun colors:
**
Sun
**
 →
**
Sun color
**
 is set to
**
orange
**
, which you can see illuminating the terrain. But the
**
Sky Light
**
 →
**
Sun intensity
**
 has been set to a
**
green
**
 color that wouldn't naturally occur from this perspective (unless someone had managed to turn the atmosphere very green).

![Image](https://www.cryengine.com/docs/static/attachments/56659005)

The examples below use
**
only
**

**
skylight
**
 (Sun → Sun intensity (lux) = 0) with the Sky Light → Sun intensity set to white, and fog completely disabled.

**
Sun intensity multiplier = 200, Rayleigh scattering = 6
**

![Image](https://www.cryengine.com/docs/static/attachments/56659001)
2

**
Sun intensity multiplier = 200, Rayleigh scattering = 20
**

![Image](https://www.cryengine.com/docs/static/attachments/56659002)

**
Sun intensity multiplier = 1000, Rayleigh scattering = 310
**

![Image](https://www.cryengine.com/docs/static/attachments/56659003)

**
Sun intensity multiplier = 8, Rayleigh scattering = 1
**

![Image](https://www.cryengine.com/docs/static/attachments/56659004)

##
The Sky Box Option

There is one very simple way to
**
bypass
**
 all of the variables that affect the sky: just use a
[SkyBox](../Tutorial%20-%20Adding%20a%20Sky%20Box%20to%20Your%20Level.md)
 - a high resolution, seamless, static photograph of a real sky hemisphere. Assign a skybox material to Constants → Skybox and set the SkyBox → Opacity to 1 (100%), and it will
**
completely cover the actual sky
**
. The light the sun produces, the sun orb, any sun rays, volumetric clouds, and fog are still visible in front of the sky box. Be sure to match the CRYENGINE sun position, size, color, and brightness to the sun in the SkyBox texture.

Keep in mind that a SkyBox texture is a static image, so if it has clouds in it, they're not going to move (although you can animate the
**
Variables → Skybox →
**

**
Rotation
**
 parameter to rotate your texture around the horizon and create the illusion of moving clouds). You can also enable volumetric clouds that float in front of it, affected by the wind.

You also have the option of making part of your SkyBox texture transparent using the
**
SkyBox → Filter
**
 property, as well as setting the opacity of the entire texture. This allows you to blend your SkyBox texture with the color of the sky.

For detailed information on how to set up a sky box texture, see
[this](../Tutorial%20-%20Adding%20a%20Sky%20Box%20to%20Your%20Level.md)
 tutorial.

Don’t leave a sky box material assigned to your environment preset if you’re not using it, because even with the opacity set to 0, it will still hide any sky settings you make under Variables → Sky Light.
In the forthcoming additional episodes of this tutorial series, we'll go through volumetric fog, SVOGI, ambient light, HDR, and real-world use cases in detail.

##
Video Tutorial

This tutorial is also available in video form on our YouTube channel:

[Embed: https://www.youtube.com/watch?v=tztIyT7MNP0]
[Environment Editor Design](#environment-editor-design)
[Dynamic vs. Static Time of Day and Curve Editor](#dynamic-vs-static-time-of-day-and-curve-editor)
[Creating and Assigning a New Environment Preset](#creating-and-assigning-a-new-environment-preset)
[Key Lighting Parameters: Sun, Sky, Fog](#key-lighting-parameters-sun-sky-fog)
[Environmental Lighting: A Quick Tour](#environmental-lighting-a-quick-tour)
[Sun in Depth](#sun-in-depth)
[Sky in Depth](#sky-in-depth)
[Video Tutorial](#video-tutorial)
