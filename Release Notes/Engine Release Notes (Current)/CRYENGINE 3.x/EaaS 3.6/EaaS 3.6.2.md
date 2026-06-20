# EaaS 3.6.2

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/47316993/pages/44963007
- Page ID: 44963007
- Breadcrumb: Engine Release Notes (Current) > CRYENGINE 3.x > EaaS 3.6 > EaaS 3.6.2
- Parent: EaaS 3.6

## Content

Released May 28th, 2014

##
Fixed

-
(Shaders) Water ripples are not generated when shooting at or entities collide with Ocean surface) (CE-217).

-
(Shaders) Water sss was not taking into account fog color neither sun intensity anymore (CE-628).

-
(Shaders) Eyeball is rendered as opaque object to avoid sorting issues with the tear layer (CE-3022).

-
(Shaders) Fixed generic SSS support in Illum shader (CE-3023).

-
(Shaders) Fix for shader compile error: SParticleVertex.blendTC needs to be float4.

-
(Rendering) Ensure that light projector textures don't get downscaled in low spec and are not streamed, otherwise they won't work with tiled shading (CE-3231).

-
(Rendering) Revived radial/directional blur and merged into regular motion blur (CE 3249).

-
(Rendering) Fix dissolve for vegetation.

-
(Rendering) Render shadow casters inside vis areas into static shadow map.

-
(Rendering) Fixed specular target not being bound for ambient pass (CE-3207).

-
(Rendering) Enabled BC1 compression for LightProjector preset so that texture will work with tiled shading (CE-3231).

-
(Rendering) Fixed probe box clipping in tiled shading (could have caused NaNs).

-
(Rendering) Fix static shadow map when e_StreamCgf=1: Don't consider collision and raycast proxies as shadow casters.

-
(Rendering) Update streaming status on designer objects so they will get rendered into static shadow map.

-
(Rendering) Don't globally overwrite shader specified cull mode for point lights. Enable back face culling for sun shadows (CE-3001).

-
(Rendering) Fixed vertex color support for eyes so that the specular overlay can be masked properly.

-
(Rendering) Fix for sampler mismatch in fog shadows (CE-1186).

-
(Rendering) Potential crash in dependency of r_MSAA CVar accessed in r_AntialiasingMode callback (CE-3375).

-
(Rendering) Disabled depth clip for stencil passes so geometry beyond far plane is handled correctly.

-
(Audio) Fixed where we lost the audio listener on a view.

-
(Audio) Fixed footstep sound culling distance by checking actor against listener instead of actor against client.

-
(Audio) Fixed sound obstruction so delayed playback works again.

-
(Statoscope) Datagroup a - need metrics (CE-3215).

-
(Statoscope) DataGroup g - Unknown stat tracked needs explanation (CE-3226).

-
(Statoscope) Datagroup e (ef_lists) broken (CE-3217).

-
(Statoscope) datagroup broken (CE-3185).

-
(Statoscope) Screenshot capture - fullscreen 1080p = bad screenshot (CE-1701).

-
(Statoscope) Crash when e_statoscopeScreenshotCapturePeriod is set in system.cfg.

-
(Statoscope) ArtProfile - NumLightingDrawcalls - incorrect stat (CE-3250).

-
(Statoscope) Default the log destination to 1 (socket logging) (CE-3208).

-
(AISystem) Crash when creating a new level in Sandbox while AI/Physics is active fixed (CE-3094)

-
(AISystem) Out-of-bounds access in InterpolatedPath.

-
(AISystem) Fixed AI alertness level not being set in MBT.

-
(Material) Fix for material editor causing crash when texture slot didn't contain fullstop (nearest_cubemap).

-
(Material) Hiding Environment map slot for PBR based shaders (CE-1711).

-
(CryDesigner) Switched data format of designer from xml text to xml encoded Binary.

-
(CryDesigner) Fixed a bug on a crash happening when entering edit mode (CE-3207).

