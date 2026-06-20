# Personalization

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/26873106
- Page ID: 26873106
- Breadcrumb: CRYENGINE Sandbox Programming > Sandbox Framework > Personalization
- Parent: Sandbox Framework

## Content

##
In a nutshell

-
**
Personalization
**
is the application adapting its behavior to its user, without the user actively requesting customization.

-
**
Customization
**
is when the user changes a customization setting that was exposed to him.
In practice, this means we should aim for the tools to adapt to the user's behavior if we can, rather than expose all of these as explicit customization settings to the user.

This is a much better user experience and doesn't add to the tool's complexity, it just happens as the user uses the tool, it is implicit, and therefore much better.

**
If possible, always use personalization over customization.
**

Concrete examples:

-
We can remember if an "advanced" category was opened or closed and always display it as its last state.

-
We remember the expanded state of every category in the inspector and restore them.

-
We always store and restore the last used layout by the user, even if they didn't explicitly save it.

-
We remember the user's favorited assets and recently used assets and display them again.

##
How to use

See
**
 PersonalizationManager.h
**
for full API.

Personalization is stored as a QVariantMap, and based on unique keys.

There are two possible storage locations:

-
**
Global:
**
will be stored in AppData and shared for all versions of Cryengine and all projects

-
See Set/GetProperty

-
**
Per Project:
**
will be stored as a temporary file in the project directory (user folder). Examples are favorites and recent files which are inherently project-specific.

-
See Set/GetProjectProperty
You can also access personalization with helper methods from
**
CEditor, CAssetEditor,
**
or
**
 CEditorDialog.
**
