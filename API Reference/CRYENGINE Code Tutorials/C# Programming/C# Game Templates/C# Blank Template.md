# C# Blank Template

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/29798417
- Page ID: 29798417
- Breadcrumb: CRYENGINE Code Tutorials > C# Programming > C# Game Templates > C# Blank Template
- Parent: C# Game Templates

## Content

The blank template is designed for those situations when you want to start a project from scratch.
This template only includes an FPS counter and a basic setup of a
[CryEnginePlugin](https://www.cryengine.com/sdk/5.3.0/cs_api/interface_cry_engine_1_1_i_cry_engine_plugin.html)
 which can be used as a starting point for initializing your project. However, if you are not familiar with programming in C# in CRYENGINE, then we recommend that you first start off with another one of the available templates.

Related Content:

-
[C# API Reference](../../../CRYENGINE%20API%20Reference/C%23%20API%20Reference.md)

-
[C# Programming](../../C%23%20Programming.md)

##
FPS-Counter

The FPS counter is rendered by using the
[CryEngine.UI](https://www.cryengine.com/sdk/5.2.0/cs_api/namespace_cry_engine_1_1_u_i.html)
. The
[Canvas](https://www.cryengine.com/sdk/5.2.0/cs_api/class_cry_engine_1_1_u_i_1_1_canvas.html)
is set up by the
**
CreateUI
**
 method. The
[Text](https://www.cryengine.com/sdk/5.2.0/cs_api/class_cry_engine_1_1_u_i_1_1_components_1_1_text.html)
 component is added to the Canvas and placed in the correct position. In the
**
OnUpdate
**
 method, the amount of frames that have passed are counted, and every second this gets written to the
**
Text
**
 component and the count is reset to 0. The
**
OnUpdate
**
 method is called every frame by the
[GameFramework](https://www.cryengine.com/sdk/5.3.0/cs_api/class_cry_engine_1_1_game_framework.html)
, which is achieved by calling
[RegisterForUpdate](https://www.cryengine.com/sdk/5.3.0/cs_api/class_cry_engine_1_1_game_framework.html#a732a13b0937ed7342d0af3528eb45ec2)
in the constructor of the
**
Game
**
 class.

The
**
CreateUI
**
 and
**
DestroyUI
**
 are subscribed to the engine reload event. This is required to handle cleaning up the UI when the C# plugins are reloaded, for example when a C# asset has been edited.
