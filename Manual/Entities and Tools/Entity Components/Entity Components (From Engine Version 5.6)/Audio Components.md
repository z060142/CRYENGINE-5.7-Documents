# Audio Components

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/44966043
- Page ID: 44966043
- Breadcrumb: Entities and Tools > Entity Components > Entity Components (From Engine Version 5.6) > Audio Components
- Parent: Entity Components (From Engine Version 5.6)

## Content

##
Environment

Attach this to an Area, such as shape, box, solid, sphere, etc, to assign this environment to the Area.

Setting
 |
Description
 |

**
Environment
**
 |
The environment you want to apply (the environment is created and set up in the Audio Controls Editor).
 |

**
FadeDistance
**
 |
Distance between Audio Listener and the Area over which the Environment should fade (in engine units).
 |

##
Listener

Functions similar to a microphone; you listen to the world audio from a Listener position. The most prominent use is to attach it to cameras.

Setting
 |
Description
 |

**
Name
**
 |
Name of the audio listener.
 |

**
Offset
**
 |
Offset of the listener position.
 |

##
Trigger

Barebone Audio Trigger that handles Audio Triggers created in the Audio Controls Editor.

Setting
 |
Description
 |

**
Play
**
 |
Setting
 |
Description
 |

**
AutoPlay
**
 |
Enabled by default. When disabled, the trigger will be executed and stopped immediately after the component has been created.
 |

**
PlayTrigger
**
 |
This trigger is executed when Play is called.
 |

 |

**
Stop
**
 |
Setting
 |
Description
 |

**
Can Stop
**
 |
Enabled by default. Defines if the trigger can be stopped by the Stop Trigger content.
 |

**
Stop trigger
**
 |
Available is
**
Can Stop
**
 is set to
**
Stop
**
. This trigger is executed when Stop is called.
 |

 |

**
Debug
**
 |
Setting
 |
Description
 |

**
Play
**
 |
Executes the PlayTrigger
 |

**
Stop
**
 |
Stops the PlayTrigger if no StopTrigger is assigned - otherwise executes the StopTrigger.
 |

**
Draw PlayTrigger Radius
**
 |
Shows the radius of the PlayTrigger if there is any radius information for the 3D sound.

Not all audio middleware implementations support this; it currently works for Wwise and SDL Mixer.
 |

**
Draw StopTrigger Radius
**
 |
Shows the radius of the StopTrigger if there is any radius information for the 3D sound.

Not all audio middleware implementations support this; it currently works for Wwise and SDL Mixer.
 |

 |

For more information about Play/Stop behavior, please refer to the
[Play/Stop Behavior](../../../Audio/Audio%20Overview/Play%20Stop%20Behavior.md)
 page.

[Environment](#environment)
[Listener](#listener)
[Trigger](#trigger)
