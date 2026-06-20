# Asset Browser

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/35260066
- Page ID: 35260066
- Breadcrumb: Editor Tools > Asset Browser
- Parent: Editor Tools

## Child Pages

- [Asset System](Asset Browser/Asset System.md)

## Content

##
Overview

CRYENGINE's Asset Browser provides an overview of your project by allowing you to browse its contents, search for particular assets, as well as import new assets in
[/docs/static/engines/cryengine-5/categories/23756816/pages/44966294](
FBX
)
 format.

The goal is to provide users with the freedom to interact with their project's contents on disk solely through the Editor, to the point where a regular File Explorer should no longer be necessary when working on a CRYENGINE project. In the future all asset management functionality will be added to the Asset Browser.

More on the engine's Asset System can be found on
[/docs/static/engines/cryengine-5/categories/23756816/pages/29447695](
Asset System - Generating Metadata
)
.

[Image: /docs/static/attachments/44958919]

*
Asset Browser Overview
*

Certain default assets that arrive with your CRYENGINE build are separated from your project's assets; these default assets are situated under the
**
Engine
**
 folder, while all project assets are stored under
**
Assets
**
.

**
For Programmers
**

Engine assets can be addressed by prefixing %ENGINE% prefix to file paths, with ICryPak handling all subsequent path resolution.

Every hard-coded reference to
**
Engine
**
 assets meanwhile
must
 make use of this prefix. Paths with no prefix still do work for reasons of backward compatibility, as CryPak defaults to the
**
Engine
**
 directory when the
**
Assets
**
 folder contains no file matching the specified path.

##
Opening the Asset Browser

To be able to use and view the contents of an existing project within the Asset Browser,
**
.cryasset
**
 files will need to be generated as explained in the
[/docs/static/engines/cryengine-5/categories/23756816/pages/29447695](
Asset System - Generating Metadata
)
 documentation.

The Asset Browser can be accessed via
**
 Tools -> Asset Browser.
**

##
1. Menu

Accessed via the
[Image: /docs/static/attachments/36838191]
 icon situated at the top-right corner of the Asset Browser, the Menu contains the following options:

##
File

Option

 |
Description

 |

**
New Folder
**
 |
Creates a new folder within the folder currently selected on the Folder Tree.
 |

**
New Asset
**

 |
**
C# Script -
**
Creates a new C# asset before opening Visual Studio or a similar text editor as specified in your Sandbox
[/docs/static/engines/cryengine-5/categories/23756816/pages/35848616](
Preferences
)
. A corresponding C# Output window will also be generated if the Sandbox doesn't start up with one by default.

Since the names of C# classes cannot begin with a number, any created C# Script asset of the name '01Class' or similar will result in a compile error. This can be quickly fixed via the text editor interface that opens on creating a C# asset; your choice of text editor needs to specified in the
**
General → File → C# Text Editor
**
 field of your Sandbox Preferences.

In the text editor, simply locate the public class of the same name as the created C# Script, correct the name and save the file to fix the error.

**
Environment
**
 -
Creates a new Environment asset that specifies the environmental settings of the current level, such as fog, volumetric clouds and the positioning of the sun over a 24-hour period, via the
[/docs/static/engines/cryengine-5/categories/23756816](
Environment Editor (Old as of 26/2)
)
.

**
Level
**
 - Creates a new level file, before opening the New Level dialog box that allows users to specify the level's general Heightmap, Texture and Terrain properties.

**
Material
**
 - Creates a new material asset with the
**
.mtl
**
 extension in the current folder.

**
Particles
 -
**
 Creates a new particle effect with the
**
.pfx
**
 extension in the current folder.

**
Prefab
**
 - A
[/docs/static/engines/cryengine-5/categories/23756816/pages/36866251](
Prefab
)
 is an asset type that contains one or more objects along with their properties, of which multiple instances can be created such that each instance is an exact replica of the other. To create a new Prefab, one or more objects from the Level Explorer that are to comprise it must first be selected/highlighted via the Level Explorer.

**
Schematyc Entity
**
 - Creates a new
[/docs/static/engines/cryengine-5/categories/23756816/pages/36868211](
Schematyc
)
 Entity containing graphs, variables, signals and state machines to be placed within a level. An Entity can use an existing Schematyc Entity as a base, and creating a new Entity automatically opens the Schematyc Editor.

**
Schematyc Library
**
 - Creates a new Schematyc Library and opens the Schematyc Editor; as opposed to an Entity, a Schematyc Library cannot be placed within a level and contains functions, enumerations and signals.

 |

**
Import
**

 |
Opens your system's file explorer to locate and import assets of appropriate file types.

Assets can also be imported by dragging & dropping them into the Asset Browser.

 |

**
Save All
**

 |
When an asset is modified via its respective asset editor, the Asset Browser will keep any changes made to that asset even if the asset editor is closed without saving. The
**
Save
**

**
All
**
option saves unsaved changes made to all modified assets.

Assets that have been modified, but not saved, are indicated by an asterisk in
**
Shows Details
**
 and
**
Shows Thumbnails
**
 view.

 |

**
Discard Changes
**
 |
Discards unsaved changes made to the selected asset.
 |

**
Generate All Thumbnails
**
 |
Generates thumbnails for all the assets included within your project. This must be done for all projects created before CRYENGINE 5.4.
 |

