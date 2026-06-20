# Enabling Charts in Sandbox

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/27593341
- Page ID: 27593341
- Breadcrumb: Post-processing > Tutorial - Color Grading > Enabling Charts in Sandbox
- Parent: Tutorial - Color Grading

## Content

##
Applying the LUT in the Editor

There are a few ways to apply the LUT in the editor. Unfortunately there's no UI integration for this, so for previewing purposes, you need to use the Console.

##
Using the Console

Make sure colorgrading is active by default (it should be) with this CVar:
**
r_ColorGrading 1
**

Load the new colorchart/LUT using this cvar:
**
r_ColorGradingChartImage Textures/Colorcharts/colorgrade_cch.tif
**

Note that you need to give the full path with GameSDK as the root.

##
Using Flowgraph (applying the LUT during gameplay)

Open flowgraph, and add the node:
**
Image:ColorGradient
**

For single player missions, you will also need to add a few nodes to set "default" colorgrading options. This is because the UI calls certain colorgrading LUTs when the player is hit, or when the player uses Focus.

The node is called:
**
Image:ColorGradientDefaults
**

-
You'll need to set the "Effect" input to "ColorGradeTexture" to set this LUT as the default applied LUT

-
Depending on the grade, and how it looks in gameplay when you get hit or use focus, you might also need to apply this LUT to the Effects named "FadeOutHitGradeTexture", and "FocusStartGradeTexture".
In the "TexturePath" input, add the full path of the LUT (just like in the Console example above).

Trigger it all on GameStart or something else.

The flowgraph should look something like this:

![Image](https://www.cryengine.com/docs/static/attachments/14975509)

Now when you jump in game (or trigger it), the grade should be switched on.

Icon
Note that if you have multiple grades throughout a level, you can use the "TransitionTime" input to blend them together.
