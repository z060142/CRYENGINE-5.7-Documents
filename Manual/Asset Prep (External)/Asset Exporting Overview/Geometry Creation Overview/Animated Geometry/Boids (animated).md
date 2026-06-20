# Boids (animated)

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/23308008
- Page ID: 23308008
- Breadcrumb: Asset Prep (External) > Asset Exporting Overview > Geometry Creation Overview > Animated Geometry > Boids (animated)
- Parent: Animated Geometry

## Content

[Image: /docs/static/attachments/29934053]

##
Overview

##
Sections

Boids are flocks of characters that play a few animations. These characters are usually birds, fish, insects, etc.

You can find out more about setting up Boids in Sandbox here:
[/docs/static/engines/cryengine-5/categories/23756816/pages/29796926](
Boids Entities
)
.

[#sections](
Sections
)
[#rigging-the-characters](
Rigging the Characters
)
[#animation](
Animation
)
[#entity-properties](
Entity Properties
)

##
Rigging the Characters

There are few boid requirements:

-
Must be a skinned character.

-
LOD's (especially LOD1 for the ragdoll).
CRYENGINE 3.5 - LOD's in CHR's
The skin with LOD's needs to be re-exported from DCC tools as a .skin. LOD's in CHR's are not supported any more.

Animations also need to be re-exported/imported through the
[/docs/static/engines/cryengine-5/categories/23756816/pages/29450423](
Animation Compression Editor
)
 and Animation Importer tool as well.

Simple boids like insects or fish can have one single bone and point to null animations.

##
Animation

There are three animations boid characters use or require:

-
"swim_loop"

-
"fly_loop"

-
"landing"
Don't forget that each boid character needs a CAL file that points to its animations. As you see below, these three animations will be slightly scaled according to the speed of the boid.

##
Entity Properties

 |
**
Boid
**

 |
 |

**
n
**

 |
Count

 |
**
[FLOAT, 10]
**
 - The number of characters in the group

 |

**
n
**

 |
Mass

 |
**
[FLOAT, 10]
**
 - The mass of one character in kg

 |

**
?
**

 |
Model

 |
**
[RELATIVE PATH]
**
 - The CGA model you created

 |

**
n
**

 |
Size

 |
**
[FLOAT, 1]
**
 - The scale of the characters in the group

 |

**
n
**

 |
SizeRandom

 |
**
[FLOAT, 0]
**
 - Random size multiplier

 |

**
n
**

 |
gravity_at_death

 |
**
[FLOAT, -9.81]
**
 - Gravitational impulse applied to a member of the group on death

 |

 |
**
Flocking
**

 |
 |

**
n
**

 |
AttractDistMax

 |
**
[FLOAT, 20]
**
 - The maximum distance from the boid in meters (radius) wherein it will be attracted to another

 |

**
n
**

 |
AttractDistMin

 |
**
[FLOAT, 5]
**
 - The minimum distance from the boid in meters (radius) wherein it will repel others

 |

**
?
**

 |
EnableFlocking

 |
**
[BOOL, False]
**
 - Enable/Disable flocking, when disabled, every boid will be on his own

 |

**
n
**

 |
FactorAlign

 |
**
[FLOAT, 0]
**
 - A multiplier effecting the coherency of the aligned direction of the boids

 |

**
n
**

 |
FactorCohesion

 |
**
[FLOAT, 1]
**
 - A multiplier effecting how strong the attraction is for the group to stay together

 |

**
n
**

 |
FactorSeperation

 |
**
[FLOAT, 10]
**
 - The strength of the force repelling the boids when they are in another's AttractDistMin radius

 |

**
n
**

 |
FieldOfViewAgle

 |
**
[FLOAT, 250]
**
 - Each boids angle of sight (cone) wherein he can see other boids

 |

 |
**
Movement
**

 |
 |

**
n
**

 |
FactorAvoidLand

 |
**
[FLOAT, 10]
**
 - How strong of a force is applied for them to avoid land

 |

**
n
**

 |
FactorHeight

 |
**
[FLOAT, 0.4]
**
 - A lower value means more vertical movement, a higher value, more horizontal movement

 |

**
n
**

 |
FactorOrigin

 |
**
[FLOAT, 0.1]
**
 - How strong the boids attraction to the origin point of the boids system is

 |

**
n
**

 |
FactorRandomAcceleration

 |
**
[FLOAT, 2]
**
 - Random acceleration multiplier

 |

**
n
**

 |
HeightMax

 |
**
[FLOAT, 20]
**
 - Maximum height (meters) boids will travel from the terrain (water clamps fish)

 |

**
n
**

 |
HeightMin

 |
**
[FLOAT, 2]
**
 - Minimum distance (meters) boids will come to the terrain

 |

**
n
**

 |
MaxAnimSpeed

 |
**
[FLOAT, 1.7]
**
 - Multiplier, the maximum deviation allowed from the original animation speed. (Anim speed scales based on boid speed)

 |

**
n
**

 |
SpeedMax

 |
**
[FLOAT, 8]
**
 - Maximum amount (meters/sec) the boids can move

 |

**
n
**

 |
SpeedMin

 |
**
[FLOAT, 2]
**
 - Minimum amount (meters/sec) the boids can move

 |

 |
**
Options
**

 |
 |

**
?
**

 |
Activate

 |
**
[BOOL, False]
**
 - Whether or not the boids system is activated in the game

 |

**
?
**

 |
FollowPlayer

 |
**
[BOOL, False]
**
 - When enabled the player will be the origin of the boids system, and it's box the radius

 |

**
?
**

 |
NoLanding

 |
**
[BOOL, False]
**
 - When enabled the boids will not attempt to land (above water only)

 |

**
?
**

 |
ObstacleAvoidance

 |
**
[BOOL, False]
**
 - The boids will occasionally cast rays in their flight direction to navigate around objects (more resource usage)

 |

**
n
**

 |
Radius

 |
**
[FLOAT, 20]
**
 - Distance from the origin (meters) that the boids attempt to stay within

 |

**
n
**

 |
VisibilityDist

 |
**
[FLOAT, 20]
**
 - Distance from the origin (meters) to update boids within, to be safe, should be 2 times the radius they move within

 |
