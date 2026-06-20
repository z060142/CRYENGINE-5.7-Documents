# FreeSDK 3.5.5

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/47316993/pages/44963032
- Page ID: 44963032
- Breadcrumb: Engine Release Notes (Current) > CRYENGINE 3.x > FreeSDK Archive > FreeSDK 3.5.5
- Parent: FreeSDK Archive

## Content

Version not released

### Important Info

Merged Meshes changes
All levels using Merged Meshes need to be re-exported before opening in Launcher due to a change in code.

Level Creation changes
Please note that it is no longer possible to create levels larger than 4 x 4km (16km²). This only effects level creation though and support for existing larger heightmaps remains. New features and official support for larger levels will be coming in the future through a new system called "Segmented Worlds" which we'll be talking about more in the future.

AI System changes
The AI system has undergone numerous cleanups, fixes and refactorings. Legacy AI navigation (pre-MNM) has now been fully deprecated. This is a necessary step in better supporting the main [Multi-layer Navigation](/docs/static/engines/cryengine-3/categories/1114113/pages/1048672) system with more fixes, features and optimizations to come!

### Fixed

- NumSides for Solid Tool limited to 128. Higher values are unstable and can cause crashes (CE-263).
- Fixed error with unregistered goalop query "DefendAreaCover".
- Fixed log-spam when loading CHR without animations.
- (Flowgraph) Crash when deleting a module.
- (LODGenerator) Assert and crash on close.
- Enabled game so it forwards player health to the music logic.
- (Game) Crash if projectiles use rigid body physics and the entity pool system.
- (MergedMesh) Increased chunk version and moved it into a define (NEEDS A REEXPORT OF ALL LEVELS USING MERGED MESHES!).
- Fixed it so if navmesh is generated with a blocking call it'll still generate islands. (Needed to be set to the working state to trigger that, and that normally happens when we exit out).
- Cleanup of ModelJoint.h.
- Making rc.ini in bin32 equal (by content) to rc.ini in bin64.
- Fixed crash bug where a particle system could have an invalid octree pointer and crash at level unload.
- Fixes if a light is too close to an object all 6 shadow frustums are not aligned correctly (CE-1282).
- Fixes data race condition between asynchronous octree update jobs and the main thread causing a crash in FindPotentialLightSources on unoptimized builds (CE-1605).
- TRACKVIEW: Crash on play simple TV sequence (CE-1477).
- CRASH: When player lands from a height (CE-1478).
- Fpe in character sim.
- Fpe in character rope sim.
- Fpe in rope sim.
- SDK_Advanced_Grunt.xml: root no longer bails out when the TPS fails (CE-1601).
- (Game) Recording System assert/warning.
- (CryDesigner) Fixed a few small bugs related to drawing lines and triangulations etc.
- Fixed Collapse/Expand all options not functioning in Time of Day Editor (CE-390).
- Fix so non-fixed size text is centered and aligned correctly.
- Sound browser - buttons disconnect off the interface (CE-1529).
- Character cloth sync issue.
- Registering AI objects on a dedicated server will cause the server to crash.
- Fixed crash and scheduling bugs rendering particles in Character Editor. Update and render now done synchronously.
- Particle static bounds computation now considers bEmitOffsetDir.
- CPickObjectButton crashing editor when clicked on new Object - Fixes a crash when creating a new object in the viewport, while at the same time trying to click buttons ("Pick Object" button for example) in the object's properties panel (CE-1261).
- Refs to static objects in particles weren't being released, causing leak warnings at shutdown.
- Sandbox crash when toolbar shortcut button is used (CE-1681).
- Sandbox: Error dialog. Made Editor usable while errors are spamming (CE-57).
- (Network) Network Stall Ticker thread name not correctly set.
- (Flowgraph) New module default folder is not relative to game folder when using pak files (CE-1771).
- (Game) Interactor not resetting interactor entityid if interaction type is none.
- EntityToScreenPos flownode holds onto a cleaned up entity pointer (CE-1410).
- (Flowgraph) Only clear modules if level was really loaded before. Editor sends unload event in the beginning.
- Rope solver friction fix.
- Restored particle fill rate limiting (e_ParticlesMaxScreenFill).
- Sandbox: Terrain Layer Textures: Load.dds file if there is no.tif (CE-229).
- Added explosivegrenade to entityscheduler.
- "Check level for errors" is usable even if "ed_showErrorDialog" is set to 0 (CE-1161).
- Crash in editor when attaching skin with broken 0-ptr-material.
- When painting vegetation the brush radius is not displayed on the terrain (CE-1225).
- Proper bbox awakening on articulated parts update (CE-1573).
- (Flowgraph) Red/Blue channel inverted on color settings (CE-1471).
- If a material was waiting to be deleted and something requested it, it could get a pointer that would be deleted a few frames later. This fix ensures that they'll get a new copy of the material instead.
- Actor dying in a vehicle causes crash (CE-1350).
- Fixed it so if distance scaled icons are on, the pick size for the icon is scaled too.
- (Shader) Crash when starting the Launcher (CE-1746).
- Wrong character joint rotation in char rope/cloth sim.
- (Scaleform) Crash on exit - GFxState.
- (PerfHud) Crash when enabling stats_rendersummary.
- 3DHUD is gone / crashes after sv_restart (CE-1371).
- (GameStream) Updated game stream to solve wrong file management type.
- Sandbox: Fix Fetch for Heightmap (keep vegetation) (CE-260).
- (3DEngine) Crash while checking if segment is safe to use.
- (FlowGraph) Level modules don't load.
- Turret: OnPrePhysicsUpdate isn't being called (CE-1769).
- (Shader) Lightbeam fixes for volumetric lighting support.
- Fixed textures being marked "native" even though they are not.
- Sandbox: Add ReplaceMe icon for terrain layer texture preview if there is no texture (CE-216).
- (FlashUI) Shutdown before shared flash player resources.
- PREFAB: "Extract All" does not work as intended. Clicking on "Extract All" in the Prefab Panel, objects have to be cloned outside the prefab, leaving it intact, which was not the case. This fix solves the above problem (CE-1439).
- PREFAB: "Remove object" does not function as intended (CE-1432).
- Improved rendering of Facing=Water particles, by forcing them to draw before water.
- Fixed particle above/below water rendering and clipping: Render emitters intersecting water in 2 passes, before and after.
- Fixed particle vis area clipping: Use actual camera vis area, rather than delayed "global" vis area.
- Now clip particles against water and vis area boundaries with alpha fade, not size, and efficiently in culling pass. Clip geometry particles as well.
- Script error with SpawnPoint.lua (CE-1536).
- SAdvancedInfo is constructed every frame instead of copying one from the current level (CE-1755).
- SDK_Basic_Grunt behavior tree: wasn't setting its alertness.
- Fixed buffer overfllow in audio command player (CE-262).
- Fixed broken music logic control flowgraph node where presets did not get listed and adding of input values did not work, enabled music logic to receive data from default events, fixed wrong error message popup upon saving empty music logic presets.
- Crash when loading a second level in the dedicated server (CE-1538).
- TOD: Entering Play Speed then closing TOD resets it to 0 (CE-1528).
- TOD: Cannot simulate a slow sunset (CE-962).
- Database - Prefabs - menus options need re-wording to reflect the function it does (CE-1481).
- Fixes to ropes tied to end 1.
- (Game) OnLevelEnd callback never called.
- (Flowgraph) Check if module already exists before creating a new one.
- Fixed terrain modify tool not working when blocked by overlapping brushes (CE-1416).
- More character cloth fixes.
- (IComponent) Crash after killing AIs.
- Autobackup overwrites the original files when crashing or exiting from the Editor and reloading the level (CE-1616).
- (PlayerState) Animation controlled cutscene.
- Fixed muzzle-flash delay.
- Changed category from Log to Debug for CSVDumper node.
- DisableHUD trackview setting does not work (CE-1450).
- SDK_Advanced_Grunt.xml didn't set its Alertness state (CE-1658).
- (GameDLL) Some configs used default base address instead of GameDll.
- Vehicle Editor: new vehicle cannot be set up - save as 'MyVehicle.xml' does not function (CE-1516).
- Force opaque rendering in wireframe mode for particles (CE-1580).
- Fixed a bug about that it didn't work about a light with a clipping bound whose shadow config is less than config spec (CE-1, CE-961, CE-1324).
- Fixed a bug that caused the Multiplayer lobbies to hang.
- Fixed a error causing the minimap to not load, removed the in-level menu feature (for now) and re-added multiplayer, added a standard background image instead, and re-disabled the loading image.
- Fixed music not playing on start.
- (HitDeathReactions) Don't use StealthKill by default in MP.
- Fixing hit and reaction file for multiplayer (to avoid asserts due to not existing or wrong hit types).
- (Mannequin) Don't use procedural clip "Ragdoll" in MP.
- Added default ML events and fixed naming of existing ones.
- (Audio) Audio preloads for multiplayer.
- (SmartObject) Null rotation.
- Updated blood_bullet_hit flowgraph, referencing non-existent CVar, added missing blood textures.
- Holes needed to be closed for the trunk (breakable trunk feature).
- Fixing minor issues with the navigation.
- Helicopter: wouldn't move anymore.

