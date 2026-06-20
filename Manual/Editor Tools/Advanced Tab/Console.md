# Console

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/44967641
- Page ID: 44967641
- Breadcrumb: Editor Tools > Advanced Tab > Console
- Parent: Advanced Tab

## Content

## Overview

The Console is a command-line editor, allowing access to many advanced functions within the Sandbox Editor, including various debug and test modes.

It is located in the top-left corner of the UI by default, in a tab next to the Create Object tool:

![Image](https://www.cryengine.com/docs/static/attachments/44967643)

It can also be opened by going to **Tools → Advanced → Console**.

When in Game Mode (**Ctrl+G**), the Console can be opened by pressing the tilde key (**~** on most keyboards, typically located in the top-left corner of your keyboard):

![Image](https://www.cryengine.com/docs/static/attachments/44967719)

The Console window in the Sandbox Editor is used to input Console Commands and Console Variables (CVars). It is treated as any other tool, and is therefore able to be docked anywhere in the User Interface.

### Menu

The Menu can be accessed via the![Image](https://www.cryengine.com/docs/static/attachments/44967642) icon on the top-right corner of this tool. When clicked, it reveals the following sub-menus:

#### File

Option | Description
--- | ---
**Save** | Exports a Console log file to a specified folder.

#### Edit

Option | Description
--- | ---
**Clear** | Clears the Console output window.
**Find...** | Opens a Search bar to search in the Console output window.
**Find Previous** | Finds the previous occurrence of your search.
**Find Next** | Finds the next occurrence of your search.

#### Toolbars

Option | Description
--- | ---
**Customize...** | Opens the toolbar customization window allowing users to customize existing toolbars, and/or create new toolbars within this tool.
**Lock Toolbars** | When disabled, the positions of toolbars and spacers within this tool can be changed by drag and drop.
**Spacers** | The following options allow users to use spacers in positioning their toolbars. **Insert Expanding Spacer** | Adds an expanding spacer to the toolbar layout; an expanding spacer pushes all elements situated at its ends to the edge of a panel. --- | --- ** Insert Fixed Spacer** | Adds a fixed spacer, which has a fixed size of one icon. The ** Spacers** menu options are only available when ** Toolbars → Lock Toolbars** is disabled.
**Insert Expanding Spacer** | Adds an expanding spacer to the toolbar layout; an expanding spacer pushes all elements situated at its ends to the edge of a panel.
**Insert Fixed Spacer** | Adds a fixed spacer, which has a fixed size of one icon.
**Toolbars** | Lists all default and custom toolbars (if any) created for this tool, allowing users to select which toolbar they'd like to hide or display.

When a tool has a toolbar, whether this is a default one or a custom one, the options above are also available when right-clicking in the toolbar area (only when a toolbar is already displayed).

#### Help

Option | Description
--- | ---
**Go to documentation...** | Opens the documentation page for this tool.
**Console Commands** | Opens a list of Console commands.
**Console Variables** | Opens a list of CVars.

### Command Line & Output Window

In the bottom of the Console you'll find the command line where you can enter Console Commands and Console Variables (CVars).

![Image](https://www.cryengine.com/docs/static/attachments/44967644)

For example, a console variable that is used rather often is **r_DisplayInfo**, to which different integral numbers can be assigned. A value of '1' for example means that some basic profiling information like the current Frames Per Second are shown at the top-right corner of the Viewport. A value of '0' disables the display of that information, while the value '2' will use another display mode with slightly different information.

### Using the Console

Using the Console is very straightforward: you enter a command or CVar in the command line, hit **Enter** and it will be executed.

The Console has its own search function built in, so you don't necessarily have to open the Console Commands and Console Variables screens mentioned above.

You can simply start typing part of a Console Command or CVar into the command line and you will see a list of color-coded search results in the Search Results window:

![Image](https://www.cryengine.com/docs/static/attachments/44967718)

You can then scroll through this list of search results by scrolling with the **mouse wheel** or with the ** Up** and ** Down** ** arrows**. Hitting ** Enter** or clicking the Console Command or CVar of your choice will select it and display it in the command line. All you then need to do is enter a value and hit ** Enter** again to execute it.

The second column displays the console variable name, where the first letter(s) before the underscore represent the module the command belongs to. For example: **r** for render and **g** for game.
For more advanced information please see the [Console and Config Usage](/docs/static/engines/cryengine-3/categories/1638401/pages/1605736) document.

### Console Commands & CVar Search Windows

In the Sandbox Editor, there are also separate windows to search for Console Commands that also give a description of what they do. This is especially useful for less advanced users.

#### Console Commands

For a full list of Console Commands, you can go to **Help -> Console Commands**. The following window will open:

![Image](https://www.cryengine.com/docs/static/attachments/44967648)

This is a fairly basic Search window for all existing Console Commands in the Sandbox Editor.

##### Search Bar

In the Search bar in the top, you can type anything you want to look for, and any command with the text you typed in its name will be displayed in the Search Results window below.

##### Search Results Window

In this window, results of searches you have entered in the Search Bar will be displayed. For example, searching for "position" will result in several commands including the text "position":

![Image](https://www.cryengine.com/docs/static/attachments/44967647)

In the Description column, a description of the command will be displayed.

#### Console Variables

For a full list of Console Variables, you can go to **Help -> Console Variables**. The following window will open:

![Image](https://www.cryengine.com/docs/static/attachments/44967646)

This is a similar search window to the Console Commands window, but this one is specifically designed for Console Variables.

##### Search Bar

In the Search bar in the top, you can type anything you want to look for, and any CVar with the text you typed in its name will be displayed in the Search Results window below.

##### Search Results Window

In this window, results of searches you have entered in the Search Bar will be displayed. For example, searching for the often-used "displayinfo" will result in a couple of CVars including the text "displayinfo":

![Image](https://www.cryengine.com/docs/static/attachments/44967645)

There are 4 columns in this Search Results window:

Column | Description
--- | ---
**Variable** | Shows the name of the Console Variable.
**Value** | Shows the value the CVar has in your level at the time of the search. Double-clicking on this value will let you change it right away without having to go back to the Console itself. Hit Enter to confirm the change and the change will be implemented.
**Description** | Gives a description of what the CVar does, including all possible values.
**Type** | Shows the type of the CVar.

##### Importing and Exporting CVars

There are also two buttons for importing and Exporting CVars in case you want to save them as a *.json file.

[Menu](#menu)[Command Line & Output Window](#command-line-and-output-window)[Using the Console](#using-the-console)[Console Commands & CVar Search Windows](#console-commands-and-cvar-search-windows)
