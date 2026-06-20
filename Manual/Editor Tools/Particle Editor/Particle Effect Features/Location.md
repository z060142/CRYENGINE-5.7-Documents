# Location

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/36867977
- Page ID: 36867977
- Breadcrumb: Editor Tools > Particle Editor > Particle Effect Features > Location
- Parent: Particle Effect Features

## Content

##
Overview

This category sets the location of the particles that will be placed in the game world. By default, newborn particles are always placed on the same location as the particle emitter or their parent particle location. For more information about parent-child relationships, see
[SecondGen](SecondGen.md)
.

Some of the location features also allow the user to change the velocity or the location of a particle, even after it spawns.

A very important aspect to take into account is that these features can be combined with each other. Using the right combination(s) allows users to create striking and advanced visual effects.

The following options are available under the Location category:

##
Beam

Spawn particles in a consecutive line forming a beam between a source and a destination. This feature is best used when paired with
[Spawn: Count](Spawn.md)
 and
[Render: Ribbon](Render.md)
.

Property

 |
Description

 |

**
Source
**

 |
Start location of the beam.

 |

**
Destination
**

 |
End location of the beam.

 |

**
Position
**

 |
Defines the fractional position along the beam. Position can take any modifiers, including functions with a domain of Spawn Fraction, Spawn Id, Random etc.

 |

Both source and destination are internally treated as targets which have the following properties:

Target Property

 |
Description

 |

**
Source and Destination dropdown menus
**

 |
The location that the target uses as a source; not to be confused with beam source which is the location at which the beam starts.

-
**
Self -
**
 Uses the new born particle position itself as a source.

-
**
Parent -
**
 Uses the parent position, or emitter position if there is no parent present, as a source.

-
**
Target -
**
Uses particle emitter's target position, which is usually another game entity, as a source.

For more information on targeting, see
[Key Concepts](../../../Graphics%20%26%20Rendering/Particles/Key%20Concepts.md)
 about Emitter Targets.
 |

**
Offset
**

 |
Additional offset applied to the source in local space (X, Y and Z).

 |

##
BindToCamera

This feature allows the new born particles to spawn relative to the camera instead of its parent or emitter. All other Location and Velocity features will then be relative to the camera. This feature is especially useful for certain types of screen effects.

Property

 |
Description

 |

**
Spawn Only
**

 |
When enabled, spawns new born particles relative to the camera, but then they will behave like regular particles. If enabled, particles will be permanently attached to the camera.

 |

##
Box

This feature allows the new born particles to be randomly but uniformly placed within a box. It can also be used to create uniform planes and uniform lines by collapsing one or two axes.

Property

 |
Description

 |

**
Dimension
**

 |
Configures the size of the box on X (width), Y (length) and Z (height) axes.

Setting a zero value to an axis will collapse that dimension. If a single axis is collapsed, a plane is created; if two axes are collapsed, a line is created.

 |

**
Scale
**

 |
Allows scaling the dimension up or down. This option is useful when used with
[Modifiers](Modifiers.md)
.

 |

**
Distribution
**

 |
Particles are distributed to different dimensions based on the selected parameter:

-
**
Random -
**
Particles are distributed to randomly selected dimensions.

-
**
Ordered -
**
 When selected, one Modulus field appears for each dimension that is available for distribution. To distribute particles along these dimensions, each of these fields must be set to
**
a value greater than 1
**
.
 |

##
Circle

This feature allows the new born particles to be randomly but uniformly placed in a circle around the parent particle. This circle is in the plane XY of the parent. When the parent is rotated, the circle will also rotate.

Property

 |
Description

 |

**
Radius
**

 |
Specifies the radius of the circle in meters. By default, it spawns the particles on the perimeter of a circle until
[Modifiers](Modifiers.md)
 are used. When the Random modifier is set to 100%, particles can be uniformly spawned within the circle instead of spawning around the perimeter.

 |

**
Velocity
**

 |
Specifies initial particle velocity in meters per second. Positive values make particles move in an XY plane outwards from the center. Negative values make particles move in an XY plane inwards toward the center.

 |

