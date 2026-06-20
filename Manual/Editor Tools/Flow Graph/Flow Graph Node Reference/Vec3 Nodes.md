# Vec3 Nodes

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/29450642
- Page ID: 29450642
- Breadcrumb: Editor Tools > Flow Graph > Flow Graph Node Reference > Vec3 Nodes
- Parent: Flow Graph Node Reference

## Content

##
AddVec3

Used to output the sum of two vectors.

[Image: /docs/static/attachments/29688072]

**
Inputs
**

Port
 |
Type
 |
Description
 |

**
A
**
 |
Vec3
 |
First operand
 |

**
B
**
 |
Vec3
 |
Second operand
 |

**
Outputs
**

Port
 |
Type
 |
Description
 |

**
Out
**
 |
Vec3
 |
Addition of A and B
 |

##
Calculate

Used to output the specified calculation between two vectors.

[Image: /docs/static/attachments/29688071]

**
Inputs
**

Port
 |
Type
 |
Description
 |

**
Operator
**
 |
Integer
 |
Math operation to perform
 |

**
A
**
 |
Vec3
 |
First operand
 |

**
B
**
 |
Vec3
 |
Second operand
 |

**
Outputs
**

Port
 |
Type
 |
Description
 |

**
Out
**
 |
Vec3
 |
Calculated operation of A and B
 |

##
ClampVec3

Used to clamp the output range of a vector between a minimum and a maximum.

[Image: /docs/static/attachments/29688070]

**
Inputs
**

Port
 |
Type
 |
Description
 |

**
In
**
 |
Vec3
 |
Input value
 |

**
Min
**
 |
Vec3
 |
Minimum clamping value
 |

**
Max
**
 |
Vec3
 |
Maximum clamping value
 |

**
Outputs
**

Port
 |
Type
 |
Description
 |

**
Out
**
 |
Vec3
 |
Triggers when the input value is between the minimum and maximum values
 |

##
CrossVec3

Used to output the cross product of two vectors.

[Image: /docs/static/attachments/29688069]

**
Inputs
**

Port
 |
Type
 |
Description
 |

**
A
**
 |
Vec3
 |
First operand
 |

**
B
**
 |
Vec3
 |
Second operand
 |

**
Outputs
**

Port
 |
Type
 |
Description
 |

**
Out
**
 |
Vec3
 |
Outputs the cross product of the inputs
 |

##
DotVec3

Used to output the dot product of the inputs.

[Image: /docs/static/attachments/29688068]

**
Inputs
**

Port
 |
Type
 |
Description
 |

**
A
**
 |
Vec3
 |
First operand
 |

**
B
**
 |
Vec3
 |
Second operand
 |

**
Outputs
**

Port
 |
Type
 |
Description
 |

**
Out
**
 |
Float
 |
Outputs the dot product of the inputs
 |

##
EqualVec3

Used to trigger an output when both vectors are equal in value.

[Image: /docs/static/attachments/29688067]

**
Inputs
**

Port
 |
Type
 |
Description
 |

**
A
**
 |
Vec3
 |
First operand
 |

**
B
**
 |
Vec3
 |
Second operand
 |

**
Outputs
**

Port
 |
Type
 |
Description
 |

**
Out
**
 |
Boolean
 |
Triggers when A and B are equal in value
 |

##
FromVec3

Used to output the x, y, and z values of the vector.

[Image: /docs/static/attachments/29688066]

**
Inputs
**

Port
 |
Type
 |
Description
 |

**
Vec3
**
 |
Vec3
 |
Input vector
 |

**
Outputs
**

Port
 |
Type
 |
Description
 |

**
X
**
 |
Float
 |
X-axis value of vector
 |

**
Y
**
 |
Float
 |
Y-axis value of vector
 |

**
Z
**
 |
Float
 |
Z-axis value of vector
 |

##
MagnitudeVec3

Used to output the magnitude (length) of the vector.

[Image: /docs/static/attachments/29688065]

**
Inputs
**

Port
 |
Type
 |
Description
 |

