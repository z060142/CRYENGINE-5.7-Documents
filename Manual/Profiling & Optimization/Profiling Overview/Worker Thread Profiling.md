# Worker Thread Profiling

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/25535461
- Page ID: 25535461
- Breadcrumb: Profiling & Optimization > Profiling Overview > Worker Thread Profiling
- Parent: Profiling Overview

## Content

##
Overview

CryENGINE features several methods of analyzing
**
worker
**
 performance at run-time as well as in offline mode.

-
For a quick overview of the current worker load, use the console command
**
Profile 5
**
.

-
For a more detailed overview used the
**
[/docs/static/engines/cryengine-3/categories/1638401/pages/9220332](
Statoscope
)
**
 tool which can be found in the
*
game_branch/Tools
*
 folder.

##
Profile 5

The console command
**
Profile5
**
 displays information of individual worker threads work loads.

The feature should be used to get a rough overview. For a more detailed per frame analysis of data please refer to using the
**
[/docs/static/engines/cryengine-3/categories/1638401/pages/9220332](
Statoscope
)
**
 tool.

##
How to use:

-
In-game console command:
**
Profile 5
**

##
Features:

Worker utilization summary:

-
SampleTime:
*
The time period the samples have been taken in
*
Individual Worker Stats:

-
WorkTime:
*
The total time this worker has been executing jobs in the sample period.
*

-
Idle Time:
*
The total time the worker has been idling in the sample period.
*

-
Workload:
*
Percentage of WorkTime in relation to the sample time.
*

-
Workload Per Job:
*
Percentage divided by number of jobs.
*

-
Jobs: T
*
he number of jobs executed in the sample period.
*

-
*
---
*

-
Meter: Worker execution time
*
of the sample frame.
*

-
Histogram:
*
Worker execution time per frame over the last X frames.
*
Page Faults:

*
(PC only)
*

-
Faults:
*
Number of page faults in the sample period
*
 .

-
---

-
Meter:
*
Log10 representation of the sample frame's page faults.
*

-
Histogram:
*
Log10 representation of page faults per frame over the last X frames.
*
Frame Timings:

-
Time:
*
Frame time in milliseconds.
*

-
Frames:
*
Frames per second.
*

##
Limitations

-
Only none-blocking/SPU(PS3) workers are displayed

##
Statoscope

**
Statoscope
**
 offers live as well as offline analysis of data on a per frame basis.

Link to the
[/docs/static/engines/cryengine-3/categories/1638401/pages/9220332](
Statoscope Guide
)
 where more information about the tool can be found.

##
How to use:

Step 1:

-
In the in game console type:
**
e_StatoscopeLogDestination 1
**
Step2:

-
In the console type:
**
e_StatoscopeDataGroups WX
**

-
DataGroup

**
W
**

=

*
Worker Information Individual
*

-
DataGroup

**
X
**

=

*
Worker Information Summary
*

-
*
(Note the capital letters)
*
Step3:

-
Start
**
Statoscope
**
Step4:

-
Click File->Connect
Step5:

-
Connect to the platform the game is running on.

##
Features:

**
Worker Information Individual:
**

DataGroup:
**
W
**

Individual worker stats for the various backend types for a given frame.

Backend Types:

-
None-Blocking

-
Blocking

-
SPU
For each worker:

-
SamplePeriodInMs :
*
The sample period in milliseconds.
*

-
ExecutionTimeInMs:
*
The total time the worker has spend executing jobs.
*

-
IdelTimeInMs:
*
The total time the worker has been idling (sample period - execution time).
*

-
UtilPerc:
*
Percentage of usage in the sampling time.
*

-
NumJobs:
*
Number of jobs executed.
*
 |
 |

**
Worker Information Summary:
**

DataGroup:
**
X
**

Summary of all worker activity for the various backend types for a given frame.

Backend Types:

-
None-Blocking

-
Blocking

-
SPU
For each backend:

-
SamplePeriodInMs :
*
The sample period in milliseconds.
*

-
ActiveWorkers:
*
Active workers.
*

-
AvgUtilPercentage:
*
Average utilization percentage in the sampling time.
*

-
TotalExecutionPeriodInMs:
*
Total time spend executing jobs.
*

-
TotalNumberOfJobs:
*
Total number of jobs executed.
*
 |
 |

[#profile-5](
Profile 5
)
[#how-to-use](
How to use:
)
[#features](
Features:
)
[#limitations](
Limitations
)
[#statoscope](
Statoscope
)
[#how-to-use](
How to use:
)
[#features](
Features:
)
