# Decal Texture

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/27593380
- Page ID: 27593380
- Breadcrumb: Asset Prep (External) > Asset Exporting Overview > Texture Creation Overview > Decal Texture
- Parent: Texture Creation Overview

## Content

![Image](https://www.cryengine.com/docs/static/attachments/29933276)

##
Overview

##
Sections

In this tutorial you'll learn how decals are created from a texture perspective, how to setup materials for decals and how to place them in Sandbox.

[Sections](#sections)
[Texture Setup](#texture-setup)
[Material Setup](#material-setup)
[Sandbox Setup](#sandbox-setup)

##
Texture Setup

The main difference with a decal diffuse texture is that it should have an alpha channel to control what parts of the RGB channels are visible.

 |
 |

Diffuse RGB Channels
 |
Diffuse Alpha Channel
 |

In this example we're going to use a concrete decal, with the main "feature" being a large crack. This will be useful in breaking up tiling and monotony on standard concrete materials.

You can see in the above images the alpha channel closely resembles the RGB channel information, but is acting as a mask. The white resembles where the RGB content is shown, black defines where the RGB is not shown.

Below you can see a comparison of how the Alpha channel controls visible content.

 |
 |

Decal Diffuse with no Alpha
 |
Decal Diffuse with Alpha
 |

After you've got your textures completed, save them in an appropriate place such as:
`
<root>/GameSDK/Textures/decals/concrete/
`

##
Material Setup

Open the Material Editor (press 'M' on the keyboard while the perspective view is active) or click on the material sphere button in the toolbar, or via
**
View -> Open View Pane -> Material Editor
**
.

With the Material Editor open, we can now create a new material for our decal texture.

Click on the
**
Add New Item
**
 button in the toolbar.

Now select an appropriate folder where you want to save the material file. In order to keep things consistent, lets save it alongside our existing decal materials.

By default, the location of these materials won't be visible in the file dialog because they're zipped up inside the
[GameData.pak](/docs/static/engines/cryengine-3/categories/1638401/pages/1605746)
. But we can manually create the path:
`
<root>/GameSDK/Materials/decals/concrete/concrete_crack_new.mtl
`

After you save the material, the Material Editor will automatically select your new material and apply default settings to it to get you started.

Lets start customizing this new material by
[adding the Diffuse texture](/docs/static/engines/cryengine-3/categories/1114113/pages/1048667)
 which we created earlier in the Texture Setup section.

We've already got the
[Illum Shader](/docs/static/engines/cryengine-3/categories/1114113/pages/1048911)
 selected by default and you don't need to specify surface types for decals, as they're purely a visual projection with no surface logic behind them.

In the Shader Gen Parameters, just enable the
**
Decal
**
 checkbox so that the engine understands this material is to be used by the
[Decal entity](/docs/static/engines/cryengine-3/categories/1114113/pages/1048871)
.

As of CRYENGINE 3.6, a few additional parameters have been added to Decals to control Alpha Multiplier/Falloff as well as Opacity.

##
Examples

 |
 |

Standard, Planar Projection
 |
Diffuse Opacity 0.5
 |

 |
 |

Alpha Falloff 10
 |
Alpha Falloff 128
 |

 |
 |

Alpha Multiplier 2
 |
Alpha Multiplier 10
 |

Note that currently these only affect Planar, non-deferred decals.
We can leave all other settings default for now as we'll tweak those further once the decal is in the level.

##
Sandbox Setup

Lets start with a small, basic level. See
[Creating a New Level](/docs/static/engines/cryengine-3/categories/1114113/pages/1048859)
 for more information.

Place a few concrete objects in and have them all use the same, tiling concrete texture for an extreme example.

Now place a Decal in the level by going to
**
RollupBar -> Objects -> Misc -> Decal
**

You should see the decal object with its default "Replace Me" material applied.

Check you've enabled "
[Follow Terrain and Snap to Objects](/docs/static/engines/cryengine-3/categories/1114113/pages/1048827#ManipulatingObjects-PlacingandModifyingObjects-AdvancedObjectManipulation)
" before you bring it into the level to help with navigation.
Now, with the Decal still selected, click on the Material button in the RollupBar to open the Material Editor.

Right-click on your new Decal material in the list and choose
**
Assign to Selected Objects
**
.

The first button in the toolbar of the Material Editor also does this same function: Assign Item to Selected Objects. Hover over icons with your mouse to reveal tool-tips!

Now our Decal looks like this:

Experiment with placing numerous decals with various sizes and rotation to try and break up the scene.

##
Examples

An easy way to get decals to follow the contours of objects is to set them to Deferred (or "Project on Static Objects").

 |
 |

Planar Projection
 |
Deferred Projection
 |

You can also tweak settings such as projection depth to get different blend amounts. This also works based off the distance the decal is from the object.

 |
 |

Projection Depth 0.5
 |
Projection Depth 1
 |

Keep in mind this is just one base concrete material and one decal. The more flavor you add, the better the final result will be!

 |
 |

Without Helpers
 |
With Helpers
 |
