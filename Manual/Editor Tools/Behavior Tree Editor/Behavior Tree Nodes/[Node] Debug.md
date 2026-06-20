# [Node] Debug

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/36869479
- Page ID: 36869479
- Breadcrumb: Editor Tools > Behavior Tree Editor > Behavior Tree Nodes > [Node] Debug
- Parent: Behavior Tree Nodes

## Content

##
Debug Nodes

**
Debug
**
nodes are primarily used to log in-game information for purposes of debugging.

##
Check Timestamp

**
Description
**

 |
Checks if a
**
Timestamp
**
 exceeds or fails to reach a specified duration of time as per a defined
**
Comparator
**
.

 |

**
Parameters Accepted
**

 |
Parameter Name

 |
Description

 |
Value

 |

**
Timestamp
**

 |
Specifies the
**
Timestamp
**
 to track.

 |
Accepts the name of a
**
Timestamp
**
.

The Timestamp must be previously defined in the
**
Timestamp
**
 section of the Data Definitions block of the Behavior Tree Editor.

 |

**
Comparator
**

 |
The logic by which a
**
Timestamp
**
 must be compared against a defined
**
Duration.
**

 |
**
More Than
**

 |
Checks if the
**
Timestamp
**
 exceeds the specified
**
Duration
**
.

 |

**
Less Than
**

 |
Checks if the
**
Timestamp
**
 fails to reach the specified
**
Duration.
**

 |

 |

**
Duration
**

 |
The duration of time against which the specified
**
Timestamp
**
 must be compared.

 |
Accepts a floating point integer that represents the
**
Duration
**
, in seconds.

 |

**
Succeed If It Was Never Set
**

 |
Forces the node to succeed if no Timestamp is specified in the node's
**
Timestamp
**
 parameter field.

 |
Boolean; ticking the provided checkbox will force the node to succeed.

 |

 |

**
Results
**

 |
Outcome

 |
Criteria

 |

**
Success
**

 |

-
When the
**
Comparator
**
 between the specified
**
Timestamp
**
 and
**
Duration
**
yields true.

-
If no Timestamp is specified in the node's
**
Timestamp
**
 parameter field, and the
**
Succeed If It Was Never
**

**
Set
**
checkbox is checked.
 |

**
Failure
**

 |
Never.

 |

 |

**
Additional Information
**

 |
None.

 |

##
Halt

**
Description
**

 |
Permanently stops execution of the behavior tree.

 |

**
Parameters Accepted
**

 |
None.

 |

**
Results
**

 |
Outcome

 |
Criteria

 |

**
Success
**

 |
Never.
 |

**
Failure
**

 |
Never.

 |

 |

**
Additional Information
**

 |
None.

 |

##
Log Message

**
Description
**

 |
Logs a message in the behavior tree log.

Use the Behavior Tree Editor's
**
[Debug](../Behavior%20Tree%20Editor%20Window.md)

**
options for a visualization of log messages and the tree's sequence of execution.

 |

**
Parameters Accepted
**

 |
Parameter Name

 |
Description

 |
Value

 |

**
Message
**

 |
Specifies the message the node must log.

 |
Accepts a string value.

 |

 |

**
Results
**

 |
Outcome

 |
Criteria

 |

**
Success
**

 |
When the specified
**
Message
**
 is logged.
 |

**
Failure
**

 |
Never.

 |

 |

**
Additional Information
**

 |
None.

 |

[Debug Nodes](#debug-nodes)
[Check Timestamp](#check-timestamp)
[Halt](#halt)
[Log Message](#log-message)
