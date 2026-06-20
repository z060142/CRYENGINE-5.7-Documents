# MemReplay in Code

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/23306663
- Page ID: 23306663
- Breadcrumb: CRYENGINE Tools > MemReplay > MemReplay in Code
- Parent: MemReplay

## Content

##
Overview

This article describes how MemReplay is hooked into the CRYENGINE code and how it is used from there.

Chapters:

[Tracking Allocations](#tracking-allocations)
[Contexts](#contexts)
[#defines](#defines)
[Locations](#locations)

##
Tracking Allocations

In methods that make an allocation, such as CryMalloc,
**
MemReplay
**
 is told that it is entering an allocation method and then also told when it is leaving the method - along with the pointer and size that the allocation created. This allows MemReplay to track high level allocations such as those from a pool, as well as low-level physical allocations such as those through the CRTMalloc.

##
Contexts

Each
**
MEMSTAT_CONTEXT
**
 (or
**
MEMSTAT_CONTEXT_FMT
**
) creates a local stack object that effectively creates a new child node in the (root) context tree as seen in MemReplay. When the context is destroyed (because the function has been left), the context node is closed. The (root) context tree can be seen as a high-level annotated picture of the code paths that the game has taken.

Whenever an allocation occurs it is added to the top of the current context for that thread.

When a free occurs the allocation is removed from allocation's context. The current context is not affected.

**
Reallocs
**
 are just seen as a separate
**
free
**
 and
**
alloc
**

Contexts can have a type (from the EMemStatContextTypes::Type enum) - feel free to add more, but only at the end of the enum. MemReplay relies on the order to correctly label them.

Contexts can also have an
**
"instance" flag
**
 set (EMemStatContextFlags::MSF_Instance). When a context is entered that has this flag, a counter on that node is incremented. This allows MemReplay to calculate an average size for what conceptually should be separate instances.

##
#defines

-
**
CAPTURE_REPLAY_LOG
**
 - Set to 1 if MemReplay hooks, contexts and logging support should be compiled in (set to 0 otherwise). Any code that should be compiled out if MemReplay isn't going to be available (such as for release builds) should have a #if CAPTURE_REPLAY_LOG around it

-
**
REPLAY_RECORD_FREECS
**
 - If set to 1, then callstacks are captured when a free occurs - this allows MemReplay to show where frees occured, instead of just removing it from the allocation site in the treemap

-
**
REPLAY_RECORD_USAGE_CHANGES
**
 - If set to 1, then changes to the size (not the capacity of) of containers such as DynArray and PodArray and they will be tracked. This allows MemReplay to calculate the approximate efficiency of how those containers are being used

-
**
REPLAY_RECORD_THREADED
**
 - If set to 1, then all compression and disk writing is accomplished on a separate thread. Note there's really no reason to turn this off

##
Locations

The Engine code is distributed over:

-
CryCommon/
**
CryMemReplay.h
**
 - defines the IMemReplay interface and context types/flags

-
CrySystem/
**
MemReplay.h
**
 - defines the internal MemReplay types, and has a handful of #defines for controlling its internal behavior

-
CrySystem/
**
MemReplay.cpp
**
 - the actual implementation of MemReplay's tracking

-
CryCommon/
**
ProjectDefines.h
**
 - a bunch of macro logic to set/unset CAPTURE_REPLAY_LOG
