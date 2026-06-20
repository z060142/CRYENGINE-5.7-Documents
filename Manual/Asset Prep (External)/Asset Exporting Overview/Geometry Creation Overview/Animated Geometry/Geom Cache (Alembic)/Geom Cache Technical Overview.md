# Geom Cache Technical Overview

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/25535717
- Page ID: 25535717
- Breadcrumb: Asset Prep (External) > Asset Exporting Overview > Geometry Creation Overview > Animated Geometry > Geom Cache (Alembic) > Geom Cache Technical Overview
- Parent: Geom Cache (Alembic)

## Content

##
Resource Compiler

##
Links to other supporting documentation

Link to asset creation documentation for GeomCaches can be found
[/docs/static/engines/cryengine-5/categories/23756816/pages/25534123](
here...
)

Reads alembic file format (currently HDF5 based up to version 1.1) and outputs compiled frame data into FIFOs for the encoder. TODO: Alembic 1.5 introduced a new data format which should greatly benefit read speed.

##
Supported alembic features

We support static and dynamic transforms with static or homogeneous poly meshes as leafs. Heterogeneous meshes (with changing topology) are not currently supported as they are not suitable for our compression scheme.

##
Frame generation

Alembic supports different frame spacing per object in the scene tree. E.g. a mesh can have frames at irregular intervals and a transform instead has a fixed 1/30s time step in the same file. CryEngine geometry caches do not support this. Each frame contains data for all objects in the scene to make realtime decoding simpler. To achieve this the alembic compiler first creates the superset of all frame times of the objects in the scene (
AlembicCompiler
::
CheckTimeSampling
). For each unique found frame time a frame will be output.

##
Vertex splitting

Alembic has seperate arrays for each vertex data element. This for example allows two triangles to share the same position data for a vertex, but don't share the texture coordinates. GPUs only support a single index buffer for all elements therefore in this case we need to also duplicate the position data. This even is true if the UVs would only be different in one frame of the entire animation because we need the topology to stay the same for all frames.

To achieve this we first calculate a 64 bit hash for each vertex over all frames of the mesh's animation (
AlembicCompiler
::
ComputeVertexHashes
). If the hash of a vertex is different for two triangles it needs to be split. Note that there is a chance of a hash collision, but this is pretty unlikely with 64 bits. Checking for collisions would be pretty slow, so we don't do this at the moment.

##
Smooth normal generation

If the mesh is does not contain normals we need to calculate smooth normals for the mesh in those cases (
AlembicCompiler
::
CalculateSmoothNormals
). We couldn't drop support meshes without normals because Maya doesn't store any normal information for a mesh if it is completely smooth. The used algorithm averages the normals of the adjacent triangles multiplied by angle of the respective corners.

##
Tangent space calculation

We use Mikkelson's tangent space algorithm for calculating a tangent space for each frame of the animation from the normals and UVs of the mesh.

##
Mesh optimization

Meshes are optimized with Forsyth's face reorder algorithm to better utilize the GPU's transform cache. This is also necessary as a preparation for inter prediction which assumes the index order follows strips of triangles over the mesh.

##
Materials

The engine format supports multiple materials per mesh. For this the index buffer will be split into chunks for each material. Currently this is done by parsing the name of the face sets of the mesh in the alembic file where the first number in the name is interpreted as the material ID (
AlembicCompiler
::
GetMeshFaceSets
).

##
Vertex quantization and conversion

For compression purposes all data is quantized to integer values (
AlembicCompiler
::
CompileVertices
).

##
Positions

Positions are first normalized to [0,1] per axis where 0 and 1 represent the minimum and maximum extent for that axis of the AABB of the mesh's entire animation. After that the position is quantized to uint16. The value representing 1 is chosen so that enough bits are allocated to be better or good enough to match the specified position precision which can be set by RC command line. Smaller meshes therefore use a smaller range of values and therefore compress better.

##
UVs

Texcoords are quantized to uint16. The range is 0-63. Values wrap outside of that range.

##
Colors

Colors are stored as four individual streams for red, green and blue where each value is coded as one uint8 representing range 0-1.

##
Normals & tangents

Tangent frames consisting of normal, bitangent and tangent are converted to QTangents and then each component is quantized to int16 where 10 bits are used for range [-1, 1]. The reflection of the first frame is enforced for all successive frames to avoid interpolation issues. This only happens in edge cases where the tangent frame calculation produces different orientations for different frames. (
AlembicCompiler
::
EncodeQTangent
)

##
Static and animated data

Each vertex channel of a mesh (positions, uv, color, QTangent) can either be static or dynamic. Static data is only stored once in the beginning of the file, so only animated channels are stored per frame.

##
Transform hierarchy optimization

As an optimization the alembic transform hierarchy is flattened as far as possible. All unnecessary transforms in the hierarchy are removed, e.g. a mesh with two dynamic transforms and no siblings will only have a single dynamic transform in the engine format (
AlembicCompiler
::
CompileStaticDataRec
). RC with verbose output will print the resulting tree for debugging purposes.

