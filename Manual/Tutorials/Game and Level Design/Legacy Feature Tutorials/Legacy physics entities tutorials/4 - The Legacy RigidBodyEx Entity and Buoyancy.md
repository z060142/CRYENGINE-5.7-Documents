# 4 - The Legacy RigidBodyEx Entity and Buoyancy

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/27592208
- Page ID: 27592208
- Breadcrumb: Tutorials > Game and Level Design > Legacy Feature Tutorials > Legacy physics entities tutorials > 4 - The Legacy RigidBodyEx Entity and Buoyancy
- Parent: Legacy physics entities tutorials

## Content

##
Where Would I Need Bouyancy In My Game?

An aspect of the physics system that can provide large amounts of fun is the ability to have objects physically interact with water within your scene. This could be seen as a player that has a certain buoyancy value or is being pushed by a stream, to the times where you could have barrels or rocks running down into the water to float away. Understanding the most basic parameters is essential to getting interactions that are believable from the start.

##
Manipulating Buoyancy to Make Objects Float or Sink

Follow the steps below to see how buoyancy can be driven through a couple settings for various results:

-
Go to
**
Create Object -> Area -> Water Volume
**
 and then click several times to get the pattern of a square as shown below. Finally, double click to add your final 4th point.

-
Assign a material to the entity by going to the properties panel, clicking on the
**
Folder Icon
**
 and go to
**
GameSDK -> Materials -> Water -> WaterVolumes
**
. In here, select the
**
water_cave
**
 material.

-
To test the first object, drag in a
**
RigidBodyEx Entity
**
 and change the object model to a
**
primitive_cube
**
 in the object
**
Model
**
 property. Uncheck
**
Resting
**
 and set
**
Mass
**
 to
**
1000
**
. Keep in mind the
**
Water
**
 settings below as we will adjust these in a later step. Once set you should see the cube resting nicely on the surface of the water.

-
For the next step we will duplicate the
**
RigidBody entity
**
 by pressing
**
CTRL+D
**
 and then we will be changing the
**
Water Density
**
 value to be
**
100
**
, thus making the density value 1/10 and causing it to plummet below the surface.

-
Finally we have a cube set to
**
Water Density
**
 of
**
300
**
 which allows the cube to tumble and bob up and down on the surface of the water. Keep in mind that anything below the value of
**
125
**
 will cause the cube to sink below the surface immediately.

##
Step 1

![Image](https://www.cryengine.com/docs/static/attachments/29928962)

##
Step 2

![Image](https://www.cryengine.com/docs/static/attachments/29928963)

##
Step 3

![Image](https://www.cryengine.com/docs/static/attachments/29928964)

##
Step 4

![Image](https://www.cryengine.com/docs/static/attachments/29928965)

##
Step 5

![Image](https://www.cryengine.com/docs/static/attachments/29928966)
