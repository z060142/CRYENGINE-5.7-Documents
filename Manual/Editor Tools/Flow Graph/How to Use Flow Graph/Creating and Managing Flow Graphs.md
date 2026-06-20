# Creating and Managing Flow Graphs

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/29450518
- Page ID: 29450518
- Breadcrumb: Editor Tools > Flow Graph > How to Use Flow Graph > Creating and Managing Flow Graphs
- Parent: How to Use Flow Graph

## Content

##
Creating a New Graph

Graphs belong to a specific entity are stored as a property of the entity. When the entity is saved or exported, the corresponding graph is also automatically saved.

Select the entity in the viewport, and navigate to the
**
Flow Graph
**
 section under
**
Properties
**
 tab. There are three buttons:
**
Open
**
,
**
List
**
, and
**
Remove
**
.

There are two ways to create a new graph for an entity:

-
Click
**
Open
**
 in the
**
Flow Graph
**
 section under
**
Properties
**
 tab to create a new Flow Graph.

-
**
Right-click
**
 the entity in the Viewport, and select
**
Create Flow Graph
**
.
![Image](https://www.cryengine.com/docs/static/attachments/35394498)

If this is the first Flow Graph in a level, a new dialog box will be displayed (
*
see below
*
), asking you to enter a new group for the Flow Graph.

![Image](https://www.cryengine.com/docs/static/attachments/44971086)

Enter a name and click
**
OK
**
. This will create the new graph and automatically put it in the group.

If a Flow Graph group is already present, you will see the following dialog box:

![Image](https://www.cryengine.com/docs/static/attachments/44971087)

Click
**
New...
**
 to create a new group name for the Flow Graph or select from the existing group.

The graph overview window will show the new graph and automatically open it. You can right-click a graph node in the overview window to display a context menu, with additional options to edit the graph.

##
Deleting a Graph

As a graph belongs to an entity in the level, the graph is removed if the associated entity is deleted. You can delete a graph as follows:

-
Graphs can be removed from the entity by using the graph context menu or the Remove button under the entity's
**
Properties
**
 tab.

-
Deleting the graph by deleting the graph entity: Select the entity and in the
**
Edit
**
 menu, click
**
Delete
**
.

-
Deleting the graph without deleting the graph entity: In the Flow Graph window under the Flow Graph Editor,
**
right-click
**
 the graph, and click
**
Delete Graph
**
.
![Image](https://www.cryengine.com/docs/static/attachments/44971088)

![Image](https://www.cryengine.com/docs/static/attachments/35395024)

##
Renaming and Re-Grouping Graphs

The graph's name is always the name of the entity on which it has been created. When the entity's name is changed, the name in the graph overview window automatically gets changed. The graph's context menu a has an option to move the graph to a different group.

Under the Flow Graph editor, in the Flow Graph window,
**
right-click
**
 the graph and select
**
Change Folder
**
. If no groups have been created, you will now be prompted to enter a new group name. Enter the desired group name and confirm it by pressing
**
Enter
**
 or by clicking
**
OK
**
.

If one or more groups already exist in the level, a new window will be displayed where you can select the group where you want the graph to be placed. Select the group and click
**
OK
**
 to confirm, or select
**
New
**
 to open the group creation window in order to create a new group.

##
Disabling and Enabling Graphs

To enable or disable the graphs, right-click the desired graph in the Flow Graph overview window and select
**
Disable
**
. By disabling, the nodes within the graphs will be ignored while the game is running.

You can choose
**
Enable
**
 in the context menu to activate the graph again.

To disable entire graphs within a group,
**
right-click
**
 the group folder in the Flow Graph overview window and select
**
Disable All
**
. You can also select
**
Enable All
**
 to enable all the graphs within the group.

![Image](https://www.cryengine.com/docs/static/attachments/44971090)

When a level is exported with some graphs in the disabled mode, these graphs will remain in the disabled state in the game.
