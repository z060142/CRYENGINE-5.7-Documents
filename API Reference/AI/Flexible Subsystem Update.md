# Flexible Subsystem Update

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/44964565
- Page ID: 44964565
- Breadcrumb: AI > Flexible Subsystem Update
- Parent: AI

## Content

## Overview

Flexible Subsystem Updates provide a way to call, from game code, the *Update* function of subsystems within the AI system. This allows developers to easily modify the order or frequency in which these subsystems are updated by:

- Telling the AI system which subsystems are manually updated from game code, making the *Update* function skip updating those subsystems. This is done to prevent the same subsystems from being updated twice.
- Manually updating the subsystems from game code. This immediately executes the *Update* function on the specified subsystems.

The following is a list of AI subsystems that can be manually updated from game code:

AI Subsystem
---
Audition Map
Behavior Tree Manager
Cluster Detector
Cover System
Movement System
Navigation System
Global Intersection Tester
Global Raycaster
Vision Map

The above subsystems can be accessed from code by typing *IAISystem::ESubsystemUpdateFlag::SubsystemName,* where *SubsystemName* corresponds to the name of the AI subsystem that you'd like to manually update.

### Setting Override Update Flags

As mentioned in the Overview, the first step in modifying the order/frequency in which AI subsystems are updated, is to tell the AI system which subsystems you'd like to override. This is done by calling *GetOverrideUpdateFlags* only once during initialization, and setting the right flags.

The following example demonstrates how to override the NavigationSystem AI subsystem.

```
// Get the IAISystem from gEnv.
IAISystem* pAISystem = gEnv->pAISystem;

// Get the Override Update Flags structure.
// By setting the flag to 1 on the updateFlags structure, we indicate which AI subsystems we want to override to update manually.
CEnumFlags<ESubsystemUpdateFlag> updateFlags = pAISystem->GetOverrideUpdateFlags();

// This will will prevent the AI system from updating the subsystem (NavigationSystem, in this case) automatically.
updateFlags.Set(IAISystem::ESubsystemUpdateFlag::NavigationSystem);
```

### Manually Updating the Subsystem

The next step is to manually call the *Update* function on the NavigationSystem AI subsystem by calling * UpdateSubSystem*on the AISystem.

```
// Game loop.
void Game::Update(const CTimeValue frameStartTime, const float deltaTime)
{
// Get the IAISystem from gEnv.
IAISystem* pAISystem = gEnv->pAISystem;

// Call the UpdateSubSystem function, mentioning which system we want to manually update.
pAISystem->UpdateSubSystem(frameStartTime, deltaTime, IAISystem::ESubsystemUpdateFlag::NavigationSystem);

// Update any other game systems.
// ...
}
```

[Setting Override Update Flags](#setting-override-update-flags)[Manually Updating the Subsystem](#manually-updating-the-subsystem)
