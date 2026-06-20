# Math Lua

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/23306629
- Page ID: 23306629
- Breadcrumb: CRYENGINE Engine Code > Engine Modules > CryScriptSystem > Lua Scripting > Common Lua Functions > Math Lua
- Parent: Common Lua Functions

## Content

##
Math utility functions, constants and global vector definitions

Defines commonly used math utility functions, constants and global vectors.

-
File location:
`
Game/Scripts/Utils/Math.lua
`

-
Loaded from:
`
Game/Scripts/common.lua
`

##
Global Vectors

The following globals should be used to avoid temporary Lua memory allocations:

**
Global Name
**

 |
**
Description
**

 |

g_Vectors.v000

 |
basic zero vector

 |

g_Vectors.v001

 |
positive z-axis direction vector

 |

g_Vectors.v010

 |
positive y-axis direction vector

 |

g_Vectors.v100

 |
positive x-axis direction vector

 |

g_Vectors.v101

 |
x and z-axis direction vector

 |

g_Vectors.v110

 |
x and y-axis direction vector

 |

g_Vectors.v111

 |
x, y and z-axis vector

 |

g_Vectors.up

 |
positive z-axis direction vector

 |

g_Vectors.down

 |
negative z-axis direction vector

 |

g_Vectors.temp

 |
temporary zero vector

 |

g_Vectors.tempColor

 |
temporary zero vector, commonly used for passing rgb color values

 |

g_Vectors.temp_v1

 |
temporary zero vector

 |

g_Vectors.temp_v2

 |
temporary zero vector

 |

g_Vectors.temp_v3

 |
temporary zero vector

 |

g_Vectors.temp_v4

 |
temporary zero vector

 |

g_Vectors.vecMathTemp1

 |
temporary zero vector

 |

g_Vectors.vecMathTemp2

 |
temporary zero vector

 |

##
Constants

**
Constant Name
**

 |
**
Description
**

 |

g_Rad2Deg

 |
basic radian to degree conversion value

 |

g_Deg2Rad

 |
basic degree to radian conversion value

 |

g_Pi

 |
basic Pi constant based on
**
math.pi
**

 |

g_2Pi

 |
basic double Pi constant based on
**
math.pi
**

 |

g_Pi2

 |
basic half Pi constant based on
**
math.pi
**

 |

##
Vector Functions

-
[/docs/static/engines/cryengine-5/categories/23756813/pages/23306629#MathLua-IsNullVector](
#IsNullVector
)

-
[/docs/static/engines/cryengine-5/categories/23756813/pages/23306629#MathLua-IsNotNullVector](
#IsNotNullVector
)

-
[/docs/static/engines/cryengine-5/categories/23756813/pages/23306629#MathLua-LengthSqVector](
#LengthSqVector
)

-
[/docs/static/engines/cryengine-5/categories/23756813/pages/23306629#MathLua-LengthVector](
#LengthVector
)

-
[/docs/static/engines/cryengine-5/categories/23756813/pages/23306629#MathLua-DistanceSqVectors](
#DistanceSqVectors
)

-
[/docs/static/engines/cryengine-5/categories/23756813/pages/23306629#MathLua-DistanceSqVectors2d](
#DistanceSqVectors2d
)

-
[/docs/static/engines/cryengine-5/categories/23756813/pages/23306629#MathLua-DistanceVectors](
#DistanceVectors
)

-
[/docs/static/engines/cryengine-5/categories/23756813/pages/23306629#MathLua-dotproduct3d](
#dotproduct3d
)

-
[/docs/static/engines/cryengine-5/categories/23756813/pages/23306629#MathLua-dotproduct2d](
#dotproduct2d
)

-
[/docs/static/engines/cryengine-5/categories/23756813/pages/23306629#MathLua-LogVec](
#LogVec
)

-
[/docs/static/engines/cryengine-5/categories/23756813/pages/23306629#MathLua-ZeroVector](
#ZeroVector
)

-
[/docs/static/engines/cryengine-5/categories/23756813/pages/23306629#MathLua-CopyVector](
#CopyVector
)

-
[/docs/static/engines/cryengine-5/categories/23756813/pages/23306629#MathLua-SumVectors](
#SumVectors
)

-
[/docs/static/engines/cryengine-5/categories/23756813/pages/23306629#MathLua-NegVector](
#NegVector
)

-
[/docs/static/engines/cryengine-5/categories/23756813/pages/23306629#MathLua-SubVectors](
#SubVectors
)

-
[/docs/static/engines/cryengine-5/categories/23756813/pages/23306629#MathLua-FastSumVectors](
#FastSumVectors
)

