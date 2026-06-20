# Eye Shader

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/29448900
- Page ID: 29448900
- Breadcrumb: Graphics & Rendering > Shaders > Shaders in CRYENGINE > Shader Reference > Eye Shader
- Parent: Shader Reference

## Content

##
Overview

The eye shader is a specialized shader for rendering eyes. Eyes are very complex not only in shading but also in composition, therefore their shading/look cannot be achieved via regular shading methods.

[Image: /docs/static/attachments/35397791]

##
Shader Parameters

Shader Params

 |
Description

 |

**
Cornea Refraction
**

 |
With this slider the eyes pupil size can be controlled, and potentially animated

 |

**
Cornea Smoothness
**

 |
Controls the glossiness of the corneas reflections. The default 1 gives smaller and sharper highlights much as in real life.

 |

**
Iris Color
**

 |
Tweaks the Iris color without affecting the eye white, can potentially be used for eye variation between characters using the same texture.

 |

**
Iris Depth
**

 |
Simulates the actual form of the Iris, since the in-game mesh has the shape of a sphere.

 |

**
Iris Shadowing
**

 |
Selfshadowing of the Iris, further simulating the actual form of the iris. Note that this shader effect is only affected by sunlight and not by other light sources.

 |

**
Iris SSS
**

 |
The SSS of the Iris, blurring the shadows. The higher the value the more it blurs the shading.

 |

**
Sclera SSS
**

 |
Controls the SSS of the eye whites, blurring the shadows. The higher the value the more it blurs the shading.

 |

**
Depth bias scale
**

 |
Sets the depth bias of the overlay mesh to avoid clipping with the eyes.

 |

**
Diffuse occlusion strength
**

 |
Controls how strong the occlusion effect on the eyes is.

 |

**
Specular occlusion strength
**

 |
Controls how strong the occlusion effect on the eyes specular highlights are.

 |

##
Shader Generation Params

**
Shader Gen Params
**

 |
Description

 |

**
Environment Map
**

 |
If the blending cube map feature is not used this box needs to be marked, and “nearest_cubemap” needs to be assigned in the environment slot of the textures.

 |

**
Ambient Occlusion Overlay
**

 |
Needs to be turned on for the occlusion mesh that overlays the eye. This mesh gives the eyes a more natural shadowing and integrates them with the head.

 |

**
Specular Overlay
**

 |
Used for the eye water mesh.

 |

##
Eye Anatomy

[Image: /docs/static/attachments/35397792]

An eye is made of several "components". The most relevant ones in this case are:

-
The sclera (white area).

-
The iris (where eye color comes from).

-
The pupil (the dark spot in middle).

-
The eye cornea (the "windshield" of the iris).
The eye shader simulates these components using various techniques in a single draw call.

##
In-Game Eye Parts

The first step is to setup the meshes needed for the eye. There are 5 meshes used to create a believable eye.

[Image: /docs/static/attachments/35397793]

-
**
The eye ball
**
: Rather simple. Just a small sphere/hemisphere.

-
**
The eye water
**
: A slim mesh surrounding the eye and tear duct. Provides the wetness surrounding the edges of an eye.

-
**
The eye tear duct
**
: Rather simple. Just a small mesh representing the tear duct. Uses a standard Illum shader. This part could potentially be part of the actual head mesh.

-
**
The eye occlusion mesh
**
: A small mesh that covers the gap between the eye lids that is used for ambient occlusion.

-
**
The eye lashes
**
: A simple mesh with an alpha blended eye lash texture applied. See:
[/docs/static/engines/cryengine-5/categories/23756816/pages/29448981](
Hair Shader
)
.
The modeling process is relatively straightforward. The eye occlusion mesh and the eye water topology should have the same density and align with the eye lids edge loops; this is to make the skinning easier and animations smooth.

[Image: /docs/static/attachments/28898482]

##
Textures

When setting up the UVs it’s crucial that the pupil and iris are centered in the middle of the UV space, otherwise some of the shader features will not work properly. The textures should follow these guidelines:

##
Eye ball

-
The diffuse map is used as the main source of color.

-
The alpha map defines the Iris and Pupil for the eye shader.

-
The normal maps give the necessary normal information for the eye.

-
The first Normal map works as a regular one giving detail to the inner layer of the eye.

-
The Cornea normal map defines the surface shape of the eye.

-
The displacement map provides the information for how the iris and pupil should deform, this information is stored in the alpha of the texture (as standard for all _displ textures).

-
The Iris Depth slider under Shader Params can further tweak the intensity of the displacement.
[Image: /docs/static/attachments/28898490]

Previous versions of the Eye shader had a dedicated "Subsurface" map but this is obsolete with the current Eye shader, as this masking information is received from the Diffuse Alpha channel and controlled with the Iris/Sclera SSS sliders.

##
Eye Water

-
The specular map defines where the highlights should occur.
Even if it’s a specular map it hooks up to the diffuse slot of the texture maps.
[Image: /docs/static/attachments/28898484]

##
Tear Duct

-
This mesh uses the standard
[/docs/static/engines/cryengine-5/categories/23756816/pages/29449070](
Illum Shader
)
 and works as regular assets when it comes to the texture maps.

##
Eye Occlusion

-
The diffuse map defines where and how much occlusion should appear.

-
The strength can be later on be controlled with the Diffuse occlusion strength slider under Shader Params.

-
The specular map defines where and how much occlusion should appear on the specular highlights.

-
The strength can be later on be controlled with the Specular occlusion strength slider under Shader Params.
[Image: /docs/static/attachments/28898481]

##
Eye Lashes

This mesh works as a regular hair setup. See:
[/docs/static/engines/cryengine-5/categories/23756816/pages/29448981](
Hair Shader
)
.

##
Shader Texture Setup Examples

##
Eye Ball

[Image: /docs/static/attachments/28898489]

##
Eye Occlusion

[Image: /docs/static/attachments/28898486]

##
Eye Water

[Image: /docs/static/attachments/28898487]

##
Shader Params Examples

[Image: /docs/static/attachments/28898485]

[#shader-parameters](
Shader Parameters
)
[#shader-generation-params](
Shader Generation Params
)
[#eye-anatomy](
Eye Anatomy
)
[#in-game-eye-parts](
In-Game Eye Parts
)
[#textures](
Textures
)
[#shader-texture-setup-examples](
Shader Texture Setup Examples
)
[#shader-params-examples](
Shader Params Examples
)
