# Update 5.2 - UI Improvements

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/25533211
- Page ID: 25533211
- Breadcrumb: CRYENGINE - Getting Started > For New CRYENGINE Users > CRYENGINE V Interface > Update 5.2 - UI Improvements
- Parent: CRYENGINE V Interface

## Content

##
Overview

Other than the previously mentioned components, there are more small but important components in the top-right corner of the UI; the
**
Main
Menu Search
**
 window and the
**
Notification Center
**
. Also, the file dialog window has been changed.

##
Main Menu Search Window

In the top-right corner of the UI the Menu Search window can be found:

*
![Image](https://www.cryengine.com/docs/static/attachments/25510249)

*

With this window, any tool or option in the
 main
**

**
menu bar can be found and executed very easily.

For example, typing "material" will show all options and tools in the menu bar containing "material:

![Image](https://www.cryengine.com/docs/static/attachments/25510250)

The right column will show where each tool or option is located in the menu bar.

You can then either click on the tool or option you're looking for to execute it, or navigate through the list with the
**
Up
**
 and
**
Down
**

**
arrow
**
 buttons and press
**
Enter
**
.

##
Notification Center

The notification center is a combination of pop-up messages that are not modal and don't require user input, and is a place where a list of tasks, errors and warnings can be seen. These messages show notifications, warnings and errors and background tasks.

*
![Image](https://www.cryengine.com/docs/static/attachments/25510410)

*

In this corner, by default, pop-up messages will appear. These messages:

-
will contain an icon detailing its critical level (Info, Warning, Assert and Error)

-
can be clicked on to immediately hide them and take you to where the error is

-
will be, by default, combined into a single pop-up (if they are notifications coming from warnings, asserts and errors)

-
can be completely disabled in the preferences panel described below
**
Shift+left click
**
 will hide all current pop ups.

When you click on the button next to the Menu Search window, the Notification Center window appears. This window has three tabs,
**
Current
**
,
**
History
**
 and
**
Preferences
**
.

The Notification Center can also be opened by going to
**
Tools -> Advanced -> Notification Center
**
.

##
Current

The Current tab shows a collection of all notifications.

![Image](https://www.cryengine.com/docs/static/attachments/25511199)

-
Notifications coming from warnings, asserts and errors will be, by default, combined into a single notification after more than 25 are displayed. This option can be disabled, and the number can be tweaked in the preferences panel described below

-
Clicking on a notification in this panel will hide it, and if possible, take the user to were the error originated from

-
Right clicking a notification will spawn a context menu with an option to copy the contents of the message in the notification

-
All notification can be hidden by clicking the
**
Clear All
**
(
![Image](https://www.cryengine.com/docs/static/attachments/25510420)
) button on the top-left

##
History

The Notification History contains a full history of messages. Double-clicking an item will, if possible, take the user to where the error originated from.

![Image](https://www.cryengine.com/docs/static/attachments/25510419)

Button
 |
Description
 |

![Image](https://www.cryengine.com/docs/static/attachments/25510420)
 |
Clears the list of messages.
 |

![Image](https://www.cryengine.com/docs/static/attachments/25510452)
 |
Shows the complete history of messages.
 |

![Image](https://www.cryengine.com/docs/static/attachments/25510453)
 |
Shows/hides info messages.
 |

![Image](https://www.cryengine.com/docs/static/attachments/25510454)
 |
Shows/hides warnings.
 |

![Image](https://www.cryengine.com/docs/static/attachments/25510455)
 |
Shows/hides errors.
 |

Clicking on the column headers (
**
Type
**
,
**
Time
**
,
**
Title
**
,
**
Message
**
) will sort the items in the list.

##
Preferences

*
![Image](https://www.cryengine.com/docs/static/attachments/25510421)

*

Option
 |
Description
 |

**
Allow Pop-ups
**
 |
Enable/disable notification pop-ups for warnings, asserts and errors. These will still be stored in both the notification list and history.
 |

**
Combine Notifications
**
 |
Enable/disable warnings, asserts and errors being combined into a single notification when the max number of notifications is displayed in the notification list.
 |

**
Notification Max Count
**
 |
Maximum number of notifications displayed before they are combined into a single notification in the notification list.
 |

##
File Dialog

In update 5.2, some buttons have been added to the file dialog windows:

*
![Image](https://www.cryengine.com/docs/static/attachments/25515885)

*

The highlighted buttons are new. From left to right, they are:

Button
 |
Name
 |
Description
 |

![Image](https://www.cryengine.com/docs/static/attachments/25515887)
 |
**
Directories
**
 |
Shows the standard tree view of directories.
 |

![Image](https://www.cryengine.com/docs/static/attachments/25515889)
 |
**
History
**
 |
List of folders for last selected files. This will store the last 30 entries.
 |

![Image](https://www.cryengine.com/docs/static/attachments/25515891)
 |
**
Favorites
**
 |
List of your favorite folders and files.

Click this button and then you can simply drag&drop folders and files from the right to the Favorites window on the left.

**
Right-click
**
 on them and choose
**
Remove from Favorites
**
 to remove.
 |

[Main Menu Search Window](#main-menu-search-window)
[Notification Center](#notification-center)
[File Dialog](#file-dialog)
