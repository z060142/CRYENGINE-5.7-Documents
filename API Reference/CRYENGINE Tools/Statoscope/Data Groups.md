# Data Groups

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/23306654
- Page ID: 23306654
- Breadcrumb: CRYENGINE Tools > Statoscope > Data Groups
- Parent: Statoscope

## Content

##
Overview

This page holds a list of the available data groups used in Statoscope and the treeview path where the respective information can be accessed.

Group identifiers are case sensitive!
Chapters:

[#reference](
Reference
)
[#d-device-buffer-pool](
D: Device Buffer Pool
)
[#l-overload-scene-manager-osm](
L: Overload Scene Manager (OSM)
)
[#o-frame-performance-overview](
O: Frame Performance Overview
)
[#p-texture-stream-pools](
P: Texture Stream Pools
)
[#s-texture-streaming-items](
S: Texture Streaming Items
)
[#w-individual-worker-information](
W: Individual Worker Information
)
[#x-summarized-worker-information](
X: Summarized Worker Information
)
[#y-individual-job-information](
Y: Individual Job Information
)
[#z-summarized-job-information](
Z: Summarized Job Information
)
[#a-audio-streaming](
a: Audio Streaming
)
[#b-device-buffer-pool-manager](
b: Device Buffer Pool Manager
)
[#c-per-cgf-gpu-profiling](
c: Per-CGF GPU Profiling
)
[#d-network-profiling](
d: Network Profiling
)
[#e-effect-processing](
e: Effect Processing
)
[#f-frame-timing](
f: Frame Timing
)
[#g-graphics](
g: Graphics
)
[#i-gpu-timing](
i: GPU Timing
)
[#j-cpu-timing](
j: CPU Timing
)
[#l-camera-location](
l: Camera Location
)
[#m-memory-usage](
m: Memory Usage
)
[#n-network-traffic](
n: Network Traffic
)
[#o-object-streaming](
o: Object Streaming
)
[#p-particles](
p: Particles
)
[#r-frame-profilers](
r: Frame Profilers
)
[#s-streaming](
s: Streaming
)
[#t-threading](
t: Threading
)
[#u-user-defined-markers](
u: User-defined Markers
)
[#v-vertex-counts](
v: Vertex Counts
)
[#w-physical-entity-profiling](
w: Physical Entity Profiling
)
[#x-texture-streaming](
x: Texture Streaming
)
[#z-network-channel](
z: Network Channel
)

##
Reference

##
D: Device Buffer Pool

Path

 |
Description

 |

/DevBuffers/$/poolAllocatedSize

 |
Amount of space allocated for the device buffer pool

 |

/DevBuffers/$/poolFrag

 |
Amount of fragmentation in the device buffer pool

 |

/DevBuffers/$/poolFreeBlocks

 |
Amount of free blocks in the device buffer pool

 |

/DevBuffers/$/poolFreeMB

 |
Amount of free space in the device buffer pool, measured in MB

 |

/DevBuffers/$/poolMovingBlocks

 |
Amount of blocks being moved during defragmentation of the device buffer pool

 |

/DevBuffers/$/poolNumAllocs

 |
Number of allocations present in the device buffer pool

 |

/DevBuffers/$/poolNumBanks

 |
Number of memory banks allocated for the device buffer pool

 |

/DevBuffers/$/poolUsageMB

 |
Amount of memory used by the device buffer pool, measured in MB

 |

##
L: Overload Scene Manager (OSM)

Path

 |
Description

 |

/Overload/currentStats/frameRate

 |
Frame rate calculated from real time needed for a single frame

 |

/Overload/currentStats/gpuFrameRate

 |
Frame rate calculated from GPU time needed for a single frame

 |

/Overload/enabled

 |
Whether the OSM is enabled

 |

/Overload/fbScale

 |
Output scale for the OSM

 |

/Overload/smoothedStats/frameRate

 |
Frame rate calculated from real time needed for rendering, smoothed over 1 second

 |

