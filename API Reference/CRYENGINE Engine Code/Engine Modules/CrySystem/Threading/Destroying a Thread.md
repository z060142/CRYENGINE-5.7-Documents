# Destroying a Thread

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/24282483
- Page ID: 24282483
- Breadcrumb: CRYENGINE Engine Code > Engine Modules > CrySystem > Threading > Destroying a Thread
- Parent: Threading

## Content

## Destroying a Thread

It is advised to follow the following procedure to shutdown a thread.

```
// Where m_pMyThread pointed object inherits from IThread

// Signal the thread that it should stop
m_pMyThread->SignalStopWork(); // Function implement by you, signaling your thread to exiting IThread::ThreadEntry()

// Wait for the thread to exit IThread::ThreadEntry()
gEnv->pThreadManager->JoinThread(m_pMyThread, eJM_Join);

// Delete shared data
delete m_pMyThread;
m_pMyThread= nullptr;
```

#### 1. Signal the thread that it should stop doing more work

Signal your thread that it should exit by setting some exit condition.

In our example this is done by calling SignalStopWork(). It is important to notice that the signaled thread does not terminate immediately. It can only break out of the while loop once it completed all the work within an iteration which could be as bad as a few milliseconds.

```
m_pMyThread->SignalStopWork();
```

#### 2. Wait for the thread to exit cleanly

In many cases there is a dependency between the thread signaling another thread to stop doing work and the thread doing work. In our example once we called *m_pMyThread->SignalStopWork()* we no longer need the * m_pMyThread*object*.* However we need to wait until we can be 100% sure that the thread we signaled to stop doing work, is not using the data anymore. Hence we have to wait until we know it terminated. This is done by joining the thread.

```
gEnv->pThreadManager->JoinThread(m_pMyThread, eJM_Join);
```

#### 3. Cleaning up shared thread data

Once we know the target thread has terminated and is no longer working on a specific set of data, we can go ahead and delete all resources that it shared with the signaling thread, as well as deleting the IThread object itself, too.

```
delete m_pMyThread;
m_pMyThread= nullptr;
```