**
Vector
**
 |
Vec3
 |
Input vector
 |

**
Outputs
**

Port
 |
Type
 |
Description
 |

**
Length
**
 |
Any
 |
Magnitude (length) of the input vector
 |

##
MulVec3

Used to output the multiplication of two vectors.

[Image: /docs/static/attachments/29688064]

**
Inputs
**

Port
 |
Type
 |
Description
 |

**
A
**
 |
Vec3
 |
First operand
 |

**
B
**
 |
Vec3
 |
Second operand
 |

**
Outputs
**

Port
 |
Type
 |
Description
 |

**
Out
**
 |
Vec3
 |
Multiplication of A and B
 |

##
NormalizeVec3

Used to output the normalized value of the vector.

[Image: /docs/static/attachments/29688063]

**
Inputs
**

Port
 |
Type
 |
Description
 |

**
Vector
**
 |
Vec3
 |
Vector input
 |

**
Outputs
**

Port
 |
Type
 |
Description
 |

**
Out
**
 |
Vec3
 |
Normalized vector input
 |

**
Length
**
 |
Float
 |
Magnitude
 |

##
ReciprocalVec3

Used to output the reciprocal of the vector.

[Image: /docs/static/attachments/29688062]

**
Inputs
**

Port
 |
Type
 |
Description
 |

**
Vector
**
 |
Vec3
 |
Input vector
 |

**
Outputs
**

Port
 |
Type
 |
Description
 |

**
Length
**
 |
Float
 |
Reciprocal value of input
 |

##
Scalevec3

Used to output a scaled value of the vector.

[Image: /docs/static/attachments/29688061]

**
Inputs
**

Port
 |
Type
 |
Description
 |

**
Vector
**
 |
Vec3
 |
Input vector
 |

**
Scale
**
 |
Float
 |
Scale factor to apply to the input
 |

**
Outputs
**

Port
 |
Type
 |
Description
 |

**
Out
**
 |
Vec3
 |
Result of the scaling
 |

##
SetVec3

Used to output the input value when the Set input is activated.

[Image: /docs/static/attachments/29688060]

**
Inputs
**

Port
 |
Type
 |
Description
 |

**
Set
**
 |
Any
 |
Triggers the vector to the output
 |

**
In
**
 |
Vec3
 |
Input value
 |

**
Outputs
**

Port
 |
Type
 |
Description
 |

**
Out
**
 |
Vec3
 |
Outputs the input value
 |

##
SubVec3

Used to output the subtracted value of two vectors.

[Image: /docs/static/attachments/29688059]

**
Inputs
**

Port
 |
Type
 |
Description
 |

**
A
**
 |
Vec3
 |
First operand
 |

**
B
**
 |
Vec3
 |
Second operand
 |

**
Outputs
**

Port
 |
Type
 |
Description
 |

**
Out
**
 |
Vec3
 |
Subtraction of B from A
 |

##
ToVec3

Used to output three floating point values to a vector.

[Image: /docs/static/attachments/29688058]

**
Inputs
**

Port
 |
Type
 |
Description
 |

**
X
**
 |
Float
 |
X-axis value
 |

**
Y
**
 |
Float
 |
Y-axis value
 |

**
Z
**
 |
Float
 |
Z-axis value
 |

**
Outputs
**

Port
 |
Description
 |

**
Vec3
**
 |
Vector output
 |

[#addvec3](
AddVec3
)
[#calculate](
Calculate
)
[#clampvec3](
ClampVec3
)
[#crossvec3](
CrossVec3
)
[#dotvec3](
DotVec3
)
[#equalvec3](
EqualVec3
)
[#fromvec3](
FromVec3
)
[#magnitudevec3](
MagnitudeVec3
)
[#mulvec3](
MulVec3
)
[#normalizevec3](
NormalizeVec3
)
[#reciprocalvec3](
ReciprocalVec3
)
[#scalevec3](
Scalevec3
)
[#setvec3](
SetVec3
)
[#subvec3](
SubVec3
)
[#tovec3](
ToVec3
)
