# Light

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/36868283
- Page ID: 36868283
- Breadcrumb: Editor Tools > Particle Editor > Particle Effect Features > Light
- Parent: Particle Effect Features

## Content

##
Overview

Light feature allows the particles to act as light sources to illuminate the space around them. CRYENGINE provides an advanced and efficient dynamic light rendering system which is utilized by the Particle Effect System.

##
Light

This feature allows users to enable particles as light sources.

This feature should be used carefully. Even though the Particle Effect System is efficient in simulating thousands of small particles and CRYENGINE V has a very efficient light engine, light sources are much more complex than simple flat particles.

This feature is best used with either invisible particles or with those particles that have 0% albedo and only use Emissive; more information can be found on the Lighting option in
[Appearance](Appearance.md)
. Different setups are possible and we strongly recommend experimentation; however, they also may not look right.

Properties

 |
Description

 |

**
Intensity
**

 |
Controls brightness of the light sources. Lights are also filtered by the particle color.

 |

**
Radius Clip
**

 |
Limits the light in a radius in meters. This does not need to be set. If the default option, infinite, is active the light extends to its natural radius, based on its intensity.

 |

**
Affects Fog
**

 |
Only valid when Volumetric Fog is enabled. For more information, see Volumetric Fog under the
[Environment Editor (Old as of 26/2)](/docs/static/engines/cryengine-5/categories/23756816)
:

-
**
No -
**
 When enabled, allows the light source to only affect meshes.

-
**
Fog Only -
**
 When enabled, affects the volumetric fog while preventing the light source from affecting meshes.

-
**
Both -
**
 When enabled, affects both meshes and volumetric fog. This is the most realistic setting.
 |

**
Affects This Area
**
**
Only
**

 |
When turned on, particle light sources only affect the VisArea where the emitter is located. When placed in interior type scenes this helps to prevent light leaking through walls. For more information on how VisAreas work, see
[Vis Area](../../Level%20Editor%20Tab/Create%20Object/Area/Vis%20Area.md)
.

 |

**
Flare
**

 |
The name of an Optics asset which applies a special optics element to the light.

 |

The color of the Light feature is affected by the values set in the Color and Opacity features of the Component.

##
GPU Support

This feature is not supported in the GPU Pipeline.

[Light](#light)
[GPU Support](#gpu-support)
