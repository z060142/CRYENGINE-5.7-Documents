# GetEntitiesInBox

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/23306412
- Page ID: 23306412
- Breadcrumb: CRYENGINE Engine Code > Engine Modules > CryPhysics > GetEntitiesInBox
- Parent: CryPhysics

## Content

##
Overview

It's possible to query the physics system to get all the physical objects/entities contained into a specific box volume defined by a minimum and a maximum point using
**
GetEntitiesInBox
**
function

```

`
virtual int GetEntitiesInBox(Vec3 ptmin,Vec3 ptmax, IPhysicalEntity **&pList, int objtypes, int szListPrealloc=0) = 0;
`

```

... as follows:

```

`
IPhysicalEntity** entityList = 0;
int entityCount = gEnv->pPhysicalWorld->GetEntitiesInBox(m_volume.min, m_volume.max, entityList,
      ent_static | ent_terrain | ent_sleeping_rigid | ent_rigid);
`

```

The function
**
GetEntitiesInBox
**
 returns the number of entities found and receives the following parameters:

Parameter

 |
Description

 |

ptmin

 |
Minimum point in the space that defines the desired box volume.

 |

ptmas

 |
Maximum point in the space that defines the desired box volume.

 |

pList

 |
Pointer to a list of objects that will be filled by the function.

 |

objtypes

 |
Types of objects that need to be considered in the query.

 |

szListPrealloc

 |
If specified it's the maximum number of objects contained by the pList array.

 |

The possible object types are described into the header
**
physinterface.h
**
 in the
**
entity_query_flags
**
 enumerators. Some of the possibilities are:

Entity type flag

 |
Description

 |

ent_static

 |
Static entities

 |

ent_terrain

 |
Terrain

 |

ent_sleeping_rigid

 |
Sleeping rigid bodies

 |

ent_rigid

 |
Rigid bodies

 |

...

 |
Others

 |

At this point you can easily iterate through the objects and perform the desired operations

```

`
for (int i = 0; i < entityCount; \++i)
{

   IPhysicalEntity\* entity = entityList[i];

   [...]

   if (entity->GetType() == PE_RIGID)
   {
      [...]
   }

   [...]

}

`

```

The function
uses an internal 2d grid to return entities that have their bounding boxes overlapped with the specified box. The function supports optional sorting of the output list by entity mass (in ascending order). If
*
ent_alloctate_list
*
 is specified, the function allocates memory for the list (the memory can later be freed by a call to
`
pWorld->GetPhysUtils()->DeletePointer
`
). Otherwise, an internal pointer will be returned. One should keep in mind that the physics system uses this pointer in almost all operations that require forming an entity list, thus no such calls should be made when the list is in use (or the list will be invalidated). If calls like this are required and memory allocation is undesired, one can copy the list to a local pre-allocated array before iterating over it. In order to make sure that the entity pointers in the list remain valid while it's accessed,
*
ent_addref_results
*
flag can be set.
