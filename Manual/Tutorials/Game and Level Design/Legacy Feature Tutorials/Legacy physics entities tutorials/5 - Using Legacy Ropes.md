# 5 - Using Legacy Ropes

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/27591011
- Page ID: 27591011
- Breadcrumb: Tutorials > Game and Level Design > Legacy Feature Tutorials > Legacy physics entities tutorials > 5 - Using Legacy Ropes
- Parent: Legacy physics entities tutorials

## Content

##
What Are Some Rope Use Cases?

Something that is common in gameplay is the need to be able to hang an entity from a cable to create an element within a scene. These items can range from chandeliers to bells and need to behave not only properly on the cable but also constrain the object accurately at the tip and withstand serious physics disruptions when they get shot or need to break off entirely.

For this breakdown we will be using a Rope Entity as well as RigidBody sphere and then we will be attaching the rope to a ceiling that will be a static object. This should cover quite a large amount of use cases and get the general understanding of the workflow when interacting with the Rope Entity.

##
Creating Our Rope

Follow the steps below to create a rope with a ball hanging from it:

-
Go to
**
Create Object -> Legacy Entities -> Physics -> RigidBodyEx
**
 and drag it into your scene.

-
Select the Spawnpoint entity, go into
**
Flow Graph
**
, make sure the
*
flowQuickStart
*
 graph is open and click
**
RMB
**
 to
**
Add selected entity
**
 for the Spawnpoint to be added with its properties.

-
For this part we will be interacting with the points of the rope so that we can move our other point to above the ball.

In order to edit, click
**
 Edit Shape
**
 in the
**
Properties
**
 panel and use the
**
Move
**
 tool (
**
1
**
 Key) to move the point into place as shown below.

-
Grab a primitive box from
**
Create Object -> Brush -> Default
**
. Make sure you DO NOT select the box with no proxy. Placing this above the rope top point should show a green box when the physics is active.

-
Finally, you can jump into your game (
**
Ctrl+G
**
) and shoot the sphere to see that the rope will hold and fling around in the air until it comes to a resting halt naturally.

##
Step 1

![Image](https://www.cryengine.com/docs/static/attachments/29928926)

##
Step 2

![Image](https://www.cryengine.com/docs/static/attachments/29928961)

##
Step 2

![Image](https://www.cryengine.com/docs/static/attachments/29928927)

##
Step 3-1

![Image](https://www.cryengine.com/docs/static/attachments/29928928)

##
Step 4

![Image](https://www.cryengine.com/docs/static/attachments/29928930)

##
Step 5

![Image](https://www.cryengine.com/docs/static/attachments/29928931)
