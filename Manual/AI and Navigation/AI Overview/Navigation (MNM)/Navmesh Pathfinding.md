# Navmesh Pathfinding

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/25534842
- Page ID: 25534842
- Breadcrumb: AI and Navigation > AI Overview > Navigation (MNM) > Navmesh Pathfinding
- Parent: Navigation (MNM)

## Content

[Image: /docs/static/attachments/29933210]

##
Overview

##
Sections

The pathfinder uses the A* search on the triangles of the mesh, with the distance to the destination as the heuristic. Naturally, the smaller the mesh, the smaller the search space and the faster the search will be.

Also note:

-
To pathfind, the AI character must be of an
[/docs/static/engines/cryengine-5/categories/23756816/pages/44961796](
agent type
)
 supported by the navigation mesh.

-
The AI character should always stay within the navigation mesh. Otherwise, it may not be able to pathfind anymore.

-
It is, however, possible for an AI character to get slightly out of the mesh (or try to pathfind to a location slightly out of the mesh). It will then try to find the closest triangle within a certain range.

[#sections](
Sections
)
[#time-slicing](
Time-slicing
)
[#testing](
Testing
)

##
Time-slicing

To avoid spikes when requesting paths, the pathfinder is time-sliced: requests for paths are not processed immediately, but are rather added to the queue, so it can take a few frames to get the result. To tweak the time-slicing, the following console variables can be used:

Name

 |
Values

 |

**
ai_MNMPathFinderQuota
**

 |
Pathfinding quota per frame, in seconds.

 |

**
ai_MNMPathFinderDebug
**

 |
**
0
**
/
**
1
**
 - Hide/show pathfinder debug statistics: queue size, average and maximum number of A* search steps, average and maximum search time.

 |

##
Testing

To test the pathfinder and navigation in the Editor:

-
Add an AI character to the map.

-
Select it.

-
Enable
**
[AI/Physics]
**
.

-
Set
**
ai_DrawPath
**
 to
**
all
**
 to visualize the path.

-
Set
**
ai_DrawPathFollower
**
 to
**
1
**
 to visualize the pathfollower, if needed.

-
Click the middle mouse button on the desired destination.

Other debugging tools are described at this
[/docs/static/engines/cryengine-5/categories/23756816/pages/29798769](
LINK
)
.
