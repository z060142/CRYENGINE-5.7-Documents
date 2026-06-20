# EaaS 3.6.5

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/47316993/pages/44963011
- Page ID: 44963011
- Breadcrumb: Engine Release Notes (Current) > CRYENGINE 3.x > EaaS 3.6 > EaaS 3.6.5
- Parent: EaaS 3.6

## Content

Released August 7th, 2014

### Sandbox Editor

- **New**: FBX Import Dialog (View -> Open View Pane -> FBX Import). Preview version with lots more features to come!
- **New**: Send mousewheel event in Editor.
- **New**: Character editor shows tris count and drawcalls.
- **New**: Revived "KillOnTrigger" function to "RemoveOnTrigger" for ProximityTrigger to remove entities (except player) on entering the proxy trigger.
- **New**: (LODGen) Added LOD Generator option "Add to parent material" (CE-3670, CE-3913)
- **New**: (Mannequin) Added a simple new "MannequinObject" GameObject entity. This allows mannequin testing without a complete Player/AI character.
- **New**: Added ability to project deferred decals further than '1'. Will now project up to '10' times further (CE-1576).
- **Fixed**: Editor fails to start using Chinese (simplified) system language (CE-3309).
- **Fixed**: Crash in save level stats.
- **Fixed**: AI Navigation Area "DisplayFilled" property didn't work (CE-3696).
- **Fixed**: Debug visual toolbar was causing warning popups due to type mismatch on cvar "ai_drawPath" (CE-3621).
- **Fixed**: (LODGen) Produced invalid material files during multi-material conversion.
- **Fixed**: (LODGen) Crash when closing LOD generator dialog in rare circumstances.
- **Fixed**: Adding more than 2 reference pictures in a level crashes the editor (CE-3890).
- **Fixed**: Graph Tokens dialog shows/selects wrong tokens (CE-3879).
- **Fixed**: Crash when adding entity link.
- **Fixed**: Bug where grouped objects would move to near (0, 0, 0) if entering game mode or loading level.
- **Fixed**: Undo crash due to invalid parent material pointer (CE-3811).
- **Fixed**: Issue where a TIF file in the an Engine (sub)folder resulted in a DDS in the Game (sub)folder (CE-3862).
- **Fixed**: (Vegetation) Can have more than 256 different vegetation objects in VegetationMap.dat (CE-3914).
- **Fixed**: Counting of vertices, lods, etc in static mesh preview of the file open dialogs.
- **Fixed**: (Vertex Snapping) Made a pivot of the group or prefab of the selected object move instead of moving the object as an another vertex is picked (CE-3908).
- **Fixed**: Non-threadsafe code fixed (CE-3845).
- **Fixed**: Problems with transform delegate and bone attached attached objects. Attachment bug fixes.
- **Fixed**: Uninitiated m_bAttach in CUndoAttachBaseObject.
- **Fixed**: Some asserts, crashes and STL runtime errors.
- **Fixed**: (SplineObject) Prevent spline hit test crash from out of bounds access. Fixed hit-test code.
- **Fixed**: Uninitialized variable in CAxisHelper::Prepare causing missing axes in transform gizmos.
- **Fixed**: (Mannequin) Various crash fixes with the Mannequin nodes when using incorrect data.
- **Fixed**: (Mannequin) Crash in PlayMannequinFragment node when using empty entity field.
- **Optimized**: (Vegetation) Optimize Undo for Removing vegetation instances (CE-3870).
- **Optimized**: Completely replaced old bone link attachment system.
- **Optimized**: Disable temporal effects when resizing window.
- **Optimized**: Removed obsolete "AmbientColor" parameter from VisAreas and Portals.
- **Optimized**: Made parsing of lua comments for property tooltips more robust (CE-4032).
- **Optimized**: Improved error message about multiple objects sharing the same location (CE-3544).
- **Optimized**: Object Layers: Clean up saving code.
- **Optimized**: Removed deprecated XT Toolkit defines.

### CryDesigner

