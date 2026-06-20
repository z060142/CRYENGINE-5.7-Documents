# Navigation Areas

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/44961882
- Page ID: 44961882
- Breadcrumb: AI and Navigation > AI Overview > Navigation (MNM) > Navigation Areas
- Parent: Navigation (MNM)

## Content

##
Overview

To create navigation meshes, Navigation Areas need to be added to your level in the Editor. The following is a simple overview of this process.

##
Creating a New Navigation Area

To create a new Navigation Area:

-
Select the
**
AI → Navigation Area
**
 option from the
[Create Object](../../../Editor%20Tools/Level%20Editor%20Tab/Create%20Object.md)
 tool.

-
On the terrain in the Viewport, create a shape that encloses the area within which you want your AI characters to navigate.

-
With the Navigation Area selected, set its
**
Height
**
 property under the
**
Navigation Area
**
 tab of the Properties Tool to suit your needs.

-
Next, set the
[Agent Type](Navigation%20Configuration.md)
 of the Navigation Area to match the Agent Types of the AI characters that need to use the navigation mesh.
Checkboxes for available Agent Types are listed in the
**
Navigation Area
**
 panel of the Properties Tool, under the
**
Display Filled
**
 checkbox, as shown in the image below. Tick the corresponding boxes to set the Agent Type of the Navigation Area.

![Image](https://www.cryengine.com/docs/static/attachments/44961883)

*
Navigation Area properties
*

Agent Types will only be listed if they are first defined and configured in
 the
*
Navigation.xml
*

file located under
*
ProjectFolder/Scripts/AI/.

*
Please refer to the NavMesh Agent Types

[documentation](/docs)

for more information.

The
*
MediumSizedCharacters
*
and
*
VehicleMedium
*
 agent types pictured in the image above are included in the GameSDK sample project.

NavMesh generation is handled in a separate thread so that it doesn't stall the Editor.
To see the generated mesh, set the
**
ai_DebugDrawNavigation
**
 CVar to
**
1
**
,
**
2
**
, or
**
3
**
. Also set
**
 ai_DebugDraw
**

**
1
**
,
 or use the
**
Debug Navigation Agent Type
**
 option from the
**
Game → AI
**
 menu.
The following screenshot shows a created Navigation Area (purple shape) and the NavMesh generated inside it.

![Image](https://www.cryengine.com/docs/static/attachments/44965395)

*
Selected Navigation Area and its properties
*

##
Shape Surface Alignment

Creating Navigation Areas above or below the terrain or object surface can prevent NavMeshes from generating properly. To avoid this, make sure you place the base of the Navigation Area's shape below the terrain/object, and its top above the terrain/object to provide plenty of clearance.

![Image](https://www.cryengine.com/docs/static/attachments/44965392)

 |
![Image](https://www.cryengine.com/docs/static/attachments/44965396)

 |

*
Navigation Area is too small and isn't covering all geometry.
*
 |
*
Properly sized and positioned Navigation Area.
*
 |

The Editor's
**
Game → AI
**
 menu contains options to visualize and update Navigation Areas; for a complete list of options and their functions, please refer to the
[Game Menu](/docs)
's documentation.

Debugging in the Game Launcher
It's possible to visualize NavMeshes within the
[Game Launcher](../../../Packaging%20and%20Deployment/Game%20Executable%20Launcher.md)
 by using the following CVars:

-
**
ai_debugMNMAgentType
**

*
AgentTypeName
*
 (e.g.
**
MediumSizedCharacters).
**

-
**
ai_debugDraw
**

**
1
**
.

-
**
ai_debugDrawNavigation
**

**
1
**
 (or one of the other options associated with this CVar).

##
Exclusion Areas

If you don't want a NavMesh to be generated within a specific region of an existing Navigation Area:

-
Create a new Navigation Area within the existing Navigation Area.

-
From under the
**
Navigation Area
**
tab in the Properties Tool, enable the
**
Exclusion
**
 property of the new Navigation Area.
Areas that are so excluded from a Navigation Area are colored red to indicate that they cannot be used by AI to navigate within, as shown in the image below.

![Image](https://www.cryengine.com/docs/static/attachments/44965393)

*
Exclusion Area marked in red
*

The Exclusion Area placed in the middle of the image above ensures that the NavMesh isn't generated on rough rocky terrain.

##
Accessibility and Seed Points

Creating a NavMesh around multiple objects generates areas that might be inaccessible to AI characters while path-finding; these inaccessible areas can be filtered out by using Seed Points. Refer to the
[Accessibility and Seed Points](Accessibility%20and%20Seed%20Points.md)
 documentation for more information on placing Seed Points and computing the accessibility of NavMeshes.

![Image](https://www.cryengine.com/docs/static/attachments/44965390)

 |
![Image](https://www.cryengine.com/docs/static/attachments/44965391)

 |

*
NavMesh at the top is blocked by a boat (in the middle), therefore it is not accessible (shown in grey).
*
 |
*
If the inaccessible part of a NavMesh is needed for navigation from a level design perspective, additional Seed Points can be placed within that part.
*
 |

##
Updating Navigation

If navigation updates are enabled in Sandbox, modifying the level map (e.g. adding/deleting/moving objects or modifying the terrain in a way that affects the navigation) causes the navigation system to automatically recalculate NavMeshes to reflect these changes. However, only those parts of the NavMeshes that are affected by the change are recalculated.

Users can choose between three different update modes from under the
**
Game → AI → Navigation Update Modes
**
 menu, namely,
**
Continuous
**
,
**
After Change
**
 and
**
Disabled
**
. For a complete description of their functions, please refer to the
[Game Menu](/docs)
's documentation.

You can easily tell if a Navigation Area is being updated by a small character icon that is displayed at the top left of the screen. If multiple NavMeshes need to be updated, a progress bar might be shown as well.

##
Multi-threading

By default, navigation updates run on multiple threads and the number of different jobs that can run per thread is specified by the ai_NavGenThreadJobs CVar (default value is 1).

Although raising this value can speed up NavMesh generation, doing so may also create stalls in the Editor as the results of NavMesh generation jobs are applied to NavMeshes in the main frame. Multi-threaded generation can be disabled by setting the value of the
**
ai_NavigationSystemMT
**
 CVar to
**
0
**
.

##
Updating at Run-time

Although automatic navigation updates are disabled at run-time, it is possible to update parts of NavMeshes manually. To learn more, refer to the
[Run-Time MNM Regeneration](Run-Time%20MNM%20Regeneration.md)
 documentation.

##
Navigation System Warning

While the navigation is being updated or while parts of NavMeshes are not up to date, you may sometimes receive a "Navigation System Warning" when trying to export your level. This warning is to prevent the navigation from being in an inconsistent state, and should not be interrupted to be safe.

![Image](https://www.cryengine.com/docs/static/attachments/44965394)

*
Navigation System Warning
*

[Creating a New Navigation Area](#creating-a-new-navigation-area)
[Exclusion Areas](#exclusion-areas)
[Accessibility and Seed Points](#accessibility-and-seed-points)
[Updating Navigation](#updating-navigation)
[Navigation System Warning](#navigation-system-warning)
