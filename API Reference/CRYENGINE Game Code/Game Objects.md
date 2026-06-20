# Game Objects

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/23306555
- Page ID: 23306555
- Breadcrumb: CRYENGINE Game Code > Game Objects
- Parent: CRYENGINE Game Code

## Child Pages

- [Game Object Extensions](Game%20Objects/Game%20Object%20Extensions.md)

## Content

## Overview

Game Objects are effectively an extension to the standard **[IEntity](/docs/static/engines/cryengine-3/categories/17399809/pages/17074747)** implementation, allowing more complex logic and custom user code contained in modules other than CryEntitySystem and CryAction to be applied to entities.

The primary use cases for game objects are:

- Binding an entity to the network, done by calling IGameObject::BindToNetwork.

Network bound entities can trigger **[Remote Method Invocations](../CRYENGINE%20Engine%20Code/Engine%20Modules/CryNetwork/RMI%20Functions.md)**, or **[serialize](/docs/static/engines/cryengine-5/categories/23756813/pages/23306392)**bits of data to a remote version of the same entity.

- Creating extensions for more complex entities, noteworthy examples being actors (**[IActor](/docs/static/engines/cryengine-3/categories/17399809/pages/17074661)**) and the animated character helper (**[IAnimatedCharacter](/docs/static/engines/cryengine-3/categories/17399809/pages/17074683)**).

Keep in mind that while every Game Object must have a parent Entity, every entity does not necessarily need to have a Game Object assigned to it.

### Implementation Details

The *CGameObject* (known as **[IGameObject](/docs/static/engines/cryengine-3/categories/17399809/pages/17074810)** to projects other than CryAction) class is implemented as an Entity Proxy, residing in the * ENTITY_PROXY_USER* slot. This means that a game object pointer can be retrieved by calling * IEntity:GetProxy(ENTITY_PROXY_USER)*and casting to IGameObject. Note that this logic is wrapped in * IGameFramework::GetGameObject*, allowing easy access to an entity's game object assuming that its entity id is known.

### Methods of creating a Game Object

#### Spawning a New Entity with a Game Object

The game object system supports registering new game object extensions with the intent of automatically creating a game object with a pre-activated instance of the game object extension in question. This is done by calling **[IGameObjectSystem::RegisterExtension](/docs/static/engines/cryengine-3/categories/17399809/pages/17074815)** with the *pClsDesc* parameter set to a description of the entity class you want to create.

The default SDK sample supports this by default in the *REGISTER_GAME_OBJECT* and * REGISTER_GAME_OBJECT_EX* preprocessor helpers inside * Game/GameDll/GameFactory.h*.

#### Creating a New Game Object Instance for an Already Spawned Entity

In some cases it might not be desired behavior to have every instance of a specific entity class automatically create a game object (for example if spawning an entity with the standard**[IEntityClass](/docs/static/engines/cryengine-3/categories/17399809/pages/17074752)** implementation). In this case we can create one per entity:

```
IEntity *pMyEntity = //..

IGameObjectSystem *pGameObjectSystem = gEnv->pGame->GetIGameFramework()->GetIGameObjectSystem();
IGameObject *pGameObject = pGameObjectSystem->CreateGameObjectForEntity(pMyEntity->GetId());
```

The above code provides a newly created game object that is permanently attached to the entity, and can also now be retrieved via *IGameFramework::GetGameObject*.

### Game Object Extensions

Game Object extensions are defined by inheriting from the *IGameObjectExtension* interface, and denote the extension of a game object (and indirectly the entity it is linked to) with custom (usually game-specific) code.

[Implementation Details](#implementation-details)[Methods of creating a Game Object](#methods-of-creating-a-game-object)[Game Object Extensions](#game-object-extensions)
