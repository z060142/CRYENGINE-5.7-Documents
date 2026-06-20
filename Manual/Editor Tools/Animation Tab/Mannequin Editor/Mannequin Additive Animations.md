# Mannequin Additive Animations

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/28186271
- Page ID: 28186271
- Breadcrumb: Editor Tools > Animation Tab > Mannequin Editor > Mannequin Additive Animations
- Parent: Mannequin Editor

## Content

### Overview

Additive Animations are relative animations, which means they don't overwrite the animation on the joint controllers, but instead add to it.

This means that an additive animation will preserve the underlying animation and style and is thus great for adding poses and animations for example to the upperbody. It allows the reuse of the same fullbody animations, but adds lots of variation to it. Playing an additive with a different length on top of a fullbody loop can break the monotonous look. And since the underlying rotations are not overwritten, an additive will still work when the character is, for example, turned to the side with his upperbody, has raised his arm, etc. This can reduce the overall asset count greatly and add a lot of variation to the animations.

Possible uses of additives are for example breathing, looking around, flinching, posture change, and many more. Additives cannot modify bones below the character's hips at the moment, in order to prevent footsliding.

Additives can be started like regular animations, as the engine will automatically recognize it as an additive/relative animation after it has been processed by the resource compiler. The Animation Graph offers a Modifier which allows to start additive animations alongside the regular animation states, but with different blend settings, etc.

### Creating Additives

Additive animations allow you to create animations that can be added as layers on top of a base animation. The additive animation is usually a partial-body animation, so it can be applied to a base full-body animation without interfering with the important parts of the base animation.

To create an additive animation, you start with a typical base pose, and then animate only the parts you want to be included in the additive animation.

- 1st frame of the animation is the Base Pose.
- this will be subtracted by the resource compiler upon export and *not* be part of the final animation.
- The rest of the animation becomes the 'delta' from this base pose.
- Only animate bones that need to be animated.
- Bones that do not differ from the base pose (frame 0) will not be used.

For users of **3ds Max**, be sure to follow the [Creating Additive Animations](../../../Tutorials/Animation%20and%20Characters/Mannequin%20Editor/Tutorial%20-%20Creating%20Additive%20Animations%20with%20Mannequin%20Editor.md) tutorial sub-page.

### Exporting Additives:

The Resource compiler will process the file as an additive if:

1. The animsettings of the animations.i_caf has:

```
<AnimationSettings>
<AdditiveAnimation value="1"/>
</AnimationSettings>
```
