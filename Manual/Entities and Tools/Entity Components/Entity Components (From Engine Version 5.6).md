# Entity Components (From Engine Version 5.6)

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/44966029
- Page ID: 44966029
- Breadcrumb: Entities and Tools > Entity Components > Entity Components (From Engine Version 5.6)
- Parent: Entity Components

## Child Pages

- [AI Components](Entity%20Components%20(From%20Engine%20Version%205.6)/AI%20Components.md)
- [Audio Components](Entity%20Components%20(From%20Engine%20Version%205.6)/Audio%20Components.md)
- [Cameras Components](Entity%20Components%20(From%20Engine%20Version%205.6)/Cameras%20Components.md)
- [Debug Components](Entity%20Components%20(From%20Engine%20Version%205.6)/Debug%20Components.md)
- [Effects Components](Entity%20Components%20(From%20Engine%20Version%205.6)/Effects%20Components.md)
- [Geometry Components](Entity%20Components%20(From%20Engine%20Version%205.6)/Geometry%20Components.md)
- [Light Components](Entity%20Components%20(From%20Engine%20Version%205.6)/Light%20Components.md)
- [Physics Components](Entity%20Components%20(From%20Engine%20Version%205.6)/Physics%20Components.md)
- [Physics Constraint Components](Entity%20Components%20(From%20Engine%20Version%205.6)/Physics%20Constraint%20Components.md)
- [Sensor Volume](Entity%20Components%20(From%20Engine%20Version%205.6)/Sensor%20Volume.md)
- [UQS Component](Entity%20Components%20(From%20Engine%20Version%205.6)/UQS%20Component.md)
- [Utilities Components](Entity%20Components%20(From%20Engine%20Version%205.6)/Utilities%20Components.md)

## Content

##
Overview

The Entity Component system removes the need for CRYENGINE game code to expose and manage Entities within a scene. Furthermore, the system has been designed to provide a modular and an intuitive way for Developers to construct games, both at a system and at an Entity level.

The interaction model (within the Sandbox Editor) allows Developers to create empty (blank) Entity containers which in turn house the advanced game logic all wrapped into specific Components. Some examples of the Components are: Mesh, Lights, Constraints and even Character Controllers. With these types of Components users can develop prefabs that can be placed by Level Designers throughout a game for standardization.

The Components panel contains all of the available Components that can be applied to an Entity. This article details the individual settings for each of the Components.

![Image](https://www.cryengine.com/docs/static/attachments/44967981)

When these Entity Components have been applied to an Entity, a new subsection appears in the Properties of that Entity:

![Image](https://www.cryengine.com/docs/static/attachments/44966031)

It can be removed from the entity by clicking the button in the top-right corner and choosing
**
Remove
**
.

##
Transformation

Many of the components have a Transform setting. This allows their position and orientation to be offset from the entity they are attached to, while still following it.

Setting
 |
Description
 |

**
Translation
**
 |
The positional offset in relation to the entity - for example a value of 0,0,1 will mean an offset of one unit upwards (Z axis).
 |

**
Rotation
**
 |
The rotation offset in relation to the entity.
 |

**
Scale
**
 |
The scale offset in relation to the entity. The linking symbol locks the scaling so that the values are relative to each other. For e.g. a value of 1,2,3, scaled by 2x would result in 2,4,6. (if unlocked then the scaling cannot be guaranteed).
 |

##
In This Section
