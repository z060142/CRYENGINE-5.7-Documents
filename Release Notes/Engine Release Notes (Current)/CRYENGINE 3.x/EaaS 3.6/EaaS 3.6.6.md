# EaaS 3.6.6

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/47316993/pages/44963012
- Page ID: 44963012
- Breadcrumb: Engine Release Notes (Current) > CRYENGINE 3.x > EaaS 3.6 > EaaS 3.6.6
- Parent: EaaS 3.6

## Content

Released September 2nd, 2014

##
Sandbox

-
**
New
**
: (FBX) Added support for 'pivot' attribute in export info file.

-
**
New
**
: (FBX) Updated dialog with static mesh import options.

-
**
New
**
: (Material) Option to convert single- to Multi-Material via right-click context menu (CE-4116).

-
**
Fixed
**
: (FBX) Some usability fixes for colors, default column widths.

-
**
Fixed
**
: (FBX) Changed implementation of QProgressDialog to custom implementation that actually blocks until the operation finishes.

-
**
Fixed
**
: (FBX) Remove many modal loops that are incompatible with current Qt usage, causing a crash on exit.

-
**
Fixed
**
: (FBX) Updated dialog with static mesh import options.

-
**
Fixed
**
: (FBX) No longer enumerate the rootnode when generating the node path name.

-
**
Fixed
**
: (FBX) Refactored scene/node access from INode* to IScene* & SNode.

-
**
Fixed
**
: (FBX) Update XML + world/local logic for RC.

-
**
Fixed
**
: (FBX) FBX origin was double-escaped.

-
**
Fixed
**
: Editor crashes during map load if the lighting tool is still open (CE-4139).

-
**
Fixed
**
: Several map contents missing when loading a map for second time after saving it (CE-3406).

-
**
Fixed
**
: Erasing heightmap also erases material painting (CE-364).

-
**
Fixed
**
: Don't attempt to load manifest file if it doesn't exist, or warnings will show in the log (CE-4284).

-
**
Optimized
**
: (FBX) Default save location is now inside sys_game_folder/Objects.

-
**
Optimized
**
: (FBX) Refactored tree background color to better solution.

-
**
Optimized
**
: (FBX) Refactored XML generator for better XML and RC escaping.

##
Audio

-
**
New
**
: (ACB) Added icon for sound banks. Show in connection panel instead of preload icon.

-
**
New
**
: (ACB) Added hardcoded defaults when config.xml file is not present.

-
**
New
**
: (ACB) Save with Ctrl+S.

-
**
New
**
: (ACB) Show all levels in the scope drop-down.

-
**
New
**
: (ACB) In the scope menu highlight levels not found in the project.

-
**
New
**
: (ACB) Prevent controls with the same name in the same scope.

-
**
New
**
: (ACB) Loads default controls when they don't exist in the project.

-
**
New
**
: Added AudioAreaAmbience entity for convenient implementation of area based audio ambiences.

-
**
Fixed
**
: (ACB) Remove extension when making a preload from a sound bank.

-
**
Fixed
**
: (ACB) Prevent controls with the same name when dragging directly from the middleware panel.

-
**
Fixed
**
: (ACB) Adding same control to different groups in a preload.

-
**
Fixed
**
: (ACB) Typo on the default controls folder name. Use lower case for the levels folder.

-
**
Fixed
**
: (ACB) Prevent dragging controls to the root of the tree view.

-
**
Fixed
**
: (ACB) Disable drag and drop from the ATL controls panel to the connection list

-
**
Fixed
**
: (ACB) Problems with controls getting added inside switches.

-
**
Fixed
**
: (ACB) Only alphanumeric characters and no spaces in a controls name.

-
**
Fixed
**
: AudioSystem handles blocking-sync-callback type PushRequests properly now.

-
**
Fixed
**
: Audio performance counter in the DisplayInfo (CE-4137).

-
**
Optimized
**
: (Editor) Removed obsolete audio options from Sandbox.

-
**
Optimized
**
: Eased out internal AudioThread to not busy loop.

-
**
Optimized
**
: Audio listeners are only informed if their request generally processed, removed event for signaling the audio thread as it proved too expensive.

##
Engine

-
**
Fixed
**
: (FBX) Updated FBX functionality to match dialog, other RC fixes.

-
**
Fixed
**
: (FBX) Properly handling Y-up and Z-up information from the scene, instead of ignoring it.

