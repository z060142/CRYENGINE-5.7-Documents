# 1 - Gameplay Setup

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/27593405
- Page ID: 27593405
- Breadcrumb: Tutorials > Game Logic > Flow Graph Tutorials > Tutorial - Getting Started With Gameplay > 1 - Gameplay Setup
- Parent: Tutorial - Getting Started With Gameplay

## Content

[![Image](https://www.cryengine.com/docs/static/attachments/44971004)Tutorial - Getting Started With Gameplay](/docs/static/engines/cryengine-5/categories/23756816/pages/27593403)

[![Image](https://www.cryengine.com/docs/static/attachments/44971005)2 - Game Variables](/docs/static/engines/cryengine-5/categories/23756816/pages/29450191)

[/docs](/docs)

#### What do you mean by gameplay?

The concept of the Editor is simple in that it needs to give you access to entities and logic to create compelling gameplay. Within this section we will be looking at how we can use data to execute logic and be able to store variables that track the changes and state of your game. Deep down this is a core requirement to actually create any gameplay if you want to enter the mass market.

To begin, one of the main ways that we store variables on the designer end of the Editor is through a system called Game Tokens and these will be the basis of this exercise. The writing will be housed inside of Flow Graph as well as we will be saving to disk through an.xml file to show the flexibility of the system.

These types of elements will be covered in this tutorial which allows for you to start piecing Entities together to create compelling gameplay mechanics.

[Embed: https://vimeo.com/271653454]

#### Setting Up Our DisplayMessage Node and Input

You need to follow these below mentioned steps to begin printing information to the viewport and input to control an entity:

- To determine where the player spawns, add a **Spawnpoint Entity** and add a ** Flow Graph** named ** gameplayQuickstart.**
- Connect **Game:Start**'s ** Output** to the ** Spawn** input of the ** SpawnPoint**entity.
- Add both a **Primitive Box Brush** and a **Proximity Trigger** to the scene. The box will be used as a platform or destination to walk to for reference after spawn.
Select the **Proximity trigger**, go to your graph, **right click** in an empty space and choose **Add Selected Entity**. Connect the **Output** of the **Game:Start** node to the **Enable** input of the **ProximityTrigger** node.
- Now that we have standardized where the player will begin we can add a **Debug DisplayMessage** node to trigger a message of "Success" when the ** Enter**output port fires from the ** Proximity Trigger**.
- When you jump into the game (**Ctrl+G**) you should notice that you not only start exactly where the origin of the ** SpawnPoint** sits, but also you should see a message in the ** top left** printing out "Success" in ** white**.
- To take this one step more we will connect a **Light Entity** to an ** InputKey** to enable the light in your scene when connected to a player device (keyboard, controller, VR). Go to ** Create Object -> Legacy Entities -> Lights -> Light** and drag it into the scene.
- To be able to see the light better, change the **Diffuse Color** to a ** Green** and then increase the ** Diffuse Multiplier** to ** 150**. Make sure to drag it up a little so you see enough light.
- **Add** it to the graph and then add the ** Debug:InputKey** we mentioned earlier.
- Assign the **P Key** too the ** InputKey** node and add a ** Logic:Sequentializer** node in the middle of them.
- Connect the **Pressed** output node to the ** In** input port of the ** Sequentializer** and then feed the first two ** Output** ports into the ** Disable** and ** Enable** slots of the light.
- Jump into the game (**Ctrl+G**) and toggle the ** P**key turn the light ** Off** and ** On**.

##### Step 1

![Image](https://www.cryengine.com/docs/static/attachments/29931452)

##### Step 2

![Image](https://www.cryengine.com/docs/static/attachments/29931453)

##### Step 3-1

![Image](https://www.cryengine.com/docs/static/attachments/29931454)

##### Step 3-2

![Image](https://www.cryengine.com/docs/static/attachments/29931455)

##### Step 4

![Image](https://www.cryengine.com/docs/static/attachments/29931456)

##### Step 5

![Image](https://www.cryengine.com/docs/static/attachments/29931457)

##### Step 6

![Image](https://www.cryengine.com/docs/static/attachments/29931458)

##### Step 7

![Image](https://www.cryengine.com/docs/static/attachments/29931459)

##### Step 8

![Image](https://www.cryengine.com/docs/static/attachments/29931460)

##### Step 9

![Image](https://www.cryengine.com/docs/static/attachments/29931461)

##### Step 10

![Image](https://www.cryengine.com/docs/static/attachments/29931462)

##### Final Setup

![Image](https://www.cryengine.com/docs/static/attachments/29931451)

![Image](https://www.cryengine.com/docs/static/attachments/44971004)

[![Image](https://www.cryengine.com/docs/static/attachments/44971005)2 - Game Variables](/docs/static/engines/cryengine-5/categories/23756816/pages/29450191)
