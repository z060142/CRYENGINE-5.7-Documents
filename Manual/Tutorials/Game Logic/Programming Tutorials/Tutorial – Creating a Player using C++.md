# Tutorial – Creating a Player using C++

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/101679110
- Page ID: 101679110
- Breadcrumb: Tutorials > Game Logic > Programming Tutorials > Tutorial – Creating a Player using C++
- Parent: Programming Tutorials

## Child Pages

- [Tutorial - Adding Specialized Controls to a Player (Sprint)](Tutorial%20%E2%80%93%20Creating%20a%20Player%20using%20C%2B%2B/Tutorial%20-%20Adding%20Specialized%20Controls%20to%20a%20Player%20(Sprint).md)
- [Tutorial - Adding Specialized Controls to a Player (Jump)](Tutorial%20%E2%80%93%20Creating%20a%20Player%20using%20C%2B%2B/Tutorial%20-%20Adding%20Specialized%20Controls%20to%20a%20Player%20(Jump).md)
- [Tutorial - Adding Specialized Controls to a Player (Crouch)](Tutorial%20%E2%80%93%20Creating%20a%20Player%20using%20C%2B%2B/Tutorial%20-%20Adding%20Specialized%20Controls%20to%20a%20Player%20(Crouch).md)

## Content

### Overview

In this tutorial, we will be covering the basics of how to use C++ to create a usable and controllable first-person player (FPP). More specifically, we will be creating a "Player Component" that can be configured directly within CRYENGINE by changing values such as the player’s height, walking speed, rotation speed, etc.

