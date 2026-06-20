# Creating a Thread

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/23306433
- Page ID: 23306433
- Breadcrumb: CRYENGINE Engine Code > Engine Modules > CrySystem > Threading > Creating a Thread
- Parent: Threading

## Content

## Creating a Thread

To create a thread you will need to:

#### 1. Register the thread: (optional)

Locate your game's *<your_game_asset_folder>/config/game.thread_config*

```
<ThreadConfig>
<Platform name="PC_Common">
...
<Thread name ="FooThread" Affinity="5" Priority="Normal" StackSizeKB="32"/>
...
</Platform>
...
</ThreadConfig>
```

#### 2. Creating a class inheriting from IThread:

Note: If you skipped step 1, the default configuration of the given platform for your thread will be used.

```
#include <IThreadManager.h>

struct SMyThread : public IThread
{
SMyThread()
: m_bStop(false)
{
}

// Once the thread is up and running it will enter this method
virtual void ThreadEntry()
{
while (!m_bStop)
{
// Do work ... your code
}

// On return, thread dies
}

// Signal the thread to stop working
void SignalStopWork()
{
m_bStop = true;
}
volatile bool m_bStop; // Member variable to signal thread to break out of work loop
};
```

#### 3. Spawn the thread in code:

```
SFooThread* pFooThread = new SFooThread();
if (!gEnv->pThreadManager->SpawnThread(pFooThread , "FooThread"))
{
// your failure handle code
delete pFooThread;
CryFatalError(...);
}

m_pMyThread = pFooThread; // Store thread for later access
```
