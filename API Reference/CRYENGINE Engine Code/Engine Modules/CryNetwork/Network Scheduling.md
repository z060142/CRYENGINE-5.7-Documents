# Network Scheduling

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/23306391
- Page ID: 23306391
- Breadcrumb: CRYENGINE Engine Code > Engine Modules > CryNetwork > Network Scheduling
- Parent: CryNetwork

## Content

##
Overview

Network Scheduling controls the delivery of network data is done based on these priorities + available space in the packet.

##
Defining scheduling types

The scheduling types are defined inside an XML that is loaded during engine startup. This file should have this path:
`
Game/Scripts/Network/Scheduler.xml
`

Here is an example of a type:

```

`
<Group name="auth" priority="15" latency="2">

`

```

This define a type named auth. It has a base priority of 15. The latency should be of 2 seconds, meaning the message can sit around in the queue for 2 seconds before its priority is artificially raised to attempt to force it out onto the network.

The mapping of entity class and scheduling types are set inside another XML file. This file should have this path:
`
Game/Scripts/Network/EntityScheduler.xml
`

##
Priority Value

Scheduling in the network is driven by priorities. 16 – 0, with 16 as the highest (read most important). Priority values are exponential. The priority 1 is twice as important as priority 0, priority 2 is twice as important as priority 1, etc.

##
Adjusting the priority

Note that the priority is a base priority. It can be adjusted via a number of optional values.

Here are some examples.

```

`
normalDistance="nnn" close="ccc" far="fff"

`

```

-
nnn is distance where base priority applies.

```

`
Foi="aaa" front="fff" back="bbb"

`

```

-
aaa = angle of incidence with camera (within angle front priority boost is applied – outside back priority reduction is applied).

-
fff = maximum amount of priority to boost.

-
bbb = maximum amount of priority reduction.

```

`
Drawn="n"

`

```

-
If n == 1 then after all other considerations, if the renderer has decided the object should be culled, its priority is reduced to 0.

##
Pulse

A set of programmer pulses can be defined. This is useful to temporarily increase the network update priority of a game object from within code because of an internal state change.

Here is an example:

```

`
<Pulse name="bump" bump="3" decayTime="2">

`

```

-
Bump gives the priority a boost (of 3 in this example), which the network slowly reduces (over 2 seconds in this example).
See the
*
CGameObject::Pulse()
*
 function for more information.
