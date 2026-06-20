# Water Volume

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/36869912
- Page ID: 36869912
- Breadcrumb: Editor Tools > Level Editor Tab > Create Object > Area > Water Volume
- Parent: Area

## Content

## Overview

Water Volumes are shape objects which can be used in a variety of different circumstances, such as rivers, lakes, pools, puddles or even oceans.

![Image](https://www.cryengine.com/docs/static/attachments/36849699)

### Properties

For the detailed description of the Shape area properties, please refer to [Shape](Shape.md).

**Property** | **Descriptions** |
--- | --- | ---
**Depth** | Specifies how deep the water volume should be. |
**Speed** | Specifies at which speed the water should be moving. Not used for water volumes, inherited from Area Shapes. |
**Fog Density** | Specifies the density of the fog. |
**Fog Color** | Defines the underwater fog color. |
**Fog Color Multiplier** | Determines how bright the underwater fog color is. |
**Fog Color Affected By Sun** | If true, Sun Color value set in the [Environment Editor (Old as of 26/2)](/docs/static/engines/cryengine-5/categories/23756816) will affect fog color of the water volume. |
**Fog Shadowing** | If enabled, the surface of the water volume will receive shadows. You can control the shadow darkness by using a valid input between 0 and 1. **r_FogShadowsWater** needs to be set to '1' for this to function, which is currently only enabled on Very High Spec. If ** Vol Fog Shadows** in ** Level Settings** is used, users lose control of shadow darkness which is automatically set to its full value. However, the upside of this is that the fog in the water volume will receive volumetric shadows. See the ** Usage Examples** section below for comparisons. |
**Cap Fog At Volume Depth** | If false, fog will continue to render below the specified Depth of water volume. |
**U Scale** | Specifies how much the water surface (bump) texture is tiled horizontally. |
**V Scale** | Specifies how much the water surface (bump) texture is tiled vertically. |
**Caustics** | Enables Caustics for this entity. |
**Caustic Intensity** | Controls the intensity of the caustics (this scales the normals of the surface when rendering to the caustic map, producing stronger caustics).![Image](https://www.cryengine.com/docs/static/attachments/1213737) |![Image](https://www.cryengine.com/docs/static/attachments/1213738) |![Image](https://www.cryengine.com/docs/static/attachments/1213739) --- | --- | --- **Intensity 1** | ** Intensity 4** | ** Intensity 8** |
![Image](https://www.cryengine.com/docs/static/attachments/1213737) | ![Image](https://www.cryengine.com/docs/static/attachments/1213738) | ![Image](https://www.cryengine.com/docs/static/attachments/1213739)
**Intensity 1** | **Intensity 4** | **Intensity 8**
**Caustic Tiling** | This is a multiplier for the tiling applied to the surface normals during caustic generation. It's used to scale the caustics generation independently from the surface material in cases of strong tiled normals or vice-versa.![Image](https://www.cryengine.com/docs/static/attachments/1213737) |![Image](https://www.cryengine.com/docs/static/attachments/1213746) |![Image](https://www.cryengine.com/docs/static/attachments/1213744) --- | --- | --- **Tiling 1** | ** Tiling 4** | ** Tiling 8** |
![Image](https://www.cryengine.com/docs/static/attachments/1213737) | ![Image](https://www.cryengine.com/docs/static/attachments/1213746) | ![Image](https://www.cryengine.com/docs/static/attachments/1213744)
**Tiling 1** | **Tiling 4** | **Tiling 8**
**Caustic Height** | Controls the height above the water entity in which caustics can be cast. This can be used to cause caustics on overhangs and other nearby objects.![Image](https://www.cryengine.com/docs/static/attachments/1213742) |![Image](https://www.cryengine.com/docs/static/attachments/1213749) |![Image](https://www.cryengine.com/docs/static/attachments/1213748) --- | --- | --- **Height 1** | ** Height 3** | ** Height 6** |
![Image](https://www.cryengine.com/docs/static/attachments/1213742) | ![Image](https://www.cryengine.com/docs/static/attachments/1213749) | ![Image](https://www.cryengine.com/docs/static/attachments/1213748)
**Height 1** | **Height 3** | **Height 6**
Advanced | Descriptions |
**Fixed Volume** | Will trace a ray down to find a vessel entity and spill the requested amount of water into it. For static entities, it will try to boolean-merge any surrounding static that intersects with the first vessel. Use **No Dynamic Water** flag on brushes that don't need that. |
**Volume Accuracy** | Water level will be calculated until the resulting volume is within this (relative) difference from the target volume. If it's set to 0 it'll run up to a hard coded iteration limit. |
**Extrude Border** | Will extrude the border by the defined distance. It's particularly useful if **wave sim** is on since waves can raise the surface and thus reveal open edges if they lie exactly on the vessel geometry. |
**Convex Border** | Will take convex hull of the border. Mainly useful if the border would otherwise have multiple contours which is not supported in the areas. |
**Object Size Limit** | The Only object that has volume larger than this will take part in water displacement. This is set in fractions of Fixed Volume. |
**Wave Sim Cell** | Size of cell for wave simulation, 0 meaning no waves. Can be enabled regardless of whether Fixed Volume is used or not. |
**Wave Speed** | Sets how fast the water movement looks. |
**Wave Damping** | Standard damping. |
**Wave Timestep** | Might need to be decreased to maintain stability if more aggressive values of speed are used. |
**Min Wave Vel** | Sleep threshold for the simulation. |
**Depth Cells** | Sets how deep the moving layer of water is (in Wave Sim Cell units). Larger values make waves more 'dramatic'. |
**Height Limit** | Sets a hard limit on wave height (in Wave Sim Cell units). |
**Resistance** | Sets how strongly moving objects transfer velocity to the water. |
**Sim Area Growth** | If changing water level is expected to make the area expand, the wave sim grid should take it into account from the beginning. This sets the projected growth in fractions of the original size. If wave sim is not used, this will have no effect. |

When editing a shape or area, it is possible to snap a vertex to terrain or physicalized objects using **Ctrl + Shift + LMB**.

This is true for all Area objects, except Occluders.

Water volumes also have special interpretation of helper types (use a_[suffix] to show helpers for areas only). a_g will draw the outline and the tessellated surface, a_gj will draw the wave sim as a checkerboard-like heightfield, a_l will draw the vessel geometry (a union of all overlapping potential vessels).

### Console Variables

CVar | Description | Values
--- | --- | ---
**r_WaterVolumeCaustics** | Enables or disables caustics for water volumes | 0 - 1 (default depends on system - currently 0 on all except PC high-spec).
**r_WaterVolumeCausticsDensity** | Sets the density of the grid mesh. | 16 - 256 (default is 128 for lower specs, 256 for high specs).
**r_WaterVolumeCausticsMaxDist** | Sets the maximum view distance caustics are visible. | Anything. Default 25.
**r_WaterVolumeCausticsRes** | Sets the resolution of the caustics map/g-buffer. | Texture resolution. Default 1024 for high specs, 512 for low specs.
**r_WaterCausticsSnapFactor** | Sets the snap factor of the caustic render, helps prevent aliasing during motion. | Anything. Default: 0.1.

### Usage Examples

#### Caustics

Caustics are a great way to give the water volumes a much bigger visual presence and involve them more into the scenes that has been created. For more information, please refer to [CRYENGINE V Manual](/docs/static/engines/cryengine-5/categories/23756816).

![Image](https://www.cryengine.com/docs/static/attachments/36849706) | ![Image](https://www.cryengine.com/docs/static/attachments/36849702)
--- | ---
Caustics Off | Caustics On

#### Fog Shadowing

Fog Shadows gives real visual depth to the water volumes, also making optional use of the global Vol Fog Shadows function available in the [Level Settings](../../Level%20Settings.md).

Due to a technical limitation, using **Vol Fog Shadows** will limit the opacity function of the ** Fog Shadowing** param to be either off or full.

![Image](https://www.cryengine.com/docs/static/attachments/36849695) | ![Image](https://www.cryengine.com/docs/static/attachments/36849694)
--- | ---
Vol Fog Shadows Disabled | Vol Fog Shadows Enabled

![Image](https://www.cryengine.com/docs/static/attachments/36849697) | ![Image](https://www.cryengine.com/docs/static/attachments/36849698) | ![Image](https://www.cryengine.com/docs/static/attachments/36849693)
--- | --- | ---
Fog Shadowing 0 | Fog Shadowing 0.25 | Fog Shadowing 0.5

#### Depth

The **Depth** parameter defines both visual and physical depth of the water volume. Things such as the underwater distortion effect is based off the Depth setting.

![Image](https://www.cryengine.com/docs/static/attachments/36849703) | ![Image](https://www.cryengine.com/docs/static/attachments/36849704)
--- | ---
Depth 0 | Depth 10

#### Cap Fog At Volume Depth

With this disabled, the fog settings from the water volume will display infinitely on the Z axis (downwards).

A usage example would be if you had a room that was accessible underneath a water volume, then you would probably activate this setting to prevent the fog from being seen inside the room.

![Image](https://www.cryengine.com/docs/static/attachments/36849703) | ![Image](https://www.cryengine.com/docs/static/attachments/36849705)
--- | ---
Depth 0 / Cap Fog False | Depth 0 / Cap Fog True

#### Height

Although the **Height** parameter is not used for water volumes, it can be useful for visualizing the edges of the volume which would typically be hidden underground.![Image](https://www.cryengine.com/docs/static/attachments/36849692)

#### Speed

Although Speed isn't supported by water volumes (because there's no easy way to define direction on an arbitrarily user-designed shape with infinite results) there's an easy way you can physicalize your water volumes.

[Rivers](../Misc%20Objects/River%20Tool.md)support the Speed parameter and can be placed without any visual representation by simply not applying a material to the object. Layering Rivers on top of your Water volumes (remember to match depths!)

When placing Rivers for this use, make sure to keep them straight (the 'Speed' is applied only for the initial vector and cornering is not supported) and overlap where you want them to change course so they don't get stuck.

![Image](https://www.cryengine.com/docs/static/attachments/36849700) | ![Image](https://www.cryengine.com/docs/static/attachments/36849701) | ![Image](https://www.cryengine.com/docs/static/attachments/36849696)
--- | --- | ---

In the above example, we have three main Rivers (with outside supports to simulate from waterfall) atop the main water volume, carrying several RigidBodyEx entities along for a ride.

[Properties](#properties)[Console Variables](#console-variables)[Usage Examples](#usage-examples)