![Image](https://www.cryengine.com/docs/static/attachments/101679139)

This "Player Component" will be written entirely in C++, and while we will be using either a First Person Shooter or Third Person Shooter project template for the animations, we will be building the movements ourselves from scratch. The player itself is comprised of four main components; the Camera, the Input, the Physics and the Animation. By the time you're done, your player character will have:

- A simple capsule collision model
- Basic **WASD** controls
- A mouse-look camera controller

Whether you are familiar with C++ or not, by the end of the lesson you will have learned valuable C++ basics while also introducing a simple character into your project, one which you can modify and reuse in any project.

### Prerequisites

- CRYENGINE 5.7 LTS
- Visual Studio (2017, 2019 or 2020 work just fine) or any other IDE or code editor of your choice

### Getting Started

Before adding any kind of movement to our player, we first need to set a few things up; the most crucial being to create a Player that we can apply movement too. This Player is simply a combination of C++ based components (camera, mesh, inputs, velocity), that together become the foundation of a playable character. To begin, we first need to create these components, learn where they belong, and understand how this all works together with CRYENGINE.

#### Creating a New Project

To get started, the first step is to create a project. While the templates we will use contain player controls, we will be removing all of the code and building our own player with customizable variables, while preserving the animations that come with the character.

- Begin by creating a new project in CRYENGINE 5.7 LTS. For a template, select either the Third Person Shooter or First Person Shooter template.
For more information on how to create a project, please see [Creating, Importing & Upgrading Projects](../../../CRYENGINE%20-%20Getting%20Started/Installing%20CRYENGINE/CRYENGINE%20Launcher%20Reference/Managing%20Projects.md).
Make sure you select the **CPP** and not **C#** template, as we will be using C++.
- Name your project and open it in CRYENGINE 5.7 LTS Sandbox. Upon the project loading, immediately close the Sandbox Editor. For this tutorial, we will mostly be working outside of the Sandbox Editor.
- Open the CRYENGINE Launcher and navigate to the Projects tab. Once there, click the![Image](https://www.cryengine.com/docs/static/attachments/101679116) icon corresponding to our newly-created project and select **Reveal in Explorer**.
If you're confused about the Launcher interface, please see [CRYENGINE Launcher Reference](../../../CRYENGINE%20-%20Getting%20Started/Installing%20CRYENGINE/CRYENGINE%20Launcher%20Reference.md).
- Within our Project’s root directory, go to*CRYENGINE Projects/<YourProjectName>/Code/Components* and delete *bullet.h***,** * SpawnPoint.cpp* and * SpawnPoint.h* - we will not be needing them.
The only files remaining within the Components folder should be *Player.h* and* Player.cpp*, which is where the bulk of our work will take place. While we will not delete these files, we will modify their contents later when we generate our solution.
- Next, right-click the.*cryproject* file corresponding to the project we just created, and select **Generate Solution** from the dropdown menu.
![Image](https://www.cryengine.com/docs/static/attachments/101679141)
*The Generate Solution option*This will create a new folder named *Solutions* within your project’s root directory, where our "solution" file (.sln), will reside. The solution file is a database of all of the game’s.cpp and.h files that we can modify.
- Within our new *Solutions* folder is a folder called *win64*. It contains quite a few files, but all you need to do is open the * Game.sln* file in your preferred version of Visual Studio, through which we can directly modify these.cpp and.h files.
![Image](https://www.cryengine.com/docs/static/attachments/101679142)
*Game.sln file in the win64 folder*
From the CRYENGINE Launcher, you can also click the![Image](https://www.cryengine.com/docs/static/attachments/101679116) button corresponding to your project and select **Open in Visual Studio** to open this same file.

#### Cleaning up GamePlugin.cpp and GamePlugin.h

Now that we've generated our solution, we must go into it and remove certain lines of code that are included in the First/Third Person Shooter templates but which will not be needed since they cause bloat and are subject to removal; this is to ensure that there are no conflicts later on.

We will now remove unnecessary lines, beginning with those which relate mainly to networking.

- Once*Game.sln* is open in Visual Studio, in the Solution Explorer, navigate to * Project>Game>GamePlugin.cpp*to begin. Proceed as indicated in the collapsible section below:
GamePlugin.cpp
- First at the top, delete:
```
#include "Components/Player.h"
```
This line is used for networking, to get a reference to the player; it is not needed for our player.
- Next, go into the destructor member section and remove the following:
```
// Remove any registered listeners before 'this' becomes invalid
if (gEnv->pGameFramework != nullptr)
{
gEnv->pGameFramework->RemoveNetworkedClientListener(*this);
}
```
- Next, delete the network lines under`Post Initialization`, as they are also networking lines:
```
// Listen for client connection events, in order to create the local player
gEnv->pGameFramework->AddNetworkedClientListener(*this);
```
- Under the `ESYSTEM_EVENT_LEVEL_UNLOAD`, delete the line:
```
m_players.clear();
```
- Lastly for our *GamePlugin.cpp,* there are four functions at the end which can all be removed, again, since they relate to networking. The lines to delete are as follows:
```
bool CGamePlugin::OnClientConnectionReceived(int channelId, bool bIsReset)
{
// Connection received from a client, create a player entity and component
SEntitySpawnParams spawnParams;
spawnParams.pClass = gEnv->pEntitySystem->GetClassRegistry()->GetDefaultClass();
// Set a unique name for the player entity
const string playerName = string().Format("Player%s%d" PRISIZE_T, m_players.size());
spawnParams.sName = playerName;
// Set local player details
if (m_players.empty() && !gEnv->IsDedicated())
{
spawnParams.id = LOCAL_PLAYER_ENTITY_ID;
spawnParams.nFlags |= ENTITY_FLAG_LOCAL_PLAYER;
}
// Spawn the player entity
if (IEntity* pPlayerEntity = gEnv->pEntitySystem->SpawnEntity(spawnParams))
{
// Set the local player entity channel id, and bind it to the network so that it can support Multiplayer contexts
pPlayerEntity->GetNetEntity()->SetChannelId(channelId);
// Create the player component instance
CPlayerComponent* pPlayer = pPlayerEntity->GetOrCreateComponentClass<CPlayerComponent>();
if (pPlayer != nullptr)
{
// Push the component into our map, with the channel id as the key
m_players.emplace(std::make_pair(channelId, pPlayerEntity->GetId()));
}
}
return true;
}
bool CGamePlugin::OnClientReadyForGameplay(int channelId, bool bIsReset)
{
// Revive players when the network reports that the client is connected and ready for gameplay
auto it = m_players.find(channelId);
if (it != m_players.end())
{
if (IEntity* pPlayerEntity = gEnv->pEntitySystem->GetEntity(it->second))
{
if (CPlayerComponent* pPlayer = pPlayerEntity->GetComponent<CPlayerComponent>())
{
pPlayer->OnReadyForGameplayOnServer();
}
}
}
return true;
}
void CGamePlugin::OnClientDisconnected(int channelId, EDisconnectionCause cause, const char* description, bool bKeepClient)
{
// Client disconnected, remove the entity and from map
auto it = m_players.find(channelId);
if (it != m_players.end())
{
gEnv->pEntitySystem->RemoveEntity(it->second);
m_players.erase(it);
}
}
void CGamePlugin::IterateOverPlayers(std::function<void(CPlayerComponent& player)> func) const
{
for (const std::pair<int, EntityId>& playerPair : m_players)
{
if (IEntity* pPlayerEntity = gEnv->pEntitySystem->GetEntity(playerPair.second))
{
if (CPlayerComponent* pPlayer = pPlayerEntity->GetComponent<CPlayerComponent>())
{
func(*pPlayer);
}
}
}
}
```
- That is all for cleaning up *Gameplugin.cpp*. Press **Ctrl + S** to save the progress, and now load up * GamePlugin.h*. Proceed as indicated in the collapsible section below:
GamePlugin.h
- As with *GamePlugin.cpp*, we will begin by removing lines relevant to networking. Delete the line:
```
#include <CryNetwork/INetwork.h>
```
- Since we won’t be accessing the player from our *GamePlugin.cpp*, delete the existing `Player Component` class line:
```
class CPlayerComponent;
```
- Delete the line:
```
, public INetworkedClientListener
```
- Underneath `INetworkClientListening` there are several lines which need to be deleted:
```
// INetworkedClientListener
// Sent to the local client on disconnect
virtual void OnLocalClientDisconnected(EDisconnectionCause cause, const char* description) override {}

// Sent to the server when a new client has started connecting
// Return false to disallow the connection
virtual bool OnClientConnectionReceived(int channelId, bool bIsReset) override;
// Sent to the server when a new client has finished connecting and is ready for gameplay
// Return false to disallow the connection and kick the player
virtual bool OnClientReadyForGameplay(int channelId, bool bIsReset) override;
// Sent to the server when a client is disconnected
virtual void OnClientDisconnected(int channelId, EDisconnectionCause cause, const char* description, bool bKeepClient) override;
// Sent to the server when a client is timing out (no packets for X seconds)
// Return true to allow disconnection, otherwise false to keep client.
virtual bool OnClientTimingOut(int channelId, EDisconnectionCause cause, const char* description) override { return true; }
// ~INetworkedClientListener
// Helper function to call the specified callback for every player in the game
void IterateOverPlayers(std::function<void(CPlayerComponent& player)> func) const;
```
- For *GamePlugin.h*, delete the player map, which is the only line under the `protected` class:
```
// Map containing player components, key is the channel id received in OnClientConnectionReceived
std::unordered_map<int, EntityId> m_players;
```
- Finally, press **Ctrl**+ ** Shift**+ ** S**to save the open * GamePlugin.h* and * GamePlugin.cpp*files.

Trying to build this will result in an error, so we now need to modify *Player.cpp* and* Player.h*.

#### Cleaning up Player.cpp and Player.h

Again, we need to remove not only the references to networking, but also the lines that we just removed from *GamePlugin.cpp* and * GamePlugin.h*.

- Using the Solution Explorer, open *Player.cpp*. Proceed as indicated in the collapsible section below:
Player.cpp
- To start, we can delete these `#include` lines at the top of our *Player.cpp*:
```
#include "Bullet.h"
#include "SpawnPoint.h"
#include <CryRenderer/IRenderAuxGeom.h>
#include <CryNetwork/Rmi.h>
```
- Delete everything below and including the following line:
```
void CPlayerComponent::Initialize():
```
- Save your progress with **Ctrl**+ ** Shift**+** S**, and open * Player.h*. Proceed as indicated in the collapsible section below:
Player.h
- Delete line **111** and every line below it, which corresponds to the implementation of pure virtual methods introduced by `INetworkedClientListener`:
```
void OnReadyForGameplayOnServer();
bool IsLocalClient() const { return (m_pEntity->GetFlags() & ENTITY_FLAG_LOCAL_PLAYER) != 0; }
protected:
void Revive(const Matrix34& transform);
void UpdateMovementRequest(float frameTime);
void UpdateLookDirectionRequest(float frameTime);
void UpdateAnimation(float frameTime);
void UpdateCamera(float frameTime);
void HandleInputFlagChange(CEnumFlags<EInputFlag> flags, CEnumFlags<EActionActivationMode> activationMode, EInputFlagType type = EInputFlagType::Hold);
// Called when this entity becomes the local player, to create client specific setup such as the Camera
void InitializeLocalPlayer();
// Start remote method declarations
protected:
// Parameters to be passed to the RemoteReviveOnClient function
struct RemoteReviveParams
{
// Called once on the server to serialize data to the other clients
// Then called once on the other side to deserialize
void SerializeWith(TSerialize ser)
{
// Serialize the position with the 'wrld' compression policy
ser.Value("pos", position, 'wrld');
// Serialize the rotation with the 'ori0' compression policy
ser.Value("rot", rotation, 'ori0');
}
Vec3 position;
Quat rotation;
};
// Remote method intended to be called on all remote clients when a player spawns on the server
bool RemoteReviveOnClient(RemoteReviveParams&& params, INetChannel* pNetChannel);
protected:
bool m_isAlive = false;
Cry::DefaultComponents::CCameraComponent* m_pCameraComponent = nullptr;
Cry::DefaultComponents::CCharacterControllerComponent* m_pCharacterController = nullptr;
Cry::DefaultComponents::CAdvancedAnimationComponent* m_pAnimationComponent = nullptr;
Cry::DefaultComponents::CInputComponent* m_pInputComponent = nullptr;
Cry::Audio::DefaultComponents::CListenerComponent* m_pAudioListenerComponent = nullptr;
FragmentID m_idleFragmentId;
FragmentID m_walkFragmentId;
TagID m_rotateTagId;
CEnumFlags<EInputFlag> m_inputFlags;
Vec2 m_mouseDeltaRotation;
MovingAverage<Vec2, 10> m_mouseDeltaSmoothingFilter;
const float m_rotationSpeed = 0.002f;
int m_cameraJointId = -1;
FragmentID m_activeFragmentId;
Quat m_lookOrientation; //!< Should translate to head orientation in the future
float m_horizontalAngularVelocity;
MovingAverage<float, 10> m_averagedHorizontalAngularVelocity;
```
- Delete the following networking lines:
```
/ IEntityComponent
virtual void Initialize() override;
virtual Cry::Entity::EventFlags GetEventMask() const override;
virtual void ProcessEvent(const SEntityEvent& event) override;
virtual bool NetSerialize(TSerialize ser, EEntityAspects aspect, uint8 profile, int flags) override;
virtual NetworkAspectType GetNetSerializeAspectMask() const override { return InputAspect; }
// ~IEntityComponent
```
- Lastly, we have lines for `Enums` and ` class`, which also relate to networking and input flags, and can be deleted:
```
enum class EInputFlagType
{
Hold = 0,
Toggle
};
enum class EInputFlag : uint8
{
MoveLeft = 1 << 0,
MoveRight = 1 << 1,
MoveForward = 1 << 2,
MoveBack = 1 << 3
};
static constexpr EEntityAspects InputAspect = eEA_GameClientD;
template<typename T, size_t SAMPLES_COUNT>
class MovingAverage
{
static_assert(SAMPLES_COUNT > 0, "SAMPLES_COUNT shall be larger than zero!");
public:
MovingAverage()
: m_values()
, m_cursor(SAMPLES_COUNT)
, m_accumulator()
{
}
MovingAverage& Push(const T& value)
{
if (m_cursor == SAMPLES_COUNT)
{
m_values.fill(value);
m_cursor = 0;
m_accumulator = std::accumulate(m_values.begin(), m_values.end(), T(0));
}
else
{
m_accumulator -= m_values[m_cursor];
m_values[m_cursor] = value;
m_accumulator += m_values[m_cursor];
m_cursor = (m_cursor + 1) % SAMPLES_COUNT;
}
return *this;
}
T Get() const
{
return m_accumulator / T(SAMPLES_COUNT);
}
void Reset()
{
m_cursor = SAMPLES_COUNT;
}
private:
std::array<T, SAMPLES_COUNT> m_values;
size_t m_cursor;
T m_accumulator;
};
```
- Delete all `#include` lines within *Player.h*:
```
#include <array>
#include <numeric>
#include <CryEntitySystem/IEntityComponent.h>
#include <CryMath/Cry_Camera.h>
#include <ICryMannequin.h>
#include <CrySchematyc/Utils/EnumFlags.h>
#include <DefaultComponents/Cameras/CameraComponent.h>
#include <DefaultComponents/Physics/CharacterControllerComponent.h>
#include <DefaultComponents/Geometry/AdvancedAnimationComponent.h>
#include <DefaultComponents/Input/InputComponent.h>
#include <DefaultComponents/Audio/ListenerComponent.h>
```
- And finally, delete the `Mouse_Delta_Threshold` line:
```
#define MOUSE_DELTA_TRESHOLD 0.0001f
```
- Press **Ctrl** + **Shift** + **S** to save your progress across all tabs, and **Ctrl** + **Shift** + **B** to build. You should receive the following error:
![Image](https://www.cryengine.com/docs/static/attachments/101679146)*Unrecognized class error*
- The reason for this error is that it does not recognize the class, and we need to include it. To fix this, add this line to your *Player.cpp*:
```
#include <CrySchematyc/Env/IEnvRegistrar.h>
```
- Save your progress and build your solution by pressing **Ctrl**+ ** Shift**+ ** B**. No errors should pop-up this time.

At this point, *GamePlugin.cpp* and * GamePlugin.h* are complete, and * Player.cpp* and * Player.h* are also ready to be built upon. You can now close the * GamePlugin.cpp* and * GamePlugin.h* as we will no longer be touching these.

### Creating a Player

Now that we have removed the lines which we won’t be needing in our Game solution, we can start to add lines that will serve as the base interface for our playable character – we call these Components.

#### Adding Components

In *Player.h*, we will start forming our header.

It is common practice in headers to have a `public` section at the top for your publicly-accessible members, a `protected` section below for your inherited members, and a ` private` section last for member variables or functions you don’t want anything else to access.

![Image](https://www.cryengine.com/docs/static/attachments/101679147)

*Public, protected and private sections*

- Start by adding the `CCameraComponent` under our ` private` section:
```
Cry::DefaultComponents::CCameraComponent* m_pCameraComponent;
```
- You may notice that after adding this line, our `CCameraComponent` is underlined in red. That is because we need to add the relevant `#include` lines at the top of the header:
```
#include <DefaultComponents/Cameras/CameraComponent.h>
```
- We will follow these steps for each component. Next up, we will add our `CInputComponent` by including this line underneath the ` private` section:
```
Cry::DefaultComponents::CInputComponent* m_pInputComponent;
```
- Now add the`#include` line corresponding to our ` CInputComponent` up top:
```
#include <DefaultComponents/Input/InputComponent.h>
```
- Next, add the `CCharacterControllerComponent` line:
```
Cry::DefaultComponents::CCharacterControllerComponent* m_pCharacterController;
```
- And the relevant `#include` line:
```
#include <DefaultComponents/Physics/CharacterControllerComponent.h>
```
- The last component we will add is the `CAdvancedAnimationComponent`:
```
Cry::DefaultComponents::CAdvancedAnimationComponent* m_pAdvancedAnimationComponent;
```
- Followed by the last `#include` line:
```
#include <DefaultComponents/Geometry/AdvancedAnimationComponent.h>
```
![Image](https://www.cryengine.com/docs/static/attachments/101679148)
*The final list of added Components with the corresponding #include lines*

#### Adding Initialize to Components

A lot of things can get called throughout the run-time of a game, things like "Reset", "Awake", "GameplayStarted"; within our `IEntityComponent`, which is the base interface of our current player. We can add a few of these, but first we need add an ` Initialize`, which is called at the very first initialization of the component: the creation time in game run-time.

This `Initialize` is a great occasion to call upon some of the components, such that they are called upon immediately when the player is loaded in the game.

- In order to use this method, we need to call upon the Initialize by adding this call in our *Player.h*:
```
virtual void Initialize() override;
```
- Since we declared it, we now need to define it in our *Player.cpp*. This is what the red underline in this newly added line is eluding to. Highlight and right-click `Initialize()`, select **Quick Actions and Refactorings**, and select ** Create Definition**of "Initialize" in* Player.cpp*.
- Within the curly-brackets underneath our void`CPlayerComponent::Initialize`, add these definitions for each of our components:
```
m_pCameraComponent = m_pEntity->GetOrCreateComponent<Cry::DefaultComponents::CCameraComponent>();
m_pInputComponent = m_pEntity->GetOrCreateComponent<Cry::DefaultComponents::CInputComponent>();
m_pCharacterController = m_pEntity->GetOrCreateComponent<Cry::DefaultComponents::CCharacterControllerComponent>();
m_pAdvancedAnimationComponent = m_pEntity->GetOrCreateComponent<Cry::DefaultComponents::CAdvancedAnimationComponent>();
```
Now, when we add our `CPlayerComponent` to an Entity in CRYENGINE, all of these components will be added to it.

#### Player Component - Adding Inputs

We will now add our Inputs, both keyboard and mouse, so that we can look and walk around as a player. We need to tell CRYENGINE what keys and mouse axes we want to use, and for what. Later on in the tutorial, we will tell CRYENGINE how we want these inputs to function and when to load them with EventFlags.

- To get started, we can add Register Actions and Bind Actions to our added Input Component so that we can move.
- First, in our *Player.h*, underneath the `private` section, create the member variable:
```
void InitializeInput();
```
- Next in our *Player.h*, also underneath the `private` section, we will also create a member variable and name it * movementDelta*:
```
Vec2 m_movementDelta;
```
- With our member variables defined in our header, we now need to go into *Player.cpp* and add both the `InitializeInput()` to our `CPlayerComponent`:
![Image](https://www.cryengine.com/docs/static/attachments/101679177)
*InitializeInput() inCPlayerComponent*
- Within the curly-brackets in our new`InitializeInput()`, we will add our ` RegisterAction` line, and for the value at the end add our new *movementaDelta* member variable. The complete ` RegisterAction` line:
```
m_pInputComponent->RegisterAction("player", "moveforward", [this](int activationMode, float value) {m_movementDelta.y = value});
```
- Now that we have our `RegisterAction`, we need something to call it: a key. This will be a ` BindAction` line, and we will add this right underneath our` RegisterAction,` which will assign the **W** key as our forward movement input:
```
m_pInputComponent->BindAction("player", "moveforward", eAID_KeyboardMouse, eKI_W);
```
- Now, we want to repeat this step for the rest of the keys we would like to register and bind, which would be the **A**, ** S**, and ** D** keys. For that, you can copy and paste the completed input line.
```
m_pInputComponent->RegisterAction("player", "moveforward", [this](int activationMode, float value) {m_movementDelta.y = value});
m_pInputComponent->BindAction("player", "moveforward", eAID_KeyboardMouse, eKI_W);
```
- For each of the keys, change the name of the action and`eKI` to the key you want to assign that action (ex. “movebackward” and “eKI_S”).
Another important difference for each of these input lines is that the `m_movementDelta` will now be` movementDelta.x` or ` movementDelta.y` depending on the axis we want for the assigned key. (Right/left is X axis, forward/back is Y axis. While these changes will reflect the axis, we also want to change the value to assign which specific direction on that axis each key moves the player).
This can be set by changing the value to a negative. (ex. "moveforward’ is an **=value** on the Y axis, while ‘movebackward’ would be **=-value**.)
- Once the keys are all added, add a `RegisterAction` and ` BindAction` line for each of the mouse axes:
```
m_pInputComponent->RegisterAction("player", "yaw", [this](int activationMode, float value) {m_mouseDeltaRotation.y = -value;  });
m_pInputComponent->BindAction("player", "yaw", eAID_KeyboardMouse, eKI_MouseY);
```
![Image](https://www.cryengine.com/docs/static/attachments/101679181)

*The complete input lines for the **W**, ** A**, ** S** and ** D** keys.*

The only difference between them, other than the names and key inputs, is the value is set to "-value"’, or negative value, so it provides the opposite m_movementDelta value.

#### Player Component – GetEventMask

After your inputs are in, we need to tell CRYENGINE which Events we want to use throughout game run-time, as well as what we would like to apply them to. We will be using `GameplayStarted`, and applying it to our ` CPlayerComponent`.

- Let's add the `public` method declarations that we will be adding to our *Player.cpp* later. Underneath the ` public` section of *Player.h,* add:
```
virtual Cry::Entity::EventFlags GetEventMask() const override;
virtual void ProcessEvent(const SEntityEvent& event) override;
```
![Image](https://www.cryengine.com/docs/static/attachments/101679183)
*The added lines under the public section in Player.h*
- With these declared, we can now add the relevant lines into our *Player.cpp*. Within * Player.cpp*, underneath our inputs, create a new line and add the Events we will be using:
```
Cry::Entity::EventFlags CPlayerComponent::GetEventMask() const
{
return Cry::Entity::EEvent::GameplayStarted | Cry::Entity::EEvent::Update |  Cry::Entity::EEvent::Reset;
}
```
- The events we clarified we want to use are `GameplayStarted`, `Update`and `Reset`. So far we have only declared `GameplayStarted`.![Image](https://www.cryengine.com/docs/static/attachments/101679155)
*Note that the events are separated by the “|” key, and not by the “:” or “;” keys which you may be used to seeing*
Under `GameplayStarted` will be anything we want to get called on game start, under `Update`will be anything we want called repeatedly and quickly, and under `Reset`we will call for certain variables to be reset upon quitting the game.

#### ProcessEvent – GameplayStarted

Now that we have specified the Events processed by the Component, we can begin to define how we want to implement them to give them purpose.

- Before we add any of our Events, we need to create a `ProcessEvent` so that we can specify which actions should be done on a specific event for this instance of the Component. For this, we must clarify that we want to use ` CPlayerComponent` to process our Event by adding the following lines underneath the Event Masks in *Player.cpp*:
```
void CPlayerComponent::ProcessEvent(const SEntityEvent & event)
{
switch (event.event)
}
```
- Then, within our `switch` statement, we can define our first Event, which is ` GameplayStarted`. We want to tell it to process our input via ` InitializeInput``()`; at the start of our game. Within our ` switch`, we will add:
```
{
case Cry::Entity::EEvent::GameplayStarted:
{
InitializeInput();
}
break;
```
![Image](https://www.cryengine.com/docs/static/attachments/101679158) *Defining GameplayStarted*
These are the lines where we tell CRYENGINE which events we will be using, followed by adding this event and the details of what we want it to do, to call on our `InitializeInput``();` at the start of `CPlayerComponent`, which is at the start of our game.

#### Preparing and finalizing the Player.h

Before we add anything to our `Update`, we need to first create the members that we expect to be called within it. Things like player movement, look orientation, movement deltas and rotation speeds are a few of the members we will want to define.

In this instance, "Update" means anything we want to update continuously throughout our game run-time. Under `Update`will be the specific details on how our player moves through the world. While we defined what buttons we will press to do this, we still need to write the code on what actually happens when we trigger these inputs.

- Add the full list of the members underneath the `private` section in our *Player.h*(the names of these members can be whatever suits your intent):
```
void PlayerMovement();
Quat m_lookOrientation;
Vec3 m_camerDefaultPos;
Vec2 m_movementDelta;
Vec2 m_mouseDeltaRotation;
float m_movementSpeed;
float m_rotationSpeed;
float m_rotationLimitsMinPitch;
float m_rotationLimitsMaxPitch;
```
![Image](https://www.cryengine.com/docs/static/attachments/101679159)*The final list of what to add under the private section of Player.h*
While the names given to these members might tip off what we will be using them for, you may notice some are `Quat`, some are `void`, `Vec2`, `Vec3` and `float`. These are return types;
- `void` specifies that the function doesn't return a value.
- `Quat` is a quaternion rotation
- `Vec2` represents a 2D vector.
- `Vec3` represents a 3D vector.
- `float` defines numeric values with floating decimal points.
- With our `private` section updated in *Player.h*, the last thing we need to do is ` AddMember`. This will add our members to ` CPlayerComponent`, so that we can modify the values directly within CRYENGINE via the [Properties tool](../../../Editor%20Tools/Level%20Editor%20Tab/Properties.md) when we add and select our Player Entity. Under the ` ReflectType` in *Player.h*, add an ` AddMember` line along with the name and a brief description for each of the members:
```
desc.AddMember(&CPlayerComponent::m_movementSpeed, 'pms', "playermovespeed", "Player Movement Speed", "Sets the Player Move Speed", ZERO);
desc.AddMember(&CPlayerComponent::m_rotationSpeed, 'pros', "playerrotationspeed", "Player Rotation Speed", "Sets the speed of the players rotation", ZERO);
desc.AddMember(&CPlayerComponent::m_camerDefaultPos, 'cdp', "cameradefaultpos", "Camera Default Position", "Sets camera default position", ZERO);
desc.AddMember(&CPlayerComponent::m_rotationLimitsMaxPitch, 'cpm', "camerapitchmax", "Camera Pitch Max", "Maximum rotation value for camera pitch", 1.5f);
desc.AddMember(&CPlayerComponent::m_rotationLimitsMinPitch, 'cpmi', "camerapitchmin", "Camera Pitch Min", "Minimum rotation value for camera pitch", -0.85f);
```
All the members in this list will be able to be modified directly in CRYENGINE by inputing custom values in the **Properties** of the Player Entity.
![Image](https://www.cryengine.com/docs/static/attachments/101679249)

*The final list of what to add under the private section of Player.h*

#### Defining Update in Player.cpp

So far we have completed our *Player.h*, added all of the members we intend to use, and specified the first Event for * Player.cpp*. Now that we completed our * Player.h* and have seen how we can add Events, we will add the last two Events to our * Player.cpp* – `Update` and ` Reset`.

- First, we want to add the case, and to specify that we want the Event to be updated. Add the following line:
```
case Cry::Entity::EEvent::Update:
{
}
```
- Within `Update`, we want to add the ` private` function which we intend to use. Anything under ` Update`will be called upon continuously throughout the game runtime, so makes sense for us to include our ` PlayerMovement` here. Within ` Update`, add:
```
Ang3 rotationAngle = CCamera::CreateAnglesYPR(Matrix33(m_lookOrientation));
rotationAngle.x += m_mouseDeltaRotation.x * m_rotationSpeed;
rotationAngle.y = CLAMP(rotationAngle.y + m_mouseDeltaRotation.y * m_rotationSpeed, m_rotationLimitsMinPitch, m_rotationLimitsMaxPitch);
rotationAngle.z = 0;
m_lookOrientation = Quat(CCamera::CreateOrientationYPR(rotationAngle));
Ang3 yawAngle = CCamera::CreateAnglesYPR(Matrix33(m_lookOrientation));
yawAngle.y = 0;
const Quat finalYaw = Quat(CCamera::CreateOrientationYPR(yawAngle));
m_pEntity->SetRotation(finalYaw);
Ang3 pitchAngle = CCamera::CreateAnglesYPR(Matrix33(m_lookOrientation));
pitchAngle.x = 0;
Matrix34 finalCamMatrix;
finalCamMatrix.SetTranslation(m_pCameraComponent->GetTransformMatrix().GetTranslation());
Matrix33 camRotation = CCamera::CreateOrientationYPR(pitchAngle);
finalCamMatrix.SetRotation33(camRotation);
m_pCameraComponent->SetTransformMatrix(finalCamMatrix);
```
It's easier to understand this code block if you notice that each `Ang3` is defining one of the three axes – the ` rotationAngle`, the ` yawAngle`, and the ` pitchAngle`.
With this setup, the camera will pivot up and down when looking up and down on the pitch axis independently and separate from the player’s body, but when looking left and right on the yaw axis, the player’s body will rotate with the camera. This is to prevent the player’s body from moving in strange ways when looking up or down by separating the `CCamera` from the player only on. This is achieved by creating Matrix33 and Matrix34 functions named ` camRotation` and ` finalCamMatrix` and nullifying the ` pitchAngle.x` and` yawAngle.y` to ` 0`.
Note that the `CLAMP` is only added to the `rotationAngle.y`, since we only want to clamp the mouse when looking up or down.

#### Defining Reset in Player.cpp

We added `GameplayStarted` and ` Update`, and now we need to add ` Reset`. ` Reset`is what we want to reset to zero upon closing the game. Therefore, the members we want to reset in this case are ` movementDelta`, ` mouseDeltaRotation` and ` lookOrientation`.

- Start by adding the case line for `Reset`:
```
case Cry::Entity::EEvent::Reset:
{
}
```
- Within the curly-brackets, we can add the members we want to`Reset` upon game close:
```
m_movementDelta = ZERO;
m_mouseDeltaRotation = ZERO;
m_lookOrientation = IDENTITY;
```
You may notice that the first two members are set to “`ZERO`” on ` R``eset`, while ` lookOrientation` is set to “` IDENTITY`”. "` IDENTITY`" is zero rotation on all axis – which makes sense since ` lookOrientation`is a ` Quat`, and so is on multiple axis.
- Next, we want to make sure to reset the`camDefaultMatrix` seen in the ` Ang3` ` pitchAngle,` so that the camera is always reset.
Skipping this step can result in issues such as spawning in and facing backwards.
To do this, add the relevant lines to the `Reset`:
```
Matrix34 camDefaultMatrix;
camDefaultMatrix.SetTranslation(m_camerDefaultPos);
camDefaultMatrix.SetRotation33(Matrix33(m_pEntity->GetWorldRotation()));
m_pCameraComponent->SetTransformMatrix(camDefaultMatrix);
```
- We want to end this last case with a break, and so our complete `Reset` should look like this:
![Image](https://www.cryengine.com/docs/static/attachments/101679188)*Complete Reset section*

#### Finalizing Player Movement

Our last step can be considered the missing link, as we have yet to define our player’s walking movement. To do this, we are going to call upon the `PlayerMovement`(), the ` private` function that we added in our *Player.h*, and define it with ` movementDelta` and ` movementSpeed`.

- First add the `PlayerMovement` to our ` CPlayerComponent` by adding the line:
```
void CPlayerComponent::PlayerMovement()
{
}
```
- Within the curly-brackets of `PlayerMovement``()`, we need to add the ` Vec3` for our velocity that will equal our movement by adding:
```
Vec3 velocity = Vec3(m_movementDelta.x, m_movementDelta.y, 0.0f);
```
- Next we need to normalize the movement. In older games, pressing “forward” and “left” or “right” at the same time would result in an overall higher running speed, as it would combine both of the movement values at the same time. With a normalize line added, it will do vector math to calculate the average speed when you press two movement keys at once, making it impossible to go faster than the movement speed you set for those keys.
```
velocity.Normalize();
```
- The last line we will add to `PlayerMovement` is for` m_pCharacterController`:
```
m_pCharacterController->SetVelocity(m_pEntity->GetWorldRotation() * velocity *          m_movementSpeed);
```
![Image](https://www.cryengine.com/docs/static/attachments/101679187)
*Last line in PlayerMovement*
- To finish everything off, press **Ctrl**+ ** Shift**+ ** S** to save all tabs, and ** Ctrl**+ ** Shift**+ ** B** to build the completed solution.

![Image](https://www.cryengine.com/docs/static/attachments/101679186)

*The completed Player Movement section*

### Testing the Character

Once the solution is built, we can now test the character in CRYENGINE. Begin by launching the Sandbox Editor directly from Visual Studio:

- By default, clicking the **Local Windows Debugger** button at the top will launch our project in the [Game Executable Launcher](../../../Packaging%20and%20Deployment/Game%20Executable%20Launcher.md). We want to change this so that when the project is launched from Visual Studio, it runs CRYENGINE Sandbox in Editor Mode. To do this, go to the Solution Explorer and right-click on **Editor** → **Set as StartUp Project**.
![Image](https://www.cryengine.com/docs/static/attachments/101679199)*Defining the Sandbox Editor as the default project launch application*
- Once that is done, click **Windows Local Debugger** and launch the project.
- After opening a level, navigate to the **Create Object** panel and place an ** Empty Entity**in your scene. For clarity, name it something like "Player".
- Within the properties of this new “Player” Entity, click **+Add Component** and select the **CPlayerComponent** that should now be available.
![Image](https://www.cryengine.com/docs/static/attachments/101679198)![Image](https://www.cryengine.com/docs/static/attachments/101679197)
*CPlayerComponent Entity Component properties*
- With the**CPlayerComponent** added to our “*Player*” Entity, you can now configure different variables such as walking speed, camera position, rotation speed, etc.
Recommended Values
**Player Movement Speed**:Values between ** 3-5** correspond to a reasonable walking speed.
**Player Rotation Speed**: Rotation speed is very sensitive, so you should set it to a low value such as ** 0.002**.
**Camera Default Position**: Modify the Camera’s height (position in the Z axis) to reflect that of the average human height. Any value between ** 1.5** and ** 2** can fit this criteria.
**Camera Pitch Max/Min**: Set the camera clamping to ** 1.5** (Max) and **-0.85** (Min) - these values limit how far the player character can tilt its head back or forwards.

With these variables set for your Player Entity’s **CPlayerComponent** properties, you can now press ** Ctrl + G** and test the game with your very own playable character.

### Conclusion

This concludes the tutorial. To learn more about C++ in CRYENGINE and/or other topics, please refer to the [CRYENGINE V Manual](/docs/static/engines/cryengine-5/categories/23756816/pages/23307414).

### Video Tutorial

You can also follow this tutorial series in video form on our YouTube channel:

[Embed: https://www.youtube.com/watch?v=63PuJoVoQMg]

### Related Information

[Tutorial - Coding in C++ - Creating a Player Controller - CRYENGINE Summer Academy](https://youtu.be/xKTygGa6hg0)

[Prerequisites](#prerequisites)[Getting Started](#getting-started)[Creating a Player](#creating-a-player)[Testing the Character](#testing-the-character)[Conclusion](#conclusion)[Video Tutorial](#video-tutorial)[Related Information](#related-information)
