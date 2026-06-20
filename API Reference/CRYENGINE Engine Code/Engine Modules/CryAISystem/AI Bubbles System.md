# AI Bubbles System

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/23306472
- Page ID: 23306472
- Breadcrumb: CRYENGINE Engine Code > Engine Modules > CryAISystem > AI Bubbles System
- Parent: CryAISystem

## Content

##
What is the AI Bubbles System?

The AI Bubbles System wants to be a global hub to collect the AI error messages that needs to be addressed to level designers.

Too many times debugging wrong behavior of any AI agent can take lots of time because it's hard to track down which system is connected with the problem and which cvars needs to be enabled to retrieve the important information.

The solution to this problem is to push important messages into the
**
AI Bubbles System
**
: programmers need to push important messages into the system, and then then the latter will take care of notify to the level designers what's wrong in a specific moment.

##
Different message types

Each message pushed inside the system can be displayed as:

-
Speech Bubble over the AI agent:

[Image: /docs/static/attachments/23461247]

-
Message in the console:

[Image: /docs/static/attachments/23461246]

-
Blocking windows popup with a set of information (agent name, agent position, ...) to allow the designer to understand something is wrong in the normal flow.

[Image: /docs/static/attachments/23461245]
You can specify the type of the message queued in the system when calling the AIQueueBubbleMessage.

This function is defined as:

```

`
bool AIQueueBubbleMessage(const char* messageName, const IAIObject* pAIObject,
  const char* message, uint32 flags);

`

```

Where the different parameters are:

Parameter name

 |
Description

 |

**
messageName
**

 |
It's a string describing the message. This is needed to queue the same message error more than once (The message can be pushed into the system again when it will expire and will be deleted from the queue)

 |

**
pAIObject
**

 |
It's a pointer to the object that is connected to the message

 |

**
message
**

 |
The message that needs to be displayed

 |

**
flags
**

 |
The message type. This value of this variable can be obtained combining the following flags:

-
eBNS_Log

-
eBNS_Balloon

-
eBNS_BlockingPopup
 |

##
CVars to control the system

The following CVars are available to control the AI Bubble System behavior.

CVar name

 |
Description

 |

**
ai_BubblesSystem
**

 |
Enables/disables the AI Bubbles System.

 |

**
ai_BubblesSystemDecayTime
**

 |
Specifies the number of seconds a speech bubble will last on screen before the next message can be drawn.

 |

**
ai_BubblesSystemAlertnessFilter
**

 |
Specifies the alertness level the designer wants to have:

 0 - none

 1 - Only logs in the console

 2 - Only bubbles

 3 - Logs and bubbles

 4 - Only blocking popups

 5 - Blocking popups and logs

 6 - Blocking popups and bubbles

 7 - All notifications

 |

**
ai_BubblesSystemUseDepthTest
**

 |
Specifies if the notification needs to be occluded by the world geometries or not.

 |
\

 |

**
ai_BubblesSystemFontSize
**

 |
Defines the font size for the message displayed in the 3D world.

 |

##
C++ Usage

```

`
AIQueueBubbleMessage("COPStick::Execute PATHFINDER_NOPATH non continuous", pPipeUser, "I cannot find a path.", eBNS_Log|eBNS_Balloon);

`

```

##
Lua Usage

```

`
local entityID = System.GetEntityIdByName("Grunt.AlienGrunt1");
AI.QueueBubbleMessage(entityID,"This is just a test to try the lua connection with the bubble system");

`

```
