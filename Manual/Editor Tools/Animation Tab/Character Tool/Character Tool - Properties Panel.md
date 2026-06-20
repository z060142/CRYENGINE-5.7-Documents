# Character Tool - Properties Panel

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/35849282
- Page ID: 35849282
- Breadcrumb: Editor Tools > Animation Tab > Character Tool > Character Tool - Properties Panel
- Parent: Character Tool

## Content

##
Overview

The Properties panel lets you modify character definition scripts and adjust certain supplemental parameters of various assets involved in character authoring. These supplemental properties are usually stored in separate scripts next to the actual asset file.

Below you can find parameter descriptions for all available asset types:

##
Properties Panel Header

The header of the properties panel is always the same, independent of the currently edited asset type.

*
[Image: /docs/static/attachments/35960129]

*

Button / Option
 |
Description
 |

[Image: /docs/static/attachments/35960149]
 |
Navigate back to the previously selected asset.

 |

[Image: /docs/static/attachments/35960148]
 |
Navigate forward to the next selected asset.

 |

[Image: /docs/static/attachments/35960147]
 |
Name of the currently edited asset. The asterisk next to the file name signals that some properties have been changed and differ from what is currently stored in the disk file.

 |

[Image: /docs/static/attachments/35960146]
 |

-
**
Follow selection -
**
 Make this property panel follow the Asset panel selection at all times.

-
**
Lock -
**

Lock this property panel to the currently edited asset, ignoring Asset panel selection changes.
**

**
 |

[Image: /docs/static/attachments/35960145]
 |
Change display mode for character attachments list.

-
**
Single Tree -
**
Display all attachment properties in a single tree
 structure.
**

**

-
**
Outline: Top
**
 -
**

**
Split the panel horizontally and display properties of the currently highlighted attachment in the bottom part.

-
**
Outline: Left
**
 -
**
**
 Split the panel vertically and display properties of the currently highlighted attachment in the right part.
 |

[Image: /docs/static/attachments/35960144]
 |
Undo the last property modification.

 |

[Image: /docs/static/attachments/35960143]
 |
Redo the previously undone property modification.

 |

[Image: /docs/static/attachments/35960142]
 |
Revert all changes and go back to the last saved state.

 |

[Image: /docs/static/attachments/35960141]
 |
Save all property changes.

 |

[Image: /docs/static/attachments/35960140]
 |
Show the location of the currently edited asset file in the Windows Explorer.

 |

##
Character Properties

These properties are only displayed when editing a character definition.

Option
 |
Description
 |

**
Skeleton
**
 |
Skeleton asset to be used by the character.

 |

**
Skeleton Material
**
 |
Material to be used for geometry stored in the skeleton file. Although this workflow is still supported, character geometry should generally be stored in separate skin assets and bound to a character using skin attachments.

 |

##
Attachments

List of character attachments. The button next to
**
Attachments
**
 lets you add a new attachment to your character. There are 6 types of attachments available, each with its own specific properties:

##
Joint Attachment

Joint attachments let you define sockets bound with the skeletal hierarchy of the character to which various objects can be connected.

Option
 |
Description
 |

**
Name
**
 |
Name of the attachment.

 |

**
Type
**
 |
Attachment type (Joint Attachment).

 |

**
Joint
**
 |
A skeleton joint the attachment is connected to.

 |

**
Geometry
**
 |
An object to be connected to this attachment socket. Can be a *.cgf,
*.
cga,
*.
chr or another
*.
cdf asset. Can be changed at
runtime.

 |

**
Material
**
 |
Material to be used when rendering the attached object. Can be changed at runtime.
**

**

 |

**
View Distance Multiplier
**
 |
An additional parameter for fine-tuning LoD selection of the connected object's geometry.

 |

**
Store Position
**
 |
Specifies how the attachment will be positioned.

-
**
Relative to Character -
**
 Attachment position will always be relative to the character's position
**
.

**

-
**
Relative to Joint -

**

Attachment position will always be relative to the selected joint's position
**
.
**
 |

