# Locomotion Locator

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/23307989
- Page ID: 23307989
- Breadcrumb: Asset Prep (External) > Asset Exporting Overview > Geometry Creation Overview > Animated Geometry > Basics (animated) > Rigging (animated) > Locomotion Locator
- Parent: Rigging (animated)

## Content

![Image](https://www.cryengine.com/docs/static/attachments/29934055)

##
Locomotion Locator Rig Element

The locomotion locator or Locator_Locomotion as the node is called, is used in the engine to describe the logical movement and orientation of the animation. This node needs to be added to motions which translate in a non uniform way, such as a start or stop transition which have peaks and troughs in acceleration.

-
The skeleton must contain the bone Locator_Locomotion only for animations that are required to contain it. For loops it is not necessary, as all animations are processed with the locator for ease of batching later on.

-
In biped the easiest way to add this node is to turn on figure mode and create a prop. In this way the animation for the locator can be saved inside the biped file, making it easier for batch exporting.

-
The following image shows how to add the prop. Simply access figure mode, traverse to the structure menu of biped and check the box
Props:1
.
![Image](https://www.cryengine.com/docs/static/attachments/23994376)

-
Make sure the bone faces the positive Y axis in its local coordinate system.

-
The following image is a check list for the required points above. Name, coordinate system and direction of Y+.

![Image](https://www.cryengine.com/docs/static/attachments/23994375)
