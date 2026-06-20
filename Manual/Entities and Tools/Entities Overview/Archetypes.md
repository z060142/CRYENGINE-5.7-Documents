# Archetypes

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/27593225
- Page ID: 27593225
- Breadcrumb: Entities and Tools > Entities Overview > Archetypes
- Parent: Entities Overview

## Content

[Image: /docs/static/attachments/29933302]

##
Overview

##
Topics

An Archetype Entity is based on a regular Entity and specifies individual parameter values for that Entity. If the value of an Archetype parameter is changed, all instances of that Archetype in the scene will be updated automatically.

Archetype Entities are organized in libraries which can be created in
[/docs/static/engines/cryengine-5/categories/23756816/pages/36869094](
The DataBase View
)
.

So technical level designers can predefine variations of Entity classes as Archetype Entities that can be used throughout the whole game. For global changes affecting all instances, the Archetype Entity just needs to be changed once in the Database View.

[#topics](
Topics
)
[#placing-archetype-entities](
Placing Archetype Entities
)
[#creating-archetype-entity-libraries](
Creating Archetype Entity Libraries
)
[#difference-between-archetype-settings-and-script-defaults](
Difference between Archetype settings and script defaults
)
[#revert-to-script-defaults](
Revert to Script Defaults
)
[#checking-the-script-default-value](
Checking the Script Default value
)

##
Placing Archetype Entities

Archetype Entities can be accessed by using
**
Create Object → Archetype Entity
**
 or alternatively, they can be dragged directly from the DataBase View.

The browser window shows all the Archetype Entity libraries that are currently loaded for the level.

Navigate these libraries by clicking once. Drag the individual Archetype Entities to the level to place them.

##
Filter of Archetype Entity Browser

This filter specifies a search string for the currently loaded Archetype library. All libraries containing Archetype Entities appropriate for the search string will be shown upon pressing the Reload button. Also, the Reload button can be used to update any recently altered archetype library files.

##
Archetype Entity Object Properties

Once you have placed an Archetype Entity in the level, select it to view its properties.

##
EntityArchetype Params

EntityArchetype Params are a basic set of parameters shared by all Archetype Entities.

**
Parameter
**

 |
**
Description
**

 |

**
Outdoor Only
**

 |
When set, the object will not be rendered when inside a visarea.

 |

**
Cast Shadow
**

 |
When set, the object will cast a shadow.

 |

**
LodRatio
**

 |
Defines how far from the current camera position, the different Level Of Detail models for the object are used.

 |

**
ViewDistRatio
**

 |
Defines how far from the current camera position, the the object can be seen.

 |

**
HiddenInGame
**

 |
When set, this object is not shown in the pure game mode.

 |

**
Receive Wind
**

 |
When set, this object will be influenced by any wind setup in the level.

 |

**
RenderNearest
**

 |
 |

**
NoStaticDecals
**

 |
 |

**
Created Through Pool
**

 |
 |

##
EntityArchetype Properties2

Below is an example of the EntityArchetype Properties2 dialog box. This dialog box contains a selection of properties from the Entity type, allowing you to edit the Archetype Entities on a case by case basis.

The example below shows the properties2 set for an AI entity:

[Image: /docs/static/attachments/51347848]

##
Creating Archetype Entity Libraries

Archetype Entity Libraries can be created and configured in the
[/docs/static/engines/cryengine-5/categories/23756816/pages/36869094](
The DataBase View
)
.

[Image: /docs/static/attachments/51347849]

##
Difference between Archetype settings and script defaults

Every highlighted property in the database view has actually a different value than the script default.

[Image: /docs/static/attachments/51347850]

##
Revert to Script Defaults

To revert the Archetype setting back to the actual script default value you can right click on a property and choose
**
Revert to Script Default
**
.

[Image: /docs/static/attachments/51347851]

##
Checking the Script Default value

It is possible to check the default value in the entities script by hovering over the property.

[Image: /docs/static/attachments/51347852]

##
Toolbar

[Image: /docs/static/attachments/51347853]

**
Action
**

 |
**
Description
**

 |

**
Load Library
**

 |
Allows the loading of an XML library file; the default path is
`
Game\Libs\EntityArchetypes
`

Please note that some prefabs can contain links to archetype objects; therefore, it is useful to load all the available Archetype libraries into the level.

 |

**
Save Modified Library
**

 |
Saves the Archetype library; when the level is saved, the Archetype library will also be automatically saved.

 |

**
Add Library
**

 |
Creates a new library.

 |

**
Remove Library
**

 |
Removes the currently selected library from the level; you need to manually delete it from the hard drive if you want to permanently remove it.

 |

**
Library Drop-Down List
**

 |
Lets you access all the loaded libraries in the level.

 |

**
Reload Library
**

 |
Discards all the changes made to the library and reloads the library from the HDD.

 |

##
Item Toolbar

**
Action
**

 |
**
Description
**

 |

**
Add New Item
**

 |
Creates a new archetype object, based on a selectable entity class script; you need to define a Group (folder) and a Name.

 |

**
Clone Library Item
**

 |
Duplicates the selected Archetype entity; uses the same name and adds a number to it.

 |

**
Remove Item
**

 |
Deletes the selected archetype object.

 |

**
Assign Item to Selected Objects
**

 |
Assigns the selected Archetype entity to the currently selected Archetype entity in the Perspective view.

 |

**
Reload Item
**

 |
Resets the scene Archetype entities of this type.

 |

**
Get Material from Selection
**

 |
Assigns the material from the currently selected item.

 |

##
Standard Toolbar

**
Action
**

 |
**
Description
**

 |

**
Undo
**

 |
Undoes the last action - set the number in
**
Tools > Preferences
**
.

 |

**
Redo
**

 |
Redoes the last action - set the number in
**
Tools > Preferences
**
.

 |

**
Copy Item
**

 |
Copies the XML script of the current item to the clipboard.

 |

**
Paste Item
**

 |
Pastes the item from the clipboard.

 |

##
Library Lister

The library lister organizes all the Archetype entities of the currently selected library, by group; browse through the groups in a similar manner to as is done in the standard Windows Explorer.

##
Class Properties Window

The Class Properties window displays all the values that are defined in the entity scripts.

These scripts are created by programmers.

##
Objects Parameters

The window holds general object parameters, which exist in all the Archetype entities. They are independent of the separate entity scripts.

##
Model Preview

This option shows the selected Archetype entity in a special, perspective, model preview window.

**
Mouse Control
**

 |
**
Function
**

 |

**
Click
**

 |
Rotates the view.

 |

**
Right-click
**

 |
Zooms the view.

 |
