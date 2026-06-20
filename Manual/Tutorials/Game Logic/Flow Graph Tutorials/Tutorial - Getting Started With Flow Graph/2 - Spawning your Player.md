# 2 - Spawning your Player

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/27591903
- Page ID: 27591903
- Breadcrumb: Tutorials > Game Logic > Flow Graph Tutorials > Tutorial - Getting Started With Flow Graph > 2 - Spawning your Player
- Parent: Tutorial - Getting Started With Flow Graph

## Content

[![Image](https://www.cryengine.com/docs/static/attachments/52593269)1 - Flow Graph Scene Setup](/docs/static/engines/cryengine-5/categories/23756816/pages/27591067)

[![Image](https://www.cryengine.com/docs/static/attachments/52593270)3 - Clock Counting Down](/docs/static/engines/cryengine-5/categories/23756816/pages/27591905)

The easiest and most useful way to learn Flow Graph is by using a Spawnpoint Entity and then hooking this up to spawn the player at that point on game start. To do this we will be using the prior made Flow Graph but adding an entity to it and then executing functionality through a **Game:Start** node.

#### Spawning Your Player

Follow the steps below to spawn your player within your level:

- Go to **Create Object -> Legacy Entities -> Others -> Spawnpoint** and drag it into your scene.
- Select the Spawnpoint, open Flow Graph, click on the flowQuickStart graph and then click **RMB** and choose ** Add Selected Entity** to add the Spawnpoint with its properties.
- Connect a **Game:Start** node to the ** Spawn** property of the ** Spawnpoint** node and jump into game (** Ctrl+G**) to see we spawn at that origin.

##### Step 1

![Image](https://www.cryengine.com/docs/static/attachments/36309389)

##### Step 2

![Image](https://www.cryengine.com/docs/static/attachments/36309390)

##### Step 3

![Image](https://www.cryengine.com/docs/static/attachments/36309391)

[![Image](https://www.cryengine.com/docs/static/attachments/52593269)1 - Flow Graph Scene Setup](/docs/static/engines/cryengine-5/categories/23756816/pages/27591067)

[![Image](https://www.cryengine.com/docs/static/attachments/52593270)3 - Clock Counting Down](/docs/static/engines/cryengine-5/categories/23756816/pages/27591905)
