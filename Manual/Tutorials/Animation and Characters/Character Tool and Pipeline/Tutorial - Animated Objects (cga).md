# Tutorial - Animated Objects (cga)

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/23299172
- Page ID: 23299172
- Breadcrumb: Tutorials > Animation and Characters > Character Tool and Pipeline > Tutorial - Animated Objects (cga)
- Parent: Character Tool and Pipeline

## Content

##
Overview

This section covers how to setup simple animated geometry. *.cga's can be used in a wide variety of situations, from single one-shot animations to complex setups such as vehicles with multiple animations.

##
Rules for CGA's & Exporting Animations

-
Transform controllers must be converted to
**
tension-continuity-bias
**
 (
TCB), for both position and rotation tracks.

-
*.cga animations (*.anm) do not support compression!

-
If the object only requires 1 animation, then this will be stored within the *.cga file as the Default animation.

-
The Default animation will be the entire timeline.

-
Multiple animations for the same object must be saved & exported out as *.anm files.
**
These have to follow a strict naming convention
**
.

-
Must be prefixed with the *.cga's name.

**
Correct
:
**

**
hmmwv
**
_door_left_front_enter.anm

**
Incorrect
:
**

**

**
door_left_front_enter.anm

-
The
**
first underscore
**
 within the filename denotes the start of the animation name in the engine.

-
When inside the
**
Character Tool
**
 and when previewing the *.cga's animations only the animation name is shown and not the entire filename.
*
Pic1: Note the filename difference between the actual filename in the .pak file vs. what is seen in the Character Tool

*
[Image: /docs/static/attachments/23434655]

##
Tutorials

Depending on the DCC tool used - the links below show you how to setup *.cga's.

-
**
[/docs/static/engines/cryengine-5/categories/23756816/pages/23299331](
Tutorial For 3dsMax
)
**

-
**
[/docs/static/engines/cryengine-5/categories/23756816/pages/23299333](
Tutorial For Maya
)
**

##
Distinction between a Maya CGA export and Max CGA export

Maya:
 |
3ds Max:
 |

A *.cga file exported from Maya always needs at least ONE *.anm file to have animation, so make use of the "Anim Manager" to set at least a time range of a "default" animation.
 |
A "default" named animation is always inside the *.cga file exported from Max. You needn't export an *.anm file separately.
 |

Maya scene hierarchy for *.cga is more complex than in Max. This involves adding "*_helper" group node(s) and a standard material export. First this is because the "*_helper" node acts as the ROOT and any root node may not have any animations.
 |
Straightforward scene hierarchy.
 |

Naming of your Maya groups, the "cryExportNode"(s) especially, is important for your *.cga and animation file names. Since Maya depends on names (the string value), you must consider this when building the export hierarchy.
 |
Naming of your *.cga object and its animation (and at long last, your *.cga & *.anm files) is critical when it involves multiple *.cga animations.
 |

Only the "*_group" nodes in your Maya scene hierarchy can hold animation data (animCurves). Any other animated transform node will be ignored in the *.cga export.
 |
Convert your "Animation Controllers" to TCB-type Controllers before export. This may include baking the animation frame-by-frame and collapsing any layered controllers (List Controllers!).
 |

Exporting multiple animations is straightforward using "Anim Manager".
 |
Current *.cga export for Max is a bit awkward with the CRYENGINE Export utility when it comes to generating multiple *.anm files.
 |

[#rules-for-cgas-and-exporting-animations](
Rules for CGA's & Exporting Animations
)
[#tutorials](
Tutorials
)
[#distinction-between-a-maya-cga-export-and-max-cga-export](
Distinction between a Maya CGA export and Max CGA export
)
