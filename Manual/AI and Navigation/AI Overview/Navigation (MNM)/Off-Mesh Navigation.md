# Off-Mesh Navigation

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/25534290
- Page ID: 25534290
- Breadcrumb: AI and Navigation > AI Overview > Navigation (MNM) > Off-Mesh Navigation
- Parent: Navigation (MNM)

## Child Pages

- [Smart Objects System](Off-Mesh Navigation/Smart Objects System.md)
- [AI Paths](Off-Mesh Navigation/AI Paths.md)

## Content

[Image: /docs/static/attachments/29933211]

##
Overview

##
Sections

Off-Mesh Navigation implies AI traversing inside the game world which is not using the Multilayer Navigation Mesh system. There are two main methods of this,
[/docs/static/engines/cryengine-3/categories/1114113/pages/1048823#AIControlObjects-SmartObject](
Smart Objects
)
 and
[/docs/static/engines/cryengine-3/categories/1114113/pages/1048823#AIControlObjects-AIPath](
AI Paths
)
.

Navigational
*
Smart Objects
*
 can be used on top of navigation meshes. This helps AI characters transition from one object to another which would be otherwise impossible to navigate and plays a custom animation during the traversal.

For example, a Crysis 3
*
Stalker
*
 running alongside the wall of a building and then leaping onto a lamp post... this is done with Smart Objects.

AI Paths are simpler to setup and don't require any additional animations, but both options have their pros and cons.

[#sections](
Sections
)
[#smart-objects](
Smart Objects
)
[#ai-paths](
AI Paths
)

##
Smart Objects

When adding a Smart Object, make sure its entry and exit points are within the navigation mesh area. An incorrectly placed Smart Object will flash red.

For an AI character to be able to use the Smart Object, its
[/docs/static/engines/cryengine-3/categories/1114113/pages/1048689](
agent type
)
 definition should list one or more
*
Smart Object User Classes
*
 which the
*
Smart Object
*
 has.

For example, if a
*
Smart Object
*
 has class
**
Human
**
 and an AI character is of agent type
**
MediumSizedCharacters
**
, the following lines should present in the
`
Scripts/AI/Navigation.xml
`
 file, within tag
**
<AgentType name="MediumSizedCharacters" ... >
**
:

```

`
<SmartObjectUserClasses>
  <class name="Human"/>
  ...
</SmartObjectUserClasses>
`

```

The usual debug draw for the
*
Smart Object
*
 will show if it is properly connected to the navigation mesh.

Also, you can set
**
ai_DebugDrawNavigation
**
 to
**
3
**
 to display the linked triangles (the ones with
*
red
*
 edges).

##
AI Paths

It is also possible to use
[/docs/static/engines/cryengine-3/categories/1114113/pages/1048823#AIControlObjects-AIPath](
AI Paths
)
 for off-mesh navigation. This can be useful for intersecting multiple separate MNM areas, if AI need to traverse between them.

Care should be taken when using AI Paths in this manner however. If an AI manages to get into combat during the AI Path travels, they can become stuck as they have no freedom of movement like they would inside an MNM area.

Unless your level markup ensures it, off-mesh navigation should be done as non-interruptible in the AISequence:Start node.
