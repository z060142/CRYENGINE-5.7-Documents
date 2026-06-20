# Qt Programming in Sandbox

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/26873088
- Page ID: 26873088
- Breadcrumb: CRYENGINE Sandbox Programming > Qt Programming > Qt Programming in Sandbox
- Parent: Qt Programming

## Content

##
Guidelines

Using Qt in Sandbox comes with a few guidelines and restrictions

-
Do not include Qt in places that don't need it, separate code using our
[/docs/static/engines/cryengine-5/categories/23756813/pages/26873090](
UI Programming Patterns
)
.

-
Lambdas, bind and functional approach is a godsend to UI programming, use it!.

-
**
Use Qt5 c++11 syntax for connect
**
:

-
Bad: connect ( sender, SIGNAL(valueChanged(QString,QString)), receiver, SLOT(updateValue(QString)) ).

-
Good: connect ( sender, &Sender::valueChanged, receiver, &Receiver::updateValue).

-
Good: connect ( sender, &Sender::valueChanged, [](){ /*lambda*/ } ).

-
**
Do not use UI files
**
 (Qt Creator)

-
The generated code is often more complex than if you had written it by yourself. Writing Qt layouts is not hard, quite the contrary.

-
It obfuscates for debugging. Now you have to look in several places including generated code to understand how the final result is produced.

-
By using UI files you are effectively avoiding learning how to program Qt Widgets. It's better for everyone involved if you learn and get comfortable with it.

-
All UI Strings must be available for localization (using QObject::tr method or QT_TR_NOOP macro).

-
Use
**
CrySignal
**
 to implement observable structures that should not depend on Qt.

-
Always make sure that you are not duplicating functionality that otherwise exists in the framework.

-
Expose
**
generic functionality in EditorCommon
**
 and try to
**
reuse
**
 as much as is possible. A lot of reusable components are already there, please add more if necessary.

-
**
Use our replacement classes for some Qt classes
**
(see below).

-
**
Use ItemModels effectively:
**

[/docs/static/engines/cryengine-5/categories/23756813/pages/26873086](
ItemModels and ItemViews
)
.

-
**
Only QWidgets
**
 and QGraphicsViews are allowed. QtQuick or other parts of Qt are not available.

##
Reusable classes

The Sandbox code contains a large library of reusable components, such as Qt Widgets, various helpers, and platform abstraction tools. All of these extensions can be found in the
**
EditorCommon
**
project, in particular, EditorCommon/Controls and EditorCommon/Dialogs.

The goal is to provide a more powerful framework and a unified way to solve UI problems across the whole tool. By using these you will get a better UI, a faster result, and help the Sandbox look and feel consistent. Feel free to call and extend this framework as much as possible.

##
Must Use

You should always use the following classes instead of the original ones. Failure to do this should be caught during code review. Only by using the right set of classes everywhere can we ensure consistency throughout the Sandbox.

Qt Class
 |
Replacement
 |
Reason
 |

QDialog
 |
CEditorDialog
 |
Styling and personalization can only be achieved like this. Will also handle more things such as platform-specific placement of buttons etc.
 |

QComboBox
 |
QMenuComboBox
 |
QComboBox has several bugs and many issues with styling. We opted for a full replacement with a similar API. Please do not use QComboBox.
 |

QIcon
 |
CryIcon
 |
Unified styling, icon color tinting etc. See
[/docs/static/engines/cryengine-5/categories/23756813/pages/26873114](
Theme, Styling, and Colors
)

Once constructed a CryIcon may safely be stored in a QIcon variable, so this is fine: QIcon foo = CryIcon("bar");

 |

QPixmap
 |
CryIcon.pixmap()
 |
If you are using a pixmap that should behave like an icon, prefer using CryIcon.pixmap() to get the benefits of styling and tinting.
 |

QMessageBox
 |
CQuestionDialog
 |
Styling and unification. Our CQuestionDialog dialogs look amazing, just use them!
 |

QPalette
 |
QSS Stylesheet
 |
QPalette is deprecated as we use style sheets. See
[/docs/static/engines/cryengine-5/categories/23756813/pages/26873114](
Theme, Styling, and Colors
)
 |

QLineEdit
 |
QNumericBox
 |
For numeric fields only: Implements many advanced behaviors and interactions.
 |

##
Recommended use

It is recommended to use the following classes instead of the original ones.

Qt Class
 |
Replacement
 |
Reason
 |

QTreeView
 |
QAdvancedTreeView
 |
Provides extra generic functionality. Handles Layout concerns.
 |

QStyledItemDelegate
 |
QAdvancedItemDelegate
 |
Provides extra generic functionality, such as drag-checking, or displaying a different icon than a checkbox.
 |

QMimeData
 |
CDragDropData
 |
Provides extra generic functionality. Drag-tooltip, and a much easier interface to drag complex types within the application.
 |

##
Other reusable UI components

All the reusable widgets and Qt helpers are available in the
**
EditorCommon
**
package. Take a look at the source code to discover more useful classes!

Another set of extensions to Qt is the
[/docs/static/engines/cryengine-5/categories/23756813/pages/26873086](
ItemModel Framework which is described in a dedicated page
)
.

Component
 |
Description
 |

QControls.h
 |
Contains a lot of fairly simple reusable widgets and UI components.
 |

QMenuLabelSeparator
 |
Menu separator with a label.
 |

QLoading
 |
Rotating icon to symbolize loading/processing.
 |

QEditableComboBox
 |
ComboBox with editable content through a LineEdit.
 |

QSearchBox
 |
Unified search box, do not use QLineEdit for this.
 |

CDynamicPopupMenu / CMenuBuilder
 |
Abstracted menu system used to build complex dynamic menus without depending on Qt.
 |

QCollapsibleFrame
 |
UI component to group widgets has a title, can be collapsed.
 |

QFullScreenWidget
 |
Enables any widget to react to full screen (F11) command and go fullscreen.
 |

QTrackingTooltip
 |
Very useful to denote contextual information in particular for drag-operations. This should be used liberally as it makes the UX much more predictable and drag-features are some of the hardest ones to discover.
 |

QPopupWidget
 |
Creates a resizable popup window that can embed any widget. Useful for popup tools, such as the notification center and other tray area widgets.
 |

[#guidelines](
Guidelines
)
[#reusable-classes](
Reusable classes
)
[#must-use](
Must Use
)
[#recommended-use](
Recommended use
)
[#other-reusable-ui-components](
Other reusable UI components
)
