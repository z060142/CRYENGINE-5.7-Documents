# Reading & Writing XML

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/29793409
- Page ID: 29793409
- Breadcrumb: Filesystem_ > Reading & Writing XML
- Parent: Filesystem_

## Content

##
Overview

The engine includes an XML parsing and saving library by default in order to easily support cases of storing data in XML.

##
Table of Contents

[#api-types](
API Types
)
[#loading](
Loading
)
[#saving](
Saving
)
[#conclusion](
Conclusion
)

##
API Types

-
[/docs/static/engines/cryengine-5/categories/28704770/pages/29797037](
IXmlNode
)

-
[/docs/static/engines/cryengine-5/categories/28704770/pages/29797434](
IXmlUtils
)

-
[/docs/static/engines/cryengine-5/categories/28704770/pages/29797038](
XmlNodeRef
)

-
[/docs/static/engines/cryengine-5/categories/28704770/pages/29797039](
XmlString
)

##
Loading

To load an XML from buffer, see
[/docs/static/engines/cryengine-5/categories/28704770/pages/29797143](
ISystem::LoadXmlFromBuffer
)
 - this allows for parsing from a string into an
[/docs/static/engines/cryengine-5/categories/28704770/pages/29797038](
XmlNodeRef
)
object that can be programatically parsed.

[/docs/static/engines/cryengine-5/categories/28704770/pages/29797143](
Example
)

##
Saving

Saving an XML node can be done using
[/docs/static/engines/cryengine-5/categories/28704770/pages/29797037](
IXmlNode::saveToFile
)
. We can either use an existing XML node loaded from a buffer or file (see above) - or create a new XML node from scratch using the
[/docs/static/engines/cryengine-5/categories/28704770/pages/29797143](
ISystem::CreateXmlNode
)
 function.

[/docs/static/engines/cryengine-5/categories/28704770/pages/29797143](
Example
)

##
Conclusion

This concludes the article on Reading & Writing XML, you may be interested in:
