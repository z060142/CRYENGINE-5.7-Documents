# Tutorial - Lighting - Creating a 24 hour cycle

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/24285386
- Page ID: 24285386
- Breadcrumb: Tutorials > Graphics > Lighting Tutorials > Tutorial - Lighting - Creating a 24 hour cycle
- Parent: Lighting Tutorials

## Content

## Overview

In this tutorial we will be going over the process of creating a day-night cycle using the Environment Editor inside CRYENGINE, which will serve as a good basis for most Earth like lighting scenarios. This will cover setting up a few different times of day as well as the transitions between them, while also staying within the boundaries of physically accurate lighting.![Image](https://www.cryengine.com/docs/static/attachments/24154263) *Pic1: Time-lapse of a full day-night cycle achieved in CRYENGINE*

Before we get into the details please keep in mind that all of the parameters in the Environment Editor contribute to the final look of your level and they are all affecting each other. The influence of some of them only becomes apparent when certain conditions are met so creating a polished lighting scenario requires quite a lot of back and forward between different elements. This tutorial is not a step by step workflow, it’s aimed at giving you a better understanding of the system and the things you can achieve by controlling the parameters made available by it.

### Helpful Information

It is important to note that CRYENGINE uses two distinct fog models to create atmospheric effects. For high quality results we are using a voxel-based volumetric fog model designed to accurately interact with all entities in your level. Keep in mind that this has a noticeable impact on performance, so as an alternative for the lower end we provide the option to use regular fog. In a nutshell, Volumetric Fog allows lights, cubemaps, and shadow to interact with the global/local atmosphere, whereas regular fog does not. We will be covering both of these options in this tutorial.

As mentioned in the beginning it is important to stay within physically accurate illuminance values when setting up any lighting scenario in order to get the most out of our PBS pipeline, so depending on the result you are trying to achieve, some research might be in order as to what your illuminance values should be. At the same time getting the desired look for your environment is always the highest priority so it takes some fine tuning to achieve something that looks good but still follows real world values.

To open the Environment Editor go to **Tools Menu -> Environment Editor** from the list. The layout of this tool incorporates a number of different elements. On the left side we have the Presets list, under it there is the Sun orientation/angle settings and next to these there’s the list of customizable parameters. On the right side you can find the curve editing tools, the timeline at the top, a visual representation of the selected property over the course of the 24 hour cycle & under it and at the bottom, we have the Start/Current/End time values as well as controls for playing the cycle.

![Image](https://www.cryengine.com/docs/static/attachments/24154167) *Pic2: Environment Editor Layout*

To change the time of day simply drag the control handle (triangle) in the timeline to either side. You cannot go beyond the 0 and 1 values since they represent a full 24 hour cycle.

The Environment Editor contains a wide number of advanced parameters that would allow you to fully customize the lighting in your level as well as the appearance of the sky. These parameters are split into logical groups that each control different aspects of your environment.

### Curve Editor

The curve editor is used to control the transition between variable values at different times of day (not constants, which can only have one value for all times of day). Changing a variable value will automatically create a key for you at the current time. To see the current keyframes for a variable, click on that variable name in the Variables panel. Clicking on an actual value will also show the current keyframes, but will create a new keyframe unless you press ESC.

You can zoom in on the timeline at the top of the Curve Editor using your scroll wheel; doing so will also increase the precision of the current time display. If you want to edit the value of an existing keyframe, you need to set the current time to match the keyframe's position, which you can do either by typing it in the Current Time box (presuming you already know the exact time of a keyframe), or zoom all the way in on a keyframe until you see its exact position, then drag on the time ruler to get the current time to match the keyframe position.

It's a common mistake to assume that the current time matches the time position of a key frame and change the value, only to find that you've created a new keyframe very close to the existing one. A good practice to simplify the use of keyframes is to agree on a studio policy of only setting keyframes at common times, like exactly on the hour, half hour, or quarter hour.

### Dynamic Time of Day and Curve Editor Settings

The other values set in Curve Editor are **Start Time**, ** Current Time**, ** End Time**, and the ** Playback Speed**.

Dynamic time of day means that you'll need to change the playback Speed in the Curve Editor to a value greater than 0. A Playback Speed of 1 means that one hour of game time (i.e., on the time rules) passes in each second of real time. Since an hour = 3600 seconds, "real time" would be a Playback Speed of.0002.

Since the precision of the Playback Speed parameter is limited to.001,.001 is as close to "real time" as can be set using this interface. (i.e., 5x real time) For slower playback speeds, time of day could be changed through C++, and the device's internal clock consulted for greater precision.

Assuming Playback Speed is greater than 0, the current time will progress from the Start Time to the End Time, then jump back to the Start Time and continue to loop. This gives you the flexibility not only to create full 24 hour day/night cycles, but also to create more subtly changing lighting conditions during a game mission by looping between daylight or nighttime hours that introduce a variety of lighting and weather conditions over the course of a day or part of a day, instead of static lighting.

Note that in Sandbox editor, playback begins at the Current Time while pure game mode begins at the Start Time. You can of course also set the current environment preset and modify its parameters through visual scripting or code.

TIP
If you want to use a playback speed that is significantly faster then normal, at some point you may need to adjust how often the sky is updated. The cVar **e_SkyUpdateRate** sets what *percentage* of the sky is updated per frame. The default value is 1, which means that the sky is only fully updated every 100 frames. For fast, timelapse-style time of day change, you may need to  increase this value, and at very fast times, even use a value of 100 to insure that the sky is fully updated every frame. Use this with discretion, as it obviously has a performance cost.
We won’t be going over all of these parameters as some of them don’t require any changes for the generic Earth-like scenario we’re creating here. We will however cover the sections that we are changing to get a better idea of what they control. We will also go through the process of creating smooth transitions as the time of day changes by using the curve editor.

### Initial Setup

In this example our goal is to achieve a generic day-night cycle at 45° latitude.

We will begin by right clicking on the left side (in the explorer tree view) **Add -> New** and save it as ** day-night_cycle.xml**. To open up an existing preset you will have to select ** Add -> Existing**. Presets are saved in **<YOUR_PROJECT_FOLDER\Assets\libs\environmentpresets**.

Next we need to set up the Sun direction and the latitude. These values are located under the preset list on the left side of the editor. Set the **Sun Direction** to 180° so it rises in front of the camera. For the latitude we have to change the ** NortPole..Equator..Southpole** value to 45. These two values are not stored in the environment preset file so you can use the same preset with different settings for orientation and latitude.

The first thing that we need to do before we start setting up our cycle is change the **Film curve whitepoint** to 4 (default is 1). This can be found under the HDR group in the Environment Editor. We will also be using the new and improved Eye Adaptation mode, to do this open up the console and simply type in ** r_HDREyeAdaptationMode 1**. These 2 values dramatically change the sensitivity to light so they need to be set up properly before changing any of the other parameters.

![Image](https://www.cryengine.com/docs/static/attachments/24154168) *Pic3: Location of the Film Curve Whitepoint setting*

Now we are ready to start creating our day-night cycle.

### Setting up the Sun

The Sun category contains the settings that affect the color and the intensity of the direct sun light.

#### Sun Color:

We start off by setting the current time to 12:00 and giving it a slightly yellow tint (240, 225, 210). This will create a key at that time and update the preview to represent the change we just made. Select the newly created key and set the In/Out tangent to linear.

This value needs to remain constant throughout the day so we will create another key at 09:00 and assign it the same color. For this one set the In tangent to Zero and the Out to linear. Mirror the result at 15:00.

As it nears Dusk/Dawn the sun color transitions into a saturated orange, to set this up change the current time to 06:00 and assign it the appropriate color (170, 84, 0) and set both In/out tangents to Zero. Mirror this newly created key at the 18:00 time.

At this point it is worth noting that the Sun parameters are also used to control the Color/Intensity of the light coming from the moon, although the moon doesn’t move throughout the night.

To set this up we create a key at 05:56 and give it a blue tint (140, 160, 176). To keep this constant over the whole night we need additional keys with the same value at 00:00, 18:04 and 23:59 respectively. Change the In/Out tangents for all of these keys to linear.

If you set this up correctly your preview and curves should look like this:

![Image](https://www.cryengine.com/docs/static/attachments/24154169) *Pic4: Screenshot of the Sun Color gradient preview and curves*

#### Sun intensity (lux):

This property controls the illuminance of the sun and as mentioned previously it is important to keep this close to the physically based value. A quick search on the internet comes up with an average illuminance value of 100000 lux for bright sunlight.

![Image](https://www.cryengine.com/docs/static/attachments/24154170) *Pic5: Screenshot from the Wikipedia page containing the Illuminance values chart*

Change the current time to 12:00 and create a key with the value set to 120000. The reason why this is higher than real world values is some of the light gets absorbed by the materials giving them a final lux value that’s considerably smaller than the source. We will get back to this once we set up our Sky Light later on.

Now that we have the basis for our Sun Intensity laid out we can go ahead and set up the rest of the keys for this value.

The intensity of the sun diminishes as it gets closer to the horizon so to achieve that we need to set up a few more keys. Change the time to 08:00 and set the intensity down to 110000, do the same on the opposite side at 16:00.

As we get closer to sunset/sunrise the intensity drops very low. We will now create a key at 06:00 with the value set to 5 and mirror the value at 18:00.

Real world measurements read <1 lux values for moonlight, this number is way too small for the engine to still accurately render shadows coming from the moon, so we will stick with the same constant value of 5 for night time. For that we need to set up keys at 00:00 and 23:59.

Making sure the transitions between your keys are smooth your gradient and curves should look like this:

![Image](https://www.cryengine.com/docs/static/attachments/24154171) *Pic6: Screenshot of the Sun Intensity (lux) gradient preview and curves*

Sun Specular multiplier:

As you might have guessed this controls the specular contribution of the sunlight. For any realistic lighting scenario this value should always be kept at 1.

### Sky Light

You’re probably wondering why we skipped all the way to sky light. The reason is a lot of the settings in the environment editor affect each other. It’s good practice to get the sun/sky settings nailed down before you go into setting up your fog.

Parameters in this section are solely used to compute the sun light scattering through the atmosphere effectively controlling the appearance of the sun disk as well as the hue of your sky. They do not directly affect the rendering of objects in the world (for example, lighting colors and intensities). They do however affect the overall illuminance of your scene through the use of Environment Probes as mentioned earlier.

#### Sun Intensity Multiplier

Change the time to 12:00 and set the intensity to 50. At 05:45 and 18:15 drop this value to 1. Create two more keys at 00:00 and 23:59 and set the value to 0. The transition from 0 to 1 gives us the effect of the sky brightening in the area where the sun is just about to set.

![Image](https://www.cryengine.com/docs/static/attachments/24154176) *Pic7: **Sun Intensity Multiplier** curve setup*

*![Image](https://www.cryengine.com/docs/static/attachments/24154225) Pic8: Screenshot taken at 05:30*

Note the slight brightening of the horizon around the area where the sun is about to rise.

To get an accurate reading of the illuminance in your level you need to measure it on a surface that’s perpendicular to the sun. We can setup a couple of planes for this purpose so then all you need to then do is set **r_HDRdebug 1** in the console and simply look at the surface. Keep in mind that turning this on brightens the whole scene so don’t forget to turn it off once you’re done measuring your illuminance.

![Image](https://www.cryengine.com/docs/static/attachments/24154172) *Pic9: Planes facing the sun used for measuring full sunlight/shadow illuminance*

By looking directly at the surface we’re getting a reading of approximately 80000 lux. At this point the only source for our illuminance is the sun light so to refine this further we will have to enable the sky light to contribute to it as well.

In order to do that we will need to set up an Environment Probe. This handles indirect lighting effectively acting as ambient lighting that you would normally get from the sky. We won’t get into specifics about Environment Probes (for that check the dedicated page **[Environment Probes](/docs/static/engines/cryengine-3/categories/1114113/pages/1048591)**) but for now go to your ** Create Objects** tab and under ** Misc** there’s the Environment probe entity. Drag that into your scene, change its size to encompass your whole terrain, make it active and generate cubemap. Keep in mind that any changes that you do to your time of day will require regenerating the cubemap (It’s recommended to do that with the entity turned off so it doesn’t pick up any lighting information from a previously generated cubemap).

By doing this we are now getting blue tinted shadows as opposed to pure black and our lux value also jumped up to about 100000 while keeping the shadow illuminance at around 20000. A 1/5 ratio between fully lit/shadow areas is close to real world values.

![Image](https://www.cryengine.com/docs/static/attachments/24154173) *Pic10: Top - Fully lit area lux reading, Bottom - Shadow area lux reading*

Rayleigh Scattering

This controls how much the sun light is scattered by the atmosphere. Set this to 1 for the whole timeline.

#### Wavelength (R/G/B)

The parameters that control the hue of the atmosphere are the Wavelength (R/G/B) values. We only need to set these once for the whole cycle.

Taken from the Wikipedia page on Diffuse Sky Radiation (also known as Skylight) we set these values at 650 (R), 550 (G), 450 (B).

![Image](https://www.cryengine.com/docs/static/attachments/24154179) *Pic11: Screenshot from the Wikipedia page detailing Diffuse sky radiation*

Going forward it is important to note that each of the parameters that control the Fog as well as the Volumetric Fog have an impact on the overall illuminance of your scene.

### Fog

Now that we have a smooth transition in the light intensity and color throughout the day we can continue to refine the appearance of the sky in relation to the time of day. For that we will be using fog.

Fog is used to enhance the depth of our scene and it’s also responsible for creating the haze at the horizon as well as the glow around the sun.

There are two different components that contribute to the fog:

- The first one is a vertical gradient of fog throughout your level for which you can control the colors used (**Color bottom/top** parameters), the intensity of those colors (** Color bottom/top multiplier**) as well as the start/end height (** Height bottom/top**) and overall density (** Density bottom/top parameters**). Anything beyond the specified heights will use the defined color, multiplier and density for bottom and top respectively. Caution should be taken before using high fog density values as it can completely override the sky colors and dramatically change the look of your level. Basically fog should be used to enhance your scene and add more color to specific scenarios rather than fully control the appearance of your sky. With that in mind please note that it is possible to set the top density to a higher value than the bottom density. This will effectively flip the vertical fall off and produce thick fog in the sky and clear views at the bottom if such a result is desired. We also have the option to offset the transition between the top and bottom of this gradient by using the ** Color Height Offset** parameter.
- The second component is the radial fog which controls the bloom around the sun. This can be used to enhance effects like the strong orange colors you’d expect to have around the sun at sunset/sunrise. We can specify the color/multiplier for it and we can control the size of the glow perpendicular to the camera (**Radial Size**) as well as the size towards the camera (** Radial Lobe**).

Inside the Fog group there are also settings that control the overall impact fog has over the level. The **Final Density Clamp** parameter controls the maximum density for the fog. This can be used in extremely foggy environments to avoid the background completely fading into the fog.

**Global Density** controls the overall fogginess of the scene so it multiplies on top of the top/bottom density values as well as the radial fog.

Here we also have the option to remove the fog around the camera and make it fade in at a specified distance. This can be achieved by using the **Ramp Start/End/Influence** parameters.

Lastly we have the **Shadow Darkening** settings that are only used to control the appearance of the fog in shadow areas. In order to enable the effect of these values VolFogShadows needs to be enabled in the Environment Panel. This is not to be confused with the Volumetric Fog in the Environment Editor which has a global influence.

![Image](https://www.cryengine.com/docs/static/attachments/24154199) *Pic12: The Fog parameters section inside the Environment Editor*

Now that we have a better understanding of what the different settings for fog control we can continue setting up our day-night cycle.

#### Color (bottom)

We start by setting the current time to 12:00 and assigning a light blue color (185, 251, 251). This value needs to stay consistent throughout the day and will start fading to almost black once we get close to sunset/sunrise. Create two more keys at 07:00 and 17:00 and assign the same color. After we’ve done that create a key at 06:00 and 18:00 and assign them a very dark grey color (13, 13, 13). Copy the same value to 00:00 and 23:59 to keep it constant for night time. We will be using this to create the illusion of light pollution on the horizon at night time.

![Image](https://www.cryengine.com/docs/static/attachments/24154204) *Pic13: Color (bottom) curves setup*

Color (bottom) multiplier

Set this value to 3 for mid day and gradually drop it to 0.02 towards dusk/dawn. The reason for that is as the sun descends we need to allow the radial color to kick in so it creates the localized orange bloom around the sun. So we need a key at 12:00 with the value set to 3 and 4 more keys at 00:00, 06:00, 18:00 and 23:59 with the value set to 0.02.

If you are wondering why this is set so low for night time it is because of the way eye adaptation works making the fog way too strong in low light conditions.

![Image](https://www.cryengine.com/docs/static/attachments/24154213) *Pic14: Color (bottom) multiplier curves setup*

Height (bottom)

We only need to set this once for the whole timeline so let’s set two keys at 00:00 and 23:59 with the same value of 70. We only have to do this because the Ocean height for our test level is set to 70 and we want the gradient to start at that height.

#### Density (bottom)

We want the amount of fog to ramp up at sunset/sunrise. To achieve this set some keys at 06:00, 07:00, 17:00 and 18:00 wih a value of 0.3 then set 3 more keys at 00:00, 12:00 and 23:59 with a value of 0.2. As always make sure you have a smooth transition from one key to another by using editing their tangents.

![Image](https://www.cryengine.com/docs/static/attachments/24154232) *Pic15: Density (bottom)curves setup*

Color (top)

This value will be very subtle as we will be setting our top density quite low. For midday assign a light blue color, slightly darker than the bottom one, let’s say 131, 183, 231. At 07:00 and 17:00 change the value to a darker blue like 51, 72, 90. With the low density we will be using this color has no impact at night time. I have created more keys at 00:00, 06:00, 18:00 and 23:59 and set the value to black, but this is entirely optional.

![Image](https://www.cryengine.com/docs/static/attachments/24154233) *Pic16: Color (top) curves setup*

Color (top) multiplier

The only key we need to create for this parameter is at 12:00 so change your current time accordingly and set the value to 1. Set the tangent to auto so it gradually transitions to 0 towards the ends of the timeline.

#### Height (top)

We don’t need to change this value for this particular scenario.

#### Color height offset

As mentioned before this value can be used to offset the height of the transition between our top and bottom colors which is not necessary for our level.

![Image](https://www.cryengine.com/docs/static/attachments/24154234) *Pic17: The effect of Color height offset*

Color (radial)

Between 08:00 and 16:00 set this color to a light yellow like 193, 158, 100. As we get closer to the ends of our timeline this should transition into a gradually darker orange. To get this result set two keys at 07:00 and 17:00 and assign them a dark yellow color like 192, 126, 49 and leave the 00:00 and 23:59 times to their default value of black. Provided you’ve set up the curves properly this should give you the orange color when the sun is right above the horizon.

![Image](https://www.cryengine.com/docs/static/attachments/24154235) *Pic18: Color (radial) curves setup*

Color (radial) multiplier

To start with set this to 16 for mid day. The impact of the radial fog becomes more obvious as the light intensity drops so we will have to decrease the multiplier as we go towards the ends of the timeline. Create two keys at 07:00 and 17:00 set the value to 10.

It’s probably a good time to mention that the radial fog also gets applied to the moon during night time so if we keep our multiplier at 10, as soon as the sun goes under the horizon we will get a huge orange glow for the moon. To fix this create some keys at 05:55 and 18:05 and set the value to 0. It’s possible to set this up to control the bloom for the moon but there is a dedicated section for night sky. We will go over that later on.

![Image](https://www.cryengine.com/docs/static/attachments/24154236) *Pic19: Color (radial) multipliercurves setup*

Radial size

We only need to change this slightly to get a more pronounced effect. Set two keys with a value of 0.8 at the 07:00 and 17:00 times.

#### Radial lobe

Same as the Radial size, set this to 0.8 at 07:00 and 17:00 respectively.

![Image](https://www.cryengine.com/docs/static/attachments/24154237) *Pic20: Top: Radial size curve, Bottom: Radial lobe curve*

Global density

As mentioned previously we want our fog to be denser in the morning/evening and fade out as the sun gets higher in the sky. Set a key at 12:00 and put in a value of 0.05. To handle the smooth transition add a few more keys at 00:00, 06:00, 18:00 and 23:59 with the value of 0.1.

![Image](https://www.cryengine.com/docs/static/attachments/24154238) *Pic21: Global densitycurve setup*

These are all the parameters we need to change in the Fog section for our day-night cycle. By now you should have a fully working transition from dawn to dusk.

Next we will be setting up the values for night time in order to get a complete 24 hours cycle.

### Night Sky

Similarly to the fog the night sky is controlled by a vertical gradient by specifying the bottom color (**Horizon**) and the top one (** Zenith**). You can also control the offset of this gradient by changing the ** Zenith Shift** value.

This group also contains the parameters that control the intensity of the stars (**Star intensity**), the appearance of the moon as well as the glow effect around it (** Moon color** and the ** Inner/Outer corona color and scale**)

We will only set most of these values once for the whole timeline, the reason being the moon doesn’t move so there is no need for any transitions during night time.

#### Horizon color

Let’s start by setting this to a dark blue color like 20, 36, 51. This will help make the light pollution effect more pronounced.

#### Zenith Color

We want our night sky to gradually turn darker towards the top as less residual light is able to penetrate the upper layers of the atmosphere. To achieve this set the Zenith color to pure black.

#### Zenith Shift

To get a smooth transition between the two colors set this to 0.8. This works in a similar way to the **Color height offset** parameter for Fog.

#### Star intensity

Set this to 0.01 for night time between 00:00 – 06:00 and 18:00 – 23:59 respectively. We want some of the stars to also be visible for a little while after the sun has risen above the horizon. To achieve this add two more keys at 06:30 and 17:30 and set the value to 0.1.

![Image](https://www.cryengine.com/docs/static/attachments/24154239) *Pic22: Star Intensity curve setup*

![Image](https://www.cryengine.com/docs/static/attachments/24154240) *Pic23: Some of the brighter stars still being visible after the sun has risen*

Moon color

This parameter controls the emissive color of the moon. For night time set this to a desaturated blue like 51, 58, 65. Assign this value for the whole night duration by creating the appropriate keys. For day time this will transition to a light blue color, as we want the moon to still be visible for most of the day. Create two keys at 07:00 and 17:00 and assign them the color 200, 228, 255.

![Image](https://www.cryengine.com/docs/static/attachments/24154241) *Pic24: Moon colorcurve setup*

Moon inner/outer corona scale and color

As mentioned previously these parameters control the glow around the moon. We only need to set these once for the whole timeline:

Moon inner corona – color 140, 160, 176

Moon inner corona scale - 2

Moon outer corona – color 34, 57, 70

Moon outer corona scale – 2

### Night Sky Multiplier

This section contains parameters that control the intensity of the colors used by the Night Sky. These only need to be set up once for the whole cycle and here are the values:

Horizon color – 0.01

Zenith color – 0.003 (please note that since we set this to black the multiplier has no impact)

Moon color – 0.1 – setting this to 0 completely removes the moon texture

Moon inner corona color – 0.01

Moon outer corona color – 0.01

![Image](https://www.cryengine.com/docs/static/attachments/24154242) *Pic25: Night time screenshot of the finished result*

Now that we finished setting up the night sky we have a complete day-night cycle. Next we will be looking at how to set this up to work with the Volumetric Fog as well.

### Volumetric Fog

Turning this on completely overrides the regular fog and it offers a higher quality fog solution that is designed to properly interact with other entities in your level. As mentioned in the beginning this has a considerable impact on performance so it should be used wisely.

To enable it use the command **e_volumetricfog 1** in the console. To insure that this (and any other cVars) will be set correctly in the game and/or in the editor, you either need to use [config files](/docs/static/engines/cryengine-3/categories/1638401/pages/1605736) or add them to your.cryproject file.

Although there are some similarities between regular fog and volumetric fog, the later one has a unique set of parameters that are better suited for its functionality.

We will go over these parameters in order to get a better understanding of what they do, however we only need to adjust some of them for what we’re trying to achieve.

#### Height (bottom)

Same logic applies as for the regular fog, set this value to 70 for the whole timeline.

#### Density (bottom)

Set this to 0.5 at 00:00, 05:00, 12:00, 19:00 and 23:59 and add two more keys at 06:15 and 17:45 with a value of 0.8. Setting the tangents for these keys to get a smooth curve between them will make the fog gradually ramp up at sunset/sunrise.

![Image](https://www.cryengine.com/docs/static/attachments/24154243) *Pic26: Density (bottom)curve setup*

Height/Density (top)

Keep these parameters at their default value.

#### Global density

As you probably guessed this controls the overall density of the volumetric fog. Set the value to 0.5 for the 00:00, 05:00, 19:00, 23:59. Add another key with a value of 0.2 at 12:00.

![Image](https://www.cryengine.com/docs/static/attachments/24154245) *Pic27:Global densitycurve setup*

Ramp start/end

They have the same functionality as the corresponding values for the regular fog. No changes required for this particular scenario.

#### Color (atmosphere)

This controls the overall fog color of the atmosphere. Set it to a light blue color for midday like 140, 230, 255. As we get closer to sunset/sunrise this will transition into a darker blue like 90, 148, 164 (Add keys at 06:00 and 18:00).

For night time set this color to pure white at the 00:00, 05:55, 17:55 and 23:59 times. Same as the regular fog bottom color this is used to create the effect of light pollution at the horizon.

![Image](https://www.cryengine.com/docs/static/attachments/24154246) *Pic28: Color (atmosphere)curve setup*

Anisotropy (atmosphere)

This value can only be defined between the -1 to 1 range, however neither the minimum or the maximum values should be used as they create artifacts. Values lower than 0 will shift the fog in the opposite direction from the sun so using these is not recommended for realistic lighting scenarios. A positive value closer to 0 produces a more consistent appearance of the atmospheric fog regardless of the viewing angle in relation to the sun. The default value of 0.2 is appropriate for our scene.

![Image](https://www.cryengine.com/docs/static/attachments/24154249) *Pic29: Anisotropy (atmosphere) going from 0.01 to 0.99 in 0.1 step*

Notice how the fog shifts towards the sun as the value goes up.
Color (sun radial)

Similar to the regular fog radial color this is used to control the color of the glow around the sun.

At 12:00 set this to a light yellow color (199, 183, 119). Change this to orange (184, 111, 64) at sunset/sunrise. The effect produced by this color is also applied to the moon at night time. Since we are already controlling that through the night sky settings we will have to change this color to black at night time to completely remove the effect. Add some keys at 00:00, 05:55, 18:05 and 23:59 and assign them the color black.

![Image](https://www.cryengine.com/docs/static/attachments/24154247) *Pic30: Color (sun radial)curve setup*

Anisotropy (sun radial)

Similar to **Anisotropy (atmosphere)** this value defines the dependency of the glow effect in relation to the sun position. Setting this to a positive low value makes the radial color visible even when looking away from the sun, while using negative numbers the effect will gradually shift to the opposite side of the sun. We will leave this at the default value of 0.95.

![Image](https://www.cryengine.com/docs/static/attachments/24154250) *Pic31: Anisotropy (sun radial)0.95 - 0.05 range*

The sun is behind the camera on the right side. Notice how the radial color transitions from a localized effect to a global one as the value goes down.

#### Radial blend factor

This parameter enables the blending of the sun radial color with the atmospheric color and it can only be set to values between 0 and 1. Setting it to 0 effectively turns off the radial fog. We will leave this at its default value of 1.

![Image](https://www.cryengine.com/docs/static/attachments/24154254) *Pic32: The impact of Radial blend factorset to 0, 0.5 and 1*

Radial blend mode

Controls the method used to blend between atmosphere fog and radial fog.

Blend mode = 0 completely additive blending

Blend mode = 1 completely linear interpolation

We will be using the default mode 0.

#### Color (entities)

It can be used to control the global fog color for volumetric lights other than the sun as well as fog volumes.

#### Anisotropy (entities)

It defines the appearance of volumetric fog entities based on the viewing angle in relation to the sun. Leave this at its default value of 0.6

#### Range

There are two elements that make up the Volumetric Fog in CRYENGINE:

- Ray-marching Volumetric Fog

- Analytical Volumetric Fog

Ray-marching Volumetric Fog handles all types of light and differing fog densities, while analytical Volumetric Fog handles sun light without dynamic shadow and exponential height fog density.

The area near to the camera is covered by ray-marching Volumetric Fog, while everything else is covered by analytical Volumetric Fog.

The radius of this area is controlled via the Range parameter. We will set this at 256 for the whole timeline.

![Image](https://www.cryengine.com/docs/static/attachments/24154255) *Pic33: Range set at 64 and 256*

Notice the difference in quality between the ray-marching volumetric fog and the analytical one.
In-scattering

It controls how much the sun light and any other lights get scattered by the fog. Higher values will make your scene appear foggier (even though the fog density doesn't change) and you will notice an increase in the size and brightness of the glow effects. We will leave this at its default value of 1.

Keep in mind that this parameter has a big impact on the overall illuminance of the scene so it should be used with caution.

![Image](https://www.cryengine.com/docs/static/attachments/24154257) *Pic34: The effect of different In-Scatteringvalues*

The darkening of the ground is a byproduct of the Eye Adaptation trying to balance out the overly brightened sky.

Extinction

This handles the amount of light the fog will absorb making it harder for the sun light to penetrate it. Higher values will produce a thick atmosphere effect. A good use for it would be for creating an underwater scene. For our scene we will set this to 0.15 for the whole timeline.

![Image](https://www.cryengine.com/docs/static/attachments/24154258) *Pic35: Extinction set at different values showing the effect it has on the sun light*

Analytical fog visibility

This controls the global visibility for the analytical fog. Set this to 0.8 for the entire timeline.

#### Finaly density clamp

Similarly to the corresponding option for regular fog this controls the maximum density fog can reach. It can be used to bring back background objects in extremely foggy scenarios.

### Sun Rays Effect

This section contains all the different parameters that control the sun rays effect. The only one we will be changing for this particular scenario is the **Sun rays attenuation.**

#### Sun rays visibility

This value controls the visibility of sun rays. Higher values cause brighter rays around the sun.

#### Sun rays attenuation

This value controls the attenuation of sun rays. Higher values produce shorter sun rays. Set this to 1.5 for the whole timeline.

![Image](https://www.cryengine.com/docs/static/attachments/24154259) *Pic36: The impact of different Sun rays attenuation values*

Sun rays suncolor influence

This value controls how much the sun color contributes to the color of the sun rays. If the parameter is set to 1.0, the sun rays get the color of the sun. If it is set to 0.0, the rays use the custom color. Values in between interpolate between the custom and sun color.

#### Sun rays custom color

This value defines the custom color that will be used by the sun rays if **Sun rays suncolor influence** is set to a value larger than 0.

### Advanced

This section contains the parameters that control the appearance of the ocean. We will be adjusting the **Ocean Fog Color** to reflect the changes in lighting as the time progresses.

#### Ocean Fog Color

This value effectively controls the tint of the ocean surface as well as the color used to create the fog effect when the camera is underwater.

Set this to a blue color like 36, 67, 77 between 08:00 and 16:00 times. this will fade into a darker blue as it nears sunset/sunrise. Set two more keys with the value of 25, 36, 46 at 06:00 and 18:00. For night time we'll be using a dark desaturated green color like 55, 68, 61 so add some keys with this value at 00:00, 05:30, 18:30 and 23:59.

![Image](https://www.cryengine.com/docs/static/attachments/24154260) *Pic37: Ocean Fog Colorcurves setup*

Ocean Fog Color Multiplier

This controls how much of the **Ocean Fog Color** is actually being used by the ocean shader. Setting this to 0 completely removed the color.

#### Ocean Fog Density

This value controls the density of the ocean fog.

#### Skybox multiplier

The effect of this parameter is visible only when using a static sky and it controls the brightness of the skybox being used. Needless to say this does not apply for our scene.

### Volumetric Clouds

Procedural volumetric clouds (r_volumetricClouds 1 in the Console) are a nice way to enhance your level, but particularly nice if you're using a faster-than-normal timelapse style time of day speed. To make the clouds move faster than normal to match the speed of your time of day change, set Variables > Volumetric Clouds > Wind Influence to a value that produces the desired cloud movement speed at the current wind speed (Constants > Wind > Wind Vector).

### Making Time of Day Dynamic

Last but not least, don't forget to use the Curve Editor to set your Playback Speed to a non-zero value, and make sure your Start Time is 00:00 and your End Time is 23:59 for a full 24 hour day/night cycle (or a more limted range of time, as you like).

At this point you should have a full day-night cycle set up to work with both Volumetric Fog and Standard Fog. Hopefully you also have a better understanding of how the Environment Editor works, allowing you to create your own unique lighting setups inside CRYENGINE.

[Helpful Information](#helpful-information)[Curve Editor](#curve-editor)[Dynamic Time of Day and Curve Editor Settings](#dynamic-time-of-day-and-curve-editor-settings)[Initial Setup](#initial-setup)[Setting up the Sun](#setting-up-the-sun)[Sky Light](#sky-light)[Fog](#fog)[Night Sky](#night-sky)[Night Sky Multiplier](#night-sky-multiplier)[Volumetric Fog](#volumetric-fog)[Sun Rays Effect](#sun-rays-effect)[Advanced](#advanced)[Volumetric Clouds](#volumetric-clouds)[Making Time of Day Dynamic](#making-time-of-day-dynamic)
