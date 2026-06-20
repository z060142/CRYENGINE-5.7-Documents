# Environment Editor Use Cases

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/60523568
- Page ID: 60523568
- Breadcrumb: Tutorials > Graphics > Environment Tutorials > Environment Editor Tutorials > Environment Editor Use Cases
- Parent: Environment Editor Tutorials

## Content

This tutorial builds on the Environment Editor tutorial series, which explains the techniques used here in depth. The first part simply walks you through the steps to create one example look using only the Environment Editor settings.

The second part of this tutorial provides screenshots of how these free environment presets look in sample levels.  You can download these presets from the
[https://www.cryengine.com/marketplace/product/crytek/environment-preset-pack](
Asset Database
)
, study their settings, freely modify and use them in your own levels.

Since terrain and ocean heights are an important factor, the Asset Database bundle also provides the heightmaps used so you can download and import them into your own levels. Make sure the size of your heightmaps matches the sample you wish to import.

##
Creating a Foggy Night Look

Volumetric fog must be
**
disabled
**
 for this example (by typing the CVar
**
e_VolumetricFog 0
**
 in the Console).
Begin by creating a new environment preset and assigning it to your level.

To create a believable night look, we need to darken the sky, dim the sun, brighten the stars (and optionally, the moon), and balance the need for darkness with the need for light by which the player can navigate.

First, let's darken the sky: set
**
Variables
**
 →
**
Sky Light
**
 →
**
Sun Intensity Multiplier
**
 to
**
0
**
 or a very dark value. This also hides the sun's orb; otherwise, the white disc of the sun will appear in the sky. You can choose to hide the moon and use the simple white sun orb to impersonate the moon and add some illumination. Change this to
**
0
**
 to hide the sun's orb and match the latitude and longitude of the sun and moon to make the sun's luminance emit from the same position as the moon texture.

Keep in mind that the sun's orb (
**
Variables → Sky Light → Sun Intensity Multiplier
**
) doesn't need to be visible in order to have illumination from the sun (
**
Variables → Sun → Sun Intensity (lux)
**
).

[Image: /docs/static/attachments/60523588]

 |
**
Constants → Sun → Latitude
**
 and
**
Constants →
**

**
Moon → Latitude
**
 are the same and
**
Variables
**
 →
**
Sky Light
**
 →
**
Sun Intensity Multiplier
**
is greater than
**
0
**
, so the sun's orb is visible, smaller than the moon texture and positioned on top of it - not a very useful setup.
 |

[Image: /docs/static/attachments/60523587]

 |
Here
**
Constants → Sun → Latitude
**
 has simply been changed to position it next to the moon, its orb is still visible.
 |

[Image: /docs/static/attachments/60523586]

 |
**
Latitude
**
 and
**
Longitude
**
 of
**
 Constants → Sun
**
 and
**
Constants → Moon
**
 are identical and
**
Variables
**
 →
**
Sky Light
**
 →
**
Sun Intensity Multiplier
**
 is greater than zero, placing the sun directly on top of the moon texture.
**
Sun Intensity Multiplier
**
 affect both the visibility and the size of the sun's orb, in this case set so the sun orb is large enough to cover the moon texture completely. A useful setup if you prefer a simple white orb as the moon, insuring that the sun's illumination comes from the same position as the orb. Since the moon texture isn't visible anyway, you could simply set
**
Variables
**
 →
**
Night Sky
**
 →
**
Moon Color
**
 to black to hide the moon completely.
 |

##
Moon Appearance

Now let's configure the moon texture itself: first, let's make it visible by raising
**
Variables
**
 →
**
Night Sky
**
 →
**
Moon Color
**
 to a value greater than zero. Voila, your moon appears. The color and brightness of the moon texture is also affected by
**
Night Sky → Moon Color
**
. You could use this to tint your moon texture any color.

