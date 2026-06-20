# DataBase View

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/36869094
- Page ID: 36869094
- Breadcrumb: Editor Tools > DataBase View
- Parent: Editor Tools

## Child Pages

- [Entity Library](DataBase View/Entity Library.md)
- [Particles Tab (Legacy Particle Editor)](DataBase View/Particles Tab (Legacy Particle Editor).md)
- [Game Tokens](DataBase View/Game Tokens.md)

## Content

Entity Library, Particles and GameTokens tabs on DataBase View are no longer supported in CRYENGINE. They will be removed from the engine in the future and some features might not function as expected.

##
Overview

The DataBase View panel is used to organize the game item libraries. These libraries can be accessed and modified on this panel.

Unlike other panels that can be found under the Tools section, DataBase View is actually not a tool and it serves as a hub which lets users to access libraries like the Entity Library, the Particle Editor Legacy and the GameTokens database. In order to access these separate panels on the DataBase View panel, click on the tabs above the toolbar.

DataBase View can be found on
**
Tools → DataBase View
**
.

For more information about the DataBase View tabs and their functions, please refer to the
[/docs/static/engines/cryengine-5/categories/23756816/pages/36869335](
Entity Library
)
,
[/docs/static/engines/cryengine-5/categories/23756816/pages/36868751](
Particle Editor Legacy
)
 and
[/docs/static/engines/cryengine-5/categories/23756816/pages/36869337](
Game Tokens
)
 sections.

[Image: /docs/static/attachments/36848708]

##
Benefits of Using Libraries

The main use of the library system for entities and particles is to make variations on top of the standard default setting that can be found within the Entity list on the Create Object tool.

As an example, an AI entity can be implemented into a level via the
**
Create Object
**
 tool by choosing
**
Entity → AI → Characters → Human
**
.

This is the most basic reference of an AI entity,
or any entity,
 in the engine. This AI's properties can be modified directly on the AI that has just been added via the Properties panel. If the user wants to make variations of the AI via different weapon load-outs such as rifle, rifle + pistol, shotgun etc, or if a large number of AI has been set up, users would have to individually configure each placed entity in the world.

Storing these AI variations into a library means you can create a template within the database, detailing the load-out, health or faction of the AI entity, and then populate the level via these Entity Archetypes.

The benefit of using a library is that now the user only has to configure the template once, here in the database. Every instance of this Entity Archetype that has been placed on the level will automatically inherit the settings defined within the database. To make changes to the configuration of the entity, simply modify the item in the database and all the instances you placed in the level will also automatically inherit these updates.

##
Library Types

There are 2 ways libraries are stored:

-
**
Level-based
**

-
**
Library-based
**
A level-based library is local
*
only to that level,
*
 hence to the name. Another level in the game
*
cannot
**

**
*
view the contents of another level's based library.

A Library-based library,
*
can be shared
*
 between levels. Think of it as a
*
global
*
 library. Since it's not tied down to any specific level, all levels may access the contents of a global library. These external, or global, libraries are saved as
**
.xml
**
 files.

##
Library Locations

-
Level-based databases are baked into the level files so there isn't a designated location for them.

-
Library-based databases are stored within a specific area within the game folder:
Library Type
 |
Location
 |

Entity

 |
*
GameSDK\Libs\EntityArchetypes
*

 |

Particles

 |
*
GameSDK\Libs\Particles
*

 |

Game Tokens

 |
*
GameSDK\Libs\GameTokens
*

 |

All Libraries have two or three things in common:

-
On the
*
top
*
is  a toolbar with various tools to interact with an individual library.

-
On the
*
left
*
 is the items browser.

-
On the
*
right
*
 are their properties.

-
Additionally, some libraries have a
*
3D Preview window
*
.

##
Menu

The Menu can be accessed via the
[Image: /docs/static/attachments/44966586]
 icon on the top-right corner of the panel. When clicked, it reveals the

**
Help
**
 sub-menu
with the

**
Go to documentation...
**
 option that directs the user to the documentation page for this tool.

##
Toolbar

