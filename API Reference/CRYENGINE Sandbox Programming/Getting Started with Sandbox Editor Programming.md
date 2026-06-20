# Getting Started with Sandbox Editor Programming

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/26875248
- Page ID: 26875248
- Breadcrumb: CRYENGINE Sandbox Programming > Getting Started with Sandbox Editor Programming
- Parent: CRYENGINE Sandbox Programming

## Content

## Overview

Welcome to the Sandbox Editor Programming section!

Here we go over the resources and knowledge that are necessary to work with Sandbox Editor code and to develop Editor Plugins that are fully integrated with the Sandbox and its most advanced systems. Do be aware that the 'Sandbox Editor' is often referred to as just the 'Sandbox' - hence the terms Sandbox Editor and Sandbox are completely interchangeable.

We are looking forward to contributions from the CRYENGINE community to strengthen and supplement the tools that are offered with CRYENGINE.

## Qt and MFC

Sandbox relies primarily on Qt and in particular QWidgets. Please get familiar with this library as all the new UI code must be made using **Qt**.

If you are not familiar with this, then there are plenty of very well documented online resources. You can also download the Sandbox Editor source code to help to debug certain issues.

- [Qt Widgets](https://doc.qt.io/qt-5/qtwidgets-index.html)
- [Widgets Tutorial](https://doc.qt.io/qt-5/qtwidgets-tutorials-widgets-windowlayout-example.html)

From CRYENGINE 5.0 onwards, the Sandbox has been partially rewritten using Qt and its architecture has been restructured towards a more modern and modular Editor while supporting extensions for the various Editor and Engine plugins.

This was an extremely ambitious goal, so we decided to focus on the core of the Sandbox whilst still allowing certain modules within the Sandbox to remain unchanged. Some of these modules still use some MFC UI components (MFC was used in pre-CRYENGINE 5.0 versions of the Engine), hence MFC only remains in modules that haven't yet been converted to Qt.

So the main takeaway is that even though new modules should be made according to the rules laid out in these documentation pages, you may still encounter code that does not follow all of the rules and still uses MFC components and parts of the old architecture. **The Sandbox code is still going through a major transition** and while the **interfaces should remain stable** the core code is still subject to major changes as we continue the conversion effort. When operating in "legacy" modules make sure that you only fix bugs as necessary and in general **avoid copy-pasting code** as legacy modules no longer follow our new conventions.

## Guidelines

All of the following are **MUST-READ** documents for every Programmer that deals with Tools code. These guidelines need to be followed for any contribution to the main Sandbox code or the official plugins. We recommend that 3rd party developers also follow these guidelines to ensure quality and consistency in the code and user experience.

- [User Experience Guidelines](User%20Experience%20Guidelines.md)
- [Qt Programming in Sandbox](Qt%20Programming/Qt%20Programming%20in%20Sandbox.md)
- [UI Programming Patterns](Qt%20Programming/UI%20Programming%20Patterns.md)

## Getting Started

In order to program in the Sandbox you must generate the projects using the CMake option **OPTION_SANDBOX**. It is also useful to have the ** OPTION_SAMPLEPLUGIN**turned on if you want to use this as a template to base your plugin on.

For more information on CMake, please refer here: [CMake 5.5.2](/docs/static/engines/cryengine-5/categories/23756813)

## Common Use Cases

If you are developing for the Sandbox, then the chances are you are trying to do one of the following common tasks. If so, follow the process below.

- [Create a new plugin](Sandbox%20Framework/Sandbox%20Plugins/Sandbox%20C%2B%2B%20plugins.md)
- [Add a new asset type and an editor for this asset type](Sandbox%20Framework/Asset%20System.md)
- [Add a new tool window that is not related to ass](Sandbox%20Framework/Creating%20a%20new%20editor%20window.md)[et](Sandbox%20Framework/Creating%20a%20new%20editor%20window.md)[management or editing](Sandbox%20Framework/Creating%20a%20new%20editor%20window.md)
- [Add new commands](/docs/static/engines/cryengine-5/categories/23756813/pages/26873100)
- Add any **reusable Sandbox code** (i.e. widget, utilities...). These should always go in ** EditorCommon**and be contributed to the main CRYENGINE branch.
- Fix any bug. This should be contributed back through a pull request as it serves the entire CRYENGINE community.

In general, new asset types and associated tools should go into one separate plugin. In this case you only need to focus on editing the content of your asset type, the Sandbox should provide the rest of the functionality such as file management, source control and integration with the Asset Browser.

## Architecture Overview

### Projects and Packages

- **EditorQt:** It is the core of the application itself but still contains some legacy code.
- **EditorInterface:** All the public abstract interfaces provided by the Editor. These will be replicated to Python/C#.
- **EditorCommon (Plugins/EditorCommon):**
- Reusable components and utilities for Editor programming. If you are making something reusable, then write your code there and not in your plugin.
- Implementation of some interfaces. Some systems are fully implemented in EditorCommon, but their instantiation and management are done in the Sandbox.
- **Sandbox (EditorQt):**

- The executable application itself. Implements and/or instantiates all the systems from the interface and loads all the plugins.
- Sandbox is host to all the level editor code and logic.
- No other package should have a dependency towards the Sandbox.
- Sandbox still depends on MFC for the time being.

- **Plugins:**
- A self-contained feature that plugs into the Sandbox.
- All new functionality should be made as a plugin, unless it is part of an already existing module/plugin. New plugins should only depend on EditorInterface and EditorCommon.
- Deprecated features should be moved into a plugin and released with the source to the public for them to maintain if necessary.
- Some old plugins still depend on MFC.

### Features

- [Creating a new editor window](Sandbox%20Framework/Creating%20a%20new%20editor%20window.md)
- [Asset System](Sandbox%20Framework/Asset%20System.md)
- [Sandbox Plugins](Sandbox%20Framework/Sandbox%20Plugins.md)
- [Editor Command System](Sandbox%20Framework/Editor%20Command%20System.md)
- [Preferences and Settings](Sandbox%20Framework/Preferences%20and%20Settings.md)
- [Personalization](Sandbox%20Framework/Personalization.md)
- [Serialization and Property Trees](Sandbox%20Framework/Serialization%20and%20Property%20Trees.md)
- [Undo system](Sandbox%20Framework/Undo%20system.md)
- [Notifications and Error Reporting](Sandbox%20Framework/Notifications%20and%20Error%20Reporting.md)
- [Integrated Documentation](Sandbox%20Framework/Integrated%20Documentation.md)
- [Theme, Styling and Colors](Sandbox%20Framework/Theme%2C%20Styling%20and%20Colors.md)
- [Sandbox Threading API](Sandbox%20Framework/Sandbox%20Threading%20API.md)

[Qt and MFC](#qt-and-mfc)[Guidelines](#guidelines)[Getting Started](#getting-started)[Common Use Cases](#common-use-cases)[Architecture Overview](#architecture-overview)
