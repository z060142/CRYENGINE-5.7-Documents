# 7-1 - Calling The Module

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/29793346
- Page ID: 29793346
- Breadcrumb: Tutorials > Game Logic > Flow Graph Tutorials > Tutorial - Getting Started With Flow Graph > 7 - Flow Graph Modules > 7-1 - Calling The Module
- Parent: 7 - Flow Graph Modules

## Content

[![Image](https://www.cryengine.com/docs/static/attachments/52593314) 7 - Flow Graph Modules](/docs/static/engines/cryengine-5/categories/23756816/pages/27591916)

##
How do I expose the Module functionality to other graphs?

In the previous chapter
[7 - Flow Graph Modules](../7%20-%20Flow%20Graph%20Modules.md)
 we created a module that allowed us to plug in a string into the input ports of the Module. In this chapter we will see how easy it is to set up the String port that we are given and have it print to the screen so we know it is functioning off the modular graph.

##
Calling Your Flow Graph Module

Follow the steps below to call a Flow Graph Module in your scene:

-
Go to
**
Create Object -> Empty Entity
**
 and drag it into the scene.

-
**
Right click
**
 the new entity and choose
**
Create Flow Graph
**
.
**
 N
**
ame it
**
moduleQuickstart
**
 to match the previous FG Module.

-
Right click to see the node tree and navigate to
**
Add Node -> Module -> Call_moduleQuickstart
**
.

-
With the module now in our level graph we can add a
**
Game:Start
**
 node to the
**
Call
**
 input port of the Module node.

-
Finally, we want to create a
**
String:SetString
**
 node to our custom
**
displayText
**
 input port in the Module. For the Message inside the String node we will want to type "MODULE FIRED" to know the module executed the call.

##
Step 1

![Image](https://www.cryengine.com/docs/static/attachments/36310051)

##
Step 2

![Image](https://www.cryengine.com/docs/static/attachments/36310052)

##
Step 3

![Image](https://www.cryengine.com/docs/static/attachments/36310053)

##
Step 4

![Image](https://www.cryengine.com/docs/static/attachments/36310054)

##
Step 5.1

![Image](https://www.cryengine.com/docs/static/attachments/36310056)

##
Step 5.2

![Image](https://www.cryengine.com/docs/static/attachments/36310057)

##
Conclusion

Although this tutorial has concluded, feel free to venture out on your own development path based on what we've covered in the previous chapters.
For information on the topics covered in this tutorial and more
, please refer to the
[CRYENGINE V Manual](/docs/static/engines/cryengine-5/categories/23756816/pages/23307414)
.

[![Image](https://www.cryengine.com/docs/static/attachments/52593314) 7 - Flow Graph Modules](/docs/static/engines/cryengine-5/categories/23756816/pages/27591916)