**
Generate/Repair All Metadata
**
 |
Generates
**
.cryasset
**
 files for an existing project in order to be able to view and use its contents in the Asset Browser, Please refer to
[/docs/static/engines/cryengine-5/categories/23756816/pages/29447695](
Asset System - Generating Metadata
)
 for more information.

This option does not work for assets located in
**
.pak
**
 files.
**

**

 |

##
Edit

Option
 |
Description
 |

**
Copy
**

 |
Copies the selected asset to the clipboard.

 |

**
Paste
**

 |
Pastes a copied asset from the clipboard into the selected folder.

The
**
Paste
**
 option is only available when
**
View → Recursive View
**
is inactive.

 |

**
Rename
**
 |
Allows users to give the selected asset a custom name.
 |

**
Delete
**
 |
Deletes the selected asset.
 |

**
Duplicate
**
 |
Creates a copy of the selected asset within the same folder.
 |

**
Reimport
**
 |
Reloads the selected asset into the Asset Browser.
 |

**
Copy Name
**
 |
Copies the name of the selected asset to the clipboard, so that it can be pasted into another application.
 |

**
Copy Path
**
 |
Copies the file path of the selected asset to the clipboard, so that it can be pasted into another application.
 |

**
Work Files
**
 |
Lists all work files associated with the selected asset, a work file being any multimedia file type from which the asset is developed. Additionally the following options are provided for each listed work file:

-
**
Open...
**
: Opens an appropriate desktop application to view the selected work file.

-
**
Copy Path:
**
Copies the address of the selected work file to the clipboard.

-
**
Show in File Explorer:
**
Locates the selected work file on disk.

Additional work files can be linked to an asset while previously linked files may be deleted via the
**
Work Files ->
**

**
Manage Work Files...
**
option, which also lists previously linked work files. Please refer to
[/docs/static/engines/cryengine-5/categories/23756816/pages/35260066#AssetBrowser-AssociatingWorkFiles](
Associating Work Files to Assets
)
 in the Functionality section for more information.

 |

**
Open in File Explorer
**
 |
Opens the File Explorer to locate the selected asset/folder on disk
 |

##
View

Option

 |
Description

 |

**
Shows Details
**

 |
Displays multiple asset properties in columns within the Search Results pane.
**
Shows Details
**
may alternatively be toggled using the
[Image: /docs/static/attachments/36838194]
 button in the Asset Browser's View Type toolbar.

 |

**
Shows Thumbnails
**

 |
Displays asset thumbnails instead of column-listed details in the Search Results pane, alternatively toggled by the
[Image: /docs/static/attachments/36838195]
 button in the Asset Browser's View Type toolbar.

Choose between four different sizes of thumbnails by h
olding down the left mouse button
 over or
right-clicking
 upon the
**
Shows Thumbnails
**
 button.

 |

**
Split Horizontally
**

 |
Displays asset properties in columns and asset thumbnails, across two horizontal divisions of the Search Results pane. Selecting an asset in column view will also highlight it on the thumbnail pane, and vice versa.

Also corresponds to the
[Image: /docs/static/attachments/36838197]
 icon of the Asset Browser's View Type toolbar.

 |

**
Split Vertically
**

 |
Displays asset properties in columns and asset thumbnails, across two vertical divisions of the Search Results pane.
 Selecting an asset in column view will also highlight it on the thumbnail pane, and vice versa.

Corresponds to the
[Image: /docs/static/attachments/36838196]
 button of the Asset Browser's View Type toolbar.

 |

**
Show Folder Tree
**

 |
Hides/reveals the Folder Tree pane.

**
Show Folder Tree
**
 can also be toggled via the
[Image: /docs/static/attachments/36838184]
 icon of the Asset Browser's View Type toolbar.

 |

**
Recursive View
**

 |
With Recursive View active, assets included within both the selected folder of the Folder Tree and its sub-folders are displayed in the Search Results pane. Deactivating Recursive View on the other hand displays only files included within the selected folder.

Alternatively toggled by the
[Image: /docs/static/attachments/36838185]
 button of the Asset Browser's View toolbar.

 |

**
Thumbnail Sizes
**
 |
Allows users to set the thumbnail size of assets/folders displayed within the Asset Browser to any of the following values:

-
**
16 px
**

-
**
32 px
**

-
**
64 px
**

-
**
128 px
**
 |

**
Adaptive Layout
**

 |
When
**
Adaptive Layout
**
 is enabled, the positions of the toolbars and the Folder Tree change with respect to the size of the Asset Browser window.

 |

##
Toolbars

**
Option
**
 |
**
Description
**
 |

**
Customize
**
 |
Opens the toolbar customization window allowing users to customize existing toolbars, and/or create new toolbars within the Asset Browser.
 |

**
Lock Toolbars
**
 |
When disabled, the positions of toolbars and spacers within the Asset Browser can be changed by drag and drop.
 |

**
Spacers
**
 |
The following options allow users to use spacers in positioning their toolbars.

**
Insert Expanding Spacer
**
 |
Adds an expanding spacer to the toolbar layout; an expanding spacer pushes all elements situated at its ends to the edge of the tool window.
 |

**
Insert Fixed Spacer
**
 |
Adds a fixed spacer, which has a fixed size of one icon.
 |

The
**
Spacers
**
 menu options are only available when
**
Toolbars → Lock Toolbars
**
 is disabled.

 |

