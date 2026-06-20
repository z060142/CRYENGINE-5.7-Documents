# Sensor Volume

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/44966035
- Page ID: 44966035
- Breadcrumb: Entities and Tools > Entity Components > Entity Components (From Engine Version 5.6) > Sensor Volume
- Parent: Entity Components (From Engine Version 5.6)

## Content

The Sensor Volume component can be used as a trigger. Whenever another Sensor Volume with specific Tags hits or passes through the current Sensor Volume, an event trigger can be executed.

For example, it can be used to create a door trigger that whenever a player walks into the Sensor Volume, the door would open or close.

Setting

 |
Description

 |

**
Shape
**
 |
Defines if the Sensor Volume is a box or a sphere in shape.

Setting

 |
Description

 |

**
Box
**
 |

-
**
Size -

**
Determines the size of the box shaped Sensor Volume.
 |

**
Sphere
**
 |

-
**
Radius -

**
Determines the radius of the sphere shaped Sensor Volume.
 |

 |

**
Tags
**
 |
List of Tags that can be used to define a Sensor Volume's
**
Attribute
**
, or if it should act as a
**
Listener
**
.

Option

 |
Description

 |

**
Attribute
**
 |
Tags that act as a label for a Sensor Volume. When in contact with a Listener with the same tags, specific events can be triggered.
 |

**
Listener
**
 |
Determines the attribute tags that the volume needs to listen for. If another Sensor Volume with the specific tag as an Attribute makes contact with the current Sensor Volume, an event can be triggered.

For example, it can be used in a case where you set a campfire and you only want to listen to entities that are flammable. You can also have multiple Listeners tags or none, depending on whether you want to trigger an event or not.

 |

There are six different tags in total that can be used in a Sensor Volume:

-
**
Player
**

-
**
Default
**

-
**
Flammable
**

-
**
Trigger
**

-
**
Interactive
**

-
**
Flame
**
 |

For more information about how to set up a Sensor Volume, please refer to
[Sensor Volume Component](../../../Tutorials/Game%20and%20Level%20Design/Entity%20Component%20Tutorials/Tutorial%20-%20SensorVolume%20Component.md)
 use case page.
