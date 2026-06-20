# Test Runner

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/44109859
- Page ID: 44109859
- Breadcrumb: Editor Tools > Advanced Tab > Test Runner
- Parent: Advanced Tab

## Content

## Overview

The Test Runner is the tool dedicated to testing certain features of the engine, projects or the plugins that have been previously implemented. The Test Runner makes it possible to run feature tests more easily and quickly. It is especially useful for non-programmers as it can be used to run custom tests provided that they have been already introduced to the Engine.

The default tests that have been provided in the Test Runner tool can only be used to test the Engine-specific features. If a different feature needs to be tested, a related test should be introduced to the Engine first.

For more information about introducing new tests to Test Runner, please refer to the [Test Runner](../../../API%20Reference/CRYENGINE%20Game%20Code/Miscellaneous%20Game%20Code/Feature%20Tests/Custom%20Tests%20in%20the%20Test%20Runner.md) programming page.

The Test Runner tool can be used to run all the tests that are available under a category, or to run a test individually.

The tool can be found in **Tools → Advanced → Test Runner** and it is comprised of the following sections:

![Image](https://www.cryengine.com/docs/static/attachments/44957853)

### 1. Menu

The Menu can be accessed via the button on the top-right corner of the Test Runner. When clicked, it reveals the followingsub-menus.

#### Toolbars

Option | Description
--- | ---
**Customize...** | Opens the toolbar customization window allowing users to customize existing toolbars, and/or create new toolbars within this tool.
**Lock Toolbars** | When disabled, the positions of toolbars and spacers within this tool can be changed by drag and drop.
**Spacers** | The following options allow users to use spacers in positioning their toolbars. **Insert Expanding Spacer** | Adds an expanding spacer to the toolbar layout; an expanding spacer pushes all elements situated at its ends to the edge of a panel. --- | --- ** Insert Fixed Spacer** | Adds a fixed spacer, which has a fixed size of one icon. The ** Spacers** menu options are only available when ** Toolbars → Lock Toolbars** is disabled.
**Insert Expanding Spacer** | Adds an expanding spacer to the toolbar layout; an expanding spacer pushes all elements situated at its ends to the edge of a panel.
**Insert Fixed Spacer** | Adds a fixed spacer, which has a fixed size of one icon.
**Toolbars** | Lists all default and custom toolbars created for this tool, allowing you to select which toolbar you'd like to hide or display.

When a tool has a toolbar, whether this is a default one or a custom one, the options above are also available when right-clicking in the toolbar area (only when a toolbar is already displayed).

#### Window

Option | Description
--- | ---
**Panels** | Displays the panels that have been previously closed or not yet opened in the Test Runner. The following panels can be displayed with this option: - **Output** - ** Tests**
**Reset layout** | Resets the layout. This option is a quick way to go back to the default Test Runner layout.

#### Help

Opens the documentation page for this tool.

### 2. Tests Panel

The Tests panel displays all the available tests that can be executed. These can either be the default tests or the custom ones that were already introduced to the Engine by the user.

When a single test or a category is **right-clicked**, a context menu appears with ** Run selected tests** option which then can be clicked upon to execute these test(s).

The Tests panel is comprised of the following sections:

Section | Description
--- | ---
**Run All** | Executes all the tests that are currently available in the Tests list.
**Search Bar** | Searches for a specific test based on its name, displaying only the related tests on the list.
**Tests** | Displays the tests that can be executed.
**Results** | Displays the result of the tests that have been previously executed.

### 3. Output Panel

The Output panel of the Test Runner tool displays the result of each test that has been previously executed. The outcome of each test can be different depending on whether a it fails or succeeds.

The Output panel is especially useful to see where exactly in the Engine a test failed and why. It then helps the user to find the source of the problem and potentially fix it.

The test results will be archived in *<Project Folder>\user\testresults*, as an **.xml**file.
[1. Menu](#1-menu)[2. Tests Panel](#2-tests-panel)[3. Output Panel](#3-output-panel)
