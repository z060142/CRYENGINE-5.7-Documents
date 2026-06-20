# Creating a Vehicle (Max)

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/29798896
- Page ID: 29798896
- Breadcrumb: Physics > Vehicles Basics (GameSDK) > Creating a Vehicle (Max)
- Parent: Vehicles Basics (GameSDK)

## Content

##
Overview

Vehicles are special geometry objects, which are driven by scripts, which also determine the functionality.

##
Sample Files

-
[/docs/static/attachments/1441795](
HMMWV.rar
)

##
General Setup

Vehicles are complex objects that need careful setup in the 3d package. Basically, the setup should be applicable to any package. Polycounts need to be carefully calculated, as extended functionality increase object (drawcall) and polycount drastically.

Important
All vehicles have to face towards +Y in the coordinate system (front looking towards up in top view).

**
Example:
**
 rotation and position of the chassis pivot:

Every moving part needs to be a separate object within the 3d package. The pivot needs to be set correctly within the 3d package, as the engine will use the object's individual pivot to make transformations.

##
Linking

Linked objects have the advantage that only the root needs to be selected and exported. All child nodes will automatically be exported. The name and pivot will be derived from the root joint.

-
Use a dummy as the root, make sure rotation is 0/0/0 and transformation in world space is 0/0/0.

-
All attachments (like doors, spare wheels, glasses, exploding fuel canisters, etc) have to be linked to the main object which is called "hull". It can be the chassis of a car, the fuselage of an aircraft, or the hull of the ship.

*
General rule: If the chassis moves in the 3d application, the parts should move too.
*

-
LOD's can also be linked to the respective LOD0. i.e. $lod1_hull to hull; $lod1_wheel1 and $lod2_wheel1 to wheel1.

##
Moving Parts

Every moving part needs to be a separate object within the 3d package. The pivot needs to be set correctly within the 3d package because the engine will use the object's individual pivot to make transformations.

##
Naming Conventions

Naming is needed for scripts to identify the objects and interact with them. The examples below reflect the asset names used in Crysis - they can be different for other games.

-
The parts need to be named in a logical way (chassis, wheel1, wheel2.., turret) as the objects will be referenced later in the Vehicle Editor and scripts.

-
The scripts for damaged versions of vehicles expect an asset which contains the name of the intact model, plus the suffix "_damaged" (hull -> hull_damaged, door_left_1 -> door_left_1_damaged, etc).

##
Wheels Setup

-
Place the wheel object in the correct position.

-
Place the wheel's pivot in correct position. (the picture below shows top View in 3ds Max.

