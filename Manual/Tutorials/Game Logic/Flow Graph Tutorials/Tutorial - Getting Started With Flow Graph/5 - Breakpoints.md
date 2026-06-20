# 5 - Breakpoints

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/29793935
- Page ID: 29793935
- Breadcrumb: Tutorials > Game Logic > Flow Graph Tutorials > Tutorial - Getting Started With Flow Graph > 5 - Breakpoints
- Parent: Tutorial - Getting Started With Flow Graph

## Content

[![Image](https://www.cryengine.com/docs/static/attachments/52593299)4 - Debugging](/docs/static/engines/cryengine-5/categories/23756816/pages/27591908)

[![Image](https://www.cryengine.com/docs/static/attachments/52593300)6 - Entity Communication](/docs/static/engines/cryengine-5/categories/23756816/pages/27591911)

#### How do you use breakpoints?

It may be hard to understand at first just exactly what a Breakpoint contributes beyond freezing your game and letting you know that a port fired off. Looking closer in the Breakpoint Tree, though, we can see that we are also rewarded with the exact information fired at that point. Gathering these facts together lets us see the execution order of our graph and makes it easier to find improper data being passed down through the ports.

#### Adding Breakpoints

- Add a **Math:Equal** node and check for the value of **95** to be the breakpoint trigger. Add a Breakpoint by right clicking on the port and select **Add Breakpoint**. Be aware that you will need **Debugging** turned on as well.
In our case, the Breakpoint will fire when it hits **5**.
- Jump into the game; this should not trigger anything until you have reached the countdown of **95** and thus had the game pause to investigate the specific point that fired. You'll see the game freeze in the viewport and the Breakpoint will be set to "True" in the Breakpoints panel of the Flow Graph Editor.
- Keep in mind that you can clear a single instance to remove a Breakpoint by right clicking on a single port. In this same menu you can also clear all associated with the graph.
- The last point to keep in mind is that you can have very complex graphs that have multiple breakpoints down the tree. An easier but not so noticeable way of sorting those is through the **Breakpoints** tree panel in the bottom right of the Flow Graph tool.

##### Step 1.1

![Image](https://www.cryengine.com/docs/static/attachments/36309987)

##### Step 1.2

![Image](https://www.cryengine.com/docs/static/attachments/36309988)

##### Step 2

![Image](https://www.cryengine.com/docs/static/attachments/36309989)

##### Step 3

![Image](https://www.cryengine.com/docs/static/attachments/36309990)

##### Step 4

![Image](https://www.cryengine.com/docs/static/attachments/36309991)

[![Image](https://www.cryengine.com/docs/static/attachments/52593299)4 - Debugging](/docs/static/engines/cryengine-5/categories/23756816/pages/27591908)

[![Image](https://www.cryengine.com/docs/static/attachments/52593300)6 - Entity Communication](/docs/static/engines/cryengine-5/categories/23756816/pages/27591911)
