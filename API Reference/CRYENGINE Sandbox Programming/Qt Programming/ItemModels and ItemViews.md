# ItemModels and ItemViews

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/26873086
- Page ID: 26873086
- Breadcrumb: CRYENGINE Sandbox Programming > Qt Programming > ItemModels and ItemViews
- Parent: Qt Programming

## Content

-
[Introduction](/docs)

-
[How to write your model](/docs)

-
[Combining models](/docs)

-
[Advanced Usage in CRYENGINE Sandbox](/docs)

-
[Advanced ItemModels](/docs)

-
[Advanced ItemViews and UI components](/docs)

-
[Attributes](/docs)

##
Introduction

Item models are the single most useful and powerful feature of Qt. You will use a lot of them as you make trees, lists, and search boxes. Learn how they work, learn how to use them, this is one of the fundamentals of good Qt programming.

Qt documentation and tutorial:

-
[https://doc.qt.io/qt-5/model-view-programming.html](https://doc.qt.io/qt-5/model-view-programming.html)

-
[https://doc.qt.io/qt-5/modelview.html](https://doc.qt.io/qt-5/modelview.html)
ItemModels follow a variant of MVC called
[Model-View-ViewModel](https://en.wikipedia.org/wiki/Model%E2%80%93view%E2%80%93viewmodel)
 where the ViewModel (the QItemModel) sits in the middle and negotiates all communication with the model (your system).

The below image describes a realistic diagram of a typical usage of QItemModel:

![Image](https://www.cryengine.com/docs/static/attachments/26952237)

**
Important things to note:
**

-
Neither the ItemModel nor the view replicates the state of the System, i.e.
**
there are no fields in the ItemModel
**
, only a pointer to the system.

-
The view may bypass the ItemModel to act as a controller itself and modify the System directly.

-
It is possible to write the view without even including a dependency to System, by calling all modifications on the model (setData).

##
How to write your model

There are two options to choose from when writing your model:
inheriting from QAbstractItemModel
 or using
QStandardItemModel
.
The good choice is almost always inheritance.

-
QStandardItemModel has a very verbose and hardly readable syntax.

-
QStandardItemModel has its own state and therefore breaks the MVC pattern.

-
QStandardItemModel is always less efficient in memory and performance.

On the other hand QAbstractItemModel:

-
Will store no state except a pointer to your System.

-
Gives access to all the features for models that will change in their lifetime.

-
Enables a lot of tricks that we will talk about later in this document.

**
Conclusion: Always inherit from QAbstractItemModel (or QAbstractListModel for lists)
**

The only time where QStandardItemModel is reasonable for a fully static model that does not have a corresponding system already, i.e. for pure UI things that never change. Even then, it is a debatable choice due to the clumsiness of using QStandardItemModel.

##
Combining models

Models and views can be combined in very creative ways to achieve the desired results. Note that this means we can display the data of the System in very different ways without having to change System at all.

![Image](https://www.cryengine.com/docs/static/attachments/26952238)

In this diagram, the QListView sees a "flat" list of the model whereas the QTreeView sees a filtered hierarchy of the model.

For each instance of System, we only need one corresponding ItemModel. From then on Proxies can be attached to the original model which will modify the data (restructure, filter, translate, etc…), and at the end of each chain, a different kind of view can be attached.

This is used for example in the AssetBrowser where the Thumbnails View and the Details View are attached to the same chain of models, providing different views.

##
Advanced Usage in CRYENGINE Sandbox

##
Advanced ItemModels

-
**
DeepFilterProxyModel
**

-
Probably the most useful enables various powerful search modes most notably the often needed “deep search”.

-
**
MergingProxyModel
**

-
Concatenates several models into one.

![Image](https://www.cryengine.com/docs/static/attachments/26952239)

-
**
MountingProxyModel
**

-
Allows combining different models into one hierarchy.

-
Each model will be “mounted” as a child of an element of the main model.

Example: LevelExplorer: Layer models that contain the objects inside the layer are mounted under the row representing the layer in the model that contains all the layer hierarchies.

![Image](https://www.cryengine.com/docs/static/attachments/26952240)

##
Advanced ItemViews and UI components

-
**
QAdvancedTreeView
**
 (recommended to use over QTreeView)

-
Use over QTreeView, provides a lot of advanced features.

-
Will restore selection and expanded state better than QTreeView.

-
Provides layout saving/restoring features.

-
Is adapted to work with attributes.

-
**
QThumbnailsView
**

-
Specialized list view to display thumbnails. Please use those wherever you need to display thumbnails/browse images for consistency.

-
**
QSearchBox
**

-
Basic search box. Use this, do not reinvent the wheel.

-
**
QFilteringPanel
**

-
Advanced search box and query system, use with attributes.

##
Attributes

Please refer to
**
ItemModelAttribute.h
**
 for the code, and check existing usages.

Attributes are additional metadata that can be exposed by a mo
del to enable advanced functionality. This is a system that is not part of Qt and you must use CRYENGINE views to make the best use of it/

In practice you must implement the following:

-
Create static instances of attributes describing your model's columns or use one of the many generic attributes in ItemModelAttribute.h.

-
getHeaderData with s_getAttributeRole to return the pointer to the attribute of this column.

-
getHeaderData with other attribute roles for more advanced features.
Then use one of our widgets that interact with the attributes system:

-
QFilteringPanel: advanced search/filtering based on attributes (see LevelExplorer and AssetBrowser).

-
QAdvancedTreeView: menu to hide and show columns.

-
QtThumbnailsView: needs attributes to display properly.
