# MFC Editor to Qt Editor Interface (CRYENGINE V)

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/44963398
- Page ID: 44963398
- Breadcrumb: CRYENGINE - Getting Started > Migration Guides > MFC Editor to Qt Editor Interface (CRYENGINE V)
- Parent: Migration Guides

## Content

##
Overview

With the release of CRYENGINE 5.3 the old MFC Editor (up to CRYENGINE 3.8.6) has been deprecated, and is therefore no longer available for use. So to assist CRYENGINE users transition to our new QT Editor interface (CRYENGINE V onwards) we have put together the following short guide.

##
RollupBar

One of the main differences is the removal of the RollupBar:

![Image](https://www.cryengine.com/docs/static/attachments/44963448)

This was split into smaller tools. Starting from the left:

##
1st Tab (Objects)

The first tab
 has been replaced by 2 different tools:

Old (MFC)
 |
New (Qt)
 |

![Image](https://www.cryengine.com/docs/static/attachments/44963447)

 |
![Image](https://www.cryengine.com/docs/static/attachments/44963446)

![Image](https://www.cryengine.com/docs/static/attachments/44963449)

 |

**

**

**
[Create Object](../../Editor%20Tools/Level%20Editor%20Tab/Create%20Object.md)
**
 (
**
Tools -> Level Editor -> Create Object
**
 and
**
top left
**
 by default): this is the tool where the user can add
all objects
to a scene just like in the old Sandbox Editor.

**
[Properties](../../Editor%20Tools/Level%20Editor%20Tab/Properties.md)

**
(
**
Tools -> Level Editor -> Properties
**
 and on the
**
right
**
 by default): this panel shows all relevant properties of the selected object.

##
2nd Tab (Terrain)

 The second tab has been separated into 3 tools:

Old (MFC)
 |
New (Qt)
 |

![Image](https://www.cryengine.com/docs/static/attachments/44963445)

 |
![Image](https://www.cryengine.com/docs/static/attachments/44963409)

![Image](https://www.cryengine.com/docs/static/attachments/44963410)

![Image](https://www.cryengine.com/docs/static/attachments/44963442)

 |

**
[Terrain Editor](../../Editor%20Tools/Terrain%20Editor.md)
**
 (
**
Tools -> Terrain Editor
**
): this tool not only contains the elements that
were
previously located in the second tab of the
RollupBar,
 but it also contains other terrain relevant tools that were scattered in different places in the old Sandbox Editor such as Terrain Texture Layers.

**
[Vegetation Editor](../../Editor%20Tools/Vegetation%20Editor.md)
**
 (
**
Tools -> Vegetation Editor
**
): this is a tool that has basically been stripped out of the RollupBar. However, it still has the same functionality and serves the same purpose as it did before.

**
[Level Settings](../../Editor%20Tools/Level%20Editor%20Tab/Level%20Settings.md)

**
(
**
Tools -> Level Editor -> Level Settings
**
): most of the settings under Environment have been stripped out of the RollupBar and changed to the Level Settings. Notice that Volumetric Cloud settings have been added.

##
3rd Tab (Modelling)

The modelling tools in the third tab are no longer supported:

![Image](https://www.cryengine.com/docs/static/attachments/44963441)

##
4th Tab (Display)

Most of the display settings in the fourth tab have been moved to the
**
[Display](../For%20New%20CRYENGINE%20Users/CRYENGINE%20V%20Interface/Viewport%20Window/Display%20Settings.md)
**
 menu in the header of the 3D Viewport.

Some tools also include V
iewports. In these cases
**

**
the Display menu is also included to allow for customization.
Old (MFC)
 |
New (Qt)
 |

![Image](https://www.cryengine.com/docs/static/attachments/44963440)

 |
![Image](https://www.cryengine.com/docs/static/attachments/44963425)

 |

##
5th Tab (Layers)

The fifth tab has turned into its own tool, the
**
[Level Explorer](../../Editor%20Tools/Level%20Editor%20Tab/Level%20Explorer.md)
**
. The Level Explorer also takes over the functionality of the
**
Select Objects
**
 tool. It’s the way that the user can configure the Level Explorer tool that defines its purpose:

Old (MFC)
 |
New (Qt)
 |

![Image](https://www.cryengine.com/docs/static/attachments/44963438)

 |
![Image](https://www.cryengine.com/docs/static/attachments/44963436)

 |

The Level Explorer can be configured to cover functionality of both previous tools and it can also be opened more than once, hence if you want to mimic the behavior of those tools it's completely possible.

By adding filters a user can get the same setup as the previous
**
Select Object
**
 tool. The example below shows that filters can be setup exactly the same way as before:

Old (MFC)
 |
New (Qt)
 |

![Image](https://www.cryengine.com/docs/static/attachments/44963437)

![Image](https://www.cryengine.com/docs/static/attachments/44963407)

 |
![Image](https://www.cryengine.com/docs/static/attachments/44963406)

![Image](https://www.cryengine.com/docs/static/attachments/44963435)

 |

##
Filters

By using the
**
[filter system](../For%20New%20CRYENGINE%20Users/CRYENGINE%20V%20Interface/Update%205.3%20-%20UI%20Improvements.md)
**
 in the
**
Level Explorer
**
(accessed with the  button), the same filter options are available, and more:

Old (MFC)
 |
New (Qt)
 |

![Image](https://www.cryengine.com/docs/static/attachments/44963434)

 |
![Image](https://www.cryengine.com/docs/static/attachments/44963431)

 |

It is possible to create a separate filter for each type, but it is recommended to tick all the preferred types in the list and combine them into one single filter (see above).

##
Other MFC Editor Tools

##
Lighting Tool

The functionality of the
**
Lighting Tool
**
 was moved to the bottom left corner of the
**
Environment Editor
**
.

The
**
 Environment Editor
**
is a new name for the
**
Time Of Day
**
 Editor. The name has been changed due to our future plans of expanding its functionality:

Old (MFC)
 |
New (Qt)
 |

![Image](https://www.cryengine.com/docs/static/attachments/44963430)

![Image](https://www.cryengine.com/docs/static/attachments/44963404)

 |
![Image](https://www.cryengine.com/docs/static/attachments/44963429)

 |

##
Navigation Toolbars and Options

Old (MFC)
 |
(click images to enlarge)

![Image](https://www.cryengine.com/docs/static/attachments/44963428)

 |

New (Qt)
 |
![Image](https://www.cryengine.com/docs/static/attachments/44963427)

 |

##
Camera Settings

Previously at the top of the Viewport there were options such as fov, ratio, resolution and settings inside of the perspective menu.

These options have now moved to the
[Camera](../For%20New%20CRYENGINE%20Users/CRYENGINE%20V%20Interface/Viewport%20Window/Camera%20Settings.md)
menu in the top-left corner of the Viewport:

![Image](https://www.cryengine.com/docs/static/attachments/44963401)

On the right side are 3 speed settings that
were
previously located at the bottom of the screen:

Old (MFC)
 |
New (Qt)
 |

![Image](https://www.cryengine.com/docs/static/attachments/44963426)

 |
![Image](https://www.cryengine.com/docs/static/attachments/44963400)

 |

##
Snapping

The 7 icons next to the
**
Display
**
 button in CRYENGINE V represent ways of
**
[snapping objects](../For%20New%20CRYENGINE%20Users/CRYENGINE%20V%20Basics/Snap%20%26%20Alignment.md)
**
. These were previously located in the
**
Object
**
 toolbar. The 6
th
 icon is a 3 toggle type button that will change how detailed frame statistics are displayed. The 7th icon is a toggle to hide or unhide helpers:

Old (MFC)
 |
New (Qt)
 |

![Image](https://www.cryengine.com/docs/static/attachments/44963422)

 |
![Image](https://www.cryengine.com/docs/static/attachments/44963424)

 |

##
Bottom Bar

The bottom bar of the old MFC Editor has been removed. These options have been moved to different places:

![Image](https://www.cryengine.com/docs/static/attachments/44963423)

The
**
coordinates for selected objects
**
 are now located in the
**
Properties
**
 (when an object is selected):

![Image](https://www.cryengine.com/docs/static/attachments/44963402)

**
Camera speed
**
has moved to the top-left of the 3D Viewport:

![Image](https://www.cryengine.com/docs/static/attachments/44963400)

**
Enabling AI/Physics
**
 has moved to the
**
Game
**
 menu. It also has a button in the Game toolbar that is displayed by default at the top of the main UI:

![Image](https://www.cryengine.com/docs/static/attachments/44963399)

**
Audio
**
 related options are now located in the
**
Game -> Audio
**
 menu.

The
**
Goto position
**
 tool is now located in the
**
Level
**
 menu.

##
Error Report

In older versions of CRYENGINE (up to 3.8.6) a window popped up when an error occurred. From CRYENGINE V, we now have the
**
[Notification Center](../../Editor%20Tools/Advanced%20Tab/Notification%20Center.md)
**
.
**

**
This is a centralized place where errors, warnings and ongoing tasks as well as completed tasks and other useful information are displayed:

Old (MFC)
 |
New (Qt)
 |

![Image](https://www.cryengine.com/docs/static/attachments/44963420)

 |
![Image](https://www.cryengine.com/docs/static/attachments/44963419)

 |

##
Asset Browser/Texture Browser

Among other changes that come with the latest revision of the Sandbox Editor it's important to mention that new
**
[Asset Browser](../../Editor%20Tools/Asset%20Browser.md)

**
is
**
NOT
**
 the same or just a visually improved old
**
Asset
**
 or
**
Texture Browser
**
.

The new Asset Browser will (in the future) have a central role in managing assets available for the Sandbox:

Old (MFC)
 |

 |
New (Qt)
 |

![Image](https://www.cryengine.com/docs/static/attachments/44963418)

 |
![Image](https://www.cryengine.com/docs/static/attachments/44963403)

 |
![Image](https://www.cryengine.com/docs/static/attachments/44963416)

 |

##
Menu Items Rearrangement

In order for the layout to make more sense in the new Qt Editor, the tools and menus have been rearranged, some tools have been combined and some items have been split. However, all the tools that users could find in the 'old' MFC Editor can still be found, but with more purpose and logic behind them.

Some deprecated items have been removed.
Old (MFC)
 |
![Image](https://www.cryengine.com/docs/static/attachments/44963415)

 |

New (Qt)
 |
![Image](https://www.cryengine.com/docs/static/attachments/44963414)

 |

##
Merged Windows Feature

One of the behaviors that many users liked in the 'old' MFC Editor was that the Sandbox and its windows were shown as a single tab on a task bar. For some users “alt tabbing” between tools is cumbersome and ineffective, so there is an option in the new Qt Editor under the
**
[Preferences](../For%20New%20CRYENGINE%20Users/CRYENGINE%20V%20Basics/Customizing%20CRYENGINE%20Sandbox/Changing%20Sandbox%20Preferences.md)
**
 menu that allows for the same behavior that could be found in the 'old' MFC Editor:

![Image](https://www.cryengine.com/docs/static/attachments/44963413)

Please note that by default the UX is designed with the above option set to 'off'. Windows management will be less efficient once the Sandbox Editor has more complex tools with more sub-windows. Also the child windows will be obscured, thus making it more cumbersome to use. For example: the Asset System will give one window for each asset the user wants to have open, hence many windows will very likely be hidden behind other bigger windows and without the user even noticing it.

[RollupBar](#rollupbar)
[1st Tab (Objects)](#1st-tab-objects)
[2nd Tab (Terrain)](#2nd-tab-terrain)
[3rd Tab (Modelling)](#3rd-tab-modelling)
[4th Tab (Display)](#4th-tab-display)
[5th Tab (Layers)](#5th-tab-layers)
[Other MFC Editor Tools](#other-mfc-editor-tools)
[Lighting Tool](#lighting-tool)
[Navigation Toolbars and Options](#navigation-toolbars-and-options)
[Snapping](#snapping)
[Bottom Bar](#bottom-bar)
[Error Report](#error-report)
[Asset Browser/Texture Browser](#asset-browsertexture-browser)
[Menu Items Rearrangement](#menu-items-rearrangement)
[Merged Windows Feature](#merged-windows-feature)
