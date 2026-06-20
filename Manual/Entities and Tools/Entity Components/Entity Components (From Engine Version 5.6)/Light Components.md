# Light Components

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/44966059
- Page ID: 44966059
- Breadcrumb: Entities and Tools > Entity Components > Entity Components (From Engine Version 5.6) > Light Components
- Parent: Entity Components (From Engine Version 5.6)

## Content

##
Environment Probe

With the Environment Probes Components you have the ability to place cubemaps throughout the level. It is very useful especially with reflective materials because it will automatically assign the cubemap to anything within its radius.

Property
 |
Description
 |

**
Environment Probe Settings
**
 |
Setting
 |
Description
 |

**
Active
**
 |
Determines whether the environment probe is enabled.
 |

**
Box Size
**
 |
Size of the area the probe affects.
 |

 |

**
Options
**
 |
Setting
 |
Description
 |

**
IgnoreVisAreas
**
 |
Whether to ignore vis areas placed in the level.
 |

**
Sort Priority
**
 |
Sorting priority, used to resolve depth issues with other light sources.
 |

**
Maximum Attenuation Falloff
**
 |
Maximum Attenuation Falloff.
 |

**
Affect Volumetric Fog
**
 |
Whether this probe will affect volumetric fog.
 |

**
Only Affect Volumetric Fog
**
 |
Whether this probe will
**
only
**
 affect volumetric fog.
 |

**
Only Affect This Area
**
 |
Whether this probe will
**
only
**
 affect the area it is currently in.
 |

**
Use Box Projection
**
 |
Whether to use box projection for this environment probe.
 |

 |

**
Color
**
 |
Setting
 |
Description
 |

**
Color
**
 |
Color for the probe.
 |

**
Diffuse Multiplier
**
 |
Diffuse color multiplier for the probe.
 |

**
Specular Multiplier
**
 |
Specular color multiplier for the probe.
 |

 |

**
Generation Parameters
**
 |
Setting
 |
Description
 |

**
Cube Map Path
**
 |
Path to the cube map to load.
 |

**
Load Texture Automatically
**
 |
Whether to attempt loading a texture when the environment probe is created.
 |

**
Resolution
**
 |
Resolution of the probe (Editor only).
 |

**
Generate
**
 |
Generates a cube map with the specified resolution (Editor only).
 |

 |

##
Point Light

The Point Light adds a light source to the entity which emits light in all directions, it behaves like a light bulb in the real world and ca be used as area lights.

Property
 |
Description
 |

**
Point Light Settings
**
 |
Setting
 |
Description
 |

**
Active
**
 |
Determines whether the point light is enabled.
 |

**
Radius
**
 |
Determines the range of the point light.
 |

**
View Distance
**
 |
The maximum view distance of the point light.
 |

 |

**
Optics
**
 |
Setting
 |
Description
 |

**
Enable
**
 |
Enables the Optics options.
 |

**
Lens Flare Name
**
 |
Defines the Lens Flare Effect to be used on the entity.
 |

**
Attach To Sun
**
 |
Attaches the Lens Flare Effect to the sun to simulate a sun oriented flare effect.
 |

**
Flare Field of View
**
 |
Defines the field of view of the Lens Flare Effect that has been assigned to the entity.
 |

 |

**
Color
**
 |
Setting
 |
Description
 |

**
Color
**
 |
Color of the point light.
 |

**
Diffuse Multiplier
**
 |
Diffuse color multiplier for the point light.
 |

**
Specular Multiplier
**
 |
Specular color multiplier for the point light.
 |

 |

**
Shadows
**
 |
Setting
 |
Description
 |

**
Minimum Shadow Graphics
**
 |
Minimum graphical setting to cast shadows.
 |

**
Shadow Bias
**
 |
Moves the shadow cascade toward or away from the shadow-casting object.
 |

**
Shadow Slope Bias
**
 |
Adjusts the slope-based gradient bias used to calculate the shadow bias.
 |

**
Shadow Resolution Scale
**
 |
Adjusts the shadow resolution. The
**
Radius
**
 value is multiplied by this value.
 |

