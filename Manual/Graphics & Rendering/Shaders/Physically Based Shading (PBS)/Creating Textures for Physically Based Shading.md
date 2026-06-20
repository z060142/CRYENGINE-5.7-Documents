# Creating Textures for Physically Based Shading

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/54427668
- Page ID: 54427668
- Breadcrumb: Graphics & Rendering > Shaders > Physically Based Shading (PBS) > Creating Textures for Physically Based Shading
- Parent: Physically Based Shading (PBS)

## Content

Please note that many example images shown in this article state that Material Diffuse Color should be 186/187. This was correct on earlier iterations of the PBR implementation but is no longer the case.

Diffuse Color should always be 255,255,255 to get the maximum information from the texture. These example images will be updated with current information in the future.

##
Overview

##
Photoshop set up for Physically Based Shaders

The first thing we have to do is set up Photoshop correctly. When working with Physically Based Shaders you have to be aware that the default RGB color space is sRGB. In sRGB space, a 50% mid-gray is not 0.5 or 127 but rather 0.5 raised by the inverse of gamma 2.2, which equals 187 in Photoshop. In a nutshell, the reason that sRGB is used is to avoid banding artifacts (and to use a conservative range of values to avoid misrepresentation on the typical non-calibrated monitor). In sRGB space you get more precision for darker colors to which the human eye is more sensitive. Before working on colors, please make sure that your screen is calibrated properly.

To achieve that, we have to go to "
**
Color Settings".
**
 To get there we go to
**
"Edit" and then select "Color Settings...".
**
 The RGB should be set to
**
sRGB
**
 and Gray to
**
Gray Gamma 2.2
**
.

By default, Gray is usually set to
*
Dot Gain 20%
*
 which will result in a color transformation in the alpha channel. In this case, a value of 127 will come into the engine as 104, which can cause inconsistencies, so please make sure Gamma 2.2 is used instead.

[Image: /docs/static/attachments/54427812]

[Image: /docs/static/attachments/54427813]

After Photoshop has been set up we can get our correct values by looking at the chart and "color" picking the values. Please remember that your Gloss Map goes into the Alpha of Normal Map.

Here are the values for all the materials. To get the values "color" pick the swatches. Please click on the image to download the .bmp source file (it is uncompressed and gives you the true values) and DO NOT color pick from the images here in the document since it's a .jpeg, meaning it's compressed and therefore will give you the wrong values!

**
[Image: /docs/static/attachments/69468498]

**

[Image: /docs/static/attachments/54427798]

If you want to understand more about Physically Based Shaders and how they work, please see:
[/docs/static/engines/cryengine-5/categories/23756816/pages/44959238](
Physically Based Shading
)
.

##
Specular Texturing for Physically Based Shaders

As we're using physically based shading for our project and truly being "next gen", the gloss map is one of the most important map if not the most. It requires a different thinking in how we use our specular maps.

The gloss maps have to be treated like a diffuse texture and customized according to it and in some occasions painted like one.
**
If you don't use any metals or your asset has no metal parts, then we don't use a spec map at all
**
.

All the gloss maps go into the Alpha Channel of the Normal Map.

##
Material types

There are only two categories of substances which are relevant for rendering:
**
metals
**
 (conductors like iron, gold, copper, etc.) and
**
non-metals
**
 (dielectric materials like plastic, stone, wood, skin, glass, etc.). Both have special characteristics regarding diffuse and specular reflectance.

Metal absorbs all light that enters underneath the surface; hence metal has no diffuse reflection. This means that metal should have a black diffuse color. All visible light is reflected directly from the surface (specular reflectance). The different types of metal have characteristic specular colors.

In contrast to metal, non-metal has diffuse reflection; however the specular reflection is a lot weaker and less varied than for metal. Specular reflectance for non-metal is monochromatic (no color, just gray). Most non-metals reflect only a small fraction of the light as specular - for most materials between 2% and 5%.

##
Specular Color and what it does to the asset

