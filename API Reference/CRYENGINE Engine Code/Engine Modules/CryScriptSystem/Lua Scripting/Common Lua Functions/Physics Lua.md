# Physics Lua

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/23306628
- Page ID: 23306628
- Breadcrumb: CRYENGINE Engine Code > Engine Modules > CryScriptSystem > Lua Scripting > Common Lua Functions > Physics Lua
- Parent: Common Lua Functions

## Content

##
Registering explosion and crack shapes

Commonly used to register new explosion and crack shapes in the physics engine by using 2 functions from the Lua global
**
Physics
**
.

-
File location:
`
Game/Scripts/physics.lua
`

-
Loaded from:
`
Game/Scripts/main.lua
`

##
Functions

-
[/docs/static/engines/cryengine-5/categories/23756813/pages/23306628#PhysicsLua-RegisterExplosionShape](
#RegisterExplosionShape
)

-
[/docs/static/engines/cryengine-5/categories/23756813/pages/23306628#PhysicsLua-RegisterExplosionCrack](
#RegisterExplosionCrack
)

##
Physics.RegisterExplosionShape( sGeometryFile, fSize, BreakId, fProbability, sSplintersfile, fSplintersOffset, sSplintersCloudEffect )

Registers a boolean carving shape for breakable objects in the physics engine.

**
Parameters
**

 |
**
Description
**

 |

sGeometryFile

 |
boolean shape cgf filename

 |

fSize

 |
shape's 'characteristic' size

 |

BreakId

 |
breakability index (0-based), used to identify the breakable material

 |

fProbability

 |
shape's relative probability – when several shapes with the same size appear as candidates for carving, they are selected with these relative probabilities

 |

sSplintersfile

 |
splinters cgf filename, used for trees to add splinters at the place where it broke

 |

fSplintersOffset

 |
helper size offset for the splinters

 |

sSplintersCloudEffect

 |
splinters particle fx name – is played when a splinters-based constraint breaks and splinters disappear

 |

##
Physics.RegisterExplosionShape( sGeometryFile, BreakId )

Registers a new explosion crack for breakable objects in the physics engine.

**
Parameters
**

 |
**
Description
**

 |

sGeometryFile

 |
crack shape cgf name (must have 3 helpers that mark the corners, named "1","2" and "3")

 |

BreakId

 |
breakability index (same meaning as for the explosion shapes)

 |
