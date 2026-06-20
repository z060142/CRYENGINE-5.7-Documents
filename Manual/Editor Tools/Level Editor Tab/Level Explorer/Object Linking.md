# Object Linking

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/36866230
- Page ID: 36866230
- Breadcrumb: Editor Tools > Level Editor Tab > Level Explorer > Object Linking
- Parent: Level Explorer

## Content

##
Overview

As projects grow in size, the number of objects included within a single level might naturally increase, leading to a cluttered and disorganized level design environment.

This is partly overcome by working with multiple layers to which objects may be assigned in the
[/docs/static/engines/cryengine-5/categories/23756816/pages/35259541](
Level Explorer
)
. Additionally, the Engine also allows for links or associations to be created between multiple objects such that any changes made to a single object automatically influences others with which it might be associated.

These associations are of three basic types; Groups, Parent - Child Links and Entity Links.

##
Grouping

Grouping places multiple objects into a container which can then be manipulated as one single object. By default, objects included within a group cannot be independently edited unless the group has been opened.

##
Functionality

##
Creating a Group

In order to create a group, the objects that need to be included within it must be selected either by:

-
Individually clicking upon them within the Viewport while holding the
**
Ctrl
**
 key or;

-
Dragging a selection box around multiple objects within the Viewport.
[Image: /docs/static/attachments/36840427]

*
Group Creation
*

Right-clicking upon any of the selected objects generates a context menu with the
**
Create Group
**
 option, as seen in the above image.

Once created, a bounding box will be displayed around the group along with a group-specific pivot point that helps in easier selection/manipulation of the group as a whole via the Viewport.

[Image: /docs/static/attachments/36840431]

*
Bounding Box
*

The Properties panel will additionally reflect the following group-specific options when a group is created or selected.

##
Ungroup/Open

**
Ungroup
**
 discards the association existing between a group's objects, such that each of them are returned to their original individual states.

[Image: /docs/static/attachments/36840432]

*
Ungroup/Open
*

The
**
Open
**
 option meanwhile allows the objects contained within a group to be individually edited, moved, transformed, rotated or scaled, without affecting the group association between them as demonstrated below.

Selecting a grouped object from the Level Explorer or double-clicking it within the Viewport automatically opens its containing group. allowing the object to be individually edited, moved, transformed, rotated or scaled as desired.
[Image: /docs/static/attachments/36842659]

*
Open Group
*

##
General

The General tab contains options to change the name, bounding box color and material assigned to the selected group as a whole.

##
Transform

Contains options to Move, Rotate and Scale the objects included within the group as a whole.

##
Attach to...

The
**
 Attach to...
**
 option allows other objects and groups to be added to an existing group.

This is done by:

-
Selecting the desired object from the Viewport;

-
Right-clicking the object and selecting the
**
Attach to...
**
 option;

-
Selecting the target group to which the selected object must be added.
[Image: /docs/static/attachments/36842025]

*
Attach to...
*

Having trouble selecting the target group? Activate Helpers by clicking the
[Image: /docs/static/attachments/36842673]
 icon at the top of the Viewport, hold the
**
Spacebar
**
 to show pivot points, and click the pivot point of the Group.

Also note that once the
**
Attach to...
**
 option has been selected, the next mouse click must select the destination group of the selected object.

##
Detach

The
**
Detach
**
 option removes the selected object from its group.

This is done by:

-
Opening the object's group using the
**
Open
**
 button from the group's Properties panel;

-
Selecting the desired object from the Viewport;

-
Right-clicking the object and selecting the
**
Detach
**
 option.
[Image: /docs/static/attachments/36842026]

*
Detach
*

Alternatively, objects can attached to/detached from groups from the
**
Level -> Group -> Attach to.../Detach
**
 options of the Main Menu, which also contains options to create, open, ungroup and close groups.

##
Importing/Exporting Grouped Objects

A selected group may be saved as an external OBJ file from the
**
Level -> Export Selected Object(s)
**
 option of the Main Menu.
Previously saved groups can then be imported into a level using the
[/docs/static/engines/cryengine-5/categories/23756816/pages/35260066](
 Asset Browser
)
.

##
Linking

As opposed to Grouping, Linking creates parent-child hierarchies between objects such that any physical transformations applied to a parent object is automatically propagated to its children.

Transformations applied to a child object however do not influence its parent. Moreover while Grouping essentially creates a container around selected objects within the Viewport, this container/group doesn't exist in game code nor can any logical relationship between the group's members.

Parent-child objects on the other hand might exhibit logical relationships in game code.

[Image: /docs/static/attachments/28274866]

*
Moving a child object
*

*
[Image: /docs/static/attachments/28274867]

Moving a parent object
*

Linking does not work on static Brush objects; only
[/docs/static/engines/cryengine-5/categories/23756816/pages/26870341](
Entity
)
 type objects can be linked.

##
Functionality

##
Creating a Link

To create a parent-child link between two objects within the Viewport:

-
Select the desired child object, right-click it and click
**
Link To...
**
;

-
Select the target parent object immediately after as shown.
[Image: /docs/static/attachments/36842751]

