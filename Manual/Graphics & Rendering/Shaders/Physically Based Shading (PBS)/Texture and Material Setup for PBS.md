# Texture and Material Setup for PBS

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/44959244
- Page ID: 44959244
- Breadcrumb: Graphics & Rendering > Shaders > Physically Based Shading (PBS) > Texture and Material Setup for PBS
- Parent: Physically Based Shading (PBS)

## Content

### Overview

The appearance of physical based shading materials will be heavily controlled via textures rather than individually tweaked Specular/Gloss values in the material file. The Specular/Gloss values should have locked values for a project to ensure visual consistency for the content production.

#### Albedo (Diffuse Color)

The albedo (formerly known as diffuse color) defines how bright a surface is when lit directly by a white light source with an intensity of one. More physically speaking, it defines which percentage for each component of the RGB spectrum does not get absorbed when light scatters underneath the surface. For dielectrics (non-metals), an albedo map is always required. Pure metal usually uses a black diffuse map, oxidized metal (for example rust) however has a diffuse color.

The albedo map is usually rather clean with a low contrast and should not contain any lighting, shading or shadowing information, as all of those get added dynamically by the engine. The only exception is some micro-scale occlusion, for example darkening in tiny creases or cracks which are too small to be handled by the engine.

#### Surface Normals

Most materials should have a normal map. Make sure that the correct texture preset is used, otherwise the normal map might be gamma-corrected and give wrong shading results.

#### Reflectance (Specular Color)

Reflectance (formerly known as specular color) defines how much light gets reflected immediately from the surface when the light source is directly above the surface. This is the minimum specular intensity, under grazing angles it will increase due to the Fresnel effect. The reflectance is a physical value which should be picked directly from a reference table. As such, it does not leave much artistic freedom.

Most non-metals reflect 2% to 5% (usually 4%) of the light as specular and the highlight is monochrome/gray. As the variation is so little, it is often enough to use a constant specular color instead of a specular texture map. However, if metal and non-metal are mixed in a single texture, it is required to use a specular map, as metal has a much brighter specular color than non-metal. If a specular map is used, the specular color in the material editor should be set to white which is 255/255/255, as it gets multiplied with the values from the specular map and would otherwise lower the physical values from the map.

#### Smoothness (Gloss)

The smoothness defines how rough or glossy a surface is. A a low smoothness value means that the surface is rough while a high value means the surface is very polished and shiny. The surface roughness influences the size and the intensity of specular highlights. The smoother/glossier a surface is, the smaller the specular highlight will be. A more narrow/smaller highlight will at the same time be brighter in order to obey to the rules of energy conservation.

Most materials should use a smoothness map, as it allows to give a lot of variation to the shading and makes a surface look interesting. Gloss is closely related to normal maps, as high frequency details in a normal can create some feeling of roughness as well. However, gloss is more the micro-scale roughness of the material.

![Image](https://www.cryengine.com/docs/static/attachments/44970769)

The smoothness map is stored in the alpha channel of the normal map. If the preset **NormalsWithSmoothness** is selected, the RC will automatically adjust the smoothness map stored in the alpha channel based on the normal variance and lower the smoothness at parts where normals are very bumpy. This can greatly help to reduce temporal aliasing (shimmering, sparkling highlights).

### Guidelines for Creating Different Materials

The material substance is defined to a huge degree by the specular color. Use a reference table to pick the appropriate color for the desired material type.

#### Non-Metals

- Non-metal has monochrome/gray specular color. Never use colored specular for anything except metals.
- The sRGB color range for most non-metal materials is usually between 40 and 60. It should never be higher than 80/80/80.
- A good clean albedo map is required.
- Rusted metal can be considered as a non-metal but has colored specular.

#### Metals

- The specular color for metal should usually be above sRGB 180.
- Metal can have colored specular highlights (for gold and copper for example).
- Metal has a black or very dark diffuse color.

### Checklist for Asset Setup

- Diffuse color multiplier is set to 255/255/255
- Specular colors are physically plausible values (see reference section for the correct values)
- No specular map is used for purely non-metal materials
- If a specular map is used, Material Specular Color should be 255/255/255
- If no specular map is used, Material Specular Color is the physically based value
- A smoothness map is used and creates interesting and plausible variation on the specular highlights

### Tips

- The smoothness map is one of the most important textures. With the smoothness map you can give some history to an asset. For example, make parts of an object that were touched a lot by people less rough.
- Put variation into the smoothness map. Not just random noise but think really where the object would be less or more rough.
- For non-metal objects, don't waste time with a specular map but focus rather on the smoothness map. This will also help to save memory, as a constant specular material color is enough in most cases.
- Always test the specular reaction of objects/materials, by rotating them against a light source and viewing them from different angles. Specular is what gives objects the sense of volume and breaks the flat look.
- Make sure that the lighting is setup properly when testing assets (you can use a special asset test level with calibrated lighting).
- If an object has the correct physical specular color but you see hardly any specular highlights on top of the diffuse, the smoothness might be too low. Try to increase the brightness of the smoothness map.
- To see just the specular without any diffuse, put the Diffuse Color to black in the material editor.
- Use the histogram in the material editor to identify issues in the material setup. You can easily judge the overall brightness of textures using the histogram.

### Reference Values

##### Reflectance (Specular Color)

If a non-metal material is not in the list, you can assume a typical reflectance of 4% which is around 55 in sRGB space.

Material | sRGB Color | Linear (Blend Layer)
--- | --- | ---
**Water** | 38 38 38 | 0.02
**Skin** | 51 51 51 | 0.03
**Hair** | 65 65 65 | 0.05
**Plastic / Glass (Low)** | 53 53 53 | 0.03
**Plastic High** | 61 61 61 | 0.05
**Glass (High) / Ruby** | 79 79 79 | 0.08
**Diamond** | 115 115 115 | 0.17
**Iron** | 196 199 199 | 0.57
**Copper** | 250 209 194 | N/A
**Gold** | 255 219 145 | N/A
**Aluminum** | 245 245 247 | 0.91
**Silver** | 250 247 242 | N/A

#### See also

[Albedo (Diffuse Color)](#albedo-diffuse-color)[Surface Normals](#surface-normals)[Reflectance (Specular Color)](#reflectance-specular-color)[Smoothness (Gloss)](#smoothness-gloss)[Non-Metals](#non-metals)[Metals](#metals)[See also](#see-also)