- **New**: Implemented the [Smoothing Group](/docs/static/engines/cryengine-3/categories/1114113/pages/17829070) tool.
- **New**: Implemented the [RemoveDoubles](/docs/static/engines/cryengine-3/categories/1114113/pages/17829615) Tool.
- **New**: Implemented the [HideFace](/docs/static/engines/cryengine-3/categories/1114113/pages/17829524) Tool.
- **New**: Added switch sides of a selected region in the magnet tool.
- **New**: Made it possible to create rectangle and Disc separately.
- **New**: Added an undo for selection of vertices, edges and faces.
- **New**: Added a new way of moving the selected vertices, edges and faces on a viewport by moving a mouse holding LMB.
- **New**: Added a function to insert edges connecting between the selected face and the inset face holding CTRL in the Offset Tool.
- **Fixed**: Top face can be glued to the face touching the top face in the Stair Tool.
- **Fixed**: Reset xform caused by wrong calculation of a transformed plane of a region.
- **Fixed**: Offset tool on creating an unexpected non-closed region after scaling and the boundary check.
- **Fixed**: Number of selected objects doesn't display in status bar (CE-3674).
- **Fixed**: Dimension helper updated realtime while moving vertices or edges or faces with the move tool (CE-3240).
- **Fixed**: Crash after deleting edges and selecting them. Fixed a bug on not selecting a edge in a open region (CE-3886).
- **Fixed**: Rare bug which may occur when slicing a face in the SortVerticesAlongCrossLine() method.
- **Fixed**: Moved the dialog box of the Slice tool up.
- **Fixed**: Fill tool creating an incorrect face as filling a space between two edges.
- **Fixed**: Remaining an unexpected region after finishing extruding a region to the opposite side in the Extrude Tool.
- **Fixed**: Bugs of the Extrude, Bevel, HideFace, Move, RemoveDoubles and Stair Profile tools in the Mirror Mode.
- **Optimized**: Changed a few settings for the Exclusive mode so that an object in the new rendering context of 3.6 is rendered well.
- **Optimized**: Put the Border selection tool into the Loop selection tool and removed the Border Selection tool.
- **Optimized**: Changed the status text displayed as elements (vertices, edges or faces) are selected so that the message will be clearer.
- **Optimized**: Refactored the Move tool code.
- **Optimized**: Changed the layout of the menu buttons in the Designer Panel.
- **Optimized**: Moved the check boxes of DisplayDimensionHeler and DisplayTriangulation to the Preference panel.

### Trackview

- **Fixed**: Switching to other director not updating camera correctly.
- **Fixed**: Track gizmos of inactive nodes being shown.
- **Fixed**: Always change track when moving camera through view.
- **Fixed**: Wrong type check in CTrackViewNodesCtrl::AddGroupNodeAddItems (prevented adding same node to multiple directors).
- **Fixed**: Issue with TrackView and entering/exiting game mode.
- **Fixed**: Trackview event nodes warning about node already exists (CE-3548).
- **Fixed**: Update curve editor time range when sequence settings changed (CE-3693).
- **Fixed**: CryMovie post effects not disabled when active camera is not sequence camera
- **Optimized**: Set time warp track default value to 1.0f on creation (CE-3461).
- **Optimized**: Remove remaining preroll code.
- **Optimized**: Remove broken CViewport::IsActive && CViewManager::GetActiveViewport.

### Flow Graph

- **New**: (Action) Added "PlayerProfile" nodes to interact with user stats.
- **New**: Split Input:Mouse node up into smaller nodes for performance reasons and made some improvements and fixes.
- **New**: Added FlowSystem containers and nodes to manipulate them.
- **New**: (Mannequin) EnslaveCharacter node can now define a custom ScopeContext.
- **Fixed**: Load level archetypes in the Flownode drop-down list.
- **Fixed**: Unable to cancel flowgraph module (CE-3969).
- **Fixed**: (AISystem) AISequence:Animation FlowGraph node had mismatching values for the "Stance" property.
- **Fixed**: FlowGraph Modules can't be started multiple times.
- **Fixed**: Custom module ports use inconsistent names (CE-3967).
- **Fixed**: Don't operate on invalid nodes.
- **Fixed**: Modules are allowed to override their node factory.
- **Fixed**: Only Update/Cancel a module if a valid module instance id is provided

### Particles

- **New**: ParticleParams.eGeometryPieces is now has 3 options: Whole, RandomPiece, AllPieces.
- **New**: Added options for particle collision: die/ignore/stop. Finally renamed Bounciness to Elasticity.
- **Fixed**: Unified render positioning for sprites, decals, and geometry – all now obey Aspect and Pivot params (CE-3777). Fixed PivotY to work in positive text direction. Static bounding box computation properly accounts for Aspect and Pivot.
- **Fixed**: Correctly position sub-geometry pieces when bNoOffset=1.
- **Fixed**: Geometry centering, when used as emit geom for attached particles. Centralized centering behavior in SEmitGeom. Fixed minor bug in GetRandomPos with sub-meshes.
- **Fixed**: Broken particle physicalization (CE-3984).
- **Fixed**: Crash when particle video memory buffer count exceeded (CE-4056, CE-4079).

