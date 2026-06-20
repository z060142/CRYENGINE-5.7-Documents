# Rope Tool

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/36867658
- Page ID: 36867658
- Breadcrumb: Editor Tools > Level Editor Tab > Create Object > Misc Objects > Rope Tool
- Parent: Misc Objects

## Content

##
Overview

Ropes can be used to attach objects together or to hang objects from. They react to objects around them, but will not affect those objects.

The Rope tool can be found under
**
Create Object → Misc → Rope
**
.

##
Properties

**
Rope Parameters
**

 |
**
Description
**

 |

**
Radius
**

 |
The radius, or thickness, of the rope.

 |

**
Smooth
**

 |
Defines if the rope will be smoothed out or not.

 |

**
Use Bones
**

 |
Ropes that use bones create their render meshes only once (during initialization or when the parameters change) and only update bone transformation at runtime.

See for examples.

 |

**
Num Segments
**

 |
The number of segments of geometry used in the rope along its length.

 |

**
Num Sides
**

 |
The number of sides around the circumference of the rope. 4 sides would make it a diamond-shaped tube, 8 sides would make it much smoother, etc.

 |

**
Radius Change
**

 |
Allows to change the rope's radius (or scaling of its segment meshes) along its length. For instance, -1 will reduce the size at the end to 0, creating a cone-shaped rope:

[Image: /docs/static/attachments/36846997]

This is only a visual effect; it doesn't affect the physical simulation.

 |

**
Bone Smooth Iters
**

 |
The number of smoothing passes on the rope. The more passes, the smoother the rope gets. However, how many are needed depends on factors such as the length of the rope, the length of the segments and the number of segments.
Generally, only 2-3 iterations are enough for a decent result. More than 5 are not necessary, as the rope would be "oversmoothed".

 |

**
Texture U Tiling
**

 |
Texture tiling in the U direction.

 |

**
Texture V Tiling
**

 |
Texture tiling in the V direction.

 |

**
Cast Shadows
**

 |
Enable shadow casting from the rope.

 |

**
Bind Ends Radius
**

 |
Specifies whether the ends will be automatically attached.

 |

**
Bind Radius
**

 |
The environment around the ends of the rope will be tested using a box of this radius to find places for the rope to attached to.

Note that if bind radius is greater than 0.05 the ends are snapped to the colliding surface.

 |

**
Custom Segment Mesh
**

 |
 |

**
Mesh
**

 |
Selects the .cgf (only non-compound cgfs are supported). If the rope has no material, it will be changed to use the material from the .cgf.

Only a single submaterial will be used for the entire mesh.

Using custom meshes always activates bone skinning mode, even if
**
Use Bones
**
 flag is not set explicitly.

 |

**
Mesh Axis
**

 |
Sets the axis that will be aligned to the rope's direction.

 |

**
Repeat Length
**

 |
Sets the repeat point, relative to the .cgf size along that axis. For instance, 1.5 will add 50% of extra free space after each instance of the mesh.

 |

**
Repeat Rotation
**

 |
Allows to rotate the mesh around the axis at each iteration.

 |

**
Bendable
**

 |
Makes skinning to bones interpolated instead of per-instance rigid.

 |

Physics Parameters

 |

 |

**
Subdivide
**

 |
Turns dynamic subdivision on.

 |

**
Max Subdiv Verts
**

 |
Maximum number of subdivided vertices per segment.

 |

**
Physical Segments
**

 |
Number of rope segments in physics (can be different from the number of segments used for rendering).

For colliding ropes, make sure that there are enough physical segments so that segment length is at least two times smaller than the dimensions of the objects the rope collides with.

 |

**
Tension
**

 |
Specifies tension in the original state. A positive value will cause the rope ends to pull together, negative will add slack to the rope (-0.02 is a good starting point for experiments).

 |

**
Friction
**

 |
The friction effective in a non-strained mode. In a strained mode with dynamic tessellation, this prevents the rope from slipping until it tilts too much.

 |

**
Wind X, Y, Z

**

 |
Simulated wind, additional to any area-specific winds around.

 |

**
Wind Variation
**

 |
How much the wind varies. Basically a randomization multiplier on top of the base Wind XYZ values.

 |

**
Air Resistance
**

 |
Must be set in order for global environment wind to take effect. Not necessary for simulated Wind XYZ values.

 |

