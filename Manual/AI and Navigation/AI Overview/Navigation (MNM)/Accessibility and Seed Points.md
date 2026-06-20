# Accessibility and Seed Points

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/36340564
- Page ID: 36340564
- Breadcrumb: AI and Navigation > AI Overview > Navigation (MNM) > Accessibility and Seed Points
- Parent: Navigation (MNM)

## Content

##
Overview

Creating a NavMesh around multiple objects often generates areas that might be inaccessible to AI characters while path-finding, such as rooftops, the interiors of structures and so forth.

These inaccessible areas can be filtered out by using Seed Points, such that the triangles of a mesh that are not connected to a Seed Point are marked as inaccessible.

This accessibility is computed by performing a flood-fill algorithm within the NavMesh; islands with triangles that are connected to a Seed Point directly or by off-mesh links are accessible and hence colored blue, while the rest are grayed out.

![Image](https://www.cryengine.com/docs/static/attachments/36316040)

*
Areas inaccessible from the Seed Point (center) are grayed
*

An island is any isolated area within the created NavMesh that contains a placed prop or object. In the images on this page, each of the placed structures are islands in themselves.

##
Functionality

##
Seed Points

-
In order to compute the accessibility of islands within a NavMesh, at least one Seed Point needs to be placed inside the NavMesh's Navigation Area volume. Seed Points are found under
**
AI → Navigation Seed Point
**
 within the
[Create Object](../../../Editor%20Tools/Level%20Editor%20Tab/Create%20Object.md)
 tool.

-
The flood-fill algorithm begins with the triangle that is at a distance of one unit from the placed Seed Point on the triangulated NavMesh; a triangle is colored blue if accessible from the Seed Point, else it is grayed out.
If the position of the Seed Point is changed, the accessibility to triangles is recalculated and updated accordingly. Similarly if a NavMesh had no Seed Points, it will not contain any inaccessible (gray) areas as shown below.

*
![Image](https://www.cryengine.com/docs/static/attachments/36316223)

*

*
Navmesh (bottom-right) with no seed point
*

Any number of Seed Points may be included within a NavMesh, allowing the accessibility of multiple areas of importance to be computed.

Moreover, the AI characters included within GameSDK (
**
Legacy Entities → AI → Characters → Human
**
) are also considered as Seed Points, when placed within a NavMesh, provided the
[Agent Type](Navigation%20Configuration.md)
 of the NavMesh is the same as that of the character.

To set the Agent Type of a NavMesh,

-
Select the NavMesh from the Viewport/Level Explorer; this will cause its properties to be displayed within the Properties Tool.

-
Checkboxes for available Agent Types should be listed in the
**
Navigation Area
**
 panel of the Properties Tool, below the
**
Display Filled
**
 option, as shown in the image below. Tick the corresponding boxes to set the Agent Type of the NavMesh.
Agent Types must first be defined and configured in
 the
*
Navigation.xml
*

file located under
*
ProjectFolder/Scripts/AI/.
*
Please refer to the Navmesh Agent Types
[documentation](Navigation%20Configuration.md)
 for more information.

![Image](https://www.cryengine.com/docs/static/attachments/44960186)

*
Navigation Area
*

The position of islands and their accessibility is calculated only after the generation of a NavMesh has been fully completed. Moreover, the time taken to update a NavMesh depends on the size of the mesh itself.

Hence, when making any changes to a NavMesh in Game Mode, users must be aware that its accessibility information might be in an inconsistent state until the NavMesh has been completely updated.

##
Removing Inaccessible Triangles

If the inaccessible triangles of a NavMesh aren't used within a game, they're best discarded to improve performance; the fewer triangles a NavMesh has, the more efficient computational queries within the NavMesh become.

Enabling the
**
Remove Inaccessible Triangles
**
 property of a Navigation Area removes inaccessible triangles when the level is loaded in the
[Game Launcher](../../../Packaging%20and%20Deployment/Game%20Executable%20Launcher.md)
; this property is located under the
**
Navigation Area
**
tab of the Properties panel, when an existing Navigation Area is selected via the Level Explorer or Viewport.

![Image](https://www.cryengine.com/docs/static/attachments/44960184)

*
Remove Inaccessible Triangles
*

-
**
Remove Inaccessible Triangles
**
 is enabled by default.

-
Navigation Areas are displayed with a darker blue color when the
**
Remove Inaccessible Triangles
**
 property is enabled.

-
If the value of the
**
ai_MNMRemoveInaccessibleTrianglesOnLoad
**
 CVar is set to
**
0
**
 (default=1), the inaccessible triangles of Navigation Areas will not be removed even if the
**
Remove Inaccessible Triangles
**
 property is enabled.
![Image](https://www.cryengine.com/docs/static/attachments/36316039)

*
The NavMesh from the
[first image](Accessibility%20and%20Seed%20Points.md#AccessibilityandSeedPoints-inaccessible)
 with inaccessible triangles removed
*

The value of
**
ai_MNMRemoveInaccessibleTrianglesOnLoad
**
 is ignored when loading a NavMesh in the Sandbox Editor, and is taken into account when in the Game Launcher only. Moreover, removed triangles might reappear when the NavMesh is updated, although they'd still be marked as inaccessible (gray).

[Functionality](#functionality)
[Seed Points](#seed-points)
[Removing Inaccessible Triangles](#removing-inaccessible-triangles)