The default moon texture lives in your CRYENGINE folder in
*
engine\engine.pak\EngineAssets\Textures\Skys\Night\half_moon.dds
*
. You can replace this with any 1024x1024 pixel TIF file using the
**
Albedo with transparency
**
 mode in the Photoshop CryTif exporter if you like. (See
[/docs/static/engines/cryengine-5/categories/23756816/pages/60523568#EnvironmentEditorUseCases-nwcmt](
Night with Custom Moon Texture
)
 below for an example.)

##
Creating Moonlight

Next, let's set the
**
Sun
**
 →
**
Sun intensity (lux)
**
 to a much lower value.
**
0
**
 will certainly make it dark, but will make it very difficult for the player to navigate your level without a lot of supplemental lighting. Try a value between
**
200
**
 and
**
1000
**
 to get started. The use of volumetric clouds can also have a profound effect on how much sunlight reaches your level. The values suggested as a starting point are not physically accurate in terms of Earth night values, but you'll find that compromises are required to allow players to see, not to mention factors like the wide range of monitor calibration out there. And, you obviously have creative license in game design. Your HDR settings will also have a strong effect on what the player sees.

Also, since the sun is below the horizon at night, any natural light comes from outer space from sunlight (very faintly from other stars, for example), and when the moon is above the horizon and not blocked by clouds, is reflected off of the moon.

It's unusual that the angle between the sun and the moon forces the sunlight to pass through the dense atmosphere close to Earth's surface, which means that the sunlight reflected by the moon is closer to the actual white color of the sunlight. (Those times when the moon receives only sunlight scattered through the denser atmosphere, the light is reddened just like you see at sunrise, creating the rare "blood moon" phenomenon.) Try setting
**
Sun → Sun color
**
 to
**
white
**
or a
**
slightly blue
**
 tint. Human beings aren't as sensitive to blue as to warm colors, so a blue tint can help create the feeling of night.

Since the moon texture itself does not produce any light, we need to synchronize the positions of the sun and the moon and use a little sunlight to pass for moonlight:

Adjust
**
Constants
**
 →
**
Moon → Latitude
**
 and
**
Longitude
**
 to match
**
Constants →
**

**
Sun
**
 →
**
Latitude
**
 and
**
Longitude
**
.

##
Setting Fog for Night

Set your
**
Variables →
**

**
Fog → Color (Bottom)
**
 and
**
Color (Top)
**
 to a
**
dark
**
,
**
slightly blue
**
 tint. Making these black will effectively turn fog off completely, along with your distance cue - perfect for the surface of the moon with its lack of atmosphere, but not very believable for Earth.

Your level will look something like this:

[Image: /docs/static/attachments/60523611]

##
Light Scattering Around the Moon (Moon Glow)

One of the more subtle aspects of creating a believable moon is setting the way light scatters around (and on top of) it. Here are four groups of settings that will affect this:

1:
**
Sun Radial Beams
**
- Set
**
Variables → Fog → Color (radial)
**
. Setting this to
**
black
**
 will remove all moon glow scattering around the moon texture, like this:

[Image: /docs/static/attachments/60523612]

Not very realistic, is it? Make it just slightly brighter, and use
**
Fog → Color (radial)
**
 multiplier to adjust the intensity. Be sure to set the
**
Fog → Radial
**
 size so the glow spread makes sense with your moon size, and the
**
Fog → Radial
**
 lobe will tweak its further spread over the terrain. Your fog density and color will also interact with this.

[Image: /docs/static/attachments/60523613]

2 -
**
Moon Corona Color -
**
 This is the recommended technique for naturalistic moon glow.

a- Set
**
Variables →
**
**
Night Sky Multiplier → Moon Inner Corona Color
**
and
**
Moon Outer Corona
**

**
Color
**
 to
**
0.1
**

b- Set
**
Variables →
**
**
Night Sky → Moon Inner Corona Color
**
 and
