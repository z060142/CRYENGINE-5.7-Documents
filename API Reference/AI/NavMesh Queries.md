# NavMesh Queries

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/44964078
- Page ID: 44964078
- Breadcrumb: AI > NavMesh Queries
- Parent: AI

## Content

##
Overview

NavMesh Queries provide an easy way to query for NavMesh triangles within an Axis Aligned Bounding Box (AABB), inside a NavMesh. These Queries are an essential part of the AI system and, among other things, may be used to obtain the NavMesh triangle ID of a specific location, the borders of a NavMesh around an agent, and so forth.

The system is powerful since it supports custom C++ filters and post-processing structures, and, as we'll see later on in this page, allows the user to filter out 'invalid' triangles from NavMeshes and perform post-processing transformations on them.

Refer to
[Navigation Areas](../../Manual/AI%20and%20Navigation/AI%20Overview/Navigation%20(MNM)/Navigation%20Areas.md)
 in the CRYENGINE V Manual for information on creating NavMeshes.

The two types of NavMesh Queries available are Instant Queries and Batch Queries. The following documentation describes their configuration, usage and debugging.

##
Common Parameters

The following parameters are common to both Instant and Batch Queries.

Parameter
 |
Description
 |

**
Configuration
**
 |
The following configuration parameters are required to specify how the NavMesh Query must be performed.

**
MeshID
**
 |
The ID of the NavMesh on which the Query must run.
 |

**
Caller (Optional)
**
 |
Identifies the AI agent performing the NavMesh Query. This identifier can be a user-defined name, and is used for debugging purposes.
 |

**
AABB
**
 |
The coordinates of the Query's Axis Aligned Bounding Box.
 |

**
Overlapping Mode
**
 |
Defines the criteria according to which the overlap between a NavMesh triangle and the Query's AABB is calculated. This parameter must have one of the following values:

**
BoundingBox_Partial
**
 |
Checks if there's an overlap between the AABB of the NavMesh triangle and the AABB of the Query.
 |

**
BoundingBox_Full
**
 |
Checks if the AABB of the NavMesh triangle is fully inside the AABB of the Query.
 |

**
Triangle_Partial
**
 |
Checks if there's an overlap between the NavMesh triangle and the AABB of the Query.
 |

**
Triangle_Full
**
 |
Checks if the triangle is fully contained inside the AABB of the Query.
 |

 |

**
Query Filter
**
 |
Contains additional logic to filter out triangles that satisfy the criteria specified by the
**
Overlapping Mode
**
 parameter. This is useful to determine which triangles are to be passed as input to the NavMesh's post-processing logic.

The C++ class
*
SAcceptAllQueryTrianglesFilter
*
 is the default filter, which accepts all triangles.

 |

 |

**
Processing Size
**
 |
The size of the batch in which triangles should be post-processed. The default value is
**
1024
**
, which means the post–processing function is applied on every 1024 triangles returned by the running Query.
 |

**
Query Processing
**
 |
Holds the triangle post-processing logic of the NavMesh Query.

The Query Processing logic works as a queue, such that the queue is filled with triangles that require processing while the Query is running. As soon as this queue reaches the size specified by the
**
Processing Size
**
 parameter, the triangles are processed and the queue is emptied. How the triangles are processed depends on the specific implementation of the Query Processing logic.

For example, the default processing logic (
*
MNM: CDefaultProcessing
*
 in C++) simply stores the IDs of the triangles returned by the NavMesh Query within an array, which is then accessed by the user.

 |

**
Result
**
 |
Describes the execution status of the NavMesh Query. It can have the following values:

**
Uninitialized
**
 |
The Query is not yet initialized.
 |

**
Running
**
 |
The Query is running currently.
 |

**
Done_QueryProcessingStopped
**
 |
Processing of the Query was stopped by the Query Processing logic, after the desired result was obtained.
 |

**
Done_Complete
**
 |
All triangles were successfully processed, and the Query was completed.

The difference between
**
Done_QueryProcessingStopped
**
and
**
Done_Complete
**
 is that in the case of the former, the Query is stopped when the Query Processing logic decides. Whereas in the case of
