# Notification Center

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/44967728
- Page ID: 44967728
- Breadcrumb: Editor Tools > Advanced Tab > Notification Center
- Parent: Advanced Tab

## Content

The notification center is a combination of pop-up messages that are not modal and don't require user input, and is a place where a list of tasks, errors and warnings can be seen. These messages show notifications, warnings and errors and background tasks.

![Image](https://www.cryengine.com/docs/static/attachments/44967735)

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
Tools → Advanced → Notification Center
**
.

![Image](https://www.cryengine.com/docs/static/attachments/44967734)

##
Menu

The Menu can be accessed via the
![Image](https://www.cryengine.com/docs/static/attachments/44967739)
 icon on the top-right corner of the panel. When clicked, it reveals the

**
Help
**
 sub-menu
with the

**
Go to documentation...
**
 option that directs the user to the documentation page for this tool.

##
Current

The Current tab shows a collection of all notifications.

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
![Image](https://www.cryengine.com/docs/static/attachments/44967731)
) button on the top-left

##
History

The Notification History contains a full history of messages. Double-clicking an item will, if possible, take the user to where the error originated from.

Button
 |
Description
 |

![Image](https://www.cryengine.com/docs/static/attachments/44967730)
 |
Clears the list of messages.
 |

![Image](https://www.cryengine.com/docs/static/attachments/25510452)
 |
Shows the complete history of messages.
 |

![Image](https://www.cryengine.com/docs/static/attachments/44967729)
 |
Copies the history to the clipboard.
 |

![Image](https://www.cryengine.com/docs/static/attachments/44967736)

 |
Shows/hides info messages.
 |

![Image](https://www.cryengine.com/docs/static/attachments/44967737)

 |
Shows/hides warnings.
 |

![Image](https://www.cryengine.com/docs/static/attachments/44967738)

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

[Menu](#menu)
[Current](#current)
[History](#history)
[Preferences](#preferences)
