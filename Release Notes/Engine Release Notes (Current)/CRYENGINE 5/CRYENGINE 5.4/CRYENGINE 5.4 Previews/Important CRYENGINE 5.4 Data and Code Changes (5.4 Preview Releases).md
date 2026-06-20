# Important CRYENGINE 5.4 Data and Code Changes (5.4 Preview Releases)

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/47316993/pages/44962727
- Page ID: 44962727
- Breadcrumb: Engine Release Notes (Current) > CRYENGINE 5 > CRYENGINE 5.4 > CRYENGINE 5.4 Previews > Important CRYENGINE 5.4 Data and Code Changes (5.4 Preview Releases)
- Parent: CRYENGINE 5.4 Previews

## Content

The following is not intended to be a complete list of CRYENGINE 5.4 C++ API changes, rather it is an indication of the most important changes that Programmers need to be aware of.

##
Table of Contents

##
Visual Studio Support

CRYENGINE 5.4.0 introduces support for Visual Studio 2017. In addition, Visual Studio 2015 users are required to install Update 3 in order to successfully compile the 5.4.0 version of Engine source code.

##
Deprecation Notices

This release officially deprecates:

-
Game Objects (IGameObject, IGameObjectExtension - Replaced with the new Entity Components (IEntityComponent). Note: (IGameObject, IGameObjectExtension will be removed in a future Engine release.

-
Game Rules (IGameRulesSystem, IGameRules) - Replaced with INetworkedClientListener (see below for more information).

-
Actors (IActorSystem, IActor) - Replaced by the new Entity Components, to be used in-conjunction with INetworkedClientListener.

-
5.3.0 standard entities (see below for more information) - Replaced with new Standard Components.

-
Legacy Game Folders (sys_game_folder, sys_dll_game) - Replaced with the Project System. Note: Automatic migration (after running 5.4.0 for the first time) will be performed. The old game folder support will be removed in a future Engine update.

-
CryPlugin.csv - Replaced with the Project System. Automatic migration will be performed on first boot, moving all plug-ins into your .cryproject file.
Keep in mind that the legacy GameSDK project uses many deprecated systems and it will be dropped in the future. However, we have not yet marked it as deprecated, because we are waiting for the templates to accurately match the functionality of the GameSDK first.

##
Entity System & Schematyc

##
Schematyc

The new Entity Component system (that was introduced with CRYENGINE 5.3.0) has been adjusted in order to unify with the Schematyc setup. This means that any component exposed with the new 5.4.0 format (example below) will automatically become available in the Inspector and Schematyc so that Designers can build more complex logical entities.

The existing 5.3.0 method of creating components is still available, however we'll be phasing it out over time as the new unified setup matures. Part of evolving the new setup will be to reduce the amount of code required to expose a component, so keep in mind that the example below will not be as rough in the future:

```

`
#include <CrySchematyc/CoreAPI.h>
class CMyComponent final : public IEntityComponent
{
public:
  static CryGUID& IID()
  {
    static CryGUID id = "{AD383B41-C144-4F99-9A2B-0FA2D9D86245}"_cry_guid;
    return id;
  }

  void MyFunction()
  {
    // Print to the console
    CryLogAlways("Hello world!");

    // Signals can only be sent when the component was attached through Schematyc
    if(Schematyc::IObject* pObject = m_pEntity->GetSchematycObject())
    {
      // Send the signal back to Schematyc, along with our instance GUID
      pObject->ProcessSignal(SMySignal { m_bSignalResult }, GetGUID());
    }
  }
  struct SMySignal { bool m_bReturnValue; };
  bool m_bSignalResult = false;
};
void ReflectType(Schematyc::CTypeDesc<CMyComponent>& desc)
{
  desc.SetGUID(CMyComponent::IID());
  desc.SetEditorCategory("MyCategory");
  desc.SetLabel("MyComponent");
  desc.SetDescription("Does awesome things!");
  desc.SetComponentFlags({ IEntityComponent::EFlags::Socket, IEntityComponent::EFlags::Attach });
  desc.AddMember(&CMyComponent::m_myMember, 'memb', "MyMember", "My Member", "A property that can be changed", 10);
}
static void ReflectType(Schematyc::CTypeDesc<CMyComponent::SMySignal>& desc)
{
  desc.SetGUID("{DBBDB49C-6C48-446E-9451-DAA32E6FA240}"_cry_guid);
  desc.SetLabel("My Signal");
  desc.AddMember(&CMyComponent::SMySignal::m_bReturnValue, 'ret', "ReturnVal", "Return Value", "Description", false);
}
static void RegisterMyComponent(Schematyc::IEnvRegistrar& registrar)
{
  Schematyc::CEnvRegistrationScope scope = registrar.Scope(IEntity::GetEntityScopeGUID());
  {
    Schematyc::CEnvRegistrationScope componentScope = scope.Register(SCHEMATYC_MAKE_ENV_COMPONENT(CMyComponent));
    // Functions
    {
      auto pFunction = SCHEMATYC_MAKE_ENV_FUNCTION(&CMyComponent::MyFunction, "{FE5B34ED-A5DD-4C3B-A81C-38B5D980A770}"_cry_guid, "MyFunction");
      pFunction->SetDescription("Triggers our test function");
      componentScope.Register(pFunction);
    }
    // Signals
    componentScope.Register(SCHEMATYC_MAKE_ENV_SIGNAL(CMyComponent::SMySignal));
  }
}
CRY_STATIC_AUTO_REGISTER_FUNCTION(&RegisterMyComponent);
`

```

##
Standard Components

The default entities introduced with CRYENGINE 5.3.0 are still part of the Engine, but are now considered deprecated and will be removed in a future Engine release. These entities are no longer available for creation in the Sandbox Editor, but existing instances will continue to work.

The new standard components can be used by Designers as well as Programmers using C++. For example, the updated 5.4 templates heavily utilize the new standard components in order to cut down on the amount of code required when getting started. The new components can be included with the path <DefaultComponents/...`>.

The components all reside in the Cry::DefaultComponents namespace.

##
Miscellaneous

-
EntityGUID is now a proper 128-bit GUID. Parsing of legacy 64-bit GUIDs will still work, but convert on export.

-
IEntity::Activate has been removed. Individual components can now return BIT64(ENTITY_EVENT_UPDATE) in GetEventMask and call UpdateComponentEventMask to trigger re-activation.

-
For legacy code, use IGameObject::ForceUpdate(true) to mimic the same behavior as before.

-
IEntity::IsActive has been renamed to IsActivatedForUpdates.

-
IEntityComponent functions PreInit, Initialize, OnShutDown, OnTransformChanged, ProcessEvent and Run are now protected and can thus not be called from outside the component itself.

-
If you need to send an event to a specific component, use IEntityComponent::SendEvent.

##
Templates

The templates have been refactored to require much less code for the same end result.
New systems have also been introduced, which have allowed us to remove dependencies on legacy systems:

-
Replaced IGameObject and IGameObjectExtension usage - Now using the new IEntityComponent system directly.

-
Removed large blocks of duplicated code across templates - Now using the new Standard Components in order to simplify the creation of basic gameplay.

-
Replaced IGameRules and IActor - Now using INetworkedClientListener (see below for more information) and IEntityComponent directly. Games no longer need to utilize the legacy actor system to support players.

##
Network

Refactoring of our network is in progress and will start with the public API. The goal is to remove network dependencies (in the legacy CryAction module) in order to simplify how games can utilize networking in code. This is also preparation for a future refactoring of our network internals.

##
Receiving Client Connection Callbacks

INetworkedClientListener and INetwork::AddNetworkedClientListener was added as an alternative for the legacy game rules system. This interface can be used to receive callbacks when clients connect over the network, making it possible to skip usage of game rules in projects. The templates have been updated to utilize this.

##
Remote Method Invocation (RMI) Support for New Entity Components

In the initial 5.3.0 Engine release, the new Entity Component system did not support RMI's, this has now been corrected and allows new entity code to be networked. See example below.

```

`
#include <CryNetwork/Rmi.h>
class CNetworkedComponent final : public IEntityComponent
{
  virtual void Initialize() final
  {
    SRmi<RMI_WRAP(&CNetworkedComponent::RemoteEntityMethod)>::Register(this, eRAT_NoAttach, false, eNRT_ReliableOrdered);
    m_pEntity->GetNetEntity()->BindToNetwork();
  }
  // Parameters to serialize an entity id across the network
  struct SEntityParams
  {
    EntityId entityId;
    void SerializeWith(TSerialize ser)
    {
      // Called to serialize and deserialize the entity id, note the 'eid' policy
      // This policy is used to convert entity identifiers between machines as id's are not unique over the network.
      ser.Value("entityId", entityId, 'eid');
    };
  };
  bool RemoteEntityMethod(SEntityParams&& params, INetChannel* pNetChannel)
  {
    if (IEntity* pEntity = gEnv->pEntitySystem->GetEntity(params.entityId))
    {
      // Success!
    }
    // Return true to indicate that RMI was valid, a value of false indicates that something went wrong - for example validation of input indicates cheating.
    return true;
  }
  void InvokeRemoteEntityMethod(EntityId id)
  {
    SRmi<RMI_WRAP(&CNetworkedComponent::RemoteEntityMethod)>::InvokeOnRemoteClients(this, SEntityParams{ id }, id);
  }
};
`

```

##
Network Aspect Serialization for New Entity Components

In addition to RMI's, 5.4 also introduces support for serializing chunks of data as aspects over the network. This can be useful, for example to synchronize player input of a player. We've attached an example below:

```

`
class CNetworkedAspectComponent final : public IEntityComponent
{
  virtual void Initialize() final
  {
    m_pEntity->GetNetEntity()->BindToNetwork();
  }
  virtual NetworkAspectType GetNetSerializeAspectMask() const final { return 1 << GetNetSerializationAspect(); }
  // Called when serializing and deserializing
  virtual bool NetSerialize(TSerialize ser, EEntityAspects aspect, uint8 profile, int flags) final
  {
    if (aspect == GetNetSerializationAspect())
    {
      // Serialize or deserialize our flags, note that the optional third parameter specifies the selected compression policy
      ser.Value("m_flags", m_flags);
    }
  }
  const EEntityAspects GetNetSerializationAspect() const { return eEA_GameClientD; }
  // Call when m_flags changes and we want to serialize the data to the other machines.
  void RequestNetSyncToOthers() { m_pEntity->GetNetEntity()->MarkAspectsDirty(GetNetSerializationAspect()); }
  uint32 m_flags;
};
`

```

##
Animation

-
IAnimEventPlayerGame introduced - Replaces hardcoded string lookup.

-
The Character Tool previously found the game's custom IAnimEventPlayer implementation by searching for a class with the name of the 'sys_game_name' CVar. This has now been removed. Instead, the system now searches for the first IAnimEventPlayerGame implementation it can find and exposes that to the Character Tool.

-
IAnimationPoseAligner::Update - Now takes character instance.

-
IActionController::FindOrCreateProceduralContext - Can no longer take a string, instead passes the class id, for example CProceduralContextRagdoll::GetCID()

##
Audio

-
The entirety of the audio interfaces have been refactored to utilize the new CryAudio namespace.

-
For example, AudioControlId is now CryAudio::ControlId.

##
Asset Browser & Paths

-
Engine assets can no longer be loaded through the "Engine/EngineAssets" path - This will now have to be changed to "%ENGINE%/EngineAssets". Engine assets will automatically show up in the Asset Browser, and will use the new path automatically.

##
Miscellaneous

-
CryCreateClassInstance(const char*,  std::shared_ptr<T>&) - Has been removed, please use CryCreateClassInstance(const CryClassID& cid, std::shared_ptr<T>& p) or CryCreateClassInstanceForInterface(const CryInterfaceID& iid, std::shared_ptr<T>& p).

-
For example, CryCreateClassInstance("AnimationPoseModifier_OperatorQueue", m_poseModifier); becomes CryCreateClassInstanceForInterface(cryiidof<IAnimationOperatorQueue>(), m_poseModifier);

-
Loading of Engine assets in code now requires the "%ENGINE%" prefix, for example "%ENGINE%/EngineAssets/Textures/White.dds".

-
Flow node registration no longer requires extensive extra logic to be implemented for each game. Instead, call CryRegisterFlowNodes during initialization and CryUnregisterFlowNodes during shutdown.

-
CryMath/Random.h - Is no longer included by default in certain header files. This may result in projects having to include the files manually (#include <CryMath/Random.h>).

-
IConsole functions that were used to register console commands and CVars are no longer publicly accessible. You might have to update your code to use the already existing macros or the new ConsoleRegistrationHelper class (all of which are located in <CrySystem/ISystem.h>.
[#visual-studio-support](
Visual Studio Support
)
[#deprecation-notices](
Deprecation Notices
)
[#entity-system-and-schematyc](
Entity System & Schematyc
)
[#templates](
Templates
)
[#network](
Network
)
[#animation](
Animation
)
[#audio](
Audio
)
[#asset-browser-and-paths](
Asset Browser & Paths
)
[#miscellaneous](
Miscellaneous
)
