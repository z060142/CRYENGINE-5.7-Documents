# EaaS 3.6.4

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/47316993/pages/44963010
- Page ID: 44963010
- Breadcrumb: Engine Release Notes (Current) > CRYENGINE 3.x > EaaS 3.6 > EaaS 3.6.4
- Parent: EaaS 3.6

## Content

Released July 4th, 2014

### Editor

- **New**: Added a flag to disable dynamic water volumes on selected editor objects.
- **New**: Add an implementation of SHAllocator that uses malloc/free from the Sandbox (that may de #defined as something else).
- **New**: Flowgraph Debug draw nodes: Debug:Draw:Direction, Debug:Draw:Cone, Debug:Draw:Cylinder, Debug:Draw:Line, Debug:Draw:Sphere, Debug:Draw:AABB, Debug:Draw:PlanarDisc, Debug:Draw:EntityTag, Debug:Draw:EntityTagAdvanced.
- **Fixed**: Updating the FlowGraph system one last time right before systems get reset during level unload to ensure that pending requests get executed.
- **Fixed**: #define USE_MEM_ALLOCATOR to fix allocator mismatch between Sandbox and PRT. This could cause a crash during terrain surface generation.
- **Fixed**: Layer dialog doesn't set new layer ([hotfix 2674](http://steamcommunity.com/games/220980/announcements/detail/1531536305658403230)).
- **Fixed**: UI Layout not remembered (CE-3684) ([hotfix 2685](http://steamcommunity.com/games/220980/announcements/detail/1534914552418872868)).
- **Fixed**: Support all possible extensions in File Export dialog (even those not necessarily compatible) (CE-3704).
- **Fixed**: Mark Editor as not DPI-aware in manifest (CE-3729) to prevent crash on non-100% (default) Windows font size ([hotfix 2685](http://steamcommunity.com/games/220980/announcements/detail/1534914552418872868)).
- **Fixed**: Editor ignores DPI Aware flag from Manifest Tool after clean build, force embedding of DPI Aware XML file as well.
- **Fixed**: Vegetation panel: Changed encoding of.bmp that MFC BarTool was unable to load because it only supports indexed bitmaps.
- **Fixed**: Deleting a vehicle from a level which is open in the VE crashes the editor (CE-3446).
- **Fixed**: Allow cancel creation mode while starting terrain tool (CE-2257), otherwise tool would simply not open.
- **Fixed**: Updated Boid scripts to have minimum count of 0 to prevent crash where -1 or less is used (CE-3750). Removed dead params. Added separators for structure clarity.
- **Fixed**: Boid's Activate param didn't work (CE-3801).
- **Fixed**: Infinite loop in code when linking the camera target to the camera.
- **Fixed**: Crash when creating a new level, selecting "Calculate Terrain Sky Accessibility" (CE-3450).
- **Optimized**: Remove deprecated Z and ModelPreview views from Viewport options (CE-328).
- **Optimized**: Removing unsupported Ribbon UI code.
- **Optimized**: Removed obsolete "AffectThisAreaOnly" parameter from Light entities (CE-1650).
- **Optimized**: Moved the Stop All Sounds Button from the InfoBar to the Sound Menu ([hotfix 2674](http://steamcommunity.com/games/220980/announcements/detail/1531536305658403230)).
- **Optimized**: Remove final AVI recorder references.
- **Optimized**: Delete AICheckInBox (use ProxyTrigger), Delete DelayTrigger (use Time:Delay FG node), Delete MultipleTrigger. Removed Bounding Box visuals from AreaTrigger as it serves no purpose.

### Audio

- **New**: Added the basic AudioEnvironment (reverb) handling to the AudioSystem.
- **Fixed**: Reinstated ATL type audio on the particle system for that moved the basic audio proxy into the audio system and optimized handling along some minor code cleanups.
- **Fixed**: Fixed a bug where audio objects didn't release properly also added CVar for setting the audio event pool size, fixed leaking of AudioProxies when not returning them back to the pool, preliminary fix for leaking audio proxies.
- **Fixed**: Fixed leaking audio object IDs and descriptions.
- **Fixed**: Fixed forwarding of AudioObject names to Wwise.
- **Fixed**: Nested area setup bugfix.
- **Fixed**: Changing the game folder broke audio ([hotfix 2685](http://steamcommunity.com/games/220980/announcements/detail/1534914552418872868)).
- **Fixed**: Crash when accessing a dangling AudioSystem pointer on system quit.
- **Fixed**: Crash in AudioProxy where it accessed a dangling AudioSystem pointer.
- **Fixed**: OnFarToNear not triggering on AudioAreaEntity FG node when spawning inside the area ([hotfix 2674](http://steamcommunity.com/games/220980/announcements/detail/1531536305658403230)).
- **Optimized**: Renamed SoundProxy to EntityAudioProxy and enabled it to be able to utilize the AudioProxy.
- **Optimized**: ACB: Updated look and feel of filter bar and the connection properties.

### Engine

- **New**: Ability to detect HMD device (CE-3603).
- **Fixed**: Geom cache decoder was still using an SSE4.1 instruction on PC (crash on older AMD CPUs) ([hotfix 2674](http://steamcommunity.com/games/220980/announcements/detail/1531536305658403230)).
- **Fixed**: Geom cache: Need to stop streaming on Reset, otherwise geom caches with streaming distance = 0 will stream in. Streaming will be started again by frame update logic if distance > 0.
- **Fixed**: Geom cache: Fix deadlock on AbortAndWait (happens when adjusting buffer size while geom caches are still playing).
- **Fixed**: Updated Resource files to improve Visual Studio Express compatibility.
- **Fixed**: Disabled texture streaming from Skybox_highQ to prevent blurry textures (CE-3613).
- **Fixed**: CGA material precaching for independent static objects attached to joints.
- **Fixed**: Fixed CrySystem loadingprofiler.
- **Fixed**: (Physics) UnprojectionNeeded doesn't take radius into account for the z component (CE-3636).
- **Fixed**: (Physics) Crash when issuing ray cast request with invalid physics streamer (CE-3742).
- **Fixed**: (Physics) Some fixes to constraints.
- **Fixed**: (Action) Registering game object event with wrong name (CE-3606).
- **Fixed**: (Action) Moved sv_LoadAllLayersForResList from game side to game framework (CE-3683).
- **Fixed**: (Network) Format sessionid correctly.
- **Fixed**: (Scaleform) Potential crash when playing movie (due to global initializer order issue).
- **Fixed**: Now properly handling of the booleans in the ScriptProperty serialization
- **Optimized**: Move GameToken script bindings to their own file.
- **Optimized**: Rename CGameTokenScriptBind to CScriptBind_GameToken for consistency with all other script bindings.
- **Optimized**: Updated to use DirectX SDK June 2010.
- **Optimized**: Extended interface to allow for more threadlocal operations on the container.

### Rendering

- **Fixed**: Set Glow in Diffuse Alpha shader gen param to hidden as it's not needed. If Diffuse alpha is detected then the mask is automatically applied and due to deferred shading, cannot be un-applied (CE-1526).
- **Fixed**: Wrong threadid usage for recursive spinlock.
- **Fixed**: Fix for display disconnect/reconnect not being handled correctly (CE-3549).
- **Optimized**: Drop dependency on d3dx9 and d3d10.

### CryDesigner

- **New**: Implemented The First Complete Version of The Lathe tool.
- **Fixed**: Made the cursor showing move, rotation or scale updated according to whether the cursor is in the object or gizmo manipulator or not (CE-3443).
- **Fixed**: Added eNotify_OnEndUndoRedo message for better handling of undo/redo operations.
- **Optimized**: Removed the Detach tool. Instead detaching faces can be done by holding shift and moving the faces in the move tool.
- **Optimized**: Separated the exiting stair tool to the stair tool and the StairProfile tool.
- **Optimized**: Improved the method of creating stairs.
- **Optimized**: Changed the key to select multiple edges/vertices/faces from Ctrl to Shift.
- **Optimized**: Removed the LoopCut button.

### Particles

- **New**: Added ParticleParams.fSortBoundsScale to adjust BB used for sorting; 0 => sort by origin (CE-2649).
- **Fixed**: Geometry particles with sub-meshes again emit a random submesh, rather than full mesh, as designed.
- **Fixed**: Water-facing particles on water volumes: fixed pe_status_area query by restoring removed code which tests box containment within area; again returns 1 for containment, -1 for intersection, allowing optimized tests. PhysEnv for static bounds now queries all water volumes. Removed useless ATTACH_BUFFER_DIST offset (CE-3756).
- **Fixed**: Rare crash with attached particles, when GetRandomPos selected empty part at end of list. Empty parts now automatically trimmed, removed TrimParts() function.
- **Optimized**: Refactored SPhysEnviron struct for clarify and efficiency: Renamed some elements, removed unused arguments and code. Combined force and water plane queries into single function. ENV_WATER must now be explicitly passed to query areas; now only included when needed.

### Tools

- **Fixed**: RC ImageCompiler dialog (CryTif) had bad layout when the taskbar is at the top or at a side of the screen (CE-3697).
- **Fixed**: Crash in CrySCompileServer when an empty error message is processed.
- **Fixed**: changed someStr to someStr.c_str() in log output for Max exporter.
- **Optimized**: Move statoscope files to user directory rather than Root directory.

### Animation and Characters

- **New**: Added support for bone links with 16-bit bone indices.
- **Fixed**: Moved vertex index format to typedef so 32-bit vertex indices can be used.
- **Fixed**: Removed hard-coded DivBy4 in ca_AttachmentCullingRation (instead we added the correct value in the config-file). This affects character view distance.
- **Fixed**: Only activate the render mesh and chunks for character mesh after the bone remapping has happened on the main thread.
- **Fixed**: Speculative fix for broken pre-caching CHR's without attachments.
- **Fixed**: Recursive getChildren() in script crashes 3ds max when object/bone hierarchy is > ~250 bones deep. Fixed by making getChildren() non-recursive.

### Assets

- **New**: Cleaned up Forest TOD and added 7am and 12am times to show basic night time and sunrise setup. Probe switch logic WIP.
- **New**: Re-baked MH60 Blackhawk normals at 2x resolution. Tweaked material/textures.
- **Fixed**: Numerous asset updates throughout sample asset library. Most buildings and Misc props have been updated for PBS in basic form. Other props WIP.
- **Fixed**: Several assets missing LODs and other small issues fixed.
