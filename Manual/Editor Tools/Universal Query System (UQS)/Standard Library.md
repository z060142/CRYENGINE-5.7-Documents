# Standard Library

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/29450482
- Page ID: 29450482
- Breadcrumb: Editor Tools > Universal Query System (UQS) > Standard Library
- Parent: Universal Query System (UQS)

## Content

## Overview

The Universal Query System (UQS) Standard Library (StdLib) is a set of item types, functions, generators and evaluators that are meant as a reference for how to implement custom ones but can also be used out of the box by your game.

It's a static library and needs to be linked to your game executable.

Technically speaking, the StdLib resides on the same layer as your game's custom item types, functions, etc.

In order to make the StdLib's content available for registration in the UQS core, a single method call will suffice:

```
UQS::StdLib::CStdLibRegistration::InstantiateAllFactoriesForRegistration();
```

### Contents of the StdLib

As of writing, the StdLib currently provides the following elements, which are all registered with the "std::" prefix:

- **Item types:**
- std::EntityId
- std::int
- std::bool
- std::float
- std::Pos3
- std::Ofs3
- std::Dir3
- std::NavigationAgentTypeID

- **Functions:**
- std::Pos3 std::Pos3AddOfs3 (std::Pos3 pos, std::Ofs3 ofs)
- std::Pos3 std::PosFromEntity (std::EntityId entityId)

- **Generators:**
- std::Pos3[] std::PointsOnPureGrid (std::Pos3 center, std::float size, std::float spacing)
- std::Pos3[] std::PointsOnNavMesh (std::Pos3 pivot, std::Ofs3 localAABBMins, std::Ofs3 localAABBMaxs, std::NavigationAgentTypeID navigationAgentTypeID)

- **InstantEvaluators:**
- std::TestMinDistance (std::Pos3 pos1, std::Pos3 pos2, std::float minRequiredDistance)
- std::TestMaxDistance (std::Pos3 pos1, std::Pos3 pos2, std::float maxAllowedDistance)
- std::TestLocationInNavMesh (std::Pos3 locationToTest, std::NavigationAgentTypeID navigationAgentTypeID)
- std::ScoreDistance (std::Pos3 pos1, std::Pos3 pos2, std::float distanceThreshold)
- std::ScoreDistanceInverse (std::Pos3 pos1, std::Pos3 pos2, std::float distanceThreshold)
- std::ScoreRandom ()

- **DeferredEvaluators:**
- std::TestRaycast (std::Pos3 from, std::Pos3 to, bool raycastShallSucceed)

std::TestRaycast
Notice about the **std::TestRaycast** evaluator: the underlying raycaster uses the Renderer to regulate the number of raycasts per frame and will therefore not work on a dedicated server! (Read: null-pointer crash!)

Also, the parameters for testing specific object types and flags for Ray <-> World intersections are all hardcoded. Due to these limitations, it's not recommended to use this Deferred Evaluator in a production environment - you should rather consider it as a reference for your own implementation.
