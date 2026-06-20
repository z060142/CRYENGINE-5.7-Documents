# Project

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/36868302
- Page ID: 36868302
- Breadcrumb: Editor Tools > Particle Editor > Particle Effect Features > Project
- Parent: Particle Effect Features

## Content

##
Overview

Project features are used to align particle positions to other objects or constrain their motion to the environment.

The following options are available under the Project category:

##
Terrain

Projects particles to the closest point in the terrain.

##
Water

Projects particles to the closest water surface. If no water surface is found above or below a particle, then it will be forcibly killed.

##
Common Project Properties

All Project features share the same properties:

Property
 |
Description
 |

**
Spawn Only
**

 |
If enabled, particles will only get projected when they spawn. If disabled, particles will always be projected. This option restricts the movement of the particles over the object they are being projected upon.

 |

**
Project Positions
**

 |
If enabled, projects particle positions to the object they are being projected upon.

 |

**
Offset
**

 |
Only available if Project Position is activated. Allows the addition of an offset to the projected position. Offset is specified in meters.

 |

**
Project Velocity
**

 |
If enabled, projects particle velocity upon the surface that the particle is projected upon.

 |

**
Project Angles
**

 |
If enabled, this option rotates particles and forces them to align themselves to the surface that they are projected upon. Best used with free facing sprites, free facing ribbons or mesh particles.

 |

**
Align Axis
**

 |
Only available if
**
Project Angles
**
 is enabled. Specifies which axis of the particle is to be aligned to the surface that the particle is projected upon.

-
**
Forward -
**
 Forces the alignment on the forward axis. Corresponds to the X axis on meshes.

-
**
Normal -
**
 Forces the alignment on the axis sticking out of a sprite. Corresponds to the Z axis on meshes.
 |

**
Align View
**

 |
Only available if
**
Project Angles
**
 is enabled. Specifies if a second constraint is to be set to the other particle axis.

-
**
None -
**
 Avoids adding a second constraint.

-
**
Screen -
**
 Tries to align the other particle axis to the screen.

-
**
Camera -
**
 Tries to align the other particle axis directly to the camera.
This type of alignment is tentative, meaning that it will not forcibly align the axis as opposed to Align Type. Note that Align View never distorts particles.

 |

**
High Accuracy
**

 |
Performs more expensive computations to place the particle above the surface.

-
**
For Terrain
**
, this uses the size of the particle to make sure all points are above the terrain, rather than just the center.

-
**
For Water
**
, this incorporates the wave heights of the ocean, instead of the average height value.
 |

[Terrain](#terrain)
[Water](#water)
[Common Project Properties](#common-project-properties)