**
Done_Complete
**
, the Query stops when it has processed all triangles inside its AABB.
 |

**
Invalid_InitializationFailed
**
 |
The Query failed to initialize.
 |

**
Invalid_NavMeshRegenerated
**
 |
Processing of the Query ended because of a NavMesh regeneration.
 |

**
Invalid_NavmeshAnnotationChanged
**
 |
Processing of the Query ended because of a change in a NavMesh's annotation.
 |

**
Invalid_CachedNavMeshIdNotFound
**
 |
Processing of the Query failed because the internal ID of the NavMesh was no longer valid after a regeneration.
 |

 |

##
Types

##
Instant Query

Returns the complete result when executed. Because of this, Instant Queries don't maintain an internal state and are particularly useful when it is known that the running time of the Query will be short, or when developers cannot afford to wait for the next frame for the Query's result.

```

`
// Create the Query config. Note that it is of type SNavMeshQueryConfigInstant.
const MNM::INavMeshQuery::SNavMeshQueryConfigInstant config(...);

// Create the Query Processing parameter.
MNM::CDefaultProcessing defaultProcessing(1024);

// Call the QueryManager to run an instant query, passing the Query Configuration and the Query Processing parameter.
MNM::INavMeshQuery::EQueryStatus queryStatus = gEnv->pAISystem->GetNavigationSystem()->GetNavMeshQueryManager()->RunInstantQuery(config, defaultProcessing);

// Check if the Query ran successfully.
if (queryStatus == MNM::INavMeshQuery::EQueryStatus::Done_Complete)
{
  // Access the IDs of the resultant triangles stored in the Query Processing queue.
  DoSomethingWithTheResult(defaultProcessing.GetTriangleIdArray());
}
`

```

##
Batch Query

Returns only a batch/part of the complete result when executed; the next batch of results is returned when the Query is executed again, until the complete result has been returned.

Because of this, Batch Queries maintain an internal state to keep track of where execution should next begin from, and are useful when computing must be split across multiple frames for performance.

Batch Queries require the following additional parameters in their configuration:

**
Parameter
**
 |
Description
 |

**
Processing Triangles Max Size
**
 |
The maximum number of triangles that can be processed by the Query in total.

This parameter is not to be confused with the
**
P
**
**
rocessing Size
**
 parameter described in the Common Parameters section above.
**
Processing Triangles Max Size
**
 must be equal to or bigger than
**
Processing Size
**
.

 |

**
Action on NavMesh Regeneration
**
 |
Defines how the Query should react when the queried NavMesh is being regenerated. This parameter can take one of the following values:

**
Ignore
**
 |
Changes in the NavMesh are ignored and execution of the Query continues, unless a change in the NavMesh occurs within the same NavMesh tile that the Query is processing.
 |

**
Invalidate Always
**
 |
The NavMesh Query is immediately invalidated and it's execution is stopped when the NavMesh changes.
 |

**
Invalidate if Processed
**
 |
The Query is invalidated and its execution is stopped only when a NavMesh regeneration affects a NavMesh tile that has already been processed by the Query.
 |

 |

**
Action on NavMesh Annotation Change
**
 |
Defines how the Query should react when the queried NavMesh's annotation changes. This parameter can take the following values:

**
Ignore
**
 |
Changes in the NavMesh are ignored and triangles continue to be processed, unless a change in the NavMesh's annotation occurs within the same tile that the Query is processing.
 |

**
Invalidate Always
**
 |
The NavMesh Query is immediately invalidated and it's processing is stopped when the NavMesh's annotation changes.
 |

**
Invalidate if Processed
**
 |
The Query is invalidated and its execution is stopped only when the change in a NavMesh's annotation occurs within a tile that has already been processed by the Query.
 |

 |

```

`
// Create the Query config. Note that it is of the type SNavMeshQueryConfigBatch.
const MNM::INavMeshQuery::SNavMeshQueryConfigBatch config(...);

// Create the Query Processing. The size of the defaultProcessing should be smaller or equal to the size of the batches (performance reasons).
MNM::CDefaultProcessing defaultProcessing(batchSize)

