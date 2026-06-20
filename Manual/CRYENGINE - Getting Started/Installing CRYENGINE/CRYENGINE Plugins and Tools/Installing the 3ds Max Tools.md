# Installing the 3ds Max Tools

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/44963469
- Page ID: 44963469
- Breadcrumb: CRYENGINE - Getting Started > Installing CRYENGINE > CRYENGINE Plugins and Tools > Installing the 3ds Max Tools
- Parent: CRYENGINE Plugins and Tools

## Child Pages

- [CryMaxTools - Phys Proxy Tool](Installing the 3ds Max Tools/CryMaxTools - Phys Proxy Tool.md)
- [CRYENGINE Exporter in 3dsMax](Installing the 3ds Max Tools/CRYENGINE Exporter in 3dsMax.md)

## Content

##
Overview

The Tools package includes the CryExporter plugins for 3ds Max as well as
**
[/docs/static/engines/cryengine-5/categories/23756816/pages/23308297](
CryMaxTools
)
**
.

The CryExporter enables you directly export engine ready assets from within 3ds Max.

##
Installation via CryToolsInstaller

We recommend using the
[/docs/static/engines/cryengine-5/categories/23756816/pages/44963458](
CryToolsInstaller
)
 to install all DCC tool packages, including 3dsMax. If you need to manually install them, follow the instructions in the sections below.

Before the installation of any plugins via CryToolsInstaller make sure to have setup your build information via the
**
Settings Manager
**
 tool.

##
Manual Installation CryExporter

Plugin files can be found in the
`
<root>\Tools\3dsmax
`
\
`
plugins\
`
 folder. Copy the relevant plugin files (see list below) to the
`
...\plugins
`
 directory in the matching 3dsMax install folder (do not put it into the
`
Stdplugs
`
 Folder).

Version

 |
File

 |

**
3dsMax 2010
**

 |
32 Bit

 |
CryExport12.dlu

 |

64 Bit

 |
CryExport12_64.dlu

 |

**
3dsMax 2011
**

 |
32 Bit

 |
CryExport13.dlu

 |

64 Bit

 |
CryExport13_64.dlu

 |

**
3dsMax 2012
**

 |
32 Bit

 |
CryExport14.dlu

 |

64 Bit

 |
CryExport14_64.dlu

 |

**
3dsMax 2013
**

 |
32 Bit

 |
CryExport15.dlu

 |

64 Bit

 |
CryExport15_64.dlu

 |

**
3dsMax 2014
**

 |
64 Bit

 |
CryExport16_64.dlu

 |

**
3dsMax 2015
**

 |
64 Bit

 |
CryExport17_64.dlu

 |

**
3dsMax 2016
**
 |
64 Bit
 |
CryExport18_64.dlu
 |

**
3dsMax 2017
**

 |
64 Bit

 |
CryExport19_64.dlu

 |

**
3dsMax 2018
**

 |
64 Bit

 |
CryExport20_64.dlu

 |

**
3dsMax 2019
**
 |
64 Bit
 |
CryExport21_64.dlu
 |

**
3dsMax 2020
**
 |
64 Bit
 |
CryExport22_64.dlu
 |

**
3dsMax 2021
**
 |
64 Bit
 |
CryExport23_64.dlu
 |

**
3dsMax 2022
**
 |
64 Bit
 |
CryExport24_64.dlu
 |

**
3dsMax 2023
**
 |
64 Bit
 |
CryExport25_64.dlu
 |

##
Manual Installation CryMaxTools

The CryMaxTools Maxscripts is a collection of tools coded in MAXScript for helping artists, modeling and animation staff to speed up their workflow.

The tools are separated into Animation, Artist, Morph and Rigging packages with user interface, menu entries and shortcuts.

CryMaxTools MAXScripts are available for the most recent versions of 3dsMax and will automatically choose the right version to load.

[Image: /docs/static/attachments/44963472]

The script files can be found in the
`
\Tools\CryMaxTools
`
 folder. The tools can be installed by copying the tools loader (LoadCryMaxTools.ms) into
`
\Scripts\Startup
`
 of the 3dsMax root directory. After restarting 3dsMax the tools should load automatically.

[Image: /docs/static/attachments/44963470]

To uninstall the tools, delete the "LoadCryMaxTools.ms" file located in the
`
\Scripts\Startup
`
 folder of the 3ds Max directory.
