# Reading & Writing XML

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/29793409
- Page ID: 29793409
- Breadcrumb: Filesystem_ > Reading & Writing XML
- Parent: Filesystem_

## Content

## Overview

The engine includes an XML parsing and saving library by default in order to easily support cases of storing data in XML.

## Table of Contents

[API Types](#api-types)[Loading](#loading)[Saving](#saving)[Conclusion](#conclusion)

## API Types

- [IXmlNode](/docs/static/engines/cryengine-5/categories/28704770/pages/29797037)
- [IXmlUtils](/docs/static/engines/cryengine-5/categories/28704770/pages/29797434)
- [XmlNodeRef](/docs/static/engines/cryengine-5/categories/28704770/pages/29797038)
- [XmlString](/docs/static/engines/cryengine-5/categories/28704770/pages/29797039)

## Loading

To load an XML from buffer, see [ISystem::LoadXmlFromBuffer](/docs/static/engines/cryengine-5/categories/28704770/pages/29797143) - this allows for parsing from a string into an [XmlNodeRef](/docs/static/engines/cryengine-5/categories/28704770/pages/29797038)object that can be programatically parsed.

[Example](/docs/static/engines/cryengine-5/categories/28704770/pages/29797143)

## Saving

Saving an XML node can be done using [IXmlNode::saveToFile](/docs/static/engines/cryengine-5/categories/28704770/pages/29797037). We can either use an existing XML node loaded from a buffer or file (see above) - or create a new XML node from scratch using the [ISystem::CreateXmlNode](/docs/static/engines/cryengine-5/categories/28704770/pages/29797143) function.

[Example](/docs/static/engines/cryengine-5/categories/28704770/pages/29797143)

## Conclusion

This concludes the article on Reading & Writing XML, you may be interested in:
