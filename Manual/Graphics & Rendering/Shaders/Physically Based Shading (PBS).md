# Physically Based Shading (PBS)

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/44959238
- Page ID: 44959238
- Breadcrumb: Graphics & Rendering > Shaders > Physically Based Shading (PBS)
- Parent: Shaders

## Child Pages

- [System Setup for PBS](Physically%20Based%20Shading%20(PBS)/System%20Setup%20for%20PBS.md)
- [Texture and Material Setup for PBS](Physically%20Based%20Shading%20(PBS)/Texture%20and%20Material%20Setup%20for%20PBS.md)
- [Physically Based Shading - Debugging](Physically%20Based%20Shading%20(PBS)/Physically%20Based%20Shading%20-%20Debugging.md)
- [Creating Textures for Physically Based Shading](Physically%20Based%20Shading%20(PBS)/Creating%20Textures%20for%20Physically%20Based%20Shading.md)

## Content

##
Overview

CRYENGINE 3.6 and beyond uses a shading model that is based on fundamental physical rules. Instead of using a plenty of fudge and tweak factors which don't have a reasonable meaning in the real world, materials use physical properties to describe how the incoming light should interact with them. A huge advantage of using a physically based model with certain rules is that material assets will look a lot more consistent and more convincing under different lighting conditions.

Although it is not absolutely necessary to know how light interacts with surfaces in the real world, a basic understanding can be very helpful when setting up materials.

##
Diffuse and Specular Reflectance

When light hits a surface, it splits into two directions: some part of it is reflected immediately while the rest gets refracted and enters the surface. The refracted light can be absorbed or can be scattered around underneath the surface and exit again at a slightly different location.

Light that gets reflected directly from the surface is handled as
**
specular
**
 reflectance in a shading model. The light that is refracted and undergoes subsurface scattering is handled as
**
diffuse
**
 reflectance.

The amount of light that is reflected versus refracted depends on the surface substance and the angle at which the light hits the surface. At a grazing angle, the amount of light that gets reflected directly (specular) gets higher, until it reaches 100% at an extreme angle. This behavior is described by the Fresnel effect.

##
Material Types

There are only two categories of substances which are relevant for calculating physical based shading, which each have

special characteristics regarding diffuse and specular reflectance
:

-
**
metals
**
 (conductors like iron, gold, copper, etc.)

-
**
non-metals
**
 (dielectric materials like plastic, stone, wood, skin, glass, etc.)
Metal absorbs all light that enters underneath the surface, hence metal has no diffuse reflection. This means that metal should have a black diffuse color. All visible light is reflected directly from the surface (specular reflectance). The different types of metal have characteristic specular colors.

Non-metal surfaces have diffuse reflection, with the specular reflection being a lot weaker and less varied than for metal. Specular reflectance for non-metal is monochromatic (no color, just gray). Most non-metals reflect only a small fraction of the light as specular, for most materials it's between 2% and 5%.

##
Related Topics

-
[System Setup for PBS](Physically%20Based%20Shading%20(PBS)/System%20Setup%20for%20PBS.md)

-
[Texture and Material Setup for PBS](Physically%20Based%20Shading%20(PBS)/Texture%20and%20Material%20Setup%20for%20PBS.md)

-
[Physically Based Shading - Debugging](Physically%20Based%20Shading%20(PBS)/Physically%20Based%20Shading%20-%20Debugging.md)

-
[Lighting Levels Using PBS](../Lighting/Lighting%20Overview/Lighting%20Levels%20Using%20PBS.md)