Transforms are converted to QuatTNS (Quaternion with translation and non-uniform scale) and stored per frame if they are dynamic. This is not optimized yet because the data rate was not an issue compared to vertex animation.

##
Parallel frame processing

Dynamic meshes and transforms are updated for each frame. For transforms the influences for that transform are read from the Alembic scene each frame and the final result is computed. For meshes the vertex data is updated, smooth normals are recompiled if required and the tangent space is recomputed. Finally the vertices are converted to engine format again (see "Vertex quantization and conversion").

For output there is one FIFO buffer per mesh and transform which is written by the compiler and read from the encoder in frame order.

As this is an expensive operation the updates are run as jobs. One job per mesh and one job for all frame transform updates is spawned. To get enough parallelism data for multiple frames is processed in parallel. As the output must be in order a reservation buffer is used for each mesh and transform and data is only passed to the encoder if the next frame is completed. In case the reservation buffer runs full, the compiler stalls.

The encoder's job is to take the quantized data and try to predict it so the resulting residual is as small as possible. Smaller residual frames result in better compression ratio. The geometry cache format uses inter- (prediction of data with references only to the same frame) and intra prediction (prediction with references to other frames) to accomplish this goal. There currently is no prediction for animated transforms which also get stored as full QuatTNS in float format. There is a lot of room for optimization there if necessary.

##
Inter prediction

Index frames can only use inter prediction as they must be able to be decoded without any other frame information. For vertex positions and texcoords we use parallelogram prediction.

The next vertex value is predicted from the previous triangle with P = C + B - A. The stored value is r = V - P, which is the residual from the prediction. For this prediction the encoder and the decoder need to know the adjacent triangle. We store the distance to the vertices that form the triangle we predict from as three uint16 values. The maximum look back distance is currently 4096. If no match can be found only one value is stored (0xFFFF) and we just use the previous vertex value as the predicted value.

To maximize the possibility for prediction we rearrange the vertices based on first use in the index array (
GeomCacheEncoder
::
OptimizeMeshForCompression
). This results in an vertex array where the distance to the last triangle's vertices is minimized.

For color and QTangents we don't use parallelogram prediction and just average B and C, which results in slightly better compression ratios.

##
Intra prediction

For even better compression ratio by default only every 10th frame is an index frame and frames between are predicted from the two frames before and the previous and next index frames (
InterpolateMotionDeltaPredictor
).

The formulas for the predictor are:

-
P
m
 = F
p
 + a * (F
p
 - F
pp
)

-
P
i
 = I
p
 + b * (I
n
 - I
p
)

-
P = P
i
 + c * (P
m
 - P
i
)
The motion predictor (1) assumes that the vertex' motion continues in the same direction. Therefore it predicts it's value with the previous frame value plus the direction of motion derived from the last two frames. Factor a is the acceleration which can be in the range [0, 2] encoded as a uint8. For the first B frame there is no motion prediction as we can't access the B frame before the I frame. The interpolation predictor (2) just does a linear interpolation between the previous and next I frame with the factor b. The factor b is stored as a uint8. Finally both predictors are combined in another linear interpolation (3) with factor c stored as a uint8. This means for each frame and mesh we store three uint8 values for the predictor.

To minimize the search space for a, b and c the encoder first searches for the optimal entropy for (1) and (2) with a binary search and finally does another binary search with the found values for (3).

The writer has the function to take data from the compiler and encoder and store it in the final disk format with the chosen block compression.

##
File structure

First after compiling the static data the header is written which contains the 64 bit file signature, a version number, the block compression format, a flags field, the number of frames, the total uncompressed animation size and the AABB for the entire geom cache animation. Note that the signature is initially written with zeroes to prevent the cache from being loaded when the conversion fails. Only at the very if everything else was successful end we write the final signature ("CRYCACHE").

The writer then leaves out room for a frame info struct (
SFrameInfo
) for each frame which contains the frame type (I or B frame, 32 bit), frame size (32 bit) and frame offset (64 bit). The frame sizes and offsets can only be known after compilation because compression size varies. Those will be written in at the very end as well. The file header and frame infos are stored uncompressed.