**
Inner Fraction
**

 |
Sets the inner radius of distribution on circles. This is an easier and more precise way to distribute particles within the radius
than adding a Random modifier to the radius parameter.

 |

**
Axis Scale
**

 |
Enables the scaling of X and Y axes individually. Use this to create ellipses instead of circles.

 |

**
Axis
**

 |
Specifies which axis, relative to the parent particle or emitter that should be perpendicular to the circle's plane. For example, if Y axis value is set to 0, 1, 0 the circle will be displayed in the XoZ plane.

 |

**
Distribution
**

 |
Particles are distributed to different dimensions based on the selected parameter:

-
**
Random -
**
Particles are distributed to randomly selected dimensions.

-
**
Ordered -
**
 When selected, one Modulus field appears for each dimension available for distribution. To distribute particles along these dimensions, each of these fields must be set to
**
a value greater than 1
**
.
 |

##
Geometry

This feature allows the new born particles to be randomly but uniformly distributed along a mesh geometry.

When parent particles are not meshes or the component does not include SecondGen feature, the emitter needs to be linked to another entity that has a mesh.

Property

 |
Description

 |

**
Source
**

 |
Specifies the geometrical source of locations.

-
**
Render -
**
 Receives location details from the mesh used to render linked entity.

-
**
Physics -
**
 Receives location details from the linked physical entity.
 |

**
Location
**

 |
Specifies the location from where the particles should be emitted.

-
**
Vertices -
**
 Grabs the positions of the mesh vertices. This might not work when the source is set to physics and the mesh does not have any vertices; e.g. perfect spheres.

-
**
Edges -
**
 Locates new particles along the edges of the source mesh. Might not work when the source is set to physics and the mesh does not have any edges; e.g. perfect spheres.

-
**
Surface -
**
 Uniformly places the new particles along the surface of the source mesh.

-
**
Volume -
**
 If Source is set to Physics and the mesh is a well defined geometric shape like spheres, boxes or capsules, this option ensures that particles are uniformly distributed inside the defined volume. When the mesh source is Render or the physics mesh is a triangle soup, this option makes the particles spawn uniformly within the third degree simplex which is connected to the origin of the source mesh. This type of distribution works well if the source mesh is strictly convex and contains its origin.
 |

**
Offset
**

 |
By default, places the particles exactly on the mesh. Offset displaces the particles using the normal vector. This property is defined in meters.

 |

**
Velocity
**

 |
Specifies the initial particle velocity in meters per second. Its orientation is the same as the normal vector.

 |

**
Orient to Normal
**

 |
Rotates the particle so that its normal vector, but not the forward vector, aligns with the surface normal. Given enough particles, they can recreate the underlying mesh almost perfectly. For more information on Euler angles, see
[Angles: Rotate3D](Angles.md)
.

 |

**
Augment Location
**

 |
If true, adds the location offsets from other location features to the geometry location.

If false, ignores other location features and places particles directly on the geometry.

 |

##
Noise

This feature displaces the particle location using a potential vector field based on a simplex noise. This feature can distort and randomly shape the other location features while maintaining their geometric features without getting fuzzy or diffused.

Property

 |
Description

 |

**
Amplitude
**

 |
Specifies how far the particles can move away from their original location. The distance is calculated in meters.

 |

**
Size
**

 |
Noise uses Simplex Noise to generate a vector field, which is similar to Perlin Noise, but can be more efficient in some cases. This type of noise creates a uniform grid of vertices in space and sets each vertex to a random value. The actual displacement added to the particle is interpolated from this grid. Therefore, size specifies the distance between the vertices in this grid. If the size is too small, noise will start to get more random, fuzzy and diffuse. If the size is too large, particles will start to displace mostly to the same direction and no interesting shapes will appear.

 |

**
Rate
**

 |
One of the main advantages of Simplex Noise is that it is relatively efficient in generating a smooth noise in space. However, those can also smoothly evolve over time. Rate parameter controls how fast this evolution takes place. A value of 0 means no evolution and noise will always result in the same shape for particles coming from the same location.

 |

**
Octaves
**

 |
