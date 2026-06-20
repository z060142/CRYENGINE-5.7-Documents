# Sandbox Python Plugins

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/26873118
- Page ID: 26873118
- Breadcrumb: CRYENGINE Sandbox Programming > Sandbox Framework > Sandbox Plugins > Sandbox Python Plugins
- Parent: Sandbox Plugins

## Content

##
Creating a Basic Python Plugin

To create a basic python plugin, create a folder in
**
`
<Editor Folder>/Editor/Python/plugins
`
**
 and create a file called "startup.py" there. On Sandbox startup, those files are executed automatically. (though there is no proper editor interface for Python plugins yet).

To create a Sandbox view pane, you can use template code:

**
Sample startup.py
**

```

`
from PySide2 import QtWidgets
import SandboxBridge

class TestWindow(QtWidgets.QWidget):
    def __init__(self):
        super(TestWindow, self).__init__()
        self.setLayout(QtWidgets.QVBoxLayout())
        self.layout().addWidget(QtWidgets.QPushButton("HELLO SANDBOX, I COME FROM THE WORLD OF PYTHON"))

SandboxBridge.register_window(TestWindow, "Test Window", category="Test", needs_menu_item=True, menu_path="Test", unique=False)
`

```

##
Creating Sandbox View Panes

It is also possible to create Sandbox view panes containing Python created panels through the "SandboxPythonBridge" Sandbox plugin. It exposes the function "register_window" directly to Python:

```

`
def register_window(window_type, name, category="", needs_menu_item=True, menu_path="", unique=True):
    """
    Register a new window type with the Sandbox.
    This should only be called once per window type, when your python plugin is initialized.
    :param class window_type: The class of your window. This must be a subclass of QWidget.
    :param str name: The name of your window.
    :param str category: The category of your window.
    :param bool needs_menu_item: If true, the window will be displayed in the "tools" submenu of the sandbox filemenu.
    :param str menu_path: The path (within the tools menu) to display your tool's menu item. Nested menus can be decalred with forward slahes.
    :param bool unique: If true, only one instance of your menu can be displayed at a time. Otherwise, multiple may be opened simultaneously.
    """
    ...
`

```
