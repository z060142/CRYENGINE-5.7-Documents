# Theme, Styling and Colors

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/26873114
- Page ID: 26873114
- Breadcrumb: CRYENGINE Sandbox Programming > Sandbox Framework > Theme, Styling and Colors
- Parent: Sandbox Framework

## Content

### Overview:

#### Icons:

Icons are created white/gray scale and tinted when using our own CryIcon. The required format for all icons is.ico and multiple resolutions should be provided within the same file. All icons are embedded into the executable using qt resource files (**.qrc**). Our main QRC file can be found at ** Code/Sandbox/Plugins/EditorCommon/EditorCommon.qrc**. When using this resource file or creating a new one, please follow the following steps:

- Make sure a top level **prefix** named****"\icons"****is defined for all icons.
- Any icon file in the QRC should have an alias property that should be equivalent to the path but without the initial icon's folder.
- When referencing a file in the QRC, the path should look like this: "**icons:** CategoryFolder/MyIcon.ico" and **not** "** Icons/**CategoryFolder/MyIcon.ico". Both will seem like they work but the first will allow our designers to work on the icons without needing to generate an executable of the editor every time they change an icon.

For more info on the Qt Resource System, please refer **[here](http://doc.qt.io/qt-5/resources.html)**.

#### Styling & Colors:

Styling in the editor is achieved through QSS style sheets. There is a single file that controls the style of the whole editor. It can be found in **Editor/Styles/stylesheet.qss**. The use of ** QPalette** for styling is prohibited since it conflicts with the use of style sheets. Palette colors are defined in QSS and can be accessed through EditorStyleHelper.

For a full list of objects and properties that can be styled, please look at the [Qss Reference](http://doc.qt.io/qt-5/stylesheet-reference.html).

#### Styling FAQ:

Why does the stylesheet not affect my custom widget?If this happens then it means you must override the **paintEvent** on your widget, it should look something like this:

1 2 3 4 5 6 | `void` ` MyCustomWidget::paintEvent(QPaintEvent* pEvent)` `{` ` QStyleOption opt;` ` opt.init(``this``);` ` QPainter p(``this``);` ` style()->drawPrimitive(QStyle::PE_Widget, &opt, &p,``this``);` `}`
--- | ---

I want to style a widget contained by my custom widget, but I don't want to change all other instances. Is that possible?Yes, you would need to reference the widget like this:

`MyCustomWidget TargetWidget` `{` ` color``:``red``;` ` background-color``: yellow;` `}`
---

Actually, I just want to change direct children of my widget. Is that possible?Yes, you can reference direct children by doing the following:

`MyCustomWidget > TargetWidget` `{` ` color``:``red``;` ` background-color``: yellow;` `}`
---

How do I access my Widget if it's defined within another class or inside a namespace?If you have something like the following:

1 2 3 4 5 6 7 8 9 | `class` ` MyWidget:``public` ` QWidget` `{` ` Q_OBJECT` ` public``:` ` class` ` MyOtherWidget:``public` ` QWidget` `{` `...` `};` `...` `};`
--- | ---

You would access my other widget properties in QSS by doing the following:

`MyWidget--MyOtherWidget` `{` ` color``:``red``;` ` background-color``: yellow` `}`
---

How can I expose a custom property of my widget for designers to modify to their liking?Here's how you can do this:

1 2 3 4 5 6 7 8 9 10 | `class` ` MyCustomWidget:``public` ` QWidget` `{` ` Q_PROPERTY(``float` ` awesomeness READ GetAwesomeness WRITE SetAwesomeness DESIGNABLE``true``)` ` public``:` `...` ` float` ` GetAwesomeness() {``return` ` awesomeness; }` ` void` ` SetAwesomeness(``float` ` newValue) { awesomeness = newValue; }` `...` ` private``:` ` float` ` awesomeness;` `}`
--- | ---

And designers can then access that property through QSS by doing this:

`MyCustomWidget` `{` ` qproperty-awesomeness:``0``;` `}`
---

How do I target a widget that has a property set to a certain value?
1 2 3 4 | `QLineEdit[readOnly=``"true"``]` `{` ` color``: yellow;` ` background-color``:``red``;` `}`
--- | ---

Is there a place where I can access common colors or properties in general?Yes, our **EditorStyleHelper**class defines many common properties to be used all across editor and plugins. Feel free to expose properties here if you think they'll be useful to standardize across the editor as well.
