# Vis Area

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/36869910
- Page ID: 36869910
- Breadcrumb: Editor Tools > Level Editor Tab > Create Object > Area > Vis Area
- Parent: Area

## Content

## Overview

The Vis Area is a shape object which is used to define indoor areas for culling and optimization purposes, as well as lighting.

Objects inside a Vis Area won't be rendered from outside and vice versa, this can help with performance immensely.

Vis Areas also can be setup to occlude certain lighting elements, such as the Sun, which gives flexibility in setting up lighting for the indoor areas. Note that since CRYENGINE 3.6, AmbientColor is no longer supported and Environment Probes should be used instead.

Vis Areas can have any number of corners; just double-click when the last one has been added.

### Vis Area Properties

**Property** | **Description**
--- | ---
**Height** | Specifies how high the Vis Area is.
**Display Filled** | Just for visibility in the editor this option defines if the area should be rendered as filled or not.
**Affected By Sun** | Specifies if shadows from the world outside the Vis Area can travel inside.
**Ignore Sky Color** | If this option is turned off the ambient color (sky color in time of day window) is not used indoors.
**Ignore GI** | If true, Global Illumination won't be used inside this object.
**View Dist Ratio** | Specifies how far the Vis Area is rendered.
**Sky Only** | Lets users choose to see only the skybox when you look outside the Vis Area. If the terrain and outside brushes are not rendered, the performance can be improved. Use this option when it is appropriate.
**Ocean Is Visible** | Specifies if the ocean rendering should be visible inside the Vis Area.
**Ignore Outdoor AO** | Ignores the outdoor Ambient Occlusion.

When editing a shape or area, it is possible to snap a vertex to terrain or physicalized objects using **Ctrl + Shift + LMB**.

This is true for all Area objects, except Occluders.

### Setting Up a Vis Area

- Place the Vis Area shape around the room.
- Set the height.
- Be sure everything related is inside the Vis Area.
- Try to stay on the grid by enabling "Snap To Grid".
- Keep the shape of the Vis Area as simple as possible.

![Image](https://www.cryengine.com/docs/static/attachments/36849691)

### Transitioning from Indoor to Outdoor Areas

- If the player leaves the Vis Area (indoor), everything behind the player will disappear, including the walls that are located inside.
- A wall inside the Vis Area and a wall outside the Vis Area are needed.

![Image](https://www.cryengine.com/docs/static/attachments/36849690)

- Transitions from indoor to indoor are handled the same way; two walls are needed, one in room 1 and one in room 2.
- Also for better lighting separate Vis Areas should be added to each room.

![Image](https://www.cryengine.com/docs/static/attachments/36849687)

[Vis Area Properties](#vis-area-properties)[Setting Up a Vis Area](#setting-up-a-vis-area)[Transitioning from Indoor to Outdoor Areas](#transitioning-from-indoor-to-outdoor-areas)