/Overload/smoothedStats/gpuFrameRate

 |
Frame rate calculated from GPU time needed for rendering, smoothed over 1 second

 |

/Overload/targetFrameRate

 |
Target frame rate

 |

##
O: Frame Performance Overview

Path

 |
Description

 |

/Overview/FrameScaleFactor

 |
Scale factor used by the Viewport. Controlled by the Overload Scene Manager if enabled

 |

/Overview/GPULoadInMS

 |
Number of milliseconds needed by the GPU for this frame

 |

/Overview/MTLoadInMS

 |
Number of milliseconds needed by the main thread for this frame

 |

/Overview/NetTLoadInMS

 |
Number of milliseconds needed by the networking thread for this frame

 |

/Overview/RTLoadInMS

 |
Number of milliseconds needed by the rendering thread for this frame

 |

/Overview/frameLengthInMS

 |
Total number of milliseconds needed for this frame

 |

/Overview/lostProfilerTimeInMS

 |
Number of milliseconds spent for profiling during this frame

 |

/Overview/numDrawCalls

 |
Number of draw calls in this frame

 |

/Overview/profilerAdjFrameLengthInMS

 |
Number of milliseconds needed for this frame, excluding profiling time

 |

##
P: Texture Stream Pools

Path

 |
Description

 |

/TexPools/$/n

 |
Shows texture pool activity. Divided into Total, InUse and Free each of which is subcategorized by texture type and size

 |

##
S: Texture Streaming Items

Path

 |
Description

 |

/TexStrm/$/requiredMB

 |
Shows the amount of memory used for each texture stream, measured in MB

 |

##
W: Individual Worker Information

This contains information for each worker, split into blocking and non-blocking tasks.

Path

 |
Description

 |

/WorkerInformation/Individual/$/$/ExecutionTimeInMS

 |
Number of milliseconds the specified worker spent executing tasks

 |

/WorkerInformation/Individual/$/$/IdleTimeInMS

 |
Number of milliseconds the specified worker was idle during tasks

 |

/WorkerInformation/Individual/$/$/NumJobs

 |
Number of jobs executed by the worker

 |

/WorkerInformation/Individual/$/$/SamplePeriodInMS

 |
Duration of the sample period, measured in milliseconds

 |

/WorkerInformation/Individual/$/$/UtilPerc

 |
Percentage of the sample period spent executing tasks for this worker

 |

##
X: Summarized Worker Information

This contains summarized information on all workers, split into blocking and non-blocking tasks.

Path

 |
Description

 |

/WorkerInformation/Summary/$/ActiveWorkers

 |
Number of active workers

 |

/WorkerInformation/Summary/$/AvgUtilPerc

 |
Average percentage of the sample period spent executing tasks on workers

 |

/WorkerInformation/Summary/$/SamplePeriodInMS

 |
Duration of the sample period, measured in milliseconds

 |

/WorkerInformation/Summary/$/TotalExecutionPeriodeInMS

 |
Combined time spent executing jobs on workers

 |

/WorkerInformation/Summary/$/TotalNumberOfJobsExecuted

 |
Number of jobs executed by all workers

 |

##
Y: Individual Job Information

This contains information for each job, split into blocking and non-blocking tasks.

Path

 |
Description

 |

/JobInformation/Individual/$/$/ExecutionTimeInMS

 |
Number of milliseconds spent executing this job

 |

/JobInformation/Individual/$/$/NumberOfExecutions

 |
Number of times this job was executed

 |

##
Z: Summarized Job Information

This contains information for all jobs, split into blocking and non-blocking tasks.

Path

 |
Description

 |

/JobInformation/Summary/$/TotalExecutionTimeInMS

 |
Total number of milliseconds spent executing jobs

 |

/JobInformation/Summary/$/TotalNumberOfIndividualJobsExecuted

 |
Total number of distinct jobs executed

 |

/JobInformation/Summary/$/TotalNumberOfJobsExecuted

 |