**
Toolbars
**
 |
Lists all default and custom toolbars created for the Asset Browser, allowing users to select which toolbar they'd like to hide or display. By default, the following toolbars are available to the Asset Browser:

**
File
**
 |
[Image: /docs/static/attachments/44964639]

**
Import
**
 |
Opens your system's file explorer to locate and import assets of appropriate file types.
 |

[Image: /docs/static/attachments/44964640]

**
Save All
**
 |
Saves unsaved changes made to all modified assets.
 |

 |

**
View
**
 |
[Image: /docs/static/attachments/36838185]
**
Recursive View
**

 |
When enabled, assets included within both the selected folder of the Folder Tree and its sub-folders are displayed in the Search Results pane.

Disabling this button on the other hand displays only files included within the selected folder.

 |

[Image: /docs/static/attachments/44959744]

**
Hide Irrelevant Folders
**
 |
When enabled, folders containing assets that are not relevant to a specified search criteria/filter are dimmed in the Folder Tree pane, and hidden when
**
View → Shows Details/Shows Thumbnails
**
 is active.
 |

 |

**
View Type
**
 |
[Image: /docs/static/attachments/36838184]

**
Show Folder Tree
**
 |
Hides/reveals the Folder Tree pane of the Asset Browser.
 |

[Image: /docs/static/attachments/36838197]

**
Split Horizontally
**
 |
Displays asset properties in columns and asset thumbnails, across two horizontal divisions of the Search Results pane.
 |

[Image: /docs/static/attachments/36838196]

**
Split Vertically
**
 |
Displays asset properties in columns and asset thumbnails, across two vertical divisions of the Search Results pane.
 |

[Image: /docs/static/attachments/36838194]

**
Shows Details
**
 |
Displays multiple asset properties in columns within the Search Results pane.
 |

[Image: /docs/static/attachments/36838195]

**
Shows Thumbnails
**
 |
Displays asset thumbnails instead of column-listed details in the Search Results pane.
 |

 |

 |

When a tool has a toolbar, whether this is a default one or a custom one, the options above are also available when right-clicking in the toolbar area (only when a toolbar is already displayed).

##
Help

Option
 |
Description
 |

**
Help
**
 |
Opens the user documentation for the Asset Browser.
 |

##
2. Navigation Bar

Indicates the path of the currently selected folder from the folder tree, also permitting quick switching between previous/successive folders along its path.

##
3. Folder Tree

Lists a directory of folders and their sub-folders included within your project, allowing for quick navigation between these. The
**
Search Folders
**
 bar at its top further helps searching for specific folders/sub-folders on the basis of their names.

##
Context Menu

Right clicking anywhere within this pane yields a context menu with the following items.

Option
 |
Description
 |

**
New Folder
**

 |
Creates a new folder within the folder tree. With a folder/sub-folder selected and right-clicked within the folder tree, the option creates a new folder as the selected folder's sub-folder; with the Assets folder/no folder selected however, all newly created folders are automatically added to the Assets folder.

 |

**
Delete
**

 |
Removes the currently selected folder, provided it is a new/custom folder created by the user, from the Folder Tree.

 |

**
Rename
**

 |
Modifies the name provided to the selected new/custom folder within the Folder Tree.

 |

**
Open in File Explorer
**

 |
Locates and displays the contents of the selected folder within your system's File Explorer, only if the folder contains assets and/or other items.

 |

**
Generate All Thumbnails
**

 |
Manually generates thumbnails for all assets included within the currently selected folder of the Folder Tree.

 |

##
4. Search Results Pane

The contents of folders selected within the Folder Tree, assets retrieved by searches and their corresponding search filters are displayed within this Search Results pane.

The thumbnails of assets are assigned colors based on their type within the Search Results Pane, and these are visible only when
**
View → Shows Thumbnails/Split Horizontally/Split Vertically
**
 is active as seen in the image below.

[Image: /docs/static/attachments/36842638]

*
Thumbnails
*

The colors and the types of assets they indicate are as follows:

Color

 |
Asset Type

 |
File Extension

 |

[Image: /docs/static/attachments/36842640]

 |
Audio

 |
**
.ogg
**
 |

[Image: /docs/static/attachments/36848672]

 |
Environment

 |
**
.env
**
 |

[Image: /docs/static/attachments/36842641]

 |
Level

 |
**
.lyr
**
 |

[Image: /docs/static/attachments/36842642]

 |
Material

 |
**
.mtl
**
 |

[Image: /docs/static/attachments/36842643]

 |
Mesh

 |
**
.cgf
**
 |

[Image: /docs/static/attachments/36842644]

 |
Particle

 |
**
.pfx
**

 |

[Image: /docs/static/attachments/36842645]

 |
Prefab

 |
**
.prefab
**

 |

[Image: /docs/static/attachments/36842639]

 |
Skeletal Animation

 |
**
.caf
**
 |

[Image: /docs/static/attachments/36842646]

 |
SchematycEntity

 |
**
.schematyc_ent
**

 |

[Image: /docs/static/attachments/36842647]

 |

Script

 |
**
.lua
**

 |

[Image: /docs/static/attachments/36842648]

 |
Texture

 |
**
.tif
**

 |

Context menus are generated by right-clicking virtually anywhere on the Search Results pane and depending on where these right-clicks occur, the menus may differ in their listed options as follows.

