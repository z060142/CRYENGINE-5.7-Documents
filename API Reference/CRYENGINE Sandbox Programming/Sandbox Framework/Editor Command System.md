# Editor Command System

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/26873102
- Page ID: 26873102
- Breadcrumb: CRYENGINE Sandbox Programming > Sandbox Framework > Editor Command System
- Parent: Sandbox Framework

## Content

## Using commands

Editor commands are used to allow automation and scripting of the editor and should be one of the primary means of extending editor functionality. It is one of the most central systems and making sure all possible actions of your plugin or module are available through commands should be a priority.

Here are things that editor commands can do:

- All registered commands can be used in Console panel (Tools -> Advanced -> Console).
- Editor commands not taking any parameters can be bound to a keyboard shortcut (Edit -> Keyboard Shortcuts)
- Custom commands can be created out of existing commands to make custom shortcuts
- Commands are the primary means to create menu entries
- Commands can be used in user-created toolbars

## Editor Command

To create a simple command that can be executed via console use `REGISTER_EDITOR_COMMAND` marco defined in the ` ICommandManager.h` file.

**Sample console command**

`#include <ICommandManager.h>` ` void` ` SampleCommand()` `{` `// the body of the command` `}` ` REGISTER_EDITOR_COMMAND(SampleCommand, sample, sample_command, CCommandDescription(``"Sample command description"``));`
---

It accepts the following parameters:

- Function the needs to be executed.
- Module's name the command belongs to.
- Command's name.
- Command's description.

This command, therefore, can be executed via console by typing "sample.sample_command".

The editor commands are also made available to Python and other scripting languages the Sandbox can interface with.

## Python console command

It is also possible to register a command in a way so that it will be possible to access the command via Python eco system, as well as other scripting languages if the Sandbox gets interfaced with new scripting languages. It is not recommended to register Python commands as Editor commands are also made available to Python.

In order to do that one of the following macros can be used: `REGISTER_PYTHON_COMMAND` or ` REGISTER_PYTHON_COMMAND_WITH_EXAMPLE`. It makes the command accessible through the console as well as other Python tools (like Tools -> Advanced -> Python Interactive Console).

The signature of `REGISTER_PYTHON_COMMAND` is identical to `REGISTER_EDITOR_COMMAND`. For ` REGISTER_PYTHON_COMMAND_WITH_EXAMPLE,` it takes one additional parameter which is a string that shows the usage of the command in a Python script.

**Sample Python command**

`void` ` SampleCommand()` `{` `// the body of the command` `}` ` REGISTER_PYTHON_COMMAND_WITH_EXAMPLE(SampleCommand, sample, sample_command,``"Sample command description"``,``"sample.sample_command()"``);`
---

## Attaching to menu items

The Registered command can be added to menus as such. Note that CEditor provides helper methods to add commands to its menus.

`void` ` showContextMenu()` `{` ` ICommandManager* pManager = GetIEditorImpl()->GetICommandManager();` ` QMenu* pMenu =``new` ` QMenu();` ` pMenu->addAction(pManager->GetAction(``"sample.sample_command"``));` ` pMenu->popup(QCursor::pos());` `}`
---

## Setting additional properties

Some additional property can be specified for a command: shortcut displayed text and icon (for UI components).

In order to set them, the `REGISTER_EDITOR_UI_COMMAND_DESC` macro is to be used. It takes the following parameters:

- Module name
- Command name
- Text to display
- Shortcut (of type `CKeyboardShortcut).` Can also be given as string as there is implicit conversion to ` CKeyboardShortcut.`
- Icon to display (formatted string).

There are also some convenience macros in case only one of aforementioned properties needs to be set: `REGISTER_EDITOR_COMMAND_SHORTCUT`, ` REGISTER_EDITOR_COMMAND_ICON` and ` REGISTER_EDITOR_COMMAND_TEXT`.

**Setting additional properties**

`REGISTER_EDITOR_UI_COMMAND_DESC(general, copy,``"Copy"``, CKeyboardShortcut::StandardKey::Copy,``"icons:General/Copy.ico"``);` ` REGISTER_EDITOR_COMMAND_SHORTCUT(asset, open_browser,``"Alt+F2; Ctrl+Alt+B"``);` ` REGISTER_EDITOR_COMMAND_ICON(physics, single_step,``"icons:Trackview/trackview_time_pause.ico"``);` ` REGISTER_EDITOR_COMMAND_TEXT(terrain, duplicate_layer,``"Duplicate Layer"``);`
---

## Engine console command

Engine console commands can also be called from the editor console however they do not allow any editor functionality such as shortcuts or menu usage.

To register a new console command, use macro `REGISTER_COMMAND` defined in ` CrySystem/ISystem.h`. See CrySystem documentation: **[Console](../../CRYENGINE%20Engine%20Code/Engine%20Modules/CrySystem/Console.md)**
