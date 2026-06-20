# 1 - Using the RigidBodyEx legacy entity

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/27591003
- Page ID: 27591003
- Breadcrumb: Tutorials > Game and Level Design > Legacy Feature Tutorials > Legacy physics entities tutorials > 1 - Using the RigidBodyEx legacy entity
- Parent: Legacy physics entities tutorials

## Content

#### Physics Introduction

CRYENGINE is well-known to have a very versatile physics implementation that spans the range of characters, objects, and interactive vehicles for dynamic gameplay. Keep in mind that much of the advanced functionality will be housed in the GameSDK sample that is provided, which allows you to see all of the sample gamecode that exposes functionality to designers through mostly XML files.

In this Quick Start we will be examining how we can interact with several physics entities that are provided and look at adjusting global settings that can permanently alter the speed and interaction within your game. To start out we will begin with creating a basic RigidBodyEx entity and then we will be looking at the basic parameters any users will need to know in order to quickly interact properly with the entity.

[Embed: https://vimeo.com/272152219]

Some of the most important parameters are defined here:

- **Model** - Defines the model to be used.
- **Mass** - The weight of the object (the density of the object multiplied by its volume). This can be calculated as Mass = (Density * Volume).
- **Water Density** - This can be used to override the default water density (1000). Lower values assume that the body is floating in the water that's less dense than it actually is, and thus it will sink more easily.

It is important to look at the Mass and Density values of the RigidBodyEx as these will be of importance depending on how you wish to tackle the situation as both values will counteract each other. For the sake of simplicity we will be using a simpler method of only moving the mass on all sections except the section covering floating objects, which will manipulate the Water Density only. There are many topics within Physics and this Quick Start will be the entry point to understanding them deeper.

#### Creating a RigidBodyEx Entity to Interact With

- Go to **Create Object -> Legacy Entities -> Physics -> RigidBodyEx** and drag the entity into the scene.
- Click the **Resting** checkbox and making sure it is no longer resting. Next we will be setting the ** Mass** to ** 100.**You should now jump into the game and shoot the ball to see it applying a physical impulse to roll away.
- Lastly, for the sake of interaction you also have the ability to make your Entity **Usable** and display a ** Use Message**. In the image shown it uses the name "COLLIN" which will print out to the screen inside of a global radius.

##### Step 1

![Image](https://www.cryengine.com/docs/static/attachments/52592997)

##### Step 2

![Image](https://www.cryengine.com/docs/static/attachments/29928968)

##### Step 3

![Image](https://www.cryengine.com/docs/static/attachments/52592999)
