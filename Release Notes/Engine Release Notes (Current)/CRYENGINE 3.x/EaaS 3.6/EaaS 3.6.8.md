# EaaS 3.6.8

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/47316993/pages/44963014
- Page ID: 44963014
- Breadcrumb: Engine Release Notes (Current) > CRYENGINE 3.x > EaaS 3.6 > EaaS 3.6.8
- Parent: EaaS 3.6

## Content

Released 2nd October, 2014.

### Editor

- **New**: (Flowgraph) Flow Graph node "AI:ActiveCountInFaction" to count the currently active AIs of a specific faction (4522).
- **New**: (Flowgraph) Added flow graph nodes for regenerating the nav mesh and for getting an entity's bounds (AI:RegenerateMNM + Entity:GetBounds) (CE-4351).
- **New**: (Flowsystem) Support multiple port activations per update.
- **New**: Increased Time of Day 'Bloom Amount' param maximum to 10.
- **Fixed**: (FBX) Updated FBX dialog to use RC manifest function (CE-4448).
- **Fixed**: (FBX) Made CGF save more user-friendly (CE-4379).
- **Fixed**: (FBX) Warnings and errors encountered by RC will now be logged to the editor.
- **Fixed**: (Trackview) HUD + crosshair are not getting disabled & enabled properly (CE-631).
- **Fixed**: (Trackview) HUD visible (floating in midair) during seq playback (CE-2696).
- **Fixed**: (Trackview) Player hands are still attached to the camera during a cutscene.
- **Fixed**: (Flowgraph) Prefab flowgraph node will remember it's visibility settings for ports after changes.
- **Fixed**: (Flowgraph) Input:ActionFilter node outputs not firing.
- **Fixed**: Mute button status remembered when restarting the editor (CE-4015).
- **Fixed**: Some Flare Editor slider bars are not adjustable via click & drag (CE-1690).
- **Fixed**: AI movement request in simulation mode is no longer blocked by a potentially running animation
- **Fixed**: Prevent obsolete "file not found" error message from being displayed when trying to load terrain layer textures (CE-229).
- **Fixed**: AI/Physics is grayed out after creating a new level (CE-4516).
- **Fixed**: Player entity could spawn at a position different than the camera, when switching to game mode (CE-4389).
- **Fixed**: Creating a new level while a level is already loaded no longer attempts to load AI data from the previous level (CE-4430).
- **Fixed**: Converting a material to a multi-material and renaming the sub-material causes a crash (CE-4507).
- **Fixed**: Crash from being stuck in the infinite loop happening as copying a light entity having a lensflare with a lens flare editor open (CE-4494).
- **Optimized**: (Trackview) Re-grouped cutscene settings in trackview scene-edit dialog and greyed out non-compatible features.
- **Optimized**: Set initial default for Terrain Color Multiplier to '8' to lessen color artifacts from terrain texture generation. Any changes are stored to the registry and will become the new default (CE-3774).
- **Optimized**: Improved single-step physics button tooltip.
- **Optimized**: Removed unused IDDs from CryEdit.rc
- **Optimized**: More general names for IDC members.

### CryDesigner

- **Fixed**: Expected behavior as ESC pressed continually (CE-4453).
- **Fixed**: Made a pivot point kept in the middle of the boundbox every time a new primitive shape is created (CE-4457).
- **Fixed**: Crash in the Stair Tool caused by consecutive clicks of a mouse button in the view port (CE-4455).
- **Fixed**: Going into the infinite loop when loading a designer object having lots of polygons.
- **Fixed**: Disappearing a previous created designer object after creating a box object (CE-4357).
- **Optimized**: Renamed a check box called "Display Back Faces" to "Display Back Faces(Editor Only)" to clarify that it's only for Editor use and won't display in Launcher.
- **Optimized**: Renamed "Split" to "Clip" in the codes.
- **Optimized**: Renamed "Faceter" to "PolygonDecomposer".

