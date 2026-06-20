# Items Entities

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/29796933
- Page ID: 29796933
- Breadcrumb: Editor Tools > Level Editor Tab > Create Object > Legacy Entities > Items Entities
- Parent: Legacy Entities

## Content

##
Overview

The item entities are weapon and equipment objects that the player or enemy can pickup and use. They are based on game scripts and in order to add more items, you need to write new scripts.

The item entities can be found in
**
Create Object → Legacy Entities → Items
**

##
Item Properties

The properties of Item Entities are all the same.

[Image: /docs/static/attachments/56000545]

**
Property
**

 |
**
Description
**

 |

**
AutoPickup
**

 |
**
DEPRECATED -
**
 Specify if the object should be picked up automatically if the player walks over the object.

 |

**
HitPoints
**

 |
Specifies the hitpoints, or health, of the object.

 |

**
initialSetup
**

 |
Specifies initial setup parameters.

 |

**
Mounted
**

 |
Specifies if a gun is mounted.

 |

**
Physics
**

 |
Specifies if physics is applied to the object.
**
None
**
,
**
Rigid
**
 and
**
Static
**
 are available.

 |

**
Pickable
**

 |
Specifies if the object can be picked up.

 |

**
SmartObjectClass
**

 |
Specifies the smart object type of the object.

 |

**
SpecialSelect
**

 |
The weapon will play an alternative selection animation when you pick it up for the first time.

 |

**
Useable
**

 |
Specifies if the object is usable.

 |

**
Respawn
**

 |
 |

**
Respawn
**

 |
Specifies if the object will respawn once destroyed or picked up.

 |

**
Timer
**

 |
Specifies the time, in seconds, the object takes to respawn after being picked up.

 |

**
Unique
**

 |
Specifies if the object is unique.

 |

##
AmmoCrate

The Ammo Crate entity can be used to refill ammo of particular categories. It has additional functionality for limited number of uses and whether to give grenades.

There is a multiplayer specific version of this entity here:
[/docs/static/engines/cryengine-5/categories/23756816/pages/29796939](
AmmoCrateMP
)

**
Property
**

 |
**
Description
**

 |

**
Ammo0-4Recharges

**

 |
Model to be used for the different stages of use. Typically this would be less ammunition visible in the box per use.

 |

**
BoxModel
**

 |
Model to be used for the box which encases the ammunition.

 |

**
numOfRecharges
**

 |
How many uses allowed on this entity.

 |

**
Usable
**

 |
See
[/docs/static/engines/cryengine-5/categories/23756816/pages/29796951](
Common Entity Parameters
)
.

 |

**
UseMessage
**

 |
See
[/docs/static/engines/cryengine-5/categories/23756816/pages/29796951](
Common Entity Parameters
)
.

 |

Ammo

 |

 |

**
AmmoCategory
**

 |
Each
[/docs/static/engines/cryengine-3/categories/1638401/pages/1933328#WeaponScripts-Ammo](
ammunition script
)
 should define the "ammo_category" that it should be part of. The most commonly used is "Regular".

You can use this category type to define which ammo types are given upon use of this entity.

 |

**
FragGrenades
**

 |
How many frag grenades to give on use.

 |

[#item-properties](
Item Properties
)
[#ammocrate](
AmmoCrate
)