**
Store Rotation
**
 |
Specifies how the attachment
will
be oriented.

-
**
Relative to Character -
**
 Attachment orientation will always be relative to the character's orientation
**
.

**

-
**
Relative to Joint -

**

Attachment orientation will always be relative to the selected joint's orientation
**
.
**
 |

**
*
Transform
*
**

Option
 |
Description
 |

**
T
**
 |
Positional offset of the attachment, relative to its
**
Store Position
**
.

 |

**
R
**
 |
Rotational offset of the attachment, expressed in degrees, relative to its
**
Store Rotation
**
.

 |

**
Simulation
**
 |
Enable sim
plified physical simulation for generating attachment motion in response to the character's movement.
T
he simulation is efficient but will not interact with objects surrounding the character in game.

 |

**
Hidden
**
 |
Make this attachment hidden by default when spawning a new character in game. This prevents the attached object from being rendered.

 |

**
Physicalized Rays
**
 |
Make this attachment take part in ray casting intersection tests.

 |

**
Physicalized Collisions
**
 |
Make this attachment take part in physical collision tests.

 |

*
**
Rope/Cloth Physics
**
*

Enable full physical simulation for this attachment. This is less efficient than the algorithm used by the
**
Simulation
**
 property, but will respect collisions with objects surrounding the character in game.
*
**

**
*

Option
 |
Description
 |

**
Type
**
 |

-
**
None -
**
 Disable physics
**
.

**

-
**
Rope -
**
Use algorithm specialized for rope-like objects.
**

**

-
**
Cloth
**

**
-
**
Use algorithm specialized for cloth-like objects.
**

**
 |

##
Face Attachment

Face Attachments provide the same functionalities as
**
Joint Attachments
**
, but are bound to character's geometry (a mesh face) rather than its skeletal hierarchy.

Option
 |
Description
 |

**
Name
**
 |
Name of the attachment.

 |

**
Type
**
 |
Attachment type (Face Attachment).

 |

**
Geometry
**
 |
An object to be connected to this attachment socket. Can be a *.cgf,
*.
cga,
*.
chr or another
*.
cdf asset. Can be changed at
runtime.

 |

**
Material
**
 |
Material to be used when rendering the attached object. Can be changed at runtime.
**

**

 |

**
View Distance Multiplier
**
 |
An additional parameter for fine-tuning LoD selection of the connected object's geometry.

 |

*
**
Transform
**
*

Option
 |
Description
 |

**
T
**
 |
Positional offset of the attachment.

 |

**
R
**
 |
Rotational offset of the attachment, expressed in degrees.

 |

**
Simulation
**
 |
Enable sim
plified physical simulation for generating attachment motion in response to the character's movement.
T
he simulation is efficient but will not interact with objects surrounding the character in game.

 |

**
Hidden
**
 |
Make this attachment hidden by default when spawning a new character in game. This prevents the attached object from being rendered.

 |

**
Physicalized Rays
**
 |
Make this attachment take part in ray casting intersection tests.

 |

**
Physicalized Collisions
**
 |
Make this attachment take part in physical collision tests.

 |

##
Skin Attachment

Skin attachments let you connect a skinned mesh directly to its corresponding bones of the character's skeletal hierarchy.

Option
 |
Description
 |

**
Name
**
 |
Name of the attachment.

 |

**
Type
**
 |
Attachment type (Skin Attachment).

 |

**
Geometry
**
 |
A *.skin file containing the skinned mesh.

 |

**
Material
**
 |
Material to be used when rendering the skin geometry.

 |

**
View Distance Multiplier
**
 |
An additional parameter for fine-tuning LoD selection of the skin geometry.

 |

**
Skinning Method
**
 |
Skinning algorithm to be used for geometry deformation:

-
**
Vertex Shader (4 weights)

**
The mesh is skinned using a vertex shader algorithm. The number of bone weighs for each vertex is limited to 4 when using this method. Does not support blend shape (morph targets) deformations. This is the default algorithm, offering the best performance but also the lowest fidelity.

