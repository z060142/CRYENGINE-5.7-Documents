# Mannequin Parameters/Conditions

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/29450867
- Page ID: 29450867
- Breadcrumb: Editor Tools > Animation Tab > Mannequin Editor > Mannequin Concepts > Mannequin Parameters/Conditions
- Parent: Mannequin Concepts

## Content

![Image](https://www.cryengine.com/docs/static/attachments/29934023)

##
Overview

##
Sections

The mannequin editor lets you edit two different types of parameters: 'real' mannequin parameters and motion parameters. Both are displayed as parameters in the mannequin editor but are quite different under the hood.

[Sections](#sections)
['Real' Mannequin Parameters](#real-mannequin-parameters)
[Motion Parameters](#motion-parameters)

##
'Real' Mannequin Parameters

These are the parameters the game code uses to provide extra information to playing
[actions](../Mannequin%20Technical%20Topics/Mannequin%20Actions.md)
 and
[procedural clips](Mannequin%20Procedural%20Clips/Procedural%20Clip%20Directory.md)
. Some examples are: a target position when aligning an entity in the world, a weight value when fading an animation in/out, or a sound parameter passed to the sound system.

All parameters simply have a
*
name
*
 and a
*
value
*
. The value's type can be anything from a number over a position/orientation in space to even more complicated structures.

Only a standard location with name "TargetPos" can be previewed in the editor though by using the
*
Params
*
 track in the
[Mannequin Previewer](../../Mannequin%20Editor.md#MannequinEditor-previewer)
.

When a procedural clip relies on a specific parameter and specific parameter type it is documented along with the procedural clip, see
[Procedural Clip Directory](Mannequin%20Procedural%20Clips/Procedural%20Clip%20Directory.md)
.

##
Motion Parameters

Motion parameters are the parameters that get passed along to parametric animation, the
[Blend Spaces](../../Character%20Tool/Blend%20Spaces%20-%20Character%20Tool.md)
.

You can preview how these motion parameters will influence your animation
 by adding keys on the track named
*
Params
*
 in the
[Mannequin Previewer](../../Mannequin%20Editor.md#MannequinEditor-previewer)
. (see also
[Mannequin Editor Tutorial 2 - Tags & Previewing](../../../../Tutorials/Animation%20and%20Characters/Mannequin%20Editor/Mannequin%20Editor%20Tutorial%202%20-%20Tags%20%26%20Previewing.md)
)