-
Type "Wheel" in the objects properties. (the picture below shows the 3ds Max Objects property window)
The wheel proxy must be simple enough to be recognized as a cylinder by physics. Support for an additional detailed proxy (if the wheel's shape demands it) will follow.

##
Material Setup (Proxies, Breaklights, Damage Lights, Max > mtl File)

-
Create one Multi/Sub-Object Material in 3ds Max which includes all materials associated with the asset.

-
You must use Crytek shader in the max files to set up the material file for export.

-
In the 3d application, the proxy material must have "Physicalize" turned on and the Value set to "Physical Proxy (NoDraw)". For further information, please see:
[/docs/static/engines/cryengine-5/categories/23756816/pages/23308590](
Creating Material Files
)
.

-
Operational break lights, headlights, and different indicators on the dashboards have to be on different material IDs, so code can identify them, and deal with them (like setting glow value from code for example).

##
Physics Setup

Vehicles are complex objects and simplifying collision calculation is very important for performance. Therefore it is advisable to create two physics proxies. one is for collision with the terrain and characters and one for collision with bullets, grenades etc...

-
Vehicles must have a very simple physics proxy which is called "hull_proxy". This is a separate, collision object for character and terrain collision. It should be slightly larger than the enclosed detailed proxies. Polycount for this proxy must be fairly low. For land-based vehicles like cars, tanks and hovercrafts, the proxy should not have parts sticking out in places which can frequently bounce into and slide across walls, like the front and side parts of a truck cabin.

-
For collision detection of bullets, grenades, the hull, etc... - object should contain a more detailed embedded physics proxy. It should resemble the shape of the vehicle more closely, but small elements could be left out. It should certainly include cutouts, like holes for the doors, windows, and other open areas.

-
Attached parts like doors and bumpers need their own simplified proxy in case the embedded proxy is too detailed and calculation heavy for terrain/water collision. In this case, add the suffix "_proxy" to the object name.

-
Proxy material must have "Physicalize" turned on in the shader options within the 3d application (please refer to the Material setup section); the type should be set to "Physical Proxy (NoDraw)".

-
LODs do not have to contain proxies, as it will be used from the LOD0. In versions with lower performance settings, where LOD1 is used as the base mesh, the proxy from the High Spec LOD0 is taken into account.

-
Damaged model has to contain its own proxy to follow deformed / different geometry (LODs do not need a proxy)

##
LODs

-
For general information refer to the
[/docs/static/engines/cryengine-5/categories/23756816/pages/26215356](
Creating LODs
)
 page, for specialties in vehicle creation, please see below.

-
Because of the asset complexity it is recommended to link subsequent LOD's to the LOD0 version and include the LOD0 name in the suffix (i.e. "hull" has LODs linked to it called $lod1_hull; $lod2_hull).
You can have a different number of LOD levels for different parts of the vehicle. i.e; the chassis of a car may have 4 LOD levels whereas the door, being a more simple object, has only 2.

LOD switching is based on screen size, smaller objects will switch earlier than big ones. Keep this in mind when doing LOD's.

##
Vehicle Damage Model

The damage model for vehicles is a separate asset which replaces the vehicles on destruction. It can be a simple static model or a complex pre-broken object.

-
It replaces the original model and therefore needs a separate proxy model.

-
The damaged objects needs the suffix "_damaged" to its name (like hull -> hull_damaged, door_left_1 -> door_left_1_damaged, etc).

-
To have some extra debris (if one object is breaking apart to more debris parts), you can add further objects to the damaged model. These should be called the object's name + "
*
debris
*
_" suffix. (hull -> hull_debris_1, hull_debris_2, etc...) These will spawn and fly away from the blast when the vehicle explodes.
It happens only when the SpawnDebris damage behavior is set on a vehicle. Please refer to the Sandbox
[/docs/static/engines/cryengine-5/categories/23756816/pages/26214869](
Vehicle Editor
)
 guide for this.

-
The damage model can also include LOD's.
To manage objects easier, it is recommended to sort LOD's via layers.

##
Animations

-
In 3ds Max, the TBC controller for the animations (translation and rotation) must be used. Any other controller will create unpredictable results. Please refer to the Animation guide for more details!

-
Animations have to be saved as .anm files. To save certain animations, you must select the objects you would like to save the animations of, and add to the export list. If you want to animate the doors closing, then you have to export with only the doors in the export list. File names have to start with the object names + the animation's name. If the vehicle's main file is called car.cga, then the animation should be called something like car_door_opening.cga for example.

-
Once you have animated your objects, you have to export the default state. It has to be called something like the object .cga file (if the object is tank.cga then the default animation has to be tank.anm). This default state has to contain all the animated objects.

-
Please see exporter documentation for further exporting features and parameters!
You can test if your animations are exported and playing correctly by loading the vehicle to the character editor, and clicking on the animation on the right.

##
Position Helpers for Characters

-
Character sitting and enter positions need to be indicated with position helpers in the 3D package (i.e. Dummy objects in 3ds Max).

##
Export Options

Vehicles are very complex objects and can cause major problems if the exporting is not done carefully. To avoid complications in the scene:

-
Add the root node to the export window and check Custom File Name. Choose an appropriate filename and export.

-
Vehicles except Tanks: export all parts as one cga. uncheck "file per Node" and "merge all nodes".

-
Tanks: export all parts except the tank treads together as one cga.uncheck "file per Node" and "merge all nodes"

-
Tank Treads: Export right and left tank tread separately as chr. uncheck "merge all nodes"; check "file per node" if you like. Choose only the tank treads object, not the wheels or the bones.

-
Choose the top node and relevant helpers and export only these. The linked children will be exported automatically.
Setting up named selection sets can help you in re-exporting your assets.

##
Setup in Sandbox

In order to work properly, a vehicle script is required. Otherwise the vehicle can only be judged visually as a Geom Entity.

-
Drag and drop the item from the entity section in the RollupBar or the Entity Library (in the Database View) into the level.

-
If no script is available, drag and drop the asset from the Geom Entity section in the RollupBar into the level.
Please refer to the
[/docs/static/engines/cryengine-3/categories/1114113/pages/1048909](
Vehicle Editor
)
 section for information on the vehicle editor.

##
Debugging

There are some useful commands you can use to check your asset and see if it works as expected. Some of these are listed below (you can turn off any of these drawing modes by entering 0 after the command instead of the number given here).

CVar

 |
Description

 |

**
p_draw_helpers 1
**

 |
Used to check physique proxies.

 |

**
e_debug_draw 1
**

 |
Used to check LOD's. Using this variable you can see the bounding box of the object, see the name of it,

number of LOD levels available for the object, the one which is currently displaying, and the polycount of the current LOD.

 |

**
e_debug_draw 2
**

 |
Displays polycount only for the given LOD.

 |

**
e_debug_draw 3
**

 |
Different LOD levels are represented in different colors, so you can clearly see the transition between two LOD levels.

Also see the total number of LOD's and the one currently displaying. Blinking one shows up if the given object does not have an LOD.

 |

**
e_debug_draw 5
**

 |
Shows how many material IDs are in use on the given objects.

 |

**
e_lod_min 0 - 6
**

 |
Shows the specified LOD number as LOD0 - very handy for debugging LOD's in the engine.

 |

[#sample-files](
Sample Files
)
[#general-setup](
General Setup
)
[#export-options](
Export Options
)
[#setup-in-sandbox](
Setup in Sandbox
)
[#debugging](
Debugging
)
