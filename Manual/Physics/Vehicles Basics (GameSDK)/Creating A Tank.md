# Creating A Tank

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/29793891
- Page ID: 29793891
- Breadcrumb: Physics > Vehicles Basics (GameSDK) > Creating A Tank
- Parent: Vehicles Basics (GameSDK)

## Content

##
Overview

Tanks need special treatment because they are a combination of .cga and .chr files. For general information about vehicle setup, please refer to
[/docs/static/engines/cryengine-3/categories/1638401/pages/1605652](
Vehicle System
)
.

##
Sample Files

-
[/docs/static/attachments/1441827](
max_abrams.rar
)

-
[/docs/static/attachments/1441793](
ma_abrams.rar
)

##
General Setup in 3D Applications

-
The vehicle needs to
*
look
*
 down the positive y-axis (-Z for Maya).

-
The tank treads need to be skinned characters and exported as a chr
*
separately
*
 from the rest of the tank because the tank itself will be exported as a cga file.

-
Have a root node with the name of your asset and have your whole hierarchy under it.

##
Wheels Setup

Place the wheel object in the correct position. Place the wheel's pivot in the correct position (the image above shows the top view in 3ds Max on the left, Maya on the right).

Type
**
Wheel
**
 in the objects properties/UDP section (see StatCGFPhysicalize.cpp). This will refine the proxy into a cylinder shape, best optimized for this type of use. The wheel proxy must be simple enough to be recognized as a cylinder by physics.

*
Both wheels have the same proxy. The wheel on the right uses the "wheel" UDP flag.
*

Make sure your wheel proxy is attached as an element and not as a child of the mesh, otherwise you'll likely run into issues when exporting the skinned tread CHRs.

##
Tank Tread Setup

-
Create a helper in the middle of the tank tread. Give it the same name as the tank tread, plus the suffix (example:
*
tread_left_root
*
).

-
Create a 2-link bone chain for each tank tread wheel and position them like in the picture below. The first bone of the wheel needs to be named like the wheel plus the suffix (example:
*
wheel01_bone
*
). The child (terminator bone) needs to be named like the wheel, plus the suffix (example:
*
wheel01_term
*
).

-
The bones of the wheel (wheel01_bone) need to be linked to the root, which was created in the first step (tread_left_root).

-
Assign a skin modifier to the tank tread (not the wheels) and add the bones, without the terminator bones, for the weighting. Then adjust the weighting of the vertices on the tank tread.
The treads must be exported as a CHR one at a time, as they have different skeletons and will conflict on export.

##
In Sandbox

For more information please see the
[/docs/static/engines/cryengine-5/categories/23756816/pages/26214869](
Vehicle Editor
)
 article.
