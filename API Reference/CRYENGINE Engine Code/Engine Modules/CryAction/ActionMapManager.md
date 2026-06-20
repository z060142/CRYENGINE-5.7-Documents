# ActionMapManager

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/24283649
- Page ID: 24283649
- Breadcrumb: CRYENGINE Engine Code > Engine Modules > CryAction > ActionMapManager
- Parent: CryAction

## Content

Related:
[CryInput](../CryInput.md)

For information on controller mapping, head over to the documentation here:
[Setting Up Controls and Action Maps](../../../CRYENGINE%20Game%20Code/Miscellaneous%20Game%20Code/Setting%20Up%20Controls%20and%20Action%20Maps.md)

##
Overview

The Action Maps Manager provide an high-level interface to handle input controls inside a game. The Action Maps System is implemented in CryAction, and can be used directly by any code inside CryAction or the GameDLL.

##
Initialization

The Action Map Manager is initialized during the initialization of CryAction.

We simplified the initialization process by moving most of the code into the Action Map Manager itself, so the Game just has to provide the path for the defaultProfile.xml (default path is Game/Libs/Config/defaultProfile.xml).

This can be done by simply passing the path to the manager like this:

```

`
IActionMapManager* pActionMapManager = m_pFramework->GetIActionMapManager();
if (pActionMapManager)
{
  pActionMapManager->InitActionMaps(filename);
}
`

```

Note: The ActionMapManager will clear all existing initialized maps, filters and controller layouts on initialization.

##
ActionMapManager Events

If you have other systems in place that need to know about action map events, you can subscribe to the ActionMapManager events through an IActionMapEventListener. The following events are currently available:

-
eActionMapManagerEvent_ActionMapsInitialized - The ActionMapManager successfully initialized the given action map definitions

-
eActionMapManagerEvent_DefaultActionEntityChanged - The default action entity got changed (the manager will assign new action maps automatically to this entity)

-
eActionMapManagerEvent_FilterStatusChanged - An existing filter got enabled/disabled

-
eActionMapManagerEvent_ActionMapStatusChanged - An existing action map got enabled/disabled

##
Receiving Actions During Runtime

##
Enabling/Disabling Action Maps

It is required to enable each Action Map because being able to receive the actions. It's possible to enable or disable individual Action Map at any time during run-time.

The following code:

```

`
pActionMapMan->EnableActionMap("default", true);

`

```

##
Listener

To receive Actions, it's required to implement the IActionListener interface in a class.
