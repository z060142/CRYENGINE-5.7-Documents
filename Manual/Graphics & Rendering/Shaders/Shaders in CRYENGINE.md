# Shaders in CRYENGINE

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/29448758
- Page ID: 29448758
- Breadcrumb: Graphics & Rendering > Shaders > Shaders in CRYENGINE
- Parent: Shaders

## Child Pages

- [Shader Features (Shader Generation Params)](Shaders%20in%20CRYENGINE/Shader%20Features%20(Shader%20Generation%20Params).md)
- [Shader Reference](Shaders%20in%20CRYENGINE/Shader%20Reference.md)

## Content

##
Overview

The following shaders are currently available in CRYENGINE:

Shader Name

 |
Description

 |

[DistanceClouds Shader](Shaders%20in%20CRYENGINE/Shader%20Reference/DistanceClouds%20Shader.md)

 |
Used by Environment Artists to create 2D DistanceClouds.

 |

[Eye Shader](Shaders%20in%20CRYENGINE/Shader%20Reference/Eye%20Shader.md)

 |
Used by Character Artists to create the eyes of characters. Can also control the amount of dynamic pupil dilation.

 |

[Glass Shader](Shaders%20in%20CRYENGINE/Shader%20Reference/Glass%20Shader.md)

 |
Used by Artists to create glass. Comes with specific features that are tailored for glass use and also specific breakability functionality.

 |

[Hair Shader](Shaders%20in%20CRYENGINE/Shader%20Reference/Hair%20Shader.md)

 |
Used by Character Artists to create hair. Gives wide control over coloring and physicalization options.

 |

[HumanSkin Shader](Shaders%20in%20CRYENGINE/Shader%20Reference/HumanSkin%20Shader.md)

 |
Used by Character Artists and offers a wide variety of options to achieve realistic looking skin.

 |

[Illum Shader](Shaders%20in%20CRYENGINE/Shader%20Reference/Illum%20Shader.md)

 |
The most commonly used shader, can be used to create an extremely wide variety of effects. If there is no specific shader for the type of effect you are trying to achieve, use the Illum Shader.

 |

[Multilayeredmaterials Shader](Shaders%20in%20CRYENGINE/Shader%20Reference/Multilayeredmaterials%20Shader.md)
 |
A shader tha can be used to combine different layers of materials to achieve unique and realistic surfaces.
 |

[NoDraw Shader](Shaders%20in%20CRYENGINE/Shader%20Reference/NoDraw%20Shader.md)

 |
Used for physics proxy. The NoDraw Shader forces the Engine to not render the geometry on which the shader is applied. There are no specific Shader Params.

Alternatively, for level design it may be preferable to use
`
Materials/special/collision_proxy_entitiesonly
`
, so that you can see the solid in Editing mode, but not in Game mode.

 |

[ParticleImposter Shader](Shaders%20in%20CRYENGINE/Shader%20Reference/ParticleImposter%20Shader.md)

 |
The ParticleImposter shader is used to create particle effects that are not affected by light and hence do not cast shadows or cause reflections.

 |

[Particles Shader](Shaders%20in%20CRYENGINE/Shader%20Reference/Particles%20Shader.md)

 |
Used by Artists who require particle effects.

 |

[ReferenceImage Shader](Shaders%20in%20CRYENGINE/Shader%20Reference/ReferenceImage%20Shader.md)

 |
Forces the Engine to render the object without any shading or post-processing effects.

 |

[Sky Shader](Shaders%20in%20CRYENGINE/Shader%20Reference/Sky%20Shader.md)

 |
Is only used for creating the sky box. The Sky Shader has no parameters, and the materials can only be applied through the Material settings via the Material Editor.

 |

[SkyHDR Shader](Shaders%20in%20CRYENGINE/Shader%20Reference/SkyHDR%20Shader.md)

 |
Is the same as the Sky Shader, with the exception, that if you want to use a dynamically changing sky through the Time Of Day settings, then you always have to use the SkyHDR Shader.

 |

[TemplBeamProc Shader](Shaders%20in%20CRYENGINE/Shader%20Reference/TemplBeamProc%20Shader.md)

 |
The TempleBeamProc Shader can be used to create very cheap fog light beam effects.

 |

[Terrain.Layer Shader](Shaders%20in%20CRYENGINE/Shader%20Reference/Terrain.Layer%20Shader.md)

 |
Used for all the terrain materials for painting terrain texture layers.

 |

[Vegetation Shader](Shaders%20in%20CRYENGINE/Shader%20Reference/Vegetation%20Shader.md)

 |
Used for all vegetation.

 |

[Water Shader](Shaders%20in%20CRYENGINE/Shader%20Reference/Water%20Shader.md)

 |
Used for the ocean.

 |

[WaterVolume Shader](Shaders%20in%20CRYENGINE/Shader%20Reference/WaterVolume%20Shader.md)

 |
Used for water volumes and rivers.

 |

##
 In This Topic

-
[Shader Features (Shader Generation Params)](Shaders%20in%20CRYENGINE/Shader%20Features%20(Shader%20Generation%20Params).md)

-
[Shader Reference](Shaders%20in%20CRYENGINE/Shader%20Reference.md)
