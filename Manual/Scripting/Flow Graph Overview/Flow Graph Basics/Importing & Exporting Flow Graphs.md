# Importing & Exporting Flow Graphs

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/29450529
- Page ID: 29450529
- Breadcrumb: Scripting > Flow Graph Overview > Flow Graph Basics > Importing & Exporting Flow Graphs
- Parent: Flow Graph Basics

## Content

##
Overview

Graphs can be exported to an XML file for use in other levels. The graph structure, including all nodes and links, can be exported. However, the entities to which the nodes refer are not exported. You will need to reset the target entities after importing.

When a graph is imported, the nodes that do not have target entities displays a red
**
Choose Entity
**
 highlight.

##
Exporting

To export a graph, you need to perform the following steps:

-
Open the graph and select the nodes that you want to export.

-
**
Right-click
**
 anywhere in the main editing pane, and then got to
**
Selection -> Export Selected Nodes
**
.

![Image](https://www.cryengine.com/docs/static/attachments/44971123)

-
A new window will be displayed and it will prompt you to specify a file name for the exported graph.

-
Select a name and click
**
Save
**
to finish exporting the graph.

##
Importing

To import a previously exported graph into another graph, first open the graph that you want to add the exported graph to.

-
Open the context menu by
**
right-clicking
**
 the main editing pane, and then selecting
**
Import
**
.

-
Select the .xml file that contains the graph, and click
**
OK
**
to finish importing the graph. You can also
**
right-click
**
 directly inside the Flow Graph window and import the graph from there:

![Image](https://www.cryengine.com/docs/static/attachments/44971124)
The imported graph will not be inserted into the new graph at the position of the mouse pointer; it'll be positioned relative to the old graph.
