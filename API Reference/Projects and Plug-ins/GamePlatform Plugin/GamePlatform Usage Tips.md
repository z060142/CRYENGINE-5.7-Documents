# GamePlatform Usage Tips

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/76448695
- Page ID: 76448695
- Breadcrumb: Projects and Plug-ins > GamePlatform Plugin > GamePlatform Usage Tips
- Parent: GamePlatform Plugin

## Child Pages

- [C++ API GamePlatform Usage Tips](GamePlatform Usage Tips/C++ API GamePlatform Usage Tips.md)
- [Flow Graph GamePlatform Usage Tips](GamePlatform Usage Tips/Flow Graph GamePlatform Usage Tips.md)
- [Schematyc (Experimental) Usage Tips](GamePlatform Usage Tips/Schematyc (Experimental) Usage Tips.md)

## Content

This section includes various examples and usage tips to get you started with the GamePlatformPlugin
[/docs/static/engines/cryengine-5/categories/23756813/pages/76448424](
features
)
.

The GamePlatformPlugin itself is comprised of a management system (CryGamePlatformPlugin) and various implementations of platform services. For example, CryGamePlatformSteam). There is also an additional module that provides Flow Graph and Schematyc (Experimental) Nodes and Components to allow non-programmer development and interaction with these services via Visual Graphs (CryGamePlatformNodes).

##
C++ API, Flow Graph or Schematyc?

-
Flow Graph and Schematyc are implemented separately for the most part. It is hence recommended to separate the necessary logic accordingly if you are to use both systems in your project. Ideally, you would choose only one.

For example, events triggered by the platform will be sent to both systems. Event data will then be duplicated for those events you are handling in each system. Tracking issues will be made much more difficult if both systems are handling the same events.

-
Some overhead in performance and memory will be introduced by using the Flow Graph and Schematyc methods. However, most platform service actions are not time sensitive and should not be a concern most of the time.

However, for the most control and performant access/use of the platform service API, we always recommend using the C++ interface directly when possible.

##
Interaction and Response of the GamePlatform Services

There are 3 main interactions with the GamePlatform Services:

-
Direct functions - These are actions taken immediately.

-
Asynchronous functions - These actions are triggered immediately, but the result may take some time and most likely trigger an event when ready.

-
Events - These are triggered by the platform service, either due to a request via an asynchronous function, or via the platform itself.

##
API Throttling

Most platforms will penalize applications that over saturate the platform service unnecessarily.

-
Care should be taken about what data you pull and how often you pull that data to prevent the platform from restricting further API calls.

-
In some cases, poor throttling can even prevent a game from passing a platform viability/conformance check, and your game will not be able to be released on that platform.

##
In This Section

-
[/docs/static/engines/cryengine-5/categories/23756813/pages/76448706](
C++ API GamePlatform Usage Tips
)

-
[/docs/static/engines/cryengine-5/categories/23756813/pages/76448709](
Flow Graph GamePlatform Usage Tips
)

-
[/docs/static/engines/cryengine-5/categories/23756813/pages/76449009](
Schematyc (Experimental) Usage Tips
)

[#c-api-flow-graph-or-schematyc](
C++ API, Flow Graph or Schematyc?
)
[#interaction-and-response-of-the-gameplatform-services](
Interaction and Response of the GamePlatform Services
)
[#api-throttling](
API Throttling
)
[#in-this-section](
In This Section
)