-
**
Fixed
**
: (FBX) Handling of non-identity transforms in root nodes.

-
**
Fixed
**
: (Steam) Crash when taskID was invalid.

-
**
Fixed
**
: (Steam) Guard for toomanytasks errors.

-
**
Fixed
**
: (Physics) Some rope collision fixes (line mode).

-
**
Fixed
**
: (Physics) CPhysArea.GetStatus now properly forwards to base class. Fixed improper transform in CGeometry::GetRandomPos.

-
**
Fixed
**
: (RC) Stopped making incorrect assumptions in ANMSaver.cpp about the order and the values of chunk ids in chunk files (CE-4182).

-
**
Fixed
**
: (Action) Timedemo - NULL pointer crash on Loading/Saving if m_pGameSerialize is not initialized.

-
**
Optimized
**
: Automatic rope assignment for bones not named "rope...".

##
Particles

-
**
Fixed
**
: More reliable phys area updates; EventPhysAreaChange now merges old and new area bounding boxes; SPhysEnviron event handler now updates area position synchronously, avoiding 1-frame delay in most cases. SPhysEnviron.GetWorldPhysAreas retains existing SArea objects rather than replacing them, to avoid references to obsolete SAreas.

-
**
Optimized
**
: Manager.Update optimisation. Removed some obsolete PS3 code. All emitters can now Update in threads. Fixed invalid asserts.

##
Game

-
**
Fixed
**
: Set hud_double_taptime CVar from 0 to 0.25 by default as it's required for gamepad grenade doubletap switching.

-
**
Fixed
**
: Set correct (case-sensitive) path for lightning entity particle effect (CE-4159).

-
**
Fixed
**
: Don't call profile save every time a server comes in.

-
**
Fixed
**
: Spawning a vehicle and entering it via FG causes a crash on exiting game mode (CE-4209).

-
**
Fixed
**
: Vehicle system assumes that actors have animated characters (CE-4133).

##
Assets

Several new assets have been implemented into the build. Feel free to start using them now! There will be further implementation script/code side to make these usable and further changes and more items will come in future updates.

-
**
New
**
: Added sniper scope asset.

-
**
New
**
: Added assault scope asset.

-
**
New
**
: Added knife asset.

-
**
New
**
: Added character glasses asset.

-
**
New
**
: Added assets for daytime ambience.

-
**
New
**
: Added forest/hangar reverb environment.

-
**
New
**
: Adding Object and Animations and Libs for new boids.

-
**
New
**
: Added environment_listener and environment_sound parameter.

-
**
New
**
: Added v_shared_a bank.

-
**
New
**
: Added wind_intensity game parameter.

-
**
New
**
: Added new metal cable mat and textures.

-
**
New
**
: Created soundcaster session for airfield.

-
**
New
**
: Animations for the spider boid.

-
**
New
**
: Added assets to originals folder for general_ambience.

-
**
New
**
: Added Sound layer to Airfield Level. Removed Sound Objects from Airfield Layer and added to Sound Layer.

-
**
New
**
: Added forest and airfield reverb auxiliary.

-
**
New
**
: Added several archetype examples for Light setups.

-
**
New
**
: Added forest reverb and created a shareset workunit for the sdk reverb presets.

-
**
New
**
: Added AS_wind_intensity on mountain.

-
**
New
**
: Game parameter general_ambience_wind_intensity in ACB.

-
**
New
**
: Added v_shared_a, containing shared vehicle media.

-
**
New
**
: Added Generic Leaderboard (CE-3527).

-
**
New
**
: Lobby can support voice chat between teammembers, or everyone in the lobby (CE-3525).

-
**
New
**
: User stats for Steam (CE-4128).

-
**
New
**
: Create dialog spinner for waiting times (CE-4178).

-
**
Fixed
**
: Issue with Humanoid character not holding weapon correctly by adding 'weapon' bone joint.

-
**
Fixed
**
: (UIActions) Re-implement loading screen for loading levels in menu (CE-4184).

-
**
Fixed
**
: (UIActions) Disable mistakenly activated scrollbar in leaderboard.

-
**
Fixed
**
: (UIActions) Coordinates for setting images in Main UI now are positioned with origin point in 0/0.

-
**
Fixed
**
: (UIActions) Added visible attribute to addImage FG node to make image visible once it's loaded (CE-3793).

-
**
Fixed
**
: (UIActions) Remove auto search link (CE-4180).

