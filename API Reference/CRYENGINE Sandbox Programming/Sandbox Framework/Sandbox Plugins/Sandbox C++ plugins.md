# Sandbox C++ plugins

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/26873092
- Page ID: 26873092
- Breadcrumb: CRYENGINE Sandbox Programming > Sandbox Framework > Sandbox Plugins > Sandbox C++ plugins
- Parent: Sandbox Plugins

## Content

## Sample Plugin

In order to simplify creating a new plugin, and to demonstrate some of the plugin features, we have created the SamplePlugin. You can find the code for the SamplePlugin in **Code/Sandbox/Plugins/SamplePlugin.**

If you want to test the sample plugin for yourself, use the CMake option **OPTION_SAMPLEPLUGIN** when generating your solution.

## Creating a New Plugin

- Create a new folder to host your plugin.
- First Method: Copy the SamplePlugin
- Keep the following files:
- SamplePlugin.h
- SamplePlugin.cpp
- StdAfx.h
- StdAfx.cpp
- CMakeLists.txt
- Rename the file and its contents as necessary.
- Delete the demo files as they are unnecessary, or keep them as an example.
- Second Method: From Scratch
- Create a CMakeLists.txt file to it, following the model of other projects. See dependencies below to ensure you are only using what is appropriate for an editor plugin.
- We recommend you follow the folder structure of the Sample Plugin which contains a precompiled header, and a separate header/cpp file for the plugin. However, you can write the code in any file. Registering a plugin looks like this:

```
class CSamplePlugin : public IPlugin
{
public:
CSamplePlugin() { /* entry point of the plugin, perform initializations */ }
~CSamplePlugin() { /* exit point of the plugin, perform cleanup */ }
int32       GetPluginVersion() { return 1; };
const char* GetPluginName() { return "Sample Plugin"; };
const char* GetPluginDescription() { return "Some description of your plugin"; };
private:
};

//Macro to register the plugin
REGISTER_PLUGIN(CSamplePlugin);
```

## Package Dependencies

- Plugins should always depend on **EditorInterface** and ** EditorCommon.**
- Plugins may, of course, depend on engine packages and modules.
- It is also possible for editor plugins to depend on one another.
- Reusable components should go to EditorCommon, share the products of your work, don't keep it locked inside your plugin code.
- Do not add a dependency on MFCToolsPlugin, MFC or Windows SDK. As much as possible your plugin should be platform agnostic. There are several choices for hardware abstraction from CryEngine API and Qt API that should fulfill your needs.
- Do not add a dependency on Sandbox even if it looks like you need it. If you need some things from Sandbox that have not been exposed, you must expose them by one of these methods:
- Add an interface in EditorInterface that is implemented by Sandbox. This way you have exposed some functionality without tying your plugin to the implementation in Sandbox which is highly likely to change. This will need a pull request to be accepted by the engine team.
- Move classes to EditorCommon, that is only if they are meant to be reusable classes and try to avoid bringing too many dependencies with it. This will need a pull request to be accepted by the engine team.
- Not recommended: Add new methods to IEditor. This is only really relevant when exposing a "global" type of functionality, as all the new concepts should be added to separate interfaces in order to not bloat IEditor and keep the editor architecture modular.
- Remember the Sandbox code is still undergoing heavy changes and should be considered as a "black box".

## What You Can Do with a Plugin

- [Add new tools and dockable windows](../Creating%20a%20new%20editor%20window.md)
- [Add commands](/docs/static/engines/cryengine-5/categories/23756813/pages/26873100)
- [Add preference pages](../Preferences%20and%20Settings.md)
- Add tray widgets
- [Register new asset types](../Asset%20System.md)
- Register new object types to be placed in a level

Please refer to the SamplePlugin code in order to see some examples of some of these.
