# Vegetation 01 Grass (Patch) CRYENGINE

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/24285888
- Page ID: 24285888
- Breadcrumb: Tutorials > Game and Level Design > Vegetation Tutorials > Tutorial - Vegetation Asset Creation > Vegetation 01 Grass (Patch) > Vegetation 01 Grass (Patch) CRYENGINE
- Parent: Vegetation 01 Grass (Patch)

## Content

##
Material Setup in CRYENGINE

Having reached this point you should have now successfully exported out the geometry and material from 3dsMax or Maya into a desired folder. We will now continue with the setup in CRYENGINE. In this section we will first define the material parameters that are required for the vegetation to be rendered and so that it behaves correctly. Then we will use the vegetation tool to place the assets into the world.

First open the Material Editor and navigate to your object.

![Image](https://www.cryengine.com/docs/static/attachments/24157020)

*
Pic1: Material Editor overview
*

Set the correct
**
Shader
**
 and
**
Surface Type
**
 for the object and set both to
**
Vegetation
**
.

##
Material Settings

You need to set the correct
**
Shader
**
 and the
**
 Surface Type
**
 for the object and in this case both have to be changed to
**
Vegetation
**
. This is achieved by selecting
**
Vegetation
**
 from the drop down lists.

![Image](https://www.cryengine.com/docs/static/attachments/26509315)

*
Pic2: Material settings
*

When we use the
**
Vegetation Shader
**
 on the material SubID, it exposes specific parameters that only apply to the Vegetation system. Note how the Material Editor updates the two sections for the
**
Shader Params
**
 and the
**
Shader Generation Params
**
when we swap from the default Illum Shader to the Vegetation Shader. For more information go to the Shader Generation Params section later in this article.

##
Opacity Settings

Here we are using the default values that we setup in 3dsMax.
**
Opacity
**
 at 100% and the
**
AlphaTest
**
 set to around 35. There is no hard and fast rule for the setting of the alpha test level. Set it to what looks right for your asset.

![Image](https://www.cryengine.com/docs/static/attachments/24157021)

*
Pic3: Opacity
*

![Image](https://www.cryengine.com/docs/static/attachments/24157022)

*
Pic4: Re-cap of where this info came from in 3dsMax
*

##
Lighting

Under the
**
Lighting Settings
**
 we find the color parameters. To be correctly in line with the PBS pipeline, we have to:

-
Set our
**
Diffuse Color
**
 to pure white 255,255,255.

-
Set the
**
Specular Color
**
 within the 40,40,40 - 60,60,60 range (dark grey).

-
Set the
**
Smoothness
**
 slider to a low value such as 30.
![Image](https://www.cryengine.com/docs/static/attachments/24157023)

*
Pic5: Lighting Settings
*

Since we are using the
**
grass
**
 parameter in the shader, this means the material does not require a normalmap. In CRYENGINE, we save our smoothness value into the alpha channel of the normalmap (ddna) and since this is not present in the material, it reads the smoothness value directly from the
**
Smoothness
**
 slider instead.

For more information on the PBS rendering setup please go
[HERE](../../../../../Graphics%20%26%20Rendering/Shaders/Physically%20Based%20Shading%20(PBS).md)
for a full explanation.

##
Texture Maps

The
**
Texture Maps
**
 section should already have been filled out with our
**
Diffuse
**
 (*.diff) details through the material export from 3dsMax.

*
![Image](https://www.cryengine.com/docs/static/attachments/24157025)

Pic6: Texture maps with only the diffuse assigned
*

##
Shader Generation Params

This tab in the Material Editor will show you different options depending on the shader type you assign to the material SubId. Since we have selected the
**
Vegetation
**
 shader, it exposes the options that are applicable to the vegetation. To continue, check the box for the
**
Grass
**
 parameter. We want our asset to run through the cheaper and faster pipeline.

![Image](https://www.cryengine.com/docs/static/attachments/24157024)

*
Pic7: Shader Generation Params with grass enabled
*

Name
 |
Description
 |

**
Leaves
**
 |
Uses a higher quality rendering pass on the asset
 |

**
Grass
**
 |
Uses a cheaper and faster rendering pass on the asset
 |

**
Detail bending
**
 |
Used for adding random noise into the leaves movement (not required for this tutorial).
 |

**
Detail mapping
**
 |
Used for adding a detail map into the asset (not required for this tutorial).
 |

**
Blend layer
**
 |
Used for blending a second set of Diffuse and Normalmap textures (not required for this tutorial).
 |

**
Displacement mapping
**
 |
This is for applying tessellation to the asset (not required for this tutorial).
 |

**
Phong tessellation
**
 |
This is for applying tessellation to the asset (not required for this tutorial).
 |

**
PN triangles tessellation
**
 |
This is for applying tessellation to the asset (not required for this tutorial).
 |

##
Shader Params

As you may have noticed, we jumped this section in favor of the
**
Shader Generation Params
**
. We wanted to enable the
**
Grass
**
 options first to expose all the parameters that we need to configure the asset correctly. By enabling the
**
Grass
**
 parameter, some additional options have been exposed in the
**
Shader Params
**
 section. It should now look like this.

![Image](https://www.cryengine.com/docs/static/attachments/26509316)

*
Pic8: Shader Params
*

Name
 |
Description
 |

**
Bending branch amplitude
**
 |
Detail bending control. Please see
**
[this page](../Vegetation%2003%20Bushes%20(Detail%20Bending).md)
**
 for information on detail bending (not required for this tutorial).
 |

**
Bending edges amplitude
**
 |
Detail bending control. Please see
**
[this page](../Vegetation%2003%20Bushes%20(Detail%20Bending).md)
**
 for information on detail bending (not required for this tutorial).
 |

**
Cap opacity fall off
**
 |
Controls how strongly vegetation polygons fade out when looking at them at a steep angle. This helps to disguise the plane shape of vegetation geometry.
 |

**
Detail bending frequency
**
 |
Detail bending control. Please see
**
[this page](../Vegetation%2003%20Bushes%20(Detail%20Bending).md)
**
 for information on detail bending (not required for this tutorial).
 |

**
Indirect bounce color
**
 |
Keep this at the default value.
 |

**
Normal View Dependency
**
 |
This value orients the normals towards the player and is useful for planes.
 |

**
Terrain Color Blend
**
 |
If you enable
**
UseTerrainColor
**
 in the
**
Vegetation
**
 tool for the object, this will absorb some of the color information of the underlying terrain where the vegetation object has been placed. This nice feature helps distant vegetation objects blend into the scene at distance.
 |

**
Terrain Color Blend Dist
**
 |
This slider controls how close to the camera the 'absorption' of the terrain color will happen.
 |

**
Transmittance Color
**
 |
This color is what you would get if you were to shine a light through the leaf and look at it from the other side.
 |

**
Transmittance Multiplier
**
 |
Controls how strong the translucency effect must be.
 |

**
Vtx Alpha Blend Factor
**
 |
Used for faking AO. If you have applied some vertex paint to the base of the geometry, you can control the strength of the blend effect with this slider. Technically we don't need to use this because of technology such as SSDO, SSAO and SVOGI, but sometimes it can help the asset by using this.
 |

##
Vegetation Editor

Before we continue to configure the material params, it will help if we place some of these grass objects down using the vegetation tool to get instant visual feedback as we update the material. We will not go into an in-depth tutorial of the vegetation tool here.

For more information of the usage of the vegetation editor, please refer
**
[HERE](../../../../../Editor%20Tools/Vegetation%20Editor.md)
**
.

##
Create a vegetation category and add the grass

Navigate to the
**
Tools
**
menu option, and under the menu select the
**
Vegetation
**
 Editor.

*
![Image](https://www.cryengine.com/docs/static/attachments/25035762)

Pic9: Selecting the "Vegetation" tool
*

Add a new Group and call it something appropriate (initial name =
**
Default1
**
).

![Image](https://www.cryengine.com/docs/static/attachments/25035763)

*
Pic10: Adding a Vegetation group
*

Click the
**
Add Vegetation Object
**
(
first button
) to add a vegetation object to this group.

![Image](https://www.cryengine.com/docs/static/attachments/25035764)

*
Pic11: Adding a vegetation object to the group
*

In the browse dialog, go to your folder where you saved the asset and select the grass patch we created.

-

-
`
<
`
*
Your_Project
*
>\Assets\
`
Objects\tutorial\vegetation\01\grass_patch\tutorial_grass_patch
`

##
Place some vegetation down

Now highlight the object you just added to the group to select it, and you can perform any one of the following procedure:

-
Enable the paint objects button to paint down lots of instances your bush asset, or

-
To be more precise, do not select the paint objects button (so it's not active) and on the terrain Shift+LMB to place only 1 instance.
Paint down about 100 - 150m worth of grass over the terrain. Enough to cover most of the ground around the vicinity of the player and off into the distance. We need some distance to be able to observer the changes in the object when we modify some of the properties such as terrain color blending.

![Image](https://www.cryengine.com/docs/static/attachments/25035781)

*
Pic12: Accessing the Ruler Tool
*

Adjust the ruler tool to quickly judge distances accurately. Simply highlight the tool so its active, then click left-mouse button (LMB) where you want the start and end points of the ruler to measure.

*
![Image](https://www.cryengine.com/docs/static/attachments/24157035)

Pic12a: Unused area in the Woodland level. Using the ruler tool to judge the distance covered by the grass
*

##
Modify the properties of the grass material

With our object now placed down in a level we can adjust its properties to see the updates as we change them.

##
Normal View Dependency

Inside the Shader Params section of the material editor, first we need to set the Normal View Dependency to maximum (0.95). This value orients the normals towards the player's view and is useful for simple geometry (what our grass asset is built of, multiple planes). This feature helps to blend the individual geometry planes to provide consistent look from the same direction (your viewpoint).

##
Terrain Color Blend and Terrain Color Blend Dist

These two sliders work with each other. If you modify one, you'll probably have to change the other. The two values work in coordination with each other to control the strength of the effect and the distance to the camera where this will become active.

To use this feature within the objects material, we must enable the
**
UseTerrainColor
**
 flag inside the Vegetation Editor. Select the
**
Grass
**
 object and check the box to make it active.

![Image](https://www.cryengine.com/docs/static/attachments/24157036)

*
Pic13: Enabling the terrain color blending to be used on this vegetation object
*

Move the camera down to the player's height for a better reference, as this is where your viewpoint will be played from in the game.

Once you enable the
**
UseTerrainColor
**
 in the vegetation object, this tech is now active. Even though you have the sliders set as low as possible there will be some color bleeding from the terrain into the vegetation object at the far distance.
This enables the blending of your vegetation into its surroundings. If you do not want this to happen, you have to disable the check box in the vegetation properties.

![Image](https://www.cryengine.com/docs/static/attachments/24157026)
![Image](https://www.cryengine.com/docs/static/attachments/24157027)
![Image](https://www.cryengine.com/docs/static/attachments/24157028)

*
Pic13,14,15: Same setup, but with different blend strengths, 0, 0.5 & 1.
*

-
At strength=0 very slight coloring at the far distance

-
At strength=0.5 you can see the color affecting more of the vegetation as it comes closer to the camera

-
At strength=1 the terrain color floods all of the grass objects. Right up the camera. This is not really something you would set to, since it has completely overwritten the texture info in the grass asset.
In general, keep this in the range of 0 - 0.5, but its truly up to you where you want the terrain color to start to influence the vegetation object.
The second slider,
**
Terrain Color Blend Dist
**
, works from the end of the
**
Terrain Color Blend
**
 setting, up to the camera.

So you would set
**
Terrain Color Blend
**
 first, then you adjust the distance further with
**
Terrain Color Blend Dist
**
 to fine tune the color blend. Again, setting this to a maximum value will flood the grass with terrain color.

![Image](https://www.cryengine.com/docs/static/attachments/24157032)
![Image](https://www.cryengine.com/docs/static/attachments/24157033)
![Image](https://www.cryengine.com/docs/static/attachments/24157034)

*
Pic16,17,18: As above, Terrain Color Blend (0.5) but added on top with Terrain Color Blend Dist at values 0.01, 0.5, 0.75
*

##
Transmittance

The transmittance effect (light passing through the surface) defines the foliage thickness and how much light can pass through from the backside.

Unlike the
**
Leaves
**
 shader param, we do not get an opacity channel to use. (Since the
**
Grass
**
 shader param is the cheaper variation).
But we can still use this feature (without the opacity channel), and set a color for the transmittance and also the strength of the transmittance effect, but it will be applied over the whole asset.

-
Set the Transmittance Color to something 203,205,194 (a very light green)

-
Leave the Transmittance Multiplier to 1
Again, there is no hard and fast rule to use when picking the "back-face" color for the transmittance. It all depends on the asset color. But in general, the color has to be brighter than the front side.

##
Adding some movement to the vegetation

Now we have configured the material properties, its time to finish up with adjusting some params in the vegetation tool.

Currently the grass is very static, no movement in the grass blades. We can apply some "procedural noise" to the grass by modifying the
**
Bending
**
slider. This will act as a simple back and forth waving pattern.

There are two ways to apply some movement to the grass:

-
**
Bending
**
 property in the vegetation tool

-
**
Vertex deformation
**
 in the material

##
Bending

Using the bending property in the vegetation tool on an object, will sync up its movement with the global wind vector that you set in the environment tab. The different ways to configure the assets bending properties are:

-
First pick the global wind strength and direction, that you want in your level.

-
Then in the vegetation categories, set the amount of bending you would like to have on the asset at that level of global wind.
Then if you were to modify the global wind in the level (because there is a storm or something) as you increase the global wind strength, its effect will be multiplied through the vegetation instances bending setting. So if all the vegetation is configured to move correctly at one wind setting, as you change the global wind up and down, they should all multiply up or down in coordination with the wind strength.

![Image](https://www.cryengine.com/docs/static/attachments/24157016)

*
Pic19 : Setting the global wind strength / direction in the environment tab
*

![Image](https://www.cryengine.com/docs/static/attachments/24157031)

*
Pic20: The Bending slider to set per vegetation object
*

This is the preferred method for getting some vegetation interaction with the global wind.

##
Vertex deformation

In the material editor under the Vertex Deformation tab, we also have control over wave-type wavelength, amplitude and frequency etc...

This allows you to apply a simple wave function to run on the vegetation asset. This method of applying movement provides very consistent repeating waves. This makes the grass look as if its all moving in sync with each other and not very natural looking. You can fix this by providing a gentle effect (very low numbers).

Since this movement is applied through the material settings, it cannot take advantage of the global wind state that you set inside the
**
Environment
**
 panel.

Also note that this material setting of vertex deformation
**
overrides
**
 the bending attribute in the vegetation properties. To reset the asset to re-take advantage of the vegetation bending, setup the vertex deformation back to
**
none
**
(instead of Sin Wave in this example).

![Image](https://www.cryengine.com/docs/static/attachments/24157037)

*
Pic21: Vertex Deformation panel with Sin Wave active
*

The vertex deformation properties are quite vast where you can use different setups to control that assets movement. For more information on
**
Detail Bending,
**
 go to the following
**
[page](../Vegetation%2003%20Bushes%20(Detail%20Bending).md)
**
.

##
LODs (Level of detail)

As we set our model to contain some LODs, lets check them out in CRYENGINE.

![Image](https://www.cryengine.com/docs/static/attachments/24157017)

*
Pic 22: Recap of the LOD hierarchy in 3dsMax (dropping approx 50% polys per LOD step).
*

To help us debug the LODs, we can enable a console variables (CVar) to help;

-
e_debugdraw 3 (with help text & colors)

-
e_debugdraw -3 (without help text, only colors)
We can use this CVar to color code the assets and depending on the LOD that the asset is in, it will receive a different color. This is very helpful to quickly visualize the LOD levels. The color order for the LODs is as follows;

LOD Level
 |
Color
 |

0
 |
Red
 |

1
 |
Green
 |

2
 |
Blue
 |

3
 |
Turquoise
 |

4
 |
Yellow
 |

5
 |
Purple
 |

As we only added 2 LODs to the grass patch, when we see enable the debug view to inspect the LODs, we should only see the first 3 levels, Red, green and blue (0,1,2).

![Image](https://www.cryengine.com/docs/static/attachments/24157018)

*
Pic23: e_debugdraw -3 (color coded lod visualization)
*

To adjust where the LOD swap will happen, we control this using settings in the vegetation editor.

![Image](https://www.cryengine.com/docs/static/attachments/24157019)

*
Pic24: View Distance & LOD ratios in the vegetation editor
*

Note that we do not support vegetation sprites anymore. So modifying the slider will not impact the settings.
To get the correct view distance and LOD ratios, here is the best way to configure them according to your preferred settings:

-
Set the MaxVistDistRatio. This is going to be the final distance at which the objects will be rendered at.

-
Next, adjust the LodDistRatio. This is always calculated out from the MaxViewDistRatio. It will always try to get the full range of LODs into the maximum view distance, before it finally stops rendering.

##
MaxViewDistRatio

The value range runs from 0 - 2.55
**
(not 255)
**
 The smaller the number, the closer to the camera the vegetation will stop drawing.

##
LodDistRatio

This value works in the opposite direction. The range again runs from 0 - 2.55 . But the smaller the number, the further the distance that LOD0 will be preserved. You could phrase it as "delaying the LOD switch".

##
Final Notes

After finishing this document, you should now know the following concepts and asset setup guidelines / rules, behind the grass patch asset:

-
Setting up the hierarchy in max (LOD chain).

-
Do not add a physics proxy to a simple grass asset (not required).

-
Apply the correct material setup in CRYENGINE to take advantage of the Grass Shader Parameter.

-
Making use of the global wind to influence the assets movement through the bending attribute in the vegetation tool (or use the materials vertex deformation for the same effect, but without the link to the global wind).

-
Using the vegetation tool correctly to setup the asset.

-
Configure and debug your LOD ratios and settings.

-
Using grass patches means you
**
cannot
**
 use MergedMesh technology. So each grass object you place down has its own set of drawcalls (visualize with
**
r_stats=6
**
).

-
Do not enable MergedMesh technology on grass patches. The geometric grid setup inside the asset is too complex for the system to handle (MergedMesh technology requires simple individual grass planes, not patches).
[Material Setup in CRYENGINE](#material-setup-in-cryengine)
[Vegetation Editor](#vegetation-editor)
[Modify the properties of the grass material](#modify-the-properties-of-the-grass-material)
[Adding some movement to the vegetation](#adding-some-movement-to-the-vegetation)
[LODs (Level of detail)](#lods-level-of-detail)
[Final Notes](#final-notes)
