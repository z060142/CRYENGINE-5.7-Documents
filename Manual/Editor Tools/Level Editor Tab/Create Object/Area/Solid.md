# Solid

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/36869905
- Page ID: 36869905
- Breadcrumb: Editor Tools > Level Editor Tab > Create Object > Area > Solid
- Parent: Area

## Child Pages

- [Using Area Solid with Audio Entities](Solid/Using Area Solid with Audio Entities.md)

## Content

##
Overview

The Area Solid is for defining a complex range of sound obstructions with the Designer Tool.

[Image: /docs/static/attachments/44966493]

##
Properties

Property

 |
Description

 |

**
Inner Fade Distance
**

 |
This value (specified in meters) determines how far an ambience sound can blend into the shape with higher priority.

 |

**
Area Id
**

 |
Sets up the ID of the area, so areas with another ID can overlap.

 |

**
Fade In Zone
**

 |
Specifies in meters how big the zone around the box is that is used to fade in the effect attached to the box. Only when the player is inside the box the effect is rendered at 100%, at the beginning of the Fade In Zone it's rendered at 0%.

 |

**
Group Id
**

 |
Sets up the Group ID of the area, so areas with another group ID can overlap.

 |

**
Priority
**

 |
Defines the Priority so areas with a higher priority will be processed first.

 |

**
Filled
**

 |
Just for visibility in the editor this option defines if the area should be rendered as filled or not.

 |

**
Area
**

 |
Opens the
[/docs/static/engines/cryengine-5/categories/23756816/pages/25534693](
Designer Tool
)
 which can be used to edit the shape of the Area Solid
when
**
Edit
**
 button is clicked.

 |

When editing a shape or area, it is possible to snap a vertex to terrain or physicalized objects using
**
Ctrl + Shift + LMB
**
.

This is true for all Area objects, except Occluders.
