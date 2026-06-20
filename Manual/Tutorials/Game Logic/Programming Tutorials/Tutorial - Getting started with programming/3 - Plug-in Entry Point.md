# 3 - Plug-in Entry Point

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/27592193
- Page ID: 27592193
- Breadcrumb: Tutorials > Game Logic > Programming Tutorials > Tutorial - Getting started with programming > 3 - Plug-in Entry Point
- Parent: Tutorial - Getting started with programming

## Content

Each plug-in has to provide a single implementation of the
Cry::IEnginePlugin
 interface. In our case, one was automatically created along with our project; see
*
GamePlugin.cpp
*
 and
*
**

**
GamePlugin.h
*
.

Before we take a look at the default implementation, let's have a look at the bare minimum implementation of an engine plug-in:

##
Plug-in Breakdown

```

`
class CGamePlugin final : public Cry::IEnginePlugin
{
  CRYINTERFACE_SIMPLE(Cry::IEnginePlugin)
  CRYGENERATE_SINGLETONCLASS_GUID(CGamePlugin, "Blank", "f01244b0-a4e7-4dc6-91e1-0ed18906fe7c"_cry_guid)

  virtual bool Initialize(SSystemGlobalEnvironment& env, const SSystemInitParams& initParams) override
  {
  }
};

CRYREGISTER_SINGLETON_CLASS(CGamePlugin)
`

```

**
Let's dissect this into parts:
**

##
Inheritance

```

`
class CGamePlugin final : public Cry::IEnginePlugin
`

```

Here we declare our game plug-in implementation as
*
CGamePlugin
*
, and inherit from
*
Cry::IEnginePlugin
*
. On startup, the engine parses the
**
Game.cryproject
**
 file in your project directory, which in turn contains a path to our game plug-in DLL. Once the plug-in is loaded, an instance of our plug-in is created, invoking the
CGamePlugin
constructor.

##
Extension Framework

```

`
CRYINTERFACE_SIMPLE(Cry::IEnginePlugin)
`

```

Plug-ins utilize the engine's extension framework. This is a form of reflection allowing us to query implementations based on a specific interface. In this case, we indicate that our implementation implements
Cry::IEnginePlugin
.

```

`
CRYGENERATE_SINGLETONCLASS_GUID(CGamePlugin, "Blank", "f01244b0-a4e7-4dc6-91e1-0ed18906fe7c"_cry_guid)
`

```

In the next section, we need to provide our plug-in with a name and a GUID.
