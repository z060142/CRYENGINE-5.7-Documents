# _Shaders

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/26216243
- Page ID: 26216243
- Breadcrumb: _Shaders

## Content

##
Overview

**
Shaders
**
allow to mathematically calculate the color of pixels rendered, based on data sent by the engine such as lighting and textures from materials. This means that the full flow from
object
 to shader becomes:

-
Geometry (
*
.cgf, .cdf, .chr, .skin, .cga
*
)

-
Material (
*
.mtl
*
)

-
Shader Item
Keep in mind that any material can have multiple sub-materials - this means that multiple shaders have to be drawn separately via unique
**
draw calls
**
. This is a major reason for keeping the number of materials down, as each additional sub-material requires a separate request to the GPU.

##
Table of Contents

[#the-shader-directory](
The Shader Directory
)
[#extension-files](
Extension Files
)
[#the-common-techniques](
The Common Techniques
)
[#shader-editing](
Shader Editing
)

##
The Shader Directory

Shaders are contained inside the
*
Shaders/
*
 directory, and can be loaded from either
*
Engine/Shaders/
*
 for the default engine shaders, or
*
<asset folder>/Shaders/
*
. A shader is defined by the
*
.cfx
*

extension, and are contained inside
*
Shaders/HWScripts/CryFX/
*
. At engine startup, a search for
*
 .cfx
*
 files will be performed, resulting in all shader source files being parsed and added to the internal shader registry.

##
The Shader Format (.cfx)

CRYENGINE shaders are written in a custom shader format that is very similar to HLSL.

Most commonly, materials in the engine will use the Illum shader - as this is already set up to go through the common shader paths. This is defined in
*
Engine/Shaders/HWScripts/CryFX/Illum.cfx
*
. For a more simple example, see the ReferenceImage shader in
*
Engine/Shaders/CryFX/ReferenceImage.cfx
*
. This shader is much more light-weight and is intended to draw a diffuse texture without in-engine lighting affecting or distorting the image.

Once a .cfx file has been discovered, it is parsed to detect script information, denoted by the variable name
*
'Script'
*
, typically provided at the top of your shader source file as follows:

```

`
// Shader global descriptions
float Script : STANDARDSGLOBAL
<
  string Script =
    // Determines if the shader will be made visible to UI elements
    // For example, if set the shader will be available in the Material Editor
    "Public;"
    // If set when SupportsFullDeferredShading is not set, we go through the tiled forward pass
    // In the tiled forward case, we will execute the pass defined in this file - and not Common*Pass
    "SupportsDeferredShading;"
    // Determines that the shader supports fully deferred shading, so will not go through the forward pass
    "SupportsFullDeferredShading;"
>;
`

```

After the main script declaration, we typically include common headers that we will utilize using the
**
'#include'
**
 macro, just like we would in C++. Includes in the engine's shader system are denoted by the
*
.cfi
*
 extension. For example:

```

`
#include "ShadeLib.cfi"
`

```

...would automatically find and include the ShadeLib.cfi file inside the
*
Shaders/HWScripts/CryFX/
*
 directory. The common headers are followed by definitions of the techniques and shaders that we will use. For example:

```

`
vert2FragGeneral MyVertexShader(app2vertGeneral IN)
{
  vert2FragGeneral OUT = (vert2FragGeneral)0;
  streamPos vertPassPos = (streamPos)0;
  vs_shared_output(IN, OUT, vertPassPos, true);

  return OUT;
}

pixout MyPixelShader(vert2FragGeneral IN)
{
  pixout OUT = (pixout)0;
  OUT.Color.rgb = GetDiffuseTex(diffuseTex, IN.baseTC);
  OUT.Color.a = 1;
  return OUT;
}
`

```

However, these shaders won't be executed immediately - we have to define the General technique that defines our shaders behavior. This is typically done at the very bottom of the file:

```

`
technique General
<
  string Script =
        "TechniqueZ=ZPass;"
    "TechniqueZPrepass=ZPrepass;"
        "TechniqueMotionBlur=MotionBlurPass;"
        "TechniqueCustomRender=CustomRenderPass;"
        "TechniqueShadowGen=ShadowGen;"
        "TechniqueDebug=DebugPass;"
