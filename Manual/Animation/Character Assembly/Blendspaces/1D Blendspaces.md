# 1D Blendspaces

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/26873847
- Page ID: 26873847
- Breadcrumb: Animation > Character Assembly > Blendspaces > 1D Blendspaces
- Parent: Blendspaces

## Content

![Image](https://www.cryengine.com/docs/static/attachments/29933230)

##
1D-Blend Spaces Overview

The blend-spaces are XML files and they are edited with a text-editor. In CharEdit we support
**
hot-loading of files
**
. This means you can change the file with a text editor on disk and the system will update it automatically and render the result. With a bit of experience it's very easy to prototype things and do a lot of experimentation.

We will explain all the concepts and parameters while we build different types of blend-spaces. Almost all parameters in the XML files are identical for 1D, 2D and 3D blend-spaces, so it's recommended to do experiments with 1D or 2D blend-spaces, because its much easier to understand the interactions between assets, annotations and different parameters. Don't start with a huge 3D blend space.

##
Chapters:

[1D-Blend Spaces Overview](#1d-blend-spaces-overview)
[Chapters:](#chapters)
[1D-bspace_DummyPara1.bspace](#1d-bspacedummypara1bspace)
[1D-bspace_DummyPara2.bspace](#1d-bspacedummypara2bspace)
[1D-bspace_DummyPara3.bspace](#1d-bspacedummypara3bspace)
[1D-bspace_Move1.bspace](#1d-bspacemove1bspace)
[1D-bspace_Move2.bspace](#1d-bspacemove2bspace)
[1D-bspace_Move3.bspace](#1d-bspacemove3bspace)
[1D-BSpace_Turn.bspace](#1d-bspaceturnbspace)
[1D-BSpace_Slope.bspace](#1d-bspaceslopebspace)
[1D-BSpace_StrafeMove_8clips.bspace](#1d-bspacestrafemove8clipsbspace)
[1D-BSpace_StepRot.bspace](#1d-bspacesteprotbspace)
[1D-BSpace_I2M_left.bspace](#1d-bspacei2mleftbspace)

##
1D-bspace_DummyPara1.bspace

```

`
<ParaGroup>
  <Dimensions>
    <Param name="BlendWeight" min="0.0" max="1.0" cells="1"/>
  </Dimensions>
  <ExampleList>
    <Example AName="stand_tac_walk_rifle_fwd_slow_3p_01" SetPara0="0.0" />
    <Example AName="stand_tac_sprint_rifle_fwd_3p_01" SetPara0="1.0" />
  </ExampleList>
  <Blendable>
    <Face p0="0" p1="1" />
  </Blendable>
</ParaGroup>
`

```

This is the simplest blend-space you can build, without any advanced features. The only purpose is to lerp two animations.

![Image](https://www.cryengine.com/docs/static/attachments/35400777)

You can start this in CharEdit and move the
**
BlendWeight
**
 slider between [0.0f … 1.0f] to create a continuous blend between walk and sprint.

```

`
<Param name="BlendWeight" min="0.0" max="1.0" cells="1"/>
`

```

BlendWeight is the control parameter, and min/max is the range for the blend-space.  "cells="1""  are the amount of cells for the virtual examples. The minimum value is 3. If you pass a lower value (as in out example) the system clamps it to 3. More about that later.

```

`
<Example AName="stand_tac_walk_rifle_fwd_slow_3p_01"  SetPara0="0.0" />
<Example AName="stand_tac_runTurn_rifle_lft_fast_3p_01" SetPara0="1.0" />
`

```

"AName" are the names of the CAF files.
"SetPara0=?"
 is assigning this asset a position in the 1D blend-space. Because this is a 1D-blend space, we place both assets at different positions on the x-axis. The walk is at pos 0.0 and the sprint is at 1.0.

```

`
<Blendable>
  <Face p0="0" p1="1" />
</Blendable>
`

```

With the Face, tag is used for annotations. Here we tell the blend-node which assets we want to blend. Because this is a super simple setup, the only option is to blend between asset 0 and 1. "p0" and "p1" are the indices of the 2 assets.

If you delete this tag from the XML, the system will show only the first assets in the BSpace and blending is not possible.

For 1D blend-spaces it is important that "p0" points to the lower parameter and "p1" points the higher parameter. If the order is reversed or both parameters are identical, the system will halt with an error. For more on this, see "Rules of Annotations".

In this example (1+2) the character can only move on the spot
*
(even if you disable the
**
InPlaceMovement
**
)
*
, because we didn't specify yet how to deal with the locator motion. That will happen later in
**
Example 3
**
.

##
1D-bspace_DummyPara2.bspace

Now we can build a generalized one-dimensional blend-space by placing an arbitrary number of clips along a linear scale. This blend-node is doing a lerp between 2 clips adjacent to the input-value.

![Image](https://www.cryengine.com/docs/static/attachments/35400778)

```

`
<ParaGroup>
  <Dimensions>
    <Param name="BlendWeight" min="0.0" max="1.0" cells="29" scale="3.4" />
  </Dimensions>
  <ExampleList>
    <Example AName="stand_tac_walk_rifle_fwd_slow_3p_01" SetPara0="0.0" />
    <Example AName="stand_tac_run_rifle_fwd_slow_3p_01" SetPara0="0.3333" />
    <Example AName="stand_tac_run_rifle_fwd_fast_3p_01" SetPara0="0.6666" />
    <Example AName="stand_tac_sprint_rifle_fwd_3p_01" SetPara0="1.0" />
  </ExampleList>
  <Blendable>
    <Face p0="0" p1="1" />
    <Face p0="1" p1="2" />
    <Face p0="2" p1="3" />
  </Blendable>
</ParaGroup>
`

```

This example creates a continuous blend between all 4 assets in the space when you move the
**
BlendWeight
**
 slider. Also note that all 4 assets in the blend-space are
**
time-warped
**
 when you change the slider. Without this feature you would get foot-sliding and foot-crossing and other funny things. For time-warping we align several motions by using a single animation counter and scale the delta-time in relation to the blend-weights.

Imagine these are two motions in a blend-space: A walk and a sprint. If the "
*
sprint
*
" has a higher priority, then the "
*
walk
*
" looks more like a snappy Charlie Chaplin animation. If the "
*
walk
*
" has a higher priority, then the "
*
sprint
*
" animates in slow-motion. This kind of time-scaling is something we do with all motions in a blend-space.

Time-warping is a simple and powerful feature. It works best for motions with identical features but different amount of key-frames
*
(i.e. it is perfect for
**
locomotion-assets
**
)
*
. In our case, we had to make sure, that all assets start with the left foot on the ground.

```

`
<Dimensions>
  <Param name="BlendWeight" min="0.0" max="1.0" cells="29" scale="3.4" />
</Dimensions>
`

```

The scale tag is optional. It's only for debugging in CharEdit. In this case all 4 assets would be very close together and almost rendered on top of each other. With this parameter we scale the position on the x-axis. This has absolutely no impact on the blending itself.

```

`
<Blendable>
  <Face p0="0" p1="1" />
  <Face p0="1" p1="2" />
  <Face p0="2" p1="3" />
</Blendable>
`

```

All assets in the example list need to be annotated for blending. Assets that are not annotated in <Blendable> will not contribute to the blend. Here we have four assets and we need to tell the system explicitly how we want to blend them based on the input value. Because all assets are placed on a line, we need only
**
line-segments
**
 for annotations. For a blend-space with four assets, three line-segments are needed.

It is important that "p0" points to the lower parameter and "p1" points the higher parameter of the examples. If the order is reversed or both parameters are identical, the system will halt with an error.

##
1D-bspace_DummyPara3.bspace

In order to get motion-extraction, we have to add these parameters, because BlendWeight doesn't say that directly.

```

`
<AdditionalExtraction>
  <Param name="MoveSpeed"   />
  <Param name="TravelAngle" />
  <Param name="TurnSpeed"   />
  <Param name="TravelSlope" />
</AdditionalExtraction>
`

```

If we add these parameters to the previous BSpace, the character is using its locator motion to move though the world
*
(in this special case the "MoveSpeed" would be enough, because the assets have only forward motion)
*
. Also make sure "
**
Animation Driven
**
" is activated and "
**
InPlaceMovement
**
" deactivated. The move speed can be controlled again with the BlendWeight slider. If the assets are clean
*
(we have special rules to create locomotion assets)
*
 you can blend between different move-speeds without getting foot-sliding. That's pretty much all about simple animation blending with blend-spaces.

##
1D-bspace_Move1.bspace

And now we move to the main topic of blend-spaces: Parametric Blending. This is still a simple binary lerp, but we tell the system to
*
extract the parameters
*
 directly out of the motions. The parameter "MoveSpeed" tells the system to extract the move-speed out of the root-motion and inserts it into automatically into the blend-space. The result is a blend-space where all assets have a different positions on the x-axis. These positions are what we call the "natural" motion parameters, because they are coming from the motion directly. In this case, the blend-space represents the real motion parameter, which is not the case when you use "SetPara0="?"" as we did before.

![Image](https://www.cryengine.com/docs/static/attachments/35400779)

```

`
<ParaGroup>
  <Dimensions>
    <Param name="MoveSpeed" min="0.2" max="+10.0" cells="19" />
  </Dimensions>
  <ExampleList>
    <Example AName="stand_tac_walk_rifle_fwd_slow_3p_01" />
    <Example AName="stand_tac_run_rifle_fwd_slow_3p_01" />
    <Example AName="stand_tac_run_rifle_fwd_fast_3p_01" />
    <Example AName="stand_tac_sprint_rifle_fwd_3p_01" />
  </ExampleList>
  <Blendable>
    <Face p0="0" p1="1" />
    <Face p0="1" p1="2" />
    <Face p0="2" p1="3" />
  </Blendable>
</ParaGroup>
`

```

Even in the case of automatic extraction it is important that
*
all examples in the list are sorted by size
*
 starting with the lowest parameter. All parameters must be in ascending order or the system will halt with an error. Below you can find an example that will halt the system, because the slowest asset (walk) is at the end. It is important to evaluate all assets before you do the annotation.

```

`
<ExampleList>
  <Example AName="stand_tac_run_rifle_fwd_slow_3p_01" />
  <Example AName="stand_tac_run_rifle_fwd_fast_3p_01" />
  <Example AName="stand_tac_sprint_rifle_fwd_3p_01" />
  <Example AName="stand_tac_walk_rifle_fwd_slow_3p_01" /> //bad
</ExampleList>
`

```

If the blend-space is correct, we can use the MoveSpeed slider to move the cursor between the assets and create a continuous blend between all four assets. The big difference between
**
*
simple blending
*
**
 and
**
*
parametric blending
*
**
 is that we can set the desired move-speed directly with the slider
*
(i.e. run at the speed 6.5m/sec)
*
 and the system automatically blends the correct assets to generate the move-speed that we want. Fort AI programmers this is more intuitive then setting a [0...1] blend-tree parameter.

This BSpace is a special case where you need SDK 3.5.2, which supports automatic extrapolation for 1D blend-spaces. In previous versions it will simply pop to the first asset if you move the cursor outside the range of the fastest/slowest asset. We used pseudo examples to overcome this.

##
1D-bspace_Move2.bspace

This example shows how to create
**
pseudo assets
**
 by extrapolating two existing assets. The pseudo assets are rendered with a red cube. These are basically procedurally generated assets.

![Image](https://www.cryengine.com/docs/static/attachments/35400780)

```

`
<ParaGroup>
  <Dimensions>
    <Param name="MoveSpeed" min="0" max="+10.0" cells="19" />
  </Dimensions>
  <ExampleList>
    <Example AName="stand_tac_walk_rifle_fwd_slow_3p_01" />
    <Example AName="stand_tac_run_rifle_fwd_slow_3p_01" />
    <Example AName="stand_tac_run_rifle_fwd_fast_3p_01" />
    <Example AName="stand_tac_sprint_rifle_fwd_3p_01" />
  </ExampleList>
  <ExamplePseudo>
    <Pseudo p0="1" p1="0" w0="-0.5" w1="1.5" />
    <Pseudo p0="2" p1="3" w0="-1.0" w1="2.0" />
  </ExamplePseudo>
  <Blendable>
    <Face p0="4" p1="0" />
    <Face p0="0" p1="1" />
    <Face p0="1" p1="2" />
    <Face p0="2" p1="3" />
    <Face p0="3" p1="5" />
  </Blendable>
</ParaGroup>
`

```

Our blend-space is almost perfect for running forward, but there is still a little issue we need to fix. The blend-spaces have a min/max range from
**
0.1f
**
 -
**
10.0f
**
, which means we can select a move-speed between
**
0.1m/sec
**
 and
**
10.0m/sec
**
. The only problem is that the
*
slow-walk
*
 has a speed of
**
0.85m/sec
**
 and the
*
fast-sprint
*
 has a speed of
**
9.26m/sec
**
. These assets are coming from mocap, and we didn't want to change them too much. It's also the physical limit for motions a human can do, which means we can't cover the whole blend-space.

It's always possible tell an animator to keyframe a new asset, but let's say we want to get away with as few motion-clips as possible. With
**
extrapolation
**
 we can pick 2 real examples and extrapolate them along a line. The new example is a
**
pseudo-example
**
. It has only two indices/weights that point to the real examples.

```

`
<ExamplePseudo>
  <Pseudo p0="1" p1="0" w0="-0.5" w1="1.5" />
  <Pseudo p0="2" p1="3" w0="-1.0" w1="2.0" />
</ExamplePseudo>
`

```

From a technical point of view it is surprisingly simple. You don't have to change anything in your blending-code. Actually, it's exactly the same blending formula we use for interpolation, just that the blend-weights are outside of the [0…1] range. For extrapolation it might be acceptable for some motions to have negative values or values bigger then 1.0f. In all cases, the weights should be normalized to always sum to 1.0 to avoid scaling of the character. In our example we do the following operation to create a pseudo asset:

pe1 =
-0.5
*clip0 +
1.5*
clip1

pe2 =
-1.0
*clip2 +
2.0*
clip3

Once we placed our pseudo example in the blend-space, we can annotate the new example for blending and create animations even for the area outside of the existing space.

```

`
<Blendable>
  <Face p0="4" p1="0" /> //clip4 is a pseudo example
  <Face p0="0" p1="1" />
  <Face p0="1" p1="2" />
  <Face p0="2" p1="3" />
  <Face p0="3" p1="5" /> //clip5 is a pseudo example
</Blendable>
`

```

The result of extrapolation can be
**
very unpredictable
**
. Sometimes you get surprisingly interesting results, and sometimes only a weird twisted pose. There is no way to tell in advance whether extrapolation will produce good or bad animations. This feature can be very useful in blend-spaces with higher dimensions. With "extrapolated pseudo examples" you can test several asset-combinations in a blend-space, and see which give acceptable results. It's a kind of
**
controlled extrapolation
**
. If you are not happy with the result, then you have to "patch" the blend-space with new examples. We don't recommend overuse of extrapolation, but if you use it only for a couple of seconds, then it's perfectly fine and it helps to save a lot of memory.

##
1D-bspace_Move3.bspace

This example shows how to create
**
pseudo assets
**
 by scaling the playback rate of existing assets. The pseudo assets are rendered with a green cube. These is yet another method to create procedurally generated assets.

![Image](https://www.cryengine.com/docs/static/attachments/35400781)

```

`
<ParaGroup>
  <Dimensions>
    <Param name="MoveSpeed" min="0.1" max="+10.0" cells="19" />
  </Dimensions>
  <ExampleList>
    <Example AName="stand_tac_walk_rifle_fwd_slow_3p_01" PlaybackScale="0.1"/>
    <Example AName="stand_tac_walk_rifle_fwd_slow_3p_01" />
    <Example AName="stand_tac_run_rifle_fwd_slow_3p_01" />
    <Example AName="stand_tac_run_rifle_fwd_fast_3p_01" />
    <Example AName="stand_tac_sprint_rifle_fwd_3p_01" />
    <Example AName="stand_tac_sprint_rifle_fwd_3p_01" PlaybackScale="1.5"/>
  </ExampleList>
  <Blendable>
    <Face p0="0" p1="1" />
    <Face p0="1" p1="2" />
    <Face p0="2" p1="3" />
    <Face p0="3" p1="4" />
    <Face p0="4" p1="5" />
  </Blendable>
</ParaGroup>
`

```

This blend-node is using the same asset twice and because of the
**
PlaybackScale
**
="0.1" and
**
PlaybackScal
**
e="1.5" we place it at 2 different positions on the line. When you use the Move-slider, then you can generate a parameterized walk in the range [0.1 … 10.0] without foot-sliding.

##
1D-BSpace_Turn.bspace

So far we had only moving-forward, but it's easy to combine it with a turn animation. All we need are three assets:
*
run-forward
*
,
*
run-turn-right
*
 and
*
run-turn-left
*
. The curved yellow locator indicates a turning animation. In all cases the character always moves in the direction his body points.

![Image](https://www.cryengine.com/docs/static/attachments/35400782)

```

`
<ParaGroup>
  <Dimensions>
    <Param name="TurnSpeed" min="-4.0" max="+4.0" cells="17"/>
  </Dimensions>
  <ExampleList>
    <Example AName="stand_tac_runTurn_rifle_rgt_fast_3p_01" />
    <Example AName="stand_tac_run_rifle_fwd_fast_3p_01" />
    <Example AName="stand_tac_runTurn_rifle_lft_fast_3p_01" />
  </ExampleList>
  <AdditionalExtraction>
    <Param name="MoveSpeed" />
  </AdditionalExtraction>
  <Blendable>
    <Face p0="0" p1="1" />
    <Face p0="1" p1="2" />
  </Blendable>
</ParaGroup>
`

```

There is one thing in this XML that is not immediately obvious: the tags AdditionalExtraction and Param name="
MoveSpeed
". It's similar to what we mentioned in Example3 before. But in this case we specified only the "TurnSpeed" for control, motion-extraction and delta movement. The system is not aware that we need the move speed for the delta-movement as well, unless we say it explicitly. Once we set "
MoveSpeed
" we can move through the world.

With the blend slider "
**
Travel Angle
**
" in CharEdit you can control the curvature. There is no way to adjust the move-speed. Character moves exactly at the speed the animations are authored. We will show later with 2D-blend spaces how to overcome this.

##
1D-BSpace_Slope.bspace

Another practical example is moving uphill and downhill. All we need are three assets:
*
walk-forward
*
,
*
walk-up
*
 and
*
walk-down
*
. The yellow locator indicates a slope-angle. In all cases the character always moves in the direction his body points.

![Image](https://www.cryengine.com/docs/static/attachments/35400783)

```

`
<ParaGroup>
  <Dimensions>
    <Param name="TravelSlope" min="-0.5" max="+0.5" scale="4.4" cells="5"/>
  </Dimensions>
  <ExampleList>
    <Example AName="stand_tac_walkDown_rifle_fwd_slow_3p_01" />
    <Example AName="stand_tac_walk_rifle_fwd_slow_3p_01" />
    <Example AName="stand_tac_walkUp_rifle_fwd_slow_3p_01" />
  </ExampleList>
  <AdditionalExtraction>
    <Param name="MoveSpeed" />
  </AdditionalExtraction>
  <Blendable>
    <Face p0="0" p1="1" />
    <Face p0="1" p1="2" />
  </Blendable>
</ParaGroup>
`

```

With the blend slider "
**
Slope
**
" in CharEdit you can control the slope angle. The move-speed is not controllable and the character will move exactly at the speed the animations are authored. We will show later with 2D-blend spaces how to overcome this.

##
1D-BSpace_StrafeMove_8clips.bspace

A classical motion example for games is
**
strafing movement
**
 where the character keeps his body-direction constant
*
(i.e. always looking forward)
*
, but wants to move with his legs forward, sideways or backwards. A simple way to do this with blend-spaces is to take four, six or eight assets which cover all move-directions we need, and represent each direction by a radiant. Moving forward is always a value of 0.0. All values between 0.0 and -3.147 are movements to the right. All values between 0.0 and +3.147 are movements to the left. The values +3.147 and -3.147 both represent a perfect backwards motion. To cover a full circle we need a blend-space that ranges from -3.147 to +3.147. Or 2pi, if you want.

![Image](https://www.cryengine.com/docs/static/attachments/35400784)

```

`
<ParaGroup>
  <Dimensions>
    <Param name="TravelAngle" min="-3.14" max="+3.14" cells="17" />
  </Dimensions>
  <ExampleList>
    <Example AName="crouch_tac_walk_rifle_bwd_slow_3p_01" SetPara0="-3.147" />
    <Example AName="crouch_tac_walkCross_rifle_bRgt_slow_3p_01" />
    <Example AName="crouch_tac_walkStr_rifle_rgt_slow_3p_01" />
    <Example AName="crouch_tac_walkCross_rifle_fRgt_slow_3p_01" />
    <Example AName="crouch_tac_walk_rifle_fwd_slow_3p_01" />
    <Example AName="crouch_tac_walkCross_rifle_fLft_slow_3p_01" />
    <Example AName="crouch_tac_walkStr_rifle_lft_slow_3p_01" />
    <Example AName="crouch_tac_walkCross_rifle_bLft_slow_3p_01" />
    <Example AName="crouch_tac_walk_rifle_bwd_slow_3p_01" SetPara0="+3.147" />
  </ExampleList>
  <AdditionalExtraction>
    <Param name="MoveSpeed" />
  </AdditionalExtraction>
  <Blendable>
    <Face p0="0" p1="1" />
    <Face p0="1" p1="2" />
    <Face p0="2" p1="3" />
    <Face p0="3" p1="4" />
    <Face p0="4" p1="5" />
    <Face p0="5" p1="6" />
    <Face p0="6" p1="7" />
    <Face p0="7" p1="8" />
  </Blendable>
</ParaGroup>
`

```

The result is a straighten out on the circle on which the directional animation clips were placed and use the movement direction angle
*
θ.
*
 The parameter "TravelAngle" is doing this extraction automatically
*
(except for the backwards movement)
*
. With the blend slider "
**
Travel
**
**
Angle
**
" in CharEdit you can control the move direction.

It is probably not immediately obvious why
SetPara0="-3.147"
 and
SetPara0="+3.147"
 are needed. Why do we need to set these values manually? Why can't we extract them automatically out of the file? As mentioned before, to cover a full circle we need a blend-space that ranges from -3.147 to +3.147
*
(or from -pi to +pi)
*
. Unfortunately it is impossible for an artist to create two different assets, one that moves -3.147 and one that moves +3.147. Technically both are the same assets and with automatic extraction both would end up at the same position in the blend-space. That is an illegal case. The only way to use it in the context of a linearized blend-space is to set the parameter directly and place the same asset at different positions in the space. In order words, the parameter
SetParaX
 is yet another way to create pseudo assets to populate a blend-space.

##
1D-BSpace_StepRot.bspace

Another practical example are
**
IdleStep-Rotations
**
 where a character is turning on the spot.

![Image](https://www.cryengine.com/docs/static/attachments/35400785)

```

`
<ParaGroup>
  <Dimensions>
    <Param name="TurnAngle" min="-1.6" max="+1.6" cells="9" locked="1" deltaextraction="1"/>
  </Dimensions>
  <ExampleList>
    <Example AName="stand_tac_stepRot_rifle_rgt_3p_01" />
    <Example AName="stand_tac_step_rifle_idle_3p_01" />
    <Example AName="stand_tac_stepRot_rifle_lft_3p_01" />
  </ExampleList>
  <Blendable>
    <Face p0="0" p1="1" />
    <Face p0="1" p1="2" />
  </Blendable>
</ParaGroup>
`

```

The parameter locked="1" avoids changing the parameters while the animation is playing. In most blend-spaces you can change the parameter any time and see the result immediately. But for a few types of blends this is not recommended, for example with Step-Rotations and Idle2Moves. For these blend-spaces we don't want to change the parameter while the animation is playing.

The problem is more extreme for the Idle2Moves. Just imagine a character leans in to start a 90-degree-to-the left run, and the user suddenly decides he wants to run in a different direction. if we change the blend-weights immediately, the animation would look weightless and implausible. With the flag set, the BSpace only takes new inputs when it is pushed into the queue or when the animation reaches the end of the cycle and loops.

The parameter deltaextraction="1" is a used for distance-based motion extractions and is necessary for step-rotations and idle2Moves.

##
1D-BSpace_I2M_left.bspace

Another practical example are
**
Idle2Move
**
 animations, where a character is standing in an idle pose and then starts a run-transition into any direction.

This is a special case: In a blend-space it is required that all assets are blendable, but for an Idle2Move this is not always possible. The reason is the way how we created the assets. All assets moving to the
**
*
right
*
**
 start with the
**
*
right foot on the ground
*
**
, and all moving to the
**
*
left
*
**
 start with the
**
*
left foot on the ground
*
**
. This means we also need two different forward-assets
*
(one starting with the left foot and one with the right foot)
*
. Because we parameterize its turn-angle, both forward assets would be exactly at the same position (=angle 0) in the blend-space. This is an illegal case. The same issue would happen for the 180-degree turn.

```

`
<ParaGroup>
  <VEGPARAMS Idle2Move="1" />
  <Dimensions>
    <Param name="TurnAngle" min="0.00" max="+3.15" cells="9" locked="1" deltaextraction="1"/>
  </Dimensions>
  <AdditionalExtraction>
    <Param name="MoveSpeed" />
    <Param name="TravelAngle" />
  </AdditionalExtraction>
  <ExampleList>
    <Example AName="stand_tac_runStart_rifle_fwd_fast_lf_3p_01" /> //forward
    <Example AName="stand_tac_runStart_rifle_lft_fast_lf_3p_01" /> //90-degree left
    <Example AName="stand_tac_runStart_rifle_rev_fast_lf_3p_01" /> //180-degree left
  </ExampleList>
  <Blendable>
    <Face p0="0" p1="1" />
    <Face p0="1" p1="2" />
  </Blendable>
</ParaGroup>
`

```

The only solution is to make two separate blend-spaces: one that moves to the left and one that moves to the right. Then we can either leave it up to the high level application to pick the correct BSpace
*
(based on the desired move-direction)
*
, or we can do a simple trick and combine them in the low-level application. With a .COMB file it is possible to have several BSpaces and automatically select the right one based on the input-parameter.

```

`
<CombinedBlendSpace>
  <VEGPARAMS Idle2Move="1" />
  <Dimensions>
    <Param name="TurnAngle" ChooseBlendSpace="1" locked="1" />
  </Dimensions>
  <AdditionalExtraction>
    <Param name="MoveSpeed" />
    <Param name="TravelAngle" />
  </AdditionalExtraction>
  <BlendSpaces>
    <BlendSpace AName="animations/human/male/lmg/stand/1D-BSpace_I2M_left.bspace" />
    <BlendSpace AName="animations/human/male/lmg/stand/1D-BSpace_I2M_right.bspace" />
  </BlendSpaces>
</CombinedBlendSpace>
`

```

The parameter <VEGPARAMS Idle2Move="1"/> indicates that this is an I2M blend-space. This information is needed in the transition-queue.

Next to "
**
TurnAngle
**
" you can find ChooseBlendSpace="1". This parameter activates the selection mode.

The BSpace for
**
I2M_left
**
 has a range of
**
min="0.00"
**
 and
**
max="+3.15"
**
.

The BSpace for
**
I2M_right
**
 has a range of
**
min="-3.15"
**
 and
**
max="0.00"
**
.

If we pass a parameter between
**
-3.15
**
 and
**
+3.15
**
, then we just need to check if the parameter is inside the range of at least one of those BSpaces and pick it to execute the blend. Of course, we have to make sure that the BSpaces don't overlap.
