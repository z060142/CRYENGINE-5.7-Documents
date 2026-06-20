# ScriptBind_Physics

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/23306603
- Page ID: 23306603
- Breadcrumb: CRYENGINE API Reference > ScriptBind Reference > CRYENGINE Functions > ScriptBind_Physics
- Parent: CRYENGINE Functions

## Content

##
SimulateExplosion

  Simulate physical explosion. Does not apply any game related explosion damages, this function only apply physical forces. The parameters are passed as a table containing the elements described below.

```

`
Physics.SimulateExplosion( explosionParams )
`

```

Parameter
 |
Description
 |

pos
 |
Explosion epicenter position.
 |

radius
 |
Explosion radius.
 |

direction
 |
Explosion impulse direction.
 |

impulse_pos
 |
Explosion impulse position (Can be different from explosion epicenter).
 |

impulse_presure
 |
Explosion impulse presur at radius distance from epicenter.
 |

rmin
 |
Explosion minimal radius, at this radius full pressure is applied.
 |

rmax
 |
Explosion maximal radius, at this radius impulse pressure will be reaching zero.
 |

hole_size
 |
Size of the explosion hole to create in breakable objects.
 |

##
RegisterExplosionShape

  Register a new explosion shape from the static geometry. Does not apply any game related explosion damages, this function only apply physical forces.

```

`
Physics.RegisterExplosionShape( sGeometryFile, fSize, nMaterialId, fProbability, sSplintersFile, fSplintersOffset, sSplintersCloudEffect )
`

```

Parameter
 |
Description
 |

sGeometryFile
 |
Static geometry file name (CGF).
 |

fSize
 |
Scale for the static geometry.
 |

nMaterialId
 |
ID of the breakable material to apply this shape on.
 |

fProbability
 |
Preference ratio of using this shape then other registered shape.
 |

sSplintersFile
 |
additional non-physicalized splinters cgf to place on cut surfaces.
 |

fSplintersOffset
 |
the lower splinters piece wrt to the upper one.
 |

sSplintersCloudEffect
 |
particle effect when the splinters constraint breaks.
 |

##
RegisterExplosionCrack

 Register a new crack for breakable object.

```

`
Physics.RegisterExplosionCrack( sGeometryFile, int nMaterialId )
`

```

Parameter
 |
Description
 |

sGeometryFile
 |
Static geometry file name fro the crack (CGF).
 |

nMaterialId
 |
ID of the breakable material to apply this crack on.
 |

##
RayWorldIntersection

 Check if ray segment from src to dst intersect anything.

```

`
Physics.RayWorldIntersection( vPos, vDir, nMaxHits, iEntTypes [, skipEntityId1 [, skipEntityId2]] )
`

```

Parameter
 |
Description
 |

vPos
 |
Ray origin point.
 |

vDir
 |
Ray direction.
 |

nMaxHits
 |
Max number of hits to return, sorted in nearest to farest order.
 |

iEntTypes
 |
Physical Entity types bitmask, ray will only intersect with entities specified by this mask (ent_all,...).
 |

skipEntityId1
 |
(optional) Entity id to skip when checking for intersection.
 |

skipEntityId2
 |
(optional) Entity id to skip when checking for intersection.
 |

##
RayTraceCheck

 Check if ray segment from src to dst intersect anything.

```

`
Physics.RayTraceCheck( src, dst, skipEntityId1, skipEntityId2 )
`

```

Parameter
 |
Description
 |

src
 |
Ray segment origin point.
 |

dst
 |
Ray segment end point.
 |

skipEntityId1
 |
Entity id to skip when checking for intersection.
 |

skipEntityId2
 |
Entity id to skip when checking for intersection.
 |

##
SamplePhysEnvironment

 Find physical entities touched by a sphere.

```

`
Physics.SamplePhysEnvironment( pt, r [, objtypes] )
`

```

Parameter
 |
Description
 |

pt
 |
center of sphere.
 |

r
 |
radius of sphere.
 |

objtypes
 |
(optional) physics entity types.
 |