**
Moon O
**
**
uter Corona Color
**
 to the desired color (and brightness) of your moon glow. (Here we've given it a slight blue tint.)

c- Adjust
**
Variables → Night Sky → Moon Inner Corona Scale
**
and
**
Moon Outer Corona Scale
**
**

**
so the glow appears to emanate from the entire moon (not a bright spot smaller than the moon itself). Try values of
**
0.1
**
:

[Image: /docs/static/attachments/60523614]

3 -
**
Variables → Sun Rays Effect
**
 →
**
Sun Rays Visibility -
**
 While you can raise this to a higher value for more dramatic breaking of the moonlight around the terrain and any entities, you'll need to carefully check how this looks by putting something in the foreground to inspect the sun ray breaking around it. You'll find that you'll need to balance
**
Variables → Sun Rays Effect → Sun Rays Visibility
**
 with
**
Sun Rays Attenuation
**
 to brighten up the moon through the use of sun rays but keep them from getting too dramatic around geometry. Try values of
**
2
**
 and
**
6
**
, respectively, as a starting point. We also brightened
**
Variables →
**

**
Fog → Color (Bottom)
**
 and
**
Color (Top)
**
 slightly to create this look:

[Image: /docs/static/attachments/60523615]

4 -
**
Variables →
**

**
Sky Light → Sun Intensity Multiplier -
**
 Setting this to a non-zero value is just going to make the sun's orb visible, which wouldn't make sense unless you'd prefer to use the sun's orb to pass as a simple white circular moon instead of a moon texture (i.e. set this to a positive value and set
**
Variables → Night Sky Multiplier → Moon Color
**
 to
**
0
**
). Obviously you'll need to keep this value low to avoid brightening the sky unrealistically.

##
Setting Up a Night Sky

Now let's set our final values: set
**
Variables
**
 →
**
Night Sky Multiplier
**
 →
**
Horizon Color
**
 and
**
Zenith Color
**
 to
**
non-zero
**
 values to brighten the horizon glow and sky, respectively. Small changes will make a big difference here.

Don't forget to add at least one global environment probe and generate cubemaps once you're finished tweaking your lighting. This will generate specular reflections as well as diffuse ambient light whose intensity you can fine-tune.

Here's the same scene with an environment probe placed dead center, its box size is set to match the heightmap size, and using a
**
Diffuse Multiplier
**
 of
**
2
**
:

[Image: /docs/static/attachments/60523616]

Optionally, you can also enable SVOGI to provide ambient light, although its contribution in dark night scenes may not be worth the performance cost.

In our example, we also placed a few local fog volumes (
**
Create Object → Components → Effects → Fog Volume
**
) in the level to simulate mist in the valley, over the river, and around the lighthouse just to enhance the beams of light.

Lastly, to make your night scene more consistent with human vision in dark conditions, you could experiment with using
**
Variables → HDR → Saturation
**
 to desaturate the entire scene (human eyes lose color perception before they lose the ability to see tones), and/or even use
**
Variables → HDR →
**
**
Color Balance
**
 to tint the entire scene slightly blue. However, if you plan to use artificial light sources such as fire or electric lights, you may not want to desaturate the scene as a whole. Also, although there is no true digital equivalent for the human loss of sharp vision in very dark conditions, you could also subtly increase
**
Variables → Depth of Field → Blur Amount
**
 to soften the appearance slightly.

**
Variables → Night Sky Multiplier → Moon Color
**
 must be
**
0
**
 for the moon texture to appear, otherwise it will simply make a moon-sized hole in the sky that covers the stars.
**
Variables →
**

**
Sky Light → Sun Intensity Multiplier
**
 must be set to
**
0
**
 at night unless you want the sun orb glowing on top of the moon. Optionally, if you want to use the sun as a simple, glowing orb that mimics the moon without any details of its surface, you can hide the moon texture completely by keeping
**
Variables →
**

**
Night Sky Multiplier → Moon Color
**
 at
**
0
**
 and keep
**
Variables →
**

**
Sky Light → Sun Intensity Multiplier
**
 above zero to keep the sun visible. Remember that the size and visibility of the sun orb is also affected by the halo of light scattered around it, controlled by
**
Variables →
**

**
Sun Rays Effect
**
 →
**
Sun Rays Visibility
**
.

##
Environment Preset Examples

##
Foggy Night with Clear Skies

[Image: /docs/static/attachments/60523618]

Above is the environment preset you just created and implemented in a mountainous level. Here, three volumetric fog volumes are used (river, valley, lighthouse).

Additional light components: projectors (headlamps on AIs and vehicle) and point light (lighthouse, radar dish, area light (without shadows) supplementing moonlight appearance on lighthouse and vehicle). No volumetric clouds.

To download the Foggy Night with Clear Skies environment preset, please click
[/docs/static/attachments/56660064](
env_demo_01-night.env
)
.
Since these environment presets are tailored to the terrain heightmaps and ocean height, you can also download the heightmaps used in all examples (except where otherwise noted)
[/docs/static/attachments/60523590](
mountains_and_river.raw
)
.

In the
[/docs/static/engines/cryengine-5/categories/23756816/pages/35849146](
Terrain Editor
)
, change
**
 Edit → Set Terrain Max Height
**
 to
**
562m
**
 before importing.)

