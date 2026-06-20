# Color Modifiers

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/36869028
- Page ID: 36869028
- Breadcrumb: Editor Tools > Particle Editor > Particle Effect Features > Modifiers > Color Modifiers
- Parent: Modifiers

## Content

## Overview

Color Modifiers are special Modifiers that can be found and, are only available, on the **Field: Color** feature.

The following features can be found under the Color Modifier category:

![Image](https://www.cryengine.com/docs/static/attachments/44107855)

For more information about colors, see [Field](../Field.md).

For more information about Modifiers, please refer to the [Modifiers](../Modifiers.md) page.

Colors from different modifiers are always combined using multiply blend.

### Attribute

This modifier can read the value of any attribute that is available on the emitter. This is one of the most important color modifiers, for it allows attributes to actually control the tone of the effect.

Properties | Description
--- | ---
**Attribute Name** | Defines a name for the attribute. If the attribute does not exist in this emitter, modifiers will be white.
**Scale and Bias** | Allows the attribute color to be scaled and biased based on the values in these properties.
**Gamma** | Adjusts the levels of the attribute. Specifies how bright the mid grey colors should be, but without changing white or black levels.
**Spawn Only** | Enables the attribute color to be applied on new born particles.

### Color Curve

This Modifier is a function-based Modifier; for more information please refer to [Function-based Modifiers Common Settings](../Modifiers.md).

Color Curve uses the Time Source input to sample a Bezier curve per color channel. In Particle Effects System, Bezier curves have an unlimited number of points. Each point has to be in the range 0 to 1 in the X axis; but there are no enforced limits on Y axis. For performance reasons, Bezier points support slopes but not the slope weight.

With this modifier, no additional properties are added to the feature; only function based properties are used and the color gradient is based on the Bezier curves.

### Color Random

This modifier is an equivalent to the**Random** modifier,but it outputs a random color. For more information about the Random modifier, please refer to the [Modifiers](../Modifiers.md) section.

Properties | Description
--- | ---
**Luminance** | Specifies the amount of luminance (brightness) variation to be added to the particle.
**RGB** | Specifies the amount of color saturation variance to be added to the particle. With a value of 0 all particles will look white, with a value of 1 all particles will have a fully saturated random color.

### Inherit

This option allows child particles to inherit a parent's color.

Properties | Description
--- | ---
**Spawn Only** | Inherits the parent color when a particle is born.

### GPU Support

Currently, there is limited support for the color modifiers on the GPU. The only color value that can be modified on the GPU is the color value of **Field: Color**. Color Curve can only be used when and only if the ** Self**time-source is the main property source to take a value from. Please refer to [Function-based Modifiers Common Settings](../Modifiers.md) for more information about ** Self**time-source option.

[Attribute](#attribute)[Color Curve](#color-curve)[Color Random](#color-random)[Inherit](#inherit)[GPU Support](#gpu-support)