##
Column Headers Context Menu

With
**
 View →
**

**
Shows Details/Split Horizontally/Split Vertically
**
 active, asset listings are displayed in column view within the Search Results pane such that each column header corresponds to specific properties of the displayed assets. Right-clicking on the column
**
headers
**
 within this pane allows the inclusion of additional property columns.

##
Search Results Pane Context Menu

With
**
View → Recursive View
**
 inactive, right-clicking on empty space within the Search Results pane without selecting any particular asset yields:

Option
 |
Description
 |

**
New Folder
**

 |
Creates a new sub-folder within the currently selected folder.

 |

**
New Asset
**

 |
Creates new C# Script, Environment, Level, Material, Prefab, Particles, Schematyc Entity and/or Schematyc Library assets, as does the
**
File -> New Asset
**
 option of the
[/docs/static/engines/cryengine-5/categories/23756816/pages/35260066#AssetBrowser-Menu](
Menu Bar
)
 described above.

 |

**
Paste
**

 |
Pastes an asset that was previously copied using the
**
Copy
**
 option of its context menu, within the currently selected folder. Alternatively this can also be achieved by pressing
**
Ctrl + V
**
.

 |

**
Import
**

 |
Opens your system's File Explorer to locate and import assets of appropriate file types, as does the
**
 File -> Import
**
 option of the Menu Bar described above.

 |

**
Open in File Explorer
**

 |
Locates and displays the contents of the selected folder within the system's File Explorer, as does the
**
File -> Show in File Explorer
**
 option of the Menu Bar described above.

 |

**
Generate All Thumbnails
**

 |
Manually generates thumbnails for all assets included within the currently selected folder of the Folder Tree.

 |

[Image: /docs/static/attachments/36838185]

**
Recursive View
**

 |
When enabled, assets included within both the selected folder of the Folder Tree and its sub-folders are displayed in the Search Results pane. Disabling this button on the other hand displays only files included within the selected folder.
 |

[Image: /docs/static/attachments/36838194]

**
Shows Details
**

 |
Displays multiple asset properties in columns within the Search Results pane.
 |

[Image: /docs/static/attachments/36838195]

**
Shows Thumbnails
**

 |
Displays asset thumbnails instead of column-listed details in the Search Results pane.
 |

**
[Image: /docs/static/attachments/36838197]
 Split Horizontally
**

 |
Displays asset properties in columns and asset thumbnails, across two horizontal divisions of the Search Results pane. Selecting an asset in column view will also highlight it on the thumbnail pane, and vice versa.

 |

**
[Image: /docs/static/attachments/36838196]

Split Vertically
**

 |
Displays asset properties in columns and asset thumbnails, across two vertical divisions of the Search Results pane.
 Selecting an asset in column view will also highlight it on the thumbnail pane, and vice versa.

 |

[Image: /docs/static/attachments/36838184]

**
Show Folder Tree
**

 |
Hides/reveals the Folder Tree pane of the Asset Browser.
 |

##
Asset Context Menu

Generated by right-clicking a specific asset within the Search Results pane, its options include:

Option
 |
Description
 |

**
Copy
**

 |
Copies the selected asset, located within a project's
**
Engine
**
 or
**
Asset
**
 directory, to the clipboard. The copy can be pasted at the desired folder location using the
**
Paste
**
 option of the Search Results Pane Context Menu.

-
Assets can only be copied to locations within a project's
**
Asset
**
 directory. The
**
Engine
**
folder is immutable; assets cannot be copied to or duplicated within it.

-
Assets copied to the clipboard can only be pasted at the target location when
**
View → Recursive View
**
is inactive.

An asset can also be copied to clipboard using
**
Ctrl + C
**
.

 |

**
Duplicate
**

 |
Creates a duplicate of an asset in the same folder, as does
**
Ctrl + D
**
.

 |

**
Reimport
**

 |
Reloads the selected asset into the Asset Browser.

 |

**
Delete
**

 |
Deletes the selected asset.

 |

**
Save All
**

 |
When an asset is modified via its respective asset editor, the Asset Browser will keep any changes made to that asset even if the asset editor is closed without saving. The
**
Save
**

**
All
**
option saves unsaved changes made to all modified assets.

Assets that have been modified, but not saved, are indicated by an asterisk (*) in
**
Shows Details
**
 and
**
Shows Thumbnails
**
 view.

 |

**
Discard Changes
**
 |
Discards unsaved changes made to the selected asset.
 |

**
Preview Environment Asset
**

 |
Allows users to preview an Environment asset by temporarily applying its settings, such as the positioning of the sun, lighting, fog and cloud density, to the Viewport.

This option is only available to Environment assets.
 |

**
Set as Default for this Level
**

 |
Sets the current Environment asset as the Viewport's default.

This means that whenever a window of the Environment Editor is not in focus, the Viewport will reflect to the environmental settings specified by the current asset.

This option is only available to Environment assets.

The environmental settings specified by an Environment asset can also be made the Viewport's default by dragging the asset from the Asset Browser into the Viewport.

This also adds the asset to the level's list of Environment Presets in the
[/docs/static/engines/cryengine-5/categories/23756816/pages/35848989](
Level Settings
)
 tool.

 |

**
Create Instance
**

 |
Creates a Substance Instance file (
**
.crysub
**
) from a Substance Archive (
**
.sbsar
**
).