-
[/docs/static/engines/cryengine-5/categories/23756813/pages/23306629#MathLua-DifferenceVectors](
#DifferenceVectors
)

-
[/docs/static/engines/cryengine-5/categories/23756813/pages/23306629#MathLua-FastDifferenceVectors](
#FastDifferenceVectors
)

-
[/docs/static/engines/cryengine-5/categories/23756813/pages/23306629#MathLua-ProductVectors](
#ProductVectors
)

-
[/docs/static/engines/cryengine-5/categories/23756813/pages/23306629#MathLua-FastProductVectors](
#FastProductVectors
)

-
[/docs/static/engines/cryengine-5/categories/23756813/pages/23306629#MathLua-ScaleVector](
#ScaleVector
)

-
[/docs/static/engines/cryengine-5/categories/23756813/pages/23306629#MathLua-ScaleVectorInPlace](
#ScaleVectorInPlace
)

-
[/docs/static/engines/cryengine-5/categories/23756813/pages/23306629#MathLua-NormalizeVector](
#NormalizeVector
)

-
[/docs/static/engines/cryengine-5/categories/23756813/pages/23306629#MathLua-FastScaleVector](
#FastScaleVector
)

-
[/docs/static/engines/cryengine-5/categories/23756813/pages/23306629#MathLua-VecRotate90_Z](
VecRotate90_Z
)

-
[/docs/static/engines/cryengine-5/categories/23756813/pages/23306629#MathLua-VecRotateMinus90_Z](
VecRotateMinus90_Z
)

-
[/docs/static/engines/cryengine-5/categories/23756813/pages/23306629#MathLua-crossproduct3d](
#crossproduct3d
)

-
[/docs/static/engines/cryengine-5/categories/23756813/pages/23306629#MathLua-RotateVectorAroundR](
#RotateVectorAroundR
)

-
[/docs/static/engines/cryengine-5/categories/23756813/pages/23306629#MathLua-ProjectVector](
#ProjectVector
)

##
Utility Functions

-
[/docs/static/engines/cryengine-5/categories/23756813/pages/23306629#MathLua-LerpColors](
#LerpColors
)

-
[/docs/static/engines/cryengine-5/categories/23756813/pages/23306629#MathLua-Lerp](
#Lerp
)

-
[/docs/static/engines/cryengine-5/categories/23756813/pages/23306629#MathLua-__max](
__max
)

-
[/docs/static/engines/cryengine-5/categories/23756813/pages/23306629#MathLua-__min](
__min
)

-
[/docs/static/engines/cryengine-5/categories/23756813/pages/23306629#MathLua-clamp](
#clamp
)

-
[/docs/static/engines/cryengine-5/categories/23756813/pages/23306629#MathLua-Interpolate](
#Interpolate
)

-
[/docs/static/engines/cryengine-5/categories/23756813/pages/23306629#MathLua-sgn](
#sgn
)

-
[/docs/static/engines/cryengine-5/categories/23756813/pages/23306629#MathLua-sgnnz](
#sgnnz
)

-
[/docs/static/engines/cryengine-5/categories/23756813/pages/23306629#MathLua-sqr](
#sqr
)

-
[/docs/static/engines/cryengine-5/categories/23756813/pages/23306629#MathLua-randomF](
#randomF
)

-
[/docs/static/engines/cryengine-5/categories/23756813/pages/23306629#MathLua-iff](
#iff
)

-
[/docs/static/engines/cryengine-5/categories/23756813/pages/23306629#MathLua-DistanceLineAndPoint](
#DistanceLineAndPoint
)

-
[/docs/static/engines/cryengine-5/categories/23756813/pages/23306629#MathLua-random](
#random
)

##
IsNullVector( a )

Returns
**
true
**
 if all vector components of the given vector
**
a
**
 are null.

**
Parameters
**

 |
**
Description
**

 |

a

 |
vector to check if it's components are null

 |

##
IsNullVector( a )

Returns
**
true
**
 if any vector components of the given vector
**
a
**
 is not null.

**
Parameters
**

 |
**
Description
**

 |

a

 |
vector to check if any of it's components are not null

 |

##
LengthSqVector( a )

Returns the squared length of the given vector
**
a
**
.

**
Parameters
**

 |
**
Description
**

 |

a

 |
vector to get the squared length from

 |

##
LengthVector( a )

Returns the length of the given vector
**
a
**
.

**
Parameters
**

 |
**
Description
**

 |

a

 |
vector to get the length from

 |

##
DistanceSqVectors( a, b )

Returns the squared distance between vector
**
a
**
 and vector
**
b
**
.

**
Parameters
**

 |
