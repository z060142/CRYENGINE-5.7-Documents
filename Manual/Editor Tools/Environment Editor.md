# Environment Editor

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/56658466
- Page ID: 56658466
- Breadcrumb: Editor Tools > Environment Editor
- Parent: Editor Tools

## Content

##
Overview

The Environment Editor is used to setup different aspects of the environment in the level such as fog, volumetric clouds and the direction and position of the sun for each individual preset in a 24-hours range.

Users can open multiple Environment Editor instances at the same time. However, the Viewport environment settings are determined by the window which is currently on the focus point. If an environment editor is closed, the Viewport settings fall back to the default settings. Only when an Environment Editor window gains focus does it apply its settings to the Viewport.

![Image](https://www.cryengine.com/docs/static/attachments/56658505)

##
1. Menu

The Menu can be accessed by clicking on the
![Image](https://www.cryengine.com/docs/static/attachments/56658510)
 icon on the top-right corner of the Environment Editor. When clicked, it reveals
**
File
**
and
**
Help
**
 sub menus.

##
File

Button

 |
Description

 |

**
New
**

 |
Brings up the Create Environment panel where an environment asset can be created and saved in a folder.

 |

**
Open
**

 |
Allows users to choose an existing environment asset to modify or use in the current level.

The environment asset options can also be accessed
by double-clicking an environment asset
 on the Asset Browser.

 |

**
Close
**

 |
Closes the current environment asset parameters.

 |

**
Save
**

 |
Saves the current environment asset.

 |

**
Recent Files
**

 |
Shows a list of environment assets that were opened recently.

 |

##
Edit

Button

 |
Description

 |

**
Undo
**

 |
Undoes the last action.

 |

**
Redo
**

 |
Redoes a previously undone action.

 |

##
Toolbars

Option

 |
Description

 |

**
Customize...
**

 |
Opens the toolbar customization window allowing users to customize existing toolbars, and/or create new toolbars within this tool.
 |

**
Lock Toolbars
**

 |
When disabled, the positions of toolbars and spacers within this tool can be changed by drag and drop.
 |

**
Spacers
**

 |
The following options allow users to use spacers in positioning their toolbars.

**
Insert Expanding Spacer
**
 |
Adds an expanding spacer to the toolbar layout; an expanding spacer pushes all elements situated at its ends to the edge of a panel.
 |

**
Insert Fixed Spacer
**
 |
Adds a fixed spacer, which has a fixed size of one icon.
 |

The
**
Spacers
**

menu options are only available when

**
Toolbars → Lock Toolbars
**

is disabled.
 |

When a tool has a toolbar, whether this is a default one or a custom one, the options above are also available when right-clicking in the toolbar area (only when a toolbar is already displayed).

##
Window

Reveals the Panels and Reset Layout options.

Button

 |
Description

 |

**
Panels
**

 |
Displays the panels that can be turned on and off:

-
**
Asset Browser
**

-
**
Constants
**

-
**
Curve Editor
**

-
**
Variables
**
 |

**
Reset Layout
**

 |
Resets the tool layout.

 |

##
Help

Opens the documentation page for this tool.

##
2. Asset Browser

Tool-specific Asset Browser panels let users view and edit the assets within the tool that is currently being used. Unlike the stand-alone Asset Browser tool, the assets that are displayed on this panel are pre-filtered by default; meaning it only displays the assets that are relative to the tool itself.

Menu options and their functionalities on both the stand-alone and the tool-specific Asset Browsers are the same and they can be used to achieve the same goal. For more information about the Asset Browser Menu options, please refer to the
[Asset Browser](Asset%20Browser.md)
 page.
When the Sync Selection
![Image](https://www.cryengine.com/docs/static/attachments/56658506)
 button in the toolbar is active, selecting a different asset in a tool-specific Asset Browser will instantly open it. This button makes it very easy to cycle through different assets and edit them on the fly.

##
3. Constants

These settings remain as set by the user no matter what the time of day is (unlike Variables, which can be keyframed and animated).

These options cannot be modified by using the Curve Editor.

##
Sun

Setting

 |
Description

 |

**
Latitude
**

 |
This option can be set to a value between 0 and 360; where 0 means the sun will be shining from the north, 90 means that it will shine from the west, 180 from the south and 270 from the east.

Use this slider when the north position in an imported heightmap is not set to
**
Up
**
 in 2D image.

 |

**
Longitude
**

 |
This setting determines where the level is on the equator. This can be set from 0 to 180, where 0 is on the North Pole, 90 is on the equator and 180 is on the South Pole.

 |

**
Sun Linked to TOD
**

 |
When turned on, the sun will move across the sky when the time of day changes. Disabling this check box means that the user can keep the game at a specified time of day, and fake the sun moving through the sky without updating the time.

 |

##
Moon

Setting

 |
Description

 |

**
Latitude
**

 |
Sets the latitude for the position of the Moon.

 |

**
Longitude
**

 |
Sets the longitude for the position of the Moon.

 |

**
Size
**

 |
Changes the size of the moon.

 |

**
Texture
**

 |
Defines a texture for the moon.

 |

##
Skybox

Setting
 |
Description
 |

**
Material (default-spec)
**
 |
Defines the material for the sky box.
 |

**
Material (low-spec)
**
 |
Defines a material for the sky box that will be available only in low spec.
 |

##
Wind

Setting

 |
Description

 |

**
Wind vector
**

 |
Adjusts the global wind vector. Positive Y values mean how fast the wind moves to north, negative Y south, positive X east, negative X west.

 |

**
Breeze Enabled
**

 |
Turns breeze generation on or off.

 |

**
Breeze Strength
**

 |
Controls the strength of the breeze that is generated.

 |

**
Breeze Variance
**

 |
Adds speed, size, strength etc. variations to the breezes that are generated.

 |

**
Breeze Life Time
**

 |
Controls the maximum time each generated breeze should live for.

 |

**
Breeze Count
**

 |
How many breezes should be generated at once.

 |

**
Breeze Radius
**

 |
Controls the size of the generated breeze.

 |

**
Breeze Spawn Radius
**
 |
From the location of the player, defines the radius where breezes should be allowed to traverse. Smaller numbers will see more centralized breezes pass the player, larger numbers will vary the passes.
 |

**
Breeze Spread
**

 |
High spread values will allow the breezes to travel in more varied directions around the player, but still, follow the general global wind vector direction.

 |

**
Breeze Movement Speed
**

 |
Controls the movement speed of the breeze. Works in conjunction with Breeze Strength. With this option, rapid gusts of wind can be created; however, this would only move the vegetation gently.

 |

**
Breeze Awake Threshold
**

 |
Breeze generator proxies will "wake" sleeping physicalized objects.

 |

**
Breeze Fixed Height
**

 |
Puts the center of the breeze at the defined height above the (z=0)-plane. This is intended for levels without terrain.

 |

##
Cloud Shadows

Using a cloud shadow texture, users can fake the effect of having clouds pass in front of the sun, projecting shadows onto the level below.

Setting

 |
Description

 |

**
Texture
**

 |
Specifies which global shadow texture is cast on the entire level.

 |

**
Speed
**

 |
Specifies a speed at which the cloud shadows texture moves along the X, Y and Z axis. Only X and Y values would have an effect. The Z value does nothing.

 |

**
Tiling
**

 |
Increase this value to tile the texture more densely. Decrease this value to stretch it out more.

 |

**
Brightness
**

 |
Controls the brightness of the cloud shadows.

 |

**
Invert
**

 |
Since this texture should be a simple black / white cloud pattern, enabling this will flip the clouds to use black instead of white.

 |

##
Color Grading

Color Grading lets users choose a color palette to change the environment color based on the desired atmosphere.

Setting
 |
Description
 |

**
Use Static Texture
**
 |
Enable to activate color grading.
 |

**
Texture
**
 |
Choose a color palette in the
**
textures → colorcharts
**
 folder. The possible result can be previewed instantly in the Viewport by simply clicking the browse button and selecting the color palette.

 |

There is a more powerful way to change the color grading via Flow Graph or C++ access to the 3D Engine. Using the
**
ColorGradient
**
node in Flow Graph and setting its
**
Transition Time
**
option to a value
**
higher than 0
**
 would result in a periodic color blending rather than instantly changing it. The blending time is defined by the
**
Transition Time
**
value. To change the color palette instantly, set its value to
**
0
**
.

The CVar
**
r_ColorGradingChartImage
**
has been changed; henceforth, it only changes the current state immediately to one texture, without blending. This means that getting the current static LUT has become obsolete as the blending process is now dynamic.

##
Total Illumination

This Global Illumination (GI) solution, also knows as SVOGI, is based on voxel ray tracing and provides the following effects:

-
Total Illumination

-
Dynamic indirect light bounce from static and majority of dynamic objects.

-
Large-scale AO and indirect shadows from static geometry (vegetation, brushes and terrain).

-
Works without pre-baking and does not require manual setup of many bounce lights or light volumes.
For more information about Global Illumination, see
[Voxel-Based Global Illumination (SVOGI)](../Graphics%20%26%20Rendering/Lighting/Lighting%20Overview/Voxel-Based%20Global%20Illumination%20(SVOGI).md)
 page.

Setting

 |
Description

 |

**
Active
**

 |
Activates Voxel-Based Global Illumination.

 |

**
Injection Multiplier
**

 |
Increases the intensity of the bunce light in the GI from direct light sources (sun, and any lights with GI enabled).

 |

**
Sky Color Multiplier
**

 |
Adjusts the intensity of the skylight. This value may be multiplied with
**
Fog → Color (top)
**
 value in the Variables panel.

 |

**
Use TOD Sky Color
**

 |
Controls how much the
**
Fog → Color (top)
**
 saturates the GI ambient light. A value of

**
0
**

means the sky color will be colorless. A value of

**
1
**

means the color is controlled entirely by the

**
Fog → Color (top)
**
 option
in the Variables panel
.

 |

**
Specular Amplifier
**

 |
Adjusts the output brightness of cone traced indirect specular component.

 |

**
Diffuse Bias
**

 |
Constant ambient value added to Global Illumination. Helps prevent completely black areas. If negative, modulate it with near range AO.

 |

**
Cone Max Length
**

 |
Maximum length of the tracing rays in meters. Shorter rays work faster.

 |

**
Update Geometry
**

 |
When toggled on, it forces single complete re-voxelization of the scene. This is needed if terrain, brushes or vegetation were modified.

 |

**
Min Node Size
**

 |
The size of the smallest SVO node to be created during level voxelization. Smaller values help getting more detailed lighting but may work slower and use more memory in pool. It may be necessary to increase Voxel Pool Resolution in order to prevent running out of voxel pool (see
[below](Environment%20Editor.md#EnvironmentEditor-vpr)
).

 |

**
Low Spec Mode
**

 |
Sets low spec mode. Values greater than 0 simplify shaders and scale down the internal render targets. If set to
**
-2
**
, it will be initialized by the value specified in
**
sys_spec_Light.cfg
**
, on level load.

 |

**
SSAO Amount
**

 |
Allows scaling down SSAO (SSDO) amount and radius when GI is active.

 |

##
Total Illumination Advanced

Setting

 |
Description

 |

**
Integration Mode
**

 |
GI computations may be used in several ways:

**
0
**
 =
**
 AO + Sun bounce
**

      Large scale ambient occlusion (static) modulates or replaces the default ambient lighting.

      Single light bounce (fully real-time) is supported for sun and, with limitations, for projectors.

      This mode takes less memory and only the opacity is voxelized. This also works acceptably on consoles.

**
1 = Diffuse GI mode (experimental)
**

      GI completely replaces the default diffuse ambient lighting.

      Two indirect light bounces are supported for sun and semi-static lights. Use
**
_TI
**
 in light name.

      Single fully dynamic light bounce is supported for projectors. Use
**
_TI_DYN
**
 in light name.

      Default ambient specular is modulated by the intensity of the diffuse GI.

**
2 = Full GI mode (very experimental)
**

      Both ambient diffuse and ambient specular lighting is computed by voxel cone tracing.

      This mode works fine only on high-end modern PCs.

 |

**
Portals Deform
**

 |
Increases the precision of tracing in direction of portals.

 |

**
Portals Inject
**

 |
Injects portal lighting together with direct lights, allows good indoor sky light even with just one indirect bounce.

![Image](https://www.cryengine.com/docs/static/attachments/56658520)

 |

**
Diffuse Amplifier
**

 |
Adjusts the output brightness of cone traced indirect diffuse component.

 |

**
Specular From Diffuse
**

 |
Allows to minimize or completely remove requirement for environment probes by analyzing results of diffuse cone tracing.

-
**
Pros -
**
 Low cost, full screen resolution; no probes needed.

-
**
Cons -
**
 Smooth surfaces like mirrors show very blurry approximation of reflections.
![Image](https://www.cryengine.com/docs/static/attachments/56658519)

 |

**
Number Of Bounces
**

 |
Maximum number of indirect bounces from 0 to 2.
 The first indirect bounce is completely dynamic. The rest of the bounces are cached in SVO and are mostly static.

 |

**
Saturation
**

 |
Controls color saturation of all propagated light.

 |

**
Propagation Booster
**

 |
Controls fading of the light during in -SVO propagation. Values greater than 1 help propagating light further but may bring more light leaking artifacts.

 |

**
Diffuse Cone Width
**

 |
Controls wideness of diffuse cones. Wider cones work faster but may cause over-occlusion and more light leaking.

 |

**
Update Lighting
**

 |
When switched ON, it forces a single full update of SVO lighting.

 |

**
Halfres Kernel Primary
**

 |
Uses fewer rays for secondary bounce for faster update. Difference is only visible when the number of bounces is higher than 1.

 |

**
Halfres Kernel Secondary
**

 |
Uses fewer rays for secondary bounce. This gives a faster update of cached lighting but may reduce the precision of secondary bounce. The difference is only visible when the number of bounces is
**
higher than 1
**
.

 |

**
Use Light Probes
**

 |
If enabled, environment probes lighting is multiplied with GI. If disabled, diffuse contribution of environment probes is ignored. In modes
**
1
**
 or
**
2
**
, it enables usage of global environment probe for skylight instead of
**
Variables → Color (top)
**
 and
**
Color (top) multiplier
**
.

 |

**
Voxelization LOD Ratio
**

 |
Controls distance LOD ratio for voxelization. Bigger values help getting more detailed lighting at distance but may work slower and will use more memory in pool. It may be necessary to increase Voxel Pool Resolution parameter in order to prevent running out of voxel pool.

 |

**
Voxelization Map Border
**

 |
Skips voxelization of geometry close to the edges of the map. In case of offline voxelization this will speed up the export process and reduce data size on disk.

 |

**
Voxel Pool Resolution
**

 |
Size of volume textures (x,y,z dimensions) used for SVO data storage. Valid values are 128 and 256. The engine has to be restarted if this value was modified. Too large pool size may cause long stalls when some GI parameter was changed.

 |

**
Objects Max View Distance
**

 |
Voxelizes only objects with maximum view distance greater than this value. It only affects big and important objects. If set to
**
0
**
, it disables this check and also disables skipping of triangles that are too small. Changes are visible after full re-voxelization. Click
**
Update Geometry
**
 or restart the engine for a full re-voxelization.

 |

**
Sun RSM Inject
**

 |
Enables additional RSM sun injection. Helps getting sun bounces in over-occluded areas where primary injection methods are not able to inject enough sun light. Works only in
**
Low Spec Mode 0
**
.

 |

**
SS Depth Trace
**

 |
Uses SS depth tracing together with voxel tracing.

 |

**
Shadows From Sun
**

 |
Calculates sun shadows using SVO ray tracing. Normally, it is supposed to be used in combination with normal shadow maps and screen space shadows.

 |

**
Shadows Softness
**

 |
Controls softness of ray traced sun shadows if Shadows From Sun is enabled.

 |

**
Shadows From Heightmap
**

 |
Includes terrain heightmap of the whole level into ray-traced sun shadows.

 |

**
Troposphere Active
**

 |
Activates SVO atmospheric effects, it completely replaces the default fog computations. After the activation, the scene needs to be re-voxelized.
Click
**
Update Geometry
**
 or restart the engine for a full re-voxelization.

 |

**
Troposphere Brightness
**

 |
Controls intensity of atmospheric effects.

 |

**
Troposphere Density
**
 |
Controls the density of the atmospheric effects.
 |

**
Analytical Occluders
**

 |
Enables basic support for hand-placed occlusion shapes like boxes, cylinders and capsules. This also enables indirect shadows from characters. Shadow capsules are defined in
**
.chrparams
**
 files.

 |

**
Analytical GI
**

 |
Completely replaces voxel tracing with analytical shape tracing. Light bouncing is supported only in integration mode 0.

 |

**
Trace Voxels
**

 |
Includes voxels into tracing. Allows excluding voxel tracing if only proxies are needed.

 |

**
Stream Voxels
**

 |
Enables streaming of voxel data from disk instead of run-time voxelization. Streaming is only used in the Game Launcher. In the Editor, voxels are always generated at run-time.

If enabled, level export will include voxels pre-computation process which may take up to one hour for big, complex levels.

 |

**
Translucent Brightness
**

 |
Adjusts the brightness of semi-translucent surfaces. Affects mostly vegetation leaves and grass.

 |

**
Point Lights Bias
**

 |
Modulates non-shadowed injection from point lights. This helps simulate multiple bounces.

 |

**
High Gloss Occlusion
**

 |
Normally, the specular contribution of environment probes is corrected by the diffuse GI. This parameter controls the amount of the correction; usually darkening the very glossy and reflective surfaces.

 |

##
4. Variables

This section houses the settings that can be changed with the Curve Editor to the right.

Clicking on a setting will highlight the name in and show a graphical representation of that setting in the bar above the Curve Editor, showing the outcome of the values at different times of the day:

##
Sun

Setting

 |
Description

 |

**
Sun color
**

 |
This RGB value sets the color of the light source used as the sun. Click on the color box next to
**
Sun color
**
 to pick a color manually or enter an RGB value.

 |

**
Sun intensity (lux)
**

 |
Specifies the luminance value of the sun in lux.

 |

**
Sun specular multiplier
**

 |
Controls the specular contribution of the sunlight.

This should always be set to 1 to ensure that the materials work properly based on the Physically Based Shading (PBS) pipeline. For more information, please refer to
[Physically Based Shading (PBS)](../Graphics%20%26%20Rendering/Shaders/Physically%20Based%20Shading%20(PBS).md)
.

 |

##
Skybox

Setting
 |
Description
 |

**
Rotation
**
 |
Rotates the sky box around the X and Y axes.
 |

**
Vrtical stretch
**
 |
Stretches the sky box material and sets the height on the Z axis.
 |

**
Color
**
 |
Defines an additional color for the sky box material.
 |

**
Intensity (lux)
**
 |
Sets the intensity of the sky box luminescence, i.e. brightness.
 |

**
Filter
**
 |
Adds a filter color on the sky box.
 |

**
Opacity
**
 |
Adjusts the opacity of the sky box.
 |

##
Fog

Setting

 |
Description

 |

**
Color (bottom)
**

 |
This controls the bottom color of the vertical gradient used to create the atmospheric fog
.

 |

**
Color (bottom) multiplier
**

 |
The strength of the effect Color (bottom) has on the global fog.

 |

**
Height (bottom)
**

 |
Specifies the height at which the gradient starts.

 |

**
Density (bottom)
**

 |
Density of the fog at the bottom of the gradient. The value range is from 0 to 1 and the default value is 1.

 |

**
Color (top)
**

 |
This controls the top color of the vertical gradient used to create the atmospheric fog.

 |

**
Color (top) multiplier
**

 |
Determines the intensity of the top color.

 |

**
Height (top)
**

 |
Specifies the height at which the gradient ends.

 |

**
Density (top)
**

 |
Density of the fog at the top of the gradient. The value range is 0 to 1 and the default value is 1.

 |

**
Color height offset
**

 |
Shifts the color of the vertical fog gradient towards the top or bottom.
The value range is from -1 to 1 and the default value is 0.

 |

**
Color (radial)
**

 |
Specifies the color of the fog component responsible for producing halos around the sun.

 |

**
Color (radial) multiplier
**
 |
Specifies the intensity of the color used for the radial fog.
 |

**
Radial size
**

 |
Specifies the size of the halo around the sun.
The value range is from 0 to 1 and the default value is 0.75.

 |

**
Radial lobe
**

 |
Specifies how much the radial fog component is affected by distance. The value range is from 0 to 1 and the default value is 0.5.

Small values will make this setting affect the horizon while bigger values will make over glow the scene.

*
Radial Lobe at 0 (sharp horizon)
*
 |
*
Radial Lobe at 0.3 (blurred horizon)
*
 |

![Image](https://www.cryengine.com/docs/static/attachments/56658538)
 |
![Image](https://www.cryengine.com/docs/static/attachments/56658539)
 |

Be aware that if a the Radial Lobe value is too high, it can get projected in front of objects:

*
Radial Lobe at 1
*
 |
*
Radial Lobe at 0
*
 |

![Image](https://www.cryengine.com/docs/static/attachments/56658541)
 |
![Image](https://www.cryengine.com/docs/static/attachments/56658540)
 |

 |

**
Final density clamp
**

 |
Specifies the maximum fog density that is allowed for final blending with the scene.
The value range is 0 to 1 and the default value is 1.

This allows the sky, horizon and other bright distant objects to punch through even if the fog is dense. However, this value shouldn't be set too low. Otherwise the depth perception can get compromised and this will result in implausible visuals and seemingly apparent artifacts especially when moving the camera.

 |

**
Global density
**

 |
This value specifies the global density of the fog. Higher values produce denser fog.

 |

**
Ramp start
**

 |
The ramp values can be used to control the fog density in relation to the camera.

This value sets the distance in meters from the camera at which the fog will start to be rendered at 0 density. The distance value is calculated in meters.

 |

**
Ramp end
**

 |
This defines the distance from the camera at which the fog will be rendered at its maximum density which is defined by the Global Density parameter.

 |

**
Ramp influence
**

 |
This value determines how much the ramp values affect the rendering of the fog.

 |

**
Shadow darkening
**

 |
Affects the way fog looks in shadow areas.

Specifies how much the fog color, computed per pixel via the settings above, is generally darkened based on the volumetric shadow value computed by the engine per pixel.
The value range is from 0 to 1 and the default value is 0.25 where
0 is fully darkened and 1 turns off the effect shadows have on the fog.

The factor is applied after a darkened fog color has been calculated using the sun and ambient darkening factor below.

 |

**
Shadow darkening sun
**

 |
Specifies how much the radial fog color is influenced individually in range from 0 to 1,
where 0 means a lot of influence and 1 means none.
 The default value is 1.

 |

**
Shadow darkening ambient
**

 |
Specifies how much the ambient fog color such as height gradient is influenced individually in range from 0 to 1

where 0 means a lot of influence and 1 means none.
 The default value is 1.

 |

**
Shadow range
**

 |
Specifies how far the volumetric shadows get traced in range from 0 to 1 and the default value is 0.1; that is, up to 10% of the level's far clip plane distance.

Please note that the number of samples per view ray do not increase, hence, smaller values will result in more accurate results but shadows won't cast that far.

 |

##
Volumetric Fog

Volumetric fog is turned off by default. To use Volumetric Fog instead of Fog, use the CVar
**
e_VolumetricFog
**
**
 1
**
 in the console window or add it to the
*
system.cfg
*
 or
*
game.cfg
*
. For further information, please refer to the
[Volumetric Fog](../Graphics%20%26%20Rendering/Lighting/Lighting%20Overview/Volumetric%20Fog.md)
 page.

Setting

 |
Description

 |

**
Height (bottom)
**

 |
Specifies the height at which the gradient starts.

 |

**
Density (bottom)
**

 |
Density of the fog at the bottom of the gradient in range from 0 to 1 and the default is 1.

 |

**
Height (top)
**

 |
Specifies the height at which the gradient ends.

 |

**
Density (top)
**

 |
Density of the fog at the top of the gradient in range from 0 to 1, where default is 0.0001.

 |

**
Global density
**

 |
This value specifies the global density of the fog. Higher values produce denser fog.

 |

**
Ramp start
**

 |
The ramp values can be used to control the fog density in relation to the camera.

This value sets the distance,
in meters,
 from the camera at which the fog will start to be rendered at 0 density.

 |

**
Ramp end
**

 |
This sets the distance from the camera at which the fog will be rendered at its maximum density, set by the Global Density parameter.

 |

**
Color (atmosphere)
**

 |
Specifies the fog albedo color for sun atmosphere scattering.

 |

**
Anisotropy (atmosphere)
**

 |
Adjusts the anisotropy for sun atmosphere scattering. Where 0 is isotropic, 1 is perfect forward, -1 is perfect backward in-scattering.

 |

**
Color (sun radial)
**

 |
Specifies the fog albedo color for sun radial scattering.

 |

**
Anisotropy (sun radial)
**

 |
Adjusts the anisotropy for sun radial scattering. Where 0 is isotropic, 1 is perfect forward, -1 is perfect backward in-scattering.

 |

**
Radial blend factor
**

 |
Adjusts the blend factor of blending sun atmosphere and sun radial scattering.

 |

**
Radial blend mode
**

 |
Adjusts the blend mode factor of blending sun atmosphere and sun radial scattering. Blending is achieved as follows:

**
Sun scattering = ((1.0 - blend factor *
**
blend mode
**
) * sun atmosphere) + (blend factor * sun radial)
**

Blend mode = 0 means completely additive blending:

**
Sun scattering = sun atmosphere + (blend factor * sun radial)
**

Blend mode = 1 means completely linear interpolation:

**
Sun scattering = ((1.0 - blend factor) * sun atmosphere) + (blend factor * sun radial)
**

 |

**
Color (entities)
**

 |
Specifies the global fog albedo color for scatterings of all types of light except the sun.

 |

**
Anisotropy (entities)
**

 |
Adjusts the anisotropy of all participating media, e.g. fog volume, except the global fog. Where 0 is isotropic, 1 is perfect forward, -1 is perfect backward in-scattering.

 |

**
Range
**

 |
Adjusts the maximum distance

of ray-marching Volumetric Fog
in meters
. The out of range is covered by analytical Volumetric Fog. Default setting is 64.

 |

**
In-scattering
**

 |
Adjusts the factor of in-scattering of all participating media.

 |

**
Extinction
**

 |
Adjusts the factor of extinction of all participating media.

 |

**
Analytical fog visibility
**

 |
Adjusts the visibility of analytical Volumetric Fog. Where 0 is no analytical Volumetric Fog, 1 is visible analytical Volumetric Fog.

 |

**
Final density clamp
**

 |
Specifies the maximum fog density that is allowed for final blending with the scene in range from 0 to 1, where default is 1.

This allows the sky, horizon and other bright distant objects to punch through even if the fog is dense.

However, users should be careful not to set this value too low, otherwise the depth perception gets compromised and will result in implausible visuals and seemingly apparent artifacts especially when moving the camera.

 |

##
Sky Light

Setting

 |
Description

 |

**
Sun intensity
**

 |
An RGB value specifying the sun color that is used to compute the atmosphere color.

 |

**
Sun intensity multiplier
**

 |
This value sets the brightness of the sun. It gets multiplied by the sun intensity to yield the overall color.

Higher values will result in brighter skies. Fading down this value during the day time helps simulate an eclipse.

 |

**
Mie scattering
**

 |
This parameter sets the Mie scattering constant. Mie scattering is caused by aerosols in the lower atmosphere up to 1 km.

It is wavelength independent and responsible for haze and halos around the sun on foggy days.

Smaller values result in a clearer sky and bigger values make the sky appear hazier. The default value for the Mie scattering constant is 4.8.

Mie scattering constant of 2.0
 |
Mie scattering constant of 100.0
 |
Mie scattering constant of 2000.0
 |

![Image](https://www.cryengine.com/docs/static/attachments/56658526)
 |
![Image](https://www.cryengine.com/docs/static/attachments/56658525)
 |
![Image](https://www.cryengine.com/docs/static/attachments/56658524)
 |

 |

**
Rayleigh scattering
**

 |
This parameter specifies the Rayleigh scattering constant. Rayleigh scattering is caused by particles in the atmosphere, up to 8 km, and is wavelength dependent. With a default value around 2.0, it produces typical earth-like sky colors; blue sky during the day, reddish/yellowish colors at sun set. Higher values cause a denser atmosphere, with sky colors shifting towards red and yellow. Smaller values produce a bluer sky.

Rayleigh scattering constant of 2.5
 |
Rayleigh scattering constant of 4.8
 |

![Image](https://www.cryengine.com/docs/static/attachments/56658502)
 |
![Image](https://www.cryengine.com/docs/static/attachments/56658501)
 |

 |

**
Sun anisotropy factor
**

 |
The anisotropy factor controls the appearance of the sun in the sky. The closer this value gets to -1.0, the sharper and smaller the sun spot will be.

Higher values cause more fuzzy and bigger sun spots. The default value is -0.995.

Sun anisotropy constant of -0.999
 |
Sun anisotropy constant of -0.8
 |

![Image](https://www.cryengine.com/docs/static/attachments/56658500)
 |
![Image](https://www.cryengine.com/docs/static/attachments/56658499)
 |

 |

**
Wavelength R, G, and B
**

 |
This triple values defines the wavelengths of the RGB primaries
in NM (nautical miles)
. Tweaking these values will shift the colors of the resulting gradients and produce different kinds of atmospheres. This can be very useful in combination with Rayleigh scattering if a sun intensity of pure, bright white is chosen.

RGB=(650.0, 570.0, 475.0)

 |
RGB=(750.0, 601.0, 555.0)
 |

![Image](https://www.cryengine.com/docs/static/attachments/56658498)
 |
![Image](https://www.cryengine.com/docs/static/attachments/56658497)
 |

 |

##
Night Sky

Setting

 |
Description

 |

**
Horizon color
**

 |
This RGB value that is scaled by the multiplier specifies the horizon color of the night sky gradient. For more information,
see the Night Sky Multiplier section below.

 |

**
Zenith color
**

 |
This RGB value that is scaled by the multiplier specifies the zenith color of the night sky gradient.
For more information,
see the Night Sky Multiplier section below.

 |

**
Zenith shift
**

 |
This value shifts the night sky gradient. Small values shift it more towards the bottom. Higher values shift it towards the top.

A zenith shift of 0.2
 |
A zenith shift of 0.8
 |

![Image](https://www.cryengine.com/docs/static/attachments/56658496)
 |
![Image](https://www.cryengine.com/docs/static/attachments/56658495)
 |

 |

**
Star intensity
**

 |
This value controls the overall brightness of the stars.

Please note that the flickering of stars due to atmosphere turbulence is completely procedural and cannot be controlled.

 |

**
Moon color
**

 |
This RGB value that is scaled by the multiplier specifies the moon's emissive color.
For more information,
see the Night Sky Multiplier section below.

 |

**
Moon inner corona color
**

 |
This RGB value that is scaled by the multiplier specifies the color of the moon's inner corona.
For more information,
see the Night Sky Multiplier section below.

 |

**
Moon inner corona scale
**

 |
This value controls the size and blurriness of the moon's inner corona. Smaller values will produce a bigger, blurry corona whereas higher values will produce a smaller, more focused corona.

 |

**
Moon outer corona color
**

 |
This RGB value that is scaled by the multiplier specifies the color of the moon's outer corona.
For more information,
see the Night Sky Multiplier section below.

 |

**
Moon outer corona scale
**

 |
This value controls the size and blurriness of the moon's outer corona. Smaller values will produce a bigger, blurry corona whereas higher values will produce a smaller, more focused corona.

Different moon corona inner and outer scales:

Inner = 0.5, Outer = 0.01
 |
Inner = 0.5, Outer = 0.5
 |
Inner = 1.5, Outer = 0.05
 |

![Image](https://www.cryengine.com/docs/static/attachments/56658494)
 |
![Image](https://www.cryengine.com/docs/static/attachments/56658493)
 |
![Image](https://www.cryengine.com/docs/static/attachments/56658492)
 |

 |

##
Night Sky Multiplier

Setting

 |
Description

 |

**
Horizon color
**

 |
Changes the intensity of the color of the horizon.

 |

**
Zenith Color
**

 |
Changes the intensity of the color of the zenith.

 |

**
Moon Color
**

 |
Changes the intensity of the color of the moon used in the level.

 |

**
Moon inner corona color
**

 |
Changes the intensity of the color of the moon's inner corona.

 |

**
Moon outer corona color
**

 |
Changes the intensity of the color of the moon's outer corona.

 |

##
Cloud Shading

Setting

 |
Description

 |

**
Sun contribution
**

 |
This value specifies how much the sunlight affects the cloud brightness.

 |

**
Sky contribution
**

 |
This value specifies how much the sky light affects the cloud brightness.

 |

**
Sun custom color
**

 |
Gives the user the option to use a custom color for the sunlight.

 |

**
Sun custom color multiplier
**

 |
Affects the intensity of the
**
Sun custom color
**
 on the clouds.

 |

**
Sun custom color influence
**

 |
A value of 0 uses the global color of the sun (specified in
**
Sun → Sun color
**
 in the Environment Editor), a value of 1 enables it. Any value in-between blends between the two colors.

 |

##
Volumetric Clouds

Volumetric Clouds is turned off by default. To use Volumetric Clouds, set the CVar
**
r_VolumetricClouds
**
to
**
 1
**
or
**
 2
**
 in the console window or by adding them to the
*
system.cfg
*
 or
*
game.cfg
*
.
For further information, please see the
[Procedural Volumetric Clouds](../Graphics%20%26%20Rendering/Lighting/Lighting%20Overview/Procedural%20Volumetric%20Clouds.md)
 page.

Setting

 |
Description

 |

**
Global cloudiness
**

 |
Adjusts the global cloudiness of volumetric clouds.

 |

**
Clouds altitude
**

 |
Adjusts the altitude of the bottom of volumetric clouds.

 |

**
Clouds thickness
**

 |
Adjusts
the vertical thickness of volumetric clouds.

 |

**
Clouds edge turbulence
**

 |
Adjusts
the turbulence intensity on the edge region of volumetric clouds.

 |

**
Clouds edge threshold
**

 |
Adjusts
the density threshold of the edge region of volumetric clouds.

 |

**
Sun single scattering multiplier
**

 |
Adjusts
the multiplier for the amount of the sun lighting of single scattering in one scattering event.

 |

**
Sun low-order scattering multiplier
**

 |
Adjusts
the multiplier for the amount of the sun lighting of low-order multiple scattering in 2 to 30 scattering events.

 |

**
Sun low-order scattering anisotropy
**

 |
Adjusts
the amount of low-order multiple scattering and determines if the light is scattered forwards or backwards. Low-order multiple scattering is approximated by Schlick's phase function. This determines the average direction of the scattering light. A value of 1 means completely forward scattering, 0 means scattered in all directions, -1 means completely backward scattering.

 |

**
Sun high-order scattering multiplier
**

 |
Adjusts
the multiplier for the amount of the sun lighting of high-order multiple scattering in more than 30 scattering events.

 |

**
Sky lighting multiplier
**

 |
Adjusts
the multiplier for the amount of the sky lighting. The sky lighting is treated as high-order multiple scattering.

 |

**
Ground lighting multiplier
**

 |
Adjusts
the multiplier for the amount of the ground lighting which illuminates clouds from the ground. The ground lighting is treated as high-order multiple scattering.

 |

**
Ground albedo
**

 |
Adjusts
the average albedo color of the ground.

 |

**
Multi-scattering attenuation
**

 |
Adjusts
the attenuation factor for high-order multiple scattering light. When this value is increased, the light becomes less attenuated when it travels in clouds, and thus clouds look brighter.

 |

**
Multi-scattering preservation
**

 |
Adjusts
the amount of light of high-order multiple scattering coming out from clouds after infinite scattering events.

Multiple scattering light which came out from clouds increases along with the distance which the light travels in clouds. This determines the maximum amount of it. If it's set to 0.5, up to 50 percent of the light comes out from clouds after infinite scattering events.

 |

**
Powder shading effect
**

 |
Adjusts
the powder effect factor for shading clouds. It gets darker according to
 the thickness of clouds
.

 |

**
Absorption percentage
**

 |
Adjusts
the percentage ratio of absorption factor against scattering factor of clouds. Increasing this makes clouds look darker.

 |

**
Atmospheric albedo
**

 |
Adjusts
the albedo color of atmospheric participating media.

 |

**
Atmospheric scattering
**

 |
Adjusts
the intensity multiplier of atmospheric scattering. The luminance of atmospheric scattering changes corresponding to the sun intensity.

 |

**
Wind influence
**

 |
Adjusts
the influence of wind determined in Level Settings.

 |

##
Sun Rays Effect

Setting

 |
Description

 |

**
Sun shafts visibility
**

 |
**
DEPRECATED -
**
 This value controls the visibility of sun shafts.

Higher values accentuate the shadow streaks that are caused by the sun light penetrating objects.

 |

**
Sun rays visibility
**

 |
This value controls the visibility of sun rays. Higher values cause brighter rays around the sun.

 |

**
Sun rays attenuation
**

 |
This value controls the attenuation of sun rays. Higher values cause shorter rays around the sun:

![Image](https://www.cryengine.com/docs/static/attachments/56658491)

*
Sun rays attenuation
*

 |

**
Sun rays suncolor influence
**

 |
This value controls how much of the sun color contributes to the color of the sun rays.

If the parameter is set to 1.0, the sun rays get the color of the sun. If it is set to 0.0, the rays use a custom color. Values in between interpolate between the custom and sun color.

 |

**
Sun rays custom color
**

 |
This value specifies a custom color for the sun rays.

Sun shafts and sun rays combined, with the following values; these values are, from the left to the right,
**
sun shafts visibility/sun rays visibility/sun rays attenuation
**
:

0.0/0.0/1.0
 |
1.0/0.0/1.0
 |
1.0/2.0/1.0
 |
1.0/2.0/0.5
 |

![Image](https://www.cryengine.com/docs/static/attachments/56658490)
 |
![Image](https://www.cryengine.com/docs/static/attachments/56658489)
 |
![Image](https://www.cryengine.com/docs/static/attachments/56658488)
 |
![Image](https://www.cryengine.com/docs/static/attachments/56658487)
 |

 |

##
Advanced

Setting

 |
Description

 |

**
Ocean fog color
**

 |
This RGB color specifies the ocean fog color for a specific time of day.

 |

**
Ocean fog color multiplier
**

 |
This parameter controls the brightness of the ocean fog and is multiplied by the ocean fog color.

 |

**
Ocean fog density
**

 |
This value controls the density of the ocean fog.

 |

##
Obsolete

The settings under this variable are deprecated.

##
HDR

Setting

 |
Description

 |

**
Film curve shoulder scale
**

 |
Controls the slope at the tip of the curve; modifies bright values.

 |

**
Film curve midtones scale
**

 |
Controls the linearity of the middle of the curve; modifies grey values.

 |

**
Film curve toe scale
**

 |
Controls the slope at the base of the curve; modifies dark values.

 |

**
Film curve whitepoint
**

 |
Sets the value to be mapped as pure white in the tone mapped image. The recommended value for this parameter is 4.

 |

**
Saturation
**

 |
Color saturation before tone-mapping.

 |

**
Color balance
**

 |
HDR Color balance to control overall color of the scene.

 |

**
EV Min
**

 |
Controls how brightly the image will expose in areas of low illuminance, e.g. dark interiors.

 |

**
EV Max
**

 |
Controls how dim the image will expose to in areas of high illuminance, e.g. bright exteriors.

 |

**
EV Auto compensation
**
 |
Provides more control over the scene exposure. By default, the scene tries to expose to a mid-grey value. This option can be useful when a slightly over/underexposed scene is aimed for.
 |

**
Bloom amount
**

 |
Controls the amount of bloom that comes from glowing/lit objects.

 |

##
Filters

Setting

 |
Description

 |

**
Grain
**

 |
This parameter applies a grain filter to the final image.

In previous versions, this parameter was bugged and in certain situations would randomly display or hide the grain filter. If this behavior is to be used in a project, it can be turned back on with the CVar
**
r_GrainEnableExposureThreshold.
**

 |

**
Photofilter color
**

 |
This parameter applies a color filter to the final image.

 |

**
Photofilter density
**

 |
This parameter controls the strength of the photo color filtering.

 |

##
Depth Of Field

Setting

 |
Description

 |

**
Focus Range
**

 |
This parameter specifies at what distance the background begins to become blurry when it is out of focus.

 |

**
Blur Amount
**

 |
This parameter controls how strong the areas that are out of focus are blurred.

 |

##
Shadows

The parameters in this section give the user a control over the sun's cascaded shadow map bias settings at different ranges. It does not affect point lights.

Bias settings can be defined per light in the light properties.

CRYENGINE supports multiple cascades. Cascade 0 is the closest to the camera, cascade 1 is the farthest, etc. The higher the cascade, the lower the precision of the shadows, i.e. lower resolution for higher cascades.

Shadow map acne is usually visible at medium range on the 3rd and 4th cascade especially. To prevent shadow map artifacts, the sun shadows bias and slope bias settings are exposed in the time of day.

![Image](https://www.cryengine.com/docs/static/attachments/56658486)

*
Cascaded Sun Shadow Map
*

Setting

 |
Description

 |

**
Bias
**

 |
Moves the shadow cascade toward or away from the shadow-casting object(s).

 |

**
Slope Bias
**

 |
Allows the user to adjust the gradient, slope-based bias used to compute the shadow bias.

 |

**
Shadow jittering
**

 |
Customizes the sharpness of the shadows.

 |

##
Shadow Bias

The lower the Bias value, the more connected the shadows will be to the shadow caster.

In most cases, the Bias value should be kept as low as possible to ensure a proper connection between the shadow and the shadow caster. Values between 0.01 and 0.05 offer the best outcome.

Below, it can be perceived the shadow cast by the sphere moves as its Bias is changed
:

Bias = 0

 |
Bias = 0.05

 |

![Image](https://www.cryengine.com/docs/static/attachments/56658484)
q

 |
![Image](https://www.cryengine.com/docs/static/attachments/56658483)

 |

Bias = 1

 |
Bias = 5

 |

![Image](https://www.cryengine.com/docs/static/attachments/56658482)

 |
![Image](https://www.cryengine.com/docs/static/attachments/56658481)

 |

##
Shadow Slope Bias

The higher the Slope Bias, the less shadows will be cast from surface with a high angle of incidence of the light.

In most cases, the Slope Bias should be kept at a fairly high value, to remove the artifacts usually produced by the low shadow bias. Values between 32 and 64 offer the best outcome.

Slope Bias = 8

 |
Slope Bias = 32

 |

![Image](https://www.cryengine.com/docs/static/attachments/56658475)

 |
![Image](https://www.cryengine.com/docs/static/attachments/56658478)

 |

Slope Bias = 64

 |
Bias = 0.025 / Slope Bias = 32

 |

![Image](https://www.cryengine.com/docs/static/attachments/56658479)

 |
![Image](https://www.cryengine.com/docs/static/attachments/56658485)

 |

In the last image above, a compromise was made between Bias of 0.025 and Slope Bias of 32. Some artifacts are visible, but the self shadowing is better overall.

There is no "one-size-fits-all" setting for shadow cascades. It depends on the assets, position of sun, lighting conditions, etc. Tweak these settings depending on the desired outcome and keep in mind that they have little to no impact on performance.

##
Shadow Jittering

Shadow Jittering can be defined through the Environment Editor, as well as the
**
r_ShadowJittering
**
 CVar, to give the user the control over shadow sharpness.

Note that the more jittering that is used, the heavier on performance it is.

Shadow Jittering = 2.5 (default)

 |
Shadow Jittering = 1

 |
Shadow Jittering = 10

 |

![Image](https://www.cryengine.com/docs/static/attachments/56658473)

 |
![Image](https://www.cryengine.com/docs/static/attachments/56658472)

 |
![Image](https://www.cryengine.com/docs/static/attachments/56658471)

 |

##
ShadowsAutoBias

This CVar Provides a mode that attempts to automatically compute an optimal shadow bias.

Cvar/Command

 |
Description

 |
Comment and examples

 |

**
e_ShadowsAutoBias
**

 |
0: Deactivated

1.0: Good default value

 |
Activates feature and acts as a scale for the computed bias.

 |

##
Deprecated

This section parameters are deprecated.

##
5. Curve Editor

In the Curve Editor, a visual representation of the changes that has been made in the aforementioned options are displayed. With this panel, it is possible to view the progression of the values for the selected setting over the course of one day and how gradually they change over time.

![Image](https://www.cryengine.com/docs/static/attachments/56658470)

The Curve Editor is comprised of the following sections:

##
Toolbar

The Curve Editor has its own toolbar:

![Image](https://www.cryengine.com/docs/static/attachments/56658469)

Button

 |
Name

 |
Description

 |

**
1
**

 |
**
Set in and out tangent to auto
**

 |
Sets the tangents for the selected key(s) (the squares in the graph) to auto.

 |

**
2
**

 |
**
Set in tangent to zero
**

 |
Sets the in tangent for the selected key(s) (the squares in the graph) to zero.

 |

**
3
**

 |
**
Set in tangent to step
**

 |
Sets the
in
tangent for the selected key(s) (the squares in the graph) to step.

 |

**
4
**

 |
**
Set in tangent to linear
**

 |
Sets the
in
tangent for the selected key(s) (the squares in the graph) to linear.

 |

**
5
**

 |
**
Set out tangent to zero
**

 |
Sets the out tangent for the selected key(s) (the squares in the graph) to zero.

 |

**
6
**

 |
**
Set out tangent to step
**

 |
Sets the
out
tangent for the selected key(s) (the squares in the graph) to step.

 |

**
7
**

 |
**
Set out tangent to linear
**

 |
Sets the
out
tangent for the selected key(s) (the squares in the graph) to linear.

 |

**
8
**

 |
**
Fit curves horizontally
**

 |
Fits the graph into the graph window horizontally.

 |

**
9
**

 |
**
Fit curves vertically
**

 |
Fits the graph into the graph window vertically.

 |

**
10
**

 |
**
Break tangents
**

 |
Sets the tangents for the selected key(s) (the squares in the graph) to auto.

 |

**
11
**

 |
**
Unify tangents
**

 |
Sets the tangents for the selected key(s) (the squares in the graph) to auto.

 |

**
12
**

 |
**
Copy curve content
**

 |
Copies the curves in the current graph to the clipboard.

 |

**
13
**

 |
**
Paste curve content
**

 |
Pastes the previously copied curves from the clipboard to the current graph.

 |

##
Ruler

The Ruler can be found at the top of the panel:

![Image](https://www.cryengine.com/docs/static/attachments/56658468)

This ruler shows the time of day at the triangular arrow. Dragging this arrow back and forth will change the time of day in the level and add the effects that the settings have in real-time to the Viewport.

When selecting a color, the colored ribbon attached to the bottom of the ruler shows a preview of that color over a 24-hour period, showing how that color changes over the course of a day.

##
Values

On the left of the graph, values that correspond with the setting that is selected in the Settings Window can be displayed.

##
Graph

The actual graph is interactive as well; a key will appear where a value starts changing:

![Image](https://www.cryengine.com/docs/static/attachments/56658467)

These squares can be selected by clicking on them or dragging a selection box around them. Then, they can be dragged around, which will change the settings in the Settings Window that are related to the selected line. Once again, the changes will be displayed in real-time in the Viewport.

Also, a new key can be created by double clicking on a line.

Holding Shift will let users move the keys horizontally or vertically in a straight line.

##
Time Options

Time Options can be found at the bottom of the Graph:

![Image](https://www.cryengine.com/docs/static/attachments/56658504)

Option

 |
Description

 |

**
Start
**

 |
Initial time that will be used when the mission is started.

If this value is not set correctly, the Time of Day will not be set accordingly in pure-game mode.

If the Current Time is set to 07:00 and Start Time is set to 12:00, it will be 12:00 in pure-game mode and 07:00 in Sandbox.

 |

**
Current
**

 |
Displays the current time that is being edited.

 |

**
Stop
**
**
Button
**

 |
Stops the playback of the Time Of Day sequence in the Editor.

 |

**
Play
**
**
Button
**

 |
Starts or resumes the playback of the Time Of Day sequence in the Editor.

If the current time is not within the specified time range, which is between the start and end time, frame playback begins at the specified start time.

 |

**
Speed
**

 |
Speed at which the time advances, where a value of 1 means an hour of game time passes per second of real time.

 |

**
End
**

 |
End time that will be used for the mission. When the end time is reached, the time will loop, starting the next Time of Day cycle at the Start Time.

 |

##
Environment Assets

As of release 5.6, the File View section is removed from the Environment Editor's default layout. Henceforth, users can create and modify environment assets through the Asset Browser.

Just like any other asset in CRYENGINE, environment assets house specific value types. The environment assets can be used to manipulate the visual aspects of the level such as the time of the day, volumetric clouds, shadows etc.

##
Creating and Using Environment Assets

New assets can be created by right-clicking on an empty space in the Asset Browser and choosing
**
New → Environment
**
. Double-clicking on an environment asset on the Asset Browser would bring up a new editor instance and apply its parameters to the current level even if the
**
Instant Editing Button
**
 is off.

You can right click on an environment asset to bring up the context menu. Then, by choosing the
**
Set as Default for this Level
**
option, you can set an environment asset as default. It is also possible to preview the asset results through the
**
Preview Environment Setting
**
option.

Alternatively, dragging and dropping an environment asset into the Viewport would manipulate the environment based on its parameters and set it as the default environment asset:

![Image](https://www.cryengine.com/docs/static/attachments/56658513)

Setting an Environment Asset as default by either dragging and dropping it into the Viewport or choosing
**
Set as Default for this Level
**

after right clicking on it adds it to the

**
Environment Presets
**

tab on the
**
Level Settings
**
 panel. This tab can be used to manage the list of environment assets that are assigned to the level. For more information about the
**
Environment Presets

**
tab, please refer to the

[Level Settings](Level%20Editor%20Tab/Level%20Settings.md)

section.
[1. Menu](#1-menu)
[2. Asset Browser](#2-asset-browser)
[3. Constants](#3-constants)
[4. Variables](#4-variables)
[5. Curve Editor](#5-curve-editor)
[Environment Assets](#environment-assets)
**
Related content
**
:

[Environment](/docs)
[Tutorials](../Tutorials/Graphics/Environment%20Tutorials.md)

[Lighting Tutorials](../Tutorials/Graphics/Lighting%20Tutorials.md)
