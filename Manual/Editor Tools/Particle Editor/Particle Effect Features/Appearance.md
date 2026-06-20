# Appearance

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/36868247
- Page ID: 36868247
- Breadcrumb: Editor Tools > Particle Editor > Particle Effect Features > Appearance
- Parent: Particle Effect Features

## Content

## Overview

The Appearance category controls how the particles are supposed to look when rendered.

The following options are available under the Appearance category:

### Lighting

Particles are fully integrated with CRYENGINE's scene lighting. This feature provides the ability to control how particles interact with scene illumination. Particle rendering is an approximate of Physically Based Rendering (PBR), and all parameters will be in physical terms.

Properties | Description
--- | ---
**Diffuse** | The fraction of light that is reflected diffusely from the particle surface.This is a pure fraction from 0 to 1, as opposed to a percentage.
**Back Light** | Specifies the amount of light that can go through the particle to simulate basic scattering. With a value of 0 a particle behaves as a complete solid; the particles will have full brightness towards the light source and will be completely dark in the opposite direction. With a value of 1, a particle becomes isotropic and the particles will reflect diffused light equally in all directions. Fully isotropic particles might look dimmer than the solid or scattering particles, this is due to the laws of conservation of energy.
**Emissive (kcd/m2)** | Specifies the amount of light that a particle can emit. This value is measured in kcd/m2 (kilo-candela per square meter) or knits (kilo-nits). This setting only affects apparent brightness on the surface and does not actually cast light onto the scene. This feature can be paired with [Light](Light.md) for the full effect.
**Curvature** | Enables the surface of a particle to be considered as a sphere, even though a particle tends to be flat in shape. This allows the user to add a significant amount of depth and volume to a particle effect. When the value is set to 0, particles that are illuminated will be considered as totally flat. When the value is set to 1, particles that are illuminated will be considered as perfect spheres. Curvature is achieved by bending the normals of each vertex of the particle.
**Environment Lighting** | Enables illumination from environment probes for a greater consistency with other objects in the scene.
**Receive Shadows** | Enables a particle to receive shadow from the sun. It is recommended not to enable this option unless strictly necessary, since it requires a significant amount of processing time in the renderer.
**Affected by Fog** | Specifies whether a particle should be affected by environmental fog.
**Volume Fog** | Renders the effects as a fog volume. This option is currently non-functional but will be fixed in a future release.

### Material

This feature allows you to set up material particles that will be used in rendering an effect. You can either provide a simple texture or you can use a CRYENGINE material.

Properties | Description
--- | ---
**Material** | Lets you use a CRYENGINE material to render this particle. This option overrides texture.
**Texture** | Provides a single albedo texture to the particle if no Material is assigned.

### Opacity

Opacity of a particle can be used to set the amount of transparency of each particle. In graphics, this feature is known as the alpha channel. While the alpha channel of a texture can specify how translucent a particle should look per pixel, the opacity option specifies the amount of transparency of a particle.

The CVar **r_UseZPass** must be set to **2 or a greater value** for depth buffering (also known as Z-buffering) to work. If not, the particles will render in the transparent pass as normal, without proper depth sorting.

Properties | Description
--- | ---
**Value** | Controls the alpha test threshold. If it is set to **0.25**, only texels with alpha ** above 0.75** will render.
**Blend Mode** | The following options are available in the**Blend Mode:** - ** Opaque -** Disables blending completely. - ** Alpha -** Enables regular alpha blending using the alpha channel from the albedo texture. - ** Additive -** Accumulates particles additively. - ** Multiplicative -** Accumulates particles with multiplication.
**Soft Intersect** | Enables soft intersection of particles against a scene. Even though it can cost additional fill-rate, it prevents hard-edge intersections against the scene. This option is only available if **Blend Mode** is ** not** set to ** Opaque**.
**Alpha Scale** | Only available if **Blend Mode** is ** not** set to ** Opaque**. Enables you to set the opacity of the particle. The values specify the opacity to be used when alpha = 0 and alpha = 1. An opacity value of 0 provides full transparency and thus makes the particle invisible, while an opacity value of 1 has the particle fully use the diffuse texture alpha channel. Any value outside of this range will be clamped to 0 or 1. By default the Alpha Scale = 0 and 1, meaning that the Alpha Value directly maps onto opacity.
**Clip Low** | Provides the lowest texture alpha value to a render. All values below this will be transparent (not rendered). These values specify the clip value to be used when alpha = 0 and alpha = 1. By default, **Clip Low** values are set as ** 0** ** and 0**, which means no alpha clipping can be performed. Setting these values to a ** non-zero value** will enable alpha clipping.
**Clip Range** | Provides the number of texture alpha values to be used for feathering during alpha clipping. These two values specify the feathering range to be used when alpha = 0 and alpha = 1.
**Cast Shadows** | If **Blend Mode** is set to ** Opaque**, this option appears. If it's set to ** true**, it will make the opaque particles cast shadows. Shadow casting depends on the CVar ** r_UseZPass**. It needs to be set to ** 2 or a greater value**; otherwise the particles will not cast shadows.