-
(CryDesigner) Fixed a bug on areasolid having physical data (CE-3207).

-
(CryDesigner) Fixed a crash bug happening when entering the pivot tool.

-
(CryDesigner) Fixed creation of invisible designer object after clicking "Designer" button during creating a primitive shape.

-
(CryDesigner) Fixed a bug related to plunging into the infinite loop when switching a designer mode after undoing.

-
(CryDesigner) Fixed a bug of the Extrude Tool about incorrectly dealing with the side regions in extruding and not deleting opposite regions.

-
(CryDesigner) Fixed a bug of some regions disappearing after drawing lines between inner parts in a region.

-
(CryDesigner) Fixed a bug in the Move Tool omitting a vertex between an another edge.

-
(CryDesigner) Improved a way of editing in 2D viewport (CE-2479).

-
(CryDesigner) Got the manipulator for selected elements(Vertices,Edges or Faces) to be invisible when the empty space is selected (CE-3418).

-
(CryDesigner) Fixed a bug so that empty designer is not allowed to be cloned.

-
(Trackview) Fix delete sequence always throwing an exception.

-
(Trackview) Fix sequence renaming by context menu (CE-2976).

-
(Trackview) Fix infinite loop when renaming entity that is in sequence.

-
(Trackview) Crash during shutdown if trackview sequence is active.

-
(Scaleform) Crash when UIElement is invalid in material editor.

-
(Scaleform) UI disappeared when hitting return.

-
(Scaleform) UIElements are not updated in the renderer (CE-3152).

-
(Scaleform) Stall during level unload.

-
(Scaleform) Changed logic for in-game mission display.

-
(Game) Assert failed when jumping rapidly - caused by camera shake.

-
(Game) Timedemo crashing the editor (CE-3073).

-
(Game) Need to restart before doing a second timedemo.

-
(Game) Added check to prevent AI from receiving health regeneration (CE-772).

-
(Ropes) Some rope attachment serialization fixes.

-
(Ropes) Rope slicing sometimes not detaching tied objects (CE-3328).

-
(Ropes) refcounting issue with subdivided ropes (CE-3122).

-
(Ropes) Potential mem corruption in rope serialization (CE-3122).

-
(Particles) bOrientToVelocity and TurbulenceSpeed/Size combination, fCameraOffset, connected-particle tiling with negative texture frequency.

-
(Particles) Make sure particle don't creep during 0 steps (CE-3103).

-
(Particles) Fixed incorrect emitter location during the first frame when using the mannequin ParticleEffect proc clip.

-
(Particles) Fixed particle effects created from the dedicated Mannequin proc clip ignoring the given reference joint name (CE-3162).

-
(Physics) Editing water level not affecting the physics immediately (CE-1073).

-
(Editor) Objects: Better link visualization.

-
(Editor) Generated a name of GeomEntity type based on a mesh file name (CE-2370).

-
(Mannequin) Fixed Gizmo manipulations in the Mannequin editor not triggering a modification of the database being updated.

-
(Assets) Forest: Fixed cave solid using incorrect material, fixed broken cover surface entities.

-
(Assets) Turret: Added in Mannequin setup and audio.

-
(Assets) Fixed shading issue with concrete_beam assets.

-
(Assets) Fixed Light projector textures not being set to 512x512px and using the LightProjector preset.

-
(Assets) Numerous material/texture fixes for missing content.

-
(Assets) Numerous PBS-related tweaks to Materials/Textures.

-
(JobManager) Profiler doesn't show main/render thread information (CE-2935).

-
Fix deadlocks if number of job threads is greater than number of frames in Alembic.

-
When resizing to a larger terrain size, only manipulate the area that matches the size of previous heightmap and leave the rest of the area with zero height (CE-3166).

-
Disabled async dips for PC (Editor may crash when opening character editor in CCryDeviceContextWrapper::PSSetShaderResources) (CE-3147).

