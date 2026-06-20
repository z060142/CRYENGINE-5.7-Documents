# Solids

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/27593386
- Page ID: 27593386
- Breadcrumb: Entities and Tools > Entities Overview > Area Objects > Solids
- Parent: Area Objects

## Content

[Image: /docs/static/attachments/29933297]

##
Overview

 The Solid is for defining complex range of sound obstructions with CryDesigner, which is the Geometry Editing Tool.

##
Designer Tool

With the
[/docs/static/engines/cryengine-5/categories/23756816/pages/25534693](
Designer Tool
)
, any complex area for sound can be created. You can enter it by clicking
**
Edit
**
button in the Properties panel.

The "Designer Tool" will be started automatically when the empty areasolid is selected or new areasolid object is created.

##
Display of Memory Usage

You can see how much memory is used for the AreaSolid Object, which is displayed in the Edit mode.

It can be an indication to optimize the AreaSolid shape. The displayed memory usage is the real size occupied in the game mode.

 |
 |

Memory size is displayed.

 |
Every time you change the shape,

the memory usage will be updated.

 |

##
Workflow

1. Create a Box as an AreaSolid object.

2. Create "AudioAreaAmbience" entity in "Audio" group

3. Place the ambience sound entity near the AreaSolid Object

4. Select the ambience sound entity. Then you can see AudioAreaAmbience Properties on the right panel as below.

Fill PlayTrigger and RtpcDistance properties.

5. There is the "Attached Entities" dialog box in the AreaSolid roll-up bar on the right. You should attach the ambience sound entity to the AreaSolid object as a target of the "AreaSolid" object.

6. Try to modify the AreaSolid object with the Designer tool as explained above. If you want to visualize the sound to see how it works, type '
**
s_DrawAudioDebug = abcdefvw
**
' in the console. When you approach near an open space in the AreaSolid Object, you will be able to see the red ball as follows.

7. Every time you modify the AreaSolid object with the Designer Object, polygons consisting of the area solid will be transferred to the Engine side and you will be able to make sure the interaction between the sound object and the AreaSolid object as a result of the modification.

##
Go to "Solid Edit Mode"

1. Select the "AreaSolid" type of "Area" under the "Objects" menu on the roll-up bar.

2. Click "Designer" in the panel on the right to enter the edit mode.

[#designer-tool](
Designer Tool
)
[#display-of-memory-usage](
Display of Memory Usage
)
[#workflow](
Workflow
)
[#go-to-solid-edit-mode](
Go to "Solid Edit Mode"
)
