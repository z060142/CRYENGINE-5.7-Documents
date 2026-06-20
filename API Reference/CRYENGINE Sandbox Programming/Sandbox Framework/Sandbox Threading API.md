# Sandbox Threading API

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/26873110
- Page ID: 26873110
- Breadcrumb: CRYENGINE Sandbox Programming > Sandbox Framework > Sandbox Threading API
- Parent: Sandbox Framework

## Content

The Sandbox threading API is part of EditorCommon.

##
Header files:

`
#include <ThreadingUtils.h>
`

##
Namespace:

`
ThreadingUtils
`

##
Motivation:

Responsiveness of the user-interface is a critical aspect of the user-experience. The user-interface runs on only a single thread called the main thread. It is imperative that the main thread is never blocked by some long-running operation. Any operation that takes more than a few milliseconds to complete should run asynchronously (i.e., on another thread).

Multithreaded programming is inherently difficult and error prone, so we need to provide some common concepts that are used throughout the Sandbox. Also, threads should be managed by a single system so that we can utilize resources efficiently. In addition, the API must be simple enough to encourage concurrent programming.

##
Multi-threading in Qt:

The Sandbox user-interface is built on top of the Qt library, so you must conform to Qt's assumptions with respect to multi-threading. For a comprehensive description of Qt's multithreading model read
[Thread Basics](http://doc.qt.io/qt-5/thread-basics.html)
.

Among the central features of Qt are QObject, QWidget, and the signal&slot mechanism. QObject is the base class of virtually every other class in Qt. QWidget (which derives from QObject) is the base class of every user-interface class. The signal&slot mechanism is used to connect events (signals) of one QObject to callbacks (slots) of one or more other QObjects. Signal&slot implements loose coupling, in the sense that the signaling object is not aware of its listeners.

Nothing is thread-safe unless stated otherwise.

Qt's documentation explicitly states what functions are thread-safe. For example, see the note in the text of
[postEvent()](http://doc.qt.io/qt-5/qcoreapplication.html#postEvent)
.

Qt is inherently single-threaded, as it is built around a single main event loop. As a corollary,
**
 all user-interface elements (objects deriving from QWidget) must be created on the main thread
**
. This is also true for (modal) dialogs. In particular, do not call
`
CQuestionDialog::SQuestionDialog
`
 (our version of
`
QMessageBox::question
`
) asynchronously.

QObjects have the notion of
**
thread affinity
**
. An object can be explicitly moved to another thread. Each thread has its own event loop which processes the slots of objects it owns.

Signals&slots are thread-safe and non-blocking
**
by default
**
. The connection mode can be changed, however, rendering a connection potentially unsafe.

Therefore, when reasoning about the thread-safety of a particular signal&slot connection, consider the connection mode and the thread affinity of the target object.

Qt does a good job giving you debugging information. In the Visual Studio output window, look for messages similar to these:

**
Qt debugging messages
**

`
Qt: QApplication: Object
`
`
event
`

`
filter cannot be
`
`
in
`

`
a different thread.
`
`
Qt: QObject::setParent: Cannot
`
`
set
`

`
parent,
`
`
new
`

`
parent
`
`
is
`

`
in
`

`
a different thread
`
 |

##
Documentation:

Two function templates are provided for
**
task-based
**
 concurrency:
`
Async
`
 and
`
PostOnMainThread
`
.

**
ThreadingUtils.h
**

`
template
`
`
<
`
`
typename
`

`
Fn,
`
`
typename
`
`
... Args>
`
`
std::future<std::result_of_t<std::decay_t<Fn>(std::decay_t<Args>...)>> Async(Fn&& fn, Args&&... args);
`

`
template
`
`
<
`
`
typename
`

`
Fn,
`
`
typename
`
`
... Args>
`
`
std::future<std::result_of_t<std::decay_t<Fn>(std::decay_t<Args>...)>> PostOnMainThread(Fn&& fn, Args&&... args);
`
 |

`
Async
`
 runs a function on a thread different from the main thread, and
`
PostOnMainThread
`
 runs a function on the main thread (i.e., user-interface thread). Both functions return a
[std::future](http://en.cppreference.com/w/cpp/thread/future)
 that can be used to retrieve the result. If
`
PostOnMainThread
`
 is called on the main thread, the function is executed immediately. Otherwise, the function is pushed on a FIFO-queue. A function passed to
`
Async
`
 can be executed by any worker thread in any order.

Both functions are recursive, which means that a function executed by either
`
Async
`
 or
`
PostOnMainThread
`
 is also free to call
`
Async
`
 or
`
PostOnMainThread
`
 again. However, an asynchronous task should never block on another asynchronous task. Since there is usually just a fixed number of worker threads, this could lead to a deadlock.

`
Async([]()
`
`
{
`
`

`
`
DoSomething();
`
`

`
`
Async(DoSomethingElse());
`
`
// This is fine.
`
`
});
`

`
Async([]()
`
`
{
`
`

`
`
DoSomething();
`
`

`
`
int
`

`
result = Async(DoSomethingElse()).get();
`
`
// Warning! Potential deadlock, due to fixed number of worker threads.
`
`
});
`

`
Async([]()
`
`
{
`
`

`
`
DoSomething();
`
`

`
`
int
`

`
result = PostOnMainThread(DoSomethingElse()).get();
`
`
// This is fine.
`
`
});
`

`
PostOnMainThread([]()
`
`
{
`
`

`
`
DoSomething();
`
`

`
`
int
`

`
result = PostOnMainThread(DoSomethingElse()).get();
`
`
// This is fine. Function will be called immediately.
`
`
});
`
`

`
 |

Arguments are copied, and the same rules apply as for passing arguments to
[std::async](http://en.cppreference.com/w/cpp/thread/async)
 or
[std::thread](http://en.cppreference.com/w/cpp/thread/thread)
. Use
[std::ref](http://en.cppreference.com/w/cpp/utility/functional/ref)
 for pass-by-reference; or capture-by-reference, if the function is a lambda.

The functions are modeled after
[std::async](http://en.cppreference.com/w/cpp/thread/async)
.
`
Async
`
 should be preferred over
`
std::async,
`
 however, as it uses Sandbox' thread pools. Note that, in contrast, to
`
std::async, Async
`
 does not block when the return value is ignored:

**
LaunchAsync vs std::async
**

`
std::async(std::launch::async, []{ f(); });
`
`
// temporary's destructor waits for f()
`
`
Async([] { f(); });
`
`
// Runs asynchronously.
`
 |

##
Example 0:

A typical scenario is that a costly operation should produce some value asynchronously, which is then consumed by the main thread. With a task-based approach, this can be written as follows.

`
 std::vector<CItem> CreateItems();
`
`
// Creates items, can be run asynchronously.
`
`

`
`
void
`

`
UseItems(
`
`
const
`

`
std::vector<CItem>& items);
`
`
// Should be called on main thread, copies items to some data-structure.
`

`
Async([]()
`
`
{
`
`

`
`
auto items = CreateItems();
`
`

`
`
PostOnMainThread(UseItems, items);
`
`
}
`
 |

##
Example 1: Wait for the main thread.

Sometimes, asynchronous operations need to call back to the main thread. For example, they might need to show a confirmation dialog. Recall that all widgets, including dialogs, must be created on the main thread.

`
bool
`

`
DiscardChanges(
`
`
const
`

`
string& what)
`
`
{
`
`

`
`
return
`

`
CQuestionDialog::SQuestion(
`
`
"Discard changes?"
`
`
, what) == QDialogButtonBox::Yes;
`
`
}
`

`
// Unsafe.
`
`

`
`
Async([]()
`
`
{
`
`

`
`
bool
`

`
discard = DiscardChanges(
`
`
"Level"
`
`
);
`
`
// Error! Might crash.
`
`

`
`
if
`

`
(discard)
`
`

`
`
{
`
`

`
`
// ...
`
`

`
`
}
`
`
});
`

`
// Safe.
`
`
 Async([]()
`
`
{
`
`

`
`
bool
`

`
discard = PostOnMainThread(DiscardChanges, string(
`
`
"Level"
`
`
)).get();
`
`
// Here, get() is blocking.
`
`

`
`
if
`

`
(discard)
`
`

`
`
{
`
`

`
`
// ...
`
`

`
`
}
`
`
});
`
 |

##
Example 2:

Another example is that two functions can be run in parallel before their results are used:

`
double
`

`
DoComputation0();
`
`
double
`

`
DoComputation1();
`

`
double
`

`
MergedResult()
`
`
{
`
`

`
`
std::future<
`
`
double
`
`
> r0 = Async(DoComputation0);
`
`

`
`
r1 = DoComputation1();
`
`

`
`
return
`

`
Merge(r0.get(), r1);
`
`
// Here, r0.get() is blocking.
`
`
}
`
 |

##
Continuations:

In some other task-based APIs, there is the concept of a continuation (see
[NET framework,](https://msdn.microsoft.com/en-us/library/ee372288(v=vs.110).aspx)

[PPL's then](https://msdn.microsoft.com/library/cdc3a8c0-5cbe-45a0-b5d5-e9f81d94df1a.aspx#task__then_method)
 or
[boost's then](http://www.boost.org/doc/libs/1_55_0/doc/html/thread/synchronization.html#thread.synchronization.futures.reference.unique_future.then)
). Continuations are a powerful concept in which tasks can be chained together arbitrarily. Most importantly, a task need not be aware of what other tasks follow. Typically, there are also functions to synchronize with a group of tasks, and you can wait for the completion of any tasks in a group, or all of them. In conjunction with continuations, task-based programming is a very powerful paradigm.

In example 0, we showed how to launch one task on the main thread, once an asynchronous task has finished. This is a special case of continuation, where the task executed on the main thread is a continuation of the asynchronous task. Since this is a very common use-case, two convenience function templates are provided —
`
AsyncFinalize
`
 and
`
AsyncNotify
`
 ----  that build on top of
`
Async
`
 and
`
PostOnMainThread
`
:

**
AsyncFinalize and AsyncNotify
**

`
template<typename WorkFn, typename FinalizeFn>
`
`
std::future<std::result_of_t<std::decay_t<WorkFn>()>> AsyncFinalize(WorkFn&& workFn, FinalizeFn&& finalizeFn)
`

`
template<typename WorkFn, typename FinalizeFn>
`
`
std::future<std::result_of_t<std::decay_t<WorkFn>()>> AsyncNotify(WorkFn&& workFn, FinalizeFn&& finalizeFn)
`
 |

Both function templates take to functions as an argument: a work function run asynchronously, and a finalize function to run on the main thread. The difference between
`
AsyncFinalize
`
 and
`
AsyncNotify
`
 is that the former passes the result of the work function to the finalize function, whereas the latter calls the finalize function without any arguments. Both functions return a future of the work function.

Note that no additional arguments can be passed to
`
workFn
`
 and
`
finalizeFn
`
. Use lambdas with capture instead.

**
Example 3:

**

`
std::vector<CItem> ImportItems(
`
`
const
`

`
std::vector<string>& filePaths,
`
`
const
`

`
CImportParams& importParams);
`
`
void
`

`
UseItems(
`
`
const
`

`
std::vector<CItem>& items);
`

`
AsyncFinalize([filePaths, importParams]
`
`
{
`
`

`
`
return
`

`
ImportItems(filePaths, importParams);
`
`
}, UseItems);
`
 |