The toolbar can be divided into two groups: buttons for library control and buttons for library item control.

##
Library Control

[Image: /docs/static/attachments/44966589]

Button

 |
Description

 |

**
Load Library
**

 |
Loads a library and adds it to the Library drop down List.

 |

**
Save Modified Libraries
**

 |
Saves the changes made to the active library.

 |

**
Add Library
**

 |
Adds a new, custom library.

 |

**
Remove Library
**

 |
Removes the selected library.

 |

**
Library List
**

 |
Drop-down list of libraries within the current tab.

 |

**
Reload Library
**

 |
Reloads the active library. All changes that has been made since the last save will be lost.

 |

##
Item Control

[Image: /docs/static/attachments/44966588]

Button

 |
Description

 |

**
Add New Item
**

 |
Adds a new item to the active library. Depending on the currently active Tab, it will offer you different options:

-
**
Entity -
**
 Defines the class, then the folder and item name

-
**
Others Tabs -
**
 Offer the option to only add a
folder and item name

 |

**
Clone Library Item
**

 |
Makes an exact copy of the selected item and pastes it in the same group.

 |

**
Remove Item
**

 |
Deletes the selected item from the database.

 |

**
Assign Item to Selected Objects
**

 |
Select an item in the 3D Viewport and assign the highlighted item in the DB to the selection.

 |

**
Get Properties From Selection
**

 |
Select an item in the
3D Viewport and this will open up the corresponding DB and highlight the entry in the list.

 |

**
Reload Item
**

 |
Reloads the selected item.

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
Redoes a previously undone action.

 |

**
Copy Item
**

 |
Copies the selected item.

 |

**
Paste Item
**

 |
Pastes the copied item.

 |

 |

Only available in the Particles Library

 |

 |

**
Button
**

 |
**
Description
**

 |

Reset Item to Default

 |
Resets all the properties of the selected item to their default values.

 |

Enable/Disable Item and All Children

 |
This feature is used to enable / disable the hierarchy within the particle itself. Useful for debugging particle effects where 1 child emitter is causing problems, but you don't know which one.

By disabling the individual emitters within a particle effect, or all at once, users can track down which is the offending effect.

 |

##
Adding Items to a Database

Adding new entries into a library is the same process for Particles and Game Tokens. However, the Entities are added to the libraries with one additional step which is to define what
*
type
*
 of entity it is.

##
Entities

Either have an existing library open or just use the level library.

Add a new database item, and the first window to pop up allows selecting which class of entity to add.

Note how the structure of the available entities is similar to the list available in the creation panel (add entity).

In this example we are adding a new AI (human class) to the database:

[Image: /docs/static/attachments/36848715]

Then once the class is selected, the next window that appears is the
**
Group
**
 and
**
Name
**
 options. This is where the structure of how the info is displayed back to yourself can be organized.

[Image: /docs/static/attachments/44966591]

Define a
**
Group
**
 to logically keep items within the same area, and define a
**
Name
**
 to how this Entity Archetype is going to be called. To continue on with the example, let's set the group to
**
Enemy
**
. This will place the new item into the
**
Enemy
**
 folder that already exists in the
**
Characters
**
 database.

The names of the existing entries describe what the contents of this Archetype is. The naming convention is down to the user, but using names that reflect the main purpose, such as an enemy character, with easy difficulty settings and equipped with a rifle, is advised because the developers would benefit from a simple naming convention during production.

##
Particles and Game Tokens

Particles and game-tokens work in the same way as entities, but without selecting a class.

Add a new item and a pop-up will appear. Use the
**
Group
**
 to logically keep items within the same area, and use the
**
N
**
**
ame
**
 to define what this item is going to be called.

DataBase View is no longer used to create and store prefabs. For more information, please refer to the
[/docs/static/engines/cryengine-5/categories/23756816/pages/36866251](
Prefabs
)
documentation.
[#benefits-of-using-libraries](
Benefits of Using Libraries
)
[#menu](
Menu
)
[#toolbar](
Toolbar
)
[#adding-items-to-a-database](
Adding Items to a Database
)