-
**
CPU (slow) (8 weights, morphs, normals)
**

**
**
The mesh is skinned using a CPU algorithm. This method was introduced to overcome limitations of the vertex shader algorithm. It supports up to eight bone weights per vertex, blend shape (morph target) deformations and tangent frame recalculation. This method offers the lowest performance, so it should be used with care
.

-
**
Compute Shader (8 weights, morphs, normals)
**

**
**
The mesh is skinned using a compute shader algorithm. This method offers the same feature set as the CPU algorithm (up to 8 bone weights per vertex, blend shapes, tangent frame recalculation), with increased fidelity and significantly better performance.
 |

**
Hidden
**
 |
Make this attachment hidden by default when spawning a new character in game. This prevents the attached geometry from being skinned and rendered.

 |

##
Proxy Attachment

Proxy attachments let you define physical proxies and connect them to the skeletal hierarchy of the character. Physical proxies interact with other types of attachments and are used for fine-tuning the behavior of
**
VCloth
**
 attachment and any
**

**
attachments that make use of the
**
Simulation
**
 property.

Option
 |
Description
 |

**
Name
**
 |
Name of the attachment.

 |

**
Type
**
 |
Attachment type (Proxy Attachment).

 |

**
Joint
**
 |
A skeleton joint the attachment is connected to.

 |

**
Store Position
**
 |
Specifies how the attachment is going to be positioned.

-
**
Relative to Character -
**
 Attachment position will always be relative to the character's position
**
.

**

-
**
Relative to Joint -

**

Attachment position will always be relative to the selected joint's position
**
.
**
 |

**
Store Rotation
**
 |
Specifies how the attachment is going to be oriented.

-
**
Relative to Character -
**
 Attachment orientation will always be relative to the character's
orientation.
**

**

-
**
Relative to Joint -

**

Attachment orientation will always be relative to the selected joint's orientation.
 |

*
**
Transform
**
*

Option
 |
Description
 |

**
T
**
 |
Positional offset of the attachment, relative to its
**
Store Position.
**

 |

**
R
**
 |
Rotational offset of the attachment, expressed in degrees, relative to its
**
Store Rotation
**
.

 |

**
Purpose
**
 |
Specifies what should the proxy interact with.

-
**
Auxiliary -
**
 Proxy will affect all attachments with the
**
Simulation
**
 property enabled.
**

**

-
**
Cloth
**
 -
**
**
Proxy will affect
**
VCloth
**
 attachments.
**
**

**
**

-
**
Main Physics -
**
Enables extra proxy options:

-
**
Min Angle -
**
Minimum angle of the proxy attachment.

-
**
Max Angle -
**
Maximum angle of the proxy attachment.

-
**
Rotation0 -
**
Rotation of the proxy attachment.

-
**
Spring Tension -
**
Spring Tension of the proxy attachment (directly ported from the DCC tool joint properties).

-
**
Spring Damping -
**
Spring Damping of the proxy attachment (directly ported from the DCC tool joint properties)
 |

*
**

**
*

*
**
Lozenge
**
*

Option
 |
Description
 |

**
Border Width
**
 |
Width of the proxy border.

 |

**
Size X
**
 |
Length of the proxy along its X axis.

 |

**
Size Y
**
 |
Length of the proxy along its Y axis.

 |

**
Size Z
**
 |
Length of the proxy along its Z axis.

 |

##
PRow Attachment

Option
 |
Description
 |

**
Name
**
 |
Name of the attachment.

 |

**
Type
**
 |
Attachment type (PRow Attachment).

 |

**
Row Joint Name
**
 |
First joint in the first row of the attachment.

**
Naming is important:
**
 It should be YOURNAME_x00_y01 (replace YOURNAME by your object name) - the following attached joints would be detected automatically, i.e. YOURNAME_x01_y01, YOURNAME_x02_y01, YOURNAME_x03_y01, ...

 |

**
Clamp Mode
**
 |
Determines the style of constraining the movement of the pendulas.

 |

**
Debug Setup
**
 |
