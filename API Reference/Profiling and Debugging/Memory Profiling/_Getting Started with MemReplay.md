# _Getting Started with MemReplay

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/29791764
- Page ID: 29791764
- Breadcrumb: Profiling and Debugging > Memory Profiling > _Getting Started with MemReplay
- Parent: Memory Profiling

## Content

## Overview

This article will explain how to collect memory information from a running CRYENGINE game.

Chapters:

[Offline Recording of Memory Information](#offline-recording-of-memory-information)[Offline Recording on Xbox One](#offline-recording-on-xbox-one)

## Offline Recording of Memory Information

Make sure you are using a Profile build. Debug builds don't always redefine new/malloc.

Run the game with **-memreplay** in your arguments list.

MemReplay is now tracking every allocation/free call and streams it into a **memlog-date-time.zmrl** file. See table below for file location (depending on platform type):

Platform | Folder
--- | ---
**PC** | `<root>\bin\<build folder>`, e.g. ` win_x64`
**Xbox One** | Game root on console
**PS4** | Data folder on console

MemReplay can be stopped manually by calling the console command **memReplayStop**. This will flush the remaining information to the disc.

Do not use the console command **memReplayResume**as a replacement for argument **-memreplay** or after **memReplayStop** has been called.

### Offline Recording on Xbox One

The Xbox One platform requires some extra steps to get a valid call stack:

- Call **memReplayStop** via console.
- Go to the debugger and save a [core dump](http://msdn.microsoft.com/en-us/library/d5zhxt22.aspx) (without heap) - ***.dmp** file.
- Make sure you have the dump file and the.zmrl file available locally.
- Open MemReplay and load the.zmrl file.
- MemReplay asks you to locate the dump file.
