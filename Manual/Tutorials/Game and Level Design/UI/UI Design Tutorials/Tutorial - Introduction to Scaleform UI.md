# Tutorial - Introduction to Scaleform UI

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/89456793
- Page ID: 89456793
- Breadcrumb: Tutorials > Game and Level Design > UI > UI Design Tutorials > Tutorial - Introduction to Scaleform UI
- Parent: UI Design Tutorials

## Child Pages

- [Chapter 1 - UI Scene Setup](Tutorial - Introduction to Scaleform UI/Chapter 1 - UI Scene Setup.md)
- [Chapter 2 - Flash and Gfx](Tutorial - Introduction to Scaleform UI/Chapter 2 - Flash and Gfx.md)
- [Chapter 3 - UI Elements](Tutorial - Introduction to Scaleform UI/Chapter 3 - UI Elements.md)
- [Chapter 4 - Exposing a Function from Flash](Tutorial - Introduction to Scaleform UI/Chapter 4 - Exposing a Function from Flash.md)
- [Chapter 5 - Exposing an Event from Flash](Tutorial - Introduction to Scaleform UI/Chapter 5 - Exposing an Event from Flash.md)
- [Chapter 6 - Font Embedding](Tutorial - Introduction to Scaleform UI/Chapter 6 - Font Embedding.md)
- [Chapter 7 - Using the Exposed Function](Tutorial - Introduction to Scaleform UI/Chapter 7 - Using the Exposed Function.md)
- [Chapter 8 - Using the Exposed Event](Tutorial - Introduction to Scaleform UI/Chapter 8 - Using the Exposed Event.md)

## Content

##
Overview

The Scaleform integration in CRYENGINE is a flexible and performant solution that uses the Autodesk Scaleform technology to provide tools and capabilities to render functional user interfaces for your projects.

Since the release of CRYENGINE 5.7 LTS, the implementation provides support for Scaleform 3 and Scaleform 4. The inclusion of Scaleform 3 is meant as a fall back for users relying on functionality that is possibly changed in Scaleform 4, so that they can continue to develop their projects without hindrance.

Scaleform 4 supports Actionscript 2.0, as well as Actionscript 3.0. This means that you can use any Adobe Flash or animation software that supports either ActionScript 2.0 or 3.0 to create your Scaleform GFX assets. Although the workflow has remain unchanged
, there are differences with regards to the tools that now exist and other technical elements that warrant the separation of Scaleform 3 and Scaleform 4 asset creation.

[Image: /docs/static/attachments/90833088]

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
[/docs/static/engines/cryengine-5/categories/23756813/pages/90833060](
Enabling Scaleform 4 for Projects and Custom Engine Builds
)
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
[/docs/static/engines/cryengine-5/categories/23756816/pages/69468180](
Installing CRYENGINE
)

-
[/docs/static/engines/cryengine-5/categories/23756816/pages/26877242](
Tutorial - Getting Started With Flow Graph
)
Additionally, for applying UI elements to an in-game mesh, we recommend watching
[/docs/static/engines/cryengine-5/categories/23756816/pages/56656939](
Tutorial - How to apply Scaleform UI to a game object
)
.

##
In This Section

-
[/docs/static/engines/cryengine-5/categories/23756816/pages/89456795](
Chapter 1 - UI Scene Setup
)

-
[/docs/static/engines/cryengine-5/categories/23756816/pages/89456800](
Chapter 2 - Flash and Gfx
)

-
[/docs/static/engines/cryengine-5/categories/23756816/pages/89456803](
Chapter 3 - UI Elements
)

-
[/docs/static/engines/cryengine-5/categories/23756816/pages/89456814](
Chapter 4 - Exposing a Function from Flash
)

-
[/docs/static/engines/cryengine-5/categories/23756816/pages/89456818](
Chapter 5 - Exposing an Event from Flash
)

-
[/docs/static/engines/cryengine-5/categories/23756816/pages/90833227](
Chapter 6 - Font Embedding
)

-
[/docs/static/engines/cryengine-5/categories/23756816/pages/89456821](
Chapter 7 - Using the Exposed Function
)

-
[/docs/static/engines/cryengine-5/categories/23756816/pages/89456826](
Chapter 8 - Using the Exposed Event
)

##
Related Information

-
[/docs/static/engines/cryengine-5/categories/23756816/pages/56656939](
Tutorial - How to apply Scaleform UI to a game object
)

-
[/docs/static/engines/cryengine-5/categories/23756816/pages/56656931](
Tutorial - How to create Dynamic Text in Scaleform UI
)

-
[/docs/static/engines/cryengine-5/categories/23756816/pages/56656609](
Tutorial Series - Flappy Boid Beginner's Course
)
