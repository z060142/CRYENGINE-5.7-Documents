# Creating a Flow Graph Node as a C++ Plugin

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/44958448
- Page ID: 44958448
- Breadcrumb: CRYENGINE Game Code > Flowgraph Programming > Creating a Flow Graph Node as a C++ Plugin
- Parent: Flowgraph Programming

## Content

## Overview

In CRYENGINE, it is possible to create a custom Flow Graph node by using C++ to generate a.dll file that can be introduced to CRYENGINE as a plugin. This technique offers another solution for the users who prefer creating a custom node without having to create it from scratch. For more information about creating a Flow Graph node, please refer to the [Creating a New Flow Node](Creating%20a%20New%20Flow%20Node.md) section.

In this example, a SubString function is used as the first and most basic example to create a custom Flow Graph node.

### Prerequisites

The following applications will need to be installed in order to compile projects and the Engine itself.

Name | Minimum Version | Latest Supported Version | Notes
--- | --- | --- | ---
[Visual Studio](https://www.visualstudio.com/downloads/) | 2015 (All Editions), vc140 compiler | 2017 (All Editions), vc141 compiler |
[Windows SDK](https://developer.microsoft.com/en-us/windows/downloads/windows-10-sdk) | 10.0.15063.0 | 10.0.15063.0 | Early installations of Visual Studio 2015 may have installed 10.0.10150.0 instead. In this scenario, re-run the Visual Studio installer and select the recommended version. Please note that you have to restart your computer after installing the Windows SDK before attempting to compile the engine.
[CMake](https://cmake.org/download/) | 3.6 | 3.9 |

### Steps

- Create a **Plugin CPP** project and open the project folder. For more information about creating a project, please refer to the [Creating, Importing & Upgrading Projects](/docs/static/engines/cryengine-5/categories/23756816/pages/36870288) page.
The project files are stored separately from the engine. A **.cryproject** file will be generated for you; this can be right-clicked to reveal helper functionality or opened with a text editor to reveal JSON detailing the project.
- Next, in the project folder, **right-click** on the ** Plugin.cryproject** file and choose ** Generate solution**;![Image](https://www.cryengine.com/docs/static/attachments/44958449) Go to the solution file that has been generated and open the ** Plugin.sln** file; e.g:*\MyProject\solutions\win64\Plugin.sln*
- In the Solution Explorer, open *project\Plugin\Plugin.cpp* and paste the class & macro shown below just before the last line of the code block, which is **CRYREGISTER_SINGLETON_CLASS(CPlugin)**:
```
// This is the class that is going to be registered by the REGISTER_FLOW_NODE macro at the bottom
class CFlowSubstringNode : public CFlowBaseNode<eNCT_Singleton>
{
public:
CFlowSubstringNode(SActivationInfo* pActInfo) {};
virtual void GetConfiguration(SFlowNodeConfig& config)
{
static const SInputPortConfig in_config[] = {
InputPortConfig_Void("Get",        _HELP("Substring, retrieves letters from defined string.")),
InputPortConfig<string>("String", _HELP("String to retrieve letters from")),
InputPortConfig<int>("Int1", _HELP("Start retrieving from")),
InputPortConfig<int>("Int2", _HELP("Number of letters to retrieve")),
{ 0 }
};
static const SOutputPortConfig out_config[] = {
OutputPortConfig<string>("Out"),
{ 0 }
};
config.sDescription = _HELP("Substring");
config.pInputPorts = in_config;
config.pOutputPorts = out_config;
config.SetCategory(EFLN_APPROVED);
}
virtual void ProcessEvent(EFlowEvent evt, SActivationInfo* pActInfo)
{
switch (evt)
{
case eFE_Activate:
if (IsPortActive(pActInfo, 0))
{
string str1 = GetPortString(pActInfo, 1);
int int1 = GetPortInt(pActInfo, 2);
int int2 = GetPortInt(pActInfo, 3);
if (int1 + int2 > str1.length())
{
CryWarning(
VALIDATOR_MODULE_FLOWGRAPH,
VALIDATOR_WARNING,
"Failed to get %d characters starting from %d in a string %d characters long.",
int2, int1, str1.length());
}
ActivateOutput(pActInfo, 0, str1.substr(int1, int2));
}
break;
}
};
virtual void GetMemoryUsage(ICrySizer* s) const
{
s->Add(*this);
}
};
//Register Flownode (you will need to do this for every FlowNode once)
//The REGISTER_FLOW_NODE Macro takes 2 parameters, the name as first and the class as second parameter.
REGISTER_FLOW_NODE("String:Substring", CFlowSubstringNode)
```
In this example, the node will be called **String:Substring**, as indicated in the last line of the code block above.
The last line of this block should be **CRYREGISTER_SINGLETON_CLASS(CPlugin)**.
- After copying the code, go to the **Plugin.h → CPlugin** class on the Solution Explorer and paste the following two lines at the bottom of the public section:
```
PLUGIN_FLOWNODE_REGISTER
```
```
PLUGIN_FLOWNODE_UNREGISTER
```
When the process is finished, the code block should look as follows:
```
#pragma once
#include <CrySystem/ICryPlugin.h>
#include <CryGame/IGameFramework.h>
#include <CryEntitySystem/IEntityClass.h>
class CPlugin
: public Cry::IEnginePlugin
, public ISystemEventListener
{
public:
CRYINTERFACE_SIMPLE(Cry::IEnginePlugin)
CRYGENERATE_SINGLETONCLASS_GUID(CPlugin, "MyPlugin", "2711a23d-3848-4cdd-a95b-e9d88ffa23b0"_cry_guid)
virtual ~CPlugin();

// Cry::IEnginePlugin
virtual bool Initialize(SSystemGlobalEnvironment& env, const SSystemInitParams& initParams) override;
// ~Cry::IEnginePlugin

// ISystemEventListener
virtual void OnSystemEvent(ESystemEvent event, UINT_PTR wparam, UINT_PTR lparam) override;
// ~ISystemEventListener
//Include Flownode Registering and unregistering (just needs to be included once in total)
PLUGIN_FLOWNODE_REGISTER
PLUGIN_FLOWNODE_UNREGISTER
};
```
These two lines will make sure that the Flow Graph node is registered/unregistered and they only need to be included once in total. After confirming the code position is correct, proceed to the next steps:
- **Build** the solution by choosing ** Build → Build Solution** on the Visual Studio menu bar. This will generate a.dll file in the * MyPlugin\bin\win_x64*folder;
- **Copy** that .dll file to the *\bin\win_x64* folder of any existing CRYENGINE project in which you want to use your plugin.
In this example, the GameSDK project is being used, so the .dll file is coped to *\GameSDK\bin\win_x64;*
- **Right-click** on the **GameSDK.cryproject** file and ** Edit** it in a plain text editor to add the following reference of the.dll file in the plugins section; keep in mind that the reference code shown below can be different based on the path of the project's * bin* folder: { "type": "EPluginType::Native", "path": "bin/win_x64/plugin.dll" }.
If the new line is not the last line of the plug-in, make sure it ends with a comma.
- Open the **GameSDK.cryproject** file in the Sandbox editor. Then proceed to Flow Graph to use the new node;![Image](https://www.cryengine.com/docs/static/attachments/44958450)
You may also want to use visual panels to communicate related information, tips or things users need to be aware of.
