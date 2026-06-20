# CRYENGINE User Interface in Maya

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/13205569
- Page ID: 13205569
- Breadcrumb: CRYENGINE - Getting Started > Installing CRYENGINE > CRYENGINE Plugins and Tools > Installing the Maya Tools > CRYENGINE User Interface in Maya
- Parent: Installing the Maya Tools

## Child Pages

- [Exporting using Crytek Shelf in Maya](CRYENGINE User Interface in Maya/Exporting using Crytek Shelf in Maya.md)

## Content

##
Overview

This article will cover the User Interface for Maya use with CRYENGINE.

[#tools-and-icons](
Tools and Icons
)
[#more-information](
More Information
)

##
Tools and Icons

After the CRYENGINE addon is installed, you can find a shelf icon labelled
**
Crytek
**
. Under the
**
Crytek
**
 tab, you can access the following tools:

[Image: /docs/static/attachments/25506779]

Tools
 |
Description
 |

[Image: /docs/static/attachments/13271314]
 Export Tool (Export)

 |
Lets you open the
**
Crytek Export
**
 window. It allows you to export the objects from the Maya scene to the CRYENGINE sandbox editor.

[Image: /docs/static/attachments/25506782]

 |

[Image: /docs/static/attachments/13271318]
 Material Editor (MAT.ED)

 |
Lets you access the
**
Material Groups
**
 window used for organizing all your materials which will be used in Sandbox.

[Image: /docs/static/attachments/25506783]

 |

[Image: /docs/static/attachments/13271323]
 Cleanup imported FBX scene (FBX)

 |
Cleans up nodes created while importing an FBX scene from Max. It renames all the root nodes to
*
cryexportnode.
*

 |

[Image: /docs/static/attachments/13271322]
 Fix Export node pivot position (PIVOT)

 |
Helps to fix the node's pivot position to quickly get an object's translation data from world space 0,0,0. This enables the origin of the selected node to be moved to its pivot position. You can also enable the
**
Center Pivot
**
 checkbox to center the pivot position.

 |

[Image: /docs/static/attachments/25506780]
 CryMayaTools Toolbox (Tools)

 |
Provides access to the following Crytek tools:

-
Node Tools

-
Animation Tools

-
Plug-in Tools

-
Helpers
*
[Image: /docs/static/attachments/25506784]

*

 |

[Image: /docs/static/attachments/13271320]
 User Defined Properties Editor (UDP)

 |
Lets you specify user-defined properties for an object. You can create, modify or delete the properties in the
**
User Defined Properties
**
 window. To view the user-defined properties specified in an object, select the entire object and click the
**
UDP
**
 icon in the
**
Crytek
**
 tab.

[Image: /docs/static/attachments/25506790]

 |

[Image: /docs/static/attachments/13271313]
 Export Validation (VALID)

 |
Performs validation checks before exporting an object or scene. It will abort the export operation when it encounters any errors or warning in the validation checks. There are two types of messages produced by the validation, critical and ignorable. If there are any critical messages you can't export until they are fixed. Ignorable messages can be ignored but will displayed the every time the validation is run until fixed.

[Image: /docs/static/attachments/25506981]

You can also use the
**
Focus
**
 button for selecting the node or component where the validation has failed.

 |

[Image: /docs/static/attachments/13271325]
 Check export geometry for validity

 |
Checks for degenerate faces in the scene.
 |

[Image: /docs/static/attachments/25506781]
 Configuration interface for CryMayaTools core functionality

 |
Lets you configure the interface options for all the CryMayaTools in the shelf. It also lets you specify the following options:

-
Startup features

-
Debug level

-
Project Configurations

-
Environment info
[Image: /docs/static/attachments/25506982]

 |

##
More Information

-
[/docs/static/engines/cryengine-5/categories/23756816/pages/25531270](
Exporting using Crytek Shelf in Maya
)

-
[/docs/static/engines/cryengine-5/categories/23756816/pages/23308292](
Basic Asset Setup and Export - Maya
)
