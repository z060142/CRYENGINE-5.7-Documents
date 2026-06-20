# Math Lua

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/23306629
- Page ID: 23306629
- Breadcrumb: CRYENGINE Engine Code > Engine Modules > CryScriptSystem > Lua Scripting > Common Lua Functions > Math Lua
- Parent: Common Lua Functions

## Content

### Math utility functions, constants and global vector definitions

Defines commonly used math utility functions, constants and global vectors.

- File location: `Game/Scripts/Utils/Math.lua`
- Loaded from: `Game/Scripts/common.lua`

### Global Vectors

The following globals should be used to avoid temporary Lua memory allocations:

**Global Name** | **Description**
--- | ---
g_Vectors.v000 | basic zero vector
g_Vectors.v001 | positive z-axis direction vector
g_Vectors.v010 | positive y-axis direction vector
g_Vectors.v100 | positive x-axis direction vector
g_Vectors.v101 | x and z-axis direction vector
g_Vectors.v110 | x and y-axis direction vector
g_Vectors.v111 | x, y and z-axis vector
g_Vectors.up | positive z-axis direction vector
g_Vectors.down | negative z-axis direction vector
g_Vectors.temp | temporary zero vector
g_Vectors.tempColor | temporary zero vector, commonly used for passing rgb color values
g_Vectors.temp_v1 | temporary zero vector
g_Vectors.temp_v2 | temporary zero vector
g_Vectors.temp_v3 | temporary zero vector
g_Vectors.temp_v4 | temporary zero vector
g_Vectors.vecMathTemp1 | temporary zero vector
g_Vectors.vecMathTemp2 | temporary zero vector

### Constants

**Constant Name** | **Description**
--- | ---
g_Rad2Deg | basic radian to degree conversion value
g_Deg2Rad | basic degree to radian conversion value
g_Pi | basic Pi constant based on **math.pi**
g_2Pi | basic double Pi constant based on **math.pi**
g_Pi2 | basic half Pi constant based on **math.pi**

### Vector Functions

