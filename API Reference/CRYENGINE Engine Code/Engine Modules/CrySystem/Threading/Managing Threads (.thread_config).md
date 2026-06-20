# Managing Threads (.thread_config)

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/23306434
- Page ID: 23306434
- Breadcrumb: CRYENGINE Engine Code > Engine Modules > CrySystem > Threading > Managing Threads (.thread_config)
- Parent: Threading

## Content

##
Overview

Creating a thread on various platforms with all the right flags can be a tedious task. The ThreadManager offers a simple interface to create and manage threads. Internally it uses the ThreadConfigurationManager to offer a data driven solution for managing your various threads characteristics. It also allows for tweaking your threads without the need to re-compile.

##
Loading a .thread_config file at runtime

Once you have create your
*
thread_config
*
 you will need to load it at runtime.

```

`
#include "ThreadConfigManager.h"

void Foo()
{
  ...
  // Load thread config
  gEnv->pThreadManager->GetThreadConfigManager()->LoadConfig("config/my_game.thread_config");
  ...
}
`

```

##
Overwriting thread configurations

The ThreadConfigurationManager allows loading of multiple
*
thread_config
*
 files. It is important to be aware of the fact that later loaded
*
thread_config
*
files will override a thread's characteristics if it was already defined by a previously loaded
*
thread_config
*
 file. The engine will load engine specific thread_config files prior to the game code.

Load order:

-
engine_core.thread_config

-
engine_sandbox.thread_config

-
<your game's>.thread_config (controlled by you via LoadConfig() invocation)
1. and 2. will be loaded in CSystem::Init() just after the Engine folders have been initialized.

It is recommend to load your <your game's>.thread_config in CGameStartup::Init to avoid the case where you try to initialize a thread without having loaded it's configuration yet.

##
Creating a .thread_config file

The
*
thread_config
*
 should be created within the engine/game visible environment path. e.g. in your
*
Assets
*
 folder/pak file.

```

`
<ThreadConfig>
  <Platform name="TargetPlatform">
    <ThreadDefault Affinity="-1" Priority="Normal" StackSizeKB="32"/>

    <Thread name ="Bar" Affinity="-1" Priority="Normal" StackSizeKB="128"/>
    <Thread name ="Foo" Affinity="4,5" Priority="Normal"/>
    ...
  </Platform>

  <Platform name="OtherTargetPlatform">
    ...
   </Platform>

</ThreadConfig>
`

```

The following XML nodes can be used :

XML Nodes
 |

 |

 |
XML Node keys
 |

<ThreadConfig>
 |
- XML root node
 |

 |

 |

<Platform>
 |
- Platform target for child nodes
 |

 |
name
 |

<Thread>
 |
- Thread characteristics for platform
 |

 |
name, Affitinity, Priority, StackSizeKB,
DisablePriorityBoost
 |

<ThreadDefault>
 |
- "Default"
thread
characteristics for platform
 |

 |
name, Affitinity, Priority, StackSizeKB,
DisablePriorityBoost

 |

<platform name"">
The following platform names are supported:

Platform name
 |

PC
 |

LINUX
 |

DURANGO
 |

ORBIS
 |

ANDROID
 |

MAC
 |

##
Platforms with unknown logical core count:

Sometimes you run into the situation where you want to change thread group characteristics such as their affinity, depending on the number of cores available.

The
ThreadConfigurationManager allows you to post-fix each platform name with the "_Common" as well as "_<AvailableCoreCount>"

**
"_Common":

**
*
        e.g.
*
<Platform name="PC_Common">

Defines thread characteristics
shared
 by all
AvailableCoreCount groups. Each
AvailableCoreCount may override each thread's characteristic in its own section. This minimizes the need to rewrite the same thread characterstics for each group.

**
"_<AvailableCoreCount>

**
*
        e.g.
*
<Platform name="PC_8">

Defines an
AvailableCoreCount group. If the logical core count is 8 for example, the
ThreadConfigurationManager will first search for the
"PC_8" setup and load its thread configurations. If it cannot find such a setup it will search for the next lower logical core group.

```

`
<ThreadConfig>
  <!-- ============ -->
  <!-- === PC_Common === -->
  <!-- ============ -->
  <Platform name="PC_Common">
    <ThreadDefault Affinity="-1" Priority="Normal" StackSizeKB="32"/>
    <Thread name ="Foo" Priority="Normal"/>
  </Platform>

  <!-- ============ -->
  <!-- === PC_4 === -->
  <!-- ============ -->
  <Platform name="PC_4">
    <!-- Extend for 4 core specific machines. May override Common settings -->
    <Thread name ="Foo_1" Affinity="0" Priority="Normal"/>
    <Thread name ="Foo_2" Affinity="0" Priority="Normal"/>
    <Thread name ="Foo_3" Affinity="1" Priority="Normal"/>
    <Thread name ="Foo_4" Affinity="1" Priority="Normal"/>
  </Platform>

  <!-- ============ -->
  <!-- === PC_8 === -->
  <!-- ============ -->
  <Platform name="PC_8">
    <!-- Extend for 8 core specific machines. May override Common settings -->
    <Thread name ="Foo_1" Affinity="0" Priority="Normal"/>
    <Thread name ="Foo_2" Affinity="0" Priority="Normal"/>
    <Thread name ="Foo_3" Affinity="1" Priority="Normal"/>
    <Thread name ="Foo_4" Affinity="1" Priority="Normal"/>
    <Thread name ="Foo_5" Affinity="2" Priority="Normal"/>
    <Thread name ="Foo_6" Affinity="2" Priority="Normal"/>
    <Thread name ="Foo_7" Affinity="3" Priority="Normal"/>
    <Thread name ="Foo_8" Affinity="3" Priority="Normal"/>
  </Platform>