>
{
  pass p0
  {
    VertexShader = MyVertexShader() GeneralVS;
    PixelShader = MyPixelShader() GeneralPS;
    ZEnable = true;
    ZWriteEnable = true;
    CullMode = Back;
  }
}
`

```

In the example above, the Main shader technique is set up to use sub-techniques imported in the engine. This ensures that we go through the common deferred path of the engine, instead of having to rewrite all aspects of each shader every time. The most important aspect for us here, is defining use of the common depth buffer technique, defined in
*
Engine/Shaders/HWScripts/CryFX/CommonZPass.cfi
*
. For more information, see "The Common Techniques" further below.

After defining sub-techniques, we defined the main pass of our shader to use in the case of forward rendering. In our example, this means setting up the vertex and pixel shaders we defined above to be called. If you want to go through the forward path at all times, remove the  "SupportsDeferredShading;" and "SupportsFullDeferredShading;" strings from the script declaration at the top of the file.

##
Extension Files

Once a shader is done parsing, the engine looks for a
*
.ext
*
 file with the same name as our shader (
*
.cfx
*
) inside the
Shaders/
 directory. This file is optional, and allows for exposing properties that can be applied to each material by the user. For example, the
*
Engine/Shaders/HWScripts/CryFX/Illum.cfx
*
 file has an equivalent extension file called
*
Engine/Shaders/Illum.ext
*
.

For example, we could add a property like this:

```

`
Property
{
  Name = %MY_PROPERTY
  Mask = 0x100
  Property    (My Property Name)
  Description (Creates a shader permutation that does fancy stuff!)
}
`

```

Once created, a tick-box appears inside the material editor when a material with your shader is selected. This allows for ticking our property, applying the mask to the material's shader generation flags and letting us catch the use of the property inside one of our shader functions:

```

`
#if %MY_PROPERTY
  // Custom property logic here
#endif
`

```

This effectively creates a variation of our shader where a number of options are toggled on or off - usually referred to as a
**
shader permutation
**
. Properties are stored as flags, which is why we need a mask to define the bit that identifies whether or not our property is set.

Keep in mind that additional flags beyond properties can be set, the different types are:

Flag type
 |
Description
 |

Engine
 |
This type of flag is directly exposed by the engine. Engine flags contain general information like the supported shader model or the platform on which the engine is currently running.
 |

Material
 |
The properties that we mentioned above are referred to as material flags, and are evaluated at compile-time, so they cannot be modified at run-time. These are typically exposed to designers via the Material Editor.
 |

Runtime
 |
Runtime flags are dynamically set and unset by the engine during rendering. They make it possible to disable a special feature if it is not required for the current object in the current stage of the rendering pipeline. All available run-time flags are defined in the extension file
*
Engine/Shaders/RunTime.ext
*
.
 |

##
The Common Techniques

The example we used above referenced common techniques such as ZPass and ZPrePass. These techniques define a common ground between the  engine's shaders, ensuring that we re-use functionality and go through similar paths instead of having an inconsistent pipeline.

This article will not go into the detail of all of the techniques, but will instead focus on the two that matter most - the depth pass, referred to in the engine as the Z pass.

To start, we'll open up
*
Engine/Shaders/HWScripts/CryFX/CommonZPass.cfi
*
. At the very bottom is a definition of the 'ZPass' technique that we ended up referencing above. This defines which shaders to use, in our case we'll focus on:

```

`
VertexShader = Common_ZPassVS() ZVS;
PixelShader = Common_ZPassPS() ZPS;
`

```

This sets the two functions to use for the vertex and pixel shaders, with the actual functions being defined further up in the file. This knowledge can be used to insert common effects, for example to modify the output color of our material. Note that since the depth pass is included into our source file, we can always reference our material flags to support custom effects that are only activated for our material - instead of affecting all shaders going through the regular pipeline.

##
Shader Editing

During development, the engine will automatically compile shader permutations on demand as they are used. However, run-time reloading is also implemented and can be enabled by setting the
**
r_ShadersEditing
**
 CVar to a value of 1. This ensures that when a file change is detected in a .cfx file, the shader is automatically recompiled.

Additionally, we can set
**
r_ReloadShaders=1
**
to manually force a reload of all shaders in the scene.
