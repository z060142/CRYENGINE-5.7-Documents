# CAT Bones Proxy and Ragdoll Setup

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/26214946
- Page ID: 26214946
- Breadcrumb: Tutorials > Digital Content Creation > Autodesk 3DS Max Tutorials > Tutorial - Setting up a CAT Rig for CRYENGINE in 3ds Max > CAT Bones Proxy and Ragdoll Setup
- Parent: Tutorial - Setting up a CAT Rig for CRYENGINE in 3ds Max

## Content

##
Overview

In this tutorial we will cover the process of setting up the CAT Rig with proper physical proxy's. We are going over some CAT specific things, later on we will explain the process of setting up a ragdoll for our mesh.

This tutorial relies on assets used in the GameSDK Sample Project. We recommend that you download this from the
**
[Asset Database](https://www.cryengine.com/marketplace/product/crytek/cryengine-gamesdk-sample-project)
**
, import it into your Launcher, start it from there and then create a new level.

See
**
[this page](/docs/static/engines/cryengine-5/categories/23756816/pages/44963099)
**
 to find out how to import a project to your Launcher. (The default folder for the GameSDK Sample Project when downloaded is
`
**
C:\Program Files (x86)\Crytek\CRYENGINE Launcher\Crytek\gamesdk_<XXX>\GameSDK
**
`
).

This folder will be referred to in this tutorial as the "GameSDK folder".

##
Setting up Custom Mesh Bones in CAT

If we want to have any collision for our character in CRYENGINE we need to setup a physicalized hitbox. For this system we are using the CAT bones to define the hitbox for the engine. The shape for the bone can be manipulated to fit the shape of the mesh. For the manipulation we are using the custom bone option in CAT.

In the
**
Bone Setup
**
 section in every bone you will have this checkbox where you can enable and disable the custom mesh function.

*

*
*

Pic1: Bone Settings with Use Custom Mesh option
*

To edit an existing bone you simply put an
**
Edit Poly
**
 modifier on top. This allows the customization of the bones, its also possible to append a completely new geometry and deleting the old one. Keep in mind to have a clean topology, no flipped faces or open edges, this can cause errors in the engine. When done with this step, collapse the modifier stack and you will have the new appearance of the custom bone.

There is a bug in 3dsMax and CAT: collapsing the
**
Edit Poly
**
 modifier can cause a rotation of the bone, if that's the case and you have this bug simply press
**
Ctrl+Z
**
 and repeat collapse, this should fix the issue)
The ragdoll and the physic proxys are the same shape.

-
To create the proxy's we don't need every single bone.

-
The geometry should be very lowpoly and it should roughly fit around the mesh/character.

-
For a starting point your mesh should be in the binding position.

-
Make sure that all the models are NOT linked to anything.
Let's start creating custom bones for physics proxy.

We are starting with the head of our character. Click on the head bone and go to the
**
Bone Setup
**
 section and check the
**
Use Custom Mesh
**
 checkbox. When ticked go to the
**
Modify Panel
**
 and add an
**
Edit Poly
**
 modifier on top. Now we have to customize our polygon to fit the shape of the head. Choose very simple geometry, a box should be enough for this purpose. When done click on
**
Collapse To
**
and now we have our
**
Bone Object
**
 back with all the settings and the
**
Use Custom Mesh
**
 box ticked. You can toggle it on and off to switch between both states the default and the custom mesh for the bone.

Go through every bone that needs to be physicalized and generate a custom mesh. Try to match the base geometry as good as possible but keep it at a very low resolution, also avoid open faces and twisted geometry.

If you are done, the setup should be similar like this in the Picture below. Always use the
**
Edit Poly
**
 modifier to scale, rotate or translate your bones, do not scale the bone itself, all bones in the main skeleton should be non-scaled.

*

*
*

Pic2: Custom mesh bone and layer setup
*

##
Creating Physic Proxy's

Its not necessary to physicalize every bone in your skeleton, but every bone that will have physical behavior requires an empty node, this can be any object. It´s not important where its located in the scene. The very important thing is the naming convention. It must have the same name as your selected bone plus a space and the suffix
**
phys
**
, e.g. "jaw_bone" phys mesh (for collision/ragdoll/hit detection) must be name "jaw_bone phys".

Before we start to build the physics node, make a new layer in the Layer Explorer and call it "Phys" for a better overview.

Let's start with the headbone. First set your bone settings to
**
Use Custom Mesh
**
. Next step is to create the empty node in this case we are creating a simple box, but you can create whatever you like. The location of this box it not important, because it has just the node function for the bone. In this case we place it on top of the head bone so we can easily see which bone belongs to which node.
**

**

CRYENGINE looks for the naming convention. It is really important in this step to name it the right way.
We call this box "headbone phys". This box will not shown up in the engine it's just an empty node which stores information about the bone it's linked to. What you will see in the engine is the head bone and it's custom mesh volume as a physics proxy.

-
The bones will have their shapes and masses taken into account, so the skeleton should be physically valid in order to behave valid.
*

*
*

Pic3: Headbone phys object box
*

