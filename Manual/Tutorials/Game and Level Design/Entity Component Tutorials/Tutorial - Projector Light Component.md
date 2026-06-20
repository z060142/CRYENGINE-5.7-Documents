# Tutorial - Projector Light Component

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/44966009
- Page ID: 44966009
- Breadcrumb: Tutorials > Game and Level Design > Entity Component Tutorials > Tutorial - Projector Light Component
- Parent: Entity Component Tutorials

## Content

This tutorial introduces the use of the Projector Light component and its most often used settings. The Projector Light component emits light in a specific direction. The radius of its beam, brightness, color, the animation of its brightness and color, and projected textures are just some of the many properties that can be controlled. Common use cases include spotlights, flashlights, vehicle headlights, architectural light fixtures from desk lamps to ceiling lights, and much more. Whereas the Point Light component can be compared to a naked light bulb, Projector Lights are similar to real-world light
*
fixtures
*
 - light bulbs mounted in some kind of fixture that provides full control over all of their visual characteristics.

##
Before You Start

Before attempting this tutorial we recommend that you read the documentation on the
[Entity Components (From Engine Version 5.6)](../../../Entities%20and%20Tools/Entity%20Components/Entity%20Components%20(From%20Engine%20Version%205.6).md)
. Doing so will give you a much better understanding of the concepts behind CRYENGINE's Entity Components. You'll also find a reference guide here to all of the properties available to each component.

Different methods can be used to create new entities. For more information see the
[Entity Components](../../../Entities%20and%20Tools/Entity%20Components.md)
 documentation.

##
Creating the Light

Before you begin creating a light, use the Environment Editor to change the time of day to night so the sun doesn't overpower your lights. In order to see these examples, we set the time of day to 00:15. The sun intensity is 8000 and its color is set to #5ed7fb, a more saturated green-blue than the default. We've positioned the moon to come from the top right in these screenshots. You'll also notice that the moonlight casts shadows that stretch to the left from the Designer objects we've placed in the scene.

While you can
*
add
*
 a light component to an
*
existing
*
entity (such as a visible mesh representing a light bulb or fixture), they can also be added directly to a level as components independent of any entity. In this case, the light component itself is invisible to the player; only its effect is seen:

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
Projector Light
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
 mode. This has the advantage of allowing you to use the scroll wheel to
**
rotate
**
 the entity around the Z (vertical) axis and aim your light before you click to place it on the level. You may want to adjust the current camera speed in the Perspective Viewport's Camera menu to affect how fast the scroll wheel rotates the entity.

Unless you clicked on an existing entity to place your new light component onto it, the pivot of the light component will
*
snap
*
to the terrain, trapping most of the light under the terrain. Use the
**
Move
**
 gizmo to move it
*
up
*
 into the air.

##
Setting Core Light Properties

##
Transform properties

Note that when you click on a Projector Light component, a set of yellow lines show you an important property: the
*
radius of the beam
*
in degrees, which you'll find in the Properties panel under
**
Transform
**

**
-> Angle
**
. The default is a 45° angle, but you can use any value between 0 (in which case
*
no light
*
 will escape!) and 180°.

**
Helpers
**
 must be enabled to see the beam angle - try
**
Ctrl + H
**
 to toggle them on/off.
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

Once you've made your light bright enough that you can see its effect, try using the
**
Move
**
 and
**
Rotate
**
 gizmos to aim it more precisely.

TIP
When you're trying to aim a light precisely, try temporarily reducing the
**
Angle
**
 to a very small value (3-5°) and increasing the
**
Diffuse Multiplier
**
 to brighten it. (Using a hard-edge circular or square texture in the
**
Projector Options -> Projected Texture
**
 property will make its beam even more clear.) Use the
**
Move
**
 and
**
Rotate
**
 gizmos to aim it. Just don't forget to restore the
**
Angle
**
 and
**
Diffuse Multiplier
**
 to the desire values when you're done.

You can control the brightness of specular highlights independently (
**
Color -> Specular Multiplier
**
). For example, project a light onto a sphere so you can see the specular reflection of the light source on the ball. Set
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
 an occluding entity will cast a shadow.

**
Range
**
 is the maximum distance (in meters) that the light can reach. To mimic light in the real world, light diminishes in brightness
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
 of their Range distance. Starting at 80%, they begin to fall off
*
linearly
*
until they are forced to
*
zero
*
 brightness at 100% of the Range.
The screenshots below indicate how falloff is calculated and affected by the
**
Range
**
 and
**
Attenuation Bulb Size
**
 settings in a variety of use cases. All instances are set up as follows:

-
The number meshes indicate how many meters away they are from the light source in the lower left corner

-
The poles are exactly
*
1m
*
 apart, and the red poles mark every
*
10m
*

-
Shadows have been
*
disabled
*
on the Projector Light component so the light can shine through and illuminate all of the number meshes without obstruction

-
The color of the light has been made slightly
**
orange
**
 to distinguish it from the blue-green moonlight coming from the opposite direction.
In this first example, the
**
Range
**
 of the Projector Light has been set to exactly