Total number of jobs executed

 |

##
a: Audio Streaming

Path

 |
Description

 |

/StreamingAudio/bandwidthActualKBsecond

 |
Bandwidth used for streaming audio, measured in KB/s

 |

/StreamingAudio/bandwidthRequestedKBsecond

 |
Bandwidth requested for streaming audio, measured in KB/s

 |

##
b: Device Buffer Pool Manager

Path

 |
Description

 |

/DevBuffer/cb

 |
Amount of KB used in the constant buffer. Only available if CONSTANT_BUFFER_ENABLE_DIRECT_ACCESS is defined as a non-false preprocessor token

 |

/DevBuffer/cpu_flush

 |
Amount of time spent flushing the CPU

 |

/DevBuffer/creation_time

 |
Amount of time spent performing other tasks

 |

/DevBuffer/gpu_flush

 |
Amount of time spent flushing the GPU

 |

/DevBuffer/io_time

 |
Amount of time spent performing I/O

 |

/DevBuffer/read_kb

 |
Amount of KB read from pools

 |

/DevBuffer/written_kb

 |
Amount of KB written to pools

 |

##
c: Per-CGF GPU Profiling

Statistics on draw calls, organized by CGF and type of rendering. Also covers Scaleform rendering.

Path

 |
Description

 |

/DrawCalls/$/numInstances

 |
Number of instances for this CGF

 |

/DrawCalls/$/totalDrawCallCount

 |
Number of draw calls used for the CGF

 |

##
d: Network Profiling

Shows network profiling statistics, divided according to traffic source.

Path

 |
Description

 |

/NetworkProfile/$/calls

 |
Number of calls made for network traffic

 |

/NetworkProfile/$/rmiBits

 |
Number of bits sent for remote method invocation (RMI)

 |

/NetworkProfile/$/seqBits

 |
Number of non-RMI bits sent

 |

/NetworkProfile/$/totalBits

 |
Total number of bits sent

 |

##
e: Effect Processing

Path

 |
Description

 |

/Effects/sumTimeEffects

 |
Total amount of milliseconds spent processing effects

 |

/Effects/timeAfterHDRPostProcess

 |
Number of milliseconds spent after applying HDR post-processing

 |

/Effects/timeAfterPostProcess

 |
Number of milliseconds spent after applying post-processing

 |

/Effects/timeDecal

 |
Number of milliseconds spent applying decal effects

 |

/Effects/timeDeferredPreProcess

 |
Number of milliseconds spent pre-processing before deferred passes

 |

/Effects/timeEyeOverlay

 |
Number of milliseconds spent on eye overlay effects

 |

/Effects/timeGeneral

 |
Number of milliseconds spent on opaque ambient light and shadow passes

 |

/Effects/timeHDRPostProcess

 |
Number of milliseconds spent applying HDR post-processing

 |

/Effects/timeHalfResParticles

 |
Number of milliseconds spent applying half-resolution particles

 |

/Effects/timeInvalid

 |
Number of milliseconds spent on other effects

 |

/Effects/timeLensOptic

 |
Number of milliseconds spent processing lens optics

 |

/Effects/timeParticlesThickness

 |
Number of milliseconds spent on particle thickness passes

 |

/Effects/timePostProcess

 |
Number of milliseconds spent applying post-processing

 |

/Effects/timePreProcess

 |
Number of milliseconds spent applying pre-processing

 |

/Effects/timeShadowGen

 |
Number of milliseconds spent generating shadow maps

 |

/Effects/timeShadowPass

 |
Number of milliseconds spent generating shadow masks

 |

/Effects/timeSkin

 |
Number of milliseconds spent pre-processing skin rendering

 |

/Effects/timeTerrainLayer

 |
Number of milliseconds spent processing terrain layers

 |

/Effects/timeTransparent

 |
Number of milliseconds spent processing transparency

 |

/Effects/timeWater

 |
Number of milliseconds spent processing water surfaces

 |

