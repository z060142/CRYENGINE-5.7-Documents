# TemplBeamProc Shader

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/29449224
- Page ID: 29449224
- Breadcrumb: Graphics & Rendering > Shaders > Shaders in CRYENGINE > Shader Reference > TemplBeamProc Shader
- Parent: Shader Reference

## Content

## Overview

The TemplBeamProc Shader can be used to create very cheap fog light beam effects.

### How To Create a Cheap Fog Light Beam

- Create a 3D object with a back plane and 4 intersecting planes like this:
![Image](https://www.cryengine.com/docs/static/attachments/28898590)
- Create a texture (all faces share UVs) with the following contents:
![Image](https://www.cryengine.com/docs/static/attachments/28898587)

This texture is only gray scale and has no alpha.

The TemplBeamProc Shader can handle fading out rendering faces, that are at a certain angle to the camera. It's best to use sub-materials for the different parts because you can control the angle of visibility, so the back plane gets 1 sub-material and the other planes get 1 sub-material.

This effect is very cheap. Between 1 and 2 drawcalls, depending on how you set it up. Please make sure that this is only the fog light effect – a light still has to be placed.

### Tips

- Although the shader doesn't seem to produce shadows, check the **No Shadow** option to make sure.
- The opacity must be set to 100% - the shader itself controls the opacity and you have enough control due to diffuse color, diffuse multiplier, etc.
- With the diffuse color, you can set the color and brightness of your light beams. It is suggested to not use only 1 RGB channel, in order to get good results (avoid 255,0,0 and similar stuff). Always try to give every channel at least a small percentage.
- Use the texture with no alpha and gray scale as diffuse.
- The Shader Params give you control over the blending but also the render size of the beam.

### Shader Params

**Shader Params** | **Description**
--- | ---
**Color Multiplier** | Increase/decrease brightness and blending.
**End Color** | Set the end color for the gradient.
**End Radius** | Set the radius (in meters) of the effect at the end of the object.
**Length** | Adjust the scaling of the rendered effect (like scaling of the actual mesh).
**Original Length** | Scaling factor. If the length and original length are the same, the object has a scale of 100%.
**Original Width** | Same as above.
**Soft Intersection Factor** | Controls softness of surface interaction with other opaque scene geometry.
**Start Color** | Set the start color for the gradient.
**Start Radius** | Set the radius (in meters) of the effect at the start of the object.
**View Dependency Factor** | Controls the blending in and out depending on the facing angle to the camera. The higher the value, the longer it will be visible even when nearly 90° to the camera, the smaller the value the earlier it will start to vanish.

### Shader Generation Params

Shader Gen Options | Description
--- | ---
**Noise Map** | Gives a nice motion to the beams but cannot be controlled by any parameters.
**Muzzleflash** | Option to be used for muzzle flash.

### Examples

![Image](https://www.cryengine.com/docs/static/attachments/28898589)

[How To Create a Cheap Fog Light Beam](#how-to-create-a-cheap-fog-light-beam)[Tips](#tips)[Shader Params](#shader-params)[Shader Generation Params](#shader-generation-params)[Examples](#examples)
