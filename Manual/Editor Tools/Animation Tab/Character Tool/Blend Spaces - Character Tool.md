# Blend Spaces - Character Tool

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/28186170
- Page ID: 28186170
- Breadcrumb: Editor Tools > Animation Tab > Character Tool > Blend Spaces - Character Tool
- Parent: Character Tool

## Content

##
Overview

This document explains the basic steps to setup and debug BSpaces in the
[Character Tool](../Character%20Tool.md)
. It doesn't cover any game-code, AI or CryMannequin specific thing.

##
Visualizing BSpaces

The best way to get a feeling how BSpaces work internally, is to start a simple 2D-BSpaces, visualize it in the Character Tool and a play around with the different debug options.

-
Start the Character Tool and load a model.

-
Select "2D-BSpace_MoveTurn" from the animation list. The character should start to run forward.

-
If the character runs in place, make sure the checkbox "Animation Driven" is activated.

-
Once the characters moves, go to "Blend Space Control" and use the first to sliders to change speed and curvature.

-
Go to the
**
DebugOptions
**
 in the Character Tool (right/down corner) and activate
**
InPlaceMovement
**
. This will put the base-character back to the origin.
*
(This is necessary, because for debugging we render the blend-space and the base-character in the same view-port and the camera is attached to the base-character)
*

-
Next go to the console and type in
**
ca_DrawVEGInfo 3.5
**

-
With the mouse and WASD move the camera back from the origin. On the left you can see the grid for the BSpace and on the right the blended character. To simplify the debug-output it might help to disable the grey ground grid (
**
ShowGrid
**
), or the world coordinate system (
**
ShowBase
**
), or the yellow locomotion locator (
**
ShowLocator
**
) You'll find both check-boxes in
**
DebugOptions
**
 in the Character Tool (right/down corner).
![Image](https://www.cryengine.com/docs/static/attachments/28878091)

##
Debug parameters of ca_DrawVEGInfo

In SDK 3.5 we improved the CVar parameters slightly for better debug output. The
**
CVar
**
 takes a float value in the format
**
ca_DrawVEGInfo 2.344455
**
. By default its
**
ca_DrawVEGInfo 0.0
**
, which means debugging is disabled.

The
**
fractional
**

**
part
**
 (value right of the comma) represent the scaling of the example models in the BSpace. If you use only
**
ca_DrawVEGInfo 0.5
**
, then it draws only the characters at 0.5 of the original size.

If you use any value between
**
0.001
**
 and
**
0.9999
**
, you'll get the following information on screen:

![Image](https://www.cryengine.com/docs/static/attachments/28878092)

**
a)
**
 All animation-files available the BSpace (as a mini version of the character model).

**
b)
**
 Each model has either a
*
white
*
 or
*
red
*
 spinning cube at its root joint.

-
A
**
white cube
**
 represents the
**
*
real animation asset
*
**
 (which is a CAF file on disk)

-
A
**
red cube
**
 represents an
**
*
extrapolated pseudo example
*
**
 (more about that later)

-
A
**
green cube
**
 (not in the picture) represents a
**
*
playback scaled pseudo example
*
**
 (more about that later).
**
c)
**
 Each cube has an index. This is the order of the animation-clips how they appear in the BSpace-xml, including all the pseudo examples.

```

`
<ExampleList>
  <Example AName="stand_tac_walk_rifle_fwd_slow_3p_01" />
  <Example AName="stand_tac_run_rifle_fwd_slow_3p_01" />
  <Example AName="stand_tac_run_rifle_fwd_fast_3p_01" />
  <Example AName="stand_tac_sprint_rifle_fwd_3p_01" />
  <Example AName="stand_tac_walkTurn_rifle_lft_slow_3p_01" />
  <Example AName="stand_tac_runTurn_rifle_lft_slow_3p_01" />
  <Example AName="stand_tac_runTurn_rifle_lft_fast_3p_01" />
  <Example AName="stand_tac_walkTurn_rifle_rgt_slow_3p_01" />
  <Example AName="stand_tac_runTurn_rifle_rgt_slow_3p_01" />
  <Example AName="stand_tac_runTurn_rifle_rgt_fast_3p_01" />
</ExampleList>
<ExamplePseudo>
  <Pseudo p0="1" p1="0" w0="-1.0" w1="2.0" />
  <Pseudo p0="0" p1="4" w0="-3.2" w1="4.2" />
  <Pseudo p0="0" p1="7" w0="-3.0" w1="4.0" />
  <Pseudo p0="1" p1="5" w0="-1.0" w1="2.0" />
  <Pseudo p0="1" p1="8" w0="-1.5" w1="2.5" />
  <Pseudo p0="2" p1="6" w0="-1.5" w1="2.5" />
  <Pseudo p0="2" p1="9" w0="-1.5" w1="2.5" />
  <Pseudo p0="2" p1="3" w0="-2.0" w1="3.0" />
</ExamplePseudo>
`

```

**
d)
**
 There is also a
**
green wireframe quat
**
. This shows which assets are currently considered in the blend. In a 2D BSpace we have either triangles (blends between 3 assets) or quats (blends between 4 assets)

**
e)
**
 Inside of a triangle or quat there is always a
**
red flashing cursor
**
. You can control it with the blend-space sliders in the Character Tool and see at any time which assets contribute to the final blend.

The number in front of the comma are now interpreted as bit-fields.

##
Bit 1:

If set it shows only the pink lines of the blend-space grid (i.e.
**
ca_DrawVEGInfo 1.5
**
). For an 1D-BSpace it's a simple line segment. For an 2D-BSpace it's a plane. For an 3D-BSpace it's a cube.