/Effects/timeWaterVolumes

 |
Number of milliseconds spent processing water volumes

 |

##
f: Frame Timing

Path

 |
Description

 |

/frameLengthInMS

 |
Number of milliseconds spent rendering the frame

 |

/lostProfilerTimeInMS

 |
Number of milliseconds lost to profiling for the frame, or -1 if profiling is disabled

 |

##
g: Graphics

Path

 |
Description

 |

/Graphics/GPUFrameLengthInMS

 |
Number of milliseconds spent by the GPU for this frame

 |

/Graphics/GPUUsageInPercent

 |
Percentage of the frame length where the GPU was busy

 |

/Graphics/numDrawCalls

 |
Number of regular draw calls for this frame

 |

/Graphics/numForwardLights

 |
Number of forward lights in this frame

 |

/Graphics/numForwardShadowCastingLights

 |
Number of forward lights casting shadows in this frame

 |

/Graphics/numGeneralDrawCalls

 |
Number of draw calls for general effects for this frame

 |

/Graphics/numPostEffects

 |
Number of active post-processing effects in this frame

 |

/Graphics/numShadowDrawCalls

 |
Number of shadow draw calls for this frame

 |

/Graphics/numTotalDrawCalls

 |
Number of total draw calls for this frame

 |

/Graphics/numTransparentDrawCalls

 |
Number of draw calls for transparency effects for this frame

 |

/Graphics/numTris

 |
Number of triangles for this frame

 |

##
i: GPU Timing

Path

 |
Description

 |

/GPUTimes/Frame

 |
GPU time spent on the overall frame

 |

/GPUTimes/Lighting

 |
GPU time spent on lighting

 |

/GPUTimes/Scene

 |
GPU time spent on the overall scene rendering

 |

/GPUTimes/Shadows

 |
GPU time spent on shadows

 |

/GPUTimes/VFX

 |
GPU time spent on visual effects

 |

##
j: CPU Timing

Path

 |
Description

 |

/CPUTimes/aiTime

 |
CPU time spent on AI processing, measured in milliseconds

 |

/CPUTimes/animNumCharacters

 |
Number of character instances processed

 |

/CPUTimes/animTime

 |
CPU time spent processing animations, measured in milliseconds

 |

/CPUTimes/flashTime

 |
CPU time spent processing Flash, measured in milliseconds

 |

/CPUTimes/particleSyncTime

 |
CPU time lost to profiling during particle processing, measured in milliseconds

 |

/CPUTimes/particleTime

 |
CPU time spent on particle processing, measured in milliseconds

 |

/CPUTimes/physTime

 |
Real time spent for this frame, measured in milliseconds

 |

##
l: Camera Location

This data is not directly shown as a graph in Statoscope, instead it is displayed as part of the tooltip for graphs.

Path

 |
Description

 |

/posx

 |
X-position of the camera

 |

/posy

 |
Y-position of the camera

 |

/posz

 |
Z-position of the camera

 |

/rotx

 |
X-rotation of the camera

 |

/roty

 |
Y-rotation of the camera

 |

/rotz

 |
Z-rotation of the camera

 |

##
m: Memory Usage

Path

 |
Description

 |

/Memory/mainMemUsageInMB

 |
Main memory used, measured in MB

 |

/Memory/vidMemUsageInMB

 |
Video memory used, measured in MB

 |

##
n: Network Traffic

Path

 |
Description

 |

/Network/FragmentedBandwidthSent

 |
Fragmented data sent, measured in bits

 |

/Network/FragmentedPacketsSent

 |
Fragmented data sent, measured in packets

 |

/Network/LobbyBandwidthSent

 |
Lobby data sent, measured in bits

 |

/Network/LobbyPacketsSent

 |
Lobby data sent, measured in packets

 |

/Network/OtherBandwidthSent

 |
Other data sent, measured in bits

 |

/Network/OtherPacketsSent

 |
Other data sent, measured in packets

 |