Enables debug rendering of pendulas for debugging purpose.

 |

**
Debug Text
**
 |
Shows debugging info.

 |

**
Activate Simulation
**
 |
Enables simulation.

 |

**
Simulation FPS
**
 |
Determines the framerate at which to update the physical simulation, values between 10-255 can be selected. In the case of pendula cloth, the value chosen is actually the real physical update per second. Furthermore, with a fixed simulation framerate then the simulation will be more deterministic. If the default value of 10 is selected, then there will not be any more than 10 physics updates per render frame. If the difference between the render and simulation framerates is large, then the simulation fps may demonstrate some stuttering - this stuttering can be visually very unpleasant. Therefore, it is recommended to set the simulation framerate to something between 30 and 60 fps. If the game is using a fixed framerate, then the physics should ideally use the same framerate.

 |

**
Mass
**
 |
Defines the mass of the pendulum bob and as long as the
**
joint spring
**
 is 0, then the mass has no impact on the period of oscillation.

 |

**
Gravity
**
 |
The default value of
**
9.81m/sec
**
 is the standard acceleration of falling objects due to gravity acting on the Earth. While the mass of the bob has no effect on the oscillation of the pendulum the force of gravity does.

 |

**
Damping
**
 |
This value can be used to simulate
**
velocity dependent forces
**
, for example air resistance. So, the faster an object moves then the more air friction it encounters. This means that the friction force decelerates an object at a rate that is proportional to the velocity, hence higher damping values will make oscillating objects come to rest more quickly.

 |

**
Joint Spring
**
 |
This value can be used to simulate
**
position dependent forces
**
, and is a value between 0-999 applied to the spherical joint. The further the pendulum swings away from the axis of the
**
spring target
**
, then the harder it tries to return. A value of 0 has no spring effect, so the pendulum will hang downward when it comes to rest. The higher the value, then the faster the bob oscillates and is attracted by the
**
Spring Target
**
, which can point in any direction. It is important to mention that the tension of the spring is a counter force to the mass & gravity and that a higher mass will always pull the bob downwards.

 |

**
Cone Angle
**
 |
The movement of the pendula can be constrained by three bounding volumes: cone, half-cone and hinge-plane. This slider allows you to choose the opening angle for the cone, half-cone or hinge-plane and by default is set at 45-degrees. A range of angles are available (0-179) and where values larger than 90-degrees create an inverse cone.

 |

**
Cone Rotation
**
 |
Enables rotation of the cone, half-cone and the hinge-plane relative to the joint.

 |

**
Rod Length
**
 |
Defines the length of the rod. The length of the rod has a large impact on the swinging frequency of the pendulum, so the longer the rod then the longer it will take for the pendulum to oscillate back and forth.

 |

**
Spring Target
**
 |
The parameters
**
spring target
**
 and
**
joint spring
**
 are closely related, and where the spring target is an axis relative to the x-axis of the joint. Furthermore, there are two planes of rotation that a user has at their disposal and these permit the spring target axis to rotate about the simulation axis – in this way any position can be reached both inside and outside of the cone, half-cone or hinge-plane.

 |

**
Turbulence
**
 |
This is a modulation of the dampening value and is based on the movement speed of the character. The first value controls the frequency, the second the amplitude and by using the turbulence feature subtle noise can be added to the simulation to simulate elements such as the effect of the wind on cloth.

 |

**
Max Velocity
**
 |
The bob of the pendulum can reach very high velocities, especially when the character is undertaking sudden pose changes or is teleported from one position to another. Clamping the velocity prevents large impulses which can bring the simulation into an uncontrolled state.

 |

**
Cycle
**
 |
Pendula cloth operates on a joint set-up that has a rectangular grid structure. In the case of capes and coats the left and right side of the grid are not connected to each other. However, in the case of skirts all pendula need to be connected on the horizontal axis. By activating the
**
Cycle
**
 checkbox the last joint in the row gets connected to the first joint in the row. Hence, the row is actually a circle of pendula.

 |

**
Stretch
**
 |
