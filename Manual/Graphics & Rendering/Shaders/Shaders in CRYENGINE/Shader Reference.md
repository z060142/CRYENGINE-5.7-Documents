# Shader Reference

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/29448786
- Page ID: 29448786
- Breadcrumb: Graphics & Rendering > Shaders > Shaders in CRYENGINE > Shader Reference
- Parent: Shaders in CRYENGINE

## Child Pages

- [DistanceClouds Shader](Shader Reference/DistanceClouds Shader.md)
- [Eye Shader](Shader Reference/Eye Shader.md)
- [Glass Shader](Shader Reference/Glass Shader.md)
- [Hair Shader](Shader Reference/Hair Shader.md)
- [HumanSkin Shader](Shader Reference/HumanSkin Shader.md)
- [Illum Shader](Shader Reference/Illum Shader.md)
- [Multilayeredmaterials Shader](Shader Reference/Multilayeredmaterials Shader.md)
- [NoDraw Shader](Shader Reference/NoDraw Shader.md)
- [ParticleImposter Shader](Shader Reference/ParticleImposter Shader.md)
- [Particles Shader](Shader Reference/Particles Shader.md)
- [ReferenceImage Shader](Shader Reference/ReferenceImage Shader.md)
- [Sky Shader](Shader Reference/Sky Shader.md)
- [SkyHDR Shader](Shader Reference/SkyHDR Shader.md)
- [TemplBeamProc Shader](Shader Reference/TemplBeamProc Shader.md)
- [Terrain.Layer Shader](Shader Reference/Terrain.Layer Shader.md)
- [Vegetation Shader](Shader Reference/Vegetation Shader.md)
- [Water Shader](Shader Reference/Water Shader.md)
- [WaterVolume Shader](Shader Reference/WaterVolume Shader.md)

## Content

##
Overview

The following shaders are currently available in CRYENGINE:

**
Shader Name
**

 |
**
Description
**

 |

[/docs/static/engines/cryengine-5/categories/23756816/pages/29448860](
DistanceClouds Shader
)

 |
Used by the environment artists to create 2D DistanceClouds.

 |

[/docs/static/engines/cryengine-5/categories/23756816/pages/29448900](
Eye Shader
)

 |
Used by the character artists to create the eyes of characters. Control even the amount of dynamic pupil dilation.

 |

[/docs/static/engines/cryengine-5/categories/23756816/pages/29448946](
Glass Shader
)

 |
Used by artists to create glass. Comes with specific features tailored for glass use and also specific breakability functionality.

 |

[/docs/static/engines/cryengine-5/categories/23756816/pages/29448981](
Hair Shader
)

 |
Used by character artists to create hair. Gives wide control over coloring and physicalization options.

 |

[/docs/static/engines/cryengine-5/categories/23756816/pages/29449035](
HumanSkin Shader
)

 |
Used by character artists and offers a wide variety of options to achieve realistic looking skin.

 |

[/docs/static/engines/cryengine-5/categories/23756816/pages/29449070](
Illum Shader
)

 |
The most commonly used shader, can be used to create an extremely wide variety of effects. If there is no specific shader for the type of effect you are trying to achieve, use the Illum Shader.

 |

[/docs/static/engines/cryengine-5/categories/23756816/pages/44959873](
Multilayeredmaterials Shader
)

 |
A shader type that is used for modeling materials as a stack of thin layers, including an optional thin-film on top. Each of these layers is a micro-facet surface with its own physical properties, which when combined together, act as a single material with a unique optical response that generally can not be reproduced with the traditional single-layer models.
 |

[/docs/static/engines/cryengine-5/categories/23756816/pages/29449083](
NoDraw Shader
)

 |
Used for physics proxy, the NoDraw Shader forces the Engine to not render the geometry on which the shader is applied. There are no specific Shader Params.

Alternatively, for level design it may be preferable to use
`
Materials/special/collision_proxy_entitiesonly
`
so that you can see the solid in editing mode, but not in Game mode.

 |