**
Notes
**
:

-
Make sure that you click on these images to view them full screen so your perception isn't skewed by the white background.

-
Click on the name of each environment preset to download them and try them in your own level.  They should be saved to your project
*
libs\environmentpresets
*
 folder.

-
After downloading, click on each downloaded environment preset in the Environment Editor's Asset Browser to load it temporarily in your level, or drag it onto the Perspective Viewport to permanently assign it to your level.

##
Dawn

Set
**
TOD
**
 to
**
12:00
**
. SVOGI on, moon and stars are dimmed to balance to brightening sky.. Enable volumetric clouds and volumetric fog to see as shown. One global environment probe used in this example image.

To download the Dawn environment preset, please click
[/docs/static/attachments/60523589](
env_demo_02-dawn.env
)
.
 |

[Image: /docs/static/attachments/60523571]

 |
[Image: /docs/static/attachments/60523570]

 |

##
Sunny, Windy Midday

Set
**
TOD
**
 to
**
16:30
**
. SVOGI on. Enable volumetric fog and clouds; strong wind influence set on clouds. Global and local environment probes are used in detailed areas in this screen shot.

To download the Sunny, Windy Midday environment preset, please click
[/docs/static/attachments/60523719](
env_demo_03-midday.env
)
**
.
**
 |

[Image: /docs/static/attachments/60523718]

 |
[Image: /docs/static/attachments/60523717]

 |

##
24 Hour Day - Night Cycle

SVOGI on. Enable volumetric fog and clouds. In these screen shots, one global environment probe and 200m probes are used around key areas. Fog volumes are deactivated at certain times of day. Separate set of environment probes are toggled on only for each specific hour of the day. Environment probes can be blended by making each pair of adjacent times visible and using visual scripting to fade their diffuse and specular multiplier values up and down to effectively crossfade them. See the
[/docs/static/engines/cryengine-5/categories/23756816/pages/24285386](
Creating a 24 Hour Cycle
)
 tutorial for additional information.

To download the 24 hour Day - Night Cycle environment preset, please click
[/docs/static/attachments/60523697](
day_night_cycle_2.env
)
**
.
**
 |

[Image: /docs/static/attachments/60523704]
**
4:00 AM
**

 |
[Image: /docs/static/attachments/60523700]
**
5:00 AM
**

 |

[Image: /docs/static/attachments/60523662]
**
5:45 AM
**

 |
[Image: /docs/static/attachments/60523663]
**
6:00 AM
**

 |

[Image: /docs/static/attachments/60523669]

**
8:00 AM
**

 |
[Image: /docs/static/attachments/60523668]
**
12:00 PM
**

 |

[Image: /docs/static/attachments/60523667]

**
4:00 PM
**

 |
[Image: /docs/static/attachments/60523666]
**
4:30 PM
**

 |

[Image: /docs/static/attachments/60523691]
**
8:00 PM
**

 |
[Image: /docs/static/attachments/60523708]
**
4:00 AM
**

 |

##
Late Afternoon, Partly Cloudy