This value is used to define
**

**
how much the
**

**
cloth can stretch horizontally. A value of 0 (combined with a high value for Relaxation Loops) enforces a fixed horizontal distance between the pendula. A value of 0.2 means the distance can stretch or shrink by 20%. The default horizontal "default distance" is the distance between the joints in the default pose.

 |

**
Relax Loops
**
 |
This method uses an iterative approach to keep the pendula together and in a horizontal row. Each iteration brings them closer together and this occurs every frame. For most instances a value of 2-4 is recommend.

 |

**
Capsule
**
 |
Collision detection is a simple overlap test between a lozenge and either a capsule or a sphere. To enable collision detection for a pendula row the blue proxies
must first be set-up.
**

**
Each joint in a pendula row can have a
**
Capsule
**
 for collision detection and one end of the capsule is always connected to the joint (pivot), this means that you can only change the
**
length
**
 along the rod-axis and the radius. Changing these values will change the capsule for the entire row.

 |

**
Projection Type
**
 |
If you choose a
**
Projection Type
**
, it will activate the list for
**
Available Collision Proxies
**
. These proxies are applied for the whole row of capsules. Collision response has been covered in the previous section under
**
Enabling Collision Detection
**
.

 |

##
VCloth 2.0 Attachment

Parameter
 |
Description
 |

**
Name
**
 |
Name of the attachment.

 |

**
Type
**
 |
Attachment type (one of the types described here).

 |

*
*

*
*

*
**
Animation Control
**
*

Parameter

 |
Description

 |
Recommended value/range

 |

**
Force Skinning
**

 |
Skips simulation pass and enforces skinning for cloth - useful for debugging.

 |

 |

**
Force Skinning FPS Thresh
**

 |
If the game's/editor's frame rate drops under the provided FPS, simulation is skipped and skinning is enforced. This should be used as a stability threshold. If the frame rate drops strongly, no time should be spent on the cloth simulation, which would slow down the game even further.

 |
20

 |

**
Force Skinning Translate Thresh
**

 |
If the translation distance per frame exceeds the provided threshold, simulation is skipped and skinning is enforced. This way, character jumps/beams could be handled, without weird side-effects of the cloth simulation.

 |
0.5

 |

**
Check Animation Rewind
**

 |
Reset particle positions to skinned positions. If a time jump occurs in the animation (e.g. in case of animation rewind). Helpful for debugging your animations, since animation restarts are detected and the cloth is reset in those cases.

 |

 |

**
Disable Simulation At Distance
**

 |
Disable simulation/enable skinning depending on camera distance (world distance). If the camera distance exceeds this threshold, the simulated cloth fades to skinning to improve performance and to avoid spending time on characters which are far away.

Set to 0.0 to disable.

 |
10.0

 |

**
Disable Simulation Time Range
**

 |
Defines the physical time [in seconds] which is used for fading between simulation and skinning, e.g. 0.5 implies half a second for fading.

 |
0.3 - 0.5

 |

**
Enable Simulation SS Size
**

 |
If the size of characters' bounding boxes in screen space exceeds this percentage of the viewport size, Vcloth simulation is enabled.

Therefore, the Vcloth simulation can be controlled according to the characters' actual size on screen.

This value is used for X and Y direction separately.

 |

 |

Parameter

 |
Description

 |
Recommended value/range

 |

**
Time Step
**

 |
Physical simulation time step - maximum time step, which is used within sub-stepping of cloth simulation.

 |
0.007 -0.01

 |

**
Time Step Max Iteration
**

 |
Maximum number of iterations for the time discretization between two frames. If the number of sub-steps exceeds this threshold, simulation is aborted.

 |
30

 |

**
Coll./Stiffness Iterations
**

 |
Number of stiffness/collision iterations per time step. Per sub-step, the collision- and stiffness-solver are executed several times to increase stiffness and stability.

 |
5

 |

**
Collide Every n-th Step
**

 |
