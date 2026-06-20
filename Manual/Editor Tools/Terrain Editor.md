# Terrain Editor

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/35849146
- Page ID: 35849146
- Breadcrumb: Editor Tools > Terrain Editor
- Parent: Editor Tools

## Child Pages

- [Terrain Block Import & Export](Terrain%20Editor/Terrain%20Block%20Import%20%26%20Export.md)
- [Terrain Minimaps](Terrain%20Editor/Terrain%20Minimaps.md)
- [Terrain Object Blending](Terrain%20Editor/Terrain%20Object%20Blending.md)

## Content

##
Overview

The Terrain Editor is used to modify the terrain in the current level. With this tool, it is possible to create mountains, valleys and everything that is terrain related. Users can also assign textures and materials to the terrain to make it look like any kind of surface which suits the current project.

By default, the Terrain Editor is displayed on the right side of Sandbox, but it can also be opened via
**
Tools → Terrain Editor
**
.

![Image](https://www.cryengine.com/docs/static/attachments/44107954)

There are currently three editing modes on the Terrain Editor namely;

-
**
Sculpt
**

-
**
Paint
**

-
**
Mini Map
**
These modes manipulate the different aspects of the terrain and users can achieve unique results by combining them.

The default Terrain Editor layout is comprised of the following main sections:

##
1. Menu

The menu is always the same regardless of which editing mode is active and it can be displayed by clicking the
![Image](https://www.cryengine.com/docs/static/attachments/44109371)
 icon on the top-right corner of the Terrain Editor.

##
File

Option

 |
Description

 |

**
Generate Terrain Texture...
**

 |
Generates terrain texture that will be used in the game mode. This option only generates the tint texture, not the material layers.

When
**
Generate Terrain Texture...
**
 is chosen, the following options will be displayed:

-
**
Texture Dimensions -
**
 This option should be set to the desired size of the terrain texture. It can be set to a value lower than the terrain texture resolution to save time.
Setting the resolution higher than the actual terrain texture size will not affect the rendering time because it will only render max resolution of the terrain.

-
**
Terrain Color Multiplier -
**
 When the generated surface texture is compressed using DXT, its colors always get somewhat distorted. If the colors use the full dynamic range (0-255), they are preserved better. If artists know that they have used only darker colors in the level, they can use the
**
Terrain Color Multiplier
**
 to make the colors use more of the dynamic range. For example, if only colors in the 0-63 range have been used, entering a multiplier value of 4 would make them fill the entire 0-255 range and "survive" the compression in a better shape. When rendering, the decompressed color values should be divided by the multiplier in the shader to restore the original brightness.

-
**
High Quality Terrain Texture -
**

-
Uses a more different code for texture compression.

-
Terrain texture generation will take 2-3 times longer but there will be less compression on the artifacts.

-
Does not affect memory usage or CPU in final game.
 |

**
Generate Terrain...
**

 |
Randomly creates terrain depending on a several parameters. The parameters that can be changed are:

-
**
Feature Size -
**
 Determines the amount of land created.

-
**
Bumpiness/Noise -
**
 Determines the degree of bumpiness or deformation of the surface.

-
**
Detail -
**
 Determines the number of times that effects will be applied.

-
**
Variation -
**
 Determines the random seeding of the islands.

-
**
Blurring -
**
 Sets the number of times that smoothing will be applied to the noise filter.

-
**
**
**
**
**
**
Cover (Exp. Substract) -
**
**
**
**
**
**

**
**
**
**
**
**
DEPRECATED
**
**
**
**
**
**

-
**
Sharpness (Exp. Base) -
**
 Determines the sharpness of the surface.

-
**
Sharpness (Freq. Step) -
**
 Determines the number of times that the sharpness filter will be used on the surface.
 |

**
Import Heightmap...
**

 |
Lets users import an image to be used as the new heightmap. The size of the heightmap must be equal to or smaller than the current level heightmap resolution.

Supported files are as follows:

-
**
8-bit.bmp
**

-
**
16-bit.pgm
**

-
**
16-bit.raw
**

-
**
16-bit.raw r16
**
 |

**
Export Heightmap...
**

 |
Use this option to export the heightmap file to be edited in Photoshop (version CS1+ required).

Supported files are as follows:

-
**
8-bit.bmp
**

-
**
16-bit.pgm
**

-
**
16-bit.raw
**

-
**
16-bit.raw r16
**
 |

**
Import Terrain Block...
**

 |
Imports a block of terrain including the vegetation on it.

 |

**
Export Terrain Block...
**

 |
Exports a block of terrain including the vegetation on it.

 |

**
Export Terrain Area...
**

 |
Exports a terrain area
 as an
**
.obj
**
 file that can be opened in other 3D software.

 |

**
Export Terrain Area With Objects...
**

 |
Exports a terrain area includin
g the objects on it as

an
**
.obj
**
 file that can be loaded in other 3D software.

 |

**
Export/Import Terrain Texture...
**

 |
Exports and imports terrain texture of a selected tile or tiles. The t
errain can be divided into tiles by choosing
**
Terrain Editor → Edit → Refine Terrain Texture Tiles
**
.

 |

**
Import Layers...
**

 |
Imports layers that have been set up and exported.

 |

**
Export Layers...
**

 |
Exports the layers that have been set up in the
**
Paint
**
 mode.

 |

##
Edit

Option

 |
Description

 |

**
Select Terrain
**

 |
Lets users select a part of the terrain.

 |

**
Make Isle
**

 |
Sinks the current heightmap.

 |

**
Remove Ocean
**

 |
Sets the water level to -100000.

 |

**
Set Ocean Height
**

 |
This feature adjusts the water level. The default level sits on 16m.

 |

**
Set Terrain Max Height
**

 |
Adjusting this value will change how high the tallest mountain can be. The default height is 1024.

 |

**
Flatten (Light)
**

 |
Flattens terrain to either the highest or the lowest point.

 |

**
Flatten (Heavy)
**

 |
Flattens terrain to either the highest or the lowest point.

 |

**
Smooth
**

 |
Removes hard edges on the entire terrain.

 |

**
Smooth Slope
**

 |
Removes hard edges from steep areas.

 |

**
Smooth Beach/Coast
**

 |
Removes hard edges from flat areas.

 |

**
Normalize
**

 |
Makes sure that the entire greyscale spectrum is used. The highest point is the one specified in max height and the lowest point is 0.

 |

**
Reduce Range (Light)
**

 |
Makes mountains smaller.

 |

**
Reduce Range (Heavy)
**

 |
Makes mountains smaller.

 |

**
Erase Terrain
**

 |
This option will delete the current heightmap data.

 |

**
Resize Terrain
**

 |
Re-opens the initial heightmap creation panel to adjust the Heightmap Resolution and Meters Per Unit scale.

 |

**
Invert Heightmap
**

 |
Changes black to white on the heightmap.

 |

**
Reload Terrain
**

 |
Reloads the terrain.

 |

**
Refine Terrain Texture Tiles
**

 |
Divides the terrain tiles into more smaller sections.

 |

**
Brush Settings...
**

 |
Opens the Brush Preferences panel where users can modify Terrain Editor's brush.

-
**
Hardness Sensitivity -
**
The rate at which the brush Hardness changes per pixel.

-
**
Radius Sensitivity -
**
The rate at which the brush Outside Radius changes per pixel.
Alternatively, users can adjust the Sensitivity values by scrolling up or down when using the
**
Alt + LMB
**
 function which is explained in the
[Sculpt Mode → Brush](Terrain%20Editor.md#TerrainEditor-sculptbrush)
 section below.
 |

##
Toolbars

Option
 |
Description
 |

**
Customize
**
 |
Opens the toolbar customization window allowing users to create new toolbars within the Terrain Editor window.
 |

**
Lock Toolbars
**
 |
When disabled, the positions of toolbars and spacers within the Terrain Editor window can be changed by drag and drop.
 |

**
Spacers
**
 |
The following options allow users to use spacers in positioning their toolbars.

**
Insert Expanding Spacer
**
 |
Adds an expanding spacer to the toolbar layout; an expanding spacer pushes all elements situated at its ends to the edge of the tool window.
 |

**
Insert Fixed Spacer
**
 |
Adds a fixed spacer, which has a fixed size of one icon.
 |

The
**
Spacers
**
 menu options are only available when
**
Toolbars → Lock Toolbars
**
 is disabled.

 |

**
Toolbars
**
 |
Lists all default and custom toolbars created for the Terrain Editor, allowing you to select which toolbar you'd like to hide or display.
 |

When a tool has a toolbar, whether this is a default one or a custom one, the options above are also available when right-clicking in the toolbar area (only when a toolbar is already displayed).

##
Layers

Sandbox uses layers for two main reasons: Organizing your level content and Streaming performance.

Any object you place on a layer (vegetation/terrain excluded) can be hidden/unhidden via the Layer Control and also via Flowgraph, which allows loading/unloading of level areas to keep performance high and memory consumption low.

Option

 |
Description

 |

**
Create Layer
**

 |
Creates a new layer on the Paint tab.

 |

**
Delete Layer
**

 |
Removes the selected layer from the Paint tab.

 |

**
Duplicate Layer
**

 |
Duplicates the selected layer and places it above the original layer.

 |

**
Move to Top
**

 |
Moves the selected layer to the top of the layers list.

 |

**
Move Up
**

 |
Moves the selected layer up one place in the list.

 |

**
Move Down
**

 |
Moves the selected layer down one place in the list.

 |

**
Move to Bottom
**

 |
Moves the selected layer to the bottom of the layers list.

 |

**
Flood Layer
**

 |
Paints the whole terrain with selected terrain texture layer.

 |

##
Tools

The Tools menu provides quick access to each of Sculpt Mode's terrain modification tools, along with the option to switch to Paint Mode to alter any of the textures/materials assigned to the terrain.

##
Help

Opens the documentation page for this tool.

##
2. Modes

##
Sculpt Mode

Sculpt mode is enabled by default when the Terrain Editor is opened.

*
![Image](https://www.cryengine.com/docs/static/attachments/36835898)

*

With this mode, it is possible to modify the terrain height in various ways such as flattening it, raising/lowering it, making holes, smoothing it, duplicating it and filling the holes.

##
Flatten

When the
**
Flatten
**
 button is clicked, the following options appear:

![Image](https://www.cryengine.com/docs/static/attachments/36835893)

Section

 |
Options
 |

**
**
Brush
**
**

 |
Option
 |
Description
 |

**
Share Parameters
**
 |
Sets the values of the brush (inside/outside radius etc.) to be applied across all the tools within the Terrain Editor. Untick the box to make these values independent again.
 |

**
Radius (outside)
**
 |
Changes the outside radius of the brush that is used to modify the terrain.

The Outside Radius can also be adjusted by holding
**
Alt+LMB
**
 and moving the mouse left and right. The rate at which the Outside Radius changes by doing this is determined in the Preferences.

 |

**
Radius (inside)
**
 |
Changes the inside radius of the brush that is used to modify the terrain. If the inside radius is the same as the outside
radius, a column will be created. If the inside radius is smaller, a dome effect will be created when the terrain is being modified.

![Image](https://www.cryengine.com/docs/static/attachments/35959297)
 |
![Image](https://www.cryengine.com/docs/static/attachments/35959296)
 |

*
Inside Radius = 20
*

*
 Outside Radius = 20 -> column
*

 |
*
Inside Radius = 0
*

*
 Outside Radius = 20 -> dome
*

 |

 |

**
Hardness
**
 |
(0 - 1) The higher the Hardness value is, the more quickly the terrain will be modified.

The Hardness can also be adjusted by holding
**
Alt+LMB
**
 and moving the mouse up and down. The rate at which the Hardness changes by doing this is determined in the Preferences.
 |

**
Height Target
**
 |
Is used as a multiplier for when users paint with the brush. Using a
**
Height Target
**
 value of
**
1
**
 with a
**
Hardness
**
 of
**
1
**
 will move the

terrain up 1 meter with one click. A
**
H
**
**
eight Target
**
 value of
**
2
**
 with a
**
Hardness
**
 of
**
1
**
 will move the terrain up 2 meters with one click etc.
 |

The
**
Pick
**
 button next to the
**
Height Target
**
 value lets users pick a Height value directly from the terrain in the Viewport.

 |

**
Displacement
**
 |
Here, a displacement map can be chosen and used. This lets users paint with a texture map, for example multiple photogrammetry or pre-made displacement maps, to quickly build detailed terrain.

Option
 |
Description
 |

**
Enable Displacement
**
 |
When this option is enabled, the Editor will immediately load the displacement map set below and use it during painting.
 |

**
Displacement Scale
**
 |
Defines the size of the area the displacement map will be painted on.
 |

**
Displacement Map
**
 |
Selects the displacement map to be used.

 |

 |

**
Reposition
**
 |
Option
 |
Description
 |

**
Objects
**
 |
When enabled, this option will make sure that the objects remain placed on the terrain when flattening the terrain to a different height.
 |

**
Vegetation
**
 |
When enabled, this option will make sure that the vegetation remains placed on the terrain to a different height.
 |

 |

##
Raise/Lower

With this mode enabled, the terrain can be raised or lowered. It is the primary tool for terrain sculpting, allowing users to make mountains, lakes and adjust terrain freely.

When the
**
Raise/Lower
**
 button is clicked, the same options appear as above, with the exception of the
**
Pick
**
 button:

![Image](https://www.cryengine.com/docs/static/attachments/36835894)

Section
 |
Option
 |

**
Brush
**
 |
Option
 |
Description
 |

**
Share Parameters
**
 |
Sets the values of the brush, such as inside/outside radius, to be applied across all the tools within the Terrain Editor. Untick the box to make these values independent again.
 |

**
Outside Radius
**
 |
Changes the outside radius of the brush that is used to modify the terrain.

The outside radius of the brush can also be adjusted by holding
**
 Alt+LMB
**
 and moving the mouse left and right. The rate at which the Outside Radius changes by doing this is determined in the Preferences.

 |

**
Inside Radius
**
 |
Changes the inside radius of the brush that is used to modify the terrain. If the inside radius is the same as the outside
radius, a column will be created. If the inside radius is smaller, a dome effect will be created when the terrain is being modified.
 |

**
Hardness
**
 |
(0 - 1) The higher the Hardness value is, the more quickly the terrain will be modified.

The Hardness can also be adjusted by holding
**
Alt+LMB
**
 and moving the mouse up and down. The rate at which the Hardness changes by doing this is determined in the Preferences.

 |

**
Height
**
 |
Is used as a multiplier for when users
paint with the brush. Using a
**
Height
**
 value of
**
1
**
 with a
**
Hardness
**
 of
**
1
**
 will move the
terrain up 1 meter with 1 click. A
**
H
**
**
eight
**
 value of
**
2
**
 with a
**
Hardness
**
 of
**
1
**
 will move the terrain up 2 meters with 1 click etc.
 |

 |

**
Displacement
**
 |
Here, a displacement map can be chosen and used. This lets users paint with a texture map, for example multiple photogrammetry or pre-made displacement maps, to quickly build detailed terrain.

Option
 |
Description
 |

**
Enable Displacement
**
 |
When enabled, the Editor will immediately load the displacement map set below and use it during painting.
 |

**
Displacement Scale
**
 |
Defines the size of the area on which the displacement map will be painted.
 |

**
Displacement Map
**
 |
Select the displacement map to be used.
 |

 |

**
Reposition
**
 |
Option
 |
Description
 |

**
Objects
**
 |
When enabled, this will make sure that the objects remain placed on the terrain when raising/lowering the terrain to a different height.
 |

**
Vegetation
**
 |
When enabled, this will make sure that the vegetation remains placed on the terrain when raising/lowering the terrain to a different height.
 |

 |

##
Make Holes

This mode lets users cut holes in the terrain. This is not the same as lowering the terrain; instead of digging the terrain until it's under the level of the ocean, it actually cuts a square piece out of the terrain.
It can be used to create cave entrances or cliff overhangs which are built with meshes.

**
![Image](https://www.cryengine.com/docs/static/attachments/36835895)
**

In this mode, only
**
Brush
**
 options are available:

Option

 |
Description

 |

**
Share Parameters
**

 |
Sets the values of the brush, such as inside/outside radius, to be applied across all the tools within the Terrain Editor.
Untick the box to make these values independent again.

 |

**
Radius (outside)
**

 |
Changes the size of the brush.

The Outside Radius can also be adjusted by holding
**
 Alt+LMB
**
 and moving the mouse left and right. The rate at which the Outside Radius changes by doing this is determined in the Preferences.

 |

##
Smooth

The
**
Smooth
**
 mode lets users create smooth edges in the terrain, making the change in height more gradual.

![Image](https://www.cryengine.com/docs/static/attachments/36835896)

![Image](https://www.cryengine.com/docs/static/attachments/35959295)

![Image](https://www.cryengine.com/docs/static/attachments/35959294)

*
Terrain before and after smoothing
*

Section
 |
Description
 |

**
Brush
**
 |
Option
 |
Description
 |

**
Share Parameters
**
 |
Sets the values of the brush, such as inside/outside radius, to be applied across all the tools within the Terrain Editor.
Untick the box to make these values independent again.
 |

**
Radius
**
 |
Changes the size of the brush that is used to modify the terrain.

The Outside Radius can also be adjusted by holding
**
 Alt+LMB
**
 and moving the mouse left and right. The rate at which the Outside Radius changes by doing this is determined in the Preferences.

 |

**
Hardness
**
 |
(0 - 1) The higher the Hardness value is, the more quickly the terrain will be modified.

The Hardness can also be adjusted by holding
**
Alt+LMB
**
 and moving the mouse up and down. The rate at which the Hardness changes by doing this is determined in the Preferences.

 |

 |

**
Reposition
**
 |
Option
 |
Description
 |

**
Objects
**
 |
When enabled, will make sure that objects remain placed on the terrain when smoothing the terrain to a different height.
 |

**
Vegetation
**
 |
When enabled, will make sure that vegetation remains placed on the terrain when smoothing the terrain to a different height.
 |

 |

##
Duplicate

This mode allows the user to duplicate one area of the map to another based on Source and Target boxes.

![Image](https://www.cryengine.com/docs/static/attachments/36835904)

This mode has the following
**
Clone Terrain
**
 options:

Option

 |
Description

 |

**
Select
**

 |

-
**
Source -
**
 Place a box around the terrain to copy.

-
**
Target -
**
 Place a box on the position where the terrain to be copied.
 |

**
Size
**

 |
Determines the size of the Source and Target boxes.

 |

**
Target Rotation
**

 |
Rotates the terrain in the Target box by 0/90/180/270 degrees counterclockwise.

 |

**
Only Vegetation
**

 |
Copies only the vegetation in the
Source
box to the Target box and leaves the terrain as it is.

 |

**
Only Terrain
**

 |
Copies only the terrain in the Source box to the Target box.

 |

**
Sync Height
**

 |
Synchronizes the height of the Source and Target boxes so they are always at the same height, independent of the height of the terrain.

 |

**
Move Objects
**

 |
Moves objects on the terrain from the Source box to the Target box instead of copying them. Using this option will cause the objects in the Source box to disappear.

 |

**
Action
**

 |

-
**
Apply
**
**
-
**
 Copies the terrain in the
Source
box to the Target box.
 |

##
Fill Holes

**
Fill Holes
**
 is the opposite of Make Holes. The sole purpose of this mode is to close the holes that were made with the Make Holes mode.

![Image](https://www.cryengine.com/docs/static/attachments/36835905)

This mode has the same two options as the
**
Make Holes
**
 mode:

Option

 |
Description

 |

**
Share Parameters
**

 |
Sets the values of the brush, such as inside/outside radius, to be applied across all the tools within the Terrain Editor.
Untick the box to make these values independent again
.

 |

**
Radius
**

 |
Changes the size of the brush.

The Outside Radius can also be adjusted by holding
**
 Alt+LMB
**
 and moving the mouse left and right. The rate at which the Outside Radius changes by doing this is determined in the Preferences.

 |

##
Paint Mode

Paint mode lets users change the textures and materials of the terrain, making it look like the desired surface. The default is a checkerboard, but this material can be replaced by any
**
.mtl
**
 file.

![Image](https://www.cryengine.com/docs/static/attachments/36835906)

The Paint mode consists of three sections:

-
**
Layers window
**

-
**
Brush parameters
**

-
**
Layer parameters
**

##
Layers Window

In the Layers window, layers that are painted on the terrain in the level can be found. They can be re-named by double-clicking on their name field. Right-clicking anywhere in the Layers window will reveal a context menu with the following options:

Option

 |
Description

 |

**
Create Layer (below)
**

 |
Creates a new layer below the currently selected layer of the Layers Window. Right clicking below the final layer and selecting the
**
Create Layer
**
 option also creates a new layer under the selected layer.

 |

**
Delete Layer
**

 |
Deletes the selected layer.

 |

**
Duplicate Layer
**

 |
Makes a copy of the selected layer.

 |

**
Move to Top
**

 |
Moves the selected layer to the topmost level of the list.

 |

**
Move Up
**

 |
Moves the selected layer up a single level on the list.

 |

**
Move Down
**

 |
Moves the selected layer down a single level.

 |

**
Move to Bottom
**

 |
Moves the selected layer to the bottom of the list.

 |

**
Flood Layer
**

 |
Floods the layer according to the parameters set in the layer's parameters.

 |

Layers can also be reordered by dragging and dropping in the Layers window.

##
Brush Parameters

The brush parameters are shown when the
**
Paint
**
 button in this section is pressed.

Option

 |
Description

 |

**
Range
**

 |
Changes the size of the brush.

The Outside Radius can also be adjusted by holding
**
 Alt+LMB
**
 and moving the mouse left and right. The rate at which the Outside Radius changes by doing this is determined in the Preferences.

 |

**
Hardness
**

 |
The
**
Hardness
**
 slider changes the strength of the brush in applying the material. A lower value will give a softer translucent effect, whereas 1 means the material painting is completely opaque.

The Hardness can also be adjusted by holding
**
Alt+LMB
**
 and moving the mouse up and down. The rate at which the Hardness changes by doing this is determined in the Preferences.

 |

**
Paint with Material
**

 |
When set, the painter will only paint the detail texture of the terrain material.

 |

**
Mask by Height/Angle
**

 |
Sets the material to only paint between the Height and Angle parameters defined within the Layer section below.

 |

**
Mask by Layer
**

 |
Select a layer from the drop-down list to make sure this is the only layer that is painted on.

 |

##
Layer Parameters

The Layer parameters determine what the layer will look like and where it is painted on the terrain.

Option

 |
Description

 |

**
 Color
**

 |
Assigns a color to the currently selected layer.

 |

**
Texture
**

 |
Chooses a texture for the selected layer.

 |

**
Material
**

 |
Chooses a material for the selected layer.

 |

**
Height (min)
**

 |
Sets a maximum height mask for painting. The layer will only be painted above this height.

 |

**
Height (max)
**

 |
Sets a minimum height mask for painting. The layer will only be painted below this height.

 |

**
Angle (min)
**

 |
Sets a minimum angle mask in degrees for painting. The layer will only be painted on terrain that is angled higher than this value.

 |

**
Angle (max)
**

 |
Sets a maximum angle mask in degrees for painting. The layer will only be painted on terrain that is at an angle lower than this value.

 |

##
Mini Map

This part of the Terrain Editor is known to be nonfunctional. It will either be fixed or replaced in the future.

##
Context Menu

Right-clicking a field name or its corresponding value within the
**
Brush
**
 or
**
Layer
**
 parameter sections reveals a context menu with varying options. Depending on where the user clicks, the context menu may include the following options:

Option

 |
Description

 |

**
Expand
**

 |
Expands the Brush and Layer parameters.

 |

**
Collapse
**

 |
Collapses the Brush and Layer parameters.

 |

**
Pick Color
**

 |
Opens the Select Color window in which a color can be chosen or specfic RGB values can be entered.

 |

**
Pick Resource
**

 |
Picks a texture or material, depending on whether the user right-clicks on the texture or the material box. This option has the same functionality as the browser button next to these boxes.

 |

**
Clear
**

 |
Unassigns the texture or material, depending on whether the user right-clicks on the texture or the material box. this option has the same functionality as the browser button next to these boxes.

 |

**
Undo
**

 |
Undoes the last action in that particular box.

 |

**
Copy
**

 |
Copies the value in the selected box to the clipboard.

 |

**
Paste
**

 |
Pastes the value from the clipboard to the selected box.

 |

**
Copy All
**

 |
Copies all values in the Layers parameters to the clipboard, with the exception of
Filter Color value.

 |

**
Paste All
**

 |
Pastes all values from the clipboard,
except for the Filter Color value,
 and replaces the Layers parameters with these.

 |

**
Filter...
**

 |
Filters the options that can be displayed on the panel based on the text that has been entered on the field.

 |

**
Filter by
**

 |
Filters the options that can be displayed on the panel based on the
name, the value or the type of the selected parameter.

 |

[1. Menu](#1-menu)
[2. Modes](#2-modes)
[Context Menu](#context-menu)