/Network/SeqBandwidthSent

 |
Sequence data sent, measured in bits

 |

/Network/SeqPacketsSent

 |
Sequence data sent, measured in packets

 |

/Network/TotalBandwidthRecvd

 |
Total data received, measured in bits

 |

/Network/TotalBandwidthSent

 |
Total data sent, measured in bits

 |

/Network/TotalPacketsSent

 |
Total data sent, measured in packets

 |

##
o: Object Streaming

Path

 |
Description

 |

/StreamingObjects/bandwidthActualKBsecond

 |
Bandwidth used for streaming objects, measured in KB/s

 |

/StreamingObjects/bandwidthRequestedKBsecond

 |
Bandwidth requested for streaming objects, measured in KB/s

 |

##
p: Particles

Path

 |
Description

 |

/Particles/numEmittersActive

 |
Number of active particle emitters

 |

/Particles/numEmittersAllocated

 |
Number of allocated particle emitters

 |

/Particles/numEmittersRendered

 |
Number of rendered particle emitters

 |

/Particles/numParticlesActive

 |
Number of active particles

 |

/Particles/numParticlesAllocated

 |
Number of allocated particles

 |

/Particles/numParticlesClipped

 |
Number of clipped particles

 |

/Particles/numParticlesCollideHit

 |
Number of particles involved in a collision

 |

/Particles/numParticlesCollideTest

 |
Number of particles tested for collision

 |

/Particles/numParticlesReiterated

 |
Number of particles that were re-calculated

 |

/Particles/numParticlesRejected

 |
Number of particles not rendered

 |

/Particles/numParticlesRendered

 |
Number of particles rendered

 |

/Particles/particleScreenFractionProcessed

 |
Fraction of the screen pixels that were processed for particles

 |

/Particles/particleScreenFractionRendered

 |
Fraction of the screen pixels that rendered particles

 |

##
r: Frame Profilers

Details the amount of time spent in various tasks.

Path

 |
Description

 |

/Threads/$/count

 |
Number of times this task was executed

 |

/Threads/$/peak

 |
Peak amount of time spent executing this task

 |

/Threads/$/selfTimeInMS

 |
Total amount of milliseconds spent executing this task

 |

##
s: Streaming

Path

 |
Description

 |

/Streaming/cgfStreamingMemRequiredInMB

 |
Memory required for streaming CGF's, measured in MB

 |

/Streaming/cgfStreamingMemUsedInMB

 |
Memory used for streaming CGF's, measured in MB

 |

/Streaming/cgfStreamingPoolSize

 |
Size of the CGF streaming pool, measured in MB

 |

/Streaming/tempMemInKB

 |
Temporary memory used for streaming, measured in KB

 |

##
t: Threading

Path

 |
Description

 |

/Threading/MTLoadInMS

 |
Amount of milliseconds where the main thread was busy

 |

/Threading/MTWaitingForRTInMS

 |
Amount of milliseconds where the main thread was waiting for the render thread

 |

/Threading/NetThreadTimeInMS

 |
Amount of milliseconds spent by the networking thread

 |

/Threading/RTFrameLengthInMS

 |
Amount of milliseconds spent by the rendering thread on processing the frame

 |

/Threading/RTLoadInMS

 |
Amount of milliseconds where the render thread was busy

 |

/Threading/RTSceneDrawningLengthInMS

 |
Amount of milliseconds spent by the rendering thread on drawing the scene

 |

/Threading/RTWaitingForGPUInMS

 |
Amount of milliseconds where the render thread was waiting for the GPU

 |

/Threading/RTWaitingForMTInMS

 |
Amount of milliseconds where the render thread was waiting for the main thread

 |

##
u: User-defined Markers

The initial $ token is used to categorize markers.

Path

 |
Description

 |

/UserMarkers/$/name

 |
Name of the marker

 |

##
v: Vertex Counts

Path

 |
Description

 |

/VertexData/SkinnedPolyCountZ

 |
