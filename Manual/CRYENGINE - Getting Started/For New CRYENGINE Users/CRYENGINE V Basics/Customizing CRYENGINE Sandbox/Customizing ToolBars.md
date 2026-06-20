# Customizing ToolBars

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/36870764
- Page ID: 36870764
- Breadcrumb: CRYENGINE - Getting Started > For New CRYENGINE Users > CRYENGINE V Basics > Customizing CRYENGINE Sandbox > Customizing ToolBars
- Parent: Customizing CRYENGINE Sandbox

## Content

##
Overview

The toolbars can be customized to suit your needs. There are standard preset toolbars, but you can also create and customize your own toolbars.

The Sandbox Editor comes with a limited number of predefined toolbars. These can be found by going to the
**
Editor ->Toolbars
**
 folder in your Engine folder.

**
NOTE:
**
 the AppData is a hidden folder.
**
[/docs/static/engines/cryengine-5/categories/23756816/pages/23308628](
Check here
)
**
 how to display hidden folders.

Any new or modified toolbars will be saved to this Toolbars folder. When you edit one of the standard toolbars that came with the Editor, the edited version will also be saved here. If you ever remove this edited version, the toolbar will revert to the standard toolbar that came with the Editor.

##
Showing and Hiding Preset Toolbars

When opening the Sandbox Editor for the first time, not all preset toolbars are shown. By right-clicking the toolbar area, a context menu is opened in which you can show and hide several preset toolbars:

[Image: /docs/static/attachments/36850235]

##
Customizing Toolbars

The
**
Customize
**
 option in the context menu opens the toolbar customization
**

**
window which allows you to customize existing toolbars and create your own toolbars from scratch:

[Image: /docs/static/attachments/36850236]

##
Search Bar

In the top you'll find a search bar:

[Image: /docs/static/attachments/36850237]

This bar can be used to filter actions in the window below. For example, typing
*
display
*
 will filter out the
*
Cycle Displayinfo
*
 action, which lets you toggle between displaying different amounts of debug information in the top-right corner of the Viewport.

You can then drag and drop an action of your choice to the toolbar preview (see below) to add it to a toolbar.

##
Toolbar Editing Section

Under the list of actions is the toolbar editing section:

[Image: /docs/static/attachments/36850238]

In this section, you can switch between the existing toolbars, add new toolbars and remove them. You also see a preview of the toolbar with all the buttons that are on the toolbar you have chosen.

The following options are available in this section:

Button
 |
Option
 |
Description
 |

[Image: /docs/static/attachments/44958887]

 |
**
Toolbar dropdown menu
**
 |
Lets you display a preview of the existing toolbars so you can edit them.
 |

[Image: /docs/static/attachments/44958891]

 |
**
Create New Toolbar
**
 |
Lets you create a new toolbar.
 |

[Image: /docs/static/attachments/44958889]

 |
**
Rename Toolbar
**
 |
Lets you rename the selected toolbar.
 |

[Image: /docs/static/attachments/44958890]

 |
**
Remove Toolbar
**
 |
Removes the toolbar selected in the dropdown menu.
 |

You can drag and drop actions from the top of the window into the preview area at the bottom of this section. For example under
**
General
**
 the action
**
Clear Selection
**
**

**
can be dragged into the preview area. You can also right-click on a function (once it has been selected from a drop down menu) and then choose
**
Add.
**

In the Toolbar Preview, you can move buttons around as you see fit - just drag a button to a new position of your liking.

Right-clicking on the toolbar preview area will display a context menu:

[Image: /docs/static/attachments/36850239]

With this menu, you can perform the following actions:

Action
 |
Description
 |

**
Add Separator
**
 |
Adds a separating line between buttons for organization purposes.
 |

**
Add CVar
**
 |
Adds a button that a Console Variable can be assigned to. Click the button to choose a CVar and accompanying value (see Button Editing Section).
 |

**
Remove
**
 |
Removes the selected toolbar button or separator from the preview.
 |

##
Button Editing Section

The bottom section of the window is where you can edit the buttons:

[Image: /docs/static/attachments/36850240]

Depending on what kind of button you have selected in the toolbar preview, different options appear in the bottom of this window:

Option
 |
Description
 |

**
Name
**
 |
Displays the name of the button.
 |

**
Command
**
 |
Displays the command that is assigned to the button.
 |

**
CVar
**
 |
Shows the CVar assigned to the CVar button. The Browser button next to this field lets you browse and choose a CVar.
 |

**
Value
**
 |
Lets you assign a value to the CVar, for example: when choosing the
**
r_displayinfo
**
 CVar, a value of
**
0
**
 will let you turn off the debug info in the top-right corner of the Viewport (but not turn it back on again!), while entering a value of
**
1
**
 for the same CVar will let you toggle it on and off.
 |

**
Icon
**
 |
Lets you choose an icon for the buttons in the toolbar preview from a wide variety of old and new icons. Click the
**
Browse
**
 button next to the field to browse through a list of icons.
 |

##
Tool-Specific Toolbars

Many of the Sandbox's tools have their own toolbars. These toolbars have some default buttons, but they are just as customizable as the main toolbar, and work in the same way.

##
Toolbars Menu

In the Toolbars option in the menu
[Image: /docs/static/attachments/44965696]
, the following options are available:

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
Opens the toolbar customization window (
[/docs/static/engines/cryengine-5/categories/23756816/pages/36870764#CustomizingToolBars-CustomizingToolbars](
see above
)
) allowing users to create new toolbars and/or customize them, adding buttons specific to the tool the toolbar is in.

Most of the options available to put on a toolbar are also options in the menu
[Image: /docs/static/attachments/44965696]
of the respective tool.

 |

**
Lock Toolbars
**
 |
When disabled, the positions of toolbars and spacers within the tool can be changed by dragging and dropping, and spacers can be added.

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
Adds an expanding spacer to the toolbar layout; an expanding spacer pushes all elements situated at its ends to the edge of a panel.
 |

**
Insert Fixed Spacer
**
 |
Adds a spacer which has a fixed size of one button.
 |

**
Convert to Expanding/Fixed Spacer
**
 |
Changes the type of the spacer you right-clicked on.
 |

**
Toggle Spacer Type
**
 |
Toggles the type of the spacer you right-clicked on.
 |

**
Remove Spacer
**
 |
Removes the spacer you right-clicked on.
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
Lists all default and custom toolbars created for the respective tool, allowing you to select which toolbar you'd like hide or display.

 |

When a tool has a toolbar, whether this is a default one or a custom one, the options above are also available when right-clicking in the toolbar area (only when a toolbar is already displayed).

[#showing-and-hiding-preset-toolbars](
Showing and Hiding Preset Toolbars
)
[#customizing-toolbars](
Customizing Toolbars
)
[#tool-specific-toolbars](
Tool-Specific Toolbars
)