</ThreadConfig>
`

```

<Thread name ="">

##
Wildecard character "*":

The "Thread name" XML node allows the usage of wild card characters. This is useful if you want to create any number of threads using the same settings.

We could rewrite the example above;
*
"Example: PC with logical core count of 4 and 8 defined"
*
 which requires the manual setup of each thread for the available core count in a more generalistic way where threads are grouped into affinity groups.

**
Runtime code:
**

```

`
// Create arbitrary number of threads and distribute them on cores evently
int nMaxCoreCount = GetCoreCount();
for (int i = 0; i < nNumThreadsToSpawn; ++i)
{
    int nAffinityGroup= i % nMaxCoreCount; // stay within the bounds of available cores

  SFooThread* pFooThread = new SFooThread();
  if (!gEnv->pThreadManager->SpawnThread(pFooThread , "Foo_A%i_%i", nAffinityGroup, i))
  {
      // Handle error
  }

  // Store thread for later access
}
`

```

**
.thread_config
**

```

`
<ThreadConfig>
  <!-- ============ -->
  <!-- === PC_Common === -->
  <!-- ============ -->
  <Platform name="PC_Common">
    <ThreadDefault Affinity="-1" Priority="Normal" StackSizeKB="32"/>
    <Thread name ="Foo_A0_*" Affinity="0" Priority="Normal"/>
    <Thread name ="Foo_A1_*" Affinity="1" Priority="Normal"/>
    <Thread name ="Foo_A2_*" Affinity="2" Priority="Normal"/>
    <Thread name ="Foo_A3_*" Affinity="3" Priority="Normal"/>
  </Platform>

  <!-- ============ -->
  <!-- === PC_4 === -->
  <!-- ============ -->
  <Platform name="PC_4">
    <!-- Now empty as all cases are handled by PC_Common section -->
  </Platform>

  <!-- ============ -->
  <!-- === PC_8 === -->
  <!-- ============ -->
  <Platform name="PC_8">
    <!-- Now empty as all cases are handled by PC_Common section -->
  </Platform>
</ThreadConfig>
`

```

**
Node keys:
**

**
Name:
**
 |

 |

"x" (string)
 |
Name of thread
 |

"x*y" (string)
 |
Name of thread with wildcard character e.g. "WorkerThread*" which matches "WorkerThread_0",
"WorkerThread_1", ...
 |

**

**

**
Affinity:
**
(optional)
**
**
 |

 |

"-1"
 |
Put SW thread affinity in the hands of the scheduler -
**
(default)
**
 |

"x"
 |
Run thread on specified core
 |

"x, y, ..."
 |
Run thread on specified cores
 |

"ignore"
 |
Do not touch this value, use whatever the underlying API has set
 |

**
Priority:

**
(optional)
**
**
 |

 |

"idle" :
 |
Use CRYENGINE defined value
 |

"below_normal"
 |
Use
CRYENGINE
defined value
 |

"normal"
 |
Use
CRYENGINE
defined value -

**
(default)
**
 |

"above_normal"
 |
Use
CRYENGINE
CRYENGINE
gine defined value
 |

"highest"
 |
Use
CRYENGINE
defined value
 |

"time_critical"
 |
Use
CRYENGINE
defined value
 |

 |

 |

"x" (number)
 |
User defined thread priority number
 |

"ignore"
 |
Do not touch this value, use whatever the underlying API has set
 |

**
StackSizeKB:
**
(optional)
**
**
 |

 |

"0"
 |
Let platform decide on the stack size -
**
(default)
**
 |

"x"
 |
Create thread with "x" KB of stack size
 |

"ignore"
 |
Do not touch this value, use whatever the underlying API has set
 |

**
DisablePriorityBoost:
**
(optional)
**
**
 |

 |

"true"
 |
Disable priority boosting -
**
(default)
**
 |

"false"
 |
Enable priority boosting
 |

"ignore"
 |
Do not touch this value, use whatever the underlying API has set
 |

<ThreadDefault name="">
Has the same characteristics as the <Thread> XML Node except that it is used for all threads where the name of the thread has not been defined by a <Thread> XML node.

[Loading a .thread_config file at runtime](#loading-a-threadconfig-file-at-runtime)
[Overwriting thread configurations](#overwriting-thread-configurations)
[Creating a .thread_config file](#creating-a-threadconfig-file)