SVOGI on, sky dome texture used. Enable volumetric fog. Set
**
TOD
**
 to
**
16:30
**
 for correct settings. While volumetric clouds are not used here, you could enable them and configure them to match the sky dome to have some more realistic cloud movement.

To download the Late Afternoon, Partly Cloudy environment preset, please click
[/docs/static/attachments/60523592](
desert_gold_magic_hour.env
)
.
 |

[Image: /docs/static/attachments/60523593]

 |
[Image: /docs/static/attachments/60523591]

 |

##
Night with Dense Fog

Set
**
TOD
**
to
**
12:00
**
. SVOGI is disabled,
**
Sun Intensity (Lux)
**
is set to
**
 1000
**
. Enable volumetric fog. Note that in this example, the ocean height is
**
50m
**
 and camera height is
**
55m
**
. Global volumetric fog:
**
Height (Bottom)
**
isset to
**
50m
**
,
**
Global Density
**
 is set to 1.3.
**
Variables → Shadows → Shadow Jittering
**
 is set to
**
7
**
 to soften shadows, but in reality the shadows are still much harder and stronger than they would be in such dark, foggy conditions. One global environment probe with a
**
Diffuse Multiplier
**
 of
**
0.3
**
 is used in these screenshots.

To download the Night with Dense Fog environment preset, please click
[/docs/static/attachments/60523597](
foggy_dense.env
)
.
 |

[Image: /docs/static/attachments/60523599]

 |
[Image: /docs/static/attachments/60523598]

 |

##
Dark Clear Night

**
Set TOD
**
to
**
12:00
**
. SVOGI is disabled,
**
Sun Intensity (lux)
**
 is set to
**
300
**
. Enable volumetric fog. Note that in these images, the ocean height is
**
50m
**
 and the camera height is
**
55m
**
.

To download the Dark Clear Night environment preset, please click
[/docs/static/attachments/60523595](
night_dark_clear.env
)
.
 |

[Image: /docs/static/attachments/60523596]

 |
[Image: /docs/static/attachments/60523594]

 |

##
Night Vision

Set
**
TOD
**
 to
**
12:00
**
. Color is desaturated, HDR is used to tint everything green. Grain effect and depth of field blur are used.

To download the Night Vision environment preset, please click
[/docs/static/attachments/60523573](
nightvision.env
)
.
 |

[Image: /docs/static/attachments/60523582]

 |
[Image: /docs/static/attachments/60523580]

 |

##
Magic Hour, Low Clouds

Set
**
TOD
**
 to
**
12:00
**
. Download the 4K terrain heightmap
[/docs/static/attachments/60523574](
magic_hour_low_clouds_4K.raw
)
. Create a 4K level and set
**
Terrain Max Height
**
 to
**
500m
**
 before importing the heightmap. See
[/docs/static/engines/cryengine-5/categories/23756816/pages/35849146](
Terrain Editor
)
 for more information.

SVOGI on. Enable volumetric fog and volumetric clouds. Volumetric clouds are placed
**
below
**
 the terrain to mimic fog volumes, strongly affected by wind.
**
[/docs/static/engines/cryengine-5/categories/23756816/pages/35848989](
Level Settings
)

**
must have the following options enabled:

-
**
Env State → Sun Shadows from Terrain
**

-
**
Vol Fog Shadows → Enable
**

-
**
Vol Fog Shadows → Enable for Clouds
**
Make sure
**
TOD
**
 is set to
**
12:00
**
in the Environment Editor.

To download the Magic Hour, Low Clouds environment preset, please click
[/docs/static/attachments/60523572](
magic_hour_low_clouds.env
)
.
 |

[Image: /docs/static/attachments/60523578]

 |
[Image: /docs/static/attachments/60523575]

 |

##
Dark Night Lit by Fog Volumes

Set
**
TOD
**
 to
**
12:00
**
. With
**
Variables → Sun → Sun Intensity (Lux)
**
 set to only