During stiffness/collision iterations, only execute collision resolve every n-th step.
**
0
**
 disables collisions. Improve performance by changing no. of collision steps in relation to stiffness steps. Smaller means faster but less responsible to collisions.

Works in relation to the previous parameter,
**
Coll./Stiffness Iterations
**
. E.g.
**
2
**
 means on 2 stiffness steps, one collision step is executed.

Set to 0.0 to disable.

 |
2

 |

**
Multi-Collisions Shift Factor
**

 |
In case of multiple collisions at the same time, the particle is shifted by this factor into the average direction.
**
0.0
**
 disables multiple-collision handling. At the moment a maximum of 2 simultaneous collisions is handled.

This value gets important if several collision proxies are intersecting (e.g. at the knees). If collisions are not handled convincingly, increase this value.

Set to 0.0 to disable.

 |
Depending on your proxy setup: 0.0 - 1.0

(only enable if there are problems in the area of on proxy intersections during animations)

 |

**
Gravity Factor
**

 |
Defines intensity of gravity. This factor is multiplied with the gravity. This parameter can be used to tweak the weight of your cloth.

 |
0.1 - 0.5

(normally, a reduced gravity looks good and is much more stable)

 |

For more information about time stepping see
**
[/docs/static/engines/cryengine-5/categories/23756816/pages/29799532#VCloth2.0-TimeStepping](
here
)
**
.

*
**
Stiffness and Elasticity
**
*

Parameter

 |
Description

 |
Recommended value/range

 |

**
Stretch Stiffness
**

 |
Define Stretch Strength - smaller values indicate less stiffness, larger values indicate stronger stiffness.

A value of 0.0 disables Stretch Stiffness.

Set to 0.0 to disable.

 |
0.1 - 1.0

 |

**
Shear Stiffness
**

 |
Define Shear Strength - smaller values indicate less stiffness, larger values indicate stronger stiffness.

A value of 0.0 disables Shear Stiffness.

Set to 0.0 to disable.

 |
0.1 - 1.0

 |

**
Bend Stiffness
**

 |
Define Bend Strength - smaller values indicate less stiffness, larger values indicate stronger stiffness.

A value of 0.0 disables Bend Stiffness.

Set to 0.0 to disable.

 |
0.1 - 1.0

 |

**
Bend Stiffness By Angle
**

 |
Bend stiffness depends on triangle angles. Therefore, this bending stiffness does not affect elasticity. This parameter acts fairly similar to the previous parameter, but does not use springs to determine the bend stiffness. Rather, it works directly on neighboring triangles and their according angles.

A value of 0.0 disables Bend Stiffness By Angle.

Set to 0.0 to disable.

 |
0.0 - 1.0

*
If you are happy with the normal bending stiffness, this should be disabled, since it is more expensive.

*

 |

**
Pull Stiffness
**

 |
Strength of pulling pinched vertices towards their determined skinned position. Also used for parameter
**
Max Skin Distance
**
 (see below).

This parameter can improve stiffness without reducing stability.

Set to 0.0 to disable.

 |
0.0 - 1.0

 |

*
**
Friction and Damping
**
*

Parameter

 |
Description

 |
Recommended value/range

 |

**
Friction
**

 |
Global friction. A simple friction. This value reduces particle velocities linearly. A minor value of friction is usually necessary for stability reasons.

 |
As starting point: 0.01

Then reduce slowly to increase dynamics.

 |

**
Rigid Damping
**

 |
Special damping - the higher this value, the more rigid the cloth appears.
**
0.0
**
 represents no damping,
**
1.0
**
 represents rigid cloth.

 |
As starting point: 0
.03

Then reduce slowly to increase dynamics.

 |

*
**
Nearest Neighbor Distance Constraints
**
*

Parameter

 |
Description

 |
Recommended value/range

 |

**
Nearest Neighbor Distance Constraints
**

 |
Enables NNDC for improved stiffness, while reducing elasticity.

 |

 |

**
NNDC maximum shift factor
**

 |
Scales maximum shift per iteration in direction of closest neighbor, e.g.
**
0.5
**
 -> halfway to closest neighbor. Smaller values result in higher stability.

 |
