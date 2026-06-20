# Important CRYENGINE 5.3 Data and Code Changes

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/47316993/pages/44962674
- Page ID: 44962674
- Breadcrumb: Engine Release Notes (Current) > CRYENGINE 5 > CRYENGINE 5.3 > CRYENGINE 5.3.0 > Important CRYENGINE 5.3 Data and Code Changes
- Parent: CRYENGINE 5.3.0

## Content

### Level Format Changed

The exported level format has changed, users will need to re-export levels containing roads in order to load them with a 5.3.0 based Launcher.

### Game DLL Deprecation

**Optional Game dlls:**

With 5.3.0. we're introducing optional game code binaries. This is the first step towards a clear(er) separation of Engine and game code. The idea is to remove unnecessary code from the code base and to make sure your project only needs to maintain code that is actually used by it.

Legacy game code binaries (like GameSDK or GameZero) are still supported, but they might disappear at some point.

**Plugins Instead of a Single Game dll:**

Re-usable but game related code will be moved to plugins (eventually). Your project then defines which plugins to include. As a temporary solution there is a cryplugin.csv file that defines the currently included plugins. Eventually this will happen in the form of dependencies in your main *.cryproject file.

**New Initialization Order:**

In order to make the game dlls optional, we had to move the main game loop out of the game code into CryAction. This way, CryAction is now in charge of starting the Engine and also shutting it down correctly.

This created new dependency problems that we had to resolve. Please keep in mind that whatever module registers things in the Engine (e.g. Listeners, CVars) it also needs to unregister them correctly on shutdown to prevent leaks and crashes. We believe that even though this looks more fragile at the moment it will lead to a more stable development experience in general.

**What Happened to CEditorGame?**

This was used in older game binaries to implement custom game code behavior for the Sandbox. We have moved all the the important things that were in there to the Engine side of things (nothing stops you from re-implementing it in your game code, but keep in mind that we won't maintain this interface for much longer).

**Access Legacy Game Code from Within the Engine:**

In order to clean up interfaces and make the Engine less dependent on legacy game code, we removed the gEnv->pGame pointer. As a general rule IGame should only be accessed (if at all) within CryAction (GetIGame()).

Keep in mind that in the case of no existing legacy game dll, then this will return a nullptr from now on. We will move the corresponding Interfaces as soon as it is possible to do so (to limit access further).

### Default Entities Plugin

For the on-going move away from Lua-based entities, we now provide the CryDefaultEntities module. This contains a few C++ written entities using the new entity component system, meant to replace a few of the GameSDK specific implementations previously done in Lua.

It is important to be aware of the new entities, as they are **not** ** backwards compatible** with older levels using the Lua entities. If you are still in need of the Lua based entity, then simply utilize the existing Lua script and it'll override the newer version.

### Entity Component System

The new entity component system is intended as the future replacement of the game object system. This means that any new entity extensions will be written as components that can then be attached to any entity.

Although the entity component system will fully replace game objects in the future, game objects have not yet been removed for legacy compatibility reasons.

#### Entity Property Rework

With the new entity component system comes a rework of how entity properties are stored. The previous implementations of IEntityAttribute and IEntityPropertyHandler have been removed so they can no longer be used with the Engine.

To migrate properties, implement the IEntityPropertyGroup interface and return a pointer to an instance in the IEntityComponent::GetPropertyGroup function on your entity component or game object extension.

As an example:

```
class CExampleComponent : public IEntityComponent, public IEntityPropertyGroup
{
CRY_ENTITY_COMPONENT_INTERFACE_AND_CLASS(CExampleComponent, "ExampleComponent", 0x26AA3CDD57584144, 0xA46E31FE08554C36);
public:
// IEntityComponent
virtual struct IEntityPropertyGroup* GetPropertyGroup() override { return this; }
// ~IEntityComponent

// IEntityPropertyGroup
virtual const char* GetLabel() const override { return "Example Component Properties"; }

virtual void Serialize(Serialization::IArchive& archive) override
{
archive(m_myBoolean, "myBoolean", "MyBoolean");
archive(m_myInteger, "myInteger", "MyInteger");

if (archive.isInput())
{
CryLogAlways("Properties changed, bool is %s, int %i", m_myBoolean ? "true" : "false", m_myInteger);
}
}
// ~IEntityPropertyGroup

protected:
bool m_myBoolean;
int m_myInteger;
};

CRYREGISTER_CLASS(CExampleComponent);
```

### CryAction

- View initialization was previously done on level load - now automated in IGameObject::CaptureView - no code changes should be necessary
- Default actionmap initialization has been moved from CryAction level load to GameSDK - projects based on GameSDK will need to replicate this in CGame::LoadActionmaps.

### C#

- Requirement to have a standalone C++ game dll has been removed - C# plugins can now operate independently
- GameMono and MonoLauncher projects have been removed as they are no longer necessary
- Entity components now have to implement the EntityComponent interface
- Entities need to implement EntityComponent and use the EntityClass attribute to be registered
- ICryPlugin interface has changed
- New math classes have been introduced to improve performance - older versions will still work, but rely on a virtual call to C++ for every single math operation
- Vec3 -> Vector3
- Ang3 -> Angle3
- Vec2 -> Vector2
- Vec4 -> Vector4
- Quat -> Quaternion
- Matrix34 -> Matrix3x4