The specular color defines how much light gets reflected immediately from the surface when the light source is directly above the surface. This is the minimum specular intensity, under grazing angles it will increase due to the Fresnel effect. As the specular color is specific for a certain type of material, it can also be considered as a mask for the type of material/substance. The specular color is a physical value which should be picked directly from a reference table. As such, it does not leave much artistic freedom.

Most non-metals reflect 2% to 5% of the light as specular and the highlight is monochrome/gray. As the variation is so little, it is often enough to use a constant specular color instead of a specular texture map. However, if metal and non-metal are mixed in a single texture, it is required to use a specular map, as metal has a much brighter specular color than non-metal. If a specular map is used, the specular color in the material editor should be set to white which is 255/255/255, as it gets multiplied with the values from the specular map and would otherwise lower the physical values from the map.

If no metal is used in the texture your spec map should be white and the specular color values based on provided by the "Physically Based Shading" image. You can get it again by clicking this link.

##
Gloss values and what they do to the asset

Another big thing to keep in mind is how gloss works and how it should be used.

Gloss defines the
**
roughness
**
 of a surface. A
**
low
**
 gloss value means that the surface is
**
rough
**
 while a
**
high
**
 value means the surface is very
**
smooth
**
 and shiny. The roughness influences the size and the intensity of specular highlights. The smoother/glossier a surface is, the
**
smaller
**
 the specular highlight will be. A more narrow/smaller highlight will at the same time be brighter in order to obey to the rules of energy conservation.

Most materials should have a gloss map, as it can give a lot of variation to the shading. Gloss is closely related to normal maps, as high frequency details in a normal can create some feeling of roughness as well. However, gloss is more the micro-scale roughness of the material.