### Audio

- **New**: Switched to PostingRequests for all external communications with the AudioSystem.
- **New**: (ACB) Create controls by dragging directly from the middleware panel.
- **Fixed**: (ACB) Ignore Init.bnk file as a preload.
- **Fixed**: (ACB) Folders are added as child when using the context menu.
- **Fixed**: Comparison of invalidated iterators in CSoundSystem::ProcessLoopedSounds().
- **Fixed**: Comparisons of invalidated iterators in CMusicSystem::Update().
- **Fixed**: Nested area setup bugfix.
- **Fixed**: Minor code cleanup.
- **Fixed**: Removed GetVolatilePreloadRequestNames() from the interface.
- **Fixed**: Switched to using a blocking request for drawing debug info.
- **Fixed**: Switched to PostingRequests for all external communications with the AudioSystem.
- **Fixed**: Fixed AudioDebug null ptr to AuxGeomRenderer crash; fixed stalling the main thread from DrawAudioDebugData().
- **Fixed**: Double deletion issue of audio listeners.
- **Fixed**: Removed implementation of private copy ctor of CAudioListenerManager.
- **Fixed**: Now actually removing audio listeners upon a remove request.
- **Fixed**: Deadlock when internally pushing audio requests.
- **Fixed**: ATL now allows scoped enums only if possible.
- **Fixed**: AudioProxy null pointer crash when using NULLAudioSystem.
- **Fixed**: AudioProxy does not listen to audio events therefore not setting the request owner anymore.
- **Fixed**: Only push audio debug draw requests when the DrawAudioDebug CVar is set.
- **Optimized**: (ACB) Integrated all the audio controls under one panel.

### Tools

- **Fixed**: Distorted matrices were written by collada exporter because Matrix44::Invert() produced weird results (depending on FP mode used in code generation) (CE-3763).
- **Fixed**: Several updates to Documentation tools, tidied script output, added new Scriptbind classes.

### Engine

