# Customizing Sandbox Layout

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/36865952
- Page ID: 36865952
- Breadcrumb: CRYENGINE - Getting Started > For New CRYENGINE Users > CRYENGINE V Basics > Customizing CRYENGINE Sandbox > Customizing Sandbox Layout
- Parent: Customizing CRYENGINE Sandbox

## Content

## Overview

CRYENGINE allows you to scale, move and dock windows any way you want. On this page, we'll explain how.

### Scaling and Moving Tools

Scaling and moving tools works the same way as in Windows.

To scale a window, move the mouse pointer to the edge of the window so that it turns into a double-ended arrow. Click and hold the left mouse button and move the mouse cursor.

To move a window, click and drag its title bar to your preferred position.

### Docking Windows

Docking helpers will automatically appear whenever a window is dragged over another window, or the Sandbox Editor itself.

There are various places a window can be docked to: to the sides, top and bottom of the entire screen, to the sides, top and bottom within another window and as a tab within another window. These are all detailed below.

To explain how it works, the**Flow Graph** window is used, but of course this applies to any window.

#### Docking in the Entire Screen

To dock the selected window to the side, top or bottom of the entire screen, select the title bar of the window that should move and drag it. A docking helper will appear in the middle and the edges of the screen. Drag the title bar of the window over one of the outer helpers:

![Image](https://www.cryengine.com/docs/static/attachments/36839216)

A blue preview of where the window will end up in the screen will appear:

![Image](https://www.cryengine.com/docs/static/attachments/36839215)

Let go once this preview is visible and the window will be docked in the specified location:

![Image](https://www.cryengine.com/docs/static/attachments/36839214)

#### Docking Within Another Window

To dock the selected window to the side, top or bottom of another window, drag the window by its title bar and move it over to the window it needs to be docked into. The docking helpers will appear in the middle of that window instead of in the middle of the entire screen. Now drag the title bar of the selected window over the inner docking helpers:

![Image](https://www.cryengine.com/docs/static/attachments/36839213)

Once again, a blue preview of where the window will end up will appear:

![Image](https://www.cryengine.com/docs/static/attachments/36839212)

Let go of the mouse button and the window will be docked.

This can also be done within other windows next to the Viewport:

![Image](https://www.cryengine.com/docs/static/attachments/36839211)

#### Docking a Window as a Tab

This is a great space saver, especially if only one monitor is used.

There are two ways to dock a window as a tab.

##### Using the Docking Helper

Drag the title bar of the window that needs to be docked onto the central docking helper:

![Image](https://www.cryengine.com/docs/static/attachments/36839210)

The whole window that it will be docked into as a tab will turn blue:

Now let go and another tab will have appeared in the window:

![Image](https://www.cryengine.com/docs/static/attachments/36839209)

Now it is possible to switch between the windows in that section by clicking on the appropriate tab.

##### Dropping Inside the Tab Area

The title bar of the selected window cab also be dragged into the tab area of the target window. It will then be placed to the right of the tab that turns blue:

![Image](https://www.cryengine.com/docs/static/attachments/36839208)

### Changing Tab Order

The order of tabs within a window can be changed by dragging a tab and dropping it:

![Image](https://www.cryengine.com/docs/static/attachments/36839207)

### Undocking Windows

To move a window from its docked position to somewhere else, simply drag the tab of the window away and it will undock and behave as a normal, floating window.

#### Undocking More Than One Tab

It is also possible to undock (and re-dock) more than one tab at a time. To do this, click and drag the empty space next to the tabs in a pane:

![Image](https://www.cryengine.com/docs/static/attachments/36839316)

### Closing Tabs

Tabs do not have a cross in the top-right corner to close them, as you may expect. Instead, they require a right click to display an option to close them:

![Image](https://www.cryengine.com/docs/static/attachments/36839206)

### More Tabs than Fit the Screen

When there are more tabs in a panel than fit the screen, a dropdown menu will appear for easy access to all the tabs:

![Image](https://www.cryengine.com/docs/static/attachments/36839205)

### Resetting the Sandbox Layout

If the Sandbox layout needs to be reset to the default settings, choose**Layout -> Reset Layout**. This will undo all the changes made to the layout and show only the toolbars that are shown by default.

### Project Layouts

When working in a team of developers and using source control, it is possible to share custom layouts with others very easily.

Do this by copying its *.json file from your * local* project folder (by default `C:\Users\<User_Name>\AppData\Roaming\Crytek\CRYENGINE\Layouts`) to the ` Engine\Layouts`folder in your game folder. The latter folder may need to be created as it doesn't exist by default.

Now the custom layout can be checked into source control along with the rest of the project data so they appear for the rest of the team as well, next to any layouts they have created for themselves.

*![Image](https://www.cryengine.com/docs/static/attachments/36839282)*

[Scaling and Moving Tools](#scaling-and-moving-tools)[Docking Windows](#docking-windows)[Changing Tab Order](#changing-tab-order)[Undocking Windows](#undocking-windows)[Closing Tabs](#closing-tabs)[More Tabs than Fit the Screen](#more-tabs-than-fit-the-screen)[Resetting the Sandbox Layout](#resetting-the-sandbox-layout)[Project Layouts](#project-layouts)
