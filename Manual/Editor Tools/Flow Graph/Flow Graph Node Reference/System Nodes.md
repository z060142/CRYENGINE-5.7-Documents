# System Nodes

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/29450634
- Page ID: 29450634
- Breadcrumb: Editor Tools > Flow Graph > Flow Graph Node Reference > System Nodes
- Parent: Flow Graph Node Reference

## Content

##
Container Nodes

##
Create

Used to create a container.

[Image: /docs/static/attachments/29688001]

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
Id
**
 |
Integer
 |
Container ID
 |

**
Create
**
 |
Any
 |
Creates a container
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
Error
**
 |
Integer
 |
Triggers when an error occurs
 |

**
Success
**
 |
Any
 |
Tiggers when a container is created
 |

**
Id
**
 |
Integer
 |
Outputs the container ID
 |

##
Edit

Used to edit a container.

[Image: /docs/static/attachments/29688000]

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
Id
**
 |
Integer
 |
Container ID
 |

**
Add
**
 |
Any
 |
Adds the passed item to the container
 |

**
AddUnique
**
 |
Any
 |
Adds the passed item if it didn't exist
 |

**
Remove
**
 |
Any
 |
Removes all occurrences of the current item
 |

**
Clear
**
 |
Any
 |
Empties the container
 |

**
GetCount
**
 |
Any
 |
Gets the number of items in the container
 |

**
Delete
**
 |
Any
 |
Deletes the container
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
Error
**
 |
Integer
 |
Triggers when an error occurs
 |

**
Success
**
 |
Any
 |
Triggers when the operation successfully completed
 |

##
Iterate

Used to iterate over a container.

[Image: /docs/static/attachments/29687999]

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
Id
**
 |
Integer
 |
Container ID
 |

**
Start
**
 |
Any
 |
Starts iterating the container
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
Error
**
 |
Integer
 |
Triggers when an error occurs
 |

**
Done
**
 |
Any
 |
Triggers when the operation successfully completed
 |

**
Out
**
 |
Any
 |
Outputs the container ID
 |

[#container-nodes](
Container Nodes
)
[#create](
Create
)
[#edit](
Edit
)
[#iterate](
Iterate
)