#### Alpha Clipping Examples

Alpha Scale | Clip Low | Clip Range | Function
--- | --- | --- | ---
0, 1 | 0, 0 | 1, 1 | Standard alpha function. Opacity scales from 0 to 1 (default behavior).
1, 1 | 1, 0 | 0, 0 | Hard alpha clipping. Texture alpha cutoff point ranges from 1 (fully visible) to 0 (invisible), with no transparency.
1, 1 | 1, 0 | 1, 1 | Soft alpha clipping, with transparency. Texture alpha cutoff point ranges from 1 to 0 and opacity values above this point scale from 0 to 1.
0, 1 | 1, 0 | 1, 1 | Opacity scaling with clipping. Opacity scales from 0 to 1 and texture alpha cutoff ranges from 1 to 0.

### Texture Tiling

This feature allows you to split particle texture coordinates into multiple tiles, and displays only one tile every time. This enables you to add variation or animations to a particle.

Properties | Description
--- | ---
**TilesX, TilesY** | Lets you specify the number of tiles that a texture can be split into (on each dimension).
**Tile Count** | Lets you specify the total number of valid tiles for this component (may be less than TilesX * TilesY). If no animation parameters are specified, then it uses the number of variant tiles for individual particles.
**First Tile** | Lets you specify the first valid tile index for this component.
**Variant Mode** | Allows you to choose the following options: - **Random -** Selects a random tile for each particle. - ** Ordered -** Assigns the tiles in spawn order, looping.
**Animation** | Allows you to use texture tiles as animation.
**Frame Count** | Enables the number of consecutive tiles to be used for the animation. It is possible to use texture animation along with the texture variants. Multiple variants of an animation can be placed in a tiled texture, each animation consisting of consecutive tiles of the same frame count. In this case *Frame Count* is the frame count of each animation and *Tile Count*= number of variants * frame count which is the total number of tiles in the texture.
**Frame Rate** | Lets you specify the speed of an animation in frames per second. If the value is set to 0 it plays one animation cycle during the particle's lifetime.
**Cycle Mode** | Allows you to choose the following options: - **Once*-*** Allows the animation to be played for a single cycle then stops. - ** Loop*-*** Allows the animation to be played in a continuous loop. Requires * Frame Rate > 0.* - **Mirror -** Allows the animation to be played until the end and then reverses the animation cycle back to the starting point (continuously). Requires * Frame Rate > 0.*
**Frame Blending** | Enables blending between frames for smoother animation. Slightly more expensive, since it samples the texture twice and blends the frames together.

### Visibility

This feature allows you to customize aspects, such as when and how the effects will be rendered.

Properties | Description
--- | ---
**Max Screen Size** | Sets the maximum screen size at which a particle will be rendered (For example, the value 1 corresponds to a size that fills the entire screen.) This option overrides the CVar **e_ParticlesMaxDrawScreen**. If both values are higher than or equal to 2, no screen size limit is enforced.
**Min Camera Distance** | Sets the minimum distance at which the particles are drawn. **Max Screen Size** is a better way to set this, as it limits the rendered size consistently with different particle sizes and camera FOVs.
**Max Camera Distance** | If the value is set to a value **higher than 0**, sets the maximum distance at which the particles are drawn. ** View Distance Multiple** can be a better option while using different resolutions, as it enforces a minimum rendered size consistently with different screen resolutions.
**View Distance Multiple** | Adjusts the maximum distance at which the effect is rendered. The default view distance for each effect is determined automatically from its maximum particle size, screen resolution and CVar **e_ParticlesMinDrawPixels**. When you need to fade out an effect closer than normal, then set ** View Distance Multiple <1**.
**Indoor Visibility** | Specifies if particles should be visible indoors or outdoors: - **Indoor Only -** Particles will only be visible indoors. - ** Outdoors Only -** Particles will only be visible outdoors. - ** Both -** Particles will be visible both indoors and outdoors.
**Water Visibility** | Specifies if particles should be visible above or underwater: - **Above Water Only -** Particles will only be visible when they are above water. - ** Below Water Only -** Particles will only be visible when they are below water. - ** Both -** Particles will be visible above and below water.
**Draw Near** | Renders effect in a special near (1st-person) Viewport.
**Draw On Top** | Disables depth testing.

### GPU Support

Since GPU and CPU particles share the same rendering pipeline, features in the **Appearance** category are shared and supported by both.

[Lighting](#lighting)[Material](#material)[Opacity](#opacity)[Texture Tiling](#texture-tiling)[Visibility](#visibility)[GPU Support](#gpu-support)
