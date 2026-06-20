# Angles

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/36868243
- Page ID: 36868243
- Breadcrumb: Editor Tools > Particle Editor > Particle Effect Features > Angles
- Parent: Particle Effect Features

## Content

##
Overview

Angles feature provides the ability to rotate and orient particles in a component. It allows users to align, rotate or orient particles in a specific space or on two and three dimensions.

On this feature, values are provided in degrees, rotations are in a counterclockwise direction and spin values are in degrees per second

The following options are available under the Angles category:

##
Align

Allows users to align particles in a space with certain conditions. It is best used with free facing sprites, free facing ribbons or meshes.

Property

 |
Description

 |

**
Particle Axis
**

 |
Specifies on which axis the Align feature should be enforced:

-
**
Forward -
**
 Forces the alignment on the forward axis. Best used with velocity alignment. Corresponds to the X axis on meshes.

-
**
Normal -
**
Forces the alignment on the axis sticking out of a sprite. Best used for camera alignment. Corresponds to the Z axis on meshes.
 |

**
Align Type
**

 |
Specifies the type of alignment that will be forced on the selected particle axis:

-
**
Screen -
**
 Forces the selected axis to point to the screen.

-
**
Camera -
**
 Forces the selected axis to point directly to the camera.

-
**
Velocity -
**
 Forces the selected axis to point in the direction the particle is moving. If particle is not moving, constraint is not enforced.

-
**
Parent -
**
 Forces the selected axis to align itself with the parent particle or emitter. For more information about parent child relationships, please check the
[SecondGen](SecondGen.md)
 section.

-
**
World -
**
Aligns the selected axis to the world vector specified in Axis.
 |

**
Axis
**

 |
When Align Type is set to Parent or World, Axis fields appear. The values on these fields specify on which axis of the parent the feature to be aligned. By default, it aligns to the parent's up direction.

 |

**
Align View
**

 |
When the Align Type is either Velocity or Parent, Align View option appears at the bottom of the feature properties list. It allows a second constraint to be added. This constraint is applied to the other particle axis:

-
**
None -
**
 Does not add a second constraint.

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
As opposed to Align Type, this type of alignment is tenatative; meaning it will not forcibly align the axis. Align View never distorts particles.

 |

##
Rotate2D

Rotate2D feature allows a particle to rotate in two dimensions. It also enables the user to rotate particles relative to the viewer.

Property

 |
Description

 |

**
Initial Angle
**

 |
Base angle at which all particles will be spawned. For example, if the Initial Angle is set to 20, all particles will spawn rotated 20 degrees to the right. Negative values makes the particles spawn rotated to the left.

 |

**
Random Angle
**

 |
Random variance of the initial angle. For example, if Initial Angle is set to 20 and Random Angle to 10, particles will spawn with a random angle set between 10 and 30 degrees to the right (between 20 minus 10 and 20 plus 10). If Initial Angle is set to 0 and Random Angle is set to 90, particles will spawn at random angles between -90 and +90, meaning they will spawn randomly to the right or left of the initial spawn point.

 |

**
Initial Spin
**

 |
Base spin rate at which all particles will be spawned. For example, if Initial Angle is set to 20 and Initial Spin is set to 30, the particles will spawn spinning at 20 degrees to the right; after one second, they will have a rotation of 50 degrees and after 2 seconds, they will have a rotation of 80 degrees.

 |

**
Random Spin
**

 |
Similar to the Random Angle, this option is a variance randomizer of Initial Spin.

 |

##
Rotate3D

This feature allows a particle to rotate on three dimensions using Euler rotation. This allows particles to free spin or orient themselves in the world space rather than moving relative to the camera. All parameters have an X, Y and Z axes that corresponds to the Euler axis of rotation.

Property

 |
Description

 |

**
Initial Angle
**

 |
Base angle at which all particles will be spawned. For example, if the Initial Angle is set to 20, all particles will spawn rotated 20 degrees to the right. Negative values makes the particles spawn rotated to the left.

 |

**
Random Angle
**

 |
Random variance of the initial angle. For example, if Initial Angle is set to 20 and Random Angle to 10, particles will spawn with a random angle set between 10 and 30 degrees to the right (between 20 minus 10 and 20 plus 10). If Initial Angle is set to 0 and Random Angle is set to 90, particles will spawn at random angles between -90 and +90, meaning they will spawn randomly to the right or left of the initial spawn point.

 |

**
Initial Spin
**

 |
Base spin rate at which all particles will be spawned. For example, if Initial Angle is set to 20 and Initial Spin is set to 30, the particles will spawn spinning at 20 degrees to the right, after one second they will have a rotation of 50 degrees, and after 2 seconds they will have a rotation of 80 degrees.

 |

**
Random Spin
**

 |
Similar to the Random Angle, this option is a variance randomizer of Initial Spin.

 |

##
GPU Support

As GPU particles do not currently store a rotation angle, this feature is not supported on the GPU.

[Align](#align)
[Rotate2D](#rotate2d)
[Rotate3D](#rotate3d)
[GPU Support](#gpu-support)
