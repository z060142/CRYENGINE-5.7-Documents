# Streaming System

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/23306430
- Page ID: 23306430
- Breadcrumb: CRYENGINE Engine Code > Engine Modules > CrySystem > Streaming System
- Parent: CrySystem

## Content

### Overview

The CRYENGINE streaming engine takes care of the streaming of meshes, textures, audio, animations and more.

### Low-level streaming system

#### CryCommon Interfaces & Structs

The file IStreamEngine.h in CryCommon contains all the important interfaces and structs used by the rest of the engine.

First of all there is the IStreamEngine itself. There is only one IStreamingEngine in the application and it controls all the possible I/O streams. Most of the following information comes directly from the documentation inside the code, so it's always good to read the actual code in IStreamEngine.h file for any missing information.

The most important function in IStreamEngine is the StartRead function and is used to start **any** streaming requests.

```
UNIQUE_IFACE struct IStreamEngine
{
public:

// Description:
//   Starts asynchronous read from the specified file (the file may be on a
//   virtual file system, in pak or zip file or wherever).
//   Reads the file contents into the given buffer, up to the given size.
//   Upon success, calls success callback. If the file is truncated or for other
//   reason can not be read, calls error callback. The callback can be NULL
//   (in this case, the client should poll the returned IReadStream object;
//   the returned object must be locked for that)
// NOTE: the error/success/progress callbacks can also be called from INSIDE
//   this function
// Return Value:
//   IReadStream is reference-counted and will be automatically deleted if
//   you don't refer to it; if you don't store it immediately in an auto-pointer,
//   it may be deleted as soon as on the next line of code,
//   because the read operation may complete immediately inside StartRead()
//   and the object is self-disposed as soon as the callback is called.
virtual IReadStreamPtr StartRead (const EStreamTaskType tSource, const char* szFile, IStreamCallback* pCallback = NULL, StreamReadParams* pParams = NULL) = 0;

};
```

Here are the currently supported streaming task types, and this enum should be extended if a new object type wants to be streamed:

```
enum EStreamTaskType
{
eStreamTaskTypeCount      = 13,
eStreamTaskTypePak        = 12, // Pak file itself
eStreamTaskTypeFlash      = 11, // Flash file object
eStreamTaskTypeVideo      = 10, // Video data (when streamed)
eStreamTaskTypeReadAhead  = 9,  // Read ahead data used for file reading prediction
eStreamTaskTypeShader     = 8,  // Shader combination data
eStreamTaskTypeSound      = 7,
eStreamTaskTypeMusic      = 6,
eStreamTaskTypeFSBCache   = 5,  // Complete FSB file
eStreamTaskTypeAnimation  = 4,  // All the possible animations types (dba, caf, ..)
eStreamTaskTypeTerrain    = 3,  // Partial terrain data
eStreamTaskTypeGeometry   = 2,  // Mesh or mesh lods
eStreamTaskTypeTexture    = 1,  // Texture mip maps (currently mip0 is not streamed)
};
```

A callback object can be provided to the StartStream function to be informed when the streaming request has finished. The callback object should implement the following 2 function:

```
class IStreamCallback
{
public:
// Description:
//   Signals that reading the requested data has completed (with or without error).
//   This callback is always called, whether an error occurs or not, and is called
//   from the async callback thread of the streaming engine, which happens
//   directly after the reading operation
virtual void StreamAsyncOnComplete (IReadStream* pStream, unsigned nError) {}

// Description:
//   Same as the StreamAsyncOnComplete, but this function is called from the main
//   thread and is always called after the StreamAsyncOnComplete function.
virtual void StreamOnComplete (IReadStream* pStream, unsigned nError) = 0;
};
```

Some extra optional parameters can also be provided when starting a read request:

```
struct StreamReadParams
{
public:

// The user data that'll be used to call the callback.
DWORD_PTR dwUserData;

// The priority of this read
EStreamTaskPriority ePriority;

// Description:
//   The buffer into which to read the file or the file piece
//   if this is NULL, the streaming engine will supply the buffer.
// Notes:
//   DO NOT USE THIS BUFFER during read operation! DO NOT READ from it, it can lead to memory corruption!
void* pBuffer;

// Description:
//   Offset in the file to read; if this is not 0, then the file read
//   occurs beginning with the specified offset in bytes.
//   The callback interface receives the size of already read data as nSize
//   and generally behaves as if the piece of file would be a file of its own.
unsigned nOffset;

// Description:
//   Number of bytes to read; if this is 0, then the whole file is read,
//   if nSize == 0 && nOffset != 0, then the file from the offset to the end is read.
//   If nSize != 0, then the file piece from nOffset is read, at most nSize bytes
//   (if less, an error is reported). So, from nOffset byte to nOffset + nSize - 1 byte in the file.
unsigned nSize;

// Description:
//   The combination of one or several flags from the stream engine general purpose flags.
// See also:
//   IStreamEngine::EFlags
unsigned nFlags;
};
```

