# Startup and Update

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/29450480
- Page ID: 29450480
- Breadcrumb: Editor Tools > Universal Query System (UQS) > Startup and Update
- Parent: Universal Query System (UQS)

## Content

##
Overview

##
UQS CryPlugin

The Universal Query System (UQS) is implemented as a CryPlugin. Please refer to the official Plugin System documentation for any further information (this is not part of the UQS documentation):
[Plugin System](../../Beta%20Features/Plugin%20System.md)

##
Startup and Update

In order to make use of UQS in your game, you are first required to carry out some initialization. More specifically, your game class will need to subscribe to UQS Hub events in order to register custom item types, generators, functions, evaluators and to also load the library of query blueprints. Query blueprints are basically templates specifying what a query consists of and they will get instantiated when running a live query.

At run-time, your game will need to periodically update the UQS to keep queries running and to allow UQS to perform some in-game debug rendering.

Below you'll find a minimalistic game class that you could use as a base for your own code:

```

`
// MyGame.h
#pragma once

#include <CryUQS/Interfaces/InterfacesIncludes.h>
#include <CryUQS/DataSource_XML/DataSource_XML_Includes.h>

class CMyGame : public ISystemEventListener, public UQS::Core::IHubEventListener
{
public:
    CMyGame();
    ~CMyGame();

    // ISystemEventListener
    virtual void OnSystemEvent(ESystemEvent event, UINT_PTR wparam, UINT_PTR lparam) override;
    // ~ISystemEventListener

    // UQS::Core::IHubEventListener
    virtual void OnUQSHubEvent(UQS::Core::EHubEvent ev) override;
    // ~UQS::Core::IHubEventListener

    // pseudo method for illustration purpose only
    void Update();

private:
    UQS::DataSource_XML::CXMLDatasource m_uqsXmlDatasource;
};
`

```

```

`
// MyGame.cpp
#include "StdAfx.h"
#include "MyGame.h"

#include <CryUQS/Client/ClientIncludes.h>
#include <CryUQS/StdLib/StdLibRegistration.h>

// This is the directory where all query blueprints will be loaded from.
// Also, the query editor will save new query blueprints to this location as well.
#define UQS_QUERIES_LIBRARY_ROOT_PATH "libs/ai/uqs"

CMyGame::CMyGame()
{
    gEnv->pSystem->GetISystemEventDispatcher()->RegisterListener(this);
}

CMyGame::~CMyGame()
{
    gEnv->pSystem->GetISystemEventDispatcher()->RemoveListener(this);
}

void CMyGame::OnSystemEvent(ESystemEvent event, UINT_PTR wparam, UINT_PTR lparam)
{
    switch (event)
    {
  //
  // Accessing the potentially loaded UQS-Plugin should only be done after the ESYSTEM_EVENT_GAME_POST_INIT event.
  // If the CryPlugin system actually loaded the UQS-Plugin, it's guaranteed to be present at that point in time.
  // Notice that it's important to subscribe to the UQS Hub upon ESYSTEM_EVENT_GAME_POST_INIT (and *not* upon
  // ESYSTEM_EVENT_GAME_POST_INIT_DONE). The _DONE event is used internally by the UQS Hub to notify all listeners.
  //
    case ESYSTEM_EVENT_GAME_POST_INIT:
        if (UQS::Core::IHub* pHub = UQS::Core::IHubPlugin::GetHubPtr())
        {
            pHub->RegisterHubEventListener(this);
        }
        break;
    }
}

void CMyGame::OnUQSHubEvent(UQS::Core::EHubEvent ev)
{
    switch (ev)
    {
    case UQS::Core::EHubEvent::RegisterYourFactoriesNow:
        {
            //
            // instantiate all factories that the UQS StdLib provides
            //

            UQS::StdLib::CStdLibRegistration::InstantiateAllFactoriesForRegistration();

            //
            // register all instantiated factories that our game provides
            //

            UQS::Core::IHub& hub = UQS::Core::IHubPlugin::GetHub();
            UQS::Client::CFactoryRegistrationHelper::RegisterAllFactoryInstancesInHub(hub);
        }
        break;

    case UQS::Core::EHubEvent::LoadQueryBlueprintLibrary:
        {
            //
            // load all query blueprints from the XML data source
            //

            UQS::Core::IHub& hub = UQS::Core::IHubPlugin::GetHub();
            m_uqsXmlDatasource.SetupAndInstallInHub(hub, UQS_QUERIES_LIBRARY_ROOT_PATH);
        }
        break;
    }
}

// pseudo method for illustration purpose only
void CMyGame::Update()
{
    // ...
    if (UQS::Core::IHub* pHub = UQS::Core::IHubPlugin::GetHubPtr())
    {
        //
        // update UQS core (to run all ongoing queries and deliver their results once finished)
        //

        pHub->Update();

        //
        // update UQS debug rendering in the 3D world
        //

        if (IView* pActiveView = gEnv->pGameFramework->GetIViewSystem()->GetActiveView())
        {
            const SViewParams* pViewParams = pActiveView->GetCurrentParams();
            UQS::Core::SDebugCameraView debugCameraView;
            debugCameraView.pos = pViewParams->position;
            debugCameraView.dir = pViewParams->rotation.GetColumn1();
            pHub->GetQueryHistoryManager().UpdateDebugRendering3D(debugCameraView, UQS::Core::IQueryHistoryManager::SEvaluatorDrawMasks::CreateAllBitsSet());
        }
    }
    // ...
}
`

```

[UQS CryPlugin](#uqs-cryplugin)
[Startup and Update](#startup-and-update)
