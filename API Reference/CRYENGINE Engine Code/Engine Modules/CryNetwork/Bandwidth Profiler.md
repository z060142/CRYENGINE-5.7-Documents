# Bandwidth Profiler

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/23306396
- Page ID: 23306396
- Breadcrumb: CRYENGINE Engine Code > Engine Modules > CryNetwork > Bandwidth Profiler
- Parent: CryNetwork

## Content

##
Overview

The Bandwidth Profiler is a tool that enables tracking of network serialization calls from CryAction and CryGame to track estimated usage of bandwidth from game objects.

It presently tracks all calls to NetSerialise and DispatchRMI, grouping calls by class type (e.g. player, game rules) and provides functionality for budgeting entries (e.g. an entry must not exceed 256 k/bits).

##
Usage

Any file looking to use the profiler needs to include INetwork.h, this provides the interface.

Profiling is started by calling NET_PROFILE_BEGIN and terminated by NET_PROFILE_END. NET_PROFILE_BEGIN takes two parameters, a name for the profile entry and a bool to denote if this is a read or write call. At present only write calls are measured.

NET_PROFILE_SCOPE can also be used to initiate profiling and will automatically end the profiling when it goes out of scope. It takes the same parameters as NET_PROFILE_BEGIN.

Additionally, there is NET_PROFILE_BEGIN_BUDGET and NET_PROFILE_SCOPE_BUDGET. These take a third parameter that specifies a bandwidth budget for that entry in kilobits. At present this value is tested against the estimated worst case send for that entry and will display a warning to the screen if this is exceeded.

When profiling RMI's, there is NET_PROFILE_BEGIN_RMI and NET_PROFILE_SCOPE_RMI. Presently, all known RMI calls are captured and logged accordingly at a high level; further break down (i.e. individual SerialiseWith calls) could be undertaken using these macros if desired.

##
Logging

Net Profile is capable of logging to two output files if the appropriate cvars are enabled.

-
**
net_profile_logging
**
 is used for logging per frame stats to net_profile.log. The file name can be changed by setting the cvar net_profile_logname appropriately. Log files created here contain a flat view of the data (root and its children only), and a complete breakdown of the hierarchy, showing all nodes and appropriate data.

-
**
net_profile_budget_logging
**
 is used to dump the current profile hierarchy to net_profile_budget.log if the budget of an entry is exceeded. The log name can be changed by setting the value of net_profile_budget_logname.
Log files include the following categories:

Category

 |
Description

 |

**
calls
**

 |
number of times the entry was called.

 |

**
bits
**

 |
number of bits written within a second, for rmi's this is the size of 1 rmi to 1 channel, for net serialises, this is the number of bits written to 1 channel over a second.

 |

**
written
**

 |
kilobits written in a second.

 |

**
sent
**

 |
estimated kilobits sent in a second for number of connected clients.

 |

**
worst
**

 |
estimated worst send rate, uses net_profile_worst_num_channels to calculate this.

 |

**
heir
**

 |
percentage of parent bandwidth the entry took.

 |

**
self
**

 |
percentage of overall bandwidth the entry took.

 |

##
Restrictions

Net Profile can only be used with CryNetwork, CryAction and CryGame at this time.

##
CVars

-
net_profile_logname - log name for net profiler.

-
net_profile_logging - enable/disable logging.

-
net_profile_budget_logname - exceeded budget log name for net profiler.

-
net_profile_budget_logging - enable/disable budget logging.

-
net_profile_worst_num_channels - maximum number of channels expected to connect.

-
net_profile_root_budget - maximum budget for root node.
