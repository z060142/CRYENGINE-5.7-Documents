# Time Nodes

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/29450636
- Page ID: 29450636
- Breadcrumb: Editor Tools > Flow Graph > Flow Graph Node Reference > Time Nodes
- Parent: Flow Graph Node Reference

## Content

##
Delay

This node will delay passing the signal from [In] to [Out] for the specified number of seconds in [Delay]

##
FrameDelay

This node will delay passing the signal from [In] to [Out] for one frame

##
MeasureTime

Node to measure elapsed time.

##
RandomDelay

This node will delay passing the signal from the [In] to [Out] for a random amount of time in the interval [MinDelay,MaxDelay]

##
RealTime

This node reads your system time and can be used for things such as displaying time on a players watch or synchronizing time of day with real-world time, etc.

##
ServerTime

Reads the server time and reports the current time (seconds or milliseconds) for the specified period.

![Image](https://www.cryengine.com/docs/static/attachments/29688002)

**
Inputs
**

Port
 |
Type
 |
Description
 |

**
Basetime
**
 |
Float
 |
Base time in seconds. The server time output is relative to the base time

Default value: 0

Valid values: 0-100

 |

**
Period
**
 |
Float
 |
Number of seconds that should pass before the timer resets to 0

Default value: 0

Valid values: 0
-100

 |

**
Outputs
**

Port
 |
Type
 |
Description
 |

**
Secs
**
 |
Integer
 |
Current time in seconds, relative to the base time

 |

**
Msecs
**
 |
Integer
 |
Current time in milliseconds, relative to the base time

 |

**
Period
**
 |
Boolean
 |
Triggers the Period output once for each period of time, as specified by the Period input

Valid values: 0=false|1=true

 |

##
Time

Outputs the total number of seconds from the start of the game, ticking once per frame.

![Image](https://www.cryengine.com/docs/static/attachments/29688003)

**
Inputs
**

Port
 |
Type
 |
Description
 |

**
Paused
**
 |
Boolean
 |
Pauses the time output when set to true.

Default value: 0

Valid values:
0=false|1=true

 |

**
Outputs
**

Port
 |
Type
 |
Description
 |

**
seconds
**
 |
Float
 |
Current time in seconds

 |

**
tick
**
 |
Any
 |
Triggers a tick once per frame

 |

##
TimeOfDay

Triggers the TimeOfDay, which is set in the flownode and can change the speed of at which it progresses.

ForceUpdate should be on. Same node can also read out the current TimeOfDay setting.

![Image](https://www.cryengine.com/docs/static/attachments/29688004)

##
TimeOfDayLoadDefinitionFile

Loads a TOD (Time of Day definition file).

##
TimeOfDayTransitionTrigger

Time of Day and sun position transitions.

##
TimeOfDayTrigger

Works as a trigger when a specific time of day has been reached.

##
TimedCounter

Counts a number of ticks specified by 'limit', and then outputs 'finished' with the value the input 'start' had when it was triggered.

##
Timer

Timer node will output count from min to max, ticking at the specified period of time.

[Delay](#delay)
[FrameDelay](#framedelay)
[MeasureTime](#measuretime)
[RandomDelay](#randomdelay)
[RealTime](#realtime)
[ServerTime](#servertime)
[Time](#time)
[TimeOfDay](#timeofday)
[TimeOfDayLoadDefinitionFile](#timeofdayloaddefinitionfile)
[TimeOfDayTransitionTrigger](#timeofdaytransitiontrigger)
[TimeOfDayTrigger](#timeofdaytrigger)
[TimedCounter](#timedcounter)
[Timer](#timer)