Next in the files is the first compressed block which contains the static data. For all meshes this contains the index data (we don't support topology changes, remember), the static vertex channels and for meshes with at least one animated channel the uint16 adjacent triangle array for the parallelogram predictor. For transforms this contains the transform type and a QuatTNS for static transforms.

Each frame then gets stored as one compressed block each which contain the residual data after prediction for all animated channels and the QuatTNS animated transforms.

##
Block compression formats

We support three different options for block compression, store, deflate and LZ4HC. Store just stores the raw data which is good for decoding speed, but mostly is implemented as a debugging feature. Deflate results in best compression ratio but is quite slow to decode. LZ4HC is very fast to decode (in the order of a magnitude faster than deflate) but results in about 20% bigger files.

In general LZ4HC seems to be the best option if the scene where the cache is used is heavy on CPU usage from other systems, otherwise if CPU time isn't of concern use Deflate.

##
Asynchronous writes

Each pushed block from the encoder gets pushed in a queue which jobs for compression pick up. After compression they get handed to a write thread which asynchronously writes to disk.

##
Engine Playback

-
Gets an update each frame from the engine (
CGeomCacheManager
::
StreamingUpdate
)

-
Issues async disk read requests for all registered and active streams

-
Issues decompress jobs when async read is ready

-
Each decompress and decode buffer holds multiple frames to allow getting them in one sequential read from disk. Every buffer always ends with an index frame.

-
All buffers get allocated in a heap of fixed size that is allocated on engine startup (e_geomCacheBufferSize)

-
Every frame has a decode dependency counter. Those get initialized to 1 for index frames, 3 for the first b frame after an index frame and 2 for all other b frames. Initialization is done when a stream is created and when retiring a buffer.

-
When a job decreases another frame's dependency counter to zero it starts the decode job. Done decompress jobs decrement the dependency counter of their frame's decode job. Index frame decode jobs. Done index frame jobs decrement the dependency counter of the the next B frame and the first b frame after the last index frame. B frame jobs decrement the next B frame's depedency counter. This makes sure that every frame always has the data it needs (it's own decompressed data and for b frames the prev two b frames and the prev and next index frame data).

-
Frame is marked as ready as soon as the decode job

-
If the cache is playing the manager issues an async fill job that takes the finished decoded data and fills the render element data for the frame

-
Reads static data from disk

-
Each frame has a struct with the frame's offset, size, type and offsets to the prev and next index frame

-
Data will be loaded/unloaded asynchronously at runtime if render node gets hidden/unhidden if e_streamCGF is set to 1.

-
Animation data will be read and decompressed completely if cache is set to "play back from memory" and its size is under the limit set by e_GeomCacheMaxPlaybackFromMemorySize. Only the async fill job will run for those caches when playing back.

-
Multiple geometry caches share static meshes if their hash is exactly identical

-
This class manages construction of render meshes for the geom caches and deduplicates them if the hash is the same.

-
Created and owned by the render proxy of the entity (GeomCache.lua in most cases)

-
Registers with the manager. The manager creates one stream object for each registered render node

-
Has the interface to change the current playback and stream position (streaming can be done at a different point than playback in case playback needs to continue from a different location)

-
Creates one render element for each material in the cache

-
The Render method issues the draws for each render element to the engine

-
There is support for drawing CGFs instead of the cache at a certain distance (stand ins). There are three options for stand ins: One for the first frame, one for the last frame and one for all other frames. If you only specify the one for all frames it will also be used for first and last frame.

-
Automatic start of streaming when getting to a certain distance of the cache is also supported

-
Waits for the asynchronous update job in the render thread

-
Goes over each mesh and issues draw calls to the engine

-
For static meshes instancing is supported on PC and Durango (default threshold for that is 10 instances)

##
CVars

CVar

 |
Description

 |

**
e_GeomCaches
**

 |
Disables drawing of geometry caches. Also disables launching of new async reads and launching of decompress & decode jobs in the manager.

 |

**
e_GeomCacheBufferSize
**

 |
Sets the size in MB for the streaming buffer heap. Default is 128MB, which is enough ~10MB/s.

Other values are conservative in Ryse, could potentially be enough for more.

 |

**
e_GeomCacheMaxPlaybackFromMemorySize
**

 |
Limits "playback from memory" to caches with less than the specified size in MB (default 16).

 |

**
e_GeomCachePreferredDiskRequestSize
**

 |
The preferred size for one read in KB. Currently set to 1MB. The manager will try to read as many frames as possible until it hits this limit or the max buffer ahead time.

 |

**
e_GeomCacheMinBufferAheadTime
**

 |
The minimum amount of time the manager will always try to keep in memory for each stream.

Lower values will result in a higher likelihood of stream aborts. If this is already reached there will be no more disk requests issued for the frame.

 |

**
e_GeomCacheMaxBufferAheadTime
**

 |
The max amount of time it will buffer ahead. This allows the manager to reach the preferred disk request size more often.

 |

**
e_GeomCacheDecodeAheadTime
**

 |
The amount of time when the manager will start creating decode buffers and launch decompress and decode jobs for the frames in them.

 |

**
e_GeomCacheDebug
**

 |
Shows a debug overlay which represents the buffers in the heap and shows all active streams

 |

**
e_GeomCacheDebugFilter
**

 |
Filters the active streams by name when e_GeomCacheDebug is active

 |

**
e_GeomCacheDebugDrawMode
**

 |
1: Only animated meshes

2: Only static meshes

3: Displays the same render meshes with the same color. Useful for debugging instancing.

Note that 1 and 2 will only have effect when the cache is playing at the moment.

 |

**
e_GeomCacheLerpBetweenFrames
**

 |
If set to 0 disables interpolation between frames. Used for debugging, it has no performance advantage.

 |
