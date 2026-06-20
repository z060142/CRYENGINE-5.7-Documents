# Creating new Data Groups

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/23306655
- Page ID: 23306655
- Breadcrumb: CRYENGINE Tools > Statoscope > Creating new Data Groups
- Parent: Statoscope

## Content

##
Overview

This document covers how to add new data groups to Statoscope.

The log format is self describing, so that the tool doesn't need updating when new stats are added. All that needs to be done is to create an implemetation of
*
IStatoscopeDataGroup
*
 and register it with
*
CStatoscope::RegisterDataGroup()
*
.

Chapters:

[Basic Example](#basic-example)
[Profilers Data Group Example](#profilers-data-group-example)

##
Basic Example

Here is an example of the simplest data group:

```

`
struct SFrameLengthDG : public IStatoscopeDataGroup
{
  virtual SDescription GetDescription() const
  {
    return SDescription('f', "frame lengths", "['/' (float frameLengthInMS)]");
  }
  virtual void Write(IStatoscopeFrameRecord& fr)
  {
    fr.AddValue(gEnv->pTimer->GetRealFrameTime() * 1000.0f);
  }
};
...
RegisterDataGroup(new SFrameLengthDG());
...

`

```

It can be enabled by adding 'f' to e_StatoscopeDataGroups, "frame lengths" will appear in the e_StatoscopeDataGroups's help string, and every frame it will output a single float value that appears as "/frameLengthInMS" in the
*
Overview
*
 tree view in the tool.

When adding a new data group, be sure to choose a letter that is not already in use. Check already existing groups in
*
Statoscope.cpp
*
 and
[Statoscope - Data Groups](/docs/static/engines/cryengine-3/categories/1638401/pages/9220402)
.

##
Profilers Data Group Example

Here is the frame profilers data group, which shows how to record bar data:

```

`
struct SFrameProfilersDG : public IStatoscopeDataGroup
{
  virtual SDescription GetDescription() const
  {
    return SDescription('r', "frame profilers", "['/Threads/$' (int count) (float selfTimeInMS)]");
  }
  virtual void Enable()
  {
    IStatoscopeDataGroup::Enable();
    ICVar *pCV_profile = gEnv->pConsole->GetCVar("profile");
    if (pCV_profile)
      pCV_profile->Set(-1);
  }
  virtual void Disable()
  {
    IStatoscopeDataGroup::Disable();
    ICVar *pCV_profile = gEnv->pConsole->GetCVar("profile");
    if (pCV_profile)
      pCV_profile->Set(0);
  }
  virtual void Write(IStatoscopeFrameRecord &fr)
  {
    for (uint32 i=0; i<m_frameProfilerRecords.size(); i++)
    {
      SPerfStatFrameProfilerRecord &fpr = m_frameProfilerRecords[i];
      string fpPath = GetFrameProfilerPath(fpr.m_pProfiler);
      fr.AddValue(fpPath.c_str());
      fr.AddValue(fpr.m_count);
      fr.AddValue(fpr.m_selfTime);
    }
    m_frameProfilerRecords.clear();
  }
  virtual uint32 PrepareToWrite()
  {
    return m_frameProfilerRecords.size();
  }
  std::vector<SPerfStatFrameProfilerRecord> m_frameProfilerRecords;  // the most recent frame's profiler data - filled out externally
};
`

```

With bar stats like this, the same format is output many times per frame, in this case
*
count
*
 and
*
selfTimeInMS
*
 for each named profiler. The number of items needs to be returned by
*
PrepareToWrite()
*
. To specify the name of each item, put a '$' in the appropriate place in the format string of
*
GetDescription()
*
 and the first value output will be used to replace it. In this example, if
*
fpPath
*
 is "Main/Action/CFlowSystem::Update()", the values output will be attributed to "/Threads/Main/Action/CFlowSystem::Update()" and appear in a hierarchy in the tool.

Values can either be given type
*
float
*
 or
*
int
*
 and are ultimately stored as floats in the tool. The distinction with ints is only for a neater display (i.e. 423 rather than 423.0000000).
