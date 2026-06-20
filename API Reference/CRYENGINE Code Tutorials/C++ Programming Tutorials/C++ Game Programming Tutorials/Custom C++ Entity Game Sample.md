# Custom C++ Entity Game Sample

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/25530072
- Page ID: 25530072
- Breadcrumb: CRYENGINE Code Tutorials > C++ Programming Tutorials > C++ Game Programming Tutorials > Custom C++ Entity Game Sample
- Parent: C++ Game Programming Tutorials

## Content

##
Table of Contents

##
About the sample

This sample is a minimal Game DLL implementation meant to showcase how a game project can be built using only C++ code, as opposed to combining C++ with C# and / or Lua.

The sample implements the following:

-
Animated Entity - Basic entity that with the help of editor properties can play raw animations (Does not use Mannequin!)

-
Environment Probe - Native implementation of an environment probe, normally loaded via Lua in the GameSDK and GameZero projects.

-
Physicalized Entity - Native entity implementation that allows physicalizing a specified model as a rigid or static entity.
The sample does
**
not
**
 implement a player using the IActorSystem interface, instead opting for a dummy player entity for the sake of sample simplicity.

##
Code Breakdown

##
Startup

Keep in mind that the startup section only covers the Launcher functionality, Editor operates differently via the
*
IEditorGame
*

interface.

-
The Launcher application (see
*
<engine root>/Code/Launcher/WindowsLauncher/

*
for an example) loads the sample Game DLL and invokes the external
*
'CreateGameStartup'
*

function.

-
The sample function
*
CreateGameStartup
*
 in
*
<sample root>/Code/Game/GameDll/Main.cpp
*
 is invoked and calls
*
CGameStartup::Create,
*
resulting in the
*
 CGameStartup
*
 instance being created.

-
The Launcher application calls
*
IGameStartup::Init
*
, which in turn initializes the engine and its modules.

-
This function is responsible for initializing the Game Framework (contained in
*
CryAction.dll
*
), which in turn initializes the engine via the CrySystem module.

-
The Launcher then calls
*
IGameStartup::Run
*
, invoking the main game loop that runs until the engine is shut down.

-
This function largely delegates the actual process of updating to the
*
IGame
*
 implementation inside the game module, which in turn calls
*
IGameFramework::PreUpdate
*
 and
*
IGameFramework::PostUpdate
*
 in order to start the engine update and render flow.

##
Entities

Entities in the sample all implement the
*
CNativeEntityBase
*
 helper, a class that in turn implements
*
ISimpleExtension
*
 and
*
IGameObjectExtension
*
 in order to expose a few helper methods for setting and getting Entity properties that can be manipulated via the Sandbox Editor's Properties panel. The sample also implements a custom
*
IEntityPropertyHandler
*
 implementation (instantiated once per entity class) in order to provide support for pure C++ entities. Without this, entities need a Lua script in order to expose properties to designers.

Each entity is registered in
*
<sample root>/Code/Game/GameDll/Game/GameFactory.cpp
*
, inside the
*
CGameFactory::Init
*
 function. The entity being registered can specify any number of entity properties and then register using
*
CGameFactory::RegisterNativeEntity
*
 in order to have the engine recognize and expose the entity to designers.

##
Dummy Player

The "Player" in this sample is merely a dummy entity automatically spawned at the center of the map in
*
CGameRules::OnClientConnect
*
 (called shortly after level load). The entity has no responsibility barring a manual update of the view camera position each frame to match the entity position.

[#about-the-sample](
About the sample
)
[#code-breakdown](
Code Breakdown
)
[#startup](
Startup
)
[#entities](
Entities
)
[#dummy-player](
Dummy Player
)
