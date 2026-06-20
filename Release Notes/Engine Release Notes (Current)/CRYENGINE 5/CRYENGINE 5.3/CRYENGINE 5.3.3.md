# CRYENGINE 5.3.3

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/47316993/pages/44962667
- Page ID: 44962667
- Breadcrumb: Engine Release Notes (Current) > CRYENGINE 5 > CRYENGINE 5.3 > CRYENGINE 5.3.3
- Parent: CRYENGINE 5.3

## Child Pages

- [Third-party SDKs in 5.3.3](CRYENGINE 5.3.3/Third-party SDKs in 5.3.3.md)

## Content

##
Release Highlights

CRYENGINE 5.3.3 includes various fixes and marks the launch of a new C# Rolling Ball template. We’re also removing the Sydewinder project and making it available as a standalone download from CRYENGINE Marketplace.

The
[/docs/static/engines/cryengine-5/categories/23756813/pages/29791343](
C# Rolling Ball template
)
 is a simple game which is ideal for people who are unfamiliar with using C# in CRYENGINE. This template demonstrates how you can use the Entity Component to modify the behavior of entities in your game, use physics to move entities around a level, and receive input from the player. It’s a great way to get up and running quickly with C# and CRYENGINE.

The
[/docs/static/engines/cryengine-5/categories/23756813/pages/24283087](
Sydewinder tutorial
)
is now available as a standalone download from the CRYENGINE Marketplace. Sydewinder focuses on programming-driven game development and presents an endless side-scrolling game with a high score counter. This tutorial guides you through all the necessary steps in order to get started from scratch using the CE# Framework, as well as direct interaction with CryEngine.Common.

##
Game Templates

-
**
New:
**
 Added RollingBall template to the C# game template selection.

-
**
Refactored:
**
Removed the Sydewinder application - this will be maintained as a separate project and is available as a download from the
[https://www.cryengine.com/marketplace](
CRYENGINE Marketplace.
)

##
Audio

##
Audio General

-
**
Fixed:
**
 Bug where the MS compiler auto-vectorizer produced illegal instructions in mpeg code.

##
Core/System

##
Engine General

-
**
Fixed:
**
 Added ScaleformHelper to builds.

-
**
Fixed:
**
 Download of 5.3.1 SDKs package.

-
**
Fixed:
**
 Crash during Scaleform shutdown.

##
System

-
**
Fixed:
**
 Sydewinder doesn't close properly in Launcher.

-
**
Fixed:
**
 Encoding fixes for command line parsing.

-
**
Fixed:
**
 Crash reporter not producing crash dumps on Windows 7.

##
WAF

-
**
Fixed:
**
 ScaleformHelper usage by WAF (all configs) and CMake (release config).

-
**
Tweaked:
**
 Don't monolithically link MonoBridge into release configs, it's an optional feature.

-
**
Tweaked:
**
 Copy the right portaudio binaries (performance and release config).

##
CMake

-
**
Optimized:
**
 Don't copy unnecessary debug DLLs or PDBs to bin/win_x64.

-
**
Fixed:
**
 Compiler detection for VS2017.

##
Action General

-
**
Fixed:
**
 The ability to load a second level after the first has been loaded.

##
C#

-
**
Fixed:
**
 The Input class not registering mouse-movement.