### Audio

- **New**: (ACB) Multiple selection support.
- **New**: (ACB) AutoLoad on by default.
- **Fixed**: Updated Door.lua to be able and work with the new AudioSystem.
- **Fixed**: Adjusted audio preloads handling code to properly handle new "AutoLoad" property.
- **Fixed**: Fixed the environments not being set for the collisions and bullet impacts.
- **Fixed**: Changed Wwise to use switch logic for rain ambience and integrated in ACB accordingly.
- **Fixed**: Particle effects did not properly initialize their AudioProxy if only the StopTrigger was set.
- **Fixed**: Particle Audio not being affected by the environments.
- **Fixed**: Returning a pointer to a local in GetConfigPath().
- **Fixed**: AudioObjects got stuck due to dangling physics RWI requests.
- **Fixed**: FlowAudioSwitchNode not resetting the same switch state after the first time it is set.
- **Optimized**: (ACB) Hide AutoLoaded preload controls from the control selection.
- **Optimized**: ATL debug name store is now only present in non-release builds.
- **Optimized**: Removed INCLUDE_AUDIO_PRODUCTION_CODE from CryCommon as it is audio specific.
- **Optimized**: Minor cleanup that removed obsolete audio type code.
- **Optimized**: Making full use of NULL pointer check against pEvent in CAudioObjectManager::ReportFinishedEvent.
- **Optimized**: Corrected CVar description and formatting, renamed Wwise specific CVar s_AudioImplementationPrimaryPoolSize and s_AudioImplementationSecondaryPoolSize to s_WwisePrimaryPoolSize and s_WwiseSecondaryPoolSize.

### Engine

- **New**: (RCJob) Support for compiling lua scripts.
- **New**: Removed 64K mesh vertex limit.
- **New**: Allow vertex cloth character attachments.
- **New**: Allow mesh slicing on character attachments + improved cloth-cgf association consistency.
- **New**: Adjusted proxy dialog for different proxy types.
- **Fixed**: (RCJob) Take converted files originally in the levels folder as well, and add them to the loose files.
- **Fixed**: (RC FBX Converter) Added "unitSizInCm" to manifest file.
- **Fixed**: (RC ColladaLoader) Getting rid of internal data duplication (scale/translation/rotation were stored both in transform matrix and in vectors); made some functions 'static' (file scope).
- **Fixed**: (JobManager) Unable to create enough colors for on screen profiler, switching to "golden ratio" color distribution.
- **Fixed**: (Scaleform) Release builds now link against Scaleform Shipping Libs - AMP will be disabled.
- **Fixed**: (Physics) Fix for cloth re-loading.
- **Fixed**: (CryPak) Path "../../../../foo" was "folded" to non-equivalent "..\..\foo", causing incorrect paths being used when saving level.pak (CE-4322).
- **Fixed**: (Action) Exiting game mode while entering a vehicle with a transition animation crashed the engine (CE-4209).
- **Fixed**: Debugging and visualization of proxies.
- **Fixed**: E_debugdraw crash in editor (CE-2836).
- **Fixed**: Crash in r_stats 2 when tech is unknown.
- **Fixed**: Morph threshold popping.
- **Fixed**: Handle incompatible skel-extensions without fatal-errors.
- **Fixed**: Crash when a dba contains animations with more than 255 controllers.
- **Fixed**: Increased buffer for global animations.
- **Optimized**: Removed unused clockspeed measure.
- **Optimized**: Reorder initialization so font is no longer required before intromovie.
- **Optimized**: Fastload is now used only when intromovie is used.
- **Optimized**: Don't sync rmesh on invisible cloth (CE-4451).
- **Optimized**: Vehicle friction tweak (CE-4477).
- **Optimized**: Removed RSA initialization if key is not present.
- **Optimized**: Cleanup r_stat - removing obsolete stats and adding info for the working ones.
- **Optimized**: Improved load profiler annotations.
- **Optimized**: Moved ProfVis compiled version to correct folder.