// Call the QueryManager to create a Batch Query. As opposed to Instant Queries, we're not running the Batch Query directly here but are being returned a pointer instead that we will use to execute the Query when we need to.
MNM::INavMeshQueryPtr * pQuery = gEnv->pAISystem->GetNavigationSystem()->GetNavMeshQueryManager()->CreateBatchQuery(config);

// Imagine that we want to run the Query while we still have some time left in this frame.
// This will execute the query in batches of batchSize until the Query is done, fails or we run out of time.
while(pQuery->IsValid() && !pQuery->IsDone() && timeLeftInThisFrame)
{
  // Run a single Query batch of the specified size.
  pQuery->Run(defaultProcessing, batchSize);

  // Access the result stored in Query Processing.
  DoSomethingWithTheResult(defaultProcessing.GetTriangleIdArray());

  // Update time left in this frame.
  UpdateTimeLeftInFrame();
}

`

```

##
Debug

The following CVars can be used for debugging NavMesh Queries.

**
Name
**
 |
**
Variable
**
 |
Default
 |
Description
 |
Flags
 |

**
ai_storeNavigationQueriesHistory
**

 |
StoreNavigationQueriesHistory

 |
0

 |
When enabled, a history of NavMesh Queries is maintained. This history can be displayed by enabling the
**
ai_DebugDrawNavigationQueriesUDR
**
 or
**
ai_DebugDrawNavigationQueriesList
**
CVars.

Requires CVars
**
ai_debugDraw
**
 and
**
ai_debugDrawNavigation
**
 to be enabled.

 |
VF_CHEAT | VF_CHEAT_NOCHECK
 |

**
ai_DebugDrawNavigationQueriesUDR
**

 |
DebugDrawNavigationQueriesUDR

 |
0
 |
Displays the debug information (config, triangles and invalidations) of NavMesh Queries using UDR.

Requires
**
ai_debugDraw, ai_debugDrawNavigation
**
 and
**
ai_storeNavigationQueriesHistory
**
 to be enabled.

 |
VF_CHEAT | VF_CHEAT_NOCHECK
 |

**
ai_DebugDrawNavigationQueriesList
**

 |
DebugDrawNavigationQueriesList

 |
0
 |
Displays a list of NavMesh Queries, with all batches and elapsed times.

Requires
**
ai_debugDraw, ai_debugDrawNavigation
**
 and
**
ai_storeNavigationQueriesHistory
**
 to be enabled. Note that, by their nature, instant queries won't be listed here.

 |
VF_CHEAT | VF_CHEAT_NOCHECK
 |

**
ai_DebugDrawNavigationQueryListFilterByCaller
**

 |
DebugDrawNavigationQueryListFilterByCaller
 |
None
 |
Displays a list of NavMesh Queries, containing only those queries that contain the given filter string.

By default, its value is set to None (no filter is applied).

Requires
**
ai_debugDraw, ai_debugDrawNavigation
**
 and
**
ai_DebugDrawNavigationQueriesList
**
 to be enabled.

 |

 |

There are two debug modes available:

##
List Mode

In List mode (enabled by the
**
ai_DebugDrawNavigationQueriesList
**
CVar), all running NavMesh Queries are displayed in a list in real time. This is very useful to see when a query is being executed, and the number of frames it lasts for. Using the
**
ai_DebugDrawNavigationQueryListFilterByCaller
**
 CVar, we can only display calls from a specific caller.

Since

**
InstantQueries
**

only run for a single frame, they

won't show up in List debugging mode.

*
List mode when debugging NavMesh Queries. Shows one query with 5 batches of 3 triangles each
*

##
UDR Mode

The results of all NavMesh Queries can also be visualized in the
[UDR Visualizer](../../Manual/Editor%20Tools/Advanced%20Tab/Universal%20Debug%20Recordings%20(UDR)%20Visualizer.md)
. The
**
ai_DebugDrawNavigationQueriesUDR
**
CVar has to be enabled for this.

 |
 |
 |

*
Hierarchy of different Queries and all other information
*
 |
*
 Results of Query 13. Bounding box and Triangles are drawn
*
 |
*
Statistics child expanded
*
 |

[Common Parameters](#common-parameters)
[Types](#types)
[Debug](#debug)
