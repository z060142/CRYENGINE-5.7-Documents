# Cameras Components

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/44966046
- Page ID: 44966046
- Breadcrumb: Entities and Tools > Entity Components > Entity Components (From Engine Version 5.6) > Cameras Components
- Parent: Entity Components (From Engine Version 5.6)

## Content

##
Camera

This represents a camera in the world from which the level can be rendered. Keep in mind that only one camera can be active at the a time.

Entities with Camera components will then show up in the
**
Camera
**
 menu in the
**
Perspective
**
 viewport, under
**
Camera Entity
**
.

Setting
 |
Description
 |

**
Type
**
 |
Setting
 |
Description
 |

**
Default
**
 |
A normal, one-directional camera.
 |

**
Omnidirectional
**
 |
Renders the full 360 view to screen.
 |

 |

**
Active
**
 |
Whether or not this camera should be activated on component creation.
 |

**
Near Plane
**
 |
Sets the distance from the camera that the engine will start rendering from (by default 0.25 meters).
 |

**
Far Plane
**
 |
Sets the distance from the camera that the engine will start rendering to(by default 1024 meters).
 |

**
Field of View
**
 |
The field of view or angle that the camera will render.
 |

##
Roomscale VR Camera

Expose a new Entity Component that allows for easily creating a Roomscale VR camera. This works quite simply, in that all the user has to do is to drag the component into their Schematyc entity, and it'll be activated. Additionally, the component automates asynchronous camera injection, effectively retrieving the headset's coordinates as late as possible to avoid unnecessary lag.

Setting
 |
Description
 |

**
Active
**
 |
Activates the Roomscale VR Camera.
 |

**
Near Plane
**
 |
Determines the minimum distance that the engine will start rendering from. (Example: 0.25 means the engine will render starting at 0.25m fromt he camera and forward)
 |

**
Far Plane
**
 |
Determines the maximum distance that the engine will start rendering from. (Example: 1 means the engine will render up to 1 m from the camera, so after 1m you will not see anything)
 |

[#camera](
Camera
)
[#roomscale-vr-camera](
Roomscale VR Camera
)