**
800 lux
**
, this level is lit mostly by
[/docs/static/engines/cryengine-5/categories/23756816/pages/44966059#LightComponents-pointlight](
Point Light
)
 entity components set to emit flickering light to simulating light coming from the very large emissive fog volumes to which they're attached, each using various noise settings to create animated patterns. SVOGI on. Enable volumetric fog. In these example images, a full grid of environment probes with box sizes of
**
200m
**
 which overlap by
**
10m
**
 cover the entire heightmap as well as a global probe (see the respective image below).

To download the Magic Hour, Low Clouds environment preset, please click
[/docs/static/attachments/60523641](
night_elephant_moon.env
)
.
 |

[Image: /docs/static/attachments/60523637]

 |
[Image: /docs/static/attachments/60523634]

 |

[Image: /docs/static/attachments/60523638]

 |
[Image: /docs/static/attachments/60523631]

 |

[Image: /docs/static/attachments/60523644]

Partial environment probe grid that covers the entire heightmap is shown in this image.

 |

 |

##
Foggy Night and Day

SVOGI on. Enable volumetric clouds and volumetric fog. Set
**
TOD
**
to
**
18:00
**
. The look of this environment preset depends wholly on the use of a large (effectively global) emissive fog volume. The first row of images show how the environment preset looks without the fog volume. To the right, you can see some key settings, including the settings for the global fog volume that's currently disabled. You can also see in the environment preset that there is no sunlight and only the slightest brightness in the sky. Effectively, there is no light on the terrain or meshes except from the light components and environment probes, and the lightening effect of the emissive fog between the camera and the meshes (even though emissive fog does not actually emanate light except onto itself).

To download the Foggy Night and Day environment preset, please click
[/docs/static/attachments/60523783](
overcast.env
)
.
 |

[Image: /docs/static/attachments/60523865]

 |
[Image: /docs/static/attachments/60523867]

 |

This row of images below shows how this environment preset was intended to be used for a foggy night look. Global and a few local environment probes were used. The fog provides a significant lightening atmospheric effect (combined with environment probes).
 |

[Image: /docs/static/attachments/60523863]

 |
[Image: /docs/static/attachments/60523781]

 |

Finally, this exact same environment preset is used in the images below to create a daytime foggy look simply by changing
**
Constants
**
 →
**
Global Illumination
**
 →
**
Sky Color Multiplier
**
 to
**
10
**
, changing the fog volume's
**
Emission Intensity
**
 from
**
0.2
**
 to
**
1.0
**
, and disabling the nighttime light components. A different set of environment probes was also used. Note that setting
**
Variables → Sun → Sun Intensity
**
 to
**
0
**
 removes the hard shadows that it would produce, leaving only soft contact shadows that are consistent with overcast/foggy conditions.
 |

[Image: /docs/static/attachments/60523778]

 |
[Image: /docs/static/attachments/60523779]

 |

Here's the same daytime version of this environment preset used in a different level. A sky dome was used for clouds. The first two examples use a snow texture; the second two do not.
 |

[Image: /docs/static/attachments/60523650]

 |
[Image: /docs/static/attachments/60523651]

 |

[Image: /docs/static/attachments/60523722]

 |
[Image: /docs/static/attachments/60523721]

 |

##
Night with Custom Moon Texture

Although this example is not downloadable, it demonstrates the use of a custom moon texture using a Hubble telescope image of Titan, tinted red using
**
Variables → Night Sky → Moon Color
**
, the color of the sunlight is set to a similar color to cast red light on the terrain, and just for extra fun, set the fog color to dark green. SVOGI and volumetric fog were both disabled.

[Image: /docs/static/attachments/60523622]

[#creating-a-foggy-night-look](
Creating a Foggy Night Look
)
[#moon-appearance](
Moon Appearance
)
[#creating-moonlight](
Creating Moonlight
)
[#setting-fog-for-night](
Setting Fog for Night
)
[#light-scattering-around-the-moon-moon-glow](
Light Scattering Around the Moon (Moon Glow)
)
[#setting-up-a-night-sky](
Setting Up a Night Sky
)
[#environment-preset-examples](
Environment Preset Examples
)
