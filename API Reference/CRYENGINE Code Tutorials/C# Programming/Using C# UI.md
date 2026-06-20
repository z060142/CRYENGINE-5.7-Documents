# Using C# UI

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/26874996
- Page ID: 26874996
- Breadcrumb: CRYENGINE Code Tutorials > C# Programming > Using C# UI
- Parent: C# Programming

## Child Pages

- [01. Creating a Basic UI](Using C# UI/01. Creating a Basic UI.md)
- [02. Creating a Menu](Using C# UI/02. Creating a Menu.md)
- [03. Creating a Popup](Using C# UI/03. Creating a Popup.md)

## Content

The C# UI makes it possible to quickly create a simple UI without using external tools such as Scaleform. Currently the C# UI is able to:

-
Show text and images.

-
Receive user-input.

-
Render directly to the screen, or render to a texture.

-
Organise the UI with layout groups.

##
Introduction

The UI in C# runs basically on two classes. The first class is the
`
UIElement
`
-class, which inherits from
`
SceneObject
`
 and adds support for a
`
RectTransform
`
. The
`
RectTransform
`
 defines information about the location, orientation and size of each
`
UIElement
`
. The second class is the
`
UIComponent
`
-class, which defines the behavior of the
`
UIElement
`
. Each
`
UIElement
`
 can have multiple
`
UIComponents
`
.

[Image: /docs/static/attachments/26954502]

Every UI starts with a
`
Canvas
`
. The
`
Canvas
`
 is responsible for drawing the UI to the screen or to a render texture and delegating events to its child
`
UIElements
`
. Every
`
UIElement
`
 has to be a child of a
`
Canvas
`
. A scene can have multiple
`
Canvas
`
 instances at the same time.

-
[/docs/static/engines/cryengine-5/categories/23756813/pages/26874999](
01. Creating a Basic UI
)

-
[/docs/static/engines/cryengine-5/categories/23756813/pages/26875001](
02. Creating a Menu
)

-
[/docs/static/engines/cryengine-5/categories/23756813/pages/26875003](
03. Creating a Popup
)
