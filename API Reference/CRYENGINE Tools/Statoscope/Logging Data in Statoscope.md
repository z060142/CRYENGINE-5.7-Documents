# Logging Data in Statoscope

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/23306649
- Page ID: 23306649
- Breadcrumb: CRYENGINE Tools > Statoscope > Logging Data in Statoscope
- Parent: Statoscope

## Content

##
Overview

This article will guide you on the steps needed to log data into Statoscope.

Enabling data groups
**
does
**
 impact on performance, especially if you enable everything all at once.

Only select the data groups that you want to display, this reduces the impact of logging data to Statoscope.

Chapters:

[#estatoscopelogdestination](
e_StatoscopeLogDestination
)
[#estatoscopedatagroups](
e_StatoscopeDataGroups
)
[#usage](
Usage
)
[#data-groups](
Data Groups
)
[#function-profiling](
Function Profiling
)
Two CVar's need to be set in the Launcher or Editor to enable logging:
**
 e_StatoscopeLogDestination
**
 and
**
e_StatoscopeDataGroups
**

##
e_StatoscopeLogDestination

This controls where to log to:

**
0 - File
**
 - saves a log to the
*
root/statoscope
*
 folder. On 360 this will be on your dev/testkit.
**

1 - Socket
**
 - the tool connects directly to the game.

##
e_StatoscopeDataGroups

This controls what data to log. It's an upper and lower case bitfield CVar, so you can do things like e_StatoscopeDataGroups fg, e_StatoscopeDataGroups A+, e_StatoscopeDataGroups g- to get the equivalent of e_StatoscopeDataGroups fA.

Obviously adding and removing groups like this is most useful at run time in the console.

To add data groups at run-time use the + sign:

-
**
e_StatoscopeDataGroups A+
**
To remove data groups at run-time use the – sign:

-
**
e_StatoscopeDataGroups A-
**

For a list of available data groups see
[/docs/static/engines/cryengine-5/categories/23756813/pages/23306654](
Statoscope - Data Groups
)
 or search in Visual Studio for '
**
`
public IStatoscopeDataGroup'
`
**
 you should be able to find them all.

##
Usage

The defaults are set to upload some basic data which is useful for QA play-throughs and net tests.

If you just want to record some data to see how your game is performing, then the best setup is usually socket logging as this gives you a live update in the tool and avoids the hassle of managing log files.

If you want to log QA sessions or compare time demo runs, then file logging is preferable.

##
Data Groups

These are collections of stats. So for instance, the streaming audio data group ('a') records both actual and requested audio bandwidth. It is not possible to split data groups - in that case you get both stats or neither.

Which data groups you enable will of course depend on what data you are interested in. Many are self explanatory, but it may be worth looking at the implementation of the appropriate
*
IStatoscopeDataGroup
*
 class.

See
[/docs/static/engines/cryengine-5/categories/23756813/pages/23306655](
Creating new data groups
)
 for more details on how data groups work in code.

##
Function Profiling

The 'r' data group records function profiler data - the same stats that "profile 1" displays (this was initially implemented to find large single frame spikes). To keep log size down some CVars have been added that control which functions are recorded:

-
**
e_StatoscopeMaxNumFuncsPerFrame
**
 - Determines the number of functions to include in the list of profile measurements. The functions kept in the output are the ones with the highest self time i.e. total execution time minus the time spent calling other functions. (default: 150 functions)

-
**
e_StatoscopeMinFuncLengthMs
**
 - Ignores functions below this threshold - removes the small incidental functions, especially ones that took 0ms (default: 0.01ms).

-
**
e_StatoscopeDumpAll
**
 - If set to 1, e_StatoscopeMaxNumFuncsPerFrame is ignored, all are taken and any functions that don't meet the e_StatoscopeMinFuncLengthMs threshold are added together into one "SmallFunctions/SmallFunctions/" stat (default: 0). Since CRYENGINE implements streamed binary logging this is a safe option to be enabled at all times.
If you are looking for data outside of the main thread, then set
**
profile_allthreads 1
**
. Statoscope supports filtering by thread and module, both in the interface, after capturing the log and during logging. To filter at logging time, then use
**
profile_filter
**
 and
**
profile_filter_thread
**