*
Linking and Unlinking
*

##
Linking to Character Bones

Entities can also be attached to characters with skeletal meshes by creating a bone attachment link. This is especially useful for characters that will be picking/moving objects within a scene.

To link an Entity-type object to a character bone:

-
Select the desired entity, right-click it and click
**
Link To...
**
;

-
Hold down the
**
Shift
**
 button and select the target character by clicking upon it once in the Viewport; this displays a list of the character's bones in a pop-up menu.

-
Select the target bone by clicking upon its listing in the pop-up menu.

##
Unlink

Similarly, right-clicking a child object and selecting the
**
Unlink
**
 option will remove all its links and dependencies.

Alternatively, objects can be linked and unlinked from the
**
Link -> Link/Unlink
**
 options of the Main Menu or via the
[Image: /docs/static/attachments/36840435]
 icons of the
[/docs/static/engines/cryengine-5/categories/23756816/pages/35848748#Toolbars-Selection](
Selection
)
 toolbar.

[Image: /docs/static/attachments/36840434]

*
Link -> Link/Unlink
*

To Link two objects using either of the two methods:

-
Select
**
Link -> Link
**
 option from the Main Menu or the
[Image: /docs/static/attachments/36842754]
 icon;

-
Click upon the object that will be the child in the new link, hold down the LMB and drag the mouse between this child object and its target parent object.
A link in progress is indicated by a red line whereas a blue line represents a completed link; clicking upon
[Image: /docs/static/attachments/36842752]
 at the top of the Viewport will exit Link mode. Similarly a child is unlinked from its parent by selecting it within the Viewport, and clicking upon either
**
Link -> Unlink
**
 or the
[Image: /docs/static/attachments/36842755]
 icon.
[Image: /docs/static/attachments/28274864]

*
Link In Progress
*
[Image: /docs/static/attachments/28274865]

*
Link Completed
*
Moreover objects can also be grouped/linked from the Level Explorer so that:

-
Dragging an object onto a group or prefab adds the object to the group or prefab;

-
Dragging an object to a layer moves it into that layer;

-
Dragging an object onto another object creates a parent-child relationship between the two objects;

-
Dragging an Entity type object onto another Entity type object that has bones, displays a menu through which the first object can be linked to either a specific bone or the target object itself.
[Image: /docs/static/attachments/36842412]

*
Level Explorer Grouping/Linking
*

##
Entity Links

A third kind of link that can exist between objects is an Entity Link.

An Entity Link merely represents a logical relationship that exists between
[/docs/static/engines/cryengine-5/categories/23756813/pages/26216196](
Entity
)
 type objects, and any change made to an entity within an Entity Link doesn't affect the other.

Such logical links between entities can be used to script sequences of events using
[/docs/static/engines/cryengine-5/categories/23756816/pages/27594282](
Flow Graph
)
 for example, where the
[/docs/static/engines/cryengine-5/categories/23756816/pages/29450603](
GetEntity
)
node retrieves created Entity Links.

##
Functionality

##
Creating and Deleting an Entity Link

To link multiple objects using Entity links:

-
Select the first e
ntity
 and scroll down to the
**
Entity Links
**
 section in the Properties panel.

[Image: /docs/static/attachments/36840378]

*
Entity Links section.
*
*

*

-
Click
**
Pick
**

and select the target Entity type object with which the currently selected entity needs to be linked.
A green line will indicate that the link process has been successfully completed.

[Image: /docs/static/attachments/36840377]

*
Pick
*

-
Users may continue selecting multiple Entities to link the currently selected object with or edit the current link's properties from the Properties panel. Selecting the
**
Clear
**
 option discards all created Entity links, while clicking
[Image: /docs/static/attachments/36842756]
 exits the Entity Links mode.
Cannot see a green line between linked entities?

Make sure Display Object
**
s Link is
**
 enabled in the Editor preferences at
**
Edit->Preferences->Viewport->General.
**
[Image: /docs/static/attachments/36840376]

*
Display Objects Link
*

##
Renaming

The
**
Name
**
 field under the
**
Links
**
 section can be edited to provide Entity Links with a custom name.

[Image: /docs/static/attachments/36840375]

*
Renaming
*

##
Replacing Targets

To replace the target entity of any given Entity Link, click the
**
Arrow
**
 button
[Image: /docs/static/attachments/36840380]
 next to the
**
Target
**
 field of the
**
Entity Links
**
 section before making a new selection.

##
Run-time Links Using Flow Graph

Objects can be linked and unlinked during game run-time through
[/docs/static/engines/cryengine-5/categories/23756816/pages/27594282](
Flow Graph
)
 by making use of the
[/docs/static/engines/cryengine-5/categories/23756816/pages/29450587#EntityNodes-AttachDetach](
 ChildAttach and ChildDetach
)
 Entity Nodes respectively.

[#grouping](
Grouping
)
[#linking](
Linking
)
[#entity-links](
Entity Links
)
[#run-time-links-using-flow-graph](
Run-time Links Using Flow Graph
)
