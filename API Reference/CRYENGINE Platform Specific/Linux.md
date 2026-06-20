# Linux

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/23306675
- Page ID: 23306675
- Breadcrumb: CRYENGINE Platform Specific > Linux
- Parent: CRYENGINE Platform Specific

## Content

##
Overview

CRYENGINE is supported on the
[http://www.ubuntu.com/download/desktop](
Ubuntu 16 64bit
)
 Linux distribution. Other Linux distributions will likely work as well, however they are not actively tested and supported by development team.

Chapters:

[#compilation-prerequisites](
Compilation prerequisites
)
[#compiling](
Compiling
)
[#running-prerequisites](
Running prerequisites
)
[#stack-traces-and-core-dumps](
Stack Traces & Core Dumps
)
[#known-issues](
Known issues
)

##
Compilation prerequisites

CRYENGINE compilation on Linux requires that you have some externally provided packages installed on your system.
The following table explains how to make sure you have every package required for compilation installed.

Package
 |
How to install (Ubuntu)
 |
Notes
 |

Build Essential
 |
sudo apt-get install build-essential
 |
This package provides the C libraries and gcc compiler
 |

Clang (optional)
 |
sudo apt-get install clang-3.8
 |
Install if you wish to use the clang compiler instead of gcc
 |

Python + TK
 |
sudo apt-get install python python-tk
 |
Python and Tk are used by the WAF build system to configure and setup the build
 |

*
SDL2
*
 |
sudo apt-get install libsdl2-dev
 |
Install only for CRYENGINE 3.8.5 and older, for 3.8.6 it is automatically included
 |

*
NCurses
*
 |
sudo apt-get install libncurses5-dev libncursesw5-dev
 |
Install only for CRYENGINE 3.8.5 and older, for 3.8.6 it is automatically included
 |

##
Compiling

The CRYENGINE runtime and game code can be compiled for 64-bit Linux using the WAF build system.

In order to compile you can enter the following command in a Linux terminal in the root directory:

**
./cry_waf.sh build_
**
linux_
**
x64_<compiler>_<configuration> --project-spec=<spec>
**

with the following replacements

<compiler>
 |
Compiler of choice. Can be either
**
gcc
**
 or
**
clang.
**
 |

<configuration>
 |
Build configuration. Possible values are
**
release
**
,
**
performance
**
,
**
profile
**
 and
**
debug
**
.
 |

<spec>
 |
Name of the chosen project spec (for example
**
gamesdk
**
,
**
gamesdk_and_tools
**
,
**
gamezero
**
...).
 |

For example, to build the
CRYENGINE
with the GameSDK project in Profile configuration with GCC, type:

**
./cry_waf.sh build_linux_x64_gcc_profile --project-spec=gamesdk
**

This command will produce the binaries for the project in the BinLinux64<compiler> sub-folder (in this case BinLinux64gcc).

Visit
[/docs/static/engines/cryengine-5/categories/23756813](
WAF Build System
)
 for more informations about WAF and more advanced options.

##
Running prerequisites

CRYENGINE does not support the open source graphics drivers usually enabled by default in Linux distributions as they are often not fully OpenGL compliant.

Please make sure you install the latest proprietary drivers for your graphics card.

For Ubuntu you can follow these guides to get the correct vendor drivers installed:

-
NVIDIA graphics cards:
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](
https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia
)

-
AMD graphics cards:
[https://help.ubuntu.com/community/BinaryDriverHowto/AMD?action=show&redirect=BinaryDriverHowto%2FATI](
https://help.ubuntu.com/community/BinaryDriverHowto/AMD
)
CRYENGINE on Linux also uses the SDL2 library runtime.

The command to install  it on Ubuntu is:

```

`
sudo apt-get install libsdl2-2.0-0
`

```

##
Stack Traces & Core Dumps

Stack traces will be written to a file name
**
backtrace.log
**
in the current working directory of the executable.

To enable core dumps, please run the Launcher with the generated shell script Launch_GameSDK.sh in the bin/linux_x64_<compiler>/ folder.

##
Known issues

These are the current known limitations specific to the Linux version of CRYENGINE:

-
Hardware tessellation is not supported.

-
CRYENGINE requires at least an OpenGL 4.3 compliant system.

-
Some older graphics drivers are not supported. For this reason it is recommended to update your graphics driver before running CRYENGINE.