**
Water Resistance
**

 |
How the rope interacts with water effectively damping when under water.

 |

**
Check Collisions
**

 |
Ignore collisions from other objects, bullets, etc.

 |

**
Ignore Attachment Collisions
**

 |
Ignore collisions with the object it is attached to.

 |

**
Ignore Player Collisions
**

 |
Ignore collisions with players.

 |

**
Non-shootable
**

 |
Rope cannot be broken by shooting. The rope will still react to physical impulses from bullets.

 |

**
Disabled
**

 |
Simulation is completely disabled.

 |

**
Static Attach Start
**

 |
Attach start point to the 'world'.

 |

**
Static Attach End
**

 |
Attach endpoint to the 'world'.

 |

Advanced Physics

 |

 |

**
Mass
**

 |
This affects how strongly the rope will react to bullet hits. When interacting with solid physicalized objects, it is always treated as weightless.

 |

**
Friction Pull
**

 |
How strongly the rope opposes movement in its pull direction (when strained with dynamic tessellation).

Keep this value either small enough (0.1 - 0.3) to get some resistance, or large enough (5-10 - 100+) to make sure the rope sticks firmly in most cases.

Intermediate values can lead to unstable behavior when the object the rope rubs against (ex. a pulley) is light enough compared to the objects it is tied to.

When the subdivision is off, it's used as 'twist' damping for attached objects.

 |

**
Max Force
**

 |
The rope will detach itself when this strain limit is breached.

 |

**
Awake
**

 |
By default, the object is in a sleep mode so that it doesn't use any resources from the physics engine until it is required to do so. You can make the object to be "awake" by default by checking the Awake
parameter.

 |

**
Solver Iterations
**

 |
Ropes with very large segment counts (40+) might need this increased (values up to 10k are still viable).

 |

**
Max Timestep
**

 |
Sets the maximum time step the entity is allowed to make (defaults to 0.01). Smaller time steps increase stability (can be required for long and thin objects, for instance), but are more expensive.

Each time the physical world is requested to make a step, the objects that have their maxsteps smaller than the requested one slice the big step into smaller chunks and perform several substeps.

If several objects are in contact, the smallest max_time_step is used.

 |

**
Stiffness
**

 |
The rope's stiffness against stretching. Might need tweaking for longer ropes.

Note the in most cases ropes will use exact length enforcement (meaning 'infinite' stiffness), but internally stiffness will still be used to compute the dynamics.

 |

**
Contact Hardness
**

 |
Hardness of contacts and length enforcement in subdivision mode, when strained and potentially touching other objects in the middle. Higher values make it potentially less stable.

 |

**
Damping
**

 |
Sets the strength of the damping on an object's movement. Most objects can work with 0 damping; if an object has trouble coming to rest, try values like 0.2 - 0.3.

Values of 0.5 and higher appear visually as overdamping. Note that when several objects are in contact, the highest damping is used for all associated contacts.

 |

**
Sleep Speed
**

 |
If the object's kinetic energy falls below some limit over several frames, the object is considered "sleeping". This limit is proportional to the square of the sleep speed value.

A sleep speed of 0.01 loosely corresponds to the object's center moving at a velocity of the order of 1 cm/s.

 |

Audio Parameters

 |

 |

**
Start Trigger
**

 |
This audio system Trigger is executed once the rope starts moving.

 |

**
Stop Trigger
**

 |
This audio system Trigger is executed once the rope comes to rest.

In this case the
**
Start Trigger
**
 instance is not explicitly stopped. See
[http://84.16.230.215:8090/display/C5/Defining+PlayTrigger+and+StopTrigger+Behavior](
Defining PlayTrigger and StopTrigger Behavior
)
.
 |

**
Angle Parameters
**

 |
This parameter indicates the angle between the two segments that the audio object is attached to.

Values available are between 0-180°.

This parameter won't be updated (always 180°) in case the sound is attached to either the very end, or the beginning of the rope.
 |

**
Occlusion Type
**

 |
Sets the number of ray casts that are used to calculate occlusion for the created audio object. Using more ray casts means greater performance requirements, but provides a more accurate result.

-
**
Ignore -

**
The audio object does not calculate occlusion against the level geometry.

-
**
Adaptive -
**
The audio object switches between the occlusion types depending on its distance to the audio listener.

