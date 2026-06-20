# _Online Recording in MemReplay

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/29791768
- Page ID: 29791768
- Breadcrumb: Profiling and Debugging > Memory Profiling > _Online Recording in MemReplay
- Parent: Memory Profiling

## Content

##
Overview

This article will explain how to connect the MemReplay Tool to a running process called
**
Online Recording
**
.

Chapters:

[#online-recording-of-memory-information](
Online Recording of Memory Information
)
[#online-recording-on-xbox-one](
Online Recording on Xbox One
)

##
Online Recording of Memory Information

Make sure you are using a Profile build. Debug builds don't always redefine new/malloc.

Please make sure to have setup the MemReplay tool as described in
[/docs/static/engines/cryengine-5/categories/23756813/pages/23306659](
Setup and Loading data with MemReplay Tool
)
 before you continue. In addition to capturing logs to disk, MemReplay also supports capturing the data over the network. This can save a lot of time due to the less copying of logs, and by parallelizing indexing and symbol resolution as the log is captured.

To set this up, first find your ip address by running
**
ipconfig
**
 at a command line. Then start MemReplay, and select
**
File -> Capture Log
**
 from the menu. Select a file to capture.

Finally, start the game with the following command line:

```

`
-memreplay socket:<your ip address>
`

```

All being well, the capture dialog's progress bars should start updating as the log is grabbed.

To stop capturing, run
**
memReplayStop
**
 in the in-game console at any time. If the game crashes, MemReplay will timeout after 5 minutes.

##
Online Recording on Xbox One

Xbox One does not yet support call stack information for Online Recording. However,
[/docs/static/engines/cryengine-5/categories/23756813/pages/23306658](
Getting Started with MemReplay
)
 describes how symbols can be dumped for Xbox One. This .
**
dmp
**
 file can be applied to online recorded .zmrl files.

-
After Online Recording has finished close MemReplay.

-
Create a
**
.dmp
**
 file and make sure it is available locally.

-
Delete the
**
.zmrl.sym
**
 file located in the same folder where your .zmrl file resides.

-
Open MemReplay and load the .zmrl file.

-
MemReplay will ask you to locate the .dmp file.
