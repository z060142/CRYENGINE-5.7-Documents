# Creating a new editor window

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/26873098
- Page ID: 26873098
- Breadcrumb: CRYENGINE Sandbox Programming > Sandbox Framework > Creating a new editor window
- Parent: Sandbox Framework

## Content

##
CEditor base class

The
**
CEditor
**
class is the base class for all the editor windows such as every tool from the Tools menu, every asset editor, and most dockable windows in the Sandbox.

You can find the
**
CEditor
**
interface in the following file:
**
Sandbox/Plugins/EditorCommon/EditorFramework/Editor.h
**

CEditor provides numerous services and features intended to be used by every tool in the Sandbox. Here is a non-exhaustive list of features it supports:

-
Saving and Loading Layouts.

-
Easier access to
[/docs/static/engines/cryengine-5/categories/23756813/pages/26873106](
Personalization
)
.

-
Menu building system.

-
Handling of all general commands (New, Open, Save, Undo/Redo, Copy/Paste...).

-
Customized menus through a plugin.

-
Docking system nested within the CEditor.

-
Preventing window from closing in the case of unsaved changes.

CEditor and its derivates are the main means of providing a framework to build new tools within Sandbox. While you can choose to operate outside of this framework, we recommend to use it in order to ensure consistency of all the tools, but also because you will benefit from any additions, bugfixes, and improvements we make to this system simply by inheriting from it.

##
Creating a new window

In order to create a new tool window, you must inherit from CEditor, and use its numerous services and advanced features to create your tool. There are however more specialized versions of CEditor for specific purposes that are recommended to use.

-
**
CEditor:
**
 Most basic version, does not support docking.

-
**
CDockableEditor:
**
 Extension of CEditor that supports docking, this is a good base class for any tool except for an Asset Editor (see below). A tool that doesn't edit any assets or files can be made from CDockableEditor but most new systems should probably be CAssetEditor and integrate with the Asset System.

-
**
CAssetEditor:
**
Adds extra functionality relevant to editing asset types.
In this case please follow the documentation on the
[/docs/static/engines/cryengine-5/categories/23756816/pages/26874315](
Asset System 5.5.2
)
.

One most basic example of a CDockableEditor can be found in
**
PlaygroundDockable.h/cpp
**

Here is a code sample to demonstrate how to declare and register a new editor window:

```

`
class CExampleEditor : public CDockableEditor
{
public:
  CExampleEditor()
  {
    auto exampleContent = new QWidget();
    /*build the content of your editor*/
    SetContent(exampleContent);
  }
  ~CExampleEditor() {}
  virtual const char* GetEditorName() const override { return "Example"; };
};

//Register the Example Editor
//REGISTER_VIEWPANE_FACTORY(CExampleEditor, "Example", "", false);
`

```