Adds additional complexity by sampling the noise field multiple times with different sizes. This creates what is known as Fractal Noise.

The Octaves option multiplies the number of times the noise is sampled.

 |

##
Offset

This feature displaces the particles in a given direction in space. While seemingly not a very interesting feature in itself, combining multiple features together and using
[Modifiers](Modifiers.md)
 on the scale parameter make the Offset feature one of the most useful features in the Location category. In fact, most of the Location features in this page could in theory be recreated by just using Offset feature; however, it would not be a very practical way.

Property

 |
Description

 |

**
Offset
**

 |
Specifies spatial offset in meters to add to each new born.

 |

**
Scale
**

 |
Scales the size of the offset vector. Can be used with Modifiers to change particle location dynamically. By adding a Spawn Id modifier, it is ensured that the particles are distributed regularly along the vector. Please refer to
[Modifiers](Modifiers.md)
 for more information.

 |

##
Omni

This feature causes the effect to be omnipresent, in other words, environmental. This is implemented by spawning particles in a volume in front of the camera and whenever the camera moves.

Property

 |
Description

 |

**
Visibility Range
**

 |
Provides the maximum visibility range of the effect. This determines the size of the volume in front of the camera.

 |

**
Spawn Outside View
**

 |
This option is necessary to create Omni particles that can collide with surfaces before they enter the camera view. When this is set, the particles will spawn further away from the camera. This distance is determined by the particle
**
Life: time
**
 and
**
Motion: Physics
**
 values, such that as the particle falls, it will reach the view within its lifetime.

If the
**
Motion: Collision
**
 feature is also added, the particle can collide with objects outside the view volume, and not enter the view.
 |

**
Use Emitter Location
**

 |
A debugging option that fixes the view volume at the emitter's location, rather than moving it with the camera. This allows you to move around in the editor and view the Omni volume from outside.

 |

The features Location: Omni and
[Motion: Collisions](Motion.md)
 can be used together to create an omnipresent colliding effect.
By setting the feature parameters appropriately, an omnipresent environmental
effect like
rain or snow can be authored. With the addition of Motion: Collisions feature, these effects can react to collisions and stay out of indoors or other specific areas.
 For more information, see
[Tutorial - Creating an Omnipresent Colliding Effect](../../../Tutorials/Graphics/Particle%20Tutorials/Tutorial%20-%20Creating%20an%20Omnipresent%20Colliding%20Effect.md)
.

##
Sphere

This feature allows the new born particles to be randomly and uniformly distributed on a sphere surface.

Property

 |
Description

 |

**
Radius
**

 |
Specifies the radius of the sphere in meters. By default, it spawns particles on the surface of the sphere until
[Modifiers](Modifiers.md)
 are used. Using the Random modifier and setting it to 100% ensures that the particles spawn uniformly in the sphere's volume.

 |

**
Inner Fraction
**

 |
Sets the inner radius of distribution on circles. This is an easier and more precise way to distribute particles within the radius
than adding a Random modifier to the radius parameter.

 |

**
Velocity
**

 |
Specifies initial particle velocity in meters per second. Positive values allow the particles to move outwards from the center while negative values allow the particles to move inwards, toward the center.

 |

**
Axis Scale
**

 |
Enables scaling of each axis individually. Use this to create ellipsoids instead of spheres.

 |

**
Distribution
**

 |
Particles are distributed to different dimensions based on the selected parameter:

-
**
Random -
**
Particles are distributed to randomly selected dimensions.

-
**
Ordered -
**
 When selected, one Modulus field appears for each dimension available for distribution. To distribute particles along these dimensions, each of these fields must be set to a value greater than 1.
 |

##
GPU Support

All Location features are supported in the GPU pipeline, although there is no support for modifiers on the properties of the features.

##
One This Page

[Beam](#beam)
[BindToCamera](#bindtocamera)
[Box](#box)
[Circle](#circle)
[Geometry](#geometry)
[Noise](#noise)
[Offset](#offset)
[Omni](#omni)
[Sphere](#sphere)
[GPU Support](#gpu-support)