The option opens the
**
Create Substance Graph Preset
**
 window that allows users to specify the location, resolution and outputs for the desired Substance Instance.

This option is only available to Substance Archives; please refer to the documentation on the
[/docs/static/engines/cryengine-5/categories/23756816/pages/44968527](
Substance
)
 tool for more information on Substance Archives and Instances.

 |

**
Rebuild All Instances
**

 |
Regenerates all Substance Instances and texture files created from the currently selected Substance Archive.

This option is only available to Substance Archives; please refer to the documentation on the
[/docs/static/engines/cryengine-5/categories/23756816/pages/44968527](
Substance
)
 tool for more information on Substance Archives and Instances.

 |

**
Rebuild Instance
**

 |
Regenerates the currently selected Substance Instance.

This option is only available to Substance Instances; please refer to the documentation on the
[/docs/static/engines/cryengine-5/categories/23756816/pages/44968527](
Substance
)
 tool for more information on Substance Instances.

 |

**
Parent (Substance Instance)
**

 |

-
**
Go to
**
: When a Substance-based texture is located within the same folder as its parent Substance Instance, this option locates the parent Instance.

-
**
Open
**
: Opens the Substance Instance Editor tool, allowing users to edit the parent Substance Instance of the currently selected Substance-based texture.
This option is only available to Substance-based textures created from Substance Instances; please refer to the documentation on the
[/docs/static/engines/cryengine-5/categories/23756816/pages/44968527](
Substance
)
 tool for more information on Substance Archives and Instances.

 |

**
Work Files
**

**

**

 |
Lists all work files associated with the selected asset; a work file being any multimedia file type from which the asset is developed. Additionally the following options are provided for each listed work file:

-
**
Open...:
**
 Opens an appropriate desktop application to view the selected work file.

-
**
Copy Path:
**
Copies the address of the selected work file to the clipboard.

-
**
Show in File Explorer:
**
Locates the selected work file on disk.
Additional work files can be linked to an asset while previously linked files can be deleted via the
**
Work Files →
**

**
Manage Work Files...
**
option, which also lists previously linked work files. Please refer to
[/docs/static/engines/cryengine-5/categories/23756816/pages/35260066#AssetBrowser-AssociatingWorkFiles](
Associating Work Files to Assets
)
 in the Functionality section for more information.

 |

**
Rename
**

 |
Allows users to provide a custom name to created copies or duplicates of an asset.

 |

**
Open in File Explorer
**

 |
Locates the selected copy or duplicate of an asset on disk.

 |

**
Show Assets That Use
**

 |
Applies a dependency filter to the Search Results pane, such that only those assets which make use of the currently selected asset are displayed.

 |

**
Show Assets Used By
**

 |
Applies a filter that retrieves only those assets which are utilized by the currently selected asset are displayed.

 |

**
Assets
**

 |

-
**
Show Dependency Graph:
**
**

**
Depicts relationships between the currently selected asset and other assets of your project in a separate
[/docs/static/engines/cryengine-5/categories/23756816/pages/36868203](
Dependency Graph
)
 tool window.
 |

Assets contained in the
[https://www.cryengine.com/asset-db/product/crytek/cryengine-gamesdk-sample-project](
GameSDK
)
Sample Project are compressed and stored within
**
.pak
**
 files on disk.

Since archived files cannot be directly modified, users working with GameSDK may find that the
**
Rename
**
 and
**
Open in File Explorer
**
 options of the Asset Context Menu are unavailable for assets located within the GameSDK assets directory.

##
Version Control Context Menu

With a
[/docs/static/engines/cryengine-5/categories/23756816/pages/35848808](
Version Control System
)
 setup, the Folder Tree, Search Result Pane and Asset Context Menus might include additional options:

Option
 |
Description
 |

**
Refresh
**

 |
Manually updates the status of the selected version controlled assets.

With
**
View -> Shows Details/Split Horizontally/Split Vertically
**
 active, the
**
Version Control status
**
 column also serves to reflect the status of all version controlled assets. This column can further be used with search filters described in the
**
[/docs/static/engines/cryengine-5/categories/23756816/pages/35260066#AssetBrowser-search](
Smart & Advanced Search
)
**
 section below to make search queries specific to the status of these assets.

[Image: /docs/static/attachments/44959825]

*
Version Control Status
*

The status of these version controlled assets are also indicated at the top-right corner of their thumbnails when
**
View -> Thumbnails/Split Horizontally/Split Vertically
**
 is active.

[Image: /docs/static/attachments/44959826]

*
Version Controlled Assets
*

 |

**
Get Latest
**

 |
Retrieves the most recently modified version of the selected asset file from the repository.

 |

**
Check Out
**

 |
Retrieves an asset file from the repository to be worked upon locally; once Checked Out, a file will no longer be editable by other developers until local modifications have been Submitted or Reverted.

 |

**
Revert
**

 |
Discards all changes made to an asset file and restores it to its last local version.

 |

**
Revert if Unchanged
**

 |
Performs the above Revert operation upon an asset file only if its contents haven't been modified.

 |

**
Submit...
**

 |
Commits the selected locally modified assets to the repository.

The
**
Submit...
**
 option displays a separate window that lists within it all locally modified assets, work files and layers, and allows users to tick which changes they'd like to commit (including deletions made, if any).

