# _Setup and Loading data with MemReplay Tool

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/29791766
- Page ID: 29791766
- Breadcrumb: Profiling and Debugging > Memory Profiling > _Setup and Loading data with MemReplay Tool
- Parent: Memory Profiling

## Content

## Overview

This article will explain how to set up the MemReplay tool. Depending on your CRYENGINE license, you may have to add some files to your MemReplay folder.

Chapters:

[Requirements](#requirements)[Xbox One](#xbox-one)[PS4](#ps4)[Loading and Analyzing a ZMRL File](#loading-and-analyzing-a-zmrl-file)

## Requirements

MemReplay 1.9 and earlier versions require Visual Studio 2010 to resolve symbols from.pdb files. This requirement does not exist for MemReplay 1.10 and later versions.

If you are planning to compile CRYENGINE with a different version than Visual Studio 2012, then you will have to replace `bin/<platform>/dbghelp.dll`

`dbghelp.dll` can be found in the installation folder of the current Visual Studio version. For e.g. if Visual Studio 2012 is used the files can be found here:

```
C:\Program Files (x86)\Microsoft Visual Studio 11.0\Common7\IDE\Remote Debugger\x64
```

### Xbox One

In addition to the.zmrl file, MemReplay requires a core dump file on this platform. Please refer to [Getting Started with MemReplay](../../CRYENGINE%20Tools/MemReplay/Getting%20Started%20with%20MemReplay.md).

### PS4

MemReplay will ask you to locate the following file when opening a.zmrl file the first time. It is located here:

```
$SCE_ROOT_DIR/ORBIS SDKs/<version>/host_tools/bin/orbis-bin.exe
```

## Loading and Analyzing a ZMRL File

A.**zmrl** (** z**libbed ** m**em** r**eplay ** l**og) file is a compressed stream which contains information about memory actions in CRYENGINE. Please read [Getting Started with MemReplay](../../CRYENGINE%20Tools/MemReplay/Getting%20Started%20with%20MemReplay.md) to find out how to create a.zmrl file.

Run MemReplay.exe either from Win32 or x64 and open the.zmrl file. You will be asked to help MemReplay locating some files such as.pdb files.

![Image](https://www.cryengine.com/docs/static/attachments/29926171)

![Image](https://www.cryengine.com/docs/static/attachments/29926170)

MemReplay will start indexing and resolving symbols from the data given. It will take some time the first time it is run, but will be quicker on reloads as a lot of information is cached.

![Image](https://www.cryengine.com/docs/static/attachments/29926169)

If MemReplay does not load the.pdb file you have selected, then it is highly likely that the.pdb file does not match the information inside the.zmrl file.

Please make sure you select the.pdb files which have been used while creating the.zmrl file. If they do not come from the same build as the executable that generated the memory log, then symbols will not be resolved correctly.