### Rendering

- **Fixed**: Rain entity "DisableOcclusion" function is broken (CE-4329).
- **Fixed**: Square shadow rendering bug with Snow entity.

### Game

- **New**: (AISystem) AI corpses are now also enabled and managed when playing in Sandbox (CE-4520).
- **New**: (Action) Allow custom player entities.
- **New**: Added back Sprint Stamina function. Tweaked stamina params. Exposed PlayerParams script reloading to Reload Actor Scripts function in Editor.
- **New**: Added "Jump" and "Sprint" outputs to Actor:Sensor flownode.
- **Fixed**: (AISystem) SDK_Grunt behavior trees: whether or not to return to the initial position on Idle can now be controlled via script property "GoBackToStartOnIdle" (CE-4484).
- **Fixed**: CameraShake entity doesn't load params on spawn (CE-1146).
- **Fixed**: CEditorGame::OnSaveLevel() was causing warnings about not found cry file due to duplicates in the file path (CE-4430).
- **Fixed**: Actor:Sensor node doesn't output player sprint (CE-4508).
- **Fixed**: Save/Load Item is not clearing up Actioncontroller ScopeContext when deleted, resulting in dangling pointers.
- **Fixed**: HUD: Ammo for frag grenade reads 0 even if you have one (CE-4306). Clipsize was set to 0 in weapon script.
- **Fixed**: Spawngroups not working (CE-4433).
- **Optimized**: Removed unused spawntext and equipmentpacks from spawngroup entity.
- **Optimized**: Removed unneeded bStopTriggerExecuted variable from Door.lua.
- **Optimized**: Door.lua now only executes stop trigger if it was either opened or closed.

### Assets

