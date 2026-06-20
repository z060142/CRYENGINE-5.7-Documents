# Shader Reference

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/29448786
- Page ID: 29448786
- Breadcrumb: Graphics & Rendering > Shaders > Shaders in CRYENGINE > Shader Reference
- Parent: Shaders in CRYENGINE

## Child Pages

- [DistanceClouds Shader](Shader%20Reference/DistanceClouds%20Shader.md)
- [Eye Shader](Shader%20Reference/Eye%20Shader.md)
- [Glass Shader](Shader%20Reference/Glass%20Shader.md)
- [Hair Shader](Shader%20Reference/Hair%20Shader.md)
- [HumanSkin Shader](Shader%20Reference/HumanSkin%20Shader.md)
- [Illum Shader](Shader%20Reference/Illum%20Shader.md)
- [Multilayeredmaterials Shader](Shader%20Reference/Multilayeredmaterials%20Shader.md)
- [NoDraw Shader](Shader%20Reference/NoDraw%20Shader.md)
- [ParticleImposter Shader](Shader%20Reference/ParticleImposter%20Shader.md)
- [Particles Shader](Shader%20Reference/Particles%20Shader.md)
- [ReferenceImage Shader](Shader%20Reference/ReferenceImage%20Shader.md)
- [Sky Shader](Shader%20Reference/Sky%20Shader.md)
- [SkyHDR Shader](Shader%20Reference/SkyHDR%20Shader.md)
- [TemplBeamProc Shader](Shader%20Reference/TemplBeamProc%20Shader.md)
- [Terrain.Layer Shader](Shader%20Reference/Terrain.Layer%20Shader.md)
- [Vegetation Shader](Shader%20Reference/Vegetation%20Shader.md)
- [Water Shader](Shader%20Reference/Water%20Shader.md)
- [WaterVolume Shader](Shader%20Reference/WaterVolume%20Shader.md)

## Content

## Overview

The following shaders are currently available in CRYENGINE:

**Shader Name** | **Description**
--- | ---
[DistanceClouds Shader](Shader%20Reference/DistanceClouds%20Shader.md) | Used by the environment artists to create 2D DistanceClouds.
[Eye Shader](Shader%20Reference/Eye%20Shader.md) | Used by the character artists to create the eyes of characters. Control even the amount of dynamic pupil dilation.
[Glass Shader](Shader%20Reference/Glass%20Shader.md) | Used by artists to create glass. Comes with specific features tailored for glass use and also specific breakability functionality.
[Hair Shader](Shader%20Reference/Hair%20Shader.md) | Used by character artists to create hair. Gives wide control over coloring and physicalization options.
[HumanSkin Shader](Shader%20Reference/HumanSkin%20Shader.md) | Used by character artists and offers a wide variety of options to achieve realistic looking skin.
[Illum Shader](Shader%20Reference/Illum%20Shader.md) | The most commonly used shader, can be used to create an extremely wide variety of effects. If there is no specific shader for the type of effect you are trying to achieve, use the Illum Shader.
[Multilayeredmaterials Shader](Shader%20Reference/Multilayeredmaterials%20Shader.md) | A shader type that is used for modeling materials as a stack of thin layers, including an optional thin-film on top. Each of these layers is a micro-facet surface with its own physical properties, which when combined together, act as a single material with a unique optical response that generally can not be reproduced with the traditional single-layer models.
[NoDraw Shader](Shader%20Reference/NoDraw%20Shader.md) | Used for physics proxy, the NoDraw Shader forces the Engine to not render the geometry on which the shader is applied. There are no specific Shader Params. Alternatively, for level design it may be preferable to use `Materials/special/collision_proxy_entitiesonly` so that you can see the solid in editing mode, but not in Game mode.
[ParticleImposter Shader](Shader%20Reference/ParticleImposter%20Shader.md) | The ParticleImposter shader is used to create particle effects that are not affected by light and hence do not cast shadows or cause reflections.
[Particles Shader](Shader%20Reference/Particles%20Shader.md) | Used by particle artists.
[ReferenceImage Shader](Shader%20Reference/ReferenceImage%20Shader.md) | Forces the Engine to render the object without any shading or post-processing effects.
[Sky Shader](Shader%20Reference/Sky%20Shader.md) | Is only used for creating the sky box. The Sky Shader has no parameters, and the materials can only be applied via the Material Settings in the Material Editor.
[SkyHDR Shader](Shader%20Reference/SkyHDR%20Shader.md) | Is the same as the Sky Shader, except that if you want to use the dynamically changing sky with the Time Of Day settings, you always have to use the SkyHDR Shader.
[TemplBeamProc Shader](Shader%20Reference/TemplBeamProc%20Shader.md) | The TempleBeamProc Shader can be used to create very cheap fog light beam effects.
[Terrain.Layer Shader](Shader%20Reference/Terrain.Layer%20Shader.md) | Used for all the terrain materials for painting terrain texture layers.
[Vegetation Shader](Shader%20Reference/Vegetation%20Shader.md) | Used for all vegetation.
[Water Shader](Shader%20Reference/Water%20Shader.md) | Used for the ocean.
[WaterVolume Shader](Shader%20Reference/WaterVolume%20Shader.md) | Used for water volumes and rivers.

The following shaders are obsolete and have been removed in latest versions of CRYENGINE:

**Shader Name** | **Description** | Removed in version
--- | --- | ---
CloakLayer Shader | Used to create see-through / aberration effects. | 5.4
Common.Cloud Shader | Used by environment artists to create CloudVolumes. | 5.4
GeometryBeam Shader | Used by artists and level designers to create volumetric light beams imposter. | 5.4
Lightbeam.LightBeam Shader | Used by environment lighting artists to create light shafts. | 5.4
Monitor Shader | Used by artists to create effects you would typically see on older televisions, such as grain, noise, chroma shift and interlacing. Useful for in-game displays. | 5.4
Ping Shader | N/A | 5.4
Scopes Shader | Shader specifically tailored for use on weapon scope attachments. | 5.4
VolumeObject Shader | Used for Volume Objects. | 5.4
Waterfall Shader | Used for creating layered water effects. | 5.4
Cloth Shader | Used mainly by character artists. Gives extra controls for physicalization settings. | 3.7
Custom Shader | N/A |
EnergyShield Shader | Crysis specific effects. |
FrozenLayerWip Shader | N/A |
FX_VelocityBeamParticles Shader | Crysis specific effects. |
Hologram Shader | N/A |
LensOptics.Enable Shader | Used for Lens Flare effects. | 3.7
LightFlares.Flare Shader | Used by lighting environment artists to create the corona effect, like a glow on a lamp. Deprecated by lens flare system. | 3.7
Metal Shader | Used for metallic objects. Use Illum instead. |
WaterSurface Shader | Used for rivers. Use WaterVolume instead. |
WaterVols Shader | Used for lakes and other water areas. Use WaterVolume instead. |
