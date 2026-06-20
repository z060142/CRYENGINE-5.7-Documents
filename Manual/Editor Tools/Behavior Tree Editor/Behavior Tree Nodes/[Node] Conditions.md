# [Node] Conditions

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/36869469
- Page ID: 36869469
- Breadcrumb: Editor Tools > Behavior Tree Editor > Behavior Tree Nodes > [Node] Conditions
- Parent: Behavior Tree Nodes

## Content

##
Conditions Nodes

The functioning of
**
Conditions
**
nodes is based on the value of Variables previously defined in the
[Data Definitions](../Behavior%20Tree%20Editor%20Window.md)
block of the Behavior Tree Editor.

##
Condition gate

**
Description
**

 |
Has exactly one child, which is only executed if the Condition gate is "open".

A gate is "open" only when the condition associated with it is satisfied.

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
Condition
**

 |
Specifies the condition that needs to be evaluated for the gate to be opened/closed.

 |
Accepts a logical expression containing Variables
(for example,
*
!a and b,
*
where
*
a
*
 and
*
b
*
**

**
are variables)
, that must return True/False as its result.

Any Variables used must be defined in the Data Definitions block.

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
When the Condition gate node is "open" and it's child node succeeds.

 |

**
Failure
**

 |
If the gate is "closed", or if its child node fails when the gate is "open".

 |

 |

**
Additional Information
**

 |
None.

 |

##
Check Condition

**
Description
**

 |
Checks if a specified condition has been satisfied.

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
Condition
**

 |
Specifies the condition that needs to be evaluated.

 |
Accepts a logical expression containing Variables (for example,
*
!a and b,
*
where
*
a
*
 and
*
b
*
**

**
are variables), that must return True/False as its result.

Any Variables used must be defined in the Data Definitions block.

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
If the specified
**
Condition
**
 is satisfied.

 |

**
Failure
**

 |
If the
**
Condition
**
 isn't satisfied.

 |

 |

**
Additional Information
**

 |
None.

 |

[Conditions Nodes](#conditions-nodes)
[Condition gate](#condition-gate)
[Check Condition](#check-condition)
