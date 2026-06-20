# Tutorial - Introduction to Scaleform UI

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/89456793
- Page ID: 89456793
- Breadcrumb: Tutorials > Game and Level Design > UI > UI Design Tutorials > Tutorial - Introduction to Scaleform UI
- Parent: UI Design Tutorials

## Child Pages

- [Chapter 1 - UI Scene Setup](Tutorial%20-%20Introduction%20to%20Scaleform%20UI/Chapter%201%20-%20UI%20Scene%20Setup.md)
- [Chapter 2 - Flash and Gfx](Tutorial%20-%20Introduction%20to%20Scaleform%20UI/Chapter%202%20-%20Flash%20and%20Gfx.md)
- [Chapter 3 - UI Elements](Tutorial%20-%20Introduction%20to%20Scaleform%20UI/Chapter%203%20-%20UI%20Elements.md)
- [Chapter 4 - Exposing a Function from Flash](Tutorial%20-%20Introduction%20to%20Scaleform%20UI/Chapter%204%20-%20Exposing%20a%20Function%20from%20Flash.md)
- [Chapter 5 - Exposing an Event from Flash](Tutorial%20-%20Introduction%20to%20Scaleform%20UI/Chapter%205%20-%20Exposing%20an%20Event%20from%20Flash.md)
- [Chapter 6 - Font Embedding](Tutorial%20-%20Introduction%20to%20Scaleform%20UI/Chapter%206%20-%20Font%20Embedding.md)
- [Chapter 7 - Using the Exposed Function](Tutorial%20-%20Introduction%20to%20Scaleform%20UI/Chapter%207%20-%20Using%20the%20Exposed%20Function.md)
- [Chapter 8 - Using the Exposed Event](Tutorial%20-%20Introduction%20to%20Scaleform%20UI/Chapter%208%20-%20Using%20the%20Exposed%20Event.md)

## Content

##
Overview

The Scaleform integration in CRYENGINE is a flexible and performant solution that uses the Autodesk Scaleform technology to provide tools and capabilities to render functional user interfaces for your projects.

Since the release of CRYENGINE 5.7 LTS, the implementation provides support for Scaleform 3 and Scaleform 4. The inclusion of Scaleform 3 is meant as a fall back for users relying on functionality that is possibly changed in Scaleform 4, so that they can continue to develop their projects without hindrance.

Scaleform 4 supports Actionscript 2.0, as well as Actionscript 3.0. This means that you can use any Adobe Flash or animation software that supports either ActionScript 2.0 or 3.0 to create your Scaleform GFX assets. Although the workflow has remain unchanged
, there are differences with regards to the tools that now exist and other technical elements that warrant the separation of Scaleform 3 and Scaleform 4 asset creation.

![Image](https://www.cryengine.com/docs/static/attachments/90833088)

*
Adobe Animate
*

##
Goals

The focus of this tutorial is to get you started on using the Scaleform 3 and/or 4 implementations that ship with CRYENGINE V.

-
Where applicable, instructions for Scaleform 3 and 4 have been provided separately in each of the chapters.

-
When following this tutorial for Scaleform 3, it is recommended to use CRYENGINE versions between 5.0 and 5.6.7. and Adobe Flash CS6.

-
The Scaleform 4 aspects of this tutorial meanwhile are recommended for CRYENGINE version 5.7 LTS. You also need to enable Scaleform 4 for your Engine build; see
[Enabling Scaleform 4 for Projects and Custom Engine Builds](../../../../../API%20Reference/CRYENGINE%20Game%20Code/Miscellaneous%20Game%20Code/User%20Interface/Enabling%20Scaleform%204%20for%20Projects%20and%20Custom%20Engine%20Builds.md)
 for more information.
You will also be doing parts of XML and visual scripting in this tutorial to achieve basic functionality; with regards to visual scripting, you can choose between the instructions provided for Flow Graph and Schematyc (Experimental) in the relevant chapters. It is however not recommended to mix the Flow Graph and Schematyc (Experimental) approaches as this can lead to issues that are hard to resolve.

You will also learn how to:

-
Create a new Flash project for Scaleform usage.

-
Convert SWF files to GFx files.

-
Generate the required DDS images.

-
Expose UI functions and events to Visual Scripting.

-
Call and handle UI functions in Flow Graph.

-
Test your UI in-game.

##
Prerequisites

This tutorial provides instructions for both Scaleform 3 and 4, and assumes you have prior knowledge of the following topics:

-
[Installing CRYENGINE](../../../../CRYENGINE%20-%20Getting%20Started/Installing%20CRYENGINE.md)

-
[Tutorial - Getting Started With Flow Graph](../../../Game%20Logic/Flow%20Graph%20Tutorials/Tutorial%20-%20Getting%20Started%20With%20Flow%20Graph.md)
Additionally, for applying UI elements to an in-game mesh, we recommend watching
[Tutorial - How to apply Scaleform UI to a game object](../UI%20with%20Flash%206/Tutorial%20-%20How%20to%20apply%20Scaleform%20UI%20to%20a%20game%20object.md)
.

##
In This Section

-
[Chapter 1 - UI Scene Setup](Tutorial%20-%20Introduction%20to%20Scaleform%20UI/Chapter%201%20-%20UI%20Scene%20Setup.md)

-
[Chapter 2 - Flash and Gfx](Tutorial%20-%20Introduction%20to%20Scaleform%20UI/Chapter%202%20-%20Flash%20and%20Gfx.md)

-
[Chapter 3 - UI Elements](Tutorial%20-%20Introduction%20to%20Scaleform%20UI/Chapter%203%20-%20UI%20Elements.md)

-
[Chapter 4 - Exposing a Function from Flash](Tutorial%20-%20Introduction%20to%20Scaleform%20UI/Chapter%204%20-%20Exposing%20a%20Function%20from%20Flash.md)

-
[Chapter 5 - Exposing an Event from Flash](Tutorial%20-%20Introduction%20to%20Scaleform%20UI/Chapter%205%20-%20Exposing%20an%20Event%20from%20Flash.md)

-
[Chapter 6 - Font Embedding](Tutorial%20-%20Introduction%20to%20Scaleform%20UI/Chapter%206%20-%20Font%20Embedding.md)

-
[Chapter 7 - Using the Exposed Function](Tutorial%20-%20Introduction%20to%20Scaleform%20UI/Chapter%207%20-%20Using%20the%20Exposed%20Function.md)

-
[Chapter 8 - Using the Exposed Event](Tutorial%20-%20Introduction%20to%20Scaleform%20UI/Chapter%208%20-%20Using%20the%20Exposed%20Event.md)

##
Related Information

-
[Tutorial - How to apply Scaleform UI to a game object](../UI%20with%20Flash%206/Tutorial%20-%20How%20to%20apply%20Scaleform%20UI%20to%20a%20game%20object.md)

-
[Tutorial - How to create Dynamic Text in Scaleform UI](Tutorial%20-%20How%20to%20create%20Dynamic%20Text%20in%20Scaleform%20UI.md)

-
[Tutorial Series - Flappy Boid Beginner's Course](../../../Build-A-Game%20Courses/Tutorial%20Series%20-%20Flappy%20Boid%20Beginner%27s%20Course.md)
