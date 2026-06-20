# Tracking File Access

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/23306408
- Page ID: 23306408
- Breadcrumb: CRYENGINE Engine Code > Engine Modules > CrySystem > File System > Tracking File Access
- Parent: File System

## Content

##
Overview

It's possible to track invalid file reads happening in the game during run-time. The error message
*
'Invalid File Access'
*
 means reading or trying to open files from a thread which is not the streaming thread. These file access operations can cause quite severe stalls.

Currently the file access tracking only logs access from the main and render thread.

This feature is disabled in RELEASE builds.

##
CVars

The following cvars will trigger different option to track the file access.

**
sys_PakLogInvalidFileAccess:
**

1 (default):

-
Access is logged to game.log.

-
Generates a perfHUD warning.

-
Written on screen in red in upper left corner of the screen.

-
Stall for 3 secs in non-release builds.
2:

-
File access, along with callstack is logged and saved to a file on the console in the sub-directory FileAccess (currently for Xbox 360 only).

-
Also all the functionality of 1.
**
sys_PakMessageInvalidFileAccess:
**

-
Creates a popup dialog (for PC and Xbox 360, debugbreak on PS3) when a file is accessed, you can choose to break into the debugger or continue.

##
Where is invalid access defined

The points which define when file access is invalid are set using ICryPak::DisableRuntimeFileAccess with true or false. These points may need to be tweaked for single player and multiplayer.

##
Exceptions

It is possible to add some exceptions to the file access tracking, so you ignore certain files (e.g game.log).

Simply create an instance of CDebugAllowFileAccess in the scope which accesses the file.

##
Resolving file access callstacks

The files collected using
**
pak_LogInvalidFileAccess 2
**
 will need their callstacks resolving, to this we need the
**
.pdb
**
/s from the build, the
**
XenonStackParse
**
 tool, and the helper script
**
ProcessFileAccess.py
**

The tools can found in the
*
 XenonStackParse
*
 folder of the Tools directory.
*

*

The directory structure for running ProcessFileAccess.py should be as follows:

*
<Root>

--> XenonStackParse
*

*
--> FileAccessLogs (this dir should contain the .pdbs)
*

*
------> Processed (outut from XenonStackParse)
*

Run
**
ProcessFileAccess.py
**
 from the
*
FileAccessLogs
*
 dir (XenonStackParse uses the working directory to search for the .pdb files). This will create a direction called processed, which will have a file containing the resolved callstack for each of the logged files.
