# Additive Animations

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/25535365
- Page ID: 25535365
- Breadcrumb: Animation > Character Assembly > Additive Animations
- Parent: Character Assembly

## Content

[Image: /docs/static/attachments/29933219]

##
Overview

Additive Animations are relative animations, which means they don't overwrite the animation on the joint controllers, but instead add to it.

This means that an additive animation will preserve the underlying animation and style and is thus great for adding poses and animations for example to the upperbody. It allows the reuse of the same fullbody animations, but adds lots of variation to it. Playing an additive with a different length on top of a fullbody loop can break the monotonous look. And since the underlying rotations are not overwritten, an additive will still work when the character for example, is turned to the side with his upperbody, has raised his arms, etc... This can reduce the overall asset count greatly and add a lot of variation to the animations.

Possible uses of additives for example, are breathing, looking around, flinching, posture change, and many more. At the moment, additives cannot modify bones below the character's hips in order to prevent footsliding.

Additives can be started like regular animations, as the engine will automatically recognize it as an additive/relative animation after it has been processed by the resource compiler. The Animation Graph offers a Modifier which allows us to start additive animations alongside the regular animation states, but with different blend settings, etc.

##
Chapters:

[#chapters](
Chapters:
)
[#animation-layers](
Animation Layers
)
[#creating-additives](
Creating Additives
)
[#exporting-additives](
Exporting Additives
)
[#testing-additives-in-the-character-tool](
Testing Additives in the Character Tool
)

##
Animation Layers

Animations are started in layers:

[Image: /docs/static/attachments/35391838]
We have a total of 16 animation layers available.

Layer 0 is special as it is considered the base layer. Layer 0 supports blend spaces and motion extraction.

Animations are mixed by running them on different layers concurrently. Layers that have no animations have no effect (eg. it is possible to only have animations in layer 0 and layer 6).

The base layer will usually contain full body animation (affecting most joints and containing motion), while higher layers usually play override or additive partial body animations (affecting only a subset of joints).

##
Creating Additives

Additive animations allow you to create animations that can be added as layers on top of a base animation. The additive animation is usually a partial body animation, so it can be applied to a base full-body animation without interfering with the important parts of the base animation.

To create an additive animation, you start with a typical base pose, and then animate only the parts you want to be included in the additive animation.

-
1st frame of the animation is the Base Pose

-
this will be subtracted by the resource compiler upon export and
*
not
*
 be part of the final animation

-
The rest of the animation becomes the 'delta' from this base pose

-
Only animate bones that need to be animated

-
Bones that do not differ from the base pose (frame 0) will not be used
For users of
**
3ds Max
**
, be sure to follow the
[/docs/static/engines/cryengine-5/categories/23756816/pages/28186273](
Creating Additive Animations
)
 tutorial sub-page.

##
Exporting Additives

The Resource compiler will process the file as an additive if:

1. The animsettings of the animations .i_caf has:

```

`
<AnimationSettings>
  <AdditiveAnimation value="1"/>
</AnimationSettings>
`

```

##
Testing Additives in the Character Tool

**
Open
**
 the
**
Character Tool
**
 and load the
**
sdk_player.cdf
**
 (if it does not load on default).

Check that your new animations show up on the left side of the Character Tool. If you test the additive animation, don't be scared about any deforming that you see. As it is an additive animation, you are not supposed to play it on the Primary layer.

[Image: /docs/static/attachments/35400769]

Make sure the Layer is set to
**
Primary
**
, Animation Driven is on, and all the IKs are off.

[Image: /docs/static/attachments/35400770]

Click on the
**
relaxed_run_forward_fast
**
 animation in the Animation panel on the left.

Now, change the Layer to
**
Secondary .1
**
:

[Image: /docs/static/attachments/35400771]

Click the additive animation
**
additive_walk_forward_fast_CF_01
**
 in the Animation panel on the left.

Notice how the additive animation is basically added on to the existing run animation. The character cowers while running.

Change the Layer now to
**
Secondary .2
**
 and click on the
**
arms_coverFire_01
**
 in the Animation panel on the left.

You can now see how you get a new cower animation by using additives and upperbody animation. And the end result is what you were previewing in Max already.

[Image: /docs/static/attachments/35400772]

Keep a check on your mesh's deformation when creating additive animations.

You can actually adjust the weights of the Additive Animation. If you go back to Layer Secondary .1, you can see the
**
Additive Anim Weights
**
. 1 is the default value.

[Image: /docs/static/attachments/35400773]
