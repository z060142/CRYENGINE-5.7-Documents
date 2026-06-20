# Debugging and Profiling Tools

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/36868666
- Page ID: 36868666
- Breadcrumb: Profiling & Optimization > Profiling Overview > Debugging and Profiling Tools
- Parent: Profiling Overview

## Child Pages

- [DisplayInfo Icons](Debugging%20and%20Profiling%20Tools/DisplayInfo%20Icons.md)

## Content

## Overview

CRYENGINE has various built-in debugging and profiling tools that help to locate and fix problems as well as performance issues. This article outlines some of the most widely used tools.

### Basic Logging Functionality

**log_IncludeTime** ``` Toggles time stamping of log entries. Usage: log_IncludeTime [0/1/2/3/4/5] 0=off (default) 1=current time 2=relative time 3=current+relative time 4=absolute time in seconds since this mode was started 5=current time+server time ```

### Basic Asset Information

#### Error Report Window

The Error Report window displays error messages created by missing objects and broken assets. The console can also be accessed under **Tools → Check Level for Errors**.

**SaveLevelStats** ``` Calling this command creates multiple XML files with level statistics. The data includes file usage, dependencies, size in more/disk. The files can be loaded in Excel. ```

Stats for your level are saved within the level folder, with further information saved in the `GameSDK/TestResults` folder.

### System

#### MemInfo

Displays current memory info. Useful for finding memory leaks.