**
Description
**

 |

a

 |
vector a

 |

b

 |
vector b

 |

##
DistanceSqVectors2d( a, b )

Returns the squared distance between vector
**
a
**
 and vector
**
b
**
 in 2D space (without z-component).

**
Parameters
**

 |
**
Description
**

 |

a

 |
vector a

 |

b

 |
vector b

 |

##
DistanceVectors( a, b )

Returns the distance between vector
**
a
**
 and vector
**
b
**
.

**
Parameters
**

 |
**
Description
**

 |

a

 |
vector a

 |

b

 |
vector b

 |

##
dotproduct3d( a, b )

Returns the dot product between vector
**
a
**
 and vector
**
b
**
.

**
Parameters
**

 |
**
Description
**

 |

a

 |
vector a

 |

b

 |
vector b

 |

##
dotproduct2d( a, b )

Returns the dot product between vector
**
a
**
 and vector
**
b
**
 in 2D space (without z-component).

**
Parameters
**

 |
**
Description
**

 |

a

 |
vector a

 |

b

 |
vector b

 |

##
LogVec( name, v )

Logs a given vector to console.

**
Parameters
**

 |
**
Description
**

 |

name

 |
description name of the vector

 |

v

 |
vector v

 |

##
Example:

```

`
LogVec("Local Actor Position", g_localActor:GetPos())

Console output:
<Lua> Local Actor Position = (1104.018066 1983.247925 112.769440)
`

```

##
ZeroVector( dest )

Sets all vector components of the given vector
**
dest
**
 to zero.

**
Parameters
**

 |
**
Description
**

 |

dest

 |
vector dest

 |

##
CopyVector( dest, src )

Copies the components of the vector
**
src
**
 to the vector
**
dest
**
.

**
Parameters
**

 |
**
Description
**

 |

dest

 |
destination vector

 |

src

 |
source vector

 |

##
SumVectors( a, b)

Adds up the components of vector
**
a
**
 and vector
**
b
**
.

**
Parameters
**

 |
**
Description
**

 |

a

 |
vector a

 |

b

 |
vector b

 |

##
NegVector( a )

Negates all components of the given vector
**
a
**
.

**
Parameters
**

 |
**
Description
**

 |

a

 |
vector a

 |

##
SubVectors( dest, a, b )

Copies the componentwise subtraction of vector
**
b
**
 and vector
**
a
**
 to vector
**
dest
**
.

**
Parameters
**

 |
**
Description
**

 |

dest

 |
destination vector

 |

a

 |
vector a

 |

b

 |
vector b

 |

##
FastSumVectors( dest, a, b )

Copies the componentwise addition of vector
**
b
**
 and vector
**
a
**
 to vector
**
dest
**
.

**
Parameters
**

 |
**
Description
**

 |

dest

 |
destination vector

 |

a

 |
vector a

 |

b

 |
vector b

 |

##
DifferenceVectors( a, b )

Returns the difference between vector
**
a
**
 and vector
**
b
**
.

**
Parameters
**

 |
**
Description
**

 |

a

 |
vector a

 |

b

 |
vector b

 |

##
FastDifferenceVectors( dest, a, b )

Copies the componentwise difference between vector
**
a
**
 and vector
**
b
**
 to vector
**
dest
**
.

**
Parameters
**

 |
**
Description
**

 |

dest

 |
destination vector

 |

a

 |
vector a

 |

b

 |
vector b

 |

##
ProductVectors( a, b )

Returns the product of vector
**
a
**
 and vector
**
b
**
.

**
Parameters
**

 |
**
Description
**

 |

a

 |
vector a

 |

b

 |
vector b

 |

##
FastProductVectors( dest, a, b )

Copies the product of vector
**
a
**
 and vector
**
b
**
 to vector
**
dest
**
.

**
Parameters
**

 |
**
Description
**

 |

dest

 |
destination vector

 |

a

 |
vector a

 |

b

 |
vector b

 |

##
ScaleVector( a, b )

Scales the given vector
**
a
**
 by the factor of
**
b
**
.

**
Parameters
**

 |
**
Description
**

 |

a

 |
vector a

 |

b

 |
scalar b

 |

##
ScaleVectorInPlace( a, b )

Returns a new vector based on a copy of the scaled vector
**
a
**
 by the factor
**
b
**
.

**
Parameters
**

 |
**
Description
**

 |

a

 |
vector a

 |

b

 |
scalar b

 |

##
ScaleVectorInPlace( dest, a, b )

Copies the scaled vector
**
a
**
 by the factor of
**
b
**
 to vector
**
dest
**
.

**
Parameters
**

 |