The return value of the StartRead function is a IReadStream object which can be optionally stored on the client. The IReadStream object is refcounted internally. When the callback object can be destroyed before the reading operation is finished then the readstream should be stored somewhere, and abort needs to be called on it. This will take care of cleaning up the complete read request internally, and will also call the async and sync callback functions.

The Wait function can be used to perform a blocking reading requests on the streaming engine. This function can be used from an async reading thread, which wants to use the cryengine streaming system to perform the actual reading.

```
class IReadStream : public CMultiThreadRefCount
{
public:
virtual void Abort() = 0;
virtual void Wait( int nMaxWaitMillis=-1 ) = 0;
};
```

#### Internal flow of a read request

The CryENGINE StreamEngine uses extra worker and IO-Threads internally. For every possible IO input a different StreamingIOThread is created which can run independent from each other.

Currently it has the following IO threads:

- Optical: Streaming from the optical data drive.
- HDD: Streaming from installed data on the HDD (could be fully installed game or shadow copied data).
- Memory: Streaming from the in memory packed files, which doesn't require any real IO at all.

When a reading request is made on the streaming engine, it first of all checks which IO thread to use, and computes the sortkey. The request is then inserted into one of the IOThreads.

After the reading operation is finished the request is forwarded to one of the decompression threads (if the data was compressed), and then into one of the async callback threads. The amount of async callback threads is dependent on the platform, and some async callback threads are reserved for specific streaming requests types such as geometry and textures. After the async callback has been processed, the finished streaming request is added on to the streaming engine to be processed on the main thread. The next update on the streaming engine from the main thread will then call the sync callback (StreamOnComplete) and clean up the temporary allocated memory if needed.

For information regarding the IO/WorkerThreads please check the StreamingIOThread and StreamingWorkerThread class.

#### Read Request Sorting

Requests to the streaming engine are **not** processed in a the same order as which they have been requested. The system tries to internally 'optimize' the order in which to read the data, to maximize the read bandwidth.

When reading data from an optical disc, it is very important to reduce the amount of seeks (and also from an HDD but to a lesser extent). A single seek can take over a 100msec, while the actual read time would be only a few msecs. Some official statistics from the 360 XDK:

- Outer diameter throughput: 12× (approximately 15 MB per second).
- Inner diameter throughput: 5× (6.8 MB per second).
- Average seek (1/3rd stroke) time: 110 ms typical, 140 ms maximum.
- Full stroke seek time: 180 ms typical, 240 ms maximum.
- Layer switch time: 75 ms.

The internal sorting algorithm takes the following rules into account in this order:

- **priority** of the request - High priority requests always take precedence but can be very expensive if there are to many (a lot of extra seeks could be introduced).
- **time grouping** - Requests made within a certain time are grouped together to create a continuous reading operation on the disc for every time group. The default value is 2 secs, but can be changed using the following cvar: * sys_streaming_requests_grouping_time_period*. Time grouping has a huge impact on the average completion time of the requests. It increases the time of a few otherwise quick reading requests, but drastically reduces the overall completion time, because most of the streaming request are coming from 'random' places on the disc.
- actual **offset on disc** - The actual disc offset is computed and used during the sorting. Files which have a higher offset get a higher priority, so it is important to organize the layout of the disc to reflect the desired streaming order.

For Crysis 2 the following order was used: sounds/music, animations, meshes, low mip textures, high mip textures.

For information regarding the sorting, please refer to the source code in StreamAsyncFileRequest::ComputeSortKey(). Here is the essential sorting code:

```
void CAsyncIOFileRequest::ComputeSortKey(uint64 nCurrentKeyInProgress)
{
.. compute the disc offset (can be requested using CryPak)

// group items by priority, then by snapped request time, then sort by disk offset
m_nDiskOffset += m_nRequestedOffset;
m_nTimeGroup = (uint64)(gEnv->pTimer->GetCurrTime() / max(1, g_cvars.sys_streaming_requests_grouping_time_period));
uint64 nPrioriry = m_ePriority;

int64 nDiskOffsetKB = m_nDiskOffset >> 10; // KB
m_nSortKey = (nDiskOffsetKB) | (((uint64)m_nTimeGroup) << 30) | (nPrioriry << 60);
}
```

#### Streaming Statistics

The streaming engine can be polled for streaming statistics using the GetStreamingStatistics() function.

