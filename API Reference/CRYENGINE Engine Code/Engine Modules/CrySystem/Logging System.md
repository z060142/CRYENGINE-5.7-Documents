# Logging System

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/23306426
- Page ID: 23306426
- Breadcrumb: CRYENGINE Engine Code > Engine Modules > CrySystem > Logging System
- Parent: CrySystem

## Content

##
CryLog Logging Functionality

Logging in CryENGINE should be done using the following global functions:

-
**
CryLog
**
 (eMessage)

-
**
CryLogAlways
**
 (eAlways)

-
**
CryError
**
 (eError)

-
**
CryWarning
**
 (eWarning)

-
**
CryComment
**
 (eComment)
If more control is required, the
**
ILog
**
 interface can be used directly, e.g:

```

`
gEnv->pLog->LogToFile("value %d",iVal);

`

```

##
Verbosity Level and Coloring

The console variables
**
log_Verbosity
**
 and
**
log_FileVerbosity
**
 enable to suppress logging.

The following table shows how verbosity suppression works and in which color it will show up in the console:

 |
**
verbosity 0
**

 |
**
verbosity 1
**

 |
**
verbosity 2
**

 |
**
verbosity 3
**

 |
**
verbosity 4
**

 |
**
Color in console
**

 |

**
eAlways
**

 |
**
X
**

 |
**
X
**

 |
**
X
**

 |
**
X
**

 |
**
X
**

 |
 |

**
eErrorAlways
**

 |
**
X
**

 |
**
X
**

 |
**
X
**

 |
**
X
**

 |
**
X
**

 |
**
red
**

 |

**
eWarningAlways
**

 |
**
X
**

 |
**
X
**

 |
**
X
**

 |
**
X
**

 |
**
X
**

 |
**
yellow
**

 |

**
eInput
**

 |
**
?
**

 |
**
?
**

 |
**
?
**

 |
**
?
**

 |
**
?
**

 |
 |

**
eInputResponse
**

 |
**
?
**

 |
**
?
**

 |
**
?
**

 |
**
?
**

 |
**
?
**

 |
 |

**
eError
**

 |

 |
**
X
**

 |
**
X
**

 |
**
X
**

 |
**
X
**

 |
**
red
**

 |

**
eWarning
**

 |
-

 |
-

 |
**
X
**

 |
**
X
**

 |
**
X
**

 |
**
yellow
**

 |

**
eMessage
**

 |
-

 |
-

 |

 |
**
X
**

 |
**
X
**

 |
 |

**
eComment
**

 |
-

 |
-

 |
-

 |
-

 |
**
X
**

 |
 |

-
**
X
**
 means message type is logged to console or file

-
**
?
**
 means some special logic is involved

-
**
TIP:
**
 Full logging (to console and file) can be enabled with
**
log_Verbosity 4
**
.

##
Log Files

Sandbox is logging to "Editor.log" while the game uses a file "game.log" by default. Error messages are additionally written to the file "Error.log".

##
Console Variables

**
log_IncludeTime
**

```

Toggles time stamping of log entries.
Usage: log_IncludeTime [0/1/2/3/4/5]
  0=off (default)
  1=current time
  2=relative time
  3=current+relative time
  4=absolute time in seconds since this mode was started
  5=current time+server time

```

**
ai_LogFileVerbosity
**

```

None = 0, progress/errors/warnings = 1, event = 2, comment = 3

```

**
log_Verbosity
**

DUMPTODISK

```

defines the verbosity level for log messages written to console
-1=suppress all logs (including eAlways)
0=suppress all logs(except eAlways)
1=additional errors
2=additional warnings
3=additional messages
4=additional comments

```
