# CryExtension Samples

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/23306449
- Page ID: 23306449
- Breadcrumb: CRYENGINE Engine Code > Engine Modules > CryCommon > CryExtension > CryExtension Samples
- Parent: CryExtension

## Content

### Sample 1 - Implementing a source control plugin via extensions

```
//////////////////////////////////////////////////////////////////////////
// source control interface

struct ISourceControl : public ICryUnknown
{
CRYINTERFACE_DECLARE(ISourceControl, 0x399d8fc1d94044cc, 0xa70d2b4e58921453)

virtual void GetLatest(const char* filename) = 0;
virtual void Submit() = 0;
};

typedef cryshared_ptr<ISourceControl> ISourceControlPtr;

//////////////////////////////////////////////////////////////////////////
// concrete implementations of source control interface

class CSourceControl_Perforce : public ISourceControl
{
CRYINTERFACE_BEGIN()
CRYINTERFACE_ADD(ISourceControl)
CRYINTERFACE_END()

CRYGENERATE_SINGLETONCLASS(CSourceControl_Perforce, "CSourceControl_Perforce", 0x7305bff20ee543e3, 0x820792c56e74ecda)

virtual void GetLatest(const char* filename) { ... };
virtual void Submit() { ... };
};

CRYREGISTER_CLASS(CSourceControl_Perforce)

class CSourceControl_SourceSafe : public ISourceControl
{
CRYINTERFACE_BEGIN()
CRYINTERFACE_ADD(ISourceControl)
CRYINTERFACE_END()

CRYGENERATE_SINGLETONCLASS(CSourceControl_SourceSafe, "CSourceControl_SourceSafe", 0x1df62628db9d4bb2, 0x8164e418dd5b6691)

virtual void GetLatest(const char* filename) { ... };
virtual void Submit() { ... };
};

CRYREGISTER_CLASS(CSourceControl_SourceSafe)

//////////////////////////////////////////////////////////////////////////
// using the interface (submitting changes)

void Submit()
{
ICryFactoryRegistry* pReg = gEnv->pSystem->GetFactoryRegistry();

ICryFactory* pFactory = 0;
size_t numFactories = 1;
pReg->IterateFactories(cryiidof<ISourceControl>(), &pFactory, numFactories);

if (pFactory)
{
ISourceControlPtr pSrcCtrl = cryinterface_cast<ISourceControl>(pFactory->CreateClassInstance());
if (pSrcCtrl)
{
pSrcCtl->Submit();
}
}
}
```
