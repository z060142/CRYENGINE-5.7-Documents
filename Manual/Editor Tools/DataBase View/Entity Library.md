# Entity Library

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/36869335
- Page ID: 36869335
- Breadcrumb: Editor Tools > DataBase View > Entity Library
- Parent: DataBase View

## Content

Entity Library tab on DataBase View is no longer supported in CRYENGINE. It will be removed from the engine in the future and some features might not function as expected.

##
Overview

An Archetype Entity is based on a regular Entity and specifies individual parameter values for that Entity itself. If the value of an Archetype parameter is changed, all the instances of that Archetype in the scene will be updated automatically.

Archetype Entities are organized in libraries which can be created in
[/docs/static/engines/cryengine-5/categories/23756816/pages/36869094](
DataBase View
)
.

This means that technical level designers can predefine variations of Entity classes as Archetype Entities that can be used throughout the whole game. For global changes affecting all instances, the Archetype Entity just needs to be changed once in the Database View.

[Image: /docs/static/attachments/36849031]

##
Toolbar

[Image: /docs/static/attachments/36849032]

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
*
Game\Libs\EntityArchetypes.
*

Some prefabs can contain links to archetype objects; therefore, it is useful to load all the available Archetype libraries into the level.

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
Removes the currently selected library from the level; it needs to be manually deleted from the hard drive if it is required to be permanently removed.

 |

**
Library Drop-Down List
**

 |
Lets users access all the loaded libraries in the level.

 |

**
Reload Library
**

 |
Discards all the changes that has been made to the library and reloads the library from the HDD.

 |

##
Item Toolbar

[Image: /docs/static/attachments/44108011]

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
Creates a new archetype object based on a selectable entity class script; a Group (folder) and a Name needs to be defined.

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

[Image: /docs/static/attachments/44108012]

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
Undoes the last action.

 |

**
Redo
**

 |
Redoes the last action.

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
Entity Library Layout

##
Library Lister

The library Lister organizes all the Archetype entities of the currently selected library, by group.

##
Class Properties Window

The Class Properties window displays all the values that are defined in the entity scripts.

These scripts are created by programmers.

##
Objects Params

The window holds general object parameters that exist in all the Archetype entities. They are independent of the separate entity scripts.

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

[#toolbar](
Toolbar
)
[#entity-library-layout](
Entity Library Layout
)
[#toolbar](
Toolbar
)
[#entity-library-layout](
Entity Library Layout
)
Entity Library tab on DataBase View is no longer supported in CRYENGINE. It will be removed from the engine in the future and some features might not function as expected.

##
Overview

An Archetype Entity is based on a regular Entity and specifies individual parameter values for that Entity itself. If the value of an Archetype parameter is changed, all the instances of that Archetype in the scene will be updated automatically.

Archetype Entities are organized in libraries which can be created in
[/docs/static/engines/cryengine-5/categories/23756816/pages/36869094](
DataBase View
)
.

This means that technical level designers can predefine variations of Entity classes as Archetype Entities that can be used throughout the whole game. For global changes affecting all instances, the Archetype Entity just needs to be changed once in the Database View.

[Image: /docs/static/attachments/36849031]

##
Toolbar

[Image: /docs/static/attachments/36849032]

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
*
Game\Libs\EntityArchetypes.
*

Some prefabs can contain links to archetype objects; therefore, it is useful to load all the available Archetype libraries into the level.

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
Removes the currently selected library from the level; it needs to be manually deleted from the hard drive if it is required to be permanently removed.

 |

**
Library Drop-Down List
**

 |
Lets users access all the loaded libraries in the level.

 |

**
Reload Library
**

 |
Discards all the changes that has been made to the library and reloads the library from the HDD.

 |

##
Item Toolbar

[Image: /docs/static/attachments/44108011]

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
Creates a new archetype object based on a selectable entity class script; a Group (folder) and a Name needs to be defined.

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

[Image: /docs/static/attachments/44108012]

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
Undoes the last action.

 |

**
Redo
**

 |
Redoes the last action.

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
Entity Library Layout

##
Library Lister

The library Lister organizes all the Archetype entities of the currently selected library, by group.

##
Class Properties Window

The Class Properties window displays all the values that are defined in the entity scripts.

These scripts are created by programmers.

##
Objects Params

The window holds general object parameters that exist in all the Archetype entities. They are independent of the separate entity scripts.

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