-
Fixed access to 0-entry arrays.

-
Fix crash in alembic compiler when color array is missing.

-
Handle light volume hash collisions. Fix light volume index calculation.

-
Fixed int overflow when biasing.

-
Fixed assert in SSAO blur (CE-3042).

-
Scale depth values in r_deferredshadingdebug 1 (CE-2114).

-
Fixed texture stream thrashing due to double advancement of far zone round id.

-
Fix wrong LOD calculation in character texture streaming.

-
Ensure precache lod is clamped to available lods.

-
Pivot distance was wrong for streaming, uses adjusted bbox distance, real fix is to precache +1/-1 LODs everywhere.

-
Crash on level load when path contains special characters.

-
Fixed issues with duplicate CVars registered in config files and code (CE-3198).

-
Potential fix for printf validation fatal error.

-
Fixed restarting the Editor with the character editor open causing in-game textures to appear low res (CE-3195).

-
Fixed NaN check in SSRRaytrace (D3D11 define is not existing any more) (CE-3199).

-
Breakable joint assignment issue (CE-2576).

-
Fixed problem with multi-part living entities.

-
Fixed contact stability problems with small breakable chunks.

-
Fixed problem with character aux physics and bones' rotational velocity estimation.

-
CHitDeathReactions Found more than one tag in container (CE-1359).

-
Fixed Rope on Light in starting Ruin. Had FrictionPull set to max (100). Reduced down to 2.

-
Fixed missing material warning in HUD.

-
Fixed getControlVal() for listbox items. Now returns the value specified when item was created instead of the caption. to get caption, use GetListboxItemCaption.

##
Added

-
(AISystem) Added AIActionSequence-compatible flow node to approach and enter vehicles.

-
(AISystem) Added AISequence-compatible flow node "AISequence:WeaponDrawFromInventory".

-
(AISystem) Added AISequence-compatible nodes for drawing and holstering the weapon.

-
(Flowgraph) Exposed "FileName" to DecalPlacer entity via Flowgraph.

-
Added toolbar icons for animation import panel and animation compression editor.

-
Added Snow.lua script for use with Snow entity.

##
Deleted

-
(Entity) Hide obsolete ShootingTarget entity.

-
(Entity) Set RigidBody entity to invisible. RigidBody is obsolete as users should always use RigidBodyEx instead.

-
(Entity) Hiding ParticleEffect entity from entity list. Deprecated method of adding PFX to level. Use Particle Editor or Particle Effect button in rollupbar (CE-1205).

-
(Entity) Remove unused TowerSearchLight entity and code.

-
(FlowGraph) Hide obsolete nodes: Image:Glittering, Image:Global, Image:Glow, Image:DistantRain, Image:HUDHitEffect, Image:Scratches. Fixed bug with Image:Condensation node not being properly set in Obsolete category (CE-296).

-
Delete unused ZeroG/GravitySphere lua script. Note the GravitySphere script inside Entities/Physics remains functional (CE-873).

##
Optimization

-
(SSE) Enabled on 64bit.

-
(Config) Update all PC configurations with better performance CVars.

-
Additional motion blur optimizations.

-
Use r_motionBlurQuality 0 on low specs.

-
Geometry cache SSE3 code path for PC.

-
Ocean rendering optimization: Fixed wrong flag usage, disabled deprecated matrixes usage to prevent redundant CBs update (CE-3101).

##
Refactored

-
(Common) ZeroInit<>.

-
Reviving grain params through common grain rendering (CE-296).

-
Rollback change which removed Terrain Occlusion / Sky Brightening from TOD/Terrain Texture Generation dialog (CE-3230).

-
Move geom cache hit test to CGeomCacheEntity.

-
Tiny cleanup in ShadowMaskGen.cfx.

