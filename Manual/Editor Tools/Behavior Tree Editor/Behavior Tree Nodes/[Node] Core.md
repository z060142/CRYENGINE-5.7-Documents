# [Node] Core

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/36869477
- Page ID: 36869477
- Breadcrumb: Editor Tools > Behavior Tree Editor > Behavior Tree Nodes > [Node] Core
- Parent: Behavior Tree Nodes

## Content

##
Core Nodes

**
Core
**
nodes exhibit functionality for a variety of purposes.

##
Fail

**
Description
**

 |
Returns failure as its result, regardless of the outcome of its child's execution. A
**
Fail
**
 node has exactly one child.

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
When execution/processing of its child node is complete.

 |

 |

**
Additional Information
**

 |
None.

 |

##
Random Gate

**
Description
**

 |
Has exactly one child, which is executed when the
**
Random Gate
**
 node is "open".

The probability of the gate being "open" is random, although the degree of this randomness may be modified.

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
Chance to Open
**

 |
Modifies the degree of randomness by which the gate is opened.

 |
Accepts a floating point value in the range [0.0, 1.0] such that,

**
0.0
**

 |
The Random Gate will always be "closed".

 |

**
1.0
**

 |
The gate will always be "open".

 |

Any value in between accordingly affects the probability of the gate being "open".

For example, a
**
Chance to Open
**
value of
**
0.5
**
 gives the gate a 50% chance of being open.

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
When the gate is "open" and its child node succeeds.

 |

**
Failure
**

 |
If the gate is "closed", or if its child node fails when "open".

 |

 |

**
Additional Information
**

 |
None.

 |

##
Send Event

**
Description
**

 |
Sends an event to the Behavior Tree, that may in turn be used to trigger a change in a Variable, Timestamp, or similar.

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
Event
**

 |
Specifies the Event that should be sent by the node.

 |
Accepts any
**
Built-in
**
 or
**
Game
**
 Event as its value.

However the Event must be previously defined in the Data Definitions block.

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
If the
**
Event
**
 was successfully sent.

 |

**
Failure
**

 |
If the
**
Event
**
 wasn't sent.

 |

 |

**
Additional Information
**

 |
None.

 |

##
Suppress Failure

**
Description
**

 |
Returns success as its result, regardless of the outcome of its child's execution. A
**
Suppress Failure
**
 node has exactly one child.

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
As soon as execution/processing of its child node is complete.

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

[#core-nodes](
Core Nodes
)
[#fail](
Fail
)
[#random-gate](
Random Gate
)
[#send-event](
Send Event
)
[#suppress-failure](
Suppress Failure
)