0.1 - 0.4

 |

**
NNDC shift collision factor
**

 |
Scales in case of shift the velocity,
**
0.0
**
 = no shift,
**
1.0
**
 = no velocity change,
**
-1
**
 = increase velocity by change.

 |
*
Should normally be 1.0, otherwise stability issues might occur. Only change value if flickering due to NNDCs occur.
*

 |

**
NNDC allowed extension
**

 |
Allowed extension for Nearest
Neighbor Distance Constraints
, e.g.
**
0.1
**
 = 10%

Set to 0.0 to disable.

 |
0.0 - 1.0

 |

*
**
Additional
**
*

Parameter

 |
Description

 |
Recommended value/range

 |

**
Max Skin Distance
**
 |
Maximum allowed particle distance from skinned position. Threshold for the maximum distance between simulation mesh and skinned cloth.

Can be used to keep cloth kind of "in place".

Set to 0.0 to disable.

 |
0.0

 |

**
Mesh Filter Laplace
**
 |
Enables post-process laplace smoothing filter for the simulation mesh. Accept values between 0 and 1, where 0.0 means no filtering and 1.0 full filtering.

Set to 0.0 to disable.

 |
0.0

(otherwise it might be expensive)

 |

*
**
Reset Damping
**
*

Parameter

 |
Description

 |
Recommended value/range

 |

**
Reset Damping N Frames
**
 |
Damps particles velocity for N frames after reset, to prevent cloth from strong fluttering. When the cloth is initialized, for this number of frames, the cloth is damped additionally to let the cloth settle down.

 |
3

 |

**
Reset Damping Factor
**
 |
Strength of initial damping (is related to previous parameter).

 |
0.0
*
(i.e. strong damping)
*

 |

*
**
Files
**
*

Parameter
 |
Description
 |

**
renderMeshName
**
 |
Name for the render mesh (e.g., "my_cloth_render").

 |

**
Binding
**
 |
File path for the render skin file (e.g., "characters/my_player/attachments/vcloth/my_player_my_cloth_render.skin").

 |

**
simMeshName
**
 |
Name for the simulation mesh (e.g. "my_cloth_sim").

 |

**
simBinding
**
 |
File path for the simulation skin file (e.g. "characters/my_player/attachments/vcloth/my_player_my_cloth_sim.skin").

 |

**
material
**
 |
File path for the material file (e.g., "characters/my_player/materials/my_player_material.mtl").

 |

*
**
Debug
**
*

See
[/docs/static/engines/cryengine-5/categories/23756816/pages/25530479#Tutorial-VCloth2.0Setup-VCloth2DebugSim](
here
)
 for more information.

##
Skeleton Properties

These properties are only displayed when editing a skeleton asset and are stored within a .chrparams script next to it. Skeleton properties are mainly used for defining an animation set associated with a skeleton.

Option
 |
Description
 |

**
Includes
**
 |
Other .chrparams scrips to include animation sets from. This can be used to reuse animation sets across different skeletons.

 |

**
Animation Set Filter
**
 |
List of rules defining which animations should belong to the set associated with this skeleton. Each rule consists of a base directory path and a list of wildcard patterns for matching files within this directory. Animation names are generated based on how the wildcard pattern matches their corresponding file names.

 |

**
Animation Events File
**
 |
Path to an .animevents script storing animation events for this skeleton's animation set.

 |

**
DBA Path
**
 |
Path to a directory containing DBA files associated with this skeleton. All animation clips contained in DBAs found within this directory will be included in this skeleton's animation set. DBA association is independent from
**
Animation Set Filter
**
 and is required for DBA clips to be usable by characters built with this skeleton.

 |

**
Individual DBAs
**
 |
List of additional DBA files, supplementary to ones matched using
**
DBA Path
**
.

-
**
Persistent -
**
 Disable data streaming for a particular DBA file and force all of its clips to always stay in memory in the final build of the game.
 |

##
Animation Properties

