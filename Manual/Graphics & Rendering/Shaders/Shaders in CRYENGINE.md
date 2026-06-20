# Shaders in CRYENGINE

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/29448758
- Page ID: 29448758
- Breadcrumb: Graphics & Rendering > Shaders > Shaders in CRYENGINE
- Parent: Shaders

## Child Pages

- [Shader Features (Shader Generation Params)](Shaders in CRYENGINE/Shader Features (Shader Generation Params).md)
- [Shader Reference](Shaders in CRYENGINE/Shader Reference.md)

## Content

##
Overview

The following shaders are currently available in CRYENGINE:

Shader Name

 |
Description

 |

[/docs/static/engines/cryengine-5/categories/23756816/pages/29448860](
DistanceClouds Shader
)

 |
Used by Environment Artists to create 2D DistanceClouds.

 |

[/docs/static/engines/cryengine-5/categories/23756816/pages/29448900](
Eye Shader
)

 |
Used by Character Artists to create the eyes of characters. Can also control the amount of dynamic pupil dilation.

 |

[/docs/static/engines/cryengine-5/categories/23756816/pages/29448946](
Glass Shader
)

 |
Used by Artists to create glass. Comes with specific features that are tailored for glass use and also specific breakability functionality.

 |

[/docs/static/engines/cryengine-5/categories/23756816/pages/29448981](
Hair Shader
)

 |
Used by Character Artists to create hair. Gives wide control over coloring and physicalization options.

 |

[/docs/static/engines/cryengine-5/categories/23756816/pages/29449035](
HumanSkin Shader
)

 |
Used by Character Artists and offers a wide variety of options to achieve realistic looking skin.

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
A shader tha can be used to combine different layers of materials to achieve unique and realistic surfaces.
 |

[/docs/static/engines/cryengine-5/categories/23756816/pages/29449083](
NoDraw Shader
)

 |
Used for physics proxy. The NoDraw Shader forces the Engine to not render the geometry on which the shader is applied. There are no specific Shader Params.

Alternatively, for level design it may be preferable to use
`
Materials/special/collision_proxy_entitiesonly
`
, so that you can see the solid in Editing mode, but not in Game mode.

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
Used by Artists who require particle effects.

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
Is only used for creating the sky box. The Sky Shader has no parameters, and the materials can only be applied through the Material settings via the Material Editor.

 |

[/docs/static/engines/cryengine-5/categories/23756816/pages/29449154](
SkyHDR Shader
)

 |
Is the same as the Sky Shader, with the exception, that if you want to use a dynamically changing sky through the Time Of Day settings, then you always have to use the SkyHDR Shader.

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

##
 In This Topic

-
[/docs/static/engines/cryengine-5/categories/23756816/pages/29449533](
Shader Features (Shader Generation Params)
)

-
[/docs/static/engines/cryengine-5/categories/23756816/pages/29448786](
Shader Reference
)
