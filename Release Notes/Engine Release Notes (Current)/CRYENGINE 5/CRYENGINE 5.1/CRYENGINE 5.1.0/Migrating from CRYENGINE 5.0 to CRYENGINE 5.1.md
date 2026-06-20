# Migrating from CRYENGINE 5.0 to CRYENGINE 5.1

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/47316993/pages/44962617
- Page ID: 44962617
- Breadcrumb: Engine Release Notes (Current) > CRYENGINE 5 > CRYENGINE 5.1 > CRYENGINE 5.1.0 > Migrating from CRYENGINE 5.0 to CRYENGINE 5.1
- Parent: CRYENGINE 5.1.0

## Content

##
Overview

If you migrated your project to CRYENGINE 5.0 you will have noticed a lot of new features at your disposal such as DX12, C# and a brand new Sandbox UI.

This article is aimed at easing migration of projects from CRYENGINE 5.0 to CRYENGINE 5.1. It will focus on changes made to the CRYENGINE's source code format.

CRYENGINE 5.0:

Although CRYENGINE 5.0 development focused on new features, it also refined some existing features to ease client interaction with CRYENGINE. Examples of which are the data driven thread manager; unifying all existing thread managers and changes to the way windows.h is included as well as a cleanup of outdated defines. For a full list of changes please see:
[/docs/static/engines/cryengine-5/categories/47316993/pages/44962603](
Important data and code changes (CRYENGINE 5.0)
)

CRYENGINE 5.1:

CRYENGINE 5.1
development focused on
 stability and standardizing engine source code formatting.

##
Highlights :

-
Automatic code style rules; introduced in
CRYENGINE 5.0,
 have been finalized.

-
 See
[/docs/static/engines/cryengine-5/categories/47316993/pages/44962623](
Upgrading to CRYENGINE 5.1 - Code Formatting
)
 if you have made changes to CRYENGINE source code, to ease integration.

-
CryCommon files have physically moved on disk. They are now sorted by category

##
Automatically converting your project to the new CryCommon layout:

Rather than hand editing every single file. WAF provides a quick solution to convert your project files to the new layout.

1. As a first step start the WAF GUI and select "Custom folder and subfolders" in the "Apply new CryCommon layout" category.

2. Now switch to the WAF's output  window. You are requested to enter a folder name that you want to be converted. Note that in addition to your folder all subfolders will also be converted.

3. If you use P4, you can enter your workspace name here and the tool will automatically checkout all changed files into the default changelist. If you don't have or want to use P4, just leave the line empty

4. WAF will now start the conversion process.

 |
[Image: /docs/static/attachments/44962621]
 |

**
Note:
**
If you used file names similar to the ones in CryCommon in your project, the converter might falsely identify such a file and replace it with a path to the CryCommon file. The converted first tries to find a file in the local folder though.

##
CryCommon layout changes (detail)

With CryEngine 5.1, CryCommon has received a visual lift. Rather than a flat file hierarchy, all file have been remapped into categorized folders, making it easier to get a quick overview of features provided by the CryCommon interface.

Current

(flat hierarchy)

[On Disk]

 |

 |
Re-organised

(sorted by module)

[On Disk]

 |
Re-organised

(sorted by module)

[Visual Studio]

 |

[Image: /docs/static/attachments/44962620]
 |
**
=>
**

 |
[Image: /docs/static/attachments/44962619]

 |

[Image: /docs/static/attachments/44962618]
 |

Categorizing CryCommon files does come at a slight cost though as all current files that are #including a CryCommon file have to obey the new layout.

```

`
#include <ICryAnimation.h>
// to
#include <CryAnimation/ICryAnimation.h>

#include <IShader.h>
// to
#include <CryRenderer/IShader.h>
`

```