- [#IsNullVector](Math%20Lua.md#MathLua-IsNullVector)
- [#IsNotNullVector](Math%20Lua.md#MathLua-IsNotNullVector)
- [#LengthSqVector](Math%20Lua.md#MathLua-LengthSqVector)
- [#LengthVector](Math%20Lua.md#MathLua-LengthVector)
- [#DistanceSqVectors](Math%20Lua.md#MathLua-DistanceSqVectors)
- [#DistanceSqVectors2d](Math%20Lua.md#MathLua-DistanceSqVectors2d)
- [#DistanceVectors](Math%20Lua.md#MathLua-DistanceVectors)
- [#dotproduct3d](Math%20Lua.md#MathLua-dotproduct3d)
- [#dotproduct2d](Math%20Lua.md#MathLua-dotproduct2d)
- [#LogVec](Math%20Lua.md#MathLua-LogVec)
- [#ZeroVector](Math%20Lua.md#MathLua-ZeroVector)
- [#CopyVector](Math%20Lua.md#MathLua-CopyVector)
- [#SumVectors](Math%20Lua.md#MathLua-SumVectors)
- [#NegVector](Math%20Lua.md#MathLua-NegVector)
- [#SubVectors](Math%20Lua.md#MathLua-SubVectors)
- [#FastSumVectors](Math%20Lua.md#MathLua-FastSumVectors)
- [#DifferenceVectors](Math%20Lua.md#MathLua-DifferenceVectors)
- [#FastDifferenceVectors](Math%20Lua.md#MathLua-FastDifferenceVectors)
- [#ProductVectors](Math%20Lua.md#MathLua-ProductVectors)
- [#FastProductVectors](Math%20Lua.md#MathLua-FastProductVectors)
- [#ScaleVector](Math%20Lua.md#MathLua-ScaleVector)
- [#ScaleVectorInPlace](Math%20Lua.md#MathLua-ScaleVectorInPlace)
- [#NormalizeVector](Math%20Lua.md#MathLua-NormalizeVector)
- [#FastScaleVector](Math%20Lua.md#MathLua-FastScaleVector)
- [VecRotate90_Z](Math%20Lua.md#MathLua-VecRotate90_Z)
- [VecRotateMinus90_Z](Math%20Lua.md#MathLua-VecRotateMinus90_Z)
- [#crossproduct3d](Math%20Lua.md#MathLua-crossproduct3d)
- [#RotateVectorAroundR](Math%20Lua.md#MathLua-RotateVectorAroundR)
- [#ProjectVector](Math%20Lua.md#MathLua-ProjectVector)

### Utility Functions

- [#LerpColors](Math%20Lua.md#MathLua-LerpColors)
- [#Lerp](Math%20Lua.md#MathLua-Lerp)
- [__max](Math%20Lua.md#MathLua-__max)
- [__min](Math%20Lua.md#MathLua-__min)
- [#clamp](Math%20Lua.md#MathLua-clamp)
- [#Interpolate](Math%20Lua.md#MathLua-Interpolate)
- [#sgn](Math%20Lua.md#MathLua-sgn)
- [#sgnnz](Math%20Lua.md#MathLua-sgnnz)
- [#sqr](Math%20Lua.md#MathLua-sqr)
- [#randomF](Math%20Lua.md#MathLua-randomF)
- [#iff](Math%20Lua.md#MathLua-iff)
- [#DistanceLineAndPoint](Math%20Lua.md#MathLua-DistanceLineAndPoint)
- [#random](Math%20Lua.md#MathLua-random)

#### IsNullVector(a)

Returns **true** if all vector components of the given vector ** a** are null.

**Parameters** | **Description**
--- | ---
a | vector to check if it's components are null

#### IsNullVector(a)

Returns **true** if any vector components of the given vector ** a** is not null.

**Parameters** | **Description**
--- | ---
a | vector to check if any of it's components are not null

#### LengthSqVector(a)

Returns the squared length of the given vector **a**.

**Parameters** | **Description**
--- | ---
a | vector to get the squared length from

#### LengthVector(a)

Returns the length of the given vector **a**.

**Parameters** | **Description**
--- | ---
a | vector to get the length from

#### DistanceSqVectors(a, b)

Returns the squared distance between vector **a** and vector ** b**.

**Parameters** | **Description**
--- | ---
a | vector a
b | vector b

#### DistanceSqVectors2d(a, b)

Returns the squared distance between vector **a** and vector ** b** in 2D space (without z-component).

**Parameters** | **Description**
--- | ---
a | vector a
b | vector b

#### DistanceVectors(a, b)

Returns the distance between vector **a** and vector ** b**.

**Parameters** | **Description**
--- | ---
a | vector a
b | vector b

#### dotproduct3d(a, b)

Returns the dot product between vector **a** and vector ** b**.

**Parameters** | **Description**
--- | ---
a | vector a
b | vector b

#### dotproduct2d(a, b)

Returns the dot product between vector **a** and vector ** b** in 2D space (without z-component).

**Parameters** | **Description**
--- | ---
a | vector a
b | vector b

#### LogVec(name, v)

Logs a given vector to console.

**Parameters** | **Description**
--- | ---
name | description name of the vector
v | vector v

##### Example:

```
LogVec("Local Actor Position", g_localActor:GetPos())

Console output:
<Lua> Local Actor Position = (1104.018066 1983.247925 112.769440)
```

#### ZeroVector(dest)

Sets all vector components of the given vector **dest** to zero.

**Parameters** | **Description**
--- | ---
dest | vector dest

#### CopyVector(dest, src)

Copies the components of the vector **src** to the vector ** dest**.

**Parameters** | **Description**
--- | ---
dest | destination vector
src | source vector

#### SumVectors(a, b)

Adds up the components of vector **a** and vector ** b**.

**Parameters** | **Description**
--- | ---
a | vector a
b | vector b

#### NegVector(a)

Negates all components of the given vector **a**.

**Parameters** | **Description**
--- | ---
a | vector a

#### SubVectors(dest, a, b)

Copies the componentwise subtraction of vector **b** and vector ** a** to vector ** dest**.

**Parameters** | **Description**
--- | ---
dest | destination vector
a | vector a
b | vector b

#### FastSumVectors(dest, a, b)

Copies the componentwise addition of vector **b** and vector ** a** to vector ** dest**.

**Parameters** | **Description**
--- | ---
dest | destination vector
a | vector a
b | vector b

#### DifferenceVectors(a, b)

Returns the difference between vector **a** and vector ** b**.

**Parameters** | **Description**
--- | ---
a | vector a
b | vector b

#### FastDifferenceVectors(dest, a, b)

Copies the componentwise difference between vector **a** and vector ** b** to vector ** dest**.

**Parameters** | **Description**
--- | ---
dest | destination vector
a | vector a
b | vector b

#### ProductVectors(a, b)

Returns the product of vector **a** and vector ** b**.

**Parameters** | **Description**
--- | ---
a | vector a
b | vector b

#### FastProductVectors(dest, a, b)

Copies the product of vector **a** and vector ** b** to vector ** dest**.

**Parameters** | **Description**
--- | ---
dest | destination vector
a | vector a
b | vector b

#### ScaleVector(a, b)

Scales the given vector **a** by the factor of ** b**.

**Parameters** | **Description**
--- | ---
a | vector a
b | scalar b

#### ScaleVectorInPlace(a, b)

Returns a new vector based on a copy of the scaled vector **a** by the factor ** b**.

**Parameters** | **Description**
--- | ---
a | vector a
b | scalar b

#### ScaleVectorInPlace(dest, a, b)

Copies the scaled vector **a** by the factor of ** b** to vector ** dest**.

**Parameters** | **Description**
--- | ---
dest | destination vector
a | vector a
b | scalar b

#### NormalizeVector(a)

Returns the normalized vector **a**.

**Parameters** | **Description**
--- | ---
a | vector a

#### VecRotate90_Z(v)

Rotates vector **v** by 90 degree around the z-axis.

**Parameters** | **Description**
--- | ---
v | vector v

#### VecRotateMinus90_Z(v)

Rotates vector **v** by -90 degree around the z-axis.

**Parameters** | **Description**
--- | ---
v | vector v

#### crossproduct3d(dest, p, q)

Copies the result of the cross product between vector **p** and vector ** q** to vector ** dest**.

**Parameters** | **Description**
--- | ---
dest | destination vector
p | vector p
q | vector q

#### RotateVectorAroundR(dest, p, r, angle)

Copies the result of the vector rotation of vector **p** around vector ** r** by the given ** angle** to vector ** dest**.

**Parameters** | **Description**
--- | ---
dest | destination vector
p | vector p
r | vector r
angle | rotation angle

#### ProjectVector(dest, P, N)

Copies the result of the vector projection of vector **P** to the surface with the given normal ** N** to vector ** dest**.

**Parameters** | **Description**
--- | ---
dest | destination vector
P | vector pP
N | surface normal

#### DistanceLineAndPoint(a, p, q)

Returns the distance between the point **a** and the line between ** p** and ** q**.

**Parameters** | **Description**
--- | ---
a | vector a
p | vector p
q | vector q

#### LerpColors(a, b, k)

Linear interpolation between color/vector **a** and color/vector ** b** with the factor of ** k**.

**Parameters** | **Description**
--- | ---
a | color/vector a
b | color/vector b
k | factor k

#### Lerp(a, b, k)

Linear interpolation between scalar **a** and scalar ** b** with the factor of ** k**.

**Parameters** | **Description**
--- | ---
a | scalar a
b | scalar b
k | factor k

#### __max(a, b)

Returns the maximum of **a** and ** b**.

**Parameters** | **Description**
--- | ---
a | scalar a
b | scalar b

#### __min(a, b)

Returns the minimum of **a** and ** b**.

**Parameters** | **Description**
--- | ---
a | scalar a
b | scalar b

#### clamp(_n, _min, _max)

Clamps the number **_n** between **_min** and **_max**.

**Parameters** | **Description**
--- | ---
_n | number to clamp
_min | lower limit to clamp
_max | upper limit to clamp

#### Interpolate(actual, goal, speed)

Interpolates the given number **actual** to the given ** goal** by the given ** speed**.

**Parameters** | **Description**
--- | ---
actual | number actual
goal | number goal
speed | interpolation speed

#### sgn(a)

Returns the sign of a given number (0 returns 0).

**Parameters** | **Description**
--- | ---
a | number a

#### sgnnz(a)

Returns the sign of a given number (0 returns 1).

**Parameters** | **Description**
--- | ---
a | number a

#### sqr(a)

Returns the square of a given number.

**Parameters** | **Description**
--- | ---
a | number a

#### randomF(a, b)

Returns a random float between **a** and ** b**.

**Parameters** | **Description**
--- | ---
a | number a
b | number b

#### iff(c, a, b)

Returns **a** if ** c** is not ** nil**, otherwise it returns ** b**.

**Parameters** | **Description**
--- | ---
c | condition value c
a | value a
b | value b