**
Shadow Min Update Radius
**
 |
Defines the minimum radius between the light source and the player camera where the Shadow Update Ratio setting will be ignored.
 |

**
Shadow Min Resolution
**
 |
Specifies the percentage of the shadow pool the light should use for its shadows. The default should be used for the best performance, unless a different value is specifically required.
 |

**
Shadow Update Ratio
**
 |
Defines the update ratio for shadow maps cast from this light. The lower the value (example 0.01), the less frequent the updates will be and the more the shadow will stutter.

This setting should be enabled or disabled depending on the Shadow Min Update Radius value and how far the player camera is from the light source.

This will not work in very high spec as Shadow Caching is disabled.
 |

 |

**
Options
**
 |
Setting
 |
Description
 |

**
Attenuation Bulb Size
**
 |
Controls the falloff exponentially from the origin. A value of 1 means that the light is at full intensity (within a 1 meter ball) before it begins to falloff. See
[/docs/static/engines/cryengine-5/categories/23756816/pages/26215193](
Attenuation and Falloff
)
 for more information.
 |

**
Ignore VisAreas
**
 |
Whether the light source ignores VisAreas in the level.
 |

**
Affect Volumetric Fog
**
 |
Whether the light source should affect volumetric fog.
 |

**
Only Affect Volumetric Fog
**
 |
Whether the light source will
**
only
**
 affect volumetric fog.
 |

**
Only Affect This Area
**
 |
Whether the light source will
**
only
**
 affect the area it is currently in.
 |

**
Link To Sky Color
**
 |
Whether this light should consider the sky color.

When enabled, this setting automatically shifts the color value to match the sun color value, and is hence good to provide an ambient fill that seamlessly shifts no matter the time of the scene you are in.

 |

**
Ambient
**
 |
Makes the light behave like an ambient light source, with no point of origin.
 |

**
Fog Radial Lobe
**
 |
Adjusts the blend ratio of the main radial lobe (parallel to the eye ray) and side radial lobe (perpendicular to the eye ray). The direction of the main radial lobe depends on the Anisotropic parameter value used (found in the Time of Day dialog window).
 |

**
Global Illumination
**
 |

-
**
Disabled -
**
 Light does not affect GI.

-
**
Static -
**
 Light produces light bounces and (in modes 1-2) supports multiple bounces.

-
**
Dynamic -
**
 Light produces single completely real-time bounce.

-
**
Hide if GI is Active -
**
 Light is deactivated if GI is active.
 |

 |

**
Animations
**
 |
Setting
 |
Description
 |

**
Style
**
 |
The animation style of the light.
 |

**
Speed
**
 |
The animation speed of the light.
 |

 |

**
Shape
**
 |
Setting
 |
Description
 |

**
Shape
**
 |
Defines the shape of the light source. The shapes that can be assigned to a light source are as follows;

-
**
Point
**

-
**
Rectangle
**

-
**
Disk
**
 |

**
Two Sided
**
 |
When enabled, makes the light shine in two opposite directions instead of one.

 |

**
Texture
**
 |
File input for the texture to be used to shape the light.

The texture format needs to be
**
BC4 / 512x512
**
 and it is only supported for rectangular lights. A texture can also be used to shape the light in a fog volume.
 |

**
Width/Height
**
 |
Controls the width and height of the light source shape.
 |

 |

##
Projector Light

The Projector Light Component adds a light to entity which projects/emits light in a certain direction based on projection texture. Typical used for a flashlight as an example.

Property
 |
Description
 |

**
Projector Light Settings
**
 |
Setting
 |
Description
 |

**
Active
**
 |
Determines whether the projector light is enabled.
 |

**
Range
**
 |
Determines the range of the projector light.
 |

**
Angle
**
 |
Determines the angle/field of view of the projector light.
 |

 |

**
Projector Options
**
 |
Setting
 |
Descripton
 |

**
Near Plane
**
 |
Determines the distance from the light itself and where it will start projecting.
 |

**
Projected Texture
**
 |
The texture to project.
 |

**
Material
**
 |