-
**
Low -
**
The audio object uses fewer ray casts, which results in the least accurate calculation of occlusion and the best performance.

-
**
Medium -
**
The audio object uses more ray casts, which results in more precise occlusion calculation but a poorer performance than the

**
Low
**

occlusion type.

-
**
High  -
**
The audio object uses the maximum amount of ray casts, which results in the most precise occlusion calculation and the worst performance.
 |

**
Segment
**

 |
Choose which segment the audio object should attach itself to.

 |

**
Position Offset
**

 |
The position offset indicates how far a sound is moved away from its original attachment point.

The number (.0-1) moves the sound along the length of the segment to which the sound is attached.

 |

-
Please note, that when setting up a sound in FMOD for use with ropes, a new parameter has been added. "Angle" indicates the angle of the nearest joint, unless that joint is at the very beginning or end of the rope. The angle that the two segments form, from 0-180 degrees, will then affect the sound as the designer decides.

-
The audio object implicitly enables the TrackAbsoluteVelocity feature, which is handled entirely by the underlying middleware implementation.

-
When setting up the sound, also pay attention to the sound's speed in km/h.

##
Rope Creation

Turn on
**
 Snapping to terrain
**
 and
**
Snapping to geometry
**
. Place the rope by using
**
LMB
**
. This works in a similar way as placing a road.

A rope can be edited using the
**
Edit Shape
**
 button in its properties.

You can move points in the normal way, add points by
**
Ctrl + LMB
**
 and remove them by
**
double clicking
**
.

When in
**
Edit Shape
**
mode, a point can be green or red. Green means the rope is validly attached, and red means the rope is not attached to anything:

[Image: /docs/static/attachments/36844658]

##
Dynamic Tessellation/Subdivide

There are two rope simulation modes, with dynamic tessellation on or off. Without dynamic tessellation rope, segments are asset-based and are simulated as rigid sticks. In this mode, the rope cannot properly collide with objects when it's tied with both ends and strained.

With dynamic tessellation the rope has a certain number of segments (Num Segments, independently of the actual rope asset), and each of them can have a maximum number of subdivided internal vertices, created at collision points.

More segments make the rope less likely to tunnel through thin objects, but increase the simulation cost. Refer to the art documentation on how to author rope assets for these two modes.

##
Examples For Bone Usage

The Use Bones property works in combination with some other properties. Below some examples of how it works.

-
(
**
Bones
**
 or
**
no Bones
**
) +
**
 no Subdivision
**
 +
**
no Smoothing
**
 - generates
*
Physical Segments
*
 amount of rigid bones

-
**
Bones
**
 +
**
Smoothing
**
 - places
*
Num Segments
*
 amount of segments over the physical rope (subdivided or not), then smooths (averages) their positions (
*
Bone Smooth Iters
*
 number of times). Skinning to bones is interpolated instead of rigid

-
**
no bones
**
 +
**
smoothing
**
 - generates a spline with
*
Num Segments
*
 points from physical rope points

-
**
no bones
**
 +
**
no smoothing
**
 generates straight mesh segments between physical vertices, subdivided or not (as before)

-
**
bones
**
 +
**
subdivision
**
 +
**
no smoothing
**
 - uses old (mesh-based) mode whenever intermediate points are added by the physics, and bone-based with
*
Physical Segments
*
 amount of bones otherwise. to avoid switching to non-bones mode, it's possible to enable smoothing and set
*
Num Segments
*
 to be sufficiently larger than
*
Physical Segments
*
 (to accommodate new subdivided vertices).
*
Bone Smooth Iters
*
 can be set to 0 if no actual smoothing is needed.

-
If
**
custom mesh
**
 is used,
**
Num Segments
**
 is less than
**
Physical Segments
**
,
**
subdivision
**
 is
**
off
**
, and
**
Bendable
**
is on, the rope will use physical segments as bones and will redistribute mesh vertices among then. In this mode it's possible to skin the mesh to several (more than 2) bones.

[Image: /docs/static/attachments/36847643]

[#properties](
Properties
)
[#rope-creation](
Rope Creation
)
[#dynamic-tessellationsubdivide](
Dynamic Tessellation/Subdivide
)
[#examples-for-bone-usage](
Examples For Bone Usage
)
