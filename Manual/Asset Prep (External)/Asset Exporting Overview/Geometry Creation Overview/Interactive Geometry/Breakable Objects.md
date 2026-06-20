# Breakable Objects

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/23308020
- Page ID: 23308020
- Breadcrumb: Asset Prep (External) > Asset Exporting Overview > Geometry Creation Overview > Interactive Geometry > Breakable Objects
- Parent: Interactive Geometry

## Child Pages

- [Destroyable Objects](Breakable Objects/Destroyable Objects.md)
- [Jointed Breakable Objects](Breakable Objects/Jointed Breakable Objects.md)
- [Automatic Generation of Breakable Joints in Sandbox](Breakable Objects/Automatic Generation of Breakable Joints in Sandbox.md)
- [Boolean Destructibles](Breakable Objects/Boolean Destructibles.md)
- [Breakable Glass](Breakable Objects/Breakable Glass.md)
- [Deformable Objects](Breakable Objects/Deformable Objects.md)
- [Fractionalizing Objects Tutorial](Breakable Objects/Fractionalizing Objects Tutorial.md)
- [Jointed Destructable Object](Breakable Objects/Jointed Destructable Object.md)
- [Pre-Baked Physics](Breakable Objects/Pre-Baked Physics.md)

## Content

##
Overview

There are several methods of setting up breakable assets that the player can destroy in CRYENGINE. In this section, you can read an overview about destroyable objects in the CRYENGINE and find tutorials on creating breakable assets, 2D and 3D Procedural Breaking, and pre-baked physics. It also contains information about how to set up breakable assets in specific 3D programs, and on using the 3ds Max Procutter plugin.

##
Breakable Assets

-
[/docs/static/engines/cryengine-5/categories/23756816/pages/23308021](
Jointed Breakable Objects
)
 are structures that are built of separate pieces held together by virtual joints. Breakable Objects can also be broken up in to even smaller pieces or particles. Please see
[/docs/static/engines/cryengine-5/categories/23756816/pages/23308021](
Jointed Destructable Objects
)
 for further information.

-
[/docs/static/engines/cryengine-5/categories/23756816/pages/23308024](
Destroyable Objects
)
 (also referred to as Assembled Pieces) are structures that contain the original object and pre-created pieces that appear when the original object is destroyed.

-
[/docs/static/engines/cryengine-5/categories/23756816/pages/23308028](
Jointed Destructable Objects
)
 is a jointed breakable object that can be set up to break into smaller pieces when being detached from the joint. For example a wooden sign falls off the signpost and breaks into several planks.