### Deleted

- Removed deprecated Camera:CameraYPR flownode.
- PrismObject: Hide entity. Not intended to be used in game world.
- Removed deprecated BoundingContainer entity from GameSDK (CE-1781).
- Deprecate Fog entity (not FogVolume), no longer supported.
- Caf files are not supported by the build process anymore: solution re-export with.i_caf and.animsettings file format.
- Lod1.chrs are not supported anymore.
- Not needed anymore. The generic_male is mismatching with the player skeleton. Therefore we only need the player skeleton.
- Delete light_flare materials. Deprecated for Lens Flare system.
- Removed unused music.
- Deprecated View:Shake node as View:ShakeEx does everything and more.

### Optimization

- Small cloth collision stability improvement.
- Allow cloth animation to change attachment points.
- Particle shadows now work without tessellation, with per vertex test. Added texture binding calls to vertex stages, and fixed erroneous sampler state caching due to CTexture.m_bVertexTexture usage.
- GenericAStarSolver optimization: GetPath() methods now reserve memory beforehand.
- Merged particle culling and rendering job stages into single jobs. Optimized culling pass, no longer compute full vertex information except for occlusion culling. Alpha and culling status saved in local array and reused. No longer write cull status to Particle, allowing const iteration in both passes.
- Removed, simplified, combined, and optimized many obsolete and inefficient particle structs and functions, nuking 1000 lines of code. Management of CREParticles simplified from 3 redundant lists into 1. Greatly simplified SRenderVerticesToVMEMAdapter, SRenderVertices. Moved ComputeVertices job management into Renderer. Nuked SParticleCullInfos, IAllocRender, CParticleQueue, many APIs.
- Shrunk particle sorting struct to just sort by distance; complex sorting for merging no longer needed.
- Merged particle rendering functions in main and recursive passes into one, with tests for job dispatch where needed. Moved misc remaining particle functions from Renderer.cpp to CREParticle.cpp.
- Removed unneeded camera pointer from CREParticle.
- Jobsystem updates.
- Thread layout improved.
- Fixed timing of particle stat gathering, and incorporated into emitter update loop for efficiency.