These properties are only displayed when editing an animation asset and are stored within an .animsettings script next to it. Animation properties are mainly used for specifying preprocessing and compression settings. Depending on the situation, you may have to click the
**
Create New AnimSettings
**
 button first.

Option
 |
Description
 |

**
Additive
**
 |
Enable additive motion pre-processing step for this animation asset.

 |

**
Skeleton Alias
**
 |
Skeleton used to author this animation asset. Used for motion extraction and controller filtering.

 |

**
Tags
**
 |
List of custom user tags.

 |

##
Compression

Option
 |
Description
 |

**
Compression Value
**
 |
General quality setting for the lossy compression algorithm. Lower = higher fidelity, larger file size.

 |

##
Controller Auto Removal Threshold

Threshold values for particular controller types over which animation controllers will be completely removed during the compression step.
**

**

Option
 |
Description
 |

**
Position
**
 |
Removal threshold for position controllers.

 |

**
Rotation
**
 |
Removal threshold for rotation controllers.

 |

**
Scale
**
 |
Removal threshold for scale controllers.

 |

##
Per-Joint Settings

Provides a way to fine-tune compression settings on a per-controller basis.

The drop-down list specifies whether a controller shall be unconditionally kept or removed.

The numeric field provides an additional multiplier applied to the general
**
Compression Value
**
.
**

**

##
Compression (Animations)

##
Compression Presets

List of global compression settings for animation assets. Each entry can be configured with the following options:

Option
 |
Description
 |

**
Name
**
 |
Name of the compression preset.

 |

**
Filter
**
 |
S
pecifies which animation assets should be affected by this preset. The filter can be composed from a set of rules based on file names, directories, associated skeleton aliases and custom tags
**
.

**

 |

##
Settings

Option
 |
Description
 |

**
Compression Value
**
 |
General quality setting for the lossy compression algorithm. Lower = higher fidelity, larger file size.

 |

*
**
Controller Auto Removal Threshold
**
*

Threshold values for particular controller types over which animation controllers will be completely removed during the compression step.

**

**

Option
 |
Description
 |

**
Position
**
 |
Removal threshold for position controllers.

 |

**
Rotation
**
 |
Removal threshold for rotation controllers.

 |

**
Scale
**
 |
Removal threshold for scale controllers.

 |

##
Per-Joint Settings

Provides a way to fine-tune compression settings on a per-controller basis.

The dropdown list specifies whether a controller shall be unconditionally kept or removed.

The numeric field provides an additional multiplier applied to the general
**
Compression Value
**
**
.

**

##
Matching Local Animations

Lists all animation assets that are currently matched with
**
Filter
**
 and will be affected by this compression preset.

##
DBA Table

 List of DBA file definitions.
 Each entry can be configured with the following options:

Option
 |
Description
 |

**
Path
**
 |
Output path for the DBA file.

 |

**
Filter
**
 |
S
pecifies which animation assets should be affected by this preset. The filter can be composed from a set of rules based on file names, directories, associated skeleton aliases and custom tags
.

 |

##
Matching Local Animations

Lists all animation assets that are currently matched with
**
Filter
**
 and will be included in the generated DBA file.

##
Skeleton List

List of skeleton aliases.

Each entry maps a skeleton alias to a skeleton asset.

Note that you can copy and paste each of the properties and also filter the property list by using the right click context menu!

##
Related Pages

For more information on how to use VCloth, check the following pages:

[/docs/static/engines/cryengine-5/categories/23756816/pages/29799532](
VCloth 2.0
)

[/docs/static/engines/cryengine-5/categories/23756816/pages/25530837](
How To - Export VCloth from Maya to CRYENGINE
)

[/docs/static/engines/cryengine-5/categories/23756816/pages/25530479](
Tutorial - VCloth 2.0 Setup
)

[#properties-panel-header](
Properties Panel Header
)
[#character-properties](
Character Properties
)
[#skeleton-properties](
Skeleton Properties
)
[#animation-properties](
Animation Properties
)
[#compression-animations](
Compression (Animations)
)
