# Level Explorer

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/35259541
- Page ID: 35259541
- Breadcrumb: Editor Tools > Level Editor Tab > Level Explorer
- Parent: Level Editor Tab

## Child Pages

- [Object Linking](Level%20Explorer/Object%20Linking.md)

## Content

## Overview

The **Level Explorer** lists every object that has been added to a level, allowing users to browse through them without affecting their states. It also allows users to hide, freeze and search for objects within the Viewport.

![Image](https://www.cryengine.com/docs/static/attachments/44958428) *Level Explorer Overview*

Objects may further be grouped into layers, which may in turn be locked, hidden or grouped into folders.

This is particularly useful in instances where multiple objects need to be locked/hidden all at once, where different layers of objects need to be displayed at differing points of time within a game, or simply to prevent members of your development team from working on the same level objects simultaneously.

As an example, a cinematic demonstrating the destruction of a village could be designed to use different layers of assets before and after the event of destruction. By default the **Level****Explorer** is displayed in the bottom-left panel of the Sandbox interface, but it can also be accessed via ** Tools → Level Editor → Level Explorer.**

### Menu

The Level Explorer's Main Menu can be found under the![Image](https://www.cryengine.com/docs/static/attachments/36838198) icon in the top-right corner and contains the following options:

#### File

Option | Description
--- | ---
**New Layer** | Creates a new layer in the Level Explorer.
**New Folder** | Creates a new folder in the Level Explorer.
**Import...** | Brings up the system's File Explorer to locate a previously exported layer; layer files must carry a **.lyr** extension and may be imported into multiple levels as required.

#### Edit

Option | Description
--- | ---
**Delete** | Deletes the selected object(s)/layer(s)/folder(s).
**Find** | Allows users to search for objects within a level by using the Search Bar in the Level Explorer.
**Visible** | Toggles the visibility of the object(s)/layer(s)/folder(s) currently selected in the Level Explorer.
**Isolate Visibility** | Toggles the visibility of all object(s)/layer(s)/folder(s) in the Viewport, except the object/layer/folder currently selected in the Level Explorer.
**More** | **Hide All** | Hides all folders/layers of objects in the Viewport. --- | --- ** Unhide All** | Makes visible all folders/layers of objects in the Viewport. ** Toggle Child Object Visibility** | Toggles the visibility of all objects that belong to the currently selected layer. ** Hide Child Objects** | Hides all objects that belong to the currently selected layer, in the Viewport. ** Unhide Child Objects** | Makes visible all objects that belong to the currently selected layer, in the Viewport.
**Hide All** | Hides all folders/layers of objects in the Viewport.
**Unhide All** | Makes visible all folders/layers of objects in the Viewport.
**Toggle Child Object Visibility** | Toggles the visibility of all objects that belong to the currently selected layer.
**Hide Child Objects** | Hides all objects that belong to the currently selected layer, in the Viewport.
**Unhide Child Objects** | Makes visible all objects that belong to the currently selected layer, in the Viewport.
**Locked** | Locks the current object/folder/layer, preventing it from being edited. A locked object/folder/layer is indicated by the![Image](https://www.cryengine.com/docs/static/attachments/44960484) icon in the Level Explorer. Learn more about locking and unlocking in the [Locking Layers/Folders/Objects](Level%20Explorer.md#LevelExplorer-lock)section below.
**Isolate Locked** | Toggles the lock on all object(s)/layer(s)/folder(s), except the object/layer/folder currently selected in the Level Explorer.
**More** | **Lock All** | Locks all folders/layers of objects that have been placed in the current level. --- | --- ** Unlock All** | Unlocks all folders/layers of objects in the Viewport. ** Toggle Child Object Locking** | Locks/unlocks all objects that belong to the currently selected layer. ** Lock Child Objects** | Locks all objects that belong to the currently selected layer. ** Unlock Child Objects** | Unlocks all objects that belong to the currently selected layer.
**Lock All** | Locks all folders/layers of objects that have been placed in the current level.
**Unlock All** | Unlocks all folders/layers of objects in the Viewport.
**Toggle Child Object Locking** | Locks/unlocks all objects that belong to the currently selected layer.
**Lock Child Objects** | Locks all objects that belong to the currently selected layer.
**Unlock Child Objects** | Unlocks all objects that belong to the currently selected layer.
**Open in File Explorer** | Opens the file explorer and locates the selected layer's **.lyr** file in the project's directory of assets.
**Copy Name** | Copies the name of the selected layer/folder to the clipboard, so that it can pasted into another application.
**Copy Path** | Copies the file path of the selected layer/folder to the clipboard, so that it can be pasted into another application.

#### View

Option | Description
--- | ---
**Show Full Hierarchy** | Lists all existing layers and folders in the Level Explorer; these layers/folders can also be expanded to reveal the objects they contain. The **Show Full Hierarchy** option can also be toggled by clicking the![Image](https://www.cryengine.com/docs/static/attachments/36842404) button on the Level Explorer's View toolbar.
**Show Layers** | Lists all created layers and folders without displaying the objects they contain. Alternatively toggled by clicking the![Image](https://www.cryengine.com/docs/static/attachments/36842405) button on the Level Explorer's View toolbar.
**Show All Objects** | Lists all existing objects within the Level Explorer, without displaying the layers/folders these objects belong to. Also toggled by clicking the![Image](https://www.cryengine.com/docs/static/attachments/36842406) button on the Level Explorer's View toolbar.
**Show Active Layer Contents** | Lists the contents of the Active Layer in the Level Explorer. An Active Layer is the primary layer within which all inserted objects are placed by default; any layer might be set as the Active layer by double-clicking it. **Show Active Layer Contents** can also be toggled by clicking the![Image](https://www.cryengine.com/docs/static/attachments/36842407) button on the Level Explorer's View toolbar.
**Expand All** | Lists the entire hierarchy of created folders, layers and the objects they contain.
**Collapse All** | Collapses the hierarchy of created folders, layers and the objects they contain, so that only the top-most levels within this hierarchy are displayed.
**Sync Selection** | When enabled, the Viewport camera will focus on an object when that object is selected in the Level Explorer, and vice versa. **Sync Selection** may also be enabled/disabled by clicking the![Image](https://www.cryengine.com/docs/static/attachments/36842408) button on the Level Explorer's Sync Selection toolbar.
**Apply Filter** | Previously created filters are listed under this sub-menu. When a filter is selected, only those objects/layers/folders that meet the search criteria defined by the filter are displayed in the Level Explorer. Applied filters can be cleared either by clicking the selected filter again, or by clicking the **Clear Criteria** option from the ** Apply Filter** sub-menu. Refer to the [Filter](Level%20Explorer.md#LevelExplorer-LEAnchor)section on this page for more information on creating and using filters.
**Adaptive Layout** | When **Adaptive Layout** is enabled, the positions of the toolbars change with respect to the size of the Level Explorer window.

#### Focus on Active Layer

Highlights the Active Layer in the Level Explorer.

An Active Layer is the primary layer within which all inserted objects are placed by default; any layer might be set as the Active layer by double-clicking it, or by right-clicking it and selecting the **Set as Active Layer** option from the context menu.

#### Toolbars

**Option** | **Description**
--- | ---
**Customize** | Opens the toolbar customization window allowing users to customize existing toolbars, and/or create new toolbars.
**Lock Toolbars** | When disabled, the positions of toolbars and spacers can be changed by drag and drop.
**Spacers** | The following options allow users to use spacers in positioning their toolbars. **Insert Expanding Spacer** | Adds an expanding spacer to the toolbar layout; an expanding spacer pushes all elements situated at its ends to the edge of a panel. --- | --- ** Insert Fixed Spacer** | Adds a fixed spacer, which has a fixed size of one icon. The ** Spacers** menu options are only available when ** Toolbars → Lock Toolbars** is disabled.
**Insert Expanding Spacer** | Adds an expanding spacer to the toolbar layout; an expanding spacer pushes all elements situated at its ends to the edge of a panel.
**Insert Fixed Spacer** | Adds a fixed spacer, which has a fixed size of one icon.
**Toolbars** | Lists all default and custom toolbars created for the Level Explorer, allowing users to select which toolbar they'd like to hide or display. By default, the following two toolbars are available in the Level Explorer: **Sync Selection** |![Image](https://www.cryengine.com/docs/static/attachments/36842408) | When enabled, the Viewport camera will focus on an object when that object is selected in the Level Explorer, and vice versa. --- | --- --- | ---![Image](https://www.cryengine.com/docs/static/attachments/36842408) | When enabled, the Viewport camera will focus on an object when that object is selected in the Level Explorer, and vice versa. ** View** |![Image](https://www.cryengine.com/docs/static/attachments/36842404) | Lists all existing layers and folders in the Level Explorer; these layers/folders can also be expanded to reveal the objects they contain. --- | ---![Image](https://www.cryengine.com/docs/static/attachments/36842405) | Lists all created layers and folders without displaying the objects they contain.![Image](https://www.cryengine.com/docs/static/attachments/36842406) | Lists all existing objects within the Level Explorer, without displaying the layers/folders these objects belong to.![Image](https://www.cryengine.com/docs/static/attachments/36842407) | Lists the contents of the Active Layer in the Level Explorer.![Image](https://www.cryengine.com/docs/static/attachments/36842404) | Lists all existing layers and folders in the Level Explorer; these layers/folders can also be expanded to reveal the objects they contain.![Image](https://www.cryengine.com/docs/static/attachments/36842405) | Lists all created layers and folders without displaying the objects they contain.![Image](https://www.cryengine.com/docs/static/attachments/36842406) | Lists all existing objects within the Level Explorer, without displaying the layers/folders these objects belong to.![Image](https://www.cryengine.com/docs/static/attachments/36842407) | Lists the contents of the Active Layer in the Level Explorer.
**Sync Selection** | ![Image](https://www.cryengine.com/docs/static/attachments/36842408) | When enabled, the Viewport camera will focus on an object when that object is selected in the Level Explorer, and vice versa. --- | ---
![Image](https://www.cryengine.com/docs/static/attachments/36842408) | When enabled, the Viewport camera will focus on an object when that object is selected in the Level Explorer, and vice versa.
**View** | ![Image](https://www.cryengine.com/docs/static/attachments/36842404) | Lists all existing layers and folders in the Level Explorer; these layers/folders can also be expanded to reveal the objects they contain. --- | ---![Image](https://www.cryengine.com/docs/static/attachments/36842405) | Lists all created layers and folders without displaying the objects they contain.![Image](https://www.cryengine.com/docs/static/attachments/36842406) | Lists all existing objects within the Level Explorer, without displaying the layers/folders these objects belong to.![Image](https://www.cryengine.com/docs/static/attachments/36842407) | Lists the contents of the Active Layer in the Level Explorer.
![Image](https://www.cryengine.com/docs/static/attachments/36842404) | Lists all existing layers and folders in the Level Explorer; these layers/folders can also be expanded to reveal the objects they contain.
![Image](https://www.cryengine.com/docs/static/attachments/36842405) | Lists all created layers and folders without displaying the objects they contain.
![Image](https://www.cryengine.com/docs/static/attachments/36842406) | Lists all existing objects within the Level Explorer, without displaying the layers/folders these objects belong to.
![Image](https://www.cryengine.com/docs/static/attachments/36842407) | Lists the contents of the Active Layer in the Level Explorer.

When a tool has a toolbar, whether this is a default one or a custom one, the options above are also available when right-clicking in the toolbar area (only when a toolbar is already displayed).

#### Help

Opens the user documentation for this tool in the web browser.

#### Layer

**Option** | **Description**
--- | ---
**Set as Active Layer** | When a layer is selected in the Level Explorer, this option sets that layer as the Active Layer. By default, all inserted objects are placed in the Active Layer.
**Lock Read-Only Layers** | Locks all layers that have been set to Read-Only mode on disk. This is particularly useful when using [version control](../Version%20Control%20System.md), allowing only those layers that have been marked for editing to be modified.
**More** | **Reload** | Reloads the scripts of all legacy (LUA) entities included within the selected layer. --- | --- ** Exportable** | ** Exportable** | Allows the selected layer to be exported and saved as an external **.lyr** file. --- | --- ** Exportable (Pak)** | Allows the selected layer to be exported and saved as a **.pak** file. ** Exportable** | Allows the selected layer to be exported and saved as an external **.lyr** file. ** Exportable (Pak)** | Allows the selected layer to be exported and saved as a **.pak** file. ** Auto-Load** | ** Auto-load** | When enabled, the selected layer and its contents will be loaded in the game. Choosing not to load a layer right away improves performance. --- | --- ** Auto-load** | When enabled, the selected layer and its contents will be loaded in the game. Choosing not to load a layer right away improves performance. ** Physics** | ** Physics** | Turns on the physics of physicalized objects in the selected layer. --- | --- ** Physics** | Turns on the physics of physicalized objects in the selected layer. ** Platforms** | Allows users to specify which platforms (** PC**, ** PS4**, or ** Xbox One**) the selected layer and its contents are to be displayed on.
**Reload** | Reloads the scripts of all legacy (LUA) entities included within the selected layer.
**Exportable** | **Exportable** | Allows the selected layer to be exported and saved as an external **.lyr** file. --- | --- ** Exportable (Pak)** | Allows the selected layer to be exported and saved as a **.pak** file.
**Exportable** | Allows the selected layer to be exported and saved as an external **.lyr** file.
**Exportable (Pak)** | Allows the selected layer to be exported and saved as a **.pak** file.
**Auto-Load** | **Auto-load** | When enabled, the selected layer and its contents will be loaded in the game. Choosing not to load a layer right away improves performance. --- | ---
**Auto-load** | When enabled, the selected layer and its contents will be loaded in the game. Choosing not to load a layer right away improves performance.
**Physics** | **Physics** | Turns on the physics of physicalized objects in the selected layer. --- | ---
**Physics** | Turns on the physics of physicalized objects in the selected layer.
**Platforms** | Allows users to specify which platforms (**PC**, ** PS4**, or ** Xbox One**) the selected layer and its contents are to be displayed on.

### The List View

Clicking on the titles of any of the columns within the Level Explorer's list of objects, layers and folders, automatically sorts the contents of that column in ascending/descending alphabetical order. You may further choose to display/hide specific columns via the context menu generated by right-clicking a column title.

![Image](https://www.cryengine.com/docs/static/attachments/44960477) *Right-clicking a column title*

This context menu contains the following as its primary items.

Column | Description
--- | ---
**Layer Color** | Displays colors assigned to objects, layers and folders within the Level Explorer's list. Colors may be assigned to an item within the Level Explorer by right-clicking it, and selecting the **Color** option from the context menu. Both preset and custom colors may be assigned.![Image](https://www.cryengine.com/docs/static/attachments/36842410) * Color option*
**Visible** | When enabled, visible/invisible objects, layers and folders are indicated by the![Image](https://www.cryengine.com/docs/static/attachments/44960483)/![Image](https://www.cryengine.com/docs/static/attachments/44960487) icon in the Level Explorer.
**Frozen** | Locked/unlocked objects, layers and folders are indicated by the![Image](https://www.cryengine.com/docs/static/attachments/44958434)/![Image](https://www.cryengine.com/docs/static/attachments/44960484) icon in the Level Explorer, when this option is enabled.
**Name** | The names of all objects, layers and folders are displayed in the Level Explorer, when this option is enabled.
**Objects** | This menu option is not available when **Show Layers** is active. Lists additional columns that can be added to the Level Explorer, to display information relevant to the objects included within a level. The following columns are available: Column | ** Description** --- | --- ** Layer** | Displays the name of the layer to which an object belongs. ** Object Type** | Indicates the general [type](Create%20Object.md) of an object. ** Type** | Provides a more specific description of an object's type, in addition to its ** Object Type** property. The ** Type** field could also be a modifiable string, as in the case of creating prefabs, wherein this field would indicate the user defined name assigned to a prefab. ** Default Material** | Displays the file path of the default material used by an object, when applicable. ** Custom Material** | Displays the file path of the user defined material assigned to an object in place of their default material, where applicable. ** Breakable** | Indicates whether a [breakable object](../../Asset%20Prep%20(External)/Asset%20Exporting%20Overview/Geometry%20Creation%20Overview/Interactive%20Geometry/Breakable%20Objects.md) is Jointed Breakable, Destroyable or Jointed Destructable. ** Smart Object** | Names the[Smart Object](../Deprecated%20Tab/Smart%20Objects%20Editor.md) rule that associates an object with another. Smart Objects are those which have been set up to interact with other objects within a game. ** Flow Graph** | Displays the names of the [Flow Graph](../Flow%20Graph.md) containers where the selected Entity is referenced. ** Geometry** | Displays the file path of an object's Crytek Geometry Format (**.cgf**) file, that contains information about the object's 3D geometry. ** Instances** | Indicates the number of times an object is used within the current level. ** LOD count** | Indicates the number of [Level of Detail](../../Asset%20Prep%20(External)/Asset%20Exporting%20Overview/Geometry%20Creation%20Overview/LODs.md) objects (LOD's) associated with an object, where applicable. ** Spec** | Indicates the minimal spec setting of a listed object. An object's Spec value defines the game detail setting (low/medium/high/custom spec) within and above which the object is rendered within a level. ** AI GroupID** | Identifies the AI Group associated with an AI character object included within a level. ** Linked to** | Indicates the name of the object to which the current Entity might be linked. If the current Entity is linked to the bone of a character with a skeletal mesh, the ** Linked to** column of the Entity will display the name of the bone it is linked to. Please refer to the [Object Linking](Level%20Explorer/Object%20Linking.md) page for more information on creating links between Entity-type objects.
Column | **Description**
**Layer** | Displays the name of the layer to which an object belongs.
**Object Type** | Indicates the general [type](Create%20Object.md) of an object.
**Type** | Provides a more specific description of an object's type, in addition to its **Object Type** property. The ** Type** field could also be a modifiable string, as in the case of creating prefabs, wherein this field would indicate the user defined name assigned to a prefab.
**Default Material** | Displays the file path of the default material used by an object, when applicable.
**Custom Material** | Displays the file path of the user defined material assigned to an object in place of their default material, where applicable.
**Breakable** | Indicates whether a [breakable object](../../Asset%20Prep%20(External)/Asset%20Exporting%20Overview/Geometry%20Creation%20Overview/Interactive%20Geometry/Breakable%20Objects.md) is Jointed Breakable, Destroyable or Jointed Destructable.
**Smart Object** | Names the[Smart Object](../Deprecated%20Tab/Smart%20Objects%20Editor.md) rule that associates an object with another. Smart Objects are those which have been set up to interact with other objects within a game.
**Flow Graph** | Displays the names of the [Flow Graph](../Flow%20Graph.md) containers where the selected Entity is referenced.
**Geometry** | Displays the file path of an object's Crytek Geometry Format (**.cgf**) file, that contains information about the object's 3D geometry.
**Instances** | Indicates the number of times an object is used within the current level.
**LOD count** | Indicates the number of [Level of Detail](../../Asset%20Prep%20(External)/Asset%20Exporting%20Overview/Geometry%20Creation%20Overview/LODs.md) objects (LOD's) associated with an object, where applicable.
**Spec** | Indicates the minimal spec setting of a listed object. An object's Spec value defines the game detail setting (low/medium/high/custom spec) within and above which the object is rendered within a level.
**AI GroupID** | Identifies the AI Group associated with an AI character object included within a level.
**Linked to** | Indicates the name of the object to which the current Entity might be linked. If the current Entity is linked to the bone of a character with a skeletal mesh, the **Linked to** column of the Entity will display the name of the bone it is linked to. Please refer to the [Object Linking](Level%20Explorer/Object%20Linking.md) page for more information on creating links between Entity-type objects.
**Layers** | This menu option is not available when **Show All Objects** or **Show Active Layer Contents** is enabled. Lists additional columns that can be added to the Level Explorer to display information relevant to the layers in a level. These columns are: ** Column** | ** Description** --- | --- ** Exportable** | Indicates whether a layer of objects may be exported and saved as an external **.lyr** file. Right-clicking a layer and selecting the ** More (Layer) → Exportable** option from its context menu will enable it to be exported as a **.lyr** file. ** Exportable to Pak** | Indicates whether a layer may be exported and saved as an external PAK file of **.pak** extension. Right-clicking a layer and selecting the ** More (Layer) → Exportable to Pak** option from its context menu will enable it to be exported as a **.pak** file. ** Loaded in Game** | Indicates whether a layer will be loaded in-game; choosing not to load a layer and its objects right away will improve performance. To prevent a layer from being loaded in-game, right-click the layer and disable the** More (Layer) → Auto-Load** option from its context menu. ** Has Physics** | Indicates whether the physics of physicalized objects in a layer have been enabled or not. To enable the physics of physicalized objects within a layer, right-click the layer and select the ** More (Layer) →****Physics** option from its context menu. ** Platform** | Lists the platforms (** PC, PS4, Xbox One**) across which a layer and its objects are to be displayed in the game level. These platforms are set by right-clicking a layer and ticking them in the ** More (Layer) → Platforms** menu.
**Column** | **Description**
**Exportable** | Indicates whether a layer of objects may be exported and saved as an external **.lyr** file. Right-clicking a layer and selecting the ** More (Layer) → Exportable** option from its context menu will enable it to be exported as a **.lyr** file.
**Exportable to Pak** | Indicates whether a layer may be exported and saved as an external PAK file of **.pak** extension. Right-clicking a layer and selecting the ** More (Layer) → Exportable to Pak** option from its context menu will enable it to be exported as a **.pak** file.
**Loaded in Game** | Indicates whether a layer will be loaded in-game; choosing not to load a layer and its objects right away will improve performance. To prevent a layer from being loaded in-game, right-click the layer and disable the**More (Layer) → Auto-Load** option from its context menu.
**Has Physics** | Indicates whether the physics of physicalized objects in a layer have been enabled or not. To enable the physics of physicalized objects within a layer, right-click the layer and select the **More (Layer) →****Physics** option from its context menu.
**Platform** | Lists the platforms (**PC, PS4, Xbox One**) across which a layer and its objects are to be displayed in the game level. These platforms are set by right-clicking a layer and ticking them in the ** More (Layer) → Platforms** menu.

- The Level Explorer is set to **Show Full Hierarchy** by default.
- Pressing **Ctrl+F** when working within the Level Explorer takes you to the Search Bar at its top, allowing you to quickly search for object/layer/folder. When working within another panel/tool that doesn't have a search bar however, ** Ctrl+F** opens a new Level Explorer window with a Search Bar. This window can also be configured in the same way as the default Level Explorer.

### Search Bar

Located at the top of the Level Explorer, the Search Bar enables filtering between listed objects on the basis of their names.

For instance, consider a level containing objects named *village_hut*,* anvil*,* villager* and* man_evil_01*; searching for the term* vil* via the Search Bar will cause the Level Explorer to list only these objects.

### Filter

The Filter button meanwhile allows users to describe specific criteria by which the Level Explorer must list objects.

This criteria is based on the values of various object and layer properties, which can be displayed in columns using the context menu described in [The List View](Level%20Explorer.md#LevelExplorer-Lview)section above. Clicking the Filter button adjacent to the Search Bar reveals options to **Add/Clear Criteria** and** Save/Load** custom filters.

Clicking the **Add Criterion** button presents a drop down menu from which object properties may be picked to specify search criteria; the field adjacent to this drop-down helps specify the property value by which the Level Explorer must filter the list of objects.

![Image](https://www.cryengine.com/docs/static/attachments/36836740) *Add, Clear, Save/Load Criteria*

Depending on the selected object property, these values may be as simple True/False that can be toggled via the check box situated to the left of the value, or as in the case of object properties like **Object Type** or ** Custom Material**, may need to be selected from a separate drop-down or entered manually.

Clicking the![Image](https://www.cryengine.com/docs/static/attachments/36836741) icon, where property values need to selected from a drop-down or entered manually, inverts the specified search criteria; **Clear Criteria** eliminates all specified properties and their respective values. The ** Save/Load Filter** option meanwhile generates a pop-up window which lists all previously created filters along with options to ** Save**, ** Load** or ** Delete** these; a search bar at the top of this pop-up allows filtering through the listed filters.

![Image](https://www.cryengine.com/docs/static/attachments/44960607) *Save/Load Filter*

Right-clicking the filter button makes it possible to quickly choose a saved filter instead of having to use the Save/Load Filter dialog.

### Object and Layer Context Menus

Right-clicking an object or layer in the Level Explorer opens a menu with the following options.

**Option** | **Description**
--- | ---
**New Layer** | Creates a new layer in the Level Explorer.
**New Folder** | Creates a new folder in the Level Explorer.
**Import...** | Brings up the system's File Explorer to locate a previously exported layer; layer files must carry a **.lyr** extension and may be imported into multiple levels as required.
**Edit** | **Rename** | Edits the default/existing name of the selected object, layer, or folder. --- | --- ** Delete** | Deletes the selected object, layer or folder (and its contents) from the level.
**Rename** | Edits the default/existing name of the selected object, layer, or folder.
**Delete** | Deletes the selected object, layer or folder (and its contents) from the level.
**Layer** | **Option** | ** Description** --- | --- ** Set as Active Layer** | When a layer is selected in the Level Explorer, this option sets that layer as the Active Layer. ** Lock Read-Only Layers** | Locks all layers that have been set to Read-Only mode on disk. This is particularly useful when using [version control](../Version%20Control%20System.md), allowing only those layers that have been marked for editing to be modified. ** More** | ** Reload** | Reloads the scripts of all legacy (LUA) entities included within the selected layer. --- | --- ** Exportable** | ** Exportable** | Allows the selected layer to be exported and saved as an external **.lyr** file. --- | --- ** Exportable (Pak)** | Allows the selected layer to be exported and saved as a **.pak** file. ** Exportable** | Allows the selected layer to be exported and saved as an external **.lyr** file. ** Exportable (Pak)** | Allows the selected layer to be exported and saved as a **.pak** file. ** Auto-Load** | ** Auto-load** | When enabled, the selected layer and its contents will be loaded in the game. Choosing not to load a layer right away improves performance. --- | --- ** Auto-load** | When enabled, the selected layer and its contents will be loaded in the game. Choosing not to load a layer right away improves performance. ** Physics** | ** Physics** | Turns on the physics of physicalized objects in the selected layer. --- | --- ** Physics** | Turns on the physics of physicalized objects in the selected layer. ** Platforms** | Allows users to specify which platforms (** PC**, ** PS4**, or ** Xbox One**) the selected layer and its contents are to be displayed on. ** Reload** | Reloads the scripts of all legacy (LUA) entities included within the selected layer. ** Exportable** | ** Exportable** | Allows the selected layer to be exported and saved as an external **.lyr** file. --- | --- ** Exportable (Pak)** | Allows the selected layer to be exported and saved as a **.pak** file. ** Exportable** | Allows the selected layer to be exported and saved as an external **.lyr** file. ** Exportable (Pak)** | Allows the selected layer to be exported and saved as a **.pak** file. ** Auto-Load** | ** Auto-load** | When enabled, the selected layer and its contents will be loaded in the game. Choosing not to load a layer right away improves performance. --- | --- ** Auto-load** | When enabled, the selected layer and its contents will be loaded in the game. Choosing not to load a layer right away improves performance. ** Physics** | ** Physics** | Turns on the physics of physicalized objects in the selected layer. --- | --- ** Physics** | Turns on the physics of physicalized objects in the selected layer. ** Platforms** | Allows users to specify which platforms (** PC**, ** PS4**, or ** Xbox One**) the selected layer and its contents are to be displayed on.
**Option** | **Description**
**Set as Active Layer** | When a layer is selected in the Level Explorer, this option sets that layer as the Active Layer.
**Lock Read-Only Layers** | Locks all layers that have been set to Read-Only mode on disk. This is particularly useful when using [version control](../Version%20Control%20System.md), allowing only those layers that have been marked for editing to be modified.
**More** | **Reload** | Reloads the scripts of all legacy (LUA) entities included within the selected layer. --- | --- ** Exportable** | ** Exportable** | Allows the selected layer to be exported and saved as an external **.lyr** file. --- | --- ** Exportable (Pak)** | Allows the selected layer to be exported and saved as a **.pak** file. ** Exportable** | Allows the selected layer to be exported and saved as an external **.lyr** file. ** Exportable (Pak)** | Allows the selected layer to be exported and saved as a **.pak** file. ** Auto-Load** | ** Auto-load** | When enabled, the selected layer and its contents will be loaded in the game. Choosing not to load a layer right away improves performance. --- | --- ** Auto-load** | When enabled, the selected layer and its contents will be loaded in the game. Choosing not to load a layer right away improves performance. ** Physics** | ** Physics** | Turns on the physics of physicalized objects in the selected layer. --- | --- ** Physics** | Turns on the physics of physicalized objects in the selected layer. ** Platforms** | Allows users to specify which platforms (** PC**, ** PS4**, or ** Xbox One**) the selected layer and its contents are to be displayed on.
**Reload** | Reloads the scripts of all legacy (LUA) entities included within the selected layer.
**Exportable** | **Exportable** | Allows the selected layer to be exported and saved as an external **.lyr** file. --- | --- ** Exportable (Pak)** | Allows the selected layer to be exported and saved as a **.pak** file.
**Exportable** | Allows the selected layer to be exported and saved as an external **.lyr** file.
**Exportable (Pak)** | Allows the selected layer to be exported and saved as a **.pak** file.
**Auto-Load** | **Auto-load** | When enabled, the selected layer and its contents will be loaded in the game. Choosing not to load a layer right away improves performance. --- | ---
**Auto-load** | When enabled, the selected layer and its contents will be loaded in the game. Choosing not to load a layer right away improves performance.
**Physics** | **Physics** | Turns on the physics of physicalized objects in the selected layer. --- | ---
**Physics** | Turns on the physics of physicalized objects in the selected layer.
**Platforms** | Allows users to specify which platforms (**PC**, ** PS4**, or ** Xbox One**) the selected layer and its contents are to be displayed on.
**Visibility** | **Visible** | Toggles the visibility of the object(s)/layer(s)/folder(s) currently selected in the Level Explorer. --- | --- ** Isolate Visibility** | Toggles the visibility of all object(s)/layer(s)/folder(s) in the Viewport, except the object/layer/folder currently selected in the Level Explorer. ** More** | ** Hide All** | Hides all folders/layers of objects in the Viewport. --- | --- ** Unhide All** | Makes visible all folders/layers of objects in the Viewport. ** Toggle Child Object Visibility** | Toggles the visibility of all objects that belong to the currently selected layer. ** Hide Child Objects** | Hides all objects that belong to the currently selected layer, in the Viewport. ** Unhide Child Objects** | Makes visible all objects that belong to the currently selected layer, in the Viewport. ** Hide All** | Hides all folders/layers of objects in the Viewport. ** Unhide All** | Makes visible all folders/layers of objects in the Viewport. ** Toggle Child Object Visibility** | Toggles the visibility of all objects that belong to the currently selected layer. ** Hide Child Objects** | Hides all objects that belong to the currently selected layer, in the Viewport. ** Unhide Child Objects** | Makes visible all objects that belong to the currently selected layer, in the Viewport.
**Visible** | Toggles the visibility of the object(s)/layer(s)/folder(s) currently selected in the Level Explorer.
**Isolate Visibility** | Toggles the visibility of all object(s)/layer(s)/folder(s) in the Viewport, except the object/layer/folder currently selected in the Level Explorer.
**More** | **Hide All** | Hides all folders/layers of objects in the Viewport. --- | --- ** Unhide All** | Makes visible all folders/layers of objects in the Viewport. ** Toggle Child Object Visibility** | Toggles the visibility of all objects that belong to the currently selected layer. ** Hide Child Objects** | Hides all objects that belong to the currently selected layer, in the Viewport. ** Unhide Child Objects** | Makes visible all objects that belong to the currently selected layer, in the Viewport.
**Hide All** | Hides all folders/layers of objects in the Viewport.
**Unhide All** | Makes visible all folders/layers of objects in the Viewport.
**Toggle Child Object Visibility** | Toggles the visibility of all objects that belong to the currently selected layer.
**Hide Child Objects** | Hides all objects that belong to the currently selected layer, in the Viewport.
**Unhide Child Objects** | Makes visible all objects that belong to the currently selected layer, in the Viewport.
**Lock** | **Locked** | Locks the current object/folder/layer, preventing it from being edited. A locked object/folder/layer is indicated by the![Image](https://www.cryengine.com/docs/static/attachments/44960484) icon in the Level Explorer. Learn more about locking and unlocking in the [Locking Layers/Folders/Objects](Level%20Explorer.md#LevelExplorer-lock) section below. --- | --- ** Isolate Locked** | Toggles the lock on all object(s)/layer(s)/folder(s), except the object/layer/folder currently selected in the Level Explorer. ** More** | ** Lock All** | Locks all folders/layers of objects that have been placed in the current level. --- | --- ** Unlock All** | Unhides all folders/layers of objects in the Viewport. ** Lock Read-Only Layers** | Locks all layers that have been set to Read-Only mode on disk. This is particularly useful when using [version control](../Version%20Control%20System.md), allowing only those layers that have been marked for editing to be modified. ** Toggle Child Object Locking** | Locks/unlocks all objects that belong to the currently selected layer. ** Lock Child Objects** | Locks all objects that belong to the currently selected layer. ** Unlock Child Objects** | Unlocks all objects that belong to the currently selected layer. ** Lock All** | Locks all folders/layers of objects that have been placed in the current level. ** Unlock All** | Unhides all folders/layers of objects in the Viewport. ** Lock Read-Only Layers** | Locks all layers that have been set to Read-Only mode on disk. This is particularly useful when using [version control](../Version%20Control%20System.md), allowing only those layers that have been marked for editing to be modified. ** Toggle Child Object Locking** | Locks/unlocks all objects that belong to the currently selected layer. ** Lock Child Objects** | Locks all objects that belong to the currently selected layer. ** Unlock Child Objects** | Unlocks all objects that belong to the currently selected layer. ** Color** | Allows users to assign a preset or custom color to the contents of a layer or folder in the Level Explorer.
**Locked** | Locks the current object/folder/layer, preventing it from being edited. A locked object/folder/layer is indicated by the![Image](https://www.cryengine.com/docs/static/attachments/44960484) icon in the Level Explorer. Learn more about locking and unlocking in the [Locking Layers/Folders/Objects](Level%20Explorer.md#LevelExplorer-lock) section below.
**Isolate Locked** | Toggles the lock on all object(s)/layer(s)/folder(s), except the object/layer/folder currently selected in the Level Explorer.
**More** | **Lock All** | Locks all folders/layers of objects that have been placed in the current level. --- | --- ** Unlock All** | Unhides all folders/layers of objects in the Viewport. ** Lock Read-Only Layers** | Locks all layers that have been set to Read-Only mode on disk. This is particularly useful when using [version control](../Version%20Control%20System.md), allowing only those layers that have been marked for editing to be modified. ** Toggle Child Object Locking** | Locks/unlocks all objects that belong to the currently selected layer. ** Lock Child Objects** | Locks all objects that belong to the currently selected layer. ** Unlock Child Objects** | Unlocks all objects that belong to the currently selected layer.
**Lock All** | Locks all folders/layers of objects that have been placed in the current level.
**Unlock All** | Unhides all folders/layers of objects in the Viewport.
**Lock Read-Only Layers** | Locks all layers that have been set to Read-Only mode on disk. This is particularly useful when using [version control](../Version%20Control%20System.md), allowing only those layers that have been marked for editing to be modified.
**Toggle Child Object Locking** | Locks/unlocks all objects that belong to the currently selected layer.
**Lock Child Objects** | Locks all objects that belong to the currently selected layer.
**Unlock Child Objects** | Unlocks all objects that belong to the currently selected layer.
**Color** | Allows users to assign a preset or custom color to the contents of a layer or folder in the Level Explorer.
**Path Utils** | **Open in File Explorer** | Opens the file explorer to locate the selected layer's **.lyr** file on disk. --- | --- ** Copy Name** | Copies the name of the selected layer to the clipboard, so that it can be pasted into another application. ** Copy Path** | Copies the file path of the selected layer to the clipboard, so that it can be pasted into another application.
**Open in File Explorer** | Opens the file explorer to locate the selected layer's **.lyr** file on disk.
**Copy Name** | Copies the name of the selected layer to the clipboard, so that it can be pasted into another application.
**Copy Path** | Copies the file path of the selected layer to the clipboard, so that it can be pasted into another application.
**Version Control** | **Refresh** | Manually updates the status of the selected version controlled layers. The statuses of all version controlled layers are indicated under the![Image](https://www.cryengine.com/docs/static/attachments/44960693) column of the Level Explorer. Note that a layer is tracked by the implemented Version Control System only once the corresponding level has been saved and the layer itself, written to disk as a **.lyr** file.![Image](https://www.cryengine.com/docs/static/attachments/44960695) * Level Explorer version control* --- | --- **Get Latest** | Retrieves the most recently modified version of the selected layer from the repository. ** Check Out** | Retrieves a layer file from the repository to be worked upon locally; once Checked Out, a layer will no longer be editable by other developers until local modifications have been Submitted or Reverted. ** Revert** | Discards all changes made to a layer file and restores it to its last local version. ** Revert if Unchanged** | Performs the above Revert operation upon a layer file only if its contents haven't been modified. ** Submit...** | Commits the selected locally modified layers to the repository. The ** Submit...** option displays a separate window that lists within it all locally modified assets, work files and layers, and allows users to tick which changes they'd like to commit (including deletions made, if any).![Image](https://www.cryengine.com/docs/static/attachments/44960696) * Submit window* The submission process can only be completed after a description of changes performed have been entered in the text box provided within the Submit window.
**Refresh** | Manually updates the status of the selected version controlled layers. The statuses of all version controlled layers are indicated under the![Image](https://www.cryengine.com/docs/static/attachments/44960693) column of the Level Explorer. Note that a layer is tracked by the implemented Version Control System only once the corresponding level has been saved and the layer itself, written to disk as a **.lyr** file.![Image](https://www.cryengine.com/docs/static/attachments/44960695) * Level Explorer version control*
**Get Latest** | Retrieves the most recently modified version of the selected layer from the repository.
**Check Out** | Retrieves a layer file from the repository to be worked upon locally; once Checked Out, a layer will no longer be editable by other developers until local modifications have been Submitted or Reverted.
**Revert** | Discards all changes made to a layer file and restores it to its last local version.
**Revert if Unchanged** | Performs the above Revert operation upon a layer file only if its contents haven't been modified.
**Submit...** | Commits the selected locally modified layers to the repository. The **Submit...** option displays a separate window that lists within it all locally modified assets, work files and layers, and allows users to tick which changes they'd like to commit (including deletions made, if any).![Image](https://www.cryengine.com/docs/static/attachments/44960696) * Submit window* The submission process can only be completed after a description of changes performed have been entered in the text box provided within the Submit window.
**View** | **Expand All** | Expands all layers and folders in the Level Explorer, to reveal the objects they contain. --- | --- ** Collapse All** | Collapses all expanded layers and folders in the Level Explorer.
**Expand All** | Expands all layers and folders in the Level Explorer, to reveal the objects they contain.
**Collapse All** | Collapses all expanded layers and folders in the Level Explorer.
**Objects** | **Edit** | When an [Area](Create%20Object/Area.md)Shape or other poly-line based object (Clip Volume, Game Volume, Occluder etc.) is selected, clicking the ** Edit** option enables the ** Edit Shape** operator in the Properties Tool, allowing users to change the object's shape by selecting, moving, adding or removing vertices. When a [Designer](Create%20Object/Designer%20Tool.md) object is selected, the ** Edit** option opens the [Designer Tool](../Designer%20Tool%20Tab.md) so that the object can be edited. --- | --- ** Create Flowgraph** | Allows the selected Entity to be used as a container for your Flow Graph logic. ** Flowgraphs** | Lists all Flow Graphs containers where the selected Entity is referenced. Clicking a listed Flow Graph container opens the Flow Graph tool, with its Search Panel configured to list all locations where the selected Entity is used in graph logic. ** Events** | Lists all Lua Events that can be triggered on the selected Entity. ** Reload Script** | Updates the Lua code logic of the selected Entity. ** Reload All Scripts** | Updates the Lua code logic of all Entities in the level. ** Create Group** | Creates a [Group](Level%20Explorer/Object%20Linking.md) with the currently selected object, to which multiple other objects may be added by dragging and dropping. ** Create Prefab** | Creates a [Prefab](../../Entities%20and%20Tools/Entities%20Overview/Prefabs.md) of a user defined name with the currently selected object. Multiple other objects may be added to this prefab by dragging and dropping. ** Attach To...** | Adds the selected object to an existing Group or Prefab. To add an object to a Group/Prefab, select the object from the Level Explorer and the destination Group/Prefab from the Viewport. ** Detach** | Removes the selected object from a created Group or Prefab. If the Group or Prefab belongs to a hierarchy of nested Groups/Prefabs, the detached object is moved up a level within the hierarchy. ** Detach from Hierarchy** | Removes the selected object from a created Group or Prefab. If the Group or Prefab belongs to a hierarchy of nested Groups/Prefabs, the detached object is moved to the root of the hierarchy, i.e., the current layer. ** Link To...** | Adds the selected object to an existing [link](Level%20Explorer/Object%20Linking.md). Please refer to the [Object Linking](Level%20Explorer/Object%20Linking.md) page for more information on creating links between Entity-type objects. ** Unlink** | Eliminates the parent-child relationship or link that the selected object might be a part of. ** Delete** | Deletes the object from the level. ** Transform** | Provides options to ** Clear Rotation**, ** Clear Scale** or ** Clear All** changes made to the selected object. ** Convert to Entity** | Converts a non-Entity type object into an Entity. ** Convert to Brush** | Converts an object into a [Brush](Create%20Object/Brush%20Objects.md). ** Convert to Designer** | Converts non-Designer type object into one that can be edited by the[Designer](Create%20Object/Designer%20Tool.md) tool. ** Track View Sequences** | Lists all Track View sequences where the selected Entity is used. Clicking a listed Track View sequence opens the Track View tool to reveal the Entity's position within it. ** Show in Asset Browser** | Locates the currently selected object within the Asset Browser. ** Find in Flow Graph** | Opens the [Flow Graph](../Flow%20Graph.md)tool to locate references to the selected object within any existing/created flow graphs. ** Convert to Procedural Object** | Deprecated. ** Swap Prefab** | Allows the selected prefab to be swapped with a different one from the Asset Browser. This option appears only when the selected object is a prefab. ** Select all Prefabs of Type "<prefab-name">"** | Selects all instances of the selected prefab(s) that have been included within a level, even if these are nested in other prefabs. This option appears only when the selected object is a prefab. ** Color** | Assigns a preset or custom color to an object's listing within the Level Explorer.
**Edit** | When an [Area](Create%20Object/Area.md)Shape or other poly-line based object (Clip Volume, Game Volume, Occluder etc.) is selected, clicking the **Edit** option enables the ** Edit Shape** operator in the Properties Tool, allowing users to change the object's shape by selecting, moving, adding or removing vertices. When a [Designer](Create%20Object/Designer%20Tool.md) object is selected, the ** Edit** option opens the [Designer Tool](../Designer%20Tool%20Tab.md) so that the object can be edited.
**Create Flowgraph** | Allows the selected Entity to be used as a container for your Flow Graph logic.
**Flowgraphs** | Lists all Flow Graphs containers where the selected Entity is referenced. Clicking a listed Flow Graph container opens the Flow Graph tool, with its Search Panel configured to list all locations where the selected Entity is used in graph logic.
**Events** | Lists all Lua Events that can be triggered on the selected Entity.
**Reload Script** | Updates the Lua code logic of the selected Entity.
**Reload All Scripts** | Updates the Lua code logic of all Entities in the level.
**Create Group** | Creates a [Group](Level%20Explorer/Object%20Linking.md) with the currently selected object, to which multiple other objects may be added by dragging and dropping.
**Create Prefab** | Creates a [Prefab](../../Entities%20and%20Tools/Entities%20Overview/Prefabs.md) of a user defined name with the currently selected object. Multiple other objects may be added to this prefab by dragging and dropping.
**Attach To...** | Adds the selected object to an existing Group or Prefab. To add an object to a Group/Prefab, select the object from the Level Explorer and the destination Group/Prefab from the Viewport.
**Detach** | Removes the selected object from a created Group or Prefab. If the Group or Prefab belongs to a hierarchy of nested Groups/Prefabs, the detached object is moved up a level within the hierarchy.
**Detach from Hierarchy** | Removes the selected object from a created Group or Prefab. If the Group or Prefab belongs to a hierarchy of nested Groups/Prefabs, the detached object is moved to the root of the hierarchy, i.e., the current layer.
**Link To...** | Adds the selected object to an existing [link](Level%20Explorer/Object%20Linking.md). Please refer to the [Object Linking](Level%20Explorer/Object%20Linking.md) page for more information on creating links between Entity-type objects.
**Unlink** | Eliminates the parent-child relationship or link that the selected object might be a part of.
**Delete** | Deletes the object from the level.
**Transform** | Provides options to **Clear Rotation**, ** Clear Scale** or ** Clear All** changes made to the selected object.
**Convert to Entity** | Converts a non-Entity type object into an Entity.
**Convert to Brush** | Converts an object into a [Brush](Create%20Object/Brush%20Objects.md).
**Convert to Designer** | Converts non-Designer type object into one that can be edited by the[Designer](Create%20Object/Designer%20Tool.md) tool.
**Track View Sequences** | Lists all Track View sequences where the selected Entity is used. Clicking a listed Track View sequence opens the Track View tool to reveal the Entity's position within it.
**Show in Asset Browser** | Locates the currently selected object within the Asset Browser.
**Find in Flow Graph** | Opens the [Flow Graph](../Flow%20Graph.md)tool to locate references to the selected object within any existing/created flow graphs.
**Convert to Procedural Object** | Deprecated.
**Swap Prefab** | Allows the selected prefab to be swapped with a different one from the Asset Browser. This option appears only when the selected object is a prefab.
**Select all Prefabs of Type "<prefab-name">"** | Selects all instances of the selected prefab(s) that have been included within a level, even if these are nested in other prefabs. This option appears only when the selected object is a prefab.
**Color** | Assigns a preset or custom color to an object's listing within the Level Explorer.

Levels and their comprising layer files are written to disk within the **Assets → Levels** directory of a project.

### Hiding Objects, Layers and Folders

The visibility of objects, layers and folders within a level is indicated by the![Image](https://www.cryengine.com/docs/static/attachments/35400842) column of the Level Explorer, as shown in the image below.

![Image](https://www.cryengine.com/docs/static/attachments/44960837) *Visibility column*

The![Image](https://www.cryengine.com/docs/static/attachments/44960483) icon indicates that an object is visible within the Viewport, while![Image](https://www.cryengine.com/docs/static/attachments/44960487) indicates that an object is hidden. Clicking either icon will toggle the visibility of that object.

![Image](https://www.cryengine.com/docs/static/attachments/44960839) *Toggling visibility*

- Toggling the visibility of a layer or folder will toggle the visibility of all objects within that layer or folder.
- Holding**CTRL** while clicking upon the![Image](https://www.cryengine.com/docs/static/attachments/35400842) icon of an object, layer, or folder in the Level Explorer, hides all items from the level except the currently selected one. Doing the same again reverses this effect.
- Holding **ALT** while clicking upon the![Image](https://www.cryengine.com/docs/static/attachments/35400842) or![Image](https://www.cryengine.com/docs/static/attachments/44960487) icon of a layer or folder will also make visible all the layers and objects they contain.

### Locking Objects, Layers and Folders

When an object is 'locked', it cannot be edited. The![Image](https://www.cryengine.com/docs/static/attachments/44960842) column indicates if an object, layer or folder has been locked, as shown in the image below.

![Image](https://www.cryengine.com/docs/static/attachments/44960843) *Lock column*

A locked object is indicated by the![Image](https://www.cryengine.com/docs/static/attachments/44960484) icon, while![Image](https://www.cryengine.com/docs/static/attachments/44958434) indicates an unlocked object. Clicking either icon will unlock/lock the corresponding object.

- Locking/unlocking a layer or folder will lock/unlock all objects within that layer or folder.
- Holding **Ctrl** while clicking upon the![Image](https://www.cryengine.com/docs/static/attachments/44958434) icon of an object, layer or folder in the Level Explorer locks all items in the level except the currently selected one. Doing the same again reverses this effect.
- Holding **Alt** while clicking upon the lock icon of a layer or folder unlocks all the layers and objects it contains.

Objects can still be snapped to locked objects or to objects in locked layers/folders, by holding down **Ctrl** + ** Shift** while clicking on the target object. For more information on object snapping and alignment, please refer to the [Snap & Alignment](../../CRYENGINE%20-%20Getting%20Started/For%20New%20CRYENGINE%20Users/CRYENGINE%20V%20Basics/Snap%20%26%20Alignment.md) documentation.

### Object Linking in the Level Explorer

Objects can be moved to an existing group or layer by dragging and dropping them to the destination group/layer's listing.

Dragging an object onto another object however causes both objects to be linked; if both the dragged and target objects are Entity objects such that the former has bones however, a menu is displayed to allow for linking to a specific bone of the target object. More on linking objects can be found [here](Level%20Explorer/Object%20Linking.md).

![Image](https://www.cryengine.com/docs/static/attachments/36842411)

Alternatively, objects may be moved between layers by selecting them in the Level Explorer and pressing **Ctrl** +** L**; this brings up a separate Select Layer window, allowing users to search for and select the object's destination layer.

![Image](https://www.cryengine.com/docs/static/attachments/36838550)

Note that for the Select Layer window to appear, at least one other layer must exist besides the Main layer.

[Menu](#menu)[The List View](#the-list-view)[Search Bar](#search-bar)[Filter](#filter)[Object and Layer Context Menus](#object-and-layer-context-menus)[Hiding Objects, Layers and Folders](#hiding-objects-layers-and-folders)[Locking Objects, Layers and Folders](#locking-objects-layers-and-folders)[Object Linking in the Level Explorer](#object-linking-in-the-level-explorer)
