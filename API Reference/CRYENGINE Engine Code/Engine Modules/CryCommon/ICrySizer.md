# ICrySizer

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/23306446
- Page ID: 23306446
- Breadcrumb: CRYENGINE Engine Code > Engine Modules > CryCommon > ICrySizer
- Parent: CryCommon

## Content

### Overview

The ICrySizer interface is used to record detailed information about the memory usage of a class.

### Memory profiling

The console variable "MemStats" 0/x=refresh rate in milliseconds

Also available in Editor as "Engine Memory info".

### How to use the ICrySizer interface

#### Sample:

```
void GetMemoryUsage( ICrySizer *pSizer )
{
{
SIZER_COMPONENT_NAME( pSizer, "Renderer (Aux Geometries)" );
pSizer->Add(*this);
}
pSizer->AddObject(<element_ptr>,<element_count>);
pSizer->AddObject(<container>);
m_SubObject.GetMemoryUsage(pSizer);
}
```