-
**
Fixed
**
: (UIActions) Scrollbar is now its own reusable component.

-
**
Fixed
**
: Updated Beech tree assets: Fixed LODs. Fixed and simplified beech_bush material, halved SubIDs. Added additional versions hidden in Max file.

-
**
Fixed
**
: Forest: Removed Lighthouse visarea/portal setup. Redid lighting setup in Lighthouse. Fixed doors not opening correctly (CE-4167). Removed FG logic related to doors.

-
**
Optimized
**
: Deleted Jointed_breakable library and moved two archetypes into Destroyable library.

-
**
Optimized
**
: Tweaked attenuation settings on jet. Enabled send to virtual voice on jet.

-
**
Optimized
**
: Changed environmental_sound parameter range to 1.

-
**
Optimized
**
: Tweaked mass, damage and other various physics settings for physics/destroyable archetype libraries.

-
**
Optimized
**
: Renamed to wind_intensity and relinked with gameparameter.

-
**
Optimized
**
: Added comments to flowgraph.

-
**
Optimized
**
: Tweaked attenuation settings on jet_engine_idle.

-
**
Optimized
**
: Tweaked reverb sharesets.

-
**
Optimized
**
: (Audio) Renamed tod to time_of_day.

-
**
Optimized
**
: Tweaked reverb levels.

-
**
Optimized
**
: Enabled use shareset on reverbs / auxiliary reverbs.

-
**
Optimized
**
: Enabled game defined auxiliary on footsteps

-
**
Optimized
**
: (ActionMaps) Removed unused MP radio commands. Removed commented out use functions. Re-added toggle_explosive/special actions for special weapon selection. Moved quick-throw grenades to player_mp actionmap. Readded zoom_toggle action for scope use. Cleaned out alternative controller maps with invalid setups. Increased version number.

-
**
Optimized
**
: Widened crossfade in tail blendcontainer.

-
**
Optimized
**
: Created Hangar Ambience Blend Container and Play Event.

-
**
Optimized
**
: Enabled random_crow media in l_forest_a.Disabled random_crow media in g_environment_a.

-
**
Optimized
**
: Cleaning duplicate warnings, moved shared environment media from levels to g_environment_a, excluded media and data from testsoundbank.

-
**
Optimized
**
: Enabled streaming on ambience loops.

-
**
Optimized
**
: Changed virtual voice setting to kill voice - was set to continue, so every tail would stack up when firing inside and play when you would enter an outside area.

-
**
Optimized
**
: Set up reverb environment for AAEs.

-
**
Optimized
**
: Set virtual voice behaviour on actormixers.

-
**
Optimized
**
: Renamed general_ambience_wind_intensity to wind_intensity.

-
**
Optimized
**
: Used seagull from forest for airfield.

-
**
Optimized
**
: Set attenuation for ambiences to 3D.

-
**
Optimized
**
: Disabled shadow casting on lighthouse glass submat.

-
**
Optimized
**
: Enabled Game Defined Auxiliary Sends.

-
**
Optimized
**
: Recreated woodpath LODs. Fixed proxies. Deleted 'pillars_b_0x' cgfs not in Max scene.

-
**
Optimized
**
: Changed attenuations on jet_engine_idle.

-
**
Optimized
**
: Changed hangar verb volume.

-
**
Optimized
**
: Added rtpc in flowgraph to receive tod in wwise.

-
**
Optimized
**
: Enabled overwrite g.d. auxillary on cave_psycho_tone.

-
**
Optimized
**
: Enabled random_crow_37 in crow_oneshot.

-
**
Optimized
**
: Changed game defined aux send level on footsteps.

-
**
Optimized
**
: Added AS and AAE for the hangar buildings.

-
**
Optimized
**
: Tweaked blend containers.

-
**
Optimized
**
: Set room small environment for forest hut.

-
**
Optimized
**
: Excluded newly imported environment sounds from g_environment_a to avoid duplicate media.

-
**
Optimized
**
: Switched loading screens and minimaps for Forest and Airfield to SF_Image preset (CE-4174).

-
**
Optimized
**
: Named audiotriggerspot on jet.

-
**
Optimized
**
: Excluded duplicate media now contained in v_shared_a from other vehicle soundbanks.

-
**
Optimized
**
: Added rtpc control for general_ambience_ss_wind.

-
**
Optimized
**
: Selected added shareset for cave reverb.