### Refactored

- Interface cleanup: removed redundant GetJointNameByID() and GetJointIDByCRC32() from ISkeletonPose.
- Interface cleanup: removed redundant GetJointCount()-functions in differentn interface-classes which all access CModelSkeleton.
- Code related to macro INCLUDE_AI_LEGACY_CODE removed (INCLUDE_AI_LEGACY_CODE was #defined as 0).
- AIConsoleVars::TargetTracking default value changed from 2 to 1 (value of 2 was related to INCLUDE_AI_LEGACY_CODE).
- Old nav-mesh related code removed (MNM is the one and only to use from now on).
- AI_NAVIGATION_USE_MNM macro removed.
- Some now empty methods that contained only the old nav-mesh code removed.
- Remove artificial radius limitation on explosion physics (CE-1126).
- Restricted map size creation to 4k x 4k (CE-1054). Larger heightmap levels from previous engine versions can still be loaded. Support for larger levels coming in the future.
- Added new MusicLogic setup. Implemented initial FG in Forest. Tidied up FG layouts.
- Numerous optimizations and cleanups to skeleton and model code.
- Consolidated many lines of duplicated code in SRenderingPassInfo constructors.
- Moved ParticleBatchDataManager to ParticleManager files, where it belonged. Made it base class of ParticleManager, for simplicity.
- VehicleLights: Added HDRDynamic, animSpeed, animPhase and falloff params. Removed deprecated light params. Abrams: Adjusted all lights, offset 3p camera more to the rear, disabled brake on idle, decreased accel/decel, increased topspeed, inertia and tilt. Blackhawk: Adjusted all lights, refactored damage params, removed unneeded id tags. Speedboat: Adjusted all lights, refactored damage params, removed unneeded id tags. Added enter actions/components.
- Refactoring and cleanup for all the material flownodes.
- Cleaned out substitutions script of old nodes which are either fixed in code or removed. Grouped some sections together where applicable.
- Updated the Muzzleflash for the scar. Now bound to emitter (end of barrel) to fix the lag / delay on the pfx. Also added a child that spawns a light. (small radius 2m) Added tessellation to the gun_smoke_tp / fp variations. & swapped to per stream with a tile of 1. barrel cool down smoke effect looks a lot cleaner. A lot of optimization gone into the pfx.

### Tweak

- RigidBodyLight: Removed deprecated features (rotation, corona, posteffect, fill light), fixed ambient not working. Added param descriptions and synched params closer to standard light entity.
- FogVolume: Added property descriptions and capped values.
- (Flowgraph) Port color readability.
- AIConsoleVariables: proper help text of ai_TargetTracking.
- Scripts: Updated several scripts to support particle effect selection, removed deprecated features (decal, holes), tweaked structures.
- Renamed ParticleLife parameter curve to ParticleAge.
- Temporarily disabled Missing Asset Resolver in Editor.cfg.
- Enabled LOD Generator for FreeSDK.
- Fixed it so the arithmetic compression stream writes bools as a zero or a one, instead of whatever a bool happens to cast to.
- EntityUtils: Set Invulnerable to 0 for MakeKillable function. Tidied structure, fixed typos.
- Set deprecated Camera:Camera flownode to obsolete (CE-1661). Moved HUD flowgraph nodes to correct folder structure (CE-63).
- Children of expanded controls now properly indent to multiple levels. Indentation now matches expand icon width.
- Tidied BasicActor and Player.lua scripts. Repathed sound files.
- Extended flowgraph logic nodes to 10 outputs each (CE-1617).
- Added a function to HashGrid to query an AABB.
- Added function to the random number generators to get a random number in a range.
- Added a few handy functions to the flags class.
- DestroyableLight: Added description text for several params, synched up params closer to standard light entity.
- Texture streaming pool size.
- Defaulted distance scaling to off (old behavior).
- Make obsolete flownode category accessible to non-debug builds.
- Abrams: Tidied structure, removed unnecessary id= shortcuts, increased size of enter components, added Actions section for enter components, removed modification section.
- Added GetMasterVolume() and simplified the sound muting process in the editor (set MasterVolume to zero instead of turning off music- and sound system) (CE-1613).
- (Flowgraph) Removed dead module code for renaming.
- Game Token Flow nodes - increase port count to 10 (CE-1748).
- Logic:Any - increase the input port count to 10 (CE-1747).
- Added extra vehicle light setups from 3.4.
- Rain Entity: Added mouse-over description text for parameters.
- DestroyableLight: Updated script to support particle effect selection, removed deprecated features (rotation, corona, posteffect, fill light), fixed ambient not working.
- SDK_Advanced_Grunt.xml behavior tree: using a common "Hostile" state now.
- MH60: Decreased acceleration rates, increased damage hitpoints. Speedboat: Fixed damage types, increased damage hitpoints, aligned content closer to C3 setup.
- LightEntity: Fixed typo in parameter description.
- PlayerTeamVisualization.xml: Added short description on file purpose.
- Audio: Mute override for SoundBrowser (CE-1632).
- Updated PlayerTeamVisualization script with SDK content. Friendly players will wear blue jackets, enemy players will wear red jackets.
- Added UseDistance parameter to elevator switch script. Removed "sz" part of UseMessage param.
- Blackhawk: Added decal material fade out so decals on rotor do not appear static.
- Prepared music logic update for SDK. Working on new music logic for SDK.
- Forest: Added material glow to shrine candle during night. Added supporting light triggered off night time FG (CE-673).
- Converted files to 48k 16bit.
- Added campfire PFX. Allowed PushableByPlayers for Marine lobster cage archetype.
- Set flashlight toggle key back to "L".
- Capped holes for the trunk of b_beech_a.cgf (CE-198).
- Lowered texture size and changed spec value for jacket.
- Grass_4 texture used for the grass mtl in Forest.
- Fixed position of the holster node and added half cone simulation.
- Updated PlayerTeamVisualization script with SDK content. Friendly players will wear blue jackets, enemy players will wear red jackets.

### New Feature

- Added an option to scale icons in the Sandbox based on distance from the camera (so they will get smaller when you zoom out).
- MoveOp: formation: leader can now be much further away than the implicit 20 meters before followers give up (CE-1637).
- Exporting the AI in Sandbox was causing broken MNM.bai files (and thus broken Level.pak files).
- ForbiddenArea.lua: was no longer receiving events, thus eventually not dealing damage to the player (CE-1640).
- Introduced music logic events node than enables designers to feed events to the music logic via FlowGraph.
- ParticleParam substructures now serialized with field names, allowing order-independence and backward compatibility. Added e_ParticlesSerializeNamedFields to toggle new serialization format. Tweaked spline element field names.
- Sandbox: Fix Fetch func. To fix update terrain units after Terrain Resizing. To fix operation like terrain modifying and making holes (CE-1534).
- Particle decals now support texture tiling options (CE-1487).
- Added SRenderingPassInfo.IsAuxWindow() flag, to detect rendering in editor preview windows.
- Added 6am and 6pm preset times in TOD toolbar (CE-346).
- New sample Behavior Tree added that can deal with with "CombatMove" assignment.
- Flowgraph - Debugger step through port activations with F6 - Debug menu to disable flowgraph and flowgraph type debugging.
- Made rope entity colltypes fully customizable.
- Bird boid: now supports an additional animation for when about to land on the ground (CE-1736 / CE-1798).
- (FlowGraph) Unit Tests for flowgraph debugger.
- Display of edited (non-default values in editor now enabled by UI_HIGHLIGHT_EDITED flag.
- Better polygon physarea debug rendering with p_draw_helpers a_gc
- Frame profiler: profile_allthreads = 1 now combines multiple job stats into 1; profile_allthreads = 2 displays them separately as before.
- Optimized the update and draw functions of attachments by rearrangement of inner loops, removal of virtual functions and fine-tuning of rejection tests.
- Use rope slicing when shooting ropes.
- Added "Online Documentation..." menu item to open documentation website from Sandbox help menu.
- Support for colltype flags in surfacetypes.
- CryDesigner/Bevel, Boolean: Added the Bevel Tool, Boolean Tool.
- Added a button for Flood Layer painter to terrain painting tool.
- Added some generic metal texture/material assets.
- Animsettings and i_caf for hmmwv animations.
- Added several example Smart Objects scripts.
- Bspace_tutorial assets.
- Added some additional sample LightBeam materials for use with LightBeam shader.
- Added spec texture for thin_leave_tree asset.
- Added spec texture for jungle_thin_tree asset.
- Adjusting music logic data files to new music logic.
- Major Overhaul of the GameSDK Scaleform UI/Menu. Matches new CRYENGINE design, as well as a major overhaul of the AS2 code (everything has been put into more managable classes / some extra features added).