Skinned polygon count

 |

/VertexData/StaticPolyCountZ

 |
Static polygon count

 |

/VertexData/VegetationPolyCountZ

 |
Vegetation polygon count

 |

##
w: Physical Entity Profiling

Categorized by the type of physical entity, e.g. static, living, etc.

Path

 |
Description

 |

/PhysEntities/$/nCalls

 |
Number of function calls to process the entity

 |

/PhysEntities/$/time

 |
Time spent processing the entity

 |

/PhysEntities/$/x

 |
X-coordinate of the entity

 |

/PhysEntities/$/y

 |
Y-coordinate of the entity

 |

/PhysEntities/$/z

 |
Z-coordinate of the entity

 |

##
x: Texture Streaming

Path

 |
Description

 |

/StreamingTextures/amtRequestedJobsMB

 |
Amount of data requested by jobs, measured in MB

 |

/StreamingTextures/bandwidthActualKBsecond

 |
Actual streaming bandwidth, measured in KB/s

 |

/StreamingTextures/bandwidthRequestedKBsecond

 |
Requested streaming bandwidth, measured in KB/s

 |

/StreamingTextures/bias

 |
Bias of the texture streamer

 |

/StreamingTextures/numRenderedPerSecond

 |
Not enabled

 |

/StreamingTextures/numRequestedJobs

 |
Number of requested jobs

 |

/StreamingTextures/numRequestedPerSecond

 |
Not enabled

 |

/StreamingTextures/numUpdatedPerSecond

 |
Number of updated textures per second

 |

/StreamingTextures/poolMemUsedMB

 |
Amount of memory used for the texture pool, measured in MB

 |

/StreamingTextures/poolMemWantedMB

 |
Amount of memory requested for the texture pool, measured in MB

 |

/StreamingTextures/streamAllocFails

 |
Number of failed stream allocations. Only tracked if TEXSTRM_BYTECENTRIC_MEMORY is defined

 |

/StreamingTextures/streamPoolHardCreates

 |
Amount of times the streaming pool has allocated non-shared memory

 |

/StreamingTextures/streamPoolHardFrees

 |
Amount of times the streaming pool has freed non-shared allocations

 |

/StreamingTextures/streamPoolMemBoundMB

 |
Amount of memory bound and used for the streaming pool, measured in MB

 |

/StreamingTextures/streamPoolMemInUseMB

 |
Amount of memory used for the streaming pool, measured in MB

 |

/StreamingTextures/streamPoolMemReservedMB

 |
Amount of memory reserved for the streaming pool, measured in MB

 |

/StreamingTextures/streamPoolSoftCreates

 |
Amount of times the streaming pool has shared an allocation

 |

/StreamingTextures/streamPoolSoftFrees

 |
Amount of times the streaming pool has freed a shared allocation

 |

##
z: Network Channel

Network traffic categorized per network channel.

Path

 |
Description

 |

/Channel/$/BandwidthRecvd

 |
Data received, measured in bits

 |

/Channel/$/BandwidthSent

 |
Data sent, measured in bits

 |

/Channel/$/IdealPacketSize

 |
Ideal packet size for this channel, measured in bits

 |

/Channel/$/MaxPacketSize

 |
Maximum packet size for this channel, measured in bits

 |

/Channel/$/PacketRate

 |
Rate of packets, measured in bits/s

 |

/Channel/$/Ping

 |
Ping measurement

 |

/Channel/$/SentMessages

 |
Number of messages sent by the message queue

 |

/Channel/$/SparePacketSize

 |
Spare bandwidth available for additional packets, measured in bits

 |

/Channel/$/UnsentMessages

 |
Number of unsent messages in the message queue

 |

/Channel/$/UrgentRMIs

 |
Number of urgent remote method invocations. Only available if ENABLE_URGENT_RMIS is defined as a non-false preprocessor token

 |

/Channel/$/UsedPacketSize

 |
Bandwidth used for packets, measured in bits

 |

**

**
