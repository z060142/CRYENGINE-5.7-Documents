# Physics Profiling

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/26876703
- Page ID: 26876703
- Breadcrumb: Profiling & Optimization > Profiling Overview > Physics Profiling
- Parent: Profiling Overview

## Content

## Overview

This page will describe the tools we use to investigate what is going on inside the physics system.

### p_draw_helpers 1

Renders the physics proxies on top of the render geometry.

![Image](https://www.cryengine.com/docs/static/attachments/26960124)

Objects are color coded to help display the physics proxies complexity. (Grey -> Red).

Most objects should be grey, but as the geometry gets more complex it's shaded red.

**p_proxy_highlight_threshold** (default 200)

This sets the start at which we think is an appropriate number for polygons for a physics proxy.

**p_proxy_highlight_range** (default 800)

As the polycount gets towards the upper limit (200+800), this where the red shading of the proxies comes from. Between 200 - 1000 your proxy will have different shades of red. Once above 1000, they will be a solid red color.

p_draw_helpers only draws up to a certain distance from the camera. The default is 100m, you can change it with the CVar...

**p_cull_distance**(default 100)

Setting this value to 200 will draw the debug view up to double the default range, or a value of 50 will half the default view distance.

You can also modify the distance at which it draws the wireframe overlay on the proxies. Default = 40m from the camera. If you would like to extend this, you can modify the default value with the CVar...

**p_wireframe_distance** (default 40)

Setting this value to 80 will draw the debug view up to double the default range, or a value of 20 will halve the default view distance.

### Extending p_draw_helpers 1

You can extend this debug mode by combining the following references. Select the type of entity you want to investigate, then the helper type you want to investigate with.

Same as p_draw_helpers_num, but encoded in letters Usage [Entity_Types]_[Helper_Types] - [t|s|r|R|l|i|g|a|y|e]_[g|c|b|l|t(#)]

**Entity Types:** t - show terrain s - show static entities (brushes, vegetation, non-physicalized objects). r - show sleeping rigid bodies R - show active rigid bodies l - show living entities (Players, AI) i - show independent entities (ropes, boids, cloth) g - show triggers a - show areas (gravity volumes, water volumes & wind areas) y - show RayWorldIntersection and PrimitiveWorldIntersection requests e - show explosion occlusion maps

**Helper Types:** g - show geometry c - show contact points b - show bounding boxes l - show tetrahedra lattices for breakable objects j - show structural joints (will force translucency on the main geometry) t(#) - show bounding volume trees up to the level # f(#) - only show geometries with this bit flag set (multiple f's stack)

**Example1**: ** p_draw_helpers y (y -**show RayWorldIntersection and PrimitiveWorldIntersection requests)

This view displays all the ray- and primitive-casts that are currently happening. When investigating RWI/PWI calls you can control how the info is displayed with these CVars.

**p_ray_fadeout**

This controls how long to display the marker for the RayWorldIntersections. Default is 0.2 seconds, but if you want them to hang around for a bit longer onscreen, up the value to 1 - 2 seconds.

**p_ray_peak_time**

This allows you to visually investigate the expense of individual RWI calls. Default value is 0 = (off). When set to default all the lines are blue.

When enabled you get a color code representation of the expense of each call. So red being the most expensive.

![Image](https://www.cryengine.com/docs/static/attachments/26960123)

**Example2**: ** p_draw_helpers r_g** (** r** - show ** sleeping** rigid bodies & ** g** - show geometry)

Pic1, Displays the rigid bodies in their sleep state. (Highlighted in Red)

![Image](https://www.cryengine.com/docs/static/attachments/26960130)

Pic2, Displays the rigid bodies that are still in their sleep state. (Highlighted still in Red). The Green Highlight displays the objects (I just shot) to show them in their active state. This helps differentiate the 2 types of Physics states.

![Image](https://www.cryengine.com/docs/static/attachments/26960127)

**Example3:** ** p_draw_helpers R_g**(** R** - show ** Active** rigid bodies & ** g** - show geometry)

This displays the reverse of the previous example. Where it is only displaying the geometry of the active entities.

![Image](https://www.cryengine.com/docs/static/attachments/26960129)

**Example4: p_draw_helpers r_c (** r**** - show ** sleeping**rigid bodies &** c** - contact points)

This displays via short rays, where the physics objects are coming into contact with other objects.

![Image](https://www.cryengine.com/docs/static/attachments/26960132)

**Example5:** ** p_draw_helpers R_j**(** R** - show ** Active** rigid bodies & ** j** - show joint info)

Upon the breakable object breaking, the joints will be highlighted.

![Image](https://www.cryengine.com/docs/static/attachments/26960128)

**Example6:** ** p_draw_helpers s_b**(** s** - show static objects & ** b** - show bounding box)

All static objects display their bounding box, this includes brushes, vegetation & non-rigidbody physicalized entities.

Note how the AI & HMMWV do not display a bounding box, this is due to not being a static object.

![Image](https://www.cryengine.com/docs/static/attachments/26960125)

**Example7:** ** p_draw_helpers t**(** t** - terrain)

Displays the physics information for the terrain.

![Image](https://www.cryengine.com/docs/static/attachments/26960126)

**Example8:** ** p_draw_helpers e**(** e** - explosion occlusion maps)

Displays information about explosions. Each of the grey markers indicate where the explosion hit the surface.

![Image](https://www.cryengine.com/docs/static/attachments/26960134)

### Combining multiple physics debug view modes at once

Sometimes you may want to visualize multiple entity types, and / or information about them at once. You can combine them together easily by just adding their flag to the p_draw_helpers. Check the following examples.

**Example1: p_draw_helpers a_bg** (** a** - show areas & ** b** bounding boxes + ** g** geometry)

This example show you the physics system related to areas, with bounding boxes + geometry) 1 **Type** with multiple ** Helpers**.

In the picture (from left to right) we have a gravity volume, wind area & a water volume.

![Image](https://www.cryengine.com/docs/static/attachments/26960133)

**Example2: p_draw_helpers ** larRis_g****(show ** g** - geometry for ** l** - living, ** a** - areas, ** r** - sleeping, ** R** - active, ** i** - independent & ** s** - static)

This example is in the other direction, multiple **Types** with 1 ** Helper** (geometry)

![Image](https://www.cryengine.com/docs/static/attachments/26960131)

### p_profile 1

This Mode details information of total entities, Queued Requests & World time step in ms.

![Image](https://www.cryengine.com/docs/static/attachments/26960121)

### p_profile_entities 1

Lists the physics entities active in the level. with their assigned name & EntityID.

Organised top / bottom in time spent (ms). So its easier to find the most expensive at the top.

![Image](https://www.cryengine.com/docs/static/attachments/26960119)

### Combine p_profile 1 & p_profile_entities 1

You can combine these 2 CVars together to which will further break down the entities into their groups. To see what you are spending in ms of each class of entity. With the top 16 being listed in the top left of the screen, you can teleport to each one with the additional cvar...

**p_jump_to_profile_ent N**(N being 1 - 16)

Additionally, the top 5 entities in the list are bound to the shortcut keys **alt+1 -> alt +5**.

![Image](https://www.cryengine.com/docs/static/attachments/26960122)

### p_profile_functions 1

Shows a list of all ray/primitive casts and which dll is requesting them.

![Image](https://www.cryengine.com/docs/static/attachments/26960120)

### p_debug_joints 1

This debug draw shows the mass of objects in kg and the joint linked to the object in 3ds Max.

To display joints you have to activate **p_draw_helpers 1**, or any other combination of the abovep_draw_helpers** type_helper** first.

Upon a jointed breakable breaking, it will give you information on the forces that broke that particular joint. (pull, bend, shift).

![Image](https://www.cryengine.com/docs/static/attachments/26960136)

### Standalone Physics Debugger

The Physics Debugger is a standalone windows executable that's able to load physical world dumps from the Engine and run a separate physics simulation on it. Currently not included in builds by default; the corresponding option has to be manually turned on in CMake when generating the solution.

To enable this feature, make sure that you create dumps of the physical world. A CPhysicalWorld function allows you to do that, and also you can use a cvar ***"p_do_step 2"*** that creates * worldents.txt* and * worldgeoms.txt* files in the root folder of the build. This allows you to load the dumps into PhysDebugger.exe either as startup params or through the main menu. Additionally, the cvar * p_do_step 3* allows you to create a binary dump (world.phump). You can load this binary dump instead of a world text files mentioned above.

![Image](https://www.cryengine.com/docs/static/attachments/26960138)

Several options can be changed in the menu, such as step size (fixed or real time), code and entity profiler display, number of worker threads, additional helper types. Also, when the simulation is running it's possible to possess objects with **Shift+Right** click and use some basic WASD+space movement controls on them (specifically on players and wheeled vehicles). To avoid camera choppiness when moving possessed objects it's possible to enable rendering and physics synchronization (Not recommended for profiling though since it can affect the results).

![Image](https://www.cryengine.com/docs/static/attachments/26960139)

##### CVars

Cvar/Command | Description
--- | ---
**p_do_step 2** | Default backdoor option to make world dumps.
**p_do_step 3** | Enables you to create a single-file binary dump.

[p_draw_helpers 1](#pdrawhelpers-1)[Extending p_draw_helpers 1](#extending-pdrawhelpers-1)[Combining multiple physics debug view modes at once](#combining-multiple-physics-debug-view-modes-at-once)[p_profile 1](#pprofile-1)[p_profile_entities 1](#pprofileentities-1)[Combine p_profile 1 & p_profile_entities 1](#combine-pprofile-1-and-pprofileentities-1)[p_profile_functions 1](#pprofilefunctions-1)[p_debug_joints 1](#pdebugjoints-1)[Standalone Physics Debugger](#standalone-physics-debugger)