**
100m
**
, and the
**
 Diffuse Multiplier
**
 is
**
3000
**
. You can clearly see exponentially diminishing brightness up to 80m. At that point, the falloff switches from exponential to
**
linear
**
, which you can see by the sudden, drastic drop in brightness between 80m and 90m, and then again to 0% brightness at 100m. (We've used a little bit of blue-green moonlight from behind the numbers so you can still see them, and a red light to mark the 100m point.)

![Image](https://www.cryengine.com/docs/static/attachments/44966017)

In this second example, the
**
Attenuation Bulb Size
**
 has been changed to
**
100m
**
, which means that the light is
*
100% of its brightness from 0 to 80% of the Range value
*
. (Since the change in the Attenuation Bulb Size effectively extends the full brightness of the light over an 80m radius, we've also reduced the
**
 Diffuse Multiplier
**
 to just
**
5
**
 to compensate for the added brightness.) Since the
**
Range
**
 is still
**
100m
**
, that means that the exponential part of the falloff has been completely
*
eliminated
*
. I.e., there is
*
no change in brightness from 0 to 80m
*
. Between 80 and 100m, the brightness diminishes linearly as it did in the previous example, which you can see again from the drastic change: 90m is half as bright at 0-80, and 100 is again completely dark (i.e., the orange light has fallen to 0% intensity). See
[Attenuation and Falloff](../../../Graphics%20%26%20Rendering/Lighting/Lighting%20Overview/Light%20Entity.md#LightEntity-AttenuationFalloff)
 for more information.

![Image](https://www.cryengine.com/docs/static/attachments/44966018)

##
Using Angle and Projected Textures

In this example, the light uses a 45°
**
Angle
**
 to project onto several objects and the terrain.

![Image](https://www.cryengine.com/docs/static/attachments/44966016)

Compare this to the example below, where the Angle is still 45°, but a
*
rectangular greyscale texture
*
 that's 25% as wide as it is long has been added to the
**
Projector Options -> Projected Texture
**
 property to give the beam a rectangular shape.

![Image](https://www.cryengine.com/docs/static/attachments/44966015)

You can use greyscale textures in the
**
Projector Options -> Projected Texture
**
 property to create patterns and shape the edges of a light component. Here the Angle has been set to
**
5°
**
 to spotlight only the ball.

![Image](https://www.cryengine.com/docs/static/attachments/44966014)

With a circular, hard-edge circular texture added to
**
Projector Options -> Projected Texture
**
 (GameSdk\textures\lights\generic\spot_005.dds), this 5°
**
Angle
**
 setting is much more effective as a spotlight, below.

![Image](https://www.cryengine.com/docs/static/attachments/44966013)

In this example, the Angle has been set to 24° and a texture added that imitates Venetian blinds. (You can find the Venetian blinds texture in the GameSDK
**
textures
**
 folder, and the other textures used above in
**
textures\lights\generic
**
.)

![Image](https://www.cryengine.com/docs/static/attachments/44966012)

##
Creating Your Own Projection Textures

If you want to create your own projected textures, we recommend making them 512x512 pixels, 16 bit greyscale, and exporting them as CryTif files using the
**
LightProjector
**
 preset. (Make sure you've installed the Photoshop CryTif plug-in by running Tools\CryToolsInstaller.exe.) While you can use higher resolution 1024x1024 pixel textures, you shouldn't need to in most cases; typically it will only increase memory usage without any visible benefit.

In Photoshop, create a 512x512 pixel 16-bit greyscale image. You could begin with a black background to block all light, a white background to show light everywhere, or exactly middle grey to reveal 50% of the light's intensity, then darken and lighten areas selectively.

![Image](https://www.cryengine.com/docs/static/attachments/44968219)

To add texture, paint with any black brush wherever you want to create shadows or white wherever you want to increase the intensity of the light. Black will completely block the light; white will reveal the light's full intensity. You can also try Photoshop filters to render textures. Here we've used the
**
Filters
**
 >
**
Render
**
 >
**
Clouds
**
 filter, then an 8 pixel
**
Gaussian Blur
**
.

![Image](https://www.cryengine.com/docs/static/attachments/44968220)

You can also use drag or copy and paste any image into your Photoshop document to create projected 2D images, textures, logos, etc. In this example, we've used the CRYENGINE logo as a white area within the texture, with all pixels around it black.

![Image](https://www.cryengine.com/docs/static/attachments/44968221)

Make sure that you transition to black before you reach the edges of your texture, or else you'll see a pixelated edge when projecting it with a light component, as shown below. To do so,
**
select
**
 your desired shape with any selection tool (marquee, lasso, pen, etc.), but stay well away from the edges of the canvas.

![Image](https://www.cryengine.com/docs/static/attachments/44968222)

Choose
**
Select
**
 →
**
Modify
**
 →
**
Feather...
**
 from the Photoshop menu. Enter the desire number of pixels over which you want the edge of the light to fade away.

**
Invert
**
 your selection (Ctrl-Shift-I).

**
Fill
**
 the selected area with
**
black
**
.

**
Export
**
 as
**
CryTif
**
 using the
**
LightProjector
**
 shader.

Be cautious about putting lights with projected textures too far away from surfaces, as the relatively low resolution of the textures will eventually become apparent. The example below uses a 1024 pixel circular texture placed unusually far from the terrain.

![Image](https://www.cryengine.com/docs/static/attachments/44968223)

##
Using Clip Volumes to Constrain Area Affected by Light

The property
**
Options →
**

**
Only Affect This Area
**
 can be checked if you add a
**
Clip Volume
**
 (
**
Create Object → Area → Clip Volume
**
) to the level and use the light's
**
Entity Links → Pick tool
**
 to select the
**
Clip Volume
**
. (Don't forget to
**
close
**
 the Pick mode at the top of the Perspective Viewport after you've clicked on the Clip Volume.) This forces the light to
*
only
*
appear
**
inside
**
 the Clip Volume - very useful in use cases like insuring that light does not spill outside of an interior space, etc., as shown below. You can even use
**
complex
**
 shapes after you've drawn the simple Clip Volume box by clicking on the
**
Edit
**
 button and using the Designer tool to modify the model. The Clip Volume model can be complex, but it must be watertight (i.e., not contain only holes).

![Image](https://www.cryengine.com/docs/static/attachments/44966011)

The intensity and color of lights can also be
*
animated
*
by assigning a value (
*
other than 0
*
) to the
**
Animations
**
 →
**
 Style
**
 property. The playback speed of the active animation is set through
**
 Animations → Speed
**
. There are numerous predefined animations including blink on/off and fade on/off at various speeds in both regular and irregular rhythms, and cycling through colors. Programmers can see, modify or add to these animations in the light shader (
*
engineroot\Engine\Shaders\HWScripts\CryFX\Light.cfx
*
). Non-programmers who want to create custom light intensity and color animations might want to just use Trackview.

##
Global Illumination (SVOGI) Settings

If you want a Projector Light component to be included in SVOGI calculations, set it to
**
Static
**
 (for non-moving entities) or
**
Dynamic
**
 (for real-time bounce calculations, useful with entities that will move). You can also choose
**
Hide if GI is Active
**
 to automatically disable a light whenever GI is activated.

##
Use Case: Virtual Moonlight

There may be times where you want to extend a light of uniform brightness over a longer distance. You can accomplish this by using a large
**
Attenuation Bulb Size
**
 value. In the example below, we've created
*
virtual moonlight
*
using a Projector Light component.
**
Sun brightness
**
 is set to
**
200
**
 to keep the moon texture visible while providing a bit of glow around the moon. The Projector Light component is placed far enough from the center of the level and ~430m above it with its
**
Angle
**
 set to
**
180
**
° so that it lights the entire heightmap. Since in real life the sun (and its light that reflects off of the moon) is so far away from Earth that its brightness is effectively even across the illuminated surface of the Earth, we've set the
**
Attenuation Bulb Size
**
 to
**
5000m
**
 and its
**
Range
**
 to
**
8000m
**
 so its brightness is completely even throughout the heightmap.

This is admittedly an extreme example to illustrate how the Attenuation Bulb Size property works. If you look closely at the terrain where the projector light is illuminating, particularly at its edges, you'll see why: you'll notice a very pixelated texture. Projector lights
*
always
*
 use a texture, even if you don't manually specify one under
**
Projector Options -> Projected Texture
**
. Since these must be only 512x512 pixels, the low resolution of these textures will quickly become very apparent if projected over a large area, so it's unlikely that you would put a projector light so far from a surface.

![Image](https://www.cryengine.com/docs/static/attachments/44966010)

##
Related topics

-
[Volumetric Fog](../../../Graphics%20%26%20Rendering/Lighting/Lighting%20Overview/Volumetric%20Fog.md)

-
[Clip Volumes](../../../Editor%20Tools/Level%20Editor%20Tab/Create%20Object/Area/Clip%20Volume.md)

-
[Vis Areas](../../../Editor%20Tools/Level%20Editor%20Tab/Create%20Object/Area/Vis%20Area.md)

-
[Optical Flare System](../../../Editor%20Tools/Lens%20Flare%20Editor/Optical%20Flare%20System.md)

-
[Lens Flare Editor](../../../Editor%20Tools/Lens%20Flare%20Editor.md)

-
[Global Illumination (SVOGI)](../../../Graphics%20%26%20Rendering/Lighting/Lighting%20Overview/Voxel-Based%20Global%20Illumination%20(SVOGI).md)

-
[CryTif Plug-In](/docs/static/engines/cryengine-3/categories/1114113/pages/1310742)
[Before You Start](#before-you-start)
[Creating the Light](#creating-the-light)
[Setting Core Light Properties](#setting-core-light-properties)
[Using Angle and Projected Textures](#using-angle-and-projected-textures)
[Using Clip Volumes to Constrain Area Affected by Light](#using-clip-volumes-to-constrain-area-affected-by-light)
[Related topics](#related-topics)