-
Disabled deprecated light clipvolumes (LightShape) geometry. Feature is not compatible with tiled shading/latest engine updates - from 3.6 only clipboxes (LightBox) will be supported.

-
PBR related shader cleanups: Renamed gloss to specular where appropriate. Removed gloss in specular alpha option.

-
Adjusted nearest probe picking to better fit how probes are setup now (use layers rather than global probe and check against OBB).

##
Tweak

-
(Renderer) Removed vegetation profiler left overs.

-
(Shaders) Use red channel instead of green channel for eye specular overlay texture.

-
(Audio) Add sound obstruction data to surface type instead of relying on the pierceability. Renamed some variables to suit.

-
(Audio) Turn off max obstruction radius scaling by default.

-
(Audio) Set max obstruction level to full (1.f).

-
(RC) ImageCompiler: removed CUDA, nvtt, ATI Compress.

-
(Particles) Emitters created through the ParticleEffect procedural clip are immediately created with the correct location, instead of waiting for the attachment update.

-
(CryDesigner) Added a routine to delete the existing binary files, DesignerObjects.dat and DesignerMeshes.dat as they're no longer needed/used.

-
(CryDesigner) Removed the items in the Preference related to saving designer data as binary form.

-
(CryDesigner) Added a routine to getting total polygon count of a designer object.

-
(CryDesigner) Improved the Extrude tool for boundary edges created with pulling not to remain.

-
(CryDesigner) Improved the box creation tool so that union operation can be applied to the result regions.

-
(CryDesigner) Improved the Extrude tool for boundary edges created with pulling not to remain.

-
(CryDesigner) Made the selection of elements correct and more sensitive

-
(CryDesigner) Removed "Separate" check box in the primitive creation panel.

-
(CryDesigner) Changed a destination buffer for decoding base64 type from std::vector to array.

-
(Editor) Added secondary outputs to MissionStateListener FG node.

-
(Editor) reworked reload script functions in editor (CE-1451).

-
(Statoscope) e_statoscopeEnabled=0 by default to avoid log spamming

-
(Flowgraph)  Blacklist obsolete nodes: AI:Anim/Ex, AI:Goto/SpeedStance, AI:Interested/InterestingEntity, AI:ShootAt, AI:WeaponDraw/Holster/Select. Use replacement AISequence nodes instead (CE-2964). Cleaned out Rem/Ren entries from Blacklist no longer required.

-
(Assets) Updated PFX libraries: Removed some duplicates, updated lighting settings, moved some unnecessary children pfx to parent.

-
(Assets) Forest: Lowered ropes FrictionPull from 100 to 1 (CE-3258). Removed subdivision on Ropes and increased segment count (CE-3258). Decrease LOD ratio for noticeably popping objects.

-
(UIActions) Cleaned SP_Objectives setup with new Secondary output ports. Added in IsMuliplayer check for scoreboard/objectives to only display in their appropriate mode (CE-3336).

-
Adjusted default probe falloff to 0.3.

-
Removed unnecessary attachment update call in the ParticleEffect procedural clip.

-
Player characters always have high streaming priority.

-
Removed bAll parameter in CObjectArchive::CObjectArchive().

-
Fixed missing type when only including "PixelFormats.h".

-
Adjusted error-message for incompatible texture-format for tiled-shading (CE-3253).

-
Cleaned up sketch mode configs.

##
New Feature

-
(Audio) Introduced audio obstruction offset on SoundEventSpots.

-
(AISystem) "crouch" stance is now also supported in movements (CE-3310).

-
(Lobby) Steam Invite friends.

-
(Renderer) Displayinfo compact mode (r_DisplayInfo 3: fps - ms).

-
(Particles) Comment, Inheritance, System.Default effect.

-
(Particles) Optionally disable surface alignment for particles (CE-3103).

-
(Editor) Rotate objects during creation and cloning with CTRL + mouse scrollwheel.

-
(Editor) Option to show mesh statistics on mouse over.
