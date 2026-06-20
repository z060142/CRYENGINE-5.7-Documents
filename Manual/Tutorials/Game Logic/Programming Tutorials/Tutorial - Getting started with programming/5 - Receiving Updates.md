# 5 - Receiving Updates

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/26875709
- Page ID: 26875709
- Breadcrumb: Tutorials > Game Logic > Programming Tutorials > Tutorial - Getting started with programming > 5 - Receiving Updates
- Parent: Tutorial - Getting started with programming

## Content

Plug-ins are able to subscribe to updates, receiving callbacks every frame to do any custom work on a per-frame basis. In the simplest case, we can simply override the
Cry::IEnginePlugin::MainUpdate
 function:

##
Receiving Updates

Using your CRYENGINE account, you can download the CRYENGINE launcher
 by following the below steps:

```

`
virtual bool Initialize(SSystemGlobalEnvironment& env, const SSystemInitParams& initParams) override
{
  // Enable the MainUpdate step
  EnableUpdate(EUpdateStep::MainUpdate, true);
}

virtual void MainUpdate(float frameTime) override
{
  CryLogAlways("Update with frame time %f", frameTime);
}
`

```

Once compiled, you can launch the application and notice that the logging we do each frame is output to the console. This can be extended with any custom logic you want.

Plug-ins have several update steps to choose from; typically MainUpdate is where game logic is best suited. If you're interested, have a look at the additional callbacks and information on use cases in the
IEnginePlugin
 declaration.