Repeat this step until all required bones have this setup. Important is that all the physics bones have the "
**
phys
**
" suffix
**

**
(notice the space in front of "phys"!), otherwise the Engine can't read them.

*

*
*

Pic4: Finished setup with all bones
*

To export to the
**
CRYENGINE Exporter
**
 and select the CHAR mesh and add it to the
**
Geometry Export
**
 and click the
**
Export
**
 button.

##
Testing the proxy in CRYENGINE

Open up the CRYENGINE Editor and open the Create Object tool. Click
**
Entity -> Physics
**
 and choose the
**
BasicEntity
**
 and drag it into the viewport. In the
**
Entity Properties
**
 in the
**
Properties
**
 panel you can add your character *cdf in the model section to load your mesh.

Now jump into the game mode (
**
Ctrl+G
**
) and press
**
F10
**
 to visualize the proxies.

*

*

*
Pic5: Entity -> Physics -> Basic Entity
*

*

*
*

Pic6: Choosing your character *.cdf file
*

*

*
*

Pic7: In Game Mode, press F10 and to see the proxy for the mesh
*

For testing, try to walk against the proxy and try if the collision is blocking the player.

If you can´t see any proxy's go back and check the naming convention in 3dsMax.

##
Ragdoll Creation

Since we set up everything correctly for the hit detection, we need to set up the bone limit rotation for the ragdoll system. The ragdoll is the physical simulation of a dead body, the good thing about this is we don´t need any additional animations.

We will start with the headbone. Select the
**
Headbone phys
**
 box in the
**
Phys
**
 layer and with this selected go to the
**
Hierarchy Panel
**
 and click the
**
IK
**
 button in the middle. There is a
**
Rotation Joints
**
 section for all axis. Here you choose your rotate limitation for each bone. If you don´t want to have rotation click on the
**
Limited
**
 checkbox and set all values from 0 to 0.. This will lock any rotation movement.

If you want to have a limited rotation you need to set a angle from for example -20 to 20 and check the
**
Active
**
 checkbox. This will cause a rotation in the ragdoll. Avoid rotation in the -90 and 90 degree area because this can cause gimbal lock. Try to stay slightly under the 90 degree mark.

If you tick the
**
Limited
**
 checkbox but you don't click the
**
Active
**
 checkbox you won´t see any movement in the Editor. (
**
Active
**
 and
**
Limited
**
 checkboxes have to be ticked).

*
Pic8: Bone rotation limits
*

Set the rotation limit for each bone. If you have a clear idea how your ragdoll should behave, type in the numbers for the angle limitation and see the result in the engine.

For a realistic behavior you may need to start with no movement at all. Start with only one bone and get the joint rotation limits correct before you continue with the next bone.

Some information about joint rotation in general:

-
Avoid using joints with all 3 axis locked, because they slow down the simulation.

-
Avoid rotation angle larger than -90° , 90°.

##
Stiffness and Spring Tension

Stiffness of an angular spring at a joint can be adjusted via the "Spring Tension" parameter. A value of
**
1
**
 means acceleration of 1 radian/second
2
 (1 radian = 57°). Damping should also be set to some reasonable value (1.0 corresponds to fully dumped oscillations for an isolated joint, 1.0 is also the recommended value).

##
Dampening

The 'dampening' value in the
**
IK Limit
**
 options will effect how loose the joint will be in the rag doll simulation of the dead body. Most times you will want the dampening value set at
**
1,0
**
.

##
Parent Frame

In some cases there can be problems with the physics calculation in the local joint rotation. Sometimes it is required to have a joint rotation beyond the -90°, 90° angle for instance a head, tail or leg. For this circumstance we need to create a parent frame in the ragdoll.

To create a parent frame, the workflow is the same as for the physics proxies. Let's take the
**
Head Bone
**
 for example:

-
Create a new box, this will act as node.

-
Place it where you can clearly see which bone is affected .

-
Important thing is the naming convention, in this case name it "Head Bone phys parentFrame".

-
For the rotation limits same as for the normal phys object, go to the "IK" and "Joint Rotation" and set the limits for the created ParentFrame.
If done with the Ragdoll bone limits, export the CHAR mesh again.

##
Testing the Ragdoll in CRYENGINE

For testing the asset, in CRYENGINE, open the
**
Create Object
**
 tool and  go to
**
Entity -> Physics -> Dead Body
**
 and drag it into the viewport. in the model section select your character *.cdf.

Now press the
**
Enable Physics/AI
**
 button click the little hand icon and grab your ragdoll and test the behavior while dragging it around in the viewport.

*

*

*
Pic9: Drag around the ragdoll in the viewport to test the ragdoll behavior
*

[Setting up Custom Mesh Bones in CAT](#setting-up-custom-mesh-bones-in-cat)
[Creating Physic Proxy's](#creating-physic-proxys)
[Testing the proxy in CRYENGINE](#testing-the-proxy-in-cryengine)
[Ragdoll Creation](#ragdoll-creation)
[Testing the Ragdoll in CRYENGINE](#testing-the-ragdoll-in-cryengine)
