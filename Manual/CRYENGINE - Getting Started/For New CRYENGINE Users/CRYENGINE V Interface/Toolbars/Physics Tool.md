# Physics Tool

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/24283805
- Page ID: 24283805
- Breadcrumb: CRYENGINE - Getting Started > For New CRYENGINE Users > CRYENGINE V Interface > Toolbars > Physics Tool
- Parent: Toolbars

## Content

##
Overview

The Physics tool is a useful tool for testing out the physics
of
your
objects. This is an extension of the AI/Physics mode, which allows the user to interact with placed entities in the world without entering game mode.

To use this tool, objects must be a physical entity of some sort, e.g: Basic Entity, Rigid Body, Characters, Vehicles etc.

##
Location

This tool can be found on the
**
Physics
**
 toolbar, which you can add to the UI by right-clicking in the toolbar area of the editor.

The Physics tool is the 4th button in the highlighted red toolbar.

Also you need the
**
Game
**
 toolbar active so you can enable AI/Physics mode.

![Image](https://www.cryengine.com/docs/static/attachments/28881126)

##
How to use

Once you have both toolbars active on the UI:

-
Activate the AI/Physics mode (highlighted in
blue

above). This puts the editor into simulation mode.

-
Press the Physics Tool button to enable the manipulation mode (highlighted in
red
above).
Now you can select physicalized objects in the scene and interact with them.

##
Controls

Using the
**
LMB
**
 alone or in combination
with
**
Ctrl
**
 and
**
Shift
**
, we can manipulate objects in different ways.
Depending on where you "grabbed" the object, this will be its pivot point (examples will be given later). Once an object has been selected, it will render the physics proxy on the object to allow you to see the physics mesh. Upon release the object will return to normal render mode.

Input
 |
Name
 |
Description
 |

**
Hold LMB
**
 |
Pinch
 |
Grab the object underneath the mouse cursor and have full 360 degrees no movement restrictions. The object will be completely physicalized and will be attached to the mouse until you let go of LMB.

 |

**
Hold
**
Ctrl+
**
LMB
**
 |
Pinch Axis Locked
 |
Grab the object underneath the mouse cursor and your movement of the object will be locked to the X and Y planes only, in relation to the Viewport. (Its rotation is locked, but translation isn't. T
he object will not spin.
)

 |

**
Hold Shift+LMB (Then release)
**
 |
Fire mode
 |
This mode turns the action of the mouse cursor into a
**
projectile
**
. The longer you hold down
**
Shift
**
, the more the "impulse" of this projectile will build up. The maximum level of buildup is reached after holding down
**
Shift
**
 for 3 seconds.

The buildup of "impulse" is reflected by spawning a red sphere under the mouse cursor. The longer you hold Shift and
**
LMB
**
, the bigger the red ball gets to "preview" the impulse being applied.

To "fire" the projectile, release the
**
LMB
**
 and the impulse will be applied in the direction of the camera.

-
If you want to interact with the object gently, quickly release the
**
LMB
**
 to apply a small impulse.

-
Holding
**
Shift
**
until maximum impulse is enough power to send the Hmmwv (2500kg) flying through the air!
 |

When the object selected is
active, it's
bound to the mouse via a constraint that links them together. If you flick the object around while still holding the mouse, you'll see a thin blue line that represents the link. This link has a stretchy (rubber band) component that allows some freedom of movement at high speeds. Once deselected the link is removed. It's only temporarily created upon selection and is destroyed afterwards.

##
Usage

This tool can be used to test a variety of physicalized objects.
Above we cover the interaction modes. These apply to all object / entity types, but there are also more specific controls for things like cloth and vegetation.

##
Grabbing cloth

Hold
**
LMB
**
 to select a vertex in the mesh and pull the cloth around. This will simulate the physicalization of the cloth. Dragging the cloth entity beyond its physical limits (stretching it too far) is possible and doesn't cause any problems. (It just looks odd; this is only for testing!)
 Again, holding
**
Ctrl+LMB
**
 will lock the axis and holding
**
Shift+LMB
**
 will let you fire a projectile at the cloth.

##
Vegetation

Again using all 3 modes above, we can interact with vegetation (providing your asset is configured with touch bending). You can pull the leaves around or fire a projectile into the crown to simulate the movement of the palm fronds (if your asset is a palm tree).

Also with the projectile mode, we can break a tree trunk so long as we apply enough impulse to break (
providing your asset is configured with a breakable trunk).

##
Characters

CRYENGINE Sandbox also supports the interaction with characters/AI. Using all 3 tool combinations, we can move and shoot the character's joint/skeleton to test their reactions when the impulses are applied.

##
Technical information

The following section explains how the implementation is handled, depending on the entity class you are trying to interact with.

-
Pulling is handled by adding a constraint between an entity and an invisible 0-mass rigidbody (created internally), except for cloth and actors. Cloth uses cloth-specific vertex attachment and actors use a temporary 0-length rope (since they don't support constraints) with kinematic (0-mass) rigidbodies.

-
For non-static objects hits (fire mode) use a general impulse interface (actors also add the same impulse to the physicalized character skeleton, if present). For static objects, a temporary fake bullet particle is created and launched. This allows it to interact with breakable vegetation.

##
CVars

There are some associated Cvars that control the velocity / pressure etc.. but these are for reference only. There is no need to modify these.

Cvar/Command
 |
Description
 |

ed_PhysToolHitVelMin
 |
Minimal velocity in insta-hit mode
 |

ed_PhysToolHitVelMax
 |
Maximal velocity in insta-hit mode
 |

ed_PhysToolHitProjMass
 |
Projectile mass in projectile hit mode (on statics)
 |

ed_PhysToolHitProjVel0
 |
Minimal projectile velocity in projectile hit mode (on statics)
 |

ed_PhysToolHitProjVec1
 |
Maximal projectile velocity in projectile hit mode (on statics)
 |

ed_PhysToolHitExplR
 |
Hit explosion radius
 |

ed_PhysToolHitExplPress0
 |
Hit explosion minimal pressure
 |

ed_PhysToolHitExplPress1
 |
Hit explosion maximal pressure
 |

[Location](#location)
[How to use](#how-to-use)
[Controls](#controls)
[Usage](#usage)
[Technical information](#technical-information)