- **New**: Added Shotgun mannequin setup. Still WIP, will be some bugs with it on this release.
- **New**: RocketLauncher: New geometry and textures.
- **New**: Added AI Debug config which can be executed in console for quick access to common AI debug vars. Use 'exec aidebug' to run.
- **New**: Added additional character variation CDFs to reference new character attachments.
- **New**: Tent, and Mud Geomcache example assets.
- **New**: Bush and leaves rustling loop events and assets to physics project
- **New**: Beanie, Helmet and Necklace character assets.
- **New**: Added several example glass materials.
- **New**: Added SDK character from 3.5.
- **New**: Added ATL triggers for shotgun.
- **New**: Added missing animation fragments for "Relaxed+Run" and "Relaxed+Sprint" (CE-3765) used by AI when in running/sprint stances.
- **Fixed**: (UIAction) Deleted duplicate 'Control' node loading Hud_Radar inside HUD_3D activated on weapon output. Tidied ThreatLevel nodes.
- **Fixed**: (UIAction) Exclusive controller falsely set on init.
- **Fixed**: (UIAction) hud_low_ammo string being initialized before Localization. Removed hard coded string from FLA file.
- **Fixed**: (UIAction) Multiplayer Infinity K/D Ratio (CE-3337)
- **Fixed**: (Mannequin) Fixed Shotgun jittering through players hands during reload. Needed 'swaphands' proc clip (CE-4492).
- **Fixed**: Example flash assets are not able to be opened. Minimum supported version is CS5.
- **Fixed**: Airfield FG issue of math:equal triggering true and false at the same time added math:round to FG logic to work correctly.
- **Fixed**: Incorrect select sound on Pistol.
- **Fixed**: Mannequin t-posing in MP after vehicle usage.
- **Fixed**: Beach_Rocks: Remove obsolete occlusion proxies. Separated out Proxies from rendermesh. Removed unused MatID 2 (plants) in material and max scene. Repositions LODs for better readability.
- **Fixed**: Updated wagon_goods material, fixed texture path.
- **Fixed**: Tweaked pine tree materials, fixed typo in texture path.
- **Fixed**: Added explosion placeholder to forcefeedback xml.
- **Fixed**: Rotate sunglasses 180 degrees.
- **Fixed**: Rename Geom_Cache folder to GeomCaches to match code references.
- **Fixed**: Updated turntable asset material. Fixed texture path bug.
- **Fixed**: Lighthouse_b mesh disappears if glass shot on certain angles (CE-4470).
- **Fixed**: Explosion entity sends correct explosiontype (CE-4524)
- **Fixed**: Texture path on sniper scope material.
- **Fixed**: Texture pathing in outdoor_spotlight material.
- **Fixed**: Texture path in deformable barrel material. Tweaked material.
- **Fixed**: Texture path in te_elevator asset.
- **Fixed**: Set Layer Activation to 'True' for all head submaterials.
- **Fixed**: Virtual voice setting on particles.
- **Fixed**: Bbox error spamming on coverHigh_tac_grenadeThrow_rgt_3p_01 (CE-3254).
- **Fixed**: Player can get stuck in a running animation loop (CE-3977).
- **Optimized**: Over 100 Wwise audio asset updates and additions.
- **Optimized**: (Mannequin) Deleted duplicate Rifle firemode switch fragments.
- **Optimized**: (Mannequin) Changed "Grenade" to "grenade" to match other item casing.
- **Optimized**: (Mannequin) Removed "Flag" and "Tick" mannequin fragments which are used for C3 gamemodes that SDK currently does not utilize.
- **Optimized**: (Mannequin) Added weapon contexts to 3p preview.
- **Optimized**: Changed animation references from "scar" to "rifle" for Rifle mannequin setup. Added renamed animation files.
- **Optimized**: Renamed SmartObject/Cover "Scar" animations to "Rifle". Updated Mannequin references.
- **Optimized**: Airfield: Split Sound objects into separate Sound layer. Split some FG logic into GTs so Sound is completely isolated into Sound layer.
- **Optimized**: Renamed several MaterialFX setups to work better with Wwise. Changed explode in material effect from _hit to _exp. Moved grenade collisions from collision.xml to bulletimpacts.xml
- **Optimized**: Updated PrecacheLists: Added in new/renamed weapon/attachment content.
- **Optimized**: Updated EntityScheduler: Removed content causing warnings. Added in new weapon/attachment content.
- **Optimized**: Diff and Spec now PBR standard for Knife.
- **Optimized**: Updated container_a asset materials and textures.
- **Optimized**: Tweaked gloss values for beanie.
- **Optimized**: Added DDNA and Opac textures for ground_fern_bush, tweaked material.
- **Optimized**: Removed obsolete eye shader textures from sample head materials (CE-4449). See updated Eye Shader documentation for more information.
- **Optimized**: Tiling of Shotgun detail map increased to reduce noisey look. Updated textures to PBR standards.
- **Optimized**: Changed gloss values to make helmet more shiny. Updated psd and Ddna.
- **Optimized**: Tweaked train_tunnel material and pebbles_leaves textures. Added DDNA.
- **Optimized**: Updated Deer material and textures. Added DDNA, removed DDN. Added PN Triangles Tessellation to body/antlers to smooth silhouettes.
- **Optimized**: Assault Scope added spec map. Tweaked gloss map.
- **Optimized**: Sniper Scope added spec map. Tweaked materials and textures.
- **Optimized**: Deleting unused and low quality "sand" rock asset.
- **Optimized**: Added DDNA version of tarp texture.
- **Optimized**: Removed the refraction on the waterfall pfx. Effect too strong.
- **Optimized**: Removed Flowgraph logic for door open close due to ATL triggering now possible on entity.
- **Optimized**: Removed obsolete FMOD event entries from foostep_player.xml.
- **Optimized**: Enabled raycasting on jetengine.
- **Optimized**: Updated external GameAudio Libs.
- **Optimized**: Readded FG logic for rain spotfx and global time of day rtpc.
