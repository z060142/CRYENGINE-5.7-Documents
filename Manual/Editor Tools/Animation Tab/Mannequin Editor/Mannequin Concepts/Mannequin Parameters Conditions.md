# Mannequin Parameters/Conditions

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/29450867
- Page ID: 29450867
- Breadcrumb: Editor Tools > Animation Tab > Mannequin Editor > Mannequin Concepts > Mannequin Parameters/Conditions
- Parent: Mannequin Concepts

## Content

[Image: /docs/static/attachments/29934023]

##
Overview

##
Sections

The mannequin editor lets you edit two different types of parameters: 'real' mannequin parameters and motion parameters. Both are displayed as parameters in the mannequin editor but are quite different under the hood.

[#sections](
Sections
)
[#real-mannequin-parameters](
'Real' Mannequin Parameters
)
[#motion-parameters](
Motion Parameters
)

##
'Real' Mannequin Parameters

These are the parameters the game code uses to provide extra information to playing
[/docs/static/engines/cryengine-5/categories/23756816/pages/23308467](
actions
)
 and
[/docs/static/engines/cryengine-5/categories/23756816/pages/29798726](
procedural clips
)
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
[/docs/static/engines/cryengine-5/categories/23756816/pages/27594502#MannequinEditor-previewer](
Mannequin Previewer
)
.

When a procedural clip relies on a specific parameter and specific parameter type it is documented along with the procedural clip, see
[/docs/static/engines/cryengine-5/categories/23756816/pages/29798726](
Procedural Clip Directory
)
.

##
Motion Parameters

Motion parameters are the parameters that get passed along to parametric animation, the
[/docs/static/engines/cryengine-5/categories/23756816/pages/28186170](
Blend Spaces
)
.

You can preview how these motion parameters will influence your animation
 by adding keys on the track named
*
Params
*
 in the
[/docs/static/engines/cryengine-5/categories/23756816/pages/27594502#MannequinEditor-previewer](
Mannequin Previewer
)
. (see also
[/docs/static/engines/cryengine-5/categories/23756816/pages/23308484](
Mannequin Editor Tutorial 2 - Tags & Previewing
)
)