The submission process can only be completed after a description of changes performed have been entered in the text box provided within the Submit window.

[Image: /docs/static/attachments/44959827]

*
Submit window
*

 |

The work files associated with an an asset are also tracked by the installed VCS.

If VCS is set up correctly, the
**
Work Files
**
 menu item that is visible on right-clicking an asset will contain options to perform the
**
Refresh, Get Latest, Check Out, Revert, Revert if Unchanged
**
 and
**
Submit...
**
 functions on the selected asset's work files as shown below.

[Image: /docs/static/attachments/44960117]

*
Work Files VCS
*

Additionally, the
**
Work Files
**
 version control menu also includes the option to
**
Remove local files
**
 which deletes copies of a version controlled asset's work files from the user's system, without deleting them from the repository. Since work files could be large in size, this option is especially useful in freeing up memory space.

Please refer to the
[/docs/static/engines/cryengine-5/categories/23756816/pages/35260066#AssetBrowser-AssociatingWorkFiles](
Associating Work Files to Assets
)
 section on this page for more information about adding work files to assets.

##
Functionality

Additional functionality provided by the Asset Browser includes:

##
Associating Work Files to Assets

Work files are those used in the design and development of an asset. For instance, a material (
**
.mtl
**
) file might have multiple Photoshop Document (
**
.psd
**
) files , TIFF, PNG files and or JPEG reference images as its work files.

The work files associated with any asset in the Asset Browser can be viewed from the Editor, provided these have been linked to the asset from the Asset Browser.

##
Adding Work Files

To add a work file, right-click an asset within the Asset Browser and select the
**
Work Files → Manage Work Files...
**
 option from the context menu. This opens the Manage Work Files window through which work files located within a project's asset directory can be linked to the selected asset.

*
[Image: /docs/static/attachments/36844716]

Manage Work Files
*

*
[Image: /docs/static/attachments/36844717]

Manage Work Files window
*

Clicking the
**
Add Files
**
 option brings up a file browser to locate and select the desired work files, while clicking
**
Save
**
 confirms the selection.
The different columns within the Manage Work Files window are as follows.

Column

 |
Description

 |

**
Name
**

 |
Indicates the name of the added work file.

 |

**
Path
**

 |
Specifies the directory within which the added work file is stored.

 |

**
Usage
**

 |
Indicates the number of assets that are also using the added work file.

 |

If using Version Control, an asset must be checked out before work files can be associated with it.

##
Viewing Work Files

Once linked, the work files associated with an asset can be viewed/located by right-clicking that asset's listing within the Asset Browser and selecting
**
Work Files.
**
**

**

[Image: /docs/static/attachments/36844906]

*
Work Files
*

##
Deleting Work File Associations

To delete an association between an asset and a specific work file, right-click the asset in the Asset Browser and select the
**
Work Files →
**

**
Manage Work Files...
**
 option to open the Manage Work Files window.

Hover over the desired work file with the mouse icon to reveal the
[Image: /docs/static/attachments/36844910]
 icon against its listing, and click the icon to cancel the association between the file and the currently selected asset.

While files of virtually any file type may be associated with an asset as its work files, these files must be located within the current project's
**
Assets
**
 directory.

##
Copying and Duplicating

Pressing
**
Ctrl + C
**
 with one or more assets selected within the Asset Browser copies those assets to the clipboard; these copies may be pasted within any folder of the project's
**
Assets
**
 directory using
**
Ctrl + V
**
.

Similarly pressing
**
Ctrl + D
**
with one or more assets selected creates duplicates of those assets within the same folder. Alternatively, copies and duplicates of assets can also be made using the
**
Copy
**
 and
**
 Duplicate
**
 options of the context menu generated by right-clicking an asset in the Asset Browser.

-
Although an asset located within the
**
Engine
**
 directory can be copied and pasted within a folder of a project's
**
 Assets
**
 directory,
assets cannot be copied to or duplicated in locations within the
**
Engine
**
 folder.
The
**
Engine
**
 folder is immutable by default, meaning its contents cannot be changed from within the Asset Browser.

-
When activated, the
**
View → Recursive View
**
option in the Asset Browser displays assets located within both the selected folder and its containing folders in the Search Results pane. Since the destination folder might be unclear or ambiguous in this view, copies of assets cannot be pasted with
**
Recursive View
**
 active.

-
Copying and duplicating Level, Schematyc Entity (
**
.schematyc_ent
**
) and Schematyc Library (
**
.schematyc_lib
**
) asset file types are not supported.

##
Favorites

The Favorites feature gives users the ability to bookmark and add to a list the most commonly used/liked assets. An asset may be added to/removed from the Favorites by toggling the star icon against their listings when
**
View → Shows Details/Split Horizontally/Split Vertically
**
 is active.

[Image: /docs/static/attachments/44968007]

*
Star Icons of Assets
*

Once added to the list of Favorites, the star icon against an asset's listing appears filled-in when
**
Shows
**
**
Details/Split Horizontally/Split Vertically
**
 is active, and at the top-left corner of its thumbnail when
**
Shows Thumbnails/Split Horizontally/Split Vertically
**
 is active as illustrated here.

[Image: /docs/static/attachments/36838722]

*
Star Icons of Asset Thumbnails
*

Either way, an exclusive list of Favorites may be accessed by clicking the star button situated on the left of the Search Assets bar.

[Image: /docs/static/attachments/44968008]