**
Description
**

 |

dest

 |
destination vector

 |

a

 |
vector a

 |

b

 |
scalar b

 |

##
NormalizeVector( a )

Returns the normalized vector
**
a
**
.

**
Parameters
**

 |
**
Description
**

 |

a

 |
vector a

 |

##
VecRotate90_Z( v )

Rotates vector
**
v
**
 by 90 degree around the z-axis.

**
Parameters
**

 |
**
Description
**

 |

v

 |
vector v

 |

##
VecRotateMinus90_Z( v )

Rotates vector
**
v
**
 by -90 degree around the z-axis.

**
Parameters
**

 |
**
Description
**

 |

v

 |
vector v

 |

##
crossproduct3d( dest, p, q )

Copies the result of the cross product between vector
**
p
**
 and vector
**
q
**
 to vector
**
dest
**
.

**
Parameters
**

 |
**
Description
**

 |

dest

 |
destination vector

 |

p

 |
vector p

 |

q

 |
vector q

 |

##
RotateVectorAroundR( dest, p, r, angle )

Copies the result of the vector rotation of vector
**
p
**
 around vector
**
r
**
 by the given
**
angle
**
 to vector
**
dest
**
.

**
Parameters
**

 |
**
Description
**

 |

dest

 |
destination vector

 |

p

 |
vector p

 |

r

 |
vector r

 |

angle

 |
rotation angle

 |

##
ProjectVector( dest, P, N )

Copies the result of the vector projection of vector
**
P
**
 to the surface with the given normal
**
N
**
 to vector
**
dest
**
.

**
Parameters
**

 |
**
Description
**

 |

dest

 |
destination vector

 |

P

 |
vector pP

 |

N

 |
surface normal

 |

##
DistanceLineAndPoint( a, p, q )

Returns the distance between the point
**
a
**
 and the line between
**
p
**
 and
**
q
**
.

**
Parameters
**

 |
**
Description
**

 |

a

 |
vector a

 |

p

 |
vector p

 |

q

 |
vector q

 |

##
LerpColors( a, b, k )

Linear interpolation between color/vector
**
a
**
 and color/vector
**
b
**
 with the factor of
**
k
**
.

**
Parameters
**

 |
**
Description
**

 |

a

 |
color/vector a

 |

b

 |
color/vector b

 |

k

 |
factor k

 |

##
Lerp( a, b, k )

Linear interpolation between scalar
**
a
**
 and scalar
**
b
**
 with the factor of
**
k
**
.

**
Parameters
**

 |
**
Description
**

 |

a

 |
scalar a

 |

b

 |
scalar b

 |

k

 |
factor k

 |

##
__max( a, b )

Returns the maximum of
**
a
**
 and
**
b
**
.

**
Parameters
**

 |
**
Description
**

 |

a

 |
scalar a

 |

b

 |
scalar b

 |

##
__min( a, b )

Returns the minimum of
**
a
**
 and
**
b
**
.

**
Parameters
**

 |
**
Description
**

 |

a

 |
scalar a

 |

b

 |
scalar b

 |

##
clamp( _n, _min, _max )

Clamps the number
**
_n
**
 between
**
_min
**
 and
**
_max
**
.

**
Parameters
**

 |
**
Description
**

 |

_n

 |
number to clamp

 |

_min

 |
lower limit to clamp

 |

_max

 |
upper limit to clamp

 |

##
Interpolate( actual, goal, speed )

Interpolates the given number
**
actual
**
 to the given
**
goal
**
 by the given
**
speed
**
.

**
Parameters
**

 |
**
Description
**

 |

actual

 |
number actual

 |

goal

 |
number goal

 |

speed

 |
interpolation speed

 |

##
sgn( a )

Returns the sign of a given number (0 returns 0).

**
Parameters
**

 |
**
Description
**

 |

a

 |
number a

 |

##
sgnnz( a )

Returns the sign of a given number (0 returns 1).

**
Parameters
**

 |
**
Description
**

 |

a

 |
number a

 |

##
sqr( a )

Returns the square of a given number.

**
Parameters
**

 |
**
Description
**

 |

a

 |
number a

 |

##
randomF( a, b )

Returns a random float between
**
a
**
 and
**
b
**
.

**
Parameters
**

 |
**
Description
**

 |

a

 |
number a

 |

b

 |
number b

 |

##
iff( c, a, b )

Returns
**
a
**
 if
**
c
**
 is not
**
nil
**
, otherwise it returns
**
b
**
.

**
Parameters
**

 |
**
Description
**

 |

c

 |
condition value c

 |

a

 |
value a

 |

b

 |
value b

 |
