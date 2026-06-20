# CVars and Console Commands

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/29450504
- Page ID: 29450504
- Breadcrumb: Editor Tools > Universal Query System (UQS) > CVars and Console Commands
- Parent: Universal Query System (UQS)

## Content

##
CVars and Console Commands

##
CVars

CVar
 |
Description
 |

uqs_timeBudgetInSeconds
 |
Specifies the time budget (in seconds) that the UQS is allowed to use for each update call. Internally, it will split up this time budget among all currently running queries to provide the best possible load balance. Setting this CVar to a value lower than or equal to 0.0 means that the absolute minimal amount of time-sliced work possible will be performed internally. In this case, complex queries will most likely be distributed over multiple Engine frames, thus taking a considerable amount of time until finished.
 |

uqs_debugDraw
 |
If set to 1, draws some statistics and the list of ongoing queries as 2D text on screen. Also, it will have the ongoing queries draw debug-rendering primitives in the 3D world for up to 2 seconds after they have finished.
 |

uqs_debugDrawZTestOn
 |
If set to 1, then the debug-rendering primitives of queries will enable z-testing when being drawn in the 3D world.
 |

uqs_debugDrawLineThickness
 |
Specifies the thickness of debug-rendering lines in the 3D world. This can be used to visualize, for example a raycast when otherwise it would be difficult to see.
 |

uqs_logQueryHistory
 |
If set to 1, then all running queries will also get recorded into a query history in memory. That history can be saved and restored either via the
**
Query History Inspector
**
 Editor plugin (or via console commands
**
UQS_DumpQueryHistory
**
 /
**
UQS_LoadQueryHistory
**
, see below) and be loaded into the
**
Query History Inspector
**
 for later inspection.
 |

##
Console Commands

Console Command
 |
Description
 |

UQS_ListFactoryDatabases
 |
Prints all registered factories for creating items, functions, generators and evaluators to the console.
 |

UQS_ListQueryBlueprintLibrary
 |
Prints all query blueprints in the library to the console.
 |

UQS_ListRunningQueries
 |
Prints all currently running queries to the console.
 |

UQS_DumpQueryHistory
 |
Dumps all queries that were executed so far to an XML file for de-serialization at a later time. Saving the current history in memory to disk is also possible via the
**
Query History Inspector
**
 Editor plugin.
 |

UQS_LoadQueryHistory
 |
Loads a history of queries from an XML for debug-rendering and inspection in the 3D world. Loading a history from disk into memory is also possible via the
**
Query History Inspector
**
 Editor plugin.
 |

UQS_ClearDeserialzedQueryHistory
 |
Clears the history of queries previously loaded from disk into memory. This is also possible via the
**
Query History Inspector
**
 Editor plugin.
 |

[#cvars-and-console-commands](
CVars and Console Commands
)
[#cvars](
CVars
)
[#console-commands](
Console Commands
)
