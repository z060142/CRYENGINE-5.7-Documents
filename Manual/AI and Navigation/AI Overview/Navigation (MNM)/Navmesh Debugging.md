# Navmesh Debugging

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/29798769
- Page ID: 29798769
- Breadcrumb: AI and Navigation > AI Overview > Navigation (MNM) > Navmesh Debugging
- Parent: Navigation (MNM)

## Content

[Image: /docs/static/attachments/29933207]

##
Console Variables

Name

 |
Values

 |

ai_useMNM

 |
Obsolete - 0 - use the default navigation system, 1 - use the Multi-layer Navigation.

 |

ai_DebugDrawNavigation

 |
1 - display mesh and contour, 2 - also display triangles, 3 - also display tiles and external links.

 |

ai_debugMNMAgentType

 |
agent type - the name of meshes'
[/docs/static/engines/cryengine-5/categories/23756816/pages/44961796](
agent type
)
, for which debugging information is displayed.

 |

ai_MNMPathFinderQuota

 |
[/docs/static/engines/cryengine-5/categories/23756816/pages/25534842](
pathfinding
)
 quota per frame, in seconds.

 |

ai_MNMPathFinderDebug

 |
0/1 - hide/show pathfinder debug statistics: queue size, average and maximum number of A* search steps, average and maximum search time.

 |

ai_MNMProfileMemory

 |
0/1 - hide/show memory statistics.

 |

##
Sections

[#console-variables](
Console Variables
)
[#sections](
Sections
)
[#debugging](
Debugging
)
[#memory-statistics](
Memory Statistics
)

##
Debugging

##
Debugging Meshes and/or Tiles

-
Set
ai_DebugDrawNavigation
 to
3
.

-
Place a
*
TagPoint
*
 with the name "
MNMDebugLocator
" within (a tile of) the mesh you want to debug.

-
Press
*
BackSpace
*
 key to switch between the display of the different generation steps.
Some statistics will be displayed at the top-left corner of the screen:

##
Debugging Paths

To display a path between two points, a path which can use any
*
SmartObjects
*
 – place two
*
TagPoints
*
,
MNMPathStart
 and
MNMPathEnd
:

To display a path for a particular AI character, rename it to
MNMPathStart
:

##
Debugging Raycast

To debug
[/docs/static/engines/cryengine-3/categories/1114113/pages/1048582](
raycast
)
, create two
*
TagPoints
*
,
MNMRayStart
 and
MNMPathEnd
. You can see which triangles are traversed and where there is a hit, if any:

##
Memory Statistics

To display detailed memory statistics for each existing mesh, set
ai_MNMProfileMemory
 to
1
 and also make sure
ai_DebugDrawNavigation
 is not zero.