*
List of Favorites
*

Rather than display a complete list of starred assets all at once, the list of Favorites only displays those included within the currently selected folder/sub-folder of the Folder Tree.

##
Smart and Advanced Search

The Search Assets bar searches for assets included with the Engine/Assets directories of a project, by checking the entered search string against the Name and Type values of every asset.

It hence yields in its results those assets whose names or types match the entered string.

For example, assume the project's current repository of assets contains materials named
*
my_leaf
*
,
*
my_trunk
*
 and
*
grass
*
 respectively.

A search query containing the words
*
material
*
would yield results inclusive of the
*
my_leaf, my_trunk
*
and
*
grass
*
 material assets; similarly a search query containing the words
*
my material
*
 would include the
*
my_leaf
*
and
*
my_trunk
*
 assets in its results.

By default, the Search Assets bar searches for assets within all sub-folders included under the folder currently selected in the Asset Browser's Folder Tree.

Users wishing to confine their search results to only the selected folder however, can do so be deactivating the
**
View -> Recursive View
**
 option with the search string entered in the Search Assets bar.

##
Filter

The Filter button
[Image: /docs/static/attachments/36845071]
 situated to the right of the Search bar enables users to describe specific criteria by which the Search Results pane must list a project's various assets. Clicking the button yields
options to
**
Add Criterion, Clear Criteria
**
 and

**
Save/Load
**
 custom filters as required.

Clicking the
**
Add Criterion
**
 button presents a dropdown menu from which asset properties may be picked to specify your search criteria; the field adjacent to this dropdown helps specify the property value by which the Asset Browser must filter the list of objects.

[Image: /docs/static/attachments/36838228]

*
Search Assets Filter
*

Depending on the selected property, these values may need to be entered manually, picked from a separate dropdown or in the case of properties such as
**
Dependencies
**
, may require users to physically locate and specify assets with which dependency relationships might exist.

By default, filtering only yields search results from within the folder currently selected on the Folder Tree. Activating the
**
View → Recursive View
**
 option however, allows filtering to yield results from all sub - folders included within the current folder.

Clicking the
[Image: /docs/static/attachments/44960003]
 icon inverts the specified search criteria, while
**
Clear Criteria
**
 eliminates all specified properties and their respective values. The
**
Save/Load Filter
**
 option meanwhile generates a pop-up window which lists all previously created filters along with options to
**
Save
**
,
**
Load
**
 or
**
Delete
**
 these; a search bar at the top of this pop-up allows filtering through the listed filters.

[Image: /docs/static/attachments/44960018]

*
Save/Load/Delete Filter
*

Right-clicking the filter button opens a menu containing the
**
Clear Criteria
**
option, and a list of previously saved filters.

With multiple folders selected within the Folder Tree, searching for assets using the Search Bar will yield results from every selected folder..

##
Manipulating Assets

Assets may be included within a level by simply dragging and dropping them from the Asset Browser's Search Results pane into the Viewport. This allows for the quick placement of mesh and particle type assets, while even permitting material assets to be assigned to existing objects within a level.

In addition to this, assets may be:

##
Edited

Most assets may be edited by double-clicking upon their respective listings within the Asset Browser's Search Results pane; doing so upon Environment (
**
.env
**
), Material (
**
.mtl
**
), GeometryCache (
**
.cax
**
), Particles (.
**
pfx
**
), CSharpScript (
**
.cs
**
), SchematycEntity (
**
.schematyc_ent
**
) and SchematycLibrary (
**
.schematyc_lib
**
) files brings up the relevant editor tool.

On the other hand, double-clicking a texture (
**
.dds
**
) that has a TIFF source file opens the Texture compiler settings
[/docs/static/engines/cryengine-5/categories/23756816/pages/23308299](
dialog
)
, where settings such as the compression scheme, Mip map generation parameters and normal/alpha map combinations of the TIFF file can be configured.

Please note that an imported asset can be edited by this method only if its source files are available.

Files of the Mesh (
**
.cgf
**
), Skeleton (
**
.chr
**
), SkinnedMesh (
**
.skin
**
), AnimatedMesh (.
**
cga
**
), MeshAnimation (
**
.anm
**
), Character (
**
.cdf
**
) and Animation (
**
.caf
**
) types however may only be edited when imported via the

[/docs/static/engines/cryengine-5/categories/23756816/pages/44966294](
FBX
)
 importer. Eventual engine releases will gradually allow for all kinds of assets to be edited by double-clicking.

[Image: /docs/static/attachments/36838723]

Assets with unsaved changes are marked by an asterisk icon at the bottom-right of their thumbnails and names.

##
Deleted

By highlighting an asset's listing and hitting the Delete key. If dependencies exist between the asset and others within your project, a warning prompt will appear.

##
Moved

A similar prompt appears when an attempt is made to move assets by dragging and dropping their listings to the target folder in the Folder Tree.

##
Imported

Assets can be imported via the
**
File -> Import
**
 option of the Asset Browser, which automatically triggers the following dialog to choose between the asset's various elements that need importing.

**
[Image: /docs/static/attachments/36847133]

**
*
Importing Assets dialog
*

All assets are imported with their default settings, which may be changed later in the relevant Editor as explained previously. Alternatively, dragging and dropping an asset from your system's File Explorer to the destination folder within the Asset Browser automatically imports that asset's comprising elements as well.

