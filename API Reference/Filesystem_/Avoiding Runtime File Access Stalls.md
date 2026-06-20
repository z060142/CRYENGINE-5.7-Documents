# Avoiding Runtime File Access Stalls

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/29428290
- Page ID: 29428290
- Breadcrumb: Filesystem_ > Avoiding Runtime File Access Stalls
- Parent: Filesystem_

## Content

## Overview

It is possible to track invalid file reads (occurring in the game) during run-time. The error message *'Invalid File Access'* means reading or trying to open files from a thread which is not the streaming thread. These file access operations can cause severe stalls.

Currently, the file access tracking only logs access from the main and render thread.

## Table of Contents

[CVars](#cvars)[Where is Invalid Access Defined?](#where-is-invalid-access-defined)[Exceptions](#exceptions)[Resolving File Access Callstacks](#resolving-file-access-callstacks)

## CVars

The following CVars will trigger a different option to track the file access.

**sys_PakLogInvalidFileAccess 1**(Default Setting)

- Access is logged to game.log
- Generates a perfHUD warning
- Written on screen in red in the upper-left corner of the screen
- Stall for 3 secs in non-release builds

**sys_PakLogInvalidFileAccess 2**

- File access along with callstack is logged and saved to a file on the console in the sub-directory FileAccess (currently for Xbox 360 only)
- Also all the functionality of 1 above

**sys_PakMessageInvalidFileAccess:**

- Creates a popup dialog (for PC and Xbox 360, debugbreak on PS3) when a file is accessed. You can choose to break into the debugger or continue

### Where is Invalid Access Defined?

The points which define when file access is invalid are set using ICryPak::DisableRuntimeFileAccess with true or false. These points may need to be tweaked for single player and multiplayer.

#### Exceptions

It is possible to add some exceptions to the file access tracking - so you can ignore certain files (e.g. game.log).

Simply create an instance of CDebugAllowFileAccess in the scope which accesses the file.

#### Resolving File Access Callstacks

The files collected using **pak_LogInvalidFileAccess 2** will need their callstacks resolving, to this we need the **.pdb** files from the build, the **XenonStackParse** tool and the helper script ** ProcessFileAccess.py.**

The tools can found in the*XenonStackParse* folder of the Tools directory.

The directory structure for running ProcessFileAccess.py should be as follows.

*<Root> --> XenonStackParse* *--> FileAccessLogs (this dir should contain the.pdb files)* *------> Processed (output from XenonStackParse)*

Run **ProcessFileAccess.py** from the * FileAccessLogs* dir (XenonStackParse uses the working directory to search for the.pdb files). This will create a directory called processed, which will have a file containing the resolved callstack for each of the logged files.