[/docs/static/engines/cryengine-5/categories/23756816/pages/29449085](
ParticleImposter Shader
)

 |
The ParticleImposter shader is used to create particle effects that are not affected by light and hence do not cast shadows or cause reflections.

 |

[/docs/static/engines/cryengine-5/categories/23756816/pages/29449087](
Particles Shader
)

 |
Used by particle artists.

 |

[/docs/static/engines/cryengine-5/categories/23756816/pages/29449090](
ReferenceImage Shader
)

 |
Forces the Engine to render the object without any shading or post-processing effects.

 |

[/docs/static/engines/cryengine-5/categories/23756816/pages/29449106](
Sky Shader
)

 |
Is only used for creating the sky box. The Sky Shader has no parameters, and the materials can only be applied via the Material Settings in the Material Editor.

 |

[/docs/static/engines/cryengine-5/categories/23756816/pages/29449154](
SkyHDR Shader
)

 |
Is the same as the Sky Shader, except that if you want to use the dynamically changing sky with the Time Of Day settings, you always have to use the SkyHDR Shader.

 |

[/docs/static/engines/cryengine-5/categories/23756816/pages/29449224](
TemplBeamProc Shader
)

 |
The TempleBeamProc Shader can be used to create very cheap fog light beam effects.

 |

[/docs/static/engines/cryengine-5/categories/23756816/pages/29449280](
Terrain.Layer Shader
)

 |
Used for all the terrain materials for painting terrain texture layers.

 |

[/docs/static/engines/cryengine-5/categories/23756816/pages/29449329](
Vegetation Shader
)

 |
Used for all vegetation.

 |

[/docs/static/engines/cryengine-5/categories/23756816/pages/29449362](
Water Shader
)

 |
Used for the ocean.

 |

[/docs/static/engines/cryengine-5/categories/23756816/pages/29449415](
WaterVolume Shader
)

 |
Used for water volumes and rivers.

 |

The following shaders are obsolete and have been removed in latest versions of CRYENGINE:

**
Shader Name
**

 |
**
Description
**

 |
Removed

in version
 |

CloakLayer Shader

 |
Used to create see-through / aberration effects.

 |
5.4
 |

Common.Cloud Shader

 |
Used by environment artists to create CloudVolumes.

 |
5.4
 |

GeometryBeam Shader

 |
Used by artists and level designers to create volumetric light beams imposter.

 |
5.4
 |

Lightbeam.LightBeam Shader

 |
Used by environment lighting artists to create light shafts.

 |
5.4
 |

Monitor Shader

 |
Used by artists to create effects you would typically see on older televisions, such as grain, noise, chroma shift and interlacing. Useful for in-game displays.

 |
5.4
 |

Ping Shader

 |
N/A

 |
5.4
 |

Scopes Shader

 |
Shader specifically tailored for use on weapon scope attachments.

 |
5.4
 |

VolumeObject Shader

 |
Used for Volume Objects.

 |
5.4
 |

Waterfall Shader

 |
Used for creating layered water effects.

 |
5.4
 |

Cloth Shader

 |
Used mainly by character artists. Gives extra controls for physicalization settings.

 |
3.7
 |

Custom Shader

 |
N/A

 |

 |

EnergyShield Shader

 |
Crysis specific effects.

 |

 |

FrozenLayerWip Shader

 |
N/A

 |

 |

FX_VelocityBeamParticles Shader

 |
Crysis specific effects.

 |

 |

Hologram Shader

 |
N/A

 |

 |

LensOptics.Enable Shader

 |
Used for Lens Flare effects.

 |
3.7
 |

LightFlares.Flare Shader

 |
Used by lighting environment artists to create the corona effect, like a glow on a lamp. Deprecated by lens flare system.

 |
3.7
 |

Metal Shader

 |
Used for metallic objects. Use Illum instead.

 |

 |

WaterSurface Shader

 |
Used for rivers. Use WaterVolume instead.

 |

 |

WaterVols Shader

 |
Used for lakes and other water areas. Use WaterVolume instead.

 |

 |