Holding
**
Ctrl
**
 while doing so will generate the above dialog. Either way, the following table lists all file types supported by the importer.

Asset File Extension
 |
Produces
 |

**
.fbx
**

**

**

**

**
**
.abc
**
**

**

 |
StaticMesh
 (
**
.cgf
**
),
SkinnedMesh
 (
**
.skin
**
),
Skeleton
 (
**
.chr
**
),
SkeletalAnimation
 (
**
.caf
**
),
Material
 (
**
.mtl
**
) and
CharacterDefinition
 (
**
.cdf
**
) files.

Alembic (.
**
abc
**
) files, after the following Resource Compiler runs its course.

[Image: /docs/static/attachments/35959029]

*
Resource Compiler
*

 |

**
**
**
**
**
**
**
**
**
**
**
**
**
**
**
**
**
**
**
**
**
**
**
**
**
**
**
.bmp, .bmp2, .bmp3, .icb, .ico, .icon, .j2c, .j2k, .jbg, .jbig, .jng, .jng, jp2, .jpc, .jpe, .jpeg, .jpg, .jpgm, .jps, .jpt, .pipeg, .png, .png00, .png24, .png32, .png64, .png8, .ppm, .psd, .ptif, .svg, .svgz, .tga, .tiff, .tiff64, tif
**
**
**
**
**
**
**
**
**
**
**
**
**
**
**
**
**
**
**
**
**
**
**
**
**
**
**

 |
Texture (
**
.dds
**
) files

If importing a texture file of the listed file extensions fails, verify that the ImageMagick tool exists within the
**
 Tools/thirdparty
**
 directory of your engine build.

Imagick arrives bundled with the Engine and is made use of by its texture import functionality.

 |

Multiple assets can easily be dragged and dropped into the Asset Browser by holding down on either the
**
Shift
**
 or
**
Ctrl
**
 keys.

##
Tool-specific Asset Browsers and Instant Editing

The Environment Editor, Material Editor and Particle Editor tools have their own Asset Browser panels, which only display assets relevant to them.

These tool-specific Asset Browsers can be added to the windows of the Environment, Material or Particle Editor by selecting the
**
Window → Panels → Asset Browser
**
 option from their
[Image: /docs/static/attachments/36838191]
 menu. Once opened, the tool-specific Asset Browser can be docked within the tool window as desired.

Only assets that are relevant to the tool can be created within the tool-specific Asset Browser. Moreover, while the functionality of these tool-specific Asset Browsers is the same as the standalone Asset Browser, they have an additional Sync Selection feature which can be activated by clicking the
[Image: /docs/static/attachments/44964589]
 icon.

[Image: /docs/static/attachments/44964592]

*
Sync Selection in the Material Editor's Asset Browser
*

When Sync Selection is enabled, selecting an asset in the Asset Browser of the Environment, Material or Particle Editor immediately opens that asset in the Editor. T
his makes it very easy to cycle through different assets and edit them on the fly.

##
Live Updates for Asset Resource Selectors

When an object within a level is selected from the Level Explorer or the Viewport, the Properties tool displays a multitude of options by which an object's parameters may be tweaked.

Certain options within this Properties tool allow for custom files (such as that of Mesh, Material or Animation types) to be selected in relation with the asset; this is done by clicking upon the Asset Resource Selector which appears as a folder button against option fields as demonstrated below.

[Image: /docs/static/attachments/44959912]

*
Live Updates
*

Clicking upon an Asset Resource Selector automatically opens the Select Asset window, which allows for the desired asset files to be located in the format of an Asset Browser dialog. Any changes/selections made via this dialog is automatically applied to the selected object upon the Viewport.

The Asset Browser styled dialog can alternatively be replaced by a standard Open File window by setting the value of
**
ed_enableAssetPickers
**
, a
[/docs/static/engines/cryengine-5/categories/23756816/pages/25535264](
console variable
)
 to 0 via the
[/docs/static/engines/cryengine-5/categories/23756816/pages/44967641](
Console
)
.

##
Texture Tool-tips

Given a texture asset's listing within the Search Results pane, hovering the mouse over the texture generates an overview of its basic properties as illustrated below.

[Image: /docs/static/attachments/44968011]

*
Texture Tooltip
*

Additionally holding
**
CTRL
**
 during a mouse hover provides a larger image preview of the texture asset.

[Image: /docs/static/attachments/44968012]

*
Texture Tooltip (Large)
*

[#opening-the-asset-browser](
Opening the Asset Browser
)
[#1-menu](
1. Menu
)
[#2-navigation-bar](
2. Navigation Bar
)
[#3-folder-tree](
3. Folder Tree
)
[#4-search-results-pane](
4. Search Results Pane
)
[#functionality](
Functionality
)
[#associating-work-files-to-assets](
Associating Work Files to Assets
)
[#copying-and-duplicating](
Copying and Duplicating
)
[#favorites](
Favorites
)
[#smart-and-advanced-search](
Smart and Advanced Search
)
[#filter](
Filter
)
[#manipulating-assets](
Manipulating Assets
)
[#tool-specific-asset-browsers-and-instant-editing](
Tool-specific Asset Browsers and Instant Editing
)
[#live-updates-for-asset-resource-selectors](
Live Updates for Asset Resource Selectors
)
[#texture-tool-tips](
Texture Tool-tips
)