Artists need to set up a breakable asset (CGF), with all the broken pieces in their initial location. Instances are not supported (pieces that share geometry and have different position/scale/orientation don't save memory). All the pieces should form the unbroken object. If required, physical constraints (they force the pieces to lose their hard connection) can be set up. The unbroken case should render faster than the individual pieces (if the material is the same, you can save some draw calls).

If needed, the designer can specify another mesh for the unbroken state (script side, in the Sandbox Editor). As this object might have lesser vertices, it should render even faster, but it will also use up additional memory. Generally, there are three reasons for this:

-
Render speed (lesser vertices).

-
Easier asset creation (gaps between the pieces).

-
Better asset look (no seams between the pieces).

##
Key Notes

It is also important to know the context of the asset, i.e; whether it's just a simple asset that the player can interact with or whether it's a special asset that triggers an event. You also need to know for example whether a sign post will remain standing, break off, or fall over completely leaving nothing stuck in the ground. Knowing how the asset is going to be used will help you set up the asset accordingly.

Another point that will help is knowing the differences between the Entities and Brush in Sandbox.

Object

 |
Used For...

 |
Description

 |

**
Brush
**

 |
*
Jointed Breakables
*

 |
The simplest form the asset can take, which means it is more optimized. It does not have the scripting overhead, but obviously this asset cannot be accessed by Flow Graph or by script.

This type needs grounding information to 'connect' it to the ground and that is taken from one of the pieces.

This piece should be assigned by either attaching it to the world with an open joint, or assigning it a mass of 0, which means it is unmovable.

Note
If this isn't assigned, the engine will assign one at random and that piece will not be moveable.

 |

**
Breakable Entity
**

 |
*
Jointed Breakables

Jointed Destructibles
*

 |
Same as a brush except it is accessible by script/Flow Graph, and has extra simulation parameters for physics simulation, and extra parameters for procedural breakability

('ground' planes, breakability index override, and crack parameters) and therefore has more overhead.

There is also a RigidBody option in the parameters which enables it to react to the player's force, otherwise it will remain static until it takes damage.

 |

**
Basic Entity
**

 |
*
Jointed Breakables
*

 |
This is a simpler version of the Breakable Entity.

 |

**
Rigid Body Ex
**

 |
*
Jointed Breakables
*

 |
This is best used for furniture that can be pushed around prior to being broken as it does not need to be 'ground aware'.

 |

**
Destroyable Entity
**

 |
*
Destroyable Objects
*

 |
This should be used for all Destroyable Objects. Other Entities and the Brush will not work for Destroyable objects.

It is possible to set a different name for the 'Main' and 'Remain' but it's not advised to do so unless the designers are fully aware. Geom Entities should be avoided for Breakable assets.

Important
It is recommended to have a naming convention for your assets because the level designer won't know how the asset has been set up.

For example: crate_big_DO for Destroyable object or crate_big_JB for Jointed breakable.

 |

##
2D Breakable Assets

This is a useful technique for structures like glass, ice plates, or walls. The technique works with sufficiently thin and flat mesh objects.

The definition of
*
sufficiently
*
 is as follows:

-
The object must be at least seven times thinner along its
*
break plane
*
 normal, than along the other 2 directions.

-
The triangles that form the surface must be, at the most, at a 15 degree angle to each other.

-
No triangle that forms a surface should be at more than a 45 degree angle from the average surface normal.

##
3D Destroyable Objects

[/docs/static/engines/cryengine-5/categories/23756816/pages/23308030](
Boolean Destructibles
)

The object internally splits up into tetrahedrons during the geometry export. In real-time, the object can be carved by another mesh object (boolean operation). This operation is computationally more intensive than pre-broken objects and 2D destroyable objects. New objects can be spawned in the created hole. If the carving process creates separate pieces, they become individual physical objects.

##
Deformable Objects

[/docs/static/engines/cryengine-5/categories/23756816/pages/23308029](
Deformable Objects
)

Deformable objects are basically cloth objects skinned to a skeleton. Unlike cloth, they are not constantly moving, but instead "freeze" in their deformed position, so they can be used to create deformable metal or other bending materials. To set up a deformable object, first make sure it is sufficiently tessellated, so the deformation looks convincing.

[/docs/static/engines/cryengine-5/categories/23756816/pages/23308021](
Jointed Breakable Objects
)

Learn about the types of breakable objects, the preparation and rules for their setup.

[/docs/static/engines/cryengine-5/categories/23756816/pages/23308024](
Destroyable Objects
)

This topic details the instructions for creating a destroyable object, along with an explanation of its parameters and properties.

[/docs/static/engines/cryengine-5/categories/23756816/pages/23308028](
Jointed Destructable Objects
)

This shows you how you can iterate on the jointed Breakable object and destroy the pieces further.

[/docs/static/engines/cryengine-5/categories/23756816/pages/23308027](
Breakable Glass
)

This topic shows you how to set up breakable glass assets.

[/docs/static/engines/cryengine-5/categories/23756816/pages/23308031](
Pre-Baked Physics
)

The pre-baked physics pipeline allows you to place a physics simulation in a 3D asset creation package, and then keyframe the data and load it into the Sandbox Editor.

[/docs/static/engines/cryengine-5/categories/23756816/pages/23308032](
Fractionalizing Objects Tutorial
)

Fractionalizing is a technique we use when we are breaking apart an asset which will be setup up for various forms of breakability.

##
Essential UDP Strings for physics properties of CGFs

[/docs/static/engines/cryengine-3/categories/1114113/pages/1310799](
UDP Settings
)

List of UDP settings (User Defined Properties) for use in Max and Maya to change Physics Properties for Objects.

[#breakable-assets](
Breakable Assets
)
[#2d-breakable-assets](
2D Breakable Assets
)
[#essential-udp-strings-for-physics-properties-of-cgfs](
Essential UDP Strings for physics properties of CGFs
)
