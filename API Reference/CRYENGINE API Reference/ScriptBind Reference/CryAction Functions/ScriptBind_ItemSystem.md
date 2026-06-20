# ScriptBind_ItemSystem

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/23306611
- Page ID: 23306611
- Breadcrumb: CRYENGINE API Reference > ScriptBind Reference > CryAction Functions > ScriptBind_ItemSystem
- Parent: CryAction Functions

## Content

##
Reset

 Resets the item system.

```

`
ItemSystem.Reset()
`

```

##
GiveItem

Gives the specified item.

```

`
ItemSystem.GiveItem( itemName )
`

```

Parameter
 |
Description
 |

itemName
 |
Item name.
 |

##
GiveItemPack

Gives the item pack to the specified actor.

```

`
ItemSystem.GiveItemPack( actorId, packName )
`

```

Parameter
 |
Description
 |

actorId
 |
Actor identifier.
 |

packName
 |
Pack name.
 |

##
GetPackPrimaryItem

Gets the primary item of the specified pack.

```

`
ItemSystem.GetPackPrimaryItem( packName )
`

```

Parameter
 |
Description
 |

packName
 |
Pack name.
 |

##
GetPackNumItems

 Get the number of items in the specified pack.

```

`
ItemSystem.GetPackNumItems()
`

```

Parameter
 |
Description
 |

packName
 |
Pack name.
 |

##
GetPackItemByIndex

Gets a pack item from its index.

```

`
ItemSystem.GetPackItemByIndex( packName, index )
`

```

Parameter
 |
Description
 |

packName
 |
Pack name.
 |

index
 |
Pack index.
 |

##
SetActorItem

Sets an actor item.

```

`
ItemSystem.SetActorItem( actorId, itemId, keepHistory )
`

```

Parameter
 |
Description
 |

actorId
 |
Actor identifier.
 |

itemId
 |
Item identifier.
 |

keepHistory
 |
True to keep history, false otherwise.
 |

##
SetActorItemByName

Sets an actor item by name.

```

`
ItemSystem.SetActorItemByName( actorId, name, keepHistory )
`

```

Parameter
 |
Description
 |

actorId
 |
Actor identifier.
 |

name
 |
Actor item name.
 |

keepHistory
 |
True to keep history, false otherwise.
 |

##
SerializePlayerLTLInfo

Serializes player LTL info.

```

`
ItemSystem.SerializePlayerLTLInfo( reading )
`

```

Parameter
 |
Description
 |

reading
 |
Boolean value.
 |