![Image](https://www.cryengine.com/docs/static/attachments/36848276)

**MemInfo** ``` Display memory information by modules 1=on, 0=off ```

#### MemStats

Displays detailed information of each function currently being called, sorted by size. This view contains a lot of detailed information, although on some occasions the data may be slightly distorted.

![Image](https://www.cryengine.com/docs/static/attachments/36848272)

**MemStats** ``` 0/x=refresh rate in milliseconds Use 1000 to switch on and 0 to switch off Usage: MemStats [0..] ```

#### Profile

The profile console command contains various ways to access timing and memory consumption information within CRYENGINE. To access a list of profiling views, please use the **profile** command line.

Command | Description | Image
--- | --- | ---
**Profile 1** | **Self Value -** Displays the number of executions per frame. Total value minus the totals of any subsections, e.g., if Function A takes 5ms in total to execute, but calls Function B(), which takes 2ms to execute, then the self time of Function A() would be 3ms. You can use the ** Scroll Lock** key to pause or continue the profiling recording and the ** Up** and ** Down** Arrow keys to navigate through the rows. | ![Image](https://www.cryengine.com/docs/static/attachments/44960387)
**Profile 2** | **Total Value -** Displays the total duration/allocations from start to finish. You can use the ** Scroll Lock** key to pause or continue the profiling recording and the ** Up** and ** Down** Arrow keys to navigate through the rows. | ![Image](https://www.cryengine.com/docs/static/attachments/44960388)
**Profile 3** | **Counts -** The number of executions per frame. You can use the ** Scroll Lock** key to pause or continue the profiling recording and the ** Up** and ** Down** Arrow keys to navigate through the rows. | ![Image](https://www.cryengine.com/docs/static/attachments/44960389)
**Profile 4** | **Peaks -** Shows sections for which the self value in the last frame exceeded the average value by the margin specified in the CVar** profile_peak_tolerance.** | ![Image](https://www.cryengine.com/docs/static/attachments/44960443)
**Profile 5** | **Subsystem Info -** Shows the sum of self times and the corresponding percentage of the frame time per system. More than 100% is possible, as times are summed over all threads. | ![Image](https://www.cryengine.com/docs/static/attachments/44960390)
**Profile 6** | **Thread Info -** Shows the time each thread spends in active (working) and waiting sections and the corresponding percentages of the frame time. | ![Image](https://www.cryengine.com/docs/static/attachments/44960444)
**Profile 7** | **Minimal View -** This only shows the header. | ![Image](https://www.cryengine.com/docs/static/attachments/44960445)

##### Profile_smooth

This adjusts the "smoothing" of the numbers shown in the profile displays. Increasing this value will result in less erratic movement in the values shown.

**profile_smooth** ``` Profiler exponential smoothing interval (seconds) ```

##### Profile_peak

This sets the lower limit for values shown in the latest peaks column. The lower the value is, the more the peaks are shown.

**profile_peak** ``` Profiler Peaks Tolerance in Milliseconds ```

#### sys_enable_budgetmonitoring

Displays memory budgeting information for your level, for video, frametime, sound channels, sound memory and draw calls. Individual budgets can be set up externally, using console commands beginning with **sys_budget_** (type it in to the console and press tab for a list). When a bar reaches the far right, the associated text will flash as a warning that you are over budget. As the text shown states, please test this in pure game mode, as the editor version of the game can give false results.

![Image](https://www.cryengine.com/docs/static/attachments/36848275)

**sys_enable_budgetmonitoring** ``` Enables budget monitoring. Use #System.SetBudget(sysMemLimitInMB, videoMemLimitInMB, frameTimeLimitInMS, soundChannelsPlaying) or sys_budget_sysmem, sys_budget_videomem or sys_budget_fps to set budget limits. ```

#### profile_allthreads

**profile_allthreads** ``` Enables profiling of non-main threads. ```

### 3D Engine

#### e_DebugLights

Debug draw mode visualizing the number of dynamic lights affecting a piece of static geometry. This is important as the more lights affect an object, the more often it needs to be rendered, e.g. to generate shadow maps, perform lighting (when using non-deferred lights), etc. Using this information, you would ideally place your lights in a way to get the biggest bang for the buck. That means, use only as few lights as possible to realize a certain lighting condition or mood. This debug draw mode can help to detect surfaces which are affected by more lights. It also enables designers to easily check why some of the lights may flicker on certain surfaces.

It uses different colors for objects affected by different numbers of lights.

- **black:** 0
- **blue:** 1
- **green:** 2
- **red:** 3 or more
- **blinking yellow:** more than the maximum enabled

**e_DebugLights** ``` Use different colors for objects affected by different number of lights black:0, blue:1, green:2, red:3 or more, blinking yellow: more then the maximum enabled ```

#### e_Lods

e_Lods controls the use of LOD, or Level Of Detail objects in your level. If you suspect geometry might be causing issues, simply turn off the use of LOD objects (the low detail versions of objects, which have less polygons) by typing in e_lods 0.

All objects will now use their highest detail LOD version.

In the picture below with e_lods turned off, the high detail object shows. With e_lods turned on, the appropriately calculated lower detail LOD shows:

![Image](https://www.cryengine.com/docs/static/attachments/36848271)

**e_Lods** ``` Load and use LOD models for static geometry ```

##### e_LodMin

**e_LodMin** ``` Min LOD for objects ```

##### e_LodMax

**e_LodMax** ``` Max LOD for objects ```

#### sys_ProfileLevelLoading

**sys_ProfileLevelLoading** ``` Output level loading stats into log 0 = Off 1 = Output basic info about loading time per function 2 = Output full statistics including loading time and memory allocations with call stack info ```

### Renderer

#### r_DisplayInfo

Displays various important information for debugging, such as camera position and angle, build number and name of level loaded.

![Image](https://www.cryengine.com/docs/static/attachments/36848273)

**r_DisplayInfo** DUMPTODISK, RESTRICTEDMODE ``` Toggles debugging information display. Usage: r_DisplayInfo [0=off/1=show/2=enhanced] ```

#### r_MeasureOverdraw

This option activates a special rendering mode that visualizes the rendering cost per pixel, by color. As you may notice, this command shows the accumulated instruction count per pixel, not just the overdraw.

**r_MeasureOverdraw** ``` Activate a special rendering mode that visualize the rendering cost of each pixel by color. 0=off, 1=pixel shader instructions, 2=pass count, 3=vertex shader instructions, 4=overdraw estimation with 360 Hi-Z, Usage: r_MeasureOverdraw [0/1/2/3/4] ```

![Image](https://www.cryengine.com/docs/static/attachments/36848265)![Image](https://www.cryengine.com/docs/static/attachments/36848262)

#### r_DebugLights

**r_DebugLights** ``` Display dynamic lights for debugging. Usage: r_DebugLights [0/1/2/3] Default is 0 (off). Set to 1 to display centers of light sources, or set to 2 to display light centers and attenuation spheres, 3 to get light properties to the screen ```

#### r_ShowMT

**r_ShowMT** ``` Shows render multithreading graphs. Usage: r_ShowMT [0/1] Default is 0 (off). ```

#### r_DebugRefraction

**r_DebugRefraction** ``` Debug refraction usage. Displays red instead of refraction Usage: r_DebugRefraction Default is 0 (off) ```

#### r_PostProcessEffects

This CVar makes it possible to completely disable post-processing effects to find out if they cause a specific problem. It is also possible to display the currently active post-processing effects.

**r_PostProcessEffects** ``` Enables post processing special effects. Usage: r_PostProcessEffects [0/1/2] Default is 1 (enabled). 2 enables and displays active effects ```

#### r_TexelsPerMeter

**r_TexelsPerMeter** ``` Enables visualization of the color coded "texels per meter" ratio for objects in view. The checkerboard pattern displayed represents the mapping of the assigned diffuse texture onto the object's uv space. One block in the pattern represents 8x8 texels. Usage: r_TexelsPerMeter [n] (where n is the desired number of texels per meter; 0 = off) ```

#### r_ProfileShaders

This option displays the profiling information for the currently rendered shaders.

**r_ProfileShaders** ``` Enables display of render profiling information. Usage: r_ProfileShaders [0/1] Default is 0 (off). Set to 1 to display profiling of rendered shaders. ```

#### r_TexLog

This option dumps texture information to a text file in the root of the game folder.

**r_TexLog** ``` Configures texture information logging. Usage: r_TexLog # where # represents: 0: Texture logging off 1: Texture information logged to screen 2: All loaded textures logged to 'UsedTextures.txt' 3: Missing textures logged to 'MissingTextures.txt ```

### Physics

#### p_draw_helpers

P_draw_helpers is a command which allows access to various view mode for the physics of the objects in your level.

![Image](https://www.cryengine.com/docs/static/attachments/36848268)

**p_draw_helpers** ``` Same as p_draw_helpers_num, but encoded in letters Usage [Entity_Types]_[Helper_Types] - [t|s|r|R|l|i|g|a|y|e]_[g|c|b|l|t(#)] Entity Types: t - show terrain s - show static entities r - show sleeping rigid bodies R - show active rigid bodies l - show living entities i - show independent entities g - show triggers a - show areas y - show rays in RayWorldIntersection e - show explosion occlusion maps Helper Types g - show geometry c - show contact points b - show bounding boxes l - show tetrahedra lattices for breakable objects j - show structural joints (will force translucency on the main geometry) t(#) - show bounding volume trees up to the level # f(#) - only show geometries with this bit flag set (multiple f's stack) Example: p_draw_helpers larRis_g - show geometry for static, sleeping, active, independent entities and areas ```

#### p_debug_joints

When p_draw_helpers is enabled, this CVar will show any tension on physicalized joints within a breakable object.

![Image](https://www.cryengine.com/docs/static/attachments/36848270)

**p_debug_joints** ``` If set, breakable objects will log tensions at the weakest spots ```

#### p_profile_entities

![Image](https://www.cryengine.com/docs/static/attachments/36848269)

**p_profile_entities** ``` Enables per-entity time step profiling ```

#### p_profile_functions

![Image](https://www.cryengine.com/docs/static/attachments/36848266)

**p_profile_functions** ``` Enables detailed profiling of physical environment-sampling functions ```

### AI

#### ai_DebugDraw

When set, shows any AI debugging information currently active in your level.

![Image](https://www.cryengine.com/docs/static/attachments/36848274)

**ai_DebugDraw** ``` Toggles the AI debugging view. Usage: ai_DebugDraw [-1/0/1] Default is 0 (minimal), value -1 will draw nothing, value 1 displays AI rays and targets and enables the view for other AI debugging tools. ```

##### Supported CVar Values

ai_DebugDraw | Description
--- | ---
-1 | Only warnings/errors and Interest System debug draw
0 | No AI debug draw
1 | Basic AI debug draw
71 | Draw all forbidden areas (including auto-generated ones)
72 | Draw graph errors (problematic areas are highlighted with circles)
74 | Draw the whole navigation graph (can be very slow)
79 | Draw the navigation graph close to the player (within 15 m from the camera; quicker than 74)
80 | Draw tagged nodes (during A*)
81 | Calculate (if necessary) then draw 3D (volume) hidespots
82 | Draw 3D (volume) hidespots
85 | Draw steep slopes (determined by ai_steep_slope_up_value and ai_steep_slope_across_value)
90 | Draw flight navigation within 200-m range of the player
179 | Same as 79 but also showing triangulation edges' centers
279 | Same as 179 but also showing water depth information
1017 | Visualize navigation links of node which encloses entity "test"

Setting **ai_DebugDraw** to one will enable the visualization of following variables:

#### ai_DrawStats

**ai_DrawStats** ``` Toggles drawing stats (in a table on top left of screen) for AI objects within specified range. Will display attention target, goal pipe and current goal. ```

#### ai_StatsTarget

**ai_StatsTarget** ``` Focus debugging information on a specific AI Display current goal pipe, current goal, subpipes and agentstats information for the selected AI agent. Long green line will represent the AI forward direction (game forward). Long red/blue (if AI firing on/off) line will represent the AI view direction. Usage: ai_StatsTarget AIName Default is 'none'. AIName is the name of the AI on which to focus. ```

#### ai_DebugTacticalPoints

Logs tactical point activity from the statsTarget and displays associated debug drawing.

**ai_DebugTacticalPoints** DUMPTODISK ``` Display debugging information on tactical point selection system ```

#### ai_AllTime

**ai_AllTime** ``` Displays the update times of all agents, in milliseconds. Usage: ai_AllTime [0/1] Default is 0 (off). Times all agents and displays the time used updating each of them. The name is colour coded to represent the update time. Green: less than 1 ms (ok) White: 1 ms to 5 ms Red: more than 5 ms You must enable ai_DebugDraw before you can use this tool. ```

#### ai_DrawBadAnchors

**ai_DrawBadAnchors** ``` Toggles drawing out of bounds AI objects of particular type for debugging AI. Valid only for 3D navigation. Draws red spheres at positions of anchors which are located out of navigation volumes. Those anchors have to be moved. 0 - off, 1 - on ```

#### ai_DrawFormations

**ai_DrawFormations** ``` Draws all the currently active formations of the AI agents. Usage: ai_DrawFormations [0/1] Default is 0 (off). Set to 1 to draw the AI formations. ```

#### ai_DrawModifiers

**ai_DrawModifiers** ``` Toggles the AI debugging view of navigation modifiers. ```

#### ai_DrawNode

**ai_DrawNode** ``` Toggles visibility of named agent's position on AI triangulation. See also: ai_DrawNodeLinkType and ai_DrawNodeLinkCutoff Usage: ai_DrawNode [ai agent's name] none - switch off all - to display nodes of all the AI agents player - to display player's node AI agent's name - to display node of particular agent ```

#### ai_DrawNodeLinkType

**ai_DrawNodeLinkType** ``` Sets the link parameter to draw with ai_DrawNode. Values are: 0 - pass radius (default) 1 - exposure 2 - water max depth 3 - water min depth ```

#### ai_DrawNodeLinkCutoff

**ai_DrawNodeLinkCutoff** ``` Sets the link cutoff value in ai_DrawNodeLinkType. If the link value is more than ai_DrawNodeLinkCutoff the number gets displayed in green, otherwise red. ```

#### ai_DrawOffset

**ai_DrawOffset** ``` vertical offset during debug drawing (graph nodes, navigation paths,...) ```

#### ai_DrawPath

**ai_DrawPath** ``` Draws the generated paths of the AI agents. ai_drawoffset is used. Usage: ai_DrawPath [name] none - off (default) squad - squadmates enemy - all the enemies ```

#### ai_DrawRefPoints

**ai_DrawRefPoints** ``` Toggles reference points and beacon view for debugging AI. Usage: ai_DrawRefPoints "all", agent name, group id Default is the empty string (off). Indicates the AI reference points by drawing balls at their positions. ```

#### ai_DrawTargets

**ai_DrawTargets** ``` Distance to display the perception events of all enabled puppets. Displays target type and priority ```

#### ai_DrawType

**ai_DrawType** ``` Display all AI object of specified type. If object is enabled it will be displayed. with blue ball, otherwise with red ball. Yellow line will represent forward direction of the object. <0 - off 0 - display all the dummy objects >0 - type of AI objects to display ```

#### ai_Locate

**ai_Locate** ``` Indicates position and some base states of specified objects. It will pinpoint position of the agents; it's name; it's attention target; draw red cone if the agent is allowed to fire; draw purple cone if agent is pressing trigger. none - off squad - squadmates enemy - all the enemies groupID - members of specified group ```

#### ai_ProfileGoals

**ai_ProfileGoals** ``` Toggles timing of AI goal execution. Usage: ai_ProfileGoals [0/1] Default is 0 (off). Records the time used for each AI goal (like approach, run or pathfind) to execute. The longest execution time is displayed on screen. Used with ai_DebugDraw enabled. ```

#### ai_SteepSlopeAcrossValue

**ai_SteepSlopeAcrossValue** ``` Indicates slope value that is borderline-walkable across. Usage: ai_SteepSlopeAcrossValue 0.8 Default is 0.6 Zero means flat. Infinity means vertical. Set it greater than ai_SteepSlopeUpValue ```

#### ai_SteepSlopeUpValue

**ai_SteepSlopeUpValue** ``` Indicates slope value that is borderline-walkable up. Usage: ai_SteepSlopeUpValue 0.5 Default is 1.0 Zero means flat. Infinity means vertical. Set it smaller than ai_SteepSlopeAcrossValue ```

#### ai_DrawRadar

Draws a radar overlay at the center of the view. 'ai_DrawRadar 0' disabled the radar and any other number is interpreted as the size of the radar in pixels. That is 'ai_drawradar 500' draws 500px high radar in the middle of the screen. The circles in the radar are drawn in 5m intervals.

Distance of the radar can be set using ai_DrawRadarDist console variable. The distance is specified in meters. A good combination to start with is 500px high radar with view distance of 50m. The radar displays each unit, including the name of the unit, the alertness state and the current path and readability.

![Image](https://www.cryengine.com/docs/static/attachments/36848301)

**ai_DrawRadar** ``` Draws AI radar: 0=no radar, >0 = size of the radar on screen ```

#### ai_DrawRadarDist

**ai_DrawRadarDist** ``` AI radar draw distance in meters, default=20m. ```

#### ai_DrawTrajectory

**ai_DrawTrajectory** ``` Record and draw the actual path taken by the agent specified in ai_StatsTarget. Path is displayed in aqua, and only a certain length will be displayed, after which old path gradually disappears as new path is drawn. 0=do not record, 1=record. ```

#### ai_StatsDisplayMode

Gives information on the number of active AIs, full updates and TPS queries that happen every frame.

**ai_StatsDisplayMode** ``` Select display mode for the AI stats manager Usage: 0 - Hidden, 1 - Show ```

### Entity System

#### es_ProfileEntities

**es_profileentities** ``` Usage: es_profileentities 1,2,3 Default is 0 (off). ```

#### es_DebugTimers

**es_DebugTimers** ``` This is for profiling and debugging (for game coders and level designer) By enabling this you get a lot of console printouts that show all entities that receive OnTimer events - it's good to minimize the call count. Certain entities might require this feature and using less active entities can often be defined by the level designer. Usage: es_DebugTimers 0/1 ```

[Basic Logging Functionality](#basic-logging-functionality)[Basic Asset Information](#basic-asset-information)[System](#system)[3D Engine](#3d-engine)[Renderer](#renderer)[Physics](#physics)[AI](#ai)[Entity System](#entity-system)