With this we can paint our maps dictating how much usage parts of an object has gotten (since a heavily worn parts of an object is smoother and the it will have a tighter gloss and more reflectivity than parts who haven't been used that much)

[Image: /docs/static/attachments/54427799]

Based on these basics we need to start thinking on how to set up our gloss map. This is the most important step in setting up your gloss map!

-
The general value for non metals is between 53 and 61.

-
The Gloss map always goes into the Alpha channel of the Normal map.

-
No Spec map is needed unless you have Metals or your asset has metal parts.

##
How to texture for Physically based shading

The most important maps for Physically based shading are your gloss and normal maps. You should start texturing with those two maps alone, which will help you to define your surface, and then as a last step add your diffuse map.

The diffuse texture itself should have no lighting information at all.

##
Exporting your Normal Map with your Gloss Map out of Photoshop

Gloss and normals kind of belong together. The normal map defines the bumpiness of a surface on a macro scale while the gloss is the roughness on a micro scale.

The two maps are the most important for shading detail, so you should starting to texture with your normal map and your gloss map. Once you achieved the desired result, you should start working on your diffuse texture. Please remember that your diffuse should have no lighting information at all.

The gloss map needs to go always into the normal map alpha, even if you're using a spec map for your metals and metal containing surfaces.

To export your normal map with the gloss in the alpha channel, name it and always add the suffix _ddna (in this case courtyard_wall_arch_marble_ddna).

[Image: /docs/static/attachments/54427847]

[Image: /docs/static/attachments/54427849]

##
Examples of gloss maps and how to set up the shaders

Following are some examples with explanations of how the gloss map is affecting the asset and how it defines the material. It is also explained and showed how a gloss map should look to achieve the desired material and look.

These examples are placed on Orbs in the Asset Zoo to serve as a guide. Above them are the same materials without the diffuse, so we can see better what the gloss and normal map is doing.

##
Marble tiled floor material

As you can see the marble tiled floor is a very smooth surface with a mostly tight spec, a high and sharpened reflectivity. There are some sections which are not reflective, have a wide spec, and are therefore are not as smooth looking.

[Image: /docs/static/attachments/54427800]

The big dark grey tile has a very wide spec, is not as smooth and has a very low reflectivity. By the look at the gloss map we can analyze why. As you can see most of the map is very light and bright. Where the tile is located you see that it's dark grey. This is the reason why that part is dull looking compared to rest of the tiles. Please pay also attention on how we're defining the cracks and dirt by adding localized darker areas. We also have a mid level of contrast. All this helps in conjunction with the normal map to define the material and make the surface more interesting, also making it more believable.

[Image: /docs/static/attachments/54427801]

To set up our Shader correctly we need to set in the Material editor the Glossiness to 255 otherwise the gloss map will not work.

As for the Specular Color, you have some creative freedom in how high you should set it and what achieves the best look for the asset. The values it should be between 53 and 61 for non metals.

[Image: /docs/static/attachments/54427794]

##
Stone material

Stone is a very rough surface with a very low reflectivity and a very wide spec.

[Image: /docs/static/attachments/54427795]

If we take a look at the gloss map we can see that it's pretty dark and muted. The level of contrast is not very high. All this creates a very low and unsharpened reflectivity, with a wide spec and low highlights. The material appears to have a high roughness.

If you look closely at the gloss map you'll see also that it has unevenness in light and dark areas. This helps to make the surface look interesting as it creates different values as light travels across it, helping in making it look more believable.

[Image: /docs/static/attachments/54427796]

To set up our Shader correctly we need to set in the Material editor the Glossiness to 255, otherwise the gloss map will not work.

As for the Specular Color, you have some creative freedom in how high you should set it and what achieves the best look for the asset. The values it should be between 53 and 61 for non metals.

[Image: /docs/static/attachments/54427797]

##
Sandstone bricks material

The sandstone brick material is also a rough surface with low reflectivity and a wide spec. It is though not as rough as stone.

[Image: /docs/static/attachments/54427791]

Taking a look at the gloss map we see a muted map, with greys in the mid to dark range. It is muted with a not high level of contrast and it represents a low and an unsharpened reflectivity, with a wide spec. But as opposed to stone it's not as dark and muted.

Again you can see how different values of grey help to make the surface look more interesting, as differences in specularity occur when it's hit by the light. This makes our material more believable.

[Image: /docs/static/attachments/54427792]

To set up our Shader correctly we need to set in the Material editor the Glossiness to 255 otherwise the gloss map will not work.

As for the Specular Color, you have some creative freedom in how high you should set it and what achieves the best look for the asset. The values it should be between 53 and 61 for non metals.

[Image: /docs/static/attachments/54427793]

##
Painted marble material

As you can see the painted marble material is a fairly smooth surface with a tighter spec. You can also see as the parts where the paint has worn off, it's duller with lower and less sharpen reflectivity and wider spec. It also has parts where it has the opposite.

Pay close attention to how the paint is actually visible on the spec (breaking the smoothness) where the light hits it.

[Image: /docs/static/attachments/54427787]

The general set up for this map is light and bright with greys in the mid to high range. We have a mid level of contrast. Tthe white speckles will break the roughness of the surface and the cracks. Worn off and chipped parts will be rougher and therefore darker. That way we achieve the look and believability we're looking for.

[Image: /docs/static/attachments/54427788]

To set up our Shader correctly we need to set in the Material editor the Glossiness to 255 otherwise the gloss map will not work.

As for the Specular Color, you have some creative freedom in how high you should set it and what achieves the best look for the asset. The values it should be between 53 and 61 for non metals.

[Image: /docs/static/attachments/54427789]

##
Marble unpolished material

The unpolished marble material is a rougher surface with low and unsharpened reflectivity. It shows also a high roughness, with very wide and low highlights.

[Image: /docs/static/attachments/54427790]

If we look at the gloss map, we see a dark and muted map resulting in a low level of contrast. This gives us a low and unsharpened reflectivity and makes also the material rough. This also makes the spec wide with low highlights.

The different values of dark and light in the map create uneven specular values and reflectivity, making the surface believable and interesting.

[Image: /docs/static/attachments/54427784]

To set up our Shader correctly we need to set in the Material editor the Glossiness to 255 otherwise the gloss map will not work.

As for the Specular Color, you have some creative freedom in how high you should set it and what achieves the best look for the asset. The values it should be between 53 and 61 for non metals.

[Image: /docs/static/attachments/54427785]

##
White/black and grey polished marble material

As opposed to the unpolished marble, we have a very smooth surface, with a high and much sharpened reflectivity. The spec is very tight with high highlights.

[Image: /docs/static/attachments/54427786]

To achieve that the way we need to set up our gloss map is very light and bright with some contrast.

By having through the map different values of lights and darks, we can break the spec, reflectivity and sharpness. This helps make the surface look more interesting and believable.

[Image: /docs/static/attachments/54427781]

To set up our Shader correctly we need to set in the Material editor the Glossiness to 255, otherwise the gloss map will not work.

As for the Specular Color, you have some creative freedom in how high you should set it and what achieves the best look for the asset. The values should be between 53 and 61 for non-metals.

[Image: /docs/static/attachments/54427782]

##
Polished white marble bricks material

The polished white marble brick material is a very smooth surface, but we have the crevices an in real life dirt accumulates there in making them less reflective.

[Image: /docs/static/attachments/54427783]

Looking at the gloss map for it we can see a very light and bright map with a higher contrast. This makes the material very smooth as its polished bricks, but as you look towards the corner we see dark areas creating less polished and less reflecting parts of the material.

The different values of dark and light make the material more believable and interesting as it creates different values in highness and sharpened reflectivity and smoothness.

[Image: /docs/static/attachments/54427778]

To set up our Shader correctly we need to set in the Material editor the Glossiness to 255 otherwise the gloss map will not work.

As for the Specular Color, you have some creative freedom in how high you should set it and what achieves the best look for the asset. The values it should be between 53 and 61 for non metals.

[Image: /docs/static/attachments/54427779]

##
Non metal with metal material in the same texture

When a texture contains a part that is metal, we need to add color in the spec map to the metal part of it, since the metal will have a different spec color than the non metal parts. The gloss map in the alpha channel of the normal map, still defines the smoothness, reflectivity and tightness of highlights. But we won't control the spec color in the shader. We have to do it in the texture itself, to do that we have to take the values from the Physically Based Shading chart and add the color into our spec map.

In this case we use a dedicated spec map and our gloss map will still go into the ALPHA CHANNEL of the Normal map!

We have an example of how the texture of the spec map would look. In the color map of the spec we can see the gold parts having a yellow/goldish color. This makes the specular color that gets reflected yellow/goldish, which in this case is gold. As you can see the rest of the map is grey with a value of 55,55 and 55 for the non metal parts.

[Image: /docs/static/attachments/54427775]

In the alpha channel of the normal map we still have our gloss map, which will define our reflectivity, smoothness and highlights. Pay close attention to how white and contrasting the metal parts are.

We want the metal to have a high level of reflectivity, smoothness and tight highlights with some darker parts to break up the spec and make it more believable and interesting.

Please look also at the rest of the gloss map. We see that the surfaces are being defined by parts. There are parts of the object which are rough with low highlights, wide spec and low reflectivity.

[Image: /docs/static/attachments/54427774]

Once the asset is in the engine we need to open up the material editor and set the specular value of the material to 255. This has to be done since the color map of the spec map is controlling the specular color and not the shader.

Please don't forget to set the value of the gloss also to 255 so the gloss map in the alpha channel will work.

[Image: /docs/static/attachments/54427776]

Finally our asset will look like this in the game.

[Image: /docs/static/attachments/54427780]

##
Metals

When a asset consists purely of metal, we don't need a diffuse texture at all. Metals have no color and are defined by the color of the light they bounce back. Therefore we use our spec range sheet and color sample the metal according to it.

The gloss map in the alpha channel of the normal map, still defines the smoothness, reflectivity and tightness of highlights. But we won't control the spec color in the shader.

We have to do it in the texture itself. To do that, we have to take the values from the Physically Based Shading chart and add the color into our spec map.

[Image: /docs/static/attachments/54427773]

In this case we use a dedicated spec map and our gloss map will still go into the ALPHA CHANNEL of the Normal map!

[Image: /docs/static/attachments/54427768]

In the alpha channel of the normal map we still have our gloss map, which will define our reflectivity, smoothness and highlights.

Pay close attention to how white and contrasting the metal parts are. There are two examples of the gloss map. We have an unpolished metal, with wider spec and lower reflectivity, and we have the polished metal with a whiter gloss map that gives us a tight spec and high reflectivity.

[Image: /docs/static/attachments/54427770]

[Image: /docs/static/attachments/54427764]

Once the asset is in the engine, we need to open up the material editor and set the specular value of the material to 255. This has to be done since the color map of the spec map is controlling the specular color and not the shader.

Please don't forget to set the value of the gloss also to 255 so the gloss map in the alpha channel will work.

[Image: /docs/static/attachments/54427766]

##
Oxidized / Rusted Metals

Most of the metals you will encounter in the real world and in our game will be used, worn and even oxidized. We still don't need a diffuse texture at all. Metals have no color and are defined by the color of the light they bounce back. Therefore we use our spec range sheet and color sample the metal according to it. The gloss map in the alpha channel of the normal map, still defines the smoothness, reflectivity and tightness of highlights. We need to start out with this at first and really paint in the spots where the oxidization would naturally build. Those areas we want to have less gloss and less reflectivity.

As you look at rust in general you can see that there's still some glimmer coming through it. Please think about that, look at reference, and incorporate that into your gloss map. As mentioned
before,
with metals we won't control the spec color in the shader. We have to do it in the texture itself. To do that, we have to take the values from the Physically Based Shading chart and add the color into our spec map. What we need to look at is our spec map and texture it accordingly. We start painting with the base color of the metal, taken from the spec ranges sheet, and paint in the color of the rust or oxidization in accordance of our gloss map.

In the alpha channel of the normal map we still have our gloss map, which will define our reflectivity, smoothness and highlights.

[Image: /docs/static/attachments/54427757]

After we're done with our gloss map we paint according to our gloss map our spec map, to get different specular color of the oxidization.

**
[Image: /docs/static/attachments/54427761]

**

Once the asset is in engine we need to open up the material editor and set the specular value of the material to 255. This has to be done since the color map of the spec map is controlling the specular color and not the shader.

Please don't forget to set the value of the gloss also to 255 so the gloss map in the alpha channel will work.

[Image: /docs/static/attachments/54427759]

Here's our final asset looks in game with the normal, gloss and spec map working.

[Image: /docs/static/attachments/54427755]

##
Subsurface scattering for environments

One of the biggest things to take our visual quality to truly "next gen" is using subsurface scattering in environments and the materials for it.

You have materials that have a bigger amount of subsurface scattering like marble and you have some who have less or none. Since the cost of using it is very low we recommend using it frequently. The only time you shouldn't use it is on pure metal surfaces. Sometimes a surface doesn't have a lot of subsurface scattering, but we still recommend using it with a very low value.

There are three colors of subsurface scattering we can use: red, blue and yellow. The red color of the subsurface scattering should be use more in conjunction with skin on characters. The blue should be use more with ice, but it can also be used with surfaces to give it a colder look. The yellow is the main color it should be used for environments and its surfaces, especially on marble.

To show the difference better here are two screenshots of a marble pillar, the first without subsurface scattering, the second with.

[Image: /docs/static/attachments/54427777]

[Image: /docs/static/attachments/54427771]

To set the amount of the subsurface scattering you go to the tab and set the value to something that looks good. Please be careful and don't set it too high, as it will look like wax. The recommendation is to go up by increments of .05. We have some degree of artistic freedom here.

[Image: /docs/static/attachments/54427772]

[#photoshop-set-up-for-physically-based-shaders](
Photoshop set up for Physically Based Shaders
)
[#specular-texturing-for-physically-based-shaders](
Specular Texturing for Physically Based Shaders
)
[#material-types](
Material types
)
[#specular-color-and-what-it-does-to-the-asset](
Specular Color and what it does to the asset
)
[#gloss-values-and-what-they-do-to-the-asset](
Gloss values and what they do to the asset
)
[#how-to-texture-for-physically-based-shading](
How to texture for Physically based shading
)
[#exporting-your-normal-map-with-your-gloss-map-out-of-photoshop](
Exporting your Normal Map with your Gloss Map out of Photoshop
)
[#examples-of-gloss-maps-and-how-to-set-up-the-shaders](
Examples of gloss maps and how to set up the shaders
)