Most of the statistics are divided in 2 groups, one collected during the last second and another one from the last (which usually happens during level loading), but can also be force reset in game.

The Media Type info gives information per IO input system (HDD, Optical, Memory).

```
struct SMediaTypeInfo
{
// stats collected during the last second
float fActiveDuringLastSecond;
float fAverageActiveTime;
uint32 nBytesRead;
uint32 nRequestCount;
uint64 nSeekOffsetLastSecond;
uint32 nCurrentReadBandwidth;
uint32 nActualReadBandwidth;    // only taking actual reading time into account

// stats collected since last reset
uint64 nTotalBytesRead;
uint32 nTotalRequestCount;
uint64 nAverageSeekOffset;
uint32 nSessionReadBandwidth;
uint32 nAverageActualReadBandwidth; // only taking actual read time into account
};
```

The Request Type info gives information about each streaming request type (geometry, textures, animations,...)

```
struct SRequestTypeInfo
{
int nOpenRequestCount;
int nPendingReadBytes;

// stats collected during the last second
uint32 nCurrentReadBandwidth;

// stats collected since last reset
uint32 nTotalStreamingRequestCount;
uint64 nTotalReadBytes;     // compressed data
uint64 nTotalRequestDataSize;   // uncompressed data
uint32 nTotalRequestCount;
uint32 nSessionReadBandwidth;

float fAverageCompletionTime;   // Average time it takes to fully complete a request
float fAverageRequestCount; // Average amount of requests made per second
};
```

The global statistics containing all the merged data:

```
struct SStatistics
{
SMediaTypeInfo hddInfo;
SMediaTypeInfo memoryInfo;
SMediaTypeInfo opticalInfo;

SRequestTypeInfo typeInfo[eStreamTaskTypeCount];

uint32 nTotalSessionReadBandwidth;  // Average read bandwidth in total from reset - taking full time into account from reset
uint32 nTotalCurrentReadBandwidth;  // Total bytes/sec over all types and systems.

int nPendingReadBytes;      // How many bytes still need to be read
float fAverageCompletionTime;   // Time in seconds on average takes to complete read request.
float fAverageRequestCount; // Average requests per second being done to streaming engine
int nOpenRequestCount;      // Amount of open requests

uint64 nTotalBytesRead;     // Read bytes total from reset.
uint32 nTotalRequestCount;  // Number of request from reset to the streaming engine.

uint32 nDecompressBandwidth;    // Bytes/second for last second

int nMaxTempMemory;     // Maximum temporary memory used by the streaming system
};
```

#### Streaming Debug Info

Different types of debug info can be requested using the following CVar: **sys_streaming_debug x.**

### Streaming and levelcache pak files

As mentioned earlier it is very important to minimize the seeks and seek distances when reading from an optical media drive, therefore the build system is slightly modified to optimize the internal data layout for streaming.

The easiest and fastest win is to not do any IO at all, but read the data from compressed data in memory. For this, small paks for startup and per level are created. These are loaded during level loading into memory and some stay there until the end of the level. Others are only used to speed up the level loading. All small files and small read requests should ideally be diverted to these paks.

A special RC_Job build file is used to generate these paks: Bin32/rc/RCJob_PerLevelCache.xml. These paks are generated during a normal build pipeline. The internal managment in the engine is done by the CResourceManager class, which uses the global SystemEvents to preload or unload the paks.

Currently the following pak's are loaded into memory during level loading (**sys_PakLoadCache**):

- **level.pak** - Contains all actual level data, and should not be touched after level loading anymore.
- **xml.pak**
- **dds0.pak** - Contains all lowest mips of all the textures in the level.
- **cgf.pak** & ** cga.pak** - Only loading when CGF streaming is enabled.

These paks are cached into memory during the level load process (**sys_PakStreamCache**):

- **dds_cache.pak** - Contains all dds files smaller than 6 KB (except for dds.0 files).
- **cgf_cache.pak** - Contains all cgf files smaller than 32 KB (only when CGF streaming is enabled).

Without these paks level loading can take up to a few minutes and streaming performance is reduced a lot, so be sure that they are available!

The information regarding all the resources of a level are stored in the **resourcelist.txt** and ** auto_resourcelist.txt**. These files are generated by an automatic testing system which loads each level and executes a prerecorded playthrough on it. These resourcelist files are used during the build phase to generate the level paks.

All the data which is not in these in memory paks is performing actual IO on the optical drive or HDD, and it is also best to reduce the amount of seeks here. This optimization phase is also performed during the build process using the RC.

All the data which can be streamed is extracted from all the resourcelists from all the levels, and is removed from the default pak files (Objects.pak, Textures.pak, Animations.pak,...) and put into new optimized paks for streaming inside a streaming folder.

