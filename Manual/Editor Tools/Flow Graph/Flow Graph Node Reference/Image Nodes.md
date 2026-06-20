# Image Nodes

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/29450595
- Page ID: 29450595
- Breadcrumb: Editor Tools > Flow Graph > Flow Graph Node Reference > Image Nodes
- Parent: Flow Graph Node Reference

## Content

### 3DHudInterference

Adds distortion effects to the HUD only.

![Image](https://www.cryengine.com/docs/static/attachments/28901355)

### ColorCorrection

Offers control over basic image settings such as saturation, contrast, brightness, Cyan/Magenta/Yellow, etc.

![Image](https://www.cryengine.com/docs/static/attachments/28901346)

### ColorGradient

Apply a color chart texture and specify fade-in time.

![Image](https://www.cryengine.com/docs/static/attachments/28901347)

### EffectAlienInterference

**DEPRECATED**- This effect will be removed in a future Engine release.

Adds distortion effects to the players view (doesn't affect HUD).

![Image](https://www.cryengine.com/docs/static/attachments/28901345)

### EffectBloodSplats

Places blood splats on the screen when used. Type and amount of bloodsplats can be defined using the node's input ports. 0 is human, 1 is alien. "Spawn" spawns new blood splats.

### EffectDepthOfField

Adds a depth of field effect, giving control over distance, range and amount.

![Image](https://www.cryengine.com/docs/static/attachments/28901349)

### EffectFrost

**DEPRECATED** - This effect will be removed in a future Engine release.

Simulates a frozen HUD. The amount and the center of the effect on the screen can be adjusted using the input ports of the node.

![Image](https://www.cryengine.com/docs/static/attachments/28901354)

### EffectGhosting

**DEPRECATED** - This effect will be removed in a future Engine release.

Adds a ghosting effect to the screen which overlaps and blurs previous frames together.

![Image](https://www.cryengine.com/docs/static/attachments/28901350)

### EffectRainDrops

**DEPRECATED** - This effect will be removed in a future Engine release.

Adds on-screen rain drops which travel down the players HUD.

![Image](https://www.cryengine.com/docs/static/attachments/28901357)

### EffectVolumetricScattering

**DEPRECATED** - This effect will be removed in a future Engine release.

Adds a volumetric effect which could be useful in simulating snowy environments. Also has the ability to control color, speed and amount, plus you can simulate various environments, such as lava.

![Image](https://www.cryengine.com/docs/static/attachments/28901366)![Image](https://www.cryengine.com/docs/static/attachments/28901323)

### EffectWaterDroplets

Adds a water effect which appears from various sources on the screen. Unlike RainDroplets, this simulates more of a "splash" type effect of water being thrown on the screen in various places.

![Image](https://www.cryengine.com/docs/static/attachments/28901324)

### EffectWaterFlow

Adds another type of water effect, but in this case simulates water running down the screen. This effect can be used for simulating more dense water interactions, such as standing under a waterfall.

![Image](https://www.cryengine.com/docs/static/attachments/28901325)

### FilterBlur

Blurs the entire screen. Could be used to simulate things like dense smoke affecting the players eyes. Only Gaussian blur is available at the moment.

![Image](https://www.cryengine.com/docs/static/attachments/28901351)

### FilterChromaShift

Shifts the chrominance information of the image by a certain amount. Best used in small amounts to create subtle film effects.

![Image](https://www.cryengine.com/docs/static/attachments/28901352)

### FilterDirectionalBlur

Applies a blur in a specified direction based on movement. The blur direction is defined using the vec3 input port on the node.

![Image](https://www.cryengine.com/docs/static/attachments/28901353)

### FilterGrain

**DEPRECATED** - Effect available through the Settings Window in the [Environment Editor.](../../Environment%20Editor.md)

### FilterRadialBlur

Blurs the screen around a defined 2D position on the screen. Amount and radius of the blur effect can be defined using the input ports of the node.

BlurringRadius sets the radius of the blur effect around the defined center. ScreenPos X/Y can be used to alter the center.

![Image](https://www.cryengine.com/docs/static/attachments/28901356)

### FilterSharpen

Adds sharpening to the final image. Although there is a "Type" input port, only one type is currently available. You can also use negative values to blur the screen.

![Image](https://www.cryengine.com/docs/static/attachments/28901361)

### FilterVisualArtifacts

Applies numerous effects which you would typically associate with old television sets, grain, vsync, interlacing, pixelation and others. You can mask via a texture or apply to the whole screen.

By default, all effect(s) values are set to 0 so you won't see any effects unless you specify a value for an input type. The available effect(s) inputs are: VSync, Interlacing, Pixelation, Chroma Shift and Grain.

![Image](https://www.cryengine.com/docs/static/attachments/28901365)![Image](https://www.cryengine.com/docs/static/attachments/28901362)

![Image](https://www.cryengine.com/docs/static/attachments/28901363)![Image](https://www.cryengine.com/docs/static/attachments/28901364)

### SetShadowMode

Set the shadow mode to "Normal" or "HighQuality" mode. Note: This is intended to be used for very specific lighting setups and under typical use will most likely result in a lot of self-shadowing artifacts.

![Image](https://www.cryengine.com/docs/static/attachments/28901360)![Image](https://www.cryengine.com/docs/static/attachments/28901359)

[3DHudInterference](#3dhudinterference)[ColorCorrection](#colorcorrection)[ColorGradient](#colorgradient)[EffectAlienInterference](#effectalieninterference)[EffectBloodSplats](#effectbloodsplats)[EffectDepthOfField](#effectdepthoffield)[EffectFrost](#effectfrost)[EffectGhosting](#effectghosting)[EffectRainDrops](#effectraindrops)[EffectVolumetricScattering](#effectvolumetricscattering)[EffectWaterDroplets](#effectwaterdroplets)[EffectWaterFlow](#effectwaterflow)[FilterBlur](#filterblur)[FilterChromaShift](#filterchromashift)[FilterDirectionalBlur](#filterdirectionalblur)[FilterGrain](#filtergrain)[FilterRadialBlur](#filterradialblur)[FilterSharpen](#filtersharpen)[FilterVisualArtifacts](#filtervisualartifacts)[SetShadowMode](#setshadowmode)
