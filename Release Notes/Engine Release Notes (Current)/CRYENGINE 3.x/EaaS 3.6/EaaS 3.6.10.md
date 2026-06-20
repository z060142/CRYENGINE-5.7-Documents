# EaaS 3.6.10

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/47316993/pages/44963016
- Page ID: 44963016
- Breadcrumb: Engine Release Notes (Current) > CRYENGINE 3.x > EaaS 3.6 > EaaS 3.6.10
- Parent: EaaS 3.6

## Content

Released 31st October, 2014

Remember to delete 'loose' SDK content if you've extracted pak files into your build! Otherwise that old loose content will override the new content inside the pak files.

See: [Directory Structure - PakFiles](/docs/static/engines/cryengine-3/categories/1638401/pages/1605746#DirectoryStructure-PakFiles) and [CryPak - Layering](/docs/static/engines/cryengine-3/categories/1638401/pages/1605659#CryPak-Layering)

An issue with texture streaming on objects with custom materials (manually assigned materials to objects) is present in 3.6.10. A workaround is to disable texture streaming via **r_TexturesStreaming=0** in your system.cfg.

### Editor

- **Fixed**: (ACE) Using "show in explorer" for an animation directs to the wrong path (CE-3269).
- **Fixed**: (CharEditor) 'Auto Populate Events' dialog to better display long bone names (CE-1154).
- **Fixed**: (Mannequin) Fixed ActionController holding some dangling CharInstance pointers upon reset. (CE-4618).
- **Fixed**: (Mannequin) Fixed Mannequin editor clearing its scope contexts.
- **Fixed**: (Mannequin) Fixed character not animating in the Mannequin transition editor.
- **Fixed**: (Mannequin) Option mismatch in fragment previewer (CE-4309).
- **Fixed**: (Mannequin) Playback problem in previews (CE-4772).
- **Fixed**: (Mannequin) Enable diagnosing of invalid entity error, fatal in launcher, warning in editor.
- **Fixed**: (Flowgraph) Scrolling with middle-mouse button while dragging a graph-edge no longer leaves behind a frozen edge (CE-4609).
- **Fixed**: (Flowgraph) Don't show void port types for new flowgraph modules.
- **Fixed**: (Vegetation) Deleting Procedural vegetation remains visible (CE-3595).
- **Fixed**: (Vegetation) Procedural Vegetation being assigned to wrong layers in Launcher (CE-3794).
- **Fixed**: Editor crashes when reloading a level with Highlight Missing Surface Type/Breakable Materials enabled (CE-4635).
- **Fixed**: Error window no longer corrupted when moving around (CE-4706).
- **Fixed**: Object layer manager memory trampling.
- **Fixed**: Terrain Editor brush indicator disappearing when 'Sync Radius for all Types' is enabled. Fixed negative radiuses when using shift+mmb drag (CE-4664).
- **Fixed**: Undoing "Pick and Attach" on prefabs results in the object becoming unselectable (CE-4678).
- **Fixed**: Possible crash in CDecalObject::UpdateEngineNode() (CE-4636).
- **Fixed**: (Prefab) Modifying Light params when inside open prefab (CE-4711).
- **Optimized**: (Vegetation) Remove deprecated "Grow on Voxels" param (CE-2705).

### Engine

- **New**: Added streaming support for VCloth.
- **New**: (Statoscope) Custom display scaling (CE-4605).
- **New**: (Statoscope) Append datagroups to the filename (CE-2112).
- **New**: Introduced e_MergedMeshesOutdoorOnly CVar to force ERF_OUTDOORONLY on automerged vegetation patches. Fixed Group mismatch ID on addgroup (CE-4681 / 4666).
- **New**: Change to splitted texture format, for Editor compatibility (.dds.0 is now.dds).
- **Fixed**: (Stream Engine) Environment:SkyboxSwitch node crashes (CE-1497).
- **Fixed**: (Particles) Much more accurate calculation of Maintain Density, using emitter bounding volumes and particle trajectory distance, and incorporating current wind (CE-4549).
- **Fixed**: (Particles) Stretch geometry fixed.
- **Fixed**: (Particles) Misc param fixes: Curve editing refresh; false assert; particle out-of-bounds debug color active only when bounds cvar set. Collision params for particle and surface are only combined when SurfaceType is set.
- **Fixed**: (GeomCache) Crash with e_geomCacheDebugDrawMode == 3 because of non thread safe aux rendering from render job. Fix is to move debug rendering to main thread.
- **Fixed**: (GeomCache) Hard code mass and density to -1 for geom caches to prevent them from being catapulted away by other active physics proxies near them.
- **Fixed**: (MayaCryExport2) Handling Y-up scenes with static geometry properly.
- **Fixed**: (MaxCryExporter) Project layout in Visual Studio's solution explorer: Skin17 folder (filter) was missing.
- **Fixed**: (System) BinaryXmlNode not handling 64bit values correctly.
- **Fixed**: (System) Return false if module loading fails.
- **Fixed**: (Cloth) Refcounting and statistics for VCLoth.
- **Fixed**: (Cloth) Removed optimization that disabled streaming in levels for VCloth.
- **Fixed**: (Cloth) Removed tangent updates from vertex animation in case of VCloth.
- **Fixed**: (Cloth) Update bone remapping tables for streaming with VCloth.
- **Fixed**: (Cloth) Removed CryFatalError on binding sim mesh for VCloth.
- **Fixed**: (Cloth) Removed normal computations on loading VCloth.
- **Fixed**: (Cloth) Pool of cloth pieces that was limited to 32 because the slots were stored in an int.
- **Fixed**: Activate textures for -1 and +1 for LODs to prevent streaming problems with LOD switches and different materials per LOD.
- **Fixed**: Invalid assertion (CE-3813).
- **Fixed**: Proxies of vegetation remain drawn when vegetation is hidden (CE-2569).
- **Fixed**: Mini-map & changing display size properties don't update (CE-4307).
- **Fixed**: Disable tree breaking in editing mode to prevent crash (CE-3454).
- **Fixed**: Adjusted data types for map ordering in ATLEntities_wwise.h.
- **Optimized**: (Cloth) Removed CClothManager and moved the buffer caching inside CharacterManager.
- **Optimized**: (Cloth) Moved render- and sim-mesh for vertexcloth into the same class. Skin-attachments are not needed any more.
- **Optimized**: (Cloth) Moved the initialization of the VCloth on DrawAttachment for now.
- **Optimized**: (Cloth) Encapsulated CAttachmentVCLOTH from the rest of the system.
- **Optimized**: (MaxCryExport) Deleted BuildNo.cpp to simplify the project.
- **Optimized**: (RC Animations) Now warning about missing joint is not displayed if controller is Locator_Locomotion (CE-4727).
- **Optimized**: (RC) Merged RC's and CryEngine's CGFSaver.* to avoid code duplication (CE-2455).
- **Optimized**: (Pipeline) Deleted GenerateBuildInfo.vbs to simplify project compilation.
- **Optimized**: (Particles) Generalized access to particle param variants, with templated argument types: VMAX, VMIN, VRANDOM, random range, etc. Allows templated bounding volume computation in general or specific emitter configurations. Consolidated GetStaticBounds arguments into FStaticBounds struct. Moved travel helper functions into Travel namespace.
- **Optimized**: (Build) Remove animsettings from build output, they are not required at run-time (CE-3269).
- **Optimized**: (Build) Support down-target VS2012 native toolchain from VS2013 IDE (CE-4751).
- **Optimized**: (EntitySystem) Removed deprecated OnStartAnimation and OnEndAnimation script callbacks.
- **Optimized**: (Input) Unified DeviceType and DeviceId.
- **Optimized**: (GeomCache) Split geom cache fill job in high priority transform update and mesh update jobs.
- **Optimized**: (GeomCache) Lower decompress & decode job priority to eStreamPriority.
- **Optimized**: Clean up CObjManager::UpdateRenderNodeStreamingPriority.
- **Optimized**: DynArray improvements and refactoring: Default allocator now stores pointer to original allocator in memory, for compatibility across modules. Refactored allocator templates to use one multi-purpose alloc() function. Refactored template components to be more independent: SmallDynStorage instead of SmallDynStorage<T, I>. Faster capacity storage scheme in SmallDynStorage. FixedDynArray and StaticDynArray now work correclty with non-POD types, constructing and destructing elements only on use. Removed FixedDynStorage, RawStorage, InitStorage classes. Various small fixes and optimizations. Moved code for clarity. Overall less code than before.
- **Optimized**: Moved each attachment-class is in its own file.
- **Optimized**: Updated solution file to compile the EditorWwise project.

### Audio

- **New**: (ACB) Support for localised soundbanks.
- **New**: (MaterialEffects) Added character_speed parameter support for footsteps.
- **New**: Added support for Rtpcs in AudioEnvironments, fixed AudioEnvironments being stuck at non-zero values, added removing AudioEnvironments after their amounts reach 0.0f (CE-4713).
- **New**: Adjusted audio proxies to make use of pseudo lip-sync.
- **New**: Added an ability to register a callback to be called when a Trigger is finished.
- **New**: Enabled new listener_distance feature in Wwise 2014 and implemented on explosion blend containers.
- **Fixed**: (ACB) Switches can be created inside subfolders (CE-4811).
- **Fixed**: (ACB) Crash when opening level with audio controls in the undo/redo queue (CE-4813).
- **Fixed**: (ACB) Drop down filters affect wwise controls (CE-4820).
- **Fixed**: (ACB) Folders filtered out if no control they hold matches filter (CE-4819).
- **Fixed**: (ACB) Clear all folders and switches when reloading (CE-4818).
- **Fixed**: (ACB) Fixed switches serialization (CE-4817).
- **Fixed**: (ACB) Issue with controls getting a "_1" when connected to another control (CE-4821).
- **Fixed**: (ACB) Middleware controls unique by name AND type (CE-4837).
- **Fixed**: (ACB) Saving switch local requests properly (CE-4852)
- **Optimized**: Adjusted CVar description of s_WwisePrimaryPoolSize and s_WwiseSecondaryPoolSize.
- **Optimized**: Adjusted data types for printing numbers in log messages in CryAudioImplWwise and CrySoundSystem projects.

### Rendering

There was an update for Area Lights for 3.6.10 to bring them up to PBS compatibility. To use AreaLights, please use the**r_DeferredShadingAreaLights 1** CVar. This is still WIP so please let us know any bugs you may find!

- **New**: PBR Area Lights support.
- **New**: Per Character Shadow Maps (** Environment:PerEntityShadows** node).
- **New**: Method to disable shadow lod bias per rendernode.
- **Fixed**: Don't update static shadow frustum projection parameters during incremental updates (CE-4756).
- **Fixed**: Find shadow casters in vis areas as well when static shadow bounds are reset.
- **Fixed**: Log sampler/texture mismatch once per case to prevent Editor hanging (CE-3950).
- **Fixed**: Adding missing AMD library header.
- **Fixed**: Shadows from point lights for objects with custom shadow map.
- **Fixed**: Render front and back faces for stencil cull on per object shadow maps.
- **Fixed**: Make vis areas work with tiled shading, fix 'AffectsThisAreaOnly' light flag, fix 'IgnoreGI' vis area flag (CE-4171).
- **Fixed**: Reset VisArea shader flag before the deferred shading pass (CE-4783).
- **Fixed**: NEAREST objects should be in camera space in the shadow pass as well. Make nearest shadow filter kernel size independent of nearest shadow map size (CE-4672).
- **Fixed**: Another set of MGPU optimizations (removed redundant clear from adaptive luminance, split out the measured luminance RT into a texture which is splatted onto each gpu separately, widened the mgpu begin/end resource calls around temporal AA).
- **Fixed**: Restore m_PersFlags after shadow stencil passes so RBPF_MIRRORCULL is not set for fullscreen quad.
- **Fixed**: Broken light volumes. RBPF_MIRRORCULL is still required for light volume rendering.
- **Fixed**: Clear shadow pool allocations when shadow pool is resized.
- **Fixed**: Pool shadow map update logic.
- **Optimized**: Correctly display 'Shadow pool thrashing' warning when tiled shading is used.

### Game

- **New**: Added shortcut key (numpad insert/0) to toggle mn_debug for the local player.
- **New**: Restored optional stdwheeled vehicles from SDK 3.4 (CE-4723).
- **Fixed**: AI Communication configs were not loaded in time due to different initialization order when in editor mode (CE-4383).
- **Fixed**: Refactored multiplayer ladder logic to handle unreliable aspect.
- **Optimized:** Removed obsolete params from FragGrenades script. Structure tidy.
- **Optimized:** Removed deprecated "pose" parameter from ItemSharedParams (CE-4714).
- **Optimized:** Tweaked player sprint params to make it look less like a bug when player runs out of Stamina.

### Assets

- **New**: Added RocketLauncher Mannequin setup.
- **New**: Added Grenade 3P mannequin setup. Some tweaks to nw setup to match C3.
- **New**: Shotgun: Added forcefeedback and weapon_lowering fragments.
- **New**: Added rocketlauncher animations.
- **New**: Added workshop files.
- **New**: Adding Object and Animations and Libs for C3 boids to SDK.
- **New**: Animations for the spider.
- **New**: Added HMG anims.
- **New**: (Audio) Added generic explosion assets and implemented in Wwise and Editor.
- **Fixed**: (Audio) Tagged explosion particles with new created ATL triggers.
- **Fixed**: Set FPSway fragments to "loop" for Shotgun.
- **Fixed**: Incorrect default model path on DestroyableObject entity (CE-3843).
- **Fixed**: crouch+rotation issue in MotionTurn 3P. Needs Loop flag to not cause delay.
- **Fixed**: Disabled "TriggerOnce" on Forest waterfall area trigger so the effect triggers more than once (CE-4707).
- **Fixed**: Fixed boat explosion reflection artifacts. Switched from Additive to Alpha Based blend type (CE-2545). Removed tiny smoke particle not visible.
- **Fixed**: Renamed head_noanim to head_a.skin. Renamed head_a to head_anim.skin. Anim version causing issues on ladder/vehicles (CE-4715).
- **Fixed**: (UIActions) Consoles: Removed unneeded minimap resolution logic (CE-4412).
- **Optimized:** Changed "default" 1P slide fragment to "SDKGrenade".
- **Optimized:** Changed "idle_break" and "slide" from weapon-specific to "Default" as they all shared the same settings anyway.
- **Optimized:** Updated RocketLauncher script: Setup tags, commented out DBAs precache until they're created, removed deprecated aimAnims content, removed erroneous MP param inside SP block, reference new 1p mesh, removed boneAttachments block, removed Nanosuit "PowerAttack" params, tweaked ZoomMode settings.
- **Optimized:** Delete old rocketlauncher asset.
- **Optimized:** Split human.adb CoverHigh/Low fragments into dedicated ADBs to shrink size of human.adb.
- **Optimized:** Split human.adb weapon fragments into dedicated ADBs to shrink size of human.adb.
- **Optimized:** Moved "TorsoDetail" fragments to their own ADB file to split out human.adb and shrink its size.
- **Optimized:** Split out FFEvents to separate ADB for Shotgun to match other weapon setups.
- **Optimized:** Removed empty fragment for SDKRifle leave_modify.
- **Optimized:** Pistol Mannequin setup: Removed unused proclayer clips. Fixed some 3p anims using Rifle anims instead of Pistol anims. Removed unneeded MotionJump setup (uses Default). Added additive ironsight anims.
- **Optimized:** Updated equipment pack scripts with latest accessories.