The creating of the streaming paks uses the following rules:

- Split by **extension**: Different extension files are put into different paks (dds, caf, dba, cgf,...) to put files of the same type close to each other, so they can be read in bursts. These paks are also used to increase the priority of certain files types during the request sorting by using the actual disc offset.
- Split by DDS **type**: Different dds types are sorted different, to increase the priority of different types (diffuse maps get higher priority than normal maps for example). The actual distance in the pak is used during the sorting of the request.
- Split by DDS **mip**: The highest mips are put into a separate pak file. They usually take more than 60% of the size of all the smaller mips and can then be streamed with a lower priority, and the average seek time to read the smaller textures is reduced a lot. The texture streaming system internally optimizes the reads to reflect these split texture data.
- Sort **Alphabetically**: Default alphabetical sorting is needed because some of the data (such as CGF's during MP level loading), are loading in alphabetical order, and changing this can have a severe impact on the loading times!

The actual sorting code is hardcoded in the RC, and can be found at: `Code\Tools\RC\ResourceCompiler\PakHelpers.cpp`.

It is very important that any changes to the sorting operator in the RC are reflected in the sorting operators of the texture streaming and streaming engine internally as well!

### Single Thread IO Access and Invalid File Access

It is very important that only a single thread accesses the IO devices at the same time. If multiple threads are reading from the same IO device concurrently, then the reading speed is more than halved, possibly taking seconds to read just a few KB's!

The reason is that the IO reading head will partially read a few KB's for one thread, and then reads another few KB's for another thread, while always performing the expensive seeks in between.

The solution is to exclusively read from StreamingIOThreads during gameplay. CryENGINE will by default show an **'Invalid File Access'** warning in the top left corner when reading data from the wrong thread and stall for 3 seconds to emulate the actual stall when reading from an optical drive.

For more information on how to track and fix 'Invalid File Accesses' in the game check the following confluence page: [http://confluence/display/RND/Tracking+File+Access](/docs)

### High Level Streaming Engine usage

It is very easy to extend the current streaming functionality using the StreamEngine. A small example class is explained below on how to add a new streaming type.

Create a class which derives from the IStreamCallback (used to inform of streaming completion) and add some basic functionality to read a file. The file can either be read directly or using the streaming engine. When the data is read directly, it calls the ProcessData function to actually parse the loaded data. The function is also called from the async callback. Some processing can be performed here on the data if needed, because it's not running on the main thread.

The default parameters are used when starting a reading request on the streaming engine. It is also possible to provide the final data storage itself. This helps to reduce the amount of dynamic allocations performed by the streaming engine.

The class also stores the read stream object, to get information about the streaming request, or to be able to cancel it when the callback object is destroyed. The pointer is reset in the sync callback because after this call it won't be referenced anymore by the streaming engine.

```
#include
class CNewStreamingType : public IStreamCallback
{
public:
CNewStreamingType() : m_pReadStream(0), m_bIsLoaded(false) {}
~CNewStreamingType()
{
if (m_pReadStream)
m_pReadStream->Abort();
}

// Start reading some data
bool ReadFile(const char* acFilename, bool bUseStreamingEngine)
{
if (bUseStreamingEngine)
{
StreamReadParams params;
params.dwUserData = eLoadFullData;
params.ePriority = estpNormal;
params.nSize = 0; // read the full file
params.pBuffer = NULL; // don't provide any buffer, but copy data when streaming is done

m_pReadStream = g_pISystem->GetStreamEngine()->StartRead(eStreamTaskTypeNewType, acFilename, this, ¶ms);
}
else
{
// old way of reading file in a sync way (blocking call!)
const char* acData = 0;
size_t stSize = 0;

.. read file directly using CryPak or fopen/fread

ProcessData(acData, stSize);
m_bIsLoaded = true;
}

return m_bIsLoaded;
}

// Check if the data is ready and loaded
bool IsLoaded() const { return m_bIsLoaded; }

protected:

// implement the IStreamCallback function
void StreamAsyncOnComplete(IReadStream* pStream, unsigned nError)
{
if(nError)
{
return;
}

const char* acData = (char*)pStream->GetBuffer();
size_t stSize= pStream->GetBytesRead();

ProcessData(acData, stSize);
m_bIsLoaded = true;
}

void StreamOnComplete (IReadStream* pStream, unsigned nError)
{
m_pReadStream = 0;
}

// process the actual loaded data
void ProcessData(const char* acData, size_t stSize);

// store the stream callback object to be sure it can be canceled when the object is destroyed
IReadStreamPtr m_pReadStream;
// Extra flag used to check if the data is ready
bool m_bIsLoaded;
}
```
