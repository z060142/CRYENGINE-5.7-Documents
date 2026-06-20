# Deformable Objects

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/23308029
- Page ID: 23308029
- Breadcrumb: Asset Prep (External) > Asset Exporting Overview > Geometry Creation Overview > Interactive Geometry > Breakable Objects > Deformable Objects
- Parent: Breakable Objects

## Content

## Overview

Deformable objects are basically cloth objects skinned to a skeleton. Unlike cloth, they are not constantly moving, but instead "freeze" in their deformed position, so they can be used to create deformable metal or other bending materials. To set up a deformable object, first make sure it is sufficiently tessellated, so the deformation looks convincing. A deformable object consists of two nodes: The render mesh, physics mesh, and the skeleton. The skeleton is the actual deforming object, the rendermesh and physics mesh are following its deformations in a similar fashion similarly to how a skinned character mesh is following bones.

The skeleton is not an actual bone setup in a DCC package, but simply a normal geometry mesh. Its shape has to be similar to the rendermesh. The way the mesh is following the deformation of the skeleton is controlled through the position of the skeleton mesh vertices. If the skeleton vertices are outside of the render mesh, they are considered attached to the object and won't be deformed. If they are inside of the rendermesh, the mesh will be "skinned" to them and follow their deformation. This can be used to control the degree of bending (i.e. with a deformable box, pulling the skeleton vertices at the edge of the box outside of the rendermesh will make this edge "stiff" or fixed, while the rest of the mesh is following the deformation completely).

![Image](https://www.cryengine.com/docs/static/attachments/23994756)

### General Parameters

There are several parameters for controlling the skeleton behavior. They have to be entered into the skeleton node's user defined properties (in 3dsmax).

**Property** | Description
--- | ---
**stiffness=VALUE** | Resilience to bending and shearing (default 10)
**hardness****=VALUE** | Resilience to stretching (default 10)
**max_stretch****=VALUE** | If any edge is stretched more than that, its length is re-enforced. max_stretch = 0.3 means stretched to 130% of its original length (or by 30% wrt to its original length). default 0.01
**max_impulse****=VALUE** | Upper limit on all applied impulses. default skeleton's mass*100
**skin_dist****=VALUE** | Sphere radius in skinning assignment. Default is the minimum of the main mesh's bounding box's dimensions (see below)
**thickness****=VALUE** | Sets the collision thickness for the skeleton. The skeleton collides as a cloth object, i.e. it has virtual spheres with this radius around each vertex, and it has less priority than the geometries it collides with (it will un-project itself unconditionally from them). It collides with static and rigid body objects only. It will collide with parts of the same entity it belongs to, except the one it skins (this way it's possible to set up safety shells inside the object to prevent excessive deformations). Setting thickness to 0 disables all collisions.
**notaprim****=VALUE** | A general physics proxy parameter, it keeps the physics mesh from being turned into a primitive (box, cylinder). This is especially important for deformable objects - the skeleton being a primitive will cause a crash!
**explosion_scale=VALUE** | Used to scale down the effect of explosions on the deformable. This lets you have visible deformations from bullet impacts, but without vastly distorting the object too far with explosions.

#### Explanation of the skinning process

For each main mesh's vertex (both physics and render independently, if they are different) a sphere with a fixed radius is created around it and is checked for collisions with the skeleton mesh. Based on the collision region, the average collision normal is computed and the sphere is 'moved' along it until it finds the touch point. This point is then considered the main mesh vertex's projection on the skeleton, and it's later tied to it. If the first sphere test finds no collisions, the code does a second check, with a sphere 3 times larger. The radius of this sphere can be adjusted with skin_dist.

![Image](https://www.cryengine.com/docs/static/attachments/23994755)

### Setup in 3DS Max

##### Example Asset

- [deformable.rar](/docs/static/attachments/23994746)

##### Setup

- Start out by modeling your asset as usual.
- Once finished, create the skeleton. Be sure to assign a new sub material to this skeleton that is set to Default physicalization. The skeleton mesh has to be named skeleton_nodename, with "nodename" being the name of the render mesh that the skeleton mesh is linked to. Make sure the parts of the skeleton that you want deformed are inside the render mesh.
- Now enter the properties you want in the object properties. The values for the example metal barrel are:
- notaprim
- skin_dist=0.2
- thickness=0.01
- stiffness=0.1
- max_stretch=10
- mass=0.5
- Now create your physics proxy. Make sure that it is tessellated enough, but remove the smaller details that don't need deforming.
![Image](https://www.cryengine.com/docs/static/attachments/23994754)
- You should now be ready for export so open up the Crytek export dialog and choose a.cgf file and click "Export".

### Setup in Maya

##### Example Asset

- [ma_deformable.rar](/docs/static/attachments/23994752)

##### Setup

- Start out by modeling your asset as usual.
- Once finished, create the skeleton. Be sure to assign a new sub-material to this skeleton and make sure that is set to Default physicalization. The skeleton mesh has to be named skeleton_nodename, with "nodename" being the name of the render mesh that the skeleton mesh is linked to. Make sure the parts of the skeleton that you want deformed are inside the render mesh.
- Now enter the properties you want in the UDP. Be sure to select the skeleton group. The values for the example metal barrel are:
- notaprim
- skin_dist=0.2
- thickness=0.01
- stiffness=0.1
- max_stretch=10
- mass=0.5
- Now create your physics proxy. Make sure that it is tessellated enough, but remove the smaller details that don't need deforming.
![Image](https://www.cryengine.com/docs/static/attachments/23994753)
- You should now be ready for export, so open up the Crytek export dialog and choose a .cgf file and click "Export". Do not forget to setup your materials and then click "Generate Material Files."
![Image](https://www.cryengine.com/docs/static/attachments/23994751)

### Setup in Sandbox

- The Asset must be placed as a Basic Entity or a Brush for static objects, with a Mass of at least 1. The higher the mass, the harder it is to deform.
- Be sure that your Material proxy settings are set to NoDraw.
- Now shoot at it! You should get the same results as below:

![Image](https://www.cryengine.com/docs/static/attachments/23994748)![Image](https://www.cryengine.com/docs/static/attachments/23994749)

[General Parameters](#general-parameters)[Setup in 3DS Max](#setup-in-3ds-max)[Setup in Maya](#setup-in-maya)[Setup in Sandbox](#setup-in-sandbox)
