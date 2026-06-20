# Item System

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/24283702
- Page ID: 24283702
- Breadcrumb: CRYENGINE Engine Code > Engine Modules > CryAction > Item System
- Parent: CryAction

## Content

##
Overview

The Item System manages all the items defined through XML definitions in your game folder. Every interact-able Item in your game should be based on a CItem and managed through the ItemSystem in CryAction. Once initialized, Items can be assigned to a player inventory, dropped or bundled through the Equipment Manager.

##
Initialization

The Item System is initialized during the initialization of CryAction. It will register a ILevelSystemListener to automatically reset the items on level load and precache the geometry and sound in time.

Constant values:

name
 |
value
 |

DEFAULT_ITEM_SCRIPT
 |
"Scripts/Entities/Items/Item.lua"
 |

DEFAULT_ITEM_CRTEATEFUNC
 |
"
CreateItemTable"
 |

##
Listeners

The Item System takes care of the following events:

IItemSystemListener
 |

OnSetActorItem
 |

OnDropActorItem
 |

OnSetActorAccessory
 |

OnDropActorAccessory
 |

IEquipmentManager
 |

OnBeginGiveEquipmentPack
 |

OnEndGiveEquipmentPack
 |
