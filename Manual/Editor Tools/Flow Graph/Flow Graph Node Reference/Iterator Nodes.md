# Iterator Nodes

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/29450603
- Page ID: 29450603
- Breadcrumb: Editor Tools > Flow Graph > Flow Graph Node Reference > Iterator Nodes
- Parent: Flow Graph Node Reference

## Content

##
GetEntities

Used to find and return all entities in the world.

[Image: /docs/static/attachments/29687850]

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
Start
**
 |
Any
 |
Triggers the node
 |

**
Next
**
 |
Any
 |
Gets the next entity found
 |

**
Limit
**
 |
Integer
 |
Limits how many entities are returned
 |

**
Immediate
**
 |
Boolean
 |
Iterates immediately through the results
 |

**
Type
**
 |
Integer
 |
Type of entity to iterate
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
EntityId
**
 |
Any
 |
Outputs the entity and entity ID
 |

**
Count
**
 |
Integer
 |
Outputs the current of entities
 |

**
Done
**
 |
Integer
 |
Triggered when all entities have been found, with the total count returned
 |

##
GetEntitiesInArea

Used to find and return all entities within the specified area shape.

[Image: /docs/static/attachments/29687849]

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
Start
**
 |
Any
 |
Triggers the node
 |

**
Next
**
 |
Any
 |
Gets the next entity found
 |

**
Limit
**
 |
Integer
 |
Limits how many entities are returned
 |

**
Immediate
**
 |
Boolean
 |
Iterates immediately through the results
 |

**
Type
**
 |
Integer
 |
Type of entity to iterate
 |

**
Area
**
 |
String
 |
Name of area shape to test against
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
EntityId
**
 |
Any
 |
Outputs the entity and entity ID
 |

**
Count
**
 |
Integer
 |
Outputs the current of entities
 |

**
Done
**
 |
Integer
 |
Triggered when all entities have been found, with the total count returned
 |

##
GetEntitiesInBox

Used to find and return all entities within the defined AABB box.

[Image: /docs/static/attachments/29687848]

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
Start
**
 |
Any
 |
Triggers the node
 |

**
Next
**
 |
Any
 |
Gets the next entity found
 |

**
Limit
**
 |
Integer
 |
Limits how many entities are returned
 |

**
Immediate
**
 |
Any
 |
Iterates immediately through the results
 |

**
Type
**
 |
Integer
 |
Type of entity to iterate
 |

**
Min
**
 |
Vec3
 |
Minimum vector extents of the AABB bounding box to check for entities
 |

**
Max
**
 |
Vec3
 |
Maximum vector extents of the AABB bounding box to check for entities
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
EntityId
**
 |
Any
 |
Outputs the entity and entity ID
 |

**
Count
**
 |
Integer
 |
Outputs the current of entities
 |

**
Done
**
 |
Integer
 |
Triggered when all entities have been found, with the total count returned
 |

##
GetEntitiesInBoxByClass

Used to find and return all entities assigned to the classes that are defined AABB box.

[Image: /docs/static/attachments/29687847]

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
Start
**
 |
Any
 |
Triggers the node
 |

**
Next
**
 |
Any
 |
Gets the next entity found
 |

**
Limit
**
 |
Integer
 |
Limits how many entities are returned
 |

**
Immediate
**
 |
Any
 |
Iterates immediately through the results
 |

**
ClassName
**
 |
Integer
 |
Specify the Class name.
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
EntityId
**
 |
Any
 |
Outputs the entity and entity ID
 |

**
Count
**
 |
Integer
 |
Outputs the current of entities
 |

**
Done
**
 |
Integer
 |
Triggered when all entities have been found, with the total count returned
 |

##
GetEntitiesInSphere

Used to find and return all entities within the defined sphere volume.

[Image: /docs/static/attachments/29687846]

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
Start
**
 |
Any
 |
Triggers the node
 |

**
Next
**
 |
Any
 |
Gets the next entity found
 |

**
Limit
**
 |
Integer
 |
Limits how many entities are returned
 |

**
Immediate
**
 |
Boolean
 |
Iterates immediately through the results
 |

**
Type
**
 |
Integer
 |
Type of entity to iterate
 |

**
Center
**
 |
Vec3
 |
Center of the sphere
 |

**
Radius
**
 |
Float
 |
Distance from the center of the sphere to check for entities
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
EntityId
**
 |
Any
 |
Outputs the entity and entity ID
 |

**
Count
**
 |
Integer
 |
Outputs the current of entities
 |

**
Done
**
 |
Integer
 |
Triggered when all entities have been found, with the total count returned
 |

[#getentities](
GetEntities
)
[#getentitiesinarea](
GetEntitiesInArea
)
[#getentitiesinbox](
GetEntitiesInBox
)
[#getentitiesinboxbyclass](
GetEntitiesInBoxByClass
)
[#getentitiesinsphere](
GetEntitiesInSphere
)