- **New**: (Steam) Enable Steam by default.
- **New**: (Steam) Save to steam cloud when USE_STEAM is defined
- **New**: (Steam) CVar net_useSteamAsOnlineLobby to determine to initialize Steam or not.
- **New**: (Physics) Optional runge-kutta integrator for more precise rigidbody rotation.
- **New**: (GeomCache) Added geom cache attachments.
- **Fixed**: (Steam) Remove read/write limits.
- **Fixed**: (Steam) Delay load Steam DLL to unhook the dependency at launch.
- **Fixed**: (Steam) Userstat callback was on wrong thread.
- **Fixed**: (EntitySystem) Fixed changing the contents of a container while iterating on it in CSoundProxy::OnHide()
- **Fixed**: (EntitySystem) Need to force entity xform on unhide to update physics proxy location.
- **Fixed**: (Common) CAttachmentSKIN::SoftwareSkinningDQ_VS_Emulator() was changing the global render flags but not restoring them (CE-3373)
- **Fixed**: (Common) Fix uninitialized value in frame profile system causing crash in STL sort.
- **Fixed**: (3DEngine) Object manager streaming nullptr checks.
- **Fixed**: (3DEngine) Added additional info to e_DebugLights CVar helper text to note that it is obsolete and to use r_DeferredShadingDebug instead (CE-2921).
- **Fixed**: (Network) Use correct address for parsing session id during connection.
- **Fixed**: (Network) Fix broken session handle parsing (CE-3911).
- **Fixed**: (Physics) Fixed memory deallocation bugs in physical world functions.
- **Fixed**: (Physics) Awake entities constrained to livings.
- **Fixed**: (System) Pak signature check always shows warning about unsupported signing.
- **Fixed**: (Action) One frame of animation lag.
- **Fixed**: (GeomCache) Fix compilation errors when!defined(USE_GEOM_CACHES). Fixed assets.
- **Fixed**: (GeomCache) Crash in CObjManager::PrecacheStatObjMaterial.
- **Fixed**: (Mannequin) CreateFragmentID shouldn't assign bits for fragmentid tag definitions (CE-3592).
- **Fixed**: (Game) CryAction relies on 'sv_pacifist' CVar in GameDLL (CE-3855).
- **Fixed**: (Game) Level archetypes were not working in launcher.
- **Fixed**: (Game) Presale scripts loading undefined behavior.
- **Fixed**: (Game) Modinfo fixed string size assert.
- **Fixed**: (Game) GameSerialization: fixed the BasicEntity count in the SaveGame file.
- **Fixed**: (Game) Player can get stuck in slide state (CE-3977).
- **Fixed**: (Game) Pistol: Fixed ammo accessory setups and added information into scripts. Reference new CGF assets for Standard/Incendiary ammo clips. Define ammo count through weapon script rather than Equipment pack to move inline with C3 approach. 27 bullets for standard ammo and 18 bullets (9 with weapon, 9 with accessory) for Incendiary ammo. Added NoAttachmentX and Ironsight accessories to be used as defaults as per C3 approach (if you remove a Scope attachment, you reassign the Ironsight attachment, etc). Removed GameMode specific tags for accessories. Set Incendiary ammo to Bullet class rather than Rocket as it was behaving erratically against AI. Incendiary effect now applied through ammo script rather than MFX system for simplicity.
- **Fixed**: (Game) EntityUtils.lua: entity.Server:OnHit() wasn't considering the case where the collision partner is not an entity but terrain or something else, which caused a warning by AI.GetReactionOf() (CE-2953).
- **Fixed**: (Game) Flashlight not working properly, creating static volFog spheres after save/load (CE-3174).
- **Fixed**: (AISystem) FactionMap should never be destroyed (CE-3959).
- **Fixed**: (AISystem) SDK_Grunt TPS queries are now using "grid" instead of "pointsInNavigationMesh" when generating points to be more reliable.
- **Fixed**: (AISystem) Formations: converted formations using the deprecated AddFormationPointFixed() function to use AddFormationPoint() now (CE-4117).
- **Fixed**: (AISystem) Behavior tree SDK_Grunt_06 now shoots at the target during long TPS queries (CE-4055).
- **Fixed**: Added CRenderAuxGeomRenderFlagsRestore to automatically restore previous render flags.
- **Fixed**: Timer returned wrong time scaling.
- **Optimized**: (AISystem) CSmartPathFollower now clamps the look-ahead position on the path segments (CE-3877)
- **Optimized**: (Physics) Reduce phys area change event callbacks by specifying phys area media.
- **Optimized**: (Physics) Updated warning message "Shootable object has material (%s) with invalid surface type" to "Physicalized object has material (%s) with invalid surface type" as this error doesn't only affect bullet impacts.
- **Optimized**: (GeomCache) Don't allocate memory for colors if no colors are used.
- **Optimized**: (Action) Updated i_giveammo CVar description text for clarification on usage (CE-4038).
- **Optimized**: (Game) Added information to PickableAmmo entity (and hid from Editor as it's not usable with base code) (CE-1475).

### Render

- **Fixed**: Vegetation sprites rendering not thread safe (CE-3938).
- **Fixed**: Make Post Effect Params thread safe.
- **Fixed**: r_UseZPass = 1 causes blurry artifacts (CE-3815).
- **Fixed**: Calculate correct RowPitch for Texture::Map() return value.
- **Fixed**: CopyResource accounts for cubemap side subresources.
- **Fixed**: Motion blur nor dealing properly with time scaling.
- **Optimized**: Dedicated server allocating memory in NULL renderer (CE-3691). Disabled a few more code paths for NULL renderer (regarding texture loading).
- **Optimized**: Load global cache to memory when using preactivate 3, speeds up engine init.

### Assets

- **New**: Added Radar threat level in HUD (CE-3521).
- **Fixed**: (Audio) Changed Preload Request xml layout and parsing to accommodate the related ACB functionality
- **Fixed**: (Scripts) Updated equipment pack to include PickAndThrowWeapon needed for Pickable objects.
- **Fixed**: Improved UV layout of Tunnel asset. Recreated LOD1.
- **Fixed**: Removed faces inside windows on Storage hall asset. Fixed materialID assignment on LOD.
- **Optimized**: Pistol: Refactored accessory setup, removed unnecessary incendiary MFX/PFX setup (brought down to 1 effect called in ammo script). Removed Flashlight and Incendiary ammo by default (will obtain in Forest level instead). Lowered ammo counts to make picking up ammo more useful. Added 'incendiary' version of pistol magazine and added new material subID to reference different texture for visual difference between ammo types. Also added 1p and optimized 3p versions. Tweaked DDNA glossmap. Added "Mission_Forest" equipment pack which will be called via level FG to showcase per-level equipment packs. Set Pistol to default weapon for default equipment pack and configured default/initial attachments.
- **Optimized**: Bad LODs in Chimney assets.
- **Optimized**: Added missing Rock textures for Erosion assets. Updated erosion material and textures.
- **Optimized**: Updated drain material and textures. Recreated broken LODs.
- **Optimized**: Updated concrete pillar material.
- **Optimized**: Re-exported Jungle Tree assets, now using shared material setup, simplified filename, removed unused submat IDs.
- **Optimized**: Updated ceiling assets material and textures.
- **Optimized**: Removed unnecessary LODs from Window Frame assets. Added missing proxies. Updated concrete material version.
- **Optimized**: Updated electrical box materials and textures.
- **Optimized**: Added LODs for small_plane assets, fixed some erroneous faces on plane_a. Deleting DDNs.
- **Optimized**: Updated more Industrial props assets materials and textures.
- **Optimized**: Tweaked fishing houses assets materials and textures.
- **Optimized**: Updated Chenyan truck material and textures.
- **Optimized**: Electric Pole: Exported additional mesh versions. Separated and fixed proxies and material assignment. Adjusted textures and material. Added missing DDNA textures.
- **Optimized**: Natural assets updates. Deleted unused textures. Tweaked textures and materials.
- **Optimized**: Delete external water tank LODs, updated material.
- **Optimized**: Updated Blood, Footsteps, Glass, Ice, Metal, Paint, Snow, Water, Wood decal materials and textures.
- **Optimized**: Updated card_reader material and textures.
- **Optimized**: Fishing houses tweaks, fixed issues with several assets and missing tex paths.
- **Optimized**: Updated factory_door material and textures. Moved door frame Max content into Door Max file so pivots can be setup easily. Deleted unnecessary frame LODs. Reset scene materials.
- **Optimized**: Updated cooling tower, shrunk it to usable size, added DDNA, updated materials.
- **Optimized**: Barbwire fence: recreated LODs, tweaked material and textures.
- **Optimized**: Added LODs for stone_barrier assets. Deleted unrelated rock assets. Added DDNA, removed DDN. Updated materials and textures.
- **Optimized**: Added LOD to storage_hall_destroyed asset.
- **Optimized**: Added LOD for Binoculars TP asset. Tweaked material.
- **Optimized**: Updated dirt, concrete and rock decal material and textures.
- **Optimized**: Updated watertower_stone materials and textures. Added DDNAs, deleted DDNs. Added LODs for interior pieces.
- **Optimized**: Updated Sawmill asset material and textures. Created additional LOD1 and LOD2. Updated proxy.
- **Optimized**: Updated Chimney asset, added DDNA and Spec, updated material.
- **Optimized**: Updated trainyard assets.
- **Optimized**: Various Industrial props updates
- **Optimized**: Updated aspen tree material and textures.
- **Optimized**: Overhaul of Radiator max file. Relinked LODs. Updated material. Added DDNA and new DIFF texture.
- **Optimized**: Updated Generator assets materials and textures.
- **Optimized**: Updated lift assets materials and textures.
- **Optimized**: Airfield assets update. Various material tweaks, texture updates. Deleted DDN's with DDNA's.
- **Optimized**: Updated Chinese lantern material, added DDNA deleted DDNs, updated ceiling metal materials.
- **Optimized**: Updated various vegetation materials and textures. Deleted unused DDNs.
- **Optimized**: Tweaked distance trees material and texture, renamed _diff.
- **Optimized**: Updated bed material and textures
- **Optimized**: Increased edge count on soda can assets to make them look less boxy.
- **Optimized**: Changed Forest time from 11:30 to 09:45.
- **Optimized**: Removed bad vertex painting on sb wooden bridge asset. Added another LOD for broken mesh. Updated material and textures.
- **Optimized**: Updated track cart and pipe asset materials and textures
- **Optimized**: Updated handgear, industrial lamp, lightswitch and panels material and textures.
- **Optimized**: Set DefaultSolids, material_layers_default and material_terrain_default materials to use mat_concrete surface type. Unified material settings across all default materials, including only using textures from Engine folder.
- **Optimized**: Updated generic concrete and metal materials and textures.
- **Optimized**: Updated junk, palette and walkway material and textures.
- **Optimized**: Updated vending machine material and textures.
- **Optimized**: Updated old gas pump material and textures.
