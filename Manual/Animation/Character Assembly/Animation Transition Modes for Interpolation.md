# Animation Transition Modes for Interpolation

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/26216402
- Page ID: 26216402
- Breadcrumb: Animation > Character Assembly > Animation Transition Modes for Interpolation
- Parent: Character Assembly

## Content

##
Overview

For improving animation transition quality, you need to introduce blending options globally per CVar or per Animation. This CVar option allows you to
find the right style of interpolation in a project.

##
Implementation

To activate this functionality, enable the cvar
**
ca_DefaultTransitionInterpolationType
**
 from the console.

Cvar
 |
Description
 |

**
*
ca_DefaultTransitionInterpolationType
*
**
 |
Changes transition interpolation method, and allows autocomplete of transition modes. The various types of modes that can be used are listed below:

-
Linear

-
QuadraticIn

-
QuadraticOut

-
QuadraticInOut

-
SineIn

-
SineOut

-
SineInOut
Sample command:
*

ca_DefaultTransitionInterpolationType
*
 <
*
interpolation mode
*
>

 |

For example, if the project requires more snappy animations, you can choose
**
Linear
**
 as interpolation. If you want more smooth interpolation, you can choose
**
SineInOut
**
 mode.
