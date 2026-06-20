# 4 - Debugging

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/27591908
- Page ID: 27591908
- Breadcrumb: Tutorials > Game Logic > Flow Graph Tutorials > Tutorial - Getting Started With Flow Graph > 4 - Debugging
- Parent: Tutorial - Getting Started With Flow Graph

## Content

[![Image](https://www.cryengine.com/docs/static/attachments/52593286) 3 - Clock Counting Down](/docs/static/engines/cryengine-5/categories/23756816/pages/27591905)

[![Image](https://www.cryengine.com/docs/static/attachments/52593288) 5 - Breakpoints](/docs/static/engines/cryengine-5/categories/23756816/pages/29793935)

When creating your Flow Graphs you may find that certain things are now triggering and that overall your graph is either behaving in a way that is unsuspected or completely broken. In order to remedy this situation we have a tool named a Debugger that we can use to understand the execution order and flow of our graph visually. When building your graphs inside of the Editor you will constantly use the Debugger to make sure that your data is making it to the end of your chains.

##
Using the Debugger

Follow the steps below to execute debugging from within our countdown graph:

-
Enable the Debugger within the Flow Graph interface by clicking the
**
Bug
**
 icon in the top left menu. After doing so, jump into game mode (
**
Ctrl+G
**
) to activate the visual debugging in the graph.

-
Different connections will now have colors associated to them that correspond to the firing of the node and the amount of times it has been fired. By default the black connectors will now change to green when fired and values will be highlighted in yellow. The number values between the nodes show the number of times the output has fired into the input port. By default the left value will almost always be the only one that increments in value.

-
To clear the debugging information from the graph you will need to exit game mode and then click the
**
Trash
**
 icon.

##
Step 1

![Image](https://www.cryengine.com/docs/static/attachments/36309949)

##
Step 2

![Image](https://www.cryengine.com/docs/static/attachments/36309950)

##
Step 3

![Image](https://www.cryengine.com/docs/static/attachments/36309951)

[![Image](https://www.cryengine.com/docs/static/attachments/52593286) 3 - Clock Counting Down](/docs/static/engines/cryengine-5/categories/23756816/pages/27591905)

[![Image](https://www.cryengine.com/docs/static/attachments/52593288) 5 - Breakpoints](/docs/static/engines/cryengine-5/categories/23756816/pages/29793935)
