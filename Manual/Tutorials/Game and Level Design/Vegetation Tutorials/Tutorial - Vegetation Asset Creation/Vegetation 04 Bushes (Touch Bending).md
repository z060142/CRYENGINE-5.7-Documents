# Vegetation 04 Bushes (Touch Bending)

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/24285897
- Page ID: 24285897
- Breadcrumb: Tutorials > Game and Level Design > Vegetation Tutorials > Tutorial - Vegetation Asset Creation > Vegetation 04 Bushes (Touch Bending)
- Parent: Tutorial - Vegetation Asset Creation

## Child Pages

- [Vegetation 04 Bushes (Touch Bending) 3dsMax](Vegetation%2004%20Bushes%20(Touch%20Bending)/Vegetation%2004%20Bushes%20(Touch%20Bending)%203dsMax.md)
- [Vegetation 04 Bushes (Touch Bending) Maya](Vegetation%2004%20Bushes%20(Touch%20Bending)/Vegetation%2004%20Bushes%20(Touch%20Bending)%20Maya.md)
- [Vegetation 04 Bushes (Touch Bending) CRYENGINE](Vegetation%2004%20Bushes%20(Touch%20Bending)/Vegetation%2004%20Bushes%20(Touch%20Bending)%20CRYENGINE.md)

## Content

##
Overview

In this tutorial, we will show you the process of how to setup physical interactions between a bush asset and any other physicalized object (Player) in the level. To achieve this, we will be using our
**
Touch Bending
**
 system and learn how to set it up in CRYENGINE.
**
Touch Bending
**
 is a simple rope setup built into the
*
*.cgf
*
 file to simulate a physical interaction between the player and vegetation foliage. This method works great for bushes and ferns and also trees with big leaves (e.g. palm tree), with separate stems and/or branches.

For more information about using the
**
 Vegetation Editor
**
 in CRYENGINE, please refer
**
[HERE](../../../../Editor%20Tools/Vegetation%20Editor.md)
.
**

*
Pic1: Touch bending in action (with physics debug info displayed: F10 or p_draw_helper=1)
*

![Image](https://www.cryengine.com/docs/static/attachments/26510090)

We use instancing for the setup and it works through shared UVs (leaves which share the same UV space will automatically work with Touch Bending). The joints are set up through dummies, which are connected via an ordered naming convention. The system is basically in sleep mode for most of the time to save memory. That is why we add a volume mesh with the no-collide physics property to our asset that needs to cover all branches being used for Touch Bending. As soon as a player enters the assets
no-collide
volume region, it activates or wakes up the Touch Bending technology associated to the asset.

##
Helpful Information

Make sure to keep the following things in mind while you work on your asset:

-
Touch bending should only be used on bigger assets (bushes, ferns, trees etc.) but not on grass.

-
No-collide
proxy and proper material setup are necessary for this system to work.

-
Touch Bending can only be activated within the
no-collide
volume.

-
Dummies only work when:

-
They follow the naming convention rules and are linked to the object.

-
They are snapped to vertices of this object.

-
You do not need an entire branch setup for every leaf stem. You only need one or two branch setups, and let the engine handle the instancing on the other leaves.

-
You have to use a minimum of three dummies for each branch. Try to not exceed that number since three is enough for almost all situations.

-
Use the CVar
*
p_draw_helpers=1
*
 or
**
F10
**
 in-game to visualize the physics debug info (see
*
Pic1).
*

##
Tutorials

Depending on the DCC tool used - the links below show you how to setup vegetation assets for Touch Bending.

-
[Vegetation 04 Bushes (Touch Bending) 3dsMax](Vegetation%2004%20Bushes%20(Touch%20Bending)/Vegetation%2004%20Bushes%20(Touch%20Bending)%203dsMax.md)

-
[Vegetation 04 Bushes (Touch Bending) Maya](Vegetation%2004%20Bushes%20(Touch%20Bending)/Vegetation%2004%20Bushes%20(Touch%20Bending)%20Maya.md)

-
[Vegetation 04 Bushes (Touch Bending) CRYENGINE](Vegetation%2004%20Bushes%20(Touch%20Bending)/Vegetation%2004%20Bushes%20(Touch%20Bending)%20CRYENGINE.md)
[Helpful Information](#helpful-information)
[Tutorials](#tutorials)