The material to project.
 |

 |

**
Optics
**
 |
Setting
 |
Description
 |

**
Enable
**
 |
Enables the Optics options.
 |

**
Lens Flare Name
**
 |
The Lens Flare Effect to be used on the entity.
 |

**
Attach To Sun
**
 |
Attaches the Lens Flare Effect to the sun to simulate a sun oriented flare effect.
 |

**
Flare Field of View
**
 |
Defines the field of view of the Lens Flare Effect that has been assigned to the entity.
 |

 |

**
Color
**
 |
Setting
 |
Description
 |

**
Color
**
 |
Color of the projector light source.
 |

**
Diffuse Multiplier
**
 |
Diffuse color multiplier for the projector light source.
 |

**
Specular Multiplier
**
 |
Specular color multiplier of the projector light source.
 |

 |

**
Shadows
**
 |
Setting
 |
Description
 |

**
Minimum Shadow Graphics
**
 |
Minimum graphical setting to cast shadows
 |

**
Shadow Bias
**
 |
Moves the shadow cascade toward or away from the shadow-casting object.
 |

**
Shadow Slope Bias
**
 |
Adjusts the slope-based gradient bias used to calculate the shadow bias.
 |

**
Shadow Resolution Scale
**
 |
Adjusts the shadow resolution. The
**
Radius
**
 value is multiplied by this value.
 |

**
Shadow Min Update Radius
**
 |
Defines the minimum radius between the light source and the player camera where the Shadow Update Ratio setting will be ignored.
 |

**
Shadow Min Resolution
**
 |
Specifies the percentage of the shadow pool the light should use for its shadows. The default should be used for the best performance, unless the otherwise is specifically required.
 |

**
Shadow Update Ratio
**
 |
Defines the update ratio for shadow maps cast from this light. The lower the value (example 0.01), the less frequent the updates will be and the more the shadow will stutter.

This setting should be enabled or disabled depending on the Shadow Min Update Radius value and how far the player camera is from the light source.

This will not work in very high spec as Shadow Caching is disabled.
 |

 |

**
Options
**
 |
Setting
 |
Description
 |

**
Attenuation Bulb Size
**
 |
Controls the falloff exponentially from the origin. A value of 1 means that the light is at full intensity (within a 1 meter ball) before it begins to falloff. See Attenuation and Falloff for more information.
 |

**
Ignore VisAreas
**
 |
Whether the light source ignores VisAreas in the level.
 |

**
Affect Volumetric Fog
**
 |
Whether the light source should affect volumetric fog.
 |

**
Only Affect Volumetric Fog
**
 |
Whether the light source will
**
only
**
 affect volumetric fog.
 |

**
Only Affect This Area
**
 |
Whether the light source will
**
only
**
 affect the area it is currently in.
 |

**
Link To Sky Color
**
 |
Whether this light should consider the sky color.

When enabled, this setting automatically shifts the color value to match the sun color value, and is hence good to provide an ambient fill that seamlessly shifts no matter the time of the scene you are in.

 |

**
Ambient
**
 |
Makes the light behave like an ambient light source, with no point of origin.
 |

**
Fog Radial Lobe
**
 |
Adjusts the blend ratio of the main radial lobe (parallel to the eye ray) and side radial lobe (perpendicular to the eye ray). The direction of the main radial lobe depends on the Anisotropic parameter value used (found in the Time of Day dialog window).
 |

**
Global Illumination
**
 |

-
**
Disabled -
**
 Light does not affect GI.

-
**
Static -
**
 Light produces light bounces and (in modes 1-2) supports multiple bounces.

-
**
Dynamic -
**
 Light produces single completely real-time bounce.

-
**
Hide if GI is Active -
**
 Light is deactivated if GI is active.
 |

 |

**
Animations
**
 |
Setting
 |
Description
 |

**
Style
**
 |
The animation style of the light.
 |

**
Speed
**
 |
The animation speed of the light.
 |

 |

[#environment-probe](
Environment Probe
)
[#point-light](
Point Light
)
[#projector-light](
Projector Light
)
**
Related Content
**
