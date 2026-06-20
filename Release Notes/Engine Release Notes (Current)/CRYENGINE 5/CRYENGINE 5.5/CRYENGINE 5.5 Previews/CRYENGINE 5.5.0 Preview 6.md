# CRYENGINE 5.5.0 Preview 6

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/47316993/pages/44962793
- Page ID: 44962793
- Breadcrumb: Engine Release Notes (Current) > CRYENGINE 5 > CRYENGINE 5.5 > CRYENGINE 5.5 Previews > CRYENGINE 5.5.0 Preview 6
- Parent: CRYENGINE 5.5 Previews

## Content

##
Overview - CRYENGINE 5.5.0 Preview 6

We are very pleased to bring you the 5.5.0 Preview 6 release. Our Dev Team have been busy improving on the earlier previews that were released on 20 March 2018, 03 May 2018, 24 May 2018, 07 June 2018 and 26 June 2018.

As always we really do welcome further feedback and comments from the CRYENGINE Community, but please can these come through our normal channels i.e. the
[https://github.com/CRYTEK/CRYENGINE/issues](
Github Issue Reporter
)
 and the .

##
Accessing the 5.5.0 Preview 6 Release

Engine versions are now available through the CRYENGINE Launcher.

-
Log into the CRYENGINE Launcher.

-
Go to
LIBRARY -> My Engines
 where your currently installed and available Engines are listed. From there Engines can be updated (installed).

##
 Github

Preview Engine versions are also available from Github, however Sandbox Editor source code is only available via Github.

-
Go to:

[https://github.com/CRYTEK/CRYENGINE/releases/5.5.0_preview6](
https://github.com/CRYTEK/CRYENGINE
/releases/5.5.0_preview6
)

-
Download CRYENGINE_preview_5.5.0.327_pc.zip

-
Unzip it somewhere and open the directory “CRYENGINE_preview_5.5.0.327_pc”

-
Double click on InstallEngine.bat

##
Code Interface Changes

For more information. see the
[/docs/static/engines/cryengine-5/categories/47316993/pages/44962762](
Important CRYENGINE 5.5 Data and Code Changes
)
.

If you are updating from CRYENGINE 5.4, please read this topic:
[/docs/static/engines/cryengine-5/categories/47316993/pages/44962763](
Migrating from CRYENGINE 5.4 to CRYENGINE 5.5
)
[/docs/static/engines/cryengine-5/categories/23756816/pages/29445533](
.
)

##
Known Issues

-
**
RENDERER:
**
 Reflections are broken if a material is attached to a object. Can be tweaked with "r_ssreflsamples" and "r_ssrefldistance".

-
**
CRASH:
**
 Game will crash on startup with Vulkan.

-
**
CRASH:
**
 Legacy PFX can cause a crash shortly after being added to a level

-
**
PARTICLE EDITOR:
**
 Changes to a particle effect in the new Particle Editor are not directly applied to the Particle Effect instances in the level (currently a level reload is necessary).

-
**
CRASH:
**
 Occasionally the editor crashes if a particle effect is placed in the level and is opened in Particle Editor.

-
**
DESIGNER TOOL
**
: Objects may be invisible after levelload/chainload.

Workaround: Enable, then disable e_permanentRenderObjects 0/1.

-
**
C#:
**
 Using the CRYENGINE C# extension for Visual Studio 2017 to start the GameLauncher, Sandbox Editor or Server can cause an error when used in the latest version of Visual Studio 2017. More information and a fix for this issue can be found
[/docs/static/engines/cryengine-5/categories/23756813/pages/29791112](
here
)
.

-
**
ENTITIES:
**
 Light Projector does not cast any shadows.

-
**
ENTITIES
:
**
 Using an entity/component as movement, rotation pivot/joint in Trackview does not play the animation in-game and or in pure game.

##
Audio

##
Middleware Updates

-
Updated to Wwise SDK 2018.1.0 (
**
NOTE:
**
 If using CRYENGINE 5.5.0 Preview 6 (and future versions of CRYENGINE), then users
**
MUST
**
 update their Wwise version to at least version 2018.1.0 or later.
**
NOTE:
**
 Earlier versions of CRYENGINE i.e. up to and including CRYENGINE 5.5.0 Preview 5
**
MUST
**
 use a Wwise version that is prior to Wwise 2018.1.0.

-
Updated to Fmod Studio 1.10.07.

##
Core/System

##
Action General

-
**
Fixed:
**
 Container Entities do not output correct data.

##
Graphics and Rendering

##
Renderer General

-
**
Fixed:
**
 GetDebugName platform ifdef - fixed compilation for Durango.

-
**
Fixed:
**
 Scaleform memory leak.

-
**
Fixed:
**
 Pipeline State Object (PSO) pool growing unbounded.

-
**
Tweaked:
**
 Allow recursive release of rendernodes.

##
Additional Fixes

-
**
Fixed:
**
 (Entity System) Crash after jumping into any level and trying to exit.

-
**
Fixed:
**
 (Entity System) Unremovable entities were not hidden when they were removed.

-
**
Fixed:
**
 (Renderer) Missing information in water volume reflections.

-
**
Fixed:
**
(Sandbox Editor) Opening a level through the Asset Browser will set the wrong level path. When saving a level, legacy code in mission, terrain, vegetation etc. will fail to resolve the path.

-
**
Fixed:
**
(CryDefaultEntities) Assertion and crash in the MannequinObject after deletion. The MannequinObject was changed to an IEntityComponent but still behaved like a GameObject on shutdown.

-
**
Tweaked:
**
(Animation) Vcloth parameter names have been changed in order to clarify that constraints are enforced and propagated locally between nearest neighbors only.
**
NOTE:
**
 Users will need to override defaults and set the values for the new Nearest Neighbor Distance Constraints (NNDC) parameters.

-
**
Tweaked:
**
(Character Tool) Checkbox for NNDC now switches to disabled after re-loading.

-
**
Tweaked:
**
 (Water Volumes) Added more parameters.

-
**
Tweaked:
**
(Water Volumes) Improved fade-out parameters to suppress glaring step-artifacts between missing and non-missing Screen Space Reflection(s) (SSR) information.

-
**
Tweaked:
**
(Sandbox) Don't handle mouse events in Level Editor Viewport if no level is loaded.

-
**
Tweaked:
**
 (Renderer) Move GPU particles update into Update() rather than Execute().
