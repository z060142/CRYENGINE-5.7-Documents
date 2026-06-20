# Tutorial - Combining Components 1 - RigidBody and Particles

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/28181839
- Page ID: 28181839
- Breadcrumb: Tutorials > Game and Level Design > Entity Component Tutorials > Tutorial - Combining Components 1 - RigidBody and Particles
- Parent: Entity Component Tutorials

## Content

### Combining Components

This tutorial shows you how to combine Components - combining Components allows you to create some amazing effects and thus complex Entities can be easily created. The example below builds a Particle Effect (fire) that is triggered by a falling object.

However, before you get started you should be aware that we work with Schematyc in this tutorial, so if you are unfamiliar with Schematyc or maybe just need a memory refresh, then you can find the Schematyc documentation [here](../../../Editor%20Tools/Deprecated%20Tab/Schematyc%20Editor%20(Experimental).md).

We are also going to use the following components in this tutorial: [Tutorial - Mesh Component](Tutorial%20-%20Mesh%20Component.md), [Tutorial - Rigidbody Component](Tutorial%20-%20Rigidbody%20Component.md), [Tutorial - Particle Emitter Component](Tutorial%20-%20Particle%20Emitter%20Component.md), [Tutorial - Point Light Component](Tutorial%20-%20Point%20Light%20Component.md), and the [Tutorial - SensorVolume Component](Tutorial%20-%20SensorVolume%20Component.md). Hence, we recommend that you familiarize yourself with each of those Components first and before attempting this tutorial.

You will also need to download the [fire.pfx](/docs/static/attachments/28254533) to your project's Asset folder (anywhere in the folder will suffice). Normally this file will be downloaded into your Downloads Folder, hence you will need to copy/move it to your project's Asset folder.

Finally, the image below shows what the result of this tutorial will look like.

![Image](https://www.cryengine.com/docs/static/attachments/28254520)

First, we need to create the Entities for this tutorial and since we are going to use [Schematyc](../../../Editor%20Tools/Deprecated%20Tab/Schematyc%20Editor%20(Experimental).md), then we have to create two new schematyc Entities.

- Open the Asset Browser **Tools -> Asset Browser** and right click somewhere in the Asset Browser window. Create two new "Schematyc Entities", one named "particle" and the other "particle_trigger". After giving an Entity a name a popup will ask if you want to choose a base, in this case we don't, so say no.
![Image](https://www.cryengine.com/docs/static/attachments/28254534)
- Double click on the Entity named "particle", the Schematyc Editor will open. This Entity will be the particle on the ground and which will be triggered when the object falls into it.
- We now need to add some Components. Click on the "Add" button (middle top) and select "Component" from the context menu. Now add the following Components to the Entity: Particle Emitter, Point Light and Sensor Volume. These Components will then be visible in the "Components" category of your Entity.
- We will now add a Particle Effect (the fire particle you downloaded earlier to your project's Asset folder) to the "particle" Entity. First, Select the Particle Emitter Component, then go to the Asset Browser. The fire effect should be visible in the Asset Browser, but if it's not then go to **Edit -> Generate/Repair All Metadata**, this is basically is a refresh.
- Click on the folder icon next to the "Effect" attribute in the Properties tab, then click on the fire effect (in the Asset Browser), this places the fire.pfx in the Effect field and then make sure to click the OK button in the Asset Browser. Finally, make sure to uncheck the "Enabled" attribute of the Particle Emitter - this prevents the effect starting by default.
![Image](https://www.cryengine.com/docs/static/attachments/28254535)
- Select the Sensor Volume Component and add a Trigger Listener to it (we want to know when another Sensor Volume with that tag contacts the Sensor Volume so that we can activate the Particle Effect).
![Image](https://www.cryengine.com/docs/static/attachments/28254536)
- The "particle" Entity is now complete, so we can now start to build the logic for it. Under the "Graphs" category click on the SignalGraph. In the "Graph View" tab we now can start to build the logic. The logic of the "particle" Entity is fairly simple i.e. if something enters our Sensor Volume then we want the Particle Emitter to be activated. So right click in the graph view, in the search bar type "Entering" and select the node Entering.
![Image](https://www.cryengine.com/docs/static/attachments/28254537)
- Now we need to input all entering events and also need to activate the Particle Emitter if we get an event. Right click on the graph, in the search bar type "Activate" and select the node Activate. Then connect the "Out" of the SensorVolume::Entering (the entering node) with the "In" of the ParticleEmitter::Activate node. By default the "Activate" node would deactivate the effect, we want to activate it, so select the "Activate" node and click on the "Active" checkbox.
![Image](https://www.cryengine.com/docs/static/attachments/28254538)
- We have now finished building the "particle" Entity. So close the Schematyc Editor, go back to the Asset Browser and then drag and drop the "particle" Entity into your level somewhere.
![Image](https://www.cryengine.com/docs/static/attachments/28254539)
- We are now going to create another Entity - this is going to be the ball that falls down and triggers the effect. Go to the Asset Browser and double click on the "particle_trigger" Entity, this opens the Schematyc Editor. Once again we are going to add some components (see step 3 above for a reminder). In the case of a falling object, we need a Mesh Component, a Rigidbody Component (so the entity will be influenced by gravity) and a Sensor Volume to trigger the other Entity's Sensor Volume. Finally, we are going to add a Trigger to the Attribute field (see image below). Make sure that the SensorVolume Component is selected, then click on the Attribute field, click Add, then expand the menu and click Trigger. We need this Trigger attribute so that we can activate the Particle Effect.
![Image](https://www.cryengine.com/docs/static/attachments/28254540)
- In this example the geometry of the Mesh Component and the Sensor Volume have both been changed to a sphere, for a reminder of how to change the geometry of a Mesh, then see step 3 in the [Mesh Component](/docs) documentation. The "ball" Entity is now complete and so the Schematyc Editor can be closed. Now drag the "particle_trigger" Entity from the Asset Browser into your level and place it a little bit above the "particle" Entity.
![Image](https://www.cryengine.com/docs/static/attachments/28254541)
- After placing the "ball" Entity the whole setup is complete. To see how the setup works, then click on the small play button in the Sandbox Editor and wait until the ball hits the ground to see the Particle Effect.
![Image](https://www.cryengine.com/docs/static/attachments/28254542)
- Finally, to deepen your understanding/learning you can try to reproduce the light effect that is shown in the example.*gif file (at the top of the page). In this case search for the enable node of the Light Component in Schematyc, then enable the light when something enters the Sensor Volume (of course you will need to disable the light which is on by default).
