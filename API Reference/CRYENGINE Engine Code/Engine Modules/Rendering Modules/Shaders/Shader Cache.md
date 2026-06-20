# Shader Cache

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/23306643
- Page ID: 23306643
- Breadcrumb: CRYENGINE Engine Code > Engine Modules > Rendering Modules > Shaders > Shader Cache
- Parent: Shaders

## Child Pages

- [Remote Shader Compiler](Shader%20Cache/Remote%20Shader%20Compiler.md)
- [Generating Shader Combinations](Shader%20Cache/Generating%20Shader%20Combinations.md)
- [ShaderCache Generation](Shader%20Cache/ShaderCache%20Generation.md)

## Content

##
Overview

The Shader Cache is a collection of parsed and pre-compiled shaders.

During the play of a level, at runtime, necessary shaders will be requested with all the variables defined, such as lighting configuration and the usage of techniques like fog or transparency.
If a shader is not found in the Shader Cache, it will have to be compiled locally or via a Remote Shader Compiler.

Since all shader code is written in HLSL and cross compiled to other platforms, shader compilation is only possible on a Windows PC. Other platforms, such as consoles or systems relying on an OpenGL rendering backend need to have the shaders pre-compiled or be able to access a Remote Shader Compiler (for development only).

Because the number of possible shader configurations in abstract is huge, the possibilities for a given game need to be calculated into a list, so that they can be pre-compiled and packed into a shader cache.

A Shader Cache is necessary in any platform in order for the game to run smoothly without noticeable freezes or visual glitches.

More information on the shader cache can be found in the following topics:

-
[Remote Shader Compiler](Shader%20Cache/Remote%20Shader%20Compiler.md)

-
[Generating Shader Combinations](Shader%20Cache/Generating%20Shader%20Combinations.md)

-
[ShaderCache Generation](Shader%20Cache/ShaderCache%20Generation.md)
The shader cache generally refers to the following files:

Chapters:

Related Pages:

File
 |
Description
 |

**
Shaders.pak
**
 |
Contains the shader source files (everything inside the
`
Engine/Shaders/
`
 folders excluding
`
EngineAssets
`
). The actual shader source code (*.cfi and *.cfx) can be removed from this pak for the final released version, and is not needed anymore when the binary shaders are valid and available.
 |

**
ShadersBin.pak
**
 |
Contains the binary parsed shader information of the shader source code.
 |

**
ShaderCache.pak
**
 |
Contains the compiled shaders of all the possible combinations which have been submitted to the remote shader compiler. Generally referred to as the global shader cache.
 |

**
ShaderCacheStartup.pak
**
 |
Small subset of the global shader cache, containing only the shaders which are used during the startup phase into the menu. The small pak file is loaded into memory for fast startup times, and is not required to be there. Startup times will be slower when the file is not available.
 |
