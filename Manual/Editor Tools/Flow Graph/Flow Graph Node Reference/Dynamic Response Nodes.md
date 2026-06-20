# Dynamic Response Nodes

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/29450582
- Page ID: 29450582
- Breadcrumb: Editor Tools > Flow Graph > Flow Graph Node Reference > Dynamic Response Nodes
- Parent: Flow Graph Node Reference

## Content

##
CancelSignalProcessing

This node sends a signal to cancel the processing of the sent signal in the Dynamic Response System.

![Image](https://www.cryengine.com/docs/static/attachments/28901228)

##
SendSignal

This node sends a signal to the Dynamic Response System.

![Image](https://www.cryengine.com/docs/static/attachments/28901227)

**
Inputs
**

Port
 |
Type
 |
Description
 |

**
Send
**
 |
Any
 |
Sends the dynamic response signal
 |

**
Signal Name
**
 |
String
 |
Name of the dynamic response signal
 |

**
Outputs
**

Port
 |
Type
 |
Description
 |

**
Done
**
 |
String
 |
Triggered when the signal is sent or is canceled.
 |

##
SetFloatVariable

This node is used to set a
float
variable in a variable collection for the Dynamic Response System.

![Image](https://www.cryengine.com/docs/static/attachments/28901226)

**
Inputs
**

Port
 |
Type
 |
Description
 |

**
Set
**
 |
Any
 |
Set the given value to the specified variable
 |

**
EntityID
**
 |
Any
 |
The ID of the entity to fetch the collection from
 |

**
CollectionName
**
 |
String
 |
The name of the collection
 |

**
VariableName
**
 |
String
 |
The name of the variable to set
 |

**
FloatValue
**
 |
Float
 |
The value of the variable
 |

**
ResetTime
**
 |
Float
 |
The time after which the variable is reset to its previous value
 |

**
Outputs
**

Port
 |
Type
 |
Description
 |

**
UsedCollectionName
**
 |
String
 |
Outputs the name of the variable collection created or used
 |

##
SetIntegerVariable

This node is used to set an
integer
variable in a variable collection for the Dynamic Response System.

![Image](https://www.cryengine.com/docs/static/attachments/28901225)

**
Inputs
**

Port
 |
Type
 |
Description
 |

**
Set
**
 |
Any
 |
Set the given value to the specified variable
 |

**
EntityID
**
 |
Any
 |
The ID of the entity to fetch the collection from
 |

**
CollectionName
**
 |
String
 |
The name of the collection
 |

**
VariableName
**
 |
String
 |
The name of the variable to set
 |

**
IntegerValue
**
 |
Float
 |
The value of the variable
 |

**
ResetTime
**
 |
Float
 |
The time after which the variable is reset to its previous value
 |

**
Outputs
**

Port
 |
Type
 |
Description
 |

**
UsedCollectionName
**
 |
String
 |
Outputs the name of the variable collection created or used
 |

##
SetStringVariable

This node is used to set a
String
variable in a variable collection for the Dynamic Response System.

![Image](https://www.cryengine.com/docs/static/attachments/28901224)

**
Inputs
**

Port
 |
Type
 |
Description
 |

**
Set
**
 |
Any
 |
Set the given value to the specified variable
 |

**
EntityID
**
 |
Any
 |
The ID of the entity to fetch the collection from
 |

**
CollectionName
**
 |
String
 |
The name of the collection
 |

**
VariableName
**
 |
String
 |
The name of the variable to set
 |

**
StringValue
**
 |
Float
 |
The value of the variable
 |

**
ResetTime
**
 |
Float
 |
The time after which the variable is reset to its previous value
 |

**
Outputs
**

Port
 |
Type
 |
Description
 |

**
UsedCollectionName
**
 |
String
 |
Outputs the name of the variable collection created or used
 |

[CancelSignalProcessing](#cancelsignalprocessing)
[SendSignal](#sendsignal)
[SetFloatVariable](#setfloatvariable)
[SetIntegerVariable](#setintegervariable)
[SetStringVariable](#setstringvariable)