![Image](https://www.cryengine.com/docs/static/attachments/28878089)
![Image](https://www.cryengine.com/docs/static/attachments/28878090)
![Image](https://www.cryengine.com/docs/static/attachments/28878086)

The scope of the blend-spaces (=the grid) is defined in the XML file. These values represent the maximum range of motion. In the case of "MoveSpeed" it means we can move between 0.2m/sec and 9.5m/sec.

If the AI-code passes values outside of this range, then they are automatically clamped to these value. This also means, that we have to proved assets to cover the entire defined blend-spaces.

```

`
<Dimensions>
  <Param name="MoveSpeed" min="+0.2" max="+9.5" cells="7"/>
  <Param name="TurnSpeed" min="-3.8" max="+3.8" cells="7"/>
</Dimensions>
`

```

##
Bit 2: Visualize the Virtual Examples (little blue cubes)

In the XML-example above, the min/max values are the range of the blend-space and the cells are the density of the grid. We map a simple regular grid over the range of the blend-space and then we loop over this 2d- or 3d-array and compute the
**
virtual-examples
**
.

![Image](https://www.cryengine.com/docs/static/attachments/28878087)

These virtual examples are a runtime-optimization: At run-time we move a cursor through this space and for each new position of the cursor
*
(=motion features on the x-,y-,z-axis)
*
 we compute the correct bend-weights. The computation of blend-weights can be a complex issue and if the motion-parameters are scattered all over the parameter-space, then this step can be a serious performance problem. Some 2D- and 3D-Blend-Spaces can have very complex setups which make a run-time evaluation very unpredictable and slow.

Virtual-example grids solve that issue with a simple offline-computation by pre-computing the blend-weights and storing them in a regular-grid. This method is basically a mapping of scattered data to a regular grid structure (line-segments, rectangles, cubes). At runtime, when we move a cursor through this space, we check in which grid-cell it is, read the 2,4 or 8 pre-computed blend-weights from the edges of the grid-cell and do a either a normal interpolation, a bilinear interpolation or a trilinear interpolation. The method is efficient at runtime, since it is a simple lookup and linear interpolation over a regular grid is straightforward. The CPU-time for this is totally independent of the number of motions you have in a blend-space or the complexity of the annotations.

##
Bit 3: Additional debug information.

These use usually additional text information printed on the screen. Mainly useful for programmers for deep debugging.

##
Building Blend Spaces

The blend-spaces are XML files and they are edited with a text-editor. In the Character Tool we support
**
hot-loading of files
**
. This means you can change the file with a text editor on disk and the system will update it automatically and render the result. With a bit of experience it's very easy to prototype things and do a lot of experimentation.

We will explain all the concepts and parameters while we build different types of bend-spaces. Almost all parameters in the XML files are identical for 1D, 2D and 3D blend-spaces, so it's recommended to do experiments with 1D or 2D blend-spaces, because its way easier to understand the interactions between assets, annotations and different parameters. Don't start with a huge 3D blend space.

##
Example1: 1d-bspace_DummyPara1.bspace

![Image](https://www.cryengine.com/docs/static/attachments/28878088)

This is the simplest blend-space you can build, without any advanced features. The only purpose is to lerp two animations.

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

You can start this in the Character Tool and move the
**
BlendWeight
**
 slider between [0.0f … 1.0f] to create a continuous blend between walk and sprint.

```

`
<Param name="BlendWeight" min="0.0" max="1.0" cells="1"/>
`

```

BlendWeight is the control parameter and min and max is the range for the blend-space.  cells="1" are the amount of cells for the virtual examples. The minimum value is 3. If you pass a lower value (as in out example) the system clamps it to 3. More about that later.

```

`
<Example AName="stand_tac_walk_rifle_fwd_slow_3p_01"  SetPara0="0.0" />
<Example AName="stand_tac_runTurn_rifle_lft_fast_3p_01" SetPara0="1.0" />
`

```

AName are the names of the CAF files.
SetPara0=?
 is a assigning this asset a position in the 1D blend-space. Because this is a 1D-blend space, we place both assets at different position on the x-axis. The walk is at pos 0.0 and the sprint is at 1.0.

```

`
<Blendable>
  <Face p0="0" p1="1" />
</Blendable>
`

```

With the Face tag is used for annotations. Here we tell the blend-node which assets we want to blend. Because this is a super simple setup, the only option is to blend between asset 0 and 1. p0 and p1 are the indices of the 2 assets.

If you delete this tag from the XML, then the system will show only the first assets in the BSpace and blending is not possible.

For 1D blend-spaces it is important that p0 points to the lower parameter and p1 points the higher parameter. If the order is reversed or both parameters are identical, the system will halt with an error. See later "Rules of Annotations".
Before CryENGINE 3.7: MotionCombination
Before CryENGINE 3.7 BSpaces also supported a MotionCombination block, as explained below:

```

`
<MotionCombination>
  <NewStyle Style="stand_tac_weaponPose_rifle_3p_01" />
</MotionCombination>
`

```

The MotionCombination is optional and it is used to partially overwrite certain joints
*
after
*
 the blend. This is mainly a memory optimization feature. Animators were told to delete all finger-controllers, because they take too much memory and are usually identical for all example animations (=holding a gun).

In this special case, the file "
stand_tac_weaponPose_rifle_3p_01
" is a one-frame finger pose to hold a rifle, but it can also be a full animation clip (overwite/additive) or a list of assets, which are all time-warped with the base animation. At some point we will move the functionality into CryMannequin.

In this example1+2 the character can only move on the spot
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
Example2: 1d-bspace_DummyPara2.bspace

Then we can build a generalized one-dimensional blend-space by placing an arbitrary number of clips along a linear scale. This blend-node is doing a lerp between 2 clips adjacent to the input-value.

![Image](https://www.cryengine.com/docs/static/attachments/28878084)

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
 when you change the slider. Without this feature you would get foot-sliding and foot-crossing and other funny things. For time-warping we align several motions by using a single animation-counter and scale the delta-time in relation to the blend-weights.

Imagine these are 2 motions in a blend-space: A walk and a sprint. If the "
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

The scale tag is optional. Its only for debugging in the Character Tool. In this case all 4 assets would be very close together and almost rendered on top of each other. With this parameter we scale the position on the x-axis. This has absolutely no impact on the blending itself.

```

`
<Blendable>
  <Face p0="0" p1="1" />
  <Face p0="1" p1="2" />
  <Face p0="2" p1="3" />
</Blendable>
`

```

All assets in the example list need to be annotated for blending. Assets that are not annotated in <Blendable> will not contribute to the blend. Here we have 4 assets and we need to tell the system explicitly how we want to blended them based on the input value. Because all assets are place on a line, we need only
**
line-segments
**
 for annotations. For a blend-space with 4 assets, 3 line-segments are needed.

It is important that p0 points to the lower parameter and p1 points the higher parameter of the examples. If the order is reversed or both parameters are identical, the system will halt with an error.

##
Example3: 1d-bspace_DummyPara3.bspace

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

If we add these parameters to the previous BSpace, the characters is using its locator motion to move though the world
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
Example4: 1d-bspace_Move1.bspace

And now we move to the main-topic of blend-spaces: Parametric Blending. This is still a simple binary lerp, but we tell the system to
*
extract the parameters
*
 directly out of the motions. The parameter "MoveSpeed" tells the system to extract the move-speed out of the root-motion and inserts it into automatically into the blend-space. The result is a blend-space where all assets have a different positions on the x-axis. These positions are what we call the "natural" motion parameters, because they are coming from the motion directly. In this case, the blend-space represents these real motion parameter, which is not the case when you use SetPara0="?" as we did before.

![Image](https://www.cryengine.com/docs/static/attachments/28878085)

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

If the blend-space is correct, we can use the MoveSpeed slider to move the cursor between the assets and create a continuous blend between all 4 assets. The big difference between
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
 and the system blends automatically the correct assets to generate the move-speed that we want. Fort AI programmers this is more intuitive then setting a [0...1] blend-tree parameter.

This BSpace is a special case where you need SDK 3.5.2, which supports automatic extrapolation for 1D blend-spaces. In previous version it will simply pop to the first asset if you move the cursor outside the range of the fastest/slowest asset. We used pseudo examples to overcome this.

##
Example5: 1d-bspace_Move2.bspace

This example shows how to create
**
pseudo assets
**
 by extrapolating two existing assets. The pseudo assets are rendered with a red cube. These are basically procedurally generated assets.

![Image](https://www.cryengine.com/docs/static/attachments/28878082)

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

Our blend-space is almost perfect for running forward, but there is still a little issue we need to fix. The blend-spaces has a min/max range from
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
. It has only 2 indices/weights that point to the real examples.

```

`
<ExamplePseudo>
  <Pseudo p0="1" p1="0" w0="-0.5" w1="1.5" />
  <Pseudo p0="2" p1="3" w0="-1.0" w1="2.0" />
</ExamplePseudo>
`

```

From a technical point of view it is surprisingly simple. You don't have to change anything in your blending-code. Actually, it's exactly the same blending formula we use for interpolation, just the blend-weights are outside of [0…1] range. For extrapolation it might be acceptable for some motions to have negative values or values bigger then 1.0f. In all cases, the weights should be normalized to always sum to 1.0 to avoid scaling of the character. In our example we do the following operation to create a pseudo asset:

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

Once we placed out pseudo example in the blend-space, we can annotate the new example for blending and create animations even for the area outside of the existing-space.

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
. Sometimes you get surprisingly interesting results, and sometimes only a weird twisted pose. There is no way to tell in advance whether extrapolation will produce good or bad animations. This feature can be very useful in blend-spaces with higher dimensions. With "extrapolated pseudo examples" you can test several asset-combinations in a blend-space, and see which give acceptable results. It's some kind of
**
controlled extrapolation
**
. If you are not happy with the result, then you have to "patch" the blend-space with new examples. We don't recommend overuse of extrapolation, but if you use it only for a couple of seconds, then it's perfectly fine and it helps to save a lot of memory.

##
Example6: 1d-bspace_Move3.bspace

This example shows how to create
**
pseudo assets
**
 by scaling the playback-rate of existing assets. The pseudo assets are rendered with a green cube. These is yet another method to create procedurally generated assets.

![Image](https://www.cryengine.com/docs/static/attachments/28878083)

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
What's the difference between Extrapolated Examples and Playback Scaled Examples?

Both are pseudo examples and in the previous case both techniques gave visually similar results, because the blend-weights or scale-value was pretty small. But both are totally different techniques and in some cases they will give drastically different results.

-
**
Extrapolated Examples
**
 are a blend between
*
two existing assets
*
. With reasonable blend-weights you might get a nice exaggerated animations. The problem starts when you use blend-weights far outside of the [0...1] range. In such a case you might get weird twisted poses and a lot of funny things.

-
**
Playback Scaled Examples
**
 are generated from
*
one single asset
*
. If the scale-value is extreme it might produce a sappy "Charlie Chaplin" motion or an unnatural slow motion.
Is obvious that pseudo assets can never have the quality of real assets produced by an experienced animator, but it's a nice feature to avoid exponential assets explosions in current gen-game. The next example shows a blend-space with one single real asset (speed 4.5m/sec) and two scaled versions of the same asset to cover the full speed-range of 3m/sec - 8m/sec without foot-sliding. We used this trick A LOT in C3 to create "faked" 2D blend-spaces without making new assets. More about that that later when we cover 2D-Blend Spaces.

![Image](https://www.cryengine.com/docs/static/attachments/28878079)

```

`
<ParaGroup>
  <Dimensions>
    <Param name="MoveSpeed" min="3.0" max="+8.0" cells="19" />
  </Dimensions>
  <ExampleList>
    <Example AName="stand_tac_run_rifle_fwd_fast_3p_01" PlaybackScale="0.5" />
    <Example AName="stand_tac_run_rifle_fwd_fast_3p_01" />
    <Example AName="stand_tac_run_rifle_fwd_fast_3p_01" PlaybackScale="1.8" />
  </ExampleList>
  <Blendable>
    <Face p0="0" p1="1" />
    <Face p0="1" p1="2" />
  </Blendable>
</ParaGroup>
`

```

Some more practical example for 1D blend spaces with the remaining motion parameters:

-
MoveSpeed

-
TurnSpeed

-
TravelAngle

-
TravelSlope

-
TurnAngle

-
TravelDist
All these parameters are linked to specialized C++ code, which extracts the values from the root-motion and uses them to drive the blend-spaces. Adding new parameters requires a change in C++ code.

##
Example7:1D-BSpace_Turn.bspace

So far we had only moving-forward, but it's easy to combine it with a turn animation. All we need are 3 assets:
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

![Image](https://www.cryengine.com/docs/static/attachments/28878080)

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
". It's similar to what we mentioned in Example3 before. But in this case we specified only the "TurnSpeed" for control, motion-extraction and delta movement. The system is not aware that we need the move-speed for the delta-movement as well, unless we say it explicitly. Once we set "
MoveSpeed
" we can move through the word.

With the blend slider "
**
Travel Angle
**
" in the Character Tool you can control the curvature. There is no way to adjust the move-speed. Character moves exactly at the speed the animations are authored. We will show later with 2D-blend spaces how to overcome this.

##
Example8:1D-BSpace_Slope.bspace

Another practical example is moving uphill and downhill. All we need are 3 assets:
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

![Image](https://www.cryengine.com/docs/static/attachments/28878081)

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
" in the Character Tool you can control the slope angle. The move-speed is not controllable and the character will moves exactly at the speed the animations are authored. We will show later with 2D-blend spaces how to overcome this.

##
Example9:1D-BSpace_StrafeMove_8clips.bspace

A classical motion example for games is
**
strafing-movement
**
 where the character keeps his body-direction constant
*
(i.e. always looking forward)
*
, but wants to move with his legs forward, sideways or backwards. A simple way to do this with blend-spaces is to take 4, 6 or 8 assets which cover all move-directions we need, and represent each direction by a radiant. Moving forward is always a value of 0.0. All values between 0.0 and -3.147 are movements to the right. All values between 0.0 and +3.147 are movements to the left. The values +3.147 and -3.147 both represent a perfect backwards motion. To cover a full circle we need a blend-space that ranges from -3.147 to +3.147. Or 2pi if you want.

![Image](https://www.cryengine.com/docs/static/attachments/28878077)

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

The result is a straighten out the circle on which the directional animation clips were placed and use the movement direction angle
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
" in the Character Tool you can control the move-direction.

It is probably not immediately obvious why
SetPara0="-3.147"
 and
SetPara0="+3.147"
 are needed. Why do we need to set this values manually? Why can't we extract them automatically out of the file? As mentioned before, to cover a full circle we need a blend-space that ranges from -3.147 to +3.147
*
(or from -pi to +pi)
*
. Unfortunately it is impossible for an artist to create two different assets, one that moves -3.147 and one that moves +3.147. Technically both are the same assets and with automatic extraction both would end up at the same position in the blend-space. That is an illegal case. The only way to use it in the context of a linearized blend-space is to set the parameter directly and place the same asset at different positions in the space. In order words, the parameter
SetParaX
 is yet another way to create pseudo assets to populate a blend-space.

##
How many assets do we need for 360-degree movement?

The absolute minimum is 4 assets; forward, left, right, backwards. This will cover all directions, but the diagonal blends usually don't look good, because
*
forward-motions
*
 and
*
sideway-motions
*
 are not really a compatible for blending. You will always get with foot-sliding, foot-crossing and feet dipping through the ground. That's why 8 assets is recommended.

Another classical issue with strafing is the hip-rotation. Usually the hips point to the right, when strafing right and to the left when strafing left. This feels more natural for the mocap actor. The problem is that doing quick left/right strafes always looks like Samba dancing. That's why it is recommended to keep the hip-orientation static per blend-spaces, and create a new blend-space for each hip-rotation and play an explicit transition to adjust the gate. For such a solution you might need 16 assets for a single speed.

##
Example9:1D-BSpace_StepRot.bspace

Another practical example are
**
IdleStep-Rotations
**
 where a character is turning on the spot.

![Image](https://www.cryengine.com/docs/static/attachments/28878078)

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

The parameter locked="1" avoids changing the parameters while the animation is playing. In most blend-spaces you can change the parameter any time and see the result immediately. But for a few types of blends this is not recommended: Step-Rotations and Idle2Moves. For these blend-spaces when don't want to change the parameter while the animation is playing.

The problem is more extreme for the Idle2Moves. Just imagine a character leans in to start a 90-degree-to-the left run, and the user suddenly decides he wants to run in a different direction. if we change the blend-weights immediately, the animation would look weightless and implausible. With the flag set, the BSpace only takes new inputs when it is pushed into the queue or when the animation reaches the end of the cycle and loops.

The parameter deltaextraction="1" is a used for distance-based motion extractions and is necessary for step-rotations and idle2Moves.

##
Example10:1D-BSpace_I2M_left.bspace

Another practical example are
**
Idle2Move
**
 animations, where a character is stating in an idle pose and then starts a run-transition into any direction.

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

The only solution is to make two separate blend-spaces: one that move to the left and one that moves to the right. Then we can either leave it up to the high level application to pick the correct BSpace
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

##
2D-Blend Spaces

So far we were able to change only one single parameter at a time. But there are many cases in a game where it is required to smoothly change two aspects of a motion simultaneously and independently. This means when we change one parameter, the other parameter stays constant and vice versa.

##
Example: 2D-BSpace_MoveTurn1.bspace

A classical example for a 2D blend space could be a character who moves at different speeds
*
(i.e. slow, fast, sprint)
*
 and also changes his body orientation
*
(i.e. turn left/right at different speeds)
*
 while he moves. When we change the speed, we don't want to change the turn-radius and when we change the turn-radius it should have no impact on the speed.

![Image](https://www.cryengine.com/docs/static/attachments/28878075)

```

`
<ParaGroup>
  <Dimensions>
    <Param name="MoveSpeed" min="+0.2" max="+9.5" cells="19"/>
    <Param name="TurnSpeed" min="-3.5" max="+3.5" cells="19"/>
  </Dimensions>
  <ExampleList>
    <Example AName="stand_tac_walk_rifle_fwd_slow_3p_01" /> //move foward
    <Example AName="stand_tac_run_rifle_fwd_slow_3p_01" /> //move foward
    <Example AName="stand_tac_run_rifle_fwd_fast_3p_01" /> //move foward
    <Example AName="stand_tac_sprint_rifle_fwd_3p_01" /> //move foward
    <Example AName="stand_tac_walkTurn_rifle_lft_slow_3p_01" /> //turn left
    <Example AName="stand_tac_runTurn_rifle_lft_slow_3p_01" /> //turn left
    <Example AName="stand_tac_runTurn_rifle_lft_fast_3p_01" /> //turn left
    <Example AName="stand_tac_walkTurn_rifle_rgt_slow_3p_01" /> //turn right
    <Example AName="stand_tac_runTurn_rifle_rgt_slow_3p_01" /> //turn right
    <Example AName="stand_tac_runTurn_rifle_rgt_fast_3p_01" /> //turn right
  </ExampleList>
  <Blendable>
    <Face p0="0" p1="1" p2="5" p3="4" />
    <Face p0="0" p1="7" p2="8" p3="1" />
    <Face p0="1" p1="2" p2="6" p3="5" />
    <Face p0="1" p1="8" p2="9" p3="2" />
    <Face p0="2" p1="9" p2="3" />
    <Face p0="2" p1="3" p2="6" />
  </Blendable>
</ParaGroup>
`

```

A simple way to do this is to extract the "MoveSpeed" and the "TurnSpeed" as independent values out of the root-motion and place the
*
move-speed
*
 on the
*
x-axis
*
 and the
*
turn-speed
*
 on the
*
y-axis
*
 of a coordinate system. This is handles by the following lines in the XML.

```

`
<Dimensions>
  <Param name="MoveSpeed" min="+0.2" max="+9.5" cells="19"/> //place move-speed automatically on the x-axis
  <Param name="TurnSpeed" min="-3.5" max="+3.5" cells="19"/> //place turn-speed automatically on the y-axis
</Dimensions>
`

```

The association between motion-parameters and coordinate axes is simple: The 1
st
 parameter is always placed on the x-axis, the 2
nd
 parameter is placed on the y-axis, the 3
rd
 parameter goes to the z-axis. We could use "TurnSpeed" as the first parameter in the list to place it on the x-axis.

Because this is 2D space we have to annotate the space with faces. We use
*
triangles
*
 to blend between 3 animations and
*
quats
*
 to blend between 4 animations.

```

`
<Blendable>
  <Face p0="0" p1="1" p2="5" p3="4" /> //quat
  <Face p0="0" p1="7" p2="8" p3="1" /> //quat
  <Face p0="1" p1="2" p2="6" p3="5" /> //quat
  <Face p0="1" p1="8" p2="9" p3="2" /> //quat
  <Face p0="2" p1="9" p2="3" /> //triangle
  <Face p0="2" p1="3" p2="6" /> //triangle
</Blendable>
`

```

General rule for 2D annotations: if you look from birds-eye view onto the blend-space in the Character Tool, then all annotations happen
**
counter-clockwise
**
 for
*
triangles
*
 and
*
quats
*
. Triangles are not allowed to have overlapping points. Quats are not allowed to have overlapping points or a twisted shape.

##
Example: 2D-BSpace_MoveSlope.bspace

In the same way we did the MoveTurn, we can also build MoveSlope. When we change the speed, we don't want to change the slope-angle and when we change the slow-angle it should have no impact on the speed.

##
Example: 2D-BSpace_MoveTurn2.bspace

The previous blend-space had a large area that was not covered by real examples. If you move the cursor into such an area then the blending behaviors is undefined. Since SDK3.5.2 all blend-space type support automatic extrapolation
*
(which means the system is talking the closest annotation and extends it)
*
 but it is not recommended to rely on it. A much better way is to use extrapolated pseudo-examples to cover the whole space.

```

`
<ExamplePseudo>
  <Pseudo p0="1" p1="0" w0="-1.0" w1="2.0" />
  <Pseudo p0="0" p1="4" w0="-2.2" w1="3.2" />
  <Pseudo p0="0" p1="7" w0="-2.0" w1="3.0" />
  <Pseudo p0="1" p1="5" w0="-0.5" w1="1.5" />
  <Pseudo p0="1" p1="8" w0="-0.8" w1="1.8" />
  <Pseudo p0="2" p1="6" w0="-0.5" w1="1.5" />
  <Pseudo p0="2" p1="9" w0="-0.5" w1="1.5" />
  <Pseudo p0="2" p1="3" w0="-2.0" w1="3.0" />
</ExamplePseudo>
`

```

This is also a good case to observe how extrapolated pseudo examples work. Just move the cursor into a corner of the blend-space, i.e. MoveSpeed
**
10m/sec
**
 and TurnSpeed
**
3.14rad/sec
**
. You can see that the strides are much wider and the upper body swings like crazy. This is an extremely exaggerated version of real examples. Such an effect is not possible with pseudo example where you simply change the playback speed.

##
Example: 2D-BSpace_I2M_left.bspace

It's also possible to have
**
Idle2Moves
**
 with different speeds. In the next example we can blend between walkStart and runStart when doing a transition into a walk or run. This XML also uses a combination of real examples and scaled example to cover the whole blend-space.

![Image](https://www.cryengine.com/docs/static/attachments/28878076)

```

`
<ParaGroup>
  <VEGPARAMS Idle2Move="1" />
  <Dimensions>
    <Param name="MoveSpeed" min="+.50" max="+6.00" cells="9" JointName="Bip01 Root" skey="0.9" ekey="1.0"/>
    <Param name="TurnAngle" min="0.00" max="+3.15" cells="9" JointName="Bip01 Root" skey="0.0" ekey="1.0" locked="1" deltaextraction="1"/>
  </Dimensions>
  <AdditionalExtraction>
    <Param name="TravelAngle" />
  </AdditionalExtraction>
  <ExampleList>
    <Example AName="stand_tac_walkStart_rifle_fwd_slow_lf_3p_01" PlaybackScale="0.15" />
    <Example AName="stand_tac_walkStart_rifle_lft_slow_lf_3p_01" PlaybackScale="0.15" />
    <Example AName="stand_tac_walkStart_rifle_rev_slow_lf_3p_01" PlaybackScale="0.15" />
    <Example AName="stand_tac_walkStart_rifle_fwd_slow_lf_3p_01" PlaybackScale="1.00" />
    <Example AName="stand_tac_walkStart_rifle_lft_slow_lf_3p_01" PlaybackScale="1.00" />
    <Example AName="stand_tac_walkStart_rifle_rev_slow_lf_3p_01" PlaybackScale="1.00" />
    <Example AName="stand_tac_runStart_rifle_fwd_fast_lf_3p_01" PlaybackScale="1.00" />
    <Example AName="stand_tac_runStart_rifle_lft_fast_lf_3p_01" PlaybackScale="1.00" />
    <Example AName="stand_tac_runStart_rifle_rev_fast_lf_3p_01" PlaybackScale="1.00" />
    <Example AName="stand_tac_runStart_rifle_fwd_fast_lf_3p_01" PlaybackScale="1.40" />
    <Example AName="stand_tac_runStart_rifle_lft_fast_lf_3p_01" PlaybackScale="1.60" />
    <Example AName="stand_tac_runStart_rifle_rev_fast_lf_3p_01" PlaybackScale="1.70" />
  </ExampleList>
  <Blendable>
    <Face p0="1" p1="4" p2="5" p3="2" />
    <Face p0="0" p1="3" p2="4" p3="1" />
    <Face p0="4" p1="7" p2="8" p3="5" />
    <Face p0="3" p1="6" p2="7" p3="4" />
    <Face p0="7" p1="10" p2="11" p3="8" />
    <Face p0="6" p1="9" p2="10" p3="7" />
  </Blendable>
</ParaGroup>
`

```

One interesting aspect in this XML are the parameter next to "MoveSpeed". An idle 2 move animation has no constant velocity. It start at 0.0f
*
(because the first pose is an idle pose)
*
 and ends at the maximum velocity. The purpose is to create a natural transition into an animation
*
(or a blend-space)
*
 with a known velocity. With skey="0.9" and ekey="1.0". We evaluate only the last 10% of the root motion which
*
(if created in a correct way)
*
 has the target velocity. The parameter JointName="Bip01 Root" is the name of the root joint, which is our default joint.

```

`
<Dimensions>
  <Param name="MoveSpeed" min="+.50" max="+6.00" cells="9" JointName="Bip01 Root" skey="0.9" ekey="1.0"/>
  <Param name="TurnAngle" min="0.00" max="+3.15" cells="9" JointName="Bip01 Root" skey="0.0" ekey="1.0" locked="1" deltaextraction="1"/>
</Dimensions>
`

```

##
Example: 2D-BSpace_MoveStrafe1.bspace

Another example for a 2D blend space is a character who moves at different speeds
*
(i.e. slow, fast, sprint)
*
 and also changes his move orientation
*
(i.e. forward/left/right/backwards)
*
 while he moves. When we change the speed, we don't want to change the move-direction and when we change the move-direction it should have no impact on the speed.

![Image](https://www.cryengine.com/docs/static/attachments/28878073)

```

`
<ParaGroup>
  <Dimensions>
    <Param name="MoveSpeed" min="+1.0" max="+4.5" cells="19" />
    <Param name="TravelAngle" min="-3.14" max="+3.14" cells="17" />
  </Dimensions>
  <ExampleList>
    <Example AName="stand_tac_walk_rifle_bwd_slow_3p_01" SetPara1="-3.141" />
    <Example AName="stand_tac_walkCross_rifle_bRgt_slow_3p_01" />
    <Example AName="stand_tac_walkStr_rifle_rgt_slow_3p_01" />
    <Example AName="stand_tac_walk_rifle_fwd_slow_3p_01" />
    <Example AName="stand_tac_walkCross_rifle_fLft_slow_3p_01" />
    <Example AName="stand_tac_walkStr_rifle_lft_slow_3p_01" />
    <Example AName="stand_tac_walk_rifle_bwd_slow_3p_01" SetPara1="+3.141" />
    <Example AName="stand_tac_run_rifle_bwd_fast_3p_01" SetPara1="-3.141" />
    <Example AName="stand_tac_runCross_rifle_bRgt_fast_3p_01" />
    <Example AName="stand_tac_runStr_rifle_rgt_fast_3p_01" />
    <Example AName="stand_tac_run_rifle_fwd_fast_3p_01" />
    <Example AName="stand_tac_runCross_rifle_fLft_fast_3p_01" />
    <Example AName="stand_tac_runStr_rifle_lft_fast_3p_01" />
    <Example AName="stand_tac_run_rifle_bwd_fast_3p_01" SetPara1="+3.141" />
  </ExampleList>
  <Blendable>
    <Face p0=" 0" p1=" 7" p2=" 8" p3=" 1" />
    <Face p0=" 1" p1=" 8" p2=" 9" p3=" 2" />
    <Face p0=" 2" p1=" 9" p2="10" p3=" 3" />
    <Face p0=" 3" p1="10" p2="11" p3=" 4" />
    <Face p0=" 4" p1="11" p2="12" p3=" 5" />
    <Face p0=" 5" p1="12" p2="13" p3=" 6" />
  </Blendable>
</ParaGroup>
`

```

For this blend we use 6 walk-directions (=slow-motion) and 6 run-directions (=fast-motion). Then we extract the "MoveSpeed" and the "TravelAngle" as independent values out of the root-motion and place the
*
move-speed
*
 on the
*
x-axis
*
 and the
*
travel-angle
*
 on the
*
y-axis
*
 of a coordinate system. This is handled by the following lines in the XML.

```

`
<Dimensions>
  <Param name="MoveSpeed" min="+1.0" max="+4.5" cells="19" />
  <Param name="TravelAngle" min="-3.14" max="+3.14" cells="17" />
</Dimensions>
`

```

##
Example: 2D-BSpace_MoveStrafe2.bspace

In the previous strafe example we had walk and run assets for different speeds. Sometimes you need only a slight variations of move-speeds where the visual difference in the assets is so small that you don't want to create new assets. In this example we took the crouch strafe and use PlaybackScale to create a pseudo assets with different move-speeds. So every asset is used twice, but with a different speed. Because the duplicated assets also have different positions it the space, we can use them to build a blend space with 2 dimensions. With this simple trick we can generate move-speeds between
**
0.2m/sec
**
 and
**
2.5m/sec
**
 by scaling the speed of original assets.

![Image](https://www.cryengine.com/docs/static/attachments/28878074)

```

`
<ParaGroup>
  <Dimensions>
    <Param name="MoveSpeed" min="+0.20" max="+2.50" cells="9" />
    <Param name="TravelAngle" min="-3.14" max="+3.14" cells="29" />
  </Dimensions>
  <ExampleList>
    <Example AName="crouch_tac_walk_rifle_bwd_slow_3p_01" SetPara1="-3.147" PlaybackScale="0.15" />
    <Example AName="crouch_tac_walkCross_rifle_bRgt_slow_3p_01" PlaybackScale="0.15"/>
    <Example AName="crouch_tac_walkStr_rifle_rgt_slow_3p_01" PlaybackScale="0.15" />
    <Example AName="crouch_tac_walk_rifle_fwd_slow_3p_01" PlaybackScale="0.15" />
    <Example AName="crouch_tac_walkCross_rifle_fLft_slow_3p_01" PlaybackScale="0.15" />
    <Example AName="crouch_tac_walkStr_rifle_lft_slow_3p_01" PlaybackScale="0.15" />
    <Example AName="crouch_tac_walk_rifle_bwd_slow_3p_01" SetPara1="+3.147" PlaybackScale="0.15" />
    <Example AName="crouch_tac_walk_rifle_bwd_slow_3p_01" SetPara1="-3.147" PlaybackScale="4.50" />
    <Example AName="crouch_tac_walkCross_rifle_bRgt_slow_3p_01" PlaybackScale="6.00" />
    <Example AName="crouch_tac_walkStr_rifle_rgt_slow_3p_01" PlaybackScale="3.50" />
    <Example AName="crouch_tac_walk_rifle_fwd_slow_3p_01" PlaybackScale="3.40" />
    <Example AName="crouch_tac_walkCross_rifle_fLft_slow_3p_01" PlaybackScale="4.40" />
    <Example AName="crouch_tac_walkStr_rifle_lft_slow_3p_01" PlaybackScale="4.40" />
    <Example AName="crouch_tac_walk_rifle_bwd_slow_3p_01" SetPara1="+3.147" PlaybackScale="4.40" />
  </ExampleList>
  <Blendable>
    <Face p0="6" p1="5" p2="12" p3="13" />
    <Face p0="5" p1="4" p2="11" p3="12" />
    <Face p0="4" p1="3" p2="10" p3="11" />
    <Face p0="3" p1="2" p2="9" p3="10" />
    <Face p0="2" p1="1" p2="8" p3="9" />
    <Face p0="1" p1="0" p2="7" p3="8" />
  </Blendable>
</ParaGroup>
`

```

##
3D-Blend Spaces

All the concepts we learned about 1D and 2D apply to 3D blend-spaces as well. There is nothing special about 3D blend-spaces, except the fact that we have an additional dimension.

The only issue we have with 3D and higher dimension is, that it starts to get harder to visualize and to debug.

##
Example: 3D-BSpace_MoveTurnSlope.bspace

One application for 3d is to put m
**
ove-speed
**
 on X,
**
turn-speed
**
 on Y,
**
slope-angle
**
 on Z. You can see in which direction this is going: each
**
new control-parameter
**
 is actually
**
a new dimension
**
 in the Blend-Space. In 3D we can control uphill/downhill motion and we can combine this with all different speeds and turn-angles.

![Image](https://www.cryengine.com/docs/static/attachments/28878071)

```

`
<ParaGroup>
  <Dimensions>
    <Param name="MoveSpeed" min="+0.2" max="+9.5" cells="7"/>
    <Param name="TurnSpeed" min="-3.8" max="+3.8" cells="7"/>
    <Param name="TravelSlope" min="-0.5" max="+0.5" scale="4.4" cells="5"/>
  </Dimensions>
  <ExampleList>
    <Example AName="stand_tac_walk_rifle_fwd_slow_3p_01" />
    <Example AName="stand_tac_run_rifle_fwd_slow_3p_01" />
    <Example AName="stand_tac_run_rifle_fwd_fast_3p_01" />
    <Example AName="stand_tac_sprint_rifle_fwd_3p_01" />
    <Example AName="stand_tac_walkTurn_rifle_lft_slow_3p_01"/> //turn
    <Example AName="stand_tac_runTurn_rifle_lft_slow_3p_01" /> //turn
    <Example AName="stand_tac_runTurn_rifle_lft_fast_3p_01" /> //turn
    <Example AName="stand_tac_walkTurn_rifle_rgt_slow_3p_01"/> //turn
    <Example AName="stand_tac_runTurn_rifle_rgt_slow_3p_01" /> //turn
    <Example AName="stand_tac_runTurn_rifle_rgt_fast_3p_01" /> //turn
    <Example AName="stand_tac_walkUp_rifle_fwd_slow_3p_01" /> //slope
    <Example AName="stand_tac_runUp_rifle_fwd_slow_3p_01" /> //slope
    <Example AName="stand_tac_runUp_rifle_fwd_fast_3p_01" /> //slope
    <Example AName="stand_tac_walkDown_rifle_fwd_slow_3p_01" /> //slope
    <Example AName="stand_tac_runDown_rifle_fwd_slow_3p_01" /> //slope
    <Example AName="stand_tac_runDown_rifle_fwd_fast_3p_01" /> //slope
  </ExampleList>
  <ExamplePseudo>
    <Pseudo p0="1" p1="0" w0="-1.0" w1="2.0" />
    <Pseudo p0="0" p1="4" w0="-2.0" w1="3.0" />
    <Pseudo p0="0" p1="7" w0="-2.0" w1="3.0" />
    <Pseudo p0="1" p1="5" w0="-1.0" w1="2.0" />
    <Pseudo p0="1" p1="8" w0="-1.0" w1="2.0" />
    <Pseudo p0="2" p1="6" w0="-1.0" w1="2.0" />
    <Pseudo p0="2" p1="9" w0="-1.0" w1="2.0" />
    <Pseudo p0="2" p1="3" w0="-2.0" w1="3.0" />
    <Pseudo p0="0" p1="10" w0="-2.0" w1="3.0" />
    <Pseudo p0="1" p1="11" w0="-0.8" w1="1.8" />
    <Pseudo p0="2" p1="12" w0="-0.8" w1="1.8" />
    <Pseudo p0="0" p1="13" w0="-1.6" w1="2.6" />
    <Pseudo p0="1" p1="14" w0="-1.6" w1="2.6" />
    <Pseudo p0="2" p1="15" w0="-1.8" w1="2.8" />
  </ExamplePseudo>
  <Blendable>
//volumes facing up
    <Face p0="0" p1="17" p2="16" p3="24" /> //tetrahedron
    <Face p0="0" p1="16" p2="18" p3="24" /> //tetrahedron
    <Face p0="1" p1="19" p2="17" p3="0" p4="25" p5="24"/> //prism
    <Face p0="0" p1="18" p2="20" p3="1" p4="24" p5="25"/> //prism
    <Face p0="2" p1="21" p2="19" p3="1" p4="26" p5="25"/> //prism
    <Face p0="1" p1="20" p2="22" p3="2" p4="25" p5="26"/> //prism
    <Face p0="2" p1="23" p2="21" p3="26" />
    <Face p0="2" p1="22" p2="23" p3="26" />
//volumes facing down
    <Face p2="0" p1="17" p0="16" p3="27" /> //tetrahedron
    <Face p2="0" p1="16" p0="18" p3="27" /> //tetrahedron
    <Face p3="1" p2="19" p1="17" p0="0" p4="27" p5="28"/> //prism
    <Face p3="0" p2="18" p1="20" p0="1" p4="28" p5="27"/> //prism
    <Face p3="2" p2="21" p1="19" p0="1" p4="28" p5="29"/> //prism
    <Face p3="1" p2="20" p1="22" p0="2" p4="29" p5="28"/> //prism
    <Face p2="2" p1="23" p0="21" p3="29" /> //tetrahedron
    <Face p2="2" p1="22" p0="23" p3="29" /> //tetrahedron
  </Blendable>
</ParaGroup>
`

```

3D blend spaces look scary and confusing the first time you look at them, but they are manageable if you follow a certain structure. The base setup to this is similar to
**
2D-BSpace_MoveTurn2.bspace
**
. Just compare the first 10 entries in the <ExampleList> and the first 8 entries in <ExamplePseudo>. The only difference is that we also added 6 slope assets. To annotate a 3D blend-space we use volumes like tetrahedrons, pyramids and prisms.

Each volume has a ground plane (3-4 points) and a tip (1-2 points). If the tip points up, the vertices on the ground plane must be annotated
**
counter clockwise
**
. If the tip points down, the vertices on the ground plane must be annotated
**
clockwise
**
.

##
Example: 3D-BSpace_MoveTurnSlope_Combination.comb

3D blend spaces are more difficult to debug, even with a very structured design. Fortunately, many higher dimensional blends are a combination of simple lower-dimensional blends. This relationship makes it possible to combine two 2D spaces into a 3D space and two 3D spaces into a 4D space. These are simple linear combinations. We want to show how to recreate the previous "
**
3D-BSpace_MoveTurnSlope.bspace"
**
 with a simple combination of 2D blend-spaces. This is also a good example to show another application of the *.COMB file.

We slightly modified the 2D "MoveSlope" and "MoveTurn" blend-spaces. Take a look at these files:

-
`
2D-BSpace_MoveSlopeExt.bspace
`

-
`
 2D-BSpace_MoveTurnExt.bspace
`
In the slope example we change the scope to allow a very big and almost unnatural extrapolation of the slope assets.

```

`
<Dimensions>
  <Param name="MoveSpeed" min="+0.2" max="+9.5" cells="17"/>
  <Param name="TravelSlope" min="-1.0" max="+1.0" scale="4.4" cells="37"/>
</Dimensions>
`

```

We did the same in the turn example, where we allowed an extreme turn-speed value.

```

`
<Dimensions>
  <Param name="MoveSpeed" min="+0.2" max="+9.5" cells="19"/>
  <Param name="TurnSpeed" min="-6.30" max="+6.30" cells="39"/>
</Dimensions>
`

```

The file "
**
3D-BSpace_MoveTurnSlope_Combination.comb
**
" combines both blend-spaces by scaling the parameters "MoveSpeed" and "TurnSpeed" by 2 and then doing a 50%-50% blend with the result of both blend-spaces. The result is a new blend-spaces where you can control all 3 features independently. This is a practical example how to linearly combine blend-spaces and combine its features.

```

`
<CombinedBlendSpace>
  <Dimensions>
    <Param name="MoveSpeed" />
    <Param name="TurnSpeed" ParaScale="2.0" />
    <Param name="TravelSlope" ParaScale="2.0" />
  </Dimensions>
  <BlendSpaces>
    <BlendSpace AName="animations/human/male/lmg/stand/2D-BSpace_MoveSlopeExt.bspace" />
    <BlendSpace AName="animations/human/male/lmg/stand/2D-BSpace_MoveTurnExt.bspace" />
  </BlendSpaces>
</CombinedBlendSpace>
`

```

The same concept works with higher dimensions as well. For C3 we took two 3D blend-spaces and combined them into a 4D blend-space. That was just a proof of concept how far we can push it with blend-space algebra.

##
Rules of Annotations

With blend-spaces we treat animation-blending as a geometrical problem. The setup and the internal structures of a blend-space is similar to a model-mesh with a
**
vertex-buffer
**
 and an
**
index-buffer
**
: Each animation-clip in the ExampleList represents a point in a coordinate-system. In other words we associate each animation with a 1D, 2D or 3D position in a space and the list of all examples is the vertex-buffer. The tricky part of course is to covert animations into positions in a space. In our case the positioning of animations can happen either
**
manually
**
*
(with SetParaX=?)
*
 or with
**
automatic extraction
**
*
(which is recommended if you want proper parametric blending)
*
.

```

`
<ExampleList>
  <Example AName="stand_tac_walk_rifle_fwd_slow_3p_01" />
  <Example AName="stand_tac_run_rifle_fwd_slow_3p_01" />
  <Example AName="stand_tac_run_rifle_fwd_fast_3p_01" />
  <Example AName="stand_tac_sprint_rifle_fwd_3p_01" />
  <Example AName="stand_tac_walkTurn_rifle_lft_slow_3p_01" />
  <Example AName="stand_tac_runTurn_rifle_lft_slow_3p_01" />
  <Example AName="stand_tac_runTurn_rifle_lft_fast_3p_01" />
  <Example AName="stand_tac_walkTurn_rifle_rgt_slow_3p_01" />
  <Example AName="stand_tac_runTurn_rifle_rgt_slow_3p_01" />
  <Example AName="stand_tac_runTurn_rifle_rgt_fast_3p_01" />
</ExampleList>
`

```

These points in space are connected by an index-list. All entries in Blendable are the index-buffer. That's how we define (annotate) which assets can be blended in a reasonable way. This annotation happens manually.

```

`
<Blendable>
  <Face p0="0" p1="1" p2="5" p3="4"/> //quat annotation
  <Face p0="0" p1="7" p2="8" p3="1"/> //quat annotation
  <Face p0="1" p1="2" p2="6" p3="5"/> //quat annotation
  <Face p0="1" p1="8" p2="9" p3="2"/> //quat annotation
  <Face p0="2" p1="9" p2="3" /> //triangle annotation
  <Face p0="2" p1="3" p2="6" /> //triangle annotation
</Blendable>
`

```

This kind of
**
geometrical relationship
**
 between animation-clips is very useful for
**
parametric-blending.
**
 Because there are so many similarities to meshes and rendering, it should be obvious that it is impossible to visualize a blend-space as a tree-structure, especially if you want to do multi-dimensional blends in 2D- and 3D-spaces.

Here are the basic rules to annotate the blend-spaces:

##
1D-Annotations

In
**
1D-blend spaces
**
 all the points are on a line and that's why we use
*
line-segments
*
 for annotations. It is important that p0 points to the lower parameter and p1 points the higher parameter of the examples. If the order is reversed or both parameters are identical, the system will halt with an error.

It is also important to make sure that there are no gaps in the line
*
(holes that are not covered with a line-segments)
*
 or overlapping line-segments. This might lead to undefined behavior. At runtime we check if the
**
input-parameter
**
 is inside of one those line-segments and then interpolate between those two animations. In the ideal situation the input-parameter should always be inside of a line-segment. Since SDK3.5.2 we added automatic extrapolation
*
(which is pretty predicable for 1D spaces)
*
, but a bit slower compared to a properly annotated space.

##
2D-Annotations

In
**
2D-blend spaces
**
 all the points are on a plane. You look from birds-eye view onto the blend-space in the Character Tool, then all annotations happen
**
counter-clockwise
**
 for
*
triangles
*
 and
*
quats
*
.

It is important to make sure that there are no gaps in the space
*
(holes that are not covered with a face)
*
 or overlapping triangles and quats. This might lead to undefined behavior. At runtime we check if the
**
input-parameter
**
 is inside of one those
*
triangles
*
 (3 animations) and
*
quats
*
 (4 animations) and then interpolate between those animations. In the ideal situation the input-parameter should always be inside of a face.

##
3D-Annotations

In
**
3D blend spaces
**
 we have
**
*
tetrahedrons
*
**
,
*
pyramids
*
 and
*
prisms
*
. All of them have a ground plane (3-4 points) and a tip (1-2 points). If the tip points up, the vertices on the ground plane must be annotated
**
counter clockwise
**
.

If the tip points down, the vertices on the ground plane must be annotated
**
clockwise
**
. (This doesn't matter in the case of tetrahedrons, but it can't hurt to use the same rule for consistency.)

It is important to make sure that there are no gaps in the space
*
(holes that are not covered with a volume)
*
 or overlapping volumes. This might lead to undefined behavior. At runtime we check if the
**
input-parameter
**
 is inside of one those volumes and then interpolate between those animations. In the ideal situation the input-parameter should always be inside of a volumes.

##
Workflow to annotate blend-spaces

We are aware that the setup process with a text-editor is a bit inconvenient. But if you use the
hot-loading
 feature in a correct way, you can reduce this process to 1-5 minutes for most blend-spaces.

If we setup a new blend space we use the following steps:

**
Step 1:
**
 First we define which parameters are needed and then we create the example list in the XML-file. A minimalistic XML can look like the one below. Make sure there is nothing except <Dimensions> and the <ExampleList> in the file.

```

`
<ParaGroup>
  <Dimensions>
    <Param name="MoveSpeed" min="+0.2" max="+9.5" cells="19"/>
    <Param name="TurnSpeed" min="-3.5" max="+3.5" cells="19"/>
  </Dimensions>
  <ExampleList>
    <Example AName="stand_tac_walk_rifle_fwd_slow_3p_01" />
    <Example AName="stand_tac_run_rifle_fwd_slow_3p_01" />
    <Example AName="stand_tac_run_rifle_fwd_fast_3p_01" />
    <Example AName="stand_tac_sprint_rifle_fwd_3p_01" />
    <Example AName="stand_tac_walkTurn_rifle_lft_slow_3p_01" />
    <Example AName="stand_tac_runTurn_rifle_lft_slow_3p_01" />
    <Example AName="stand_tac_runTurn_rifle_lft_fast_3p_01" />
    <Example AName="stand_tac_walkTurn_rifle_rgt_slow_3p_01" />
    <Example AName="stand_tac_runTurn_rifle_rgt_slow_3p_01" />
    <Example AName="stand_tac_runTurn_rifle_rgt_fast_3p_01" />
  </ExampleList>
</ParaGroup>
`

```

**
Step 2:
**
 Then we load this file in the Character Tool. Blending is not possible yet, but we can already check the quality of each single assets. We use
**
ca_DrawVEGInfo 3.5
**
 and check if all assets are valid, have a proper locomotion locator, don't overlap in the space, cover the required range, etc...

**
Step 3:
**
 Then we pick 3 or 4 assets that seem to be blendable and annotate them in a text-editor with the first triangle or quat. We save the file and the the Character Tool should update the blend-space immediately. Now we use the slider in the Character Tool and move the cursor inside of the annotated face to check if the blend looks as expected. If the blend looks bad, we have to check what might be wrong with the annotation or the assets and send them back to the animators.

**
Step 4:
**
 If the first annotation gives the expected results, we move on to create the next second annotation. After each annotation we check the quality of the blending. We repeat the process until all clips are annotated for blending.

**
Step 5:
**
 Next we check for holes in the space and try to find ways to cover them with pseudo assets. If pseudo assets are not possible, we have to tell the animators to create new real assets. If pseudo assets give acceptable results, we leave them in the space and annotate them as well. We repeat the process until the whole space is covered.

The hot-loading system tries to catch most errors, i.e. typos that break the XML-format, invalid parameters, not existing file-names. If such an error is detected, the BSpace is deactivated and there is an error-messages in the log. There are still some entries possible that are hard to catch and create a fp-exception on the lowest level. In such a case restart Sandbox is the only option.

##
Additive and Override Animation

Just like a single animation, blend-spaces can be played on any animation layer (not restricted to layer 0).

A blend-space can also contain additive or override animation, though you are not allowed to mix different types within one blend-space.

Before CryENGINE 3.7: Limitations
In versions before CRYENGINE 3.7 BSpaces only work on layer 0, and additive or override animation is not supported.

[Visualizing BSpaces](#visualizing-bspaces)
[Debug parameters of ca_DrawVEGInfo](#debug-parameters-of-cadrawveginfo)
[Building Blend Spaces](#building-blend-spaces)
[2D-Blend Spaces](#2d-blend-spaces)
[3D-Blend Spaces](#3d-blend-spaces)
[Rules of Annotations](#rules-of-annotations)
[Additive and Override Animation](#additive-and-override-animation)
