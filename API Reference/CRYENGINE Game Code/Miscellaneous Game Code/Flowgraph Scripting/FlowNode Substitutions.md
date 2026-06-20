# FlowNode Substitutions

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/23306553
- Page ID: 23306553
- Breadcrumb: CRYENGINE Game Code > Miscellaneous Game Code > Flowgraph Scripting > FlowNode Substitutions
- Parent: Flowgraph Scripting

## Content

##
Overview

Flowgraph is a very important tool for Level Designers because it permits them to create gameplay. In respect to code, then Flowgraph has been developed from various directions and over multiple projects. Furthermore, Flowgraph is made up of relatively few game-specific flownodes which can be changed or removed and without conflict to other projects. Most flownodes are created in CryAction and are shared between teams and projects. However, to remove or to change them usually requires everybody to be aware of the change(s) and to then fix all Levels using the respective 'changed' flownodes.

During production of Crysis 2 we introduced significant changes to the implementation of the component system. As a result, many Engine-wide flownodes became outdated and in effect were then useless. At the same time we needed a cleanup of Flowgraph to keep it usable, maintainable and also easy to understand for new Designers.

We overcame this issue by creating a project-specific blacklist which removes or renames flownodes, but without actually changing their implementation. The blacklist can be found in
`
GameSDK/Libs/FlowNodes/FlownodeBlacklist.xml
`
and alters the Flowgraph at load time. It can also be used in conjunction with the Substitutions.xml (which can be found the same folder) to completely change the representation of the flownodes, but without altering the code whilst preserving backwards compatibility and compatibility with other projects.

##
Usage

Usage of the Substitutions.xml is fairly straight forward. You input the existing (code-side) data and output the newly requested (script-side) data.

The Substitutions.xml is only used to keep your data updated. If the name of a flownode has been changed, but previous Flowgraphs are using the old name, then you can rename them to the current name of the node.

```

`
<Node OldClass="entity:HumanGrunt" NewClass="entity:Human" />
`

```

-
**
OldClass
**
 is the name of the existing node.

-
**
NewClass
**
is the actual name of the node.

##
Notes

Substitutions will only work in the Editor and they are intended to patch
**
existing
**
 Flowgraphs in Levels. If a change has been made, then you will need to open the Level in the Editor, save it and then re-export the Level to properly "fix" any changes.

FlownodeBlacklist is intended to rename
**
new
**
 instances of a node to be used in a Flowgraph(s), but without having to change Engine/gamecode.

##
Example

Let's rename a node from Time:TimeOfDay to Environment
:DayTime
 in the
**
FlownodeBlacklist:
**

```

`
<Ren class="Time:TimeOfDay" newClass="Environment:DayTime"/>
`

```

The change you have made here is where the node will appear in the Flowgraph nodes list, and of course the name of the node. It will now appear in the Environment folder and can be used without a problem for new Flowgraphs.

However, when you load a Level which already uses the
Time:TimeOfDay
 node, the Editor will give you an error saying that it cannot find the node, and the Launcher will completely discard the Flowgraph.

Therefore, the next step is to add the following codeblock to the
**
Substitutions
**
:

```

`
<Node OldClass="Time:TimeOfDay" NewClass="Environment:DayTime" />
`

```

This will now fix existing Flowgraphs referencing the
Time:TimeOfDay
 node and update them to use the Environment
:DayTime
 node, but only in the Editor. For use in the Launcher aswell? Then simply save and re-export the Level.
