# Prefabs

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/36866251
- Page ID: 36866251
- Breadcrumb: Entities and Tools > Entities Overview > Prefabs
- Parent: Entities Overview

## Child Pages

- [Prefab Communication](Prefabs/Prefab%20Communication.md)
- [Run-time Prefabs](Prefabs/Run-time%20Prefabs.md)

## Content

![Image](https://www.cryengine.com/docs/static/attachments/36840438)

##
Overview

##
Table of Contents

Prefabs are groups of objects that can be placed in the level as instances. An instance is an object that is an exact copy of every other object of the same type.

Altering one prefab universally applies the changes to each instance of the prefab object.

Prefabs are separate assets and can be found by using the Asset Browser.

![Image](https://www.cryengine.com/docs/static/attachments/36840437)

Prefab Logic
Prefabs support Flow Graph logic, so make sure you check out the
[Prefab Communication](Prefabs/Prefab%20Communication.md)
 tutorial for more information.

[Creating a New Prefab](#creating-a-new-prefab)
[Using Prefabs](#using-prefabs)
[Prefab Object Parameters](#prefab-object-parameters)

##
Creating a New Prefab

First, place several objects in the level that you wish to change to a prefab. Select all the objects that you require. Next,
right click
**

**
on one of the selected objects and choose Create Prefab.

![Image](https://www.cryengine.com/docs/static/attachments/36840436)

Now, fill in a Group and Name for the new prefab. The prefab will be created in the currently selected library.

The prefab has now been created and is ready to be used in the level.

Alternatively, a prefab may be created by dragging and dropping multiple objects of choice from the Level Explorer into the Asset Browser. Objects can be picked from multiple layers.

![Image](https://www.cryengine.com/docs/static/attachments/36842171)

Once assigned a custom name, the created prefab will appear listed within the Level Explorer.

##
Using Prefabs

Previously created prefabs that have been saved within a project's Asset directory can be used in a level by dragging and dropping them into the Viewport from the Asset Browser.

Doing so automatically creates a numbered listing for that prefab's instance in the Level Explorer; the first instance of a prefab
*
shack_indoor
*
, for example, will be listed as
*
shack_indoor-1
*
 within the Explorer. Subsequent instances will be numbered
*
shack_indoor-2
*
,
*
shack_indoor-3
*
, and so forth.

##
Selecting All Prefab Instances

With one more instances of a prefab selected within the Level Explorer or Viewport, right-clicking on either of the selected instances generates a context menu with the option to
**
Select All Prefabs of Type "
*
<prefab-name>
*
"
**
.

Clicking this option selects all instances of the selected prefab that have been included within a level, even if these are nested in other prefabs.

![Image](https://www.cryengine.com/docs/static/attachments/36847510)

*
Select all Prefabs of Type "Open"
*

In the above example, right-clicking on a prefab
*
open
*
 brings up a context menu with the option to
**
Select all Prefabs of Type "Open"
**
. Clicking this selects all prefabs of the same type included within the level.

Alternatively, users may select one or more instances of a prefab within the Level Explorer or Viewport, and use the
**
prefab.select_all_instances_of_type
**
console command to obtain the same result.

Note that the
**
Select all Prefabs of Type "<prefab-name>"
**
will not appear
**

**
if instances of multiple different prefabs are selected, or when the selected asset is not a prefab.

##
Prefab Object Parameters

There are several important parameters when working with prefabs:

**
Prefab
**
 |

**
Auto Update All Instances
**

 |
When checked, changes made to one instance of the prefab will be updated in all other instances.

 |

**
Transform Pivot Mode
**

 |
Lets you move the pivot of the prefab.

 |

Operators
 |

**
Objects
**

 |

-
**
Extract All -
**
 Extracts the objects from this instance of the prefab, turning them into separate objects again.

-
**
Clone All -
**
 Duplicates the objects in this instance of the prefab as separate objects, allowing you to drag them out as a group, but then edit them separately.

 |

**
Edit
**

 |

-
**
Open -
**
 Lets you open the prefab and edit the individual objects within it without extracting the objects, keeping the prefab intact.
Any changes will be updated in other instances of the prefab as well.

-
**
Close -
**
(Appears when prefab is opened)
Closes the prefab again and saves the edits.

 |

**
Prefab Tools
**

 |

-
**
Pick -
**
 Select another object to add to the prefab.

-
**
Clear -
**

Empties the prefab, removing the objects inside of it. The prefab itself will still exist in your scene.
 |

**
Prefab Objects
**

 |
A list of the objects that make up the prefab.

 |
